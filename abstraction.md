# 📘 Topic: Abstraction


## 1️⃣ Why Do We Need Abstraction? (The “Why” First)

### 🤔 Beginner Thought

> “Why can’t I just write all code in one class?”

### 🧠 Real Problem

As programs grow:

* Code becomes **complex**
* Changes break many places
* Users see **too many details**
* Maintenance becomes painful

📌 **Abstraction solves this by hiding unnecessary details and exposing only what is required.**

---

### 🌍 Real-World Example

Think of a **car** 🚗
You know:

* Start
* Stop
* Accelerate

You **don’t know**:

* Fuel injection logic
* Combustion cycles
* ECU programming

👉 You use the **interface**, not the implementation.

---

## 2️⃣ What is Abstraction? (Definition)

### 📖 Simple Definition

> **Abstraction is the process of hiding implementation details and showing only essential features to the user.**

In Java, abstraction is achieved using:

1. **Abstract Classes**
2. **Interfaces**

---

### ❗ Important Clarification (Interview)

* Abstraction is a **concept**
* Abstract class / Interface are **tools**

---

## 3️⃣ Abstraction in Java – The Two Tools

| Tool           | Introduced In                              |
| -------------- | ------------------------------------------ |
| Abstract Class | Java 1.0                                   |
| Interface      | Java 1.0 (default methods added in Java 8) |

---

## 4️⃣ Abstract Classes (Step by Step)

### ✔ What is an Abstract Class?

* A class declared using `abstract` keyword
* **Cannot be instantiated**
* Can have:

  * Abstract methods
  * Concrete methods
  * Variables
  * Constructors

---

### 🔹 Basic Syntax

```java
abstract class Vehicle {
    abstract void start();
}
```

---

### ❌ Instantiation Not Allowed

```java
Vehicle v = new Vehicle(); // ❌ Compile-time error
```

Why?

* Abstract class is **incomplete**

---

### ✔ Correct Usage

```java
class Car extends Vehicle {
    void start() {
        System.out.println("Car starts with key");
    }
}
```

```java
Vehicle v = new Car();
v.start();
```

📌 **Runtime polymorphism + abstraction**

---

## 5️⃣ Abstract Methods

### ✔ Definition

* Method without body
* Must be overridden

```java
abstract void start();
```

---

### ❗ Rules (Interview Critical)

1. Abstract methods **cannot be private**
2. Abstract methods **cannot be static**
3. If a class has even **one abstract method**, class must be abstract

---

### ❌ Invalid Code

```java
abstract private void test(); // ❌
```

Why?

* Private methods cannot be overridden

---

## 6️⃣ Abstract Class with Concrete Methods

```java
abstract class Bank {
    abstract double getInterestRate();

    void displayBank() {
        System.out.println("Welcome to Bank");
    }
}
```

✔ Child classes implement only abstract methods

---

### ✔ Realistic Example

```java
class SBI extends Bank {
    double getInterestRate() {
        return 6.5;
    }
}
```

---

## 7️⃣ Constructors in Abstract Classes (Tricky!)

### ✔ Allowed

```java
abstract class Test {
    Test() {
        System.out.println("Abstract class constructor");
    }
}
```

📌 Constructor is called when **child object is created**

---

### ✔ Interview Question

> Can abstract class have constructor?

✔ **YES**

---

## 8️⃣ Interfaces – Pure Abstraction (Mostly)

### ✔ What is an Interface?

* Blueprint of a class
* All methods are **public & abstract** by default
* Variables are **public static final**

---

### 🔹 Syntax

```java
interface Animal {
    void sound();
}
```

---

### ✔ Implementation

```java
class Dog implements Animal {
    public void sound() {
        System.out.println("Bark");
    }
}
```

---

### ❗ Why `public` is mandatory?

Interface methods are **public by default**

```java
void sound(); // actually public abstract
```

---

## 9️⃣ Interface vs Abstract Class (Must Know)

| Feature              | Abstract Class      | Interface        |
| -------------------- | ------------------- | ---------------- |
| Multiple inheritance | ❌                   | ✔                |
| Constructors         | ✔                   | ❌                |
| Instance variables   | ✔                   | ❌                |
| Default methods      | ✔                   | ✔ (Java 8+)      |
| Use case             | Partial abstraction | Full abstraction |

---

## 🔥 Interview Trap: Multiple Inheritance

```java
class A {}
class B {}
class C extends A, B {} // ❌
```

Java avoids **diamond problem**

✔ Interface solves this.

---

## 1️⃣0️⃣ Java 8 Interface Enhancements (Interview Favorite)

### ✔ Default Methods

```java
interface Test {
    default void show() {
        System.out.println("Default method");
    }
}
```

---

### ✔ Static Methods

```java
interface Test {
    static void display() {
        System.out.println("Static method");
    }
}
```

📌 Static methods are **not inherited**

---

## 1️⃣1️⃣ Key Edge Cases & Tricky Points

### ⚠ Abstract Class

* Can have `main()` method ✔
* Can have static methods ✔
* Can have final methods ✔
* Cannot be instantiated ❌

---

### ⚠ Interface

* Variables are **constants**

```java
int x = 10; // public static final
```

* Cannot create object
* Supports multiple inheritance

---

## 1️⃣2️⃣ Abstraction vs Encapsulation (Interview Confusion)

| Abstraction             | Encapsulation         |
| ----------------------- | --------------------- |
| What to show            | How to protect        |
| Design level            | Implementation level  |
| Uses abstract/interface | Uses access modifiers |

---

## ✔ Checkpoint Questions (During Lecture)

1. Why can’t we create object of abstract class?
2. Can abstract class have non-abstract methods?
3. Why interface methods are public?
4. Difference between abstraction and encapsulation?
5. Can interface have method body?

---

## 🧪 Post-Lecture Questions (Assessment)

1. Design an abstract class `Shape` and implement `Circle`, `Rectangle`
2. Can an abstract class implement an interface?
3. Why multiple inheritance is not supported in Java?
4. When to prefer interface over abstract class?
5. Explain default methods with real example

---

## 🎯 Mini Assignment (Recommended)

Create:

* Abstract class `Employee`
* Subclasses `Developer`, `Tester`
* Abstract method `calculateSalary()`
* Demonstrate runtime polymorphism

---

## 💡 Interview Closing Tip

> “Use **abstract class** when classes are closely related.
> Use **interface** when behavior is common across unrelated classes.”

---
