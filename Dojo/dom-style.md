

---

🎨 dojo/dom-style (With Parameters Explained)

📘 What is dojo/dom-style?

✅ Definition

dojo/dom-style is a Dojo module used to get or set CSS style properties of DOM elements dynamically.


---

📦 Importing Module

require(["dojo/dom-style"], function(domStyle){
    // use domStyle
});


---

🔧 Method 1: domStyle.set()

✅ Purpose

Used to apply CSS styles to an element.


---

🔹 Syntax (Single Style)

domStyle.set(node, property, value);


---

🔍 Parameters Explained

Parameter	What it is	What it accepts	Why we need it

node	Target element	Element ID / DOM node	Which element to style
property	CSS property	String ("color")	Which style to change
value	CSS value	String / Number	New style value



---

🧪 Example (Single Style)

domStyle.set("box", "backgroundColor", "yellow");

✔ node → "box"
✔ property → "backgroundColor"
✔ value → "yellow"


---

🔹 Syntax (Multiple Styles)

domStyle.set(node, stylesObject);


---

🔍 Parameters Explained

Parameter	Meaning

node	Element to style
stylesObject	Object containing multiple CSS properties



---

🧪 Example (Multiple Styles)

domStyle.set("box", {
    width: "200px",
    height: "100px",
    border: "1px solid black"
});

📌 Used when applying many styles at once.


---

🔧 Method 2: domStyle.get()

✅ Purpose

Used to read the current value of a CSS property.


---

🔹 Syntax

domStyle.get(node, property);


---

🔍 Parameters Explained

Parameter	What it is	Why needed

node	Element	From where to read style
property	CSS property	Which style to read



---

🧪 Example

var color = domStyle.get("box", "backgroundColor");
console.log(color);

✔ Returns computed style value.


---

🏠 Real-Life Analogy (Parameters)

🎨 Painting a Wall

domStyle.set("wall", "color", "blue");

Code Part	Real Life

wall	Which wall
color	What to paint
blue	Paint color



---

🔄 Parameter Flexibility (Important)

node can be:

Element ID ("box")

DOM node (dom.byId("box"))


domStyle.set(dom.byId("box"), "display", "none");


---

⚠️ Common Mistakes

❌ Wrong CSS property format

domStyle.set("box", "background-color", "red");

✅ Correct (camelCase)

domStyle.set("box", "backgroundColor", "red");


---

🧠 Interview One-Liner (With Parameters)

> “domStyle.set(node, property, value) applies a CSS property to a given DOM element, where node identifies the element, property specifies the style, and value defines the style value.”




---

✅ Final Summary (Remember This)

node → where

property → what

value → how

get() → read style

set() → apply style



---

⭐ Memory Trick

> Node → Property → Value
(Where → What → How)




---

Next, I recommend:

dojo/dom-class (parameters explained same way)

dojo/on (event parameters explained deeply)

Full Dojo DOM flow (interview killer)


Just say Next 😊
