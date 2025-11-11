## 🏦 Example: Loan Approval — Full Detailed Flow

### 🎯 Business Goal

A customer applies for a loan. The system verifies documents, performs a credit check automatically, and then either routes the request to a manager for approval or rejects it automatically.

**High-level steps:**

1. Customer submits application
2. Document verification (human)
3. Credit check (system)
4. Manager approval (human)
5. Notify customer

We’ll go through: **Design → Validate → Transfer → Launch/Test → Runtime (PE) → Admin/Tracker.**

---

## 1️⃣ Process Designer — Design the Workflow

### 🧩 What You Do in the Tool

1. Open **Process Designer**.
2. Create a new process model called **LoanApprovalProcess**.
3. Add activities/nodes:

   * **Start** (start activity)
   * **CollectDocuments** (human activity — Document Verifier)
   * **CreditCheck** (system activity — calls external credit API)
   * **Decision** (decision block: credit OK? yes/no)
   * **ManagerApproval** (human activity — Manager roster)
   * **NotifyCustomer** (system activity — send email)
   * **End** (end activity)
4. Define properties for each activity:

   * `CollectDocuments` → participant = `DocumentVerifier`
   * `CreditCheck` → map input `applicantId`, configure adapter `CreditCheckAdapter`
   * `ManagerApproval` → participant = `LoanManagers`
5. Add process variables: `applicationId`, `applicantName`, `creditScore`, `status`
6. Save your model.

### ⚙️ What This Creates

* A **workflow definition** in your Process Designer workspace (a .pep file or internal artifact)
* Mappings of participants, queues, and external adapters

---

## 2️⃣ Validate (in Process Designer)

### 🧰 What You Do

* Click **Validate**
* Fix any warnings (missing participants, routes, or data issues)

### 🧠 Why

* Prevent runtime errors like missing mappings or broken transitions

### 🔍 Behind the Scenes

* Process Designer checks paths, variables, and participant mappings

---

## 3️⃣ Transfer (from Process Designer to PE)

### 🧰 What You Do

* Click **Transfer to Process Engine**
* Select the **target Object Store / Isolated Region**

### ⚙️ What Happens Internally

* Workflow definition serialized into a deployable artifact
* Sent to **Process Engine’s metadata store**
* Registered as a **Workflow Definition** in PE

### 🧾 What PE Stores

| Item                | Description                                |
| ------------------- | ------------------------------------------ |
| Workflow Definition | Name: LoanApprovalProcess, version, schema |
| Participants        | DocumentVerifier, LoanManagers             |
| Queues / Rosters    | VerificationQueue, ManagerRoster           |
| External Links      | CreditCheckAdapter, NotificationAdapter    |

✅ **After Transfer:** You can see the workflow in **Process Administrator → Process Definitions**

---

## 4️⃣ Launch (Test Run) in Process Designer

### 🧰 What You Do

* Click **Launch / Test**
* Enter sample values for variables (e.g. applicantName, creditScore)

### ⚙️ What Happens

* Process Designer requests PE to start a workflow instance
* PE creates a **Workflow Instance**
* First **Work Item** assigned to the **DocumentVerifier Queue**

✅ **Purpose:** Quick test to confirm assignments, adapter calls, and transitions

---

## 5️⃣ Process Administrator — Manage Deployed Process

### 🧰 What You Do

1. Open **Process Administrator**
2. Go to **Process Definitions → LoanApprovalProcess**
3. Actions:

   * View process version
   * Map participants to real users or LDAP groups
   * Configure queues and rosters
   * Activate/deactivate the process

### ⚙️ Behind the Scenes

* Updates PE metadata (assigns roles, queues, permissions)

💡 **Note:** In most cases, *Transfer* already deploys the process. PA lets you configure and monitor it.

---

## 6️⃣ Start a Real Instance (Runtime)

### 🔹 How It Starts

* A customer submits a form → backend calls PE API to start the process
* OR admin manually starts from PA

### ⚙️ What PE Does

* Creates **Workflow Instance (Loan-Instance-1001)**
* Initializes process variables
* Creates first **Work Item** for `CollectDocuments`

---

## 7️⃣ Runtime Behavior — Step-by-Step Flow

### Step A — Document Verification (Human)

* PE creates **Work Item** in `VerificationQueue`
* Document Verifier completes task → PE marks done
* State updates to `DocumentVerified`

### Step B — Credit Check (System)

* PE runs **CreditCheckAdapter**
* Calls external credit API → gets creditScore
* Sets process variable `creditScore`
* Evaluates decision: if `creditScore >= 650` → Manager Approval, else Reject

### Step C — Manager Approval (Human)

* PE creates **Work Item** in `ManagerRoster`
* Manager approves/rejects
* Updates `status` variable

### Step D — Notify Customer (System)

* PE triggers **NotificationAdapter** → sends email/SMS
* Workflow instance marked as **Completed**

---

## 8️⃣ Process Tracker — Monitor Workflow

### 🧰 What You Do

* Open **Tracker** from Process Administrator → select *Open in Tracker*

### 👀 What You See

| View              | Description               |
| ----------------- | ------------------------- |
| Activity Timeline | Who did what, timestamps  |
| Data Tab          | Current process variables |
| Path History      | Which decision path taken |
| Error Events      | Any adapter/system errors |

✅ **Use Case:** Check if work is stuck or adapters failed

---

## 9️⃣ PE Internal Records & Storage

| Storage        | What It Contains                                  |
| -------------- | ------------------------------------------------- |
| PE Database    | Workflow definitions, instances, work items, logs |
| Content Engine | Application documents (PDFs, images)              |
| Event Logs     | Actions like WorkItemAssigned, Completed, Errors  |
| Adapters       | Logs of external API calls (credit, email)        |

---

## 🔟 Common Problems & Fixes

| Problem                   | Cause                           | Fix                                  |
| ------------------------- | ------------------------------- | ------------------------------------ |
| Process not visible in PA | Transfer failed                 | Check transfer logs, isolated region |
| Work item not in inbox    | Missing participant mapping     | Map user roles correctly             |
| Adapter fails             | Not registered / external error | Check adapter config, logs           |
| Workflow stuck            | Routing issue or error          | Check Tracker → Event Logs           |

---

## ✅ Practical Checklist

1. Design process in **Process Designer**
2. Validate (fix all errors)
3. Transfer to **PE** (confirm logs)
4. Verify in **Process Administrator**
5. Map users/roles & queues
6. Launch test instance
7. Monitor instance in **Tracker**
8. Check event logs for failures
9. After testing → release for production

---

## 🧠 Summary Flow

```text
Process Designer → Validate → Transfer → Process Administrator → Process Engine → Process Tracker
```

| Stage         | Tool                  | What Happens             |
| ------------- | --------------------- | ------------------------ |
| Design        | Process Designer      | Build workflow visually  |
| Validate      | Process Designer      | Fix configuration issues |
| Transfer      | Process Designer      | Send to PE server        |
| Deploy/Config | Process Administrator | Activate, assign users   |
| Run           | Process Engine        | Executes automatically   |
| Track         | Process Tracker       | Monitor progress         |

---

💡 **In simple words:**

> You build and test in **Process Designer**, move to PE through **Transfer**, configure and monitor in **Process Administrator**, and track everything live in **Process Tracker**.



---

Example: Loan Approval — full detailed flow Business goal: A customer applies for a loan. The system verifies documents, performs a credit check automatically, and then either routes the request to a manager for approval or rejects it automatically. High-level steps: Customer submits application Document verification (human) Credit check (system) Manager approval (human) Notify customer We’ll go through: Design → Validate → Transfer → Launch/Test → Runtime (PE) → Admin/Tracker. 1) Process Designer — design the workflow (what you do) What you do in the tool Open Process Designer. Create a new process model called LoanApprovalProcess. Add nodes/activities: Start (start activity) CollectDocuments (human activity — Document Verifier) CreditCheck (system activity — calls external credit API) Decision (decision block: credit OK? yes/no) ManagerApproval (human activity — Manager roster) NotifyCustomer (system activity — send email) End (end activity) Define properties for each activity: For CollectDocuments: participant = role DocumentVerifier For CreditCheck: map input applicantId, configure adapter component name CreditCheckAdapter For ManagerApproval: participant = roster LoanManagers Add data attributes (process variables): applicationId, applicantName, creditScore, status Save your model. What this creates/updates A workflow definition (metadata object) in Process Designer workspace — often stored as a .pep or internal model artifact. Local mapping of participants, queues, and references to external adapters (by name). 2) Validate (in Process Designer) What you do Click Validate (often a menu or toolbar button). Fix any warnings/errors (missing participant mapping, broken transitions, uninitialized variables). Why Prevent runtime errors (missing participants cause assignment failures; wrong data mapping causes exceptions). What happens behind the scenes Process Designer performs a static check of the model: ensures every path ends in End, required data mappings exist, participant names are valid format, components referenced are registered names. 3) Transfer (from Process Designer to PE) — the important step What you do Click Transfer (or “Transfer to PE”, sometimes “Send to Server”). Fill connection info if required: select target Object Store / Isolated Region (PE runtime area). What Transfer actually does Connects to the Process Engine server / repository. Serializes the workflow definition into a deployable artifact (e.g., .pep) and sends it to the PE’s database (or the configured isolated region). The Process Engine registers the new process definition in its metadata store. Often, transfer automatically activates (deploys) the process — making it available to be instantiated. What PE stores A Workflow Definition record: name LoanApprovalProcess, version, property schema (attributes), participants/roles mapping references, adapter component reference names. Metadata linking to Content Engine object store if documents are involved (e.g., application documents stored in CE and referenced by documentId attribute). Configuration of default queues / rosters used by the process (if provided on transfer). What to check Transfer log in Process Designer (shows success/failure). On success you should see the process listed in Process Administrator → Process Definitions. If transfer fails: check connectivity, credentials, that the isolated region exists, and the adapter/component registrations referenced are available. 4) Launch (test run) in Process Designer (optional) What you do In Process Designer, click Launch (or Test) to create a test instance. Provide test values for applicationId, applicantName, etc. What happens Process Designer asks PE to create a workflow instance using the definition you just transferred. PE creates a Workflow Instance record (a running copy) and starts executing steps. First activity (CollectDocuments) is a human task — a Work Item is created and placed into the configured Queue / assigned to the roster or inbox of DocumentVerifier. Why do this Quick functional test to confirm assignment, adapter calls, transitions, and that the tracker shows expected behavior. 5) Process Administrator — view/manage deployed process (what you do here) Open Process Administrator Go to Process Administrator dashboard (web app). Locate LoanApprovalProcess under Process Definitions or Applications. Possible actions in PA View definition: confirm version, last transfer time. Set or update participants/permissions: map real users or LDAP groups to participants if not already set. Configure queues and rosters if needed (create VerificationQueue, ManagerRoster). Activate / deactivate the process (in some setups you can enable/disable a process). View system-level settings: event logging, router/process engine node mappings, isolated region health. Do you deploy here? In many environments transfer already deployed the process. PA is where you would manually import/deploy if transfer didn’t do it. In your case (you transfer from Designer), PA will show the process as available. What happens behind the scenes when you do config in PA PA updates PE metadata: assigns real user IDs to participant names, creates or points to queues/rosters, updates security/access control. 6) Start a real instance (how it starts in runtime) How a new instance is created Option A: A user fills a front-end form and a backend service calls PE API to start LoanApprovalProcess, providing applicationId and applicant info. Option B: An admin or a scheduler starts the process instance from Process Administrator or another interface. What PE does when starting Creates a Workflow Instance record (unique id, e.g. Loan-Instance-1001). Instantiates process variables (applicationId, etc.) with passed values. Creates initial Work Item(s) for first activity. Persists the instance state in the PE database. Where data is stored PE database: workflow instance metadata, activities statuses, pointers to work items, audit trail. If documents are part of the process, Content Engine stores the binary/document objects and the workflow stores references (IDs/URIs). 7) Runtime behavior — how work moves (detailed) Let’s follow one instance step-by-step. Step A — Document Verification (human activity) PE created a Work Item for CollectDocuments. The work item is placed in VerificationQueue or assigned to the inbox of user(s) in DocumentVerifier role. Any of those users picks the task in their Inbox (via user interface). When user completes the verification form, the Work Item is completed — PE marks the activity done and evaluates the next step. PE actions Update workflow instance state to DocumentVerified. Persist action in Event Logs: e.g., WorkItemAssigned, WorkItemCompleted. Step B — Credit Check (system) PE executes the CreditCheck activity. It calls the registered adapter CreditCheckAdapter with applicationId. Adapter performs an HTTP call to external Credit Bureau API and returns creditScore. The creditScore is saved into the workflow instance variable. PE evaluates the decision condition: creditScore >= 650 ? yes : no. If success Move to ManagerApproval or Notify (depending on condition). If adapter call fails PE logs an error, retries according to adapter retry configuration (or routes to an error queue / human operator). Step C — Manager Approval (human) If creditScore is good, create a Work Item in ManagerRoster. Manager picks task, approves or rejects. On approve: set status = Approved and move to NotifyCustomer. On reject: set status = Rejected and move to NotifyCustomer. Step D — Notify Customer (system) PE calls NotificationAdapter to send email/SMS with status. After notification, mark workflow instance Completed and log completion event. 8) Process Tracker — monitoring and troubleshooting Open Tracker From Process Administrator or directly open Tracker UI. Search for your instance Loan-Instance-1001 (by applicationId or instance ID). You will see a visual map of the process showing each activity node and where the instance currently is or that it’s completed. What Tracker shows Activity timeline: who did what and timestamps. Data view: current values of applicationId, creditScore, status. Path history: which decision path the instance took (approve/reject). Error events: adapter failures, timeout info. Common troubleshooting actions If task is stuck: check Queue — is the work item waiting with no assigned user? Check roster assignment. If adapter failed: check event log for exception, check adapter logs (outside PE), retry or rerun the activity. If instance has inconsistent data: check variables in the Tracker -> Data tab. 9) PE internal records and logs (what gets stored where) PE Database Workflow definitions (versioned) Workflow instances (state, variables, creation times) Work items (assigned, completed timestamps) Event logs & exception records Content Engine (if documents used) Document objects (PDFs, images) Links between documents and workflow instance by documentId Adapter / External Systems CreditCheckAdapter logs (API call logs) NotificationAdapter logs (email delivery status) Admin Consoles Process Administrator shows process definitions, queues, routers Tracker shows instance lifecycle and data 10) Edge cases & what to do if something goes wrong Problem: After Transfer, you don’t see process in Process Administrator. Check: Transfer log in Designer for errors. Check: Isolated region exists and you’re connected to correct Object Store. Check: user/credentials used to connect have permission to create workflows. Problem: Work item never appears in user inbox. Check participant mapping: did you map DocumentVerifier to a real user or roster? Check queue assignments: Is the Work Item routed to the correct queue? Check PE event logs for errors while creating the work item. Problem: Adapter (CreditCheck) fails. Check adapter registration: was CreditCheckAdapter registered in PE (PCC or component registry)? Check external API health and credentials. Look at PE retry policy — may auto-retry or raise error to an operator. Problem: Tracker shows instance stuck between two nodes. Check event logs for exceptions. Use Process Administrator to look at instance status and possibly restart/resume or reassign tasks. 11) Practical checklist you can follow next time Design process in Process Designer (name clearly, version control). Validate in Designer — fix warnings/errors. Transfer to PE — confirm transfer logs show success. In Process Administrator, confirm process appears in Definitions. Map participants/rosters and configure queues if necessary.
