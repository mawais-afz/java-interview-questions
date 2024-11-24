# Java Exceptions

1. **What is exception handling?**

   Exception handling is a mechanism in Java that allows you to handle runtime errors and exceptional conditions in a structured way. It provides a means to detect, report, and recover from errors that occur during program execution.

   The main components of exception handling in Java are:

   - **try block**: This keyword is used to define a block of code that may throw an exception. The code within the try block is monitored for exceptions.
   - **catch block**: This keyword is used to define a block of code that handles the exception thrown by the try block. It follows the try block and specifies the type of exception it can handle.
   - **finally block**: This keyword is used to define a block of code that will execute after the try and catch blocks, regardless of whether an exception was thrown or caught. It is typically used for cleanup activities, such as closing resources.
   - **throw keyword**: This keyword is used to explicitly throw an exception from a method or block of code. It can be used to indicate that an error condition has occurred.
   - **throws clause**: This keyword is used in a method signature to declare that a method can throw one or more exceptions. It informs the caller of the method that they need to handle or declare these exceptions.

   Example:

   ```java
   try {
       // Code that might throw an exception
       readFile("data.txt");
   } catch (IOException e) {
       // Handle the exception
       System.err.println("Error reading file: " + e.getMessage());
   } finally {
       // Cleanup code that always runs
       closeResources();
   }
   ```

   Exception handling helps make programs more robust and maintainable by separating error-handling code from regular business logic.

2. **What is an exception? What are the different types of exceptions?**

   An exception in Java is an event that disrupts the normal flow of the program's execution. It represents an error or unexpected behavior that can occur during runtime. Exceptions can be categorized into two main types: checked exceptions and unchecked exceptions.

   - **Checked Exceptions**: These exceptions are checked at compile-time, meaning the Java compiler requires that they be either caught using a try-catch block or declared in the method signature with the `throws` keyword. This ensures that the programmer is aware of these exceptions and can handle them appropriately. Examples of checked exceptions include `IOException`, `SQLException`, and `ClassNotFoundException`.

   - **Unchecked Exceptions**: These exceptions are not checked at compile-time, so the compiler does not require them to be handled or declared. Unchecked exceptions typically indicate programming errors, such as logic errors or improper use of an API. They are subclasses of `RuntimeException`. Examples include `NullPointerException`, `ArrayIndexOutOfBoundsException`, and `IllegalArgumentException`.

   In summary, exceptions are events that disrupt program execution, with checked exceptions requiring explicit handling or declaration, while unchecked exceptions do not have this requirement and generally indicate programming errors.

3. **Explain hierarchy of Java Exception classes?**

   In Java, all exception classes are organized in a hierarchy with `Throwable` as the root class. Here's the breakdown of the exception hierarchy:

   ```
   Throwable
   ├── Error (unchecked)
   │   ├── OutOfMemoryError
   │   ├── StackOverflowError
   │   └── ...
   └── Exception
       ├── IOException (checked)
       ├── SQLException (checked)
       ├── ClassNotFoundException (checked)
       └── RuntimeException (unchecked)
           ├── NullPointerException
           ├── ArrayIndexOutOfBoundsException
           ├── ArithmeticException
           └── ...
   ```

   - **Throwable**: The root class of the exception hierarchy. All errors and exceptions inherit from this class.

   - **Error**: A subclass of Throwable representing serious problems that applications should not try to handle.

   - **Exception**: The superclass of all exception classes. It has two main categories:
     - Checked Exceptions: Direct subclasses of Exception (excluding RuntimeException)
     - Unchecked Exceptions: RuntimeException and its subclasses

   This hierarchy helps organize different types of exceptional conditions and determines which exceptions need to be explicitly handled (checked) and which don't (unchecked).

4. **What is checked, unchecked exception and errors?**

   | Feature        | Checked Exception                                 | Unchecked Exception                                  | Error                                                       |
   | -------------- | ------------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------- |
   | Definition     | Exceptions that must be either caught or declared | Exceptions that don't need to be explicitly caught   | Serious problems that applications should not try to handle |
   | When Checked   | Compile time                                      | Runtime                                              | Runtime                                                     |
   | Need to Handle | Yes - must use try-catch or throws                | Optional                                             | Not meant to be caught                                      |
   | Base Class     | Exception (excluding RuntimeException)            | RuntimeException                                     | Error                                                       |
   | Examples       | IOException, SQLException                         | NullPointerException, ArrayIndexOutOfBoundsException | OutOfMemoryError, StackOverflowError                        |
   | Common Causes  | External factors like I/O, network issues         | Programming mistakes, logic errors                   | System/JVM level issues                                     |
   | Recovery       | Can be anticipated and recovered from             | Can be prevented through better coding               | Usually unrecoverable                                       |
   | Best Practice  | Handle explicitly with appropriate error handling | Fix the underlying code issue                        | Let the application terminate                               |

5. **What is the difference between Error and Exception in Java?**

   | Feature    | Error                                                                  | Exception                                                     |
   | ---------- | ---------------------------------------------------------------------- | ------------------------------------------------------------- |
   | Purpose    | Represents serious problems that applications should not try to handle | Represents conditions that applications can and should handle |
   | Nature     | Usually external to the application and unrecoverable                  | Usually related to application logic and recoverable          |
   | Handling   | Not meant to be caught or handled by application code                  | Should be caught and handled appropriately                    |
   | Examples   | OutOfMemoryError, StackOverflowError, VirtualMachineError              | IOException, SQLException, NullPointerException               |
   | Cause      | Typically caused by the runtime environment                            | Typically caused by the application itself                    |
   | Categories | All errors are unchecked                                               | Can be either checked or unchecked exceptions                 |
   | Recovery   | Generally impossible to recover from                                   | Can be anticipated and recovered from                         |
   | Prevention | Usually cannot be prevented by application code                        | Can often be prevented through proper coding                  |

   In summary, Errors represent serious system-level problems that applications cannot handle, while Exceptions represent conditions that applications should anticipate and handle appropriately.

6. **What is exception handling?**

   Exception handling in Java is a mechanism that allows a program to handle errors and exceptions gracefully, rather than crashing when an error occurs. It involves using try, catch, and finally blocks to catch and handle exceptions, and using throw and throws to throw exceptions.

7. **Name the base class of all the Java exception classes**

   The base class of all the Java exception classes is `Throwable`.

8. **What is NullPointerException in Java?**

   A NullPointerException is a runtime exception that occurs in Java when the Java Virtual Machine (JVM) attempts to access an object or call a method on an object that has not been initialized, meaning it is null. This exception indicates that the program is trying to use a reference that points to no location in memory.

   Common scenarios that can lead to a NullPointerException include:

   - Attempting to call a method on a null object reference.
   - Trying to access or modify a field of a null object.
   - Attempting to get the length of an array that is null.
   - Using null in a collection, such as adding a null value to a List.

   To avoid NullPointerExceptions, it is important to ensure that objects are properly initialized before use and to perform null checks where necessary. Additionally, using Java's Optional class can help manage the presence or absence of values more effectively.

9. **What is the difference between throw and throws?**

   | Feature        | throw                                           | throws                                                                   |
   | -------------- | ----------------------------------------------- | ------------------------------------------------------------------------ |
   | Purpose        | Used to explicitly throw an exception           | Used to declare that a method can throw exceptions                       |
   | Usage          | Can be used within any method or block          | Used only in method signatures                                           |
   | Exception Type | Can throw both checked and unchecked exceptions | Can declare checked exceptions only                                      |
   | Control Flow   | Transfers control to the nearest catch block    | Does not transfer control; informs the caller about potential exceptions |
   | Syntax         | `throw new ExceptionType("message");`           | `public void methodName() throws ExceptionType {}`                       |

   In summary, `throw` is used to actually throw an exception, while `throws` is used in a method declaration to indicate that the method may throw exceptions.

10. **What are custom exceptions?**

    Custom exceptions in Java are user-defined exception classes that extend the built-in Exception class or one of its subclasses. They allow developers to create specific exception types that can represent particular error conditions in their applications. By defining custom exceptions, developers can provide more meaningful error messages and handle exceptions in a way that is tailored to the application's needs.

    To create a custom exception, you typically define a new class that extends Exception (or RuntimeException for unchecked exceptions) and provide constructors to initialize the exception message and any other relevant information. For example:

    ```java
    public class MyCustomException extends Exception {
        public MyCustomException(String message) {
            super(message);
        }
    }
    ```

    Custom exceptions can be thrown using the `throw` keyword and can be caught using `try-catch` blocks, just like standard exceptions. This enhances the clarity and maintainability of the code by allowing developers to handle specific error scenarios more effectively.

    In summary, custom exceptions provide a way to define application-specific error conditions, improving error handling and making the code more understandable.

11. **How does an exception propagate in the code?**

    Exception propagation in Java occurs when an exception is thrown in a method and is not caught within that method. Instead, the exception is passed up the call stack to the method that called it. This process continues until the exception is either caught by a catch block or reaches the main method, at which point the program will terminate if the exception remains unhandled.

    When an exception is thrown, the Java Virtual Machine (JVM) looks for a matching catch block in the current method. If it does not find one, it moves to the calling method and repeats the process. This continues until a suitable catch block is found or the top of the call stack is reached.

    For example, consider the following scenario:

    ```java
    public void methodA() {
        methodB(); // Calls methodB
    }

    public void methodB() {
        throw new RuntimeException("An error occurred"); // Exception thrown here
    }
    ```

    In this case, `methodB` throws a `RuntimeException`, which is not caught within `methodB`. Therefore, the exception propagates back to `methodA`, which also does not handle it. If `methodA` does not catch the exception, it will continue to propagate up to the main method, potentially causing the program to terminate if unhandled.

    Understanding exception propagation is crucial for effective error handling in Java applications, as it allows developers to manage exceptions at appropriate levels in the call stack.

12. **How do exceptions affect the program if it doesn't handle them?**

    When exceptions are not handled in a Java program, they have several serious consequences:

    1. Program Termination: Unhandled exceptions propagate up the call stack until they reach the main method. If still unhandled, the JVM terminates the program abruptly.

    2. Stack Trace Output: The JVM prints a stack trace to the error stream (usually the console), showing where the exception occurred and its propagation path.

    3. Resource Leaks: Abrupt termination means resources like files, network connections, or database connections may not be properly closed.

    4. Data Loss: Any unsaved data or in-progress operations are lost when the program terminates unexpectedly.

    Example of program termination due to unhandled exception:

    ```java
    public static void main(String[] args) {
        String str = null;
        str.length(); // Throws NullPointerException
        // Program terminates here, this line never executes
        System.out.println("This won't be printed");
    }
    ```

    To prevent these issues, exceptions should be properly caught and handled using try-catch blocks, allowing the program to gracefully recover from errors and maintain stability.

13. **Is it mandatory for a catch block to be followed after a try block?**

    No, it is not mandatory for a catch block to follow a try block. A try block must be followed by either a catch block, a finally block, or both. There are three valid combinations:

    1. try-catch
    2. try-finally
    3. try-catch-finally

    The catch block handles exceptions that occur in the try block. The finally block contains cleanup code that executes whether an exception occurs or not. Here are examples of each:

14. **What are different scenarios causing "Exception in thread main"?**

    The "Exception in thread main" error occurs in several common scenarios:

    1. NullPointerException:

       - Attempting to access methods or properties of a null object

       ```java
       String str = null;
       str.length(); // Throws NullPointerException
       ```

    2. ArrayIndexOutOfBoundsException:

       - Accessing an array index that doesn't exist

       ```java
       int[] arr = new int[3];
       arr[3] = 1; // Throws ArrayIndexOutOfBoundsException
       ```

    3. NumberFormatException:

       - Invalid number format in string conversion

       ```java
       int num = Integer.parseInt("abc"); // Throws NumberFormatException
       ```

    4. ClassNotFoundException:

       - When JVM can't find a specified class

       ```java
       Class.forName("NonExistentClass"); // Throws ClassNotFoundException
       ```

    5. NoClassDefFoundError:

       - When a required class definition is missing at runtime

       ```java
       // Attempting to use a class that exists during compilation but missing at runtime
       MissingClass obj = new MissingClass(); // Throws NoClassDefFoundError
       ```

    6. StackOverflowError:
       - Infinite recursion or extremely deep call stack
       ```java
       public void infiniteRecursion() {
           infiniteRecursion(); // Throws StackOverflowError
       }
       ```

    These exceptions typically occur in the main thread and will terminate the program if not properly handled with try-catch blocks.

15. **While overriding a method can you throw another exception or broader exception?**

    When overriding a method, you can:

    - Throw the same exception as the parent method
    - Throw a more specific (narrower) exception than the parent method
    - Choose not to throw any exception
    - You CANNOT throw a new or broader exception than what the parent method declares

    Example:

    ```java
    class Parent {
        void method() throws IOException {
            // Method implementation
        }
    }

    class Child extends Parent {
        // Valid: throws same exception
        void method() throws IOException {
            // Method implementation
        }

        // Valid: throws more specific exception
        void method() throws FileNotFoundException { // FileNotFoundException is a subclass of IOException
            // Method implementation
        }

        // Valid: throws no exception
        void method() {
            // Method implementation
        }

        // INVALID: throws broader or new exception
        // void method() throws Exception { // Won't compile
        //     // Method implementation
        // }
    }
    ```

16. **What is difference between ClassNotFoundException and NoClassDefFoundError?**

    ClassNotFoundException and NoClassDefFoundError are two distinct issues:

    1. ClassNotFoundException:

       - It's a checked exception (extends Exception)
       - Thrown when trying to load a class through its string name using methods like Class.forName() or ClassLoader.loadClass()
       - Occurs during runtime when the class is not found in the classpath

       ```java
       try {
           Class.forName("com.example.NonExistentClass"); // Throws ClassNotFoundException
       } catch (ClassNotFoundException e) {
           e.printStackTrace();
       }
       ```

    2. NoClassDefFoundError:
       - It's an error (extends Error)
       - Thrown when a class that was present during compilation is not found during runtime
       - Usually occurs when a class was present during compilation but missing during runtime, or if a static initializer fails
       ```java
       // If MyClass.class exists during compilation but is deleted/missing at runtime:
       MyClass obj = new MyClass(); // Throws NoClassDefFoundError
       ```

    Key differences:

    - ClassNotFoundException is a checked exception that must be handled explicitly
    - NoClassDefFoundError is an error that indicates a serious problem, typically unrecoverable
    - ClassNotFoundException occurs during explicit class loading attempts
    - NoClassDefFoundError occurs when a previously available class is missing at runtime
