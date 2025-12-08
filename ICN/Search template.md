Here is the complete, simple, structured explanation of Search Templates in IBM Content Navigator (ICN) — in the same teaching style you like:

✔ Technical definition
✔ Real-life definition
✔ What it is
✔ Why we use it
✔ Types
✔ Real-life analogy
✔ FileNet example


---

🟦 ⭐ SEARCH TEMPLATES — COMPLETE EXPLANATION (ICN)


---

1️⃣ TECHNICAL DEFINITION

A Search Template in ICN is a reusable saved search configuration that defines search criteria, filters, properties, and display results so users can quickly find documents without manually entering search conditions every time.

It allows admins (or users with permission) to create predefined searches that others can use.


---

2️⃣ REAL-LIFE DEFINITION

A Search Template is like a saved filter in Google, Gmail, or Amazon — such as “Price below ₹1000”, “Unread emails”, or “Orders delivered last month”.

Instead of creating the same search again and again,
you save it once → then reuse it.


---

3️⃣ WHAT IT IS (Simple Explanation)

A Search Template contains:

Which classes to search

Which metadata fields to filter

Default search conditions

Sort order

Columns to display in results

Whether users can change the criteria

Which repository to search


It is basically a ready-made search form.

Users just open the template → click Search → get results instantly.


---

4️⃣ WHY WE USE SEARCH TEMPLATES (Purpose)

✔ Save time

Users don’t need to build complex searches every time.

✔ Maintain consistency

Everyone uses the same search criteria.

✔ Improve productivity

Single click gets all relevant documents.

✔ Reduce errors

Users cannot enter wrong filters or properties.

✔ Control what users can search

Admins restrict which properties users can filter by.

✔ Create department-based searches

HR, Finance, Legal — each can have custom search templates.


---

5️⃣ TYPES OF SEARCH TEMPLATES IN ICN

1️⃣ Simple Search Template

Basic filters

Mostly keyword searches


2️⃣ Advanced Search Template

Multiple criteria

Conditions like AND/OR

Date ranges

Numeric filters

Drop-down choices

Sorting & result formatting


3️⃣ Cross-Repository Search

Search multiple repositories at once (if configured).


---

6️⃣ WHAT IS THIS IN REAL LIFE?

📌 Real-Life Analogy: Saved Filters

Examples:

Gmail → “Unread Emails” saved filter

Amazon → “Mobiles under ₹20,000”

LinkedIn → “Jobs posted this week”


You don’t type the filter every time —
you click a saved filter.

This is EXACTLY what Search Templates do in ICN.


---

7️⃣ MATCHING FILENET EXAMPLE (Real-Time Scenario)

⭐ Scenario: Finance Team wants to find invoices quickly

Admin creates Invoice Search Template:

Conditions

Document Class = InvoiceDocument

Status = Pending OR Approved

Date >= Last 30 days

Amount <= 1,00,000


Display Columns

InvoiceNumber

Vendor

Amount

Status

Date


Settings

Users cannot change class

Optional: Users can change date filter

Repository = Finance_OS


Now Finance user just:

1. Opens Invoice Search Template


2. Clicks Search


3. Gets all invoices that match criteria




---

⭐ Another Example: HR Employee Search

Search Template: Employee File Search

Filters:

EmployeeID

Name

Department

DOJ (date range)


HR can quickly find:

All employees in a department

All employees who joined in 2025

A specific employee's file



---

8️⃣ SEARCH TEMPLATE COMPONENTS

A Search Template defines:

Component	Meaning

Repository	Where to search
Classes	Document types included
Properties	Metadata filters
Default conditions	Pre-filled values
Result columns	Which columns to show
Sort order	How results are arranged
Permissions	Who can use/edit the template



---

9️⃣ SEARCH TEMPLATE VS SAVED SEARCH

Feature	Search Template	Saved Search

Created by	Admin or power user	End user
Controls UI	Yes	No
Permissions	Controlled	Only user-level
Reusable by others	Yes	Maybe
Editable fields	Many	Limited



---

🔟 SUPER SIMPLE SUMMARY

Concept	Meaning

Search Template	Predefined search for users
Purpose	Fast, consistent, accurate search
Real life	Saved filters (e.g., unread emails)
FileNet example	Invoice Search Template



---

If you want next, I can explain:

✔ ICN Security

✔ ICN Plugins

✔ Workflow Entry Templates

✔ Difference between Search Template & Entry Template

✔ Class-Based Search vs Metadata Search

Just say “Next” or the topic name.
