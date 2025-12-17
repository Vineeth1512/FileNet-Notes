

---

# 🧩 dojo/dom-class (With Parameters Explained)

📘 What is dojo/dom-class?

✅ Definition

dojo/dom-class is a Dojo module used to add, remove, toggle, replace, or check CSS classes on HTML elements dynamically.

👉 It works with CSS classes, not inline styles.


---

🤔 Why do we use dojo/dom-class?

Without dom-class:

Use element.className

Complex string operations

Hard to maintain


With dom-class:

Clean API

Safe class handling

Easy UI state control



---

🏠 Real-Life Analogy

🏷️ Sticker on a Box

Box → HTML element

Sticker → CSS class

Adding/removing sticker → dom-class



---

📦 Importing Module

require(["dojo/dom-class"], function(domClass){
    // use domClass
});


---

🔧 Methods in dojo/dom-class


---

1️⃣ add()

✅ Purpose

Adds a CSS class to an element.

🔹 Syntax

domClass.add(node, className);


---

🔍 Parameters Explained

Parameter	Meaning	Example

node	Target element	"box"
className	Class to add	"active"



---

🧪 Example

domClass.add("box", "active");

📌 Adds .active class to element with ID box


---

2️⃣ remove()

✅ Purpose

Removes a CSS class from an element.

🔹 Syntax

domClass.remove(node, className);


---

🔍 Parameters Explained

Parameter	Meaning

node	Element
className	Class to remove



---

🧪 Example

domClass.remove("box", "active");


---

3️⃣ toggle()

✅ Purpose

Adds class if not present, removes if present.

🔹 Syntax

domClass.toggle(node, className);


---

🧪 Example

domClass.toggle("box", "highlight");

📌 Used for show/hide, expand/collapse


---

4️⃣ contains()

✅ Purpose

Checks whether an element has a specific class.

🔹 Syntax

domClass.contains(node, className);


---

🔍 Return Value

true → class exists

false → class not exists



---

🧪 Example

if(domClass.contains("box", "active")){
    console.log("Box is active");
}


---

5️⃣ replace()

✅ Purpose

Replaces one class with another.

🔹 Syntax

domClass.replace(node, addClass, removeClass);


---

🔍 Parameters Explained

Parameter	Meaning

node	Element
addClass	New class
removeClass	Old class



---

🧪 Example

domClass.replace("box", "open", "closed");

📌 Removes closed, adds open


---

🔄 Multiple Classes Support

You can pass multiple classes (space-separated).

domClass.add("box", "active highlight");


---

🔄 dom-style vs dom-class

Feature	dom-style	dom-class

Works with	Inline styles	CSS classes
Best for	Dynamic values	UI states
Reusability	Low	High



---

🧠 When to use dojo/dom-class?

Toggle UI states

Active / inactive

Error / success messages

Show / hide via CSS



---

🧪 Interview One-Liner

> “dojo/dom-class is used to dynamically manage CSS classes on DOM elements, enabling clean and maintainable UI state changes.”




---

✅ Summary (Remember This)

add() → add class

remove() → remove class

toggle() → switch class

contains() → check class

replace() → change class



---

⭐ Memory Trick

> Style value → dom-style
Style state → dom-class




---

If you want next (same deep level):

dojo/on (events + parameters)

dojo/parser

Full Dojo DOM flow (end-to-end)

Interview Q&A on Dojo DOM modules


Just say Next 😊
