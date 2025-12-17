
---

# 🧱 What is dojo/dom-construct?

✅ Definition

dojo/dom-construct is a Dojo module used to create, insert, place, or remove HTML elements dynamically using JavaScript.

👉 In short: it helps us build HTML using JS


---

🤔 Why do we use dom-construct?

Without dom-construct:

You manually write HTML

Or use complex JavaScript DOM APIs


With dom-construct:

Easy element creation

Clean code

Dynamic UI updates

Better readability



---

🏠 Real-Life Analogy

🧱 Building a Wall

Bricks → HTML elements

Builder → dom-construct

Wall → Web page


👉 dom-construct adds or removes bricks from the wall.


---

📦 Importing dom-construct
```
require(["dojo/dom-construct"], function(domConstruct){
    // use domConstruct here
});
```

---

🔧 Common Methods in dom-construct


---

1️⃣ create()

✅ What it does

Creates a new HTML element
```
Syntax

domConstruct.create(tag, attributes, referenceNode, position);
```
Parameters

Parameter	Meaning

tag	HTML tag name
attributes	Properties & attributes
referenceNode	Where to place
position	before / after / inside



---

Example
```
require(["dojo/dom-construct", "dojo/dom"], function(domConstruct, dom){
    domConstruct.create("div", {
        innerHTML: "Hello Dojo",
        style: "color:blue"
    }, dom.byId("container"));
});
```
📌 Creates a <div> inside container


---

2️⃣ place()

✅ What it does

Places an existing node in a new location

Example
```
domConstruct.place("newDiv", "container", "last");
```

---

3️⃣ destroy()

✅ What it does

Removes an element from the DOM

Example
``
domConstruct.destroy("oldDiv");

```
---

4️⃣ empty()

✅ What it does

Removes all child elements inside a node

Example
```
domConstruct.empty("container");
```

---

5️⃣ toDom()

✅ What it does

Converts HTML string → DOM node

Example

var node = domConstruct.toDom("<p>Hello</p>");


---

🔍 Full Real-Time Example

Scenario: Add items to a list dynamically
```
require(["dojo/dom-construct", "dojo/dom"], function(domConstruct, dom){

    var list = dom.byId("list");

    domConstruct.create("li", {
        innerHTML: "Item 1"
    }, list);

});

```
---

🧠 When do we use dom-construct?

Dynamic forms

Add/remove rows in tables

Show/hide messages

Build UI based on data

Enterprise dashboards



---

🧪 Interview One-Liner

> “dojo/dom-construct is used to dynamically create, place, and remove DOM elements in a clean and efficient way.”




---

✅ Summary (Easy to Remember)

dom-construct = build HTML using JS

Used for dynamic UI

Cleaner than plain DOM API

Common methods: create, place, destroy, empty



---


