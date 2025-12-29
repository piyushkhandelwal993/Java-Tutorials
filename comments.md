# 📘 Topic: Comments in Java


## 1️⃣ What are Comments?

### 🧠 Simple Definition

**Comments are non-executable statements in Java code that are ignored by the compiler.**

👉 They exist **only for humans**, not for the machine.

```java
// This is a comment
System.out.println("Hello");
```

📌 The compiler **skips comments completely**.

---

### ❓ Why Do We Need Comments?

1. Improve **code readability**
2. Explain **logic and intention**
3. Help in **maintenance**
4. Used heavily in **real-world projects**
5. Generate **documentation (JavaDocs)**

> 💡 *Code tells **what** is happening, comments tell **why**.*

---

## 2️⃣ Types of Comments in Java

Java supports **three types of comments**:

| Type          | Syntax   | Usage              |
| ------------- | -------- | ------------------ |
| Single-line   | `//`     | Short explanations |
| Multi-line    | `/* */`  | Detailed notes     |
| Documentation | `/** */` | API documentation  |

---

## 3️⃣ Single-Line Comments (`//`)

### ✔ Syntax

```java
// This is a single-line comment
```

---

### ✔ Example

```java
int age = 20; // storing user age
```

Everything after `//` on that line is ignored.

---

### ⚠ Tricky Case

```java
// System.out.println("Hello");
```

✔ Code is **commented out**, not executed.

---

### ❌ Invalid Assumption

```java
// This is a comment
This is code   // ❌ Compilation error
```

📌 Only text **after `//`** is ignored, not the next line.

---

### ✔ Checkpoint Questions

1. What does `//` indicate?
2. Does `//` affect the next line?
3. Can we use `//` after a statement?

---

## 4️⃣ Multi-Line Comments (`/* */`)

### ✔ Syntax

```java
/*
   This is a multi-line comment
*/
```

---

### ✔ Example

```java
/*
 This program calculates
 the sum of two numbers
*/
int sum = a + b;
```

---

### ⚠ Interview Trap: Nested Comments ❌

```java
/*
  This is a comment
  /* nested comment */
*/
```

❌ **Compilation error**

📌 Java **does NOT support nested multi-line comments**

---

### ⚠ Dangerous Case (Real Projects)

```java
/*
System.out.println("Hello");
System.out.println("World");
*/
```

✔ Entire block is commented
❗ Sometimes developers forget to close `*/`

---

### ✔ Checkpoint Questions

1. Can multi-line comments be nested?
2. What happens if `*/` is missing?
3. When should multi-line comments be used?

---

## 5️⃣ Documentation Comments (`/** */`) – JavaDoc

### ✔ Purpose

Used to generate **HTML documentation** using `javadoc` tool.

```java
/**
 * This class represents a Student
 */
class Student {
}
```

---

### ✔ JavaDoc Tags (Interview Important)

| Tag        | Meaning               |
| ---------- | --------------------- |
| `@author`  | Author name           |
| `@version` | Version info          |
| `@param`   | Parameter description |
| `@return`  | Return value          |
| `@throws`  | Exceptions            |

---

### ✔ Example with Method

```java
/**
 * Adds two numbers
 * @param a first number
 * @param b second number
 * @return sum of a and b
 */
public int add(int a, int b) {
    return a + b;
}
```

---

### ⚠ Interview Question

❓ Difference between `/* */` and `/** */`

✔ `/** */` is for **documentation generation**

---

### ✔ Checkpoint Questions

1. What tool uses JavaDoc comments?
2. Name any two JavaDoc tags.
3. Are JavaDoc comments executed?

---

## 6️⃣ Comments vs Code – Tricky Scenarios

### ✔ Comment Inside Statement

```java
int a = /* value */ 10;
```

✔ Valid

---

### ❌ Comment Breaking Tokens

```java
int a = 1/*comment*/0; // becomes 10
```

📌 Compiler sees `10`, not `1` and `0`

---

### ⚠ Comment Inside String ❌

```java
System.out.println("Hello // World");
```

✔ `//` is **not a comment** inside string

---

### ⚠ Unicode Escape (Interview Gold 🔥)

```java
// \u000d System.out.println("Hello");
```

❌ This **executes the code!**

Why?

* Unicode escape processed **before comments**
* `\u000d` = new line

📌 Very rare but loved in interviews

---

### ✔ Checkpoint Questions

1. Can comments exist inside expressions?
2. Do comments work inside strings?
3. What happens before comments are processed?

---

## 7️⃣ Best Practices (Real Industry Advice)

✔ Use comments to explain **why**, not **what**
✔ Avoid obvious comments
✔ Keep comments updated
✔ Prefer meaningful variable/method names
✔ Use JavaDoc for public APIs

❌ Do not over-comment
❌ Do not comment bad code—**fix it**

---

## 8️⃣ Interview Summary Table

| Topic           | Key Point                  |
| --------------- | -------------------------- |
| Single-line     | `//`                       |
| Multi-line      | `/* */`                    |
| JavaDoc         | `/** */`                   |
| Nested comments | ❌ Not allowed              |
| Unicode escape  | Processed before comments  |
| Strings         | Comments don’t work inside |

---

## 🧪 Post-Lecture Questions (Assessment)

1. Explain all three types of comments with examples.
2. Why nested comments are not allowed in Java?
3. What is JavaDoc and where is it used?
4. Explain Unicode escape issue with comments.
5. Write a JavaDoc comment for a method that divides two numbers.

---

## 🎯 Mini Assignment

* Write a Java class using:

  * All three comment types
  * JavaDoc for class and methods
* Generate JavaDoc HTML using command:

```bash
javadoc ClassName.java
```
