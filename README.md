# Basic Java

1. **What is Java?**

   Java is a popular, versatile, and object-oriented programming language known for its "write once, run anywhere" capability. It was developed by Sun Microsystems (now owned by Oracle) in 1995. Java is used for developing a wide range of applications, including desktop, web, mobile, and enterprise software.

2. **List some important features of Java.**

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

3. **Explain JDK, JRE, and JVM**

   | Component | Full Name                | Description                                                                                                                                                                                                                                          |
   | --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | JDK       | Java Development Kit     | A software development environment used for developing Java applications. It includes the JRE, an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc), and other tools needed in Java development. |
   | JRE       | Java Runtime Environment | Provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.                                                                                               |
   | JVM       | Java Virtual Machine     | An abstract computing machine that enables a computer to run a Java program. It provides a runtime environment in which Java bytecode can be executed, ensuring platform independence.                                                               |

4. **Name the types of memory allocations in Java.**

   In Java, memory is primarily allocated in two areas:

   - **Stack Memory**: Used for static memory allocation and the execution of a thread. It contains method-specific values that are short-lived and references to objects in the heap that are being referred to from the method.
   - **Heap Memory**: Used for dynamic memory allocation for Java objects and JRE classes at runtime. New objects are always created in the heap space, and the memory for these objects is managed by the Java Garbage Collector.

   Additionally, there are other memory areas such as:

   - **Method Area**: Stores class structures like metadata, the constant runtime pool, and the code for methods.
   - **Program Counter (PC) Register**: Contains the address of the Java virtual machine instruction currently being executed.
   - **Native Method Stack**: Contains all the native method information used in the application.

   These memory areas are part of the Java Memory Model which helps in the efficient execution of Java applications.

5. **What is a Java Variable?**

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

6. **What are variable types?**

   | Variable Type          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Local Variables        | - Declared in methods, constructors, or blocks<br>- Created when the method, constructor or block is entered and destroyed once it exits<br>- No access modifiers can be used<br>- Visible only within the declared method, constructor, or block<br>- No default value, must be declared and initialized before use                                                                                                                                                                                                                          |
   | Instance Variables     | - Declared in a class, but outside a method, constructor or any block<br>- Created when an object is created with the 'new' keyword and destroyed when the object is destroyed<br>- Can use access modifiers<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed directly by calling the variable name inside the class                                                                                           |
   | Class/Static Variables | - Declared with the static keyword in a class, but outside a method, constructor or block<br>- Only one copy per class, regardless of how many objects are created<br>- Created when the program starts and destroyed when the program stops<br>- Can be declared as public/private, final, and static<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed by calling with the class name: ClassName.VariableName |

7. **What are data types?**

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

8. **What is Type Casting (Type Conversion)**

   Type casting is the process of converting a value from one data type to another in Java. There are two types of type casting:

   1. Widening Casting (Implicit) - automatically converting a smaller type to a larger type size
      `byte -> short -> char -> int -> long -> float -> double`

   - **Example**:

   ```java
   byte byteValue = 10;
   int intValue = byteValue; // Widening casting from byte to int
   ```

   2. Narrowing Casting (Explicit) - manually converting a larger type to a smaller size type
      `double -> float -> long -> int -> char -> short -> byte`

   - **Example**:

   ```java
   double doubleValue = 9.78;
   int intValue = (int) doubleValue; // Narrowing casting from double to int
   ```

   Widening casting is done automatically when passing a smaller size type to a larger size type. Narrowing casting must be done manually by placing the type in parentheses in front of the value.

9. **What are Operators? What are the types of Operators?**

   Java operators are symbols that perform operations on variables and values. They allow us to execute various operations such as addition, subtraction, and comparisons. The different types of operators in Java are as follows:

   | Operator Type           | Description                                                                               |
   | ----------------------- | ----------------------------------------------------------------------------------------- |
   | Arithmetic Operators    | Used for mathematical calculations (+, -, \*, /, %, ++, --).                              |
   | Relational Operators    | Used to compare two values (==, !=, >, <, >=, <=, ===, !==).                              |
   | Bitwise Operators       | Operate on bits and perform bit-by-bit operations (&, \|, ^, ~, <<, >>, >>>).             |
   | Logical Operators       | Used to combine multiple boolean expressions (&&, \|\| ,!).                               |
   | Assignment Operators    | Used to assign values to variables (=, +=, -=, \*=, /=, %=, &=, \|=, ^=, <<=, >>=, >>>=). |
   | Miscellaneous Operators | Includes conditional (ternary) operator (`? :`), instanceof operator (`instanceof`).      |

# Control Statements

10. **What are loops? What are the types of loops?**

    Loops are control structures that allow you to execute a block of code multiple times, depending on a specified condition. In Java, there are several types of loops that you can use to handle repetitive tasks:

    1. **while loop**: Repeats a statement or a group of statements while a given condition is true. The condition is evaluated before the execution of the loop body.

    2. **for loop**: Executes a sequence of statements multiple times and is typically used when the number of iterations is known beforehand. It includes initialization, condition, and increment/decrement in a single line.

    3. **do...while loop**: Similar to the while loop, but it tests the condition at the end of the loop body, ensuring that the loop body is executed at least once.

    4. **Enhanced for loop (for-each loop)**: Introduced in Java 5, this loop is used to iterate over collections and arrays, simplifying the syntax for traversing elements.

11. **What are Loop Control Statements? What are the types of Loop Control Statements?**

    Loop control statements are used to alter the flow of control in loops. They allow you to manage the execution of loop iterations based on certain conditions. The types of loop control statements in Java include:

    1.  **break statement**: Exits the loop immediately, skipping any remaining iterations.
    2.  **continue statement**: Skips the current iteration and proceeds to the next iteration of the loop.
    3.  **return statement**: Exits from the current method and returns control to the calling method, which can also affect loop execution if used within a loop.

12. **What is Decision Making? What are the types of Decision Making?**

    Decision making in programming refers to the process of making choices based on certain conditions. It allows the program to execute different paths of code based on the evaluation of these conditions. In Java, decision-making is primarily achieved through control statements.

    | Type of Decision Making | Description                                                                            |
    | ----------------------- | -------------------------------------------------------------------------------------- |
    | **if statement**        | Executes a block of code if a specified condition is true.                             |
    | **if-else statement**   | Executes one block of code if the condition is true, and another block if it is false. |
    | **else if statement**   | Allows checking multiple conditions sequentially.                                      |
    | **switch statement**    | Selects one of many code blocks to execute based on the value of a variable.           |

# Object Oriented Programming

13. **What is Object Oriented Programming?**

    Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data in the form of fields (often known as attributes or properties) and code in the form of procedures (often known as methods).

