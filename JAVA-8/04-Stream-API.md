# 🌊 Java 8 – Topic 4 : Stream API

---

## 🚀 Introduction

Stream API is the **most powerful feature of Java 8**.

It completely changed the way we process collections in Java.

If you master Stream API, you master modern Java programming.

---

# 1️⃣ What is Stream API?

### Simple Definition

> Stream API is used to **process collections of data in a functional and declarative style**.

A Stream is:

- A sequence of elements  
- From a collection  
- On which we can perform operations  

---

# 2️⃣ Why Stream API Was Introduced?

### Problems Before Java 8

Earlier we used loops like this:
```
for(Employee e : employees) {
    if(e.getSalary() > 50000) {
        System.out.println(e);
    }
}

```
Problems:

- Too much boilerplate code  
- Manual iteration  
- Less readable  
- More chances of bugs  

---

### Java 8 Solution

```
employees.stream()
    .filter(e -> e.getSalary() > 50000)
    .forEach(System.out::println);

```
✔ No loops  
✔ Clean code  
✔ Easy to understand  

---

# 3️⃣ Real-Life Analogy

Think Stream like a:

### Water Pipeline System

- Data flows like water  
- We apply filters  
- We transform it  
- Finally collect result  

Just like:

Water → Filter → Purifier → Output  
Data → Stream → Operations → Result  

---

# 4️⃣ What Stream API Solves

Stream API helps to:

- Process large collections  
- Filter data easily  
- Transform data  
- Sort data  
- Group data  
- Reduce code length  

All in a clean functional way.

---

# 5️⃣ Basic Structure of Stream

Collection → Stream → Operations → Result

Example:

```
list.stream()
    .operation1()
    .operation2()
    .collect();

```
---

# 6️⃣ Types of Operations in Stream

There are 2 main types:

### 1. Intermediate Operations
- filter()
- map()
- sorted()
- distinct()

### 2. Terminal Operations
- forEach()
- collect()
- count()
- reduce()

---

# 7️⃣ Practical Examples

---

## Example Data

```
List<Integer> list = Arrays.asList(10, 20, 30, 40, 50);

```
---

## A. forEach()

```
list.stream()
    .forEach(System.out::println);

```
---

## B. filter()

```
list.stream()
    .filter(x -> x > 20)
    .forEach(System.out::println);

```
👉 Filters data based on condition

---

## C. map()

```
list.stream()
    .map(x -> x * 2)
    .forEach(System.out::println);

```
👉 Transforms data

---

## D. sorted()

```
list.stream()
    .sorted()
    .forEach(System.out::println);

```
👉 Sorts data

---

## E. collect()

```
List<Integer> newList = list.stream()
    .filter(x -> x > 20)
    .collect(Collectors.toList());

```
👉 Converts stream back to collection

---

# 8️⃣ Real Time Example (Employee Scenario)

```
employees.stream()
    .filter(e -> e.getDepartment().equals("IT"))
    .map(e -> e.getName())
    .forEach(System.out::println);

```
This single line replaces multiple loops!

---

# 9️⃣ Where Stream API is Used in Real Projects

You will see Streams in:

- Spring Boot services  
- Microservices  
- Data processing modules  
- Reporting applications  
- REST API response handling  
- Big data filtering  

---

# 🔟 How Stream API Fits in Architecture

Mostly used in:

👉 Service Layer  
👉 Business Logic Layer  

For:

- Processing database results  
- Manipulating API responses  
- Transforming DTO objects  

---

# 1️⃣1️⃣ Important Characteristics of Streams

- Streams do not store data  
- They operate on collections  
- They are lazy in nature  
- They support functional programming  

---

# 1️⃣2️⃣ Common Mistakes Beginners Make

❌ Using stream but still writing loops  
❌ Confusing map() and filter()  
❌ Forgetting to call terminal operation  
❌ Modifying original collection  

---

### Golden Rule

Without terminal operation:

👉 Stream will not execute

Example:

list.stream().filter(...);

This will NOT run without forEach or collect.

---

# 1️⃣3️⃣ map() vs filter()

| map() | filter() |
|------|---------|
| Used to transform data | Used to filter data |
| Changes values | Checks condition |
| Returns modified stream | Returns filtered stream |

---

# 1️⃣4️⃣ Interview-Oriented Explanation

### Question: What is Stream API?

👉 Perfect Answer:

Stream API is a feature introduced in Java 8 to process collections in a functional and declarative way. It allows operations like filter, map, sort, and collect without using explicit loops, making code clean and efficient.

---

# 1️⃣5️⃣ Advantages of Stream API

- Less code  
- Better readability  
- Easy parallel processing  
- Functional programming style  
- Cleaner business logic  

---

# 1️⃣6️⃣ Final Summary

| Concept | Meaning |
|-------|--------|
| Stream | Sequence of data |
| filter | To apply condition |
| map | To transform data |
| collect | To gather result |
| forEach | To iterate result |

---

## 🎯 Formula to Remember

Collection + Stream + Lambda  
= Modern Java Code

---

# 🔜 Next Topic

Now you have learned:

✔ Lambda Expressions  
✔ Functional Interfaces  
✔ Stream API  

---

### Next Important Topic:

👉 **Method References**

A cleaner way to write Lambda.

---

### Ready?

Reply:

👉 **“Yes – give Topic 5 (Method Reference)”**
