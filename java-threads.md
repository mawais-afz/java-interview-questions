## Java Threads

1. **What is multithreading in Java?**

   Multithreading in Java is the ability to execute multiple threads (lightweight processes) simultaneously within a single program. Each thread runs independently while sharing the same resources. This enables concurrent execution of tasks, improved performance, and better resource utilization. Java provides built-in support for multithreading through its Thread class and Runnable interface.

2. **What are the different ways of implementing multithreading in Java?**

   There are two main ways to implement multithreading in Java:

   1. **Extending Thread class:**
      - Create a class that extends the Thread class
      - Override the `run()` method
      - Create an instance and call `start()`
      
   2. **Implementing Runnable interface:**
      - Create a class that implements the Runnable interface
      - Implement the `run()` method
      - Create a Thread instance with your Runnable and call `start()`

   The Runnable interface approach is generally preferred because:
   - Java doesn't support multiple inheritance, so extending Thread limits further inheritance
   - It provides better separation between the task's logic and thread behavior
   - It's more flexible as the same Runnable can be used with different Thread configurations