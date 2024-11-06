1. **What is the difference between Error and Exception in Java?**

   In Java, both Errors and Exceptions are subclasses of the Throwable class, but they represent different types of problems that can occur during the execution of a program.

   - **Error**: Errors are serious issues that a typical application should not try to catch. They are usually external to the application and indicate problems that are not expected to be handled by the program. Examples include OutOfMemoryError, StackOverflowError, and other system-level errors. Errors are typically caused by the environment in which the application is running.

   - **Exception**: Exceptions are conditions that a program can catch and handle. They represent problems that can occur during the execution of a program and can be anticipated and recovered from. Exceptions can be further categorized into checked exceptions (which must be declared in the method signature or handled) and unchecked exceptions (which do not require explicit handling). Examples of exceptions include IOException, SQLException, and NullPointerException.

   In summary, Errors are usually fatal and indicate serious problems, while Exceptions are conditions that can be caught and handled by the application.

2. **What is exception handling?**

   Exception handling in Java is a mechanism that allows a program to handle errors and exceptions gracefully, rather than crashing when an error occurs. It involves using try, catch, and finally blocks to catch and handle exceptions, and using throw and throws to throw exceptions.

3. **Name the base class of all the Java exception classes**

   The base class of all the Java exception classes is `Throwable`.

4. **What is an exception? What are the different types of exceptions?**

   An exception in Java is an event that disrupts the normal flow of the program's execution. It represents an error or unexpected behavior that can occur during runtime. Exceptions can be categorized into two main types: checked exceptions and unchecked exceptions.

   - **Checked Exceptions**: These exceptions are checked at compile-time, meaning the Java compiler requires that they be either caught using a try-catch block or declared in the method signature with the `throws` keyword. This ensures that the programmer is aware of these exceptions and can handle them appropriately. Examples of checked exceptions include `IOException`, `SQLException`, and `ClassNotFoundException`.

   - **Unchecked Exceptions**: These exceptions are not checked at compile-time, so the compiler does not require them to be handled or declared. Unchecked exceptions typically indicate programming errors, such as logic errors or improper use of an API. They are subclasses of `RuntimeException`. Examples include `NullPointerException`, `ArrayIndexOutOfBoundsException`, and `IllegalArgumentException`.

   In summary, exceptions are events that disrupt program execution, with checked exceptions requiring explicit handling or declaration, while unchecked exceptions do not have this requirement and generally indicate programming errors.

5. **What is NullPointerException in Java?**

   A NullPointerException is a runtime exception that occurs in Java when the Java Virtual Machine (JVM) attempts to access an object or call a method on an object that has not been initialized, meaning it is null. This exception indicates that the program is trying to use a reference that points to no location in memory.

   Common scenarios that can lead to a NullPointerException include:

   - Attempting to call a method on a null object reference.
   - Trying to access or modify a field of a null object.
   - Attempting to get the length of an array that is null.
   - Using null in a collection, such as adding a null value to a List.

   To avoid NullPointerExceptions, it is important to ensure that objects are properly initialized before use and to perform null checks where necessary. Additionally, using Java's Optional class can help manage the presence or absence of values more effectively.

6. **What are the types of keywords used in Java exception handling?**

   In Java, there are several keywords that are essential for handling exceptions effectively. These keywords include:

   - **try**: This keyword is used to define a block of code that may throw an exception. The code within the try block is monitored for exceptions.

   - **catch**: This keyword is used to define a block of code that handles the exception thrown by the try block. It follows the try block and specifies the type of exception it can handle.

   - **finally**: This keyword is used to define a block of code that will execute after the try and catch blocks, regardless of whether an exception was thrown or caught. It is typically used for cleanup activities, such as closing resources.

   - **throw**: This keyword is used to explicitly throw an exception from a method or block of code. It can be used to indicate that an error condition has occurred.

   - **throws**: This keyword is used in a method signature to declare that a method can throw one or more exceptions. It informs the caller of the method that they need to handle or declare these exceptions.

   In summary, the keywords try, catch, finally, throw, and throws are fundamental to Java's exception handling mechanism, allowing developers to manage errors and maintain program stability.

7. **What is the difference between throw and throws?**

   | Feature        | throw                                           | throws                                                                   |
   | -------------- | ----------------------------------------------- | ------------------------------------------------------------------------ |
   | Purpose        | Used to explicitly throw an exception           | Used to declare that a method can throw exceptions                       |
   | Usage          | Can be used within any method or block          | Used only in method signatures                                           |
   | Exception Type | Can throw both checked and unchecked exceptions | Can declare checked exceptions only                                      |
   | Control Flow   | Transfers control to the nearest catch block    | Does not transfer control; informs the caller about potential exceptions |
   | Syntax         | `throw new ExceptionType("message");`           | `public void methodName() throws ExceptionType {}`                       |

   In summary, `throw` is used to actually throw an exception, while `throws` is used in a method declaration to indicate that the method may throw exceptions.

8. **What are custom exceptions?**
