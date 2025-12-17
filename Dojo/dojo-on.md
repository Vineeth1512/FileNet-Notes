
---

🔔 dojo/on (With Parameters Explained)

# 📘 What is dojo/on?

✅ Definition

dojo/on is a Dojo module used to listen to and handle events such as click, change, keypress, mouse events, etc.

👉 In short: it reacts to user actions.


---

🤔 Why do we use dojo/on?

Without dojo/on:

Use element.onclick

Poor control

Hard to remove events


With dojo/on:

Clean syntax

Works for all browsers

Easy to add and remove listeners

Supports advanced event handling



---

🏠 Real-Life Analogy

🔔 Doorbell

Door → HTML element

Bell → Event

Ring → dojo/on


👉 When someone presses → action happens.


---

📦 Importing Module

require(["dojo/on"], function(on){
    // use on here
});


---

🔧 Basic Syntax

on(target, eventType, listener);


---

🔍 Parameters Explained (Very Important)

Parameter	Meaning	What it accepts	Why needed

target	Event source	DOM node / ID	Where event occurs
eventType	Event name	"click", "change"	Which action to listen
listener	Function	Callback function	What to do when event happens



---

🧪 Simple Example

require(["dojo/on", "dojo/dom"], function(on, dom){
    on(dom.byId("btn"), "click", function(){
        alert("Button clicked");
    });
});

Breakdown

target → button element

eventType → "click"

listener → function executed on click



---

🔧 Common Event Types

Event	Meaning

click	Mouse click
change	Value change
keyup	Key released
keydown	Key pressed
mouseover	Mouse enters
submit	Form submit



---

🔄 Removing Events (Important)

on() returns a handle

var handle = on(node, "click", function(){
    console.log("Clicked");
});

// remove event
handle.remove();

👉 Very important for memory management.


---

🔧 Event Object Parameter

on(node, "click", function(evt){
    console.log(evt.target);
});

evt gives:

Event target

Mouse position

Key pressed

Prevent default action



---

🔧 Prevent Default Behavior

on(node, "click", function(evt){
    evt.preventDefault();
});

📌 Example: stop form submission.


---

🔧 Event Delegation (Advanced but Important)

on(parentNode, ".btn:click", function(){
    alert("Button clicked");
});

Parameters change here:

parentNode → common container

.btn:click → selector + event


👉 Useful for dynamic elements.


---

🏢 Real-Time Example (Enterprise UI)

Scenario: Disable button after click

on(dom.byId("saveBtn"), "click", function(){
    domClass.add("saveBtn", "disabled");
});


---

🔄 dojo/on vs HTML onclick

Feature	onclick	dojo/on

Multiple listeners	❌	✅
Remove listener	❌	✅
Clean code	❌	✅
Enterprise ready	❌	✅



---

🧠 Interview One-Liner

> “dojo/on is a Dojo module used to attach event listeners to DOM elements in a clean, reusable, and cross-browser manner.”




---

✅ Summary (Remember This)

target → where event happens

eventType → which action

listener → what to do

Returns handle → remove event



---

⭐ Memory Trick

> Action → Event
Reaction → Listener
Connection → dojo/on




---

If you want next (same deep explanation):

dojo/parser

dojo/request

Complete Dojo page example

Dojo interview Q&A (enterprise focused)


Just say Next 😊
