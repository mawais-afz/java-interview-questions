# Core Java & OOP Fundamentals

## JVM, JDK, JRE

### What is the difference between JDK, JRE, and JVM?

#### **1. JVM (Java Virtual Machine)**

- **What it is:** A virtual machine that runs Java bytecode.
- **Role:** Converts compiled Java code (bytecode: `.class` files) into machine code for the underlying operating system.
- **Platform independence:** The reason “**Write Once, Run Anywhere**” works — because JVM abstracts away the OS details.
- **Contains:** Just the runtime engine, memory management (Garbage Collector), and execution environment.

👉 Think of **JVM** as the **engine** that actually runs your Java program.

---

#### **2. JRE (Java Runtime Environment)**

- **What it is:** A package that provides everything needed to run Java programs.
- **Contains:**
  - **JVM**
  - Core **Java class libraries** (like `java.util.*`, `java.io.*`, etc.)
  - Supporting files
- **What it doesn’t have:** Tools for development (like `javac`, debugger).

👉 Think of **JRE** as the **car + engine**, where you can **drive/run** programs but can’t build a new car.

---

#### **3. JDK (Java Development Kit)**

- **What it is:** A superset of JRE used for **developing** Java applications.
- **Contains:**
  - **JRE** (so it also has the JVM + libraries)
  - Development tools:
    - `javac` (Java compiler)
    - `javadoc`
    - Debuggers
    - Other utilities

👉 Think of **JDK** as the **car factory**: it has tools to **build** cars (Java programs), and it also contains the car (JRE) so you can test/run them.

---

#### **Quick Comparison Table**

| Feature                    | JVM                        | JRE                              | JDK                                  |
| -------------------------- | -------------------------- | -------------------------------- | ------------------------------------ |
| **Purpose**                | Runs Java bytecode         | Provides environment to run Java | Provides environment to develop Java |
| **Includes**               | Execution engine, GC, etc. | JVM + libraries                  | JRE + development tools              |
| **Used By**                | Runtime (end user + dev)   | End users (run apps)             | Developers (build + run apps)        |
| **Can run Java program?**  | ✅                         | ✅                               | ✅                                   |
| **Can compile Java code?** | ❌                         | ❌                               | ✅                                   |

---

👉 **Summary in one line:**

- **JVM** → Runs Java bytecode.
- **JRE** → JVM + libraries → To **run** Java apps.
- **JDK** → JRE + tools → To **develop + run** Java apps.

---

### Why is Java platform-independent?

Java is **platform-independent** because of its **“write once, run anywhere” (WORA)** architecture, which relies on the **JVM and bytecode**.

1. **Compilation to Bytecode**  
   - Java source code (`.java`) is compiled by `javac` into **platform-neutral bytecode** (`.class`).  
   - Bytecode is **not native machine code**, so it is portable across platforms.

2. **Execution via JVM**  
   - Each platform (Windows, Linux, macOS) has its own **JVM implementation**.  
   - JVM translates bytecode → platform-specific machine code at runtime using **JIT compilation**.  
   - ∴ The same bytecode runs unmodified on any system with a compatible JVM.

3. **Standard Libraries (Java API)**  
   - Java provides a **consistent API** across platforms.  
   - Application behavior is standardized regardless of the underlying OS.

**Flow:**  

```
Java Source (.java) → javac → Bytecode (.class) → JVM → Native Machine Code → Execution
```

🔧 **Key Point:** Platform independence is achieved **at the bytecode + JVM level**, not by avoiding OS-specific dependencies.  

This separation allows enterprises to deploy the same Java application on multiple OSes **without recompilation**.

### What is bytecode in java?

Bytecode is the **intermediate, platform-independent representation** of a Java program, produced by the Java compiler (`javac`) from `.java` source files. It is stored in `.class` files.

**Characteristics:**  

- **Platform-neutral:** Can run on any OS with a compatible JVM.  
- **Not human-readable:** Encoded instructions for the JVM, not native machine code.  
- **Compact and efficient:** Optimized for JVM execution.  
- **Enables security:** JVM can perform verification before execution.

**Execution Flow:**  

```doc
Java Source (.java) → javac → Bytecode (.class) → JVM → Native Machine Code → Execution
```

**Purpose:**  

- Ensures **“Write Once, Run Anywhere” (WORA)**.  
- Allows **JIT compilation** within JVM for runtime performance optimization.  
- Provides a **layer of abstraction** between source code and underlying hardware.  

🔧 **Example:**  

```java
int x = 5;
```

Compiles to bytecode instruction like `iconst_5` → JVM interprets and executes it.  

Bytecode acts as the **bridge between Java source code and platform-specific execution**.

### What is JIT compiler?

The **Just-In-Time (JIT) compiler** is a component of the JVM that **dynamically translates Java bytecode into native machine code at runtime** to improve execution performance.  

**Key Points:**  

- **Runtime Compilation:** Unlike `javac`, which compiles source → bytecode ahead of time, JIT compiles **bytecode → native code during program execution**.  
- **Performance Optimization:** Frequently executed code (“hot spots”) is compiled into optimized machine code for faster execution.  
- **Integration with JVM:** Works with JVM’s interpreter; JVM may interpret bytecode initially, then JIT-compile hot methods.  
- **Adaptive Optimization:** JVM profiles code execution to decide which parts to compile for maximum efficiency.  

**Execution Flow:**  

```doc
Java Source (.java) → javac → Bytecode (.class) → JVM Interpreter (initial execution)
                           ↘ JIT Compiler (for hot spots) → Native Machine Code → Execution
```

**Benefits:**  

- ↗ Faster execution compared to interpreted bytecode.  
- ↗ Efficient memory usage via selective compilation.  
- Supports platform-independent code with near-native performance.  

🔧 **Example:**  
A method invoked repeatedly will be JIT-compiled so subsequent calls execute **directly as native instructions**, avoiding repeated interpretation overhead.  

The JIT compiler is **essential for balancing Java’s platform independence with high runtime performance**.

## Data Types & Variables

### What are primitive and non-primitive data types in Java?

#### **1. Primitive Data Types**  

- **Definition:** Basic, predefined data types provided by Java.  
- **Stored:** Directly in memory (stack).  
- **Characteristics:** Fast, fixed size, not objects, cannot call methods directly.  

| Type      | Size       | Description                  | Default Value |
|-----------|------------|-----------------------------|---------------|
| `byte`    | 1 byte     | Integer (-128 to 127)       | 0             |
| `short`   | 2 bytes    | Integer (-32,768 to 32,767)| 0             |
| `int`     | 4 bytes    | Integer                     | 0             |
| `long`    | 8 bytes    | Integer                     | 0L            |
| `float`   | 4 bytes    | Floating-point number       | 0.0f          |
| `double`  | 8 bytes    | Floating-point number       | 0.0d          |
| `char`    | 2 bytes    | Single Unicode character    | '\u0000'     |
| `boolean` | 1 bit      | `true` or `false`           | false         |

---

#### **2. Non-Primitive Data Types**  

- **Definition:** Reference types; objects created from classes, interfaces, or arrays.  
- **Stored:** Reference in stack → actual object in heap.  
- **Characteristics:** Can call methods, flexible size, `null` default value.  

**Examples:**  

- `String`  
- Arrays (`int[]`, `String[]`)  
- Classes (`Integer`, `Scanner`, `CustomClass`)  
- Interfaces (`Runnable`, `List`)  

**Key Differences:**  

| Feature              | Primitive                 | Non-Primitive           |
|----------------------|--------------------------|------------------------|
| Memory               | Stack                    | Heap (reference stored in stack) |
| Methods              | None                     | Yes                    |
| Default Value        | Type-specific (0, false) | `null`                 |
| Size                 | Fixed                    | Variable               |
| Examples             | `int`, `boolean`         | `String`, `Integer`    |

🔧 **Summary:**  
Primitives → efficient, basic data.  
Non-primitives → objects with methods and dynamic behavior.  

If you want, I can also explain **autoboxing/unboxing**, which bridges primitives and non-primitives seamlessly.

### What are wrapper classes?

**Definition:**  
Wrapper classes are **object representations of Java’s primitive data types**. They allow primitives to be treated as objects, enabling use in **collections, generics, and APIs** that require objects.  

| Primitive Type | Wrapper Class |
|----------------|---------------|
| `byte`         | `Byte`        |
| `short`        | `Short`       |
| `int`          | `Integer`     |
| `long`         | `Long`        |
| `float`        | `Float`       |
| `double`       | `Double`      |
| `char`         | `Character`   |
| `boolean`      | `Boolean`     |

**Key Points:**  

- All wrapper classes are **immutable**.  
- Provide **utility methods** (e.g., `Integer.parseInt()`, `Double.valueOf()`).  
- Enable **autoboxing/unboxing** between primitives and objects.  
- Useful in **collections** (`List<Integer>`, `Map<Character, String>`), since collections cannot store primitives directly.  

**Example:**  

```java
int num = 100;
// Autoboxing: primitive → wrapper
Integer wrapperNum = num;

// Unboxing: wrapper → primitive
int original = wrapperNum;
```

🔧 **Summary:**  
Wrapper classes bridge **primitives ↔ objects**, providing **method support, collection compatibility, and utility operations**.  

### What is autoboxing and unboxing?**  

**Definition:**  

- **Autoboxing:** Automatic conversion of a **primitive type → corresponding wrapper class object**.  
- **Unboxing:** Automatic conversion of a **wrapper class object → corresponding primitive type**.  

**Examples:**  

```java
// Autoboxing: primitive → wrapper
int num = 10;
Integer wrapperNum = num;  // compiler converts to Integer.valueOf(num)

// Unboxing: wrapper → primitive
Integer wrapperVal = 20;
int original = wrapperVal; // compiler converts to wrapperVal.intValue()
```

**Key Points:**  

- Introduced in **Java 5** to simplify primitive-object conversion.  
- Enables seamless use of primitives in **collections** and **generic APIs**.  
- Works for all 8 primitive types and their corresponding wrapper classes.  
- Reduces **manual boxing/unboxing** errors and boilerplate code.  

**Flow:**  

```doc
Primitive ↔ Wrapper (automatic by compiler)
```

🔧 **Example Use Case:**  

```java
List<Integer> list = new ArrayList<>();
list.add(5);   // Autoboxing: int → Integer
int x = list.get(0); // Unboxing: Integer → int
```

This ensures smooth interaction between **primitives** and **object-oriented features** like collections.

### Difference b/w Autoboxing vs Unboxing

| Feature                | **Autoboxing**                              | **Unboxing**                            |
|------------------------|--------------------------------------------|----------------------------------------|
| **Definition**         | Conversion of **primitive → wrapper object** automatically by the compiler. | Conversion of **wrapper object → primitive** automatically by the compiler. |
| **Direction**          | Primitive → Wrapper                         | Wrapper → Primitive                     |
| **Example**            | `int i = 5; Integer obj = i;`               | `Integer obj = 10; int i = obj;`       |
| **Introduced in**      | Java 5                                     | Java 5                                  |
| **Purpose**            | Allows primitives to be used in **collections, generics, APIs** that require objects. | Allows wrapper objects to behave like primitives in **calculations or operations**. |
| **Compiler Action**    | Calls `Integer.valueOf()`, `Double.valueOf()`, etc. | Calls `intValue()`, `doubleValue()`, etc. |

🔧 **Summary:**  

- **Autoboxing:** primitive → object  
- **Unboxing:** object → primitive  

This mechanism provides **seamless interoperability** between **primitives and objects** in modern Java.

### What are constants and how to create constants in java?

A **constant** is a variable whose value **cannot be changed once initialized**. Constants improve **code readability, maintainability, and prevent accidental modification**.  

---

#### **How to Create Constants in Java**

1. **Using `final` keyword**  
   - `final` makes a variable immutable after initialization.  

   ```java
   final int MAX_USERS = 100;
   final double PI = 3.14159;
   ```

2. **Class-level constants (static final)**  
   - Shared across all instances; accessed via class name.  

   ```java
   public class Constants {
       public static final int MAX_CONNECTIONS = 50;
       public static final String APP_NAME = "MyApp";
   }
   
   // Usage
   int connections = Constants.MAX_CONNECTIONS;
   ```

3. **Local constants**  
   - Can be defined inside methods with `final`.  

   ```java
   void calculateArea() {
       final double TAX_RATE = 0.15;
   }
   ```

---

#### **Key Points**  

- `final` → makes variable immutable.  
- `static final` → **compile-time constant**, shared across instances.  
- Naming convention: usually **UPPER_CASE** with underscores.  
- Constants can be **primitive types, Strings, or objects** (but object reference is final; object state may still be mutable).  

🔧 **Example of Object Constant:**  

```java
public static final List<String> DAYS = Collections.unmodifiableList(
    Arrays.asList("Mon", "Tue", "Wed")
);
```

- Ensures the list cannot be modified.  

Constants enforce **immutability** and help in **maintaining predictable, error-free code**.

### What are local and global variables?**  

| Feature              | **Local Variable**                          | **Global Variable (Instance/Class Variable)**       |
|----------------------|--------------------------------------------|---------------------------------------------------|
| **Definition**       | Declared inside a method, constructor, or block. | Declared inside a class but outside any method, constructor, or block. |
| **Scope**            | Accessible **only within the block/method** where declared. | Accessible throughout the class (object-level or class-level). |
| **Lifetime**         | Exists **only during method execution**. Destroyed after method exits. | Exists **as long as the object exists** (instance) or **for the lifetime of the class** (static). |
| **Default Value**    | No default; must be explicitly initialized. | Instance variables: default values (0, null, false). Static variables: default values. |
| **Declaration Example** | `void calculate() { int x = 10; }`         | `class Demo { int a; static int b; }`            |
| **Memory Area**      | Stack                                      | Heap (instance variables) / Method Area (static variables) |

**Key Notes:**  

- Local variables are **temporary and method-specific**.  
- Global variables (instance/static) maintain **state across method calls**.  
- Best practice: minimize global variables to reduce **side effects** and improve **thread-safety**.  

🔧 **Example:**  

```java
class Example {
    int instanceVar = 5;           // instance/global variable
    static int staticVar = 10;     // class/global variable

    void method() {
        int localVar = 20;         // local variable
        System.out.println(localVar + instanceVar + staticVar);
    }
}
```  

Local variables → temporary, method-scoped.  
Global variables → persist with object or class lifetime.

### What is a compile-time constant in Java?
  
A **compile-time constant** is a value that is **known and fixed at the time of compilation** and cannot be modified at runtime. The Java compiler can **replace references to the constant directly with its value**.  

---

#### **Characteristics**

- Declared using **`final`** keyword.  
- Must be **initialized at the point of declaration**.  
- Usually **primitive types** or `String` literals.  
- `static final` variables are typical examples of compile-time constants.  
- Value **cannot be changed**, ensuring immutability.

---

#### **Example**

```java
public class Constants {
    public static final int MAX_USERS = 100;  // compile-time constant
    public static final String APP_NAME = "MyApp"; // compile-time constant
}
```

- Compiler replaces `MAX_USERS` with `100` wherever it is used.  
- Efficient because no memory lookup is needed at runtime.  

---

#### **Key Points**

- Must be **`final`** and **initialized immediately**.  
- Can be **primitive types or `String` literals** only; cannot be objects initialized at runtime.  
- Improves **performance** and **code readability**.  

🔧 **Summary:**  
Compile-time constants → **immutable, known at compile time, and optimized by the compiler**.  

### What is coercion in Java?

**Coercion** in Java refers to the **automatic or explicit conversion of a value from one data type to another** to make an expression compatible or evaluable.  

There are two types of coercion:

---

#### **1. Implicit Coercion (Type Casting / Type Promotion)**

- Java **automatically converts smaller or compatible data types** to a larger type when needed.  
- Also called **type promotion**.  
- Happens **at compile time**.  

**Example:**

```java
int i = 10;
double d = i;  // int → double (implicit coercion)
```

- `i` is promoted to `double` automatically.

**Rules for numeric types:**  
`byte → short → int → long → float → double`

---

#### **2. Explicit Coercion (Type Casting)**

- Done **manually by the programmer** using parentheses.  
- Required when converting **larger type → smaller type** or incompatible types.  

**Example:**

```java
double d = 9.78;
int i = (int) d;  // double → int (explicit coercion)
```

- Fractional part is truncated.  

---

#### **Key Points**

- Ensures **type compatibility in expressions**.  
- Implicit coercion is safe; explicit coercion may cause **data loss**.  
- Applies to **primitives** and can also be used with **object references** (upcasting/downcasting).  

🔧 **Summary:**  
Coercion → **automatic or manual conversion between data types** to satisfy type requirements in operations or assignments.

### What is ASCII Code?

**ASCII (American Standard Code for Information Interchange)** is a **character encoding standard** that maps **characters to numeric values** so that computers can store and manipulate text.  

---

#### **Key Points**

- **7-bit encoding** → represents **128 characters** (`0–127`).  
- Includes:
  - Control characters (0–31) → e.g., `\n` (newline), `\t` (tab)  
  - Printable characters (32–126) → letters, digits, punctuation, symbols  
- **Each character is represented by an integer value**.

**Examples:**  

| Character | ASCII Value |
|-----------|------------|
| `A`       | 65         |
| `a`       | 97         |
| `0`       | 48         |
| `\n`      | 10         |

---

#### **Usage in Java**

- Characters can be implicitly converted to integers using **type casting**:

```java
char ch = 'A';
int ascii = (int) ch; // ascii = 65

int num = 66;
char character = (char) num; // character = 'B'
```

🔧 **Summary:**  
ASCII provides a **numerical representation of characters**, allowing text to be processed and stored efficiently in computers.  

### What is Unicode?

**Unicode** is a **universal character encoding standard** that assigns a **unique code point to every character** from virtually all writing systems, symbols, and emojis, enabling **cross-platform and multilingual text support**.  

---

#### **Key Points**

- **16-bit encoding** in Java (`char` type) → represents **0 to 65,535** code points.  
- Supports **all major languages, symbols, and special characters**, unlike ASCII which supports only 128 characters.  
- **Java uses Unicode internally** for `char` and `String`, ensuring **platform-independent text handling**.  

**Examples:**

```java
char ch = 'अ';          // Devanagari character
int codePoint = (int) ch; // Unicode value: 2309

char smiley = '\u263A'; // Unicode escape sequence for ☺
```

---

#### **Comparison with ASCII**

| Feature        | ASCII            | Unicode               |
|----------------|----------------|---------------------|
| Bits           | 7-bit           | 16-bit (Java char)  |
| Characters     | 128             | 65,536+             |
| Language Support| English only   | All major languages |
| Java Usage     | Limited         | Standard for char/String |

🔧 **Summary:**  
Unicode ensures **consistent, cross-platform representation of global text**, making Java capable of handling **multilingual and special characters seamlessly**.

### Difference between Character Constant and String Constant in java?Differences**  

| Feature                     | **Character Constant** (`char`)                     | **String Constant** (`String`)                     |
|-------------------------------|---------------------------------------------------|--------------------------------------------------|
| **Definition**               | Single character literal enclosed in **single quotes** (`'A'`). | Sequence of characters enclosed in **double quotes** (`"Hello"`). |
| **Data Type**                 | `char` (primitive type)                           | `String` (non-primitive/reference type)         |
| **Length**                    | Exactly **1 character**                           | Can be **0 or more characters**                 |
| **Memory Storage**            | Stores **Unicode value** (16-bit)                | Stores **object reference** pointing to character array in heap |
| **Immutability**              | Not applicable (primitive)                        | **Immutable object** in Java                     |
| **Usage**                     | For **single character operations**               | For **text, multiple character sequences**      |
| **Example**                   | `char ch = 'A';`                                 | `String str = "Hello";`                          |

🔧 **Summary:**  

- **Character constants** → single Unicode character, primitive.  
- **String constants** → sequence of characters, immutable object.  

This distinction is crucial for **memory management, operations, and method compatibility** in Java.

## Classes & Objects

### What is a class?

A **class** is a **blueprint or template** for creating objects in Java. It encapsulates **data (fields/attributes) and behavior (methods)** into a single unit, following **Object-Oriented Programming (OOP) principles**.  

---

#### **Key Points**

- Defines the **structure and behavior** of objects.  
- Supports **encapsulation**, **inheritance**, and **polymorphism**.  
- Can include:
  - **Fields/Variables** – to store object state  
  - **Methods/Functions** – to define behavior  
  - **Constructors** – to initialize objects  
  - **Nested classes, static blocks, and initializer blocks**  

---

#### **Syntax Example**

```java
public class Car {
    // Fields (attributes)
    private String model;
    private int year;

    // Constructor
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
    }

    // Method (behavior)
    public void displayInfo() {
        System.out.println("Model: " + model + ", Year: " + year);
    }
}
```

---

#### **Usage**

```java
Car myCar = new Car("Tesla", 2023); // Object creation
myCar.displayInfo();                // Method invocation
```

🔧 **Summary:**  
A **class** defines the **blueprint**; an **object** is the **instance**. It is the core building block of **Java’s OOP paradigm**, encapsulating **state and behavior**.

### What is a Constructor in Java? Types of constructors?

A **constructor** is a **special method** in Java used to **initialize objects** of a class. It has the **same name as the class** and **no return type**, not even `void`.  

---

#### **Key Points**

- Invoked automatically when an object is created using `new`.  
- Can initialize **fields/attributes** or perform setup tasks.  
- Supports **overloading** (multiple constructors with different parameters).  
- Cannot be **abstract, static, final, or synchronized**.  

---

#### **Types of Constructors**

1. **Default Constructor (No-Arg Constructor)**  
   - Provided by Java if **no constructor is explicitly defined**.  
   - Initializes object with **default values**.  

   ```java
   class Car {
       String model;
       int year;
       
       Car() {  // Default constructor
           model = "Unknown";
           year = 0;
       }
   }
   ```

2. **Parameterized Constructor**  
   - Accepts **arguments** to initialize object with specific values.  

   ```java
   class Car {
       String model;
       int year;
       
       Car(String model, int year) { // Parameterized constructor
           this.model = model;
           this.year = year;
       }
   }
   ```

3. **Copy Constructor (Optional Concept in Java)**  
   - Creates a **new object as a copy** of an existing object.  

   ```java
   class Car {
       String model;
       int year;
       
       Car(Car c) { // Copy constructor
           this.model = c.model;
           this.year = c.year;
       }
   }
   ```

---

#### **Example Usage**

```java
Car c1 = new Car();               // Default constructor
Car c2 = new Car("Tesla", 2023);  // Parameterized constructor
Car c3 = new Car(c2);             // Copy constructor
```

🔧 **Summary:**  
Constructors **initialize objects**, ensuring proper setup of state.  

- **Default constructor** → no arguments  
- **Parameterized constructor** → custom initialization  
- **Copy constructor** → duplicate object creation  

This is essential for **object-oriented design and safe object initialization** in Java.

### How to call one constructor from the other constructor?  

In Java, you can call one constructor from another **within the same class** using the keyword **`this()`**. This is known as **constructor chaining** and helps **avoid code duplication**.  

---

#### **Key Rules**

1. `this()` **must be the first statement** in the constructor.  
2. Can be used to call **any constructor in the same class** (default, parameterized).  
3. Helps maintain **centralized initialization logic**.  

---

#### **Example**

```java
class Car {
    String model;
    int year;

    // Default constructor
    Car() {
        this("Unknown", 0);  // Calls parameterized constructor
    }

    // Parameterized constructor
    Car(String model, int year) {
        this.model = model;
        this.year = year;
    }

    void display() {
        System.out.println("Model: " + model + ", Year: " + year);
    }
}

public class Main {
    public static void main(String[] args) {
        Car c1 = new Car();           // Calls default → parameterized
        Car c2 = new Car("Tesla", 2023); // Directly calls parameterized
        c1.display();  // Model: Unknown, Year: 0
        c2.display();  // Model: Tesla, Year: 2023
    }
}
```

---

#### **Summary**

- Use **`this()`** for **constructor chaining within the same class**.  
- Ensures **code reuse** and **consistent initialization**.  
- Must always appear as the **first line** in the constructor.  

This pattern improves **maintainability** in complex classes with multiple constructors.

### Will the compiler create a default constructor if I have a parameterized constructor in the class?Constructor in Java**  

**Rule:**  

- The **Java compiler provides a default (no-arg) constructor** **only if no constructors are explicitly defined** in the class.  
- **If you define any constructor** (including a parameterized one), **the compiler does NOT generate a default constructor automatically**.  

---

#### **Example**

```java
class Car {
    String model;

    // Parameterized constructor
    Car(String model) {
        this.model = model;
    }
}

public class Main {
    public static void main(String[] args) {
        Car c1 = new Car(); // ❌ Compile-time error: no default constructor
    }
}
```

**Fix:** Explicitly define a no-arg constructor if needed:

```java
class Car {
    String model;

    Car() {           // Explicit default constructor
        model = "Unknown";
    }

    Car(String model) { // Parameterized constructor
        this.model = model;
    }
}
```

---

#### **Summary**

- ✅ Compiler creates default constructor **only if no constructors exist**.  
- ❌ If **any constructor is defined**, default constructor must be **explicitly declared** if required.  

This ensures **controlled initialization** and avoids unintended object creation.

### What is the difference between a constructor and a method in Java?

| Feature                  | **Constructor**                                 | **Method**                                    |
|---------------------------|------------------------------------------------|-----------------------------------------------|
| **Purpose**              | To **initialize an object**                     | To **perform a specific operation or behavior** |
| **Name**                 | Must be **same as class name**                  | Can have **any valid identifier**             |
| **Return Type**          | **No return type**, not even `void`            | Must have a **return type** (void or any type) |
| **Invocation**           | Called **automatically** during object creation | Called **explicitly** on object or class      |
| **Overloading/Overriding**| Can be **overloaded** but **cannot be overridden** | Can be **overloaded and overridden**          |
| **Inheritance**          | Not inherited                                   | Inherited according to access modifiers       |
| **Static**               | Cannot be static                                | Can be static                                 |
| **Example**              | `Car() { this.model = "Tesla"; }`              | `void display() { System.out.println(model); }` |

---

#### **Summary**

- **Constructor:** Special method for **object initialization**, no return type, name = class.  
- **Method:** Defines **behavior/operations**, has a return type, can be called multiple times.  

🔧 **Key Point:**  
Constructors **set up object state**, methods **act on object state or perform tasks**.

### What is a static keyword? Static variables and methods?

**Definition:**  
The `static` keyword in Java is used to **define class-level members** that **belong to the class itself** rather than to any specific object.  

---

#### **Static Variables (Class Variables)**

- Shared by **all instances of a class**.  
- Stored in **method area**, not in individual object memory.  
- Initialized when the **class is loaded**.  

**Example:**

```java
class Car {
    static int totalCars = 0; // Static variable

    Car() {
        totalCars++; // Increment for every object created
    }
}

public class Main {
    public static void main(String[] args) {
        new Car();
        new Car();
        System.out.println(Car.totalCars); // Output: 2
    }
}
```

---

#### **Static Methods (Class Methods)**

- Belong to the **class**, can be called **without creating an object**.  
- Can **access only static variables/methods** directly.  
- Cannot use `this` or instance variables directly.  

**Example:**

```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}

public class Main {
    public static void main(String[] args) {
        int result = MathUtil.square(5); // No object creation needed
        System.out.println(result); // Output: 25
    }
}
```

---

#### **Key Points**

- Static members → **class-level**, shared across objects.  
- Useful for **constants, utility methods, counters**.  
- Accessed using **ClassName.memberName**.  

🔧 **Summary:**  

- **Static variable:** Shared state among all objects.  
- **Static method:** Class-level behavior that can operate on static variables without object instances.

---

### Can we use static methods in a Constructor?

**Rule:**  

- **Yes**, you can call **static methods from a constructor** in Java.  
- **Reason:** Static methods belong to the **class**, not the object, so they are already available when the constructor executes.  

#### **Key Points**

1. **Direct call:** You can invoke a static method **directly** inside a constructor.  
2. **No object needed:** Static methods do not require an object reference.  
3. **Cannot access instance members** from a static method, but constructors **can access both static and instance members**.  

#### **Example**

```java
class Car {
    String model;

    Car(String model) {
        this.model = model;
        printWelcomeMessage(); // Calling static method
    }

    static void printWelcomeMessage() {
        System.out.println("Welcome to the Car class!");
    }
}

public class Main {
    public static void main(String[] args) {
        Car c1 = new Car("Tesla"); 
        // Output: Welcome to the Car class!
    }
}
```

#### **Summary**

- ✅ Static methods **can be called** inside constructors.  
- ✅ Constructors can access **both instance and static members**.  
- ❌ Static methods **cannot access instance variables/methods** directly.  

This allows **utility or common operations** to be performed during object initialization without needing object references.

---

### Can Static methods access instance variables in java?

**Rule:**  

- **No**, static methods **cannot directly access instance (non-static) variables** or instance methods.  
- **Reason:**  
  - Static methods belong to the **class**, not any particular object.  
  - Instance variables exist **per object**, so without an object reference, the static method has no access to them.  

---

### **How to Access Instance Variables in a Static Method**

1. **Using an object reference**:

    ```java
    class Car {
        String model;

        Car(String model) {
            this.model = model;
        }

        static void printModel(Car c) {
            System.out.println(c.model); // Access via object
        }
    }

    public class Main {
        public static void main(String[] args) {
            Car car1 = new Car("Tesla");
            Car.printModel(car1); // Output: Tesla
        }
    }
    ```

2. **Cannot do this directly:**  

    ```java
    class Car {
        String model;
        static void display() {
            System.out.println(model); // ❌ Compile-time error
        }
    }
    ```

---

#### **Key Points**

- Static method → belongs to class → cannot access **instance members** directly.  
- Can only access **static variables or static methods** directly.  
- Instance variables require an **object reference** for access.  

🔧 **Summary:**  
Static methods are **class-level**, instance variables are **object-level** → direct access is not allowed; object reference is required.

### How do we access static members in java?

Static members (variables or methods) belong to the **class**, not individual objects. They can be accessed **without creating an instance** of the class.  

---

#### **Ways to Access Static Members**

1. **Using Class Name (Recommended)**  

    ```java
    class Car {
        static int totalCars = 0;

        static void displayTotalCars() {
            System.out.println("Total Cars: " + totalCars);
        }
    }

    public class Main {
        public static void main(String[] args) {
            Car.totalCars = 5;          // Access static variable
            Car.displayTotalCars();      // Access static method
        }
    }
    ```

2. **Using Object Reference (Not Recommended)**  

    ```java
    Car car1 = new Car();
    car1.totalCars = 10;        // Works, but misleading
    car1.displayTotalCars();    // Works, but still refers to class-level member
    ```

> ⚠️ Using objects for static members can confuse readers; always prefer **ClassName.memberName**.

---

#### **Key Points**

- Static members are **loaded when the class is loaded** → accessible before object creation.  
- Can be used for **utility methods, constants, counters, and shared resources**.  
- Static methods **cannot access instance members directly**.  

🔧 **Summary:**  

- **Preferred way:** `ClassName.staticMember`  
- **Alternative:** `object.staticMember` (works but not recommended)  
- Ensures **clarity and proper use of class-level members**.

### Can we override static methods in java?

**Rule:**  

- **No**, static methods **cannot be overridden** in Java.  
- **Reason:**  
  - Static methods belong to the **class**, not to an instance.  
  - Method overriding requires **runtime polymorphism**, which is based on **object instances**, so static methods are **resolved at compile-time** (early binding).  

---

#### **What Happens Instead**

- If a subclass defines a static method with the **same signature** as a static method in the superclass, it is called **method hiding**, not overriding.  
- Compiler binds the method call based on the **reference type**, not the object type.  

---

#### **Example**

```java
class Parent {
    static void display() {
        System.out.println("Parent static method");
    }
}

class Child extends Parent {
    static void display() {
        System.out.println("Child static method");
    }
}

public class Main {
    public static void main(String[] args) {
        Parent p = new Child();
        p.display(); // Output: Parent static method (compile-time binding)

        Child.display(); // Output: Child static method
    }
}
```

---

#### **Key Points**

- Static methods → **class-level**, resolved at **compile-time**.  
- Cannot participate in **runtime polymorphism**.  
- Method hiding is **different from overriding**.  

🔧 **Summary:**  

- ❌ Static methods **cannot be overridden**.  
- ✅ They can be **hidden** by a subclass method with the same signature.  
- Access depends on **reference type**, not object type.

### What are static blocks and static initializers in Java?Explanation**  

- A **static block** (or static initializer) is a block of code inside a class that is **executed when the class is loaded**, **before any object is created** or any static method is called.  
- Used for **class-level initialization**, such as initializing static variables or performing setup tasks.  

---

#### **Key Points**

1. **Executed only once** when the class is loaded by JVM.  
2. Useful for **complex initialization** that cannot be done in a single statement.  
3. Can have **multiple static blocks**; executed in **order of appearance**.  
4. Runs **before main()** if the class contains a main method.  

---

#### **Syntax & Example**

```java
class Config {
    static int MAX_USERS;
    static String APP_NAME;

    // Static block
    static {
        MAX_USERS = 100;
        APP_NAME = "MyApplication";
        System.out.println("Static block executed");
    }

    static void displayConfig() {
        System.out.println("App: " + APP_NAME + ", Max Users: " + MAX_USERS);
    }
}

public class Main {
    public static void main(String[] args) {
        Config.displayConfig();
    }
}
```

**Output:**

```doc
Static block executed
App: MyApplication, Max Users: 100
```

---

#### **Key Notes**

- Static blocks are executed **before any constructor or static method call**.  
- Primarily used for **initializing static variables, loading resources, or performing one-time setup**.  
- Helps in **avoiding repetitive initialization logic** in constructors.  

🔧 **Summary:**  
Static blocks → **class-level initialization code executed once at class loading**, used for preparing static resources or configuration before object creation.

### Explain about static imports in java?

- **Static import** allows you to **access static members (fields and methods) of a class directly** without prefixing them with the class name.  
- Introduced in **Java 5** to **improve code readability** and reduce verbosity.  

---

## **Syntax**

```java
import static package.ClassName.staticMember;
import static package.ClassName.*; // Import all static members
```

---

#### **Example**

```java
import static java.lang.Math.PI;
import static java.lang.Math.sqrt;

public class Main {
    public static void main(String[] args) {
        double radius = 5;
        double area = PI * sqrt(radius); // No need to write Math.PI or Math.sqrt
        System.out.println(area);
    }
}
```

**Without static import:**

```java
double area = Math.PI * Math.sqrt(radius);
```

---

#### **Key Points**

1. Static import **does not import instance members**.  
2. Can be used with **fields, methods, and nested static classes**.  
3. Improves **readability**, but **overuse may reduce clarity** (ambiguity if multiple classes have same static member names).  
4. Only affects **compile-time reference resolution**, not runtime behavior.  

🔧 **Summary:**  

- Static import → allows **direct access to class-level members** without class name.  
- Use for **constants and utility methods** to make code cleaner.  
- Avoid overuse to maintain **code readability**.

#### What is this keyword in Java?

**Definition:**  

- The `this` keyword is a **reference to the current object** whose method or constructor is being executed.  
- It is used to **differentiate instance variables from local variables**, **invoke constructors**, and **pass the current object** as a parameter.  

---

#### **Key Uses of `this`**

1. **Distinguish Instance Variables from Local Variables**

    ```java
    class Car {
        String model;

        Car(String model) {
            this.model = model; // 'this.model' refers to instance variable
        }
    }
    ```

2. **Invoke Another Constructor in the Same Class (Constructor Chaining)**

    ```java
    class Car {
        String model;
        int year;

        Car() {
            this("Unknown", 0); // Calls parameterized constructor
        }

        Car(String model, int year) {
            this.model = model;
            this.year = year;
        }
    }
    ```

3. **Pass Current Object as a Parameter**

    ```java
    class Car {
        void print(Car c) {
            System.out.println(c.model);
        }

        void show() {
            print(this); // Passing current object
        }
    }
    ```

4. **Return Current Object from Method**

    ```java
    class Car {
        Car setModel(String model) {
            this.model = model;
            return this; // Enables method chaining
        }
    }
    ```

---

#### **Key Points**

- Cannot be used in **static context** (static methods/blocks).  
- Helps in **clarity**, **constructor chaining**, and **method chaining**.  
- Always refers to the **current instance of the class**.  

🔧 **Summary:**  
`this` → reference to the current object; used for **resolving naming conflicts, constructor chaining, passing current object, and returning object for chaining**.

### What is the usage of the super keyword in Java?

- The `super` keyword is a **reference variable in a subclass** that refers to its **immediate parent class**.  
- It is used to **access parent class members** (variables, methods, constructors) that are hidden or overridden in the subclass.  

---

#### **Key Uses of `super`**

1. **Access Parent Class Instance Variables**

```java
class Vehicle {
    String type = "Generic Vehicle";
}

class Car extends Vehicle {
    String type = "Car";

    void printType() {
        System.out.println(type);       // Car
        System.out.println(super.type); // Vehicle
    }
}
```

2. **Invoke Parent Class Methods**

```java
class Vehicle {
    void start() {
        System.out.println("Vehicle started");
    }
}

class Car extends Vehicle {
    void start() {
        super.start(); // Calls Vehicle's start method
        System.out.println("Car started");
    }
}
```

3. **Call Parent Class Constructor**

```java
class Vehicle {
    Vehicle(String type) {
        System.out.println("Vehicle type: " + type);
    }
}

class Car extends Vehicle {
    Car() {
        super("Car"); // Calls parent constructor
        System.out.println("Car constructor");
    }
}
```

---

#### **Key Points**

- `super` can be used to **resolve naming conflicts** between parent and child class members.  
- `super()` must be the **first statement** in a subclass constructor when calling a parent constructor.  
- Cannot be used in **static context**.  

🔧 **Summary:**  
`super` → allows **subclasses to access parent class variables, methods, and constructors**, enabling **inheritance-based member reuse and overriding resolution**.

### Difference between this() and super() in java?Technical Comparison**  

| Feature                  | **`this()`**                                        | **`super()`**                                      |
|---------------------------|----------------------------------------------------|--------------------------------------------------|
| **Purpose**              | Calls **another constructor in the same class**    | Calls **constructor of the immediate parent class** |
| **Scope**                | Within the **same class**                          | Between **subclass and parent class**           |
| **Position in Constructor** | Must be the **first statement** in the constructor | Must be the **first statement** in the constructor |
| **Usage**                | For **constructor chaining within a class**       | For **constructor chaining across inheritance** |
| **Default Behavior**      | Not provided automatically; optional             | Compiler inserts `super()` by default if no parent constructor call exists |
| **Example**              | `this("value")`                                    | `super("value")`                                 |
| **Access**               | Only accesses constructors in **same class**      | Only accesses constructors in **parent class**  |

---

#### **Example**

```java
class Vehicle {
    Vehicle(String type) {
        System.out.println("Vehicle: " + type);
    }
}

class Car extends Vehicle {
    Car() {
        this("Default Model"); // Calls another constructor in same class
        System.out.println("Car no-arg constructor");
    }

    Car(String model) {
        super("Car");          // Calls parent constructor
        System.out.println("Car model: " + model);
    }
}

public class Main {
    public static void main(String[] args) {
        new Car();
    }
}
```

**Output:**

```doc
Vehicle: Car
Car model: Default Model
Car no-arg constructor
```

---

🔧 **Summary:**  

- `this()` → **same class constructor chaining**  
- `super()` → **parent class constructor chaining**  
- Both must be **first statement** in a constructor and cannot coexist in the same constructor simultaneously.

### Can we have a method name same as class name in java?

**Rule:**  

- **Yes**, in Java you **can have a method with the same name as the class**, but it **will not be a constructor**.  
- **Difference from Constructor:**  
  - A constructor **has no return type**.  
  - A method **must have a return type** (even `void`).  

---

#### **Example**

```java
class Car {
    void Car() { // This is a method, not a constructor
        System.out.println("This is a method named Car");
    }

    Car() { // This is the actual constructor
        System.out.println("This is the constructor");
    }
}

public class Main {
    public static void main(String[] args) {
        Car c = new Car(); // Calls constructor
        c.Car();           // Calls method named Car
    }
}
```

**Output:**

```doc
This is the constructor
This is a method named Car
```

---

#### **Key Points**

1. **Constructors** → no return type, automatically called on object creation.  
2. **Methods with same name** → need a return type, called explicitly using object reference.  
3. Can create **both a constructor and a method with the same name** in a class.  

🔧 **Summary:**  

- ✅ Allowed, but **method ≠ constructor**  
- Use a **return type** for the method to differentiate it from the constructor.

## OOP Principles

### What are the main features of Java (OOP principles)?

Java is an **object-oriented programming (OOP) language**, and its main features revolve around **OOP concepts** along with platform-independent and secure design.  

---

#### **1. Object-Oriented**

- **Everything is treated as objects** with state (fields) and behavior (methods).  
- Supports **real-world modeling** and **modular programming**.  

---

#### **2. Encapsulation**

- **Wrapping data (variables) and code (methods) together** in a class.  
- Uses **access modifiers (`private`, `protected`, `public`)** to restrict access.  
- Provides **getter and setter methods** to control access to fields.  
- Ensures **data hiding** and **security**.  

```java
class Car {
    private String model; // private variable

    public void setModel(String model) { this.model = model; }
    public String getModel() { return model; }
}
```

---

#### **3. Inheritance**

- Allows a **class to acquire properties and methods of another class**.  
- Promotes **code reuse** and **hierarchical relationships**.  
- Java supports **single inheritance for classes** and **multiple inheritance via interfaces**.  

```java
class Vehicle { void start() {} }
class Car extends Vehicle { void drive() {} }
```

---

### **4. Polymorphism**

- **Ability of an object to take many forms**.  
- Types:
  1. **Compile-time (Method Overloading)** – same method name, different parameters.  
  2. **Runtime (Method Overriding)** – subclass provides specific implementation.  

```java
class Vehicle { void start() {} }
class Car extends Vehicle { void start() {} } // Overriding
```

---

#### **5. Abstraction**

- **Hiding implementation details** and showing only essential features.  
- Achieved using **abstract classes** and **interfaces**.  

```java
abstract class Vehicle { abstract void start(); }
interface Drivable { void drive(); }
```

---

#### **6. Platform Independence**

- Java code → **compiled to bytecode** → runs on any system with JVM.  

#### **7. Additional Features**

- **Security:** Bytecode verification and no direct memory access.  
- **Multithreading:** Built-in support for concurrent programming.  
- **Automatic Memory Management:** Garbage collection.  

---

🔧 **Summary:**  
Java’s OOP principles enable **modularity, code reuse, flexibility, and maintainability**:  
**Object-Oriented → Encapsulation → Inheritance → Polymorphism → Abstraction**, plus **platform independence and security**.

### What is inheritance? Types of inheritance in Java?

- **Inheritance** is an OOP concept where a **class acquires the properties (fields) and behaviors (methods) of another class**.  
- Promotes **code reuse, modularity, and hierarchical relationships**.  

---

#### **Key Points**

- The class **which inherits** is called the **subclass/child class**.  
- The class **being inherited from** is called the **superclass/parent class**.  
- Use the keyword **`extends`** for class inheritance.  
- Java supports **single inheritance for classes**, multiple inheritance through **interfaces**.  

```java
class Vehicle {
    void start() { System.out.println("Vehicle started"); }
}

class Car extends Vehicle {
    void drive() { System.out.println("Car is driving"); }
}
```

---

#### **Types of Inheritance in Java**

1. **Single Inheritance**  
   - One subclass inherits from **one superclass**.  

   ```java
   class Vehicle {}
   class Car extends Vehicle {}
   ```

2. **Multilevel Inheritance**  
   - Inheritance chain: **grandparent → parent → child**.  

   ```java
   class Vehicle {}
   class Car extends Vehicle {}
   class ElectricCar extends Car {}
   ```

3. **Hierarchical Inheritance**  
   - **Multiple subclasses inherit from one superclass**.  

   ```java
   class Vehicle {}
   class Car extends Vehicle {}
   class Bike extends Vehicle {}
   ```

4. **Multiple Inheritance (via Interfaces)**  
   - Java **does not allow multiple class inheritance** to avoid ambiguity, but **interfaces** enable multiple inheritance.  

   ```java
   interface Drivable {}
   interface Electric {}
   class Tesla implements Drivable, Electric {}
   ```

---

#### **Key Points**

- Supports **code reuse and polymorphism**.  
- Enables **method overriding** in subclasses.  
- Must handle **`super` keyword** to access parent class members.  

🔧 **Summary:**  
Inheritance → **establishes "is-a" relationships**, types: **Single, Multilevel, Hierarchical, Multiple (via interfaces)**, enabling **modular, maintainable, and reusable code**.

### What is 'IS-A' relationship?

- The **IS-A relationship** represents an **inheritance relationship** between classes in Java.  
- It signifies that **one class is a type of another class**.  
- Implemented using **`extends`** (class inheritance) or **`implements`** (interface implementation).  

---

#### **Key Points**

1. Establishes **hierarchical relationships** between classes.  
2. Enables **polymorphism** – a subclass object can be treated as a superclass type.  
3. Promotes **code reuse** and **logical modeling**.  

---

#### **Example**

```java
// Vehicle → Parent class
class Vehicle {
    void start() { System.out.println("Vehicle started"); }
}

// Car → Child class
class Car extends Vehicle { // Car IS-A Vehicle
    void drive() { System.out.println("Car is driving"); }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v = new Car(); // Polymorphism
        v.start();             // Works
        // v.drive();          // ❌ Cannot access Car-specific methods
    }
}
```

**Explanation:**  

- `Car` **IS-A** `Vehicle` because it inherits properties and behavior of `Vehicle`.  
- You can assign a `Car` object to a `Vehicle` reference – **polymorphic behavior**.  

---

#### **Key Notes**

- **IS-A relationship** → Inheritance-based (`extends` / `implements`)  
- Opposite concept: **HAS-A relationship** (composition/aggregation)  

🔧 **Summary:**  
`IS-A` → **"subclass is a type of superclass"**, enables **inheritance, polymorphism, and code reuse** in Java OOP design.

### What is 'HAS-A' relationship?

- The **HAS-A relationship** represents **composition or aggregation** in Java, where a class **contains references to other classes** as its members.  
- Indicates that an object **“has” another object** as a part of its state.  
- Used to model **part-of relationships** rather than type hierarchies.  

---

#### **Key Points**

1. **Composition:** Strong ownership; the contained object **cannot exist independently**.  
2. **Aggregation:** Weak ownership; the contained object **can exist independently**.  
3. Supports **code reuse without inheritance**.  

---

#### **Example – Composition**

```java
class Engine {
    void start() { System.out.println("Engine started"); }
}

class Car {
    private Engine engine; // Car HAS-A Engine

    Car() {
        this.engine = new Engine(); // Composition: Engine created with Car
    }

    void startCar() {
        engine.start();
        System.out.println("Car is running");
    }
}

public class Main {
    public static void main(String[] args) {
        Car c = new Car();
        c.startCar();
    }
}
```

**Output:**

```
Engine started
Car is running
```

---

#### **Key Notes**

- **HAS-A relationship** → uses **instance variables** to include other classes.  
- Does **not involve inheritance**; focuses on **object references**.  
- Opposite concept: **IS-A relationship** (inheritance).  

🔧 **Summary:**  
`HAS-A` → **"class contains another class"**, models **composition/aggregation**, promotes **flexible design and code reuse** without inheritance.

### Why is the main method static?

- The `main` method is declared as **`public static void main(String[] args)`**.  
- The `static` keyword allows the **JVM to invoke the method without creating an instance of the class**.  

---

#### **Key Reasons**

1. **Object Not Required for Entry Point**  
   - When a Java program starts, **no objects exist yet**.  
   - JVM calls `main` directly using the **class reference**, so it must be `static`.  

```java
class Demo {
    public static void main(String[] args) {
        System.out.println("Program started");
    }
}
```

2. **Memory Efficiency**  
   - Being static, the **main method resides in the method area** and does not require object memory allocation in the heap.  

3. **Single Entry Point**  
   - Static ensures there is a **single accessible entry point** for the JVM to start execution.  

---

#### **Key Points**

- Cannot use instance variables/methods directly inside `main` → need **object references**.  

```java
class Demo {
    int x = 10;
    public static void main(String[] args) {
        // System.out.println(x); // ❌ Compile-time error
        Demo d = new Demo();
        System.out.println(d.x); // ✅ Access via object
    }
}
```

- `static` ensures **predictable program startup**.  

🔧 **Summary:**  
The `main` method is **static** so that the JVM can **call it without creating an object**, providing a **well-defined entry point** for program execution.

### Why is the main method static in Java?

**Definition:**  

- The `main` method is declared as **`public static void main(String[] args)`**.  
- `static` allows the **JVM to invoke it without creating an instance of the class**.  

---

#### **Key Reasons**

1. **No Object Needed at Startup**  
   - When the program starts, **no objects exist**.  
   - JVM calls `main` using the **class name**, so it must be `static`.  

2. **Single Entry Point**  
   - Ensures a **single, consistent entry point** for program execution.  

3. **Memory Efficiency**  
   - Being static, the main method is loaded in the **method area**, not the heap.  

---

#### **Important Note**

- **Instance variables or methods cannot be accessed directly** in `main` without creating an object.  

```java
class Demo {
    int x = 10;

    public static void main(String[] args) {
        // System.out.println(x); // ❌ Error: non-static variable x cannot be referenced from static context
        Demo d = new Demo();
        System.out.println(d.x); // ✅ Access via object
    }
}
```

🔧 **Summary:**  
The `main` method is **static** so the JVM can **call it directly at program startup**, ensuring a **consistent, object-free entry point**.

### What is polymorphism? Give examples

**Definition:**  

- **Polymorphism** is an OOP concept meaning **“one interface, multiple forms”**.  
- It allows objects to **behave differently based on their type or context**, enabling **flexible and reusable code**.  

---

#### **Types of Polymorphism in Java**

1. **Compile-Time Polymorphism (Method Overloading)**
   - Same method name, **different parameter lists** (number or type).  
   - Resolved **at compile time**.  

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 10));      // 15 → int version
        System.out.println(calc.add(5.5, 2.5));   // 8.0 → double version
    }
}
```

---

2. **Runtime Polymorphism (Method Overriding)**
   - Subclass **provides specific implementation** of a superclass method.  
   - Resolved **at runtime** using **dynamic method dispatch**.  

```java
class Vehicle {
    void start() { System.out.println("Vehicle started"); }
}

class Car extends Vehicle {
    @Override
    void start() { System.out.println("Car started"); }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v = new Car(); // Reference type Vehicle, object type Car
        v.start();             // Output: Car started (runtime polymorphism)
    }
}
```

---

#### **Key Points**

- **Compile-time polymorphism** → method overloading (early binding).  
- **Runtime polymorphism** → method overriding (late binding).  
- Enables **flexible design, code reuse, and maintainability**.  

🔧 **Summary:**  
Polymorphism → **“many forms of a single entity”**.  

- Compile-time → **overloading**  
- Runtime → **overriding**  
💡 Provides **dynamic behavior and extensibility** in Java applications.

### What is method overloading vs method overriding? 

| Feature                        | **Method Overloading**                          | **Method Overriding**                           |
|--------------------------------|------------------------------------------------|------------------------------------------------|
| **Definition**                 | Same method name, **different parameter lists** in the same class. | Subclass provides **specific implementation** of a method already defined in superclass. |
| **Inheritance**                 | **Not mandatory** – can occur in the same class. | **Mandatory** – requires inheritance.       |
| **Parameters**                  | Must be **different** (type, number, or order). | Must be **same** as the superclass method.  |
| **Return Type**                  | Can be **same or different** (if parameters differ). | Must be **same or covariant** with superclass method. |
| **Access Modifier**              | Can be **any**.                                | Cannot be **more restrictive** than superclass method. |
| **Compile-Time vs Runtime**      | **Compile-time polymorphism** (early binding). | **Runtime polymorphism** (late binding).   |
| **Static Methods**               | Can be overloaded.                             | Cannot be overridden; can be hidden (static method in subclass). |
| **Final Methods**                | Can be overloaded.                             | Cannot be overridden.                         |
| **Example**                      | `int add(int a, int b)` vs `double add(double a, double b)` | `Vehicle.start()` overridden by `Car.start()` |

---

#### **Examples**

**Overloading**

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```

**Overriding**

```java
class Vehicle {
    void start() { System.out.println("Vehicle started"); }
}

class Car extends Vehicle {
    @Override
    void start() { System.out.println("Car started"); }
}
```

---

🔧 **Summary:**  

- **Overloading** → same name, different parameters, compile-time polymorphism.  
- **Overriding** → same name & parameters, different implementation in subclass, runtime polymorphism.  
- Both enhance **flexibility, readability, and maintainability** in Java OOP design.

### Difference between overriding and overloading?

| Feature                        | **Method Overloading**                          | **Method Overriding**                           |
|--------------------------------|------------------------------------------------|------------------------------------------------|
| **Definition**                 | Same method name, **different parameter list** in the **same class**. | Subclass provides **specific implementation** of a method in the **superclass**. |
| **Inheritance**                 | Not mandatory – can occur in the **same class**. | Mandatory – requires **inheritance**.       |
| **Parameters**                  | Must be **different** (number, type, or order). | Must be **same** as the superclass method.  |
| **Return Type**                  | Can be same or different (if parameters differ). | Must be same or **covariant** with superclass method. |
| **Access Modifier**              | Can be any.                                    | Cannot be **more restrictive** than superclass method. |
| **Polymorphism Type**            | **Compile-time** (early binding).            | **Runtime** (late binding).                  |
| **Static Methods**               | Can be overloaded.                             | Cannot be overridden; can be hidden.         |
| **Final Methods**                | Can be overloaded.                             | Cannot be overridden.                         |
| **Example**                      | `int add(int a, int b)` vs `double add(double a, double b)` | `Vehicle.start()` overridden by `Car.start()` |

---

#### **Summary**

- **Overloading:** Same name, different parameters → **compile-time polymorphism**.  
- **Overriding:** Same name & parameters, different implementation → **runtime polymorphism**.  
- Both are essential for **flexible and maintainable OOP design** in Java.

### What is a covariant return?  

- A **covariant return type** allows an **overridden method in a subclass** to return a **type that is a subclass of the return type declared in the parent class**.  
- Introduced in **Java 5**, it improves **type safety** and **avoids explicit casting**.  

---

#### **Key Points**

1. Applicable only in **method overriding** (runtime polymorphism).  
2. Return type in the subclass must be a **subclass of the parent method’s return type**.  
3. Works with **reference types**, not primitives.  

---

#### **Example**

```java
class Vehicle {}

class Car extends Vehicle {}

class VehicleFactory {
    Vehicle createVehicle() {
        return new Vehicle();
    }
}

class CarFactory extends VehicleFactory {
    @Override
    Car createVehicle() { // Covariant return type
        return new Car();
    }
}

public class Main {
    public static void main(String[] args) {
        VehicleFactory factory = new CarFactory();
        Vehicle v = factory.createVehicle(); // No casting needed
        System.out.println(v.getClass().getSimpleName()); // Output: Car
    }
}
```

---

#### **Key Notes**

- Enhances **type safety** in polymorphic code.  
- Allows **subclass-specific return objects** while adhering to the **Liskov Substitution Principle**.  
- Works **only for reference types**, not primitive types.  

🔧 **Summary:**  
Covariant return → **overridden method returns a subtype of the parent method’s return type**, enabling **flexible and type-safe overriding** in Java.

### What is encapsulation and abstraction?  

Both **encapsulation** and **abstraction** are core OOP principles but serve **different purposes** in Java.  

---

#### **1. Encapsulation**

**Definition:**  

- Encapsulation is the practice of **bundling data (variables) and methods that operate on the data together** within a class and **restricting direct access to some components** using **access modifiers**.  
- Achieved using **`private` fields** and **public getters/setters**.  

**Purpose:**  

- Protects the internal state of an object (**data hiding**).  
- Prevents unauthorized access and maintains **control over object data**.  

**Example:**

```java
class Car {
    private String model; // private variable

    public void setModel(String model) { // setter
        this.model = model;
    }

    public String getModel() { // getter
        return model;
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.setModel("Tesla"); // Access via method
        System.out.println(car.getModel());
    }
}
```

---

#### **2. Abstraction**

**Definition:**  

- Abstraction is the process of **hiding implementation details** and **showing only essential features** to the user.  
- Achieved using **abstract classes** and **interfaces**.  

**Purpose:**  

- Focus on **what an object does** rather than **how it does it**.  
- Helps in designing **flexible and modular systems**.  

**Example:**

```java
abstract class Vehicle {
    abstract void start(); // implementation hidden
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Car started"); // concrete implementation
    }
}
```

---

#### **Key Differences**

| Feature             | **Encapsulation**                         | **Abstraction**                          |
|--------------------|-------------------------------------------|-----------------------------------------|
| **Definition**      | Hiding **internal data** using access modifiers | Hiding **implementation details** of behavior |
| **Achieved By**     | `private` fields + getters/setters       | `abstract` classes and interfaces      |
| **Focus**           | **How data is accessed/controlled**     | **What functionality is exposed**      |
| **Purpose**         | Protect data, maintain integrity         | Simplify complexity, hide implementation |
| **Runtime/Compile** | Compile-time mechanism                    | Compile-time abstraction (design concept) |

---

🔧 **Summary:**  

- **Encapsulation:** Protects **data** → controls access to object state.  
- **Abstraction:** Hides **implementation details** → shows only **essential behavior**.  
💡 Both work together to create **robust, modular, and maintainable Java applications**.

### How to do encapsulation in Java?

**Definition:**  
Encapsulation is the practice of **wrapping fields (variables) and methods together in a class** and **restricting direct access to the fields**. This ensures **data hiding** and controlled access.  

---

#### **Steps to Implement Encapsulation**

1. **Declare class variables as `private`**  
   - Prevents direct access from outside the class.  

2. **Provide `public` getter and setter methods**  
   - Controls how variables are accessed and modified.  

3. **Optional: Make the class `final`**  
   - To prevent subclass modification if strict encapsulation is needed.  

---

#### **Example**

```java
class Employee {
    // Step 1: Private fields
    private String name;
    private int salary;

    // Step 2: Public getter and setter
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getSalary() {
        return salary;
    }

    public void setSalary(int salary) {
        if (salary > 0) { // validation check
            this.salary = salary;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Employee emp = new Employee();
        emp.setName("John");
        emp.setSalary(5000);
        System.out.println(emp.getName() + ": $" + emp.getSalary());
    }
}
```

**Output:**

```
John: $5000
```

---

#### **Key Points**

- Use **private fields** to hide data.  
- Use **public getters/setters** to control access and validation.  
- Supports **data integrity** and **code maintainability**.  
- Can include **logic in setters** (e.g., validation, logging).  

🔧 **Summary:**  
Encapsulation = **private fields + public getter/setter methods**, ensures **data hiding, controlled access, and maintainable code** in Java.

### What is data encapsulation?

- **Data encapsulation** is the process of **wrapping data (variables) and the methods that operate on them into a single unit (class)** while **restricting direct access to the internal data**.  
- Achieved using **access modifiers**, typically `private` for fields and `public` for getter/setter methods.  

---

#### **Purpose of Data Encapsulation**

1. **Data Hiding** – Protects internal object state from unauthorized access.  
2. **Controlled Access** – Allows validation or logic in getter/setter methods.  
3. **Modularity** – Keeps related fields and behavior together.  
4. **Maintainability** – Changing internal representation does not affect external code.  

---

#### **Example**

```java
class BankAccount {
    private double balance; // Data hidden

    // Public getter and setter for controlled access
    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        account.deposit(1000);
        account.withdraw(500);
        System.out.println("Balance: $" + account.getBalance());
    }
}
```

**Output:**

```
Balance: $500.0
```

---

#### **Key Points**

- **Private fields** → hide data.  
- **Public methods** → control access and enforce rules.  
- Promotes **security, integrity, and modular design**.  

🔧 **Summary:**  
Data encapsulation → **hide object data and expose controlled access via methods**, forming the **foundation of secure and maintainable OOP design** in Java.

### When to use Interface vs Abstract Class?

Both **interfaces** and **abstract classes** provide **abstraction**, but they serve different purposes. Choosing between them depends on the design requirement.  

---

#### **Key Guidelines for Usage**

| Feature / Scenario               | **Interface**                                  | **Abstract Class**                               |
|---------------------------------|-----------------------------------------------|-------------------------------------------------|
| **Purpose**                      | Define **capabilities/contract** without implementation (behavioral abstraction). | Provide **partial implementation** with common code and shared state. |
| **Use Case**                      | When multiple classes from **different hierarchies** need to implement common behavior. | When classes share **common properties, methods, or code**. |
| **Multiple Inheritance**          | Supports **multiple inheritance** via implementing multiple interfaces. | **Single inheritance** only (cannot extend multiple classes). |
| **Default Methods**               | Java 8+ allows default and static methods.   | Can have fully implemented methods and constructors. |
| **Fields / State**                | Cannot have instance variables (can have `static final` constants). | Can have instance variables and maintain state. |
| **Constructor**                   | Cannot have constructors.                    | Can have constructors to initialize common state. |
| **Example Scenario**              | `Drivable`, `Flyable` – classes like `Car` or `Plane` implement as needed. | `Vehicle` – `Car` and `Bike` inherit common fields and methods. |

---

#### **Example**

**Interface Example**

```java
interface Drivable {
    void drive(); // behavior contract
}

class Car implements Drivable {
    @Override
    public void drive() {
        System.out.println("Car is driving");
    }
}
```

**Abstract Class Example**

```java
abstract class Vehicle {
    String model;

    Vehicle(String model) { this.model = model; }

    abstract void start(); // must be implemented by subclass

    void showModel() { System.out.println("Model: " + model); } // shared code
}

class Car extends Vehicle {
    Car(String model) { super(model); }

    @Override
    void start() { System.out.println("Car started"); }
}
```

---

#### **Key Decision Points**

1. **Use Interface**  
   - When you need **multiple inheritance** of behavior.  
   - When you only want to define **capabilities** without implementation.  

2. **Use Abstract Class**  
   - When you want to **share common state or code** across subclasses.  
   - When you want **partial implementation** along with abstract methods.  

🔧 **Summary:**  

- **Interface:** "What can it do?" → behavior contract, multiple inheritance.  
- **Abstract Class:** "What is it?" → shared state, partial implementation, single inheritance.  

### What is an abstract class?

- An **abstract class** is a class that **cannot be instantiated directly** and is meant to be **subclassed**.  
- It can contain:  
  - **Abstract methods** (methods without implementation)  
  - **Concrete methods** (fully implemented methods)  
  - **Fields (instance variables)** and **constructors**  

---

#### **Key Features**

1. Declared using the keyword **`abstract`**.  
2. Can have **abstract and non-abstract methods**.  
3. Cannot create objects directly: `new AbstractClass()` is invalid.  
4. Subclasses must **implement all abstract methods** unless they are also abstract.  
5. Can have **constructors** to initialize shared state for subclasses.  

---

#### **Syntax**

```java
abstract class Vehicle {
    String model;

    Vehicle(String model) { // constructor
        this.model = model;
    }

    abstract void start(); // abstract method

    void showModel() {     // concrete method
        System.out.println("Model: " + model);
    }
}

class Car extends Vehicle {
    Car(String model) { super(model); }

    @Override
    void start() { System.out.println("Car started"); }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v = new Car("Tesla");
        v.showModel(); // Model: Tesla
        v.start();     // Car started
    }
}
```

---

#### **Key Points**

- Provides **partial abstraction**: can mix implemented and unimplemented methods.  
- Supports **code reuse** via concrete methods and fields.  
- Helps in designing **flexible, extensible hierarchies**.  
- Cannot be instantiated → only **subclasses can be used to create objects**.  

🔧 **Summary:**  
Abstract class → **blueprint with partial implementation**, defines **common behavior** while forcing subclasses to implement specific functionality.

### What are abstract methods?

- An **abstract method** is a method **without a body** (no implementation) that is **declared in an abstract class or interface**.  
- It specifies **what a subclass must implement**, enforcing a **contract**.  

---

#### **Key Features**

1. Declared using the **`abstract`** keyword.  
2. **No method body** – ends with a semicolon (`;`).  
3. Must be implemented by the **subclass**, unless the subclass is also abstract.  
4. Cannot be **static, final, or private**.  
5. Supports **runtime polymorphism** when overridden.  

---

#### **Syntax**

```java
abstract class Vehicle {
    abstract void start(); // abstract method
    abstract void stop();  // another abstract method
}
```

#### **Example**

```java
abstract class Vehicle {
    abstract void start(); // must be implemented by subclass
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Car started");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v = new Car();
        v.start(); // Output: Car started
    }
}
```

---

#### **Key Points**

- Abstract methods **define a contract**; subclasses provide the **specific behavior**.  
- Helps achieve **abstraction** in OOP.  
- Promotes **code consistency** across subclasses.  

🔧 **Summary:**  
Abstract method → **method signature without implementation**, forces **subclasses to define concrete behavior**, enabling **flexible and maintainable OOP design**.

### Can we create a constructor in an abstract class?  

**Rule:**  

- **Yes**, an abstract class **can have a constructor** in Java.  
- However, you **cannot instantiate an abstract class directly** using `new`.  

---

#### **Purpose of Constructor in Abstract Class**

1. **Initialize fields** of the abstract class.  
2. **Perform setup tasks** when a subclass object is created.  
3. Ensures **common state or behavior** is initialized for all subclasses.  

---

#### **Example**

```java
abstract class Vehicle {
    String model;

    // Constructor in abstract class
    Vehicle(String model) {
        this.model = model;
        System.out.println("Vehicle constructor called");
    }

    abstract void start(); // abstract method
}

class Car extends Vehicle {
    Car(String model) {
        super(model); // Call abstract class constructor
    }

    @Override
    void start() {
        System.out.println(model + " started");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle v = new Car("Tesla");
        v.start();
    }
}
```

**Output:**

```
Vehicle constructor called
Tesla started
```

---

#### **Key Points**

- Abstract class constructor is **called when a subclass object is created**.  
- Useful to **initialize fields shared across all subclasses**.  
- Cannot use `new Vehicle()` directly because abstract classes **cannot be instantiated**.  

🔧 **Summary:**  

- ✅ Abstract classes **can have constructors**.  
- ✅ Used to **initialize common state** when **subclass objects are created**.

### What is an interface in Java?

- An **interface** is a **reference type in Java** that defines a **contract of methods** without specifying their implementation.  
- Classes that **implement the interface** must provide concrete implementations for all its abstract methods.  
- Introduced in Java to achieve **abstraction and multiple inheritance**.  

---

#### **Key Features**

1. Declared using the **`interface`** keyword.  
2. Can contain:
   - **Abstract methods** (no body)  
   - **Default methods** (with body, Java 8+)  
   - **Static methods** (with body)  
   - **Constants** (`public static final` by default)  
3. Supports **multiple inheritance** (a class can implement multiple interfaces).  
4. Cannot have **instance fields** (only constants).  
5. Provides a way to **specify behavior without enforcing a class hierarchy**.  

---

#### **Syntax**

```java
interface Drivable {
    int MAX_SPEED = 120; // public static final by default
    void drive();         // abstract method
    default void stop() { // default method
        System.out.println("Vehicle stopped");
    }
    static void info() {
        System.out.println("Interface info method");
    }
}
```

---

#### **Example**

```java
class Car implements Drivable {
    @Override
    public void drive() {
        System.out.println("Car is driving");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.drive(); // Car is driving
        car.stop();  // Vehicle stopped (default method)
        Drivable.info(); // Interface info method
    }
}
```

---

#### **Key Points**

- Interfaces **define a contract** → classes must implement the methods.  
- Enable **multiple inheritance** in Java, which is **not possible with classes**.  
- Supports **polymorphism**: a reference type can be the interface, pointing to any implementing class.  

🔧 **Summary:**  
Interface → **abstract behavior specification**, supports **multiple inheritance, abstraction, and polymorphism** in Java.

### What is the purpose of an interface?

- An **interface** defines a **contract or blueprint** of methods that a class must implement.  
- It specifies **“what an object can do”** without detailing **how it does it**.  

---

#### **Key Purposes**

1. **Achieve Abstraction**  
   - Hides implementation details and exposes only essential behavior.  
   - Allows **focus on “what” rather than “how”**.  

2. **Enable Multiple Inheritance**  
   - Java classes cannot extend multiple classes, but can **implement multiple interfaces**.  
   - Resolves the **diamond problem** safely.  

3. **Define a Contract**  
   - Forces implementing classes to provide specific behavior.  
   - Ensures **consistency across different classes**.  

4. **Support Polymorphism**  
   - Interface references can point to **any implementing class**.  
   - Facilitates **flexible and decoupled design**.  

5. **Promote Loose Coupling**  
   - Interfaces allow code to depend on **abstractions rather than concrete classes**, improving **maintainability and testability**.  

---

#### **Example**

```java
interface Drivable {
    void drive(); // contract
}

class Car implements Drivable {
    @Override
    public void drive() { System.out.println("Car is driving"); }
}

class Bike implements Drivable {
    @Override
    public void drive() { System.out.println("Bike is driving"); }
}

public class Main {
    public static void main(String[] args) {
        Drivable d1 = new Car();
        Drivable d2 = new Bike();
        d1.drive(); // Car is driving
        d2.drive(); // Bike is driving
    }
}
```

**Explanation:**  

- `Drivable` interface ensures all vehicles implement `drive()`.  
- Polymorphism allows **uniform handling of different vehicle types**.  

---

🔧 **Summary:**  
The **purpose of an interface** → **define a contract, achieve abstraction, enable multiple inheritance, support polymorphism, and promote loose coupling** in Java applications.

### When to use Interface vs Abstract Class?

Both interfaces and abstract classes provide **abstraction**, but they are used in **different scenarios** depending on design requirements.  

---

### **1. Use an Interface When:**

- You want to define a **capability or contract** that multiple classes can implement.  
- Classes are from **different hierarchies** but share common behavior.  
- You need **multiple inheritance** of type (Java allows implementing multiple interfaces).  
- You only need **method declarations** (abstract methods) or constants.  
- You want to provide **default or static methods** (Java 8+).  

**Example:**  

```java
interface Drivable {
    void drive(); // capability all vehicles should implement
}

class Car implements Drivable { ... }
class Bike implements Drivable { ... }
```

---

### **2. Use an Abstract Class When:**

- You want to provide **common state (fields) or shared code** to subclasses.  
- You need **partial implementation** (some methods implemented, some abstract).  
- You want to **define constructors** for initializing common data.  
- Classes share a **strong “is-a” relationship**.  
- You do **not need multiple inheritance** of class behavior.  

**Example:**  

```java
abstract class Vehicle {
    String model;
    Vehicle(String model) { this.model = model; }

    abstract void start();       // must be implemented
    void showModel() {           // shared code
        System.out.println(model);
    }
}

class Car extends Vehicle {
    Car(String model) { super(model); }
    void start() { System.out.println("Car started"); }
}
```

---

### **Key Decision Points**

| Scenario                                      | **Interface**                 | **Abstract Class**                |
|-----------------------------------------------|-------------------------------|----------------------------------|
| Multiple inheritance needed                   | ✅ Yes                        | ❌ No                           |
| Share code among related classes              | ❌ Minimal (default methods)  | ✅ Yes                          |
| Define behavior across unrelated classes      | ✅ Yes                        | ❌ No                           |
| Include constructors / maintain state        | ❌ No                        | ✅ Yes                          |
| Focus on “can do” (capabilities)             | ✅ Yes                        | ❌ No                           |
| Focus on “is-a” relationship                  | ❌ No                        | ✅ Yes                          |

---

🔧 **Summary:**  

- **Interface:** Use for **capabilities/behavior contracts**, multiple inheritance, unrelated classes.  
- **Abstract Class:** Use for **shared state/code**, partial implementation, related classes with an “is-a” relationship.

### What is the difference between an abstract class and an interface?Technical Comparison**  

| Feature                       | **Abstract Class**                                | **Interface**                                 |
|-------------------------------|--------------------------------------------------|-----------------------------------------------|
| **Definition**                 | Class with **partial implementation**; can have abstract and concrete methods. | Reference type defining **method contracts** without full implementation. |
| **Instantiation**              | Cannot be instantiated directly.                | Cannot be instantiated directly.             |
| **Purpose**                    | Share **common code/state** among related classes. | Define **capabilities/behavior contracts** across classes. |
| **Methods**                     | Can have **abstract and concrete methods**.     | Can have **abstract methods**, **default** and **static** methods (Java 8+). |
| **Fields / State**              | Can have **instance variables**, constructors, and methods. | Can have only **constants** (`public static final`). No instance variables. |
| **Constructors**                | Allowed – used to initialize common state.      | Not allowed.                                 |
| **Inheritance**                 | Supports **single inheritance**.                | Supports **multiple inheritance** via `implements`. |
| **Access Modifiers**            | Can have any access modifier for methods/fields. | All abstract methods are **public** by default. Constants are **public static final**. |
| **When to Use**                 | When classes are **closely related** and share code/state. | When classes are **unrelated** but share **behavior**. |
| **Polymorphism**                | Achieved via subclassing.                        | Achieved via interface reference to implementing class. |

---

### **Key Notes**

- **Abstract Class:** Focus on **“is-a” relationship**, shared state, and partial implementation.  
- **Interface:** Focus on **“can-do” behavior**, multiple inheritance, and polymorphism.  
- **Java 8+ Features:** Interfaces can have **default and static methods**, narrowing the gap between interfaces and abstract classes.  

🔧 **Summary:**  

- **Abstract Class:** Use for **shared code and related classes**.  
- **Interface:** Use for **behavior contracts and multiple inheritance**.  
- **Main Difference:** Abstract classes can store **state** and have **constructors**; interfaces cannot.

### What is the purpose of the default keyword in interfaces?

**Definition:**  

- The **`default`** keyword allows an interface method to have a **concrete implementation**.  
- Introduced in **Java 8** to provide **backward compatibility** without breaking existing implementations.  

---

### **Key Purposes**

1. **Provide Method Implementation in Interfaces**  
   - Interfaces traditionally could only have abstract methods.  
   - `default` lets you add new methods **without forcing all implementing classes to override them**.  

2. **Support Backward Compatibility**  
   - Existing classes implementing the interface **do not break** when a new method is added.  

3. **Enable Code Reuse**  
   - Provides **common default behavior** that can be shared across multiple classes.  

---

### **Syntax**

```java
interface Drivable {
    void drive(); // abstract method

    default void stop() { // default method
        System.out.println("Vehicle stopped");
    }
}
```

### **Example**

```java
class Car implements Drivable {
    @Override
    public void drive() {
        System.out.println("Car is driving");
    }
}

public class Main {
    public static void main(String[] args) {
        Drivable car = new Car();
        car.drive(); // Car is driving
        car.stop();  // Vehicle stopped (default method)
    }
}
```

---

### **Key Points**

- Default methods **can be overridden** by implementing classes.  
- Allows interfaces to evolve **without breaking existing code**.  
- Works with **multiple inheritance of interfaces** (diamond problem handled using `super` keyword).  

🔧 **Summary:**  
The **`default` keyword** in interfaces → **provides concrete method implementation**, enables **backward compatibility**, **code reuse**, and **flexible interface evolution** in Java.

### Can we define static methods inside an interface?

**Definition:**  

- Yes, **interfaces can have static methods** since **Java 8**.  
- Static methods in an interface **belong to the interface itself**, not to the implementing classes.  

---

### **Key Points**

1. **Called using the interface name**, not through an instance or implementing class.  
2. **Cannot be overridden** by implementing classes.  
3. Useful for **utility or helper methods** related to the interface.  

---

### **Syntax**

```java
interface Drivable {
    static void info() {
        System.out.println("All vehicles implement Drivable interface");
    }
}
```

### **Example**

```java
class Car implements Drivable {
    // No need to implement static method
}

public class Main {
    public static void main(String[] args) {
        Drivable.info(); // Interface static method called directly
    }
}
```

**Output:**

```
All vehicles implement Drivable interface
```

---

### **Key Notes**

- Static methods **cannot be accessed via object** or implementing class.  
- Helps provide **utility functionality** tied to the interface.  
- Complements **default methods** for backward-compatible code evolution.  

🔧 **Summary:**  

- ✅ Interfaces **can have static methods**.  
- ✅ Called via **interface name**.  
- ✅ Cannot be overridden.  
- ✅ Useful for **utility/helper methods**.

### What is a Marker Interface? Why use it?

**Definition:**  

- A **Marker Interface** is an interface **without any methods or fields**.  
- It serves as a **tag or marker** to indicate that a class has a certain property or should be treated in a specific way by the JVM or frameworks.  

---

### **Purpose / Why Use Marker Interfaces**

1. **Provide Metadata to Classes**  
   - Acts as a **signal** that a class possesses certain capabilities.  

2. **Enable Special Behavior**  
   - JVM or APIs **check for the marker** to enable specific operations.  

3. **Compile-Time and Runtime Checks**  
   - Used to **categorize or identify classes** without adding methods.  

---

### **Common Examples**

| Marker Interface | Purpose |
|-----------------|---------|
| `Serializable`  | Marks a class as **serializable** so its objects can be written to streams. |
| `Cloneable`     | Marks a class whose objects can be **cloned** using `Object.clone()`. |
| `Remote`        | Marks classes whose objects can be used for **RMI (Remote Method Invocation)**. |

---

### **Example**

```java
import java.io.Serializable;

class Employee implements Serializable { // Marker interface
    private String name;
    private int id;

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }
}

public class Main {
    public static void main(String[] args) {
        Employee emp = new Employee("John", 101);
        System.out.println(emp instanceof Serializable); // true
    }
}
```

**Explanation:**  

- `Employee` implements `Serializable` → JVM knows it can be serialized.  
- No methods are defined in `Serializable`; it **just acts as a marker**.  

---

### **Key Points**

- Marker interfaces **do not contain methods or fields**.  
- Used to **indicate metadata or special behavior**.  
- Alternative in modern Java: **Annotations** can replace marker interfaces.  

🔧 **Summary:**  
**Marker Interface** → empty interface used to **tag classes for special behavior**, e.g., `Serializable`, `Cloneable`. It **enables type-checking and JVM-specific processing** without adding methods.

### What is a package in Java?

**Definition:**  

- A **package** is a **namespace that organizes a set of related classes and interfaces** in Java.  
- Packages help **avoid name conflicts** and **manage code modularly**.  

---

### **Purpose of Packages**

1. **Organize Classes and Interfaces**  
   - Groups related classes, interfaces, and sub-packages together.  

2. **Avoid Name Conflicts**  
   - Classes with the same name can exist in different packages.  

3. **Access Control**  
   - Provides **controlled access** using access modifiers (`public`, `protected`, default).  

4. **Code Reusability and Maintainability**  
   - Makes large projects more **modular and maintainable**.  

---

### **Types of Packages**

1. **Built-in Packages** – Provided by Java, e.g.,  
   - `java.util` → Collections, Date, etc.  
   - `java.io` → File, InputStream, etc.  

2. **User-defined Packages** – Created by developers to organize custom classes.  

---

### **Syntax to Create and Use Packages**

**Create a Package**

```java
package mypackage; // package declaration

public class MyClass {
    public void display() {
        System.out.println("Hello from MyClass");
    }
}
```

**Use a Package**

```java
import mypackage.MyClass; // import class from package

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.display();
    }
}
```

---

### **Key Points**

- Declared at the **top of the Java file** using `package` keyword.  
- Classes in the **same package** can access each other’s default (package-private) members.  
- Packages support **modular development** and **namespace management**.  

🔧 **Summary:**  
A **package** → a **namespace for organizing classes and interfaces**, helping **modularity, reusability, access control, and avoiding name conflicts** in Java projects.

### What are access modifiers in Java (private, protected, public, default)?

**Definition:**  

- Access modifiers control the **visibility and accessibility** of classes, methods, and variables in Java.  
- Java has **four types**: `private`, `default` (no keyword), `protected`, and `public`.  

---

### **1. `private`**

- **Visibility:** Accessible **only within the same class**.  
- **Use Case:** Data hiding, encapsulation.  

```java
class Example {
    private int data = 10;
    private void show() {
        System.out.println(data);
    }
}
```

---

### **2. Default (no modifier)**

- **Visibility:** Accessible **within the same package** only.  
- **Use Case:** Package-level encapsulation for related classes.  

```java
class Example {
    int data = 10; // default access
    void show() { System.out.println(data); }
}
```

---

### **3. `protected`**

- **Visibility:** Accessible **within the same package** and by **subclasses** (even in different packages).  
- **Use Case:** Support inheritance while limiting general access.  

```java
class Example {
    protected int data = 10;
}
class SubExample extends Example {
    void display() { System.out.println(data); } // accessible in subclass
}
```

---

### **4. `public`**

- **Visibility:** Accessible **from anywhere** in the project.  
- **Use Case:** API methods or classes intended for global access.  

```java
public class Example {
    public int data = 10;
    public void show() { System.out.println(data); }
}
```

---

### **Access Levels Summary**

| Modifier   | Same Class | Same Package | Subclass | World (any class) |
|------------|------------|--------------|----------|------------------|
| `private`  | ✅         | ❌           | ❌       | ❌               |
| Default    | ✅         | ✅           | ❌       | ❌               |
| `protected`| ✅         | ✅           | ✅       | ❌               |
| `public`   | ✅         | ✅           | ✅       | ✅               |

---

🔧 **Summary:**  
Access modifiers → **control visibility of classes, fields, and methods**, enabling **encapsulation, inheritance control, and modular design** in Java.

### What is the difference between access specifiers and access modifiers?in Java**  

In Java, the terms **access specifier** and **access modifier** are often used interchangeably, but there is a subtle distinction in terminology and context.  

---

### **1. Access Modifiers**

- **Definition:** Keywords that **set the accessibility** of classes, methods, and variables.  
- **Purpose:** Control **how a member or class can be accessed**.  
- **Types:** `private`, `protected`, `public`, and **default** (no keyword).  
- **Scope:** Applies to **classes, methods, and variables**.  

```java
public class Example {  // 'public' is an access modifier
    private int data;    // 'private' is an access modifier
}
```

---

### **2. Access Specifiers**

- **Definition:** Sometimes used to **describe the level of access** granted by an access modifier.  
- **Purpose:** Explain **who can access a class, method, or variable**.  
- **Levels:**  
  - `private` → same class only  
  - default → same package  
  - `protected` → same package + subclasses  
  - `public` → accessible everywhere  

```text
Access Specifiers = levels of accessibility  
- private, default, protected, public
```

---

### **Key Difference**

| Feature                 | Access Modifier                            | Access Specifier                      |
|-------------------------|--------------------------------------------|--------------------------------------|
| **Definition**          | Keywords that **modify accessibility**      | Describes the **level of access**     |
| **Examples**            | `private`, `protected`, `public`, default  | private → class only, protected → subclass/package, etc. |
| **Purpose**             | Implement access control in code           | Explain/accessibility levels conceptually |

---

### **Summary**

- **Access Modifiers** → actual **Java keywords** used in code.  
- **Access Specifiers** → **conceptual levels of access** defined by modifiers.  
- In practice, **modifiers set the specifier**; the terms are closely related.

### What all access modifiers are allowed for a top-level class?

### **Key Points**

1. A **top-level class** is a class **not nested** inside another class.  
2. Java **restricts the access modifiers** that can be applied to top-level classes.  

---

### **Allowed Modifiers**

| Modifier   | Description |
|-----------|-------------|
| `public`  | Class is accessible **from any other class** in any package. |
| **default** (no modifier) | Class is accessible **only within the same package**. |

---

### **Not Allowed**

- `private` → ❌ Cannot be applied to top-level classes.  
- `protected` → ❌ Cannot be applied to top-level classes.  

**Reason:**  

- `private` or `protected` access does not make sense for top-level classes because they exist **outside any enclosing class**, so they cannot restrict access beyond package/subclass.

---

### **Example**

```java
// Public top-level class
public class PublicClass {
}

// Default top-level class (package-private)
class DefaultClass {
}

// Invalid:
// private class PrivateClass {}   // ❌ Compilation error
// protected class ProtectedClass {} // ❌ Compilation error
```

---

🔧 **Summary:**  

- **Top-level classes** can be either **`public`** or **default (no modifier)**.  
- **`private`** and **`protected`** are only valid for **nested (inner) classes**, not top-level classes.

### Explain the importance of the import keyword?

**Definition:**  

- The `import` keyword in Java allows a class or package to **access classes, interfaces, or sub-packages from another package** without using their **fully qualified names**.  

---

### **Key Purposes**

1. **Simplifies Code**  
   - Without `import`, you must use the **fully qualified class name**:  

   ```java
   java.util.ArrayList<String> list = new java.util.ArrayList<>();
   ```  

   - With `import`:  

   ```java
   import java.util.ArrayList;
   ArrayList<String> list = new ArrayList<>();
   ```

2. **Organizes Dependencies**  
   - Makes it clear which **external classes or packages** your code depends on.  

3. **Enhances Readability and Maintainability**  
   - Cleaner code with less clutter, easier to read and maintain.  

4. **Supports Modular Development**  
   - Enables code reuse by **using classes from Java API or custom packages**.  

---

### **Types of Import**

1. **Single Type Import**  
   - Imports a specific class or interface.  

   ```java
   import java.util.List;
   ```

2. **On-Demand (Wildcard) Import**  
   - Imports all classes/interfaces in a package.  

   ```java
   import java.util.*;
   ```

3. **Static Import** (Java 5+)  
   - Imports **static members** of a class.  

   ```java
   import static java.lang.Math.PI;
   import static java.lang.Math.sqrt;

   System.out.println(PI);
   System.out.println(sqrt(16));
   ```

---

### **Key Points**

- The `import` keyword **does not load classes**, it just provides **a shorthand reference**.  
- Only **top-level public classes/interfaces** from other packages can be imported.  
- Improves **readability, reduces verbosity, and organizes code**.  

🔧 **Summary:**  
`import` → **simplifies access to external classes**, supports **modular, readable, and maintainable Java code**, and allows usage of **Java API or user-defined packages** without fully qualified names.

### Can we have more than one package statement in a source file?Source File?**  

**Answer:**  

- ❌ **No**, a Java source file **cannot have more than one package statement**.  

---

### **Key Points**

1. **Rule:**  
   - A Java source file can **declare at most one package** at the **very top** of the file.  
   - Syntax:  

     ```java
     package packageName;
     ```

2. **Reason:**  
   - The **package declaration defines the namespace** for all classes/interfaces in that file.  
   - Allowing multiple packages would create ambiguity about **which package each class belongs to**.  

3. **Multiple Classes from Different Packages:**  
   - If you want classes in **different packages**, you must place them in **separate source files**, each with its own package declaration.  

---

### **Example**

✅ **Valid**

```java
package mypackage;

public class MyClass { }
class Helper { }
```

❌ **Invalid**

```java
package packageOne;
package packageTwo; // ❌ Compilation error
```

---

### **Key Notes**

- **All top-level classes** in a source file belong to the **same package**.  
- Inner classes are still part of the same package.  

🔧 **Summary:**  
A Java source file **can have only one package statement** at the top; multiple packages require **separate files**, ensuring clear **namespace management**.

### Can we define a package statement after an import statement?Statement in Java?**  

**Answer:**  

- ❌ **No**, the `package` statement **must always be the first statement** in a Java source file (except for comments and blank lines).  

---

### **Rules and Order in a Java Source File**

1. **Package Declaration (Optional)**  
   - If present, it **must be the first statement**.  

   ```java
   package mypackage;
   ```

2. **Import Statements (Optional)**  
   - Follow the package declaration.  

   ```java
   import java.util.List;
   import java.util.ArrayList;
   ```

3. **Class or Interface Definitions**  
   - After package and imports, define your classes or interfaces.  

---

### **Correct Order Example**

```java
package mypackage;      // package statement first

import java.util.*;    // import statements next

public class MyClass { // class definition
    // class body
}
```

### **Incorrect Order Example**

```java
import java.util.*;    // ❌ Cannot import before package
package mypackage;    // ❌ Compilation error
```

---

### **Key Notes**

- Only **comments** and **blank lines** can appear before the package statement.  
- Violating the order → **compilation error**: `illegal start of type`.  

🔧 **Summary:**  

- `package` statement → **must be first**.  
- `import` statements → **follow the package declaration**.  
- Maintaining this order ensures **proper namespace resolution** and **compilation**.

### Explain naming conventions for packages

**Definition:**  

- Packages in Java are **namespaces** that organize classes and interfaces.  
- Following **naming conventions** ensures **clarity, uniqueness, and maintainability**.  

---

### **1. General Guidelines**

1. **Lowercase letters**  
   - Package names should be **all lowercase** to avoid conflicts with class names.  

   ```java
   package mypackage;
   ```

2. **No spaces or special characters**  
   - Use **dots (`.`) to separate levels**.  

   ```java
   package com.example.utility;
   ```

3. **Hierarchical Naming**  
   - Use **reversed domain name** to ensure **uniqueness**.  

   ```java
   package com.companyname.projectname.module;
   ```

4. **Descriptive Names**  
   - Package names should describe the **purpose or functionality** of classes inside.  

   ```java
   package com.bankapp.models;     // for model classes
   package com.bankapp.services;   // for service classes
   package com.bankapp.utils;      // for utility/helper classes
   ```

---

### **2. Examples**

```java
package com.example.app;           // top-level application package
package com.example.app.models;    // sub-package for models
package com.example.app.controllers; // sub-package for controllers
```

---

### **3. Key Points**

- **Use lowercase** to avoid conflicts across operating systems (case-sensitive).  
- **Use meaningful names** that reflect the package’s contents.  
- **Avoid reserved keywords** (`int`, `class`, `package`).  
- **Follow reverse domain naming** for globally unique packages (common in libraries and APIs).  

---

🔧 **Summary:**  

- Packages should have **lowercase, hierarchical, descriptive names**, often using **reverse domain notation**.  
- This ensures **clarity, maintainability, and avoids naming conflicts** in large Java projects.

### What do you mean by the final keyword? (final variable, method, class)

**Definition:**  

- The `final` keyword in Java is used to **restrict modification**.  
- It can be applied to **variables, methods, and classes**, each with a specific meaning.  

---

### **1. Final Variable**

- A variable declared as `final` **cannot be reassigned** after initialization.  
- If it’s an object reference, the **reference cannot change**, but the object’s state can.  

```java
final int MAX_VALUE = 100;
MAX_VALUE = 200; // ❌ Compilation error

final Person p = new Person();
p = new Person(); // ❌ Reference cannot change
p.name = "John"; // ✅ Object state can change
```

---

### **2. Final Method**

- A method declared as `final` **cannot be overridden** by subclasses.  
- Useful to **prevent altering critical behavior**.  

```java
class Vehicle {
    final void start() {
        System.out.println("Vehicle started");
    }
}

class Car extends Vehicle {
    void start() { } // ❌ Compilation error
}
```

---

### **3. Final Class**

- A class declared as `final` **cannot be subclassed**.  
- Useful for **security, immutability, or utility classes**.  

```java
final class MathUtil {
    static int add(int a, int b) { return a + b; }
}

class AdvancedMath extends MathUtil { } // ❌ Compilation error
```

---

### **Key Points**

| Usage           | Meaning |
|-----------------|---------|
| `final variable` | Value/reference **cannot be changed** after initialization |
| `final method`   | **Cannot be overridden** in subclasses |
| `final class`    | **Cannot be extended** by other classes |

---

🔧 **Summary:**  
The `final` keyword → **prevents modification**:  

- Variables → immutable values/references  
- Methods → cannot override  
- Classes → cannot extend  

It’s widely used for **immutability, security, and consistent behavior** in Java.

### What is the difference between static and final keywords?Java**  

| Feature                  | **static**                                      | **final**                                   |
|--------------------------|------------------------------------------------|--------------------------------------------|
| **Definition**           | Belongs to the **class**, not instances.       | Restricts modification; used for **constants, methods, or classes**. |
| **Applies To**           | Variables, methods, blocks, nested classes.  | Variables, methods, classes.              |
| **Behavior for Variables** | Shared among all instances; only **one copy** exists. | Value cannot be reassigned after initialization. |
| **Behavior for Methods** | Can be called **without an object**; cannot be overridden in usual sense (but can be hidden). | Cannot be overridden by subclasses.       |
| **Behavior for Classes** | Cannot declare a class as `static` unless nested. | Cannot be subclassed.                     |
| **Initialization**       | Can be initialized at declaration or in static block. | Must be initialized **once** (at declaration or in constructor for instance final variables). |
| **Access**               | Accessed via `ClassName.member`.              | Accessed normally, enforced immutability or restriction. |
| **Typical Use Case**     | Shared resources/methods, utility classes.    | Constants, immutable objects, secure methods/classes. |

---

### **Example**

```java
class Example {
    static int count = 0;         // class-level variable
    final int MAX = 100;          // constant, cannot change

    static void displayCount() {
        System.out.println(count);
    }

    final void showMax() {
        System.out.println(MAX);
    }
}
```

**Key Differences**

1. `static` → **shared across all objects**; `final` → **cannot be modified**.  
2. `static` → belongs to the **class**, `final` → enforces **immutability or restriction**.  
3. Can combine: `static final int MAX = 100;` → **constant shared by all instances**.  

🔧 **Summary:**  

- **static** → **class-level** behavior.  
- **final** → **immutable or non-overridable** behavior.  
- Together, `static final` → **constant values**.

### What is the transient keyword in Java?

**Definition:**  

- The `transient` keyword in Java is used to **indicate that a field should not be serialized**.  
- When an object is serialized, **transient fields are skipped** and not saved to the output stream.  

---

### **Purpose**

1. **Prevent Sensitive Data Serialization**  
   - Fields like passwords, security tokens, or temporary data should not be persisted.  

2. **Avoid Serialization of Non-Serializable Objects**  
   - If a field references a non-serializable object, marking it `transient` prevents serialization errors.  

3. **Reduce Serialized Data Size**  
   - Skip unnecessary or large fields that don’t need persistence.  

---

### **Syntax**

```java
import java.io.Serializable;

class User implements Serializable {
    private String username;
    private transient String password; // will not be serialized

    public User(String username, String password) {
        this.username = username;
        this.password = password;
    }
}
```

---

### **Example Usage**

```java
import java.io.*;

public class Main {
    public static void main(String[] args) throws Exception {
        User user = new User("john", "secret123");

        // Serialize object
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("user.ser"));
        oos.writeObject(user);
        oos.close();

        // Deserialize object
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("user.ser"));
        User deserializedUser = (User) ois.readObject();
        ois.close();

        System.out.println(deserializedUser.username); // john
        System.out.println(deserializedUser.password); // null (transient)
    }
}
```

**Explanation:**  

- `password` was marked **transient**, so it **was not saved** during serialization.  
- After deserialization, the `password` field defaults to `null`.  

---

### **Key Points**

- Only applies to **instance variables** (not methods or class variables).  
- Helps **control serialization** and **protect sensitive data**.  
- Often used in combination with **Serializable** interface.  

🔧 **Summary:**  
`transient` → **prevents a field from being serialized**, useful for **security, reducing data size, and handling non-serializable fields** in Java.

### What is the volatile keyword?

**Definition:**  

- The `volatile` keyword in Java is used to indicate that a **variable’s value will be modified by multiple threads**.  
- It ensures that **reads and writes to that variable are always visible across threads**, providing a lightweight form of **thread-safety**.  

---

### **Key Characteristics**

1. **Visibility Guarantee**  
   - Changes made by one thread to a `volatile` variable are **immediately visible** to other threads.  

2. **No Atomicity Guarantee**  
   - Operations like `count++` are **not atomic**, even if the variable is `volatile`.  
   - Use `synchronized` or `AtomicInteger` for atomic operations.  

3. **Memory Barrier Effect**  
   - The compiler and CPU **cannot reorder reads/writes** of a `volatile` variable with respect to other reads/writes.  

---

### **Syntax**

```java
class SharedResource {
    volatile boolean flag = false;
}
```

---

### **Example**

```java
class FlagExample {
    volatile boolean flag = false;

    void writer() {
        flag = true; // changes are visible to reader threads immediately
    }

    void reader() {
        if (flag) {
            System.out.println("Flag is true");
        }
    }
}
```

**Explanation:**  

- Without `volatile`, one thread might **cache the variable**, and changes made by another thread may not be visible.  
- With `volatile`, all threads **see the latest value**.  

---

### **Key Points**

- Can be used only with **instance or static variables** (not local variables).  
- Provides **visibility but not atomicity**.  
- Often used in **flags, shutdown signals, or status indicators** in multithreading.  

🔧 **Summary:**  
`volatile` → ensures **visibility of shared variables across threads**, prevents **caching issues**, and avoids **stale values**, making it crucial in **concurrent programming**.

### What is the strictly keyword?

There is **no `strictly` keyword in Java**.  

You may be referring to **`strictfp`**, which is an actual Java keyword. Here's the explanation:

---

**Definition:**  

- `strictfp` stands for **“strict floating-point”**.  
- It is used to **restrict floating-point calculations** to follow the **IEEE 754 standard** strictly, ensuring **platform-independent results** for `float` and `double` operations.  

---

### **Key Points**

1. **Applies To:**  
   - Classes, interfaces, and methods.  

2. **Purpose:**  
   - Ensures **consistent floating-point behavior** across different platforms (CPU architectures).  

3. **Usage:**  
   - Without `strictfp`, floating-point calculations may differ slightly depending on the hardware.  

---

### **Syntax Example**

```java
strictfp class Calculator {
    strictfp double add(double a, double b) {
        return a + b;
    }
}
```

**Explanation:**  

- Both the `Calculator` class and `add` method are restricted to **strict IEEE 754 floating-point behavior**.  
- Guarantees **same results on all platforms**.  

---

### **Key Notes**

- Only affects **floating-point calculations** (`float` and `double`).  
- `strictfp` does **not affect integer calculations**.  
- Mostly used in **scientific, financial, or engineering applications** where precision consistency is critical.  

🔧 **Summary:**  
`strictfp` → ensures **platform-independent, IEEE-compliant floating-point arithmetic** in Java.  

---

If you want, I can also make a **quick table comparing all Java keywords like `final`, `static`, `volatile`, `transient`, `strictfp`** for reference. Do you want me to do that?

### yes, sure

| Keyword      | Applies To                | Purpose / Description                                                                 | Example |
|-------------|---------------------------|-------------------------------------------------------------------------------------|---------|
| **final**    | Variable, Method, Class   | - Variable → immutable<br>- Method → cannot override<br>- Class → cannot subclass | `final int MAX = 100;` |
| **static**   | Variable, Method, Block, Class | Belongs to the class, shared among all instances; can be accessed without object | `static int count = 0;` |
| **transient**| Instance Variable         | Prevents serialization of a variable                                                | `transient String password;` |
| **volatile** | Instance / Static Variable| Ensures **visibility across threads**, prevents caching issues                      | `volatile boolean flag;` |
| **strictfp** | Class, Interface, Method  | Restricts floating-point calculations to **IEEE 754 standard**, ensuring platform-independent results | `strictfp double calc(double a, double b)` |
| **abstract** | Class, Method            | Class → cannot instantiate<br>Method → must be implemented in subclass             | `abstract class Vehicle { abstract void start(); }` |
| **synchronized** | Method, Block         | Ensures **thread-safety** by locking resources                                      | `synchronized void increment() { count++; }` |
| **native**   | Method                   | Indicates method is implemented in **platform-specific code** (e.g., C/C++)        | `native void print();` |
| **interface**| Type                     | Defines a **contract for classes** to implement                                     | `interface Drivable { void drive(); }` |
| **package**  | Top-level Source File    | Declares the **namespace** for classes                                              | `package com.example;` |
| **import**   | Top-level Source File    | Allows using classes from **other packages** without fully qualified names          | `import java.util.List;` |
| **this**     | Variable, Method, Constructor | Refers to the **current object**                                                | `this.name = name;` |
| **super**    | Variable, Method, Constructor | Refers to **parent class members**                                             | `super.display();` |
| **instanceof** | Operator               | Tests if an object is an instance of a specific class or subclass                   | `if(obj instanceof Car)` |
| **enum**     | Type                     | Defines a **set of constants**                                                      | `enum Day { MON, TUE }` |
| **throw / throws** | Method / Statement  | Used for **exception handling**                                                      | `throw new IOException();` |

---

### ✅ **Summary**

- **`final`** → immutability / restriction  
- **`static`** → class-level members  
- **`transient`** → skip serialization  
- **`volatile`** → thread visibility  
- **`strictfp`** → consistent floating-point calculations  

---

I can also create a **visual map showing which keywords apply to classes, methods, variables, or blocks** for easier memory recall.  

Do you want me to make that visual map?
