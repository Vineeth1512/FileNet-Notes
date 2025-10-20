# 📄 FileNet ACCE — Document Class

---

## 🧑‍💻 Technical Definition
A **Document Class** in FileNet defines the **structure, metadata, and behavior** of documents (content-bearing objects) stored in the Object Store.  
Each document uploaded (PDF, Word file, image, etc.) is an instance of a Document Class.  

Document Classes inherit from the base system class called `Document`.  
They can contain:
- Binary **content** (files)
- Custom **properties** (metadata)
- **Security** and **versioning** rules

---

## 🗣️ Simple English Definition
A **Document Class** is like a **template for files** in FileNet.  
It defines what information every document should have and how it behaves.

Example:  
If you want to store invoices, you can create an `InvoiceDocument` class with fields like `InvoiceNumber`, `CustomerName`, and `TotalAmount`.

---

## 🎯 Purpose
- To **store actual content** (PDFs, images, Word docs).  
- To define **metadata structure** for each document type.  
- To apply **security**, **versioning**, and **lifecycle** rules.  
- To **categorize** different document types for easy search and retrieval.

---

## ❓ Why We Use It
Different document types (invoices, reports, receipts) require different properties.  
Using Document Classes allows you to manage, secure, and search each type efficiently with consistent metadata.

---

## 🔁 Alternatives / Similar Concepts

| Platform / Technology | Equivalent Concept |
|------------------------|--------------------|
| Database | Table containing file blobs |
| SharePoint | Document Content Type |
| ECM Tools | Content Type or Document Type |
| Java | Class with file and metadata attributes |

---

## 💡 Real-Time Analogy
Imagine a **filing cabinet** where each file represents a document.  
For every “Invoice File,” you always write the invoice number, date, and amount on the cover.  
That label format = **Document Class definition** in FileNet.

---

## 🧠 Real-World Scenario
In a **banking system**, the following Document Classes might exist:
- `LoanDocument` — holds PDF copies of loan agreements.  
- `KYCDocument` — holds scanned ID proofs.  
- `PaymentReceiptDocument` — holds receipts for EMI payments.  

Each class has its own metadata for search and tracking.

---

## ⚙️ Steps to Create a Document Class in ACCE

1. Open **ACCE** → Navigate to your **Object Store**.  
2. Expand **Data Design → Classes**.  
3. Right-click on **Document** → Select **New Subclass**.  
4. Enter details:
   - **Class Name:** (e.g., `InvoiceDocument`)  
   - **Display Name:** (e.g., `Invoice Document`)  
   - **Description:** (optional)  
5. In the **Properties** tab:
   - Add new property templates or reuse existing ones (e.g., `InvoiceNumber`, `Amount`).  
6. Set **security** and **versioning** behavior (optional).  
7. Click **Save and Close**.  

✅ The new Document Class is ready for use — every uploaded document of this type will follow its metadata structure.

---

## 🗣️ How to Explain in Interview (Own Words)
> “A Document Class in FileNet defines the structure and metadata of content files stored in the Object Store.  
> It acts like a template for documents, ensuring consistency, searchability, and controlled access.”

---

## 💬 Common Interview Questions

**Q1. What is the purpose of a Document Class in FileNet?**  
A: To define and manage metadata and behavior for documents stored in the Object Store.

**Q2. Can a Document Class exist without content?**  
A: Technically yes, but it’s meant to represent content-bearing objects, so it usually holds files.

**Q3. Can we inherit from another Document Class?**  
A: Yes. You can create subclass hierarchies to reuse properties and behaviors.

**Q4. How do you add metadata fields to a Document Class?**  
A: By adding **Property Templates** in the class definition within ACCE.

**Q5. How is versioning handled?**  
A: Each Document Class inherits versioning support from the base `Document` class; you can configure major/minor version control.

---

## 🧩 Quick Summary

| Feature | Description |
|----------|--------------|
| Base Class | Document |
| Stores Content | ✅ Yes |
| Used For | Defining structure and metadata for documents |
| Example | InvoiceDocument, ReportDocument |
| Editable in ACCE | ✅ Yes |

---

## 🧠 Real-Time Analogy (Simple)
In your **Google Drive**, you upload different kinds of files — resumes, bills, reports.  
Imagine creating a rule saying:  
> Every "Invoice" file must have Invoice Number, Date, and Amount.  
That’s what a **Document Class** does in FileNet.

---

## 🏁 Summary in My Own Words
> “Document Classes in FileNet define what kind of documents can be stored and what data each document should have.  
> It’s like a blueprint for documents that ensures structure, security, and easy search.”

---
