# Java Basics, JVM Internals & Language Components

## Core Java & Platform

1. **What is Java?**

   Java is a popular, versatile, and object-oriented programming language known for its "write once, run anywhere" capability. It was developed by Sun Microsystems (now owned by Oracle) in 1995. Java is used for developing a wide range of applications, including desktop, web, mobile, and enterprise software.

2. **Explain the main idea behind Java and the concept of WORA**

   The main idea behind Java is to create a language that is simple, secure, and platform-independent. The concept of "Write Once, Run Anywhere" (WORA) is one of Java's core principles, which means:

   - Java code is first compiled into an intermediate form called bytecode
   - This bytecode can run on any device that has a Java Virtual Machine (JVM) installed
   - The JVM acts as an interpreter between the bytecode and the underlying operating system
   - Developers don't need to rewrite or recompile code for different platforms
   - The same Java application can run on Windows, Mac, Linux, or any other platform with a JVM
   - This platform independence significantly reduces development and maintenance costs

   This approach differs from traditional languages like C/C++, which require platform-specific compilation and often need code modifications to work on different operating systems.

3. **List some important features of Java.**

   - **Platform Independence**: Java programs can run on any device that has the Java Virtual Machine (JVM) installed, making them highly portable.
   - **Object-Oriented**: Java follows the object-oriented programming paradigm, which helps in organizing complex programs into simpler, reusable pieces.
   - **Robust and Secure**: Java has strong memory management, exception handling, and security features that make it a reliable and secure language.
   - **Multithreading**: Java supports multithreading, allowing concurrent execution of two or more threads for maximum utilization of CPU.
   - **Automatic Memory Management**: Java uses garbage collection to automatically manage memory, reducing the risk of memory leaks and other related issues.
   - **Rich Standard Library**: Java comes with a comprehensive standard library that provides many useful utilities and frameworks for various tasks.
   - **High Performance**: Java's Just-In-Time (JIT) compiler and efficient runtime environment contribute to its high performance.
   - **Distributed Computing**: Java supports distributed computing through its networking capabilities, making it suitable for developing large-scale distributed applications.
   - **Dynamic and Extensible**: Java is designed to adapt to evolving environments, with features like dynamic class loading and reflection.
   - **Community Support**: Java has a large and active community, providing extensive resources, libraries, and frameworks to support development.

4. **Can you list some non-object oriented features of Java?**

   - **Primitive Data Types**: Java supports eight primitive data types (byte, short, int, long, float, double, boolean, char) that are not objects.
   - **Static Members**: Static methods and variables belong to the class rather than instances, resembling procedural programming.
   - **Arrays**: While arrays are objects in Java, they provide low-level, fixed-size data storage similar to procedural languages.
   - **Operator Overloading**: Java deliberately excludes operator overloading to maintain simplicity, unlike some OOP languages.
   - **Multiple Inheritance**: Java doesn't support multiple inheritance of classes (though it allows multiple interface implementation).
   - **Procedural Programming**: Java allows writing procedural code within methods, without necessarily using objects.
   - **Pass-by-Value**: Java strictly uses pass-by-value semantics, even for object references.
   - **Global Variables**: Through static fields, Java provides a way to create globally accessible variables.
   - **Command-Line Programming**: Java supports console-based, procedural programming through the main method.

5. **Why is Java Dynamic?**

   Java is considered dynamic due to several key features:

   - **Dynamic Class Loading**: Java can load classes at runtime as needed, rather than loading all classes at startup
   - **Reflection**: Allows programs to examine and modify their structure and behavior at runtime
   - **Late Binding**: Method calls are resolved at runtime rather than compile time
   - **Dynamic Memory Allocation**: Objects are allocated memory dynamically at runtime
   - **Runtime Polymorphism**: The specific method implementation to be executed is determined at runtime
   - **Dynamic Array Bounds**: Array bounds are checked dynamically at runtime
   - **Dynamic Security**: Security policies can be configured and enforced at runtime

6. **What does it mean that Java is a statically typed language? What are the Characteristics of Static Typing**

   Java is a statically typed language, which means that variable types are checked at compile time rather than runtime. This has several important characteristics:

   **Core Characteristics:**

   - All variables must have their type explicitly declared before use
   - Type checking occurs during compilation, catching type errors early
   - Once declared, a variable's type cannot be changed
   - All method parameters and return types must be explicitly declared

   **Benefits:**

   - Early detection of type-related errors during compilation
   - Improved code reliability and maintainability
   - Better performance as type checking is done at compile time
   - Enhanced IDE support with better code completion and error detection
   - Self-documenting code through explicit type declarations

   **Examples:**

   ```java
   // Valid static typing
   String name = "John";
   int age = 25;

   // Invalid - would cause compile error
   String text = "Hello";
   text = 42;  // Error: incompatible types

   // Method with explicit parameter and return types
   public String formatName(String firstName, String lastName) {
       return firstName + " " + lastName;
   }
   ```

   This differs from dynamically typed languages like Python or JavaScript, where types are checked at runtime and variables can change types freely.

7. **Distinguish between static loading and dynamic class loading?**

   Static loading and dynamic class loading are two different approaches to loading classes in Java:

   **Static Loading (Load-Time Loading)**:

   - Classes are loaded at compile time
   - All required classes must be available when the program starts
   - Uses the `new` keyword/operator for object creation
   - Loading happens automatically when the program starts
   - More predictable but less flexible
   - Better performance as classes are loaded upfront
   - Memory is allocated at startup for all classes

   Example of Static Loading:

   ```java
   class TestClass {
     public static void main(String args[]) {
       TestClass tc = new TestClass();
     }
   }
   ```

   **Dynamic Loading (Runtime Loading)**:

   - Classes are loaded on-demand at runtime
   - Classes can be loaded when needed, not necessarily at startup
   - Uses `Class.forName()` or `ClassLoader` methods
   - Loading happens explicitly when requested in code
   - More flexible and memory efficient
   - Allows for plugin architectures and modular applications
   - Can handle situations where class locations are not known at compile time
   - May have slight performance overhead due to runtime loading
   - Requires exception handling

   Example of Dynamic Loading:

   ```java
   try {
       Class.forName("com.example.MyClass");
   } catch (ClassNotFoundException e) {
       // Handle the exception
   }
   ```

8. **What is the difference between JavaEE and JavaSE?**

   JavaSE (Java Standard Edition) and JavaEE (Java Enterprise Edition) are different platforms within the Java ecosystem:

   **Java SE (Standard Edition)**:

   - The core Java platform, providing fundamental Java programming features
   - Contains core libraries and APIs for general-purpose programming
   - Includes basic functionality like collections, I/O, networking, GUI development
   - Used for developing desktop and simple server applications
   - Foundation for other Java editions

   **Java EE (Enterprise Edition)**:

   - Built on top of JavaSE, adding enterprise features
   - Designed for developing large-scale, distributed, multi-tiered enterprise applications
   - Provides additional APIs and services for:
     - Web Applications (Servlets, JSP)
     - Enterprise JavaBeans (EJB)
     - Java Persistence API (JPA)
     - Java Message Service (JMS)
     - Java Transaction API (JTA)
     - Web Services
   - Includes specifications for security, scalability, and reliability
   - Requires an application server (like WildFly, WebSphere, or GlassFish)

   Note: JavaEE has been renamed to Jakarta EE after Oracle transferred it to the Eclipse Foundation.

9. **What are the differences between JDK, JRE, and JVM?**

   | Component | Full Name                | Description                                                                                                                                                                                                                                          |
   | --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | JDK       | Java Development Kit     | A software development environment used for developing Java applications. It includes the JRE, an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc), and other tools needed in Java development. |
   | JRE       | Java Runtime Environment | Provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.                                                                                               |
   | JVM       | Java Virtual Machine     | An abstract computing machine that enables a computer to run a Java program. It provides a runtime environment in which Java bytecode can be executed, ensuring platform independence.                                                               |

10. **What is a ClassLoader? And its role in Java?**

    A ClassLoader in Java is a fundamental component of the Java Runtime Environment (JRE) responsible for loading Java classes and interfaces into the Java Virtual Machine (JVM) during runtime. Its primary role is to convert Java bytecode (.class files) into Class objects that can be used by the JVM.

    Key responsibilities of a ClassLoader include:

    - **Loading Classes**: Reads the bytecode from .class files and creates Class objects
    - **Security**: Ensures classes are loaded from trusted sources and meet Java specifications
    - **Namespace Management**: Maintains separate namespaces for different types of classes
    - **Dynamic Loading**: Loads classes on-demand when they are first referenced

    Java provides three built-in ClassLoaders, each with specific responsibilities:

    - **Bootstrap ClassLoader**:

      - Written in native code (not Java)
      - Loads core Java API classes from rt.jar
      - Parent of all other ClassLoaders

    - **Extension ClassLoader**:

      - Loads classes from extension directories (JAVA_HOME/lib/ext)
      - Child of Bootstrap ClassLoader

    - **System/Application ClassLoader**:
      - Loads application classes from classpath
      - Child of Extension ClassLoader
      - Used to load application-specific classes

    ClassLoaders follow important principles:

    1. **Delegation Hierarchy**: Before loading a class, a ClassLoader asks its parent first
    2. **Visibility**: Child ClassLoaders can see classes loaded by parents, but not vice versa
    3. **Uniqueness**: Same class loaded by different ClassLoaders are treated as different types
    4. **Non-delegation**: Each ClassLoader should load a class only once

11. **What is the difference between path and classpath?**

    | Aspect  | PATH                                                   | CLASSPATH                                           |
    | ------- | ------------------------------------------------------ | --------------------------------------------------- |
    | Purpose | System environment variable to locate executables      | Java-specific variable to locate class files        |
    | Usage   | Finds OS commands and programs (e.g., java, javac)     | Helps JVM find and load Java classes during runtime |
    | Content | Directory paths containing executable files            | Paths to .class files, JAR files, and packages      |
    | Scope   | Operating system level                                 | Java application level                              |
    | Format  | OS-specific path separator (: for Unix, ; for Windows) | Similar path separator but for Java class locations |
    | Default | Usually pre-configured by OS installation              | Current directory (.) if not explicitly set         |

    Example PATH:

    ```
    /usr/local/bin:/usr/bin:/bin
    ```

    Example CLASSPATH:

    ```
    .:/home/user/classes:/home/user/lib/example.jar
    ```

12. **What is bytecode in the context of Java?**

    Bytecode is the intermediate representation of Java code that is generated when Java source code is compiled. Key points about bytecode:

    - It's the compiled form of Java code (.class files)
    - Platform-independent - can run on any device with a JVM
    - Contains instructions that the JVM executes
    - Consists of one-byte operation codes (opcodes) followed by parameters
    - More compact than source code but not machine code
    - JVM interprets or compiles bytecode to native machine code at runtime
    - Can be decompiled back to approximate source code
    - Verified by JVM for security and correctness before execution
    - Other JVM languages (Kotlin, Scala) also compile to bytecode

    Example bytecode instruction:

    ```
    iload_1     // Load integer from local variable 1
    iload_2     // Load integer from local variable 2
    iadd        // Add two integers
    istore_3    // Store result in local variable 3
    ```

13. **What is the purpose of using javap?**

    The `javap` tool is a Java class file disassembler that provides a way to view the details of compiled Java classes. Its primary purposes include:

    - **Inspecting Class Files**: It allows developers to examine the structure of class files, including methods, fields, and their access modifiers.
    - **Understanding Bytecode**: `javap` can display the bytecode instructions contained in a class file, which helps in understanding how Java code is translated into bytecode.
    - **Debugging**: It aids in debugging by providing insights into the compiled code, which can be useful for performance tuning and optimization.
    - **Learning Tool**: It serves as an educational resource for those looking to learn more about Java's compilation process and bytecode.

    Example usage of `javap`:

    ```
    javap -c MyClass
    ```

    This command will display the bytecode for the `MyClass` class.

## Memory Management & Garbage Collection

11. **What is Garbage Collection?**

    Garbage Collection (GC) is Java's automatic memory management system that identifies and removes objects that are no longer being used by the application. Key aspects include:

    - Automatically frees memory by removing unreferenced objects
    - Runs in the background with minimal programmer intervention
    - Uses different algorithms and strategies to identify unused objects
    - Helps prevent memory leaks and manual memory management errors
    - Can impact application performance during collection cycles

    The process works by:

    1. **Marking**: Identifies which objects are in use and which aren't
    2. **Deletion**: Removes unused objects
    3. **Compaction**: Optionally defragments memory by moving remaining objects together

    Example of object eligible for garbage collection:

    ```java
    public void createObject() {
        String str = new String("Hello"); // Creates object
        str = null; // Original object now eligible for GC
    }
    ```

12. **What is the purpose of garbage collection in Java?**

    Garbage collection in Java serves several critical purposes:

    - **Automated Memory Management**: Automatically frees heap memory by removing objects that are no longer referenced by the program
    - **Memory Leak Prevention**: Helps prevent memory leaks by ensuring unused objects don't consume memory indefinitely
    - **Developer Productivity**: Eliminates the need for manual memory management, reducing development time and errors
    - **Program Safety**: Prevents common memory-related bugs like dangling pointers and double free errors
    - **Resource Optimization**: Efficiently manages and reclaims memory resources to maintain application performance

    The garbage collector achieves these goals by:
    - Tracking object references
    - Identifying unreachable objects
    - Reclaiming memory from unused objects
    - Defragmenting memory through compaction when needed

    This automatic memory management is one of Java's key features that distinguishes it from languages like C/C++ where memory must be manually managed.

12. **How can an object be unreferenced?**

    An object can become unreferenced (eligible for garbage collection) in several ways:

    1. **Nulling the Reference**:

       ```java
       Student student = new Student();
       student = null; // Object is now unreferenced
       ```

    2. **Reassigning the Reference**:

       ```java
       Student student = new Student();
       student = new Student(); // First object is now unreferenced
       ```

    3. **Object Goes Out of Scope**:

       ```java
       public void method() {
           Student student = new Student(); // Local variable
       } // student goes out of scope, object becomes unreferenced
       ```

    4. **Island of Isolation**:

       ```java
       class Node {
           Node next;
           Node() {}
       }

       Node node1 = new Node();
       Node node2 = new Node();
       node1.next = node2;
       node2.next = node1;
       node1 = null;
       node2 = null; // Both objects become unreferenced
       ```

    These unreferenced objects become eligible for garbage collection, though the exact timing of collection depends on the JVM's garbage collector implementation.

13. **What are the Memory Allocations available in Java**

    Java's memory structure consists of several key areas:

    1. **Stack Memory**:

       - Used for storing method frames and local variables
       - Follows Last-In-First-Out (LIFO) order
       - Automatically allocated and deallocated
       - Thread-specific - each thread has its own stack
       - Stores primitive values and object references

    2. **Heap Memory**:

       - Shared runtime memory area
       - Stores all objects and arrays
       - Managed by Garbage Collector
       - Divided into:
         - Young Generation (Eden Space, Survivor Spaces)
         - Old Generation
         - Permanent Generation (Removed in Java 8+)

    3. **Class(Method) Area (Metaspace)**:

       - Stores class metadata, methods, and static variables
       - Shared across all threads
       - Part of native memory (not heap) since Java 8

    4. **Program Counter (PC) Register**:

       - Per-thread register
       - Holds address of current executing instruction
       - Helps with thread execution management

    5. **Native Method Stack**:
       - Supports native method execution
       - Used for C/C++ calls from Java
       - One per thread

    Each memory area serves a specific purpose in Java's memory management system, contributing to the language's efficiency and reliability.

14. **The difference between Serial and Parallel Garbage Collector?**

    Serial and Parallel Garbage Collectors differ in several key aspects:

    1. **Serial Garbage Collector**:

       - Single-threaded collector
       - Uses only one CPU core
       - Stops all application threads during GC ("stop-the-world")
       - Best suited for:
         - Single-processor systems
         - Small applications with small heap sizes
         - Simple desktop applications
       - Enabled using -XX:+UseSerialGC

    2. **Parallel Garbage Collector**:
       - Multi-threaded collector
       - Uses multiple CPU cores simultaneously
       - Still has "stop-the-world" pauses but shorter duration
       - Best suited for:
         - Multi-processor/multi-core systems
         - Applications with medium to large heap sizes
         - Batch processing where throughput is important
       - Enabled using -XX:+UseParallelGC
       - Can configure number of threads using -XX:ParallelGCThreads

    The main tradeoff is between simplicity (Serial) and performance (Parallel), with Parallel GC generally providing better throughput on modern hardware.

15. **How does the Garbage Collector algorithm work? Or How does garbage collection work in Java?**

    Garbage Collection (GC) in Java is an automatic memory management process that identifies and removes unused objects from heap memory. Here's how it works:

    1. **Object Marking**:

       - Starts from "root" references (static variables, local variables, etc.)
       - Traverses object graph marking all reachable objects as "live"
       - Any objects not marked are considered garbage

    2. **Memory Allocation Phases**:

       - Objects are first allocated in Eden space (Young Generation)
       - Surviving objects move to Survivor spaces
       - Long-lived objects promote to Old Generation

    3. **Collection Process**:

       - **Minor GC**:

         - Collects Young Generation only
         - More frequent but faster
         - Uses "Copy and Compact" approach

       - **Major GC**:
         - Collects Old Generation
         - Less frequent but more time-consuming
         - May use different algorithms (Mark-Sweep-Compact)

    4. **Key Algorithms**:
       - Mark-Sweep: Marks live objects, removes unmarked
       - Mark-Compact: Additionally compacts memory after sweep
       - Copy Collection: Copies live objects to new space
       - Generational Collection: Different strategies for young/old objects

    The GC process is automatic but can be influenced through JVM parameters and choice of collector implementation (Serial, Parallel, CMS, G1, ZGC).

16. **What are the differences between Heap and Stack Memory in Java?**

    | Aspect            | Stack Memory                                                 | Heap Memory                                     |
    | ----------------- | ------------------------------------------------------------ | ----------------------------------------------- |
    | Memory Type       | Static memory allocation                                     | Dynamic memory allocation                       |
    | Access Speed      | Faster access                                                | Relatively slower access                        |
    | Memory Management | Automatic (LIFO order)                                       | Manual allocation, automatic deallocation by GC |
    | Size              | Smaller, fixed size                                          | Larger, flexible size                           |
    | Thread Safety     | Each thread has own stack                                    | Shared across all threads                       |
    | Storage           | Primitive values, method frames, local variables, references | Objects, arrays, class instances                |
    | Lifetime          | Short-lived - exists for method duration                     | Objects persist until no references remain      |
    | Memory Order      | Contiguous memory blocks                                     | No specific memory order                        |
    | Memory Control    | Size controlled by JVM (-Xss)                                | Initial/Max size controlled by JVM (-Xms/-Xmx)  |
    | Memory Errors     | StackOverflowError                                           | OutOfMemoryError                                |

17. **What are the possible ways of making object eligible for garbage collection (GC) in Java?**

    An object becomes eligible for garbage collection when it is no longer reachable. Here are the main ways to make an object eligible for GC:

    1. **Nullifying References**:

       - Set object references to null
       - Example: `Student student = new Student(); student = null;`

    2. **Reassigning References**:

       - Point reference variable to another object
       - Original object becomes unreachable
       - Example: `student = new Student();` // old object eligible for GC

    3. **Object goes out of Scope**:

       - Local objects become eligible when method ends
       - Example:
         ```java
         void method() {
             Student student = new Student(); // eligible after method ends
         }
         ```

    4. **Island of Isolation**:

       - Objects only reference each other but no external references
       - Example:
         ```java
         class Node {
             Node next;
             // Circular reference but no external reference
             Node a = new Node();
             Node b = new Node();
             a.next = b;
             b.next = a;
             a = b = null; // Island now eligible for GC
         }
         ```

    5. **Removing References from Collections**:
       - Clear collections or remove objects from them
       - Example: `list.clear();` or `map.remove(key);`

18. **What is a Memory Leak? Discuss some common causes of it.**

    A memory leak occurs when a program fails to release memory that is no longer needed, causing the application to consume more and more memory over time. In Java, despite having garbage collection, memory leaks can still occur.

    Common causes of memory leaks in Java:

    1. **Unclosed Resources**

       - Not closing database connections
       - Not closing file streams
       - Not releasing network sockets

    2. **Static References**

       - Adding objects to static collections but never removing them
       - Static fields holding references to objects that should be temporary

    3. **Inner Class References**

       - Non-static inner classes holding implicit references to their outer class
       - Anonymous classes in long-living objects

    4. **Improper equals()/hashCode() Implementation**

       - Objects stored in HashSet/HashMap but with poorly implemented equality methods
       - Leading to duplicate objects accumulating

    5. **Thread-Local Variables**
       - Not removing ThreadLocal variables when no longer needed
       - Especially in application servers where threads are reused

    Example of a potential memory leak:

    ```java
    public class Cache {
        private static final Map<String, Object> cache = new HashMap<>();

        public void addToCache(String key, Object value) {
            cache.put(key, value);  // Objects are never removed!
        }
    }
    ```

    Prevention strategies:

    - Always close resources using try-with-resources
    - Use WeakHashMap for caches when appropriate
    - Implement proper cleanup methods
    - Profile application memory usage regularly
    - Use memory analysis tools (like JProfiler, MAT)

19. **What are the different types of garbage collectors in Java?**

    Java provides several garbage collector implementations, each optimized for different use cases:

    1. **Serial GC**

       - Single-threaded collector
       - Simple and efficient for small applications
       - Uses mark-sweep-compact algorithm
       - Good for small heaps and single CPU environments

    2. **Parallel GC (Throughput Collector)**

       - Multiple threads for collection
       - Default GC in Java 8
       - Focuses on maximizing throughput
       - Best for multi-core systems running batch processing

    3. **CMS (Concurrent Mark Sweep)**

       - Minimizes pause times by doing most work concurrently
       - Good for applications requiring low latency
       - More CPU-intensive
       - Can lead to heap fragmentation

    4. **G1 (Garbage First)**

       - Default GC since Java 9
       - Divides heap into regions
       - Predictable pause times
       - Good for large heaps (>4GB)
       - Balance between latency and throughput

    5. **ZGC (Z Garbage Collector)**

       - Introduced in Java 11
       - Designed for very large heaps
       - Ultra-low latency (<10ms pause times)
       - Concurrent and scalable

    6. **Shenandoah**
       - Similar to ZGC
       - Ultra-low pause times
       - Concurrent compaction
       - Available in OpenJDK

    Selection can be done using JVM flags, e.g., `-XX:+UseG1GC` for G1 collector.

## Variables & Data Types

1. **What is a Java Variable?**

   A Java variable is a named storage location in memory that holds a value of a specific data type. Variables are used to store and manipulate data in a program.

   | Aspect            | Description                                                                                                        |
   | ----------------- | ------------------------------------------------------------------------------------------------------------------ |
   | Definition        | A named container for storing data values                                                                          |
   | Declaration       | Specifies the variable's name and data type                                                                        |
   | Initialization    | Assigns an initial value to the variable                                                                           |
   | Scope             | Determines where the variable can be accessed within the code                                                      |
   | Data Types        | Can be primitive (byte, short, int, long, float, double, boolean, char) or reference (objects, arrays, interfaces) |
   | Naming Convention | Follows camelCase, starts with a letter, $, or \_                                                                  |
   | Example           | `int age = 25;` or `String name = "John";`                                                                         |

2. **What are data types?**

   Data types in Java specify the type of data that can be stored in a variable. Java has two categories of data types:

   | Category             | Data Types    | Description                                                                                                                                                | Size    |
   | -------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
   | Primitive Data Types | byte          | - 8-bit signed two's complement integer<br>- Minimum value is -128 (-2^7)<br>- Maximum value is 127 (inclusive)(2^7 -1)<br>- Default value is 0<br>        | 1 byte  |
   |                      | short         | - 16-bit signed two's complement integer<br>- Minimum value is -32,768 (-2^15)<br>- Maximum value is 32,767 (inclusive) (2^15 -1)<br>- Default value is 0. | 2 bytes |
   |                      | int           | 32-bit signed two's complement integer                                                                                                                     | 4 bytes |
   |                      | long          | 64-bit signed two's complement integer                                                                                                                     | 8 bytes |
   |                      | float         | Single-precision 32-bit IEEE 754 floating point                                                                                                            | 4 bytes |
   |                      | double        | Double-precision 64-bit IEEE 754 floating point                                                                                                            | 8 bytes |
   |                      | boolean       | true or false                                                                                                                                              | 1 bit   |
   |                      | char          | 16-bit Unicode character                                                                                                                                   | 2 bytes |
   | Reference Data Types | Class objects | User-defined types                                                                                                                                         | Varies  |
   |                      | Array         | Collection of similar data types                                                                                                                           | Varies  |
   |                      | Interface     | Abstract type                                                                                                                                              | N/A     |

   Primitive types are predefined by the language and named by a keyword. Reference data types are created by the programmer and are not defined by the language (except for String).

3. **What is the difference between an int and an Integer in Java?**

   | Aspect               | int                              | Integer                                             |
   | -------------------- | -------------------------------- | --------------------------------------------------- |
   | Type                 | Primitive data type              | Wrapper class (Reference type)                      |
   | Memory               | 32 bits in stack memory          | Object in heap memory with overhead                 |
   | Default Value        | 0                                | null                                                |
   | Usage in Collections | Cannot be used directly          | Can be used in collections (ArrayList etc.)         |
   | Methods/Operations   | Only basic arithmetic operations | Additional utility methods (parseInt, valueOf etc.) |
   | Null Assignment      | Cannot be null                   | Can be assigned null                                |
   | Performance          | Better performance               | Slightly slower due to object overhead              |
   | Autoboxing/Unboxing  | N/A                              | Automatic conversion between int and Integer        |
   | Memory Usage         | Less memory                      | More memory due to object overhead                  |
   | Usage in Generics    | Cannot be used                   | Can be used as type parameter                       |

4. **What are literals in Java?**

   Literals are fixed values that can be directly used in code. Java supports several types of literals:

   | Type                    | Description                 | Examples                                                                           |
   | ----------------------- | --------------------------- | ---------------------------------------------------------------------------------- |
   | Integer Literals        | Fixed whole number values   | Decimal: `42`<br>Hexadecimal: `0xFF`<br>Binary: `0b1010`<br>Long: `42L`            |
   | Floating-Point Literals | Fixed decimal number values | Float: `3.14f`<br>Double: `3.14` or `3.14d`<br>Scientific notation: `1.23e4`       |
   | Character Literals      | Single character values     | Single character: `'A'`<br>Unicode: `'\u0041'`<br>Escape sequences: `'\n'`, `'\t'` |
   | String Literals         | Text values                 | Regular string: `"Hello World"`<br>String with escape sequences: `"Hello\nWorld"`  |
   | Boolean Literals        | Logical values              | `true`, `false`                                                                    |
   | Null Literal            | Empty reference value       | `null`                                                                             |

   Example:

   ```java
   int decimal = 42;
   double pi = 3.14;
   char letter = 'A';
   String message = "Hello";
   boolean flag = true;
   Object obj = null;
   ```

5. **What are wrapper classes? Why do we need wrapper classes?**

   Wrapper classes in Java are used to convert primitive data types into objects. Each primitive type has a corresponding wrapper class that provides a way to use these primitives as objects. This is particularly useful in situations where objects are required, such as in collections like ArrayList. The wrapper classes in Java include:

   - **Integer**: for int
   - **Double**: for double
   - **Character**: for char
   - **Boolean**: for boolean
   - **Byte**: for byte
   - **Short**: for short
   - **Long**: for long
   - **Float**: for float

   We need wrapper classes for several reasons:

   1. **Collections**: Java collections like ArrayList can only store objects, not primitives
   2. **Null values**: Primitives cannot be null, but wrapper objects can represent null values
   3. **Utility methods**: Wrapper classes provide helpful methods for:
      - Type conversion (e.g., Integer.parseInt())
      - Value comparison
      - Number formatting
   4. **Generics**: Type parameters in generic classes must be objects
   5. **Synchronization**: Objects are needed for synchronization in multithreading

   Wrapper classes also enable automatic boxing (primitive to wrapper) and unboxing (wrapper to primitive), making it convenient to work with both forms:

   ```java
   Integer num = 5;    // autoboxing
   int value = num;    // auto-unboxing
   ```

6. **What are the different ways of creating Wrapper class instances? Or What are differences in the two ways of creating Wrapper classes?**

   There are several ways to create wrapper class instances in Java:

   1. **Using Constructor (Deprecated)**:

   ```java
   Integer num1 = new Integer(42);        // Deprecated since Java 9
   Double dbl1 = new Double(3.14);        // Not recommended
   ```

   2. **Using Static Factory Methods**:

   ```java
   Integer num2 = Integer.valueOf(42);    // Preferred method
   Double dbl2 = Double.valueOf(3.14);    // Recommended approach
   ```

   3. **Autoboxing (Automatic Conversion)**:

   ```java
   Integer num3 = 42;                     // Autoboxing primitive to wrapper
   Double dbl3 = 3.14;                    // Automatic conversion
   ```

   4. **Parsing from Strings**:

   ```java
   Integer num4 = Integer.parseInt("42");     // Convert string to Integer
   Double dbl4 = Double.parseDouble("3.14"); // Convert string to Double
   ```

   5. **Using Class Methods**:

   ```java
   Integer num5 = Integer.valueOf("42");      // From string
   Long lng1 = Long.valueOf(42L);             // From long primitive
   ```

   Key points to remember:

   - `valueOf()` is preferred over constructors
   - Autoboxing provides the most concise syntax
   - Parsing methods are useful for converting strings
   - Each wrapper class has similar creation methods

7. **What are autoboxing and unboxing?**

   Autoboxing and unboxing are automatic conversions between primitive data types and their corresponding wrapper classes in Java:

   **Autoboxing**:

   - Automatic conversion of primitive types to their wrapper class objects
   - Example: `int` to `Integer`, `double` to `Double`
   - Happens when:
     - Assigning primitive to wrapper class variable
     - Passing primitive to method expecting wrapper
     - Adding primitive to collection

   **Unboxing**:

   - Automatic conversion of wrapper class objects to their primitive types
   - Example: `Integer` to `int`, `Double` to `double`
   - Happens when:
     - Assigning wrapper to primitive variable
     - Passing wrapper to method expecting primitive
     - Using wrapper in arithmetic operations

   Example demonstrating both:

   ```java
   // Autoboxing
   Integer num = 100;    // int -> Integer
   ArrayList<Integer> list = new ArrayList<>();
   list.add(50);        // int -> Integer

   // Unboxing
   int value = num;     // Integer -> int
   int sum = num + 50;  // Integer -> int for calculation
   ```

   Benefits:

   - Simplifies code by eliminating explicit conversions
   - Enables primitives to work with collections
   - Makes code more readable and maintainable

8. **What are variable types?**

   | Variable Type          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Local Variables        | - Declared in methods, constructors, or blocks<br>- Created when the method, constructor or block is entered and destroyed once it exits<br>- No access modifiers can be used<br>- Visible only within the declared method, constructor, or block<br>- No default value, must be declared and initialized before use                                                                                                                                                                                                                          |
   | Instance Variables     | - Declared in a class, but outside a method, constructor or any block<br>- Created when an object is created with the 'new' keyword and destroyed when the object is destroyed<br>- Can use access modifiers<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed directly by calling the variable name inside the class                                                                                           |
   | Class/Static Variables | - Declared with the static keyword in a class, but outside a method, constructor or block<br>- Only one copy per class, regardless of how many objects are created<br>- Created when the program starts and destroyed when the program stops<br>- Can be declared as public/private, final, and static<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed by calling with the class name: ClassName.VariableName |

9. **What is the difference between transient and volatile variable in Java?**

   | Feature | Transient                                                  | Volatile                                                   |
   | ------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
   | Purpose | Controls object serialization                              | Ensures thread-safe access to variables                    |
   | Usage   | Marks fields that should not be serialized                 | Marks fields that may be modified by multiple threads      |
   | Scope   | Serialization process                                      | Multi-threaded environments                                |
   | Effect  | Field is skipped during serialization                      | Forces reads/writes directly to main memory                |
   | Default | null for objects, 0/false for primitives after deserialize | Retains actual value but ensures visibility across threads |

   Example of transient:

   ```java
   public class User implements Serializable {
       private String username;
       private transient String password; // won't be serialized
   }
   ```

   Example of volatile:

   ```java
   public class Counter {
       private volatile int count = 0; // ensures thread-safe access

       public void increment() {
           count++;
       }
   }
   ```

10. **What is Type Casting (Type Conversion)**

    Type casting is the process of converting a value from one data type to another in Java. There are two types of type casting:

    1. Widening Casting (Implicit) - automatically converting a smaller type to a larger type size
       `byte -> short -> char -> int -> long -> float -> double`

    - **Example**:

    ```java
    byte byteValue = 10;
    int intValue = byteValue; // Widening casting from byte to int
    ```

    1. Narrowing Casting (Explicit) - manually converting a larger type to a smaller size type
       `double -> float -> long -> int -> char -> short -> byte`

    - **Example**:

    ```java
    double doubleValue = 9.78;
    int intValue = (int) doubleValue; // Narrowing casting from double to int
    ```

    Widening casting is done automatically when passing a smaller size type to a larger size type. Narrowing casting must be done manually by placing the type in parentheses in front of the value.

## Keywords & Language Features

1. **What is the difference between final, finally and finalize keywords in Java?**

   Here's a comparison of final, finally, and finalize keywords in Java:

   1. **final**:

      - Used to make variables, methods, or classes unchangeable/non-inheritable
      - Variables become constants
      - Methods cannot be overridden
      - Classes cannot be inherited

        ```java
        final class FinalExample {
            final int constant = 100;

            final void cannotOverride() {
                System.out.println("This method cannot be overridden");
            }
        }
        ```

   2. **finally**:

      - Used with try-catch blocks
      - Code in finally block always executes whether exception occurs or not
      - Used for cleanup operations like closing resources

        ```java
        try {
            // Some code that may throw exception
            FileReader file = new FileReader("file.txt");
        } catch (Exception e) {
            // Handle exception
            System.out.println("Error: " + e.getMessage());
        } finally {
            // Always executes
            System.out.println("Finally block executed");
            // Close resources here
        }
        ```

   3. **finalize**:

      - Method called by garbage collector before destroying object
      - Used to perform cleanup operations before object is garbage collected
      - Deprecated since Java 9

        ```java
        public class FinalizeExample {
            protected void finalize() throws Throwable {
                try {
                    // Cleanup operations
                    System.out.println("Finalize method called");
                } finally {
                    super.finalize();
                }
            }
        }
        ```

2. **What is the final and final blank variable? Can we initialize the final blank variable?**

   1. **Final Variable**:

      - A variable declared with the `final` keyword
      - Value cannot be changed once assigned
      - Must be initialized when declared or in constructor
      - Provides immutability
      - Helps in creating constants

      ```java
      final int MAX_VALUE = 100; // Initialized at declaration
      final String MESSAGE = "Hello"; // Can be final for Strings too
      ```

   2. **Final Blank Variable**:

      - A final variable that is not initialized at declaration
      - Must be initialized exactly once
      - Can be initialized in:
        - Constructor
        - Instance initialization block
      - Allows dynamic initialization based on constructor parameters
      - Prevents reassignment after initialization

      ```java
      public class Example {
          final int value; // Blank final variable

          // Initialization in constructor
          public Example(int val) {
              value = val; // Must be initialized here
          }

          // Another example with multiple constructors
          public Example() {
              value = 10; // Must initialize in ALL constructors
          }
      }
      ```

   **Key Points**:

   - Final blank variables MUST be initialized before use
   - Can only be assigned once
   - Provides a way to create runtime constants
   - Helps in creating immutable objects

3. **What is a compile time constant in Java?**

   A compile-time constant in Java is a variable that:

   - Is declared as `static final`
   - Is of primitive type or String
   - Is initialized with a constant expression at declaration
   - Value is known at compile time

   Example:

   ```java
   public class Constants {
       // Compile-time constants
       static final int MAX_VALUE = 100;
       static final String PREFIX = "user_";
       static final double PI = 3.14159;

       // Not compile-time constants
       static final int random = new Random().nextInt(); // Value not known at compile time
       static final StringBuilder sb = new StringBuilder(); // Not a primitive/String
   }
   ```

   Benefits:

   - Values are inlined by the compiler for better performance
   - No runtime overhead as values are resolved during compilation
   - Memory efficient as they are stored in the constant pool

4. **What is this keyword in java? Or What is the significance of the this keyword in Java?**

   The `this` keyword in Java is a reference variable that refers to the current object. It has several important uses:

   1. **Distinguish Instance Variables from Parameters**:

      ```java
      public class Employee {
          private String name;
          public Employee(String name) {
              this.name = name; // 'this.name' refers to instance variable
          }
      }
      ```

   2. **Pass Current Object as Parameter**:

      ```java
      public class Chain {
          public Chain doSomething() {
              // some code
              return this; // returns current object for method chaining
          }
      }
      ```

   3. **Call Current Class Constructor**:

      ```java
      public class Person {
          public Person() {
              // default constructor
          }
          public Person(String name) {
              this(); // calls default constructor
              // additional initialization
          }
      }
      ```

   4. **Return Current Class Instance**:
      ```java
      public class Singleton {
          private static Singleton instance;
          public static Singleton getInstance() {
              if(instance == null) {
                  instance = new Singleton();
              }
              return instance;
          }
      }
      ```

5. **What are the advantages of passing this into a method instead of the current class object itself?**

   Passing `this` into a method instead of the current class object has several advantages:

   1. **Type Safety**:

      - `this` is guaranteed to be the correct type at compile time
      - No need for type casting which could fail at runtime

   2. **Performance**:

      - No need to create a new reference to the object
      - Avoids unnecessary object creation and memory allocation

   3. **Clear Intent**:

      - Makes it explicit that you're passing the current instance
      - Improves code readability and maintainability

   4. **Method Chaining**:

      - Enables fluent interfaces and method chaining
      - Example:

      ```java
      class Builder {
          void process(Builder b) {
              // processing
          }

          Builder chainedMethod() {
              process(this); // enables chaining
              return this;
          }
      }
      ```

   5. **Event Handling**:
      - Useful in event listeners and callbacks
      - Maintains reference to the original object context

6. **What is super in java? When can you use the super keyword? What are the main uses of the super keyword?**

   The `super` keyword in Java is a reference variable that refers to the immediate parent class object. It provides a way to access parent class members that are hidden or overridden in the child class.

   The `super` keyword can be used in the following scenarios:

   1. **Call Parent Class Constructor**:

      - Must be the first statement in a child class constructor
      - Used to ensure proper initialization of parent class members
      - Syntax: `super()` or `super(parameters)`

   2. **Call Parent Class Methods**:

      - Used to call an overridden method from the parent class
      - Helps avoid recursion when overriding methods
      - Syntax: `super.methodName()`

   3. **Access Parent Class Fields**:
      - Used to access fields from parent class that are hidden by child class
      - Helps resolve naming conflicts between parent and child class fields
      - Syntax: `super.fieldName`

   Example:

   ```java
   class Vehicle {
       protected String brand = "Ford";

       public void honk() {
           System.out.println("Beep!");
       }
   }

   class Car extends Vehicle {
       private String brand = "Tesla";  // hides parent's brand

       public Car() {
           super();  // calls Vehicle's constructor
       }

       public void displayInfo() {
           super.honk();  // calls Vehicle's honk method
           System.out.println("Parent brand: " + super.brand);  // accesses Vehicle's brand
           System.out.println("Child brand: " + this.brand);    // accesses Car's brand
       }
   }
   ```

7. **What are the main uses of this keyword?**

   The `this` keyword in Java is a reference variable that refers to the current object instance. Here are its main uses:

   1. **Differentiate Instance Variables from Parameters**:

      ```java
      public class Person {
          private String name;
          public Person(String name) {
              this.name = name; // Distinguishes field from parameter
          }
      }
      ```

   2. **Call Current Class Methods**:

      - Can be used to invoke another method in the same class
      - Example: `this.methodName()`

   3. **Pass Current Object as Parameter**:

      ```java
      public void process(Handler handler) {
          handler.handle(this); // Passing current object
      }
      ```

   4. **Constructor Chaining**:

      - Call another constructor in same class
      - Must be first statement in constructor
      - Example: `this()` or `this(parameters)`

   5. **Return Current Class Instance**:

      ```java
      public Person setName(String name) {
          this.name = name;
          return this; // Method chaining
      }
      ```

   6. **Distinguish Instance Members**:
      - Access instance variables when shadowed by local variables
      - Access instance methods explicitly

8. **Can we assign the reference to this variable?**

   No, we cannot assign a reference to the `this` variable in Java. The `this` reference is implicitly assigned by the JVM and is read-only. Attempting to assign a value to `this` will result in a compilation error.

   Example:

   ```java
   public class Example {
       public void method() {
           this = new Example(); // Compilation error: Cannot assign to 'this'
       }
   }
   ```

   This restriction helps maintain object identity and prevents confusion about which object instance a method is operating on.

9. **Can this keyword be used to refer static members?**

   While it's not recommended, the `this` keyword can technically be used to refer to static members in Java. However, it's considered bad practice because:

   - The `this` keyword represents the current instance of a class
   - Static members belong to the class itself, not to any specific instance
   - Using the class name is clearer and more explicit

   Example showing it works but isn't recommended:

   ```java
   public class Main {
       private static int count = 10;
       private int id;

       public Main() {
           System.out.println(++this.count);   // Works fine with static member
           System.out.println(++this.id);      // Works with instance member
       }
   }
   ```

   The recommended way to access static members is using the class name:

   ```java
   Main.count++;    // Clearer and more explicit
   ```

10. **What are the differences between this and super keyword?**

    | Feature           | super keyword                                                          | this keyword                                                             |
    | ----------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------ |
    | Purpose           | Used to refer to immediate parent class object                         | Used to refer to current class object                                    |
    | Member Access     | Accesses parent class members hidden by child class                    | Accesses current class members                                           |
    | Constructor Usage | Must be first statement in constructor when calling parent constructor | Must be first statement in constructor when calling another constructor  |
    | Static Context    | Cannot be used in static context                                       | Cannot be used in static context                                         |
    | Common Use Case   | Used with inheritance to access overridden methods/fields              | Used to avoid naming conflicts between instance variables and parameters |
    | Constructor Call  | super() calls parent constructor                                       | this() calls another constructor in same class                           |
    | Method Call       | super.method() calls parent version                                    | this.method() calls current class version                                |
    | Variable Access   | super.variable accesses parent's variable                              | this.variable accesses current class variable                            |
    | Scope             | Can only access immediate parent class                                 | Can access all members of current class                                  |

11. **Can you use this and super both in a constructor?**

    No, you cannot use both `this()` and `super()` in the same constructor because:

    - Both `this()` and `super()` must be the first statement in a constructor
    - Only one of them can be the first statement
    - They cannot be used together in the same constructor

    Example showing this restriction:

    ```java
    class Parent {
        Parent() {
            System.out.println("Parent constructor");
        }
    }

    class Child extends Parent {
        Child() {
            super();  // OK - calls Parent constructor
            // this(); // Error - can't use both super() and this()
        }

        Child(int x) {
            this();   // OK - calls Child()
            // super(); // Error - can't use both this() and super()
        }
    }
    ```

    However, you can use `this` and `super` keywords (without parentheses) to refer to members in the same constructor:

    ```java
    class Child extends Parent {
        private int value;

        Child(int value) {
            super();  // Call parent constructor
            this.value = value;  // Use this to refer to instance variable
            super.someMethod();  // Use super to call parent method
        }
    }
    ```

12. **Is there any case when finally will not be executed? If yes then list the case.**

    Yes, there are a few cases where the finally block may not execute:

    1. If `System.exit()` is called within the try or catch block
    2. If the JVM crashes or is terminated abruptly
    3. If the thread executing the try-catch block is interrupted or killed
    4. If there is an infinite loop in the try or catch block
    5. If a fatal error occurs that causes the JVM to crash (e.g., OutOfMemoryError, StackOverflowError)

    Example with System.exit():

    ```java
    try {
        System.out.println("In try block");
        System.exit(0);  // Finally block won't execute
    } catch (Exception e) {
        System.out.println("In catch block");
    } finally {
        System.out.println("This won't be printed");
    }
    ```

13. **What is the purpose of the finalize method? How many times is the finalize method called?**

    The finalize method is called only once for each object by the garbage collector before the object is garbage collected. However, there are important points to note:

    - There is no guarantee when or if finalize() will be called, as it depends on the garbage collector
    - An object can be resurrected during finalization, but finalize() won't be called again when that object becomes garbage again
    - Since Java 9, the finalize() method has been deprecated because it is inherently problematic and unpredictable
    - It's recommended to use try-with-resources or explicit cleanup methods instead of relying on finalize()

14. **Is it possible to use this keyword in Java to refer to the static members?**

    No, the `this` keyword cannot be used to refer to static members in Java. The `this` keyword refers to the current instance of a class, while static members belong to the class itself rather than any specific instance.

    To access static members, you should:

    - Use the class name: `ClassName.staticMember`
    - Or access directly within the same class: `staticMember`

    Example:

    ```java
    public class Example {
        private static int count = 0;
        private int instanceVar = 0;

        public void method() {
            this.instanceVar = 1;    // Valid - refers to instance variable
            this.count = 1;          // Invalid - cannot use this with static
            Example.count = 1;       // Valid - proper way to access static
            count = 1;               // Also valid when in same class
        }
    }
    ```

15. **Differentiate between static and non-static methods in Java.**

    Static methods and non-static methods have several key differences:

    **Static Methods**:

    - Belong to the class rather than any specific instance
    - Can be called without creating an object of the class
    - Cannot access non-static members directly
    - Cannot use 'this' keyword
    - Memory allocated once when class is loaded
    - Often used for utility functions

    Example of static method:

    ```java
    public class Calculator {
        public static int add(int a, int b) {
            return a + b;
        }
    }
    // Called as:
    Calculator.add(5, 3);
    ```

    **Non-static Methods**:

    - Belong to instances of the class
    - Require an object instance to be called
    - Can access both static and non-static members
    - Can use 'this' keyword
    - Memory allocated for each instance
    - Used for object-specific behaviors

    Example of non-static method:

    ```java
    public class Student {
        private String name;

        public void setName(String name) {
            this.name = name;
        }
    }
    // Called as:
    Student student = new Student();
    student.setName("John");
    ```

16. **What are the restrictions that are applied to the Java static methods?**

    Static methods in Java have several restrictions:

    - **Cannot access non-static members**: Static methods cannot directly access instance variables or instance methods. They can only access static members of the class.

    - **Cannot use 'this' keyword**: Since static methods do not belong to any specific instance, they cannot use the 'this' keyword, which refers to the current object.

    - **Cannot be overridden in the same way as instance methods**: While static methods can be hidden (not overridden) in subclasses, they do not exhibit polymorphic behavior like instance methods.

    - **Cannot be abstract**: Static methods cannot be declared as abstract, as they must have a body.

    - **Cannot be synchronized**: Static methods can be synchronized, but the synchronization applies to the class level, not the instance level.

    These restrictions are important to understand when designing classes and methods in Java.

17. **Why is the main method static?**

    The main method in Java is static because it allows the Java Virtual Machine (JVM) to invoke it without needing to create an instance of the class. Since the main method serves as the entry point for the program, it must be accessible to the JVM at the start of the application. By being static, it can be called directly using the class name, ensuring that the program can start running without any prior object instantiation. Additionally, static methods cannot access instance variables or methods, which aligns with the main method's purpose of being a standalone entry point.

18. **What is the difference between static (class) method and instance method?**

    | Aspect          | Static (Class) Method                   | Instance Method                             |
    | --------------- | --------------------------------------- | ------------------------------------------- |
    | Declaration     | Declared with `static` keyword          | Declared without `static` keyword           |
    | Object Instance | Does not require object instance        | Requires object instance to be called       |
    | Access          | Can only access static members directly | Can access both static and instance members |
    | Memory          | Single copy shared across all instances | Separate copy for each instance             |
    | 'this' keyword  | Cannot use 'this' keyword               | Can use 'this' keyword                      |
    | Calling syntax  | Called using ClassName.methodName()     | Called using objectName.methodName()        |
    | Purpose         | Operations related to class as a whole  | Operations specific to object instance      |
    | Polymorphism    | Cannot be overridden (can be hidden)    | Can be overridden in subclasses             |

## Control Flow & Operators

1. **What are Operators? What are the types of Operators?**

   Java operators are symbols that perform operations on variables and values. They allow us to execute various operations such as addition, subtraction, and comparisons. The different types of operators in Java are as follows:

   | Operator Type           | Description                                                                               |
   | ----------------------- | ----------------------------------------------------------------------------------------- |
   | Arithmetic Operators    | Used for mathematical calculations (+, -, \*, /, %, ++, --).                              |
   | Relational Operators    | Used to compare two values (==, !=, >, <, >=, <=, ===, !==).                              |
   | Bitwise Operators       | Operate on bits and perform bit-by-bit operations (&, \|, ^, ~, <<, >>, >>>).             |
   | Logical Operators       | Used to combine multiple boolean expressions (&&, \|\| ,!).                               |
   | Assignment Operators    | Used to assign values to variables (=, +=, -=, \*=, /=, %=, &=, \|=, ^=, <<=, >>=, >>>=). |
   | Miscellaneous Operators | Includes conditional (ternary) operator (`? :`), instanceof operator (`instanceof`).      |

2. **What is Java instanceOf operator?**

   The instanceof operator in Java is a type comparison operator used to test whether an object is an instance of a specific class, interface, or superclass. It returns true if the object is an instance of the specified type, and false otherwise.

   Example:

   ```java
   String str = "Hello";
   if (str instanceof String) {
       // This will evaluate to true
       System.out.println("str is a String");
   }

   Object obj = new ArrayList<>();
   if (obj instanceof List) {
       // This will evaluate to true since ArrayList implements List
       System.out.println("obj is a List");
   }
   ```

   Key points about instanceof:

   - It's commonly used before type casting to prevent ClassCastException
   - Returns false if the object being tested is null
   - Can be used with interfaces and abstract classes
   - Often used in inheritance hierarchies to determine object types

3. **What is the difference between ++a and a++ increment operators?**

   The ++a (pre-increment) and a++ (post-increment) operators both increment a variable by 1, but they differ in when the increment occurs and what value is returned:

   **Pre-increment (++a)**:

   - Increments the value first, then returns the incremented value
   - The increment happens before the value is used in the expression

   **Post-increment (a++)**:

   - Returns the original value first, then increments
   - The increment happens after the value is used in the expression

   Example:

   ```java
   int a = 5;
   int b = ++a;  // a is incremented to 6, then b gets 6
   // Now a = 6, b = 6

   int x = 5;
   int y = x++;  // y gets 5, then x is incremented to 6
   // Now x = 6, y = 5
   ```

   This difference is particularly important in expressions and method calls where the returned value matters.

4. **What are loops? What are the types of loops?**

   Loops are control structures that allow you to execute a block of code multiple times, depending on a specified condition. In Java, there are several types of loops that you can use to handle repetitive tasks:

   1. **while loop**: Repeats a statement or a group of statements while a given condition is true. The condition is evaluated before the execution of the loop body.

   2. **for loop**: Executes a sequence of statements multiple times and is typically used when the number of iterations is known beforehand. It includes initialization, condition, and increment/decrement in a single line.

   3. **do...while loop**: Similar to the while loop, but it tests the condition at the end of the loop body, ensuring that the loop body is executed at least once.

   4. **Enhanced for loop (for-each loop)**: Introduced in Java 5, this loop is used to iterate over collections and arrays, simplifying the syntax for traversing elements.

5. **What are control statements in Java?**

   Control statements in Java are programming constructs that control the flow of program execution. They determine which parts of code are executed and in what order, based on certain conditions or requirements. The main types of control statements in Java are:

   1. **Selection/Conditional/Decision Making Statements**:

      - if statements
      - if-else statements
      - switch statements
      - nested if statements

   2. **Iterative/Loop Statements**:

      - for loops
      - while loops
      - do-while loops
      - enhanced for loops

   3. **Jump Statements**:
      - break statement
      - continue statement
      - return statement

   These statements allow programmers to create complex program logic and control program flow based on different conditions and requirements.

6. **What are Loop Control Statements? What are the types of Loop Control Statements?**

   Loop control statements are used to alter the flow of control in loops. They allow you to manage the execution of loop iterations based on certain conditions. The types of loop control statements in Java include:

   1. **break statement**: Exits the loop immediately, skipping any remaining iterations.
   2. **continue statement**: Skips the current iteration and proceeds to the next iteration of the loop.
   3. **return statement**: Exits from the current method and returns control to the calling method, which can also affect loop execution if used within a loop.

7. **What is Decision Making? What are the types of Decision Making?**

   Decision making in programming refers to the process of making choices based on certain conditions. It allows the program to execute different paths of code based on the evaluation of these conditions. In Java, decision-making is primarily achieved through control statements.

   | Type of Decision Making | Description                                                                            |
   | ----------------------- | -------------------------------------------------------------------------------------- |
   | **if statement**        | Executes a block of code if a specified condition is true.                             |
   | **if-else statement**   | Executes one block of code if the condition is true, and another block if it is false. |
   | **else if statement**   | Allows checking multiple conditions sequentially.                                      |
   | **switch statement**    | Selects one of many code blocks to execute based on the value of a variable.           |

8. **What is the difference between a while loop and a do-while loop?**

   | Aspect                 | while loop                                                             | do-while loop                                                |
   | ---------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------ |
   | **Condition Check**    | Checks condition before executing the loop body                        | Checks condition after executing the loop body               |
   | **Minimum Executions** | Zero or more times (may never execute if condition is initially false) | At least once (executes first, then checks condition)        |
   | **Syntax**             | `while(condition) { statements }`                                      | `do { statements } while(condition);`                        |
   | **Use Case**           | When you need to check a condition before executing any statements     | When you want to ensure the loop body executes at least once |
   | **Exit Control**       | Entry controlled loop - may exit before first execution                | Exit controlled loop - can only exit after first execution   |

9. **What is the difference between a for loop and an enhanced for loop?**

   | Aspect            | for loop                                                  | enhanced for loop/for-each loop                            |
   | ----------------- | --------------------------------------------------------- | ---------------------------------------------------------- |
   | **Syntax**        | `for(init; condition; increment) { statements }`          | `for(type element : array/collection) { statements }`      |
   | **Use Case**      | When you need control over loop iteration and index       | When you want to iterate through all elements sequentially |
   | **Index Access**  | Has direct access to loop counter/index                   | No direct access to index                                  |
   | **Flexibility**   | More flexible - can iterate in any order or skip elements | Less flexible - must iterate through all elements in order |
   | **Applicable On** | Arrays, collections, and general counting/iteration       | Only arrays and collections (Iterable objects)             |
   | **Modification**  | Can modify array/collection elements during iteration     | Modification during iteration not recommended              |

   Example of for loop:

   ```java
   for(int i = 0; i < array.length; i++) {
       System.out.println(array[i]);
   }
   ```

   Example of enhanced for loop:

   ```java
   for(int element : array) {
       System.out.println(element);
   }
   ```

## System & Runtime

1. **What is the purpose of the Runtime class and System class?**

   The Runtime class and System class serve different but important purposes in Java:

   **Runtime Class**:

   - Provides interface to interact with the Java Runtime Environment (JRE)
   - Only one instance per JVM (Singleton pattern)
   - Accessed using Runtime.getRuntime()
   - Used for:
     - Memory management (garbage collection e.g. totalMemory(), freeMemory(), gc())
     - Executing external processes (exec())
     - Getting system information
     - Shutdown hooks (addShutdownHook())
     - Shutting down JVM (exit())

   **System Class**:

   - Provides utility methods and standard I/O streams
   - All methods are static - no instantiation needed
   - Used for:
     - Standard input/output/error streams (System.in, System.out, System.err)
     - Environment variables and properties (getenv(), getProperty())
     - Array copying (arraycopy())
     - Current time in milliseconds (currentTimeMillis())
     - System garbage collection (gc())
     - System exit (exit())

   Key differences:

   - Runtime focuses on JRE interaction and process management
   - System provides utility methods for common system operations
   - Runtime uses singleton pattern, System has only static members
   - Runtime methods are instance methods, System methods are static

2. **What is the difference between System.out, System.err, and System.in?**

   In Java, System.out, System.err, and System.in are standard streams that serve different purposes:

   1. System.out:

      - This is the standard output stream
      - Used for normal program output
      - Typically prints to the console in black text
      - Common methods: println(), print(), printf()
      - Example: System.out.println("Hello World");

   2. System.err:

      - This is the standard error stream
      - Used for error messages and debugging information
      - Typically prints to the console in red text
      - Has the same methods as System.out
      - Example: System.err.println("Error occurred!");

   3. System.in:
      - This is the standard input stream
      - Used to read input from the keyboard/console
      - Returns data as bytes that need to be parsed
      - Often wrapped with Scanner or BufferedReader for easier use
      - Example: Scanner scanner = new Scanner(System.in);

   Key differences:

   - Purpose: out for normal output, err for errors, in for input
   - Direction: out and err are output streams, in is an input stream
   - Visual: err typically shows in red, while out shows in black
   - Buffer: out is buffered, err is not (immediate output)

3. **What is a native method?**

   A native method is a method that is implemented in another programming language (typically C/C++) rather than in Java. Key points about native methods:

   - Declared with the `native` keyword in Java
   - Has no method body in Java code
   - Implementation is provided in platform-specific code
   - Used for:
     - Accessing system-specific functionality
     - Performance-critical code
     - Interfacing with legacy systems
     - Hardware interaction

   Example:

   ```java
   public class NativeExample {
       // Declares native method - no implementation in Java
       public native void performNativeOperation();

       static {
           // Loads the native library containing the implementation
           System.loadLibrary("nativeLib");
       }
   }
   ```

   Native methods require the Java Native Interface (JNI) to bridge between Java and native code. While powerful, they should be used sparingly as they:

   - Reduce platform independence
   - Can introduce security risks
   - Make debugging more difficult
   - Require additional build complexity

4. **What is the role and benefit of package in Java?**

   In Java, a package is a namespace that organizes a set of related classes and interfaces. The primary role of packages is to group related classes together, which helps in avoiding name conflicts and controlling access.

   The benefits of using packages in Java include:

   1. **Namespace Management**: Packages help to avoid naming conflicts by grouping classes with similar functionality under a unique package name.

   2. **Access Protection**: Packages provide controlled access to classes and members. Classes within the same package can access each other's package-private and protected members, while classes in different packages cannot.

   3. **Code Organization**: Packages help in organizing classes and interfaces in a logical manner, making it easier to locate and manage code.

   4. **Reusability**: By grouping related classes, packages promote code reusability, allowing developers to use existing classes in new applications without modification.

   5. **Modularity**: Packages encourage modular programming, where functionality is divided into separate, manageable components.

   Overall, packages play a crucial role in structuring Java applications, enhancing maintainability, and promoting best practices in software development.

## Advanced Features

1. **What are shallow copy and deep copy in Java?**

   In Java, object copying can be done in two ways: shallow copy and deep copy.

   **Shallow Copy:**

   - Creates a new object and copies all field values from the original object
   - For primitive fields, the actual values are copied
   - For reference fields, only the references are copied (both objects point to same memory location)
   - Faster and uses less memory
   - Changes to referenced objects in copy affect original

   Example of shallow copy:

   ```java
   class Person {
       String name;
       Address address; // Reference type

       public Person shallowCopy() {
           Person copy = new Person();
           copy.name = this.name;
           copy.address = this.address; // Only copies reference
           return copy;
       }
   }
   ```

   **Deep Copy:**

   - Creates a new object and recursively copies all fields
   - Creates new instances of all referenced objects
   - Both primitive and reference fields are fully copied
   - More expensive in terms of memory and processing
   - Changes to referenced objects in copy don't affect original

   Example of deep copy:

   ```java
   class Person {
       String name;
       Address address;

       public Person deepCopy() {
           Person copy = new Person();
           copy.name = this.name;
           copy.address = new Address(this.address); // Creates new Address object
           return copy;
       }
   }
   ```

2. **Can you have virtual functions in Java?**

   In Java, all non-static methods are virtual by default. This means:

   - Methods can be overridden in subclasses without any special keyword
   - The actual method called is determined at runtime based on the object's type
   - This enables polymorphic behavior

   Example:

   ```java
   class Animal {
       public void makeSound() {
           System.out.println("Some sound");
       }
   }

   class Dog extends Animal {
       @Override
       public void makeSound() {
           System.out.println("Woof!");
       }
   }
   ```

   When calling the method:

   ```java
   Animal animal = new Dog();
   animal.makeSound(); // Prints "Woof!" - virtual method dispatch
   ```

   Only final, static, and private methods cannot be overridden, making them non-virtual.

3. **What are the observer and observable classes?**

   Observer and Observable are legacy classes from Java's built-in implementation of the Observer pattern:

   - Observable (now deprecated):

     - Base class for objects that want to notify observers
     - Maintains list of observers
     - Methods include addObserver(), deleteObserver(), notifyObservers()
     - Must call setChanged() before notification

   - Observer (now deprecated):
     - Interface implemented by objects that want to be notified
     - Has update() method called when Observable changes

   Example:

   ```java
   class NewsAgency extends Observable {
       private String news;

       public void setNews(String news) {
           this.news = news;
           setChanged();
           notifyObservers(news);
       }
   }

   class NewsChannel implements Observer {
       @Override
       public void update(Observable o, Object news) {
           System.out.println("Breaking News: " + news);
       }
   }
   ```

   Note: These classes are deprecated since Java 9. Modern alternatives include:

   - java.util.concurrent Flow API
   - Event listeners
   - PropertyChangeListener
   - Third-party reactive libraries (RxJava, Project Reactor)

4. **Why are generics used in Java Programming?**

   Generics enable type-safe programming by allowing you to write code that works with different types while providing compile-time type safety. Key benefits include:

   - Type safety: Catches type errors at compile-time rather than runtime
   - Elimination of type casting: No need for explicit casting when retrieving elements
   - Enable generic algorithms: Write code that works with different types

   Example:

   ```java
   // Without generics
   List list = new ArrayList();
   list.add("hello");
   String s = (String) list.get(0); // requires casting

   // With generics
   List<String> list = new ArrayList<>();
   list.add("hello");
   String s = list.get(0); // no casting needed
   ```

   Common use cases:

   - Collection classes (List<T>, Map<K,V>)
   - Custom data structures
   - Methods that operate on different types
   - Type-safe APIs

5. **What are generics? How did you use them in your coding?**

   Generics in Java allow you to write classes, interfaces, and methods that can work with different types while providing compile-time type safety. Here are some common examples:

   1. **Collections Framework**

      ```java
      List<Employee> employees = new ArrayList<>();
      Map<String, User> userMap = new HashMap<>();
      ```

   2. **Custom Generic Classes**

      ```java
      public class Result<T> {
          private T data;
          private String message;

          public T getData() { return data; }
          public void setData(T data) { this.data = data; }
      }
      ```

   3. **Generic Methods**

      ```java
      public <T> void printArray(T[] array) {
          for(T element : array) {
              System.out.println(element);
          }
      }
      ```

   4. **Bounded Type Parameters**

      ```java
      public class NumberProcessor<T extends Number> {
          public double sum(List<T> numbers) {
              return numbers.stream()
                         .mapToDouble(Number::doubleValue)
                         .sum();
          }
      }
      ```

   5. **Wild Card Usage**
      ```java
      public void processElements(List<? extends Animal> animals) {
          for(Animal a : animals) {
              a.makeSound();
          }
      }
      ```

   Generics provide several benefits:

   - Type safety at compile-time
   - Elimination of type casting
   - Enable reusable code that works with different types
   - Support for generic algorithms and data structures

6. **Which of the below generates a compile-time error? State the reason.**

   ```java
   int[] n1 = new int[0];
   boolean[] n2 = new boolean[-200];
   double[] n3 = new double[2241423798];
   char[] ch = new char[20];
   ```

   - `n2` will generate a compile-time error because array sizes must be non-negative. The value -200 is negative.
   - `n3` will generate a compile-time error because the size exceeds Integer.MAX_VALUE (2147483647).
   - `n1` and `ch` are valid array declarations.

## Code Analysis & Debugging

1. **Is this program giving a compile-time error? If Yes then state the reason and number of errors it will give. If not then state the reason.**

   ```java
   abstract final class InterviewBit{
       public abstract void printMessage();
   }
   class ScalarAcademy extends InterviewBit{
       public void printMessage(){
           System.out.println("Welcome to Scalar Academy By InterviewBit");
       }
   }
   class ScalarTopics extends ScalarAcademy{
       public void printMessage(){
           System.out.println("Welcome to Scalar Topics By Scalar Academy");
       }
   }

   public class Main{
       public static void main(String[] args) {
           InterviewBit ib = new ScalarTopics();
           ib.printMessage();
       }
   }
   ```

   Yes, this program will give compile-time errors. There are 2 major issues:

   1. The `InterviewBit` class is declared as both `abstract` and `final`. This is illegal in Java because:

      - An abstract class is meant to be inherited from
      - A final class cannot be inherited from
        These modifiers contradict each other, causing a compile error.

   2. Since `InterviewBit` is declared as `final`, the class `ScalarAcademy` cannot extend it.
      This causes another compile error.

   Therefore, the program will generate 2 compile-time errors.

2. **Identify the output of the below java program and Justify your answer.**

   ```java
   class Main {
   public static void main(String args[]) {
       Scaler s = new Scaler(5);
       }
   }
   class InterviewBit{
       InterviewBit(){
           System.out.println(" Welcome to InterviewBit ");
       }
   }
   class Scaler extends InterviewBit{
       Scaler(){
           System.out.println(" Welcome to Scaler Academy ");
       }
       Scaler(int x){
           this();
           super();
           System.out.println(" Welcome to Scaler Academy 2");
       }
   }
   ```

   This program will result in a compile-time error. Here's why:

   1. When `new Scaler(5)` is called, it invokes the parameterized constructor `Scaler(int x)`
   2. Inside `Scaler(int x)`, `this()` is called first which invokes the default constructor `Scaler()`
   3. The default constructor `Scaler()` implicitly calls `super()` first to initialize the parent class
   4. After returning from `this()`, the constructor attempts to call `super()` explicitly
   5. This is illegal because:
      - Constructor calls to `this()` or `super()` must be the first statement in a constructor
      - A constructor cannot call both `this()` and `super()`

   Therefore, the code will not compile due to the invalid constructor chaining in `Scaler(int x)`.

3. **What is the output of the following Java program?**

   ```java
   class Person
    {
        public Person()
        {
            System.out.println("Person class constructor called");
        }
    }
    public class Employee extends Person
    {
        public Employee()
        {
            System.out.println("Employee class constructor called");
        }
        public static void main (String args[])
        {
            Employee e = new Employee();
        }
    }
   ```

   The output will be:

   ```
   Person class constructor called
   Employee class constructor called
   ```

   This happens because:

   1. When `new Employee()` is called, Java first calls the parent class's constructor implicitly via `super()`
   2. The `Person` constructor executes and prints its message
   3. Then the `Employee` constructor executes and prints its message
   4. The constructors execute in this order because a child class must initialize its parent class before initializing itself

4. **What is the output of the following Java program?**

   ```java
   class OverloadingCalculation3{
       void sum(int a,long b){System.out.println("a method invoked");}
       void sum(long a,int b){System.out.println("b method invoked");}

       public static void main(String args[]){
           OverloadingCalculation3 obj=new OverloadingCalculation3();
           obj.sum(20,20);//now ambiguity
       }
   }
   ```

   The program will not produce any output. Instead, it will fail to compile with an error message similar to:

   ```
   reference to sum is ambiguous
   both method sum(int,long) and method sum(long,int) match
   ```

   This happens because when calling `obj.sum(20,20)`, the compiler cannot determine which overloaded method to call:

   - The first argument 20 could be used as either int or promoted to long
   - The second argument 20 could be used as either int or promoted to long
   - This creates an ambiguous situation where both method signatures are equally valid matches

5. **What is the output of the following Java program?**

   ```java
   public class ExceptionHandlingExample {
       public static void main(String args[])
       {
           try
           {
               int a = 1/0;
               System.out.println("a = "+a);
           }
           catch(Exception e){System.out.println(e);}
           catch(ArithmeticException ex){System.out.println(ex);}
       }
   }
   ```

   This program will not compile. It will generate a compilation error because the catch block for `ArithmeticException` is unreachable. This happens because:

   1. `ArithmeticException` is a subclass of `Exception`
   2. The first catch block catches all `Exception`s (including `ArithmeticException`)
   3. The second catch block can never be reached

   To fix this, either:

   - Remove the second catch block, or
   - Put the more specific exception (`ArithmeticException`) first:

   ```java
   try {
       int a = 1/0;
       System.out.println("a = "+a);
   }
   catch(ArithmeticException ex){System.out.println(ex);}
   catch(Exception e){System.out.println(e);}
   ```

   With the fixed version, the output would be:

   ```
   java.lang.ArithmeticException: / by zero
   ```

6. **How many variables are eligible for garbage collection?**

   ```java
   public static void main(String[] fruits) {
       String fruit1 = new String("apple");
       String fruit2 = new String("orange");
       String fruit3 = new String("pear");
       fruit3 = fruit1;
       fruit2 = fruit3;
       fruit1 = fruit2;
   }
   ```

   There are 2 variables eligible for garbage collection: `fruit1` and `fruit2`. The other variables (`fruit3`) are not eligible for garbage collection because it still points to the same object as `fruit1`.

7. **What is the output of the following Java program?**

   ```java
   public class InitOrder {
	public String first = "instance";
	public InitOrder() {
		first = "constructor"; 
	}
	{ first = "block"; }
	public void print() {
		System.out.println(first);
	}
	public static void main(String... args) {
		new InitOrder().print();
	}
   }
   ```

   The output will be:
   ```
   constructor
   ```

   This is because the initialization order in Java is:
   1. Static variables/blocks (not present here)
   2. Instance variables ("instance")
   3. Instance initialization blocks ("block") 
   4. Constructor ("constructor")

   So while `first` gets assigned different values, the final value that gets printed is "constructor" since the constructor runs last.
