
# 🟥 **What is a Work Item in FileNet Process Engine?**

A **Work Item** is an **individual piece of work** that belongs to a workflow step and is waiting for a user or system to process it.

👉 **Work Item = one task assigned to someone at a particular step.**

It is represented in FileNet code as:

* **VWStepElement** (work item at a step)
* **VWWorkObject** (overall workflow item)

---

# 🟦 **Simple Explanation**

When a workflow is running, it moves step by step.

At each step, something must happen:

* A user must approve
* A system must execute
* A document must be verified

The unit of work that sits at that step is called a **work item**.

💡 **If nothing is done yet at a step, the work item waits in a queue.**

---

# 🟩 **Real-Time Example (Very Simple)**

### 🏦 Loan Approval Workflow

Steps:

1. Document Verification → by employee
2. Credit Check → system
3. Manager Approval → manager

When customer **Rajesh** applies for a loan:

* Workflow starts
* At step 1 → **A work item is created**
* It appears in employee queue → "Verify Rajesh’s documents"
* Employee opens work item, verifies, completes → next step

At step 2 → **new work item**
At step 3 → **another work item**

👉 For every step, the workflow creates a WORK ITEM.

---

# 🟧 **Analogy**

Imagine an order in a restaurant kitchen.

* Order #101 = workflow instance
* Each cooking stage (cutting, frying, plating) = step
* The order ticket at each stage = **work item**

---

# 🟨 **Technical View**

A Work Item contains:

* Workflow Fields (customerName, amount, etc.)
* Step information
* Queue name
* Assigned user/role
* Deadlines
* Status (claimed, unclaimed, locked, completed)

---

# 🟪 **Code Perspective (Very Simple)**

```
VWQueue queue = session.getQueue("VerifyDocsQueue");
VWStepElement stepElement = (VWStepElement) queue.next();
```

`stepElement` = **Work Item**

---

# 🟫 **Final 1-Line Definition**

✔️ **A Work Item is a single, actionable task at a specific step in a workflow, waiting in a queue until it is processed.**

---
