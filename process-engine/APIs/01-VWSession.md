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

If you want, I can add:
✔ Real-time use cases
✔ More code samples
✔ Interview questions
✔ Practice assignments

---

## 🧩 **Code for All VWSession & VWStepElement Operations**

Below are complete Java examples demonstrating how to use every major operation.

---

# 🟦 **VWSession — Full Operations Code**

## **1️⃣ Login to PE (VWSession logon)**

```java
VWSession session = new VWSession();
session.setBootstrapCEURI("http://localhost:9080/wsi/FNCEWS40MTOM/");
session.logon("p8admin", "password", "FileNetP8WSI", "pe_connection_point");
System.out.println("Logged in as: " + session.getUserName());
```

## **2️⃣ Fetch Queue**

```java
VWQueue queue = session.getQueue("Inbox");
System.out.println("Queue Name: " + queue.getQueueName());
```

## **3️⃣ Fetch Roster & Search Workflows**

```java
VWRoster roster = session.getRoster("LoanRoster");
VWQuery query = roster.createQuery(null, null, null, null, null, VWFetchType.FETCH_TYPE_STEP_ELEMENT);
VWRosterElement element;

while ((element = (VWRosterElement) query.next()) != null) {
    System.out.println("Workflow ID: " + element.getWorkflowNumber());
}
```

## **4️⃣ Fetch Work Item from Queue**

```java
VWQueueQuery q = queue.createQuery(null, null, null, null, null, VWFetchType.FETCH_TYPE_STEP_ELEMENT);
VWStepElement step;

while ((step = (VWStepElement) q.next()) != null) {
    System.out.println("Step Name: " + step.getStepName());
}
```

## **5️⃣ Launch a Workflow**

```java
VWProcess process = session.createProcess("LoanApprovalWorkflow");
VWParameter param = process.createParameter("LoanAmount", VWFieldType.INTEGER, 50000);
process.launch();
System.out.println("Workflow started.");
```

---

# 🟩 **VWStepElement — Full Operations Code**

## **1️⃣ Read Step Details**

```java
System.out.println("Step Name: " + step.getStepName());
System.out.println("Deadline: " + step.getDeadline());
System.out.println("Received Time: " + step.getReceivedTime());
```

## **2️⃣ Lock & Unlock Step**

```java
step.doLock();
System.out.println("Step locked.");

// Unlock later
step.unlock();
System.out.println("Step unlocked.");
```

## **3️⃣ Read Parameters / Data Fields**

```java
String customerName = (String) step.getParameterValue("CustomerName");
Integer loanAmount = (Integer) step.getParameterValue("LoanAmount");
System.out.println("Customer: " + customerName + " | Amount: " + loanAmount);
```

## **4️⃣ Update Parameter Values**

```java
step.doLock();
step.setParameterValue("ApprovalStatus", "APPROVED");
step.doSave(true);
```

## **5️⃣ Access & Update Workflow Data Fields**

```java
VWDataField[] fields = step.getDataFields();
for (VWDataField f : fields) {
    System.out.println(f.getName() + " = " + f.getValue());
}

step.setDataFieldValue("DecisionBy", "Manager1");
```

## **6️⃣ Save the Step (Without Completing)**

```java
step.doSave(true);
System.out.println("Step saved");
```

## **7️⃣ Complete (Dispatch) Step**

```java
step.doDispatch();
System.out.println("Step completed and routed");
```

## **8️⃣ Reassign Step**

```java
step.reassignToUser("supervisor1");
System.out.println("Reassigned to supervisor1");
```

## **9️⃣ Get Participants Assigned to Step**

```java
VWParticipant[] participants = step.getParticipants();
for (VWParticipant p : participants) {
    System.out.println("Participant: " + p.getParticipantName());
}
```

## **🔟 Access Work Object & Attachments**

```java
System.out.println("Work Object Number: " + step.getWorkObjectNumber());
VWWorkObject wo = step.getWorkObject();
System.out.println("Fields: " + Arrays.toString(wo.getFieldNames()));
```

---

## 🎯 **Everything Above Now Added to This Markdown File**
