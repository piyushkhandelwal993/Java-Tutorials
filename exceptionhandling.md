
# 📘 Topic: Exception Handling in Java


## 1️⃣ Why Do We Need Exception Handling?

### 🧠 Real-Life Analogy

Imagine:

* You withdraw money
* ATM crashes
* Card stuck

❓ What should happen?

* Program should not crash
* User should get a proper message
* System should recover gracefully

📌 **Exception handling = Handling abnormal situations without crashing the program**

---

### ❌ Without Exception Handling

```java
int a = 10 / 0;
System.out.println("End");
```

💥 Program crashes
🚫 `End` never prints

---

### ✔ With Exception Handling

```java
try {
    int a = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
System.out.println("End");
```

✔ Program continues

---

## 2️⃣ What Is an Exception?

### ✔ Definition

An **exception** is an **object** that represents an **error condition** occurring during program execution.

📌 In Java:

> **Every exception is an object of a class**

---

### 🔹 Throwable Hierarchy (Very Important)

```
Object
 └── Throwable
      ├── Error
      └── Exception
            ├── RuntimeException
            └── Checked Exceptions
```

---

### 🔥 Interview Rule

* **Error** → Not handled (OutOfMemoryError)
* **Exception** → Should be handled

---

## 3️⃣ Types of Exceptions

### ✔ Checked Exceptions

✔ Checked at **compile time**

Examples:

* `IOException`
* `SQLException`
* `ClassNotFoundException`

```java
FileReader fr = new FileReader("abc.txt"); // ❌
```

✔ Compiler forces handling

---

### ✔ Unchecked Exceptions (Runtime)

✔ Occur at **runtime**

Examples:

* `NullPointerException`
* `ArithmeticException`
* `ArrayIndexOutOfBoundsException`

```java
int a = 10 / 0;
```

---

### ✔ Error (Not Recoverable)

Examples:

* `OutOfMemoryError`
* `StackOverflowError`

📌 **Never catch Error in real projects**

---

### ✔ Checkpoint Questions

1. Difference between Error and Exception?
2. Why RuntimeException is not checked?
3. Name 3 checked exceptions.

---

## 4️⃣ try–catch Block

### ✔ Basic Syntax

```java
try {
    // risky code
} catch (ExceptionType e) {
    // handling code
}
```

---

### ✔ Example

```java
try {
    int arr[] = {1, 2, 3};
    System.out.println(arr[5]);
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Index out of range");
}
```

---

### ⚠ Rule

✔ Catch block must match the exception type
❌ Catching unrelated exception causes compile error

---

### ✔ Multiple Catch Blocks

```java
try {
    String s = null;
    System.out.println(s.length());
} catch (NullPointerException e) {
    System.out.println("Null value");
} catch (Exception e) {
    System.out.println("Generic exception");
}
```

📌 **Child exception first, parent later**

---

### ❌ Wrong Order (Interview Favorite)

```java
catch (Exception e)
catch (NullPointerException e) // ❌ unreachable
```

---

### ✔ Checkpoint Questions

1. Why child catch must come first?
2. What happens if no catch matches?
3. Can we catch multiple exceptions?

---

## 5️⃣ finally Block

### ✔ Purpose

* Executes **always**
* Used for **cleanup**

```java
try {
    int a = 10 / 2;
} catch (Exception e) {
    System.out.println("Error");
} finally {
    System.out.println("Cleanup code");
}
```

✔ Runs even if exception occurs

---

### 🔥 Interview Edge Case

```java
try {
    return;
} finally {
    System.out.println("Finally");
}
```

✔ `finally` **still executes**

---

### ❌ When finally does NOT execute

* JVM crash
* `System.exit(0)`

---

### ✔ Checkpoint Questions

1. Is finally always executed?
2. Can finally exist without catch?
3. Can try exist without catch?

---

## 6️⃣ throw Keyword

### ✔ Purpose

Used to **explicitly throw an exception**

```java
throw new ArithmeticException("Invalid operation");
```

---

### ✔ Example

```java
int age = 15;
if (age < 18) {
    throw new IllegalArgumentException("Not eligible");
}
```

---

### ⚠ Rules

* Must throw an **exception object**
* Control immediately jumps to catch

---

### ✔ Checkpoint Questions

1. Difference between throw and throws?
2. Can we throw checked exception?

---

## 7️⃣ throws Keyword

### ✔ Purpose

Used to **declare exception** to caller

```java
void readFile() throws IOException {
    FileReader fr = new FileReader("abc.txt");
}
```

📌 Responsibility transferred to caller

---

### ✔ Multiple throws

```java
throws IOException, SQLException
```

---

### 🔥 Interview Rule

* `throws` does NOT handle exception
* Only declares

---

### ✔ Checkpoint Questions

1. Does throws handle exception?
2. Who handles exception if declared?

---

## 8️⃣ Custom (User-Defined) Exceptions

### ✔ Why Needed?

* Business logic errors
* Meaningful messages

---

### ✔ Creating Custom Exception

```java
class InvalidAgeException extends Exception {
    InvalidAgeException(String msg) {
        super(msg);
    }
}
```

---

### ✔ Using Custom Exception

```java
if (age < 18) {
    throw new InvalidAgeException("Age below 18");
}
```

---

### ✔ Interview Tip

* Extend `RuntimeException` → unchecked
* Extend `Exception` → checked

---

## 9️⃣ try-with-resources (Java 7+)

### ✔ Purpose

Automatically closes resources

```java
try (FileReader fr = new FileReader("a.txt")) {
    // use file
}
```

✔ No finally required

---

### ✔ Requirement

* Resource must implement `AutoCloseable`

---

## 🔥 Common Interview Tricky Concepts

| Question                         | Answer                |
| -------------------------------- | --------------------- |
| Can we catch Throwable?          | Yes, but bad practice |
| Can catch block throw exception? | Yes                   |
| Can finally throw exception?     | Yes                   |
| Which exception is thrown first? | First encountered     |
| What if catch throws exception?  | Caller handles        |

---

## 🧪 Post-Lecture Questions (Assessment)

1. Explain checked vs unchecked exceptions with examples.
2. What happens if exception is not handled?
3. Difference between `throw` and `throws`.
4. Can we override a method and throw broader exception?
5. Why finally is used for resource cleanup?

---

## 🎯 Mini Assignment

1. Create a custom exception for **InvalidLogin**
2. Handle file reading using try-with-resources
3. Demonstrate multiple catch and finally behavior

---

## ✅ Teaching Outcome

By the end of this lecture, students will:

* Understand **why exceptions occur**
* Handle errors gracefully
* Write **production-ready Java code**
* Answer **90% of interview questions** on exception handling

---
