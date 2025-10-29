# 📂 FileNet – Attaching Content to a Document

---

## 🧩 1. What It Is

This code block is used to **attach the actual file content** (like PDF, DOC, or image) to a **FileNet document** by creating a `ContentTransfer` object.  
It prepares the **binary data stream** so it can be uploaded to the **FileNet Object Store**.

A `ContentTransfer` represents **one file** associated with a FileNet document.

---

## 🧠 2. Purpose

The purpose is to:

1. **Create a holder** for the file’s content.  
2. **Stream the data** from the local file system into FileNet.  
3. **Define** the content type and retrieval name for the file.

Without this step, the document would only have **metadata (properties)** but **no actual content file** stored in the repository.

---
#### 🏗️ 3. Syntax Breakdown 

| Component                 | Type              | Description                                                           |
| ------------------------- | ----------------- | --------------------------------------------------------------------- |
| `Factory.ContentTransfer` | **Class**         | A utility class used to create instances of `ContentTransfer`.        |
| `createInstance()`        | **Static Method** | Creates a new, empty `ContentTransfer` object.                        |
| `setCaptureSource()`      | **Method**        | Sets the source InputStream to capture the content from a local file. |
| `set_ContentType()`       | **Method**        | Sets the file’s MIME type (like `"application/pdf"`).                 |
| `set_RetrievalName()`     | **Method**        | Sets the file’s display name when viewed or downloaded from FileNet.  |

---
#### ⚙️ 4. Parameters

| Parameter         | Type              | Description                                          |
| ----------------- | ----------------- | ---------------------------------------------------- |
| `fileInputStream` | `FileInputStream` | Reads the binary data of the local file.             |
| `mimeType`        | `String`          | Specifies the file type (e.g., `"application/pdf"`). |
| `file.getName()`  | `String`          | Gives the file name to be shown in FileNet.          |

---
