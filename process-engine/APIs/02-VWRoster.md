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
# 🏗️ IBM FileNet Process Engine --- VWRoster

## 📌 What is VWRoster?

**VWRoster** is a Process Engine API class that represents a **roster
table** in FileNet.

A **roster** is a **database table** that stores **all in-progress and
completed workflow instances** for a workflow definition.

> **Think of Roster as:**\
> 📘 *Workflow History* + 🔄 *In-Progress Work Items*

------------------------------------------------------------------------

## 🎯 Why We Use VWRoster

We use VWRoster to:

-   ✔ Query workflow instances\
-   ✔ Fetch workflow metadata\
-   ✔ Apply filters and search conditions\
-   ✔ Retrieve workflows using custom fields\
-   ✔ Track workflow progress\
-   ✔ Generate admin and support reports\
-   ✔ Build dashboard analytics

------------------------------------------------------------------------

## 🔥 Real-Time Use Cases

### 1️⃣ Loan Approval Workflow

Bank wants to know:

-   All loan applications between specific dates\
-   Only "Rejected" applications\
-   All applications created by an agent\
-   Workflows where **CreditScore \< 600**

All achieved using **VWRoster queries**.

------------------------------------------------------------------------

### 2️⃣ HR Onboarding Workflow

HR wants:

-   All onboarding workflows for the last 60 days\
-   All workflows stuck in *Background Verification*\
-   All completed workflows

Again → **VWRoster**.

------------------------------------------------------------------------

### 3️⃣ BPM Analytics Dashboard

Dashboard items using VWRoster:

-   Total workflows created today\
-   Pending workflows\
-   SLA violations\
-   Work items per user

------------------------------------------------------------------------

# 🧩 Important Methods in VWRoster

### ⭐ 1. `fetchCount()`

Returns count of workflow instances in the roster.\
**Use case:** Show *"Total workflows"* in dashboard.

------------------------------------------------------------------------

### ⭐ 2. `fetchRosterDefinition()`

Fetches roster metadata:

-   Field names\
-   Types\
-   Indexes

Useful when building dynamic search UIs.

------------------------------------------------------------------------

### ⭐ 3. `getName()`

Returns *display* name of the roster.

------------------------------------------------------------------------

### ⭐ 4. `getAuthoredName()`

Returns original name from Process Designer.

------------------------------------------------------------------------

### ⭐ 5. `setBufferSize(int size)`

Controls number of records fetched per batch.\
Used for **pagination** and **performance tuning**.

------------------------------------------------------------------------

### ⭐ 6. `createQuery()` --- MOST IMPORTANT

Used to query the roster with:

-   Index fields\
-   Date ranges\
-   Custom filters\
-   Substitution variables\
-   Query flags

------------------------------------------------------------------------

# 🎯 Important Query Flags

  ---------------------------------------------------------------------------------------------------
  Flag                                      Meaning               Real-Time Use
  ----------------------------------------- --------------------- -----------------------------------
  `QUERY_NO_OPTIONS (0)`                    Default query         Fetch writable work items

  `QUERY_READ_UNWRITABLE (4)`               Read-only items       History reports

  `QUERY_MIN_VALUES_INCLUSIVE (32)`         Include min value     `>= startDate`

  `QUERY_MAX_VALUES_INCLUSIVE (64)`         Include max value     `<= endDate`

  `QUERY_GET_NO_SYSTEM_FIELDS (1024)`       Skip system fields    Faster performance

  `QUERY_RESOLVE_NAMES (8192)`              Resolve usernames to  Filtering by user
                                            IDs                   

  `QUERY_SORT_DESCENDING_ENABLED (16384)`   Descending sort       Latest first
  ---------------------------------------------------------------------------------------------------

------------------------------------------------------------------------

# 🧨 Real-Time VWRoster Query Examples

## ▶️ Example 1: Fetch workflows between date ranges

``` java
VWRoster roster = session.getRoster("LoanRoster");

Object[] first = { startDate };
Object[] last  = { endDate };

VWRosterQuery query = roster.createQuery(
    "F_CreateDate",
    first,
    last,
    VWRoster.QUERY_MIN_VALUES_INCLUSIVE | VWRoster.QUERY_MAX_VALUES_INCLUSIVE,
    null,
    null,
    VWFetchType.FETCH_TYPE_STEP_ELEMENT
);
```

------------------------------------------------------------------------

## ▶️ Example 2: LoanAmount \> 500000

``` java
String filter = "LoanAmount > :AMOUNT";
Object[] vars = { new Integer(500000) };

VWRosterQuery query = roster.createQuery(
    "LoanAmountIndex",
    null,
    null,
    VWRoster.QUERY_NO_OPTIONS,
    filter,
    vars,
    VWFetchType.FETCH_TYPE_STEP_ELEMENT
);
```

------------------------------------------------------------------------

## ▶️ Example 3: Get workflows for a specific user

``` java
String filter = "InitiatedBy = :USER";
Object[] vars = { "john.doe" };

VWRosterQuery query = roster.createQuery(
    "InitiatedByIndex",
    null,
    null,
    VWRoster.QUERY_RESOLVE_NAMES,
    filter,
    vars,
    VWFetchType.FETCH_TYPE_STEP_ELEMENT
);
```

------------------------------------------------------------------------

## ▶️ Example 4: Sort workflows descending

``` java
VWRosterQuery query = roster.createQuery(
    "F_CreateDate",
    firstValues,
    lastValues,
    VWRoster.QUERY_SORT_DESCENDING_ENABLED,
    null,
    null,
    VWFetchType.FETCH_TYPE_WORKOBJECT
);
```

------------------------------------------------------------------------

# 🎤 Interview Cross Questions

### ❓ 1. What is a roster in FileNet?

A table that stores **completed + in-progress** workflow instances.

------------------------------------------------------------------------

### ❓ 2. Difference Between Queue and Roster

  -----------------------------------------------------------------------
  Queue                             Roster
  --------------------------------- -------------------------------------
  Holds work items waiting for user Stores all workflow instances
  action                            

  Belongs to workflow steps         One roster per workflow definition

  Used at runtime                   Used for reporting and admin queries
  -----------------------------------------------------------------------

------------------------------------------------------------------------

### ❓ 3. When to use `QUERY_READ_UNWRITABLE`?

-   When retrieving **completed** workflows\
-   For **audit/history** reports

------------------------------------------------------------------------

### ❓ 4. What happens when system fields are skipped?

-   System fields return **null**\
-   Performance improves

------------------------------------------------------------------------

### ❓ 5. How to filter using custom workflow fields?

Using:

    filter + substitutionVars

------------------------------------------------------------------------

### ❓ 6. When to use `QUERY_RESOLVE_NAMES`?

When filtering workflows by **username** --- system converts it to
**user ID**.

------------------------------------------------------------------------
