# Java 8 – Topic 1 : Anonymous Function

---

## 1. What is Anonymous Function?

An **anonymous function** is a function that has **no name**.

It is written inline wherever required instead of creating a separate named method.

---

## 2. Why we need Anonymous Functions?

### Problem Before Java 8

- Even for small logic we had to create:
  - A class
  - A method
  - Full implementation

This created:
- Too much boilerplate code
- Less readability
- More development time

---

## 3. What problem it solves

Anonymous functions help to:

- Write quick logic
- Avoid creating separate methods
- Reduce unnecessary code
- Improve readability

---

## 4. Real-Life Analogy

### Normal Function  
Saving a contact in phone with name.

### Anonymous Function  
Dialing a number directly without saving it.

Temporary usage → No need of a name.

---

## 5. Technical Example (Concept)

Normal Named Function:

public void show() {
    System.out.println("Hello");
}

Anonymous Function Style:

() -> System.out.println("Hello");

Here:
- No method name
- No return type
- No access modifier

---

## 6. Where Anonymous Functions Are Used

Anonymous functions are mainly used in:

- Lambda Expressions
- Stream API
- Threads
- Event handling
- Collections processing

---

## 7. How it fits in Java 8

In Java 8:

Anonymous Functions are implemented using:

👉 Lambda Expressions

Lambda Expression = Implementation of Anonymous Function in Java.

---

## 8. Common Mistakes Beginners Make

- Thinking anonymous function is a new Java method type  
- Trying to write big logic inside anonymous functions  
- Confusing it with normal methods  

Remember:

Anonymous function is only for SMALL and TEMPORARY logic.

---

## 9. Interview Explanation

Question: What is an Anonymous Function?

Answer:

An anonymous function is a function without a name.  
It is used to write inline logic without creating a separate method.  
In Java 8, anonymous functions are implemented using Lambda Expressions.

---

## 10. Summary

- Anonymous Function = Function without name  
- Used for small logic  
- Written inline  
- Base concept behind Lambda Expressions  

---

### Next Topic

Lambda Expression – Java’s way of implementing Anonymous Functions.
