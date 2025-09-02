# Java Interview Questions

## 📑 Table of Contents  

- [Java Fundamentals](#-java-fundamentals)  
- [Object-Oriented Programming (OOP)](#-object-oriented-programming-oop)  
- [Classes, Objects, and Methods](#-classes-objects-and-methods)  
- [Access Modifiers and Keywords](#-access-modifiers-and-keywords)  
- [Exception Handling](#-exception-handling)  
- [Multithreading and Concurrency](#-multithreading-and-concurrency)  
- [Collections Framework](#-collections-framework)  
- [Memory Management and JVM](#-memory-management-and-jvm)  
- [String Handling](#-string-handling)  
- [Java 8+ Features](#-java-8-features)  
- [Advanced Topics](#-advanced-topics)  
- [Performance and Optimization](#-performance-and-optimization)  
- [Coding Standards and Best Practices](#-coding-standards-and-best-practices)  

## 🔧 Java Fundamentals

### Platform Independence and Compilation

- Why is Java platform independent?  
- What is bytecode in Java?  
- What is JVM and how does it work?  
- What is JIT compiler?  
- What is the difference between JDK, JRE, and JVM?  
- What are the main differences between C++ and Java?  

### Data Types and Variables

- What are the data types in Java?  
- What are wrapper classes in Java?  
- What are local, instance, and class variables?  
- What is the scope/lifetime of different variables (local, instance, static)?  
- Where are variables stored in memory in Java?  
- What are constants and how to create them in Java?  
- What are identifiers in Java?  
- What is type conversion in Java?  
- What is automatic type conversion (widening)?  
- What is narrowing conversion in Java?  
- What is coercion in Java?  

### Basic Concepts

- What is ASCII Code?  
- What is Unicode?  
- What is the difference between Character Constant and String Constant in Java?  

### Operators

- What is the purpose of the `instanceof` operator?  
- Difference between `>>` and `>>>` operators in Java?  

### Control Structures

- Can we use String in switch-case statements?  

---

## 🏗️ Object-Oriented Programming (OOP)

### OOP Concepts

- What is object-oriented programming and its features?  
- What are the benefits of OOP compared to procedural programming?  
- Explain procedural programming and its features.  
- Is Java a purely object-oriented language?  

### Core OOP Principles

- What is encapsulation and how is it achieved in Java?  
- What is inheritance in Java?  
- What is polymorphism in Java?  
- What is abstraction in Java?  
- What is the difference between abstraction and encapsulation?  

### Relationships

- What is 'IS-A' relationship in Java?  
- What is 'HAS-A' relationship in Java?  
- Difference between 'IS-A' and 'HAS-A' relationships?  
- What is the difference between `implements` and `extends` in Java?  

---

## 🏛️ Classes, Objects, and Methods

### Classes and Objects

- What is a class in Java?  
- What is an object in Java?  
- What are reference variables in Java?  
- What is the difference between an object and a reference?  
- Which gets garbage collected: the object or the reference?  
- Can we pass objects as arguments in Java?  
- How do we copy or clone objects in Java?  

### Methods

- What is a method in Java?  
- What is method overloading in Java?  
- What is method overriding in Java?  
- Difference between method overloading and overriding in Java?  
- Can a private method be overridden in Java?  
- Can we override or overload static methods in Java?  
- Can static methods access instance variables in Java?  
- How does the JVM handle method overloading and overriding internally?  

### Constructors

- What is a constructor in Java?  
- What is the difference between a constructor and a method?  
- Can we call one constructor from another?  
- Does the compiler create a default constructor if a parameterized one exists?  
- Can we override constructors in Java?  
- What is a copy constructor in Java?  

### Main Method

- Why is the `main()` method public, static, and void in Java?  
- What is the purpose of the `main()` method in Java?  

---

## 🔐 Access Modifiers and Keywords

### Access Modifiers

- What are access modifiers in Java?  
- What is the difference between access specifiers and access modifiers?  
- What access modifiers can be used for classes in Java?  
- What access modifiers can be used for methods in Java?  
- What access modifiers can be used for variables in Java?  
- What access modifiers are allowed for top-level classes?  

### Keywords

- What is the `super` keyword in Java?  
- What is the `this` keyword in Java?  
- What is the difference between `this()` and `super()` in Java?  
- What is the `final` keyword in Java (variable, method, class)?  
- What is the purpose of the `synchronized` keyword?  
- What is the `transient` keyword in Java?  
- What is the `volatile` keyword in Java?  
- What is the purpose of the `strictfp` keyword?  
- What is the difference between `static` and `final` keywords?  
- What does `null` mean in Java?  

### Static Elements

- What are static blocks or static initializers in Java?  
- What is static import in Java?  
- What is a static method in Java?  
- What is a class-level lock in Java?  
- Can we synchronize static methods in Java?  

---

## ⚠️ Exception Handling

### Basics

- What is an exception in Java?  
- What is an error in Java?  
- What is exception handling in Java and what are its advantages?  
- In how many ways can we do exception handling in Java?  
- What are the types of exceptions in Java?  
- What are the keywords used in exception handling?  
- In which situations can exceptions arise in Java?  

### Try-Catch-Finally

- How do `try` and `catch` blocks work in Java?  
- Can we have a `try` block without a `catch` block?  
- Can we have multiple `catch` blocks for a single `try`?  
- Can we catch multiple exceptions in a single `catch` block?  
- What is the purpose of the `finally` block in Java?  
- Can we have code between `try`, `catch`, and `finally`?  
- When will a `finally` block not be executed?  
- What is the importance of `finally` compared to a `return` statement?  

### Checked and Unchecked

- What are checked exceptions in Java?  
- What are unchecked exceptions in Java?  
- What is the difference between checked and unchecked exceptions?  
- Can we catch checked exceptions explicitly?  

### Throw/Throws

- What is the difference between `throw` and `throws` in Java?  
- What is the purpose of the `throw` keyword?  
- What is the purpose of the `throws` keyword?  
- Can we write code after a `throw` statement?  

### Advanced

- What is default exception handling in Java?  
- What are user-defined exceptions?  
- Can we rethrow an exception from a catch block?  
- Can we use nested `try` statements in Java?  
- What is the `Throwable` class and its role?  
- What is the difference between `ClassNotFoundException` and `NoClassDefFoundError`?  
- What is `OutOfMemoryError` in Java and how can it be handled?  
- What is `IllegalMonitorStateException` and when is it thrown?  

---

## 🧵 Multithreading and Concurrency

### Thread Fundamentals

- What is a process?  
- What is a thread in Java?  
- What is the difference between a process and a thread?  
- What is multitasking, and what are its types?  
- What are the benefits of multithreaded programming?  
- What is multithreading in Java?  

### Thread Creation and Management

- What Java APIs support thread creation and management?  
- What is the main thread in Java?  
- How many ways can we create threads in Java?  
- How do we create a thread by extending the `Thread` class?  
- How do we create a thread by implementing `Runnable`?  
- Which approach is better: extending `Thread` vs implementing `Runnable`?  
- What is the difference between `Runnable` and `Callable`?  

### Thread Lifecycle

- What is the role of the thread scheduler in Java?  
- What is the life cycle of a thread in Java?  
- What are the different thread states?  
- Can we restart a dead thread in Java?  
- What happens if we don’t override the `run()` method?  
- Can we overload the `run()` method in Java?  

### Thread Control

- What methods can be used to control thread execution?  
- What is the purpose of the `yield()` method?  
- Can a yielded thread regain execution immediately?  
- What is the purpose of the `join()` method in Java?  
- What is the purpose of the `sleep()` method in Java?  
- Does calling `sleep()` release the lock on an object?  
- What is the difference between `sleep()` and `wait()`?  
- What is the `interrupt()` method and how is it used?  

### Synchronization

- What is synchronization in Java?  
- What are locks and their purpose in Java?  
- What are synchronized methods, and when should we use them?  
- What are synchronized blocks, and what are their advantages?  
- Can we use synchronized blocks for primitives?  

### Thread Communication

- What is inter-thread communication in Java?  
- How do `wait()`, `notify()`, and `notifyAll()` methods work?  
- Why are `wait()`, `notify()`, and `notifyAll()` defined in `Object` class, not `Thread`?  
- What is the difference between `wait()` and `notify()`?  
- What is the difference between `notify()` and `notifyAll()`?  
- Do `wait()`, `notify()`, and `notifyAll()` release locks?  
- Which of these methods release a lock: `yield()`, `join()`, `sleep()`, `wait()`, `notify()`, `notifyAll()`?  

### Thread Priorities

- What are thread priorities in Java?  
- How do we change a thread’s priority?  
- If two threads have the same priority, which one executes first?  

### Advanced Threading

- What are thread groups in Java?  
- What are thread-local variables?  
- What are daemon threads in Java?  
- How can we make a thread a daemon thread?  
- Can the `main()` thread be made a daemon?  
- What is context switching in Java threads?  
- What is a deadlock in Java?  
- What is thread starvation, and how can it be prevented?  

### Concurrency Utilities

- What is the difference between `Executor` and `ExecutorService`?  
- What is a `ForkJoinPool` and how is it different from a regular thread pool?  
- How does the Fork/Join framework work?  
- What is a `CyclicBarrier` in Java?  
- What is a `BlockingQueue` in Java?  
- What is the difference between `ReentrantLock` and `synchronized`?  
- What is the difference between `StampedLock` and `ReentrantLock`?  
- What is the difference between pessimistic and optimistic locking?  
- What is lock-free programming in Java?  
- What is “busy spin” in multithreading?  

---

## 📦 Collections Framework

### Collection Framework Basics

- What is the Java Collections Framework?  
- What is a Collection in Java?  
- What is the difference between `collection`, `Collection`, and `Collections` in Java?  
- What are the differences between `Collection` and `Collections`?  
- What is the `Collection` interface in Java?  
- Which interfaces extend the `Collection` interface?  
- What are the main differences between arrays and collections in Java?  
- What is the difference between `List`, `Set`, and `Map` in Java?  

### List Interface

- What is the `List` interface in Java?  
- Explain the `ArrayList` class in Java.  
- What is the difference between an array and an `ArrayList`?  
- Are dynamic arrays supported in Java?  
- Explain the `LinkedList` class in Java.  
- What is the difference between `ArrayList` and `LinkedList`?  
- What is the difference between `ArrayList` and `Vector`?  

### Set Interface

- What is the `Set` interface in Java?  
- What is the difference between `List` and `Set`?  
- Explain the `HashSet` class in Java.  
- Explain the `LinkedHashSet` class in Java.  
- Explain the `TreeSet` class in Java.  
- What is the difference between `HashSet` and `TreeSet`?  
- What is the difference between `HashSet` and `LinkedHashSet`?  
- What is the difference between `LinkedHashSet` and `TreeSet`?  

### Map Interface

- What is the `Map` interface in Java?  
- What is the difference between `Map` and `Set`?  
- What is the difference between `Map` and `Queue`?  
- Explain the `HashMap` class in Java.  
- Explain the `LinkedHashMap` class in Java.  
- Explain the `TreeMap` class in Java.  
- What is the difference between `HashMap` and `Hashtable`?  
- What is the difference between `HashMap` and `TreeMap`?  
- What is the difference between `HashMap` and `LinkedHashMap`?  
- What is the difference between `HashMap` and `ConcurrentHashMap`?  
- How does `ConcurrentHashMap` work internally?  
- What is the difference between `LinkedHashMap` and `PriorityQueue`?  

### Queue Interface

- What is the `Queue` interface in Java?  
- Explain the `PriorityQueue` class in Java.  
- What is the difference between `Queue` and `Deque`?  
- What is the `Deque` interface in Java?  
- Explain the `ArrayDeque` class in Java.  
- What is the difference between `ArrayDeque` and `ArrayList`?  

### Iterators

- What is the `Iterator` interface in Java?  
- What is the `ListIterator` interface in Java?  
- What is the difference between `Iterator` and `ListIterator`?  
- What is the `Enumeration` interface in Java?  
- What is the difference between `Enumeration` and `Iterator`?  
- What is the difference between `Iterator` and `Spliterator`?  
- What is the difference between fail-fast and fail-safe iterators?  

### Comparison

- What is the `Comparable` interface in Java?  
- What is the `Comparator` interface in Java?  
- What is the difference between `Comparable` and `Comparator`?  

---

## 🧠 Memory Management and JVM

### Memory Areas

- What is the Java Memory Model (JMM)?  
- What is the difference between Heap and Stack memory?  
- What is the difference between Path and Classpath in Java?  
- What is classpath in Java?  
- How does the Java Memory Model handle out-of-order execution and memory visibility?  
- What is a memory leak in Java?  
- What is a memory-mapped buffer in Java?  

### Garbage Collection

- What is garbage collection in Java?  
- How many times is the `finalize()` method invoked, and who invokes it?  
- What is the use of the `finalize()` method?  
- How does the G1 Garbage Collector work?  
- What are the challenges in implementing Distributed Garbage Collection (DGC)?  

### Class Loading

- What are the different types of ClassLoaders in Java?  
- How can you implement a custom ClassLoader?  
- How does Class Data Sharing (CDS) work in JVM?  

### Memory References

- What is `PhantomReference` in Java?  
- What is the difference between `WeakReference` and `SoftReference`?  

### Performance and JVM Internals

- What is Escape Analysis in Java optimizations?  
- What are Thread-Local Allocation Buffers (TLAB) in Java?  
- How do JVM flags impact performance tuning?  
- What is the Principle of Locality, and how does it apply to Java?  

---

## 🔤 String Handling

### String Basics  

- What is the Java String Pool?  
- What is the difference between `length` and `length()` in Java?  
- How can you concatenate multiple strings in Java?  
- What is the purpose of the `toString()` method in Java?  

### String Classes Comparison  

- What is the difference between `String`, `StringBuilder`, and `StringBuffer` in Java?  
- Why is `String` immutable in Java, and what are the benefits of immutability?  

---

## 🚀 Java 8+ Features

### Functional Programming  

- What are functional interfaces in Java 8?  
- What are lambda expressions in Java?  
- What are method references in Java?  

### Streams API  

- What are Java 8 Streams?  
- What is the difference between `stream()` and `parallelStream()`?  

### Default Methods  

- What is the purpose of the `default` keyword in interfaces?  
- What are default methods in Java 8 interfaces?  

### Optional Class  

- What is the `Optional` class in Java 8 and why is it used?  

### CompletableFuture  

- What is `CompletableFuture` in Java 8?  
- What are the advanced features of `CompletableFuture`?  

---

## 🔬 Advanced Topics

### Inner Classes  

- What are nested classes in Java?  
- What are inner classes (non-static nested classes) in Java?  
- Why do we use nested classes in Java?  
- What are static nested classes in Java, and how do we instantiate them?  
- What are method-local inner classes in Java, and what are their features?  
- What are anonymous inner classes in Java, and what restrictions apply?  
- What are member inner classes, and how do we instantiate them?  
- Can we instantiate an interface in Java?  

### Interfaces and Abstract Classes  

- What is an interface in Java?  
- What is an abstract class in Java?  
- What is the difference between an abstract class and an interface?  
- Can we create a constructor in an abstract class?  
- What are abstract methods in Java?  
- What is a marker interface in Java, and why is it used?  

### Generics  

- What are Java Generics?  
- What is type inference in Generics?  

### Annotations  

- What are annotations in Java?  

### Reflection  

- Why is reflection used in Java?  
- What is `java.lang.reflect.Proxy` used for?  
- What is the role of `java.lang.instrument`?  

### Serialization  

- How can objects in a Java class be prevented from serialization?  
- Can we serialize static variables in Java?  

### Packages and Imports  

- What is a package in Java?  
- Can we have multiple classes in a single file in Java?  
- Can we have more than one package statement in a source file?  
- Can we define a package statement after an import statement?  
- What is the importance of the `import` keyword in Java?  
- What are the naming conventions for packages in Java?  
- Can we import the same class or package twice in a program?  

### Advanced Language Features  

- What is field hiding in Java?  
- What are varargs in Java?  
- What is a singleton class in Java?  
- What is the difference between `new` and `newInstance()` in Java?  
- What is a compile-time constant in Java?  

### Java Modules  

- What are Java Modules, and how do they enhance security and maintainability?  

---

## ⚡ Performance and Optimization

### JVM Optimizations  

- What are Java’s non-blocking algorithms, and how do they differ from traditional blocking algorithms?  
- What are some JIT compiler optimizations (e.g., loop unrolling, vectorization)?  
- What is Polymorphic Inline Caching (PIC) in JVM?  

### Memory and Performance  

- What is false sharing in Java, and why does it hurt performance?  
- What is a Java memory fence, and why is it important?  

### Advanced Concurrency  

- What is the `Unsafe` class in Java, and what are its use cases?  
- What is a `MethodHandle` in Java, and how does it differ from reflection?  

### Tools and Debugging  

- What is the `jstack` tool, and how is it used?  
- What is a Java Decompiler, and how can it be used securely?  

### Emerging Technologies  

- What is Project Loom in Java, and how does it impact concurrency?  

### Specialized APIs  

- What is the `BitSet` class in Java, and when is it useful?  
- What is Java NIO, and how does it differ from traditional IO?  
- What are the types of JDBC statements in Java?  

### Contracts and Best Practices  

- How can you create an immutable class in Java?  
- What is the contract between `hashCode()` and `equals()` methods?  
- What is the purpose of the `hashCode()` method in Java?  
- What is the difference between `==` and `equals()` in Java?  
- What is the purpose of the `assert` statement in Java?  

---

### 📝 Coding Standards and Best Practices

- What are the recommended Java coding standards for classes?  
- What are the recommended Java coding standards for interfaces?  
- What are the recommended Java coding standards for methods?  
- What are the recommended Java coding standards for variables?  
- What are the recommended Java coding standards for constants?  

---
