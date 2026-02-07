# 🎯 Java 8 – Topic 3 : Functional Interface

---

## 🌟 Why This Topic is Important?

You already learned:

- Anonymous Functions ✔  
- Lambda Expressions ✔  

Now comes the MOST IMPORTANT RULE:

👉 **Lambda Expressions work ONLY with Functional Interfaces**

So understanding Functional Interface is mandatory.

---

# 1️⃣ What is a Functional Interface?

### Simple Definition

> A **Functional Interface** is an interface that contains  
> **exactly ONE abstract method**

---

### Key Rule

If an interface has:

- Only ONE abstract method → Functional Interface  
- More than one abstract method → NOT Functional Interface  

---

# 2️⃣ Why Functional Interface is Needed?

Because:

👉 Lambda Expressions need a target type to work.

That target type is:

### FUNCTIONAL INTERFACE

Without Functional Interface, Lambda cannot be used.

---

# 3️⃣ Real-Life Analogy

Think of a TV Remote:

- Remote with many buttons → Normal Interface  
- Remote with only ONE button → Functional Interface  

Simple and specific purpose.

---

# 4️⃣ How to Create Functional Interface

Use this annotation:

@FunctionalInterface

---

### Example

@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}

Here:

- Only ONE abstract method → add()
- So it is a Functional Interface

---

# 5️⃣ Using Functional Interface with Lambda

### Step 1 – Interface

@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}

---

### Step 2 – Implementation using Lambda

Calculator c = (a, b) -> a + b;

System.out.println(c.add(10, 20));

✔ No class  
✔ No method  
✔ Direct logic  

This is the real power of Functional Interface.

---

# 6️⃣ Built-in Functional Interfaces in Java 8

Java 8 provides many ready-made functional interfaces.

---

## Most Important Ones

| Interface | Method | Purpose |
|----------|--------|---------|
| Runnable | run() | Thread logic |
| Callable | call() | Thread with return |
| Predicate | test() | Returns true/false |
| Consumer | accept() | Takes input, no return |
| Supplier | get() | No input, returns output |
| Function | apply() | Input → Output |

---

# 7️⃣ Example of Predefined Functional Interface

### Predicate Example

Predicate<Integer> p = x -> x > 10;

System.out.println(p.test(15));

👉 Returns true

---

### Consumer Example

Consumer<String> c = s -> System.out.println(s);

c.accept("Hello");

---

# 8️⃣ Important Points to Remember

A Functional Interface can contain:

- One abstract method  
- Any number of default methods  
- Any number of static methods  

But:

👉 ONLY ONE ABSTRACT METHOD

---

### Example – Valid Functional Interface

@FunctionalInterface
interface Test {

    void show();   // abstract method

    default void display() {
        System.out.println("Default method");
    }

    static void print() {
        System.out.println("Static method");
    }
}

This is STILL a Functional Interface.

---

# 9️⃣ Common Mistakes Beginners Make

❌ Adding two abstract methods  

Example:

interface Wrong {
    void m1();
    void m2();
}

This is NOT a Functional Interface ❗

---

❌ Forgetting @FunctionalInterface annotation  

Though optional, it is recommended.

---

❌ Thinking Functional Interface is new concept  

Actually:

Interfaces existed earlier  
Java 8 just gave them new role.

---

# 🔟 Where Functional Interfaces Are Used in Real Projects

You will see them in:

- Stream API  
- Spring Boot applications  
- Collections processing  
- Event handling  
- Multithreading  
- Comparator logic  

Anywhere Lambda is used → Functional Interface is behind it.

---

# 1️⃣1️⃣ How it Fits in Architecture

Functional Interfaces are mainly used in:

- Service Layer  
- Business Logic  
- Utility classes  
- Data processing modules  

They act as base for:

👉 Lambda Expressions  
👉 Stream API  

---

# 1️⃣2️⃣ Interview-Oriented Explanation

### Question: What is a Functional Interface?

👉 Perfect Answer:

A Functional Interface is an interface that contains exactly one abstract method.  
It is used as a target type for Lambda Expressions in Java 8.  
It may contain multiple default and static methods but only one abstract method.

---

# 1️⃣3️⃣ Golden Rule to Remember

### NO Functional Interface  
=  
### NO Lambda Expression

---

# 1️⃣4️⃣ Final Summary

| Concept | Meaning |
|-------|--------|
| Functional Interface | Interface with ONE abstract method |
| Purpose | To support Lambda Expressions |
| Annotation | @FunctionalInterface |
| Examples | Runnable, Predicate, Consumer |

---

## 🎯 Simple Formula

Functional Interface + Lambda Expression  
= Clean and Modern Java Code

---

# 🔜 Next Topic

Now you clearly know:

✔ What is Functional Interface  
✔ Why it is required  
✔ How Lambda depends on it  

---

### Next MOST IMPORTANT Topic:

👉 **Stream API**

(This is where Lambda + Functional Interface are used heavily)

---

### Ready?

Reply:

👉 **“Yes – give Topic 4 (Stream API)”**
