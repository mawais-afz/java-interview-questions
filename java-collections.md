# Java Collections Framework

1. **What is the Iterator interface?**

   Iterator is a fundamental interface in Java's Collections Framework that provides a uniform way to traverse through a collection of objects. It represents a cursor pointing to elements in a collection and allows sequential access to those elements.

   Key points about Iterator:

   1. **Core Methods**:

      - `hasNext()`: Returns true if there are more elements
      - `next()`: Returns the next element in iteration
      - `remove()`: Removes the last element returned by next()
      - `forEachRemaining()`: Performs an action on remaining elements (Java 8+)

   2. **Advantages**:
      - Provides a universal way to access elements
      - Safer than direct index access
      - Supports element removal during iteration
      - Works with for-each loops

   Example usage:

   ```java
   List<String> list = new ArrayList<>();
   Iterator<String> iterator = list.iterator();
   while(iterator.hasNext()) {
       String element = iterator.next();
       // Process element
   }
   ```

2. **Explain the difference between Iterator and ListIterator.**

   | Feature           | Iterator                        | ListIterator                                        |
   | ----------------- | ------------------------------- | --------------------------------------------------- |
   | Direction         | Forward only                    | Bi-directional (forward and backward)               |
   | Add Elements      | Cannot add elements             | Can add elements using add()                        |
   | Modification      | Can only remove elements        | Can modify elements using set()                     |
   | Index Access      | No index access                 | Can get index using nextIndex() and previousIndex() |
   | Collection Types  | Works with all Collection types | Only works with List implementations                |
   | Navigation        | Only hasNext() and next()       | Has hasPrevious() and previous() in addition        |
   | Starting Position | Points before first element     | Can be positioned at any index                      |
   | Iteration Start   | Always starts from beginning    | Can start from any arbitrary position               |

   Example usage:

   ```java
   // Iterator - Forward only
   List<String> list = new ArrayList<>();
   Iterator<String> iterator = list.iterator();
   while(iterator.hasNext()) {
       String element = iterator.next();
   }

   // ListIterator - Bidirectional
   ListIterator<String> listIterator = list.listIterator();
   // Forward
   while(listIterator.hasNext()) {
       String element = listIterator.next();
   }
   // Backward
   while(listIterator.hasPrevious()) {
       String element = listIterator.previous();
   }
   ```

3. **Explain the term enumeration in Java.**

   Enumeration is an interface in Java that provides a way to iterate through a collection of objects sequentially. It was part of the original Java collections design before the introduction of Iterator.

   Key points about Enumeration:

   1. **Methods**:

      - `hasMoreElements()`: Tests if more elements exist
      - `nextElement()`: Returns the next element

   2. **Legacy Status**:

      - Considered legacy code since Java 2
      - Replaced by the Iterator interface
      - Still used in some legacy classes like Vector and Properties

   3. **Differences from Iterator**:
      - Cannot remove elements (Iterator can)
      - Method names are longer
      - Less functionality overall

   Example usage:

   ```java
   Vector<String> v = new Vector<>();
   Enumeration<String> e = v.elements();
   while(e.hasMoreElements()) {
       String element = e.nextElement();
       // Process element
   }
   ```

4. **Describe the collection framework in Java.**

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

5. **What are the differences between Arrays and ArrayList in Java?**

   Here's a comparison of arrays and ArrayList in Java:

   | Feature         | Array                            | ArrayList                                     |
   | --------------- | -------------------------------- | --------------------------------------------- |
   | Size            | Fixed length, cannot be modified | Dynamic size, grows automatically as needed   |
   | Type            | Can store primitives and objects | Can only store objects (uses wrapper classes) |
   | Syntax          | int[] arr = new int[10];         | ArrayList<Integer> list = new ArrayList<>();  |
   | Memory          | Less memory overhead             | More memory overhead due to object storage    |
   | Performance     | Faster for fixed-size operations | Slower due to resizing and object overhead    |
   | Dimension       | Can be multidimensional          | Single dimensional (can nest ArrayLists)      |
   | Generics        | Does not work with generics      | Supports generics                             |
   | Utility Methods | Limited built-in methods         | Many utility methods (add, remove, etc.)      |

   Example usage:

   ```java
   // Array example
   int[] array = new int[3];
   array[0] = 1;
   array[1] = 2;
   array[2] = 3;
   // array[3] = 4; // ArrayIndexOutOfBoundsException

   // ArrayList example
   ArrayList<Integer> list = new ArrayList<>();
   list.add(1);
   list.add(2);
   list.add(3);
   list.add(4); // Automatically resizes
   ```

6. **What is the difference between ArrayList and LinkedList in Java?**

   Here's a detailed comparison of ArrayList and LinkedList in Java:

   | Feature            | ArrayList                              | LinkedList                                     |
   | ------------------ | -------------------------------------- | ---------------------------------------------- |
   | Internal Structure | Resizable array (dynamic array)        | Doubly-linked list                             |
   | Memory Storage     | Contiguous memory locations            | Non-contiguous memory locations                |
   | Access Time        | O(1) - constant time for random access | O(n) - linear time for random access           |
   | Insertion/Deletion | Slower (requires shifting elements)    | Faster, especially at beginning/middle         |
   | Memory Overhead    | Less memory per element                | More memory per element (stores next/prev ref) |
   | Best Use Cases     | Frequent random access, less insertion | Frequent insertions/deletions, queue/stack     |
   | Performance        | Better for get() and set() operations  | Better for add() and remove() operations       |
   | Implements         | List, RandomAccess interfaces          | List, Deque interfaces                         |

   Example usage:

   ```java
   // ArrayList example
   ArrayList<String> arrayList = new ArrayList<>();
   arrayList.add("apple");     // O(1) amortized
   arrayList.get(0);           // Very fast O(1) access
   arrayList.remove(0);        // Slower, requires shifting

   // LinkedList example
   LinkedList<String> linkedList = new LinkedList<>();
   linkedList.add("apple");    // Fast O(1) insertion
   linkedList.addFirst("banana"); // Very fast first insertion
   linkedList.get(0);          // Slower O(n) access
   ```

   Key Considerations:

   - Use ArrayList when you need frequent random access
   - Use LinkedList when you need frequent insertions/deletions
   - ArrayList is more memory-efficient
   - LinkedList provides more flexible manipulation operations

7. **What is the difference between List, Set, and Map in Java?**

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

8. **What is the difference between fail-safe and fail-fast iterators?**

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

9. **What is the difference between Vector and an ArrayList?**

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

10. **What are Vector and Stack classes?**

    Vector and Stack are legacy collection classes in Java with specific characteristics:

    | Feature         | Vector                                               | Stack                                                  |
    | --------------- | ---------------------------------------------------- | ------------------------------------------------------ |
    | Inheritance     | Extends AbstractList                                 | Extends Vector                                         |
    | Synchronization | Fully synchronized (thread-safe)                     | Fully synchronized (thread-safe)                       |
    | Primary Use     | Dynamic array with synchronized operations           | Last-In-First-Out (LIFO) data structure                |
    | Key Methods     | add(), remove(), get(), size()                       | push(), pop(), peek(), empty()                         |
    | Performance     | Slower due to synchronization overhead               | Slower due to synchronization overhead                 |
    | Legacy Status   | Introduced in JDK 1.0                                | Introduced in JDK 1.0                                  |
    | Recommended     | Prefer ArrayList with Collections.synchronizedList() | Prefer Deque interface implementations like ArrayDeque |

    Example usage:

    ```java
    // Vector example
    Vector<String> vector = new Vector<>();
    vector.add("element");
    vector.remove(0);

    // Stack example
    Stack<Integer> stack = new Stack<>();
    stack.push(1);
    stack.push(2);
    int topElement = stack.pop(); // Returns 2
    boolean isEmpty = stack.empty(); // Checks if stack is empty
    ```

11. **What are the differences between Collection and Collections in Java?**

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

12. **In which scenario, LinkedList is better than ArrayList in Java?**

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

13. **Contiguous memory locations are usually used for storing actual values in an array but not in ArrayList. Explain**

    This is actually incorrect - both arrays and ArrayLists in Java use contiguous memory locations to store their elements. However, there are some key differences in how they work:

    Arrays:

    - Store primitive values or object references directly in contiguous memory
    - Fixed size allocated at creation
    - Direct memory access to elements

    ArrayList:

    - Uses an internal array to store elements contiguously
    - Automatically grows by creating new, larger array when needed
    - Elements are still stored contiguously, just in the backing array

    Example:

    ```java
    // Array - direct contiguous storage
    int[] array = new int[5];         // Fixed block of 5 integers

    // ArrayList - contiguous storage via internal array
    ArrayList<Integer> list = new ArrayList<>();  // Initial capacity 10
    list.add(1);                      // Stored in backing array
    list.add(2);                      // Next contiguous position
    // When backing array is full, ArrayList creates new larger array
    // and copies elements to maintain contiguous storage
    ```

14. **Why does the java array index start with 0?**

    Java arrays use 0-based indexing primarily because:

    1. Memory efficiency - The index represents the offset from the start of the array. For the first element, the offset is 0.

    2. Historical precedent - C language, which heavily influenced Java, used 0-based indexing. This was based on how pointer arithmetic worked.

    3. Mathematical consistency - Many mathematical sequences and iterations work more naturally with 0-based indexing.

    Example:

    ```java
    int[] arr = new int[5];  // Creates array of size 5
    arr[0] = 1;  // First element at index 0
    arr[4] = 5;  // Last element at index (length-1)

    // Memory offset calculation (conceptual)
    // Location = baseAddress + (index * elementSize)
    // For first element: baseAddress + (0 * elementSize) = baseAddress
    ```

15. **What are the differences between HashMap and HashTable in Java?**

    | Feature          | HashMap                                                         | HashTable                             |
    | ---------------- | --------------------------------------------------------------- | ------------------------------------- |
    | Synchronization  | Not synchronized, not thread-safe                               | Synchronized and thread-safe          |
    | Null Values      | Allows one null key and multiple null values                    | Does not allow null keys or values    |
    | Performance      | Generally better performance due to no synchronization overhead | Slower due to synchronization         |
    | Iterator         | Fail-fast iterator                                              | Enumerator and fail-fast iterator     |
    | Legacy Status    | Modern implementation, introduced in JDK 1.2                    | Legacy class, exists since JDK 1.0    |
    | Inheritance      | Extends AbstractMap                                             | Extends Dictionary and implements Map |
    | Initial Capacity | Default is 16                                                   | Default is 11                         |
    | Load Factor      | Default is 0.75                                                 | Default is 0.75                       |
    | Growth           | Doubles in size when threshold reached                          | Increases by (2 \* size + 1)          |

16. **What is the difference between fail-fast and fail-safe iterators?**

    | Feature       | Fail-Fast Iterator                                 | Fail-Safe Iterator                      |
    | ------------- | -------------------------------------------------- | --------------------------------------- |
    | Behavior      | Throws ConcurrentModificationException if modified | Allows modifications during iteration   |
    | Working       | Works directly on collection                       | Works on clone/snapshot of collection   |
    | Memory        | Uses less memory                                   | Uses more memory due to clone/snapshot  |
    | Performance   | Better performance                                 | Lower performance due to clone creation |
    | Examples      | ArrayList, HashMap, Vector iterators               | ConcurrentHashMap, CopyOnWriteArrayList |
    | Consistency   | Always up-to-date with collection                  | May not reflect recent modifications    |
    | Thread Safety | Not thread-safe                                    | Thread-safe                             |

    Example:

    ```java
    // Fail-fast iterator example
    ArrayList<String> list = new ArrayList<>();
    Iterator<String> iterator = list.iterator();
    list.add("item");  // Will throw ConcurrentModificationException

    // Fail-safe iterator example
    ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
    Iterator<String> safeIterator = map.keySet().iterator();
    map.put("key", 1);  // Won't throw exception
    ```

17. **What makes a HashSet different from a TreeSet?**

    | Feature          | HashSet                                      | TreeSet                                         |
    | ---------------- | -------------------------------------------- | ----------------------------------------------- |
    | Ordering         | No guaranteed order                          | Maintains natural ordering or custom Comparator |
    | Implementation   | Backed by HashMap                            | Backed by TreeMap                               |
    | Performance      | O(1) for add/remove/contains operations      | O(log n) for add/remove/contains operations     |
    | Null Elements    | Allows one null element                      | Does not allow null elements                    |
    | Memory Usage     | Uses more memory due to hash table structure | More memory efficient                           |
    | Duplicate Values | Does not allow duplicates                    | Does not allow duplicates                       |
    | Internal Storage | Hash table with buckets                      | Red-black tree                                  |
    | Use Case         | When order doesn't matter and fast access    | When sorted order is required                   |

18. **What is a Comparator in Java?**

    A Comparator is a functional interface in Java used for custom comparison of objects. It defines a way to compare two objects of the same type for ordering.

    Key points about Comparator:

    | Feature         | Description                                                     |
    | --------------- | --------------------------------------------------------------- |
    | Interface       | Functional interface with compare() method                      |
    | Purpose         | Custom ordering of objects that don't implement Comparable      |
    | Method          | compare(T o1, T o2) returns negative, zero, or positive integer |
    | Natural Order   | Can override natural ordering of objects                        |
    | Multiple Orders | Allows multiple different orderings for same class              |
    | Usage           | Commonly used with sorting methods and ordered collections      |

    Example:

    ```java
    // Comparator to sort strings by length
    Comparator<String> lengthComparator = new Comparator<String>() {
        @Override
        public int compare(String s1, String s2) {
            return s1.length() - s2.length();
        }
    };

    // Lambda expression equivalent
    Comparator<String> lengthComparator = (s1, s2) -> s1.length() - s2.length();

    // Using the comparator
    List<String> list = Arrays.asList("apple", "banana", "kiwi");
    Collections.sort(list, lengthComparator);
    ```

19. **Why is the delete function faster in the linked list than an array?**

    In a linked list, deleting a node requires updating the pointers of the adjacent nodes, which is an O(1) operation. In contrast, deleting an element from an array requires shifting all subsequent elements to fill the gap, which is an O(n) operation. This makes linked lists more efficient for frequent insertions and deletions.

20. **How to copy an array in Java?**

    There are several ways to copy an array in Java:

    1. **Using `Arrays.copyOf()` method:**
       This method creates a new array and copies the specified range of the original array into it.

       ```java
       int[] original = {1, 2, 3, 4, 5};
       int[] copy = Arrays.copyOf(original, original.length);
       ```

    2. **Using `System.arraycopy()` method:**
       This method is a native method that provides a fast way to copy elements from one array to another.

       ```java
       int[] original = {1, 2, 3, 4, 5};
       int[] copy = new int[original.length];
       System.arraycopy(original, 0, copy, 0, original.length);
       ```

    3. **Using a loop:**
       You can manually copy elements using a for loop.

       ```java
       int[] original = {1, 2, 3, 4, 5};
       int[] copy = new int[original.length];
       for (int i = 0; i < original.length; i++) {
          copy[i] = original[i];
       }
       ```

    4. **Using `clone()` method:**
       The `clone()` method creates a shallow copy of the array.

       ```java
       int[] original = {1, 2, 3, 4, 5};
       int[] copy = original.clone();
       ```

    Each of these methods has its own use cases and performance characteristics, so you can choose the one that best fits your needs.

21. **What do you understand by a jagged array?**

    A jagged array, also known as an "array of arrays," is an array whose elements are arrays. The inner arrays can be of different lengths, creating a "jagged" structure. This is in contrast to a multidimensional array, where each dimension must have the same length.

    In Java, you can declare a jagged array as follows:

    ```java
    int[][] jaggedArray = {
        {1, 2, 3},
        {4, 5},
        {6, 7, 8, 9}
    };
    ```

    In this example, `jaggedArray` is a 2D array with three rows, but the lengths of the rows are different. The first row has three elements, the second row has two elements, and the third row has four elements.

    Jagged arrays are useful when you need a collection of arrays of varying lengths, and they provide flexibility in managing such data structures.

22. **Is it possible to make an array volatile?**

    In Java, you cannot make the entire array volatile. However, you can make the reference to the array volatile. This means that the reference to the array will be volatile, but the elements within the array will not be volatile.

    ```java
    private volatile int[] array;
    ```

    In this example, the reference to the `array` is volatile, ensuring visibility of the reference across threads. However, individual elements within the array are not subject to the same visibility guarantees.

    If you need to ensure visibility of individual elements, you would need to use other synchronization mechanisms, such as `synchronized` blocks or `java.util.concurrent.atomic` classes for atomic operations on array elements.

23. **What are the advantages and disadvantages of an array?**

    | Advantages                                      | Disadvantages                                     |
    | ----------------------------------------------- | ------------------------------------------------- |
    | Fast access to elements using index             | Fixed size, cannot be resized                     |
    | Simple and easy to use                          | Insertion and deletion operations are costly      |
    | Memory efficient for storing similar data types | No built-in support for complex data structures   |
    | Supports random access                          | Can lead to wasted memory if not fully utilized   |
    | Cache-friendly due to contiguous memory storage | Does not provide type safety for primitive arrays |

24. **What is CopyOnWriteArrayList in Java?**

    CopyOnWriteArrayList is a thread-safe variant of ArrayList in which all mutative operations (add, set, remove, etc.) are implemented by making a fresh copy of the underlying array.

    Key characteristics:

    1. **Thread Safety**:

       - All operations are thread-safe without explicit synchronization
       - Particularly useful for concurrent applications

    2. **Implementation**:

       - Maintains an immutable array internally
       - Creates a new copy of array for any modification
       - Reads don't require locking

    3. **Best Use Cases**:
       - When reads greatly outnumber writes
       - In observer/listener patterns where iteration is frequent
       - In concurrent scenarios requiring thread-safe list operations

    Example usage:

    ```java
    CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
    list.add("Item 1");  // Creates new copy
    list.add("Item 2");  // Creates new copy

    // Safe iteration even if another thread modifies list
    for(String item : list) {
        System.out.println(item);
    }
    ```

    Note: While thread-safe, it has higher memory overhead and slower write performance due to array copying.

25. **What are the methods used to implement for key Object in HashMap?**

    When implementing a key object for use in HashMap, two methods are essential:

    1. **hashCode()**:

       - Must generate a consistent hash code for the object
       - Objects that are equal must return the same hash code
       - Should distribute hash codes uniformly to avoid collisions
       - Used to determine the bucket location in the HashMap

    2. **equals()**:
       - Must consistently determine if two objects are equal
       - Should be compatible with hashCode() - if equals() returns true, hashCode() must return same value
       - Used to handle hash collisions and find exact matches

    Example implementation:

    ```java
    public class CustomKey {
        private String id;
        private int value;

        @Override
        public int hashCode() {
            return Objects.hash(id, value);
        }

        @Override
        public boolean equals(Object obj) {
            if (this == obj) return true;
            if (!(obj instanceof CustomKey)) return false;
            CustomKey other = (CustomKey) obj;
            return Objects.equals(id, other.id)
                   && value == other.value;
        }
    }
    ```

    Note: Failing to properly implement these methods can lead to:

    - Incorrect storage and retrieval of values
    - Poor performance due to hash collisions
    - Memory leaks or unexpected behavior
