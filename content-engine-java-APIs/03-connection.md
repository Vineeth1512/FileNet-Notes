# 🔌 FileNet – Connection Interface

The **`Connection` interface** in FileNet Content Engine (CE) represents the **link between your Java application and the Content Engine server**.  
It is the **first step** in communicating with FileNet — before you can access any domain, object store, or document.

---

## 🧑‍💻 Technical Definition
- The **`Connection` interface** belongs to the **`com.filenet.api.core`** package.  
- It is used to **create a client connection** to the FileNet Content Engine web service.  
- Implemented using the **Factory pattern** via `Factory.Connection.getConnection()`.  
- Once a `Connection` object is created, it is used with `UserContext` and `Subject` for **authentication**.

**Syntax Example:**
```java
import com.filenet.api.core.Connection;
import com.filenet.api.core.Factory;

Connection conn = Factory.Connection.getConnection("http://servername:port/wsi/FNCEWS40MTOM/");

---

