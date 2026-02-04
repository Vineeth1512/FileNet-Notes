# 📌 Creating a Desktop in IBM Content Navigator (ICN)

A Desktop in ICN defines what users can see and access after login.  
It controls repositories, menus, features, appearance, and plug-ins.

Follow the steps below to create and configure a new Desktop.

---

## ✅ Step-by-Step Process

### **Step 1 – Open ICN Admin Desktop**
1. Login to **IBM Content Navigator** with admin credentials.
2. Open **Admin Desktop**.
3. From the left navigation panel, click on **Desktops**.
4. Click on **New Desktop**.

---

## **Step 2 – Configure General Details**

Under the **General** tab, provide the basic information:

| Field | Description |
|------|-------------|
| **Name** | Display name of the desktop |
| **ID** | Unique identifier (no spaces) |
| **Description** | Optional description of the desktop |

Example:

- Name: VK_Desktop
- ID: VKDESKTOP
- Description: Desktop for FileNet Users

  ---
  
---

## **Step 3 – Configure Authentication**

1. Scroll to the **Authentication** section.
2. Select the default repository for login.

Example:

Repository: VKMFNOS


This repository will be used for user authentication.

---

## **Step 4 – Enable Required Plug-ins**

Under the **Plug-ins** section:

- Select the plug-ins that should be enabled for this desktop.
- Enable only the required custom or system plug-ins.

✔ *Select the deployed plug-ins to enable for use with this desktop.*

---

## **Step 5 – Attach Repository**

1. Go to the **Repositories** tab.
2. Select the repository created earlier (e.g., `VKM_FNOS`).
3. Add it to the desktop.

This ensures users can access documents from the repository.

---

## **Step 6 – Configure Appearance**

In the **Appearance** tab, you can customize:

- Desktop title  
- Theme  
- Logo  
- Color scheme  

This allows branding and UI customization.

Example:
Title: VKM FileNet Desktop

---

## **Step 7 – Configure Layout (Features)**

1. Open the **Layout** tab.
2. Add required features such as:

- Browse  
- Search  
- Favorites  
- Work  
- Teamspaces  

👉 These features will appear in the navigation bar (sidebar) for users.

---

## **Step 8 – Configure Menus**

In the **Menus** tab:

- Assign custom or default menus for:
  - Document actions  
  - Folder actions  
  - Search results  
  - Context menus  

This controls what actions users can perform.

---

## 🎯 Final Step – Save Desktop

After completing all configurations:

- Click **Save and Close**

---

# 🎉 Result

Your new ICN Desktop is now successfully created and ready for users!

Users can access it using the desktop URL:

http://<server>:<port>/navigator?desktop=VKDESKTOP


