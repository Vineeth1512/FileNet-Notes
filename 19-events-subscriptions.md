# 🔔 FileNet – Events and Subscriptions

**Events and Subscriptions** in FileNet allow the system to **automatically perform actions** when certain activities occur in the Object Store.  
They are essential for **workflow automation, notifications, and auditing**.

---

## 🧑‍💻 Technical Definition
- **Event** → A specific occurrence or action on an object in the Object Store (e.g., document creation, modification, deletion).  
- **Subscription** → A configuration that **listens for events** and triggers an **action or workflow** automatically.  

**Key Components:**
1. **Event Action** – What happens when the event occurs (e.g., start workflow, send notification).  
2. **Event Subscription** – Links an **event** with its **action**.  
3. **Event Type** – The kind of action to monitor: creation, modification, deletion, check-in, check-out, etc.  

---

## 🗣️ Simple English Definition
- **Event** = Something happens to a document (like creation, check-in, or deletion).  
- **Subscription** = A rule saying “when this event happens, do this action automatically.”

---

## 🎯 Purpose
- Automate **document management processes**.  
- Notify users when important actions happen.  
- Trigger **workflows** without manual intervention.  
- Improve **efficiency** and reduce human error.

---

## 🔁 Why We Use Events and Subscriptions
- To automate tasks like **archival, approvals, or notifications**.  
- To integrate FileNet with **external systems**.  
- To maintain **audit trail** and enforce business rules.

---

## ⚙️ Types of Events
| Event Type | Description |
|------------|-------------|
| Document Creation | Triggered when a new document is created |
| Document Modification | Triggered when document metadata or content changes |
| Check-in / Check-out | Triggered when a document is checked in or out |
| Deletion | Triggered when a document is deleted |
| Folder Events | Triggered when folder properties change or objects are added |

---

## ⚙️ How Subscriptions Work
1. Define an **Event Type** to monitor.  
2. Create an **Event Action** (e.g., start workflow, send email, update properties).  
3. Configure an **Event Subscription** linking the Event Type with the Event Action.  
4. When the event occurs, the system automatically executes the action.

---

## 💡 Real-Time Analogy
Think of **Events and Subscriptions** like **IFTTT (If This Then That)**:  
- **Event** = “A new document is uploaded to the folder”  
- **Subscription/Action** = “Send an email notification to manager”  

Automation happens without human intervention.

---

## 🌍 Real-World Scenario
- **HR Document Upload**:  
  - Event → Employee uploads a contract.  
  - Subscription → Automatically notify HR manager and start approval workflow.  

- **Invoice Processing**:  
  - Event → Invoice document is checked in.  
  - Subscription → Trigger workflow for accounting approval.  

- **Archival**:  
  - Event → Document becomes 5 years old.  
  - Subscription → Move document to archive folder automatically.

---

## ⚙️ Steps to Configure Events and Subscriptions in ACCE

1. Open **ACCE → Object Store → Event Management**.  
2. Click **Create Event Action** → Define what should happen.  
3. Click **Create Event Subscription** →  
   - Select **Event Type** (e.g., Document Creation).  
   - Select **Target Object or Class**.  
   - Link the **Event Action**.  
4. Save → System automatically triggers actions when events occur.

---

## 🗣️ How to Explain in Interview (Own Words)
> “Events and Subscriptions in FileNet automate actions when certain activities occur, like creating a document or checking in a file.  
> Subscriptions define which action should run automatically, such as starting a workflow or sending a notification.”

---

## 🧾 Key Points for Interview
- **Event** = Occurrence or action on an object.  
- **Subscription** = Rule linking event to action.  
- Can trigger workflows, notifications, property updates, or archival.  
- Helps automate business processes and improve efficiency.  
- Reduces human error and ensures timely execution of tasks.

---

## 🏁 Summary Table

| Component | Description |
|-----------|-------------|
| Event | Action or occurrence in Object Store |
| Event Type | Document creation, modification, deletion, check-in, check-out |
| Event Action | What happens when event occurs (workflow, notification, update) |
| Subscription | Links Event Type with Event Action |
| Purpose | Automate processes, trigger workflows, notify users |
