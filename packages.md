
# 📦 Topic: Packages and Package Access in Java

---

## 1️⃣ Why Do We Need Packages?

### 🧠 Start With a Real-Life Analogy

Think of your **computer folders**:

```
Documents/
  ├── Photos/
  ├── Videos/
  └── Projects/
```

Packages in Java are **folders for classes**.

📌 Without packages:

* Too many classes → **name conflicts**
* No structure
* Poor maintainability

---

### ✔ Definition

A **package** is a **namespace** that groups related classes and interfaces.

```java
package com.company.project;
```

---

### ✔ Benefits of Packages

1. Avoid **class name conflicts**
2. Provide **logical grouping**
3. Enable **access control**
4. Improve **reusability**
5. Support **modular development**

---

## 2️⃣ Types of Packages in Java

### 🔹 1. Built-in Packages

Provided by Java API.

| Package     | Purpose                       |
| ----------- | ----------------------------- |
| `java.lang` | Core classes (String, System) |
| `java.util` | Collections, Scanner          |
| `java.io`   | File handling                 |
| `java.sql`  | Database                      |

📌 `java.lang` is **imported automatically**

---

### 🔹 2. User-Defined Packages

Created by developers.

```java
package mypack;
```

---

## 3️⃣ Creating a Package (Step by Step)

### ✔ Syntax

```java
package packagename;
```

📌 Must be **first statement** in the source file.

---

### ✔ Example

```java
package com.training.corejava;

public class Demo {
    public void show() {
        System.out.println("Hello from package");
    }
}
```

---

### 📁 Folder Structure Created

```
com/
 └── training/
     └── corejava/
         └── Demo.class
```

---

### ⚠ Interview Trap

```java
import java.util.Scanner;
package test; // ❌
```

📌 `package` must come **before imports**

---

## 4️⃣ How Java Finds Packages (CLASSPATH)

### 🧠 Important Concept

Java uses **CLASSPATH** to locate packages.

```bash
javac -d . Demo.java
```

✔ `-d .` creates folder structure automatically

---

### ❌ Common Beginner Error

```
Exception in thread "main" java.lang.NoClassDefFoundError
```

Cause:

* Classpath not set
* Wrong folder structure

---

## 5️⃣ Accessing Classes From a Package

### ✔ Using Fully Qualified Name

```java
com.training.corejava.Demo obj =
    new com.training.corejava.Demo();
```

---

### ✔ Using import

```java
import com.training.corejava.Demo;

Demo obj = new Demo();
```

---

### ✔ Import All Classes

```java
import com.training.corejava.*;
```

⚠ Interview note:

* Wildcard imports **do not import sub-packages**

---

## 6️⃣ Package Access Levels (VERY IMPORTANT 🔥)

Java has **4 access modifiers**, but package access makes them tricky.

| Modifier    | Same Class | Same Package | Subclass (diff pkg) | Other |
| ----------- | ---------- | ------------ | ------------------- | ----- |
| `private`   | ✔          | ❌            | ❌                   | ❌     |
| *default*   | ✔          | ✔            | ❌                   | ❌     |
| `protected` | ✔          | ✔            | ✔                   | ❌     |
| `public`    | ✔          | ✔            | ✔                   | ✔     |

---

## 7️⃣ Default (Package-Private) Access

### ✔ Definition

If **no access modifier** is specified → **default access**

```java
class A {
    int x = 10; // default
}
```

✔ Accessible **only within same package**

---

### ⚠ Interview Trap

```java
// package p1
class A { }

// package p2
A obj = new A(); // ❌
```

📌 Default ≠ public

---

## 8️⃣ Protected Access (Most Confusing)

### ✔ Key Rule

`protected` members are accessible:

1. Within same package
2. In subclasses **outside the package**

---

### ✔ Example

```java
// package p1
public class A {
    protected int x = 10;
}
```

```java
// package p2
class B extends A {
    void show() {
        System.out.println(x); // ✔
    }
}
```

---

### ⚠ Interview Trick

```java
A obj = new A();
obj.x; // ❌ outside package
```

📌 Protected works via **inheritance**, not object reference.

---

## 9️⃣ Public Access

### ✔ Definition

Accessible **everywhere**

```java
public class A {
    public int x = 10;
}
```

---

### ⚠ Interview Rule

* Only **one public class per file**
* File name must match public class

```java
public class Test { } // file name Test.java
```

---

## 🔟 Private Access (Package-Independent)

### ✔ Definition

Accessible **only inside same class**

```java
class A {
    private int x = 10;
}
```

✔ Even classes in same package **cannot access**

---

## 1️⃣1️⃣ Common Package-Related Interview Traps

### ❌ Default Package

Classes without package declaration belong to **default package**

📌 You **cannot import** default package classes.

---

### ❌ Circular Dependency

```java
package a;
import b.*;

package b;
import a.*;
```

✔ Compiles, but bad design

---

### ❌ Same Class Name in Different Packages

```java
java.util.Date
java.sql.Date
```

✔ Use fully qualified name when ambiguity occurs

---

## 1️⃣2️⃣ Best Practices (Industry Level)

✔ Use **reverse domain naming**

```java
com.company.project.module
```

✔ One public class per file
✔ Avoid default package
✔ Keep related classes together

---

## ✅ Checkpoint Questions (During Lecture)

1. Why does Java need packages?
2. What is default access?
3. Can protected be accessed without inheritance?
4. Why is `java.lang` auto-imported?
5. Difference between import and fully qualified name?

---

## 🧪 Post-Lecture Questions (Assessment)

1. Explain package access vs protected access with example.
2. Why default package is discouraged?
3. Can two classes with same name exist in Java?
4. What happens if package name and folder structure mismatch?
5. Design a package structure for an e-commerce app.

---

## 🎯 Mini Practice Task

* Create two packages: `model` and `service`
* Apply all access modifiers
* Try accessing members across packages
* Observe compile-time errors

---
