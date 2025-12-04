Here is the clear, structured, interview-ready explanation of the Difference between Document Class and Custom Object Class — with definition, purpose, real-life analogy, and FileNet examples.


---

🟦 ⭐ DIFFERENCE BETWEEN DOCUMENT CLASS & CUSTOM OBJECT CLASS


---

1️⃣ TECHNICAL DIFFERENCE (Short & Perfect)

✔ Document Class

A class used to store documents with content (PDF, image, Word file, etc.), along with metadata.

✔ Custom Object Class

A class used to store data records without any document content, only metadata.


---

2️⃣ WHAT THEY STORE

Class Type	Stores Content?	Stores Metadata?

Document Class	✔ Yes (file)	✔ Yes
Custom Object Class	✖ No file	✔ Only metadata



---

3️⃣ REAL-LIFE EXPLANATION

📌 Document Class = A physical file folder

Contains:

Actual document (paper/PDF)

Details written on it (name, date)


Example: An employee file containing a signed document.

📌 Custom Object Class = Entry in a register book

Contains:

Only information

No physical document attached


Example: An entry in a school attendance register.


---

4️⃣ PURPOSE (WHY WE USE EACH ONE)

⭐ Document Class Purpose

Store actual files (content)

Apply versioning (V1, V2, V3)

Support checkin/checkout

Store multiple renditions (PDF, TIFF)

Attach documents to workflows


⭐ Custom Object Class Purpose

Store only business data

No need for files

Fast searches

Store workflow-related info

Store configuration or reference data

Lightweight records



---

5️⃣ FEATURE DIFFERENCES

Feature	Document Class	Custom Object Class

Stores files (content)?	✔ Yes	✖ No
Versioning	✔ Supported	✖ Not supported
MIME type	Required	Not applicable
Checkin/Checkout	✔ Yes	✖ No
Renditions (PDF/TIFF)	✔ Yes	✖ No
Used in workflows	Yes	Yes
Storage footprint	Larger	Very small
Typical use	Business documents	Data records



---

6️⃣ FILENET EXAMPLES

📘 Document Class Example

InvoiceDocument

Stores: Invoice123.pdf

Metadata: InvoiceNumber, Amount

Versioning: V1, V2

Renditions: PDF, TIFF


This contains actual files.


---

📘 Custom Object Class Example

LoanApplicationRecord

Stores: LoanID, CustomerID, Status

No file attached

Used by workflow to track loan progress


This contains only metadata.


---

7️⃣ WHEN TO USE WHAT? (REAL-TIME DECISION)

✔ Use Document Class when:

There is a file involved

You need versioning

You need checkin/checkout

You store scanned or uploaded documents

Workflow requires document attachments


✔ Use Custom Object Class when:

You need only data, no file

Record supports workflows

Storing configuration/settings

When you need fast lookup

For master data or temporary process data



---

8️⃣ SUPER SIMPLE SUMMARY

Document Class	Custom Object Class

Stores files + metadata	Stores metadata only
Heavy objects	Lightweight objects
Versioning, renditions	No versioning
Used for documents	Used for data records
Example: Invoice.pdf	Example: LoanRecord



---

Want the next topic?

I can explain:

Versioning

Properties

Security inheritance

Object store

Difference between class vs instance

Document lifecycle & behaviors


Just tell me “Next”.
