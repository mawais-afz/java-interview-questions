# Java Collections Framework

1. **Describe the collection framework in Java.**

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

2. **What are the differences between arrays and ArrayList in Java?**

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

3. **What is the difference between List, Set, and Map in Java?**

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

4. **What is the difference between fail-safe and fail-fast iterators?**

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

5. **What is the difference between Vector and an ArrayList?**

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

6. **What are the differences between Collection and Collections in Java?**

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

7. **In which scenario, LinkedList is better than ArrayList in Java?**

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
