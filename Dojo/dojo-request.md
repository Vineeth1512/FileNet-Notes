Great 👍
Below is dojo/request explained deeply, with definition, why we use it, ALL methods, EVERY parameter explained, examples, real-life analogy, and interview points — in clean Markdown format, same style as before.

You can copy–paste this directly into a .md file.


---

🌐 dojo/request (With Parameters Explained)

📘 What is dojo/request?

✅ Definition

dojo/request is a Dojo module used to send HTTP requests to a server (GET, POST, PUT, DELETE) and receive responses asynchronously.

👉 In short: it is used for AJAX calls.


---

🤔 Why do we use dojo/request?

Without dojo/request:

Use XMLHttpRequest

Complex code

Hard error handling


With dojo/request:

Clean promise-based API

Easy server communication

Better error handling

Enterprise-ready



---

🏠 Real-Life Analogy

📞 Phone Call

You → Browser

Phone number → URL

Talking → Request

Reply → Response


👉 dojo/request calls the server and gets data.


---

📦 Importing Module

require(["dojo/request"], function(request){
    // use request
});


---

🔧 Common Methods in dojo/request


---

1️⃣ request.get()

✅ Purpose

Fetch data from the server.

🔹 Syntax

request.get(url, options);


---

🔍 Parameters Explained

Parameter	Meaning	Example

url	Server endpoint	"data.json"
options	Request settings	{ handleAs: "json" }



---

🧪 Example

request.get("users.json", {
    handleAs: "json"
}).then(function(data){
    console.log(data);
});


---

2️⃣ request.post()

✅ Purpose

Send data to server.

🔹 Syntax

request.post(url, options);


---

🔍 Parameters Explained (options object)

Option	Meaning

data	Data to send
headers	HTTP headers
handleAs	Response type



---

🧪 Example

request.post("login", {
    data: {
        username: "admin",
        password: "1234"
    },
    handleAs: "json"
});


---

3️⃣ request.put()

✅ Purpose

Update existing data.

request.put("user/1", {
    data: { name: "John" }
});


---

4️⃣ request.del()

✅ Purpose

Delete data.

request.del("user/1");


---

🔄 Promise Handling (Very Important)

Success & Error

request.get("data.json").then(
    function(response){
        console.log("Success", response);
    },
    function(error){
        console.log("Error", error);
    }
);


---

🔧 Important options Properties

Property	Purpose

handleAs	"json", "text", "html"
data	Request payload
headers	Content-Type, Auth
timeout	Request timeout
query	URL parameters



---

🧪 Example with Query Parameters

request.get("search", {
    query: {
        name: "Vineet",
        role: "Admin"
    }
});

👉 URL becomes: search?name=Vineet&role=Admin


---

🏢 Enterprise Example (Login)

request.post("login", {
    data: {
        userId: "emp01",
        password: "pass"
    },
    handleAs: "json"
}).then(function(resp){
    console.log("Login success");
});


---

🔄 dojo/request vs dojo/xhr

Feature	dojo/request	dojo/xhr

Modern	✅	❌
Promise based	✅	❌
Recommended	✅	❌



---

⚠️ Common Mistakes

❌ Forgetting handleAs

request.get("data.json");

✅ Correct

request.get("data.json", { handleAs: "json" });


---

🧠 Interview One-Liner

> “dojo/request is a Dojo module used to perform asynchronous HTTP requests using a promise-based API for server communication.”




---

✅ Summary (Easy to Remember)

request.get() → read

request.post() → create

request.put() → update

request.del() → delete

Uses promises



---

⭐ Memory Trick

> UI → Request → Server → Response → UI




---

Recommended Next Topics

1️⃣ Declarative vs Programmatic Widgets (deep)
2️⃣ Complete Dojo Page Example (DOM + Events + Request)
3️⃣ Dojo Interview Q&A (Enterprise focused)

Just say Next 😊
