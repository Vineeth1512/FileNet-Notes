Here is the complete, simple, structured explanation of Entry Templates in IBM Content Navigator (ICN) — in the same format you like:

✔ Technical definition
✔ Real-life definition
✔ What it is
✔ Why we use it
✔ Types
✔ Real-life example
✔ FileNet example


---

🟦 ⭐ ENTRY TEMPLATES — COMPLETE EXPLANATION (ICN)


---

1️⃣ TECHNICAL DEFINITION

An Entry Template in ICN is a predefined configuration that controls how documents are created, uploaded, filed, and assigned metadata inside a repository.

It defines:

Default document class

Pre-filled metadata

Folder location

Security

Versioning behavior

Required fields


Entry Templates standardize document creation across the organization.


---

2️⃣ REAL-LIFE DEFINITION

An Entry Template is like a pre-designed form or preset that employees must use when adding a document — similar to a pre-filled form for invoice submission or a standard template for resumes.

It ensures:

Same format

Same fields

Same location

No mistakes



---

3️⃣ WHAT IT IS (Simple Explanation)

An Entry Template controls:

✔ Where the document goes

(folder path)

✔ What class it uses

(InvoiceDocument, EmployeeDocument...)

✔ What metadata appears

(properties shown to user)

✔ Which values are pre-filled

(default values, locked values)

✔ Who gets access

(security settings)

✔ Whether versioning is enabled

(major/minor)

✔ What actions are allowed

(check-in / check-out rules)

It is like a pre-configured form for uploading documents.


---

4️⃣ WHY WE USE ENTRY TEMPLATES (Purpose)

✔ Standardize document upload

Ensure every invoice, contract, HR file follows the same structure.

✔ Reduce errors

Users cannot enter wrong values or wrong metadata.

✔ Predefined folder structure

Automatically stores files in correct location.

✔ Enforce business rules

Mandatory fields, auto-filled fields, restricted choices.

✔ Save user time

Avoid filling long forms every time.

✔ Improve data quality

Metadata becomes consistent and clean.

✔ Apply security automatically

Control who can access newly created documents.


---

5️⃣ TYPES OF ENTRY TEMPLATES

ICN supports 3 types:

1️⃣ Document Entry Template

Used to upload new documents.

2️⃣ Folder Entry Template

Used to create folders with predefined properties & security.

3️⃣ Workflow Entry Template

Used to start workflows with predefined values.


---

6️⃣ WHAT IS THIS IN REAL LIFE?

📌 Real-Life Analogy: Pre-Filled Form

Example:

When submitting a leave request, you get a pre-designed form.

When applying for a loan, you get a predefined loan application form.

When uploading an invoice, a standard template is required.


Entry Template = predefined form
Document Class = type of form
Folder = where the form is kept


---

7️⃣ MATCHING FILENET EXAMPLE (Real-Time Scenario)

⭐ Scenario: Invoice Processing

Admins create an Entry Template called:

Invoice_Upload_Template

Configuration:

Document Class → InvoiceDocument

Folder → /Finance/Invoices/2025/

Property: Year → auto-filled

Property: Department → “Finance” (locked)

Security → Finance Only

Must attach PDF (allowed MIME type)


User Upload Flow:

1. User selects Invoice_Upload_Template


2. The form opens with pre-filled fields


3. User attaches Invoice123.pdf


4. ICN stores it in the correct folder


5. Metadata is applied


6. Workflow automatically starts (if linked)



This prevents:

Mis-filing

Wrong class selection

Wrong metadata

Wrong security



---

⭐ Another Example: Employee Document Template

Entry Template: EmployeeRecord_Template

Class: EmployeeDocument

Folder: /HR/Employees/{EmployeeID}

Default security: HR-only

Required fields: Name, DOJ, Department


HR personnel simply:

Select Template

Fill minimum details

Attach document


Everything else is automated.


---

8️⃣ ENTRY TEMPLATE COMPONENTS

An Entry Template includes:

Component	Meaning

Document Class	Which class the document belongs to
Destination Folder	Where document will be stored
Pre-filled Fields	Default metadata
Locked Fields	User cannot change them
Allowed File Types	PDF, JPG, DOCX, etc.
Versioning Rules	Major/minor allowed
Security	Who gets access after creation
Auto-Launch Workflow	Optional



---

9️⃣ ENTRY TEMPLATE VS DOCUMENT CLASS

Feature	Entry Template	Document Class

Purpose	Guide how to create a document	Define structure of a document
Used by	End users	Admins
Controls	Folder, defaults, UI	Properties, metadata, behavior
Editable by user	Yes	No



---

🔟 SUPER SIMPLE SUMMARY

Concept	Meaning

Entry Template	Pre-configured form for document upload
Used for	Standardizing document creation
Controls	Class, folder, metadata, security
Real life	Pre-filled submission form
FileNet example	Invoice_Upload_Template



---

If you want next, I can explain:

✔ Teamspaces

✔ Workflow Entry Template

✔ Document vs Entry Template vs Class

✔ How to configure Entry Templates

✔ ICN Search Templates

Just say “Next” or the topic name.
