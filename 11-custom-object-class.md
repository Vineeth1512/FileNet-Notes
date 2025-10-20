# ⚙️ FileNet ACCE — Custom Object Class

---

## 🧑‍💻 Technical Definition
A **Custom Object Class** in FileNet is a **non-content object** used to store structured data or metadata that doesn’t represent a document or folder.  
It is based on the system class `CustomObject` and is mainly used for:
- Configuration data  
- Reference or lookup lists  
- Business entities that don’t need files attached

Custom Objects can have **custom properties** but do **not contain file content**.

---

## 🗣️ Simple English Definition
A **Custom Object Class** is like a **data record** inside FileNet that stores information but has no attached document.  
It’s useful when you want to store data such as a list of departments, regions, or configuration settings directly in FileNet.

Example:  
A `BranchInfo` Custom Object might store:
- `BranchName`  
- `BranchCode`  
- `Address`

---

## 🎯 Purpose
- To store **metadata, configuration, or lookup data** in FileNet.  
- To support dropdowns, mappings, or relationships for document metadata.  
- To hold reusable data that can be referenced by multiple classes or applications.  

---

## ❓ Why We Use It
Sometimes, applications need reference data that isn’t tied to any document —  
for example, department names, country lists, or system configuration values.  
Custom Object Classes allow this data to live **inside FileNet**, maintaining consistency and centralization.

---

## 🔁 Alternatives / Similar Concepts

| Platform / Technology | Equivalent Concept |
|------------------------|--------------------|
| Database | Table record without file column |
| SharePoint | List Item |
| Java | POJO (Plain Old Java Object) |
| Config File | JSON or YAML configuration |

---

## 💡 Real-Time Analogy
Imagine a **company address book** that lists branch names, codes, and locations.  
It’s not a file — it’s just information that others refer to.  
That’s what a **Custom Object** does in FileNet — it stores structured data for reference.

---

## 🧠 Real-World Scenario
In a **banking system**, a `BranchInfo` Custom Object Class might store:
- `BranchName` = “Hyderabad Main”  
- `BranchCode` = “HYD001”  
- `Manager` = “Ravi Kumar”  

When you upload a loan document, you can select this branch from a dropdown — data fetched from Custom Objects.

---

## ⚙️ Steps to Create a Custom Object Class in ACCE

1. Open **ACCE** → Navigate to your **Object Store**.  
2. Expand **Data Design → Classes**.  
3. Right-click on **Custom Object** → Select **New Subclass**.  
4. Enter details:
   - **Class Name:** (e.g., `BranchInfo`)  
   - **Display Name:** (e.g., `Branch Information`)  
   - **Description:** (optional)  
5. Go to the **Properties** tab:
   - Add property templates such as `BranchCode`, `BranchName`, `Address`.  
6. Click **Save and Close**.  

✅ You can now create instances of this class under **Browse → New Custom Object** and enter data directly.

---

## 🗣️ How to Explain in Interview (Own Words)
> “A Custom Object Class in FileNet is used to store configuration or reference data without attaching files.  
> It’s like keeping lookup tables or system settings directly inside FileNet for easy access.”

---

## 💬 Common Interview Questions

**Q1. What is a Custom Object Class in FileNet?**  
A: It’s a non-content class used to store metadata or configuration data.

**Q2. Does a Custom Object contain content?**  
A: No, it only stores property values — no binary file content.

**Q3. What are common use cases of Custom Object Classes?**  
A: Lookup lists (e.g., department names, region codes), configuration data, and business rules.

**Q4. How do Custom Objects relate to Document Classes?**  
A: Document Classes can reference Custom Objects to link metadata like department or branch info.

**Q5. Can we search for Custom Objects?**  
A: Yes, Custom Objects are searchable through Property Filters in FileNet Query.

---

## 🧩 Quick Summary

| Feature | Description |
|----------|--------------|
| Base Class | Custom Object |
| Stores Content | ❌ No |
| Used For | Storing configuration or reference data |
| Example | BranchInfo, DepartmentList |
| Editable in ACCE | ✅ Yes |

---

## 💡 Real-Time Analogy (Simple)
In your **phone**, your “Contacts” list is made of entries like Name, Number, and Address.  
They aren’t files, just structured information — just like **Custom Objects** in FileNet.

---

## 🧠 How to Explain to Interviewer in My Own Words
> “Custom Object Classes in FileNet store reusable business data without content.  
> They’re perfect for reference data like departments or branches that documents can link to.”

---

## 🏁 Summary
- **Custom Object** = Metadata holder, not a document.  
- Used for **lookup lists**, **configuration**, and **reusable information**.  
- Created under **Data Design → Classes → Custom Object**.  
- Helps keep business data centralized inside FileNet.  

---
