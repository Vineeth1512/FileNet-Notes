

# 🟦 **VWRosterElement**

---

# 🟩 **1. What is VWRosterElement?**

`VWRosterElement` represents a **single row** in a **Roster table**.

* Unlike `VWWorkObject` (which represents the full workflow work item with runtime capabilities),
  `VWRosterElement` is **read-only** and is primarily used for **reporting, querying, and listing workflow instances**.

* Each `VWRosterElement` corresponds to **one workflow instance** and contains:

  * Workflow Number (WobNum)
  * Step Name
  * Field values (custom workflow fields)
  * Launch date, Completion date
  * Workflow status (Completed, In-Progress)
  * Assigned user (optional)

👉 **In simple words:** Think of it as a **row in the workflow history or in-progress table**. You can read data but cannot perform workflow operations like dispatch or reassign.

---

# 🟦 **2. Why use VWRosterElement?**

`VWRosterElement` is ideal for:

* Generating reports (completed workflows, SLA violations)
* Listing workflows in dashboards
* Searching/filtering workflows efficiently
* Fetching metadata without locking the work item
* High-performance queries on large rosters

**Example Real-Time Uses:**

1. Banking: List all rejected loans in last 30 days.
2. HR: Show all onboarding workflows currently pending.
3. BPM Dashboard: Count workflows per user/step.

---

# 🟦 **3. How to get a VWRosterElement?**

VWRosterElement is typically fetched using `VWRosterQuery`:

```java
VWRoster roster = session.getRoster("LoanRoster");

VWRosterQuery query = roster.createQuery(
    "F_CreateDate",
    firstValues,
    lastValues,
    VWRoster.QUERY_MIN_VALUES_INCLUSIVE | VWRoster.QUERY_MAX_VALUES_INCLUSIVE,
    null,
    null,
    VWFetchType.FETCH_TYPE_ROSTER_ELEMENT
);

while (query.next()) {
    VWRosterElement element = query.getRosterElement();
    System.out.println("WobNum: " + element.getWorkObjectNumber());
    System.out.println("Loan Amount: " + element.getFieldValue("F_LoanAmount"));
}
```

> Notice the fetch type `VWFetchType.FETCH_TYPE_ROSTER_ELEMENT`.

---

# 🟩 **4. Important Methods of VWRosterElement**

| Method                            | Purpose                                           |
| --------------------------------- | ------------------------------------------------- |
| `getWorkObjectNumber()`           | Returns WobNum                                    |
| `getFieldValue(String fieldName)` | Get value of a workflow field                     |
| `getRosterName()`                 | Name of the roster this element belongs to        |
| `getStepName()`                   | Current step name                                 |
| `getStatus()`                     | Returns workflow status (Completed / In-Progress) |
| `getLaunchDate()`                 | Workflow launch date                              |
| `getCompletionDate()`             | Workflow completed date (if applicable)           |
| `getCreator()`                    | Workflow initiator                                |
| `getQueueName()`                  | Queue at which work was last waiting              |

> Unlike `VWWorkObject`, there are **no methods to modify, dispatch, or lock** a VWRosterElement.

---

# 🟦 **5. Real-Time Scenarios Using VWRosterElement**

---

### ⭐ Scenario 1 — Loan Approval Report

```java
VWRosterQuery query = roster.createQuery(
    "F_CreateDate",
    new Object[] { startDate },
    new Object[] { endDate },
    VWRoster.QUERY_MIN_VALUES_INCLUSIVE | VWRoster.QUERY_MAX_VALUES_INCLUSIVE,
    "F_Status = :A",
    new Object[] { "Rejected" },
    VWFetchType.FETCH_TYPE_ROSTER_ELEMENT
);

while (query.next()) {
    VWRosterElement element = query.getRosterElement();
    System.out.println("Loan WobNum: " + element.getWorkObjectNumber());
    System.out.println("Loan Amount: " + element.getFieldValue("F_LoanAmount"));
}
```

---

### ⭐ Scenario 2 — HR Onboarding Dashboard

Fetch all workflows stuck in “Background Verification”:

```java
String filter = "F_StepName = :A";
Object[] vars = { "BackgroundVerification" };

VWRosterQuery query = roster.createQuery(
    "F_StepNameIndex",
    null,
    null,
    VWRoster.QUERY_NO_OPTIONS,
    filter,
    vars,
    VWFetchType.FETCH_TYPE_ROSTER_ELEMENT
);
```

---

### ⭐ Scenario 3 — BPM Analytics

* Count workflows per step or per user
* Generate SLA reports
* Export data to external systems

```java
while(query.next()) {
    VWRosterElement element = query.getRosterElement();
    System.out.println("Step: " + element.getStepName() + ", Status: " + element.getStatus());
}
```

---

# 🟦 **6. Differences: VWWorkObject vs VWRosterElement**

| Feature          | VWWorkObject          | VWRosterElement           |
| ---------------- | --------------------- | ------------------------- |
| Read/Write       | Yes                   | Read-only                 |
| Dispatch / Route | Yes                   | No                        |
| Lock/Unlock      | Yes                   | No                        |
| Attachments      | Yes                   | No                        |
| Use Case         | Processing work items | Reporting / dashboards    |
| Fetch Type       | FETCH_TYPE_WORKOBJECT | FETCH_TYPE_ROSTER_ELEMENT |

---

# 🟩 **7. Interview Cross Questions**

* When to use VWRosterElement instead of VWWorkObject?
* Can you update fields in a VWRosterElement?
* Why use FETCH_TYPE_ROSTER_ELEMENT for large dashboards?
* How do you get workflow creator info?
* Difference between RosterElement and WorkObject in terms of performance?

