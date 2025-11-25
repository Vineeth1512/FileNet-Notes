# Queue vs Roster in IBM FileNet Process Engine 

## 🟦 1. What is a Queue?
A **Queue** is like a **box that stores work items** which users or the system must process.

### ✔ Simple Meaning
- A queue **holds active work items**.
- Users open the queue to see work assigned to them.
- Workflow steps send work items into a queue.

### ✔ Example
A **"Verification Step"** creates a work item and places it in a queue called `StudentVerificationQueue`.

Users may see:
- Student 1 verification  
- Student 2 verification  
- Student 3 verification  

👉 **Queues are for processing work NOW.**

---

## 🟦 2. What is a Roster?
A **Roster** is like a **history database** for workflow instances.

### ✔ Simple Meaning
- A roster **stores all workflow instances** (running, completed, terminated).
- It stores **workflow metadata**, not work items.
- It is used for **tracking**, **audit**, and **searching workflows**.

### ✔ Example
When a workflow finishes, the workflow instance is stored in `StudentWorkflowRoster`.

You may see:
- Student 1 workflow – Completed  
- Student 2 workflow – In Progress  
- Student 3 workflow – Completed  

👉 **Rosters are for tracking and history.**

---

## 🟩 3. Main Difference (Very Simple)

| Feature | **Queue** | **Roster** |
|--------|-----------|------------|
| Purpose | To **process active work items** | To **store workflow instances** |
| Contains | Work items | Workflow metadata (history + active) |
| Used by | Users during work | Admin/Developers for tracking |
| Represents | Current step | Entire workflow instance |
| Example | “Verification work item” | “Student workflow instance record” |

---

## 🟧 4. Super Simple Explanation

- **Queue = Inbox**  
  Like your email inbox → New work arrives.

- **Roster = Full email history**  
  Inbox + Sent + Archived → everything stored.

---

## 🟨 5. Real-time Example: Leave Approval Workflow

1. Employee requests leave  
   → Workflow instance created → Stored in **LeaveWorkflowRoster**

2. Work item goes to Manager Approval  
   → Stored in **ManagerApprovalQueue**

3. Manager approves  
   → Work item moves to HR Queue  
   → Same workflow instance in roster updated

4. Workflow completes  
   → Roster keeps the full history  
   → Queues become empty for that item

---
