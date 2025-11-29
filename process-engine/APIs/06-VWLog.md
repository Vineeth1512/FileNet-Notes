# VWLog in FileNet Process Engine

---

## 🔹 What is VWLog?

`VWLog` represents **Workflow logs** in FileNet Process Engine.

* A **log** is a record of actions, events, or messages associated with a workflow or a work item.
* Think of a log as:

  * 📝 **Diary of a work item** showing all its activities
  * 📊 **Audit trail** for tracking workflow execution

---

## 1️⃣ Why We Use VWLog?

We use `VWLog` to:
- ✔ Track work item history
- ✔ Debug workflow issues
- ✔ Audit approvals, rejections, or any action on a workflow item
- ✔ Fetch system-generated or user-generated log messages

---

## 2️⃣ Real-Time Workflow Scenario with 5 Fields

**Workflow Scenario:** **Loan Approval Workflow**

**Fields used in workflow:**

1. `LoanID` – Unique loan number
2. `CustomerName` – Applicant name
3. `LoanAmount` – Amount requested
4. `DocumentStatus` – Status: PENDING / VERIFIED
5. `ApprovalStatus` – Status: PENDING / APPROVED / REJECTED

**Scenario:** Manager approves a loan → Log stores the action

* Log records:

  * Who approved it
  * When it was approved
  * Previous status → new status
  * Any comments

---

## 3️⃣ How to Get VWLog

```java
VWLog log = workObject.getLog(); // VWWorkObject has logs
```

* You first fetch the work item (VWWorkObject), then get its log.

---

## 4️⃣ Important Methods in VWLog & Examples

### 1. getMessages()

```java
VWLogEntry[] entries = log.getMessages();
for (VWLogEntry entry : entries) {
    System.out.println("Message: " + entry.getMessageText());
    System.out.println("User: " + entry.getUserName());
    System.out.println("Time: " + entry.getTime());
}
```

* ✅ Retrieves all messages in the log for a workflow item

---

### 2. addMessage()

```java
log.addMessage("Loan Approved by Manager", VWLogEntry.LOG_MESSAGE_TYPE_USER);
log.save();
```

* ✅ Add a custom message to the log
* `LOG_MESSAGE_TYPE_USER` → User message
* `LOG_MESSAGE_TYPE_SYSTEM` → System-generated message

---

### 3. Access Individual Log Details

```java
VWLogEntry entry = entries[0];
System.out.println("Time: " + entry.getTime());
System.out.println("User: " + entry.getUserName());
System.out.println("Message: " + entry.getMessageText());
```

---

### 4. Filtering Logs

```java
for (VWLogEntry entry : log.getMessages()) {
    if(entry.getUserName().equals("Manager")) {
        System.out.println("Manager Action: " + entry.getMessageText());
    }
}
```

* ✅ Filter log messages by user or condition

---

## 5️⃣ Real-Time Examples Using 5 Fields

### Example 1: Manager Loan Approval Log

```java
VWWorkObject workObject = session.getWorkObject("LoanID_12345");
VWLog log = workObject.getLog();
log.addMessage("Approved Loan Amount: 800000", VWLogEntry.LOG_MESSAGE_TYPE_USER);
log.save();
```

* ✅ Records the manager’s approval action

### Example 2: Document Verification Log

```java
VWWorkObject workObject = session.getWorkObject("LoanID_12345");
VWLog log = workObject.getLog();
for (VWLogEntry entry : log.getMessages()) {
    System.out.println(entry.getTime() + " | " + entry.getUserName() + " | " + entry.getMessageText());
}
```

* ✅ Lists all document verification actions

---

## 6️⃣ Summary Table

| Concept        | Explanation                                                             |
| -------------- | ----------------------------------------------------------------------- |
| VWLog          | Stores workflow messages and events                                     |
| Why Use        | Track workflow history, debug issues, audit actions                     |
| Methods        | getMessages(), addMessage(), getTime(), getUserName(), getMessageText() |
| Real-Time Use  | Loan approval, document verification, HR onboarding logs                |
| Fields Example | LoanID, CustomerName, LoanAmount, DocumentStatus, ApprovalStatus        |

---

✅ **VWLog** is mainly for **tracking, auditing, and debugging workflow items**.

* `VWQueue` = Where items **wait**
* `VWLog` = Where items **history** is stored
