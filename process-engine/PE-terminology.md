# 🧩 FileNet PE Terminology 

## 🔁 Workflow Definition
- A **workflow definition** is like a **blueprint or model** of a business process.  
- It defines **how work should move** from one step to another.  
- Created using **Process Designer**.  
- Includes steps, participants, rules, and conditions.  

🧠 **Example:**  
In a Loan Approval workflow definition:  
- Step 1: Verify documents  
- Step 2: Check credit score  
- Step 3: Approve or reject loan  

---

## ⚙️ Workflow
- A **workflow** is a **running instance** of a workflow definition.  
- It’s the **actual execution** of the process.  
- Each time a process starts, a new workflow instance is created.  

🧠 **Example:**  
Each customer’s loan application triggers **one workflow**.

---

## 📋 Work Item
- A **work item** is a **task assigned** to a user or role in the workflow.  
- Users act on work items (like approving or reviewing something).  
- Once a user completes it, the work item moves to the next step in the workflow.  

🧠 **Example:**  
A “Loan Officer” receives a **work item** to “Verify Applicant Documents”.

---

## 📥 Queue
- A **queue** is a **holding area** for work items.  
- It groups work items for users or roles.  
- Users pick work items from their queue to work on.  

🧠 **Example:**  
All “Loan Officers” may share a **Loan Verification Queue** where work items wait.

---

## 📄 Roster
- A **roster** stores **information about workflow instances**.  
- Think of it as a **database table** containing all workflows (active and completed).  
- Used for **searching, tracking, and reporting** workflow data.  

🧠 **Example:**  
A “Loan Process Roster” keeps a record of every loan application workflow — who handled it, its status, etc.

---

## 🧾 Event Log
- An **event log** records **everything that happens** in the Process Engine.  
- Includes events like workflow started, step completed, item routed, errors, etc.  
- Helps in **auditing and troubleshooting**.  

🧠 **Example:**  
If a workflow fails, you can check the **event log** to see what went wrong.

---

## ⚡ Events
- **Events** are the **actions or changes** that occur in the workflow.  
- Triggered automatically (like “Workflow Started”) or manually (like “Step Completed”).  
- Can be used to start another workflow or send notifications.  

🧠 **Example:**  
When a loan is approved, an **event** triggers another workflow to send an email to the customer.

---

## 🧠 Summary Table

| Term | Meaning | Example |
|------|----------|----------|
| **Workflow Definition** | Blueprint/model of process | Loan approval process steps |
| **Workflow** | Running instance of a definition | A single loan request being processed |
| **Work Item** | Task for a user | “Verify documents” task |
| **Queue** | Holds work items | “Loan Officer Queue” |
| **Roster** | Stores workflow instances | “Loan Process Roster” |
| **Event Log** | Records system actions | Workflow start, errors, etc. |
| **Event** | Action or trigger | Loan approved → send email |



# 🔄 Difference Between Workflow Instance and Work Item in FileNet PE

## 🧩 Workflow Instance
- A **Workflow Instance** is a **running copy** of a workflow definition.  
- It represents the **entire process** from start to finish.  
- It includes all steps, decisions, and transitions defined in the workflow model.  
- Each time a process starts, a **new workflow instance** is created.  

🧠 **Example:**  
When a loan application is submitted, a **Loan Approval Workflow Instance** starts — it will go through steps like verification, approval, and notification.

---

## 📋 Work Item
- A **Work Item** is a **single task** or **unit of work** inside a workflow instance.  
- It is assigned to a **user or role** for action (like approve, review, verify, etc.).  
- When a user completes the task, the workflow moves to the next step.  
- Multiple work items can exist within a single workflow instance.  

🧠 **Example:**  
In the same Loan Approval Workflow Instance:  
- One **work item** is for the loan officer to **verify documents**.  
- Another **work item** is for the manager to **approve or reject** the loan.

---

## 🧠 Key Difference Table

| Feature | **Workflow Instance** | **Work Item** |
|----------|------------------------|----------------|
| **Definition** | The complete running process | A specific task within that process |
| **Scope** | Represents the whole workflow | Represents one step or assignment |
| **Created When** | A process starts | A user task becomes active |
| **Handled By** | System (managed automatically) | User or role |
| **Contains** | Many steps and work items | Only one task/action |
| **Example** | Loan Approval Process | Verify Documents task |

---

## 🧩 In Simple Words:
- A **workflow instance** = the **entire journey**.  
- A **work item** = one **stop or task** along that journey.

🧠 **Analogy:**  
Think of a **workflow instance** as a train journey from one city to another.  
Each **work item** is a **station** where something specific happens before the train moves on.
