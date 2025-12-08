Here is the complete, simple, structured explanation of Menus in IBM Content Navigator (ICN) — in the same style you prefer:

✔ Technical definition
✔ Real-life definition
✔ What it is
✔ Why we use it
✔ Types of menus
✔ Real-life analogy
✔ FileNet examples


---

🟦 ⭐ MENUS IN ICN — COMPLETE EXPLANATION


---

1️⃣ TECHNICAL DEFINITION

Menus in IBM Content Navigator are configurable sets of actions that appear in the user interface, allowing users to perform operations such as open, download, check-in, start workflow, or run custom actions.

Menus control what actions users see when they:

Right-click a document

Select a folder

View search results

Work inside Teamspaces



---

2️⃣ REAL-LIFE DEFINITION

Menus are like the options you get when you right-click on files in Windows (Open, Rename, Delete) or when you tap options on a mobile app (Share, Edit, Download).

They tell users what they are allowed to do.


---

3️⃣ WHAT MENUS ARE (Simple Explanation)

In ICN, menus are:

Lists of actions

Connected to desktops

Different for documents, folders, searches, workflows

Controlled by admin

Can include custom actions (JavaScript plugins)


When a user selects a document → menu shows all allowed actions.

Menus help control:

User capabilities

UI behavior

Available operations

Security (hide certain actions)



---

4️⃣ WHY WE USE MENUS (Purpose)

✔ To simplify UI

Only show actions that user needs.

✔ To enforce security

Hide actions user is not allowed to perform (delete, update, etc).

✔ To customize ICN

Create department-specific menus:

HR Menu

Finance Menu

Legal Menu


✔ To add custom actions

Actions like:

"Send to SAP"

"Generate Report"

"Start Custom Workflow"


✔ To avoid confusion

Users won’t see 50 unnecessary options.


---

5️⃣ TYPES OF MENUS IN ICN

ICN supports multiple menu types:


---

1️⃣ Context Menus (Right-Click Menus)

Appear when user selects or right-clicks:

Document

Folder

Search result

Teamspace item


Examples:

Open

Download

Properties

Delete

Start Workflow



---

2️⃣ Action Menus (Toolbar Menus)

Displayed at the top toolbar of ICN screen.

Examples:

Add Document

Create Folder

Search

Entry Template menus



---

3️⃣ Desktop Menus

Top header menus available across the desktop UI.

Examples:

Home

Browse

Work

Tools



---

4️⃣ Custom Menus (Added via Plugins)

Admins/developers can add custom menu actions using JavaScript plugin.

Examples:

"Send Email"

"Push to CRM"

"Validate Document"



---

6️⃣ WHAT IS THIS IN REAL LIFE?

📌 Real-Life Analogy: Right-Click Menu in Windows

When you right-click on a file, you see:

Open

Copy

Delete

Rename


If you're a normal user, you don’t see admin options.
If you're an admin, you see more options.

ICN menus work exactly the same.


---

7️⃣ MATCHING FILENET EXAMPLE (Real-Time)

⭐ Example: HR Desktop Menu

HR team needs only:

Open

View Properties

Download

Start Workflow

Add Document


Admin hides:

Delete

Check-Out

Change Security


Why?
HR users should not change security on employee files.


---

⭐ Example: Finance Desktop Menu

Finance team needs:

Start Invoice Approval Workflow

Add Document via Entry Template

View Versions


Admin hides:

Delete (to avoid mistakes)

Create Folder



---

⭐ Example: Add Custom Action

A company wants a menu option:

“Send to SAP”

Using a plugin, admin adds:

Custom JavaScript

Custom action button

Custom REST call


Now users see a new menu option: Right-click → Send to SAP


---

8️⃣ MENU VS ENTRY TEMPLATE VS DESKTOP

Feature	Menu	Entry Template	Desktop

Purpose	List of actions	Predefined upload form	Full UI layout
Used for	Operations	Document creation	User interface
Customized for	User/Document type	Class/Upload flow	Department roles


Menus define what users can DO,
Entry templates define how documents are CREATED,
Desktops define what users SEE.


---

9️⃣ SUPER SIMPLE SUMMARY

Concept	Meaning

Menu	List of actions available to user
Purpose	Control UI actions & permissions
Real life	Right-click options
FileNet example	Custom HR/Finance action menus



---

If you want next, I can explain:

✔ Custom Actions in ICN

✔ ICN Plugins

✔ Action vs Context Menu

✔ Feature Configuration in ICN

✔ How menus respect ACLs and security

Just say “Next” or give the topic.
