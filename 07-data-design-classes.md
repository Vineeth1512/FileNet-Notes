# 🧩 FileNet ACCE — Class

## 🔹 Technical Definition
A **Class** in IBM FileNet is a **blueprint for creating and storing objects** (like Documents or Folders) in an Object Store.  
Each Class defines **the structure, metadata, and behavior** of a particular type of object.  
Classes can inherit properties and behaviors from **parent classes** (e.g., `Document`, `Folder`) and can include **custom properties** through Property Templates.

---

## 🗣️ Simple Definition
A **Class** is like a **template or category** that decides what kind of documents or folders you’re storing and what information they should have.

Example: A “Resume” class might include properties like `CandidateName`, `Experience`, and `Skills`.

---

## 🎯 Purpose
- To **define document types** and their metadata.  
- To **organize and categorize content** logically within an Object Store.  
- To **apply custom properties**, workflows, and security at the class level.  
- To **enable inheritance**, where child classes reuse and extend parent class features.

---

## ❓ Why We Use It
In enterprise content management, different document types (like Invoices, Contracts, and Reports) have different sets of information.  
Creating separate Classes for each allows:
- Clear organization  
- Custom metadata  
- Easy searching and filtering  
- Consistent structure  

---

## 🔁 Alternatives / Similar Concepts

| Platform / Technology | Equivalent Concept |
|------------------------|--------------------|
| Database | Table schema |
| Java | Class / Object |
| SharePoint | Content Type |
| Excel | Worksheet Template |
| File System | Folder Type or Template |

---

## 🧠 Real-Time Analogy
Think of a **school record system**:
- You have different registers for **Students**, **Teachers**, and **Exams**.  
- Each register has its own structure (different columns).  
- That structure is the **Class definition** — for example, a “Student Record” class defines properties like Name, Roll Number, and Grade.

So, just like different forms serve different purposes, **each Class in FileNet serves a specific document type**.

---

## 🧩 Example

| Class Name | Parent Class | Example Properties |
|-------------|---------------|--------------------|
| Invoice | Document | InvoiceNumber, CustomerName, Amount |
| PurchaseOrder | Document | PO_ID, SupplierName, TotalValue |
| EmployeeRecord | Document | EmpID, Name, Department |

---

## 🧠 Real-World Scenario
In an **insurance company**, different departments store different kinds of documents:
- **PolicyDocument** – contains PolicyNumber, CustomerName, and CoverageAmount  
- **ClaimDocument** – contains ClaimID, ClaimStatus, ClaimAmount  
- **PaymentReceipt** – contains ReceiptNumber, Date, and Amount  

Each of these is defined as a **separate Class**, ensuring that each document type has relevant fields and workflows.

---

## ⚙️ Key Characteristics

| Feature | Description |
|----------|--------------|
| Inheritance | Classes can extend other classes (e.g., a custom document class extends `Document`) |
| Properties | Each class contains one or more properties defined via Property Templates |
| Security | Class-level access control can be applied |
| Behavior | Determines versioning, retention, and workflow rules |
| Storage | Each class instance represents a stored object (document/folder) |

---

## 🗂️ Types of Classes

1. **Document Class** – Used for storing documents (e.g., PDFs, images, text).  
2. **Folder Class** – Used for organizing documents.  
3. **Custom Object Class** – Used for non-document metadata objects.  
4. **Event Class** – Used for tracking actions/events on objects.

---

## 🗣️ How to Explain in Interview (In Your Own Words)
> “A Class in FileNet defines a specific type of document or folder and its structure.  
> It’s like a form template that controls what information is stored and how it behaves in the system.”

---

## 💬 Common Interview Questions

**Q1:** What is a Class in FileNet?  
**A:** A Class defines the structure and behavior of a specific document or folder type in an Object Store.

**Q2:** Can a Class inherit properties from another Class?  
**A:** Yes, FileNet supports class inheritance — child classes can extend parent classes like `Document` or `Folder`.

**Q3:** How do Property Templates relate to Classes?  
**A:** Property Templates define individual fields; Classes use those templates to define complete document types.

**Q4:** Can one Class use multiple Property Templates?  
**A:** Yes, you can attach multiple Property Templates to a single Class.

**Q5:** What is the difference between a Document Class and a Folder Class?  
**A:** A Document Class stores actual content files (like PDFs or images), while a Folder Class is used for organizing those documents.

---

## 🧭 Real-Time Example (Scenario)
**Organization:** Bank  
**Use Case:** Document Management System

| Class | Properties | Description |
|--------|-------------|-------------|
| CustomerDocument | CustomerID, Name, Address | Stores KYC-related files |
| LoanDocument | LoanID, LoanType, Amount | Stores loan agreements |
| TransactionReceipt | ReceiptID, Date, Amount | Stores payment receipts |

Each Class defines how that document type behaves and which fields it must have.

---

## 💡 Real-Time Analogy
Think of **Google Drive folders**:
- You may have a folder for “Invoices”, another for “Resumes”, and another for “Reports”.  
Each folder type has a different naming format and set of required fields.  
In FileNet, those folder/document definitions are your **Classes**.

---

## 🧠 Quick Recap
| Aspect | Description |
|--------|--------------|
| Definition | Blueprint that defines the structure and metadata of a FileNet object |
| Purpose | Organize and control document/folder types |
| Example | Invoice, Contract, Report |
| Related To | Property Templates, Choice Lists |
| Analogy | Form template or database table |

---

