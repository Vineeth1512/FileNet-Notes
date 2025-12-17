Here is the complete explanation in clean Markdown file format for dojo/query, written in the same style as dojo/dom and dom-construct.
You can copy–paste this directly into a .md file.


---

🔍 dojo/query

📘 What is dojo/query?

✅ Definition

dojo/query is a Dojo module used to select one or more HTML elements using CSS selectors.

👉 In short: it finds elements by class, tag, or attribute.


---

🤔 Why do we use dojo/query?

Without dojo/query:

Use document.getElementsByClassName

Use querySelectorAll

More complex code


With dojo/query:

Simple CSS-style selectors

Can select multiple elements at once

Easy to chain operations



---

🏠 Real-Life Analogy

🧲 Magnet

Iron pieces → HTML elements

Magnet → dojo/query

Area → Web page


👉 dojo/query pulls matching elements together.


---

📦 Importing dojo/query

require(["dojo/query"], function(query){
    // use query here
});


---

🔧 Common Usage of dojo/query


---

1️⃣ Select by Class

Example

require(["dojo/query"], function(query){
    query(".item").style("color", "blue");
});

📌 Selects all elements with class item


---

2️⃣ Select by Tag

query("p").style("fontWeight", "bold");

📌 Selects all <p> tags


---

3️⃣ Select by Attribute

query("input[type='text']").style("border", "1px solid red");


---

🔗 Chaining with Other Modules

dojo/query returns a NodeList, so we can chain methods.

require(["dojo/query", "dojo/on"], function(query, on){
    query(".btn").on("click", function(){
        alert("Clicked");
    });
});


---

🔄 dojo/dom vs dojo/query

Feature	dojo/dom	dojo/query

Selects	Single element	Multiple elements
Selector type	ID only	CSS selectors
Returns	DOM node	NodeList
Use case	Find one	Find many



---

🧠 When do we use dojo/query?

Working with lists

Applying styles to many elements

Handling events on groups

Filtering UI components



---

🧪 Interview One-Liner

> “dojo/query is used to select one or more DOM elements using CSS selectors and returns a NodeList for easy batch operations.”




---

✅ Summary (Easy to Remember)

dojo/query = select many elements

Uses CSS selectors

Returns NodeList

Supports chaining



---

⭐ Memory Tip

> One element → dojo/dom
Many elements → dojo/query




---

If you want next in the same Markdown style:

dojo/on

dojo/dom-style

dojo/dom-class

Full DOM flow in Dojo


Just say Next 😊
