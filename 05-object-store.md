# 🗃️ FileNet Object Store

## 🔹 What is an Object Store?

### 🧑‍💻 Technical Definition
In IBM FileNet, an **Object Store** is a **logical repository** within a Domain that stores **documents, folders, custom objects, and metadata definitions**.  
Each Object Store has its own **database schema** and **content storage area (CSA)**, making it an independent data container under the same Domain.  
It defines the **structure (classes, properties)** and **security rules** for content stored within it.

### 🗣️ Simple Definition
An Object Store is like a **dedicated cabinet or database** where all documents, folders, and related data are saved and organized in FileNet.

---
### 📝 How to Explain in Your Own Words
*"An Object Store is basically a separate storage space for a specific department or project where all documents and related information are kept organized. It’s like having a personal cabinet inside the main office building (Domain) that only holds the files relevant to that area."*

---

## 🔹 Why do we use an Object Store?

### 🧑‍💻 Technical Reason
- To organize and manage documents based on business functions or departments.  
- To isolate data for security, performance, and scalability reasons.  
- Provides a structure for storing metadata and classes unique to each business area.  
- Enables separate backup, recovery, and maintenance operations for each repository.

### 🗣️ Simple Reason
We use an Object Store to **store and organize all the documents of a department or project** in one place — safely and efficiently.

---

## 🎯 Purpose

| Area | Purpose |
|------|----------|
| Storage | Store documents, folders, and metadata objects |
| Organization | Separate repositories for different departments or applications |
| Security | Apply access permissions specific to each repository |
| Scalability | Distribute load by having multiple Object Stores |
| Customization | Define classes and properties unique to business needs |
| Integration | Allow applications to interact with specific repositories through APIs |

---

## 🔁 Alternatives / Similar Concepts

| Technology | Equivalent Concept | Description |
|-------------|--------------------|--------------|
| **Database Systems** | Database / Schema | Logical storage of related data |
| **SharePoint** | Site Collection / Document Library | Repository for storing documents and lists |
| **AWS S3** | Bucket | Logical container for stored objects |
| **Alfresco** | Repository | Main container for all content and metadata |

---

# ⚙️ Factory Method to Get ObjectStore
| Method                                                                | Description                                              |
| --------------------------------------------------------------------- | -------------------------------------------------------- |
| `Factory.ObjectStore.fetchInstance(Domain domain, String name, null)` | Fetches an existing ObjectStore from a Domain            |
| `Factory.ObjectStore.createInstance(Domain domain)`                   | Creates a new ObjectStore (rarely used programmatically) |

---
# ⚙️ Common ObjectStore Methods

| Method                 | Return Type          | Description                          |
| ---------------------- | -------------------- | ------------------------------------ |
| `get_Name()`           | String               | Returns the ObjectStore name         |
| `get_Description()`    | String               | Returns description                  |
| `get_Domain()`         | Domain               | Returns the parent Domain            |
| `get_DocClasses()`     | DocumentClassSet     | Returns all Document Classes         |
| `get_FolderClasses()`  | FolderClassSet       | Returns all Folder Classes           |
| `get_CustomClasses()`  | CustomObjectClassSet | Returns all Custom Object Classes    |
| `get_Properties()`     | PropertyCollection   | Returns ObjectStore properties       |
| `refresh(RefreshMode)` | void                 | Refreshes ObjectStore object from CE |
| `checkIn()`            | void                 | Checks in a document                 |
| `checkOut()`           | Document             | Checks out a document for editing    |


## 💡 Real-Time Analogy

Think of the **Object Store** as a **filing cabinet for each department** in a company.

- The **Domain** = The entire office building  
- The **Object Store** = A filing cabinet for a department (like HR, Finance)  
- The **Drawers and folders** = Classes and folders inside the Object Store  
- The **Documents** = Actual files (PDFs, Word docs, etc.)  
- The **Labels** = Metadata properties that describe each file  

Each Object Store works independently but still belongs to the same Domain.

---

## 🧠 Real-Time Scenario

Imagine a **university** using FileNet:

1. The university has multiple departments — **Admissions**, **Examinations**, and **Library**.  
2. Each department has its own **Object Store**:
   - `AdmissionsOS` stores student applications and forms.  
   - `ExaminationsOS` stores exam results and hall tickets.  
   - `LibraryOS` stores digital book copies and records.  
3. Each Object Store has **custom classes** (e.g., `StudentRecord`, `ExamResult`) and **metadata** like `StudentID`, `Marks`, `IssuedDate`.  
4. The **Domain** connects them all under one environment.  
5. Security rules ensure that each department’s data remains separate and safe.

So, each Object Store acts like a **dedicated repository** for a specific business unit.

---

## 🧩 Key Takeaways

- **Object Store** is the **core repository** where FileNet stores all content and metadata.  
- It belongs to a **Domain** and has its own **database and storage area**.  
- Used to separate data logically and securely for different departments or applications.  
- Contains **Classes**, **Properties**, and **Documents**.  
- Multiple Object Stores can exist under one Domain.

---

## 📎 Technical Summary

| Feature | Description |
|----------|--------------|
| Type | Logical content repository |
| Contained In | Domain |
| Stores | Documents, Folders, Custom Objects, Metadata |
| Backend | Relational Database + Content Storage Area |
| Managed Using | ACCE or FileNet APIs |
| Security | Repository-level ACLs and permissions |
| Typical Naming | `HRObjectStore`, `FinanceOS`, `ClaimsOS`, etc. |

---

## 🔗 Next Topics
- [Document Classes and Properties](./08-document-classes.md)
- [Storage Area](./07-storage-area.md)
