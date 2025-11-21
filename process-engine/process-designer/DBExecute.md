# DB Execute – FileNet Workflow Notes
 
## 1️⃣ What is DB Execute?
DB Execute step is used in FileNet workflow to **store workflow data into a database table** using a stored procedure.
 
- Workflow Datafields → Database Table  
- Calls DB2 / Oracle / SQL Server stored procedure  
- Used for integration, reporting, and data storage
 
---
 
## 2️⃣ Why We Use DB Execute?
- Save workflow data permanently in a database  
- Generate reports  
- Share workflow results with other systems  
- Integrate FileNet Workflow with external applications  
 
---
 
## 3️⃣ Step-1: Create DB Execute Connection (ACCE)
 
**Path:**  
`Administration → Workflow System → DB Execute Connections → New`
 
### ✔ Fill the Connection Details
| Field | Example |
|-------|---------|
| Connection Name | `FNOS-DB` |
| Database Type | `DB2` |
| Database Name | `FNOSDB` |
| Host Name | `172.16.xx.xx` |
| Port | `50000` |
| Username | `db2admin` |
| Password | `Admin@123` |
 
**Next → Validate → OK → Save**
 
---
 
## 4️⃣ Step-2: Verify Database in DB2 (Remote Server)
 
### Useful DB2 Commands:
```bash
db2 list db directory
db2 connect to FNOSDB
db2 list tables
db2 list tabels for schema FNADMIN
db2 disconnect FNOSDB
```
## Step-3 Create a Database Table
```
CREATE TABLE FNADMIN.STUDENT_INFO(
    STUDENT_ID INTEGER,
    STUDENT_NAME VARCHAR(50),
    BRANCH VARCHAR(20)
);
```

## Step-4 Create Stored Procedure

```
CREATE PROCEDURE FNADMIN.P_INSERT_STUDENT
(
    IN STUDENT_ID INTEGER,
    IN STUDENT_NAME VARCHAR(50),
    IN BRANCH VARCHAR(20)
)
LANGUAGE SQL
MODIFIES SQL DATA
BEGIN
    INSERT INTO FNADMIN.STUDENT_INFO
    VALUES (STUDENT_ID, STUDENT_NAME, BRANCH);
END
```


## 7️⃣ Step-5: Workflow Design in Process Designer
 
### ✔ Create Datafields
- **StudentID**
- **StudentName**
- **Branch**
 
### ✔ Configure DB Execute Step
 
| Parameter              | Value                        |
|------------------------|------------------------------|
| **DB Connection Alias** | FNOS-DB                      |
| **Procedure Name**      | FNADMIN.P_INSERT_STUDENT     |
| **Parameter Mapping**   | Map datafields to procedure inputs |
 
Then perform:
- **Validate**
- **Save**
- **Transfer**
- **Launch**
 
---
 
## 8️⃣ Step-6: Validate Data in DB2
 
Run the following commands:
 
```bash
db2 connect to FNOSDB
db2 "select * from FNADMIN.STUDENT_INFO"
