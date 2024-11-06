## Java Strings

1. **What is the difference between String, StringBuffer and StringBuilder in Java?**

   | Feature | String | StringBuffer | StringBuilder |
   |---------|---------|--------------|---------------|
   | Mutability | Immutable - creates new object for modifications | Mutable - can be modified without creating new objects | Mutable - can be modified without creating new objects |
   | Thread Safety | Thread-safe (immutable) | Thread-safe (synchronized methods) | Not thread-safe but better performance |
   | Performance | Slower for string modifications | Slower than StringBuilder due to synchronization | Fastest for string modifications |
   | Memory Usage | Creates multiple objects in string pool | Single object, more memory efficient | Single object, more memory efficient |
   | Storage | String Pool | Heap Memory | Heap Memory |
   | Since Version | JDK 1.0 | JDK 1.0 | JDK 1.5 |
   | Use Case | When string will not change frequently | In multi-threaded environments | In single-threaded environments |

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
