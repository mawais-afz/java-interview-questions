## Java Strings

1. **What is the difference between String, StringBuffer and StringBuilder in Java?**

   | Feature       | String                                           | StringBuffer                                           | StringBuilder                                          |
   | ------------- | ------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------ |
   | Mutability    | Immutable - creates new object for modifications | Mutable - can be modified without creating new objects | Mutable - can be modified without creating new objects |
   | Thread Safety | Thread-safe (immutable)                          | Thread-safe (synchronized methods)                     | Not thread-safe but better performance                 |
   | Performance   | Slower for string modifications                  | Slower than StringBuilder due to synchronization       | Fastest for string modifications                       |
   | Memory Usage  | Creates multiple objects in string pool          | Single object, more memory efficient                   | Single object, more memory efficient                   |
   | Storage       | String Pool                                      | Heap Memory                                            | Heap Memory                                            |
   | Since Version | JDK 1.0                                          | JDK 1.0                                                | JDK 1.5                                                |
   | Use Case      | When string will not change frequently           | In multi-threaded environments                         | In single-threaded environments                        |

2. **What makes Java Strings immutable?**

   Java Strings are immutable by design due to several implementation details:

   1. **Final Class**: The String class is declared as final, preventing inheritance and modification of its behavior.

   2. **Private Final Char Array**: The internal character array storing the string content is both private and final:

      ```java
      private final char[] value;
      ```

   3. **No Modifier Methods**: String class provides no methods to modify the existing character array after creation.

   4. **String Pool**: Java maintains a String Pool for string literals, allowing string reuse and memory optimization.

   Benefits of String immutability:

   - Thread safety
   - Security (can't be modified by malicious code)
   - String pool optimization
   - Safe for hash keys
   - Caching hashcode

   When you "modify" a String, you actually create a new String object:

   ```java
   String str = "Hello";
   str = str + " World"; // Creates new String object
   ```

3. **What is the difference between equals() and ==?**

   | Feature          | `equals()`                                                                           | `==`                                                               |
   | ---------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
   | Purpose          | Compares the content/values of two objects.                                          | Compares the reference (memory address) of two objects.            |
   | Usage            | Used for object comparison, especially for Strings and other objects.                | Used for primitive data types and reference comparison.            |
   | Null Safety      | Can handle null values without throwing an exception (returns false if one is null). | Throws a NullPointerException if one of the references is null.    |
   | Overriding       | Can be overridden in a class to provide custom equality logic.                       | Cannot be overridden; checks reference equality only.              |
   | Default Behavior | Default implementation in Object class checks reference equality unless overridden.  | Always checks reference equality.                                  |
   | Example          | `str1.equals(str2)` compares the actual string values.                               | `str1 == str2` checks if both references point to the same object. |

4. **What are string pools in Java?**

   String pools in Java refer to a special storage area in the Java heap memory where Java stores string literals. When a string literal is created, Java checks the string pool to see if an identical string already exists. If it does, the reference to the existing string is returned, rather than creating a new string object. This mechanism helps in saving memory and improving performance by reusing immutable string objects.

   Key points about string pools:

   - **String Interning**: The process of storing only one copy of each distinct string value in the pool is known as string interning.
   - **Memory Efficiency**: By reusing string literals, Java reduces memory consumption, especially when the same strings are used multiple times in an application.
   - **Creation**: Strings can be created in two ways: using string literals (which are stored in the string pool) or using the `new` keyword (which creates a new object in the heap memory, bypassing the pool).

   Example of string pool usage:

   ```java
   String str1 = "Hello"; // Stored in string pool
   String str2 = "Hello"; // Reuses the same reference from the pool
   String str3 = new String("Hello"); // Creates a new object in heap memory
   ```

   In this example, `str1` and `str2` point to the same object in the string pool, while `str3` points to a different object in the heap.
