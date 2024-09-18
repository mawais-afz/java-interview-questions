# Basic Java

1. **What is Java?**

   Java is a popular, versatile, and object-oriented programming language known for its "write once, run anywhere" capability. It was developed by Sun Microsystems (now owned by Oracle) in 1995. Java is used for developing a wide range of applications, including desktop, web, mobile, and enterprise software.

   Key features of Java include:

   - Platform independence
   - Object-oriented programming
   - Strong typing
   - Automatic memory management (garbage collection)
   - Rich standard library
   - Extensive ecosystem of frameworks and tools
   - Multithreaded

2. **Explain JDK, JRE, and JVM**

   | Component | Full Name                | Description                                                                                                                                                                                                                                          |
   | --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | JDK       | Java Development Kit     | A software development environment used for developing Java applications. It includes the JRE, an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc), and other tools needed in Java development. |
   | JRE       | Java Runtime Environment | Provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.                                                                                               |
   | JVM       | Java Virtual Machine     | An abstract computing machine that enables a computer to run a Java program. It provides a runtime environment in which Java bytecode can be executed, ensuring platform independence.                                                               |

3. **What is a Java Variable?**

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

4. **What are variable types?**

   | Variable Type          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Local Variables        | - Declared in methods, constructors, or blocks<br>- Created when the method, constructor or block is entered and destroyed once it exits<br>- No access modifiers can be used<br>- Visible only within the declared method, constructor, or block<br>- No default value, must be declared and initialized before use                                                                                                                                                                                                                          |
   | Instance Variables     | - Declared in a class, but outside a method, constructor or any block<br>- Created when an object is created with the 'new' keyword and destroyed when the object is destroyed<br>- Can use access modifiers<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed directly by calling the variable name inside the class                                                                                           |
   | Class/Static Variables | - Declared with the static keyword in a class, but outside a method, constructor or block<br>- Only one copy per class, regardless of how many objects are created<br>- Created when the program starts and destroyed when the program stops<br>- Can be declared as public/private, final, and static<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed by calling with the class name: ClassName.VariableName |

5. **What are data types?**

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

6. **What are Data Type?**

   Data types define the type and value range of the data for the different types of variables, constants, method parameters, returns type.

   | Data Type | Default Value | Default Size | Range                |
   | --------- | ------------- | ------------ | -------------------- |
   | byte      | 0             | 1 byte       | -128 to 127          |
   | short     | 0             | 2 bytes      | -32,768 to 32,767    |
   | int       | 0             | 4 bytes      | -2^31 to 2^31-1      |
   | long      | 0L            | 8 bytes      | -2^63 to 2^63-1      |
   | float     | 0.0f          | 4 bytes      | 3.4e−038 to 3.4e+038 |
   | double    | 0.0d          | 8 bytes      | 1.7e−308 to 1.7e+308 |
   | boolean   | false         | 1 bit        | true or false        |
   | char      | '\u0000'      | 2 bytes      | 0 to 65,535          |

   There are two categories of data types in Java:

   1. Primitive Data Types: These include byte, short, int, long, float, double, boolean and char.

   2. Reference/Object Data Types: These include Class objects, Arrays, and Interfaces.

7. **What is Type Casting (Type Conversion)**

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

8. **What are Operators? What are the types of Operators?**

   Java operators are symbols that perform operations on variables and values. They allow us to execute various operations such as addition, subtraction, and comparisons. The different types of operators in Java are as follows:

   | Operator Type           | Description                                                                               |
   | ----------------------- | ----------------------------------------------------------------------------------------- |
   | Arithmetic Operators    | Used for mathematical calculations (+, -, \*, /, %, ++, --).                              |
   | Relational Operators    | Used to compare two values (==, !=, >, <, >=, <=, ===, !==).                              |
   | Bitwise Operators       | Operate on bits and perform bit-by-bit operations (&, \|, ^, ~, <<, >>, >>>).              |
   | Logical Operators       | Used to combine multiple boolean expressions (&&, \|\| ,!).                               |
   | Assignment Operators    | Used to assign values to variables (=, +=, -=, \*=, /=, %=, &=, \|=, ^=, <<=, >>=, >>>=). |
   | Miscellaneous Operators | Includes conditional (ternary) operator (`? :`), instanceof operator (`instanceof`).      |

# Control Statements
