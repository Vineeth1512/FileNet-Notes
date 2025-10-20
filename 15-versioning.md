# 📝 FileNet ACCE – Versioning

Versioning in FileNet is a **powerful feature** that tracks document revisions, manages editing control, and preserves history.  

---

## 🧑‍💻 Technical Definition
Versioning maintains **multiple revisions of a document**, with each version tracked as a **separate state**.  
FileNet provides:

1. **Major Version** – Significant updates (final or approved documents).  
2. **Minor Version** – Draft or intermediate changes.  
3. **Check-in / Check-out** – Mechanism to prevent multiple users from editing simultaneously.  
4. **Cancel Check-out** – Discard changes without saving a new version.

Each document in a version-enabled Document Class can have **multiple versions**, and each version has a **status**.

---

## 📌 Document Status in FileNet
1. **Checked In**  
   - Document is **available for reading** by other users.  
   - No one can modify it until it is checked out.  
2. **Checked Out**  
   - Document is **locked for editing** by a user.  
   - Prevents concurrent changes.  
3. **Minor Version Checked In**  
   - When a **minor change** is saved.  
   - Updates the version number (e.g., 1.1 → 1.2).  
4. **Major Version Checked In**  
   - When a **significant change** is saved.  
   - Updates the version number (e.g., 1.0 → 2.0).  
5. **Cancelled Check-out**  
   - Discards all changes made during the check-out.  
   - Document **reverts to previous version**.

---

## ⚙️ Check-in / Check-out Process

### 1️⃣ Check-out
- Locks the document for editing.  
- Other users can only view, not edit.  
- Check-out can be **minor** or **major** depending on how changes will be saved.  

### 2️⃣ Editing
- Make your changes to the document or metadata.  
- Save locally or in FileNet depending on workflow.  

### 3️⃣ Check-in
- Save the changes back into FileNet as a **new version**.  
- Specify **major or minor version**.  
- Unlocks the document so others can edit.  

### 4️⃣ Cancel Check-out
- If edits are **not needed**, cancel check-out.  
- Document returns to its **last checked-in version**.  
- No new version is created.

---

## 🗣️ Simple English Definition
Think of versioning as **Google Docs with editing control**:  
- **Check-out** → You start editing, others can’t change it.  
- **Check-in** → You save changes, and it becomes a new version.  
- **Cancel check-out** → You discard your edits, no new version is saved.  

---

## 🎯 Purpose of Versioning with Check-in / Check-out
- Avoid conflicts when multiple users edit the same document.  
- Maintain **history of changes** with version numbers.  
- Allow users to **discard unwanted edits** (cancel check-out).  
- Support **approval workflows**, where drafts are revised and final versions are stored separately.

---

## 🔁 Real-Time Analogy
Imagine a **shared office document**:  
1. You take a **physical folder** from the filing cabinet (Check-out).  
2. You add notes or edits (Editing).  
3. You return it (Check-in) → now everyone can see the updated version.  
4. If you made a mistake, you throw your notes away (Cancel Check-out) → folder remains unchanged.

---

## 🌍 Real-World Scenario
A **bank contract document**:
1. Employee checks out the document to add a clause.  
2. Saves minor edits (1.1 → 1.2).  
3. Manager approves final version → major version checked in (1.2 → 2.0).  
4. If employee made a wrong edit, they cancel check-out → document stays at 1.1.  

This ensures **audit trail, compliance, and version integrity**.

---



## 🧾 Key Points for Interview
- Check-out locks the document for editing by one user.  
- Check-in creates a new version (major/minor).  
- Cancel check-out discards changes and preserves last version.  
- Versions allow **audit, history tracking, and rollback**.  
- Statuses: Checked Out, Checked In, Minor/Major Version, Cancelled Check-out.

---



## 💡 Real-Time Analogy (Simple)
- Checked Out → “I have the file on my desk for editing.”  
- Checked In → “I saved the updated file in the cabinet.”  
- Cancel Check-out → “I threw away my edits, nothing changed.”
---
# 📝 FileNet ACCE – Versioning

Versioning in FileNet tracks **all revisions of a document**, manages **editing control**, and preserves history.  

---

## 🧑‍💻 Technical Definition
Versioning maintains **multiple revisions of a document**, each with a **status** to indicate its workflow stage.  
FileNet uses these key concepts:

- **Major Version** – Significant change (e.g., final approved document)  
- **Minor Version** – Small edits or drafts  
- **Check-in / Check-out** – Control editing by locking/unlocking documents  
- **Cancel Check-out** – Discard changes without creating a new version  
- **Document Status** – Indicates the state of a version (Reserved, In Process, Released, Superseded)

---

## 📌 Document Status Definitions

| Status | Meaning |
|--------|---------|
| **Reserved** | The document is **checked out for editing** by a user but not yet saved as a new version. |
| **In Process** | The document is **being actively edited** or processed; changes are not finalized. |
| **Released** | The version is **finalized and available** for other users; can be major or minor. |
| **Superseded** | A **newer version exists**, so this version is outdated but retained for history. |

---



## 🗣️ Simple English Definition
Versioning in FileNet is like **Google Docs with editing control**:  

- **Check-out → Reserved**: You start editing; others can’t change it.  
- **Edit → In Process**: You are actively modifying the document.  
- **Check-in → Released**: Your changes are saved as a new version.  
- **Superseded**: Older versions are kept for history but a newer version exists.  
- **Cancel Check-out**: Discard edits, revert to the last released version.  

---

## 🎯 Purpose
- Prevent conflicts in multi-user environments.  
- Maintain **full history and audit trail** of changes.  
- Ensure compliance in regulated industries.  
- Allow rollback to previous versions if errors occur.  

---

## ⚙️ Steps in ACCE

1. Open **ACCE → Object Store → Browse**.  
2. Navigate to the document you want to version.  
3. Right-click → **Check Out** → Document status becomes **Reserved**.  
4. Edit content/metadata → Status is **In Process**.  
5. Right-click → **Check In** → Choose **Minor or Major Version** → Status becomes **Released**.  
6. If you want to discard changes → **Cancel Check-out** → Status returns to last **Released version**.  

---

## 🧾 Key Points for Interview
- **Statuses:** Reserved, In Process, Released, Superseded  
- Check-out locks document → Reserved  
- Editing → In Process  
- Check-in → Released  
- Older versions → Superseded  
- Cancel check-out → Revert to last Released version  
- Versioning ensures **audit trail, compliance, and rollback**  

---

## 🏁 Summary Table

| Action / Status | Description |
|-----------------|-------------|
| Reserved | Document checked out for editing |
| In Process | Actively editing the document |
| Released | Version finalized and available |
| Superseded | Old version replaced by newer version |
| Check-out | Lock document for editing |
| Check-in Minor | Save minor edits → Released |
| Check-in Major | Save major changes → Released |
| Cancel Check-out | Discard changes → Revert to last Released version |

