# Java Basics, JVM Internals & Language Components

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

27. **What is the super keyword in Java? When can you use the super keyword?**

    The `super` keyword in Java is a reference variable used to refer to the immediate parent class object. It allows you to access parent class members that are hidden or overridden by the child class.

    You can use the super keyword in the following ways:

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
