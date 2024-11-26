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

3. **What is the meaning of immutable regarding String?**

   Immutable means that once a String object is created, its contents cannot be changed. Any operation that appears to modify a String actually creates a new String object with the modified value, while the original String remains unchanged. For example:

   ```java
   String str = "Hello";
   str = str + " World"; // Creates new String object, original "Hello" is unchanged
   ```

   This is in contrast to mutable objects like StringBuilder where the same object can be modified:

   ```java
   StringBuilder sb = new StringBuilder("Hello");
   sb.append(" World"); // Modifies the same StringBuilder object
   ```

4. **What makes Java Strings immutable?**

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

5. **Why is String immutable in Java?**

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

6. **Are all String's Immutable in Java?**

   While the String class in Java is designed to be immutable, there are some nuanced scenarios that provide ways to modify string-like content:

   1. **StringBuilder and StringBuffer**

      - Mutable alternatives to String
      - Allow modification of character sequences
      - Designed for scenarios requiring frequent string manipulations
      - Not truly "Strings", but string-like objects

   2. **Reflection Techniques**

      - Advanced techniques can modify String's internal char array
      - Requires using reflection to access private fields
      - Breaks encapsulation and is strongly discouraged
      - Violates the core design principle of String immutability

   3. **String Literal vs String Object**

      - Strings created with literals are pooled and immutable
      - Strings created with `new` keyword are distinct objects
      - Both are technically immutable, but have different memory behaviors

   4. **Practical Immutability**
      - While technically immutable, new "modified" strings are created
      - Operations like `concat()` or `substring()` return new String instances
      - Original string remains unchanged

   The core principle remains: standard String objects are immutable by design, ensuring thread safety, security, and predictable behavior in Java applications.

7. **Where are String values stored in memory?**

   In Java, String values are stored in different memory areas depending on how they are created:

   1. **String Pool (Heap Memory)**

      - String literals are stored in the String Pool
      - Part of the Java heap memory
      - Managed by the Java Runtime Environment (JRE)
      - Enables string interning and memory optimization

   2. **Heap Memory**

      - Strings created using the `new` keyword are stored directly in the heap
      - Not part of the string pool
      - Each `new` String creates a separate object in memory

   3. **Memory Allocation**

      - Immutable String objects are allocated in memory when created
      - References to these objects are stored on the stack
      - Actual string content is stored in the heap

   4. **Garbage Collection**
      - Unused String objects are eligible for garbage collection
      - Memory is automatically managed by the JVM
      - Unreferenced strings are removed to free up memory

   The storage mechanism ensures efficient memory usage while maintaining the immutability of String objects in Java.

8. **Why should you be careful about String concatenation(+) operator in loops? How do you solve this problem?**

   String concatenation using the `+` operator inside loops can lead to significant performance and memory challenges:

   1. **Performance Bottleneck**

      - Each `+` operation creates a new String object
      - Creates multiple intermediate String instances
      - Generates unnecessary memory overhead

   2. **Computational Complexity**

      - Concatenation in loops has O(n²) time complexity
      - Each iteration requires creating and copying entire string contents
      - Performance degrades exponentially with increasing iterations

   3. **Memory Inefficiency**
      - Generates numerous temporary String objects
      - Increases memory consumption
      - Triggers frequent garbage collection
      - Wastes computational resources

   Recommended Solutions:

   1. **StringBuilder**

      - Provides mutable string manipulation
      - More memory-efficient
      - O(n) time complexity
      - Reduces object creation overhead

   2. **StringBuffer** (for thread-safe scenarios)
      - Similar to StringBuilder
      - Synchronized for multi-threaded environments
      - Slightly slower performance compared to StringBuilder

   Example Comparisons:

   Inefficient Approach:

   ```java
   String result = "";
   for (String item : items) {
       result += item;  // Creates new String in each iteration
   }
   ```

   Efficient Approach:

   ```java
   StringBuilder result = new StringBuilder();
   for (String item : items) {
       result.append(item);  // Modifies single object efficiently
   }
   String finalResult = result.toString();
   ```

   For large-scale string manipulations, always prefer `StringBuilder` or `StringBuffer` over the `+` operator in loops.

9. **Why is it said that the length() method of String class doesn't return accurate results?**

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

10. **What is the difference between equals() and ==?**

    | Feature          | `equals()`                                                                           | `==`                                                               |
    | ---------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
    | Purpose          | Compares the content/values of two objects.                                          | Compares the reference (memory address) of two objects.            |
    | Usage            | Used for object comparison, especially for Strings and other objects.                | Used for primitive data types and reference comparison.            |
    | Null Safety      | Can handle null values without throwing an exception (returns false if one is null). | Throws a NullPointerException if one of the references is null.    |
    | Overriding       | Can be overridden in a class to provide custom equality logic.                       | Cannot be overridden; checks reference equality only.              |
    | Default Behavior | Default implementation in Object class checks reference equality unless overridden.  | Always checks reference equality.                                  |
    | Example          | `str1.equals(str2)` compares the actual string values.                               | `str1 == str2` checks if both references point to the same object. |

11. **What is String Pool?**

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

12. **How many ways can we create the string object?**

    There are several ways to create String objects in Java:

    1. **String Literal (`String s = "hello";`)**:

       - Creates string in the String Pool
       - Most memory efficient method
       - Reuses existing string if identical one exists in pool
       - Preferred way for string creation

    2. **Using new operator (`String s = new String("hello");`)**:

       - Creates new String object in heap memory
       - Creates two objects: one in heap and one in string pool
       - Less memory efficient
       - Useful when explicitly needing a new instance

    3. **Using String constructor with byte array**:

       ```java
       byte[] bytes = {65, 66, 67};  // ASCII values
       String str = new String(bytes); // Creates "ABC"
       ```

    4. **Using String constructor with char array**:

       ```java
       char[] chars = {'h', 'e', 'l', 'l', 'o'};
       String str = new String(chars);
       ```

    5. **Using String.valueOf()**:
       ```java
       String str1 = String.valueOf(123);     // From int
       String str2 = String.valueOf(true);    // From boolean
       String str3 = String.valueOf(new char[]{'a', 'b'}); // From char array
       ```

    Example comparing literal vs new:

    ```java
    String str1 = "hello";        // Creates one object in String Pool
    String str2 = "hello";        // Reuses same object from pool
    String str3 = new String("hello"); // Creates new object in heap

    System.out.println(str1 == str2);      // true (same reference)
    System.out.println(str1 == str3);      // false (different objects)
    System.out.println(str1.equals(str3)); // true (same content)
    ```

13. **Why is the character array preferred over string for storing confidential information?**

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

14. **What is StringJoiner?**

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

15. **What are differences between String and StringBuffer?**

    | Aspect            | String                                       | StringBuffer                                                  |
    | ----------------- | -------------------------------------------- | ------------------------------------------------------------- |
    | **Mutability**    | Immutable - cannot be changed after creation | Mutable - can be modified after creation                      |
    | **Thread Safety** | Thread-safe (immutable)                      | Thread-safe (synchronized methods)                            |
    | **Performance**   | Creates new object for each modification     | Modifies existing object, more efficient for multiple changes |
    | **Memory Usage**  | Can be inefficient with many modifications   | More memory efficient for frequent modifications              |
    | **Storage**       | String pool for literals                     | Heap memory                                                   |

    Example demonstrating differences:

    ```java
    // String creates new object for each concatenation
    String str = "Hello";
    str = str + " World";  // Creates new String object

    // StringBuffer modifies existing object
    StringBuffer sbuf = new StringBuffer("Hello");
    sbuf.append(" World"); // Modifies same object
    ```

    Key points:

    1. **Use String when**:

       - Value won't change frequently
       - Thread safety is needed
       - Memory usage isn't a major concern

    2. **Use StringBuffer when**:
       - Frequent modifications needed
       - Thread safety is required
       - Memory efficiency is important
       - Working with large text manipulations

16. **What are differences between StringBuilder and StringBuffer?**

    | Aspect            | StringBuilder                               | StringBuffer                                   |
    | ----------------- | ------------------------------------------- | ---------------------------------------------- |
    | **Thread Safety** | Not thread-safe (no synchronization)        | Thread-safe (synchronized methods)             |
    | **Performance**   | Faster due to no synchronization overhead   | Slower due to synchronization                  |
    | **Use Case**      | Single-threaded environments                | Multi-threaded environments                    |
    | **Methods**       | Same methods as StringBuffer but not synced | Same methods as StringBuilder but synchronized |

    Example demonstrating usage:

    ```java
    // StringBuilder - faster but not thread-safe
    StringBuilder builder = new StringBuilder();
    builder.append("Hello");
    builder.append(" World");

    // StringBuffer - thread-safe but slower
    StringBuffer buffer = new StringBuffer();
    buffer.append("Hello");
    buffer.append(" World");
    ```

    Key points:

    1. **Use StringBuilder when**:

       - Working in single-threaded environment
       - Performance is priority
       - No thread safety needed

    2. **Use StringBuffer when**:
       - Multiple threads access the same string
       - Thread safety is required
       - Willing to trade performance for thread safety

17. **What are some common String utility methods with examples?**

    ```java
    String str = "Hello World";

    // Length
    int length = str.length();  // Returns 11

    // Case conversion
    String upper = str.toUpperCase();  // "HELLO WORLD"
    String lower = str.toLowerCase();  // "hello world"

    // Substring
    String sub = str.substring(0, 5);  // "Hello"

    // Character extraction
    char ch = str.charAt(0);  // 'H'

    // Finding index
    int index = str.indexOf("World");  // 6
    int last = str.lastIndexOf('l');   // 9

    // Trimming whitespace
    String text = "  Hello  ".trim();  // "Hello"

    // String comparison
    boolean equals = str.equals("Hello World");     // true
    boolean ignoreCase = str.equalsIgnoreCase("hello world");  // true

    // Checking content
    boolean starts = str.startsWith("Hello");  // true
    boolean ends = str.endsWith("World");      // true
    boolean contains = str.contains("lo Wo");   // true

    // Replacing
    String replaced = str.replace('l', 'w');    // "Hewwo Worwd"
    String newStr = str.replaceAll("l", "w");   // "Hewwo Worwd"
    ```

    These are some of the most commonly used String utility methods in Java. Each serves a specific purpose in string manipulation and analysis.

18. **How many objects will be created in the following code?**

    ```java
    String s1="Welcome";
    String s2="Welcome";
    String s3="Welcome";
    ```

    Only 1 String object will be created in the String pool. When string literals are used, Java first checks if the string already exists in the String pool. If it does, it reuses the same object. In this case:

    1. When `s1="Welcome"` is executed, a new String object is created in the pool
    2. When `s2="Welcome"` is executed, Java finds "Welcome" already exists in pool, so reuses it
    3. When `s3="Welcome"` is executed, Java again reuses the same pooled object

    All three variables will point to the same String object in memory.

19. **How many objects will be created in the following code?**

    ```java
    String s = new String("Welcome");
    ```

    This code creates 2 objects:

    1. A new String object in the heap(non-pool) memory
    2. A String object in the String pool (if not already present)

20. **What is the output of the following Java program?**

    ```java
    String s1 = "Hello";
    String s2 = "Hello";
    String s3 = new String("Hello");
    System.out.println(s1 == s2);  // Line 1: true
    System.out.println(s1 == s3);  // Line 2: false
    System.out.println(s1.equals(s3)); // Line 3: true
    ```

    The output will be:

    ```
    true
    false
    true
    ```

    Explanation:

    - Line 1 prints `true` because s1 and s2 both refer to the same String object in the String pool since they use string literals
    - Line 2 prints `false` because s3 creates a new String object in the heap memory using `new`, so it has a different reference than s1
    - Line 3 prints `true` because equals() compares the actual string content rather than references, and both strings contain "Hello"

21. **What is the output of the following Java program?**

    ```java
    public class Test
    {
       public static void main (String args[])
       {
          String s1 = "Sharma is a good player";
          String s2 = new String("Sharma is a good player");
          s2 = s2.intern();
          System.out.println(s1 ==s2);
       }
    }
    ```

    The output will be:

    ```
    true
    ```

    Explanation:

    - Initially, `s1` creates a string literal in the String pool
    - `s2` creates a new String object in the heap memory
    - When `intern()` is called on `s2`, it checks if the String pool has an identical string
    - Since "Sharma is a good player" already exists in the pool (referenced by s1), `intern()` returns a reference to that pooled string
    - Therefore, after interning, both `s1` and `s2` reference the same String object in the pool
    - The `==` comparison returns true because both variables now point to the same object

22. **What is the purpose of toString() method in Java?**

    The toString() method in Java is used to get a string representation of an object. Here are the key points about toString():

    - It is defined in the Object class, so every class inherits it
    - By default, it returns the class name followed by @ and the object's hashcode in hexadecimal
    - Classes typically override toString() to provide a meaningful string representation of their objects
    - It is automatically called when an object is concatenated with a String or printed
    - Common use cases include:
        - Debugging and logging
        - Displaying object state in a readable format
        - Converting objects to strings for display purposes

    Example:
    ```java
    class Person {
        String name;
        int age;
        
        @Override
        public String toString() {
            return "Person{name='" + name + "', age=" + age + "}";
        }
    }
    ```