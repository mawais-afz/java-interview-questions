# Java Interview Topics Guide

## 1. Core Java Fundamentals

### Object-Oriented Programming (OOP)

- **Encapsulation** - Data hiding and access control
- **Inheritance** - IS-A relationship, method overriding
- **Polymorphism** - Method overloading and overriding
- **Abstraction** - Abstract classes and interfaces

### Java Basics

- Data types (primitive and non-primitive)
- Variables and constants
- Operators (arithmetic, logical, bitwise, assignment)
- Control structures (if-else, switch, loops)
- Method overloading vs method overriding
- Constructor chaining and types

### Access Modifiers

- `public` - accessible everywhere
- `private` - accessible within same class
- `protected` - accessible within package and subclasses
- `default` - accessible within package

### Keywords

- **static** - class-level variables and methods
- **final** - constants, preventing inheritance/overriding
- **super** - accessing parent class members
- **this** - current object reference

## 2. Memory Management & JVM

### Java Virtual Machine (JVM)

- JVM architecture and components
- Bytecode and platform independence
- Class loading mechanism
- Just-In-Time (JIT) compilation

### Memory Areas

- **Heap Memory** - Object storage, garbage collected
- **Stack Memory** - Method calls and local variables
- **Method Area** - Class-level data
- **PC Register** - Program counter

### Garbage Collection

- Automatic memory management
- Types of garbage collectors
- Memory leaks and prevention
- finalize() method

## 3. Collections Framework

### Core Interfaces

- **Collection** - Root interface
- **List** - Ordered collection, allows duplicates
- **Set** - No duplicates allowed
- **Map** - Key-value pairs

### List Implementations

- **ArrayList** - Dynamic array, fast random access
- **LinkedList** - Doubly linked list, fast insertion/deletion
- **Vector** - Synchronized ArrayList

### Set Implementations

- **HashSet** - Hash table based, no ordering
- **LinkedHashSet** - Maintains insertion order
- **TreeSet** - Sorted set, implements NavigableSet

### Map Implementations

- **HashMap** - Hash table based, allows null
- **LinkedHashMap** - Maintains insertion/access order
- **TreeMap** - Sorted map based on keys
- **Hashtable** - Synchronized, no null values
- **ConcurrentHashMap** - Thread-safe alternative to HashMap

### Iteration and Comparison

- Iterator vs ListIterator vs Enhanced for loop
- **Comparable** - natural ordering (compareTo method)
- **Comparator** - custom ordering (compare method)

## 4. Exception Handling

### Exception Hierarchy

- **Throwable** - Root class
- **Error** - System-level errors
- **Exception** - Application-level exceptions
- **RuntimeException** - Unchecked exceptions

### Exception Types

- **Checked Exceptions** - Compile-time checking required
- **Unchecked Exceptions** - Runtime exceptions
- **Custom Exceptions** - User-defined exception classes

### Exception Handling Blocks

- `try-catch-finally` blocks
- `try-with-resources` for automatic resource management
- `throw` vs `throws` keywords
- Exception propagation

### Exception Best Practices

- Specific exception handling
- Proper resource cleanup
- Avoiding empty catch blocks
- Exception chaining

## 5. Multithreading & Concurrency

### Thread Fundamentals

- Thread creation (extending Thread, implementing Runnable)
- Thread lifecycle and states
- Thread priority and daemon threads
- Inter-thread communication

### Synchronization

- `synchronized` keyword (methods and blocks)
- `volatile` keyword
- Locks and ReentrantLock
- ReadWriteLock

### Concurrency Issues

- **Race conditions** - Multiple threads accessing shared data
- **Deadlock** - Circular dependency of locks
- **Starvation** - Thread unable to gain access to resources
- **Livelock** - Threads keep changing state in response to each other

### Advanced Concurrency

- **Executor Framework** - Thread pool management
- **Callable and Future** - Asynchronous computation
- **CompletableFuture** - Asynchronous programming
- **ThreadLocal** - Thread-specific data

### Concurrent Collections

- ConcurrentHashMap
- CopyOnWriteArrayList
- BlockingQueue implementations

## 6. String Handling

### String Characteristics

- **Immutability** - Strings cannot be changed
- **String Pool** - Memory optimization technique
- String literal vs String object creation

### String Classes

- **String** - Immutable character sequence
- **StringBuffer** - Mutable, thread-safe
- **StringBuilder** - Mutable, not thread-safe (faster)

### String Operations

- String concatenation performance
- String comparison (== vs equals())
- String methods (substring, indexOf, replace, etc.)
- Regular expressions and Pattern/Matcher classes

## 7. Generics

### Generic Concepts

- Type safety at compile time
- Generic classes and interfaces
- Generic methods
- Bounded type parameters

### Wildcards

- **Upper bounded** wildcards (? extends T)
- **Lower bounded** wildcards (? super T)
- **Unbounded** wildcards (?)
- PECS principle (Producer Extends, Consumer Super)

### Type Erasure

- Compile-time vs runtime behavior
- Bridge methods
- Limitations of generics

## 8. Java 8+ Features

### Lambda Expressions

- Functional programming concepts
- Lambda syntax and usage
- Method references
- Functional interfaces (@FunctionalInterface)

### Stream API

- Stream creation and operations
- Intermediate operations (filter, map, sorted)
- Terminal operations (collect, forEach, reduce)
- Parallel streams

### Built-in Functional Interfaces

- Predicate, Function, Consumer, Supplier
- BiFunction, BinaryOperator, UnaryOperator

### Optional Class

- Avoiding NullPointerException
- Optional methods (isPresent, orElse, ifPresent)

### Date and Time API

- LocalDate, LocalTime, LocalDateTime
- ZonedDateTime and time zones
- DateTimeFormatter
- Period and Duration

### Default Methods

- Interface evolution
- Multiple inheritance of behavior
- Diamond problem resolution

## 9. Input/Output (I/O)

### File I/O

- File and Path classes
- FileInputStream/FileOutputStream
- BufferedReader/BufferedWriter
- Try-with-resources for automatic closing

### Serialization

- Serializable interface
- ObjectInputStream/ObjectOutputStream
- transient keyword
- Custom serialization (readObject/writeObject)

### NIO (New I/O)

- Channels and Buffers
- Non-blocking I/O
- Selectors

## 10. Design Patterns

### Creational Patterns

- **Singleton** - Single instance creation
- **Factory** - Object creation without specifying exact class
- **Builder** - Step-by-step object construction

### Behavioral Patterns

- **Observer** - One-to-many dependency notification
- **Strategy** - Algorithm encapsulation
- **Command** - Encapsulating requests as objects

### Structural Patterns

- **Adapter** - Interface compatibility
- **Decorator** - Adding behavior dynamically
- **Facade** - Simplified interface to complex subsystem

## 11. SOLID Principles

- **Single Responsibility Principle** - One reason to change
- **Open/Closed Principle** - Open for extension, closed for modification
- **Liskov Substitution Principle** - Substitutability of derived classes
- **Interface Segregation Principle** - Many specific interfaces
- **Dependency Inversion Principle** - Depend on abstractions

## 12. Advanced Topics

### Reflection API

- Class metadata examination
- Dynamic method invocation
- Field access and modification
- Creating objects dynamically

### Annotations

- Built-in annotations (@Override, @Deprecated, @SuppressWarnings)
- Custom annotations
- Annotation processing
- Retention policies

### Networking

- Socket programming
- URL and URLConnection
- HTTP client libraries

### Database Connectivity

- JDBC fundamentals
- Connection pooling
- PreparedStatement vs Statement
- Transaction management

## 13. Performance & Optimization

### JVM Tuning

- Heap size configuration
- Garbage collection tuning
- JVM flags and parameters

### Code Optimization

- Object creation best practices
- String handling optimization
- Collection choice impact
- Caching strategies

### Profiling and Monitoring

- Memory profiling tools
- Performance monitoring
- JConsole and JVisualVM

## 14. Testing

### Unit Testing

- JUnit framework basics
- Test annotations (@Test, @Before, @After)
- Assertions and test methods
- Mocking with Mockito

### Testing Best Practices

- Test-driven development (TDD)
- Code coverage
- Integration testing

## 15. Common Interview Questions Categories

### Coding Questions

- Array and string manipulation
- Data structure implementations
- Algorithm problems (sorting, searching)
- Recursion and dynamic programming

### Conceptual Questions

- Explain polymorphism with examples
- Difference between abstract class and interface
- How garbage collection works
- Thread synchronization mechanisms

### Scenario-Based Questions

- Designing a thread-safe singleton
- Handling memory leaks
- Optimizing collection performance
- Exception handling strategies

## 16. Framework Knowledge (Bonus)

### Spring Framework

- Dependency Injection
- Spring Boot basics
- Spring MVC pattern

### Hibernate/JPA

- Object-Relational Mapping
- Entity relationships
- Query optimization

---

## Interview Preparation Tips

1. **Practice coding** on whiteboard or paper
2. **Understand concepts** rather than memorizing syntax
3. **Prepare examples** for each topic
4. **Practice explaining** complex topics simply
5. **Review common algorithms** and data structures
6. **Stay updated** with latest Java versions
7. **Practice system design** for senior positions

---

*Good luck with your Java interview preparation!*
