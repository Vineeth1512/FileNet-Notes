# 🔐 Security in FileNet — AD & LDAP Explained

## ✅ What is Security in FileNet?
Security in FileNet ensures that only authorized users can:
- Access documents
- Modify content
- Delete files
- View system objects (folders, classes, properties)

FileNet security is mainly controlled using:
- **Access Control Lists (ACLs)**
- **Permissions**
- **Security Policies**
- **Active Directory Groups**

---

## 🏢 What is Active Directory (AD)?
Active Directory (AD) is a **centralized identity management system** in a Windows Server.

### ✔ Technical Definition
Active Directory is a **directory service + database** used to store and manage:
- User accounts
- User groups
- Computers
- Authentication & Authorization permissions

### ✔ How AD is used by FileNet
FileNet does NOT create users inside FileNet.
Instead, FileNet **imports users and groups from AD** and applies permissions.

> **AD = Who the user is**
>  
> **FileNet = What the user can access**

---

## 🔑 What is LDAP?
LDAP (Lightweight Directory Access Protocol) is the **protocol** used to:
- Authenticate (login validation)
- Query AD to check user existence

> LDAP = Security guard who checks credentials at the entrance  
> AD = Office where user details are stored

---

## 🔁 Technical Workflow (AD + LDAP + FileNet)
1️⃣ User tries to login to FileNet  
2️⃣ LDAP validates username + password with AD  
3️⃣ AD tells FileNet the user is valid  
4️⃣ FileNet checks AD group membership  
5️⃣ FileNet applies permissions (ACL)  
6️⃣ User gets access **only** to allowed folders/documents

---

## 🔐 Types of Security in FileNet

| Type | Purpose |
|------|---------|
| Authentication | Validate the user (Done by LDAP/AD) |
| Authorization | Check access rights (Done by FileNet ACL) |
| Object-Level Security | Set permissions on Folder/Document |
| Class-Level Security | Restrict document classes |
| Property-Level Security | Restrict specific document properties |
| Administrative Security | Roles for system admins |

---

# 🌍 Real-Time Scenario
### Company Example

| Real Life | Technology Mapping |
|----------|-------------------|
| HR maintains employee info | AD stores user accounts |
| Employee shows ID card at gate | LDAP checks login |
| Only Finance team enters Finance room | FileNet allows access based on AD groups |

### Example Story
- A new employee **Vineeth** joins Finance team
- Admin creates an account in **Active Directory**
- Adds Vineeth to **FinanceGroup**
- In FileNet, Finance folder ACL allows **FinanceGroup**
- So Vineeth can open Finance docs ✅  
- He cannot open HR docs ❌

---

## 🧠 Interview Summary

| Question | Short Answer |
|---------|--------------|
| What is AD in FileNet? | A centralized identity store that provides users & groups to FileNet. |
| What is LDAP? | A protocol used by FileNet to authenticate users from AD. |
| What is Security in FileNet? | Mechanism to protect content using ACLs and permissions. |
| Who controls authorization? | FileNet using AD groups in ACL. |

---

✅ AD = Place + Service + Database  
✅ LDAP = Communication protocol for authentication  
✅ FileNet = Authorization system using AD groups

---

