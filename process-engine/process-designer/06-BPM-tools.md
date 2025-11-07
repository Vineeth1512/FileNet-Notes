# 📘 FileNet BPM Tools Overview

In FileNet BPM (Business Process Management), three main tools are used to design, manage, and monitor workflows:

- **Process Designer**
- **Process Administrator**
- **Process Tracker**

---

## ⚙️ 1. Process Designer

### 🧠 What it is:
**Process Designer** is the tool used to **create and model workflows** (called *processes*) in FileNet BPM.

### 🎯 Purpose:
It allows you to **design the step-by-step flow of work** — who does what, in what order, and under what conditions.

### 🧩 Key Features:
- Create **process maps** using palettes (Activities, Timers, Submaps, etc.)
- Define **participants** (users, roles, queues)
- Add **business rules** and **routing logic**
- Integrate with **external systems** (like web services, databases)
- Test or **simulate workflows** before deployment

### 💡 Example:
For a *Loan Approval Process*:
1. Receive Application  
2. Verify Documents  
3. Approve or Reject Loan  
4. Notify Customer  

All these steps are modeled inside the Process Designer.

---

## 🛠️ 2. Process Administrator

### 🧠 What it is:
**Process Administrator** is a **web-based management console** used to **deploy, manage, and troubleshoot** workflows.

### 🎯 Purpose:
It’s mainly used by **administrators** to handle workflow configurations, runtime settings, and user management.

### 🧩 Key Features:
- Deploy or **import process definitions**
- **Start, stop, or restart** workflow instances
- Manage **rosters**, **queues**, and **work items**
- Set **security permissions**
- **Troubleshoot** failed or stuck workflows
- Monitor **system performance**

### 💡 Example:
If a workflow instance is stuck at “Document Verification,” the administrator can:
- Check its status  
- Reassign the task  
- Restart or terminate the instance  

---

## 👀 3. Process Tracker

### 🧠 What it is:
**Process Tracker** is a tool used to **monitor and track live or completed workflow instances**.

### 🎯 Purpose:
It helps **business users or managers** see how processes are running in real time.

### 🧩 Key Features:
- View **running and completed** workflows
- Check **which step** a process is currently in
- View **history and audit trails**
- Measure **processing time** per step
- Identify **bottlenecks** or delays

### 💡 Example:
A manager can use Process Tracker to see:
- How many loan applications are “Approval Pending”
- Who is handling them
- How long each step is taking

---

## 🧾 Summary Table

| Tool | Used By | Main Purpose | Key Features |
|------|----------|---------------|----------------|
| **Process Designer** | Workflow Developers | Create and design workflows | Create process maps, define logic, simulate |
| **Process Administrator** | System/Admins | Manage and troubleshoot processes | Deploy, control instances, manage users |
| **Process Tracker** | Business Users/Managers | Monitor workflow progress | Track live/completed processes, analyze performance |

---

✅ **In short:**
- **Process Designer** → Used to *create* workflows  
- **Process Administrator** → Used to *manage* workflows  
- **Process Tracker** → Used to *monitor* workflows
