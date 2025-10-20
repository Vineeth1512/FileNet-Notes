

# 📄 FileNet CreateDocument Code – Detailed Explanation

## 1️⃣ Connection

### Type
**Class:** `com.filenet.api.core.Connection`

---

### Purpose
Represents a connection to the **FileNet Content Engine (CE)**.

---

### Why We Use
A `Connection` object is **required to communicate with the Content Engine**.  
Without it, we cannot fetch:
- **Domain**
- **ObjectStore**
- **Documents**

---

### Parameters
| Parameter | Description |
|------------|--------------|
| **URL** | The CE web service URL. Example: `http://servername:port/wsi/FNCEWS40MTOM/` |

---

### Common Methods
| Method | Description |
|---------|--------------|
| `getConnection(String url)` | Static factory method to obtain a `Connection` instance. |
| `getSubject()` | Returns the `Subject` associated with this connection. |

---

### 💡 Analogy
Think of `Connection` as **opening the door to the FileNet server** — it’s the first step before accessing any resource inside.
---

## 2️⃣ Subject

### Code

```java
Subject subject = UserContext.createSubject(connection, USERNAME, PASSWORD, null);
UserContext.get().pushSubject(subject);
```

### Type

**Class:** `javax.security.auth.Subject`

### Purpose

Represents user credentials and the security context used for authentication in FileNet.

### Why We Use

The Content Engine (CE) API requires authentication before performing any operation. The `Subject` ensures that actions are executed under a valid user session.

### Parameters

| Parameter  | Description                               |
| ---------- | ----------------------------------------- |
| connection | The active Connection object.             |
| USERNAME   | User ID for Content Engine login.         |
| PASSWORD   | Password for the CE user.                 |
| null       | Optional JAAS login module configuration. |

### Common Methods

| Method                 | Description                                |
| ---------------------- | ------------------------------------------ |
| pushSubject(Subject s) | Authenticates and starts the user session. |
| popSubject()           | Ends the authenticated session.            |

### 💡 Analogy

Think of `Subject` as your ID card, checked by the security guard (`UserContext`) before allowing you into the FileNet system.

---

## 3️⃣ Domain

### Code

```java
Domain domain = Factory.Domain.fetchInstance(connection, null, null);
```

### Type

**Class:** `com.filenet.api.core.Domain`

### Purpose

Top-level container for ObjectStores, Users, and Groups.

### Why We Use

All ObjectStores exist inside a Domain; we cannot access ObjectStores without a Domain.

### Parameters in `fetchInstance`

| Parameter  | Description                                        |
| ---------- | -------------------------------------------------- |
| connection | Active connection to Content Engine                |
| name       | Domain name (`null` = default domain)              |
| null       | Optional property filter (use `null` to fetch all) |

### Common Methods

| Method                    | Description                      |
| ------------------------- | -------------------------------- |
| get_ObjectStores()        | Fetch all ObjectStores in domain |
| get_Users()               | Get all users                    |
| get_Groups()              | Get all groups                   |
| refresh(RefreshMode mode) | Refresh domain properties        |

### 💡 Analogy

Think of a `Domain` as a building containing rooms (ObjectStores) and people (Users/Groups).

---

## 4️⃣ ObjectStore

### Code

```java
ObjectStore objectStore = Factory.ObjectStore.fetchInstance(domain, OBJECTSTORE, null);
```

### Type

**Class:** `com.filenet.api.core.ObjectStore`

### Purpose

Repository where documents, folders, and custom objects are stored.

### Why We Use

Without an ObjectStore, we cannot create or fetch documents.

### Parameters in `fetchInstance`

| Parameter | Description              |
| --------- | ------------------------ |
| domain    | Parent Domain            |
| name      | ObjectStore name         |
| null      | Optional property filter |

### Common Methods

| Method              | Description                     |
| ------------------- | ------------------------------- |
| get_DocClasses()    | Fetch all document classes      |
| get_FolderClasses() | Fetch all folder classes        |
| get_CustomClasses() | Fetch all custom object classes |
| get_Properties()    | Fetch ObjectStore metadata      |

### 💡 Analogy

Like a room inside a building, storing files (documents).

---

## 5️⃣ Document

### Code

```java
Document document = Factory.Document.createInstance(objectStore, CUSTOMCLASSNAME);
Properties properties = document.getProperties();
```

### Type

**Class:** `com.filenet.api.core.Document`

### Purpose

Represents a document object in FileNet.

### Why We Use

We create documents, set metadata, and file them.

### Parameters in `createInstance`

| Parameter   | Description                           |
| ----------- | ------------------------------------- |
| objectStore | The ObjectStore to create document in |
| className   | Document class name (from ACCE)       |

### Common Methods

| Method                 | Description                  |
| ---------------------- | ---------------------------- |
| getProperties()        | Get document metadata        |
| save(RefreshMode mode) | Save document to ObjectStore |
| checkOut()/checkIn()   | Versioning operations        |

### 💡 Analogy

Like a paper file in a cabinet (ObjectStore room).

---

## 6️⃣ Properties

### Code

```java
properties.putValue("DocumentTitle", "Suraj Student Document");
```

### Type

**Class:** `com.filenet.api.property.Properties`

### Purpose

Holds document metadata fields.

### Why We Use

To assign values like ID, Name, Branch, Date of Birth.

### Parameters in `putValue`

| Parameter    | Description                  |
| ------------ | ---------------------------- |
| propertyName | Field name in document class |
| value        | Value to set                 |

### Common Methods

| Method     | Description        |
| ---------- | ------------------ |
| putValue() | Set a property     |
| getValue() | Get property value |

### 💡 Analogy

Like labels on the paper file.

---

## 7️⃣ Folder

### Code

```java
Folder folder = Factory.Folder.fetchInstance(objectStore, FOLDER_PATH, null);
```

### Type

**Class:** `com.filenet.api.core.Folder`

### Purpose

Container to organize documents.

### Why We Use

Filing documents into a folder is mandatory for organization.

### Parameters in `fetchInstance`

| Parameter   | Description              |
| ----------- | ------------------------ |
| objectStore | Parent ObjectStore       |
| folderPath  | Folder path              |
| null        | Optional property filter |

### Common Methods

| Method                                                                                | Description     |
| ------------------------------------------------------------------------------------- | --------------- |
| get_FolderName()                                                                      | Get folder name |
| file(Document doc, AutoUniqueName auto, Object template, DefineSecurityParentage sec) | File a document |

### 💡 Analogy

Like a cabinet inside a room.

---

## 8️⃣ ReferentialContainmentRelationship

### Code

```java
ReferentialContainmentRelationship rcr = folder.file(document, AutoUniqueName.NOT_AUTO_UNIQUE, null, DefineSecurityParentage.DO_NOT_DEFINE_SECURITY_PARENTAGE);
rcr.save(RefreshMode.REFRESH);
```

### Type

**Class:** `com.filenet.api.core.ReferentialContainmentRelationship`

### Purpose

Represents the relationship between a folder and a document.

### Why We Use

Files the document in the folder programmatically.

### Parameters in `file`

| Parameter               | Description                 |
| ----------------------- | --------------------------- |
| document                | Document to file            |
| AutoUniqueName          | Handle naming conflicts     |
| null                    | Optional template           |
| DefineSecurityParentage | Folder security inheritance |

### 💡 Analogy

Like attaching a paper file to a cabinet drawer.

---

## 9️⃣ RefreshMode

### Code Example

```java
document.save(RefreshMode.REFRESH);
```

### Type

**Enum:** `com.filenet.api.constants.RefreshMode`

### Purpose

Controls how object is updated in CE and local memory.

### Values

| Value      | Description                                           |
| ---------- | ----------------------------------------------------- |
| REFRESH    | Updates the object in CE and refreshes local instance |
| NO_REFRESH | Save object without refreshing local copy             |

### 💡 Analogy

Like making sure the copy in the filing cabinet matches your local copy.



