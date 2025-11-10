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
