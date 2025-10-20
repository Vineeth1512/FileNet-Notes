# 🔍 FileNet ACCE – Search

Search in FileNet allows users to **find documents, folders, and custom objects** in an Object Store using **metadata properties, filters, or full-text content**.

---

## 🧑‍💻 Technical Definition
**Search** in FileNet ACCE enables **retrieval of objects** stored in an Object Store.  
It supports:

1. **Simple Search** – Search by a single property or text.  
2. **Advanced Search** – Search using multiple properties, conditions, or Boolean logic (AND, OR, NOT).  
3. **Full-Text Search** – Search inside document content (PDF, Word, etc.) if content indexing is enabled.  
4. **Saved Queries** – Predefined search queries for repeated use.

---

## 🗣️ Simple English Definition
Searching in FileNet is like **Google search for your office documents**.  
- You can search by **document name, type, or any metadata property**.  
- You can also search **inside the document content** if full-text indexing is enabled.

---

## 🎯 Purpose
- Quickly **find specific documents** or objects without manually browsing folders.  
- Supports **audit and compliance** by retrieving required documents.  
- Enables **workflow automation** by locating documents for processing.  
- Improves efficiency in large Object Stores with thousands of documents.

---

## 🔁 Why We Use Search
- Manually browsing folders is slow and inefficient.  
- Metadata or full-text search allows **accurate and fast retrieval**.  
- Critical in **regulated environments** (finance, healthcare) for audits.

---

## ⚙️ Types of Search in FileNet

| Type | Description |
|------|-------------|
| Simple Search | Search using a single property, e.g., “CustomerName = Vineeth” |
| Advanced Search | Use multiple properties with conditions and Boolean operators |
| Full-Text Search | Search within document content, requires indexing |
| Saved Queries | Predefined reusable queries for common searches |

---

## 💡 Real-Time Analogy
Think of FileNet search as **using a search bar in Google Drive**:  
- Enter keywords → find the file.  
- Use filters → find files by owner, date, or folder.  
- Full-text search → search inside PDFs or Word documents.  

---

## 🌍 Real-World Scenario
- A **law firm** needs all contracts for “Client A” signed in the last year.  
- Using **Advanced Search**, they filter by:
  - ClientName = Client A  
  - DocumentClass = Contract  
  - DateSigned ≥ 01-Jan-2024  
- The system quickly returns all matching documents.  

---

## ⚙️ Steps to Search in ACCE

### 1️⃣ Simple Search
1. Open **ACCE → Object Store → Search**.  
2. Select **Simple Search**.  
3. Enter a **property value** (e.g., CustomerName = Vineeth).  
4. Click **Search** → Results are displayed.

### 2️⃣ Advanced Search
1. Open **ACCE → Object Store → Search → Advanced Search**.  
2. Add multiple **criteria** (properties + conditions).  
3. Use **AND / OR / NOT** for complex filtering.  
4. Click **Search** → Results are displayed.

### 3️⃣ Full-Text Search
1. Ensure **Content Engine indexing** is enabled for full-text.  
2. Enter keywords to search **inside document content**.  
3. Click **Search** → Matching documents appear.  

### 4️⃣ Saved Queries
1. After creating a search, click **Save Query**.  
2. Give it a **name** → accessible later under Saved Queries.  

---

## 🗣️ How to Explain in Interview (Own Words)
> “Search in FileNet allows us to quickly find documents and objects based on properties or content.  
> Advanced search supports multiple conditions, full-text search looks inside documents, and saved queries make repeated searches easier.”

---

## 🧾 Key Points for Interview
- Types: **Simple, Advanced, Full-Text, Saved Queries**  
- Search by **metadata properties** or **content**.  
- Full-text search requires **indexing**.  
- Essential for **document retrieval, workflow, and audits**.  
- Saved queries improve efficiency for **repeated searches**.

---

## 🏁 Summary Table

| Search Type | Purpose | Example |
|-------------|---------|---------|
| Simple | Search using one property | CustomerName = Vineeth |
| Advanced | Multiple properties and conditions | CustomerName = Vineeth AND DateSigned > 01-Jan-2024 |
| Full-Text | Search inside document content | Keyword = “Contract” in PDFs |
| Saved Queries | Predefined queries | “All invoices for 2024” |
