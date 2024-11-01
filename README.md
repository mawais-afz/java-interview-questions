1. **What is Java?**

   Java is a popular, versatile, and object-oriented programming language known for its "write once, run anywhere" capability. It was developed by Sun Microsystems (now owned by Oracle) in 1995. Java is used for developing a wide range of applications, including desktop, web, mobile, and enterprise software.

2. **List some important features of Java.**

   - **Platform Independence**: Java programs can run on any device that has the Java Virtual Machine (JVM) installed, making them highly portable.
   - **Object-Oriented**: Java follows the object-oriented programming paradigm, which helps in organizing complex programs into simpler, reusable pieces.
   - **Robust and Secure**: Java has strong memory management, exception handling, and security features that make it a reliable and secure language.
   - **Multithreading**: Java supports multithreading, allowing concurrent execution of two or more threads for maximum utilization of CPU.
   - **Automatic Memory Management**: Java uses garbage collection to automatically manage memory, reducing the risk of memory leaks and other related issues.
   - **Rich Standard Library**: Java comes with a comprehensive standard library that provides many useful utilities and frameworks for various tasks.
   - **High Performance**: Java's Just-In-Time (JIT) compiler and efficient runtime environment contribute to its high performance.
   - **Distributed Computing**: Java supports distributed computing through its networking capabilities, making it suitable for developing large-scale distributed applications.
   - **Dynamic and Extensible**: Java is designed to adapt to evolving environments, with features like dynamic class loading and reflection.
   - **Community Support**: Java has a large and active community, providing extensive resources, libraries, and frameworks to support development.

3. **Explain JDK, JRE, and JVM**

   | Component | Full Name                | Description                                                                                                                                                                                                                                          |
   | --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | JDK       | Java Development Kit     | A software development environment used for developing Java applications. It includes the JRE, an interpreter/loader (java), a compiler (javac), an archiver (jar), a documentation generator (javadoc), and other tools needed in Java development. |
   | JRE       | Java Runtime Environment | Provides the minimum requirements for executing a Java application; it consists of the Java Virtual Machine (JVM), core classes, and supporting files.                                                                                               |
   | JVM       | Java Virtual Machine     | An abstract computing machine that enables a computer to run a Java program. It provides a runtime environment in which Java bytecode can be executed, ensuring platform independence.                                                               |

4. **Name the types of memory allocations in Java.**

   In Java, memory is primarily allocated in two areas:

   - **Stack Memory**: Used for static memory allocation and the execution of a thread. It contains method-specific values that are short-lived and references to objects in the heap that are being referred to from the method.
   - **Heap Memory**: Used for dynamic memory allocation for Java objects and JRE classes at runtime. New objects are always created in the heap space, and the memory for these objects is managed by the Java Garbage Collector.

   Additionally, there are other memory areas such as:

   - **Method Area**: Stores class structures like metadata, the constant runtime pool, and the code for methods.
   - **Program Counter (PC) Register**: Contains the address of the Java virtual machine instruction currently being executed.
   - **Native Method Stack**: Contains all the native method information used in the application.

   These memory areas are part of the Java Memory Model which helps in the efficient execution of Java applications.

5. **What is a Java Variable?**

   A Java variable is a named storage location in memory that holds a value of a specific data type. Variables are used to store and manipulate data in a program.

   | Aspect            | Description                                                                                                        |
   | ----------------- | ------------------------------------------------------------------------------------------------------------------ |
   | Definition        | A named container for storing data values                                                                          |
   | Declaration       | Specifies the variable's name and data type                                                                        |
   | Initialization    | Assigns an initial value to the variable                                                                           |
   | Scope             | Determines where the variable can be accessed within the code                                                      |
   | Data Types        | Can be primitive (byte, short, int, long, float, double, boolean, char) or reference (objects, arrays, interfaces) |
   | Naming Convention | Follows camelCase, starts with a letter, $, or \_                                                                  |
   | Example           | `int age = 25;` or `String name = "John";`                                                                         |

6. **What are variable types?**

   | Variable Type          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | Local Variables        | - Declared in methods, constructors, or blocks<br>- Created when the method, constructor or block is entered and destroyed once it exits<br>- No access modifiers can be used<br>- Visible only within the declared method, constructor, or block<br>- No default value, must be declared and initialized before use                                                                                                                                                                                                                          |
   | Instance Variables     | - Declared in a class, but outside a method, constructor or any block<br>- Created when an object is created with the 'new' keyword and destroyed when the object is destroyed<br>- Can use access modifiers<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed directly by calling the variable name inside the class                                                                                           |
   | Class/Static Variables | - Declared with the static keyword in a class, but outside a method, constructor or block<br>- Only one copy per class, regardless of how many objects are created<br>- Created when the program starts and destroyed when the program stops<br>- Can be declared as public/private, final, and static<br>- Visible for all methods, constructors and blocks in the class<br>- Have default values (0 for numbers, false for boolean, null for object references)<br>- Can be accessed by calling with the class name: ClassName.VariableName |

7. **What are data types?**

   Data types in Java specify the type of data that can be stored in a variable. Java has two categories of data types:

   | Category             | Data Types    | Description                                                                                                                                                | Size    |
   | -------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
   | Primitive Data Types | byte          | - 8-bit signed two's complement integer<br>- Minimum value is -128 (-2^7)<br>- Maximum value is 127 (inclusive)(2^7 -1)<br>- Default value is 0<br>        | 1 byte  |
   |                      | short         | - 16-bit signed two's complement integer<br>- Minimum value is -32,768 (-2^15)<br>- Maximum value is 32,767 (inclusive) (2^15 -1)<br>- Default value is 0. | 2 bytes |
   |                      | int           | 32-bit signed two's complement integer                                                                                                                     | 4 bytes |
   |                      | long          | 64-bit signed two's complement integer                                                                                                                     | 8 bytes |
   |                      | float         | Single-precision 32-bit IEEE 754 floating point                                                                                                            | 4 bytes |
   |                      | double        | Double-precision 64-bit IEEE 754 floating point                                                                                                            | 8 bytes |
   |                      | boolean       | true or false                                                                                                                                              | 1 bit   |
   |                      | char          | 16-bit Unicode character                                                                                                                                   | 2 bytes |
   | Reference Data Types | Class objects | User-defined types                                                                                                                                         | Varies  |
   |                      | Array         | Collection of similar data types                                                                                                                           | Varies  |
   |                      | Interface     | Abstract type                                                                                                                                              | N/A     |

   Primitive types are predefined by the language and named by a keyword. Reference data types are created by the programmer and are not defined by the language (except for String).

8. **What is Type Casting (Type Conversion)**

   Type casting is the process of converting a value from one data type to another in Java. There are two types of type casting:

   1. Widening Casting (Implicit) - automatically converting a smaller type to a larger type size
      `byte -> short -> char -> int -> long -> float -> double`

   - **Example**:

   ```java
   byte byteValue = 10;
   int intValue = byteValue; // Widening casting from byte to int
   ```

   1. Narrowing Casting (Explicit) - manually converting a larger type to a smaller size type
      `double -> float -> long -> int -> char -> short -> byte`

   - **Example**:

   ```java
   double doubleValue = 9.78;
   int intValue = (int) doubleValue; // Narrowing casting from double to int
   ```

   Widening casting is done automatically when passing a smaller size type to a larger size type. Narrowing casting must be done manually by placing the type in parentheses in front of the value.

9. **What are Operators? What are the types of Operators?**

   Java operators are symbols that perform operations on variables and values. They allow us to execute various operations such as addition, subtraction, and comparisons. The different types of operators in Java are as follows:

   | Operator Type           | Description                                                                               |
   | ----------------------- | ----------------------------------------------------------------------------------------- |
   | Arithmetic Operators    | Used for mathematical calculations (+, -, \*, /, %, ++, --).                              |
   | Relational Operators    | Used to compare two values (==, !=, >, <, >=, <=, ===, !==).                              |
   | Bitwise Operators       | Operate on bits and perform bit-by-bit operations (&, \|, ^, ~, <<, >>, >>>).             |
   | Logical Operators       | Used to combine multiple boolean expressions (&&, \|\| ,!).                               |
   | Assignment Operators    | Used to assign values to variables (=, +=, -=, \*=, /=, %=, &=, \|=, ^=, <<=, >>=, >>>=). |
   | Miscellaneous Operators | Includes conditional (ternary) operator (`? :`), instanceof operator (`instanceof`).      |

10. **What are loops? What are the types of loops?**

    Loops are control structures that allow you to execute a block of code multiple times, depending on a specified condition. In Java, there are several types of loops that you can use to handle repetitive tasks:

    1. **while loop**: Repeats a statement or a group of statements while a given condition is true. The condition is evaluated before the execution of the loop body.

    2. **for loop**: Executes a sequence of statements multiple times and is typically used when the number of iterations is known beforehand. It includes initialization, condition, and increment/decrement in a single line.

    3. **do...while loop**: Similar to the while loop, but it tests the condition at the end of the loop body, ensuring that the loop body is executed at least once.

    4. **Enhanced for loop (for-each loop)**: Introduced in Java 5, this loop is used to iterate over collections and arrays, simplifying the syntax for traversing elements.

11. **What are Loop Control Statements? What are the types of Loop Control Statements?**

    Loop control statements are used to alter the flow of control in loops. They allow you to manage the execution of loop iterations based on certain conditions. The types of loop control statements in Java include:

    1. **break statement**: Exits the loop immediately, skipping any remaining iterations.
    2. **continue statement**: Skips the current iteration and proceeds to the next iteration of the loop.
    3. **return statement**: Exits from the current method and returns control to the calling method, which can also affect loop execution if used within a loop.

12. **What is Decision Making? What are the types of Decision Making?**

    Decision making in programming refers to the process of making choices based on certain conditions. It allows the program to execute different paths of code based on the evaluation of these conditions. In Java, decision-making is primarily achieved through control statements.

    | Type of Decision Making | Description                                                                            |
    | ----------------------- | -------------------------------------------------------------------------------------- |
    | **if statement**        | Executes a block of code if a specified condition is true.                             |
    | **if-else statement**   | Executes one block of code if the condition is true, and another block if it is false. |
    | **else if statement**   | Allows checking multiple conditions sequentially.                                      |
    | **switch statement**    | Selects one of many code blocks to execute based on the value of a variable.           |

13. **Why is Java not considered to be purely object-oriented?**

    Java is not considered to be purely object-oriented because it supports primitive data types (such as int, char, boolean, byte, short, long, float, and double) that are not objects. In a purely object-oriented language, everything is treated as an object, and all data types would be defined as classes. While Java provides wrapper classes for these primitive types (e.g., Integer for int, Character for char, Boolean for boolean, Byte for byte, Short for short, Long for long, Float for float, and Double for double), the existence of primitives means that Java does not fully adhere to the principles of pure object-oriented programming. Additionally, Java allows for static methods and variables, which are not associated with any object instance, further distinguishing it from purely object-oriented languages.

14. **What is Object Oriented Programming?**

    Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data in the form of fields (often known as attributes or properties) and code in the form of procedures (often known as methods).

15. **What are the pillars of OOP?**

    The four pillars of Object-Oriented Programming (OOP) are:

    1. **Class**: A blueprint for creating objects, defining the properties and behaviors of an object.
    2. **Object**: An instance of a class, created from the class blueprint.
    3. **Encapsulation**: The bundling of data with the methods that operate on that data, restricting direct access to some of the object's components.
    4. **Inheritance**: The mechanism by which one class can inherit the properties and methods of another class, promoting code reuse and the creation of a hierarchical relationship between classes.
    5. **Polymorphism**: The ability of different classes to be treated as instances of the same class through a common interface, allowing for the implementation of methods in different ways.
    6. **Abstraction**: The concept of hiding the complex implementation details and showing only the necessary features of an object, simplifying the interaction with the object.

16. **What are constructors in Java?**

    Constructors in Java are special methods that are called when an object is instantiated. They have the same name as the class and do not have a return type, not even void. Constructors are used to initialize the object's attributes and allocate memory for the object. There are two types of constructors in Java:

    1. **Default Constructor**: A constructor that does not take any parameters. If no constructor is explicitly defined in a class, the Java compiler automatically provides a default constructor.

    2. **Parameterized Constructor**: A constructor that takes parameters to initialize an object with specific values at the time of creation. This allows for more flexibility in object creation.

    Here's an example of a parameterized constructor in Java:

    ```java
    public class ConstructorExample {
        private String name;
        private int age;

        // Parameterized constructor
        public ConstructorExample(String name, int age) {
            this.name = name;
            this.age = age;
        }

        // Default constructor
        public ConstructorExample() {
            this.name = "Unknown";
            this.age = 0;
        }
    }

    In this example, the `ConstructorExample` class has both a parameterized constructor and a default constructor, allowing for different ways to create objects of this class.

    ```

17. **What is a Singleton class in Java?**

    A Singleton class in Java is a design pattern that restricts the instantiation of a class to a single instance. This is useful when exactly one object is needed to coordinate actions across the system. The Singleton pattern ensures that a class has only one instance and provides a global point of access to that instance.

    To implement a Singleton class in Java, you typically follow these steps:

    1. **Private Constructor**: The constructor of the class is made private to prevent instantiation from outside the class.
    2. **Static Instance**: A static variable of the same class is created to hold the single instance of the class.
    3. **Public Static Method**: A public static method is provided to return the instance of the class. This method checks if the instance already exists; if not, it creates a new instance.

    Here’s an example of a Singleton class in Java:

    ```java
    public class Singleton {
        private static Singleton instance;

        private Singleton() {
            // private constructor to prevent instantiation
        }

        public static Singleton getInstance() {
            if (instance == null) {
                instance = new Singleton();
            }
            return instance;
        }
    }
    ```

    In this example, the `Singleton` class has a private constructor, a static instance variable, and a public static method `getInstance()` that provides access to the single instance of the class. This ensures that no more than one instance of the `Singleton` class can exist at any time.

18. **What are wrapper classes in Java?**

    Wrapper classes in Java are used to convert primitive data types into objects. Each primitive type has a corresponding wrapper class that provides a way to use these primitives as objects. This is particularly useful in situations where objects are required, such as in collections like ArrayList. The wrapper classes in Java include:

    - **Integer**: for int
    - **Double**: for double
    - **Character**: for char
    - **Boolean**: for boolean
    - **Byte**: for byte
    - **Short**: for short
    - **Long**: for long
    - **Float**: for float

    Wrapper classes also provide utility methods for converting between types, performing operations, and handling null values. For example, the Integer class has methods for parsing strings into integers and vice versa. By using wrapper classes, you can take advantage of the features of object-oriented programming while still working with primitive data types.

19. **What is encapsulation in Java?**

    Encapsulation is a fundamental concept in object-oriented programming that refers to the practice of enclosing the data (attributes) and methods (functions) that manipulate the data within a single unit, known as a class. In Java, encapsulation is achieved through the use of access modifiers (private, protected, and public), which control the visibility of class members. This mechanism ensures that the internal state of an object is not directly accessible from outside the class, promoting a controlled interface for interaction. By implementing encapsulation, you improve data security, enhance code maintainability, and reduce the likelihood of unintended modifications to an object's state.

    Here's an example of encapsulation in Java:

    ```java
    public class EncapsulationExample {
        private String name;
        private int age;

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }

        public int getAge() {
            return age;
        }

        public void setAge(int age) {
            this.age = age;
        }
    }
    ```

20. **What is inheritance in Java?**

    Inheritance is a fundamental concept in object-oriented programming that allows a class to inherit properties and behaviors from another class. In Java, inheritance is implemented using the extends keyword, which establishes a hierarchical relationship between classes. The subclass (child class) inherits attributes and methods from the superclass (parent class), and can also add its own unique attributes and methods. This mechanism promotes code reuse, simplifies maintenance, and allows for the creation of more specialized classes based on existing ones.

    Here's an example of inheritance in Java:

    ```java
    public class Animal {
        protected String name;

        public Animal(String name) {
            this.name = name;
        }

        public void eat() {
            System.out.println(name + " is eating.");
        }

        public void sleep() {
            System.out.println(name + " is sleeping.");
        }
    }

    public class Dog extends Animal {
        public Dog(String name) {
            super(name);
        }

        public void bark() {
            System.out.println(name + " is barking.");
        }
    }
    ```

    In this example, the `Dog` class inherits the properties and behaviors of the `Animal` class, including the `name` field and the `eat()` and `sleep()` methods. The `Dog` class also adds its own unique behavior, the `bark()` method.

21. **What is polymorphism in Java?**

    Polymorphism is a core concept in object-oriented programming that allows objects of different classes to be treated as instances of a common superclass. In Java, polymorphism is achieved through method overriding and method overloading. Method overriding allows a subclass to provide a specific implementation of a method that is already defined in its parent class, while method overloading enables multiple methods in the same class to have the same name but different parameters, allowing for different behaviors based on the number and type of arguments passed. This flexibility promotes code reusability and simplifies the design of complex systems by allowing objects to take on multiple forms or behaviors.

    Here's an example of polymorphism in Java:

    ```java
    public class Shape {
        public void draw() {
            System.out.println("Drawing a shape.");
        }
    }

    public class Circle extends Shape {
        @Override
        public void draw() {
            System.out.println("Drawing a circle.");
        }
    }

    public class Rectangle extends Shape {
        @Override
        public void draw() {
            System.out.println("Drawing a rectangle.");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Shape circle = new Circle();
            Shape rectangle = new Rectangle();

            circle.draw(); // Outputs: Drawing a circle.
            rectangle.draw(); // Outputs: Drawing a rectangle.
        }
    }
    ```

22. **What is the difference between loose coupling and tight coupling?**

    Loose coupling refers to a design principle in which components or classes are minimally dependent on each other, allowing for greater flexibility and easier maintenance. In a loosely coupled system, changes in one component have little to no impact on others, making it easier to modify or replace parts of the system without affecting the overall functionality.

    On the other hand, tight coupling occurs when components are highly dependent on one another, leading to a more rigid structure. In a tightly coupled system, changes in one component often require changes in others, making the system harder to maintain and adapt over time.

    In summary, loose coupling promotes better modularity and reusability, while tight coupling can lead to increased complexity and reduced flexibility in software design.

    ````java
    	// Example of Loose Coupling
    	interface Animal {
    			void makeSound();
    	}

    	class Dog implements Animal {
    			public void makeSound() {
    					System.out.println("Bark");
    			}
    	}

    	class Cat implements Animal {
    			public void makeSound() {
    					System.out.println("Meow");
    			}
    	}

    	class AnimalSound {
    			public void playSound(Animal animal) {
    					animal.makeSound();
    			}
    	}

    	public class Main {
    			public static void main(String[] args) {
    					Animal dog = new Dog();
    					Animal cat = new Cat();
    					AnimalSound animalSound = new AnimalSound();
    					animalSound.playSound(dog); // Outputs: Bark
    					animalSound.playSound(cat); // Outputs: Meow
    			}
    	}

    	// Example of Tight Coupling
    	class Dog {
    			public void makeSound() {
    					System.out.println("Bark");
    			}
    	}

    	class DogSound {
    			private Dog dog;

    			public DogSound() {
    					dog = new Dog();
    			}

    			public void playSound() {
    					dog.makeSound();
    			}
    	}

    	public class Main {
    			public static void main(String[] args) {
    					DogSound dogSound = new DogSound();
    					dogSound.playSound(); // Outputs: Bark
    			}
    	}
    	```
    ````

23. **What is the difference between cohesion and coupling?**

    | Aspect     | Cohesion                                                                 | Coupling                                                                              |
    | ---------- | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
    | Definition | Measures how closely related the functionalities within a module are.    | Measures the degree of dependence between different modules.                          |
    | Goal       | Aim for high cohesion to ensure that a module is focused and manageable. | Aim for low coupling to enhance module independence and flexibility.                  |
    | Example    | A class that handles all operations related to user authentication.      | A class that directly accesses methods of another class, creating a tight dependency. |

    ```java
    // Example of High Cohesion
    class UserAuthentication {
    	public boolean login(String username, String password) {
    		// Logic for user login
    		return true; // Assume login is successful
    	}

    	public void logout() {
    		// Logic for user logout
    	}

    	public boolean register(String username, String password) {
    		// Logic for user registration
    		return true; // Assume registration is successful
    	}
    }

    // Example of Low Coupling
    class User {
    	private String username;
    	private String password;

    	public User(String username, String password) {
    		this.username = username;
    		this.password = password;
    	}

    	public String getUsername() {
    		return username;
    	}

    	public String getPassword() {
    		return password;
    	}
    }

    class UserService {
    	public void authenticate(User user) {
    		// Logic to authenticate user
    		System.out.println("Authenticating user: " + user.getUsername());
    	}
    }
    ```

24. **What is the difference between abstract class and interface in Java?**

    | Aspect                | Abstract Class                                                                       | Interface                                                                                                               |
    | --------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
    | Definition            | A class that cannot be instantiated and can have both abstract and concrete methods. | A reference type that can contain only constants, method signatures, default methods, static methods, and nested types. |
    | Inheritance           | Supports single inheritance (a class can extend only one abstract class).            | Supports multiple inheritance (a class can implement multiple interfaces).                                              |
    | Method Implementation | Can have both abstract methods (without body) and concrete methods (with body).      | All methods are abstract by default (unless they are default or static methods).                                        |
    | Constructor           | Can have constructors.                                                               | Cannot have constructors.                                                                                               |
    | Access Modifiers      | Can have access modifiers (public, protected, private).                              | All methods are public by default; cannot have access modifiers.                                                        |
    | Use Case              | Used when classes share a common base and behavior.                                  | Used to define a contract that implementing classes must follow.                                                        |

25. **What is the difference between composition, aggregation, and association?**

	| Aspect        | Composition                                                                 | Aggregation                                                                  | Association                                                                  |
	| ------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
	| Definition    | A strong relationship where the child cannot exist independently of the parent. | A weaker relationship where the child can exist independently of the parent. | A general relationship between two classes, where one class uses or interacts with another. |
	| Lifespan      | The child's lifespan is tied to the parent's lifespan.                      | The child can outlive the parent.                                          | The lifespan of the associated objects is independent.                       |
	| Ownership     | The parent owns the child, and the child is part of the parent.            | The parent does not own the child; they can exist separately.              | There is no ownership; it is a loose relationship.                          |
	| Example       | A car and its engine (the engine cannot exist without the car).            | A university and its students (students can exist without the university). | A teacher and a student (the teacher interacts with the student, but they are independent). |

    Here's a code example demonstrating all three relationships:

    ```java
    // Composition Example
    class Engine {
        private String type;
        
        public Engine(String type) {
            this.type = type;
        }
    }

    class Car {
        private final Engine engine; // Strong relationship - engine cannot exist without car
        
        public Car() {
            engine = new Engine("V8"); // Engine is created when Car is created
        }
        
        // When Car is destroyed, Engine is also destroyed
    }

    // Aggregation Example
    class Student {
        private String name;
        
        public Student(String name) {
            this.name = name;
        }
    }

    class University {
        private List<Student> students; // Weak relationship - students can exist without university
        
        public University() {
            students = new ArrayList<>();
        }
        
        public void addStudent(Student student) {
            students.add(student);
        }
        
        public void removeStudent(Student student) {
            students.remove(student);
        }
    }

    // Association Example
    class Teacher {
        public void teach(Student student) { // No ownership, just interaction
            System.out.println("Teaching student");
        }
    }

    class Student {
        public void learn(Teacher teacher) { // No ownership, just interaction
            System.out.println("Learning from teacher");
        }
    }
    ```
26. **What is the difference between method overloading and overriding in Java?**

   - **Method Overloading**: This occurs when multiple methods in the same class have the same name but different parameters (different type, number, or both). It allows methods to perform similar functions with different inputs. Overloading is resolved at compile time.

   - **Method Overriding**: This occurs when a subclass provides a specific implementation of a method that is already defined in its superclass. The method in the subclass must have the same name, return type, and parameters as the method in the superclass. Overriding is resolved at runtime, allowing for dynamic method dispatch.
   
		Example of Method Overloading:
		```java
		public class MathUtils {
				public int add(int a, int b) {
						return a + b;
				}

				public double add(double a, double b) {
						return a + b;
				}
		}
		```

		Example of Method Overriding:
		```java
		public class Animal {
				public void sound() {
						System.out.println("Animal makes a sound");
				}
		}

		public class Dog extends Animal {
				@Override
				public void sound() {
						System.out.println("Dog barks");
				}
		}
		```
27. **What is the difference between Java Dynamic Binding and Static Binding?**

   - **Static Binding**: This occurs at compile time and is used for method calls that are resolved based on the reference type. It is typically used with private, static, and final methods. Since the method to be called is determined at compile time, it cannot be changed at runtime.

   - **Dynamic Binding**: This occurs at runtime and is used for method calls that are resolved based on the actual object type. It is typically used with overridden methods in inheritance. Dynamic binding allows for polymorphism, where the method that gets executed is determined by the actual object being referred to, rather than the reference type.

   Example of Static Binding:
   ```java
   public class StaticBindingExample {
       public static void display() {
           System.out.println("Static Binding");
       }
   }
   ```

   Example of Dynamic Binding:
   ```java
   public class Shape {
       public void draw() {
           System.out.println("Drawing a shape");
       }
   }

   public class Circle extends Shape {
       @Override
       public void draw() {
           System.out.println("Drawing a circle");
       }
   }
   ```
	
28. **What is an Instance Initializer Block? Characteristics of Instance Initializer Block?**

   An Instance Initializer Block is a block of code that is used to initialize instance variables of a class. It is executed when an instance of the class is created, before the constructor is called.

   **Characteristics of Instance Initializer Block:**
   - It is executed every time an instance of the class is created.
   - It can access instance variables and methods of the class.
   - It is useful for common initialization code that is shared among multiple constructors.
   - It can be used to initialize instance variables that require more complex logic than simple assignment.
   - It is executed in the order it appears in the class, before the constructor's body.

   Example of Instance Initializer Block:
   ```java
   public class Example {
       private int value;

       // Instance Initializer Block
       {
           value = 10; // Initialization logic
       }

       public Example() {
           System.out.println("Constructor called. Value: " + value);
       }
   }
   ```