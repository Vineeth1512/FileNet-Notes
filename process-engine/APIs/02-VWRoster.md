# IBM FileNet Process Engine – VWRoster & VWRosterQuery (Full Notes)

---

## #️⃣ 1. VWRoster

### ✅ What is VWRoster?

`VWRoster` is a Process Engine object that stores information about **workflow instances** (running or completed).

**It acts like a table that stores all workflow instances inside the Process Engine.**

### ✔ Why We Use VWRoster

- List all workflows that are running  
- Search workflow instances  
- Check workflow status  
- Troubleshoot workflow issues  
- Audit completed workflows  
- Monitor workflow progress  

### ✔ Difference Between Queue & Roster

- **Queue** = Work items assigned to users  
- **Roster** = All workflow instances (not user tasks)

---

## #️⃣ 2. Important Methods in VWRoster

| Method | Purpose |
|--------|---------|
| `createQuery()` | Search workflows |
| `fetchCount()` | Get count of results |
| `getName()` | Returns roster name |
| `getFieldNames()` | Returns all roster fields |

### ✔ Example: Load Roster

```java
VWRoster roster = session.getRoster("DefaultRoster");
System.out.println("Roster Loaded: " + roster.getName());
```

Sure! Here is your content exactly in Markdown file format, clean and ready to save as a .md file.
(You can copy–paste directly into a file named: VWRoster_VWRosterQuery.md)
```


---

# IBM FileNet Process Engine – VWRoster & VWRosterQuery (Full Notes)

---

## #️⃣ 1. VWRoster

### ✅ What is VWRoster?

`VWRoster` is a Process Engine object that stores information about **workflow instances** (running or completed).

**It acts like a table that stores all workflow instances inside the Process Engine.**

### ✔ Why We Use VWRoster

- List all workflows that are running  
- Search workflow instances  
- Check workflow status  
- Troubleshoot workflow issues  
- Audit completed workflows  
- Monitor workflow progress  

### ✔ Difference Between Queue & Roster

- **Queue** = Work items assigned to users  
- **Roster** = All workflow instances (not user tasks)

---

## #️⃣ 2. Important Methods in VWRoster

| Method | Purpose |
|--------|---------|
| `createQuery()` | Search workflows |
| `fetchCount()` | Get count of results |
| `getName()` | Returns roster name |
| `getFieldNames()` | Returns all roster fields |

### ✔ Example: Load Roster

```java
VWRoster roster = session.getRoster("DefaultRoster");
System.out.println("Roster Loaded: " + roster.getName());


---

#️⃣ 3. VWRosterQuery

✅ What is VWRosterQuery?

VWRosterQuery is used to search/filter workflow instances stored inside a roster.

It is similar to SQL SELECT query for Process Engine workflows.

✔ Why We Use VWRosterQuery

Search workflows by name

Search workflows by data fields

Monitor workflow status

Debug workflow errors

Find stuck workflows

Build admin dashboards



---

#️⃣ 4. Important Methods in VWRosterQuery

Method	Purpose

hasNext()	Checks if next record exists
next()	Returns next workflow row
getFieldValue()	Read roster field value
reset()	Restart query
fetchBuffer()	Internal caching of results



---

#️⃣ 5. Fields Available in Roster Query Results

Field	Meaning

F_WobNum	Workflow instance ID
F_WorkFlowName	Workflow template name
F_LaunchDate	Workflow start time
F_Status	Workflow status code
Custom fields	Example: StudentName, Amount



---

#️⃣ 6. Java Code Examples

✔ Example 1: Get All Workflows of a Specific Template

VWRoster roster = session.getRoster("DefaultRoster");

String[] fieldNames = {"F_WobNum", "F_WorkFlowName", "StudentName"};
String filter = "F_WorkFlowName = 'StudentApproval'";

VWRosterQuery query = roster.createQuery(fieldNames, filter, null, null, 0);

while (query.hasNext()) {
    VWWorkObject wo = (VWWorkObject) query.next();

    System.out.println("WobNum: " + wo.getFieldValue("F_WobNum"));
    System.out.println("Workflow Name: " + wo.getFieldValue("F_WorkFlowName"));
    System.out.println("Student Name: " + wo.getFieldValue("StudentName"));
}


---

✔ Example 2: Search Workflows by Data Field

String filter = "StudentID = 101";

VWRosterQuery query = roster.createQuery(null, filter, null, null, 0);

while (query.hasNext()) {
    VWWorkObject wo = (VWWorkObject) query.next();
    System.out.println("Workflow Number: " + wo.getWobNum());
}


---

✔ Example 3: Search In-Progress Workflows

String filter = "F_Status = 3";  // In-progress

VWRosterQuery query = roster.createQuery(null, filter, null, null, 0);

while (query.hasNext()) {
    VWWorkObject wo = (VWWorkObject) query.next();
    System.out.println("WobNum: " + wo.getWobNum());
}


---

#️⃣ 7. Queue vs Roster (Simple Comparison)

Feature	Queue (VWQueue)	Roster (VWRoster)

Stores	Work items / tasks	Workflow instances
Used by	End users	Admins / Developers
Purpose	Complete steps	Search / audit workflows
Scope	Current step	Entire workflow instance
Example	ApproveRequest	StudentApproval workflow



---

#️⃣ 8. Real-Time Business Example

A company uses workflow EmployeeLeaveApproval.
HR wants to:

Find all pending leave requests

Search requests by EmployeeID

Track workflows launched today

Identify failed or stuck workflows


These actions are done using:

➡ VWRoster + VWRosterQuery


---

#️⃣ 9. Summary

Concept	Description

VWRoster	Stores workflow instances
VWRosterQuery	Searches workflow instances
VWWorkObject	One row of workflow data
Filter String	Works like SQL WHERE condition



---

---

If you want, I can convert this into a **downloadable .md file** also.  
Just tell me **"give download file"**.
