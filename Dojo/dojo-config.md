

---

⚙️ Dojo Config (dojoConfig)


---

📘 What is dojoConfig?

✅ Definition

dojoConfig is a global configuration object used to tell Dojo how your application should load, behave, and find modules.

👉 In short: dojoConfig controls Dojo’s behavior before Dojo starts.


---

🤔 Why do we use dojoConfig?

Without dojoConfig:

Dojo uses default settings

Hard to manage modules

No control over loading behavior


With dojoConfig:

Control module loading

Configure async behavior

Set paths & packages

Improve performance



---

🏠 Real-Life Analogy

🚦 Traffic Rules

Road → Application

Vehicles → Modules

Traffic rules → dojoConfig


👉 Rules must be set before traffic starts.


---

📍 Where to define dojoConfig?

📌 Must be defined BEFORE loading dojo.js

<script>
    var dojoConfig = {
        async: true
    };
</script>
<script src="dojo/dojo.js"></script>


---

🔧 Common dojoConfig Properties (Explained Separately)


---

1️⃣ async

📘 What is it?

Controls whether modules load asynchronously.

Why use it?

Better performance

Non-blocking loading


Example

async: true

Interview line

> Enables modern asynchronous module loading.




---

2️⃣ parseOnLoad

📘 What is it?

Automatically runs dojo/parser on page load.

Values

true → parser runs automatically

false → manual parser.parse()


Example

parseOnLoad: false

Why usually false?

Better control

Avoid unwanted parsing



---

3️⃣ packages

📘 What is it?

Tells Dojo where to find your custom modules.

Example

packages: [{
    name: "app",
    location: "app"
}]

Meaning

name → module namespace

location → folder path



---

4️⃣ baseUrl

📘 What is it?

Base folder for module lookup.

Example

baseUrl: "/js"


---

5️⃣ paths

📘 What is it?

Create short names for long paths.

Example

paths: {
    utils: "app/utils"
}

Usage:

require(["utils/helper"], function(){});


---

6️⃣ hasCache

📘 What is it?

Feature detection flags.

Example

hasCache: {
    "dojo-debug-messages": true
}


---

7️⃣ locale

📘 What is it?

Sets application language.

Example

locale: "en-in"


---

8️⃣ isDebug

📘 What is it?

Enables debug messages.

Example

isDebug: true


---

9️⃣ deps

📘 What is it?

Modules to load immediately after Dojo loads.

Example

deps: ["app/main"]


---

🔟 callback

📘 What is it?

Function executed after deps load.

Example

callback: function(){
    console.log("Dojo Loaded");
}


---

🧩 Complete Example dojoConfig

<script>
var dojoConfig = {
    async: true,
    parseOnLoad: false,
    packages: [{
        name: "app",
        location: "app"
    }],
    deps: ["app/main"]
};
</script>

<script src="dojo/dojo.js"></script>


---

🧠 Interview One-Liner

> “dojoConfig is a global configuration object that controls Dojo’s module loading, parsing behavior, and application setup before the framework initializes.”




---

✅ Summary (Easy to Remember)

dojoConfig = Dojo settings

Defined before dojo.js

Controls loading, parsing, paths

Very important for large apps



---

⭐ Memory Trick

> Config first → Dojo next → App runs




---

Recommended Next Topics

1️⃣ Dojo application life cycle
2️⃣ Complete Dojo login page
3️⃣ Dojo interview Q&A

Just say Next 😊
