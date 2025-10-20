# 💻 FileNet – Code Modules 

FileNet provides **code modules / APIs** to programmatically interact with the Content Engine and Object Store.  
These modules enable **automation, integration, and bulk operations** beyond what ACCE offers.

---

## 🧑‍💻 Technical Definition
- Code Modules = API libraries to perform CRUD operations, search, and manage documents, folders, and custom objects programmatically.  
- Available in **Java**, **C#/.NET**, and **REST/Web Services**.

---

## 🎯 Purpose
- Automate **document management** tasks.  
- Integrate FileNet with **external systems**.  
- Perform **bulk operations** efficiently.  
- Implement **custom business logic**.

---

## ⚙️ Common Java APIs

| Module / Class | Purpose |
|----------------|---------|
| Connection | Connect to Content Engine |
| UserContext | Authenticate user |
| Domain | Access domain object |
| ObjectStore | Access and manage objects |
| Factory.Document | Create document instances |
| Factory.Folder | Create folder instances |
| Factory.CustomObject | Create custom object instances |
| SearchSQL / SearchScope | Execute queries |
| IndependentObjectSet | Result set of objects |
| RepositoryRowSet | Result set of search |

---

## 💡 Real-Time Analogy
- ACCE = GUI (manual operations)  
- Code Modules = Automation scripts/macros  

Example: Move all old invoices to archive → Code modules handle thousands of documents automatically.

---

## 🌍 Real-World Scenario
- Batch update metadata for thousands of documents after migration.  
- Automated archival of documents older than X years.  
- Integration with external workflow or ERP systems.

---

## 🗣️ How to Explain in Own Words (Interview)
> “Code modules are APIs to programmatically interact with FileNet, automate tasks, and integrate with other systems.  
> They help perform bulk operations efficiently compared to manual work in ACCE.”

---

## 🧾 Key Points
- Code modules: Java, .NET, REST APIs.  
- Automate document/folder/object management.  
- Support search, create, update, delete, and metadata operations.  
- Returns can be `IndependentObjectSet` or `RepositoryRowSet`.  

---

## ❓ Common Interview Questions

**Q1. What are FileNet Code Modules?**  
> APIs or libraries (Java, .NET, REST) to interact with Content Engine programmatically for CRUD, search, and workflow automation.

**Q2. What is the difference between ACCE and Code Modules?**  
> ACCE is a **manual GUI tool**.  
> Code Modules allow **programmatic automation**, integration, and bulk operations.

**Q3. Name some key Java classes used in FileNet coding.**  
> `Connection`, `UserContext`, `Domain`, `ObjectStore`, `Factory.Document/Folder/CustomObject`, `SearchSQL`, `IndependentObjectSet`, `RepositoryRowSet`.

**Q4. What is `IndependentObjectSet` and `RepositoryRowSet`?**  
> - `IndependentObjectSet` → Collection of full FileNet objects fetched.  
> - `RepositoryRowSet` → Collection of rows returned from a search query.

**Q5. How can you fetch documents from ObjectStore programmatically?**  
> Using `SearchSQL` with `SearchScope` or fetching by ID using `Factory.Document.fetchInstance()`.

**Q6. How do you create a document instance using Java API?**  
1. Get `ObjectStore` instance.  
2. Use `Factory.Document.createInstance()`.  
3. Set properties.  
4. Set content (`ContentElementList`).  
5. Check-in and save.

**Q7. How can Code Modules be used in real-time scenarios?**  
> Automating metadata updates, bulk archival, integrating FileNet with ERP/CRM, or running scheduled batch jobs.

**Q8. Difference between `fetchInstance()` and `createInstance()`?**  
> - `createInstance()` → Creates a new object.  
> - `fetchInstance()` → Retrieves an existing object from the repository.

**Q9. What is `UserContext` used for?**  
> To set authentication and security context for operations performed via code modules.

**Q10. How to explain Code Modules in own words?**  
> “They are libraries/APIs to work with FileNet programmatically, letting us automate tasks, manage objects, and integrate with other applications efficiently.”
