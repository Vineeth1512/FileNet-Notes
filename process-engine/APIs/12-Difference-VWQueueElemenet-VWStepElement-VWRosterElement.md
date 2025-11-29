

# 🟥 **VWQueueElement vs VWStepElement vs VWRosterElement**

**(Simple → Clear → Real-time examples)**

---

# 🟦 **1. VWStepElement — What it is?**

### ✔ Meaning

A **VWStepElement** represents **one step assigned to a user or system**.
It is the **actual work item** that someone needs to perform.

### ✔ When it is used?

You use VWStepElement when:

* A user opens a task
* A user completes a task
* A system step runs automatically

### ✔ What it contains?

It contains **step-related data**:

* Step name
* Workflow fields
* Roster name
* Work item number
* Instructions
* Step parameters
* Route information (Next step options)

### ✔ Real-time example

Loan approval workflow:

* “**Document Verification**” — Human work item
* “**Manager Approval**” — Human work item
* “**Auto Credit Score Check**” — System work item

Each of these is a **VWStepElement**.

---

# 🟦 **2. VWQueueElement — What it is?**

### ✔ Meaning

A **VWQueueElement** is the **representation of a work item inside a Queue**.

Think of this as the **object you get when you list items from a Queue**.

### ✔ When it is used?

Use VWQueueElement when:

* You fetch items from a queue
* You filter queue items (by fields, status, steps)
* You move items from queue to step
* You check how many items are pending

### ✔ What it contains?

It contains **queue-level summary info**:

* Item ID
* Roster name
* Workflow name
* Step name (current)
* Queue fields

But it is **not yet the full step** — it is only the **lightweight record**.

To work on the item, you must convert:

👉 **VWQueueElement → VWStepElement**
Using:

```java
VWStepElement step = queueElement.fetchStepElement();
```

### ✔ Real-time example

Manager Queue has:

* 10 items for approval
  Each item appears as a **VWQueueElement**.

When the manager **opens** an item → it becomes **VWStepElement**.

---

# 🟦 **3. VWRosterElement — What it is?**

### ✔ Meaning

A **VWRosterElement** is the **representation of a workflow instance inside a Roster**.

Roster = **history/registry of all workflow instances**.

A RosterElement is **one workflow instance record**.

### ✔ When it is used?

Use VWRosterElement when:

* You search workflow instances
* You check workflow status
* You view all completed workflows
* You find failed workflows
* You track workflow history

### ✔ What it contains?

It contains **workflow instance-level data**:

* Workflow number
* Launch time
* Current step
* Status (Running, Completed, Failed, Terminated)
* Parent workflow
* System fields
* Roster fields

### ✔ Real-time example

Loan workflow instances:

* Application 101 → Completed
* Application 102 → Running (At Manager Approval)
* Application 103 → Failed

These three records are **VWRosterElement**.

You cannot perform a step on these.
These are **workflow-level entries**, not task-level.

---

# 🟩 **Super Simple Comparison**

### 🟥 **VWStepElement**

👉 Actual task being worked on
👉 Full details of the step
👉 Required to complete a step

### 🟧 **VWQueueElement**

👉 Item waiting in a Queue
👉 Lightweight version
👉 Need to convert to VWStepElement to work

### 🟩 **VWRosterElement**

👉 Workflow instance info (history/status)
👉 Used for tracking, reporting
👉 Not used for task completion

---

# 🟦 **Real-time Story Example (Easy to Understand)**

Loan approval workflow:

| Stage                                  | FileNet Object                         | What it means                 |
| -------------------------------------- | -------------------------------------- | ----------------------------- |
| Workflow starts                        | **VWRosterElement**                    | New workflow instance created |
| Work item goes to "Verification Queue" | **VWQueueElement**                     | Visible in queue for officers |
| Officer opens the item                 | **VWStepElement**                      | Actual task performed         |
| Task completed → next step             | Again **VWQueueElement** in next queue | Moves automatically           |
| Workflow ends                          | **VWRosterElement updated**            | Status = Completed            |

---
