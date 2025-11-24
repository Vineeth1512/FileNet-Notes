

IBM FileNet Process Engine (PE) – Java API Notes

1. What is Process Engine (PE)?

Process Engine (PE) is the workflow engine of IBM FileNet responsible for:

Running business workflows

Assigning work items

Managing queues, rosters, steps

Executing automated activities

Integrating with external systems


Content Engine (CE) → stores documents
Process Engine (PE) → runs workflows


---

2. Build PE Java API Development Environment (Eclipse)

Step-1: Create Java Project

Open Eclipse

File → New → Java Project

Project Name: FilenetPEClient

Use JDK 8 or 11



---

3. Load All Required JAR Files

Find these JARs in:

<Process_Engine_install>/lib/

Mandatory JAR Files

JAR Name	Purpose

pe.jar	Core PE API
vwapi.jar	Workflow operations
jace.jar	Remote communication
log4j.jar	Logging
stax-api.jar	XML handling
xercesImpl.jar	XML parsing


How to Add JAR Files

Eclipse →
Right-click Project → Build Path → Configure Build Path → Add External JARs


---

4. Java Program – Create PE Session (VWSession)

This program connects to the Process Engine.

Code: Create VWSession

import com.filenet.api.exception.EngineRuntimeException;
import filenet.vw.api.VWException;
import filenet.vw.api.VWSession;

public class CreatePESession {

    public static void main(String[] args) {

        String peConnectionPoint = "P8ConnPt"; 
        String username = "p8admin";
        String password = "password";

        try {
            VWSession session = new VWSession();

            System.out.println("Connecting to Process Engine...");

            session.setBootstrapCEURI("http://localhost:9080/wsi/FNCEWS40MTOM");
            session.logon(username, password, peConnectionPoint);

            System.out.println("PE Session Established Successfully!");
            System.out.println("User: " + session.getCurrentUser());

            session.logoff();
        } 
        catch (VWException e) {
            e.printStackTrace();
        }
    }
}

Important Parameters

Parameter	Details

P8ConnPt	PE Connection Point
BootstrapCEURI	CE web service URL
username/password	Authentication credentials



---

5. Java Program – Launch a Workflow

This program launches a PE workflow (example: StudentApproval).

Code: Launch Workflow

import filenet.vw.api.*;

public class LaunchWorkflow {

    public static void main(String[] args) {

        String peConnectionPoint = "P8ConnPt";
        String workflowName = "StudentApproval";

        try {
            VWSession session = new VWSession();
            session.setBootstrapCEURI("http://localhost:9080/wsi/FNCEWS40MTOM");
            session.logon("p8admin", "password", peConnectionPoint);

            // Fetch workflow definition
            VWWorkflowDefinition wfDef = session.getWorkflowDefinition(workflowName);

            // Create workflow instance
            VWWorkflow workflow = wfDef.createWorkflow();

            // Set workflow data fields
            workflow.setParameterValue("StudentName", "Vineeth");
            workflow.setParameterValue("StudentID", "101");

            // Launch workflow
            workflow.launch();
            System.out.println("Workflow Launched Successfully!");

            session.logoff();
        }
        catch (Exception e) {
            e.printStackTrace();
        }
    }
}


---

6. What You Need to Know Before Coding

Workflow Name in Process Designer

Connection Point

Data fields defined in workflow

User credentials

Correct CE URI (MTOM/SOAP)



---

7. Expected Output

Running both programs will show:

Connecting to Process Engine...
PE Session Established Successfully!
Workflow Launched Successfully!


---

If you want, I can also create:

✅ A downloadable .md file
✅ Notes for Queue operations, Step completion, Search in roster, etc.
Just tell me!
