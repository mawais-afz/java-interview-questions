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

2. **What is concurrency?**

   Concurrency is the ability of a program to execute multiple tasks simultaneously. In Java, this is achieved through threads that can run in parallel. Key aspects of concurrency include:

   - Multiple tasks progressing at the same time
   - Shared resources being accessed by multiple threads
   - Need for synchronization to prevent race conditions
   - Can improve performance on multi-core systems
   - Requires careful handling of thread safety

   Example of concurrent execution:

   ```java
   // Two threads running concurrently
   Thread thread1 = new Thread(() -> {
       for(int i = 0; i < 5; i++) {
           System.out.println("Thread 1: " + i);
       }
   });

   Thread thread2 = new Thread(() -> {
       for(int i = 0; i < 5; i++) {
           System.out.println("Thread 2: " + i);
       }
   });

   thread1.start();
   thread2.start();
   ```

3. **What is thread safety?**

   Thread safety is a property of code that ensures correct behavior when multiple threads access shared resources concurrently. It prevents race conditions, data corruption, and unexpected results in multi-threaded environments. Key aspects of thread safety include:

   - Preventing simultaneous access to shared mutable state
   - Ensuring predictable and consistent behavior under concurrent execution
   - Using synchronization mechanisms to control thread interactions
   - Avoiding data races and maintaining data integrity

   Common techniques for achieving thread safety:

   - Synchronized methods and blocks
   - Immutable objects
   - Thread-local variables
   - Atomic operations
   - Concurrent data structures from java.util.concurrent package

   Example of a non-thread-safe scenario:

   ```java
   class Counter {
       private int count = 0;

       // Not thread-safe - multiple threads can corrupt the count
       public void increment() {
           count++; // This operation is not atomic
       }
   }

   // Thread-safe version
   class ThreadSafeCounter {
       private final AtomicInteger count = new AtomicInteger(0);

       public void increment() {
           count.incrementAndGet(); // Atomic operation
       }
   }
   ```

   Thread safety is crucial in multi-threaded applications to prevent data inconsistencies and ensure reliable concurrent programming.

4. **What is the Daemon Thread?**

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

5. **What are the different ways to use threads? Or How do you create a thread in Java?**

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

6. **What is the difference between a process and a thread?**

   A process and a thread are two fundamental concepts in concurrent programming with key differences:

   | Feature           | Process                                       | Thread                                                               |
   | ----------------- | --------------------------------------------- | -------------------------------------------------------------------- |
   | Definition        | Independent program with its own memory space | Lightweight unit of execution within a process                       |
   | Memory            | Has its own memory space and resources        | Shares memory space and resources with other threads in same process |
   | Creation Cost     | More expensive to create                      | Less expensive to create                                             |
   | Context Switching | More expensive due to separate memory spaces  | Less expensive as memory is shared                                   |
   | Communication     | Inter-process communication (IPC) needed      | Can directly share data through shared memory                        |
   | Isolation         | Isolated from other processes                 | Share resources with other threads                                   |
   | Failure Impact    | Failure contained within process              | Failure can affect entire process                                    |
   | Resource Usage    | More system resources required                | Less system resources required                                       |

   Key points:

   1. **Resource Sharing**

      - Processes are independent and don't share resources by default
      - Threads within same process share code, data, and resources

   2. **Performance**

      - Thread creation and switching is faster than processes
      - Threads provide better performance for concurrent operations

   3. **Communication**

      - Threads can communicate directly through shared memory
      - Processes require special IPC mechanisms

   4. **Reliability**
      - Process crashes don't affect other processes
      - Thread crashes can bring down entire process

7. **What is multithreading in Java?**

   Multithreading in Java is the ability to execute multiple threads (lightweight processes) simultaneously within a single program. Each thread runs independently while sharing the same resources. This enables concurrent execution of tasks, improved performance, and better resource utilization. Java provides built-in support for multithreading through its Thread class and Runnable interface.

8. **What are the different ways of implementing multithreading in Java?**

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

9. **What are the states/lifecycle of a thread?**

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

10. **What are the different types of Thread Priorities in Java? And what is the default priority of a thread assigned by JVM?**

    - **MIN_PRIORITY (1)**: The minimum priority that a thread can have.
    - **NORM_PRIORITY (5)**: The default priority assigned to a thread by the JVM.
    - **MAX_PRIORITY (10)**: The maximum priority that a thread can have.

    The default priority of a thread assigned by the JVM is `NORM_PRIORITY` (5).

    Thread priorities are used by the thread scheduler to decide when each thread should run. However, thread priority behavior can be platform-dependent and should not be relied upon for program correctness.

11. **What is the difference between start and run method in Java?**

    | Feature           | `start()`                                                          | `run()`                                                   |
    | ----------------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
    | Purpose           | Starts a new thread and invokes the `run()` method in that thread. | Contains the code that defines the thread's task.         |
    | Thread Creation   | Creates a new thread of execution.                                 | Does not create a new thread; runs in the current thread. |
    | Execution Context | Executes in a separate call stack.                                 | Executes in the current call stack.                       |
    | Thread State      | Changes the thread state to Runnable.                              | Does not change the thread state.                         |
    | Usage             | Must be called to start a thread.                                  | Can be called directly, but does not start a new thread.  |
    | Overriding        | Cannot be overridden in the Thread class.                          | Can be overridden in a subclass of Thread.                |

12. **What is the difference between sleep and wait in Java?**

    | Feature        | `sleep()`                                  | `wait()`                                                   |
    | -------------- | ------------------------------------------ | ---------------------------------------------------------- |
    | Purpose        | Pauses thread execution for specified time | Releases lock and waits for notification from other thread |
    | Lock Release   | Does not release any locks held            | Releases the lock on the object                            |
    | Method Type    | Static method of Thread class              | Instance method of Object class                            |
    | Notification   | Automatically wakes after time period      | Must be notified by notify()/notifyAll()                   |
    | Usage Context  | Can be called anywhere                     | Must be called from synchronized context                   |
    | Exception      | Throws InterruptedException                | Throws InterruptedException                                |
    | Resource State | No change in resource state                | Used when waiting for state change in shared resource      |

13. **What is the difference between yield and join in Java?**

    | Feature           | `yield()`                                           | `join()`                                                    |
    | ----------------- | --------------------------------------------------- | ----------------------------------------------------------- |
    | Purpose           | Temporarily pauses current thread for other threads | Makes current thread wait for another thread to complete    |
    | Thread State      | Moves thread from Running to Runnable state         | Moves current thread to Waiting state                       |
    | Execution Control | Thread may immediately resume execution             | Thread must wait for joined thread to finish                |
    | Lock Release      | Does not release any locks held                     | Does not release any locks held                             |
    | Method Type       | Static method of Thread class                       | Instance method of Thread class                             |
    | Exception         | Does not throw any exceptions                       | Throws InterruptedException                                 |
    | Guarantee         | No guarantee other threads will execute             | Guarantees joined thread completes before current continues |

14. **What is the difference between notify and notifyAll in Java?**

    | Feature          | `notify()`                                         | `notifyAll()`                                       |
    | ---------------- | -------------------------------------------------- | --------------------------------------------------- |
    | Purpose          | Wakes up a single waiting thread                   | Wakes up all waiting threads                        |
    | Thread Selection | Randomly selects one thread from wait set          | Notifies all threads in wait set                    |
    | Resource Usage   | More efficient when only one thread needs to wake  | Less efficient but safer when multiple need to wake |
    | Usage Context    | Must be called from synchronized context           | Must be called from synchronized context            |
    | Method Type      | Instance method of Object class                    | Instance method of Object class                     |
    | Race Conditions  | May cause issues if wrong thread is awakened       | Avoids issues by waking all threads                 |
    | Common Use Case  | When exactly one thread should handle notification | When multiple threads may need to handle state      |

15. **What is the difference between ReentrantLock and synchronized in Java?**

16. **What is the difference between a program and a process?**

    - **Program**: A program is a set of instructions written in a programming language that is designed to perform a specific task. It is a static entity stored on disk (e.g., an executable file) and does not consume system resources until it is executed.

    - **Process**: A process is an instance of a program that is currently being executed. It is a dynamic entity that includes the program code, its current activity, and the resources allocated to it (such as memory and file handles). A process can have multiple threads of execution running concurrently.

    In summary, a program is a passive collection of instructions, while a process is an active execution of those instructions with its own state and resources.

17. **Can we make the main() thread a daemon thread?**

    - No, the main() thread cannot be made a daemon thread. In Java, the main thread is the first thread that is created when a program starts, and it is not possible to change its daemon status after it has been started. Daemon threads are designed to run in the background and do not prevent the JVM from exiting when the program finishes executing. Since the main thread is responsible for the execution of the program, it must complete before the JVM can terminate, making it non-daemon by nature.

18. **Why is synchronization necessary? Explain with the help of a relevant example.**

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

19. **Assume a thread has a lock on it, calling the sleep() method on that thread will release the lock?**

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

20. **What is the synchronized keyword?**

    The synchronized keyword in Java is used to prevent multiple threads from simultaneously executing a block of code or method, ensuring thread safety. When a thread enters a synchronized block/method, it acquires a lock (monitor) that prevents other threads from entering synchronized blocks protected by the same lock.

    Key aspects of synchronized:

    1. **Method Synchronization**:

       ```java
       public synchronized void method() {
           // Only one thread can execute this at a time
       }
       ```

    2. **Block Synchronization**:

       ```java
       public void method() {
           synchronized(this) {
               // Only one thread can execute this block at a time
           }
       }
       ```

    3. **Static Synchronization**:
       ```java
       public static synchronized void method() {
           // Synchronizes on the Class object
       }
       ```

    Benefits:

    - Prevents race conditions
    - Ensures data consistency
    - Establishes happens-before relationships
    - Provides mutual exclusion

    Drawbacks:

    - Can impact performance due to thread blocking
    - May cause deadlocks if not used carefully
    - Increases contention between threads

21. **What is the volatile keyword?**

    The volatile keyword in Java is used to ensure the visibility of variable changes across multiple threads. When a variable is declared as volatile, it guarantees that:

    1. **Immediate Visibility**

       - Changes to the variable are immediately visible to other threads
       - Prevents thread caching of variable values
       - Ensures reading the most up-to-date value from main memory

    2. **Memory Barrier**
       - Prevents instruction reordering around the volatile variable
       - Creates a happens-before relationship between thread writes and reads
       - Provides a lightweight synchronization mechanism

    Example usage:

    ```java
    public class SharedResource {
        private volatile boolean flag = false;

        public void updateFlag() {
            flag = true; // Immediately visible to other threads
        }

        public void checkFlag() {
            while (!flag) {
                // Will see the most recent value of flag
            }
        }
    }
    ```

    Key characteristics:

    - Used for simple shared variables
    - Ensures visibility but not atomicity of operations
    - Lightweight compared to synchronized
    - Useful for flags, status indicators, and simple state variables

    Common use cases:

    - Thread termination flags
    - Status indicators
    - Simple shared state variables
    - Avoiding thread caching issues

22. **What is the difference between volatile and synchronized in Java?**

    | Feature           | `volatile`                                                    | `synchronized`                                                |
    | ----------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
    | Purpose           | Ensures visibility of variable changes across threads         | Provides mutual exclusion and synchronization of method/block |
    | Locking Mechanism | No locking mechanism                                          | Acquires and releases locks on objects or methods             |
    | Performance       | Lightweight, minimal performance overhead                     | Heavier, more significant performance impact                  |
    | Atomic Operations | Guarantees visibility, not atomicity of complex operations    | Ensures atomic execution of entire synchronized block/method  |
    | Use Case          | Simple shared variable that needs immediate visibility        | Complex operations requiring exclusive access to shared state |
    | Keyword Scope     | Can be applied only to variables                              | Can be applied to methods and code blocks                     |
    | Memory Barrier    | Prevents instruction reordering and ensures memory visibility | Creates memory barrier and ensures thread-safe state          |

23. **What is deadlock?**

    A deadlock is a situation in concurrent programming where two or more threads are unable to proceed because each is waiting for the other to release a lock or resource. In other words, it's a state of mutual blocking where threads are stuck in a circular dependency.

    Key characteristics of deadlock:

    1. **Circular Wait Condition**

       - Threads are waiting for resources held by each other
       - Creates a circular chain of resource dependencies
       - No thread can make progress

    2. **Four Necessary Conditions**:
       - **Mutual Exclusion**: Resources cannot be shared simultaneously
       - **Hold and Wait**: Threads hold resources while waiting for others
       - **No Preemption**: Resources cannot be forcibly taken from threads
       - **Circular Wait**: Threads form a circular chain of resource requests

    Example scenario:

    ```java
    public class DeadlockExample {
        private static final Object RESOURCE_A = new Object();
        private static final Object RESOURCE_B = new Object();

        public static void main(String[] args) {
            Thread thread1 = new Thread(() -> {
                synchronized(RESOURCE_A) {
                    System.out.println("Thread 1: Holding Resource A");
                    try { Thread.sleep(50); } catch (InterruptedException e) {}

                    synchronized(RESOURCE_B) {
                        System.out.println("Thread 1: Waiting for Resource B");
                    }
                }
            });

            Thread thread2 = new Thread(() -> {
                synchronized(RESOURCE_B) {
                    System.out.println("Thread 2: Holding Resource B");
                    try { Thread.sleep(50); } catch (InterruptedException e) {}

                    synchronized(RESOURCE_A) {
                        System.out.println("Thread 2: Waiting for Resource A");
                    }
                }
            });

            thread1.start();
            thread2.start();
        }
    }
    ```

    Prevention strategies:

    3. **Consistent Lock Ordering**

       - Always acquire locks in the same order
       - Prevents circular wait condition

    4. **Lock Timeout**

       - Set a maximum wait time for lock acquisition
       - Release locks if timeout occurs

    5. **Try-Lock Mechanisms**

       - Use `tryLock()` with timeout instead of `synchronized`
       - Allows more flexible lock handling

    6. **Resource Hierarchy**
       - Assign a global ordering to resources
       - Threads must request resources in this order

    Detecting deadlocks:

    - Thread dumps
    - Profiling tools
    - Monitoring thread states
    - Java's built-in thread management tools

24. **How do notify() and notifyAll() work, and what's the difference between them?**

    - `notify()` wakes up a single thread waiting on the object's monitor
    - `notifyAll()` wakes up all threads waiting on the object's monitor
    - Both methods must be called from within a synchronized context
    - Neither method releases the lock on the object

    Why prefer notifyAll():

    - Safer than notify() since it avoids missed wakeups
    - Prevents "lost wake-up" problems where the wrong thread gets notified
    - More predictable behavior in complex scenarios with multiple conditions
    - Small performance overhead compared to potential bugs
    - Follows principle "When in doubt, wake everybody up"

    Example usage:

    ```java
    synchronized(sharedObject) {
        // Modify state
        sharedObject.notifyAll(); // Wake up all waiting threads
    }
    ```

25. **What is a race condition and how do you avoid it?**

    A race condition occurs when multiple threads access shared data concurrently and at least one thread modifies the data, leading to unpredictable results based on the timing/sequence of thread execution.

    Ways to avoid race conditions:

    1. **Synchronization**

       - Use synchronized blocks/methods
       - Ensures only one thread can access critical section at a time
       - Example:

       ```java
       synchronized(object) {
           // Critical section - only one thread at a time
           sharedCounter++;
       }
       ```

    2. **Atomic Classes**

       - Use atomic classes from java.util.concurrent.atomic
       - Provide atomic operations without explicit locking
       - Example: AtomicInteger, AtomicReference

    3. **Locks**

       - More flexible than synchronized
       - ReentrantLock, ReadWriteLock etc.
       - Allow timeouts and interruptible lock attempts

    4. **Thread-Safe Collections**

       - Use concurrent collections
       - ConcurrentHashMap, CopyOnWriteArrayList etc.
       - Built-in thread safety

    5. **Immutable Objects**
       - Make shared objects immutable
       - Immutable objects are inherently thread-safe
       - No synchronization needed for read-only data

    Common race condition scenarios:

    - Check-then-act operations
    - Read-modify-write sequences
    - Initialization races

26. **What is a deadlock and how do you avoid it?**

    A deadlock occurs when two or more threads are blocked forever, each waiting for the other to release resources. It happens when threads hold resources and request additional ones in a circular manner.

    Example of a deadlock:

    ```java
    // Thread 1
    synchronized(resourceA) {
        synchronized(resourceB) {
            // Use both resources
        }
    }

    // Thread 2
    synchronized(resourceB) {
        synchronized(resourceA) {
            // Use both resources
        }
    }
    ```

    Ways to avoid deadlocks:

    1. **Lock Ordering**

       - Always acquire locks in a fixed, predefined order
       - Prevents circular wait conditions
       - Example: Always lock resourceA before resourceB

    2. **Lock Timeouts**

       - Use tryLock() with timeout instead of lock()
       - Prevents indefinite waiting
       - Thread can release its locks and retry

    3. **Deadlock Detection**

       - Implement detection mechanisms
       - Use thread dumps and monitoring
       - Have recovery strategies

    4. **Resource Allocation**

       - Request all resources at once
       - Release all resources before requesting new ones
       - Avoid holding resources while waiting for others

    5. **Thread Management**
       - Minimize number of locked resources
       - Keep critical sections small
       - Use higher-level concurrency utilities when possible

27. What are some of the high-level concurrency classes provided by java.util.concurrent and how do they work?

    The java.util.concurrent package provides several high-level concurrency utilities:

    1. **ExecutorService**

       - Manages thread pools and task execution
       - Provides methods for submitting tasks and controlling their lifecycle
       - Example implementations: ThreadPoolExecutor, ScheduledThreadPoolExecutor

    2. **BlockingQueue**

       - Thread-safe queue implementation
       - Supports operations that wait for the queue to become non-empty/non-full
       - Implementations: ArrayBlockingQueue, LinkedBlockingQueue, PriorityBlockingQueue

    3. **CountDownLatch**

       - Allows one or more threads to wait until a set of operations completes
       - Initialized with a count
       - Count decrements as tasks complete
       - Waiting threads released when count reaches zero

    4. **CyclicBarrier**

       - Allows a set of threads to wait for each other to reach a common barrier point
       - Can be reused after release
       - Useful for parallel algorithms

    5. **Semaphore**

       - Controls access to a shared resource through permits
       - Can be used to implement resource pools
       - Supports fair and unfair queueing

    6. **ConcurrentHashMap**

       - Thread-safe version of HashMap
       - Provides better concurrency than synchronized collections
       - Supports atomic operations and lock striping

    7. **CompletableFuture**

       - Supports asynchronous programming
       - Allows composition of asynchronous operations
       - Provides extensive error handling capabilities

    8. **Atomic Classes**
       - Provides atomic operations on single variables
       - Examples: AtomicInteger, AtomicReference, AtomicBoolean
       - Supports lock-free algorithms

28. **Can you implement a producer-consumer solution in Java?**