# 🟦 Create a Document in IBM Content Engine (Step-by-Step + Code)

## 📌 Objective
Create a document in IBM FileNet Content Engine programmatically using CE Java API.

---

## 🟦 Prerequisites
Before writing code you must:

- Install FileNet CE Java APIs  
- Have access to a FileNet domain  
- Know document class (ex: Document)  
- Know target folder path  

---

# 🟦 Steps to Create a Document

## Step 1️⃣ Connect to Content Engine
- Create an object store connection  
- Use username and password  
- Get object store instance  

---

## Step 2️⃣ Create a Document Object
- Use Factory.Document  
- Specify document class  
- Add properties  

---

## Step 3️⃣ Add Content (file, stream, text)
- Create ContentTransfer object  
- Attach stream or file  

---

## Step 4️⃣ Set Content Element List
- Add ContentTransfer into ContentElements  
- Assign to document  

---

## Step 5️⃣ Checkin the document
- Use document.checkin(AutoClassify)  

---

## Step 6️⃣ Save document into Object Store
- Use document.save(RefreshMode)  

---

## Step 7️⃣ File the document inside folder
- Create a new Folder filing  
- Save it  

---

# 🟦 Complete Example – Java Code

```java
import com.filenet.api.core.*;
import com.filenet.api.admin.*;
import com.filenet.api.property.*;
import com.filenet.api.impl.*;
import com.filenet.api.constants.*;
import java.io.*;

public class CreateDocumentExample {

    public static void main(String[] args) throws Exception {

        // Step 1: Connect to CE
        Connection connection = Factory.Connection.getConnection("http://localhost:9080/wsi/FNCEWS40MTOM");
        Subject subject = UserContext.createSubject("admin", "password", null);
        UserContext.get().pushSubject(subject);

        ObjectStore objectStore = Factory.ObjectStore.getInstance(connection, "OS1");

        // Step 2: Create Document Object
        Document document = Factory.Document.createInstance(objectStore, "Document");

        // Step 3: Add properties
        document.getProperties().putValue("DocumentTitle", "Sample Upload File");

        // Step 4: Add Content
        ContentTransfer ct = Factory.ContentTransfer.createInstance();
        FileInputStream file = new FileInputStream("C:/files/sample.pdf");

        ct.setCaptureSource(file);
        ct.set_ContentType("application/pdf");
        ct.set_RetrievalName("sample.pdf");

        ContentElementList cel = Factory.ContentElement.createList();
        cel.add(ct);
        document.set_ContentElements(cel);

        // Step 5: Checkin document
        document.checkin(AutoClassify.DO_NOT_AUTO_CLASSIFY, CheckinType.MAJOR_VERSION);

        // Step 6: Save Document
        document.save(RefreshMode.REFRESH);

        // Step 7: File into Folder
        Folder folder = Factory.Folder.fetchInstance(objectStore, "/UserDocs", null);
        ReferentialContainmentRelationship rcr = folder.file(document, AutoUniqueName.AUTO_UNIQUE, "sampleDoc", DefinesSet.DEFAULT);
        rcr.save(RefreshMode.REFRESH);
    }
}
