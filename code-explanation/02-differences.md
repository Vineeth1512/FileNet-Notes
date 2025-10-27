####  ⚖️ 🔍 Difference Between RefreshMode.REFRESH and RefreshMode.NO_REFRESH

| Feature               | `RefreshMode.REFRESH`                           | `RefreshMode.NO_REFRESH`                  |
| --------------------- | ----------------------------------------------- | ----------------------------------------- |
| **Meaning**           | Saves object and reloads it from server         | Saves object only, no reload              |
| **Server Call Count** | 2 calls (save + refresh)                        | 1 call (save only)                        |
| **Performance**       | Slower (extra round-trip)                       | Faster (less network traffic)             |
| **Data Accuracy**     | Up-to-date with latest system fields            | May contain stale or incomplete info      |
| **Common Use**        | Create new documents or need updated properties | Bulk updates or when refresh not needed   |
| **Example Use Case**  | Create Document → Need new GUID                 | Update metadata for 100 documents in loop |

---

#### ⚖️ Difference Between NOT_AUTO_UNIQUE and AUTO_UNIQUE
| Feature                        | `NOT_AUTO_UNIQUE`                | `AUTO_UNIQUE`                         |
| ------------------------------ | -------------------------------- | ------------------------------------- |
| **Meaning**                    | Do not auto-generate unique name | Auto-generate unique name             |
| **Behavior on Duplicate Name** | Throws exception                 | Creates new name automatically        |
| **Control**                    | Manual name control              | FileNet handles naming                |
| **Performance**                | Slightly faster (no extra check) | Slight overhead (FileNet adds suffix) |
| **Use Case**                   | Strict naming policies           | Bulk uploads or relaxed naming        |
| **Analogy**                    | “Replace or stop” in Windows     | “Save as Document(1)” in Windows      |
---
#### ⚖️ Difference Between DO_NOT_DEFINE_SECURITY_PARENTAGE and DEFINE_SECURITY_PARENTAGE

| Feature              | `DO_NOT_DEFINE_SECURITY_PARENTAGE` | `DEFINE_SECURITY_PARENTAGE`                   |
| -------------------- | ---------------------------------- | --------------------------------------------- |
| **Meaning**          | Keep document’s own security       | Inherit folder’s security                     |
| **Behavior**         | Retains original ACLs              | Copies folder’s ACLs                          |
| **Security Control** | Document-level                     | Folder-level                                  |
| **Use Case**         | Sensitive, custom-secured files    | Team-shared or general folders                |
| **Example**          | HR file that should not be shared  | Project files for all team members            |
| **Result**           | Document permissions unchanged     | Document inherits parent folder’s permissions |

---

#### ⚖️ Difference Between DO_NOT_AUTO_CLASSIFY and AUTO_CLASSIFY

| Feature                      | `DO_NOT_AUTO_CLASSIFY`  | `AUTO_CLASSIFY`                  |
| ---------------------------- | ----------------------- | -------------------------------- |
| **Automatic classification** | ❌ Disabled              | ✅ Enabled                        |
| **Who decides the class?**   | Developer manually      | FileNet CE automatically         |
| **Property auto-fill**       | ❌ No                    | ✅ Yes (based on templates/rules) |
| **Use Case**                 | When you know the class | When CE should infer class       |
| **Example**                  | `"Document"`            | `null` (let CE decide)           |

