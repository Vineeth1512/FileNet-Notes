# 🗂️ FileNet ACCE — Folder Class

---

## 🧑‍💻 Technical Definition
A **Folder Class** in FileNet defines the structure, metadata, and behavior of **folder objects** in the Object Store.  
Folders organize documents and other objects in a hierarchical structure.  
They can contain:
- Documents  
- Subfolders  
- Custom properties (metadata)

A Folder Class inherits from the base system class called `Folder`.

---

## 🗣️ Simple English Definition
A **Folder Class** is like a **container definition** that helps organize documents into meaningful groups.  
It describes what kind of folders can exist and what information (metadata) they hold.

Example:  
A `CustomerFolder` class may have properties like `CustomerID`, `CustomerName`, and `Region`.

---

## 🎯 Purpose
- To **group related documents** logically.  
- To apply **class-level security** or **metadata** to a set of documents.  
- To make **navigation and retrieval** easier.  
- To support **business-specific folder hierarchies**.

---

## ❓ Why We Use It
Different departments or projects may need different folder structures.  
By defining Folder Classes, you can create standardized structures and attach metadata that describes the folder’s contents.

---

## 🔁 Alternatives / Similar Concepts

| Platform / Technology | Equivalent Concept |
|------------------------|--------------------|
| Windows | Folder |
| SharePoint | Document Library Folder |
| Database | Logical grouping or schema |
| Java | Object container class |

---

## 💡 Real-Time Analogy
Think of a **filing cabinet** with folders for each client.  
Each folder holds that client’s documents and has a label (Client Name, ID, Project).  
That label = Folder properties,  
and the folder itself = Folder Class instance.

---

## 🧠 Real-World Scenario
In a **bank**, a Folder Class like `AccountFolder` can store:
- KYC documents  
- Loan agreements  
- Statements  

Folder properties: `AccountNumber`, `CustomerName`, `BranchCode`  

All documents related to one account are grouped under the same folder.

---

## ⚙️ Steps to Create a Folder Class in ACCE

1. Open **ACCE** → Navigate to your **Object Store**.  
2. Expand **Data Design → Classes**.  
3. Right-click on **Folder** → Select **New Subclass**.  
4. Enter details:
   - **Class Name:** (e.g., `CustomerFolder`)  
   - **Display Name:** (e.g., `Customer Folder`)  
   - **Description:** (optional)  
5. Go to the **Properties** tab:
   - Add property templates like `CustomerName`, `CustomerID`, `Region`.  
6. Define **security** or **inheritance rules** (optional).  
7. Click **Save and Close**.  

✅ Now you can create folders of this type in FileNet to organize documents by business logic.

---

## 🗣️ How to Explain in Interview (Own Words)
> “A Folder Class defines the structure and metadata of folders used to group documents in FileNet.  
> It helps organize content logically and allows adding metadata at the folder level.”

---

## 💬 Common Interview Questions

**Q1. What is a Folder Class in FileNet?**  
A: It defines how folders are structured and what metadata they contain for organizing documents.

**Q2. Can folders have custom properties?**  
A: Yes. Folder Classes allow custom metadata fields, just like Document Classes.

**Q3. Can we nest folders in FileNet?**  
A: Yes, you can create subfolders under a Folder Class instance to build hierarchies.

**Q4. Do Folder Classes store content?**  
A: No, they store metadata and can contain documents or subfolders.

**Q5. What is the base class for Folder Classes?**  
A: The base class is `Folder`.

---

## 🧩 Quick Summary

| Feature | Description |
|----------|--------------|
| Base Class | Folder |
| Stores Content | ❌ No |
| Used For | Organizing documents logically |
| Example | CustomerFolder, DepartmentFolder |
| Editable in ACCE | ✅ Yes |

---

## 💡 Real-Time Analogy (Simple)
In your **Google Drive**, you might have folders named:
- “Projects”  
- “Invoices”  
- “Personal Docs”  

Each has different purposes and possibly metadata.  
In FileNet, a Folder Class defines what those folders mean and how they behave.

---

## 🧠 How to Explain to Interviewer in My Own Words
> “A Folder Class in FileNet is like a structure that defines how folders are organized and what information they carry.  
> It’s used to group documents by department, customer, or project, helping with better management and searching.”

---

## 🏁 Summary
- Folders are containers, not content holders.  
- Each Folder Class can have its own metadata.  
- They help categorize and manage related document sets.  
- Created under **Data Design → Classes → Folder** in ACCE.  

---
