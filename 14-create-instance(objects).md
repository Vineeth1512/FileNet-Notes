# 🏗️ FileNet ACCE – Creating an Instance for a Class

In FileNet, after you create **Classes** (Document, Folder, Custom Object), the next step is to **create instances** of those classes.  
An **instance** is an actual object based on the class blueprint.

---

## 🧑‍💻 Technical Definition
- A **Document Instance** → An actual document stored in FileNet based on a Document Class.  
- A **Folder Instance** → A folder created in the Object Store based on a Folder Class.  
- A **Custom Object Instance** → A non-content object storing metadata, based on a Custom Object Class.

> In short, **Classes = Blueprint**, **Instances = Actual objects created from the blueprint**.

---

## 🗣️ Simple English Definition
Think of a **Class** as a cookie cutter, and an **Instance** as the actual cookie.  
- Document Class → Template for invoices → Document instance = “Invoice_123.pdf”  
- Folder Class → Template for folders → Folder instance = “Customer_A Folder”  
- Custom Object Class → Template for lookup data → Instance = “Branch: Hyderabad Main”

---

## 🎯 Purpose
- To **store actual documents** using Document Classes.  
- To **organize documents** using Folder Classes.  
- To **store metadata or configuration data** using Custom Object Classes.  
- To enable **search, retrieval, and management** of objects in the Object Store.

---

## 🔁 Alternatives / Similar Concepts

| Platform / Technology | Equivalent Concept |
|------------------------|--------------------|
| Database | Table = Class, Row = Instance |
| Java | Class = Class, Object = Instance |
| Windows | Folder template = Class, Folder = Instance |
| Google Docs | Template = Class, Document = Instance |

---

## ⚙️ Steps to Create Instances in ACCE

### 1️⃣ Document Instance
1. Open **ACCE → Object Store → Browse**.  
2. Navigate to the **Folder** where you want to store the document.  
3. Right-click → **New → Document**.  
4. Select the **Document Class** (e.g., `InvoiceDocument`).  
5. Fill in the **metadata properties** (Invoice Number, Customer Name, Amount).  
6. Upload the **content file** (PDF, Word, etc.).  
7. Click **OK / Save**.  

✅ Document instance is now created in FileNet.

---

### 2️⃣ Folder Instance
1. Open **ACCE → Object Store → Browse**.  
2. Navigate to the **parent folder** (or Object Store root).  
3. Right-click → **New → Folder**.  
4. Select the **Folder Class** (e.g., `CustomerFolder`).  
5. Fill in **folder metadata** (Customer Name, ID).  
6. Click **OK / Save**.  

✅ Folder instance is now created.

---

### 3️⃣ Custom Object Instance
1. Open **ACCE → Object Store → Browse**.  
2. Navigate to the **location** where you want the object.  
3. Right-click → **New → Custom Object**.  
4. Select the **Custom Object Class** (e.g., `BranchInfo`).  
5. Fill in **property values** (Branch Name, Branch Code, Address).  
6. Click **OK / Save**.  

✅ Custom Object instance is now created.

---

## 💡 Real-Time Analogy
- Document Class → Invoice Template → Document Instance = “Invoice_001.pdf”  
- Folder Class → Project Folder Template → Folder Instance = “Project_X”  
- Custom Object Class → Branch Info Template → Instance = “Hyderabad Main Branch”

Creating an instance = **actually using the template to create real objects**.

---

## 🧠 Real-World Scenario
- Uploading a **contract document** for a client → Document Instance of `ContractDocument` Class.  
- Creating a **new customer folder** → Folder Instance of `CustomerFolder` Class.  
- Adding a **new branch info** → Custom Object Instance of `BranchInfo` Class.

---

## 🗣️ How to Explain in Interview (Own Words)
> “In FileNet, creating an instance of a class means making an actual object (document, folder, or custom object) based on a predefined class blueprint.  
> Classes define the structure, instances are the real items we store and manage.”

---

## 🧾 Key Points
- Classes define **structure**, instances store **actual data**.  
- Document instances store files, folder instances organize files, custom object instances store metadata.  
- Instances are created **via ACCE → Browse → New → [Document/Folder/Custom Object]**.

---

## 🏁 Summary Table

| Class Type | Instance Type | Contains Content? | Purpose |
|------------|---------------|-----------------|---------|
| Document Class | Document Instance | ✅ Yes | Store actual files with metadata |
| Folder Class | Folder Instance | ❌ No | Organize documents logically |
| Custom Object Class | Custom Object Instance | ❌ No | Store reusable metadata/configuration |
