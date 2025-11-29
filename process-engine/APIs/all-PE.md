# FileNet Process Engine Components

## 🟦 VWSession

### What is VWSession?

VWSession represents a connection to the FileNet Process Engine (PE). It's used to start working with queues, rosters, logs, and workflow items.

### Why We Use VWSession?

* Establish a session with PE
* Authenticate user access
* Fetch queues, rosters, and logs

### Real-Time Example

```java
VWSession session = VWSession.getSession("peurl", "username", "password");
```

This session is then used to fetch queues, rosters, or step elements.

---

## 🟦 VWRoster

### What is VWRoster?

VWRoster represents a collection of workflow items (work objects) assigned to a role or group.

### Why We Use VWRoster?

* Fetch all work items for a role or group
* Inspect, filter, or iterate items

### Example Scenario

#### Loan Approval Workflow

Fields: `F_LoanID`, `F_CustomerName`, `F_LoanAmount`, `F_Status`, `F_SubmissionDate`

```java
VWRoster roster = session.getRoster("ManagerRole");
VWRosterQuery query = roster.createQuery(
    null,                     // No projection
    null,                     // No sort
    "F_LoanAmount > 500000",// Filter
    new Object[]{},           // No substitution vars
    VWFetchType.FETCH_TYPE_WORKOBJECT
);

VWRosterElement element;
while ((element = query.next()) != null) {
    System.out.println(element.getStringValue("F_LoanID"));
    System.out.println(element.getStringValue("F_CustomerName"));
}
```

---

## 🟦 VWQueue

### What is VWQueue?

VWQueue represents a queue in FileNet PE where workflow items wait to be processed.

### Why We Use VWQueue?

* Fetch items in a workflow step
* Read, filter, and count queue items
* Dispatch items or get queue definition

### Real-Time Example

```java
VWQueue queue = session.getQueue("Manager_Approval_Queue");
int pending = queue.fetchCount();
System.out.println("Pending Approvals: " + pending);

VWQueueQuery query = queue.createQuery(
    null,
    "F_LoanAmount DESC",
    "F_LoanAmount > 700000",
    VWFetchType.FETCH_TYPE_QUEUE_ELEMENTS,
    null
);

VWQueueElement element;
while ((element = query.next()) != null) {
    System.out.println(element.getStringValue("F_LoanID"));
    System.out.println(element.getStringValue("F_LoanAmount"));
}
```

---

## 🟦 VWLog

### What is VWLog?

VWLog represents the logging of workflow activities, such as actions, transitions, or system events.

### Why We Use VWLog?

* Audit workflow activities
* Track who performed what action
* Debug workflow issues

### Real-Time Example

```java
VWLog log = session.getLog("LoanApprovalLog");
VWLogQuery logQuery = log.createQuery(
    "F_LoanID = 'L12345'",
    VWFetchType.FETCH_TYPE_LOG_ELEMENT
);

VWLogElement logElement;
while ((logElement = logQuery.next()) != null) {
    System.out.println(logElement.getStringValue("F_Action"));
    System.out.println(logElement.getStringValue("F_User"));
}
```

---

## 🟦 VWStepElement

### What is VWStepElement?

VWStepElement represents a **single task or activity** in a workflow step.

### When We Use It?

* Inspect a specific step in a workflow
* Get properties of the step (fields, status, assigned users)
* Perform operations on the step (complete, update)

### What It Returns?

* Step Name / Step ID
* Work item fields (`F_LoanID`, `F_CustomerName`, `F_LoanAmount`, `F_Status`, `F_SubmissionDate`)
* Assigned users or roles
* Step status (Pending, Completed)

### Real-Time Example

```java
VWStepElement stepElement = queue.getStepElement(0);
System.out.println("Step Name: " + stepElement.getStepName());
System.out.println("Loan ID: " + stepElement.getStringValue("F_LoanID"));
System.out.println("Customer Name: " + stepElement.getStringValue("F_CustomerName"));
System.out.println("Loan Amount: " + stepElement.getIntegerValue("F_LoanAmount"));
System.out.println("Status: " + stepElement.getStringValue("F_Status"));
```

Output:

```
Step Name: ManagerApproval
Loan ID: L12345
Customer Name: John Doe
Loan Amount: 750000
Status: Pending
```

---

## 🟦 Summary

* **VWSession:** Connect to FileNet PE
* **VWRoster:** Fetch all workflow items for a role/group
* **VWQueue:** Fetch items waiting in a workflow step
* **VWLog:** Track workflow actions and events
* **VWStepElement:** Inspect a single task/activity in a workflow step

These classes together help manage, track, and operate workflows efficiently in FileNet.
