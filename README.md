# Java Interview Questions

## Java Basics, JVM Internals & Language Components

1. **What is Java?**

   Java is a popular, versatile, and object-oriented programming language known for its "write once, run anywhere" capability. It was developed by Sun Microsystems (now owned by Oracle) in 1995. Java is used for developing a wide range of applications, including desktop, web, mobile, and enterprise software.

2. **Explain the main idea behind Java and the concept of Write Once, Run Anywhere**

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

5. **Explain JDK, JRE, and JVM**

   | Component | Full Name                | Description                                                                                                                                                                                                                                          |
   | --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | JDK       | Java Development Kit     | A software development environment used for developing Java applications. It includes the JRE, an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc), and other tools needed in Java development. |
   | JRE       | Java Runtime Environment | Provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.                                                                                               |
   | JVM       | Java Virtual Machine     | An abstract computing machine that enables a computer to run a Java program. It provides a runtime environment in which Java bytecode can be executed, ensuring platform independence.                                                               |

6. **What is a ClassLoader? And its role in Java?**

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

7. **What is the difference between path and classpath?**

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

8. **What are the Memory Allocations available in Java**

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

   3. **Method Area (Metaspace)**:

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

9. **What are the differences between Heap and Stack Memory in Java?**

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

10. **How does garbage collection work in Java?**

    Garbage Collection (GC) in Java is an automatic memory management process that identifies and removes unused objects from heap memory. Here's how it works:

    1. **Mark Phase**:

       - GC identifies all objects that are still in use (reachable)
       - Starting from "root" references (stack, static variables, etc.)
       - Traverses object graph to mark live objects

    2. **Sweep Phase**:
       - Removes unmarked objects (garbage)
       - Compacts remaining space (in some GC algorithms)
       - Frees memory for future allocations

    Key aspects of Java's Garbage Collection:

    - **Generational Collection**:
      - Young Generation (for new objects)
        - Eden Space (initial allocation)
        - Survivor Spaces (for objects surviving collection)
      - Old Generation (for long-lived objects)
    - **Collection Types**:

      - Minor GC: Collects Young Generation
      - Major GC: Collects Old Generation
      - Full GC: Collects entire heap

    - **GC Algorithms**:
      - Serial GC: Single-threaded, simple
      - Parallel GC: Multi-threaded collection
      - CMS (Concurrent Mark Sweep): Minimizes pauses
      - G1 (Garbage First): Region-based collection
      - ZGC: Low-latency collector (Java 11+)

    Note: While automatic, GC can impact application performance during collection cycles.

11. **What is a Java Variable?**

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

12. **What is the difference between final, finally and finalize keywords in Java?**

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

13. **Can we overload or override static methods?**

    1. **Static Method Overloading**:

       - Yes, we can overload static methods
       - Must have different parameter lists
       - Example:

         ```java
         public class Calculator {
             public static int add(int a, int b) {
                 return a + b;
             }

             public static double add(double a, double b) {
                 return a + b;
             }
         }
         ```

    2. **Static Method Overriding**:

       - No, we cannot override static methods
       - If you declare same static method in child class, it's called method hiding
       - Example:

         ```java
         class Parent {
             public static void display() {
                 System.out.println("Parent's static method");
             }
         }

         class Child extends Parent {
             public static void display() { // This is method hiding, not overriding
                 System.out.println("Child's static method");
             }
         }
         ```

14. **What is the significance of the this keyword in Java?**

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

15. **What are variable types?**

    | Variable Type          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Local Variables        | - Declared in methods, constructors, or blocks<br>- Created when the method, constructor or block is entered and destroyed once it exits<br>- No access modifiers can be used<br>- Visible only within the declared method, constructor, or block<br>- No default value, must be declared and initialized before use                                                                                                                                                                                                                          |
    | Instance Variables     | - Declared in a class, but outside a method, constructor or any block<br>- Created when an object is created with the 'new' keyword and destroyed when the object is destroyed<br>- Can use access modifiers<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed directly by calling the variable name inside the class                                                                                           |
    | Class/Static Variables | - Declared with the static keyword in a class, but outside a method, constructor or block<br>- Only one copy per class, regardless of how many objects are created<br>- Created when the program starts and destroyed when the program stops<br>- Can be declared as public/private, final, and static<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed by calling with the class name: ClassName.VariableName |

16. **What is the difference between transient and volatile variable in Java?**

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

17. **What are data types?**

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

18. **What is Type Casting (Type Conversion)**

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

19. **What are autoboxing and unboxing?**

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

20. **What are Operators? What are the types of Operators?**

    Java operators are symbols that perform operations on variables and values. They allow us to execute various operations such as addition, subtraction, and comparisons. The different types of operators in Java are as follows:

    | Operator Type           | Description                                                                               |
    | ----------------------- | ----------------------------------------------------------------------------------------- |
    | Arithmetic Operators    | Used for mathematical calculations (+, -, \*, /, %, ++, --).                              |
    | Relational Operators    | Used to compare two values (==, !=, >, <, >=, <=, ===, !==).                              |
    | Bitwise Operators       | Operate on bits and perform bit-by-bit operations (&, \|, ^, ~, <<, >>, >>>).             |
    | Logical Operators       | Used to combine multiple boolean expressions (&&, \|\| ,!).                               |
    | Assignment Operators    | Used to assign values to variables (=, +=, -=, \*=, /=, %=, &=, \|=, ^=, <<=, >>=, >>>=). |
    | Miscellaneous Operators | Includes conditional (ternary) operator (`? :`), instanceof operator (`instanceof`).      |

21. **What are loops? What are the types of loops?**

    Loops are control structures that allow you to execute a block of code multiple times, depending on a specified condition. In Java, there are several types of loops that you can use to handle repetitive tasks:

    1. **while loop**: Repeats a statement or a group of statements while a given condition is true. The condition is evaluated before the execution of the loop body.

    2. **for loop**: Executes a sequence of statements multiple times and is typically used when the number of iterations is known beforehand. It includes initialization, condition, and increment/decrement in a single line.

    3. **do...while loop**: Similar to the while loop, but it tests the condition at the end of the loop body, ensuring that the loop body is executed at least once.

    4. **Enhanced for loop (for-each loop)**: Introduced in Java 5, this loop is used to iterate over collections and arrays, simplifying the syntax for traversing elements.

22. **What are Loop Control Statements? What are the types of Loop Control Statements?**

    Loop control statements are used to alter the flow of control in loops. They allow you to manage the execution of loop iterations based on certain conditions. The types of loop control statements in Java include:

    1. **break statement**: Exits the loop immediately, skipping any remaining iterations.
    2. **continue statement**: Skips the current iteration and proceeds to the next iteration of the loop.
    3. **return statement**: Exits from the current method and returns control to the calling method, which can also affect loop execution if used within a loop.

23. **What is Decision Making? What are the types of Decision Making?**

    Decision making in programming refers to the process of making choices based on certain conditions. It allows the program to execute different paths of code based on the evaluation of these conditions. In Java, decision-making is primarily achieved through control statements.

    | Type of Decision Making | Description                                                                            |
    | ----------------------- | -------------------------------------------------------------------------------------- |
    | **if statement**        | Executes a block of code if a specified condition is true.                             |
    | **if-else statement**   | Executes one block of code if the condition is true, and another block if it is false. |
    | **else if statement**   | Allows checking multiple conditions sequentially.                                      |
    | **switch statement**    | Selects one of many code blocks to execute based on the value of a variable.           |

24. **What are wrapper classes in Java?**

    Wrapper classes in Java are used to convert primitive data types into objects. Each primitive type has a corresponding wrapper class that provides a way to use these primitives as objects. This is particularly useful in situations where objects are required, such as in collections like ArrayList. The wrapper classes in Java include:

    - **Integer**: for int
    - **Double**: for double
    - **Character**: for char
    - **Boolean**: for boolean
    - **Byte**: for byte
    - **Short**: for short
    - **Long**: for long
    - **Float**: for float

    Wrapper classes also provide utility methods for converting between types, performing operations, and handling null values. For example, the Integer class has methods for parsing strings into integers and vice versa. By using wrapper classes, you can take advantage of the features of object-oriented programming while still working with primitive data types.

25. **Distinguish between static loading and dynamic class loading?**

    Static loading and dynamic class loading are two different approaches to loading classes in Java:

    **Static Loading (Load-Time Loading)**:

    - Classes are loaded at compile time
    - Uses `new` operator for object creation
    - Loading happens automatically when the program starts
    - All required classes must be available during compilation
    - More predictable but less flexible

    ```java
    class TestClass {
      public static void main(String args[]) {
        TestClass tc = new TestClass();
      	}
      }
    ```

    **Dynamic Loading (Runtime Loading)**:

    - Classes are loaded at runtime on demand
    - Uses `Class.forName()` or `ClassLoader` methods
    - Loading happens explicitly when requested in code
    - Classes can be loaded based on runtime conditions
    - More flexible but requires exception handling

    Example of Dynamic Loading:

    ```java
    try {
        Class.forName("com.example.MyClass");
    } catch (ClassNotFoundException e) {
        // Handle the exception
    }
    ```

26. **What is the purpose of the Runtime class and System class?**

	The Runtime class and System class serve different but important purposes in Java:

	**Runtime Class**:
	- Provides interface to interact with the Java Runtime Environment (JRE)
	- Only one instance per JVM (singleton)
	- Used for:
		- Memory management (garbage collection)
		- Executing external processes
		- Getting system information
		- Shutting down JVM

	**System Class**:
	- Provides utility methods and standard I/O streams
	- All methods are static - no instantiation needed
	- Used for:
		- Standard input/output/error streams (System.in, System.out, System.err)
		- Environment variables and properties
		- Array copying
		- Current time in milliseconds
		- System exit

1.  **When can you use super keyword?**

    The `super` keyword in Java can be used in the following scenarios:

    1. **Call Parent Class Methods**:

       - When a method is overridden, use `super` to call the parent version
       - Example: `super.methodName()`

    2. **Access Parent Class Fields**:

       - Access fields from parent class that might be hidden by child class
       - Example: `super.fieldName`

    3. **Call Parent Class Constructor**:
       - Must be first statement in constructor
       - Example: `super()` or `super(parameters)`

    Example:

    ```java
    class Parent {
        String name = "Parent";
        void display() {
            System.out.println("Parent method");
        }
    }

    class Child extends Parent {
        String name = "Child";

        Child() {
            super(); // Call parent constructor
        }

        void display() {
            super.display(); // Call parent method
            System.out.println(super.name); // Access parent field
        }
    }
    ```

## Object-Oriented Programming (OOP) Concepts

14. **Why is Java not considered to be purely object-oriented?**

    Java is not considered to be purely object-oriented because it supports primitive data types (such as int, char, boolean, byte, short, long, float, and double) that are not objects. In a purely object-oriented language, everything is treated as an object, and all data types would be defined as classes. While Java provides wrapper classes for these primitive types (e.g., Integer for int, Character for char, Boolean for boolean, Byte for byte, Short for short, Long for long, Float for float, and Double for double), the existence of primitives means that Java does not fully adhere to the principles of pure object-oriented programming. Additionally, Java allows for static methods and variables, which are not associated with any object instance, further distinguishing it from purely object-oriented languages.

15. **What is OOP?**

    Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data in the form of fields (often known as attributes or properties) and code in the form of procedures (often known as methods).

16. **What are the pillars of OOP?**

    The four pillars of Object-Oriented Programming (OOP) are:

    1. **Class**: A blueprint for creating objects, defining the properties and behaviors of an object.
    2. **Object**: An instance of a class, created from the class blueprint.
    3. **Encapsulation**: The bundling of data with the methods that operate on that data, restricting direct access to some of the object's components.
    4. **Inheritance**: The mechanism by which one class can inherit the properties and methods of another class, promoting code reuse and the creation of a hierarchical relationship between classes.
    5. **Polymorphism**: The ability of different classes to be treated as instances of the same class through a common interface, allowing for the implementation of methods in different ways.
    6. **Abstraction**: The concept of hiding the complex implementation details and showing only the necessary features of an object, simplifying the interaction with the object.

17. **What are classes and objects? Why use them in applications?**

    Classes are blueprints for creating objects in object-oriented programming. They define the properties (attributes) and behaviors (methods) that the objects created from the class will have. An object is an instance of a class, representing a specific entity with its own state and behavior.

    Using classes and objects in applications provides several benefits:

    1. **Modularity**: Classes allow developers to break down complex systems into smaller, manageable pieces, making the code easier to understand and maintain.

    2. **Reusability**: Once a class is defined, it can be reused to create multiple objects, reducing code duplication and promoting consistency.

    3. **Encapsulation**: Classes encapsulate data and methods, restricting access to the internal state of the object and exposing only what is necessary through public methods.

    4. **Inheritance**: Classes can inherit properties and methods from other classes, facilitating code reuse and the creation of hierarchical relationships.

    5. **Polymorphism**: Objects of different classes can be treated as objects of a common superclass, allowing for flexible and interchangeable code.

    Overall, classes and objects are fundamental to organizing and structuring code in a way that reflects real-world entities and their interactions.

18. **How to implement classes and objects in Java? What are the members of a class?**

    To implement classes and objects in Java, you need to follow these steps:

    1. **Define a Class**: A class is defined using the `class` keyword followed by the class name. Inside the class, you can declare members, which include attributes (fields), methods (functions), and constructors that define the behavior of the objects created from the class.

    ```java
    public class Car {
        // Attributes (Members)
        private String color;
        private String model;

        // Constructor (Member)
        public Car(String color, String model) {
            this.color = color;
            this.model = model;
        }

        // Method (Member)
        public void displayInfo() {
            System.out.println("Car Model: " + model + ", Color: " + color);
        }
    }
    ```

    2. **Create Objects**: Once the class is defined, you can create objects (instances) of that class using the `new` keyword.

    ```java
    public class Main {
        public static void main(String[] args) {
            // Creating objects of the Car class
            Car myCar = new Car("Red", "Toyota");
            Car yourCar = new Car("Blue", "Honda");

            // Calling methods on the objects
            myCar.displayInfo(); // Output: Car Model: Toyota, Color: Red
            yourCar.displayInfo(); // Output: Car Model: Honda, Color: Blue
        }
    }
    ```

    In this example, the `Car` class is defined with members including attributes, a constructor, and a method. Two objects of the `Car` class are created in the `Main` class, demonstrating how to implement classes and objects in Java.

19. **What is immutable object?**

    An immutable object is an object whose state cannot be changed after it is created. Once an immutable object is constructed, its contents remain constant throughout its lifetime. String is a classic example of an immutable class in Java.

    Key characteristics of immutable objects:

    1. **Final Class**: The class should be declared as final to prevent inheritance
    2. **Private Fields**: All fields should be private and final
    3. **No Setters**: No methods that modify the object's state
    4. **Deep Copy**: If mutable objects are used as fields, return copies instead of references
    5. **Initialize in Constructor**: All fields must be initialized in the constructor

    Example of an immutable class:

    ```java
    public final class ImmutablePerson {
        private final String name;
        private final int age;

        public ImmutablePerson(String name, int age) {
            this.name = name;
            this.age = age;
        }

        public String getName() {
            return name;
        }

        public int getAge() {
            return age;
        }
    }
    ```

    Benefits of immutable objects:
    - Thread-safe without synchronization
    - Safe to share and cache
    - Simple to construct, test, and use
    - Prevent temporal coupling
    - Side-effect free behavior
  
20. **How can we create an immutable class in Java?**

    To create an immutable class in Java, follow these steps:

    1. **Declare the class as final** to prevent inheritance
    2. **Make all fields private and final** to prevent direct access and modification
    3. **Don't provide setter methods** for fields
    4. **Initialize all fields via constructor**
    5. **Make deep copies of mutable objects** in constructor and getter methods
    6. **Don't expose methods that can change object state**

    Example of creating an immutable class:

    ```java
    public final class ImmutableStudent {
        private final String name;
        private final int id;
        private final List<String> courses;

        public ImmutableStudent(String name, int id, List<String> courses) {
            this.name = name;
            this.id = id;
            // Deep copy of mutable object
            this.courses = new ArrayList<>(courses);
        }

        public String getName() {
            return name;
        }

        public int getId() {
            return id;
        }

        public List<String> getCourses() {
            // Return copy to prevent modification
            return new ArrayList<>(courses);
        }
    }
    ```

    This class is immutable because:
    - It's declared final
    - All fields are private and final
    - No setter methods are provided
    - Mutable List is deep copied in constructor and getter
    - No methods can modify the object's state

20. **What is the role and benefit of package in Java?**

    In Java, a package is a namespace that organizes a set of related classes and interfaces. The primary role of packages is to group related classes together, which helps in avoiding name conflicts and controlling access.

    The benefits of using packages in Java include:

    1. **Namespace Management**: Packages help to avoid naming conflicts by grouping classes with similar functionality under a unique package name.

    2. **Access Protection**: Packages provide controlled access to classes and members. Classes within the same package can access each other's package-private and protected members, while classes in different packages cannot.

    3. **Code Organization**: Packages help in organizing classes and interfaces in a logical manner, making it easier to locate and manage code.

    4. **Reusability**: By grouping related classes, packages promote code reusability, allowing developers to use existing classes in new applications without modification.

    5. **Modularity**: Packages encourage modular programming, where functionality is divided into separate, manageable components.

    Overall, packages play a crucial role in structuring Java applications, enhancing maintainability, and promoting best practices in software development.

21. **What are access specifiers? What are the types of access specifiers?**

    Access specifiers in Java are keywords that set the accessibility (visibility) of classes, methods, and other members. They control how the members of a class can be accessed from other classes. The main types of access specifiers in Java are:

    1. **Public**: Members declared as public are accessible from any other class in any package. This means there are no restrictions on the visibility of public members.

    2. **Private**: Members declared as private are accessible only within the class they are declared in. This means that private members cannot be accessed from outside the class, providing a way to encapsulate and protect the data.

    3. **Protected**: Members declared as protected are accessible within the same package and by subclasses, even if they are in different packages.

    4. **Default (Package-Private)**: If no access specifier is declared, the member is accessible only within its own package. This is also known as package-private access.

    By using access specifiers, developers can implement encapsulation, which is a fundamental principle of object-oriented programming, ensuring that the internal representation of an object is hidden from the outside.

22. **What are constructors in Java?**

    Constructors in Java are special methods that are called when an object is instantiated. They have the same name as the class and do not have a return type, not even void. Constructors are used to initialize the object's attributes and allocate memory for the object. There are two types of constructors in Java:

    1. **Default Constructor**: A constructor that does not take any parameters. If no constructor is explicitly defined in a class, the Java compiler automatically provides a default constructor.

    2. **Parameterized Constructor**: A constructor that takes parameters to initialize an object with specific values at the time of creation. This allows for more flexibility in object creation.

    Here's an example of a parameterized constructor in Java:

    ```java
    public class ConstructorExample {
        private String name;
        private int age;

        // Parameterized constructor
        public ConstructorExample(String name, int age) {
            this.name = name;
            this.age = age;
        }

        // Default constructor
        public ConstructorExample() {
            this.name = "Unknown";
            this.age = 0;
        }
    }

    In this example, the `ConstructorExample` class has both a parameterized constructor and a default constructor, allowing for different ways to create objects of this class.

    ```

23. **What is the difference between constructor and method?**

    | Aspect           | Constructor                                                      | Method                                                      |
    | ---------------- | ---------------------------------------------------------------- | ----------------------------------------------------------- |
    | Purpose          | Used to initialize object state when creating a new instance     | Used to perform operations and implement behavior           |
    | Name             | Must have the same name as the class                             | Can have any valid name                                     |
    | Return Type      | No return type, not even void                                    | Must have a return type (void or specific type)             |
    | Invocation       | Called automatically when object is created using new keyword    | Must be explicitly called on an object                      |
    | Inheritance      | Not inherited by subclasses (though can be called using super()) | Inherited by subclasses unless declared as private or final |
    | Default Creation | Java provides a default constructor if none is defined           | No default methods are created by Java                      |

    Here's an example illustrating the differences:

    ```java
    public class Example {
        private String data;

        // Constructor - initializes object
        public Example(String data) {
            this.data = data;
        }

        // Method - performs operation
        public void processData() {
            System.out.println("Processing: " + data);
        }
    }
    ```

24. **Explain the constructor overloading**

    Constructor overloading is a technique in Java where a class can have multiple constructors with different parameter lists. Each constructor provides a different way to initialize an object of that class. The constructors must differ in their parameter lists (number of parameters, types of parameters, or both).

    Here's an example of constructor overloading:

    ```java
    public class Student {
        private String name;
        private int age;
        private String grade;

        // Constructor with no parameters
        public Student() {
            this.name = "Unknown";
            this.age = 0;
            this.grade = "N/A";
        }

        // Constructor with name parameter
        public Student(String name) {
            this.name = name;
            this.age = 0;
            this.grade = "N/A";
        }

        // Constructor with name and age parameters
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
            this.grade = "N/A";
        }

        // Constructor with all parameters
        public Student(String name, int age, String grade) {
            this.name = name;
            this.age = age;
            this.grade = grade;
        }
    }
    ```

    In this example, the `Student` class has four different constructors, each accepting different parameters. This allows for flexible object creation based on the available information:

    ```java
    Student s1 = new Student();                         // Uses no-arg constructor
    Student s2 = new Student("John");                   // Uses constructor with name
    Student s3 = new Student("Jane", 20);               // Uses constructor with name and age
    Student s4 = new Student("Mike", 21, "A");          // Uses constructor with all parameters
    ```

25. **What is Copy Constructor in Java?**

    A Copy Constructor in Java is a constructor that creates a new object by copying the values from another object of the same class. It takes an object of the same class as a parameter and creates a new object with the same values. Copy constructors are useful when you want to create a new object with the same state as an existing object.

    Here's an example of a Copy Constructor:

    ```java
    public class Student {
        private String name;
        private int age;

        // Normal constructor
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        // Copy constructor
        public Student(Student other) {
            this.name = other.name;
            this.age = other.age;
        }
    }

    // Usage example:
    Student student1 = new Student("John", 20);
    Student student2 = new Student(student1); // Creates a copy of student1
    ```

    Note that Java does not provide automatic copy constructors like C++. You need to implement them explicitly if needed. Also, when dealing with reference types, be careful to perform a deep copy if required, to avoid sharing references between the original and copied objects.

26. **What is a singleton class in Java? Describe the singleton pattern with an example.**

    A Singleton class in Java is a design pattern that restricts the instantiation of a class to a single instance. This is useful when exactly one object is needed to coordinate actions across the system, such as managing configuration settings, database connections, or thread pools.

    To implement a thread-safe Singleton class in Java, you typically follow these steps:

    1. **Private Constructor**: Make the constructor private to prevent direct instantiation
    2. **Private Static Instance**: Create a private static final instance of the class
    3. **Public Static Method**: Provide a public static method to access the single instance

    Here's an example of a thread-safe Singleton class using the initialization-on-demand holder pattern:

    ```java
    public class Singleton {
        // Private constructor prevents instantiation from other classes
        private Singleton() { }

        // Private static holder class - loaded only when getInstance() is called
        private static class SingletonHolder {
            private static final Singleton INSTANCE = new Singleton();
        }

        // Public static method to get the singleton instance
        public static Singleton getInstance() {
            return SingletonHolder.INSTANCE;
        }

        // Example method of the singleton
        public void doSomething() {
            System.out.println("Singleton is doing something");
        }
    }
    ```

    Usage example:

    ```java
    Singleton singleton = Singleton.getInstance(); // Gets the single instance
    singleton.doSomething(); // Use the singleton

    // Will return the same instance
    Singleton anotherReference = Singleton.getInstance();
    System.out.println(singleton == anotherReference); // Prints: true
    ```

    In this example, the `Singleton` class has a private constructor, a static instance variable, and a public static method `getInstance()` that provides access to the single instance of the class. This ensures that no more than one instance of the `Singleton` class can exist at any time.

27. **What is encapsulation? Explain encapsulation with an example.**

    Encapsulation is one of the four fundamental OOP concepts that involves bundling data and the methods that operate on that data within a single unit (class), while restricting direct access to some of the object's components. This is achieved in Java through:

    1. Declaring class variables/attributes as private
    2. Providing public getter and setter methods to access and modify the values

    Here's a practical example:

    ```java
    public class BankAccount {
        private double balance;  // private variable
        private String accountNumber;

        public BankAccount(String accountNumber) {
            this.accountNumber = accountNumber;
            this.balance = 0.0;
        }

        // Getter method
        public double getBalance() {
            return balance;
        }

        // Instead of directly modifying balance, we use methods
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
    ```

    In this example, the `balance` variable is private and can't be accessed directly. Instead, we provide controlled methods like `deposit()` and `withdraw()` to modify it. This ensures that:

    3. The balance can't be modified without validation
    4. The implementation details are hidden from the user
    5. We can change the internal implementation without affecting code that uses the class

28. **What is inheritance and what are its types in Java?**

    Inheritance is a fundamental object-oriented programming concept where a class (subclass/child class) can inherit attributes and methods from another class (superclass/parent class). In Java, inheritance is implemented using the `extends` keyword. This mechanism promotes code reuse, simplifies maintenance, and allows for the creation of more specialized classes based on existing ones. There are several types of inheritance supported in Java:

    1. **Single Inheritance**: A class inherits from only one superclass. This is the most common type of inheritance in Java.
       Example: Class B extends Class A

    2. **Multilevel Inheritance**: A class inherits from a class which in turn inherits from another class.
       Example: Class C extends Class B extends Class A

    3. **Hierarchical Inheritance**: Multiple classes inherit from a single superclass.
       Example: Class B and Class C both extend Class A

    4. **Multiple Inheritance**: Java does not support multiple inheritance through classes (a class cannot extend multiple classes). However, it can be achieved through interfaces.
       Example: Class A implements Interface1, Interface2

    Note: Java deliberately does not support multiple inheritance through classes to avoid the "diamond problem" where ambiguity can arise if multiple parent classes have methods with the same name.

    Here's an example of inheritance in Java:

    ```java
    public class Animal {
        protected String name;

        public Animal(String name) {
            this.name = name;
        }

        public void eat() {
            System.out.println(name + " is eating.");
        }

        public void sleep() {
            System.out.println(name + " is sleeping.");
        }
    }

    public class Dog extends Animal {
        public Dog(String name) {
            super(name);
        }

        public void bark() {
            System.out.println(name + " is barking.");
        }
    }
    ```

    In this example, the `Dog` class inherits the properties and behaviors of the `Animal` class, including the `name` field and the `eat()` and `sleep()` methods. The `Dog` class also adds its own unique behavior, the `bark()` method.

29. **What is the difference between extends and implements?**

    | Aspect                   | extends                                                 | implements                                             |
    | ------------------------ | ------------------------------------------------------- | ------------------------------------------------------ |
    | Purpose                  | Used for class inheritance                              | Used to implement interfaces                           |
    | Multiple Inheritance     | A class can extend only one class                       | A class can implement multiple interfaces              |
    | Type                     | Creates an "is-a" relationship between classes          | Creates a "can-do" relationship                        |
    | Method Implementation    | Inherits both method declarations and implementations   | Must implement all interface methods (unless abstract) |
    | Access to Parent Members | Can access protected and public members of parent class | Can only access public interface constants             |
    | Constructor Inheritance  | Inherits constructors from parent class                 | Interfaces cannot have constructors                    |
    | Code Reuse               | Allows reuse of code from parent class                  | Only provides method contracts, no implementation      |
    | Usage Example            | `class Dog extends Animal`                              | `class Bird implements Flyable`                        |

30. **What is polymorphism in Java? Explain with examples of runtime and compile-time polymorphism.**

    Polymorphism in Java comes in two forms:

    1. **Runtime (Dynamic) Polymorphism**:

       - Achieved through method overriding
       - The method to be executed is determined at runtime
       - Example:

       ```java
       class Animal {
           void makeSound() {
               System.out.println("Some sound");
           }
       }

       class Dog extends Animal {
           @Override
           void makeSound() {
               System.out.println("Woof!");
           }
       }

       // Runtime polymorphism in action
       Animal animal = new Dog();
       animal.makeSound(); // Outputs: Woof!
       ```

    2. **Compile-time (Static) Polymorphism**:

       - Achieved through method overloading
       - The method to be executed is determined at compile time
       - Example:

       ```java
       class Calculator {
           // Method overloading
           int add(int a, int b) {
               return a + b;
           }

           double add(double a, double b) {
               return a + b;
           }

           int add(int a, int b, int c) {
               return a + b + c;
           }
       }

       Calculator calc = new Calculator();
       calc.add(5, 3);       // Calls first method
       calc.add(4.5, 3.2);   // Calls second method
       calc.add(2, 3, 4);    // Calls third method
       ```

31. **What is the difference between loose coupling and tight coupling?**

    Loose coupling refers to a design principle in which components or classes are minimally dependent on each other, allowing for greater flexibility and easier maintenance. In a loosely coupled system, changes in one component have little to no impact on others, making it easier to modify or replace parts of the system without affecting the overall functionality.

    On the other hand, tight coupling occurs when components are highly dependent on one another, leading to a more rigid structure. In a tightly coupled system, changes in one component often require changes in others, making the system harder to maintain and adapt over time.

    In summary, loose coupling promotes better modularity and reusability, while tight coupling can lead to increased complexity and reduced flexibility in software design.

    ````java
    	// Example of Loose Coupling
    	interface Animal {
    			void makeSound();
    	}

    	class Dog implements Animal {
    			public void makeSound() {
    					System.out.println("Bark");
    			}
    	}

    	class Cat implements Animal {
    			public void makeSound() {
    					System.out.println("Meow");
    			}
    	}

    	class AnimalSound {
    			public void playSound(Animal animal) {
    					animal.makeSound();
    			}
    	}

    	public class Main {
    			public static void main(String[] args) {
    					Animal dog = new Dog();
    					Animal cat = new Cat();
    					AnimalSound animalSound = new AnimalSound();
    					animalSound.playSound(dog); // Outputs: Bark
    					animalSound.playSound(cat); // Outputs: Meow
    			}
    	}

    	// Example of Tight Coupling
    	class Dog {
    			public void makeSound() {
    					System.out.println("Bark");
    			}
    	}

    	class DogSound {
    			private Dog dog;

    			public DogSound() {
    					dog = new Dog();
    			}

    			public void playSound() {
    					dog.makeSound();
    			}
    	}

    	public class Main {
    			public static void main(String[] args) {
    					DogSound dogSound = new DogSound();
    					dogSound.playSound(); // Outputs: Bark
    			}
    	}
    	```
    ````

32. **What is the difference between cohesion and coupling?**

    | Aspect     | Cohesion                                                                 | Coupling                                                                              |
    | ---------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
    | Definition | Measures how closely related the functionalities within a module are.    | Measures the degree of dependence between different modules.                          |
    | Goal       | Aim for high cohesion to ensure that a module is focused and manageable. | Aim for low coupling to enhance module independence and flexibility.                  |
    | Example    | A class that handles all operations related to user authentication.      | A class that directly accesses methods of another class, creating a tight dependency. |

    ```java
    // Example of High Cohesion
    class UserAuthentication {
    	public boolean login(String username, String password) {
    		// Logic for user login
    		return true; // Assume login is successful
    	}

    	public void logout() {
    		// Logic for user logout
    	}

    	public boolean register(String username, String password) {
    		// Logic for user registration
    		return true; // Assume registration is successful
    	}
    }

    // Example of Low Coupling
    class User {
    	private String username;
    	private String password;

    	public User(String username, String password) {
    		this.username = username;
    		this.password = password;
    	}

    	public String getUsername() {
    		return username;
    	}

    	public String getPassword() {
    		return password;
    	}
    }

    class UserService {
    	public void authenticate(User user) {
    		// Logic to authenticate user
    		System.out.println("Authenticating user: " + user.getUsername());
    	}
    }
    ```

33. **What is a Marker Interface?**

    A Marker Interface in Java is an interface that does not contain any methods. It is used to mark a class that implements it, indicating that the class has a specific property or behavior. Marker interfaces are often used to indicate that a class has a particular characteristic or capability, such as being serializable, cloneable, or thread-safe.
    Here are some examples of commonly used marker interfaces in Java:

    ```java
    // Example of a custom marker interface
    public interface Deletable {
        // No methods - just marks classes that can be deleted
    }

    // Class implementing the marker interface
    public class Document implements Deletable {
        private String content;

        public Document(String content) {
            this.content = content;
        }

        public void delete() {
            // Delete implementation
            System.out.println("Document deleted");
        }
    }

    // Usage example
    public class FileManager {
        public void deleteIfPossible(Object obj) {
            if (obj instanceof Deletable) {
                System.out.println("Object can be deleted");
                ((Document) obj).delete();
            } else {
                System.out.println("Object cannot be deleted");
            }
        }
    }
    ```

    Some built-in marker interfaces in Java include:

    - `Serializable`: Marks classes that can be serialized
    - `Cloneable`: Marks classes that can be cloned
    - `Remote`: Marks classes that can be used for RMI (Remote Method Invocation)

34. **What is an abstract class? Explain its purpose and when to use it.**

    An abstract class in Java is a class that cannot be instantiated on its own and may contain both abstract and concrete methods. It serves as a blueprint for other classes and is designed to be extended by subclasses.

    Here's an example to illustrate abstract classes:

    ```java
    // Abstract class example
    public abstract class Animal {
        protected String name;

        // Constructor
        public Animal(String name) {
            this.name = name;
        }

        // Concrete method
        public void sleep() {
            System.out.println(name + " is sleeping");
        }

        // Abstract method - must be implemented by subclasses
        public abstract void makeSound();
    }

    // Concrete class extending abstract class
    public class Dog extends Animal {
        public Dog(String name) {
            super(name);
        }

        // Implementation of abstract method
        @Override
        public void makeSound() {
            System.out.println(name + " says: Woof!");
        }
    }
    ```

    Use abstract classes when:

    - You want to share code among several related classes
    - You expect classes that extend your abstract class to have common methods/fields
    - You want to declare non-public members (unlike interfaces)
    - You need to provide a template for a group of related classes
    - Some common behavior can be implemented in the abstract class, while other behavior must be implemented by each subclass

35. **What is the difference between abstract class and interface in Java?**

    | Aspect                | Abstract Class                                                                       | Interface                                                                                                               |
    | --------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
    | Definition            | A class that cannot be instantiated and can have both abstract and concrete methods. | A reference type that can contain only constants, method signatures, default methods, static methods, and nested types. |
    | Inheritance           | Supports single inheritance (a class can extend only one abstract class).            | Supports multiple inheritance (a class can implement multiple interfaces).                                              |
    | Method Implementation | Can have both abstract methods (without body) and concrete methods (with body).      | All methods are abstract by default (unless they are default or static methods).                                        |
    | Constructor           | Can have constructors.                                                               | Cannot have constructors.                                                                                               |
    | Access Modifiers      | Can have access modifiers (public, protected, private).                              | All methods are public by default; cannot have access modifiers.                                                        |
    | Use Case              | Used when classes share a common base and behavior.                                  | Used to define a contract that implementing classes must follow.                                                        |

36. **What is the difference between composition, aggregation, and association?**

    | Aspect     | Composition                                                                     | Aggregation                                                                  | Association                                                                                 |
    | ---------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
    | Definition | A strong relationship where the child cannot exist independently of the parent. | A weaker relationship where the child can exist independently of the parent. | A general relationship between two classes, where one class uses or interacts with another. |
    | Lifespan   | The child's lifespan is tied to the parent's lifespan.                          | The child can outlive the parent.                                            | The lifespan of the associated objects is independent.                                      |
    | Ownership  | The parent owns the child, and the child is part of the parent.                 | The parent does not own the child; they can exist separately.                | There is no ownership; it is a loose relationship.                                          |
    | Example    | A car and its engine (the engine cannot exist without the car).                 | A university and its students (students can exist without the university).   | A teacher and a student (the teacher interacts with the student, but they are independent). |

    Here's a code example demonstrating all three relationships:

    ```java
    // Composition Example
    class Engine {
        private String type;

        public Engine(String type) {
            this.type = type;
        }
    }

    class Car {
        private final Engine engine; // Strong relationship - engine cannot exist without car

        public Car() {
            engine = new Engine("V8"); // Engine is created when Car is created
        }

        // When Car is destroyed, Engine is also destroyed
    }

    // Aggregation Example
    class Student {
        private String name;

        public Student(String name) {
            this.name = name;
        }
    }

    class University {
        private List<Student> students; // Weak relationship - students can exist without university

        public University() {
            students = new ArrayList<>();
        }

        public void addStudent(Student student) {
            students.add(student);
        }

        public void removeStudent(Student student) {
            students.remove(student);
        }
    }

    // Association Example
    class Teacher {
        public void teach(Student student) { // No ownership, just interaction
            System.out.println("Teaching student");
        }
    }

    class Student {
        public void learn(Teacher teacher) { // No ownership, just interaction
            System.out.println("Learning from teacher");
        }
    }
    ```

37. **What is the difference between method overloading and overriding in Java?**

- **Method Overloading**: This occurs when multiple methods in the same class have the same name but different parameters (different type, number, or both). It allows methods to perform similar functions with different inputs. Overloading is resolved at compile time.

- **Method Overriding**: This occurs when a subclass provides a specific implementation of a method that is already defined in its superclass. The method in the subclass must have the same name, return type, and parameters as the method in the superclass. Overriding is resolved at runtime, allowing for dynamic method dispatch.

  Example of Method Overloading:

  ```java
  public class MathUtils {
  		public int add(int a, int b) {
  				return a + b;
  		}

  		public double add(double a, double b) {
  				return a + b;
  		}
  }
  ```

  Example of Method Overriding:

  ```java
  public class Animal {
  		public void sound() {
  				System.out.println("Animal makes a sound");
  		}
  }

  public class Dog extends Animal {
  		@Override
  		public void sound() {
  				System.out.println("Dog barks");
  		}
  }
  ```

29. **What is the difference between Java Dynamic Binding and Static Binding?**

- **Static Binding**: This occurs at compile time and is used for method calls that are resolved based on the reference type. It is typically used with private, static, and final methods. Since the method to be called is determined at compile time, it cannot be changed at runtime.

- **Dynamic Binding**: This occurs at runtime and is used for method calls that are resolved based on the actual object type. It is typically used with overridden methods in inheritance. Dynamic binding allows for polymorphism, where the method that gets executed is determined by the actual object being referred to, rather than the reference type.

Example of Static Binding:

```java
public class StaticBindingExample {
    public static void display() {
        System.out.println("Static Binding");
    }
}
```

Example of Dynamic Binding:

```java
public class Shape {
    public void draw() {
        System.out.println("Drawing a shape");
    }
}

public class Circle extends Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
}
```

30. **What is an Instance Initializer Block? Characteristics of Instance Initializer Block?**

    An Instance Initializer Block is a block of code that is used to initialize instance variables of a class. It is executed when an instance of the class is created, before the constructor is called.

    **Characteristics of Instance Initializer Block:**

    - It is executed every time an instance of the class is created.
    - It can access instance variables and methods of the class.
    - It is useful for common initialization code that is shared among multiple constructors.
    - It can be used to initialize instance variables that require more complex logic than simple assignment.
    - It is executed in the order it appears in the class, before the constructor's body.

    Example of Instance Initializer Block:

    ```java
    public class Example {
        private int value;

        // Instance Initializer Block
        {
            value = 10; // Initialization logic
        }

        public Example() {
            System.out.println("Constructor called. Value: " + value);
        }
    }
    ```

31. **What is the purpose of static members in Java?**

    Static members in Java (including methods, variables, and nested classes) belong to the class itself rather than any specific instance. They serve several important purposes:

    1. **Memory Efficiency**

       - Only one copy exists in memory regardless of how many instances are created
       - Shared across all instances of the class
       - Ideal for constants and utility functions

    2. **Accessibility Without Instance**

       - Can be accessed without creating an object of the class
       - Useful for utility methods that don't need instance data
       - Common in helper classes and factory methods

    3. **Global State Management**

       - Provides a way to maintain class-level state
       - Useful for counters, configuration values, or caches shared across instances
       - Enables communication between different instances of a class

    4. **Utility Organization**
       - Static nested classes provide logical grouping of utility code
       - Static methods organize helper functions that operate independently
       - Commonly used in design patterns like Singleton and Factory Method
         |

    Example demonstrating all three:

    ```java
    public class OuterClass {
        // Static variable
        static int count = 0;

        // Static method
        static void incrementCount() {
            count++;
        }

        // Static nested class
        static class StaticNestedClass {
            void display() {
                System.out.println("Count: " + count);
            }
        }
    }
    ```

32. **Explain the use of final keyword in variable, method and class**

    The `final` keyword in Java is used to impose restrictions on variables, methods, and classes:

    | Type                | Description                                                                                                                                                                       |
    | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | **Final Variables** | - Makes the variable a constant that can only be assigned once<br>- Value cannot be changed after initialization<br>- Must be initialized either at declaration or in constructor |
    | **Final Methods**   | - Prevents the method from being overridden in subclasses<br>- Ensures that the method implementation remains the same throughout inheritance hierarchy                           |
    | **Final Classes**   | - Prevents the class from being inherited<br>- No other class can extend a final class<br>- Useful when you want to prevent inheritance for security/design reasons               |

    Here's an example demonstrating all three uses:

    ```java
    final class FinalClass { // Cannot be inherited
        final int CONSTANT = 100; // Cannot be changed after initialization

        final void finalMethod() { // Cannot be overridden
            System.out.println("This method cannot be overridden");
        }
    }

    // This would cause compilation error:
    // class ChildClass extends FinalClass { } // Cannot extend final class
    ```

## Java Collections Framework

34. **Describe the collection framework in Java.**

    The Java Collections Framework is a unified architecture for representing and manipulating collections of objects. It provides a set of interfaces, implementations, and algorithms to store and process groups of objects.

    Key components of the Collections Framework:

    1. **Interfaces**:

       - Collection: Root interface of the collection hierarchy
       - List: Ordered collection (sequence)
       - Set: Collection that cannot contain duplicate elements
       - Queue: Collection designed for holding elements prior to processing
       - Map: Object that maps keys to values

    2. **Implementation Classes**:

       - ArrayList: Resizable-array implementation of List
       - LinkedList: Doubly-linked list implementation
       - HashSet: Hash table implementation of Set
       - TreeSet: Sorted tree implementation of Set
       - HashMap: Hash table implementation of Map
       - TreeMap: Red-black tree implementation of Map

    3. **Utility Classes**:
       - Collections: Static methods for collection operations
       - Arrays: Static methods for array operations

    Key features:

    - Reduces programming effort
    - Increases program speed and quality
    - Allows interoperability among unrelated APIs
    - Reduces effort to learn and use new APIs
    - Promotes software reuse
    - Supports data structure and algorithm reuse

    Basic hierarchy diagram:

    ```
    Collection
    ├── List
    │   ├── ArrayList
    │   ├── LinkedList
    │   └── Vector
    ├── Set
    │   ├── HashSet
    │   └── TreeSet
    └── Queue
        ├── PriorityQueue
        └── Deque
    ```

35. **What is the difference between List, Set, and Map in Java?**

    Here's a comparison of List, Set, and Map interfaces in Java:

    | Feature        | List                                | Set                             | Map                                         |
    | -------------- | ----------------------------------- | ------------------------------- | ------------------------------------------- |
    | Duplicates     | Allows duplicate elements           | Does not allow duplicates       | No duplicate keys, values can be duplicated |
    | Order          | Maintains insertion order           | May or may not maintain order   | May or may not maintain order               |
    | Null elements  | Allows multiple null elements       | Allows single null element      | One null key, multiple null values allowed  |
    | Access         | Index-based access (get(index))     | No index-based access           | Key-based access (get(key))                 |
    | Implementation | ArrayList, LinkedList, Vector       | HashSet, TreeSet, LinkedHashSet | HashMap, TreeMap, LinkedHashMap             |
    | Use case       | When element order/position matters | For unique element collections  | For key-value pair associations             |
    | Iteration      | Iterator, ListIterator              | Iterator                        | Iterator for entrySet, keySet, values       |
    | Performance    | O(1) for access, O(n) for search    | O(1) for add/remove/contains    | O(1) for add/remove/contains with good hash |

    Example usage:

    ```java
    // List example
    List<String> list = new ArrayList<>();
    list.add("apple");
    list.add("apple");  // duplicate allowed
    list.get(0);        // index access

    // Set example
    Set<String> set = new HashSet<>();
    set.add("apple");
    set.add("apple");   // duplicate ignored
    set.contains("apple"); // membership test

    // Map example
    Map<String, Integer> map = new HashMap<>();
    map.put("apple", 1);
    map.put("banana", 2);
    map.get("apple");   // key-based access
    ```

36. **What is the difference between fail-safe and fail-fast iterators?**

    Fail-fast and fail-safe iterators differ in how they handle concurrent modifications during iteration:

    | Feature         | Fail-Fast Iterator                                            | Fail-Safe Iterator                                    |
    | --------------- | ------------------------------------------------------------- | ----------------------------------------------------- |
    | Behavior        | Throws ConcurrentModificationException if collection modified | Continues iteration over clone of original collection |
    | Memory          | Uses original collection directly                             | Creates copy of collection                            |
    | Performance     | Better performance (no cloning)                               | Lower performance due to cloning                      |
    | Memory Overhead | Low memory usage                                              | Higher memory usage due to collection copy            |
    | Consistency     | Always up-to-date view                                        | May not reflect recent modifications                  |
    | Examples        | ArrayList, HashMap, Vector iterators                          | ConcurrentHashMap, CopyOnWriteArrayList iterators     |
    | Use Case        | Single-threaded applications                                  | Concurrent/multi-threaded applications                |

    Example of fail-fast iterator:

    ```java
    ArrayList<String> list = new ArrayList<>();
    list.add("one");
    list.add("two");

    Iterator<String> iterator = list.iterator();
    while(iterator.hasNext()) {
        String value = iterator.next();
        list.add("three"); // Throws ConcurrentModificationException
    }
    ```

    Example of fail-safe iterator:

    ```java
    ConcurrentHashMap<String, String> map = new ConcurrentHashMap<>();
    map.put("key1", "value1");

    Iterator<String> iterator = map.keySet().iterator();
    while(iterator.hasNext()) {
        String key = iterator.next();
        map.put("key2", "value2"); // No exception thrown
    }
    ```

37. **What is the difference between Vector and an ArrayList?**

    Vector and ArrayList are both List implementations, but they have several key differences:

    | Feature         | Vector                                         | ArrayList                                       |
    | --------------- | ---------------------------------------------- | ----------------------------------------------- |
    | Synchronization | Synchronized (thread-safe)                     | Not synchronized                                |
    | Performance     | Slower due to synchronization overhead         | Better performance in single-threaded scenarios |
    | Growth          | Doubles size when full (100% growth)           | Increases by 50% when full                      |
    | Legacy Status   | Legacy class (since JDK 1.0)                   | Modern implementation (since JDK 1.2)           |
    | Memory Usage    | Can waste more memory due to larger increments | More memory efficient                           |
    | Default Size    | 10 elements                                    | 10 elements                                     |

    Example usage:

    ```java
    // Vector (thread-safe)
    Vector<String> vector = new Vector<>();
    vector.add("element");  // synchronized operation

    // ArrayList (not thread-safe)
    ArrayList<String> list = new ArrayList<>();
    list.add("element");   // not synchronized

    // Making ArrayList thread-safe if needed
    List<String> syncList = Collections.synchronizedList(new ArrayList<>());
    ```

38. **What are the differences between Collection and Collections in Java?**

    Collection and Collections serve different purposes in Java:

    | Feature       | Collection                                    | Collections                                     |
    | ------------- | --------------------------------------------- | ----------------------------------------------- |
    | Type          | Interface                                     | Utility class                                   |
    | Purpose       | Base interface for collection hierarchy       | Provides static utility methods for collections |
    | Usage         | Implemented by collection classes (List, Set) | Contains methods like sort(), binarySearch()    |
    | Instantiation | Can be instantiated through implementations   | Cannot be instantiated (all methods static)     |
    | Methods       | add(), remove(), contains(), etc.             | sort(), shuffle(), synchronizedList(), etc.     |

    Example usage:

    ```java
    // Collection (interface) usage
    Collection<String> list = new ArrayList<>();
    list.add("item");
    list.remove("item");

    // Collections (utility class) usage
    List<String> list2 = new ArrayList<>();
    Collections.sort(list2);
    Collections.shuffle(list2);
    List<String> syncList = Collections.synchronizedList(list2);
    ```

39. **In which scenario, LinkedList is better than ArrayList in Java?**

    LinkedList and ArrayList have different performance characteristics that make each better suited for specific scenarios:

    | Operation     | LinkedList                                | ArrayList                      |
    | ------------- | ----------------------------------------- | ------------------------------ |
    | Insertion     | O(1) at known positions                   | O(n) if not at end             |
    | Deletion      | O(1) at known positions                   | O(n) if not at end             |
    | Random Access | O(n)                                      | O(1)                           |
    | Memory        | More memory (stores prev/next references) | Less memory (contiguous block) |

    LinkedList is better when:

    - Frequent insertions/deletions in the middle of the list
    - No random access needed
    - Memory size is not a constraint

    Example usage:

    ```java
    LinkedList<String> linkedList = new LinkedList<>();

    // Efficient operations for LinkedList
    linkedList.addFirst("first");     // O(1)
    linkedList.addLast("last");       // O(1)
    linkedList.add(1, "middle");      // O(1) if position is known
    linkedList.removeFirst();         // O(1)
    linkedList.removeLast();          // O(1)
    ```
