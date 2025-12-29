# 📘 Topic: Environment Setup & First Java Program

## 1️⃣ What Does “Environment Setup” Mean?

### 🧠 Beginner Explanation

Environment setup means:

> “Preparing your computer so that it can **understand, compile, and run Java code**.”

Java does **NOT** run directly like Python.
Java code goes through **multiple stages**.

---

### 🔁 Java Execution Flow (Very Important)

```text
.java (source code)
   ↓  javac
.class (bytecode)
   ↓  JVM
Machine Code → Output
```

📌 Interview Tip:
Java is **platform independent** because of **bytecode + JVM**, not because of `.java` files.

---

## 2️⃣ Components Required for Java Environment

### ✅ 1. JDK (Java Development Kit)

Contains:

* `javac` → compiler
* `java` → JVM launcher
* Standard libraries

📌 **JRE is not enough** for development.

---

### ❌ Common Beginner Confusion

| Term | Purpose                 |
| ---- | ----------------------- |
| JDK  | Development + Execution |
| JRE  | Execution only          |
| JVM  | Runs bytecode           |

✔ Interviews often ask:
**Why JDK includes JRE but not vice-versa?**

---

## 3️⃣ Installing JDK (Conceptual Steps)

> (Exact UI steps vary by OS — concept remains same)

### ✔ Steps

1. Download **JDK (LTS version preferred)**
2. Install JDK
3. Set **Environment Variables**
4. Verify installation

---

## 4️⃣ Environment Variables (Most Confusing Part 🔥)

### 🧠 Why Environment Variables?

So the system can find Java **from anywhere**.

---

### 📌 Two Important Variables

#### 1️⃣ `JAVA_HOME`

```text
JAVA_HOME = C:\Program Files\Java\jdk-21
```

Used by:

* IDEs
* Build tools (Maven, Gradle)

---

#### 2️⃣ `PATH`

Add:

```text
%JAVA_HOME%\bin
```

So commands like `javac` work globally.

---

### ❌ Common Errors

| Error                       | Reason                  |
| --------------------------- | ----------------------- |
| `'javac' is not recognized` | PATH not set            |
| Wrong Java version          | Multiple JDKs installed |
| IDE runs but terminal fails | JAVA_HOME misconfigured |

📌 Interview Question:
**Difference between PATH and JAVA_HOME?**

---

## 5️⃣ Verifying Java Installation

```bash
java -version
javac -version
```

✔ Both should work.

---

### ⚠ Tricky Case

```bash
java works
javac does not
```

👉 JRE installed, not JDK.

---

## 6️⃣ Writing Your First Java Program

### 📄 File Name

```text
HelloWorld.java
```

📌 File name **must match class name**

---

### ✍ Code (Line by Line Explanation)

```java
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

---

### 🔍 Explanation (Interview Style)

#### `class HelloWorld`

* Class name = file name
* Entry container for code

---

#### `public static void main(String[] args)`

This is **mandatory** for program execution.

| Keyword       | Meaning            |
| ------------- | ------------------ |
| public        | JVM must access    |
| static        | No object needed   |
| void          | No return          |
| main          | JVM entry point    |
| String[] args | Command-line input |

📌 Interview Favorite:
**Why main is static?**

---

#### `System.out.println()`

* `System` → class
* `out` → static PrintStream
* `println` → method

---

## 7️⃣ Compilation & Execution

### ✔ Steps

```bash
javac HelloWorld.java
java HelloWorld
```

---

### 📂 What Happens Internally

* `.class` file generated
* JVM loads `.class`
* Executes `main()`

---

### ❌ Common Beginner Mistakes

| Mistake                   | Error         |
| ------------------------- | ------------- |
| File name mismatch        | Compile error |
| Case mismatch             | Runtime error |
| Running `.java` with java | Error         |
| Semicolon missing         | Compile error |

---

## 8️⃣ Command Line Arguments (Quick Intro)

```java
class Test {
    public static void main(String[] args) {
        System.out.println(args[0]);
    }
}
```

Run:

```bash
java Test Hello
```

Output:

```text
Hello
```

---

### ⚠ Edge Case

```java
args[0]
```

without argument → `ArrayIndexOutOfBoundsException`

📌 Interview Question:
**Is args ever null?** → ❌ Never null, but may be empty.

---

## 9️⃣ Using IDE vs Command Line (Interview Angle)

| IDE          | Command Line      |
| ------------ | ----------------- |
| Easy         | Fundamental       |
| Auto compile | Manual control    |
| Hides errors | Reveals internals |

📌 **Strong fundamentals require CLI knowledge**

---

## 🔥 Interview Tricky Concepts Summary

1. Java is compiled **and** interpreted
2. Bytecode ≠ machine code
3. main() signature must be exact
4. PATH ≠ JAVA_HOME
5. Case sensitivity matters
6. One public class → one file
7. JVM searches class via classpath

---

## ✔ Checkpoint Questions (During Lecture)

1. Why Java needs compilation?
2. Why main method is static?
3. Difference between JDK, JRE, JVM?
4. What happens if PATH is not set?
5. Why file name must match class name?

---

## 🧪 Post-Lecture Questions (Assessment)

1. Explain Java execution process step by step.
2. What error occurs if main is not public?
3. Can we change main method name?
4. What happens if multiple main methods exist?
5. Write a program to accept command-line input.

---

## 🎯 Mini Lab Task

1. Install JDK
2. Set PATH manually
3. Write HelloWorld
4. Modify program to print user name from args
5. Break program intentionally & fix errors

---
