# IBM FileNet Process Engine APIs — VWSession & VWStepElement

## 🟦 1. VWSession

### ✅ What is VWSession?

`VWSession` represents the **connection** between your application and the FileNet Process Engine. It is the **entry point** for all PE API operations.

### 🎯 Purpose

* Authenticate (log in to PE)
* Connect to queues
* Connect to rosters
* Launch workflows
* Perform workflow operations

### 🟩 Why We Use It

| Task                  | Requires VWSession? |
| --------------------- | ------------------- |
| Logging in            | ✔                   |
| Fetching Queues       | ✔                   |
| Fetching Rosters      | ✔                   |
| Launching Workflows   | ✔                   |
| Getting configuration | ✔                   |

### 🟧 Important Methods

* **setBootstrapCEURI(url)** → Defines CE connection URL
* **logon(username, password)** → Logs into PE
* **getQueue(name)** → Fetch queue
* **getRoster(name)** → Fetch roster
* **createProcess(workflowName)** → Start workflow instance
* **logoff()** → Close session
* **getUserName()** → Retrieve logged-in user
* **getSessionString()** → Session ID

### 🟫 Example

```java
VWSession session = new VWSession();
session.setBootstrapCEURI("http://localhost:9080/wsi/FNCEWS40MTOM");
session.logon("admin", "password");

VWQueue queue = session.getQueue("ManagerApprovalQueue");
VWRoster roster = session.getRoster("LoanRoster");

session.logoff();
```

---

## 🟦 2. VWStepElement

### ⭐ What is VWStepElement?

`VWStepElement` represents a **single step** in the workflow after fetching a work item.

Each workflow activity (step) becomes a `VWStepElement` during execution.

### 🎯 Purpose

To **view and manipulate** workflow step properties:

* Data fields
* Parameters
* Step name
* Participants
* Complete the step
* Lock/unlock

### 🟧 Why We Use It

| Operation              | Done Using VWStepElement? |
| ---------------------- | ------------------------- |
| Get step details       | ✔                         |
| Read/Write data fields | ✔                         |
| Approve/Reject         | ✔                         |
| Reassign               | ✔                         |
| Complete step          | ✔                         |

### 🟨 Important Methods

* **getStepName()** → Returns step name
* **getDataFields()** → Returns all step fields
* **getParameterValue(name)** → Read parameter
* **setParameterValue(name, value)** → Update parameter
* **doDispatch()** → Complete step
* **doLock()** → Lock the step
* **reassignToUser(userId)** → Assign step to another user
* **getLaunchTime()** → Step start time
* **getDeadline()** → Step deadline
* **getStepDescription()** → Instructions text

### 🟫 How to Get VWStepElement

```java
VWQueue queue = session.getQueue("ManagerApprovalQueue");
VWWorkItem wi = queue.fetchNextWorkItem();
VWStepElement step = wi.fetchStepElement();
```

### 🟥 Example: Approve a Work Item

```java
VWWorkItem wi = queue.fetchNextWorkItem();
VWStepElement step = wi.fetchStepElement();

System.out.println("Step: " + step.getStepName());

step.doLock();
step.setParameterValue("Status", "Approved");
step.doDispatch();
```

---

## 🟦 VWSession vs VWStepElement — Quick Comparison

| Feature      | VWSession              | VWStepElement                |
| ------------ | ---------------------- | ---------------------------- |
| Represents   | Connection             | Workflow Step                |
| Scope        | Global                 | Task-Level                   |
| Used For     | Login, Queues, Rosters | Approve/Reject, Step actions |
| Created When | App starts             | Work item is fetched         |

---

## 🟩 Architecture Diagram

```
Your Application (Java/Spring)
        |
    VWSession
        |
--------------------
| Process Engine |  → Workflow Steps
--------------------
        |
   VWStepElement
```

---

## 🟦 Summary

* **VWSession** → Like logging into FileNet PE and accessing queues/rosters.
* **VWStepElement** → Represents a step/task of workflow used to read/update fields and complete tasks.

---


