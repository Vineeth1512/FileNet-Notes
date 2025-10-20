# 📚 FileNet Notes

Welcome to my **FileNet ACCE Notes** repository.  
This repository contains detailed notes on IBM FileNet concepts, organized for **easy learning, interview preparation, and GitHub reference**.  

Each topic includes:
- Technical definition  
- Simple explanation  
- Purpose and why it’s used  
- Alternatives  
- Real-time analogies  
- Real-world scenarios  
- Step-by-step instructions in ACCE  
- How to explain in your own words for interviews  

---

## 📌 Table of Contents

### 1️⃣ Introduction
- [FileNet Overview](./01-introduction.md) – Explanation of FileNet as a digital office system  
- [Content Engine](./02-content-engine.md) – Enhance understanding of Content Engine  
- [ACCE Overview](./03-ACCE.md) – Explanation of ACCE in own words  

### 2️⃣ Domain & Object Store
- [Domain](./04-filenet-domain.md) – Purpose, definition, and examples  
- [Object Store](./05-filenet-object-store.md) – Concepts, purpose, and alternatives  

### 3️⃣ ACCE Folders
- [BROWSE & DATA DESIGN](./06-acce-browse-data-design.md) – Explanation of ACCE folders and their functionalities  

### 4️⃣ Data Design
- [Classes Overview](./07-data-design-classes.md) – Class concept in FileNet ACCE  
- [Property Templates](./08-property-templates.md) – Reusable metadata fields  
- [Choice Lists](./09-choice-lists.md) – Field options and reusable lists  

### 5️⃣ Individual Classes
- [Document Class](./10-document-class.md) – Storing content with metadata  
- [Folder Class](./12-folder-class.md) – Organizing documents logically  
- [Custom Object Class](./11-custom-object-class.md) – Storing non-content data  

---

## 📖 How to Use These Notes
- **Learning:** Follow the Table of Contents step by step.  
- **Interview Preparation:** Each topic contains Q&A and “how to explain in own words.”  
- **Reference:** Notes include real-time analogies and examples for better understanding.  

---

## 🔗 Future Topics to Add
- Creating Classes in ACCE (step-by-step screenshots)  
- Workflow concepts in FileNet  
- Security and access control  
- Versioning and retention  
- Real-time project scenarios  

---

## 🚀 Quick Analogy
Think of FileNet ACCE as a **digital office filing system**:
- **Domains** = Company headquarters  
- **Object Stores** = Departments  
- **Classes** = File templates (Document, Folder, Custom Object)  
- **Property Templates & Choice Lists** = Field definitions for forms  
- **Folders** = Actual folders grouping files  
- **Documents** = The files stored  

Everything is structured, consistent, and easily searchable — like a perfectly organized digital filing cabinet.

## 🖼️ FileNet ACCE Hierarchy Diagram

```mermaid
graph TD
    A[Domain] --> B[Object Store]
    B --> C[ACCE Folders]
    C --> D[BROWSE Folder]
    C --> E[DATA DESIGN Folder]
    E --> F[Classes]
    E --> G[Property Templates]
    E --> H[Choice Lists]
    F --> I[Document Class]
    F --> J[Folder Class]
    F --> K[Custom Object Class]

