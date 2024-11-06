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

3. **What are the different states of thread?**

   - **New**: A thread that has been created but not yet started.
   - **Runnable**: A thread that is executing or ready to execute.
   - **Blocked**: A thread that is blocked and cannot proceed.
   - **Waiting**: A thread that is waiting for another thread to perform a specific action.
   - **Timed Waiting**: A thread that is waiting for a specified amount of time.
   - **Terminated**: A thread that has completed execution.

4. **What is the difference between start and run method in Java?**

    | Feature           | `start()`                                                          | `run()`                                                   |
    | ----------------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
    | Purpose           | Starts a new thread and invokes the `run()` method in that thread. | Contains the code that defines the thread's task.         |
    | Thread Creation   | Creates a new thread of execution.                                 | Does not create a new thread; runs in the current thread. |
    | Execution Context | Executes in a separate call stack.                                 | Executes in the current call stack.                       |
    | Thread State      | Changes the thread state to Runnable.                              | Does not change the thread state.                         |
    | Usage             | Must be called to start a thread.                                  | Can be called directly, but does not start a new thread.  |
    | Overriding        | Cannot be overridden in the Thread class.                          | Can be overridden in a subclass of Thread.                |

4. **What is the difference between sleep and wait in Java?**
5. **What is the difference between yield and join in Java?**
6. **What is the difference between notify and notifyAll in Java?**
7. **What is the difference between ReentrantLock and synchronized in Java?**
8. **What is the difference between volatile and synchronized in Java?**
