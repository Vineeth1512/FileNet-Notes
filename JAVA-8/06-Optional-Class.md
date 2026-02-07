

# 🛡 Java 8 – Topic 6 : Optional Class

---

## 🌟 Introduction

One of the most common problems in Java before Java 8 was:

👉 NullPointerException

Optional class was introduced in Java 8 to handle this problem in a clean and safe way.

---

# 1️⃣ What is Optional Class?

### Simple Definition

Optional is a container object which may or may not contain a non-null value.

It is used to avoid:

- Null checks  
- NullPointerException  
- Too many if-else conditions  

---

# 2️⃣ Why Optional Was Introduced?

### Problem Before Java 8

Developers had to write code like:

```java
if(employee != null) {
    System.out.println(employee.getName());
}
````

Too many null checks everywhere 😐

---

### Java 8 Solution

```java
Optional<Employee> emp = Optional.ofNullable(employee);

emp.ifPresent(System.out::println);
```

✔ Safe
✔ Clean
✔ Modern

---

# 3️⃣ Real-Life Analogy

Think Optional like:

A Gift Box 🎁

* Box may contain gift
* Box may be empty

Before opening, you check if something is inside.

Optional works exactly like that.

---

# 4️⃣ How to Create Optional Object

There are 3 main ways:

---

## A. Optional.of()

Used when value is definitely NOT null

```java
Optional<String> opt = Optional.of("Hello");
```

---

## B. Optional.ofNullable()

Used when value may be null

```java
Optional<String> opt = Optional.ofNullable(name);
```

---

## C. Optional.empty()

Creates an empty Optional

```java
Optional<String> opt = Optional.empty();
```

---

# 5️⃣ Important Methods in Optional

---

## 1. isPresent()

Checks if value exists

```java
opt.isPresent();
```

---

## 2. get()

Gets value (only if present)

```java
opt.get();
```

⚠ Not recommended directly

---

## 3. ifPresent()

Executes only if value exists

```java
opt.ifPresent(System.out::println);
```

---

## 4. orElse()

Provides default value

```java
String name = opt.orElse("Default Name");
```

---

## 5. orElseGet()

Lazy default value

```java
String name = opt.orElseGet(() -> "Guest");
```

---

## 6. orElseThrow()

Throws exception if value not present

```java
opt.orElseThrow(() -> new RuntimeException());
```

---

# 6️⃣ Practical Example

---

### Without Optional (Old Way)

```java
Employee emp = getEmployee();

if(emp != null) {
    System.out.println(emp.getName());
}
```

---

### With Optional (Java 8 Way)

```java
Optional<Employee> emp = Optional.ofNullable(getEmployee());

emp.ifPresent(e -> System.out.println(e.getName()));
```

Much cleaner ✔

---

# 7️⃣ Real-Time Project Usage

Optional is used in:

* Spring Boot services
* Repository layer
* Database results
* API responses

Example in Spring Boot:

```java
Optional<User> user = userRepository.findById(id);

user.orElseThrow(() -> new UserNotFoundException());
```

---

# 8️⃣ Common Mistakes Beginners Make

❌ Using get() directly without checking
❌ Wrapping everything in Optional
❌ Using Optional for fields
❌ Using Optional as method parameters

---

### Best Practices

✔ Use Optional mainly for return types
✔ Prefer orElse() or ifPresent()
✔ Avoid Optional.get()

---

# 9️⃣ Interview-Oriented Explanation

### Question: What is Optional in Java 8?

Answer:

Optional is a container class introduced in Java 8 to handle null values safely and avoid NullPointerException. It provides methods like isPresent(), ifPresent(), orElse() to write null-safe and clean code.

---

# 🔟 Final Summary

| Method       | Purpose                  |
| ------------ | ------------------------ |
| of()         | For non-null values      |
| ofNullable() | For possible null values |
| empty()      | Create empty optional    |
| isPresent()  | Check value exists       |
| ifPresent()  | Execute if value exists  |
| orElse()     | Default value            |

---

## 🎯 Golden Rule

Optional = Null Safety + Clean Code

---

