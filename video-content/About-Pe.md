# ⚙️ FileNet Process Engine (PE)

## 1️⃣ WHAT is Process Engine?
Process Engine is the **workflow engine** of FileNet.  
It manages **business processes**, assigns tasks, and moves work from one step to another.

You can call it:  
**“The traffic controller + workflow manager of FileNet.”**

It does not store documents — it **controls how work flows** between users and systems.

---

## 2️⃣ PURPOSE (Why we use Process Engine)

- To automate business processes  
- To route tasks to the correct user or group  
- To reduce manual work  
- To maintain process timelines and SLAs  
- To track each step of the process  
- To integrate multiple systems (Database, Web Services, CE, etc.)  

Companies use PE to ensure the work moves smoothly and nothing gets stuck or delayed.

---

## 3️⃣ HOW it works (Simple flow)

1. A workflow gets started (manual or automatic)  
2. PE creates a **work item**  
3. Work item moves step-by-step through the workflow  
4. Tasks are assigned to users or queues  
5. Users complete the tasks  
6. PE moves the work item to the next step  
7. Workflow ends after all steps are done  

Process Engine continuously tracks:  
- Who worked on what  
- When work was completed  
- Any delays or exceptions

---

## 📌 Real-Time Example  
### **Loan Approval Workflow**

1. A customer applies for a loan.  
2. PE starts a workflow automatically.  
3. First step: Document verification → assigned to verification team.  
4. Second step: Credit check → assigned to credit department.  
5. Third step: Manager approval.  
6. Final step: Generate approval/rejection letter.

At each stage, PE:  
- Sends tasks to the right team  
- Tracks time  
- Moves the loan file to the next step  
- Handles exceptions (missing documents, mismatches)

This ensures the loan process is **fast, traceable, and error-free**.

---

## 🟦 One-Line Summary
**Process Engine = The workflow brain that moves tasks step-by-step until the process is completed.**
