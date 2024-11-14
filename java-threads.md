## Java Threads

1. **What is a thread?**

   A thread is the smallest unit of execution within a process. It represents an independent path of execution with its own program counter, stack, and local variables, while sharing the process's resources like memory and file handles with other threads. Key points about threads:

   - They enable concurrent execution within a single program
   - Multiple threads within the same process share resources
   - Each thread has its own stack and program counter
   - Threads are lightweight compared to processes
   - Java provides built-in support for threads through the Thread class

   Example of creating a thread:

   ```java
   Thread thread = new Thread(() -> {
       System.out.println("Thread is running");
   });
   thread.start();
   ```

2. **What is the Daemon Thread?**

   A daemon thread is a low-priority background thread that provides support to user threads. Key characteristics of daemon threads:

   - They run in the background to perform tasks like garbage collection or service other threads
   - The JVM will not wait for daemon threads to complete before exiting
   - When all user threads terminate, any remaining daemon threads are automatically terminated
   - They can be created by calling setDaemon(true) before starting the thread
   - They inherit the daemon status of their parent thread by default

   Example usage:

   ```java
   Thread daemonThread = new Thread(() -> {
       // background task
   });
   daemonThread.setDaemon(true);
   daemonThread.start();
   ```

3. **What are the different ways to use threads?**

   There are two primary ways to use threads in Java:

   1. **Extending the Thread class**:

      - Create a new class that extends the Thread class.
      - Override the `run()` method with the code you want to execute in the new thread.
      - Create an instance of the new class and call the `start()` method to begin execution.

      Example:

      ```java
      class MyThread extends Thread {
          @Override
          public void run() {
              System.out.println("Thread is running");
          }
      }

      public class Main {
          public static void main(String[] args) {
              MyThread thread = new MyThread();
              thread.start();
          }
      }
      ```

   2. **Implementing the Runnable interface**:

      - Create a new class that implements the Runnable interface.
      - Implement the `run()` method with the code you want to execute in the new thread.
      - Create an instance of the Thread class, passing an instance of the new class to the Thread constructor.
      - Call the `start()` method on the Thread instance to begin execution.

      Example:

      ```java
      class MyRunnable implements Runnable {
          @Override
          public void run() {
              System.out.println("Thread is running");
          }
      }

      public class Main {
          public static void main(String[] args) {
              Thread thread = new Thread(new MyRunnable());
              thread.start();
          }
      }
      ```

   Both approaches achieve the same result, but implementing the Runnable interface is generally preferred because it allows for better separation of task and thread management, and it enables the class to extend another class if needed.

4. **What is multithreading in Java?**

   Multithreading in Java is the ability to execute multiple threads (lightweight processes) simultaneously within a single program. Each thread runs independently while sharing the same resources. This enables concurrent execution of tasks, improved performance, and better resource utilization. Java provides built-in support for multithreading through its Thread class and Runnable interface.

5. **What are the different ways of implementing multithreading in Java?**

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

6. **Explain the Java thread lifecycle/states?**

   A Java thread goes through several states during its lifecycle:

   1. **New**: When a Thread object is created but not yet started using the start() method. The thread is not yet scheduled for execution.

   2. **Runnable**: After calling start(), the thread enters the runnable state. It is now eligible to run and is waiting for the CPU. The thread scheduler will select it to run based on thread priorities.

   3. **Running**: The thread is currently executing in the CPU. A thread in runnable state moves to running state when the thread scheduler selects it.

   4. **Blocked/Waiting**: A thread enters this state when:

      - It is waiting for I/O operations to complete
      - It called wait() on an object and is waiting for notification
      - It is waiting to acquire a lock for entering a synchronized block/method
      - It called sleep() method

   5. **Terminated/Dead**: A thread enters this state when:
      - Its run() method completes execution naturally
      - An uncaught exception terminates the run() method
      - The stop() method is called (though this is deprecated)

   Key transitions:

   - New → Runnable: When start() is called
   - Runnable ↔ Running: Based on thread scheduler
   - Running → Blocked: When waiting for resources or explicitly put to wait
   - Blocked → Runnable: When resources become available or notification received
   - Running → Terminated: When execution completes

   Note that once a thread is terminated, it cannot be restarted. A new thread object must be created for new execution.

7. **What are the different types of Thread Priorities in Java? And what is the default priority of a thread assigned by JVM?**

   - **MIN_PRIORITY (1)**: The minimum priority that a thread can have.
   - **NORM_PRIORITY (5)**: The default priority assigned to a thread by the JVM.
   - **MAX_PRIORITY (10)**: The maximum priority that a thread can have.

   The default priority of a thread assigned by the JVM is `NORM_PRIORITY` (5).

   Thread priorities are used by the thread scheduler to decide when each thread should run. However, thread priority behavior can be platform-dependent and should not be relied upon for program correctness.

8. **What is the difference between start and run method in Java?**

   | Feature           | `start()`                                                          | `run()`                                                   |
   | ----------------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
   | Purpose           | Starts a new thread and invokes the `run()` method in that thread. | Contains the code that defines the thread's task.         |
   | Thread Creation   | Creates a new thread of execution.                                 | Does not create a new thread; runs in the current thread. |
   | Execution Context | Executes in a separate call stack.                                 | Executes in the current call stack.                       |
   | Thread State      | Changes the thread state to Runnable.                              | Does not change the thread state.                         |
   | Usage             | Must be called to start a thread.                                  | Can be called directly, but does not start a new thread.  |
   | Overriding        | Cannot be overridden in the Thread class.                          | Can be overridden in a subclass of Thread.                |

9. **What is the difference between sleep and wait in Java?**

   | Feature        | `sleep()`                                  | `wait()`                                                   |
   | -------------- | ------------------------------------------ | ---------------------------------------------------------- |
   | Purpose        | Pauses thread execution for specified time | Releases lock and waits for notification from other thread |
   | Lock Release   | Does not release any locks held            | Releases the lock on the object                            |
   | Method Type    | Static method of Thread class              | Instance method of Object class                            |
   | Notification   | Automatically wakes after time period      | Must be notified by notify()/notifyAll()                   |
   | Usage Context  | Can be called anywhere                     | Must be called from synchronized context                   |
   | Exception      | Throws InterruptedException                | Throws InterruptedException                                |
   | Resource State | No change in resource state                | Used when waiting for state change in shared resource      |

10. **What is the difference between yield and join in Java?**
11. **What is the difference between notify and notifyAll in Java?**
12. **What is the difference between ReentrantLock and synchronized in Java?**
13. **What is the difference between volatile and synchronized in Java?**

14. **What is the difference between a program and a process?**

    - **Program**: A program is a set of instructions written in a programming language that is designed to perform a specific task. It is a static entity stored on disk (e.g., an executable file) and does not consume system resources until it is executed.

    - **Process**: A process is an instance of a program that is currently being executed. It is a dynamic entity that includes the program code, its current activity, and the resources allocated to it (such as memory and file handles). A process can have multiple threads of execution running concurrently.

    In summary, a program is a passive collection of instructions, while a process is an active execution of those instructions with its own state and resources.

15. **Can we make the main() thread a daemon thread?**

    - No, the main() thread cannot be made a daemon thread. In Java, the main thread is the first thread that is created when a program starts, and it is not possible to change its daemon status after it has been started. Daemon threads are designed to run in the background and do not prevent the JVM from exiting when the program finishes executing. Since the main thread is responsible for the execution of the program, it must complete before the JVM can terminate, making it non-daemon by nature.

16. **Why is synchronization necessary? Explain with the help of a relevant example.**

    Synchronization is necessary to prevent race conditions and ensure thread safety when multiple threads access shared resources. Without synchronization, concurrent access to shared data can lead to data corruption and inconsistent results.

    Here's an example that demonstrates the need for synchronization:

    ```java
    public class BankAccount {
       private int balance = 1000;

       // Without synchronization - can cause race conditions
       public void withdraw(int amount) {
          if (balance >= amount) {
                // Thread might be interrupted here
                balance = balance - amount;
          }
       }
    }
    ```

    If two threads simultaneously try to withdraw money from the same account, they might both read the initial balance before either one updates it, leading to incorrect withdrawals. Here's the synchronized version:

    ```java
    public class BankAccount {
       private int balance = 1000;

       // With synchronization - thread safe
       public synchronized void withdraw(int amount) {
          if (balance >= amount) {
                balance = balance - amount;
          }
       }
    }
    ```

    With synchronization:

    - Only one thread can execute the withdraw method at a time
    - The balance will always be accurate
    - Race conditions are prevented
    - Data consistency is maintained

17. **Assume a thread has a lock on it, calling the sleep() method on that thread will release the lock?**

    No, calling sleep() on a thread that holds a lock will not release the lock. When a thread goes to sleep:

    - It temporarily pauses execution for the specified duration
    - It continues to hold any locks it has acquired
    - Other threads cannot acquire those locks until the sleeping thread wakes up
    - The thread maintains ownership of the monitor/lock throughout its sleep period

    This is an important distinction from wait(), which does release the lock when called. This is why wait() must be called from within a synchronized block, while sleep() can be called from anywhere.

    Example:

    ```java
    public synchronized void example() {
        // Thread has lock here
        Thread.sleep(1000); // Still has lock while sleeping
        // Thread still has lock here after waking
    }
    ```
