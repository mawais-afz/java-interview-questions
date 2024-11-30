# Object-Oriented Programming (OOP) Concepts

1. **What is OOP?**

   Object-oriented programming (OOP) is a programming paradigm that organizes code into objects, which are instances of classes. A class serves as a blueprint that defines both the data (attributes/properties) and behaviors (methods) that its objects will have. OOP emphasizes concepts like encapsulation, inheritance, polymorphism, and abstraction to create modular, reusable, and maintainable code.

   The main advantages of OOP include:

   - Better organization of code through objects and classes
   - Code reusability through inheritance
   - Flexibility through polymorphism
   - Data security through encapsulation
   - Reduced complexity through abstraction

2. **What is object-oriented paradigm?**

   The object-oriented paradigm is a programming approach that structures software design around data, or objects, rather than functions and logic. In this paradigm, objects are instances of classes that combine both data (attributes) and behaviors (methods) into a single entity.

   Key characteristics of the object-oriented paradigm include:

   - Organizing software as a collection of interacting objects
   - Emphasizing data abstraction and the relationships between objects
   - Promoting modular and flexible code design
   - Representing real-world entities and their interactions through code
   - Focusing on creating reusable and maintainable software components

   Unlike procedural programming, which focuses on writing procedures or functions that perform operations on data, the object-oriented paradigm treats data and the methods that operate on that data as a unified concept. This approach allows for more intuitive modeling of complex systems, better code organization, and improved software scalability.

   The object-oriented paradigm is implemented through core principles such as:

   - Encapsulation: Bundling data and methods that operate on that data
   - Inheritance: Creating new classes based on existing classes
   - Polymorphism: Allowing objects to be treated as instances of their parent class
   - Abstraction: Hiding complex implementation details

3. **Why is Java not considered to be purely object-oriented?**

   Java is not considered to be purely object-oriented because it supports primitive data types (such as int, char, boolean, byte, short, long, float, and double) that are not objects. In a purely object-oriented language, everything is treated as an object, and all data types would be defined as classes. While Java provides wrapper classes for these primitive types (e.g., Integer for int, Character for char, Boolean for boolean, Byte for byte, Short for short, Long for long, Float for float, and Double for double), the existence of primitives means that Java does not fully adhere to the principles of pure object-oriented programming. Additionally, Java allows for static methods and variables, which are not associated with any object instance, further distinguishing it from purely object-oriented languages.

4. **What are the pillars of OOP?**

   The four pillars of Object-Oriented Programming (OOP) are:

   1. **Class**: A blueprint for creating objects, defining the properties and behaviors of an object.
   2. **Object**: An instance of a class, created from the class blueprint.
   3. **Encapsulation**: The bundling of data with the methods that operate on that data, restricting direct access to some of the object's components.
   4. **Inheritance**: The mechanism by which one class can inherit the properties and methods of another class, promoting code reuse and the creation of a hierarchical relationship between classes.
   5. **Polymorphism**: The ability of different classes to be treated as instances of the same class through a common interface, allowing for the implementation of methods in different ways.
   6. **Abstraction**: The concept of hiding the complex implementation details and showing only the necessary features of an object, simplifying the interaction with the object.

5. **What are classes and objects? Why use them in applications?**

   Classes are blueprints or templates that define the structure and behavior of objects in object-oriented programming. They specify what properties (attributes/fields) and behaviors (methods) objects of that type will have. Objects are concrete instances of a class - when you create an object, you're creating a specific instance with its own set of data based on the class definition.

   For example, a Car class might define properties like color and model, and methods like start() and stop(). Each Car object would then have its own specific color and model values.

   Classes and objects are essential in applications for several reasons:

   1. **Organization**: They provide a natural way to model real-world concepts and organize code logically. For example, a banking application might have classes for Account, Customer, and Transaction.

   2. **Code Reuse**: Once you define a class, you can create many objects from it without duplicating code. For instance, you can create multiple Customer objects from a single Customer class.

   3. **Data Protection**: Classes can hide their internal details and expose only what's necessary through public methods, preventing invalid data modifications.

   4. **Maintenance**: Changes to a class automatically apply to all objects of that class, making code maintenance easier.

   5. **Extensibility**: New classes can extend existing ones, adding or modifying functionality while keeping the original code intact.

   Example:

   ```java
   // Class definition
   public class Car {
       private String color;
       private String model;

       public void start() {
           System.out.println("Car starting...");
       }
   }

   // Creating objects
   Car myCar = new Car();  // First car object
   Car anotherCar = new Car();  // Second car object
   ```

6. **What is the significant difference between object-oriented language and object-based language? Or What is the difference between object-oriented and object-based languages?**

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

7. **What is a class?**

   A class is a blueprint or template for creating objects in object-oriented programming. It defines the properties (attributes/fields) and behaviors (methods) that all objects of that type will have. A class encapsulates data for the object and methods to manipulate that data.

   Key aspects of a class:

   1. **Fields/Attributes**: Variables that store data for objects of the class
   2. **Methods**: Functions that define behaviors and operations on the class data
   3. **Constructors**: Special methods used to initialize new objects
   4. **Access Modifiers**: Keywords that control visibility and access to class members

   Example of a class:

   ```java
   public class Car {
       // Fields
       private String color;
       private String model;

       // Constructor
       public Car(String color, String model) {
           this.color = color;
           this.model = model;
       }

       // Method
       public void displayInfo() {
           System.out.println("Car Model: " + model + ", Color: " + color);
       }
   }
   ```

8. **What is inner class? What are the advantages of Java inner classes?**

   An inner class is a class defined within another class. The inner class exists within the scope of another class (outer class) and has access to all its members, including private ones.

   Types of inner classes:

   1. **Member Inner Class**: Non-static class defined at member level
   2. **Static Inner Class**: Static class defined at member level
   3. **Local Inner Class**: Class defined within a method
   4. **Anonymous Inner Class**: Class defined without a name, often used for interfaces/abstract classes

   Example of different inner class types:

   ```java
   public class OuterClass {
       private int x = 10;

       // Member inner class
       class MemberInner {
           void print() { System.out.println(x); }
       }

       // Static inner class
       static class StaticInner {
           void print() { System.out.println("Static inner"); }
       }

       void method() {
           // Local inner class
           class LocalInner {
               void print() { System.out.println(x); }
           }

           // Anonymous inner class
           Runnable r = new Runnable() {
               public void run() {
                   System.out.println(x);
               }
           };
       }
   }
   ```

   Advantages of inner classes:

   1. **Encapsulation**: Inner classes can access private members of the outer class
   2. **Code Organization**: Helps group related classes together
   3. **Better Readability**: Classes are defined close to where they are used
   4. **Security**: Inner class can be hidden from other packages
   5. **Event Handling**: Particularly useful for implementing event listeners
   6. **Memory Efficiency**: Non-static inner classes share the namespace with outer class

9. **What is a nested class?**

   A nested class is a class defined within another class. In Java, nested classes can be categorized into two main types:

   1. **Static Nested Classes**: These are static classes declared inside another class. They can access only static members of the outer class directly.

   ```java
   class OuterClass {
       static class StaticNestedClass {
           // can only access static members of OuterClass
       }
   }
   ```

   2. **Inner Classes**: These are non-static nested classes. They have access to all members of the enclosing class (both static and non-static).
      - Member inner classes
      - Local inner classes
      - Anonymous inner classes

   Key differences between static nested classes and inner classes:

   - Static nested classes cannot access non-static members of outer class directly
   - Inner classes can access all members of outer class
   - Static nested classes can be instantiated without an instance of outer class
   - Inner classes require an instance of outer class to be instantiated

   Usage:

   ```java
   OuterClass.StaticNestedClass staticNested = new OuterClass.StaticNestedClass(); // Static nested class
   OuterClass outer = new OuterClass();
   OuterClass.InnerClass inner = outer.new InnerClass(); // Inner class
   ```

10. **What are anonymous inner classes?**

    Anonymous inner classes are classes without a name that are defined and instantiated at the same time. They are typically used when you need to create a one-time-use class that implements an interface or extends a class.

    Key characteristics:

    1. **No name**: They are declared and instantiated in a single expression
    2. **One-time use**: Can only create one instance of the class
    3. **Can extend a class or implement an interface**: But not both
    4. **Can access final or effectively final local variables**: From the enclosing scope
    5. **Cannot have constructors**: Since they don't have a name

    Example:

    ```java
    // Anonymous class implementing Runnable interface
    Runnable runnable = new Runnable() {
        @Override
        public void run() {
            System.out.println("Running in anonymous class");
        }
    };

    // Anonymous class extending a class
    AbstractClass instance = new AbstractClass() {
        @Override
        public void abstractMethod() {
            System.out.println("Implementation in anonymous class");
        }
    };
    ```

    Common use cases:

    - Event handlers in GUI programming
    - Thread creation
    - Callback implementations
    - Testing and quick prototyping

11. **What is the difference between nested classes and inner classes?**

    Inner classes are a subset of nested classes. The key differences are:

    1. **Scope**:

       - Nested classes is the broader term that includes both static and non-static classes defined within another class
       - Inner classes specifically refer to non-static nested classes only

    2. **Static vs Non-static**:

       - Nested classes can be either static or non-static
       - Inner classes are always non-static

    3. **Access to outer class**:

       - Static nested classes can only access static members of outer class
       - Inner classes can access all members (static and non-static) of outer class

    4. **Instance requirement**:
       - Static nested classes don't require an instance of outer class
       - Inner classes require an instance of outer class to be created

    Example:

    ```java
    class Outer {
        // Static nested class
        static class StaticNested { }

        // Inner class (non-static nested class)
        class Inner { }
    }

    // Usage:
    Outer.StaticNested staticNested = new Outer.StaticNested(); // No outer instance needed
    Outer outer = new Outer();
    Outer.Inner inner = outer.new Inner(); // Requires outer instance
    ```

12. **How to implement classes and objects in Java? What are the members of a class?**

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

13. **What are the different ways to create objects in Java and how is the 'new' operator different from other methods?**

    There are several ways to create objects in Java, each with its own characteristics:

    1. **Using the `new` operator** (Most common):

       - Directly calls the constructor of the class
       - Simple and straightforward syntax

       ```java
       MyClass obj = new MyClass();
       ```

    2. **Using reflection with newInstance()** (Deprecated since Java 9):

       - Creates objects dynamically at runtime
       - Uses reflection to instantiate the class
       - Calls the no-argument constructor

       ```java
       MyClass obj = MyClass.class.newInstance(); // Deprecated
       // Modern approach:
       MyClass obj = MyClass.class.getDeclaredConstructor().newInstance();
       ```

    3. **Using `clone()` method**:

       - Creates a copy of an existing object
       - Class must implement Cloneable interface

       ```java
       MyClass obj1 = new MyClass();
       MyClass obj2 = (MyClass) obj1.clone();
       ```

    4. **Using `Class.forName()`**:

       - Loads the class dynamically and creates instance
       - Useful when class name is determined at runtime

       ```java
       MyClass obj = (MyClass) Class.forName("MyClass").getDeclaredConstructor().newInstance();
       ```

    5. **Using object deserialization**:

       - Recreates object from serialized form
       - Class must implement Serializable interface

       ```java
       ObjectInputStream in = new ObjectInputStream(new FileInputStream("file.ser"));
       MyClass obj = (MyClass) in.readObject();
       in.close();
       ```

    6. **Using factory methods**:
       - Encapsulates object creation in factory class
       - Provides more flexibility in instantiation
       ```java
       MyClass obj = MyClassFactory.createInstance();
       ```

    Key differences between `new` operator and other methods:

    - `new` is compile-time bound, while reflection methods are runtime bound
    - `new` is more performant than reflection-based approaches
    - Reflection methods provide more flexibility but are more complex
    - Factory methods can hide implementation details and provide better abstraction

14. **What are the ways to instantiate the Class class?**

In Java, the `Class` class cannot be instantiated directly using the `new` operator. Instead, instances of the `Class` class are created by the Java Virtual Machine (JVM) when classes are loaded. Here are some common ways to obtain a `Class` object:

1.  **Using `.class` syntax**:

    ```java
    Class<MyClass> clazz = MyClass.class;
    ```

2.  **Using `Class.forName()` method**:

    ```java
    Class<?> clazz = Class.forName("MyClass");
    ```

3.  **Using `getClass()` method on an object**:

    ```java
    MyClass obj = new MyClass();
    Class<?> clazz = obj.getClass();
    ```

4.  **Using `getComponentType()` for arrays**:
    ```java
    int[] array = new int[10];
    Class<?> clazz = array.getClass().getComponentType();
    ```

Each of these methods provides a way to obtain a `Class` object representing a specific class in Java.

14. **What is object cloning?**

    Object cloning in Java is the process of creating an exact copy of an existing object. There are two types of cloning:

    1. **Shallow Clone**: The default behavior of the `clone()` method creates a shallow copy where:

       - Primitive fields are copied with their values
       - Reference fields are copied with their references (both objects point to same memory location)

    2. **Deep Clone**: A complete copy where:
       - Primitive fields are copied with their values
       - Reference fields are copied by creating new objects (separate memory locations)

    To enable cloning, a class must:

    - Implement the `Cloneable` interface (marker interface)
    - Override the `clone()` method from Object class

    Example:

    ```java
    class Student implements Cloneable {
        String name;
        Address addr; // Reference type

        @Override
        public Object clone() throws CloneNotSupportedException {
            return super.clone(); // Shallow clone
        }
    }
    ```

15. **What do you mean by anonymous class?**

    An anonymous class in Java is a class that is defined without a name and is instantiated in a single expression. It is typically used to make the code more concise and to create a one-time use class that extends an existing class or implements an interface. Anonymous classes are often used in situations where a class is needed for a short period of time, such as when implementing event listeners or callbacks.

    Here is an example of an anonymous class:

    ```java
    Button myButton = new Button("Click Me") {
        @Override
        public void onClick() {
            System.out.println("Button clicked!");
        }
    };
    ```

    In this example, an anonymous class is created that extends the `Button` class and overrides the `onClick` method to provide specific behavior when the button is clicked.

16. **What are the differences between subclass and inner class?**

    | Aspect            | Subclass                                                 | Inner Class                                                    |
    | ----------------- | -------------------------------------------------------- | -------------------------------------------------------------- |
    | Definition        | A class that inherits from another class (extends)       | A class defined within another class                           |
    | Relationship      | "is-a" relationship with parent class                    | "has-a" relationship with outer class                          |
    | Access            | Can access only public/protected members of parent class | Can access all members (including private) of outer class      |
    | Declaration       | Declared independently using `extends` keyword           | Declared inside another class                                  |
    | Instance Creation | Can be instantiated independently                        | Requires instance of outer class (except static inner classes) |
    | Inheritance       | Can inherit from only one class                          | Can be defined inside any class regardless of inheritance      |
    | Purpose           | Code reuse and extending functionality                   | Logical grouping and encapsulation                             |
    | Scope             | Available throughout the package/project                 | Limited to the scope of outer class                            |

17. **What are constructors in Java? How many types of constructors are used in Java?**

    Constructors in Java are special methods that are called when an object is instantiated. They have the same name as the class and do not have a return type, not even void. Constructors are used to initialize the object's attributes and allocate memory for the object. There are two types of constructors in Java:

    1. **Default Constructor**: A constructor that does not take any parameters and is used to provide default initialization when no explicit constructor is defined. If no constructor is explicitly created in a class, the Java compiler automatically provides a default constructor.

    Purpose of a Default Constructor:

    - Initializes object instance variables to their default values (0 for numeric types, null for objects, false for boolean)
    - Ensures that an object can be created even without explicit initialization
    - Allows for creating objects with standard initial state
    - Provides a no-argument entry point for object creation

    2. **Parameterized Constructor**: A constructor that takes parameters to initialize an object with specific values at the time of creation.

    Purpose of a Parameterized Constructor:

    - Allows customized initialization of object attributes during object creation
    - Provides flexibility to set different initial states for different objects
    - Enables validation of input values during object instantiation
    - Supports creating objects with specific, meaningful initial configurations
    - Reduces the need for separate setter methods to initialize object state

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

18. **Can you call a constructor of a class inside another constructor? or How can constructor chaining be done using this keyword?**
    Yes, you can call a constructor from another constructor within the same class using `this()`. This is known as constructor chaining. The call to another constructor must be the first statement in the constructor. This is useful for code reuse and avoiding duplicate initialization code.

    Here's an example:

    ```java
    public class Student {
        private String name;
        private int age;
        private String id;

        // Constructor with all parameters
        public Student(String name, int age, String id) {
            this.name = name;
            this.age = age;
            this.id = id;
        }

        // Constructor with two parameters, calls the three-parameter constructor
        public Student(String name, int age) {
            this(name, age, "Not Assigned");
        }

        // Constructor with one parameter, calls the two-parameter constructor
        public Student(String name) {
            this(name, 0);
        }
    }
    ```

    In this example, the constructors are chained together, with each constructor calling another constructor using `this()`. This helps maintain clean and DRY (Don't Repeat Yourself) code.

19. **How can constructor chaining be done by using the super keyword?**
    Constructor chaining can also be done using the `super()` keyword to call a constructor from the parent class. The `super()` call must be the first statement in the constructor. This is useful when you want to reuse initialization code from the parent class.

    Here's an example:

    ```java
    // Parent class
    class Vehicle {
        private String brand;
        private String model;

        public Vehicle(String brand, String model) {
            this.brand = brand;
            this.model = model;
        }

        public Vehicle(String brand) {
            this(brand, "Unknown");  // Calls two-parameter constructor
        }
    }

    // Child class
    class Car extends Vehicle {
        private int numDoors;

        public Car(String brand, String model, int numDoors) {
            super(brand, model);  // Calls parent's two-parameter constructor
            this.numDoors = numDoors;
        }

        public Car(String brand, int numDoors) {
            super(brand);  // Calls parent's one-parameter constructor
            this.numDoors = numDoors;
        }
    }
    ```

    In this example, the `Car` class constructors use `super()` to call constructors from the parent `Vehicle` class, demonstrating constructor chaining between parent and child classes.

20. **What rules that you must follow while creating a constructor in Java?**

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

21. **What are the differences between the constructors and methods?**

    | Aspect           | Constructors                                                     | Methods                                                     |
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

22. **Can we make constructors static?**

    No, constructors cannot be declared as static in Java. Here's why:

    1. Static members belong to the class itself rather than instances
    2. Constructors are specifically for initializing new object instances
    3. The purpose of a constructor contradicts the static concept

    Example of why it's not allowed:

    ```java
    public class Example {
        // This would be invalid:
        static public Example() {  // Compilation error
            // ...
        }

        // Correct constructor:
        public Example() {
            // ...
        }
    }
    ```

    Note: While constructors can't be static, a class can have static factory methods that create and return new instances of the class. These are sometimes used as an alternative to constructors:

    ```java
    public class Example {
        private Example() { }  // Private constructor

        // Static factory method
        public static Example createInstance() {
            return new Example();
        }
    }
    ```

23. **Explain the constructor overloading? Or Can we overload the constructors?**

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

24. **Can you make a constructor final?**

    No, constructors cannot be declared as final in Java. This is because:

    1. **Purpose of Final Keyword**: The `final` keyword is used to prevent inheritance or modification, but constructors are not inherited or overridden.

    2. **Constructors are Not Inherited**: Constructors are not methods that can be inherited by subclasses. They are special methods used for object initialization.

    3. **Compilation Error**: Attempting to declare a constructor as final will result in a compile-time error.

25. **Does a constructor return any value?**

    No, constructors do not return any value, not even void. Their primary purpose is to initialize the object when it is created. Instead of returning a value, a constructor initializes the instance variables of the class and prepares the new object for use.

26. **Is constructor inherited?**

    No, constructors are not inherited in Java. Each class has its own constructors, and they are not accessible to subclasses. When a subclass is created, it does not inherit the constructors of its parent class. However, a subclass can call a parent class constructor using the `super` keyword to initialize inherited fields. This means that while constructors themselves are not inherited, the initialization of inherited properties can be achieved through the parent class's constructors.

27. **What is Copy Constructor in Java? What are the ways to copy the values of one object into another?**

    A Copy Constructor in Java is a constructor that creates a new object by copying the values from another object of the same class. It takes an object of the same class as a parameter and initializes the new object with the same values. Copy constructors are particularly useful when you want to create a new object that has the same state as an existing object.

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

    In addition to using a copy constructor, there are other ways to copy the values of one object into another:

    1. **Clone Method**: Implementing the `Cloneable` interface and overriding the `clone()` method allows for object duplication. However, this requires careful handling of deep vs. shallow copies.

    ```java
    public class Student implements Cloneable {
        private String name;
        private int age;

        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        @Override
        protected Object clone() throws CloneNotSupportedException {
            return super.clone(); // Shallow copy
        }
    }

    // Usage example:
    Student student1 = new Student("John", 20);
    Student student2 = (Student) student1.clone(); // Creates a copy of student1
    ```

    2. **Serialization**: Objects can be serialized and then deserialized to create a copy. This method is useful for deep copying complex objects.

    ```java
    import java.io.*;

    public class Student implements Serializable {
        private String name;
        private int age;

        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        public static Student deepCopy(Student original) {
            try {
                ByteArrayOutputStream byteOut = new ByteArrayOutputStream();
                ObjectOutputStream out = new ObjectOutputStream(byteOut);
                out.writeObject(original);
                ByteArrayInputStream byteIn = new ByteArrayInputStream(byteOut.toByteArray());
                ObjectInputStream in = new ObjectInputStream(byteIn);
                return (Student) in.readObject();
            } catch (IOException | ClassNotFoundException e) {
                e.printStackTrace();
                return null;
            }
        }
    }

    // Usage example:
    Student student1 = new Student("John", 20);
    Student student2 = Student.deepCopy(student1); // Creates a deep copy of student1
    ```

    3. **Manual Copying**: You can manually copy each field from one object to another using setter methods or direct field access, ensuring that you handle reference types appropriately to avoid shared references.

    ```java
    public class Student {
        private String name;
        private int age;

        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }

        // Manual copy method
        public void copyFrom(Student other) {
            this.name = other.name;
            this.age = other.age;
        }
    }

    // Usage example:
    Student student1 = new Student("John", 20);
    Student student2 = new Student("", 0); // Create an empty student
    student2.copyFrom(student1); // Copies values from student1 to student2

    Note: Java does not provide automatic copy constructors like C++. You need to implement them explicitly if needed. Also, when dealing with reference types, be careful to perform a deep copy if required, to avoid sharing references between the original and copied objects.

    ```

28. **What is a private constructor?**
    A private constructor is a constructor declared with the `private` access modifier, which restricts its instantiation from outside the class. Key characteristics include:

    1. **Prevents Direct Instantiation:**

       - Blocks creation of objects from outside the class
       - Ensures the class cannot be directly instantiated

    2. **Common Use Cases:**

       - Implementing Singleton design pattern
       - Creating utility classes with only static methods
       - Controlling object creation and maintaining strict control over object lifecycle

    3. **Example Implementations:**

    ```java
    // Singleton Pattern
    public class DatabaseConnection {
        private static DatabaseConnection instance;

        // Private constructor prevents direct instantiation
        private DatabaseConnection() {
            // Initialization logic
        }

        // Controlled object creation method
        public static DatabaseConnection getInstance() {
            if (instance == null) {
                instance = new DatabaseConnection();
            }
            return instance;
        }
    }

    // Utility Class
    public class MathUtils {
        // Private constructor prevents instantiation
        private MathUtils() {
            throw new AssertionError("Cannot instantiate utility class");
        }

        // Only static methods
        public static int add(int a, int b) {
            return a + b;
        }
    }
    ```

    4. **Benefits:**

       - Enhances encapsulation
       - Provides more control over object creation
       - Prevents unnecessary object instantiation

29. **Can you declare a constructor using static?**

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

30. **What is immutable object?**

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

31. **How can we create an immutable class in Java?**

    To create an immutable class in Java, follow these key steps:

    1. **Make the class final**: Prevent inheritance that could potentially modify the object's state
    2. **Make all fields private and final**: Ensure fields cannot be changed after initialization
    3. **Do not provide setter methods**: Prevent modification of object state after creation
    4. **Initialize all fields in the constructor**: Set values during object creation
    5. **Perform deep copy for mutable fields**: If the class contains mutable objects, return defensive copies

    Example of a comprehensive immutable class:

    ```java
    public final class ImmutableAddress {
        private final String street;
        private final String city;
        private final List<String> phoneNumbers; // Potentially mutable field

        public ImmutableAddress(String street, String city, List<String> phoneNumbers) {
            this.street = street;
            this.city = city;
            // Deep copy of mutable list
            this.phoneNumbers = phoneNumbers == null ?
                new ArrayList<>() :
                new ArrayList<>(phoneNumbers);
        }

        // Getter methods only - no setters
        public String getStreet() {
            return street;
        }

        public String getCity() {
            return city;
        }

        // Defensive copy for mutable field
        public List<String> getPhoneNumbers() {
            return new ArrayList<>(phoneNumbers);
        }
    }
    ```

    This class is immutable because:

    - It's declared final
    - All fields are private and final
    - No setter methods are provided
    - Mutable List is deep copied in constructor and getter
    - No methods can modify the object's state

    Additional considerations:

    - Use wrapper classes for primitive types
    - For complex objects, implement deep copy mechanisms
    - Ensure all methods preserve immutability

32. **What is difference between WeakReference and SoftReference in Java?**

    WeakReference and SoftReference are two types of special reference objects in Java that help with memory management. Here are their key differences:

    **WeakReference:**

    - Objects referenced only by WeakReference are eligible for garbage collection immediately when no strong references exist
    - Commonly used for implementing caches where entries can be reclaimed as soon as they're no longer strongly referenced
    - Garbage collector doesn't consider memory availability when collecting weak references
    - Example use case: WeakHashMap, where entries are removed when keys are no longer referenced

    **SoftReference:**

    - Objects referenced by SoftReference are eligible for garbage collection only when memory is tight
    - JVM will try to keep soft-referenced objects in memory as long as possible until memory is needed
    - Useful for implementing memory-sensitive caches that automatically shrink under memory pressure
    - More likely to survive garbage collection compared to WeakReference

    Example demonstrating both references:

    ```java
    // WeakReference example
    WeakReference<StringBuilder> weakRef = new WeakReference<>(new StringBuilder("Hello"));

    // SoftReference example
    SoftReference<StringBuilder> softRef = new SoftReference<>(new StringBuilder("Hello"));
    ```

    When to use which:

    - Use WeakReference when you want objects to be collected as soon as they're not needed
    - Use SoftReference for memory-sensitive caches that should only be cleared when memory is tight

33. **What are access specifiers? What are the types of access specifiers?**

    Access specifiers in Java are keywords that set the accessibility (visibility) of classes, methods, and other members. They control how the members of a class can be accessed from other classes. The main types of access specifiers in Java are:

    1. **Public**: Members declared as public are accessible from any other class in any package. This means there are no restrictions on the visibility of public members.

    2. **Private**: Members declared as private are accessible only within the class they are declared in. This means that private members cannot be accessed from outside the class, providing a way to encapsulate and protect the data.

    3. **Protected**: Members declared as protected are accessible within the same package and by subclasses, even if they are in different packages.

    4. **Default (Package-Private)**: If no access specifier is declared, the member is accessible only within its own package. This is also known as package-private access.

    By using access specifiers, developers can implement encapsulation, which is a fundamental principle of object-oriented programming, ensuring that the internal representation of an object is hidden from the outside.

34. **Can you access the private method from outside the class?**

    No, private methods cannot be accessed from outside the class where they are declared. This is because:

    1. **Encapsulation**: Private methods are used to implement encapsulation, which means hiding internal implementation details from outside access.

    2. **Access Restriction**: The private access modifier restricts the method's visibility to only within the declaring class.

    3. **Compilation Error**: Any attempt to access a private method from outside its class will result in a compilation error.

    Example demonstrating private method access:

    ```java
    public class MyClass {
        private void privateMethod() {
            System.out.println("Private method");
        }
    }

    public class AnotherClass {
        public void tryToAccess() {
            MyClass obj = new MyClass();
            // obj.privateMethod(); // This will cause compilation error
        }
    }
    ```

    However, there are ways to access private methods indirectly:

    1. Using public methods that internally call private methods
    2. Using Reflection API (though this is generally not recommended for production code)

34. **Can we override the static method? Why can we not override static method?**

    No, static methods cannot be overridden in Java. Here's why:

    1. **Static Methods Belong to Class**: Static methods belong to the class itself, not instances. They are associated with the class rather than objects.

    2. **Compile-time Binding**: Static methods use static binding at compile time. The method call is determined by the reference type, not the actual object type.

    3. **Method Hiding Instead**: When a subclass defines a static method with the same signature as its parent class, it's called method hiding, not overriding.

    Example showing method hiding vs overriding:

    ```java
    class Parent {
        static void staticMethod() {
            System.out.println("Parent static method");
        }
        
        void instanceMethod() {
            System.out.println("Parent instance method"); 
        }
    }

    class Child extends Parent {
        // This is method hiding
        static void staticMethod() {
            System.out.println("Child static method");
        }
        
        // This is method overriding
        @Override
        void instanceMethod() {
            System.out.println("Child instance method");
        }
    }

    public class Test {
        public static void main(String[] args) {
            Parent p = new Child();
            p.staticMethod();   // Prints "Parent static method" - uses reference type
            p.instanceMethod(); // Prints "Child instance method" - uses object type
        }
    }
    ```

    The key points are:
    - Static methods are bound at compile-time based on the reference type
    - Instance methods are bound at runtime based on the actual object type
    - Static methods can be hidden but not overridden
    - The @Override annotation will cause a compilation error if used with static methods

35. **Can we override the private methods?**

    No, private methods cannot be overridden in Java. This is because:

    1. **Visibility Restriction**: Private methods are not visible to subclasses. When a method is declared as private, it is only accessible within the same class where it is defined.

    2. **Inheritance Limitation**: Subclasses cannot access private methods of their parent class, which means they cannot provide a new implementation of a private method.

    Example demonstrating the impossibility of overriding private methods:

    ```java
    class Parent {
        private void privateMethod() {
            System.out.println("Private method in Parent");
        }
    }

    class Child extends Parent {
        // This is NOT overriding, but a new method in the Child class
        private void privateMethod() {
            System.out.println("Private method in Child");
        }
    }

    public class Test {
        public static void main(String[] args) {
            // The private methods remain separate and are not overridden
            Parent parent = new Parent();
            Child child = new Child();
        }
    }
    ```

    Key points:

    - Private methods are not inherited by subclasses
    - A method with the same name in a subclass is treated as a completely separate method
    - True method overriding requires the method to be accessible to the subclass

36. **Is it possible to overload the static methods in Java?**

    Yes, it is possible to overload static methods in Java. Method overloading occurs when two or more methods in the same class have the same name but different parameters (different type, number, or both). Since static methods are resolved at compile time based on the method signature, you can have multiple static methods with the same name as long as their parameter lists differ.

    Example of static method overloading:

    ```java
    class MathUtils {
        static int add(int a, int b) {
            return a + b;
        }

        static double add(double a, double b) {
            return a + b;
        }

        static int add(int a, int b, int c) {
            return a + b + c;
        }
    }

    public class Test {
        public static void main(String[] args) {
            System.out.println(MathUtils.add(5, 10));         // Calls the first method
            System.out.println(MathUtils.add(5.5, 10.5));     // Calls the second method
            System.out.println(MathUtils.add(5, 10, 15));      // Calls the third method
        }
    }
    ```

    In this example, the `add` method is overloaded with different parameter types and counts, demonstrating that static methods can indeed be overloaded.

37. **What is method overloading with type promotion?**

    Type promotion in method overloading refers to Java's automatic widening of primitive data types when matching method calls to overloaded methods. When an exact match is not found, Java will automatically promote the argument to a wider type to find a matching method.

    Example of type promotion in overloaded methods:

    ```java
    class Calculator {
        static void calculate(int x) {
            System.out.println("Using int: " + x);
        }

        static void calculate(double x) {
            System.out.println("Using double: " + x);
        }
    }

    public class Test {
        public static void main(String[] args) {
            byte b = 25;
            Calculator.calculate(b);  // Promotes byte to int

            float f = 25.5f;
            Calculator.calculate(f);  // Promotes float to double
        }
    }
    ```

    The promotion follows these rules:

    - byte → short → int → long → float → double
    - char → int → long → float → double

    When calling `calculate(b)`, even though there's no method that takes a byte parameter, Java promotes the byte to int and calls the first method. Similarly, the float argument is promoted to double for the second method call.

38. **Can we overload the methods by making them static?**

    No, we cannot overload methods just by making them static. Method overloading in Java is based on having different parameter lists (different number or types of parameters). The static modifier does not affect the method signature and therefore cannot be used as a basis for overloading.

    Example of invalid overloading with static:

    ```java
    class Example {
        public void display() {
            System.out.println("Non-static method");
        }

        public static void display() {  // Compilation error
            System.out.println("Static method");
        }
    }
    ```

    To properly overload methods, you need to change the parameter list:

    ```java
    class Example {
        public static void display() {
            System.out.println("No parameters");
        }

        public static void display(String msg) {  // Valid overload
            System.out.println(msg);
        }

        public void display(int num) {  // Valid overload (can mix static and non-static)
            System.out.println(num);
        }
    }
    ```

39. **What are the restrictions that are applied to the Java static methods?**

    There are several important restrictions that apply to static methods in Java:

    1. **Cannot access non-static members directly**

       - Static methods cannot directly access non-static (instance) variables or methods
       - They can only access other static members of the class
       - To access instance members, they need an object reference

    2. **Cannot use 'this' or 'super' keywords**

       - The 'this' keyword refers to the current instance, which doesn't exist in static context
       - The 'super' keyword refers to parent instance, which also doesn't exist in static context

    3. **Method overriding restrictions**

       - Static methods cannot be overridden (they can only be hidden)
       - If a child class defines same static method as parent, it's method hiding, not overriding

    4. **No abstract static methods**
       - Static methods cannot be declared as abstract
       - Abstract methods need to be overridden, which static methods cannot do

    Example demonstrating these restrictions:

    ```java
    public class StaticRestrictions {
        private int instanceVar = 10;
        private static int staticVar = 20;

        // Cannot access instanceVar directly
        public static void staticMethod() {
            // System.out.println(instanceVar);     // Error: Cannot access instance variable
            System.out.println(staticVar);          // OK: Can access static variable

            StaticRestrictions obj = new StaticRestrictions();
            System.out.println(obj.instanceVar);    // OK: Accessing via object reference
        }
    }
    ```

40. **What is the use of static variables and methods? or What is the purpose of static methods and variables?**

    | Feature           | Static Variables                                                                           | Static Methods                                                      |
    | ----------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
    | Memory Allocation | Single copy shared across all instances of the class                                       | Belongs to class rather than any instance                           |
    | Access            | Can be accessed without creating class instance                                            | Can be called without creating class instance                       |
    | Usage             | Common properties shared by all instances (e.g., counters, constants)                      | Utility functions that don't need instance data                     |
    | Instance Access   | Cannot directly access non-static members                                                  | Cannot directly access non-static members                           |
    | Memory Efficiency | Saves memory by avoiding multiple copies                                                   | N/A                                                                 |
    | Example Use Cases | - Counter for number of objects created<br>- Configuration constants<br>- Shared resources | - Math utility functions<br>- Factory methods<br>- Helper functions |

    Example demonstrating both static variables and methods:

    ```java
    public class MathOperations {
        // Static variable shared across all instances
        private static final double PI = 3.14159;  // Constant value
        private static int calculationCount = 0;   // Tracks number of calculations

        // Static method for utility calculation
        public static double calculateCircleArea(double radius) {
            calculationCount++;  // Increment shared counter
            return PI * radius * radius;
        }

        // Static method to get calculation statistics
        public static int getCalculationCount() {
            return calculationCount;
        }
    }
    ```

    Key Benefits:

    1. Memory Efficiency: Single copy of data/method shared by all instances
    2. Global Accessibility: Can be accessed without object instantiation
    3. Utility and Helper Functions: Provide common functionality
    4. Tracking and Counting: Maintain class-level state

41. **What is a singleton class in Java? Describe the singleton pattern with an example.**

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

42. **What is encapsulation? Explain encapsulation with an example.**

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

43. **What is inheritance and what are its types in Java?**

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

44. **Why is multiple inheritance not supported in java?**

    Multiple inheritance is not supported in Java through classes for several key reasons:

    1. **Diamond Problem**: The main reason is to avoid the "diamond problem" that can occur when a class inherits from two classes that have the same method. This creates ambiguity about which method implementation should be used.

    2. **Complexity**: Multiple inheritance can make the code more complex and harder to maintain, as it can create complicated inheritance hierarchies.

    3. **Simplicity**: Java's designers chose to favor simplicity over the flexibility of multiple inheritance.

    Instead, Java provides alternatives:

    - Interfaces can be used to implement multiple inheritance of behavior
    - A class can implement multiple interfaces
    - The composition pattern can be used as an alternative to multiple inheritance

    Example of the Diamond Problem:

    ```java
    class A { void method() {} }
    class B extends A { void method() {} }
    class C extends A { void method() {} }
    // If this were allowed:
    // class D extends B, C {} // Which method() would D inherit?
    ```

45. **Why is Inheritance used in Java?**

    Inheritance in Java is used for several important reasons:

    1. **Code Reusability**: Inheritance allows you to reuse code from existing classes, reducing code duplication and making maintenance easier.

    2. **Method Overriding**: Child classes can provide specific implementations of methods defined in parent classes, enabling runtime polymorphism.

    3. **IS-A Relationship**: Inheritance establishes a clear hierarchical relationship between classes (e.g., Dog IS-A Animal), making code more logical and organized.

    4. **Extensibility**: New classes can be created based on existing classes, allowing for easy extension of functionality without modifying the original code.

    5. **Data Hiding**: Protected members in the parent class remain hidden from the outside world but are accessible to child classes, promoting encapsulation.

    6. **Method Extension**: Child classes can add new methods while inheriting existing ones, expanding functionality in a structured way.

    For example, in the Animal-Dog relationship shown earlier, the Dog class inherits common animal behaviors (eat, sleep) while adding specific dog behaviors (bark), demonstrating efficient code organization and reuse.

46. **What do you mean by Polymorphism and what are its types?**

    Polymorphism means "many forms" and is one of the core concepts of object-oriented programming. It allows objects to be treated as instances of their parent class rather than their actual class. In Java, there are two main types of polymorphism:

    1. **Runtime Polymorphism (Dynamic/Late Binding)**

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

    2. **Compile-time Polymorphism (Static/Early Binding)**

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

47. **What is the difference between compile-time polymorphism and runtime polymorphism?**

    | Feature              | Compile-time Polymorphism                                          | Runtime Polymorphism                                   |
    | -------------------- | ------------------------------------------------------------------ | ------------------------------------------------------ |
    | **Also Known As**    | Static Binding, Method Overloading                                 | Dynamic Binding, Method Overriding                     |
    | **When Resolved**    | During compilation                                                 | During program execution                               |
    | **How Achieved**     | Multiple methods with same name but different parameters           | Method overriding in inherited classes                 |
    | **Binding**          | Static - based on reference type                                   | Dynamic - based on object type                         |
    | **Method Selection** | Based on method signature and parameter types                      | Based on actual object type at runtime                 |
    | **Performance**      | Slightly better as resolved at compile time                        | Small overhead due to runtime resolution               |
    | **Example Usage**    | Multiple versions of methods like `print(int)` and `print(String)` | Parent class reference holding child class object      |
    | **Flexibility**      | Limited to method overloading within same class                    | More flexible as behavior changes based on object type |

48. **What is the interface?**

    An interface is a blueprint of a class that contains only abstract methods, constants, default methods, static methods, and nested types. It specifies what a class must do but not how it should do it. Key points about interfaces:

    - All methods in an interface are implicitly public and abstract (except default and static methods)
    - All fields are implicitly public, static, and final
    - A class can implement multiple interfaces
    - Interfaces support multiple inheritance

    Example:

    ```java
    interface Animal {
        // constant
        String CATEGORY = "Domestic";

        // abstract method
        void makeSound();

        // default method
        default void eat() {
            System.out.println("Animal is eating");
        }

        // static method
        static void info() {
            System.out.println("Animal Interface");
        }
    }

    class Dog implements Animal {
        @Override
        public void makeSound() {
            System.out.println("Woof!");
        }
    }
    ```

49. **What is the nested interface? Can a class have an interface?**

    A nested interface is an interface declared within another class or interface. Key points about nested interfaces:

    - Can be declared as public, private, or protected (if inside a class)
    - Are implicitly static when declared inside an interface
    - Can access members of the enclosing class/interface
    - Help organize related interfaces together

    Example:

    ```java
    class OuterClass {
        // Nested interface in a class
        interface NestedInterface {
            void nestedMethod();
        }
    }

    interface OuterInterface {
        // Nested interface in an interface
        interface InnerInterface {
            void innerMethod();
        }
    }

    // Implementing nested interface
    class MyClass implements OuterClass.NestedInterface {
        @Override
        public void nestedMethod() {
            System.out.println("Nested method implementation");
        }
    }
    ```

50. **Can an Interface have a class?**

    Yes, an interface can have a class. This is known as a member class or nested class within an interface. Key points:

    - Classes inside interfaces are implicitly public and static
    - They can implement the enclosing interface or other interfaces
    - They can be instantiated and used like regular classes
    - Useful for providing default implementations or helper classes

    Example:

    ```java
    interface OuterInterface {
        void outerMethod();

        // Nested class in interface
        class NestedClass implements OuterInterface {
            @Override
            public void outerMethod() {
                System.out.println("Implementation in nested class");
            }
        }
    }
    ```

51. **Can we declare an interface as final?**

    No, an interface cannot be declared as final. This is because:

    - The `final` keyword prevents inheritance/implementation
    - Interfaces are meant to be implemented by classes
    - It would contradict the core purpose of interfaces which is to define a contract for classes to implement
    - The compiler will generate an error if you try to declare an interface as final

    Example of invalid code:

    ```java
    final interface MyInterface { // Compiler Error
        void myMethod();
    }
    ```

52. **What do you mean by abstraction and how it is achieved in Java?**

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

53. **What is the difference between extends and implements?**

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

54. **What is the difference between loose coupling and tight coupling?**

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

55. **What is the difference between cohesion and coupling?**

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

56. **What is a Marker Interface?**

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

57. **What is an abstract class? Explain its purpose and when to use it.**

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

58. **Can there be an abstract method without an abstract class?**

    Yes, abstract methods can exist without an abstract class when they are declared in an interface. In Java, interface methods are implicitly abstract (unless marked as default or static).

    For example:

    ```java
    public interface Animal {
        void makeSound(); // abstract method in interface
    }
    ```

    However, within a regular class (non-interface):

    - Abstract methods can only exist in abstract classes
    - The class must be declared abstract if it contains any abstract methods
    - Abstract methods in the class must be implemented by concrete subclasses

59. **Can you use abstract and final both with a method?**

    No, you cannot use both abstract and final modifiers with a method. This is because:

    1. abstract methods must be overridden by subclasses
    2. final methods cannot be overridden

    These are contradictory requirements - a method cannot be both required to be overridden and prevented from being overridden at the same time.

    Example of invalid code:

    ```java
    public abstract class Example {
        // This will cause a compilation error
        public abstract final void method(); // Cannot combine abstract and final
    }
    ```

60. **Is it possible to instantiate the abstract class?**

    No, it is not possible to instantiate an abstract class directly. Abstract classes are incomplete by design and can only be used as superclasses.

    For example:

    ```java
    public abstract class Animal {
        protected String name;

        public abstract void makeSound(); // abstract method
    }

    // This will cause compilation error:
    Animal animal = new Animal(); // Cannot instantiate abstract class

    // Instead, you must create a concrete subclass:
    public class Dog extends Animal {
        @Override
        public void makeSound() {
            System.out.println("Woof!");
        }
    }

    // Then instantiate the concrete class:
    Animal animal = new Dog(); // This is valid
    ```

    The only way to use an abstract class is to:

    1. Create a concrete subclass that extends it
    2. Implement all abstract methods in the subclass
    3. Instantiate the concrete subclass

61. **Can we define a class Abstract even if it does not have any abstract methods?**

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

62. **Can you make abstract methods static in Java?**

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

63. **Can we declare the static variables and methods in an abstract class?**

    Yes, we can declare static variables and methods in an abstract class. This is because:

    1. Static members belong to the class itself, not to any specific instance
    2. They can be accessed without creating an instance of the abstract class
    3. They provide utility functions that are related to the abstract class but don't require instance-specific data

    Example:

    ```java
    public abstract class Shape {
        // Static variable
        public static final double PI = 3.14159;

        // Static method
        public static double convertToRadians(double degrees) {
            return degrees * (PI / 180);
        }

        // Abstract method
        public abstract double calculateArea();
    }
    ```

    In this example:

    - The static variable `PI` can be accessed as `Shape.PI`
    - The static method `convertToRadians()` can be called as `Shape.convertToRadians(90)`
    - Both can be used without creating an instance of Shape

64. **Can you declare an interface method static?**

    Yes, starting from Java 8, you can declare static methods in interfaces. Static interface methods:

    1. Must have an implementation
    2. Cannot be overridden by implementing classes
    3. Can only be accessed through the interface name

    Example:

    ```java
    public interface Calculator {
        // Static method in interface
        static int add(int a, int b) {
            return a + b;
        }
    }
    ```

    To call this method:

    ```java
    int sum = Calculator.add(5, 3); // Called using interface name
    ```

    Static methods in interfaces are commonly used to provide utility methods that are related to the interface's purpose but don't require access to instance-specific data.

65. **What are the differences between abstract class and interface?**

    | Aspect                | Abstract Class                                                                       | Interface                                                                                                               |
    | --------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
    | Definition            | A class that cannot be instantiated and can have both abstract and concrete methods. | A reference type that can contain only constants, method signatures, default methods, static methods, and nested types. |
    | Inheritance           | Supports single inheritance (a class can extend only one abstract class).            | Supports multiple inheritance (a class can implement multiple interfaces).                                              |
    | Method Implementation | Can have both abstract methods (without body) and concrete methods (with body).      | All methods are abstract by default (unless they are default or static methods).                                        |
    | Constructor           | Can have constructors.                                                               | Cannot have constructors.                                                                                               |
    | Access Modifiers      | Can have access modifiers (public, protected, private).                              | All methods are public by default; cannot have access modifiers.                                                        |
    | Use Case              | Used when classes share a common base and behavior.                                  | Used to define a contract that implementing classes must follow.                                                        |

66. **What do you mean by association? What are the types of associations?**

    Association in object-oriented programming refers to a relationship between two classes that establishes a connection between them. It signifies that one class (the client) uses or interacts with another class (the supplier). Associations can be categorized into three main types:

    1. **One-to-One Association**: A single instance of a class is associated with a single instance of another class. For example, a person and their passport.

    2. **One-to-Many Association**: A single instance of a class is associated with multiple instances of another class. For example, a teacher and their students.

    3. **Many-to-Many Association**: Multiple instances of one class are associated with multiple instances of another class. For example, students and courses, where students can enroll in multiple courses and each course can have multiple students.

    4. **Many-to-one Association**: Multiple instances of one class are associated with a single instance of another class. For example, a car and its engine.

    Understanding these associations helps in designing systems that accurately represent real-world relationships between entities.

67. **What is aggregation?**

    Aggregation is a special form of association that represents a "has-a" relationship between two classes, where one class (the whole) contains or is composed of other classes (the parts), but the parts can exist independently of the whole. It represents a weak ownership relationship between objects.

    Example:

    ```java
    class Department {
        private List<Teacher> teachers; // Aggregation - teachers can exist without department

        public Department() {
            teachers = new ArrayList<>();
        }

        public void addTeacher(Teacher teacher) {
            teachers.add(teacher);
        }
    }

    class Teacher {
        private String name;

        public Teacher(String name) {
            this.name = name;
        }
    }
    ```

    In this example:

    - A Department has multiple Teachers (aggregation relationship)
    - Teachers can exist independently of the Department
    - If the Department is destroyed, the Teacher objects continue to exist
    - The same Teacher object could potentially belong to multiple Departments

68. **What is composition?**

    Composition is a strong form of association that represents a "part-of" relationship between classes, where one class (the whole) contains instances of other classes (the parts) and is responsible for their lifecycle. In composition, the child (part) cannot exist without the parent (whole).

    Key characteristics:

    - The child object's lifecycle is dependent on the parent object
    - When the parent is destroyed, all child objects are also destroyed
    - The child cannot exist independently of the parent
    - The child is exclusively owned by one parent

    Example:

    ```java
    class Engine {
        private String type;

        public Engine(String type) {
            this.type = type;
        }
    }

    class Car {
        private final Engine engine; // Composition - engine cannot exist without car

        public Car() {
            engine = new Engine("V8"); // Engine is created with Car
        }
        // When Car is destroyed, Engine is automatically destroyed
    }
    ```

    In this example, the Engine is composed within the Car. The Engine cannot exist without the Car, and when the Car object is destroyed, its Engine instance is also destroyed. This demonstrates the strong lifecycle dependency characteristic of composition.

69. **Difference between Composition and Aggregation. How to use them?**

    Composition and Aggregation are two types of object relationships in OOP, with key differences in how tightly coupled the objects are:

    **Composition:**
    - Represents a "part-of" relationship where the child (part) cannot exist without the parent (whole)
    - The child's lifecycle is completely dependent on the parent
    - When parent is destroyed, all child objects are destroyed
    - Child belongs to only one parent at a time
    - Example: Car and Engine

    ```java
    class Engine {
        private String type;
        
        public Engine(String type) {
            this.type = type;
        }
    }

    class Car {
        private final Engine engine; // Composition - Engine cannot exist without Car
        
        public Car() {
            engine = new Engine("V8"); // Engine created with Car
        }
    }
    ```

    **Aggregation:**
    - Represents a "has-a" relationship where child can exist independently
    - Child objects can outlive the parent
    - When parent is destroyed, children continue to exist
    - Child can belong to multiple parents
    - Example: Department and Teachers

    ```java
    class Department {
        private List<Teacher> teachers; // Aggregation - Teachers can exist independently
        
        public Department() {
            teachers = new ArrayList<>();
        }
        
        public void addTeacher(Teacher teacher) {
            teachers.add(teacher);
        }
    }
    ```

    **When to use which:**
    
    **Composition Example - Computer Parts:**
    ```java
    class CPU {
        private String processor;
        private int cores;
        
        public CPU(String processor, int cores) {
            this.processor = processor;
            this.cores = cores;
        }
    }
    
    class Computer {
        private final CPU cpu;        // CPU cannot exist without computer
        private final Memory memory;  // Memory cannot exist without computer
        
        public Computer() {
            this.cpu = new CPU("Intel i7", 8);     // Created with computer
            this.memory = new Memory("DDR4", 16);  // Created with computer
        }
        // When Computer is destroyed, CPU and Memory are also destroyed
    }
    ```
    
    **Aggregation Example - Library System:**
    ```java
    class Book {
        private String title;
        private String author;
        
        public Book(String title, String author) {
            this.title = title;
            this.author = author;
        }
    }
    
    class Library {
        private List<Book> books;  // Books can exist independently
        
        public Library() {
            this.books = new ArrayList<>();
        }
        
        public void addBook(Book book) {  // Books can be added
            books.add(book);
        }
        
        public void removeBook(Book book) {  // Books can be removed and still exist
            books.remove(book);
        }
        // Books continue to exist even if Library is destroyed
    }
    ```

69. **What is the difference between composition, aggregation, and association?**

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

70. **What is the difference between aggregation and composition?**

    | Aspect       | Aggregation                   | Composition                          |
    | ------------ | ----------------------------- | ------------------------------------ |
    | Relationship | "Has-A" (Weak)                | "Part-Of" (Strong)                   |
    | Lifetime     | Parts can exist independently | Parts cannot exist without the whole |
    | Ownership    | Shared/No ownership           | Strong ownership                     |
    | Dependency   | Low coupling                  | High coupling                        |
    | Example      | University has Students       | Car has Engine                       |

    As shown in the code above:

    - Composition: The Car class demonstrates composition with Engine. The Engine is created when Car is created and destroyed when Car is destroyed. Engine cannot exist without Car.

    - Aggregation: The University class shows aggregation with Student. Students can exist independently of University, and the University simply maintains a collection of Student references. When University is destroyed, the Students continue to exist.

71. **What is the difference between Inheritance and Composition?**

    | Aspect         | Inheritance                           | Composition                               |
    | -------------- | ------------------------------------- | ----------------------------------------- |
    | Relationship   | "Is-A"                                | "Has-A"                                   |
    | Implementation | Extends another class                 | Contains instance of another class        |
    | Coupling       | Tight coupling                        | Loose coupling                            |
    | Flexibility    | Less flexible (fixed at compile time) | More flexible (can be changed at runtime) |
    | Code Reuse     | Reuses code through class extension   | Reuses code through object composition    |
    | Access         | Can access protected members          | Can only access public interface          |
    | Polymorphism   | Supports polymorphic behavior         | Delegates to contained objects            |
    | Example        | Dog is an Animal                      | Car has an Engine                         |

    Example:

    ```java
    // Inheritance
    class Animal {
        void eat() { }
    }
    class Dog extends Animal { } // Dog IS-A Animal

    // Composition
    class Engine {
        void start() { }
    }
    class Car {
        private Engine engine; // Car HAS-A Engine
    }
    ```

    Key differences:

    - Inheritance represents an "is-a" relationship while composition represents a "has-a" relationship
    - Inheritance creates tighter coupling between classes compared to composition
    - Composition is generally preferred when possible ("favor composition over inheritance") as it provides more flexibility and looser coupling
    - Inheritance breaks encapsulation as child classes can access protected members of parent class

72. **What are the differences between method overloading and overriding?**

    | Aspect          | Method Overloading                                                                                                                                                                                                                                                                                                                              | Method Overriding                                                                                                                                                                                                                                                                                                               |
    | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | Definition      | Multiple methods with same name but different parameters in same class                                                                                                                                                                                                                                                                          | Subclass provides specific implementation of superclass method                                                                                                                                                                                                                                                                  |
    | Parameters      | Must have different parameters (type, number, or both)                                                                                                                                                                                                                                                                                          | Must have same parameters as superclass method                                                                                                                                                                                                                                                                                  |
    | Return Type     | Can be different                                                                                                                                                                                                                                                                                                                                | Must be same or covariant (subtype)                                                                                                                                                                                                                                                                                             |
    | Access Modifier | Can be different                                                                                                                                                                                                                                                                                                                                | Must be same or less restrictive                                                                                                                                                                                                                                                                                                |
    | Binding         | Static/Compile-time binding                                                                                                                                                                                                                                                                                                                     | Dynamic/Runtime binding                                                                                                                                                                                                                                                                                                         |
    | Inheritance     | Not related to inheritance                                                                                                                                                                                                                                                                                                                      | Requires inheritance relationship                                                                                                                                                                                                                                                                                               |
    | @Override       | Not required                                                                                                                                                                                                                                                                                                                                    | Recommended to use                                                                                                                                                                                                                                                                                                              |
    | Purpose         | Provides different ways to call similar method                                                                                                                                                                                                                                                                                                  | Provides specific implementation of inherited method                                                                                                                                                                                                                                                                            |
    | Rules           | - Methods must have same name but different parameter lists <br> - Parameter differences can be in number, type, or order <br> - Return type can be different <br> - Access modifiers can be different <br> - Can be done in same class or inherited class <br> - Cannot overload by only changing return type <br> - Compile-time polymorphism | - Method signature must be exactly same (name and parameters) <br> - Return type must be same or covariant <br> - Access modifier must be same or less restrictive <br> - Cannot override final or static methods <br> - Must have inheritance relationship <br> - @Override annotation recommended <br> - Runtime polymorphism |

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

73. **Why is method overloading not possible by changing the return type in java?**

    Method overloading in Java cannot be achieved by only changing the return type because:

    1. The method signature in Java only includes:

       - Method name
       - Parameter list (types and order)

    2. Return type is not part of the method signature

    Example of invalid overloading:

    ```java
    public int getValue() { return 1; }
    public double getValue() { return 1.0; } // Compilation error
    ```

    The compiler would not know which method to call in cases like:

    ```java
    getValue(); // Ambiguous - which method should be called?
    ```

    To successfully overload methods, you must change the parameter list:

    ```java
    public int getValue() { return 1; }
    public int getValue(int x) { return x; }     // Valid overload
    public double getValue(double x) { return x; } // Valid overload
    ```

74. **What is the difference between Java Dynamic Binding and Static Binding?**

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

75. **What is an Instance Initializer Block? Characteristics of Instance Initializer Block?**

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

76. **What is a static block in Java?**

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

77. **What is the purpose of static members in Java?**

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

78. **Explain the use of final keyword in variable, method and class**

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

79. **What is the difference between the final method and abstract method?**

    | Feature            | Final Method                                     | Abstract Method                                                       |
    | ------------------ | ------------------------------------------------ | --------------------------------------------------------------------- |
    | **Definition**     | A method that cannot be overridden by subclasses | A method without implementation that must be overridden by subclasses |
    | **Implementation** | Must have complete implementation                | Has no implementation (only method declaration)                       |
    | **Inheritance**    | Cannot be overridden in child classes            | Must be overridden in non-abstract child classes                      |
    | **Usage**          | Used to prevent method overriding                | Used to enforce implementation in child classes                       |
    | **Class Type**     | Can be in any concrete class                     | Can only be in abstract classes or interfaces                         |
    | **Method Body**    | Must have method body                            | Cannot have method body (except default methods in interfaces)        |
    | **Purpose**        | To preserve implementation across inheritance    | To achieve abstraction and polymorphism                               |

80. **What is the difference between encapsulation and abstraction?**

    | Feature            | Encapsulation                                                                                               | Abstraction                                                                                        |
    | ------------------ | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
    | **Definition**     | Bundling of data (attributes) and methods (functions) that operate on the data within a single unit (class) | Hiding the complex implementation details and showing only the essential features of an object     |
    | **Purpose**        | To restrict direct access to some of the object's components and protect the integrity of the data          | To reduce complexity by focusing on what an object does rather than how it does it                 |
    | **Implementation** | Achieved through access modifiers (private, protected, public) and getter/setter methods                    | Achieved through abstract classes and interfaces                                                   |
    | **Example**        | A class with private fields and public methods to access and modify those fields                            | An interface defining methods without implementation, allowing different classes to implement them |
    | **Focus**          | Focuses on the internal state and behavior of an object                                                     | Focuses on the external interface and functionality of an object                                   |

81. **Can we use both final & abstract keywords with a method?**

    No, we cannot use both final and abstract keywords with a method. A method declared as abstract must be implemented by subclasses, while a final method cannot be overridden. Therefore, it is contradictory to declare a method as both final and abstract, as one implies that the method cannot change, while the other requires it to be defined in a subclass.

82. **Can we declare a method as final in an interface?**  
    No, we cannot declare a method as final in an interface. In Java, all methods in an interface are implicitly abstract (prior to Java 8) and cannot have a body. Since final methods cannot be overridden, it contradicts the purpose of an interface, which is to provide a contract for classes to implement. However, from Java 8 onwards, interfaces can have default and static methods, but these cannot be declared as final either, as they are meant to be overridden in implementing classes if desired.

83. **Can an interface extend another interface?**  
    Yes, an interface can extend another interface in Java. When an interface extends another interface, it inherits all the abstract methods of the parent interface. A class that implements the child interface must provide implementations for all the methods declared in both the child and parent interfaces. This allows for a more flexible and modular design in object-oriented programming.

    Here's an example demonstrating interface extension:

    ```java
    interface Animal {
        void makeSound();
    }

    interface Pet extends Animal {
        void play();
    }

    class Dog implements Pet {
        @Override
        public void makeSound() {
            System.out.println("Woof!");
        }

        @Override
        public void play() {
            System.out.println("The dog is playing.");
        }
    }

    public class Test {
        public static void main(String[] args) {
            Dog dog = new Dog();
            dog.makeSound(); // Outputs: Woof!
            dog.play();      // Outputs: The dog is playing.
        }
    }
    ```

84. **Does Java work as a "pass by value" or "pass by reference" phenomenon?**
    Java is strictly pass-by-value. However, this can be confusing because when passing objects, the value being passed is actually a reference to the object. This means:

    1. For primitive types (int, double, etc.): The actual value is passed
    2. For objects: A copy of the reference (memory address) is passed

    Here's an example to illustrate:

    ```java
    public class PassByValueExample {
        public static void main(String[] args) {
            // Primitive type example
            int x = 10;
            changeValue(x);
            System.out.println(x);  // Prints 10 (unchanged)

            // Object reference example
            StringBuilder str = new StringBuilder("Hello");
            changeObject(str);
            System.out.println(str);  // Prints "Hello World" (changed)

            // But if we reassign the reference
            replaceObject(str);
            System.out.println(str);  // Still prints "Hello World" (unchanged)
        }

        static void changeValue(int a) {
            a = 20;  // Only changes local copy
        }

        static void changeObject(StringBuilder s) {
            s.append(" World");  // Modifies the object through reference
        }

        static void replaceObject(StringBuilder s) {
            s = new StringBuilder("New String");  // Only changes local reference
        }
    }
    ```

    This behavior occurs because when passing an object, Java creates a copy of the reference, but both references point to the same object in memory. If you modify the object through either reference, the changes are visible through both references. However, if you reassign the parameter to a new object, it only affects the local copy of the reference.

85. **Which Java operator is right associative?**
    In Java, several operators are right associative:

    1. Assignment operators (=, +=, -=, \*=, /=, %=, etc.)
    2. Unary operators (++, --, +, -, ~, !)
    3. Conditional operator (?:)
    4. Lambda operator (->)

    Right associative means the operations are grouped from right to left. For example:

    ```java
    a = b = c = 10;  // Evaluated as: a = (b = (c = 10))
    ```

    This is different from most binary operators which are left associative (grouped left to right).

86. **What is the covariant return type?**
    Covariant return type is a feature introduced in Java 5 that allows a method in a subclass to override a method in a superclass by returning a subtype of the original return type. This provides more type-specific return values while maintaining type safety.

    For example:

    ```java
    class Animal {
        Animal getType() {
            return new Animal();
        }
    }

    class Dog extends Animal {
        @Override
        Dog getType() {  // Returns Dog instead of Animal
            return new Dog();
        }
    }
    ```

    In this example, `Dog.getType()` returns a `Dog` object instead of an `Animal` object, even though it's overriding `Animal.getType()`. This is possible because `Dog` is a subtype of `Animal`.

87. **Difference between static methods, static variables, and static classes in Java.**

    | Feature         | Static Methods                                         | Static Variables                                         | Static Classes                                   |
    | --------------- | ------------------------------------------------------ | -------------------------------------------------------- | ------------------------------------------------ |
    | Definition      | Methods that belong to the class rather than instances | Variables that belong to the class rather than instances | Nested classes declared as static                |
    | Memory          | Loaded into memory when class is loaded                | Single copy shared across all instances                  | No instance needed to access                     |
    | Access          | Can be called without creating class instance          | Can be accessed without creating class instance          | Can be instantiated without outer class instance |
    | Instance Access | Cannot directly access instance members                | Cannot access instance variables directly                | Cannot access non-static members of outer class  |
    | Usage Example   | `Math.sqrt(4)`                                         | `Math.PI`                                                | `static class Config {...}`                      |
    | Inheritance     | Cannot be overridden (but can be hidden)               | Inherited but shared across all subclasses               | Can be inherited if nested class is extended     |
    | Purpose         | Utility functions, factory methods                     | Constants, counters, utility values                      | Independent nested classes, helper classes       |

88. **Explain the use of the final keyword in variable, method and class.**
    The `final` keyword in Java has different implications depending on where it's used:

    1. **Final Variables:**

       - Once initialized, cannot be reassigned
       - Must be initialized either at declaration or in constructor
       - Commonly used for constants: `final double PI = 3.14159;`
       - For reference variables, the reference cannot change but object state can

    2. **Final Methods:**

       - Cannot be overridden by subclasses
       - Prevents method behavior from being changed
       - Useful for core functionality that must remain consistent
       - Example: `final void calculateTax() { ... }`

    3. **Final Classes:**
       - Cannot be inherited/extended
       - Prevents class from being subclassed
       - Used when class implementation must be immutable
       - Example: Java's String class is final

    Example:

    ```java
    final class ImmutableClass {
        final int constant = 100;
        final void secureMethod() {
            // Cannot be overridden
        }
    }
    ```

89. **Dynamic Method Dispatch in Java**

    - A mechanism where a method call is resolved at runtime rather than compile time
    - Enables runtime polymorphism through method overriding
    - The method that gets called is determined by the actual object type, not the reference type
    - Only works with overridden methods, not overloaded methods
    - Example:

    ```java
    Animal animal = new Dog(); // Animal is superclass, Dog is subclass
    animal.makeSound();       // Calls Dog's makeSound() at runtime
    ```

90. **Can we use private or protected member variables in an interface?**

    - No, interface fields are implicitly public, static and final
    - Prior to Java 9, interface members could only be public
    - Since Java 9, interfaces can have private methods but still cannot have protected members
    - Any fields declared in an interface must be constants (public static final)

    Example:

    ```java
    interface Example {
        // Valid - implicitly public static final
        int CONSTANT = 100;

        // Invalid - cannot be protected or private
        protected int value = 10; // Compilation error
        private int count = 5;    // Compilation error

        // Valid in Java 9+ - private method
        private void helperMethod() {
            // implementation
        }
    }
    ```

91. **When can an object reference be cast to a Java interface reference?**

    An object reference can be cast to an interface reference when:

    1. The object's class implements the interface
    2. Any of its superclasses implements the interface

    Example:

    ```java
    interface Flyable {
        void fly();
    }

    class Bird implements Flyable {
        public void fly() { }
    }

    class Sparrow extends Bird {
        // Inherits fly() from Bird
    }

    // Valid casts:
    Bird bird = new Bird();
    Flyable flyable1 = (Flyable) bird;      // Direct implementation

    Sparrow sparrow = new Sparrow();
    Flyable flyable2 = (Flyable) sparrow;   // Through inheritance

    // Invalid cast - will throw ClassCastException:
    String str = "hello";
    Flyable flyable3 = (Flyable) str;       // String doesn't implement Flyable
    ```

    Key points:

    - The cast can be checked at runtime using the instanceof operator
    - An invalid cast will result in a ClassCastException
    - The cast may be implicit (no cast operator needed) when assigning to an interface reference

92. **What are getters and setters in Java?**

    Getters and setters are methods that allow controlled access to class fields/attributes:

    ```java
    public class Person {
        private String name; // Private field

        // Getter method
        public String getName() {
            return name;
        }

        // Setter method
        public void setName(String name) {
            this.name = name;
        }
    }
    ```

    Key points:

    1. Encapsulation: They provide encapsulation by keeping fields private while allowing controlled access
    2. Naming Convention:
       - Getters start with "get" followed by capitalized field name
       - Setters start with "set" followed by capitalized field name
       - For boolean fields, getters often start with "is" (e.g., isActive())
    3. Benefits:
       - Add validation in setters
       - Modify internal representation without changing public interface
       - Control read/write access separately
       - Enable debugging/logging when fields are accessed
    4. JavaBeans: Following these naming conventions makes classes compatible with JavaBeans specification

93. **What is static in Java?**

    The static keyword in Java is used to declare members (variables and methods) that belong to the class itself rather than instances of the class:

    ```java
    public class Counter {
        private static int count = 0;  // Static variable shared by all instances

        public static void increment() {  // Static method
            count++;
        }

        public static int getCount() {    // Static method
            return count;
        }
    }
    ```

    Key points:

    1. Static Variables (Class Variables):

       - Shared across all instances of the class
       - Can be accessed without creating class instance
       - Initialized only once when class is loaded
       - Memory efficient for common data

    2. Static Methods:

       - Can be called without creating class instance
       - Can only directly access other static members
       - Cannot use 'this' keyword
       - Common for utility functions

    3. Static Blocks:

       - Used for static initialization
       - Executed when class is loaded
       - Runs before constructor

    4. Static Classes:

       - Only inner classes can be static
       - Don't need instance of outer class to be created
       - Cannot access non-static members of outer class

    5. Common Uses:
       - Utility methods (e.g., Math.sqrt())
       - Constants (public static final)
       - Singleton pattern
       - Factory methods

94. **What is the difference between abstract classes and interfaces?**

    | Feature               | Abstract Class                                    | Interface                                                                                 |
    | --------------------- | ------------------------------------------------- | ----------------------------------------------------------------------------------------- |
    | Multiple Inheritance  | Not supported (single inheritance only)           | A class can implement multiple interfaces                                                 |
    | Variables             | Can have instance variables, static variables     | Only static final (constants) variables                                                   |
    | Method Implementation | Can have concrete and abstract methods            | Prior to Java 8: Only abstract methods. After Java 8: Can have default and static methods |
    | Constructor           | Can have constructors                             | Cannot have constructors                                                                  |
    | Access Modifiers      | Can use all access modifiers                      | Methods are implicitly public abstract, variables are public static final                 |
    | Purpose               | For related classes sharing common functionality  | To define a contract of behaviors                                                         |
    | Instantiation         | Cannot be instantiated                            | Cannot be instantiated                                                                    |
    | Member Variables      | Can have non-final and non-static variables       | Variables must be public static final                                                     |
    | Speed                 | Faster as resolved during compile time            | Slightly slower as resolved during runtime                                                |
    | Usage                 | When you want to share code among related classes | When you want to define common behavior that can be implemented by unrelated classes      |
