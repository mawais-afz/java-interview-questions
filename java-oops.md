# Object-Oriented Programming (OOP) Concepts

1. **Why is Java not considered to be purely object-oriented?**

   Java is not considered to be purely object-oriented because it supports primitive data types (such as int, char, boolean, byte, short, long, float, and double) that are not objects. In a purely object-oriented language, everything is treated as an object, and all data types would be defined as classes. While Java provides wrapper classes for these primitive types (e.g., Integer for int, Character for char, Boolean for boolean, Byte for byte, Short for short, Long for long, Float for float, and Double for double), the existence of primitives means that Java does not fully adhere to the principles of pure object-oriented programming. Additionally, Java allows for static methods and variables, which are not associated with any object instance, further distinguishing it from purely object-oriented languages.

2. **What is OOP?**

   Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data in the form of fields (often known as attributes or properties) and code in the form of procedures (often known as methods).

3. **What are the pillars of OOP?**

   The four pillars of Object-Oriented Programming (OOP) are:

   1. **Class**: A blueprint for creating objects, defining the properties and behaviors of an object.
   2. **Object**: An instance of a class, created from the class blueprint.
   3. **Encapsulation**: The bundling of data with the methods that operate on that data, restricting direct access to some of the object's components.
   4. **Inheritance**: The mechanism by which one class can inherit the properties and methods of another class, promoting code reuse and the creation of a hierarchical relationship between classes.
   5. **Polymorphism**: The ability of different classes to be treated as instances of the same class through a common interface, allowing for the implementation of methods in different ways.
   6. **Abstraction**: The concept of hiding the complex implementation details and showing only the necessary features of an object, simplifying the interaction with the object.

4. **What are classes and objects? Why use them in applications?**

   Classes are blueprints for creating objects in object-oriented programming. They define the properties (attributes) and behaviors (methods) that the objects created from the class will have. An object is an instance of a class, representing a specific entity with its own state and behavior.

   Using classes and objects in applications provides several benefits:

   1. **Modularity**: Classes allow developers to break down complex systems into smaller, manageable pieces, making the code easier to understand and maintain.

   2. **Reusability**: Once a class is defined, it can be reused to create multiple objects, reducing code duplication and promoting consistency.

   3. **Encapsulation**: Classes encapsulate data and methods, restricting access to the internal state of the object and exposing only what is necessary through public methods.

   4. **Inheritance**: Classes can inherit properties and methods from other classes, facilitating code reuse and the creation of hierarchical relationships.

   5. **Polymorphism**: Objects of different classes can be treated as objects of a common superclass, allowing for flexible and interchangeable code.

   Overall, classes and objects are fundamental to organizing and structuring code in a way that reflects real-world entities and their interactions.

5. **How to implement classes and objects in Java? What are the members of a class?**

   To implement classes and objects in Java, you need to follow these steps:

   1. **Define a Class**: A class is defined using the `class` keyword followed by the class name. Inside the class, you can declare members, which include attributes (fields), methods (functions), and constructors that define the behavior of the objects created from the class.

   ```java
   public class Car {
       // Attributes (Members)
       private String color;
       private String model;

       // Constructor (Member)
       public Car(String color, String model) {
           this.color = color;
           this.model = model;
       }

       // Method (Member)
       public void displayInfo() {
           System.out.println("Car Model: " + model + ", Color: " + color);
       }
   }
   ```

   2. **Create Objects**: Once the class is defined, you can create objects (instances) of that class using the `new` keyword.

   ```java
   public class Main {
       public static void main(String[] args) {
           // Creating objects of the Car class
           Car myCar = new Car("Red", "Toyota");
           Car yourCar = new Car("Blue", "Honda");

           // Calling methods on the objects
           myCar.displayInfo(); // Output: Car Model: Toyota, Color: Red
           yourCar.displayInfo(); // Output: Car Model: Honda, Color: Blue
       }
   }
   ```

   In this example, the `Car` class is defined with members including attributes, a constructor, and a method. Two objects of the `Car` class are created in the `Main` class, demonstrating how to implement classes and objects in Java.

6. **What is immutable object?**

   An immutable object is an object whose state cannot be changed after it is created. Once an immutable object is constructed, its contents remain constant throughout its lifetime. String is a classic example of an immutable class in Java.

   Key characteristics of immutable objects:

   1. **Final Class**: The class should be declared as final to prevent inheritance
   2. **Private Fields**: All fields should be private and final
   3. **No Setters**: No methods that modify the object's state
   4. **Deep Copy**: If mutable objects are used as fields, return copies instead of references
   5. **Initialize in Constructor**: All fields must be initialized in the constructor

   Example of an immutable class:

   ```java
   public final class ImmutablePerson {
       private final String name;
       private final int age;

       public ImmutablePerson(String name, int age) {
           this.name = name;
           this.age = age;
       }

       public String getName() {
           return name;
       }

       public int getAge() {
           return age;
       }
   }
   ```

   Benefits of immutable objects:

   - Thread-safe without synchronization
   - Safe to share and cache
   - Simple to construct, test, and use
   - Prevent temporal coupling
   - Side-effect free behavior

7. **How can we create an immutable class in Java?**

   To create an immutable class in Java, follow these steps:

   1. **Declare the class as final** to prevent inheritance
   2. **Make all fields private and final** to prevent direct access and modification
   3. **Don't provide setter methods** for fields
   4. **Initialize all fields via constructor**
   5. **Make deep copies of mutable objects** in constructor and getter methods
   6. **Don't expose methods that can change object state**

   Example of creating an immutable class:

   ```java
   public final class ImmutableStudent {
       private final String name;
       private final int id;
       private final List<String> courses;

       public ImmutableStudent(String name, int id, List<String> courses) {
           this.name = name;
           this.id = id;
           // Deep copy of mutable object
           this.courses = new ArrayList<>(courses);
       }

       public String getName() {
           return name;
       }

       public int getId() {
           return id;
       }

       public List<String> getCourses() {
           // Return copy to prevent modification
           return new ArrayList<>(courses);
       }
   }
   ```

   This class is immutable because:

   - It's declared final
   - All fields are private and final
   - No setter methods are provided
   - Mutable List is deep copied in constructor and getter
   - No methods can modify the object's state

8. **What is the role and benefit of package in Java?**

   In Java, a package is a namespace that organizes a set of related classes and interfaces. The primary role of packages is to group related classes together, which helps in avoiding name conflicts and controlling access.

   The benefits of using packages in Java include:

   1. **Namespace Management**: Packages help to avoid naming conflicts by grouping classes with similar functionality under a unique package name.

   2. **Access Protection**: Packages provide controlled access to classes and members. Classes within the same package can access each other's package-private and protected members, while classes in different packages cannot.

   3. **Code Organization**: Packages help in organizing classes and interfaces in a logical manner, making it easier to locate and manage code.

   4. **Reusability**: By grouping related classes, packages promote code reusability, allowing developers to use existing classes in new applications without modification.

   5. **Modularity**: Packages encourage modular programming, where functionality is divided into separate, manageable components.

   Overall, packages play a crucial role in structuring Java applications, enhancing maintainability, and promoting best practices in software development.

9. **What are access specifiers? What are the types of access specifiers?**

   Access specifiers in Java are keywords that set the accessibility (visibility) of classes, methods, and other members. They control how the members of a class can be accessed from other classes. The main types of access specifiers in Java are:

   1. **Public**: Members declared as public are accessible from any other class in any package. This means there are no restrictions on the visibility of public members.

   2. **Private**: Members declared as private are accessible only within the class they are declared in. This means that private members cannot be accessed from outside the class, providing a way to encapsulate and protect the data.

   3. **Protected**: Members declared as protected are accessible within the same package and by subclasses, even if they are in different packages.

   4. **Default (Package-Private)**: If no access specifier is declared, the member is accessible only within its own package. This is also known as package-private access.

   By using access specifiers, developers can implement encapsulation, which is a fundamental principle of object-oriented programming, ensuring that the internal representation of an object is hidden from the outside.

10. **What are constructors in Java?**

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

11. **Can you override static methods in Java?**

    No, static methods cannot be overridden in Java. This is because:

    1. **Static Method Binding**: Static methods are bound at compile time, meaning the method to be called is determined by the reference type, not the object type.

    2. **No Polymorphism**: Since static methods belong to the class rather than instances, they do not participate in polymorphism. Therefore, if a subclass defines a static method with the same name as a static method in its superclass, it is not considered an override but rather a method hiding.

    3. **Accessing Static Methods**: When you call a static method, it is resolved based on the reference type, not the actual object type. This means that the static method of the superclass will be called, even if the reference is of the subclass type.

    Example of static method hiding:

    ```java
    class Parent {
        static void display() {
            System.out.println("Static method in Parent");
        }
    }

    class Child extends Parent {
        static void display() {
            System.out.println("Static method in Child");
        }
    }

    public class Test {
        public static void main(String[] args) {
            Parent obj = new Child();
            obj.display(); // Outputs: Static method in Parent
        }
    }
    ```

    In this example, the static method `display()` in the `Child` class hides the static method in the `Parent` class, but it does not override it.

12. **What is the use of static variables and methods?**

    | Feature | Static Variables | Static Methods |
    |---------|-----------------|----------------|
    | Memory Allocation | Single copy shared across all instances of the class | Belongs to class rather than any instance |
    | Access | Can be accessed without creating class instance | Can be called without creating class instance |
    | Usage | Common properties shared by all instances (e.g., counters, constants) | Utility functions that don't need instance data |
    | Instance Access | Cannot directly access non-static members | Cannot directly access non-static members |
    | Memory Efficiency | Saves memory by avoiding multiple copies | N/A |
    | Example Use Cases | - Counter for number of objects created<br>- Configuration constants<br>- Shared resources | - Math utility functions<br>- Factory methods<br>- Helper functions |

    Example:
    ```java
    public class Student {
        private static int studentCount = 0;  // static variable
        private String name;

        public Student(String name) {
            this.name = name;
            studentCount++;  // tracks total number of students
        }

        public static int getStudentCount() {  // static method
            return studentCount;
        }
    }
    ```

12. **Can you declare a constructor using static?**

    No, constructors cannot be declared as static in Java. This is because:

    1. Constructors are instance-specific methods used to initialize object state
    2. Static members belong to the class rather than instances
    3. The purpose of a constructor is to create and initialize new instances
    4. Static methods cannot access instance members, which would defeat the purpose of constructors

    Example of invalid constructor declaration:

    ```java
    public class Example {
        // This would cause a compilation error
        static Example() {  // Invalid - cannot use static with constructor
            // initialization code
        }
    }
    ```

    If you need static initialization, use a static initialization block instead:

    ```java
    public class Example {
        static {
            // Static initialization code here
        }
    }
    ```

13. **What rules that you must follow while creating a constructor in Java?**

    There are several important rules that must be followed when creating a constructor in Java:

    1. **Same Name as Class**: The constructor name must be exactly the same as the class name (including case).

    2. **No Return Type**: Constructors cannot have any return type, not even void.

    3. **Access Modifiers**: Constructors can use any access modifier (public, private, protected, or default).

    4. **Cannot be Static/Final**: Constructors cannot be declared as static or final.

    5. **Cannot be Abstract**: Constructors cannot be declared as abstract.

    6. **Super/This Call**: If using super() or this() to call another constructor, it must be the first statement in the constructor.

    7. **No Inheritance**: Constructors are not inherited by subclasses, though they can be called using super().

    Example of following these rules:

    ```java
    public class Student {
        private String name;

        // Correct constructor
        public Student(String name) {
            this.name = name;  // Valid initialization
        }

        // Invalid constructor - wrong name
        public student() { }  // Compilation error

        // Invalid constructor - has return type
        public void Student() { }  // Compilation error
    }
    ```

14. **What is the difference between constructor and method?**

    | Aspect           | Constructor                                                      | Method                                                      |
    | ---------------- | ---------------------------------------------------------------- | ----------------------------------------------------------- |
    | Purpose          | Used to initialize object state when creating a new instance     | Used to perform operations and implement behavior           |
    | Name             | Must have the same name as the class                             | Can have any valid name                                     |
    | Return Type      | No return type, not even void                                    | Must have a return type (void or specific type)             |
    | Invocation       | Called automatically when object is created using new keyword    | Must be explicitly called on an object                      |
    | Inheritance      | Not inherited by subclasses (though can be called using super()) | Inherited by subclasses unless declared as private or final |
    | Default Creation | Java provides a default constructor if none is defined           | No default methods are created by Java                      |

    Here's an example illustrating the differences:

    ```java
    public class Example {
        private String data;

        // Constructor - initializes object
        public Example(String data) {
            this.data = data;
        }

        // Method - performs operation
        public void processData() {
            System.out.println("Processing: " + data);
        }
    }
    ```

15. **Explain the constructor overloading**

    Constructor overloading is a technique in Java where a class can have multiple constructors with different parameter lists. Each constructor provides a different way to initialize an object of that class. The constructors must differ in their parameter lists (number of parameters, types of parameters, or both).

    Here's an example of constructor overloading:

    ```java
    public class Student {
        private String name;
        private int age;
        private String grade;

        // Constructor with no parameters
        public Student() {
            this.name = "Unknown";
            this.age = 0;
            this.grade = "N/A";
        }

        // Constructor with name parameter
        public Student(String name) {
            this.name = name;
            this.age = 0;
            this.grade = "N/A";
        }

        // Constructor with name and age parameters
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
            this.grade = "N/A";
        }

        // Constructor with all parameters
        public Student(String name, int age, String grade) {
            this.name = name;
            this.age = age;
            this.grade = grade;
        }
    }
    ```

    In this example, the `Student` class has four different constructors, each accepting different parameters. This allows for flexible object creation based on the available information:

    ```java
    Student s1 = new Student();                         // Uses no-arg constructor
    Student s2 = new Student("John");                   // Uses constructor with name
    Student s3 = new Student("Jane", 20);               // Uses constructor with name and age
    Student s4 = new Student("Mike", 21, "A");          // Uses constructor with all parameters
    ```

16. **What is Copy Constructor in Java?**

    A Copy Constructor in Java is a constructor that creates a new object by copying the values from another object of the same class. It takes an object of the same class as a parameter and creates a new object with the same values. Copy constructors are useful when you want to create a new object with the same state as an existing object.

    Here's an example of a Copy Constructor:

    ```java
    public class Student {
        private String name;
        private int age;

        // Normal constructor
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        // Copy constructor
        public Student(Student other) {
            this.name = other.name;
            this.age = other.age;
        }
    }

    // Usage example:
    Student student1 = new Student("John", 20);
    Student student2 = new Student(student1); // Creates a copy of student1
    ```

    Note: that Java does not provide automatic copy constructors like C++. You need to implement them explicitly if needed. Also, when dealing with reference types, be careful to perform a deep copy if required, to avoid sharing references between the original and copied objects.

17. **What is a singleton class in Java? Describe the singleton pattern with an example.**

    A Singleton class in Java is a design pattern that restricts the instantiation of a class to a single instance. This is useful when exactly one object is needed to coordinate actions across the system, such as managing configuration settings, database connections, or thread pools.

    To implement a thread-safe Singleton class in Java, you typically follow these steps:

    1. **Private Constructor**: Make the constructor private to prevent direct instantiation
    2. **Private Static Instance**: Create a private static final instance of the class
    3. **Public Static Method**: Provide a public static method to access the single instance

    Here's an example of a thread-safe Singleton class using the initialization-on-demand holder pattern:

    ```java
    public class Singleton {
        // Private constructor prevents instantiation from other classes
        private Singleton() { }

        // Private static holder class - loaded only when getInstance() is called
        private static class SingletonHolder {
            private static final Singleton INSTANCE = new Singleton();
        }

        // Public static method to get the singleton instance
        public static Singleton getInstance() {
            return SingletonHolder.INSTANCE;
        }

        // Example method of the singleton
        public void doSomething() {
            System.out.println("Singleton is doing something");
        }
    }
    ```

    Usage example:

    ```java
    Singleton singleton = Singleton.getInstance(); // Gets the single instance
    singleton.doSomething(); // Use the singleton

    // Will return the same instance
    Singleton anotherReference = Singleton.getInstance();
    System.out.println(singleton == anotherReference); // Prints: true
    ```

    In this example, the `Singleton` class has a private constructor, a static instance variable, and a public static method `getInstance()` that provides access to the single instance of the class. This ensures that no more than one instance of the `Singleton` class can exist at any time.

18. **What is encapsulation? Explain encapsulation with an example.**

    Encapsulation is one of the four fundamental OOP concepts that involves bundling data and the methods that operate on that data within a single unit (class), while restricting direct access to some of the object's components. This is achieved in Java through:

    1. Declaring class variables/attributes as private
    2. Providing public getter and setter methods to access and modify the values

    Here's a practical example:

    ```java
    public class BankAccount {
        private double balance;  // private variable
        private String accountNumber;

        public BankAccount(String accountNumber) {
            this.accountNumber = accountNumber;
            this.balance = 0.0;
        }

        // Getter method
        public double getBalance() {
            return balance;
        }

        // Instead of directly modifying balance, we use methods
        public void deposit(double amount) {
            if (amount > 0) {
                balance += amount;
            }
        }

        public void withdraw(double amount) {
            if (amount > 0 && amount <= balance) {
                balance -= amount;
            }
        }
    }
    ```

    In this example, the `balance` variable is private and can't be accessed directly. Instead, we provide controlled methods like `deposit()` and `withdraw()` to modify it. This ensures that:

    3. The balance can't be modified without validation
    4. The implementation details are hidden from the user
    5. We can change the internal implementation without affecting code that uses the class

19. **What is inheritance and what are its types in Java?**

    Inheritance is a fundamental object-oriented programming concept where a class (subclass/child class) can inherit attributes and methods from another class (superclass/parent class). In Java, inheritance is implemented using the `extends` keyword. This mechanism promotes code reuse, simplifies maintenance, and allows for the creation of more specialized classes based on existing ones. There are several types of inheritance supported in Java:

    1. **Single Inheritance**: A class inherits from only one superclass. This is the most common type of inheritance in Java.
       Example: Class B extends Class A

    2. **Multilevel Inheritance**: A class inherits from a class which in turn inherits from another class.
       Example: Class C extends Class B extends Class A

    3. **Hierarchical Inheritance**: Multiple classes inherit from a single superclass.
       Example: Class B and Class C both extend Class A

    4. **Multiple Inheritance**: Java does not support multiple inheritance through classes (a class cannot extend multiple classes). However, it can be achieved through interfaces.
       Example: Class A implements Interface1, Interface2

    5. **Hybrid Inheritance**: A combination of multiple inheritance and hierarchical inheritance.
       Example: Class C extends Class A and Class B

    Note: Java deliberately does not support multiple inheritance through classes to avoid the "diamond problem" where ambiguity can arise if multiple parent classes have methods with the same name.

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

20. **What do you mean by Polymorphism and what are its types?**

    Polymorphism means "many forms" and is one of the core concepts of object-oriented programming. It allows objects to be treated as instances of their parent class rather than their actual class. In Java, there are two main types of polymorphism:

    1. **Runtime Polymorphism (Dynamic Binding)**

       - Also known as method overriding
       - Determined at runtime
       - Achieved through inheritance and method overriding
       - Example: A Dog object being treated as an Animal object

         ```java
         class Animal {
             void makeSound() {
                 System.out.println("Some sound");
             }
         }

         class Dog extends Animal {
             @Override
             void makeSound() {
                 System.out.println("Woof!");
             }
         }

         // Runtime polymorphism in action
         Animal animal = new Dog();
         animal.makeSound(); // Outputs: Woof!
         ```

    2. **Compile-time Polymorphism (Static Binding)**

       - Also known as method overloading
       - Determined at compile time
       - Achieved by defining multiple methods with the same name but different parameters
       - Example: Having multiple versions of a method like add(int, int) and add(double, double)

         ```java
         class Calculator {
             // Method overloading
             int add(int a, int b) {
                 return a + b;
             }

             double add(double a, double b) {
                 return a + b;
             }

             int add(int a, int b, int c) {
                 return a + b + c;
             }
         }

         Calculator calc = new Calculator();
         calc.add(5, 3);       // Calls first method
         calc.add(4.5, 3.2);   // Calls second method
         calc.add(2, 3, 4);    // Calls third method
         ```

    The key difference is that runtime polymorphism is resolved during program execution based on the actual object type, while compile-time polymorphism is resolved during compilation based on method signatures.

21. **What do you mean by abstraction and how it is achieved in Java?**

    Abstraction is the process of hiding implementation details and showing only the functionality to the user. It helps reduce programming complexity and effort by focusing on what an object does rather than how it does it.

    In Java, abstraction can be achieved in two ways:

    1. **Abstract Classes**

       - Declared using the `abstract` keyword
       - Can have both abstract and concrete methods
       - Cannot be instantiated
       - Must be extended by concrete classes

       ```java
       abstract class Shape {
           abstract double calculateArea(); // abstract method

           void display() { // concrete method
               System.out.println("This is a shape");
           }
       }

       class Circle extends Shape {
           double radius;

           @Override
           double calculateArea() {
               return Math.PI * radius * radius;
           }
       }
       ```

    2. **Interfaces**

       - Provides 100% abstraction
       - Contains only abstract methods (before Java 8)
       - Can be implemented by multiple classes

       ```java
       interface Drawable {
           void draw();
           void resize();
       }

       class Rectangle implements Drawable {
           @Override
           public void draw() {
               System.out.println("Drawing rectangle");
           }

           @Override
           public void resize() {
               System.out.println("Resizing rectangle");
           }
       }
       ```

    The main benefit of abstraction is that it allows you to focus on what the object does instead of how it does it, reducing complexity and coupling in your code.

22. **What is the difference between extends and implements?**

    | Aspect                   | extends                                                 | implements                                             |
    | ------------------------ | ------------------------------------------------------- | ------------------------------------------------------ |
    | Purpose                  | Used for class inheritance                              | Used to implement interfaces                           |
    | Multiple Inheritance     | A class can extend only one class                       | A class can implement multiple interfaces              |
    | Type                     | Creates an "is-a" relationship between classes          | Creates a "can-do" relationship                        |
    | Method Implementation    | Inherits both method declarations and implementations   | Must implement all interface methods (unless abstract) |
    | Access to Parent Members | Can access protected and public members of parent class | Can only access public interface constants             |
    | Constructor Inheritance  | Inherits constructors from parent class                 | Interfaces cannot have constructors                    |
    | Code Reuse               | Allows reuse of code from parent class                  | Only provides method contracts, no implementation      |
    | Usage Example            | `class Dog extends Animal`                              | `class Bird implements Flyable`                        |

23. **What is the difference between loose coupling and tight coupling?**

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

24. **What is the difference between cohesion and coupling?**

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

25. **What is a Marker Interface?**

    A Marker Interface in Java is an interface that does not contain any methods. It is used to mark a class that implements it, indicating that the class has a specific property or behavior. Marker interfaces are often used to indicate that a class has a particular characteristic or capability, such as being serializable, cloneable, or thread-safe.
    Here are some examples of commonly used marker interfaces in Java:

    ```java
    // Example of a custom marker interface
    public interface Deletable {
        // No methods - just marks classes that can be deleted
    }

    // Class implementing the marker interface
    public class Document implements Deletable {
        private String content;

        public Document(String content) {
            this.content = content;
        }

        public void delete() {
            // Delete implementation
            System.out.println("Document deleted");
        }
    }

    // Usage example
    public class FileManager {
        public void deleteIfPossible(Object obj) {
            if (obj instanceof Deletable) {
                System.out.println("Object can be deleted");
                ((Document) obj).delete();
            } else {
                System.out.println("Object cannot be deleted");
            }
        }
    }
    ```

    Some built-in marker interfaces in Java include:

    - `Serializable`: Marks classes that can be serialized
    - `Cloneable`: Marks classes that can be cloned
    - `Remote`: Marks classes that can be used for RMI (Remote Method Invocation)

26. **What is an abstract class? Explain its purpose and when to use it.**

    An abstract class in Java is a class that cannot be instantiated on its own and may contain both abstract and concrete methods. It serves as a blueprint for other classes and is designed to be extended by subclasses.

    Here's an example to illustrate abstract classes:

    ```java
    // Abstract class example
    public abstract class Animal {
        protected String name;

        // Constructor
        public Animal(String name) {
            this.name = name;
        }

        // Concrete method
        public void sleep() {
            System.out.println(name + " is sleeping");
        }

        // Abstract method - must be implemented by subclasses
        public abstract void makeSound();
    }

    // Concrete class extending abstract class
    public class Dog extends Animal {
        public Dog(String name) {
            super(name);
        }

        // Implementation of abstract method
        @Override
        public void makeSound() {
            System.out.println(name + " says: Woof!");
        }
    }
    ```

    Use abstract classes when:

    - You want to share code among several related classes
    - You expect classes that extend your abstract class to have common methods/fields
    - You want to declare non-public members (unlike interfaces)
    - You need to provide a template for a group of related classes
    - Some common behavior can be implemented in the abstract class, while other behavior must be implemented by each subclass

27. **Can we define a class Abstract even if it does not have any abstract methods?**

    Yes, we can define a class as abstract even if it doesn't have any abstract methods. This is perfectly valid in Java. The abstract keyword simply prevents the class from being instantiated directly.

    Here's an example:

    ```java
    public abstract class Vehicle {
        private String brand;
        
        public Vehicle(String brand) {
            this.brand = brand;
        }
        
        public void startEngine() {  // concrete method
            System.out.println("Engine started");
        }
    }
    ```

    While this is possible, it's generally not a common practice unless you have a specific reason to prevent instantiation of the class. Some reasons to do this might be:
    
    - You want to force developers to use subclasses instead of the base class
    - The class is not complete enough to be instantiated meaningfully
    - You're designing a framework where the base class should never be used directly

27. **Can you make abstract methods static in Java?**

    No, abstract methods cannot be static in Java. This is because:

    1. Abstract methods must be overridden by subclasses, but static methods cannot be overridden (they can only be hidden)
    2. Static methods belong to the class itself rather than instances, while abstract methods are meant to be implemented by subclass instances
    3. It would be contradictory since static methods have a body/implementation while abstract methods explicitly lack implementation

    Example of invalid code:

    ```java
    public abstract class Example {
        // This will cause a compilation error
        public static abstract void method(); // Cannot combine static and abstract
    }
    ```

    If you need static behavior in an abstract class, use a regular static method with implementation instead:

    ```java
    public abstract class Example {
        // This is valid
        public static void staticMethod() {
            // Implementation here
        }

        // This is also valid
        public abstract void abstractMethod();
    }
    ```

28. **What is the difference between abstract class and interface in Java?**

    | Aspect                | Abstract Class                                                                       | Interface                                                                                                               |
    | --------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
    | Definition            | A class that cannot be instantiated and can have both abstract and concrete methods. | A reference type that can contain only constants, method signatures, default methods, static methods, and nested types. |
    | Inheritance           | Supports single inheritance (a class can extend only one abstract class).            | Supports multiple inheritance (a class can implement multiple interfaces).                                              |
    | Method Implementation | Can have both abstract methods (without body) and concrete methods (with body).      | All methods are abstract by default (unless they are default or static methods).                                        |
    | Constructor           | Can have constructors.                                                               | Cannot have constructors.                                                                                               |
    | Access Modifiers      | Can have access modifiers (public, protected, private).                              | All methods are public by default; cannot have access modifiers.                                                        |
    | Use Case              | Used when classes share a common base and behavior.                                  | Used to define a contract that implementing classes must follow.                                                        |

29. **What is the difference between composition, aggregation, and association?**

    | Aspect     | Composition                                                                     | Aggregation                                                                  | Association                                                                                 |
    | ---------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
    | Definition | A strong relationship where the child cannot exist independently of the parent. | A weaker relationship where the child can exist independently of the parent. | A general relationship between two classes, where one class uses or interacts with another. |
    | Lifespan   | The child's lifespan is tied to the parent's lifespan.                          | The child can outlive the parent.                                            | The lifespan of the associated objects is independent.                                      |
    | Ownership  | The parent owns the child, and the child is part of the parent.                 | The parent does not own the child; they can exist separately.                | There is no ownership; it is a loose relationship.                                          |
    | Example    | A car and its engine (the engine cannot exist without the car).                 | A university and its students (students can exist without the university).   | A teacher and a student (the teacher interacts with the student, but they are independent). |

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

30. **What are the differences between method overloading & overriding?**

    | Aspect          | Method Overloading                                                     | Method Overriding                                              |
    | --------------- | ---------------------------------------------------------------------- | -------------------------------------------------------------- |
    | Definition      | Multiple methods with same name but different parameters in same class | Subclass provides specific implementation of superclass method |
    | Parameters      | Must have different parameters (type, number, or both)                 | Must have same parameters as superclass method                 |
    | Return Type     | Can be different                                                       | Must be same or covariant (subtype)                            |
    | Access Modifier | Can be different                                                       | Must be same or less restrictive                               |
    | Binding         | Static/Compile-time binding                                            | Dynamic/Runtime binding                                        |
    | Inheritance     | Not related to inheritance                                             | Requires inheritance relationship                              |
    | @Override       | Not required                                                           | Recommended to use                                             |
    | Purpose         | Provides different ways to call similar method                         | Provides specific implementation of inherited method           |

    Example of Method Overloading:

    ```java
    class Calculator {
        // Method overloading - same name, different parameters
        public int add(int a, int b) {
            return a + b;
        }

        public double add(double a, double b) {
            return a + b;
        }

        public int add(int a, int b, int c) {
            return a + b + c;
        }
    }
    ```

    Example of Method Overriding:

    ```java
    class Animal {
        public void makeSound() {
            System.out.println("Animal makes a sound");
        }
    }

    class Dog extends Animal {
        @Override
        public void makeSound() {
            System.out.println("Dog barks: Woof!");
        }
    }

    class Cat extends Animal {
        @Override
        public void makeSound() {
            System.out.println("Cat meows: Meow!");
        }
    }
    ```

    In the overloading example, the `Calculator` class has multiple `add` methods with different parameter types/counts.
    In the overriding example, `Dog` and `Cat` classes provide their own specific implementations of the `makeSound()` method inherited from `Animal`.

31. **Why is method overloading in Java not possible by changing the method's return type?**

    Method overloading in Java cannot be achieved solely by changing the return type of the method because the method signature, which is used to identify the method, consists of the method name and the parameter list (types and number of parameters). The return type is not part of the method signature. Therefore, if two methods have the same name and parameter list but different return types, the compiler cannot distinguish between them based on the return type alone, leading to ambiguity.

32. **What is the difference between Java Dynamic Binding and Static Binding?**

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

33. **What is an Instance Initializer Block? Characteristics of Instance Initializer Block?**

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

34. **What is a static block in Java?**

    A static block (also called static initialization block) is a block of code inside a class that is executed only once when the class is first loaded into memory. It is used to initialize static variables or perform one-time setup operations.

    **Characteristics of static blocks:**

    - Executes automatically when the class is loaded
    - Runs only once, regardless of how many instances are created
    - Executes before any static methods are called
    - Multiple static blocks execute in order of appearance
    - Can access only static members directly

    Example of static block:

    ```java
    public class Example {
        static int count;

        // Static block
        static {
            count = 0;
            System.out.println("Static block executed");
            // Complex initialization logic can go here
        }

        // Multiple static blocks are allowed
        static {
            System.out.println("Second static block");
        }
    }
    ```

35. **What is the purpose of static members in Java?**

    Static members in Java (including methods, variables, and nested classes) belong to the class itself rather than any specific instance. They serve several important purposes:

    1. **Memory Efficiency**

       - Only one copy exists in memory regardless of how many instances are created
       - Shared across all instances of the class
       - Ideal for constants and utility functions

    2. **Accessibility Without Instance**

       - Can be accessed without creating an object of the class
       - Useful for utility methods that don't need instance data
       - Common in helper classes and factory methods

    3. **Global State Management**

       - Provides a way to maintain class-level state
       - Useful for counters, configuration values, or caches shared across instances
       - Enables communication between different instances of a class

    4. **Utility Organization**
       - Static nested classes provide logical grouping of utility code
       - Static methods organize helper functions that operate independently
       - Commonly used in design patterns like Singleton and Factory Method
         |

    Example demonstrating all three:

    ```java
    public class OuterClass {
        // Static variable
        static int count = 0;

        // Static method
        static void incrementCount() {
            count++;
        }

        // Static nested class
        static class StaticNestedClass {
            void display() {
                System.out.println("Count: " + count);
            }
        }
    }
    ```

36. **Explain the use of final keyword in variable, method and class**

    The `final` keyword in Java is used to impose restrictions on variables, methods, and classes:

    | Type                | Description                                                                                                                                                                       |
    | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | **Final Variables** | - Makes the variable a constant that can only be assigned once<br>- Value cannot be changed after initialization<br>- Must be initialized either at declaration or in constructor |
    | **Final Methods**   | - Prevents the method from being overridden in subclasses<br>- Ensures that the method implementation remains the same throughout inheritance hierarchy                           |
    | **Final Classes**   | - Prevents the class from being inherited<br>- No other class can extend a final class<br>- Useful when you want to prevent inheritance for security/design reasons               |

    Here's an example demonstrating all three uses:

    ```java
    final class FinalClass { // Cannot be inherited
        final int CONSTANT = 100; // Cannot be changed after initialization

        final void finalMethod() { // Cannot be overridden
            System.out.println("This method cannot be overridden");
        }
    }

    // This would cause compilation error:
    // class ChildClass extends FinalClass { } // Cannot extend final class
    ```

37. **What is the significant difference between object-oriented language and object-based language?**

    Object-oriented languages and object-based languages differ in several key aspects:

    | Feature               | Object-Oriented Languages                    | Object-Based Languages                |
    | --------------------- | -------------------------------------------- | ------------------------------------- |
    | **Inheritance**       | Supports inheritance and polymorphism        | Does not support inheritance          |
    | **Class Support**     | Has full class-based abstraction             | May use prototypes instead of classes |
    | **Examples**          | Java, C++, Python, Ruby                      | JavaScript (pre-ES6), VBScript        |
    | **Code Organization** | Organized around both classes and objects    | Organized around objects only         |
    | **Data Abstraction**  | Supports both data and procedure abstraction | Primarily supports data abstraction   |

    Key points:

    - Object-oriented languages provide complete support for OOP principles (inheritance, polymorphism, encapsulation)
    - Object-based languages support objects but lack inheritance and some other OOP features
    - Object-based languages often use prototype-based programming instead of class-based inheritance
