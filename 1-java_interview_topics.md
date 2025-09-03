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

- `public` – accessible everywhere  
- `private` – accessible within same class  
- `protected` – accessible within package and subclasses  
- `default` – accessible within package  

### Keywords

- **static** – class-level variables and methods  
- **final** – constants, preventing inheritance/overriding  
- **super** – accessing parent class members  
- **this** – current object reference  

---

## 2. Memory Management & JVM

### Java Virtual Machine (JVM)

- JVM architecture and components  
- Bytecode and platform independence  
- Class loading mechanism  
- Just-In-Time (JIT) compilation  

### Memory Areas

- **Heap Memory** – Object storage, garbage collected  
- **Stack Memory** – Method calls and local variables  
- **Method Area** – Class-level data  
- **PC Register** – Program counter  

### Garbage Collection

- Automatic memory management  
- Types of garbage collectors (Serial, Parallel, CMS, G1, ZGC, Shenandoah)  
- Memory leaks and prevention  
- `finalize()` method (deprecated)  

---

## 3. Collections Framework

### Core Interfaces

- **Collection** – Root interface  
- **List** – Ordered collection, allows duplicates  
- **Set** – No duplicates allowed  
- **Map** – Key-value pairs  

### Implementations

- **List**: ArrayList, LinkedList, Vector  
- **Set**: HashSet, LinkedHashSet, TreeSet  
- **Map**: HashMap, LinkedHashMap, TreeMap, Hashtable, ConcurrentHashMap  

### Iteration and Comparison

- Iterator vs ListIterator vs Enhanced for loop  
- **Comparable** vs **Comparator**  

---

## 4. Exception Handling

- Exception hierarchy (`Throwable`, `Error`, `Exception`)  
- Checked vs Unchecked exceptions  
- Custom exceptions  
- `try-catch-finally`, `try-with-resources`  
- `throw` vs `throws`  
- Best practices (specific handling, chaining, cleanup)  

---

## 5. Multithreading & Concurrency

- Thread creation (`Thread`, `Runnable`)  
- Thread lifecycle and states  
- Synchronization (`synchronized`, `volatile`, Locks, ReentrantLock)  
- Concurrency issues (race conditions, deadlock, starvation, livelock)  
- Executor framework, Callable/Future, CompletableFuture  
- ThreadLocal  
- Concurrent collections (ConcurrentHashMap, CopyOnWriteArrayList, BlockingQueue)  

---

## 6. String Handling

- Immutability and String pool  
- String vs StringBuilder vs StringBuffer  
- String operations (comparison, concatenation, regex, common methods)  

---

## 7. Generics

- Generic classes, interfaces, methods  
- Bounded/unbounded wildcards, PECS principle  
- Type erasure and limitations  

---

## 8. Java 8+ Features

- Lambda expressions, functional interfaces, method references  
- Stream API (intermediate/terminal ops, parallel streams)  
- Built-in functional interfaces (Predicate, Function, Consumer, Supplier)  
- `Optional` class  
- Date/Time API (`LocalDate`, `LocalTime`, `LocalDateTime`, `ZonedDateTime`)  
- Default methods in interfaces  

---

## 9. Input/Output (I/O)

- File I/O (`File`, `Path`, streams, readers/writers)  
- Serialization (`Serializable`, transient, custom serialization)  
- NIO (channels, buffers, selectors)  

---

## 10. Design Patterns

- **Creational**: Singleton, Factory, Builder  
- **Structural**: Adapter, Decorator, Facade  
- **Behavioral**: Observer, Strategy, Command  

---

## 11. SOLID Principles

- Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion  

---

## 12. Advanced Topics

- Reflection API  
- Annotations (built-in, custom, retention policies)  
- Networking (sockets, URL, HTTP client)  
- JDBC (PreparedStatement, connection pooling, transactions)  

---

## 13. Performance & Optimization

- JVM tuning (GC tuning, heap sizing, flags)  
- Code optimization (string handling, collections, caching)  
- Profiling & monitoring (JConsole, JVisualVM, Flight Recorder, Mission Control)  

---

## 14. Testing

- JUnit basics and annotations  
- Mockito for mocking  
- TDD, integration testing, code coverage  

---

## 15. Common Interview Questions

- Coding: arrays, strings, data structures, algorithms, recursion, DP  
- Conceptual: polymorphism, abstract class vs interface, GC, thread sync  
- Scenarios: thread-safe singleton, handling memory leaks, optimizing performance  

---

## 16. Framework Knowledge (Bonus)

- **Spring Framework**: Dependency Injection, Boot basics, MVC pattern  
- **Hibernate/JPA**: ORM, entity relationships, query optimization  

---

## 17. New Features from JDK 9–21 🚀

### JDK 9

- **Module System (JPMS)** – `module-info.java`  
- **JShell (REPL)**  
- **Collection factory methods** (`List.of`, `Set.of`, `Map.of`)  

### JDK 10

- **Local variable type inference (`var`)**  
- **Application class-data sharing (AppCDS)**  

### JDK 11 (LTS)

- **HttpClient API** (standardized)  
- **New String methods**: `isBlank()`, `lines()`, `repeat()`, `strip()`  
- **Single-file source execution** (`java Hello.java`)  

### JDK 12–13

- **Switch expressions** (`switch` as an expression with `yield`)  
- **Text Blocks (""" multiline strings """)**  

### JDK 14–16

- **Records** – concise immutable data carriers  
- **Pattern matching for `instanceof`**  
- **`Stream.toList()`**  
- **Sealed classes** (JDK 15 preview → JDK 17 standard)  

### JDK 17 (LTS)

- Finalized **Sealed Classes**  
- Strong encapsulation of JDK internals  

### JDK 19–20

- **Record patterns (preview)** – destructuring  
- **Pattern Matching for Switch**  

### JDK 21 (LTS)

- **Virtual Threads (Project Loom)** – lightweight concurrency  
- **Structured Concurrency (preview)**  
- **String Templates (preview)** – embedded expressions in strings  
- **Sequenced Collections** – `SequencedCollection`, `SequencedMap`  
- **Key Encapsulation Mechanism (KEM) API**  

---

## 18. Additional Advanced Topics 📘

- **Java Memory Model (JMM)** – visibility, happens-before rules, atomicity  
- **ClassLoaders** – Bootstrap, Extension, System, Custom  
- **Reference Types** – Strong, Soft, Weak, Phantom references  
- **Escape Analysis & TLAB** – allocation optimization by JIT  
- **Ahead-of-Time Compilation (AOT, GraalVM)**  
- **Reactive Streams API (Flow API)** – `Publisher`, `Subscriber`  
- **Serialization Alternatives** – JSON (Jackson/Gson), Protocol Buffers  
- **Security** – JAAS, permissions, deprecation of SecurityManager  

---

## Interview Preparation Tips

1. Practice coding on whiteboard or paper  
2. Focus on understanding concepts, not memorizing syntax  
3. Prepare real examples for each concept  
4. Practice explaining topics simply and clearly  
5. Revise algorithms & data structures  
6. Stay updated with the latest Java versions  
7. Prepare for system design discussions at senior levels  

---

✅ This now covers **all major theoretical and practical Java interview topics through JDK 21**.  

Do you want me to also **highlight the most frequently asked topics** (the ones that come up almost every interview) so you can prioritize them first?
