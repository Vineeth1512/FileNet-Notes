# 🏭 FileNet – Factory Class

The **Factory class** in FileNet provides **static methods** to create or fetch instances of all major Content Engine objects such as **Connection**, **Domain**, **ObjectStore**, **Document**, **Folder**, and **CustomObject**.  
It acts like a **universal object creator** in the FileNet API.

---

## 🧑‍💻 Technical Definition
- The `Factory` class is part of the **FileNet Java API** (`com.filenet.api.core.factory` package).  
- It provides **static methods** to create, fetch, or instantiate FileNet objects.  
- It follows the **Factory Design Pattern** — a creational pattern used to create objects without exposing the instantiation logic.

**Example Methods:**
```java
Factory.Connection.getConnection();
Factory.Domain.fetchInstance();
Factory.ObjectStore.fetchInstance();
Factory.Document.createInstance();
Factory.Folder.createInstance();
Factory.CustomObject.createInstance();
```
---
# 🗣️ Simple English Definition

The **`Factory`** class helps you **create or fetch FileNet objects easily** — like a 🏭 *machine* that builds the objects you need (`Connection`, `Domain`, `Document`, etc.) instead of manually constructing them.

---

# 🎯 Purpose

- ⚙️ To **simplify the creation** of FileNet objects.  
- 🚫 To **avoid using constructors directly**, ensuring cleaner and safer code.  
- 🧩 To **ensure standard initialization** of objects within the FileNet environment.  
- 📦 To **fetch existing objects** from the Content Engine repository.
---
# ⚙️ Commonly Used Factory Methods

| Factory Method                                                | Purpose                                |
| ------------------------------------------------------------- | -------------------------------------- |
| `Factory.Connection.getConnection(URL)`                       | Creates a connection to Content Engine |
| `Factory.Domain.fetchInstance(Connection, null, null)`        | Fetches the current domain             |
| `Factory.ObjectStore.fetchInstance(Domain, name, null)`       | Retrieves the specified Object Store   |
| `Factory.Document.createInstance(ObjectStore, className)`     | Creates a new Document object          |
| `Factory.Folder.createInstance(ObjectStore, className)`       | Creates a new Folder                   |
| `Factory.CustomObject.createInstance(ObjectStore, className)` | Creates a new Custom Object            |
| `Factory.VersionSeries.fetchInstance(ObjectStore, id, null)`  | Fetches version history                |
| `Factory.SearchScope.createInstance(ObjectStore)`             | Used for performing searches           |
---
# 💡 Real-Time Analogy

Imagine a 🏭 **factory machine** in a company:

- You press different buttons to create different products — 🖊️ pens, 🧴 bottles, 📱 phones.  
- In **FileNet**, the `Factory` class works the same way — it can produce **Connections**, **Domains**, **Folders**, and **Documents** just by calling the right method.

---

# 🌍 Real-World Scenario

Let’s say you are building a **Java program** that uploads documents into FileNet:

1. 🔗 Use `Factory.Connection.getConnection()` to connect to the **Content Engine (CE)**.  
2. 🌐 Use `Factory.Domain.fetchInstance()` to get the **Domain**.  
3. 🗂️ Use `Factory.ObjectStore.fetchInstance()` to get the **Object Store**.  
4. 📄 Use `Factory.Document.createInstance()` to create a **new Document**.  
5. 💾 **Save and check in** the document.

---

✅ **In short:**  
The `Factory` class acts as your **FileNet object builder** — you just specify *what you want*, and it constructs it for you efficiently and consistently.
