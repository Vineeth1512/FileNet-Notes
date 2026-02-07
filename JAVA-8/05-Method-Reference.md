# 🔗 Java 8 – Topic 5 : Method Reference

---

## 🌟 Introduction

You already learned:

- Lambda Expressions ✔  
- Functional Interfaces ✔  
- Stream API ✔  

Now we learn:

👉 **Method References – an even cleaner form of Lambda Expressions**

---

# 1️⃣ What is Method Reference?

### Simple Definition

> Method Reference is a **shorthand notation of Lambda Expression** used to call an existing method directly.

It is used when:

👉 Lambda only calls an already existing method.

---

# 2️⃣ Why Method References Were Introduced?

### Problem

Even lambda expressions can sometimes look repetitive.

Example using Lambda:

list.forEach(x -> System.out.println(x));

Here lambda is only calling:

System.out.println()

So writing `x ->` is unnecessary.

---

### Java 8 Cleaner Solution

list.forEach(System.out::println);

✔ More readable  
✔ Shorter  
✔ Professional  

---

# 3️⃣ Real-Life Analogy

Think like this:

### Lambda Expression

Telling a friend:

“Take this number and call it”

### Method Reference

“Call this saved contact directly”

No need of middle instruction.

---

# 4️⃣ Syntax of Method Reference

ClassName::methodName

This replaces:
```
(parameters) -> ClassName.methodName(parameters)
```
---

# 5️⃣ When Can We Use Method Reference?

Method Reference can be used when:

👉 Lambda expression is only calling one existing method.

---

### Example

Instead of:
```
name -> System.out.println(name)
```

We can write:

```
System.out::println
```
---

# 6️⃣ Types of Method References

There are **4 types** of Method References:

---

## A. Reference to Static Method

### Syntax

```
ClassName::staticMethodName
```
---

### Example
```
interface Calculator {
    int operate(int a, int b);
}

class MathUtil {
    public static int add(int a, int b) {
        return a + b;
    }
}

Calculator c = MathUtil::add;

System.out.println(c.operate(10, 20));
```
---

## B. Reference to Instance Method of an Object

### Syntax
```
object::instanceMethod
```
---

### Example
```
class Printer {
    void print(String msg) {
        System.out.println(msg);
    }
}

Printer p = new Printer();

Consumer<String> c = p::print;

c.accept("Hello");
```
---

## C. Reference to Instance Method of a Class

### Syntax

ClassName::instanceMethod

---

### Example

```
List<String> list = Arrays.asList("a", "b", "c");

list.forEach(String::toUpperCase);
```

---

## D. Constructor Reference

### Syntax
```
ClassName::new
```
---

### Example
```
interface MyInterface {
    Student getStudent();
}

MyInterface m = Student::new;
```
---

# 7️⃣ Practical Real-Time Example

Instead of writing:

```
employees.forEach(e -> System.out.println(e));
```

Use Method Reference:

```
employees.forEach(System.out::println);
```

Much cleaner and professional.

---

# 8️⃣ Where Method References Are Used

You will see Method References in:

- Stream API  
- Collections  
- Spring Boot projects  
- Logging frameworks  
- Utility classes  

---

# 9️⃣ How it Fits in Architecture

Method references are mainly used in:

- Service layer  
- Utility layer  
- Data processing modules  

Wherever lambda expressions are used.

---

# 🔟 Common Mistakes Beginners Make

❌ Trying to use method reference when logic is complex  
❌ Using method reference when no matching method exists  
❌ Confusing static and instance method references  

---

### Golden Rule

Use Method Reference only when:

👉 Lambda is calling just ONE existing method

---

# 1️⃣1️⃣ Lambda vs Method Reference

| Lambda | Method Reference |
|------|----------------|
| x -> System.out.println(x) | System.out::println |
| (a,b) -> Math.add(a,b) | Math::add |
| More code | Less code |

---

# 1️⃣2️⃣ Advantages of Method References

- Improves readability  
- Reduces code length  
- More expressive  
- Cleaner than lambda  

---

# 1️⃣3️⃣ Interview-Oriented Explanation

### Question: What is Method Reference?

👉 Perfect Answer:

Method Reference is a shorthand notation of Lambda Expression used to refer to an existing method directly using the :: operator. It improves code readability and is used when lambda expression only calls a single method.

---

# 1️⃣4️⃣ Final Summary

| Concept | Meaning |
|-------|--------|
| Method Reference | Shorter form of Lambda |
| Operator Used | :: |
| Purpose | Clean and readable code |
| Works With | Functional Interfaces |

---

## 🎯 Simple Formula

Lambda calling one method  
=  
Method Reference

---

# 🔜 Next Topic

Now you have mastered:

✔ Lambda Expressions  
✔ Functional Interfaces  
✔ Stream API  
✔ Method References  

---

### Next Very Important Topic:

👉 **Optional Class**

(This helps to avoid NullPointerException)

---

### Ready?

Reply:

👉 **“Yes – give Topic 6 (Optional Class)”**
