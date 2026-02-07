# 🚀 Java 8 – Topic 2 : Lambda Expression

---

## 🌟 Introduction

Lambda Expression is the **heart of Java 8**.

It brought **Functional Programming style** into Java and changed the way Java code is written.

---

# 1️⃣ What is Lambda Expression?

### Simple Definition

> **Lambda Expression is a short and simple way to write anonymous functions in Java.**

It allows us to write method logic without:
- Creating a class
- Writing a full method
- Giving it a name

---

# 2️⃣ Why Lambda Was Introduced?

### Problems Before Java 8

Before Java 8, even for very small logic we had to write:

- Big anonymous classes  
- Too much boilerplate code  
- Less readable programs  

---

### Example – Before Java 8
```java
Runnable r = new Runnable() {
    public void run() {
        System.out.println("Hello");
    }
};
```

Too much code for just one print statement!

---

### Java 8 Solution – Lambda

```
Runnable r = () -> System.out.println("Hello");
```
✔ Short  
✔ Clean  
✔ Readable  
✔ Professional  

---

# 3️⃣ Real-Life Analogy

| Old Java Way | Java 8 Way |
|---------------|------------|
| Writing a formal letter | Sending a quick WhatsApp message |
| Lengthy and slow | Short and fast |
| Too many steps | Direct and simple |

👉 Lambda = Smart and quick way of writing logic

---

# 4️⃣ Syntax of Lambda Expression

### Basic Structure

```(parameters) -> { body }```

---

### Parts Explanation

| Part | Meaning |
|-----|--------|
| ( ) | Parameters |
| -> | Lambda operator |
| { } | Logic or body |

---

# 5️⃣ Different Forms of Lambda

---

## A. No Parameter Lambda

```() -> System.out.println("Hello");```

---

## B. Single Parameter Lambda

```x -> System.out.println(x);```

👉 Brackets are optional for single parameter

---

## C. Multiple Parameters

```(a, b) -> a + b;```

---

## D. Multi-line Lambda

```(a, b) -> {
    int sum = a + b;
    return sum;
};
```
---

# 6️⃣ Important Rule

### Lambda Expression works ONLY with:

👉 **Functional Interfaces**

If an interface has more than one abstract method,  
Lambda CANNOT be used.

---

# 7️⃣ Practical Example – Step by Step

---

### Step 1 – Create Functional Interface
```
@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}
```
---

### Step 2 – Old Style (Without Lambda)
```
Calculator c = new Calculator() {
    public int add(int a, int b) {
        return a + b;
    }
};
```
---

### Step 3 – New Style (With Lambda)

Calculator c = (a, b) -> a + b;

System.out.println(c.add(10, 20));

👉 Same logic – but very clean and simple

---

# 8️⃣ Real Project Usages

Lambda Expressions are used in:

- Stream API operations  
- Collection processing  
- Spring Boot services  
- Multithreading  
- Event handling  
- Comparator logic  

---

### Example in Streams
```
employees.stream()
         .filter(e -> e.getSalary() > 50000)
         .forEach(e -> System.out.println(e));
```
---

# 9️⃣ Where Lambda Fits in Architecture

In real applications Lambda is mainly used in:

- Service Layer  
- Business Logic  
- Data Processing  
- Utility Classes  

Especially in:

👉 Spring Boot + Microservices projects

---

# 🔟 Common Mistakes Beginners Make

❌ Using lambda for very complex logic  
❌ Forgetting that lambda needs Functional Interface  
❌ Writing unreadable long lambdas  
❌ Thinking lambda is a new method type  

---

### Best Practice

✔ Use lambda only for small and simple logic  
✔ Keep it readable  
✔ Prefer method references when possible  

---

# 1️⃣1️⃣ Interview-Oriented Explanation

### If interviewer asks:

**“What is Lambda Expression?”**

👉 Perfect Answer:

> Lambda Expression is a feature introduced in Java 8 that allows us to write anonymous functions in a concise way.  
> It reduces boilerplate code and is mainly used with functional interfaces to enable functional programming in Java.

---

# 1️⃣2️⃣ Key Benefits of Lambda

- Reduces code length  
- Improves readability  
- Enables functional programming  
- Works smoothly with Streams  
- Makes Java more modern  

---

# 1️⃣3️⃣ Final Summary

| Concept | Meaning |
|-------|---------|
| Anonymous Function | Function without name |
| Lambda Expression | Way to write anonymous functions |
| Requirement | Needs Functional Interface |
| Goal | Write less and do more |

---

## 🎯 Example to Remember

Greeting g = name -> System.out.println("Hello " + name);

g.sayHello("Vineeth");

This is a perfect Lambda Example!

---

