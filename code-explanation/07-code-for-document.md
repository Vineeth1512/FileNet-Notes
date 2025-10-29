# 📄 FileNet API – Document Creation using Factory Class


```java
Document document = Factory.Document.createInstance(objectStore, CUSTOM_CLASS_NAME);

```


---

## 🧩 1. What It Is

This line creates a new instance of a **Document object** in the **FileNet Content Engine (CE)** using the **Factory class**.  
The document will belong to a specific **custom document class** defined in the Object Store.

---

## 🧠 2. Purpose

The purpose of this line is to **instantiate (create)** a new FileNet Document object before saving it to the Object Store.  
You can think of it as **creating an empty document shell in memory** — you can later set its properties, attach content, and then save it to the repository.

---

## 🏗️ 3. Syntax Breakdown

```java
Document document = Factory.Document.createInstance(objectStore, CUSTOM_CLASS_NAME);

```

| Component           | Type                   | Description                                                                                                            |
| ------------------- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `Factory`           | **Class**              | A utility class provided by FileNet API to create or fetch instances of CE objects like Document, Folder, Domain, etc. |
| `Document`          | **Interface**          | Represents a FileNet document object stored in the Object Store.                                                       |
| `createInstance()`  | **Static Method**      | Used to create a new instance of a specified class within a given Object Store.                                        |
| `objectStore`       | **ObjectStore Object** | The repository where the document will be created and stored.                                                          |
| `CUSTOM_CLASS_NAME` | **String**             | The name of the custom document class (e.g., `"MyCustomDocumentClass"`) under which the document will be created.      |

---
#### ⚙️ 4. Parameters

| Parameter             | Type        | Description                                                                                             |
| --------------------- | ----------- | ------------------------------------------------------------------------------------------------------- |
| **objectStore**       | ObjectStore | Specifies the Object Store where the document will be created.                                          |
| **CUSTOM_CLASS_NAME** | String      | Specifies the document class name (custom or base class). Example: `"Document"` or `"InvoiceDocument"`. |

