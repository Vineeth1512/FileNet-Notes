Here is the complete, simple, structured explanation of ROSTER in IBM FileNet Process Engine (PE) — with technical meaning, real-life analogy, purpose, and FileNet example.


---

🟦 ⭐ ROSTER — COMPLETE EXPLANATION (IBM FILENET PROCESS ENGINE)


---

1️⃣ TECHNICAL DEFINITION

A Roster in IBM FileNet Process Engine is a database table that stores the status, history, and metadata of all workflow instances created from a specific workflow definition.

Each workflow definition has one roster.

Roster = Where workflow instances are listed, tracked, and queried.


---

2️⃣ REAL-LIFE DEFINITION

A Roster is like an attendance or register book used to record every workflow instance — when it started, who is handling it, and what its status is.

Example:

A register for loan applications

A register for purchase orders

A register for employee onboarding cases


Each entry = one workflow instance.


---

3️⃣ WHAT IT IS (Simple Explanation)

Roster stores:

Workflow instance ID

Workflow definition name

Launch timestamp

Status (In Progress, Completed, Suspended)

Current step

Workflow data fields

Creator

Due dates & deadlines


Every time a workflow is launched:

A new entry is added to the Roster.


Roster helps in:

Monitoring

Reporting

Searching

Auditing



---

4️⃣ WHY WE USE ROSTERS (Purpose)

✔ To track all workflow instances

Like a list of all loan applications currently being processed.

✔ To report workflow progress

Managers can see:

How many workflows started today

How many completed

How many pending


✔ To search workflow instances

Find:

All workflows assigned to “John”

All workflows with Status = “Rejected”


✔ To audit workflow activity

View:

When the workflow started

Who worked on which step

When it finished


✔ For dashboard and analytics

Used by ICN dashboards, BAM, or custom reports.


---

5️⃣ IMPORTANT: ONE ROSTER PER WORKFLOW DEFINITION

✔ 1 workflow definition = 1 roster
✔ Multiple workflow instances → stored inside that roster
✔ Cannot share rosters across definitions

Example:

LoanApproval Workflow → LoanApprovalRoster

EmployeeOnboarding Workflow → EmployeeOnboardingRoster



---

6️⃣ WHAT IS THIS IN REAL LIFE?

📌 Real-Life Analogy: Register or Logbook

Imagine a school attendance register:

Each row = one student

Contains details → name, roll number, status (present/absent)


Similarly, a roster is a logbook of all workflow instances:

Each row = one workflow instance

Contains properties → who started it, where it is now



---

7️⃣ MATCHING FILENET EXAMPLE (Real-Time)

⭐ Scenario: Loan Approval Workflow

Workflow definition: LoanApprovalWF

PE automatically creates a roster:

LoanApprovalWF_Roster

Each time a customer applies for a loan,
a new workflow instance is created.

Example entries inside the roster:

Workflow ID	Customer	Amount	Current Step	Status

WF1001	John	50000	Verification	In Progress
WF1002	Smith	120000	Manager Approval	In Progress
WF1003	Asha	80000	Completed	Done
WF1004	Ravi	200000	Rejected	Completed


Roster allows:

✔ Search for all pending approvals
✔ Search all workflows for "John"
✔ Generate reports
✔ View performance metrics


---

8️⃣ ROSTER VS INBOX VS QUEUE

Concept	Meaning

Roster	Stores all workflow instances (history + metadata)
Queue (Step Queue)	Stores work items waiting to be processed
Inbox (User’s inbox)	Shows only items assigned to a specific user



---

9️⃣ FIELDS STORED IN ROSTER

A roster stores fields such as:

Workflow Number

Launch Date & Time

Current Queue Name

Status

Region ID

Initiating User

Deadline

Data fields used in workflow



---

🔟 SUPER SIMPLE SUMMARY

Concept	Meaning

Roster	Workflow instance table
Purpose	Track, search, audit workflow instances
Real life	Register/logbook of all applications
FileNet example	LoanApprovalWF_Roster



---

If you want next, I can explain:

✔ Component Queue

✔ Work Object vs Roster Element

✔ VWWorkObject fields

✔ How workflow instance is created in CE

✔ Workflow queues (Inboxes)

✔ Step processors

Just tell me “Next” or the topic name.
