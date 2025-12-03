
# Employee Onboarding — Content Engine (CE) + Process Engine (PE) Full Workflow Design

> Complete, interview-ready design that uses both IBM FileNet Content Engine and Process Engine. Includes CE classes, Event Action, PE process map (steps, queues, timers, milestones, parallel routing, submaps), sample code snippets, and deployment/testing notes.

---

## 1. Overview

**Business Goal:** Automate new-employee onboarding so HR, Manager, IT, and Security complete tasks, documents are stored/tracked in Content Engine, and Process Engine manages routing, deadlines, escalations and auditing.

**High-level flow:**

1. HR uploads employee documents into CE (Document class `EmployeeOnboardingDoc`).
2. CE Event Action starts the PE process `Employee_Onboarding_Process`.
3. PE coordinates verification, approvals, background check submap, IT provisioning (parallel), and final closure. PE updates CE metadata and drives notifications.

**Key capabilities shown:**

* CE document storage + metadata
* CE Event Action -> start PE workflow
* PE Queues (Component & Roster), timers/deadlines, parallel routing, submaps, milestones, escalation (malfunction) handling

---

## 2. Content Engine (CE) Design

### Object Store & Foldering

* Object Store: `HR_ObjectStore`
* Root folder: `/HR/Onboarding/2025/`
* Per-employee folder: `/HR/Onboarding/2025/Employee_<EmployeeID>/`

### Document Class

**Class name:** `EmployeeOnboardingDoc`
**Base class:** `Document`

**Important Properties (CE metadata):**

* `EmployeeID` (String / indexed)
* `EmployeeName` (String)
* `Email` (String)
* `Designation` (String)
* `Department` (String)
* `JoiningDate` (Date)
* `Status` (String) — (Pending, In-Progress, Onboarding Completed, Rejected)
* `PEProcessInstanceID` (String) — link to PE
* `BackgroundCheckStatus` (String)
* `ManagerID` (String)
* `CreatedBy` (String)

### Content Type / Attachments

* Offer Letter (PDF)
* ID Proofs (PAN/Aadhaar)
* Bank Form (PDF)
* Other attachments

### Access Control / Security

* `HR` group: Full access on onboarding folder
* `Managers`: Read access to relevant folders
* `IT` group: Read access to documents necessary for provisioning
* Use CE ACLs and object store-level roles

### Event Action / Subscription

Create a CE subscription on the `EmployeeOnboardingDoc` class (or on creation in the onboarding folder) with *Event Action* to call a custom handler that starts the PE process.

* **Trigger:** `OnCreate` of `EmployeeOnboardingDoc`
* **Action:** Start PE workflow `Employee_Onboarding_Process`
* **Action data passed:** `EmployeeID`, `DocumentID (GUID)`, `EmployeeName`, `Email`, `ManagerID`, `JoiningDate`

Sample (pseudo) architecture: CE Event Action (Java) -> Call PE start process REST / JWS API or use VWSession API.

---

## 3. Process Engine (PE) — High level

**Process name:** `Employee_Onboarding_Process`

**Primary Data Fields (PE WorkObject fields):**

* `EmployeeID` (String)
* `DocumentGUID` (String)
* `EmployeeName` (String)
* `ManagerID` (String)
* `Email` (String)
* `Status` (String)
* `BackgroundCheckRequired` (Boolean)
* `BackgroundCheckResult` (String)
* `ITProvisionComplete` (Boolean)
* `HRVerificationComplete` (Boolean)
* `StartDate` (Datetime)
* `Deadline_Overall` (Datetime)

**Queues and Rosters**

* Component Queue: `HRQueue` (for HR verification)
* Component Queue: `ManagerQueue` (for Manager approval)
* Component Queue: `ITQueue` (for IT provisioning tasks)
* Component Queue: `SecurityQueue` (if physical access card needed)
* Roster: `HR_Roster`, `Manager_Roster`, `IT_Roster`

**Submaps**

* `BackgroundCheck_Submap` — handles background checks (external integration, timers, retries)
* `AssetProvision_Submap` — optional for asset procurement

**Milestones**

* `M1: Documents Verified` — when HR verification done
* `M2: Manager Approved` — when manager approves
* `M3: IT Provisioned` — when IT done
* `M4: Completed` — final completion

---

## 4. Detailed Process Map (Step-by-step)

### Start

* **Auto-start** by CE Event Action. The CE event calls the PE start API passing key fields.
* Initialize `StartDate = now`, `Status = "In-Progress"`; set `Deadline_Overall = StartDate + 7 days` (SLA: 7 days).

### Step A — HR Verification (System Step -> Component Queue)

* **Type:** Component Queue workstep (human)
* **Queue:** `HRQueue`
* **Action:** HR opens task, reviews documents stored in CE via link (DocumentGUID). HR updates `HRVerificationComplete` (True/False) and enters comments.
* **Timer / Deadline:** 48 hours; if exceeded, escalate to `HR Manager` via email and reassign to `HRQueue_Escalation`.
* **Milestone:** Set `M1` when verified.

### Decision: Basic Docs OK?

* If `No`: `Status = Rejected` → Document metadata in CE updated (`Status = Rejected`) → process ends.
* If `Yes`: Continue to Manager Approval.

### Step B — Manager Approval (Human, Conditional)

* **Type:** Component Queue
* **Queue:** `ManagerQueue` (or roster of the Manager based on `ManagerID`)
* **Action:** Manager reviews, approves or rejects.
* **Timer / Deadline:** 72 hours; escalation to Manager's manager if overdue.
* **On Approve:** Continue. **On Reject:** set `Status = Rejected` and notify HR; process ends.
* **Milestone:** `M2` on approve.

### Parallel Routing (Fork)

After Manager approval, create a **parallel split**:

* Branch 1: `BackgroundCheck_Submap` (if `BackgroundCheckRequired=true`) — can be synchronous (wait for result) or asynchronous with callback.
* Branch 2: `IT Provisioning` — tasks for IT team.

Both branches must complete before finalizing.

#### Branch 1: BackgroundCheck_Submap

* **Submap steps:**

  1. Send candidate info to third-party background-check service (system step/integration).
  2. Wait for callback or poll API (system step with timer). Poll every 6 hours; total wait up to 72 hours.
  3. On result: set `BackgroundCheckResult = Passed/Failed`. If `Failed`, set `Status = Onboarding Failed` and notify HR/Manager.
* **Escalation:** If no response in 72 hours, escalate to `HR` to decide to continue or cancel.

#### Branch 2: IT Provisioning (Parallelizable inside Branch)

* **Parallel internal split:**

  * Create Email account (task for `ITQueue`) — component queue
  * Create Laptop/Asset request (system or asset management integration) — component queue or automate via Asset Mgmt API
  * Access Card / Security clearance (task for `SecurityQueue`)
* Each IT subtask has own timers (default 48 hours). If an asset procurement is required (back-ordered), create an `AssetProvision_Submap`.
* When all IT tasks complete, set `ITProvisionComplete = True` and `M3` milestone.

### Join (Synchronize)

* The main flow waits on both background-check and IT branches to finish. If any branch results in fatal failure (e.g., background check failed), the process moves to `Onboarding Failed` path.

### Step C — Finalize by HR (Human)

* **Queue:** `HRQueue`
* **Action:** HR verifies all completed tasks, ensures CE document metadata updated, changes `Status = Onboarding Completed`, moves contents to final folder `/HR/Employees/Employee_<EmployeeID>/` and attaches final onboarding checklist.
* **Timer:** 48 hours after join; escalate if overdue.
* **Milestone:** `M4` reached.

### End

* Update CE document metadata: `Status = Onboarding Completed`, `PEProcessInstanceID` saved, `CompletedDate = now`.
* Create an Audit record (CE or external logging).
* Send notifications to Employee, Manager, and IT summary via email.

---

## 5. Exception Handling, Malfunctions & Escalations

**Common malfunctions and handling:**

* **CE Event Action fails to start PE:** Log the error in CE; create a retry mechanism (exponential backoff). If retries fail, create an administrative ticket and set CE document `Status = "StartFailed"` and notify System Admin.
* **Human step timeout:** Configure timers with escalation steps that either reassign the workitem to a supervisor roster or auto-approve after manual review depending on policy.
* **Background-check timeout/no response:** Escalate to HR after 72 hours; allow HR to mark as `Proceed` with caution or `Cancel` onboarding.
* **IT asset backorder:** `AssetProvision_Submap` handles procurement, with milestone `AssetOrdered` and a long timer (e.g., 14 days) and alerting to HR/Manager.
* **Process abort by manager:** Allow Manager to cancel process with reason; update CE metadata and archive documents with reason.

**Logging & Auditing:**

* Each PE state change should write an audit entry (WorkObject history) and optionally update CE audit properties or a separate `OnboardingAudit` CE folder.

---

## 6. Integration Points & Code Snippets

### A. CE Event Action (Pseudo-Java) — start PE via REST

```java
// Pseudo-code: CE Event Action handler
String docGuid = document.get_Id().toString();
String empId = document.get_Property("EmployeeID").getStringValue();
Map<String,String> payload = new HashMap<>();
payload.put("EmployeeID", empId);
payload.put("DocumentGUID", docGuid);
payload.put("EmployeeName", document.get_Property("EmployeeName").getStringValue());

// call PE REST Start Process API
String peStartUrl = "https://pe.server.example.com/peapi/process/start/Employee_Onboarding_Process";
HttpResponse resp = HttpClient.post(peStartUrl, payloadJson);
if(resp.status != 200) {
  // retry logic or log and create ticket
}
```

> Note: In older FileNet Runtime environments you may use VWSession API to start a process directly from Java.

### B. Example PE Start via REST (JSON body)

```json
{
  "processName": "Employee_Onboarding_Process",
  "fields": {
    "EmployeeID": "12345",
    "DocumentGUID": "{GUID}",
    "EmployeeName": "Vineeth Kumar",
    "ManagerID": "mgr_987",
    "Email": "vineeth@example.com"
  }
}
```

### C. PE Step: Access CE Document

* Provide CE document link in the PE workitem UI using a URL like: `https://ce.server.example.com/servlet/RepositoryDownload?docid={GUID}` or integrate via Content Engine APIs in a custom GUI.

---

## 7. Security Considerations

* Use HTTPS for all communications between CE and PE and external background-check services.
* Ensure least privilege: only allow users to access documents they are authorized to.
* Mask or encrypt sensitive fields (e.g., bank details) where required.
* Audit all accesses to documents and workflow decisions.

---

## 8. Testing Plan

* **Unit tests** for Event Action code (simulate CE document creation).
* **Integration tests**: CE -> PE start, PE -> CE metadata updates.
* **Happy path end-to-end**: create doc, approve, parallel branches, finalize.
* **Failure scenarios**: background-check fail, manager rejects, timers & escalations fire.
* **Load test**: open many onboarding processes simultaneously to validate queue throughput.

---

## 9. Deployment & Operational Notes

* Deploy CE Event Action handler on CE app server cluster; ensure same version across the cluster.
* Configure PE process designer artifacts (maps, submaps) in Process Designer and export to PE server.
* Keep a test/staging environment mirroring production object stores and integration endpoints.
* Setup monitoring alerts for failed starts, long-running processes, or repeated escalations.

---

## 10. Variations & Enhancements

* **Auto-approval rules:** if candidate is internal transfer, skip background check submap.
* **RPA integration:** use RPA bots for repetitive IT provisioning tasks.
* **Mobile UI:** lightweight mobile UI for managers to approve with minimal fields.
* **Reporting:** CE-based reports for onboarding time, bottlenecks, SLA breaches.

---

## 11. Appendix — Quick Reference

**Key names**

* CE class: `EmployeeOnboardingDoc`
* CE object store: `HR_ObjectStore`
* PE process: `Employee_Onboarding_Process`
* Queues: `HRQueue`, `ManagerQueue`, `ITQueue`, `SecurityQueue`
* Submaps: `BackgroundCheck_Submap`, `AssetProvision_Submap`
* Milestones: `M1: Documents Verified`, `M2: Manager Approved`, `M3: IT Provisioned`, `M4: Completed`

---

*If you want, I can now generate:*

* A BPMN-style diagram (ASCII or mermaid) of the PE map, or
* Exportable Process Designer XML template (pseudo), or
* Java sample for CE Event Action and PE REST start call with full error handling.
