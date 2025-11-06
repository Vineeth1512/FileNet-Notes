# 🧭 Palettes in IBM FileNet Process Designer (BPM)
 
In **IBM FileNet Process Designer (BPM)**, palettes contain different types of **steps or components** that you drag into your workflow — and the main ones you’ll work with are:
 
➡️ **Activity**  
➡️ **System**  
➡️ **Submap**  
➡️ **Component** steps  
 
Let’s go through each one in simple words with examples 👇
 
---
 
## 🧩 1. Activity Step
 
### **Purpose:**
Used when a **human user** needs to do some work (manual task).
 
### **Who performs it:**
A person (like a clerk, manager, or approver).
 
### **What it does:**
- Sends a work item to a user’s inbox.  
- The user opens the item, does their part (e.g., approve or reject), and completes it.  
- After that, the process continues to the next step.
 
### **Example:**
💼 *Loan Approval Process* —  
An **Activity Step** called “Verify Applicant Documents” is done by a bank officer.
 
### **In short:**
- Manual work  
- Assigned to users or roles  
- Involves human decision  
 
---
 
## ⚙️ 2. System Step
 
### **Purpose:**
Used when the **system (server)** needs to perform an automatic task — no human action needed.
 
### **Who performs it:**
The **Process Engine** automatically.
 
### **What it does:**
- Runs background logic  
- Updates data fields  
- Connects with other systems  
- Sends automatic notifications  
 
### **Example:**
📧 *Send Email Confirmation* —  
After the loan is approved, the **System Step** automatically sends an email to the applicant.
 
### **In short:**
- Fully automated  
- Runs scripts, integrations, or updates  
- No user inbox  
 
---
 
## 🔁 3. Submap Step
 
### **Purpose:**
Used to **reuse another process (subprocess)** inside the current workflow.
 
### **Who performs it:**
Either human or system — depends on what’s inside the submap.
 
### **What it does:**
- Allows **modular workflow design**.  
- Instead of repeating common steps in every workflow, you can create one submap and reuse it.
 
### **Example:**
🧾 *Employee Onboarding* —  
Main workflow has a **Submap** called “Create Employee ID”.  
That submap contains smaller steps (HR system entry, ID generation, welcome email).
 
### **In short:**
- Reusable process inside another process  
- Keeps workflows clean and modular  
 
---
 
## 🧠 4. Component Step
 
### **Purpose:**
Used to call **external components** like Java classes, web services, or custom applications.
 
### **Who performs it:**
The **system (automatically).**
 
### **What it does:**
- Integrates with outside systems or code  
- Executes custom logic that’s not built into BPM  
- Can pass input/output parameters  
 
### **Example:**
🌐 *Credit Check Service* —  
A **Component Step** calls an external Java class or web service that checks the customer’s credit score.
 
### **In short:**
- Connects to external or custom code  
- Executes reusable service logic  
- Part of system automation  
 
---
 
## 💡 Quick Summary Table
 
| Step Type | Who Performs | Description | Example |
|------------|---------------|--------------|----------|
| **Activity** | Human | Manual task for a user | Verify loan documents |
| **System** | Process Engine | Automatic background task | Send email or update DB |
| **Submap** | Human/System | Reuse another process | Run common HR sub-process |
| **Component** | System | Call external code or service | Run credit score API |
 
---
 
## 🏁 Tip to Remember
 
> **Activity = Human**  
> **System = Automation**  
> **Submap = Reuse**  
> **Component = Integration**
