# Java Interview Questions by Category

## 1. Core Java Fundamentals

### Object-Oriented Programming (OOP)

13) What is a class?
14) What is an object?
16) What is encapsulation?
151) How to do encapsulation in Java?
189) Explain about procedural programming language or structured programming language and its features?
190) Explain about object oriented programming and its features?
191) List out benefits of object oriented programming language?
192) Differences between traditional programming language and object oriented programming language?
193) Explain oops concepts in detail?
194) Explain what is encapsulation?
195) What is inheritance?
196) Explain importance of inheritance in java?
197) What is polymorphism in java?
32) What is 'IS-A' relationship in java? (Inheritance)
33) What is 'HAS A' relationship in java? (Composition/Aggregation)
34) Difference between 'IS-A' and 'HAS-A' relationship in java?

### Java Basics

15) What is method in java?
24) What are constants and how to create constants in java? (final keyword)
26) Explain Java Coding Standards for classes or Java coding conventions for classes?
27) Explain Java Coding standards for interfaces?
28) Explain Java Coding standards for Methods?
29) Explain Java Coding Standards for variables?
30) Explain Java Coding Standards for Constants?
42) What are identifiers in java?
167) What is type conversion in java?
168) Explain about Automatic type conversion in java?
169) Explain about narrowing conversion in java?
187) Can we use Switch statement with Strings?

### Access Modifiers

43) What are access modifiers in java?
44) What is the difference between access specifiers and access modifiers in java?
45) What access modifiers can be used for class?
46) Explain what access modifiers can be used for methods?
47) Explain what access modifiers can be used for variables?
48) What is final access modifier in java?

### Keywords

4) What is super keyword in java?
12) Difference between this() and super() in java?
25) Difference between '>>' and '>>>' operators in java?
35) Explain about instanceof operator in java?
36) What does null mean in java?
152) What are reference variables in java?
153) Will the compiler creates a default constructor if I have a parameterized constructor in the class?
154) Can we have a method name same as class name in java?
156) Can Static methods access instance variables in java?
157) How do we access static members in java?
158) Can we override static methods in java?
177) Explain about static imports in java?
184) Explain about field hiding in java?
185) Explain about Varargs in java?

## 2. Memory Management & JVM

10) What is JIT compiler?
11) What is bytecode in java?
160) Objects or references which of them gets garbage collected?
161) How many times finalize method will be invoked? who invokes finalize() method in java?
186) Explain where variables are created in memory? (Stack vs Heap)

## 3. Collections Framework

### Core Interfaces

198) What is collections framework?
199) What is collection?
200) Difference between collection, Collection and Collections in java?
201) Explain about Collection interface in java?
202) List the interfaces which extends collection interface?
219) Explain about Map interface in java?
221) What is SortedMap interface?

### List Implementations

203) Explain List interface?
204) Explain methods specific to List interface?
205) List implementations of List Interface?
206) Explain about ArrayList?
207) Difference between Array and ArrayList?
208) What is vector?
209) Difference between arraylist and vector?
210) Define Linked List and its features with signature?
224) Difference between arraylist and linkedlist?

### Set Implementations

213) Explain about Sets?
214) Implementations of Set interface?
215) Explain HashSet and its features?
216) Explain Tree Set and its features?
217) When do we use HashSet over TreeSet?
82) When do we use TreeSet over HashSet?
218) What is Linked HashSet and its features?

### Map Implementations

222) What is Hashtable and explain features of Hashtable?
223) Difference between HashMap and Hashtable?

### Iteration and Comparison

211) Define Iterator and methods in Iterator?
212) In which order the Iterator iterates over collection?
212) Explain ListIterator and methods in ListIterator?
225) Difference between Comparator and Comparable in java?
229) Explain about fail fast iterators in java?
230) Explain about fail safe iterators in java?

### Concurrent Collections

226) What is concurrent hashmap and its features?
227) Difference between Concurrent HashMap and Hashtable and collections.synchronizedHashMap?
228) Explain copyOnWriteArrayList and when do we use copyOnWriteArrayList?

## 4. Exception Handling

### Exception Hierarchy

52) What is an exception in java?
55) What is an error in Java?

### Exception Types

66) What are checked Exceptions?
67) What are unchecked exceptions in java?
68) Explain differences between checked and Unchecked exceptions in java?
76) What are user defined exceptions?

### Exception Handling Blocks

54) What is Exception handling in java?
56) What are advantages of Exception handling in java?
57) In how many ways we can do exception handling in java?
58) List out five keywords related to Exception handling?
59) Explain try and catch keywords in java?
60) Can we have try block without catch block?
61) Can we have multiple catch block for a try block?
62) Explain importance of finally block in java?
63) Can we have any code between try and catch blocks?
64) Can we have any code between try and finally blocks?
65) Can we catch more than one exception in single catch block?
69) What is default Exception handling in java?
73) Explain the importance of finally over return statement?
74) Explain a situation where finally block will not be executed?
78) Can we nested try statements in java?

### throw & throws

70) Explain throw keyword in java?
71) Can we write any code after throw statement?
72) Explain importance of throws keyword in java?
75) Can we use catch statement for checked exceptions?
77) Can we rethrow the same exception from catch handler?

### Specific Exceptions

53) State some situations where exceptions may arise in java?
79) Explain the importance of throwable class and its methods?
80) Explain when ClassNotFoundException will be raised?
81) Explain when NoClassDefFoundError will be raised?
131) Explain IllegalMonitorStateException and when it will be thrown?

## 5. Multithreading & Concurrency

### Thread Fundamentals

83) What is process?
84) What is thread in java?
85) Difference between process and thread?
86) What is multitasking?
87) What are different types of multitasking?
88) What are the benefits of multithreaded programming?
89) Explain thread in java?
90) List Java API that supports threads?
91) Explain about main thread in java?
92) In how many ways we can create threads in java?
93) Explain creating threads by implementing Runnable class?
94) Explain creating threads by extending Thread class?
95) Which is the best approach for creating thread?
96) Explain the importance of thread scheduler in java?
97) Explain the life cycle of thread?
98) Can we restart a dead thread in java?
99) Can one thread block the other thread?
100) Can we restart a thread already started in java?
101) What happens if we don't override run method?
102) Can we overload run() method in java?

### Synchronization

105) What is a lock or purpose of locks in java?
106) In how many ways we can do synchronization in java?
107) What are synchronized methods?
108) When do we use synchronized methods in java?
109) When a thread is executing synchronized methods, then is it possible to execute other synchronized methods simultaneously by other threads?
110) When a thread is executing a synchronized method, then is it possible for the same thread to access other synchronized methods of an object?
111) What are synchronized blocks in java?
112) When do we use synchronized blocks and advantages of using synchronized blocks?
113) What is class level lock?
114) Can we synchronize static methods in java?
115) Can we use synchronized block for primitives?

### Thread Priorities and Control

116) What are thread priorities and importance of thread priorities in java?
117) Explain different types of thread priorities?
118) How to change the priority of thread or how to set priority of thread?
119) If two threads have same priority which thread will be executed first?
120) What all methods are used to prevent thread execution?
121) Explain yield() method in thread class?
122) Is it possible for yielded thread to get chance for its execution again?
123) Explain the importance of join() method in thread class?
124) Explain purpose of sleep() method in java?
125) Assume a thread has lock on it, calling sleep() method on that thread will release the lock?
126) Can sleep() method causes another thread to sleep?
127) Explain about interrupt() method of thread class?
133) Explain which of the following methods releases the lock when yield(), join(), sleep(), wait(), notify(), notifyAll() methods are executed?

### Inter-thread Communication

128) Explain about interthread communication and how it takes place in java?
129) Explain wait(), notify() and notifyAll() methods of object class?
130) Explain why wait(), notify() and notifyAll() methods are in Object class rather than in thread class?
132) When wait(), notify(), notifyAll() methods are called does it releases the lock or holds the acquired lock?

### Thread Groups and Types

134) What are thread groups?
135) What are thread local variables?
136) What are daemon threads in java?
137) How to make a non daemon thread as daemon?
138) Can we make main() thread as daemon?

## 6. String Handling

20) What is difference between length and length() method in java?
21) What is ASCII Code?
22) What is Unicode?
23) Difference between Character Constant and String Constant in java?

## 8. Java 8+ Features

178) Can we define static methods inside interface? (Java 8+)
182) Explain enumeration in java? (Enums)
183) Explain restrictions on using enum?

## 9. Input/Output (I/O) & Serialization

231) What is serialization in java?
232) What is the main purpose of serialization in java?
233) What are alternatives to java serialization?
234) Explain about serializable interface in java?
235) How to make object serializable in java?
236) What is serial version UID and its importance in java?
237) What happens if we don't define serial version UID?
238) Can we serialize static variables in java? (Also 166)
239) When we serialize an object does the serialization mechanism saves its references too?
240) If we don't want some of the fields not to serialize How to do that? (transient)
165) Explain about transient variables in java?

## 10. Design Patterns & SOLID Principles

6) Difference between abstract class and interface? (Strategy, Factory patterns)
49) Explain about abstract classes in java?
50) Can we create constructor in abstract class?
51) What are abstract methods in java?
179) Define interface in java?
180) What is the purpose of interface?
181) Explain features of interfaces in java?

## 12. Advanced Topics

### Nested Classes

139) What are nested classes in java?
140) What are inner classes or non static nested classes in java?
141) Why to use nested classes in java? (or) What is the purpose of nested class in java?
142) Explain about static nested classes in java?
143) How to instantiate static nested classes in java?
144) Explain about method local inner classes or local inner classes in java?
145) Explain about features of local inner class?
146) Explain about anonymous inner classes in java?
147) Explain restrictions for using anonymous inner classes?
148) Is this valid in java? can we instantiate interface in java? (Anonymous class)
149) Explain about member inner classes?
150) How to instantiate member inner class?

### Packages

39) What are packages in java?
40) Can we have more than one package statement in source file?
41) Can we define package statement after import statement in java?
170) Explain the importance of import keyword in java?
171) Explain naming conventions for packages?
172) What is classpath?
173) What is jar?

### Miscellaneous

2) How to call one constructor from the other constructor? (Constructor chaining)
17) Why main() method is public, static and void in java?
18) Explain about main() method in java?
19) What is constructor in java?
37) Can we have multiple classes in single file?
38) What all access modifiers are allowed for top class?
59) What is covariant return? (Note: This appears to be misnumbered)
155) Can we override constructors in java?
159) Difference between object and reference?
162) Can we able to pass objects as an arguments in java?
188) In java how do we copy objects?

## Platform Independence & Compilation (Cross-Category)

7) Why java is platform independent?
8) What is method overloading in java?
9) What is difference between c++ and Java?
1) What are static blocks and static initializers in Java?
3) What is method overriding in java?
5) Difference between method overloading and method overriding in java?
31) Difference between overriding and overloading in java?
174) What is the scope or life time of instance variables?
175) Explain the scope or life time of class variables or static variables?
176) Explain scope or life time of local variables in java?
163) Explain wrapper classes in java?
164) Explain different types of wrapper classes in java?
