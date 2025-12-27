

# 📘 Topic: Access Control in Java



## 1️⃣ Why Do We Need Access Control? (Big Picture)

### 🧠 Real-World Analogy

Think of a **house**:

* **Bedroom** → private
* **Living room** → family only
* **Main gate** → public

👉 Not everything should be accessible to everyone.

### 🔑 In Java

Access control:

* Protects **data**
* Enforces **encapsulation**
* Controls **who can access what**
* Prevents **misuse of classes and members**

---

## 2️⃣ What Is Access Control in Java?

Access control defines **visibility** of:

* Classes
* Variables
* Methods
* Constructors

Java provides **access modifiers** to control this.

---

## 3️⃣ Types of Access Modifiers in Java

Java has **4 access levels**:

| Modifier                  | Keyword      | Visibility                |
| ------------------------- | ------------ | ------------------------- |
| Public                    | `public`     | Everywhere                |
| Protected                 | `protected`  | Same package + subclasses |
| Default (Package-private) | *no keyword* | Same package only         |
| Private                   | `private`    | Same class only           |

---

## 4️⃣ public Access Modifier

### ✔ Definition

Accessible **from anywhere**.

```java
public class Student {
    public int rollNo;
    public void display() {
        System.out.println(rollNo);
    }
}
```

📌 Used for:

* APIs
* Library classes
* Entry points (`main` method)

---

### ⚠ Interview Edge Case

```java
public class A {}
public class B {}
```

❌ **Compile-time error**

✔ Rule:

* **Only ONE public class per file**
* File name must match public class name

---

### ✔ Checkpoint Questions

1. Where can a public member be accessed?
2. How many public classes are allowed in a file?

---

## 5️⃣ private Access Modifier

### ✔ Definition

Accessible **only inside the same class**.

```java
class BankAccount {
    private double balance;

    public void deposit(double amt) {
        balance += amt;
    }
}
```

📌 Core of **Encapsulation**

---

### ❌ Common Beginner Mistake

```java
BankAccount acc = new BankAccount();
acc.balance = 5000; // ❌
```

✔ Correct way:

```java
acc.deposit(5000);
```

---

### ⚠ Interview Trap

```java
class A {
    private void test() {}
}

class B extends A {
    void test() {} // NOT overriding
}
```

📌 **Private methods are NOT inherited**

---

### ✔ Checkpoint Questions

1. Can private members be inherited?
2. Why are getters/setters used?

---

## 6️⃣ Default (Package-Private) Access

### ✔ Definition

No keyword → accessible **within same package only**

```java
class Employee {
    int id; // default access
}
```

---

### 📦 Package Example

```
com.company.hr
   └── Employee.java
com.company.admin
   └── Admin.java
```

```java
Employee e = new Employee(); // ❌ from another package
```

---

### ⚠ Interview Trick

Default ≠ public
Default ≠ protected

📌 Default is **package-level access**

---

### ✔ Checkpoint Questions

1. What happens if no modifier is used?
2. Is default access allowed across packages?

---

## 7️⃣ protected Access Modifier

### ✔ Definition

Accessible:

* Same package
* Subclasses (even in different package)

```java
class Parent {
    protected int x = 10;
}
```

---

### 🧠 Subclass Example

```java
class Child extends Parent {
    void show() {
        System.out.println(x); // ✔
    }
}
```

---

### ⚠ Interview TRAP (Very Important 🔥)

```java
Parent p = new Child();
System.out.println(p.x); // ❌ from different package
```

📌 Rule:
Protected members accessed via **child reference**, not parent reference (outside package)

---

### ✔ Checkpoint Questions

1. Where is protected accessible?
2. Can protected be accessed via parent reference?

---

## 8️⃣ Access Modifier Summary Table (Must-Remember)

| Modifier  | Same Class | Same Package | Subclass (diff pkg) | Everywhere |
| --------- | ---------- | ------------ | ------------------- | ---------- |
| private   | ✔          | ❌            | ❌                   | ❌          |
| default   | ✔          | ✔            | ❌                   | ❌          |
| protected | ✔          | ✔            | ✔                   | ❌          |
| public    | ✔          | ✔            | ✔                   | ✔          |

---

## 9️⃣ Access Control on Classes

### ✔ Rules

* Top-level classes can be:

  * `public`
  * default
* ❌ Cannot be `private` or `protected`

```java
private class Test {} // ❌
```

---

### ✔ Nested Classes

Inner classes **can be private/protected**

```java
class Outer {
    private class Inner {}
}
```

📌 Interview favorite

---

## 🔟 Access Control on Constructors

```java
class Singleton {
    private Singleton() {}
}
```

📌 Used in **Singleton Pattern**

---

## 1️⃣1️⃣ Common Interview Tricky Scenarios

### 🔥 Case 1: Method Overriding

```java
class A {
    protected void show() {}
}

class B extends A {
    public void show() {} // ✔ (wider access)
}
```

❌ Narrowing access is not allowed.

---

### 🔥 Case 2: Fields vs Methods

* Fields → accessed based on **reference type**
* Methods → accessed based on **object type**

---

### 🔥 Case 3: Interface Methods

```java
interface I {
    void test();
}
```

📌 Methods are **public by default**

---

## 1️⃣2️⃣ Common Mistakes Students Make

❌ Thinking default = public
❌ Trying to override private methods
❌ Accessing protected incorrectly across packages
❌ Forgetting access rules during inheritance

---

## 🧪 Checkpoint Questions (Mid-Lecture)

1. Can a class be private?
2. Can a method override with weaker access?
3. Difference between default and protected?
4. Why constructors can be private?

---

## 🧠 Post-Lecture Questions (Assessment)

1. Explain all access modifiers with real-world analogy.
2. Write a program showing protected access across packages.
3. Why is encapsulation impossible without access control?
4. What happens if you reduce access while overriding?
5. Why interfaces methods are public?

---

## 🎯 Mini Practice Task

* Create a package structure
* Demonstrate all access modifiers
* Show one compile-time error per modifier

---

## 🏁 Final Interview Tip

👉 **Access Control + Inheritance = Most tricky interview area**

If students master:

* Access table
* Inheritance rules
* Reference vs object access

They’ll clear **90% interview questions** on this topic.
