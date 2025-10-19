# 📂 ACCE Object Store Subfolders: BROWSE & DATA DESIGN

## 🔹 What are BROWSE and DATA DESIGN folders?

### 🧑‍💻 Technical Definition
In IBM FileNet ACCE:

- **BROWSE**: A subfolder in an Object Store used to **view and navigate** existing content objects, folders, documents, and instances. It allows admins and users to **explore the repository structure and contents** without modifying the schema.
  
- **DATA DESIGN**: A subfolder used to **define and manage content structures** such as **Classes, Properties, Folders, and Document Types**. It is the section where **object definitions and metadata models** are created or modified.

### 🗣️ Simple Definition
- **BROWSE** = “Explorer” window to see what’s inside the Object Store.  
- **DATA DESIGN** = “Builder” area where you define **how content is structured** and what properties documents should have.

### 📝 How to Explain in Your Own Words
*"In ACCE, every Object Store has two main areas: BROWSE to look at existing files and folders, and DATA DESIGN to create or change the types of documents, their properties, and folder structures. Think of BROWSE as looking inside a cabinet and DATA DESIGN as designing new compartments inside it."*

---

## 🔹 Why do we use these subfolders?

### 🧑‍💻 Technical Reason
- **BROWSE**: To **inspect and validate** stored content, check permissions, and review object structure.  
- **DATA DESIGN**: To **create or customize** classes, properties, and folders for documents.  
- Helps maintain **content integrity** and supports **development of new document types**.

### 🗣️ Simple Reason
- **BROWSE** lets you **look at your stored content** safely.  
- **DATA DESIGN** lets you **design and manage the layout** of how documents are stored and organized.

---

## 🎯 Purpose

| Folder | Purpose |
|--------|---------|
| BROWSE | Explore Object Store content, folders, documents, and instances |
| DATA DESIGN | Define Classes, Properties, Folders, and Document Types; manage metadata |

---

## 🔁 Alternatives / Similar Concepts

| Tool/Concept | Equivalent |
|--------------|------------|
| **Windows Explorer** | BROWSE |
| **Database Table Designer** | DATA DESIGN |
| **SharePoint Site Contents** | BROWSE |
| **SharePoint List Settings / Content Type Designer** | DATA DESIGN |

---

## 💡 Real-Time Analogy

Think of an **Object Store as a large filing cabinet**:

- **BROWSE** = Open the cabinet drawers to see all files and folders.  
- **DATA DESIGN** = Build new drawers or folders and decide what information each drawer will hold (like labels, sections, or compartments).  

You can look inside without changing anything (BROWSE) or reorganize the structure (DATA DESIGN).

---

## 🧠 Real-Time Scenario

A **bank** manages loan documents in FileNet:

1. **BROWSE**: The admin opens ACCE → Object Store → BROWSE to check existing `LoanApplication` documents, folders, and instances.  
2. **DATA DESIGN**: The developer creates a new class `MortgageApplication` with properties `CustomerID`, `LoanAmount`, `ApprovalStatus`.  
3. The `MortgageApplication` documents are now ready to be stored, and admins can browse them in BROWSE.  

This separation ensures **safe inspection (BROWSE)** and **controlled design (DATA DESIGN)**.

---

## 🧩 Key Takeaways

- **BROWSE** = Viewing existing content without modifying structure.  
- **DATA DESIGN** = Creating or updating content models, classes, and properties.  
- Together, they allow admins and developers to **manage content safely and efficiently**.  
- Fundamental to **ACCE Object Store operations**.

---

## 📎 Technical Summary

| Folder | Key Features |
|--------|--------------|
| BROWSE | View folders, documents, instances; check metadata and permissions; no schema modification |
| DATA DESIGN | Define Classes, Properties, Folders; manage metadata; design document types; update object structure |

---

## 🔗 Next Topics
- [Document Classes and Properties](./08-document-classes.md)
- [Workflows in FileNet](./09-workflows.md)
