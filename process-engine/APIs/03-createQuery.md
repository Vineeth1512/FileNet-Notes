Here is your complete content converted into a **clean, attractive Markdown file format** — ready to copy/paste OR download (just tell me to export as `.md`).

---

# 🟦 VWRoster.createQuery() — Full Detailed Explanation

### *(All Parameters + Real-Time Scenarios)*

This is the most powerful and advanced search method in IBM FileNet Process Engine.

It allows high-performance, index-based, range-based, and filter-based queries on a **Roster**.

---

## 🔵 Method Signature

```java
public VWRosterQuery createQuery(
    String indexName,
    Object[] firstValues,
    Object[] lastValues,
    int queryFlags,
    String filter,
    Object[] substitutionVars,
    int fetchType
) throws VWException
```

You iterate the results using:

```java
query.next();
```

---

# 🟩 SECTION 1 — Simple Explanation

`createQuery()` works like performing an **SQL query** on a Roster.

It supports:

✔️ Search via Index
✔️ Range filtering (min → max)
✔️ Sorting
✔️ WHERE-like filter expressions
✔️ Parameter substitution
✔️ Fetching either WorkObjects or RosterElements

---

# 🟦 SECTION 2 — Parameter-by-Parameter Explanation

---

## 1️⃣ **indexName — Which Search Index to Use**

A **search index** is a predefined combination of fields used for optimized queries.

### Examples:

* `"F_WobNum"` → Workflow Number
* `"F_WobTag"` → Tag
* `"F_LoanAmount"` → Custom Field
* `"MyCustomIndex"` → Created in PCC

### **Why Important?**

✔️ Makes searches **10x faster**
✔️ Allows ascending/descending sorting
✔️ Supports range-based search

### **Real-Time Example (Bank Loan Dashboard)**

Use custom index:

```txt
LoanTypeAmountIndex
```

---

## 2️⃣ **firstValues — Lower range (minimum values)**

Used to set:

* Minimum Loan Amount
* Minimum Date
* Minimum Workflow Number
* Minimum String Alphabet

### Example:

```java
Object[] firstValues = { "HomeLoan", 500000 };
```

Meaning:
Start from `"HomeLoan"` AND minimum amount `5 Lakhs`.

---

## 3️⃣ **lastValues — Upper range (maximum values)**

### Example:

```java
Object[] lastValues = { "HomeLoan", 2000000 };
```

Meaning:
End at `"HomeLoan"` AND max amount `20 Lakhs`.

---

## 🟦 Combined Range Meaning

| firstValues | lastValues | Meaning                  |
| ----------- | ---------- | ------------------------ |
| 5L          | 20L        | Loans between 5–20 Lakhs |
| Jan 1       | Jan 31     | Items created in January |
| A           | M          | Names starting from A–M  |

### **Real-Time Scenario**

Fetch all Home Loan applications between 5L–20L:

```java
indexName = "LoanTypeAmountIndex";
firstValues = { "HomeLoan", 500000 };
lastValues  = { "HomeLoan", 2000000 };
```

---

## 4️⃣ **queryFlags — Query Options**

Flags can be OR-combined (`|`).

### Common Flags:

| Flag                            | Meaning                    |
| ------------------------------- | -------------------------- |
| `QUERY_NO_SYSTEM_FIELDS`        | Ignore system fields       |
| `QUERY_PROPERTY_SELECT`         | Select specific properties |
| `QUERY_SORT_DESCENDING_ENABLED` | Sort descending            |
| `QUERY_READONLY`                | Read-only mode             |

### Example (Descending Sort):

```java
queryFlags = VWRoster.QUERY_SORT_DESCENDING_ENABLED;
```

### **Real-Time Scenario**

Insurance company wants:

* Latest claims first
* Sort by ClaimDate descending

---

## 5️⃣ **filter — SQL-like WHERE clause**

Works like SQL but only for Roster fields.

### Example:

```java
String filter = "F_LoanType = :A AND F_Status = :B";
```

Colon **(:)** is required before variable names.

---

## 6️⃣ **substitutionVars — Values for filter placeholders**

These replace `:A`, `:B`, etc.

### Example:

```java
Object[] substitutionVars = { "HomeLoan", "Pending" };
```

Final filter becomes:

```
F_LoanType="HomeLoan" AND F_Status="Pending"
```

### ⚠️ IMPORTANT

If filter has 3 placeholders → substitutionVars **must** contain 3 values.

---

## 7️⃣ **fetchType — What type of objects to fetch?**

| Value | Meaning                                 |
| ----- | --------------------------------------- |
| `1`   | Fetch WorkObject (`VWWorkObject`)       |
| `4`   | Fetch RosterElement (`VWRosterElement`) |

### Example:

Fetch full workflow data:

```java
fetchType = VWFetchType.FETCH_TYPE_WORKOBJECT;
```

Fetch only listing info:

```java
fetchType = VWFetchType.FETCH_TYPE_ROSTER_ELEMENT;
```

---

# 🟦 SECTION 3 — Complete Example (Real-Time)

### **Scenario: Loan Manager Dashboard**

Need to fetch:

* Home Loans
* Amount between 5L–20L
* Status = "Verification"
* Sorted Descending
* Fetch WorkObject

### ✅ **Code**

```java
VWRoster roster = session.getRoster("LoanRoster");

String indexName = "LoanTypeAmountIndex";

Object[] firstValues = { "HomeLoan", 500000 };
Object[] lastValues  = { "HomeLoan", 2000000 };

int queryFlags = VWRoster.QUERY_SORT_DESCENDING_ENABLED;

String filter = "F_Status = :A";
Object[] substitutionVars = { "Verification" };

int fetchType = VWFetchType.FETCH_TYPE_WORKOBJECT;

VWRosterQuery query = roster.createQuery(
    indexName,
    firstValues,
    lastValues,
    queryFlags,
    filter,
    substitutionVars,
    fetchType
);

while (query.next()) {
    VWWorkObject wo = query.getWorkObject();
    System.out.println("WobNum: " + wo.getWorkObjectNumber());
    System.out.println("Loan Amount: " + wo.getFieldValue("F_LoanAmount"));
}
```

---

# 🟩 SECTION 4 — More Real-Time Scenarios

### ⭐ **Scenario 1 — Insurance: Claims older than 5 days**

```txt
filter = "ClaimDate < :A"
substitutionVars = { "20250120T000000Z" }
```

### ⭐ **Scenario 2 — HR Onboarding: Background Check Pending**

```txt
filter = "F_StepName = :A"
substitutionVars = { "BackgroundCheck" }
```

### ⭐ **Scenario 3 — Passport Service: Police Verification Pending**

```txt
filter = "F_Status = :A"
substitutionVars = { "PoliceVerification" }
```

---

# 🟦 SECTION 5 — Summary Table

| Parameter            | Purpose                     |
| -------------------- | --------------------------- |
| **indexName**        | Which search index to use   |
| **firstValues**      | Minimum value range         |
| **lastValues**       | Maximum value range         |
| **queryFlags**       | Sorting / query options     |
| **filter**           | SQL-like filter conditions  |
| **substitutionVars** | Placeholder values          |
| **fetchType**        | WorkObject or RosterElement |

---
