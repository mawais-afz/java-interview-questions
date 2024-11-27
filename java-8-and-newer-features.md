# Java 8 & and Newer Features

## Parallel Processing

1.  **What is parallel processing in Java 8?**

    - Parallel processing in Java 8 refers to the ability to execute multiple tasks simultaneously, leveraging multi-core processors to improve performance and efficiency.
    - Java 8 introduced the `ForkJoinPool` framework and the `Stream` API, which allow developers to easily perform parallel operations on collections.
    - By using the `parallelStream()` method, developers can process data in parallel, enabling better resource utilization and faster execution times for large datasets.
    - Example:
      ```java
      List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David");
      names.parallelStream()
           .forEach(name -> System.out.println(name));
      ```
    - This approach can significantly reduce the time taken for operations like filtering, mapping, and reducing when working with large collections.
    - However, it is important to consider thread safety and the overhead of managing multiple threads when using parallel processing.

2.  **What is the difference between a parallel stream and a sequential stream?**

    - **Sequential Stream**:

      - Processes elements sequentially, one at a time
      - Executes operations in a single thread
      - Follows the order of elements in the original collection
      - Suitable for smaller datasets or when order preservation is critical
      - Default stream type when using `.stream()` method
      - Example:
        ```java
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        numbers.stream()
               .filter(n -> n % 2 == 0)
               .forEach(System.out::println);
        ```

    - **Parallel Stream**:

      - Processes elements concurrently across multiple threads
      - Utilizes multiple cores of the processor
      - Breaks the stream into multiple substreams processed in parallel
      - Created using `.parallelStream()` or `.parallel()` method
      - Better performance for large datasets and computationally intensive operations
      - Does not guarantee order of execution
      - Example:
        ```java
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        numbers.parallelStream()
               .filter(n -> n % 2 == 0)
               .forEach(System.out::println);
        ```

    - **Key Differences**:
      1. Performance: Parallel streams are faster for large datasets
      2. Thread Usage: Sequential uses one thread, parallel uses multiple
      3. Order: Sequential maintains order, parallel may not
      4. Overhead: Parallel streams have thread management overhead
      5. Use Case: Choose based on dataset size and computational complexity

3.  **What is difference between External Iteration and Internal Iteration?**

    External iteration and internal iteration represent different approaches to traversing collections in Java.

    External Iteration:

    ```java
    // Using for loop (external iteration)
    List<String> list = Arrays.asList("A", "B", "C");
    for (String item : list) {
        System.out.println(item);
    }
    ```

    Internal Iteration:

    ```java
    // Using Stream API (internal iteration)
    List<String> list = Arrays.asList("A", "B", "C");
    list.stream().forEach(System.out::println);
    ```

    Key differences:

    - Control: External iteration gives explicit control to the programmer (what and how to iterate), while internal iteration handles the iteration details internally
    - Parallelization: Internal iteration can be easily parallelized (using parallelStream()), while external iteration requires manual thread management
    - Performance: Internal iteration can optimize the iteration process as it controls the iteration strategy
    - Readability: Internal iteration often leads to more declarative and readable code
    - Memory usage: External iteration typically uses less memory as it doesn't create intermediate objects

    Common use cases:

    - Use external iteration for simple, sequential operations where explicit control is needed
    - Use internal iteration for complex operations, potential parallelization, or when working with streams

## Optional

4.  **What is Optional and How Does It Help Manage Null Values?**

    - The `Optional` class is a container object introduced in Java 8 to provide a more robust and expressive way of handling potential null values

    - **Core Purpose**: Eliminate null pointer exceptions by making null handling explicit and intentional

    - **Key Problems It Solves**:

      1. Reduces the need for repetitive null checks
      2. Makes potential absence of values clear in method signatures
      3. Encourages defensive programming practices
      4. Provides functional-style operations for handling potentially null values

    - **Main Benefits**:
      - Explicit representation of optional values
      - Safer value retrieval mechanisms
      - Functional programming support for nullable values
      - Improved code readability and intent

5.  **What is the purpose of the Optional class?**

    - The `Optional` class is a container object introduced in Java 8 to help handle potential null values more elegantly and reduce null pointer exceptions

    - **Key Purposes**:

      1. **Explicit Null Handling**: Provides a clear way to represent the possibility of a value being absent
      2. **Avoid Null Checks**: Reduces boilerplate code for null checking
      3. **Functional Programming**: Enables functional-style operations on potentially null values
      4. **Improved Code Readability**: Makes the potential absence of a value explicit in method signatures

    - **Main Benefits**:

      - Encourages developers to explicitly consider and handle potential null scenarios
      - Provides methods like `isPresent()`, `orElse()`, `orElseGet()`, and `map()` for safe value manipulation
      - Helps prevent null pointer exceptions by forcing explicit handling of potentially absent values

    - **Example Usage**:

      ```java
      // Without Optional
      String name = getName();
      if (name != null) {
          System.out.println(name.toUpperCase());
      }

      // With Optional
      Optional<String> optionalName = Optional.ofNullable(getName());
      optionalName.ifPresent(name -> System.out.println(name.toUpperCase()));
      ```

    - **Best Practices**:
      1. Use as return types for methods that might not return a value
      2. Avoid using `Optional` for method parameters
      3. Do not use `Optional.get()` without checking `isPresent()`
      4. Prefer `orElse()`, `orElseGet()`, or `orElseThrow()` for default value handling

6.  **What is the difference between Optional.empty(), Optional.of(value), and Optional.ofNullable(value)?**

    | Method                       | Description                                                   | Behavior with Null                | Use Case                                              |
    | ---------------------------- | ------------------------------------------------------------- | --------------------------------- | ----------------------------------------------------- |
    | `Optional.empty()`           | Creates an empty Optional instance with no value              | Always returns an empty Optional  | When you want to explicitly represent no value        |
    | `Optional.of(value)`         | Creates an Optional with a non-null value                     | Throws NullPointerException       | When you are certain the value is NOT null            |
    | `Optional.ofNullable(value)` | Creates an Optional that may contain a null or non-null value | Returns an empty Optional if null | When the value might be null and you want flexibility |

    **Example**:

    ```java
    Optional<String> emptyOpt = Optional.empty();  // Empty Optional
    Optional<String> presentOpt = Optional.of("Hello");  // Optional with "Hello"
    Optional<String> nullableOpt = Optional.ofNullable(null);  // Empty Optional
    Optional<String> nullableOpt2 = Optional.ofNullable("World");  // Optional with "World"
    ```

## Lambda Expressions

8.  **What is a Lambda and its Shorthand Forms with code examples?**

    - **Lambda Definition**: A lambda expression is a concise way to represent an anonymous function in Java. It was introduced in Java 8 and enables functional programming by allowing functions to be passed as arguments and stored in variables.
    - **Basic Syntax**: `(parameters) -> { expressions }`
    - **Shorthand Forms**:

      1. **Single Expression**: Omit curly braces and return
         ```java
         // Basic form
         x -> { return x * 2; }
         // Shorthand
         x -> x * 2
         ```
      2. **Single Parameter**: Omit parentheses
         ```java
         // Basic form
         (name) -> name.toUpperCase()
         // Shorthand
         name -> name.toUpperCase()
         ```
      3. **Method References**: Use :: operator

         ```java
         // Basic form
         str -> str.length()
         // Method reference
         String::length

         // Basic form
         (obj, str) -> obj.equals(str)
         // Method reference
         Object::equals
         ```

      4. **Type Inference**: Skip parameter types
         ```java
         // Basic form
         (Integer a, Integer b) -> a.compareTo(b)
         // With type inference
         (a, b) -> a.compareTo(b)
         ```

9.  **What are lambda expressions?**

    Lambda expressions are a key feature introduced in Java 8 that provide a concise way to represent anonymous functions or closures. They enable functional programming paradigms in Java by allowing developers to treat functions as first-class citizens.

    - **Definition**: A lambda expression is a short block of code which takes in parameters and returns a value
    - **Syntax**: `(parameters) -> { body }`

    - **Key Characteristics**:

      1. Enables writing inline methods without declaring a separate method
      2. Supports functional programming concepts
      3. Can be passed as arguments to methods
      4. Reduces boilerplate code compared to anonymous inner classes

    - **Basic Syntax Examples**:

      ```java
      // No parameters
      Runnable noArgLambda = () -> System.out.println("Hello, Lambda!");

      // Single parameter
      Consumer<String> singleParamLambda = (name) -> System.out.println("Hello, " + name);

      // Multiple parameters
      Comparator<Integer> multiParamLambda = (a, b) -> a - b;

      // Lambda with multiple statements
      Predicate<String> complexLambda = (str) -> {
          if (str == null) return false;
          return str.length() > 5;
      };
      ```

    - **Use Cases**:

      1. Implementing functional interfaces
      2. Enabling functional-style operations on collections
      3. Simplifying event handling and callback mechanisms
      4. Supporting stream operations

    - **Benefits**:
      - More readable and concise code
      - Enables functional programming techniques
      - Supports lazy evaluation
      - Improves code maintainability

10. **What variables do lambda expressions have access to?**

    Lambda expressions can access variables from their enclosing scope:

        1. Instance variables and static variables of the enclosing class
        2. Parameters of the enclosing method
        3. Final or effectively final local variables

    - **Variable Scope Rules**:

      - Local variables must be final or effectively final
      - Instance/static variables can be modified
      - Parameters of the lambda expression itself can be modified

    - **Example**:

      ```java
      class Example {
          private int instanceVar = 1;  // Instance variable - accessible

          void method() {
              final int finalVar = 2;   // Final local variable - accessible
              int effectivelyFinal = 3; // Effectively final - accessible
              int mutable = 4;          // Mutable - NOT accessible

              Runnable lambda = () -> {
                  System.out.println(instanceVar);    // OK
                  System.out.println(finalVar);       // OK
                  System.out.println(effectivelyFinal); // OK
                  // System.out.println(mutable);     // Compilation error
              };
          }
      }
      ```

11. **What is the difference between a lambda expression and a method reference?**

    | Aspect      | Lambda Expression                                  | Method Reference                                         |
    | ----------- | -------------------------------------------------- | -------------------------------------------------------- |
    | Definition  | An inline implementation of a functional interface | A shorthand notation for calling an existing method      |
    | Syntax      | `(parameters) -> { body }`                         | `ClassName::methodName`                                  |
    | Complexity  | Can contain multiple statements and complex logic  | Directly references an existing method                   |
    | Flexibility | More flexible, can write custom inline logic       | Less flexible, limited to existing method implementation |
    | Use Case    | When you need custom, inline implementation        | When you want to use an existing method directly         |
    | Example     | `(x, y) -> x + y`                                  | `Integer::sum`                                           |
    | Performance | Slightly more overhead                             | Typically more lightweight                               |
    | Readability | More verbose for simple operations                 | More concise for straightforward method calls            |

## Method References

10. **What is a method reference?**

    Method references are a feature introduced in Java 8 that provide a way to refer to methods or constructors without invoking them. They serve as a more concise alternative to certain lambda expressions.

    - **Definition**: A method reference is a compact syntax for referring to an existing method by name
    - **Syntax**: `ContainingClass::methodName`

    - **Key Characteristics**:

      1. Acts as shorthand for lambda expressions that only call a single method
      2. Makes code more readable when the lambda would just delegate to an existing method
      3. Can reference static methods, instance methods, or constructors
      4. Must be compatible with the functional interface being implemented

    - **Basic Examples**:

      ```java
      // Static method reference
      Function<String, Integer> parser = Integer::parseInt;

      // Instance method reference
      String str = "hello";
      Supplier<Integer> lengthFn = str::length;

      // Constructor reference
      Supplier<List<String>> listMaker = ArrayList::new;
      ```

    - A shorthand notation for calling an existing method
    - Syntax: `ClassName::methodName`

11. **What are the different types of method references?**

    There are four types of method references in Java:

    1. **Static Method Reference**:

       - Syntax: `ClassName::staticMethodName`
       - Example: `Math::abs`

    2. **Instance Method Reference of a Particular Object**:

       - Syntax: `objectInstance::instanceMethodName`
       - Example: `str::length`

    3. **Instance Method Reference of an Arbitrary Object of a Particular Type**:

       - Syntax: `ClassName::instanceMethodName`
       - Example: `String::compareToIgnoreCase`

    4. **Constructor Reference**:
       - Syntax: `ClassName::new`
       - Example: `ArrayList::new`

    **Example Usage**:

    ```java
    // Static method reference
    Function<Integer, Integer> abs = Math::abs;

    // Instance method reference of particular object
    String str = "Hello";
    Supplier<Integer> length = str::length;

    // Instance method reference of arbitrary object
    Comparator<String> comp = String::compareToIgnoreCase;

    // Constructor reference
    Supplier<List<String>> listFactory = ArrayList::new;
    ```

12. **What are Method References and Constructor References?**

    - A shorthand syntax for lambda expressions that refer to existing methods
    - Provides a more concise way to create functional interface implementations
    - Four types of method references:

      1. **Reference to a Static Method**:

         - Syntax: `ClassName::staticMethodName`
         - Example: `Function<String, Integer> parseInt = Integer::parseInt`

      2. **Reference to an Instance Method of a Particular Object**:

         - Syntax: `objectReference::instanceMethodName`
         - Example: `Consumer<String> printer = System.out::println`

      3. **Reference to an Instance Method of an Arbitrary Object of a Particular Type**:

         - Syntax: `ClassName::instanceMethodName`
         - Example: `Comparator<String> compareByLength = String::length`

      4. **Constructor Reference**:
         - Syntax: `ClassName::new`
         - Creates a new instance of a class
         - Example: `Supplier<List<String>> listCreator = ArrayList::new`

    - Simplifies lambda expressions when a method already exists
    - Improves code readability and reduces boilerplate

## Type System Enhancements

16. **What is Repeatable Annotations?**

    - A feature introduced in Java 8 that allows the same annotation to be applied multiple times to a single declaration or type
    - Before Java 8, multiple annotations of the same type were not allowed on a single element

17. **How to Use Repeatable Annotations?**

    1. Create a container annotation that will hold multiple instances of the repeatable annotation
    2. Mark the original annotation with `@Repeatable` annotation
    3. Specify the container annotation type

    - **Example**:

      ```java
      // Repeatable annotation
      @Repeatable(RolesContainer.class)
      @Retention(RetentionPolicy.RUNTIME)
      @interface Role {
          String name();
      }

      // Container annotation
      @Retention(RetentionPolicy.RUNTIME)
      @interface RolesContainer {
          Role[] value();
      }

      // Usage
      @Role(name = "ADMIN")
      @Role(name = "USER")
      public class User {
          // Class implementation
      }
      ```

    - **Benefits**:
      - Provides more flexibility in annotation usage
      - Allows multiple annotations of the same type on a single element
      - Improves code readability and expressiveness

18. **What are Annotations on Data Types?**:

    - Java 8 introduced an enhanced annotation system that allows annotations to be applied directly to types
    - This feature enables more precise type checking and provides additional metadata about types
    - Annotations can now be placed on:

      - Class declarations
      - Method return types
      - Variable declarations
      - Type parameters
      - Type uses

    - **Key Characteristics**:

      - Provides more granular type information
      - Supports type-level metadata and constraints
      - Enhances compile-time and runtime type checking

    - **Examples**:

      ```java
      // Annotation on a method return type
      public @NonNull String processData() {
          return "Result";
      }

      // Annotation on a variable
      @Nullable String userInput = null;

      // Annotation on a type parameter
      public <@NotEmpty T> List<T> filterList(List<T> input) {
          return input.stream()
                      .filter(item -> item != null)
                      .collect(Collectors.toList());
      }
      ```

    - **Benefits**:
      - Improves code quality through more explicit type declarations
      - Enables more sophisticated static analysis
      - Supports custom type-level validations
      - Enhances documentation and type safety
    - Java 8 introduced the ability to apply annotations to types (classes, interfaces, enums)
    - This allows for more declarative and concise code
    - Example:
      ```java
      @FunctionalInterface
      public interface MyFunctionalInterface<T> {
          boolean process(T input);
      }
      ```

19. **What is Type Inference in Java 8?**

    Type inference is a feature in Java 8 that allows the compiler to automatically determine the type of variables and expressions based on their context, reducing verbosity in code. The most notable enhancement was made to support lambda expressions and method references.

    Example:

    ```java
    // Before Java 8 - explicit type declaration
    List<String> list = new ArrayList<String>();

    // With Java 8 type inference - diamond operator
    List<String> list = new ArrayList<>();

    // Type inference in lambda expressions
    Predicate<String> isEmpty = s -> s.isEmpty(); // Type of 's' is inferred
    Function<Integer, String> toString = x -> x.toString(); // Types inferred

    // Type inference with method references
    List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
    names.sort(String::compareToIgnoreCase); // Types inferred from context
    ```

    Key points:

    - Reduces boilerplate code while maintaining type safety
    - Particularly useful with generic types and lambda expressions
    - Enhanced compiler can infer types from context
    - Diamond operator (<>) for generic type inference
    - Works with local variables, lambda parameters, and generic methods

## Java Reflection API

1. **What is Java Reflection API?**

   - Java Reflection API allows programs to examine and modify the behavior of classes, interfaces, fields and methods at runtime
   - It provides the ability to inspect and manipulate class information dynamically
   - Key capabilities include:

     - Examining class structure and metadata
     - Creating new instances of classes
     - Accessing and modifying fields
     - Invoking methods dynamically
     - Working with annotations

   - **Common Use Cases**:

     - Dependency injection frameworks
     - Unit testing frameworks
     - Serialization/deserialization
     - Dynamic proxy creation
     - Plugin architectures

   - **Example**:

     ```java
     // Get class information
     Class<?> clazz = MyClass.class;

     // Create new instance
     Object obj = clazz.getDeclaredConstructor().newInstance();

     // Get and invoke method
     Method method = clazz.getDeclaredMethod("myMethod", String.class);
     method.invoke(obj, "parameter");

     // Access private field
     Field field = clazz.getDeclaredField("privateField");
     field.setAccessible(true);
     field.set(obj, "new value");
     ```

   - **Considerations**:
     - Can impact performance due to runtime overhead
     - May break encapsulation if not used carefully
     - Should be used judiciously and only when necessary
     - Requires security considerations in production code

2. **What is Reflection for Method Parameters?**

   - Java 8 introduced enhanced method parameter reflection capabilities
   - Before Java 8, method parameter names were not readily available at runtime
   - The new `java.lang.reflect.Parameter` class provides detailed information about method parameters

   - **Key Features**:

     - Ability to retrieve parameter names at runtime
     - Access to parameter modifiers and annotations
     - More comprehensive introspection of method signatures

   - **Example**:

     ```java
     public void exampleMethod(String firstName, @Deprecated int age) {
         Method method = this.getClass().getMethod("exampleMethod", String.class, int.class);
         Parameter[] parameters = method.getParameters();

         for (Parameter param : parameters) {
             System.out.println("Parameter Name: " + param.getName());
             System.out.println("Is Deprecated: " + param.isAnnotationPresent(Deprecated.class));
         }
     }
     ```

   - **How to Enable Parameter Names**:

     - Compile with the `-parameters` flag
     - Allows preservation of actual parameter names during compilation
     - Without this flag, parameters will have synthetic names like `arg0`, `arg1`

   - **Benefits**:
     - Improved debugging and logging
     - Enhanced framework and library support
     - More powerful reflection capabilities
     - Better support for dependency injection and serialization frameworks

3. **What is the importance of reflection in Java?**

   - Reflection enables runtime inspection and modification of classes, methods, and fields
   - Allows programs to examine and interact with components dynamically at runtime
   - Critical for many frameworks and libraries like Spring, Hibernate, JUnit

   - **Key Use Cases**:
     - Framework development and dependency injection
     - Unit testing frameworks
     - Object-relational mapping (ORM)
     - Serialization/deserialization
     - Dynamic proxy creation
   - **Core Capabilities**:
     - Inspect class structure and metadata
     - Create new instances dynamically
     - Access and modify private members
     - Invoke methods programmatically
     - Load classes at runtime
   - **Example**:

     ```java
     // Get class information
     Class<?> clazz = obj.getClass();

     // Create new instance
     Object newInstance = clazz.newInstance();

     // Invoke method dynamically
     Method method = clazz.getMethod("methodName", paramTypes);
     method.invoke(obj, args);
     ```

   - **Considerations**:
     - Performance overhead due to dynamic nature
     - Security implications when accessing private members
     - Can break encapsulation if not used carefully
     - Should be used judiciously where static alternatives exist

## Array Operations

22. **What is Parallel Sorting of Arrays?**

    - Java 8 introduced parallel sorting methods for arrays to improve performance on multi-core processors
    - Provides built-in parallel sorting capabilities for primitive and object arrays
    - Utilizes the Fork/Join framework for efficient parallel processing

    - **Key Methods**:

      - `Arrays.parallelSort()` for various array types
      - Works with primitive arrays (int, long, double, etc.)
      - Also supports object arrays with natural ordering or custom comparators

    - **Example**:

      ```java
      int[] numbers = {5, 2, 9, 1, 7, 6, 3};
      Arrays.parallelSort(numbers);  // Sorts the array in parallel

      // Custom comparator parallel sort
      String[] names = {"Alice", "Bob", "Charlie", "David"};
      Arrays.parallelSort(names, Comparator.reverseOrder());
      ```

    - **Performance Considerations**:

      - Most beneficial for large arrays
      - Overhead of parallel processing may not be worth it for small arrays
      - Performance depends on the number of available processor cores

    - **Benefits**:
      - Faster sorting for large datasets
      - Automatic utilization of multi-core processors
      - Simple, one-method approach to parallel sorting
      - No need to manually implement parallel sorting logic

## Stream API

23. **What is Stream?**

    - A sequence of elements supporting sequential and parallel aggregate operations
    - Introduced in Java 8 as part of the Stream API
    - Provides a modern way to process data in a declarative manner

    - **Key Concepts**:

      - Not a data structure but a view of data
      - Supports functional-style operations
      - Can be created from Collections, Arrays, I/O operations
      - Designed for lambda expressions and method references

    - **Example**:

      ```java
      List<String> myList = Arrays.asList("a", "b", "c");
      Stream<String> myStream = myList.stream();
      myStream.filter(s -> s.startsWith("a"))
             .forEach(System.out::println);
      ```

    - **Types of Streams**:
      - Sequential streams (default)
      - Parallel streams (for concurrent processing)
      - Primitive streams (IntStream, LongStream, DoubleStream)
      - Infinite streams (generated streams)

24. **What are the benefits of using Streams?**

    - Provides a more concise and readable way to process collections
    - Enables functional-style programming in Java
    - Supports easy parallel processing of data
    - Reduces boilerplate code for collection manipulation
    - Allows for lazy evaluation of operations
    - Facilitates complex data transformations with minimal code
    - Improves performance for large datasets through parallel processing
    - Promotes immutability and functional programming principles
    - Integrates seamlessly with lambda expressions and method references
    - Offers a wide range of built-in operations like filter, map, reduce

25. **What is the purpose of the Stream API?**

    - The Stream API is a powerful feature introduced in Java 8 that provides a functional approach to processing collections of objects

    - **Key Purposes**:

      1. **Declarative Data Processing**: Allows processing collections in a more declarative and functional style
      2. **Parallel Processing**: Enables easy parallel processing of data with minimal code changes
      3. **Functional Transformations**: Provides methods for filtering, mapping, reducing, and collecting data
      4. **Lazy Evaluation**: Supports lazy evaluation, processing elements only when needed

    - **Main Benefits**:

      - Simplifies complex data manipulation operations
      - Reduces boilerplate code for collection processing
      - Improves code readability and expressiveness
      - Supports both sequential and parallel data processing

    - **Core Stream Operations**:

      - `filter()`: Selects elements based on a predicate
      - `map()`: Transforms elements
      - `reduce()`: Combines elements into a single result
      - `collect()`: Gathers results into a collection
      - `forEach()`: Performs an action on each element

    - **Example Usage**:

      ```java
      // Traditional approach
      List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
      List<String> filteredNames = new ArrayList<>();
      for (String name : names) {
          if (name.startsWith("A")) {
              filteredNames.add(name.toUpperCase());
          }
      }

      // Stream API approach
      List<String> streamFilteredNames = names.stream()
          .filter(name -> name.startsWith("A"))
          .map(String::toUpperCase)
          .collect(Collectors.toList());
      ```

    - **Best Practices**:
      1. Use streams for complex data transformations
      2. Prefer method references when possible
      3. Close streams after use, especially with I/O operations
      4. Be mindful of performance for large collections

26. **What is the Stream API in Java 8?**

    - A functional approach to processing collections of objects
    - Enables declarative and functional-style operations on collections
    - Supports parallel and sequential processing of data

    - **What are the key characteristics of Java Streams?**
      1. Functional in nature
      2. Not a data structure
      3. Do not modify the original data source
      4. Lazily evaluated
      5. Can be processed sequentially or in parallel

27. **What are the main operations in Stream API?**

    1. **Intermediate Operations**:

       - `filter()`: Filters elements based on a predicate
       - `map()`: Transforms elements
       - `flatMap()`: Flattens nested streams
       - `sorted()`: Sorts stream elements
       - `distinct()`: Removes duplicate elements
       - `limit()`: Limits the number of elements
       - `skip()`: Skips first n elements

    2. **Terminal Operations**:
       - `collect()`: Collects stream elements into a collection
       - `forEach()`: Performs an action on each element
       - `reduce()`: Reduces stream to a single value
       - `count()`: Counts number of elements
       - `min()` and `max()`: Find minimum and maximum
       - `anyMatch()`: Checks if any element matches a predicate
       - `allMatch()`: Checks if all elements match a predicate
       - `noneMatch()`: Checks if no elements match a predicate

28. **What is the difference between `map()` and `flatMap()`?**

    ```java
    // map(): One-to-One transformation
    List<String> names = list.stream()
                              .map(String::toUpperCase)
                              .collect(Collectors.toList());

    // flatMap(): One-to-Many transformation
    List<Integer> numbers = listOfLists.stream()
                                       .flatMap(List::stream)
                                       .collect(Collectors.toList());
    ```

29. **What are the different ways to create a Stream in Java?**

    There are several ways to create a Stream in Java:

    1. **From Collections**:

       - Using `collection.stream()`
       - Using `collection.parallelStream()`

    2. **From Arrays**:

       - Using `Arrays.stream(array)`
       - Using `Stream.of(array)`

    3. **From Static Factory Methods**:

       - Using `Stream.of(elements)`
       - Using `Stream.empty()`

    4. **From Builders**:

       - Using `Stream.builder()`

    5. **Infinite/Generated Streams**:

       - Using `Stream.iterate()`
       - Using `Stream.generate()`

    6. **From Other Sources**:

       - From Files: `Files.lines(path)`
       - From Strings: `"string".chars()`
       - From Regular Expressions: `Pattern.compile().splitAsStream()`

    7. **Primitive Streams**:
       - `IntStream`, `LongStream`, `DoubleStream`
       - Range-based: `IntStream.range(1, 100)`

30. **What is the difference between `findFirst()` and `findAny()`?**

    - `findFirst()`: Returns first element in a sequential stream
    - `findAny()`: Returns any element, useful in parallel streams

    ```java
    Optional<String> first = stream.findFirst();
    Optional<String> any = parallelStream.findAny();
    ```

31. **How to perform grouping and partitioning with Streams?**

    ```java
    // Grouping
    Map<String, List<Employee>> byDepartment =
        employees.stream()
                 .collect(Collectors.groupingBy(Employee::getDepartment));

    // Partitioning
    Map<Boolean, List<Employee>> partitioned =
        employees.stream()
                 .collect(Collectors.partitioningBy(e -> e.getSalary() > 50000));
    ```

    - **Performance Considerations**:

      - Use parallel streams for large datasets
      - Avoid modifying source collection during stream operations
      - Be cautious of boxing/unboxing overhead
      - Consider primitive streams for performance

    - **Common Pitfalls**:
      1. Streams can be consumed only once
      2. Avoid complex lambda expressions
      3. Be mindful of stateful intermediate operations
      4. Consider performance overhead of parallel streams
      ```java
      // Incorrect: Stream already consumed
      Stream<String> stream = list.stream();
      stream.forEach(System.out::println);
      stream.count(); // IllegalStateException
      ```

32. **What is the difference between Collection and Stream?**

    Key differences between Collection and Stream:

    - **Storage vs Computation**:

      - Collection is a data structure that stores elements
      - Stream is a pipeline for computing on elements

    - **State**:

      - Collections maintain state of elements
      - Streams don't store elements, they process elements on-the-fly

    - **Consumption**:

      - Collections can be accessed multiple times
      - Streams can only be consumed once

    - **Iteration**:
      - Collections use external iteration (explicit loops)
      - Streams use internal iteration (hidden from developer)

    ```java
    // Collection example
    List<String> list = Arrays.asList("a", "b", "c");
    for(String s : list) { // External iteration
        System.out.println(s);
    }

    // Stream example
    list.stream()
        .filter(s -> s.equals("a")) // Internal iteration
        .forEach(System.out::println);
    ```

33. **What is the method collect() for in streams?**

    The collect() method is a terminal operation in streams that transforms a stream into a Collection or other data structure. It's used to:

    - Accumulate stream elements into a collection
    - Group elements
    - Partition elements
    - Generate summaries

    ```java
    // Basic collection examples
    List<String> list = stream.collect(Collectors.toList());
    Set<String> set = stream.collect(Collectors.toSet());

    // More complex collection examples
    Map<String, List<Person>> peopleByCity =
        people.stream()
             .collect(Collectors.groupingBy(Person::getCity));

    String joined = stream.collect(Collectors.joining(", "));
    ```

    Common collectors from Collectors class:

    - toList(), toSet(), toMap()
    - joining()
    - groupingBy()
    - partitioningBy()
    - summarizingInt/Long/Double()

34. **Why do streams use forEach() and forEachOrdered() methods?**

    The forEach() and forEachOrdered() are terminal operations in streams that serve different purposes:

    - **forEach()**:
      - Performs an action on each element with no guaranteed order
      - Better performance for parallel streams since order doesn't matter
      - Used when element processing order is not important

    ```java
    list.parallelStream()
        .forEach(item -> System.out.println(item)); // Order not guaranteed
    ```

    - **forEachOrdered()**:
      - Processes elements in the encounter order of the stream
      - Maintains original sequence even in parallel streams
      - Used when order preservation is important

    ```java
    list.parallelStream()
        .forEachOrdered(item -> System.out.println(item)); // Order preserved
    ```

35. **What are map(), mapToInt(), mapToDouble() and mapToLong() methods in Stream?**

    These are intermediate operations in streams that transform elements:

    - **map()**:
      - Transforms each element into another object using the given function
      - Returns a Stream of the transformed elements
      - Most general mapping method that works with any type

    ```java
    List<String> names = people.stream()
                              .map(Person::getName)
                              .collect(Collectors.toList());
    ```

    - **mapToInt(), mapToLong(), mapToDouble()**:
      - Specialized mapping methods that transform elements into primitive streams
      - Return IntStream, LongStream, and DoubleStream respectively
      - Provide additional numeric operations like sum(), average(), etc.

    ```java
    int totalAge = people.stream()
                        .mapToInt(Person::getAge)
                        .sum();

    double averageSalary = employees.stream()
                                  .mapToDouble(Employee::getSalary)
                                  .average()
                                  .orElse(0.0);
    ```

36. **What is the purpose of filter() method in streams?**

    The filter() method is an intermediate operation that:

    - Selects elements from a stream that match a given predicate
    - Returns a new stream containing only the elements that satisfy the condition
    - Allows for filtering out unwanted elements based on custom criteria

    ```java
    // Example of filtering even numbers
    List<Integer> evenNumbers = numbers.stream()
                                     .filter(n -> n % 2 == 0)
                                     .collect(Collectors.toList());

    // Example of filtering by complex condition
    List<Person> adults = people.stream()
                               .filter(person -> person.getAge() >= 18)
                               .filter(person -> person.hasValidID())
                               .collect(Collectors.toList());
    ```

37. **What is the use of limit() method in streams?**

    The limit() method is an intermediate operation that:

    - Restricts the stream to a maximum number of elements
    - Returns a new stream with at most the specified number of elements
    - Useful for processing just a portion of a stream or implementing pagination

    ```java
    // Example of limiting to first 5 elements
    List<Integer> firstFive = numbers.stream()
                                   .limit(5)
                                   .collect(Collectors.toList());

    // Example of combining with other operations
    List<Person> topThreeEarners = employees.stream()
                                          .sorted((e1, e2) -> Double.compare(e2.getSalary(), e1.getSalary()))
                                          .limit(3)
                                          .collect(Collectors.toList());
    ```

38. **What is the use of sorted() method in streams?**

    The sorted() method is an intermediate operation that:

    - Orders the elements of a stream according to natural order or a custom comparator
    - Returns a new stream containing all elements sorted in the specified order
    - Can be used with both natural ordering (Comparable) and custom Comparator

    ```java
    // Example of natural ordering
    List<String> sortedNames = names.stream()
                                   .sorted()
                                   .collect(Collectors.toList());

    // Example of custom comparator
    List<Person> sortedByAge = people.stream()
                                    .sorted((p1, p2) -> p1.getAge() - p2.getAge())
                                    .collect(Collectors.toList());

    // Example using Comparator methods
    List<Employee> sortedBySalary = employees.stream()
                                            .sorted(Comparator.comparing(Employee::getSalary).reversed())
                                            .collect(Collectors.toList());
    ```

39. **What are the flatMap(), flatMapToInt(), flatMapToDouble(), and flatMapToLong() methods in streams?**

    The flatMap methods are intermediate operations that:

    - Transform each element of a stream into a stream of other elements
    - "Flatten" multiple streams into a single stream
    - Map one-to-many transformations

    Each variant handles different return types:

    - flatMap(): Returns Stream<R> for mapping to object streams
    - flatMapToInt(): Returns IntStream for mapping to primitive int streams
    - flatMapToDouble(): Returns DoubleStream for mapping to primitive double streams
    - flatMapToLong(): Returns LongStream for mapping to primitive long streams

    ```java
    // Example of flatMap with nested lists
    List<List<Integer>> nestedNumbers = Arrays.asList(
        Arrays.asList(1, 2, 3),
        Arrays.asList(4, 5, 6)
    );
    List<Integer> flattenedList = nestedNumbers.stream()
                                              .flatMap(Collection::stream)
                                              .collect(Collectors.toList());
    // Result: [1, 2, 3, 4, 5, 6]

    // Example of flatMapToInt
    List<String> words = Arrays.asList("Hello", "World");
    int[] lengths = words.stream()
                        .flatMapToInt(str -> str.chars())
                        .toArray();
    ```

40. **What are the final methods (terminal operations) of working with streams? Or What are terminal operations on Streams?**

    Terminal operations in streams are methods that produce a result or side-effect and terminate the stream pipeline. The main terminal operations are:

    1. **Collection Operations**:

       - `collect()`: Collects stream elements into a collection or other data structure
       - `toArray()`: Converts stream to an array

    2. **Reduction Operations**:

       - `reduce()`: Reduces stream elements to a single value
       - `count()`: Returns the number of elements in the stream
       - `sum()`: Returns the sum (for numeric streams)
       - `min()`: Finds the minimum element
       - `max()`: Finds the maximum element

    3. **Matching Operations**:

       - `anyMatch()`: Checks if any element matches a predicate
       - `allMatch()`: Checks if all elements match a predicate
       - `noneMatch()`: Checks if no elements match a predicate

    4. **Element Retrieval**:

       - `findFirst()`: Returns first element
       - `findAny()`: Returns any element from the stream

    5. **Iteration and Side-Effect Operations**:
       - `forEach()`: Performs an action on each element
       - `forEachOrdered()`: Performs an action on elements in stream order

    Terminal operations in Java Streams are methods that:

    - Produce a result or a side-effect
    - Terminate the stream pipeline
    - Cannot be followed by any additional stream operations
    - Trigger the processing of elements in the stream

    **Example**:

    ```java
    List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

    // Terminal operations examples
    long count = numbers.stream().count(); // Returns 5
    int sum = numbers.stream().reduce(0, Integer::sum); // Returns 15
    boolean hasEven = numbers.stream().anyMatch(n -> n % 2 == 0); // Returns true
    ```

41. **What are the intermediate operations in streams?**

    Intermediate operations in streams are operations that transform a stream into another stream. The main intermediate operations are:

    1. **Filtering**

       - filter(): Filters elements based on a predicate
       - distinct(): Removes duplicate elements
       - limit(): Limits stream to specified size
       - skip(): Skips specified number of elements

    2. **Mapping/Transformation**

       - map(): Transforms each element
       - mapToInt()/mapToLong()/mapToDouble(): Maps to primitive streams
       - flatMap(): Flattens and maps nested streams
       - flatMapToInt()/flatMapToLong()/flatMapToDouble(): Flattens to primitive streams

    3. **Sorting**

       - sorted(): Sorts elements naturally
       - sorted(Comparator): Sorts using custom comparator

    4. **Peeking**
       - peek(): Performs action on elements without modifying stream

    ```java
    // Examples of intermediate operations
    Stream<T> filtered = stream.filter(predicate);
    Stream<R> mapped = stream.map(function);
    Stream<T> sorted = stream.sorted();
    Stream<T> unique = stream.distinct();
    Stream<T> limited = stream.limit(n);
    ```

    Key characteristics:

    - Lazy evaluation (only executed when terminal operation is called)
    - Can be chained together
    - Don't modify the original stream
    - Return a new stream

42. **Explain Difference between Collection API and Stream API?**

    Key differences between Collection API and Stream API:

    1. **Purpose**

       - Collection API: Focuses on storing and managing groups of elements
       - Stream API: Focuses on performing operations and computations on elements

    2. **Storage vs Processing**

       - Collection: Stores elements in memory
       - Stream: Doesn't store elements; processes them on-the-fly

    3. **Element Access**

       - Collection: Provides direct access to elements
       - Stream: Elements can only be accessed through operations

    4. **Reusability**

       - Collection: Can be traversed multiple times
       - Stream: Can only be traversed once; becomes invalid after use

    5. **Modification**

       - Collection: Elements can be added/removed
       - Stream: Read-only view of data; can't modify source

    6. **Evaluation**

       - Collection: Eager evaluation
       - Stream: Lazy evaluation (only processes when terminal operation called)

    7. **Operations**
       - Collection: Focuses on element manipulation (add, remove, etc.)
       - Stream: Focuses on data processing (map, filter, reduce, etc.)

    ```java
    // Collection example
    List<String> list = new ArrayList<>();
    list.add("item");
    list.remove(0);

    // Stream example
    list.stream()
        .filter(s -> s.length() > 3)
        .map(String::toUpperCase)
        .collect(Collectors.toList());
    ```

## Interface Enhancements

3.  **What are default and static interface methods?**

    - Java 8 introduced two new types of methods in interfaces: default and static methods, which significantly expanded the capabilities of interfaces.

    - **Default Methods**:

      - Allow interfaces to have method implementations without forcing implementing classes to provide the implementation
      - Marked with the `default` keyword
      - Provide backward compatibility when adding new methods to existing interfaces
      - Enable adding new methods to interfaces without breaking existing implementations
      - Example:
        ```java
        interface Greeting {
            default void sayHello() {
                System.out.println("Hello, World!");
            }
        }
        ```

    - **Static Methods**:

      - Can be defined directly in the interface
      - Belong to the interface itself, not to implementing classes
      - Cannot be overridden by implementing classes
      - Useful for providing utility methods related to the interface
      - Example:
        ```java
        interface MathOperations {
            static int add(int a, int b) {
                return a + b;
            }
        }
        ```

    - **Key Characteristics**:
      1. Default methods allow for method implementations in interfaces
      2. Static methods provide utility functions at the interface level
      3. Both enhance interface flexibility and reduce code duplication
      4. Help in creating more modular and maintainable code

4.  **What are static interface methods? How to call static interface method?**

    - Static methods in interfaces were introduced in Java 8
    - They provide utility functionality that belongs to the interface type itself
    - Key characteristics:
      - Must have an implementation (method body)
      - Cannot be overridden by implementing classes
      - Can only be accessed using the interface name
      - Cannot be accessed through implementing class instances
      - Help keep related utility methods together with the interface

    Example:

    ```java
    interface StringUtils {
        // Static utility method
        static boolean isEmpty(String str) {
            return str == null || str.trim().length() == 0;
        }

        // Another static utility method
        static String reverse(String str) {
            return new StringBuilder(str).reverse().toString();
        }
    }

    // Usage
    boolean empty = StringUtils.isEmpty("  ");    // Correct
    String reversed = StringUtils.reverse("hello"); // Correct
    // MyClass.isEmpty("test");  // Wrong - cannot access through implementing class
    ```

5.  **What are default interface methods?**

    - Default methods were introduced in Java 8 to enable interface evolution
    - Allow adding new methods to interfaces without breaking existing implementations
    - Must be declared with the `default` keyword and include a method body
    - Can be overridden by implementing classes
    - Enable multiple inheritance of behavior

    Example:

    ```java
    interface Vehicle {
        // Default method
        default void startEngine() {
            System.out.println("Starting engine...");
        }

        // Abstract method
        void brake();
    }

    // Implementing class can use default method as-is
    class Car implements Vehicle {
        public void brake() {
            System.out.println("Applying brakes");
        }
        // startEngine() is inherited with default implementation
    }

    // Or can override it
    class ElectricCar implements Vehicle {
        public void brake() {
            System.out.println("Applying regenerative braking");
        }

        @Override
        public void startEngine() {
            System.out.println("Powering up electric motor...");
        }
    }
    ```

    Key points:

    - Solve the "diamond problem" through explicit override requirements
    - Cannot override Object class methods
    - Help evolve APIs while maintaining backward compatibility
    - Enable composition of behaviors through multiple interface inheritance

6.  **How to call default interface method in a class that implements this interface?**

    - Default interface methods can be called directly like any other method
    - Can also be accessed using `InterfaceName.super.methodName()`
    - Useful when implementing multiple interfaces with same default method

    Example:

    ```java
    interface Printer {
        default void print() {
            System.out.println("Printing...");
        }
    }

    class DocumentPrinter implements Printer {
        public void process() {
            // Direct call
            print();

            // Using super keyword
            Printer.super.print();
        }

        // Can also override default method
        @Override
        public void print() {
            Printer.super.print(); // Call default implementation
            System.out.println("Document printed");
        }
    }
    ```

    Key points:

    - Direct method calls work like regular instance methods
    - `InterfaceName.super.methodName()` syntax required for:
      - Accessing default method from overridden implementation
      - Disambiguating between multiple inherited default methods
    - Helps maintain clean and flexible code structure

## Functional Interfaces

14. **What are the Functional Interfaces?**

    **Definition**:

    - An interface with a single abstract method (SAM)
    - Designed to be used with lambda expressions and method references
    - Annotated with `@FunctionalInterface` (optional but recommended)

    **Key Built-in Functional Interfaces**:

    1. **Consumer<T>**:

       - Takes an input, performs an action, returns nothing
       - Method: `void accept(T t)`
       - Example: `Consumer<String> printer = s -> System.out.println(s)`

    2. **Supplier<T>**:

       - Provides a value, takes no input
       - Method: `T get()`
       - Example: `Supplier<Double> randomSupplier = () -> Math.random()`

    3. **Predicate<T>**:

       - Takes an input, returns a boolean
       - Method: `boolean test(T t)`
       - Example: `Predicate<String> isLong = s -> s.length() > 5`

    4. **Function<T, R>**:

       - Takes an input, returns a transformed output
       - Method: `R apply(T t)`
       - Example: `Function<String, Integer> lengthFunc = s -> s.length()`

    5. **Comparator<T>**:
       - Compares two objects
       - Method: `int compare(T o1, T o2)`
       - Example: `Comparator<Integer> ascendingOrder = (a, b) -> a - b`

    **Creating Custom Functional Interfaces**:

    ```java
    @FunctionalInterface
    public interface MyFunctionalInterface<T> {
        boolean process(T input);
    }
    ```

    **Benefits**:

    - Enables functional programming in Java
    - Supports lambda expressions
    - Provides standard interfaces for common operations
    - Improves code readability and conciseness

15. **What is a Functional Interface?**

    - A functional interface is an interface that contains exactly one abstract method
    - It can have multiple default or static methods, but must have only one abstract method
    - Used extensively in Java 8+ for lambda expressions and method references
    - Marked with @FunctionalInterface annotation (optional but recommended)

    Example:

    ```java
    @FunctionalInterface
    interface Calculator {
        // Single abstract method
        int calculate(int x, int y);

        // Can have default methods
        default void printInfo() {
            System.out.println("Calculator interface");
        }

        // Can have static methods
        static void about() {
            System.out.println("Calculator utility");
        }
    }

    // Usage with lambda expression
    Calculator addition = (x, y) -> x + y;
    Calculator multiplication = (x, y) -> x * y;
    ```

16. **What are the functional interfaces Function<T,R>, DoubleFunction<R>, IntFunction<R> and LongFunction<R>?**

    These are functional interfaces in the `java.util.function` package for transforming values:

    - `Function<T,R>`: Takes an input of type T and returns a result of type R
    - `DoubleFunction<R>`: Takes a double input and returns a result of type R
    - `IntFunction<R>`: Takes an int input and returns a result of type R
    - `LongFunction<R>`: Takes a long input and returns a result of type R

    Example:

    ```java
    // Function<T,R> example
    Function<String, Integer> strLength = str -> str.length();
    Integer length = strLength.apply("Hello"); // Returns 5

    // DoubleFunction<R> example
    DoubleFunction<String> doubleToStr = d -> String.format("%.2f", d);
    String formatted = doubleToStr.apply(3.14159); // Returns "3.14"

    // IntFunction<R> example
    IntFunction<String> intToHex = i -> Integer.toHexString(i);
    String hex = intToHex.apply(255); // Returns "ff"

    // LongFunction<R> example
    LongFunction<Date> longToDate = l -> new Date(l);
    Date date = longToDate.apply(System.currentTimeMillis());
    ```

    Key points:

    - All are single-method interfaces used for value transformation
    - The specialized versions (Double/Int/Long) avoid boxing/unboxing overhead
    - Can be used with method references and lambda expressions
    - Common in stream operations and functional programming patterns

17. **What are the functional interfaces UnaryOperator<T>, DoubleUnaryOperator, IntUnaryOperator and LongUnaryOperator?**

    These are functional interfaces in the `java.util.function` package for operations that take and return the same type:

    - `UnaryOperator<T>`: Takes an input of type T and returns a result of the same type T
    - `DoubleUnaryOperator`: Takes a double input and returns a double result
    - `IntUnaryOperator`: Takes an int input and returns an int result
    - `LongUnaryOperator`: Takes a long input and returns a long result

    Example:

    ```java
    // UnaryOperator<T> example
    UnaryOperator<String> toUpperCase = str -> str.toUpperCase();
    String result = toUpperCase.apply("hello"); // Returns "HELLO"

    // DoubleUnaryOperator example
    DoubleUnaryOperator square = x -> x * x;
    double squared = square.applyAsDouble(4.0); // Returns 16.0

    // IntUnaryOperator example
    IntUnaryOperator increment = x -> x + 1;
    int incremented = increment.applyAsInt(5); // Returns 6

    // LongUnaryOperator example
    LongUnaryOperator negate = x -> -x;
    long negated = negate.applyAsLong(100L); // Returns -100L
    ```

    Key points:

    - Special case of Function where input and output types are the same
    - Primitive specializations avoid boxing/unboxing overhead
    - Commonly used for transformations that preserve type
    - Can be chained using `compose()` and `andThen()` methods

18. **What are the functional interfaces BinaryOperator<T>, DoubleBinaryOperator, IntBinaryOperator and LongBinaryOperator?**

    These are functional interfaces in the `java.util.function` package that represent operations taking two operands and producing a result of the same type:

    - `BinaryOperator<T>`: Takes two operands of type T and returns a result of type T
    - `DoubleBinaryOperator`: Takes two double operands and returns a double result
    - `IntBinaryOperator`: Takes two int operands and returns an int result
    - `LongBinaryOperator`: Takes two long operands and returns a long result

    Example:

    ```java
    // BinaryOperator<T> example
    BinaryOperator<String> concat = (s1, s2) -> s1 + s2;
    String combined = concat.apply("Hello ", "World"); // Returns "Hello World"

    // DoubleBinaryOperator example
    DoubleBinaryOperator multiply = (x, y) -> x * y;
    double product = multiply.applyAsDouble(4.0, 2.0); // Returns 8.0

    // IntBinaryOperator example
    IntBinaryOperator max = (x, y) -> Math.max(x, y);
    int maximum = max.applyAsInt(10, 5); // Returns 10

    // LongBinaryOperator example
    LongBinaryOperator sum = (x, y) -> x + y;
    long total = sum.applyAsLong(100L, 200L); // Returns 300L
    ```

    Key points:

    - Special case of BiFunction where both inputs and output are the same type
    - Primitive specializations avoid boxing/unboxing overhead
    - Commonly used for reduction operations (like sum, product, max, min)
    - Often used in Stream's reduce() operations

19. **What are the functional interfaces Predicate<T>, DoublePredicate, IntPredicate and LongPredicate?**

    These are functional interfaces in the `java.util.function` package that represent predicates (boolean-valued functions):

    - `Predicate<T>`: Takes an argument of type T and returns a boolean result
    - `DoublePredicate`: Takes a double argument and returns a boolean result
    - `IntPredicate`: Takes an int argument and returns a boolean result
    - `LongPredicate`: Takes a long argument and returns a boolean result

    Example:

    ```java
    // Predicate<T> example
    Predicate<String> isEmpty = str -> str.length() == 0;
    boolean result = isEmpty.test(""); // Returns true

    // DoublePredicate example
    DoublePredicate isPositive = x -> x > 0;
    boolean isPos = isPositive.test(5.5); // Returns true

    // IntPredicate example
    IntPredicate isEven = x -> x % 2 == 0;
    boolean even = isEven.test(4); // Returns true

    // LongPredicate example
    LongPredicate isGreaterThanMillion = x -> x > 1_000_000L;
    boolean large = isGreaterThanMillion.test(2_000_000L); // Returns true
    ```

    Key points:

    - Used for testing conditions and filtering
    - Can be combined using logical operations: and(), or(), negate()
    - Primitive specializations avoid boxing/unboxing overhead
    - Commonly used in Stream's filter() operations

20. **What are the functional interfaces Consumer<T>, DoubleConsumer, IntConsumer and LongConsumer?**

    These are functional interfaces in the `java.util.function` package that represent operations that accept a single input argument and return no result:

    - `Consumer<T>`: Takes an argument of type T and performs some operation
    - `DoubleConsumer`: Takes a double argument and performs some operation
    - `IntConsumer`: Takes an int argument and performs some operation
    - `LongConsumer`: Takes a long argument and performs some operation

    Example:

    ```java
    // Consumer<T> example
    Consumer<String> printer = str -> System.out.println(str);
    printer.accept("Hello World"); // Prints: Hello World

    // DoubleConsumer example
    DoubleConsumer squareAndPrint = x -> System.out.println(x * x);
    squareAndPrint.accept(2.0); // Prints: 4.0

    // IntConsumer example
    IntConsumer factorial = x -> {
        int result = 1;
        for(int i = 1; i <= x; i++) {
            result *= i;
        }
        System.out.println(result);
    };
    factorial.accept(5); // Prints: 120

    // LongConsumer example
    LongConsumer bitCount = x -> System.out.println(Long.bitCount(x));
    bitCount.accept(127L); // Prints: 7
    ```

    Key points:

    - Used for operations that need to consume a value but don't return anything
    - Can be chained using andThen() method
    - Primitive specializations avoid boxing/unboxing overhead
    - Commonly used in Stream's forEach() operations

21. **What are the functional interfaces Supplier<T>, BooleanSupplier, DoubleSupplier, IntSupplier and LongSupplier?**

    These are functional interfaces in the `java.util.function` package that represent suppliers of values:

    - `Supplier<T>`: Takes no arguments and returns a value of type T
    - `BooleanSupplier`: Takes no arguments and returns a boolean value
    - `DoubleSupplier`: Takes no arguments and returns a double value
    - `IntSupplier`: Takes no arguments and returns an int value
    - `LongSupplier`: Takes no arguments and returns a long value

    Example:

    ```java
    // Supplier<T> example
    Supplier<String> uuidSupplier = () -> UUID.randomUUID().toString();
    String uuid = uuidSupplier.get(); // Returns a random UUID string

    // BooleanSupplier example
    BooleanSupplier randomBoolean = () -> Math.random() > 0.5;
    boolean value = randomBoolean.getAsBoolean(); // Returns true or false randomly

    // DoubleSupplier example
    DoubleSupplier piSupplier = () -> Math.PI;
    double pi = piSupplier.getAsDouble(); // Returns 3.141592653589793

    // IntSupplier example
    IntSupplier randomInt = () -> (int)(Math.random() * 100);
    int number = randomInt.getAsInt(); // Returns random int between 0-99

    // LongSupplier example
    LongSupplier timestamp = System::currentTimeMillis;
    long time = timestamp.getAsLong(); // Returns current timestamp
    ```

    Key points:

    - Used for lazy evaluation and providing values on demand
    - No input parameters required
    - Primitive specializations avoid boxing/unboxing overhead
    - Commonly used in Optional's orElseGet() and Stream's generate() methods

## Map Enhancements

52. **What additional methods for working with associative arrays (maps) appeared in Java 8?**

    Java 8 introduced several useful methods for working with Map interfaces:

    ```java
    Map<String, Integer> map = new HashMap<>();

    // putIfAbsent - only puts value if key doesn't exist
    map.putIfAbsent("A", 1); // adds entry
    map.putIfAbsent("A", 2); // does nothing since key exists

    // computeIfAbsent - compute value if key absent
    map.computeIfAbsent("B", key -> key.length()); // computes and adds value

    // computeIfPresent - compute new value if key exists
    map.computeIfPresent("A", (key, val) -> val + 1);

    // compute - compute new value regardless of presence
    map.compute("C", (key, val) -> val == null ? 1 : val + 1);

    // merge - merge value with existing value
    map.merge("D", 1, (oldVal, newVal) -> oldVal + newVal);

    // getOrDefault - get value or default if key absent
    int value = map.getOrDefault("E", 0);

    // forEach - iterate over entries
    map.forEach((key, val) -> System.out.println(key + "=" + val));

    // replaceAll - replace all values using BiFunction
    map.replaceAll((key, val) -> val * 2);

    // remove(key, value) - remove only if key maps to given value
    map.remove("A", 1);

    // replace(key, value) - replace value for key
    map.replace("B", 42);

    // replace(key, oldValue, newValue) - replace only if key maps to oldValue
    map.replace("C", 1, 2);
    ```

    Key benefits:

    - Atomic operations for common map patterns
    - Reduced boilerplate code
    - Thread-safe operations
    - More functional programming style
    - Better handling of null values
    - Improved performance for certain operations

## Base64 Encoding/Decoding

53. **What class appeared in Java 8 for encoding / decoding data?**

    The `Base64` class was introduced in Java 8, providing standard methods for encoding and decoding Base64 data. It offers three main encoding variants:

    - `Base64.getEncoder()` - Standard Base64 encoding
    - `Base64.getUrlEncoder()` - URL-safe Base64 encoding
    - `Base64.getMimeEncoder()` - MIME-style Base64 encoding

    Example usage:

    ```java
    String originalString = "Hello, World!";
    String encodedString = Base64.getEncoder().encodeToString(originalString.getBytes());
    ```

54. **How to create a Base64 encoder and decoder?**

    ```java
    // Creating a Base64 encoder
    Base64.Encoder encoder = Base64.getEncoder();

    // Creating a Base64 decoder
    Base64.Decoder decoder = Base64.getDecoder();

    // Encoding a string
    String originalString = "Hello, World!";
    String encodedString = encoder.encodeToString(originalString.getBytes());

    // Decoding a Base64 encoded string
    byte[] decodedBytes = decoder.decode(encodedString);
    String decodedString = new String(decodedBytes);

    // URL-safe encoder and decoder
    Base64.Encoder urlEncoder = Base64.getUrlEncoder();
    Base64.Decoder urlDecoder = Base64.getUrlDecoder();

    // MIME encoder and decoder
    Base64.Encoder mimeEncoder = Base64.getMimeEncoder();
    Base64.Decoder mimeDecoder = Base64.getMimeDecoder();
    ```
