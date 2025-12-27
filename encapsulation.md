
# 📘 Topic: Encapsulation


## 1️⃣ What is Encapsulation? (Start with the WHY)

### 🔹 Simple Definition

> **Encapsulation is the process of wrapping data and the methods that operate on that data into a single unit, and controlling access to that data.**

In Java, that **single unit** is a **class**.

---

### 🔹 Real-Life Analogy (Very Important for Beginners)

**Capsule 💊**

* Medicine inside (data)
* Outer cover controls access
* You cannot directly touch the medicine

👉 **Same idea in Java**

* Variables → private
* Methods → public
* Access → controlled

---

### 🔹 One-Line Interview Definition

> Encapsulation is **data hiding + controlled access using access modifiers**.

---

## 2️⃣ Why Do We Need Encapsulation?

### ❌ Problem Without Encapsulation

```java
class Account {
    public double balance;
}
```

```java
Account acc = new Account();
acc.balance = -10000; // ❌ Invalid but allowed
```

📌 Data is **unprotected**

---

### ✅ Solution With Encapsulation

```java
class Account {
    private double balance;

    public void setBalance(double balance) {
        if(balance >= 0) {
            this.balance = balance;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

✔ Data is **safe**
✔ Access is **controlled**
✔ Validation possible

---

## 3️⃣ Core Rules of Encapsulation in Java

### ✔ Rule 1: Make variables **private**

```java
private int age;
```

---

### ✔ Rule 2: Provide **public methods** (getters/setters)

```java
public int getAge() {
    return age;
}

public void setAge(int age) {
    if(age > 0) {
        this.age = age;
    }
}
```

---

### ✔ Rule 3: Access data **only through methods**

📌 **Direct access → NO**
📌 **Controlled access → YES**

---

## 4️⃣ Complete Example (Step by Step)

### Step 1: Encapsulated Class

```java
class Student {
    private int rollNo;
    private String name;

    public void setRollNo(int rollNo) {
        if(rollNo > 0) {
            this.rollNo = rollNo;
        }
    }

    public int getRollNo() {
        return rollNo;
    }

    public void setName(String name) {
        if(name != null && !name.isEmpty()) {
            this.name = name;
        }
    }

    public String getName() {
        return name;
    }
}
```

---

### Step 2: Usage

```java
Student s = new Student();
s.setRollNo(101);
s.setName("Amit");

System.out.println(s.getRollNo());
System.out.println(s.getName());
```

✔ Data protected
✔ Validation enforced

---

## 5️⃣ Access Modifiers & Encapsulation (Very Important)

| Modifier  | Scope              |
| --------- | ------------------ |
| private   | Same class only    |
| default   | Same package       |
| protected | Package + subclass |
| public    | Everywhere         |

📌 **Encapsulation relies mainly on `private` + `public`**

---

## 6️⃣ Encapsulation vs Data Hiding (Interview Trap)

### ❓ Are they same?

👉 **NO**

| Concept       | Meaning                              |
| ------------- | ------------------------------------ |
| Data Hiding   | Making variables private             |
| Encapsulation | Data hiding + methods + class design |

📌 **Encapsulation is broader**

---

## 7️⃣ Common Interview Tricky Scenarios

### 🔴 Can a class be fully encapsulated?

❌ No

Because:

* Methods must be accessible

---

### 🔴 Can we have read-only encapsulation?

✔ YES

```java
class Employee {
    private int empId = 101;

    public int getEmpId() {
        return empId;
    }
}
```

✔ No setter → read-only object

---

### 🔴 Write-only encapsulation?

✔ YES

```java
class Password {
    private String pwd;

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }
}
```

---

### 🔴 Immutable Class (Advanced Encapsulation)

```java
final class User {
    private final String name;

    User(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

✔ No setter
✔ Strong encapsulation

---

## 8️⃣ Encapsulation with Arrays & Objects (Edge Case)

### ❌ Problem

```java
class Test {
    private int[] arr = {1,2,3};

    public int[] getArr() {
        return arr;
    }
}
```

Caller can modify array ❌

---

### ✅ Correct Way (Defensive Copy)

```java
public int[] getArr() {
    return arr.clone();
}
```

📌 **Interview favorite question**

---

## 9️⃣ Encapsulation Benefits (Exam & Interview)

* Data security
* Validation
* Loose coupling
* Maintainability
* Better control
* API design

---

## 🔍 Common Mistakes by Beginners

❌ Making variables public
❌ No validation in setters
❌ Using setters blindly
❌ Confusing encapsulation with abstraction
❌ Returning internal mutable objects

---

## ✔ Checkpoint Questions (During Lecture)

1. Why should variables be private?
2. What happens if setter has no validation?
3. Can we skip getters/setters?
4. Difference between encapsulation and data hiding?
5. Can a class have only getters?

---

## 🧪 Post-Lecture Questions (Assessment)

1. Explain encapsulation with real-world example.
2. Write a fully encapsulated `BankAccount` class.
3. What is read-only encapsulation?
4. How does encapsulation improve security?
5. Why returning arrays directly breaks encapsulation?
6. Is encapsulation compulsory in Java? Why/why not?

---

## 🎯 Mini Practice Task (Recommended)

* Create a `UserProfile` class
* Fields: username, password, age
* Add validation in setters
* Make password write-only
* Explain how encapsulation is achieved

---

## 🧠 One-Line Interview Summary

> Encapsulation in Java is achieved by making data members private and providing controlled access through public methods.

---
