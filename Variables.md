### **Lecture Plan: Variables and Data Types in Java**

#### **1. Introduction to Variables**

**Definition:**  
A variable in Java is a container that holds data that can be changed during the execution of a program. Every variable is associated with a data type that determines what kind of data it can store.

**Types of Variables in Java:**
- **Instance Variables:** Defined inside a class but outside any method. They are specific to instances of a class.
- **Class/Static Variables:** Declared with the `static` keyword inside a class but outside any method. Shared among all instances of the class.
- **Local Variables:** Defined inside a method, constructor, or block. Accessible only within that scope.
- **Parameters:** Variables passed to methods.

**Example:**
```java
class Example {
    int instanceVar; // Instance Variable
    static int staticVar; // Static Variable

    void method() {
        int localVar = 10; // Local Variable
    }
}
```

**Checkpoint Questions:**
1. What is a variable in Java?
2. How do instance variables differ from static variables?
3. Can you access a local variable outside the method it’s declared in?

#### **2. Understanding Data Types**

**Definition:**  
Data types in Java define the type and size of data that can be stored in a variable. Java is a statically typed language, meaning all variables must have a declared type.

**Categories:**
- **Primitive Data Types:** Basic types built into Java.
  - **Integer Types:** `byte`, `short`, `int`, `long`
  - **Floating-point Types:** `float`, `double`
  - **Character Type:** `char`
  - **Boolean Type:** `boolean`
- **Reference/Object Data Types:** Used for objects and arrays, which are instances of classes.

**Example:**
```java
int age = 25; // Primitive Data Type (int)
double salary = 55000.50; // Primitive Data Type (double)
String name = "John"; // Reference Type (String)
```

**Edge Cases:**
- **Overflow and Underflow:** When the value assigned exceeds the storage capacity.
  - Example: `byte b = 128; // Compile-time error`
- **Floating-point Precision:** Loss of precision in calculations.
  - Example: `0.1 + 0.2 == 0.3 // returns false`

**Checkpoint Questions:**
1. What are primitive data types in Java?
2. Explain the difference between `float` and `double`.
3. What happens when an integer variable exceeds its maximum value?

#### **3. Variable Initialization and Default Values**

**Initialization:**
Variables must be initialized before use. Failing to do so results in a compile-time error.

**Default Values:**
- **Instance Variables:** Initialized to default values (`0` for integers, `0.0` for floating-point types, `false` for `boolean`, `null` for object references).
- **Local Variables:** Must be explicitly initialized.

**Example:**
```java
int uninitialized; // Compilation error if used before initialization
int initialized = 5; // Valid initialization
```

**Edge Case:**
- **Null Pointer Exception:** Attempting to access an object reference variable that points to `null`.
  - Example:
    ```java
    String s = null;
    System.out.println(s.length()); // Throws NullPointerException
    ```

**Checkpoint Questions:**
1. What are the default values for instance variables?
2. Why must local variables be explicitly initialized?
3. What exception is thrown when accessing a `null` reference?

#### **4. Type Conversion and Casting**

**Implicit Conversion:**
- **Widening Conversion:** Automatically converting a smaller data type to a larger one.
  - Example: `int to long`
- **Example:**
  ```java
  int a = 10;
  long b = a; // Implicit widening conversion
  ```

**Explicit Conversion:**
- **Narrowing Conversion:** Converting a larger data type to a smaller one, which requires explicit casting.
  - Example: `double to int`
- **Example:**
  ```java
  double x = 10.5;
  int y = (int) x; // Explicit narrowing conversion
  ```

**Edge Cases:**
- **Data Loss in Narrowing Conversion:**
  - Example: `double x = 9.78; int y = (int) x; // y becomes 9`

**Checkpoint Questions:**
1. What is implicit conversion in Java?
2. Explain with an example of narrowing conversion.
3. What issues might arise with narrowing conversion?

#### **5. Coding Exercises**

**Exercise 1:**  
Declare a `byte`, `short`, `int`, and `long` variable. Assign the maximum value possible to each and print them. What happens if you add `1` to each?

**Exercise 2:**  
Write a program to swap two numbers using a temporary variable and without using a temporary variable. Discuss the data types used.

**Exercise 3:**  
Create a program that converts temperature from Celsius to Fahrenheit. Define a method to handle this conversion, explaining the data types and conversions involved.

#### **6. Post-Lecture Questions**

1. Explain the difference between primitive and reference data types in Java.
2. What are the default values assigned to different data types when declared as instance variables?
3. Provide an example where implicit type conversion occurs. Why does it not require explicit casting?
4. Write a code snippet where narrowing conversion leads to data loss. Explain the result.
