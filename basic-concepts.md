# Basic Concepts

## What is the difference b/w JavaEE and JavaSE?

  | Aspect           | JavaSE (Standard Edition)                    | JavaEE (Enterprise Edition)                 |
  |------------------|----------------------------------------------|----------------------------------------------|
  | **Full Name**    | Java Platform, Standard Edition              | Java Platform, Enterprise Edition            |
  | **Purpose**      | Core Java platform for desktop applications | Enterprise-level applications and web services |
  | **Target**       | Desktop, client-side applications            | Server-side, distributed applications        |
  | **Components**   | Core Java APIs, JVM, basic libraries        | JavaSE + Enterprise APIs, web services      |
  | **APIs**         | Basic I/O, collections, networking          | Servlets, JSP, EJB, JPA, JMS, JTA          |
  | **Deployment**   | Standalone applications                      | Application servers (Tomcat, JBoss, WebLogic) |
  | **Use Cases**    | Desktop apps, simple utilities               | Web applications, microservices, enterprise systems |
  | **Complexity**   | Simpler, easier to learn                     | More complex, requires enterprise knowledge   |
  | **Dependencies** | Minimal external dependencies                | Requires application server and enterprise libraries |
  | **Learning Path**| Foundation for all Java development         | Advanced topic after mastering JavaSE        |

## What is the difference between JDK, JRE, and JVM?

  | Term | Stands For                  | What It Is                                                                 | What It Includes                                   | Typical Use Case                        |
  |------|-----------------------------|----------------------------------------------------------------------------|----------------------------------------------------|-----------------------------------------|
  | JVM  | Java Virtual Machine        | A virtual machine that interprets and executes Java bytecode, enabling platform independence | Class loader, bytecode verifier, execution engine   | Runs compiled Java programs (.class files) |
  | JRE  | Java Runtime Environment    | The runtime environment required to run Java applications                   | JVM + core Java libraries + supporting files        | Runs Java applications (not for development) |
  | JDK  | Java Development Kit        | The complete toolkit for Java development                                   | JRE + development tools (javac, debugger, etc.)     | Develops and runs Java applications      |

**In short:**

- **JVM**: Executes Java bytecode and provides platform independence.
- **JRE**: Supplies the libraries and JVM needed to run Java programs.
- **JDK**: Contains everything in the JRE, plus tools for developing Java applications.

## What are the main features of Java (OOP principles)?

Java is a robust, object-oriented programming language with several key features:

**Core Features:**

- **Platform Independent**: "Write Once, Run Anywhere" - compiled to bytecode that runs on JVM
- **Object-Oriented**: Everything is an object, following OOP principles
- **Strongly Typed**: Compile-time type checking prevents many runtime errors
- **Automatic Memory Management**: Garbage collection handles memory allocation/deallocation
- **Multi-threaded**: Built-in support for concurrent programming
- **Secure**: Built-in security features and sandboxing
- **High Performance**: Just-In-Time (JIT) compilation for optimized execution

**OOP Principles (Pillars of Object-Oriented Programming):**

  | Principle | Description | Example in Java |
  |-----------|-------------|-----------------|
  | **Encapsulation** | Bundling data and methods that operate on that data within a single unit (class) | Private fields with public getter/setter methods |
  | **Inheritance** | Creating new classes that are built upon existing classes, inheriting their properties and methods | `class Dog extends Animal` |
  | **Polymorphism** | Same interface, different implementations (method overriding/overloading) | Method overriding in inheritance, method overloading |
  | **Abstraction** | Hiding complex implementation details and showing only necessary features | Abstract classes, interfaces, abstract methods |

**Additional OOP Concepts:**

### 1. **Association** (Has-a Relationship)  

- **Definition**: A general relationship where one object is connected to another.  
- **Example**: A `Teacher` **has-a** `Student`.  
- **Characteristics**:  
  - Loosely coupled.  
  - No ownership implied.  
  - Can be one-to-one, one-to-many, many-to-many.  

### 2. **Aggregation** (Special Association: Whole-Part)  

- **Definition**: A “whole-part” relationship, but the **part can exist independently** of the whole.  
- **Example**: A `Library` contains `Books`. If the library is destroyed, the books can still exist.  
- **Characteristics**:  
  - Represented with a **hollow diamond** in UML.  
  - Implies ownership, but **no strong lifecycle dependency**.  

### 3. **Composition** (Strong Aggregation)  

- **Definition**: A strong form of aggregation where the **part cannot exist without the whole**.  
- **Example**: A `House` has `Rooms`. If the house is destroyed, the rooms also cease to exist.  
- **Characteristics**:  
  - Represented with a **filled diamond** in UML.  
  - Implies **strong lifecycle dependency**.  

### 4. **Coupling** (Dependency Between Classes)  

- **Definition**: The degree of interdependence between classes or modules.  
- **Good Practice**:  
  - **Low coupling** → flexible, easier to maintain, test, and reuse.  
  - **High coupling** → changes ripple through the system.  
- **Example**: If `ClassA` directly creates and manipulates `ClassB`, they are tightly coupled.  

### 5. **Cohesion** (Internal Consistency of a Class)  

- **Definition**: The degree to which elements of a class (methods, variables) are related and focused on a single purpose.  
- **Good Practice**:  
  - **High cohesion** → each class/module has a clear, single responsibility.  
  - **Low cohesion** → classes do too many unrelated things.  
- **Example**: A `FileHandler` class that only reads/writes files = high cohesion. If it also sends emails = low cohesion.  

✅ **Key Insight**:  

- **Association → Aggregation → Composition** is an increasing order of *relationship strength*.  
- **Coupling** is about how *dependent classes are on each other*.  
- **Cohesion** is about how *well-focused a class is internally*.  

---

## What are primitive and non-primitive data types in Java?

Java has two main categories of data types: **primitive** and **non-primitive** (reference types).

### 1. Primitive Data Types

Java has 8 primitive data types that are built into the language and are not objects:

| Data Type | Size (bits) | Range/Values | Default Value | Example |
|-----------|-------------|--------------|---------------|---------|
| **byte** | 8 | -128 to 127 | 0 | `byte b = 100;` |
| **short** | 16 | -32,768 to 32,767 | 0 | `short s = 1000;` |
| **int** | 32 | -2³¹ to 2³¹-1 | 0 | `int i = 100000;` |
| **long** | 64 | -2⁶³ to 2⁶³-1 | 0L | `long l = 100000L;` |
| **float** | 32 | ±3.4E-38 to ±3.4E+38 | 0.0f | `float f = 3.14f;` |
| **double** | 64 | ±1.7E-308 to ±1.7E+308 | 0.0d | `double d = 3.14;` |
| **char** | 16 | 0 to 65,535 (Unicode) | '\u0000' | `char c = 'A';` |
| **boolean** | 1 | true or false | false | `boolean flag = true;` |

**Key Characteristics:**

**Integer Types (byte, short, int, long):**

- Used for whole numbers
- `int` is the most commonly used integer type
- `long` is used for very large numbers
- `byte` and `short` are used for memory optimization

**Floating-Point Types (float, double):**

- Used for decimal numbers
- `double` is the default and more precise
- `float` is used when memory is a concern
- Always use `f` suffix for float literals

**Character Type (char):**

- Represents a single Unicode character
- Can store any character from 0 to 65,535
- Enclosed in single quotes

**Boolean Type (boolean):**

- Only two values: `true` or `false`
- Used for logical operations and control flow
- Cannot be converted to/from other types

**Memory Optimization Tips:**

- Use `byte` for small numbers (-128 to 127)
- Use `short` for medium numbers (-32K to 32K)
- Use `int` for most integer operations
- Use `long` only when `int` range is insufficient
- Use `float` only when memory is critical, otherwise prefer `double`

**Type Conversion (Casting):**

```java
// Widening (automatic - no data loss)
int i = 100;
long l = i;        // int → long

// Narrowing (explicit casting - potential data loss)
long l = 1000L;
int i = (int) l;   // long → int
```

### 2. Non-Primitive Data Types (Reference Types)

Non-primitive types are objects and are created using the `new` keyword. They include:

| Category | Examples | Description |
|----------|----------|-------------|
| **Classes** | `String`, `Integer`, `ArrayList` | User-defined or built-in classes |
| **Interfaces** | `List`, `Map`, `Runnable` | Abstract contracts for classes |
| **Arrays** | `int[]`, `String[]` | Fixed-size collections of elements |
| **Enums** | `DayOfWeek`, `Color` | Special classes representing constants |

**Key Differences:**

| Aspect | Primitive Types | Reference Types |
|--------|-----------------|-----------------|
| **Storage** | Stored in stack memory | Stored in heap memory, reference in stack |
| **Default Value** | Has default values (0, false, '\u0000') | Default value is `null` |
| **Size** | Fixed size (1-64 bits) | Variable size (depends on object) |
| **Methods** | No methods | Can have methods and properties |
| **Null** | Cannot be null | Can be null |
| **Performance** | Faster access | Slower due to indirection |

**Examples of Reference Types:**

**1. String (Most Common Reference Type):**

```java
String name = "John Doe";           // String literal
String greeting = new String("Hello"); // Using constructor
```

**2. Arrays:**

```java
int[] numbers = {1, 2, 3, 4, 5};   // Array literal
String[] names = new String[3];     // Array with size
```

**3. Collections:**

```java
List<String> list = new ArrayList<>();
Map<String, Integer> map = new HashMap<>();
```

**4. Custom Classes:**

```java
class Person {
    private String name;
    private int age;
    // constructor, getters, setters
}

Person person = new Person();  // Creating object
```

**Memory Management:**

- **Primitives**: Stored directly in stack, automatically managed
- **References**: Object stored in heap, reference in stack, managed by garbage collector

## What is autoboxing and unboxing?

**Autoboxing and unboxing** are Java features that automatically convert between primitive types and their corresponding wrapper classes.

**Wrapper Classes:**

| Primitive Type | Wrapper Class |
|----------------|---------------|
| `byte` | `Byte` |
| `short` | `Short` |
| `int` | `Integer` |
| `long` | `Long` |
| `float` | `Float` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean` | `Boolean` |

**Autoboxing (Primitive → Wrapper):**

- Automatic conversion of primitive types to wrapper objects
- Introduced in Java 5 to simplify code

```java
// Before Java 5 (manual boxing)
Integer num = Integer.valueOf(42);

// With autoboxing (automatic)
Integer num = 42;  // int → Integer automatically
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);  // All ints autoboxed to Integer
```

**Unboxing (Wrapper → Primitive):**

- Automatic conversion of wrapper objects to primitive types
- Also introduced in Java 5

```java
// Before Java 5 (manual unboxing)
int value = num.intValue();

// With unboxing (automatic)
int value = num;  // Integer → int automatically

// In expressions
Integer a = 10;
Integer b = 20;
int sum = a + b;  // Both unboxed, then added, result is int
```

**Common Use Cases:**

**1. Collections (Generic types require objects):**

```java
// Autoboxing when adding to collection
List<Integer> numbers = new ArrayList<>();
numbers.add(42);        // int → Integer (autoboxing)

// Unboxing when retrieving
int first = numbers.get(0);  // Integer → int (unboxing)
```

**2. Method Parameters:**

```java
public void processNumber(Integer num) {
    // Method expects Integer, but we can pass int
}

// Call with primitive
processNumber(42);  // int → Integer (autoboxing)
```

**3. Null Handling:**

```java
Integer nullableInt = null;
// int value = nullableInt;  // NullPointerException! (unboxing null)

// Safe unboxing
int value = (nullableInt != null) ? nullableInt : 0;
```

**Performance Considerations:**

**Autoboxing Overhead:**

```java
// Inefficient - creates new Integer objects
for (int i = 0; i < 1000000; i++) {
    Integer boxed = i;  // Creates 1 million Integer objects
}

// Efficient - use primitives when possible
for (int i = 0; i < 1000000; i++) {
    int primitive = i;  // No object creation
}
```

**Best Practices:**

✅ **Use autoboxing when:**

- Working with collections that require objects
- Passing primitives to methods expecting wrappers
- API requires wrapper types

❌ **Avoid autoboxing when:**

- In performance-critical loops
- When you can use primitives directly
- When null values are not needed

**Common Pitfalls:**

1. **NullPointerException on unboxing:**

```java
Integer nullable = null;
int value = nullable;  // Throws NullPointerException
```

2. **Performance in loops:**

```java
// Bad - creates objects in each iteration
for (Integer i = 0; i < 1000; i++) { ... }

// Good - use primitive
for (int i = 0; i < 1000; i++) { ... }
```

3. **Equality comparison:**

```java
Integer a = 1000;
Integer b = 1000;
System.out.println(a == b);      // false (reference comparison)
System.out.println(a.equals(b)); // true (value comparison)
```

## What are access modifiers in Java (private, protected, public, default)?

Access modifiers in Java control the visibility and accessibility of classes, methods, variables, and constructors. They are fundamental to encapsulation and help implement the principle of information hiding.

### Access Modifiers Overview

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| **private** | ✅ | ❌ | ❌ | ❌ |
| **default** (no modifier) | ✅ | ✅ | ❌ | ❌ |
| **protected** | ✅ | ✅ | ✅ | ❌ |
| **public** | ✅ | ✅ | ✅ | ✅ |

#### 1. Private Access Modifier

**Visibility**: Only within the same class
**Keyword**: `private`

```java
public class BankAccount {
    private double balance;  // Private field
    
    private void validateAmount(double amount) {  // Private method
        if (amount < 0) {
            throw new IllegalArgumentException("Amount cannot be negative");
        }
    }
    
    public void deposit(double amount) {
        validateAmount(amount);  // Can access private method
        balance += amount;
    }
}

// In another class - this won't compile:
// BankAccount account = new BankAccount();
// account.balance = 1000;        // ❌ Error: balance is private
// account.validateAmount(100);   // ❌ Error: method is private
```

**Use Cases:**

- Hide internal implementation details
- Encapsulate data fields
- Helper methods that shouldn't be called externally

#### 2. Default (Package-Private) Access Modifier

**Visibility**: Within the same package
**Keyword**: No keyword (default behavior)

```java
// File: com.bank.BankAccount.java
package com.bank;

class BankAccount {  // Default access - no modifier
    String accountNumber;  // Default access field
    
    void processTransaction() {  // Default access method
        // Implementation
    }
}

// File: com.bank.TransactionProcessor.java (same package)
package com.bank;

public class TransactionProcessor {
    public void process(BankAccount account) {
        account.accountNumber = "12345";           // ✅ Can access default field
        account.processTransaction();               // ✅ Can access default method
    }
}

// File: com.other.ExternalClass.java (different package)
package com.other;

public class ExternalClass {
    public void test() {
        // BankAccount account = new BankAccount();  // ❌ Error: class not visible
    }
}
```

**Use Cases:**

- Package-level encapsulation
- Internal package utilities
- Classes that should only be used within the same package

#### 3. Protected Access Modifier

**Visibility**: Within the same package + subclasses (even in different packages)
**Keyword**: `protected`

```java
// File: com.bank.BankAccount.java
package com.bank;

public class BankAccount {
    protected double balance;
    
    protected void updateBalance(double amount) {
        balance += amount;
    }
}

// File: com.bank.SavingsAccount.java (same package)
package com.bank;

public class SavingsAccount extends BankAccount {
    public void addInterest(double rate) {
        updateBalance(balance * rate);  // ✅ Can access protected method
    }
}

// File: com.other.CreditAccount.java (different package)
package com.other;

import com.bank.BankAccount;

public class CreditAccount extends BankAccount {
    public void chargeFee(double fee) {
        updateBalance(-fee);  // ✅ Can access protected method (inheritance)
        // balance = -1000;   // ❌ Error: can't access protected field directly
    }
}
```

**Use Cases:**

- Allowing subclasses to access certain members
- Framework development where you want to control inheritance
- Template method pattern implementation

#### 4. Public Access Modifier

**Visibility**: Everywhere
**Keyword**: `public`

```java
public class Calculator {
    public static final double PI = 3.14159;  // Public constant
    
    public int add(int a, int b) {  // Public method
        return a + b;
    }
    
    public Calculator() {  // Public constructor
        // Constructor implementation
    }
}

// Can be accessed from anywhere:
Calculator calc = new Calculator();
int result = calc.add(5, 3);
double pi = Calculator.PI;
```

**Use Cases:**

- Public APIs and interfaces
- Utility classes
- Main application classes
- Constants that should be globally accessible

### Access Modifier Rules and Best Practices

#### Class Access Modifiers

```java
public class PublicClass { }        // ✅ Accessible everywhere
class DefaultClass { }              // ✅ Accessible within package
private class PrivateClass { }      // ❌ Compilation error - can't be private
protected class ProtectedClass { }  // ❌ Compilation error - can't be protected
```

**Note**: Only `public` and `default` (no modifier) are allowed for top-level classes.

#### Inner Class Access Modifiers

```java
public class OuterClass {
    public class PublicInner { }        // ✅ Public inner class
    class DefaultInner { }              // ✅ Default inner class
    protected class ProtectedInner { }  // ✅ Protected inner class
    private class PrivateInner { }      // ✅ Private inner class
}
```

#### Method and Field Access Modifiers

```java
public class Example {
    public String publicField;           // ✅ Public field
    protected int protectedField;        // ✅ Protected field
    String defaultField;                 // ✅ Default field
    private boolean privateField;        // ✅ Private field
    
    public void publicMethod() { }       // ✅ Public method
    protected void protectedMethod() { } // ✅ Protected method
    void defaultMethod() { }             // ✅ Default method
    private void privateMethod() { }     // ✅ Private method
}
```

#### Best Practices

✅ **Use private for:**

- Internal implementation details
- Data fields (with public getters/setters)
- Helper methods

✅ **Use default for:**

- Package-level utilities
- Internal package classes

✅ **Use protected for:**

- Methods that subclasses need to override
- Fields that subclasses need to access
- Template method patterns

✅ **Use public for:**

- Public API methods
- Constants
- Main application classes

❌ **Avoid:**

- Making fields public (use getters/setters)
- Over-exposing internal methods
- Using public for everything

#### Real-World Example

```java
public class Employee {
    // Private fields - encapsulated data
    private String name;
    private double salary;
    private String employeeId;
    
    // Public constructor
    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
        this.employeeId = generateEmployeeId();
    }
    
    // Public getters
    public String getName() { return name; }
    public double getSalary() { return salary; }
    public String getEmployeeId() { return employeeId; }
    
    // Protected method for subclasses
    protected void updateSalary(double newSalary) {
        if (newSalary > 0) {
            this.salary = newSalary;
        }
    }
    
    // Private helper method
    private String generateEmployeeId() {
        return "EMP" + System.currentTimeMillis();
    }
    
    // Default method for package access
    void processPayroll() {
        // Internal payroll processing logic
    }
}
```

## What is a package in Java?

A package in Java is a namespace that organizes related classes, interfaces, and sub-packages. It's a way to group related classes together and avoid naming conflicts.

### Package Structure and Naming Convention

**Package Naming Rules:**

- Use lowercase letters
- Use dots (.) to separate package levels
- Follow reverse domain name convention
- Avoid Java reserved words

```java
// Good examples:
package com.company.project;
package org.apache.commons;
package edu.university.department;

// Bad examples:
package Company.Project;        // ❌ Uppercase
package com.company.package;    // ❌ Reserved word
package com.company.123;        // ❌ Starts with number
```

### Package Declaration and Directory Structure

**Package Declaration:**

```java
package com.example.bank;

public class BankAccount {
    // Class implementation
}
```

**Directory Structure:**

```
src/
├── com/
│   ├── example/
│   │   ├── bank/
│   │   │   ├── BankAccount.java
│   │   │   ├── SavingsAccount.java
│   │   │   └── Transaction.java
│   │   └── user/
│   │       ├── User.java
│   │       └── UserManager.java
│   └── util/
│       └── DateUtils.java
```

### Import Statements

**Types of Imports:**

**1. Single Class Import:**

```java
import java.util.ArrayList;
import java.util.HashMap;

public class Example {
    ArrayList<String> list = new ArrayList<>();
    HashMap<String, Integer> map = new HashMap<>();
}
```

**2. Wildcard Import:**

```java
import java.util.*;  // Imports all classes from java.util package

public class Example {
    ArrayList<String> list = new ArrayList<>();
    HashMap<String, Integer> map = new HashMap<>();
    Date date = new Date();
}
```

**3. Static Import:**

```java
import static java.lang.Math.PI;
import static java.lang.Math.sqrt;

public class Example {
    double radius = 5.0;
    double area = PI * radius * radius;
    double diagonal = sqrt(2) * radius;
}
```

**4. Fully Qualified Names (No Import):**

```java
public class Example {
    java.util.ArrayList<String> list = new java.util.ArrayList<>();
    java.time.LocalDate today = java.time.LocalDate.now();
}
```

### Built-in Java Packages

**Core Java Packages:**

| Package | Purpose | Key Classes |
|---------|---------|-------------|
| `java.lang` | Core language features | String, Object, System, Math |
| `java.util` | Utility classes | ArrayList, HashMap, Date, Scanner |
| `java.io` | Input/Output operations | File, InputStream, OutputStream |
| `java.net` | Networking | URL, Socket, HttpURLConnection |
| `java.sql` | Database connectivity | Connection, Statement, ResultSet |
| `java.time` | Date and time (Java 8+) | LocalDate, LocalTime, LocalDateTime |

**Common Import Examples:**

```java
// java.lang (automatically imported)
String name = "John";           // No import needed
Object obj = new Object();      // No import needed

// java.util (needs import)
import java.util.*;
List<String> names = new ArrayList<>();
Map<String, Integer> scores = new HashMap<>();

// java.io (needs import)
import java.io.*;
File file = new File("data.txt");
BufferedReader reader = new BufferedReader(new FileReader(file));
```

### Creating and Using Custom Packages

**1. Creating a Package:**

```java
// File: com/example/bank/BankAccount.java
package com.example.bank;

public class BankAccount {
    private String accountNumber;
    private double balance;
    
    public BankAccount(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }
    
    // Getters and setters
    public String getAccountNumber() { return accountNumber; }
    public double getBalance() { return balance; }
    public void setBalance(double balance) { this.balance = balance; }
}
```

**2. Using Classes from Custom Package:**

```java
// File: com/example/Main.java
package com.example;

import com.example.bank.BankAccount;

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("12345", 1000.0);
        System.out.println("Account: " + account.getAccountNumber());
        System.out.println("Balance: " + account.getBalance());
    }
}
```

### Package Access and Visibility

**Package-Private Access:**

```java
package com.example.bank;

class Transaction {  // Default access - package-private
    private double amount;
    
    Transaction(double amount) {  // Package-private constructor
        this.amount = amount;
    }
    
    void process() {  // Package-private method
        // Can only be accessed within the same package
    }
}

public class BankAccount {
    public void addTransaction(double amount) {
        Transaction txn = new Transaction(amount);  // ✅ Same package
        txn.process();  // ✅ Same package
    }
}
```

### Sub-packages

**Package Hierarchy:**

```java
package com.example.bank.accounts;  // Sub-package of com.example.bank

public class SavingsAccount {
    // Implementation
}
```

**Importing Sub-packages:**

```java
// Import specific sub-package
import com.example.bank.accounts.SavingsAccount;

// Import all classes from sub-package
import com.example.bank.accounts.*;

// Note: Importing parent package doesn't import sub-packages
import com.example.bank.*;  // Doesn't import com.example.bank.accounts.*
```

### Package Best Practices

✅ **Do:**

- Use meaningful package names
- Follow reverse domain convention
- Keep packages focused and cohesive
- Use appropriate access modifiers
- Import only what you need

❌ **Don't:**

- Use default package (no package declaration)
- Create overly deep package hierarchies
- Import entire packages with wildcards unnecessarily
- Use reserved words in package names

### Common Package-Related Issues

**1. Class Not Found:**

```java
// Error: cannot find symbol
// Solution: Check package declaration and import statements
import com.example.bank.BankAccount;  // Make sure this matches the actual package
```

**2. Package Declaration Mismatch:**

```java
// File is in com/example/bank/ directory
package com.example.bank;  // Must match directory structure

public class BankAccount {
    // Implementation
}
```

**3. Import Conflicts:**

```java
import java.util.Date;
import java.sql.Date;  // Conflict!

public class Example {
    // Use fully qualified names to resolve conflicts
    java.util.Date utilDate = new java.util.Date();
    java.sql.Date sqlDate = new java.sql.Date(System.currentTimeMillis());
}
```

### Real-World Package Example

```java
// Project: com.mycompany.inventory

// com/mycompany/inventory/model/Product.java
package com.mycompany.inventory.model;

public class Product {
    private String id;
    private String name;
    private double price;
    
    // Constructor, getters, setters
}

// com/mycompany/inventory/service/InventoryService.java
package com.mycompany.inventory.service;

import com.mycompany.inventory.model.Product;
import java.util.*;

public class InventoryService {
    private Map<String, Product> products = new HashMap<>();
    
    public void addProduct(Product product) {
        products.put(product.getId(), product);
    }
    
    public Product getProduct(String id) {
        return products.get(id);
    }
}

// com/mycompany/inventory/Main.java
package com.mycompany.inventory;

import com.mycompany.inventory.model.Product;
import com.mycompany.inventory.service.InventoryService;

public class Main {
    public static void main(String[] args) {
        InventoryService service = new InventoryService();
        Product product = new Product("P001", "Laptop", 999.99);
        service.addProduct(product);
    }
}
```

## What is a static keyword? Static variables, methods, and classes?

The `static` keyword in Java is used to create class-level members that belong to the class itself rather than to instances of the class. Static members are shared across all instances and can be accessed without creating an object.

### Static Variables (Class Variables)

**Characteristics:**

- Belong to the class, not to any specific instance
- Shared by all instances of the class
- Memory is allocated only once
- Can be accessed using class name or instance

```java
public class Student {
    // Instance variables (non-static)
    private String name;
    private int rollNumber;
    
    // Static variable (class variable)
    public static int totalStudents = 0;
    
    public Student(String name, int rollNumber) {
        this.name = name;
        this.rollNumber = rollNumber;
        totalStudents++;  // Increment static variable
    }
    
    public static int getTotalStudents() {
        return totalStudents;
    }
}

// Usage
Student student1 = new Student("John", 101);
Student student2 = new Student("Jane", 102);

System.out.println(Student.totalStudents);        // 2 (using class name)
System.out.println(student1.totalStudents);       // 2 (using instance - not recommended)
System.out.println(Student.getTotalStudents());   // 2 (using static method)
```

**Memory Layout:**

```
Class Area (Method Area)
┌─────────────────────┐
│ Student.totalStudents│ ← Shared by all instances
└─────────────────────┘

Heap Memory
┌─────────────┐  ┌─────────────┐
│ student1    │  │ student2    │
│ name: John  │  │ name: Jane  │
│ rollNumber: │  │ rollNumber: │
│ 101         │  │ 102         │
└─────────────┘  └─────────────┘
```

### Static Methods (Class Methods)

**Characteristics:**

- Belong to the class, not to instances
- Can be called without creating an object
- Cannot access instance variables or methods directly
- Cannot use `this` keyword
- Can access only static members
- Cannot override static method

```java
public class MathUtils {
    // Static method
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static double calculateArea(double radius) {
        return Math.PI * radius * radius;
    }
    
    public static boolean isEven(int number) {
        return number % 2 == 0;
    }
    
    // Static method calling another static method
    public static double calculateCircumference(double radius) {
        return 2 * Math.PI * radius;  // Math.PI is static
    }
}

// Usage - no object creation needed
int sum = MathUtils.add(5, 3);           // 8
double area = MathUtils.calculateArea(5); // 78.54...
boolean even = MathUtils.isEven(10);      // true
```

**Static vs Instance Methods:**

```java
public class Calculator {
    private int value;  // Instance variable
    
    public Calculator(int value) {
        this.value = value;
    }
    
    // Instance method - can access instance variables
    public int getValue() {
        return this.value;  // ✅ Can use 'this'
    }
    
    // Static method - cannot access instance variables
    public static int add(int a, int b) {
        // return this.value;  // ❌ Error: 'this' not available
        return a + b;
    }
    
    // Static method calling instance method - ERROR
    public static void printValue() {
        // getValue();  // ❌ Error: cannot call instance method from static context
        System.out.println("Cannot access instance methods");
    }
}
```

### Static Blocks

**Purpose:**

- Initialize static variables
- Perform one-time setup for the class
- Execute code when the class is loaded

```java
public class DatabaseConnection {
    private static String connectionString;
    private static Properties config;
    
    // Static block - executed when class is loaded
    static {
        System.out.println("Loading database configuration...");
        config = new Properties();
        try {
            config.load(DatabaseConnection.class.getResourceAsStream("db.properties"));
            connectionString = config.getProperty("db.url");
        } catch (IOException e) {
            connectionString = "jdbc:default:url";
        }
        System.out.println("Database configuration loaded: " + connectionString);
    }
    
    public static String getConnectionString() {
        return connectionString;
    }
}

// When this class is first accessed:
// Output: "Loading database configuration..."
//         "Database configuration loaded: jdbc:default:url"
```

### Static Classes (Nested Static Classes)

**Characteristics:**

- Can be declared inside another class
- Does not require an instance of the outer class
- Can access only static members of the outer class
- Can be instantiated independently

```java
public class OuterClass {
    private static String staticField = "Static Field";
    private String instanceField = "Instance Field";
    
    // Static nested class
    public static class StaticNestedClass {
        public void display() {
            System.out.println(staticField);        // ✅ Can access static field
            // System.out.println(instanceField);   // ❌ Cannot access instance field
        }
        
        public static void staticMethod() {
            System.out.println("Static method in nested class");
        }
    }
    
    // Non-static inner class (for comparison)
    public class InnerClass {
        public void display() {
            System.out.println(staticField);        // ✅ Can access static field
            System.out.println(instanceField);      // ✅ Can access instance field
        }
    }
}

// Usage
OuterClass.StaticNestedClass nested = new OuterClass.StaticNestedClass();
nested.display();
OuterClass.StaticNestedClass.staticMethod();

// Inner class requires outer class instance
OuterClass outer = new OuterClass();
OuterClass.InnerClass inner = outer.new InnerClass();
```

### Static Import

**Purpose:**

- Import static members directly
- Use static methods without class name prefix
- Improve code readability

```java
import static java.lang.Math.PI;
import static java.lang.Math.sqrt;
import static java.lang.Math.pow;
import static java.lang.System.out;

public class Geometry {
    public static double calculateArea(double radius) {
        return PI * pow(radius, 2);  // No Math. prefix needed
    }
    
    public static double calculateHypotenuse(double a, double b) {
        return sqrt(pow(a, 2) + pow(b, 2));
    }
    
    public static void printResult(String message, double result) {
        out.println(message + ": " + result);  // No System. prefix needed
    }
}
```

### Common Use Cases and Best Practices

**✅ When to Use Static:**

1. **Utility Methods:**

```java
public class StringUtils {
    public static boolean isEmpty(String str) {
        return str == null || str.trim().isEmpty();
    }
    
    public static String reverse(String str) {
        if (isEmpty(str)) return str;
        return new StringBuilder(str).reverse().toString();
    }
}
```

2. **Constants:**

```java
public class Constants {
    public static final String APP_NAME = "My Application";
    public static final int MAX_RETRY_ATTEMPTS = 3;
    public static final double TAX_RATE = 0.08;
}
```

3. **Factory Methods:**

```java
public class ConnectionFactory {
    public static Connection createConnection(String url) {
        // Connection creation logic
        return new Connection(url);
    }
    
    public static Connection createDefaultConnection() {
        return createConnection("jdbc:default:url");
    }
}
```

4. **Singleton Pattern:**

```java
public class Singleton {
    private static Singleton instance;
    
    private Singleton() {}  // Private constructor
    
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

**❌ When NOT to Use Static:**

1. **Instance-specific data**
2. **Methods that need access to instance variables**
3. **Methods that should be overridden in subclasses**
4. **Stateful operations**

### Memory Management and Performance

**Memory Allocation:**

- Static members are allocated in the Class Area (Method Area)
- Memory is allocated once when the class is loaded
- Shared across all instances
- Garbage collection doesn't affect static members

**Performance Considerations:**

```java
public class PerformanceExample {
    // Good: Static final for constants
    public static final String CONSTANT = "Value";
    
    // Good: Static utility methods
    public static int utilityMethod(int x) {
        return x * 2;
    }
    
    // Bad: Static for instance-specific data
    public static int instanceData;  // Shared across all instances!
    
    // Bad: Static methods that should be instance methods
    public static void processInstanceData() {
        // Cannot access instance-specific data
    }
}
```

### Real-World Example: Configuration Manager

```java
public class ConfigManager {
    private static Properties config;
    private static boolean initialized = false;
    
    // Static block for initialization
    static {
        loadConfiguration();
    }
    
    private static void loadConfiguration() {
        config = new Properties();
        try {
            config.load(ConfigManager.class.getResourceAsStream("config.properties"));
            initialized = true;
        } catch (IOException e) {
            System.err.println("Failed to load configuration: " + e.getMessage());
        }
    }
    
    // Static methods for configuration access
    public static String getProperty(String key) {
        if (!initialized) {
            loadConfiguration();
        }
        return config.getProperty(key);
    }
    
    public static String getProperty(String key, String defaultValue) {
        if (!initialized) {
            loadConfiguration();
        }
        return config.getProperty(key, defaultValue);
    }
    
    public static boolean isInitialized() {
        return initialized;
    }
    
    // Usage example
    public static void main(String[] args) {
        String dbUrl = ConfigManager.getProperty("database.url", "jdbc:default");
        String appName = ConfigManager.getProperty("app.name", "Default App");
        
        System.out.println("Database URL: " + dbUrl);
        System.out.println("App Name: " + appName);
    }
}
```

## What is a Constructor in Java? Types of constructors? Can a constructor be Private?

A constructor in Java is a special method that is automatically called when an object is created. It has the same name as the class and is used to initialize the object's state.

### Constructor Characteristics

**Key Features:**

- Same name as the class
- No return type (not even void)
- Automatically called when object is created
- Can be overloaded (multiple constructors with different parameters)
- Can have access modifiers (public, private, protected, default)

### Types of Constructors

#### 1. Default Constructor

**Characteristics:**

- Automatically provided by Java if no constructor is defined
- No parameters
- Initializes instance variables to default values

```java
public class Student {
    private String name;
    private int age;
    
    // No constructor defined - Java provides default constructor
    
    public void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

// Usage
Student student = new Student();  // Default constructor called
student.display();  // Output: Name: null, Age: 0
```

**Default Values:**

- `int`, `long`, `short`, `byte` → 0
- `float`, `double` → 0.0
- `boolean` → false
- `char` → '\u0000'
- Object references → null

#### 2. Parameterized Constructor

**Characteristics:**

- Takes parameters to initialize instance variables
- Allows custom initialization of object state

```java
public class Student {
    private String name;
    private int age;
    private String course;
    
    // Parameterized constructor
    public Student(String name, int age, String course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }
    
    public void display() {
        System.out.println("Name: " + name + ", Age: " + age + ", Course: " + course);
    }
}

// Usage
Student student = new Student("John", 20, "Computer Science");
student.display();  // Output: Name: John, Age: 20, Course: Computer Science
```

#### 3. Copy Constructor

**Characteristics:**

- Creates a new object by copying values from another object
- Useful for creating deep copies

```java
public class Student {
    private String name;
    private int age;
    private String course;
    
    // Regular constructor
    public Student(String name, int age, String course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }
    
    // Copy constructor
    public Student(Student other) {
        this.name = other.name;
        this.age = other.age;
        this.course = other.course;
    }
    
    // Getters
    public String getName() { return name; }
    public int getAge() { return age; }
    public String getCourse() { return course; }
}

// Usage
Student original = new Student("John", 20, "Computer Science");
Student copy = new Student(original);  // Copy constructor called
```

#### 4. Constructor Chaining

**Characteristics:**

- One constructor calls another constructor
- Uses `this()` keyword
- Reduces code duplication

```java
public class Student {
    private String name;
    private int age;
    private String course;
    private String email;
    
    // Constructor with all parameters
    public Student(String name, int age, String course, String email) {
        this.name = name;
        this.age = age;
        this.course = course;
        this.email = email;
    }
    
    // Constructor with 3 parameters - chains to 4-parameter constructor
    public Student(String name, int age, String course) {
        this(name, age, course, "default@email.com");  // Constructor chaining
    }
    
    // Constructor with 2 parameters - chains to 3-parameter constructor
    public Student(String name, int age) {
        this(name, age, "Undecided");  // Constructor chaining
    }
    
    // Constructor with 1 parameter - chains to 2-parameter constructor
    public Student(String name) {
        this(name, 18);  // Constructor chaining
    }
    
    // Default constructor - chains to 1-parameter constructor
    public Student() {
        this("Unknown");  // Constructor chaining
    }
    
    public void display() {
        System.out.println("Name: " + name + ", Age: " + age + 
                          ", Course: " + course + ", Email: " + email);
    }
}

// Usage
Student s1 = new Student();                    // Name: Unknown, Age: 18, Course: Undecided, Email: default@email.com
Student s2 = new Student("John");              // Name: John, Age: 18, Course: Undecided, Email: default@email.com
Student s3 = new Student("John", 20);          // Name: John, Age: 20, Course: Undecided, Email: default@email.com
Student s4 = new Student("John", 20, "CS");    // Name: John, Age: 20, Course: CS, Email: default@email.com
Student s5 = new Student("John", 20, "CS", "john@email.com");
```

### Private Constructors

**Yes, constructors can be private!** This is a powerful design pattern used in several scenarios.

#### 1. Singleton Pattern

**Purpose:**

- Ensure only one instance of a class exists
- Control object creation

```java
public class Singleton {
    private static Singleton instance;
    private String data;
    
    // Private constructor - prevents external instantiation
    private Singleton() {
        data = "Initialized";
    }
    
    // Public method to get the single instance
    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
    
    public String getData() {
        return data;
    }
    
    public void setData(String data) {
        this.data = data;
    }
}

// Usage
Singleton obj1 = Singleton.getInstance();
Singleton obj2 = Singleton.getInstance();

System.out.println(obj1 == obj2);  // true - same instance
obj1.setData("Updated");
System.out.println(obj2.getData()); // "Updated" - same instance
```

#### 2. Utility Classes

**Purpose:**

- Prevent instantiation of utility classes
- All methods are static

```java
public class MathUtils {
    // Private constructor - prevents instantiation
    private MathUtils() {
        throw new UnsupportedOperationException("Utility class cannot be instantiated");
    }
    
    public static int add(int a, int b) {
        return a + b;
    }
    
    public static int multiply(int a, int b) {
        return a * b;
    }
    
    public static boolean isEven(int number) {
        return number % 2 == 0;
    }
}

// Usage
int sum = MathUtils.add(5, 3);        // 8
int product = MathUtils.multiply(4, 6); // 24
boolean even = MathUtils.isEven(10);    // true

// This will cause compilation error:
// MathUtils utils = new MathUtils();  // ❌ Constructor is private
```

#### 3. Factory Pattern

**Purpose:**

- Control object creation through factory methods
- Enforce creation rules

```java
public class Connection {
    private String url;
    private String username;
    private String password;
    
    // Private constructor
    private Connection(String url, String username, String password) {
        this.url = url;
        this.username = username;
        this.password = password;
    }
    
    // Factory method for creating connections
    public static Connection createConnection(String url, String username, String password) {
        if (url == null || url.isEmpty()) {
            throw new IllegalArgumentException("URL cannot be null or empty");
        }
        if (username == null || username.isEmpty()) {
            throw new IllegalArgumentException("Username cannot be null or empty");
        }
        return new Connection(url, username, password);
    }
    
    // Factory method for default connection
    public static Connection createDefaultConnection() {
        return new Connection("jdbc:default:url", "admin", "password");
    }
    
    public void connect() {
        System.out.println("Connecting to: " + url + " with user: " + username);
    }
}

// Usage
Connection conn1 = Connection.createConnection("jdbc:mysql://localhost:3306/db", "user", "pass");
Connection conn2 = Connection.createDefaultConnection();

// This will cause compilation error:
// Connection conn3 = new Connection("url", "user", "pass");  // ❌ Constructor is private
```

#### 4. Builder Pattern

**Purpose:**

- Complex object construction
- Immutable objects

```java
public class DatabaseConfig {
    private final String host;
    private final int port;
    private final String database;
    private final String username;
    private final String password;
    
    // Private constructor
    private DatabaseConfig(String host, int port, String database, String username, String password) {
        this.host = host;
        this.port = port;
        this.database = database;
        this.username = username;
        this.password = password;
    }
    
    // Static builder class
    public static class Builder {
        private String host = "localhost";
        private int port = 3306;
        private String database = "default";
        private String username = "root";
        private String password = "";
        
        public Builder host(String host) {
            this.host = host;
            return this;
        }
        
        public Builder port(int port) {
            this.port = port;
            return this;
        }
        
        public Builder database(String database) {
            this.database = database;
            return this;
        }
        
        public Builder username(String username) {
            this.username = username;
            return this;
        }
        
        public Builder password(String password) {
            this.password = password;
            return this;
        }
        
        public DatabaseConfig build() {
            return new DatabaseConfig(host, port, database, username, password);
        }
    }
    
    // Getters
    public String getHost() { return host; }
    public int getPort() { return port; }
    public String getDatabase() { return database; }
    public String getUsername() { return username; }
    public String getPassword() { return password; }
}

// Usage
DatabaseConfig config = new DatabaseConfig.Builder()
    .host("192.168.1.100")
    .port(5432)
    .database("mydb")
    .username("admin")
    .password("secret123")
    .build();

// This will cause compilation error:
// DatabaseConfig config2 = new DatabaseConfig("host", 3306, "db", "user", "pass");  // ❌ Constructor is private
```

### Constructor Rules and Best Practices

#### Constructor Rules

1. **Name must match class name exactly**
2. **No return type (not even void)**
3. **Can have access modifiers**
4. **Can be overloaded**
5. **Can call other constructors using `this()`**
6. **Can call parent constructor using `super()`**

#### Best Practices

✅ **Do:**

- Use constructor chaining to reduce code duplication
- Validate parameters in constructors
- Use private constructors for design patterns
- Provide meaningful default values

❌ **Don't:**

- Perform complex operations in constructors
- Call overridable methods from constructors
- Create objects that aren't fully initialized
- Use constructors for business logic

### Constructor vs Method

| Aspect | Constructor | Method |
|--------|-------------|---------|
| **Name** | Must match class name | Can be any valid identifier |
| **Return Type** | None | Required (void if nothing returned) |
| **Calling** | Automatically called with `new` | Must be explicitly called |
| **Purpose** | Initialize object state | Perform operations |
| **Inheritance** | Not inherited | Inherited by subclasses |

### Real-World Example: Bank Account System

```java
public class BankAccount {
    private String accountNumber;
    private String accountHolder;
    private double balance;
    private String accountType;
    private LocalDateTime createdAt;
    
    // Private constructor for internal use
    private BankAccount(String accountNumber, String accountHolder, double balance, String accountType) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = balance;
        this.accountType = accountType;
        this.createdAt = LocalDateTime.now();
    }
    
    // Factory method for savings account
    public static BankAccount createSavingsAccount(String accountHolder, double initialDeposit) {
        if (initialDeposit < 100) {
            throw new IllegalArgumentException("Minimum deposit for savings account is $100");
        }
        String accountNumber = generateAccountNumber("SAV");
        return new BankAccount(accountNumber, accountHolder, initialDeposit, "Savings");
    }
    
    // Factory method for checking account
    public static BankAccount createCheckingAccount(String accountHolder, double initialDeposit) {
        if (initialDeposit < 50) {
            throw new IllegalArgumentException("Minimum deposit for checking account is $50");
        }
        String accountNumber = generateAccountNumber("CHK");
        return new BankAccount(accountNumber, accountHolder, initialDeposit, "Checking");
    }
    
    // Private method to generate account numbers
    private static String generateAccountNumber(String prefix) {
        return prefix + System.currentTimeMillis();
    }
    
    // Getters
    public String getAccountNumber() { return accountNumber; }
    public String getAccountHolder() { return accountHolder; }
    public double getBalance() { return balance; }
    public String getAccountType() { return accountType; }
    public LocalDateTime getCreatedAt() { return createdAt; }
    
    // Business methods
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }
}

// Usage
BankAccount savings = BankAccount.createSavingsAccount("John Doe", 500);
BankAccount checking = BankAccount.createCheckingAccount("Jane Smith", 100);

// This will cause compilation error:
// BankAccount account = new BankAccount("123", "User", 100, "Type");  // ❌ Constructor is private
```

## Can we use static methods in a Constructor?

**Yes, you can call static methods from within a constructor!** This is a common and useful practice in Java. However, there are important considerations and best practices to follow.

### Static Methods in Constructors - Allowed and Common

**Key Points:**

- ✅ **Static methods can be called from constructors**
- ✅ **This is a common and valid practice**
- ✅ **Useful for initialization and validation**
- ⚠️ **Be careful about calling overridable methods**

### Examples of Using Static Methods in Constructors

#### 1. Validation and Utility Methods

```java
public class Student {
    private String name;
    private int age;
    private String email;
    
    public Student(String name, int age, String email) {
        // Call static validation methods
        this.name = validateName(name);
        this.age = validateAge(age);
        this.email = validateEmail(email);
    }
    
    // Static validation methods
    private static String validateName(String name) {
        if (name == null || name.trim().isEmpty()) {
            throw new IllegalArgumentException("Name cannot be null or empty");
        }
        return name.trim();
    }
    
    private static int validateAge(int age) {
        if (age < 0 || age > 150) {
            throw new IllegalArgumentException("Age must be between 0 and 150");
        }
        return age;
    }
    
    private static String validateEmail(String email) {
        if (email == null || !email.contains("@")) {
            throw new IllegalArgumentException("Invalid email format");
        }
        return email.toLowerCase();
    }
    
    // Getters
    public String getName() { return name; }
    public int getAge() { return age; }
    public String getEmail() { return email; }
}

// Usage
Student student = new Student("John Doe", 25, "john@email.com");
```

#### 2. Factory Methods and Object Creation

```java
public class BankAccount {
    private String accountNumber;
    private String accountHolder;
    private double balance;
    private LocalDateTime createdAt;
    
    public BankAccount(String accountHolder, double initialDeposit) {
        // Call static factory method to generate account number
        this.accountNumber = generateAccountNumber();
        this.accountHolder = accountHolder;
        this.balance = initialDeposit;
        this.createdAt = LocalDateTime.now();
        
        // Call static validation method
        validateInitialDeposit(initialDeposit);
    }
    
    // Static method to generate unique account numbers
    private static String generateAccountNumber() {
        return "ACC" + System.currentTimeMillis() + Random.nextInt(1000);
    }
    
    // Static validation method
    private static void validateInitialDeposit(double amount) {
        if (amount < 0) {
            throw new IllegalArgumentException("Initial deposit cannot be negative");
        }
    }
    
    // Getters
    public String getAccountNumber() { return accountNumber; }
    public String getAccountHolder() { return accountHolder; }
    public double getBalance() { return balance; }
    public LocalDateTime getCreatedAt() { return createdAt; }
}
```

#### 3. Configuration and Setup

```java
public class DatabaseConnection {
    private String url;
    private String username;
    private String password;
    private Properties config;
    
    public DatabaseConnection(String url, String username, String password) {
        // Call static method to load configuration
        this.config = loadDefaultConfig();
        
        // Call static method to validate connection parameters
        validateConnectionParams(url, username, password);
        
        this.url = url;
        this.username = username;
        this.password = password;
    }
    
    // Static method to load default configuration
    private static Properties loadDefaultConfig() {
        Properties props = new Properties();
        try {
            props.load(DatabaseConnection.class.getResourceAsStream("db.properties"));
        } catch (IOException e) {
            // Use default values if file not found
            props.setProperty("timeout", "30");
            props.setProperty("maxConnections", "10");
        }
        return props;
    }
    
    // Static validation method
    private static void validateConnectionParams(String url, String username, String password) {
        if (url == null || url.trim().isEmpty()) {
            throw new IllegalArgumentException("Database URL cannot be null or empty");
        }
        if (username == null || username.trim().isEmpty()) {
            throw new IllegalArgumentException("Username cannot be null or empty");
        }
        if (password == null) {
            throw new IllegalArgumentException("Password cannot be null");
        }
    }
    
    public void connect() {
        System.out.println("Connecting to: " + url + " with user: " + username);
    }
}
```

#### 4. Complex Initialization Logic

```java
public class Product {
    private String id;
    private String name;
    private double price;
    private Category category;
    private List<String> tags;
    
    public Product(String name, double price, String categoryName) {
        // Call static methods for complex initialization
        this.id = generateProductId();
        this.name = name;
        this.price = price;
        this.category = Category.valueOf(categoryName.toUpperCase());
        this.tags = generateDefaultTags(categoryName);
        
        // Call static validation method
        validateProduct(name, price);
    }
    
    // Static method to generate unique product ID
    private static String generateProductId() {
        return "PROD" + System.currentTimeMillis() + "_" + Random.nextInt(9999);
    }
    
    // Static method to generate default tags based on category
    private static List<String> generateDefaultTags(String categoryName) {
        List<String> tags = new ArrayList<>();
        tags.add(categoryName.toLowerCase());
        
        // Add category-specific tags
        switch (categoryName.toLowerCase()) {
            case "electronics":
                tags.addAll(Arrays.asList("tech", "gadget", "digital"));
                break;
            case "clothing":
                tags.addAll(Arrays.asList("fashion", "style", "wear"));
                break;
            case "books":
                tags.addAll(Arrays.asList("reading", "knowledge", "education"));
                break;
            default:
                tags.add("general");
        }
        
        return tags;
    }
    
    // Static validation method
    private static void validateProduct(String name, double price) {
        if (name == null || name.trim().isEmpty()) {
            throw new IllegalArgumentException("Product name cannot be null or empty");
        }
        if (price < 0) {
            throw new IllegalArgumentException("Product price cannot be negative");
        }
        if (price > 1000000) {
            throw new IllegalArgumentException("Product price cannot exceed 1,000,000");
        }
    }
    
    // Getters
    public String getId() { return id; }
    public String getName() { return name; }
    public double getPrice() { return price; }
    public Category getCategory() { return category; }
    public List<String> getTags() { return tags; }
}

enum Category {
    ELECTRONICS, CLOTHING, BOOKS, FOOD, OTHER
}
```

### Best Practices for Using Static Methods in Constructors

#### ✅ **Good Practices:**

1. **Validation Methods:**

```java
public class Employee {
    private String name;
    private int age;
    private String email;
    
    public Employee(String name, int age, String email) {
        // Good: Static validation methods
        this.name = validateName(name);
        this.age = validateAge(age);
        this.email = validateEmail(email);
    }
    
    private static String validateName(String name) {
        if (name == null || name.trim().isEmpty()) {
            throw new IllegalArgumentException("Name cannot be null or empty");
        }
        return name.trim();
    }
    
    private static int validateAge(int age) {
        if (age < 18 || age > 65) {
            throw new IllegalArgumentException("Age must be between 18 and 65");
        }
        return age;
    }
    
    private static String validateEmail(String email) {
        if (email == null || !email.contains("@")) {
            throw new IllegalArgumentException("Invalid email format");
        }
        return email.toLowerCase();
    }
}
```

2. **Utility and Helper Methods:**

```java
public class FileProcessor {
    private String filePath;
    private String fileExtension;
    private long fileSize;
    
    public FileProcessor(String filePath) {
        // Good: Static utility methods
        this.filePath = filePath;
        this.fileExtension = getFileExtension(filePath);
        this.fileSize = getFileSize(filePath);
    }
    
    private static String getFileExtension(String path) {
        int lastDot = path.lastIndexOf('.');
        return lastDot > 0 ? path.substring(lastDot + 1) : "";
    }
    
    private static long getFileSize(String path) {
        try {
            return Files.size(Paths.get(path));
        } catch (IOException e) {
            return 0;
        }
    }
}
```

3. **Factory and Creation Methods:**

```java
public class Configuration {
    private Properties props;
    private String environment;
    
    public Configuration(String environment) {
        // Good: Static factory method
        this.environment = environment;
        this.props = loadConfiguration(environment);
    }
    
    private static Properties loadConfiguration(String env) {
        Properties props = new Properties();
        try {
            String configFile = "config-" + env + ".properties";
            props.load(Configuration.class.getResourceAsStream(configFile));
        } catch (IOException e) {
            // Load default configuration
            props = loadDefaultConfiguration();
        }
        return props;
    }
    
    private static Properties loadDefaultConfiguration() {
        Properties props = new Properties();
        props.setProperty("timeout", "30");
        props.setProperty("retry", "3");
        return props;
    }
}
```

#### ❌ **Avoid These Practices:**

1. **Calling Overridable Methods:**

```java
public class Parent {
    public Parent() {
        // Bad: Calling overridable method from constructor
        initialize();  // This could call overridden method in subclass
    }
    
    protected void initialize() {
        System.out.println("Parent initialization");
    }
}

public class Child extends Parent {
    private String name;
    
    public Child(String name) {
        super();  // Parent constructor calls initialize()
        this.name = name;
    }
    
    @Override
    protected void initialize() {
        // This runs before name is set!
        System.out.println("Child initialization: " + name);  // name is null!
    }
}
```

2. **Complex Business Logic:**

```java
public class Order {
    private String orderId;
    private double total;
    
    public Order(List<Item> items) {
        // Bad: Complex business logic in constructor
        this.orderId = generateOrderId();
        this.total = calculateTotal(items);  // Complex calculation
        processPayment();                     // Business operation
        sendNotification();                   // External service call
    }
    
    // These should not be in constructor
    private static void processPayment() { /* ... */ }
    private static void sendNotification() { /* ... */ }
}
```

## When to Use Static Methods in Constructors

### ✅ **Use Static Methods For:**

1. **Input Validation**
2. **Data Transformation**
3. **Utility Calculations**
4. **Configuration Loading**
5. **ID Generation**
6. **Default Value Creation**

### ❌ **Don't Use Static Methods For:**

1. **Complex Business Logic**
2. **External Service Calls**
3. **File I/O Operations**
4. **Database Operations**
5. **Network Calls**

### Performance Considerations

**Static methods in constructors are generally efficient because:**

- No object creation overhead
- Direct method calls
- Can be inlined by JVM
- No virtual method dispatch

```java
public class PerformanceExample {
    private String id;
    private long timestamp;
    
    public PerformanceExample() {
        // Efficient: Static method calls
        this.id = generateId();           // No object creation
        this.timestamp = getCurrentTime(); // Direct method call
    }
    
    private static String generateId() {
        return "ID" + System.currentTimeMillis();
    }
    
    private static long getCurrentTime() {
        return System.currentTimeMillis();
    }
}
```

### Summary

**Yes, you can and should use static methods in constructors for:**

- ✅ Input validation
- ✅ Data transformation
- ✅ Utility functions
- ✅ Configuration loading
- ✅ ID generation

**Key Benefits:**

- Code reusability
- Better organization
- Easier testing
- Performance efficiency

**Remember:**

- Keep constructors focused on initialization
- Use static methods for validation and utility
- Avoid complex business logic in constructors
- Be careful with overridable method calls

This approach makes your code more maintainable, testable, and follows good object-oriented design principles.

## Non-static variables, functions, and classes?

Non-static members in Java are also called **instance members** because they belong to individual instances (objects) of a class, not to the class itself. Each object has its own copy of non-static members.

### Non-static Variables (Instance Variables)

**Characteristics:**

- Belong to individual objects, not to the class
- Each object has its own copy
- Memory allocated when object is created
- Can be accessed using object reference
- Can have different values for different objects

```java
public class Student {
    // Non-static (instance) variables
    private String name;        // Each student has different name
    private int rollNumber;     // Each student has different roll number
    private double gpa;         // Each student has different GPA
    
    // Static (class) variable
    public static int totalStudents = 0;  // Shared by all students
    
    public Student(String name, int rollNumber, double gpa) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.gpa = gpa;
        totalStudents++;  // Increment static variable
    }
    
    // Getters for instance variables
    public String getName() { return name; }
    public int getRollNumber() { return rollNumber; }
    public double getGpa() { return gpa; }
    
    // Static method to get total students
    public static int getTotalStudents() { return totalStudents; }
}

// Usage
Student student1 = new Student("John", 101, 3.8);
Student student2 = new Student("Jane", 102, 3.9);

System.out.println(student1.getName());        // "John"
System.out.println(student2.getName());        // "Jane"
System.out.println(Student.getTotalStudents()); // 2
```

**Memory Layout:**

```
Class Area (Method Area)
┌─────────────────────┐
│ Student.totalStudents│ ← Shared by all instances
└─────────────────────┘

Heap Memory
┌─────────────┐  ┌─────────────┐
│ student1    │  │ student2    │
│ name: John  │  │ name: Jane  │ ← Different values
│ rollNumber: │  │ rollNumber: │ ← Different values
│ 101         │  │ 102         │
│ gpa: 3.8    │  │ gpa: 3.9    │ ← Different values
└─────────────┘  └─────────────┘
```

### Non-static Methods (Instance Methods)

**Characteristics:**

- Belong to individual objects
- Can access instance variables using `this` keyword
- Can access static members
- Can call other instance methods
- Can call static methods
- Cannot be called without object creation

```java
public class BankAccount {
    // Instance variables
    private String accountNumber;
    private double balance;
    private String accountHolder;
    
    // Static variable
    private static double interestRate = 0.05;
    
    public BankAccount(String accountNumber, String accountHolder, double initialBalance) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = initialBalance;
    }
    
    // Instance method - can access instance variables
    public void deposit(double amount) {
        if (amount > 0) {
            this.balance += amount;  // Using 'this' to access instance variable
            System.out.println("Deposited: $" + amount);
        }
    }
    
    // Instance method - can access static variables
    public void addInterest() {
        double interest = this.balance * interestRate;  // Accessing static variable
        this.balance += interest;
        System.out.println("Interest added: $" + interest);
    }
    
    // Instance method calling other instance methods
    public void transfer(BankAccount other, double amount) {
        if (this.withdraw(amount)) {  // Calling instance method
            other.deposit(amount);     // Calling instance method on other object
            System.out.println("Transfer successful");
        }
    }
    
    // Instance method calling static method
    public void displayAccountInfo() {
        System.out.println("Account: " + this.accountNumber);
        System.out.println("Holder: " + this.accountHolder);
        System.out.println("Balance: $" + this.balance);
        System.out.println("Interest Rate: " + getInterestRate() + "%");  // Calling static method
    }
    
    // Instance method
    private boolean withdraw(double amount) {
        if (amount > 0 && amount <= this.balance) {
            this.balance -= amount;
            return true;
        }
        return false;
    }
    
    // Static method
    public static double getInterestRate() {
        return interestRate * 100;  // Convert to percentage
    }
    
    // Static method to update interest rate
    public static void setInterestRate(double newRate) {
        interestRate = newRate;
    }
}

// Usage
BankAccount account1 = new BankAccount("ACC001", "John Doe", 1000);
BankAccount account2 = new BankAccount("ACC002", "Jane Smith", 2000);

account1.deposit(500);        // Instance method call
account1.addInterest();       // Instance method call
account1.transfer(account2, 300);  // Instance method call

// Static method call
BankAccount.setInterestRate(0.06);
```

### Non-static Classes (Inner Classes)

**Characteristics:**

- Defined inside another class
- Can access instance members of outer class
- Requires outer class instance to create
- Can access static members of outer class
- Can be private, protected, or public

```java
public class OuterClass {
    // Instance variables
    private String outerName;
    private int outerValue;
    
    // Static variable
    private static String staticField = "Static Field";
    
    public OuterClass(String name, int value) {
        this.outerName = name;
        this.outerValue = value;
    }
    
    // Non-static inner class
    public class InnerClass {
        private String innerName;
        
        public InnerClass(String innerName) {
            this.innerName = innerName;
        }
        
        public void display() {
            // Can access instance variables of outer class
            System.out.println("Outer Name: " + outerName);
            System.out.println("Outer Value: " + outerValue);
            System.out.println("Inner Name: " + innerName);
            
            // Can access static variables of outer class
            System.out.println("Static Field: " + staticField);
            
            // Can call instance methods of outer class
            outerMethod();
            
            // Can call static methods of outer class
            staticMethod();
        }
        
        public void updateOuter(String newName, int newValue) {
            // Can modify instance variables of outer class
            outerName = newName;
            outerValue = newValue;
        }
    }
    
    // Instance method
    public void outerMethod() {
        System.out.println("Outer method called");
    }
    
    // Static method
    public static void staticMethod() {
        System.out.println("Static method called");
    }
    
    // Method to create inner class instance
    public InnerClass createInner(String innerName) {
        return new InnerClass(innerName);
    }
}

// Usage
OuterClass outer = new OuterClass("Outer", 100);
OuterClass.InnerClass inner = outer.new InnerClass("Inner");

inner.display();
inner.updateOuter("New Outer", 200);
```

## Comparison: Static vs Non-static

| Aspect | Static (Class) | Non-static (Instance) |
|--------|----------------|----------------------|
| **Belongs to** | Class | Object |
| **Memory** | Class area, shared | Heap, individual copies |
| **Access** | Class name or object | Object reference only |
| **`this` keyword** | Not available | Available |
| **Instance variables** | Cannot access directly | Can access directly |
| **Static variables** | Can access | Can access |
| **Inheritance** | Cannot be overridden | Can be overridden |
| **Object creation** | Not required | Required |

### When to Use Non-static vs Static

#### ✅ **Use Non-static (Instance) For:**

1. **Object-specific data:**

```java
public class Person {
    private String name;        // Each person has different name
    private int age;            // Each person has different age
    private String email;       // Each person has different email
    
    public Person(String name, int age, String email) {
        this.name = name;
        this.age = age;
        this.email = email;
    }
    
    // Instance methods for object-specific operations
    public void celebrateBirthday() {
        this.age++;
        System.out.println("Happy Birthday! You are now " + this.age);
    }
    
    public void updateEmail(String newEmail) {
        this.email = newEmail;
    }
}
```

2. **Object behavior:**

```java
public class Car {
    private String model;
    private double fuelLevel;
    private boolean isRunning;
    
    public Car(String model) {
        this.model = model;
        this.fuelLevel = 100.0;
        this.isRunning = false;
    }
    
    // Instance methods for object behavior
    public void start() {
        if (fuelLevel > 0) {
            this.isRunning = true;
            System.out.println(model + " is now running");
        } else {
            System.out.println("No fuel to start the car");
        }
    }
    
    public void stop() {
        this.isRunning = false;
        System.out.println(model + " has stopped");
    }
    
    public void refuel(double amount) {
        this.fuelLevel = Math.min(100.0, this.fuelLevel + amount);
        System.out.println("Fuel level: " + this.fuelLevel + "%");
    }
}
```

3. **Object state management:**

```java
public class ShoppingCart {
    private List<Item> items;
    private String customerId;
    private LocalDateTime createdAt;
    
    public ShoppingCart(String customerId) {
        this.customerId = customerId;
        this.items = new ArrayList<>();
        this.createdAt = LocalDateTime.now();
    }
    
    // Instance methods for state management
    public void addItem(Item item) {
        this.items.add(item);
    }
    
    public void removeItem(Item item) {
        this.items.remove(item);
    }
    
    public double getTotal() {
        return this.items.stream()
                .mapToDouble(Item::getPrice)
                .sum();
    }
    
    public int getItemCount() {
        return this.items.size();
    }
}
```

#### ✅ **Use Static For:**

1. **Utility functions:**

```java
public class MathUtils {
    public static int add(int a, int b) { return a + b; }
    public static int multiply(int a, int b) { return a * b; }
    public static boolean isEven(int n) { return n % 2 == 0; }
}
```

2. **Constants:**

```java
public class Constants {
    public static final String APP_NAME = "My Application";
    public static final int MAX_RETRY_ATTEMPTS = 3;
    public static final double PI = 3.14159;
}
```

3. **Factory methods:**

```java
public class ConnectionFactory {
    public static Connection createConnection(String url) {
        // Connection creation logic
        return new Connection(url);
    }
}
```

### Real-World Example: E-commerce System

```java
public class Product {
    // Instance variables - each product is different
    private String productId;
    private String name;
    private double price;
    private int stockQuantity;
    private String category;
    private LocalDateTime createdAt;
    
    // Static variables - shared by all products
    private static int totalProducts = 0;
    private static double taxRate = 0.08;
    
    public Product(String name, double price, int stockQuantity, String category) {
        this.productId = generateProductId();
        this.name = name;
        this.price = price;
        this.stockQuantity = stockQuantity;
        this.category = category;
        this.createdAt = LocalDateTime.now();
        
        totalProducts++;  // Increment static counter
    }
    
    // Instance methods - operate on individual product
    public void updateStock(int newQuantity) {
        if (newQuantity >= 0) {
            this.stockQuantity = newQuantity;
        }
    }
    
    public void applyDiscount(double discountPercentage) {
        if (discountPercentage > 0 && discountPercentage <= 100) {
            this.price = this.price * (1 - discountPercentage / 100);
        }
    }
    
    public double getPriceWithTax() {
        return this.price * (1 + taxRate);  // Using static variable
    }
    
    public boolean isInStock() {
        return this.stockQuantity > 0;
    }
    
    public void displayInfo() {
        System.out.println("Product ID: " + this.productId);
        System.out.println("Name: " + this.name);
        System.out.println("Price: $" + this.price);
        System.out.println("Stock: " + this.stockQuantity);
        System.out.println("Category: " + this.category);
        System.out.println("Created: " + this.createdAt);
        System.out.println("Price with Tax: $" + getPriceWithTax());
    }
    
    // Static methods - operate on class level
    public static int getTotalProducts() {
        return totalProducts;
    }
    
    public static void setTaxRate(double newRate) {
        if (newRate >= 0) {
            taxRate = newRate;
        }
    }
    
    public static double getTaxRate() {
        return taxRate;
    }
    
    // Private static method for internal use
    private static String generateProductId() {
        return "PROD" + System.currentTimeMillis() + "_" + Random.nextInt(9999);
    }
    
    // Getters
    public String getProductId() { return productId; }
    public String getName() { return name; }
    public double getPrice() { return price; }
    public int getStockQuantity() { return stockQuantity; }
    public String getCategory() { return category; }
    public LocalDateTime getCreatedAt() { return createdAt; }
}

// Usage
Product laptop = new Product("Laptop", 999.99, 10, "Electronics");
Product book = new Product("Java Programming", 49.99, 25, "Books");

laptop.updateStock(5);           // Instance method
laptop.applyDiscount(10);        // Instance method
laptop.displayInfo();            // Instance method

System.out.println("Total Products: " + Product.getTotalProducts());  // Static method
Product.setTaxRate(0.10);        // Static method
```

### Summary

**Non-static (Instance) Members:**

- Belong to individual objects
- Each object has its own copy
- Can access instance variables with `this`
- Can access static members
- Require object creation to use

**Key Differences:**

- **Memory**: Instance members in heap, static in class area
- **Access**: Instance members need object reference, static can use class name
- **Behavior**: Instance members can be overridden, static cannot
- **Usage**: Instance for object-specific data/behavior, static for shared utilities

**Best Practices:**

- Use instance members for object-specific data and behavior
- Use static members for utilities, constants, and shared functionality
- Keep instance methods focused on object state
- Use static methods for operations that don't need object state

This understanding is crucial for designing effective Java classes and understanding object-oriented programming principles.
