
---

🧩 dojo/dom

📘 What is dojo/dom?

✅ Definition

dojo/dom is a Dojo core module used to access and work with existing HTML elements in the DOM using their ID.

👉 In short: it helps us find HTML elements easily.


---

🤔 Why do we use dojo/dom?

Without dojo/dom:

Use document.getElementById()

More typing

Less readable

Browser issues (older apps)


With dojo/dom:

Short and clean syntax

Consistent behavior

Easy integration with other Dojo modules



---

🏠 Real-Life Analogy

🏷 Address System

House → HTML element

Address → Element ID

Postman → dojo/dom


👉 dojo/dom finds the exact house using the address.


---

📦 Importing dojo/dom

require(["dojo/dom"], function(dom){
    // use dom here
});


---

🔧 Common Methods in dojo/dom


---

1️⃣ byId()

✅ What it does

Returns an HTML element using its ID.

Syntax

dom.byId(id);

Example

require(["dojo/dom"], function(dom){
    var node = dom.byId("title");
    node.innerHTML = "Welcome to Dojo";
});

📌 Same as document.getElementById("title")


---

🔍 Real-Time Example

Scenario: Change text of a label

require(["dojo/dom"], function(dom){
    dom.byId("status").innerHTML = "Login Successful";
});


---

🧠 When do we use dojo/dom?

Access existing HTML elements

Read or change text

Combine with events (dojo/on)

Combine with dom-construct



---

🔄 dojo/dom vs dojo/dom-construct

Feature	dojo/dom	dojo/dom-construct

Purpose	Access elements	Create/remove elements
Works on	Existing DOM	Dynamic DOM
Common method	byId()	create()
Usage	Read / update	Build / destroy



---

🧪 Interview One-Liner

> “dojo/dom is a Dojo core module used to access existing DOM elements efficiently using their IDs.”




---

✅ Summary (Easy to Remember)

dojo/dom = find elements

Works only on existing HTML

Simple and clean

Often used with dojo/on and dom-construct



---

⭐ Memory Tip

> Find → dojo/dom
Build → dom-construct




---

If you want, next I can give:

dojo/on (same markdown style)

dojo/query

dojo/dom-style

Full Dojo DOM flow diagram explanation


Just say Next 😊
