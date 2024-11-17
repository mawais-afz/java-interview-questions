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

2. **Which among String or String Buffer should be preferred when there are a lot of updates required to be done in the data?**

   When frequent updates are needed, StringBuilder is preferred over StringBuffer due to its better performance in single-threaded environments. However, if thread safety is a concern, StringBuffer should be used.

3. **What makes Java Strings immutable?**

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

4. **Why is String immutable in Java?**

   Strings in Java are immutable for several important reasons:

   1. **Security**

      - Prevents malicious code from modifying string values
      - Critical for sensitive data like database credentials, network connections
      - Ensures string parameters can't be modified unexpectedly
      - Safe to pass strings between different parts of a system
      - Maintains data integrity across network boundaries

   2. **String Pool Efficiency**

      - Enables string interning and reuse via string pool
      - Multiple references can safely share same string object
      - Reduces memory usage by avoiding duplicate strings
      - Enables safe string pooling and reuse
      - No need to create copies since strings can't be modified

   3. **Thread Safety**

      - Immutable strings are inherently thread-safe
      - Can be shared between threads without synchronization
      - No risk of concurrent modification issues
      - No synchronization needed for read operations

   4. **Hash Code Caching**

      - String's hash code only needs to be calculated once
      - Can be cached since string value never changes
      - Improves performance for hash-based collections
      - Only needs to be calculated once when used as keys in HashMaps/HashSets

   5. **Performance Benefits**

      - JVM can optimize string operations better
      - No need for defensive copies
      - Simpler garbage collection
      - Enables various internal optimizations

   6. **API Contract Safety**
      - Method parameters can't be modified unexpectedly
      - Return values remain consistent
      - Safer to use as class constants

   The combination of these benefits makes string immutability a fundamental design choice in Java that improves security, efficiency and reliability.

5. **Why is it said that the length() method of String class doesn't return accurate results?**

   The String.length() method returns the number of code units (char values) in the string, not necessarily the number of actual characters. This can lead to seemingly inaccurate results because:

   1. **Unicode Surrogate Pairs**

      - Some Unicode characters require two char values (surrogate pairs)
      - length() counts each surrogate pair as two characters
      - Example: "𝄞" (musical G-clef) has length() = 2

   2. **Combining Characters**

      - Characters with diacritical marks may use combining characters
      - Each combining character is counted separately
      - Example: "é" (e + acute accent) has length() = 2 if composed of two code units

   3. **Grapheme Clusters**
      - What appears visually as one character might be multiple Unicode code points
      - length() counts each code unit separately
      - Example: Family emoji "👨‍👩‍👧" consists of multiple code units

   For accurate character counting, alternatives include:

   - codePointCount() for Unicode code points
   - Using specialized libraries for grapheme cluster counting
   - java.text.BreakIterator for linguistic character boundaries

6. **What is the difference between equals() and ==?**

   | Feature          | `equals()`                                                                           | `==`                                                               |
   | ---------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
   | Purpose          | Compares the content/values of two objects.                                          | Compares the reference (memory address) of two objects.            |
   | Usage            | Used for object comparison, especially for Strings and other objects.                | Used for primitive data types and reference comparison.            |
   | Null Safety      | Can handle null values without throwing an exception (returns false if one is null). | Throws a NullPointerException if one of the references is null.    |
   | Overriding       | Can be overridden in a class to provide custom equality logic.                       | Cannot be overridden; checks reference equality only.              |
   | Default Behavior | Default implementation in Object class checks reference equality unless overridden.  | Always checks reference equality.                                  |
   | Example          | `str1.equals(str2)` compares the actual string values.                               | `str1 == str2` checks if both references point to the same object. |

7. **What are string pools in Java?**

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

8. **How is the creation of a String using new() different from that of a literal? or What is the difference between creating String as new() and literal?**

   When creating strings, there are two main approaches:

   1. **String Literal (`String s = "hello";`)**:

      - Creates string in the String Pool
      - Reuses existing string if identical one exists in pool
      - More memory efficient
      - Better performance due to string reuse
      - Preferred way for string creation

   2. **Using new (`String s = new String("hello");`)**:
      - Always creates new String object in heap memory
      - Bypasses String Pool (unless explicitly interned)
      - Creates two objects: one in heap and one in string pool
      - Less memory efficient
      - Useful when you explicitly need a new String instance

   Example demonstrating the difference:

   ```java
   String str1 = "hello";        // Creates one object in String Pool
   String str2 = "hello";        // Reuses same object from pool
   String str3 = new String("hello"); // Creates new object in heap

   System.out.println(str1 == str2);      // true (same reference)
   System.out.println(str1 == str3);      // false (different objects)
   System.out.println(str1.equals(str3)); // true (same content)
   ```

9. **Why is the character array preferred over string for storing confidential information?**

   Character arrays (`char[]`) are preferred over Strings for storing sensitive data like passwords for several security reasons:

   1. **Immutability of Strings**:

      - Strings are immutable in Java
      - String values remain in memory until garbage collection
      - Multiple copies may exist in memory due to String Pool
      - Sensitive data stays longer in memory, increasing security risk

   2. **Explicit Clearing**:

      - Character arrays can be explicitly cleared (zeroed out)
      - Once cleared, sensitive data is immediately removed from memory
      - Example:
        ```java
        char[] password = {'p','a','s','s'};
        // After use
        Arrays.fill(password, '0'); // Explicitly clear the data
        ```

   3. **Memory Control**:
      - Direct control over memory contents with arrays
      - Can ensure sensitive data is not kept in memory longer than needed
      - Reduces risk of memory dumps exposing confidential information

   This is why Java's `Console.readPassword()` returns a char array instead of a String, and many security-related APIs prefer character arrays for handling sensitive data.

10. **What is StringJoiner?**

    StringJoiner is a class introduced in Java 8 that helps construct a sequence of characters separated by a delimiter. It provides a convenient way to create strings with delimiters, prefixes, and suffixes.

    Key features:

    1. **Basic Usage**:

       ```java
       StringJoiner joiner = new StringJoiner(",");
       joiner.add("apple").add("banana").add("orange");
       System.out.println(joiner); // Output: apple,banana,orange
       ```

    2. **With Prefix and Suffix**:

       ```java
       StringJoiner joiner = new StringJoiner(", ", "[", "]");
       joiner.add("one").add("two").add("three");
       System.out.println(joiner); // Output: [one, two, three]
       ```

    3. **Empty Value Handling**:

       - Returns empty string if no elements added
       - Can set custom empty value using setEmptyValue()

    4. **Advantages**:
       - More efficient than repeated String concatenation
       - Cleaner alternative to StringBuilder for joining strings
       - Thread-safe (unlike StringBuilder)
       - Integrates well with Stream API
