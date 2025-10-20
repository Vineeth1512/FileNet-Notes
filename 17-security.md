# 🔐 FileNet – Security

Security in FileNet ensures that **only authorized users** can access, modify, or delete documents and objects in an Object Store.  
It’s crucial for **data integrity, compliance, and auditing**.

---

## 🧑‍💻 Technical Definition
FileNet security is based on **Access Control Lists (ACLs)** and **permissions**.  
Key components:

1. **Users and Groups** – Individual accounts or collections of users.  
2. **Roles** – Define job functions (e.g., Reader, Author, Admin).  
3. **Permissions** – Control actions on objects (Read, Write, Delete, Check-out, etc.).  
4. **Security Inheritance** – Objects can inherit security from parent folders or classes.  
5. **Object-Level Security** – ACLs can be applied to individual documents, folders, or classes.  

---

## 🗣️ Simple English Definition
Security in FileNet is like **locking files in a digital cabinet**:  
- Only certain users can open, edit, or delete files.  
- Permissions can be given individually or via groups/roles.  
- You can inherit permissions from a folder or set them for individual files.

---

## 🎯 Purpose
- Prevent **unauthorized access** to documents.  
- Ensure **data privacy** and regulatory compliance.  
- Control **who can create, read, update, or delete** objects.  
- Allow **granular security** at document, folder, and class level.  

---

## 🔁 Why We Use Security
- Organizations often store **confidential data** (contracts, HR documents, invoices).  
- Security ensures only **authorized personnel** can access sensitive information.  
- Supports **audit trails** and **regulatory compliance**.

---

## ⚙️ Types of Security in FileNet

| Type | Description |
|------|-------------|
| Object-Level Security | Permissions on individual documents, folders, or classes |
| Inherited Security | Permissions inherited from parent folder or class |
| Role-Based Security | Assign permissions to roles/groups for multiple users |
| Access Control List (ACL) | List of users/groups with specific permissions |
| Security Templates | Predefined ACL templates for faster assignment |

---

## 💡 Real-Time Analogy
- Think of FileNet as a **digital office building**:  
  - **Users** = Employees  
  - **Groups** = Departments  
  - **Roles** = Job functions (Manager, Clerk)  
  - **ACL / Permissions** = Access cards that allow entry to certain rooms  
  - **Security Inheritance** = If a department has access to a floor, all rooms on that floor are accessible automatically  

---

## 🌍 Real-World Scenario
1. HR documents → Only HR managers can **read/edit/delete**.  
2. Finance invoices → Only Finance team can access, while auditors may have **read-only** access.  
3. Legal contracts → Certain users can **check out and update**, others only **view**.  

Security ensures **confidentiality, integrity, and compliance** across the organization.

---

## ⚙️ How to Configure Security in ACCE

1. Open **ACCE → Object Store → Browse**.  
2. Navigate to the **object (Document/Folder/Class)**.  
3. Right-click → **Security → Object Security**.  
4. Add **Users/Groups** and assign **roles or permissions**.  
5. Check **Inherit Security** if you want to use parent’s ACL.  
6. Click **OK / Save**.  

---

## 🗣️ How to Explain in Interview (Own Words)
> “FileNet security controls who can access, edit, or delete documents.  
> Permissions can be applied at object level or inherited from parent folders.  
> Roles, users, and groups define access, and ACLs store the permission details.”

---

## 🧾 Key Points for Interview
- Security is **essential for confidentiality and compliance**.  
- ACLs define which users or groups can perform which actions.  
- Security can be **inherited** from parent objects or applied individually.  
- Roles and groups simplify permission management for multiple users.  
- Critical for regulated industries like **finance, healthcare, and legal**.

---

## 🏁 Summary Table

| Component | Purpose |
|-----------|---------|
| Users | Individual accounts |
| Groups | Collection of users for permission assignment |
| Roles | Define job functions (Reader, Author, Admin) |
| ACL | List of permissions for objects |
| Object-Level Security | Protect individual documents or folders |
| Inheritance | Automatically assign parent permissions |
| Security Templates | Predefined ACLs for fast assignment |
