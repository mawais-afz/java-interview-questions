# Object Oriented Programming Concepts

## What is inheritance? Types of inheritance in Java?

**Inheritance** is one of the four fundamental principles of Object-Oriented Programming (OOP). It allows a class (called the **subclass** or **child class**) to inherit properties and methods from another class (called the **superclass** or **parent class**). This promotes code reusability and establishes an "is-a" relationship between classes.

### Types of Inheritance in Java

#### 1. **Single Inheritance**

- A class inherits from only one parent class
- Java supports this directly
- Example: `Dog` extends `Animal`

#### 2. **Multilevel Inheritance**

- A class inherits from a parent class, which in turn inherits from another class
- Forms a chain: `Grandparent` → `Parent` → `Child`
- Example: `Animal` → `Mammal` → `Dog`

#### 3. **Hierarchical Inheritance**

- Multiple classes inherit from the same parent class
- Example: `Animal` is the parent of `Dog`, `Cat`, and `Bird`

#### 4. **Multiple Inheritance (through Interfaces)**

- Java doesn't support multiple inheritance with classes directly
- But a class can implement multiple interfaces
- Example: `class Dog implements Animal, Pet, Trainable`

#### 5. **Hybrid Inheritance**

- Combination of different inheritance types
- Usually involves interfaces and classes together

### Key Points

- **extends** keyword is used for class inheritance
- **implements** keyword is used for interface implementation
- Java supports **single inheritance** for classes but **multiple inheritance** for interfaces
- **Object class** is the root of all classes in Java
- **final classes** cannot be inherited
- **private members** are not inherited

## What is polymorphism? Give examples

**Polymorphism** allows objects of different classes to be treated as objects of a common superclass, enabling the same interface to be used for different underlying forms (data types or classes).
The ability of an object, method, or operator to take on multiple forms.

### Types of Polymorphism in Java

#### 1. **Compile-time Polymorphism (Static Binding)**

Also known as **Method Overloading** - multiple methods with the same name but different parameters in the same class.

**Example:**

```java
public class Calculator {
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
    
    public String add(String a, String b) {
        return a + b;
    }
}

// Usage
Calculator calc = new Calculator();
calc.add(5, 3);        // Calls first method
calc.add(5.5, 3.2);    // Calls second method
calc.add(1, 2, 3);     // Calls third method
calc.add("Hello", "World"); // Calls fourth method
```

#### 2. **Runtime Polymorphism (Dynamic Binding)**

Also known as **Method Overriding** - a subclass provides a specific implementation of a method that is already defined in its superclass.

**Example:**

```java
// Base class
class Animal {
    public void makeSound() {
        System.out.println("Some animal sound");
    }
    
    public void move() {
        System.out.println("Animal is moving");
    }
}

// Subclass 1
class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof! Woof!");
    }
    
    @Override
    public void move() {
        System.out.println("Dog is running");
    }
}

// Subclass 2
class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow! Meow!");
    }
    
    @Override
    public void move() {
        System.out.println("Cat is walking gracefully");
    }
}

// Usage demonstrating runtime polymorphism
public class PolymorphismDemo {
    public static void main(String[] args) {
        // Reference type is Animal, but objects are Dog and Cat
        Animal myAnimal1 = new Dog();  // Upcasting
        Animal myAnimal2 = new Cat();  // Upcasting
        
        // Runtime polymorphism - method calls are resolved at runtime
        myAnimal1.makeSound();  // Output: Woof! Woof!
        myAnimal1.move();       // Output: Dog is running
        
        myAnimal2.makeSound();  // Output: Meow! Meow!
        myAnimal2.move();       // Output: Cat is walking gracefully
    }
}
```

### Real-world Examples

#### **Example 1: Shape Hierarchy**

```java
abstract class Shape {
    abstract double calculateArea();
    abstract double calculatePerimeter();
}

class Circle extends Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    double calculatePerimeter() {
        return 2 * Math.PI * radius;
    }
}

class Rectangle extends Shape {
    private double length, width;
    
    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }
    
    @Override
    double calculateArea() {
        return length * width;
    }
    
    @Override
    double calculatePerimeter() {
        return 2 * (length + width);
    }
}

// Polymorphic usage
public class ShapeCalculator {
    public static void printShapeInfo(Shape shape) {
        System.out.println("Area: " + shape.calculateArea());
        System.out.println("Perimeter: " + shape.calculatePerimeter());
    }
    
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        Shape rectangle = new Rectangle(4, 6);
        
        // Same method call, different behaviors
        printShapeInfo(circle);     // Calls Circle's methods
        printShapeInfo(rectangle);  // Calls Rectangle's methods
    }
}
```

#### **Example 2: Payment System**

```java
interface PaymentMethod {
    void processPayment(double amount);
}

class CreditCard implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing credit card payment: $" + amount);
        // Credit card specific logic
    }
}

class PayPal implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing PayPal payment: $" + amount);
        // PayPal specific logic
    }
}

class BankTransfer implements PaymentMethod {
    @Override
    public void processPayment(double amount) {
        System.out.println("Processing bank transfer: $" + amount);
        // Bank transfer specific logic
    }
}

class PaymentProcessor {
    public void process(PaymentMethod payment, double amount) {
        payment.processPayment(amount);  // Polymorphic call
    }
}
```

### Key Benefits of Polymorphism

1. **Code Reusability** - Write code that works with the base class
2. **Extensibility** - Easy to add new subclasses without changing existing code
3. **Maintainability** - Changes in implementation don't affect the interface
4. **Flexibility** - Objects can be treated uniformly through a common interface

### Important Points

- **Method Overloading** is resolved at compile time (static binding)
- **Method Overriding** is resolved at runtime (dynamic binding)
- Polymorphism works with **inheritance** and **interfaces**
- The **actual object type** determines which method is called at runtime
- **Upcasting** (subclass to superclass) enables polymorphic behavior

## What is encapsulation and abstraction?

### Encapsulation

**Encapsulation** is refers to the bundling of data (attributes) and methods (functions) that operate on that data within a single unit or object, while restricting access to some of the object's components. This is also known as **information hiding**.

#### Key Principles of Encapsulation

1. **Data Hiding** - Private data members are not accessible from outside the class
2. **Bundling** - Data and methods that operate on that data are bundled together
3. **Access Control** - Controlled access to data through public methods (getters/setters)

#### Example of Encapsulation

```java
public class BankAccount {
    // Private data members (encapsulated)
    private String accountNumber;
    private String accountHolder;
    private double balance;
    private String pin;
    
    // Constructor
    public BankAccount(String accountNumber, String accountHolder, String pin) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.pin = pin;
        this.balance = 0.0;
    }
    
    // Public methods to access and modify private data (controlled access)
    public String getAccountNumber() {
        return accountNumber;
    }
    
    public String getAccountHolder() {
        return accountHolder;
    }
    
    public double getBalance() {
        return balance;
    }
    
    // Business logic methods
    public boolean deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            return true;
        }
        return false;
    }
    
    public boolean withdraw(double amount, String enteredPin) {
        if (enteredPin.equals(pin) && amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }
    
    public boolean changePin(String oldPin, String newPin) {
        if (oldPin.equals(pin)) {
            pin = newPin;
            return true;
        }
        return false;
    }
}

// Usage
public class BankDemo {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("12345", "John Doe", "1234");
        
        // Can access public methods but not private data directly
        account.deposit(1000);
        System.out.println("Balance: $" + account.getBalance());
        
        // account.balance = 5000; // This would cause compilation error
        // account.pin = "9999";   // This would cause compilation error
    }
}
```

#### Benefits of Encapsulation

1. **Data Security** - Private data cannot be accessed directly from outside
2. **Flexibility** - Internal implementation can be changed without affecting external code
3. **Maintainability** - Easier to maintain and modify code
4. **Reusability** - Encapsulated classes can be easily reused

---

### Abstraction

**Abstraction** is the process of hiding complex implementation details and showing only the necessary features of an object. It focuses on what an object does rather than how it does it.

#### Types of Abstraction in Java

1. **Abstract Classes** - Cannot be instantiated, may contain abstract and concrete methods
2. **Interfaces** - Pure abstraction, only method declarations (before Java 8)
3. **Abstract Methods** - Methods without implementation

#### Example 1: Abstract Class

```java
// Abstract class - cannot be instantiated
abstract class Vehicle {
    // Abstract method - must be implemented by subclasses
    abstract void startEngine();
    abstract void stopEngine();
    
    // Concrete method - has implementation
    public void displayInfo() {
        System.out.println("This is a vehicle");
    }
    
    // Can have instance variables
    protected String brand;
    protected String model;
    
    public Vehicle(String brand, String model) {
        this.brand = brand;
        this.model = model;
    }
}

// Concrete class implementing abstract methods
class Car extends Vehicle {
    public Car(String brand, String model) {
        super(brand, model);
    }
    
    @Override
    void startEngine() {
        System.out.println("Car engine started with key");
    }
    
    @Override
    void stopEngine() {
        System.out.println("Car engine stopped");
    }
}

// Another concrete class
class Motorcycle extends Vehicle {
    public Motorcycle(String brand, String model) {
        super(brand, model);
    }
    
    @Override
    void startEngine() {
        System.out.println("Motorcycle engine started with kick");
    }
    
    @Override
    void stopEngine() {
        System.out.println("Motorcycle engine stopped");
    }
}
```

#### Example 2: Interface (Pure Abstraction)

```java
// Interface - pure abstraction (before Java 8)
interface DatabaseOperations {
    // Abstract methods (implicitly public and abstract)
    void connect();
    void disconnect();
    void executeQuery(String query);
    void closeConnection();
}

// Implementation class
class MySQLDatabase implements DatabaseOperations {
    @Override
    public void connect() {
        System.out.println("Connecting to MySQL database...");
        // Complex connection logic hidden
    }
    
    @Override
    public void disconnect() {
        System.out.println("Disconnecting from MySQL database...");
        // Complex disconnection logic hidden
    }
    
    @Override
    public void executeQuery(String query) {
        System.out.println("Executing MySQL query: " + query);
        // Complex query execution logic hidden
    }
    
    @Override
    public void closeConnection() {
        System.out.println("Closing MySQL connection...");
        // Complex cleanup logic hidden
    }
}

// Another implementation
class PostgreSQLDatabase implements DatabaseOperations {
    @Override
    public void connect() {
        System.out.println("Connecting to PostgreSQL database...");
        // Different connection logic
    }
    
    @Override
    public void disconnect() {
        System.out.println("Disconnecting from PostgreSQL database...");
        // Different disconnection logic
    }
    
    @Override
    public void executeQuery(String query) {
        System.out.println("Executing PostgreSQL query: " + query);
        // Different query execution logic
    }
    
    @Override
    public void closeConnection() {
        System.out.println("Closing PostgreSQL connection...");
        // Different cleanup logic
    }
}

// Usage - client code works with abstraction
public class DatabaseClient {
    public static void performDatabaseOperations(DatabaseOperations db) {
        db.connect();
        db.executeQuery("SELECT * FROM users");
        db.closeConnection();
    }
    
    public static void main(String[] args) {
        DatabaseOperations mysql = new MySQLDatabase();
        DatabaseOperations postgres = new PostgreSQLDatabase();
        
        // Same interface, different implementations
        performDatabaseOperations(mysql);
        performDatabaseOperations(postgres);
    }
}
```

#### Example 3: Real-world Abstraction

```java
// Abstract representation of a payment processor
interface PaymentProcessor {
    boolean processPayment(double amount, String currency);
    String getTransactionId();
    PaymentStatus getStatus();
}

enum PaymentStatus {
    PENDING, SUCCESS, FAILED
}

// Concrete implementations
class CreditCardProcessor implements PaymentProcessor {
    @Override
    public boolean processPayment(double amount, String currency) {
        // Complex credit card processing logic hidden
        System.out.println("Processing credit card payment: $" + amount + " " + currency);
        return true;
    }
    
    @Override
    public String getTransactionId() {
        return "CC_" + System.currentTimeMillis();
    }
    
    @Override
    public PaymentStatus getStatus() {
        return PaymentStatus.SUCCESS;
    }
}

class PayPalProcessor implements PaymentProcessor {
    @Override
    public boolean processPayment(double amount, String currency) {
        // Complex PayPal processing logic hidden
        System.out.println("Processing PayPal payment: $" + amount + " " + currency);
        return true;
    }
    
    @Override
    public String getTransactionId() {
        return "PP_" + System.currentTimeMillis();
    }
    
    @Override
    public PaymentStatus getStatus() {
        return PaymentStatus.SUCCESS;
    }
}

// Client code works with abstraction
class PaymentService {
    private PaymentProcessor processor;
    
    public PaymentService(PaymentProcessor processor) {
        this.processor = processor;
    }
    
    public void makePayment(double amount, String currency) {
        boolean success = processor.processPayment(amount, currency);
        if (success) {
            System.out.println("Payment successful. Transaction ID: " + processor.getTransactionId());
        }
    }
}
```

### Key Differences Between Encapsulation and Abstraction

| Aspect | Encapsulation | Abstraction |
|--------|---------------|-------------|
| **Purpose** | Bundling data and methods, controlling access | Hiding complexity, showing essential features |
| **Focus** | How to achieve data hiding | What to show to the user |
| **Implementation** | Private fields, getters/setters | Abstract classes, interfaces |
| **Level** | Object level | Class/Interface level |

### Benefits of Abstraction

1. **Simplified Interface** - Users only see what they need to know
2. **Implementation Independence** - Can change implementation without affecting client code
3. **Code Organization** - Better structure and readability
4. **Security** - Internal details are hidden from external access

### When to Use

- **Use Encapsulation** when you want to protect data and control access
- **Use Abstraction** when you want to provide a simplified interface and hide complexity

## What is method overloading vs method overriding?

### Method Overloading (Compile-time Polymorphism)

**Method Overloading** allows a class to have multiple methods with the same name but different parameters. It's a form of **compile-time polymorphism** where the method to be called is determined at compile time based on the method signature.

#### Key Characteristics of Method Overloading

1. **Same Method Name** - Methods must have identical names
2. **Different Parameters** - Must differ in number, type, or order of parameters
3. **Same Class** - All overloaded methods must be in the same class
4. **Return Type** - Can be same or different (not considered for overloading)
5. **Access Modifier** - Can be same or different
6. **Compile-time Resolution** - Method binding happens at compile time

#### Examples of Method Overloading

```java
public class Calculator {
    // Overloaded methods with different parameter types
    public int add(int a, int b) {
        return a + b;
    }
    
    public double add(double a, double b) {
        return a + b;
    }
    
    // Overloaded method with different number of parameters
    public int add(int a, int b, int c) {
        return a + b + c;
    }
    
    // Overloaded method with different parameter order
    public String add(String prefix, int number) {
        return prefix + number;
    }
    
    public String add(int number, String suffix) {
        return number + suffix;
    }
    
    // Overloaded method with different return type (same parameters)
    public int multiply(int a, int b) {
        return a * b;
    }
    
    public double multiply(int a, int b) {
        return (double) (a * b);
    }
    // This will cause compilation error - same parameters, different return type
}

// Usage
public class OverloadingDemo {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        
        // Different method calls based on parameters
        System.out.println(calc.add(5, 3));           // Calls first method
        System.out.println(calc.add(5.5, 3.2));       // Calls second method
        System.out.println(calc.add(1, 2, 3));        // Calls third method
        System.out.println(calc.add("Result: ", 10));  // Calls fourth method
        System.out.println(calc.add(10, " is the result")); // Calls fifth method
    }
}
```

#### Constructor Overloading

```java
public class Student {
    private String name;
    private int age;
    private String major;
    
    // Default constructor
    public Student() {
        this.name = "Unknown";
        this.age = 18;
        this.major = "Undeclared";
    }
    
    // Constructor with name only
    public Student(String name) {
        this.name = name;
        this.age = 18;
        this.major = "Undeclared";
    }
    
    // Constructor with name and age
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
        this.major = "Undeclared";
    }
    
    // Constructor with all parameters
    public Student(String name, int age, String major) {
        this.name = name;
        this.age = age;
        this.major = major;
    }
    
    // Copy constructor
    public Student(Student other) {
        this.name = other.name;
        this.age = other.age;
        this.major = other.major;
    }
}
```

---

### Method Overriding (Runtime Polymorphism)

**Method Overriding** allows a subclass to provide a specific implementation of a method that is already defined in its superclass. It's a form of **runtime polymorphism** where the method to be called is determined at runtime based on the actual object type.

#### Key Characteristics of Method Overriding

1. **Same Method Signature** - Method name, parameters, and return type must be identical
2. **Inheritance Relationship** - Must exist between superclass and subclass
3. **Runtime Resolution** - Method binding happens at runtime
4. **Access Modifier** - Cannot be more restrictive than the superclass method
5. **Exception Handling** - Cannot throw broader checked exceptions

#### Rules for Method Overriding

1. **Method signature must be exactly the same**
2. **Return type must be the same or covariant (subclass of superclass return type)**
3. **Access modifier cannot be more restrictive**
4. **Cannot override final, static, or private methods**
5. **Cannot override methods from different packages unless they are public or protected**

#### Examples of Method Overriding

```java
// Base class
class Animal {
    public void makeSound() {
        System.out.println("Some animal sound");
    }
    
    public void move() {
        System.out.println("Animal is moving");
    }
    
    public Number getAge() {
        return 0;
    }
    
    // Final method - cannot be overridden
    public final void breathe() {
        System.out.println("Animal is breathing");
    }
    
    // Static method - cannot be overridden (method hiding)
    public static void sleep() {
        System.out.println("Animal is sleeping");
    }
}

// Subclass 1
class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof! Woof!");
    }
    
    @Override
    public void move() {
        System.out.println("Dog is running");
    }
    
    @Override
    public Integer getAge() {  // Covariant return type
        return 5;
    }
    
    // Method hiding (not overriding) - static method
    public static void sleep() {
        System.out.println("Dog is sleeping");
    }
}

// Subclass 2
class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow! Meow!");
    }
    
    @Override
    public void move() {
        System.out.println("Cat is walking gracefully");
    }
    
    @Override
    public Integer getAge() {  // Covariant return type
        return 3;
    }
}

// Demonstration of runtime polymorphism
public class OverridingDemo {
    public static void main(String[] args) {
        // Reference type is Animal, but objects are Dog and Cat
        Animal myAnimal1 = new Dog();  // Upcasting
        Animal myAnimal2 = new Cat();  // Upcasting
        
        // Runtime polymorphism - method calls resolved at runtime
        myAnimal1.makeSound();  // Output: Woof! Woof!
        myAnimal1.move();       // Output: Dog is running
        
        myAnimal2.makeSound();  // Output: Meow! Meow!
        myAnimal2.move();       // Output: Cat is walking gracefully
        
        // Static method calls (not polymorphic)
        Animal.sleep();  // Output: Animal is sleeping
        Dog.sleep();     // Output: Dog is sleeping
        
        // Final method calls
        myAnimal1.breathe();  // Output: Animal is breathing
        myAnimal2.breathe();  // Output: Animal is breathing
    }
}
```

#### Advanced Overriding Examples

```java
// Covariant return types
class BaseClass {
    public Object getObject() {
        return new Object();
    }
    
    public void processData(String data) throws Exception {
        System.out.println("Processing: " + data);
    }
}

class DerivedClass extends BaseClass {
    @Override
    public String getObject() {  // Covariant return type
        return "Hello World";
    }
    
    @Override
    public void processData(String data) throws RuntimeException {  // Narrower exception
        System.out.println("Derived processing: " + data);
    }
}

// Interface implementation
interface Drawable {
    void draw();
    default void display() {
        System.out.println("Displaying drawable object");
    }
}

class Circle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a circle");
    }
    
    @Override
    public void display() {
        System.out.println("Displaying circle");
    }
}

class Rectangle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing a rectangle");
    }
    // display() method not overridden, will use default implementation
}
```

---

### Key Differences Between Method Overloading and Method Overriding

| Aspect | Method Overloading | Method Overriding |
|--------|-------------------|-------------------|
| **Definition** | Multiple methods with same name, different parameters | Subclass provides specific implementation of superclass method |
| **Polymorphism** | Compile-time (Static) | Runtime (Dynamic) |
| **Class** | Same class | Different classes (inheritance) |
| **Method Signature** | Must be different | Must be exactly the same |
| **Return Type** | Can be different | Must be same or covariant |
| **Access Modifier** | Can be different | Cannot be more restrictive |
| **Exception Handling** | No restrictions | Cannot throw broader exceptions |
| **Binding** | Early binding (compile time) | Late binding (runtime) |
| **Purpose** | Provide convenience methods | Provide specific implementation |

### When to Use Each

#### **Use Method Overloading When:**

- You want to provide multiple ways to call the same functionality
- Methods perform similar operations but with different parameters
- You want to provide default values or convenience methods
- You're working within the same class

#### **Use Method Overriding When:**

- You want to provide specific behavior in subclasses
- You want to achieve runtime polymorphism
- You're implementing interfaces or extending classes
- You want to customize behavior based on object type

### Best Practices

1. **Method Overloading:**
   - Keep overloaded methods logically related
   - Don't overload methods that do completely different things
   - Use clear, descriptive parameter names

2. **Method Overriding:**
   - Always use `@Override` annotation
   - Maintain the contract of the superclass method
   - Don't change the method's intended behavior
   - Follow the Liskov Substitution Principle

## When to use Interface vs Abstract Class?

### Interface

**Interfaces** are used to define a contract or a set of methods that a class must implement. They are **purely abstract** and cannot have concrete methods (before Java 8). This makes them ideal for defining a common set of behaviors or capabilities that multiple unrelated classes can share.

#### Key Characteristics of Interfaces

1. **Pure Abstraction** - Only method declarations, no implementation (before Java 8)
2. **Multiple Inheritance** - A class can implement multiple interfaces
3. **No State** - Interfaces cannot have instance variables (before Java 8)
4. **No Concrete Methods** - All methods are abstract (before Java 8)
5. **Default Methods** (Java 8+) - Can have default implementations
6. **Static Methods** (Java 8+) - Can have static methods
7. **Private Methods** (Java 9+) - Can have private helper methods
8. **Constants** - Can have public static final constants

#### Example of Interface

```java
// Basic interface (Java 7 and earlier)
interface Drawable {
    // Abstract method (implicitly public and abstract)
    void draw();
    
    // Constant (implicitly public static final)
    String DEFAULT_COLOR = "Black";
}

// Modern interface with default and static methods (Java 8+)
interface Vehicle {
    // Abstract method
    void start();
    void stop();
    
    // Default method with implementation
    default void honk() {
        System.out.println("Vehicle is honking!");
    }
    
    // Static method
    static void displayInfo() {
        System.out.println("This is a vehicle interface");
    }
    
    // Private method (Java 9+)
    private void logAction(String action) {
        System.out.println("Action: " + action);
    }
}

// Multiple interface implementation
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

// Class implementing multiple interfaces
class Duck implements Vehicle, Flyable, Swimmable {
    @Override
    public void start() {
        System.out.println("Duck is starting");
    }
    
    @Override
    public void stop() {
        System.out.println("Duck is stopping");
    }
    
    @Override
    public void fly() {
        System.out.println("Duck is flying");
    }
    
    @Override
    public void swim() {
        System.out.println("Duck is swimming");
    }
}
```

---

### Abstract Class

**Abstract classes** are used when you want to provide a base class with some implementation and allow subclasses to extend it. They can have **concrete methods** and **instance variables**. This is useful when you want to share common functionality among related classes.

#### Key Characteristics of Abstract Classes

1. **Cannot be Instantiated** - Abstract classes cannot be instantiated directly
2. **Concrete Methods** - Can have concrete methods with implementation
3. **Abstract Methods** - Can have abstract methods that must be implemented by subclasses
4. **Instance Variables** - Can have instance variables and state
5. **Constructors** - Can have constructors
6. **Single Inheritance** - A class can extend only one abstract class
7. **Access Modifiers** - Can have any access modifier for methods and fields

#### Example of Abstract Class

```java
abstract class Animal {
    // Instance variables (state)
    protected String name;
    protected int age;
    protected String species;
    
    // Constructor
    public Animal(String name, int age, String species) {
        this.name = name;
        this.age = age;
        this.species = species;
    }
    
    // Concrete method with implementation
    public void breathe() {
        System.out.println(name + " is breathing");
    }
    
    public void sleep() {
        System.out.println(name + " is sleeping");
    }
    
    // Abstract methods that must be implemented by subclasses
    abstract void makeSound();
    abstract void move();
    abstract void eat();
    
    // Concrete method that can be overridden
    public void displayInfo() {
        System.out.println("Name: " + name + ", Age: " + age + ", Species: " + species);
    }
    
    // Final method that cannot be overridden
    public final void die() {
        System.out.println(name + " has died");
    }
}

// Concrete class extending abstract class
class Dog extends Animal {
    private String breed;
    
    public Dog(String name, int age, String breed) {
        super(name, age, "Dog");
        this.breed = breed;
    }
    
    @Override
    void makeSound() {
        System.out.println(name + " says: Woof! Woof!");
    }
    
    @Override
    void move() {
        System.out.println(name + " is running");
    }
    
    @Override
    void eat() {
        System.out.println(name + " is eating dog food");
    }
    
    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Breed: " + breed);
    }
    
    // Additional methods specific to Dog
    public void fetch() {
        System.out.println(name + " is fetching the ball");
    }
}

class Cat extends Animal {
    private boolean isIndoor;
    
    public Cat(String name, int age, boolean isIndoor) {
        super(name, age, "Cat");
        this.isIndoor = isIndoor;
    }
    
    @Override
    void makeSound() {
        System.out.println(name + " says: Meow! Meow!");
    }
    
    @Override
    void move() {
        System.out.println(name + " is walking gracefully");
    }
    
    @Override
    void eat() {
        System.out.println(name + " is eating cat food");
    }
    
    // Additional methods specific to Cat
    public void purr() {
        System.out.println(name + " is purring");
    }
}
```

---

### Detailed Comparison Table

| Feature | Interface | Abstract Class |
|---------|-----------|----------------|
| **Instantiation** | Cannot be instantiated | Cannot be instantiated |
| **Implementation** | No implementation (before Java 8) | Can have implementation |
| **Fields** | Only constants (public static final) | Can have instance variables |
| **Methods** | Abstract methods only (before Java 8) | Abstract and concrete methods |
| **Constructors** | No constructors | Can have constructors |
| **Inheritance** | Multiple inheritance (implements) | Single inheritance (extends) |
| **Access Modifiers** | Methods are implicitly public | Can have any access modifier |
| **State** | No state (before Java 8) | Can maintain state |
| **Default Methods** | Yes (Java 8+) | No (but can have concrete methods) |
| **Static Methods** | Yes (Java 8+) | Yes |
| **Private Methods** | Yes (Java 9+) | Yes |

---

### When to Use Each

#### **Use Interface When:**

1. **Multiple Inheritance Needed** - Class needs to implement multiple contracts
2. **Pure Contract Definition** - You only want to define what methods must exist
3. **Unrelated Classes** - Classes that don't share a common hierarchy
4. **Behavioral Contracts** - Defining capabilities or behaviors
5. **API Design** - Creating public APIs that multiple implementations can follow
6. **Functional Programming** - Working with lambda expressions and functional interfaces

**Examples:**

- `Comparable<T>` - For objects that can be compared
- `Serializable` - For objects that can be serialized
- `Runnable` - For objects that can run in a thread
- `Collection<E>` - For collection implementations

#### **Use Abstract Class When:**

1. **Shared Implementation** - Multiple related classes share common code
2. **State Management** - Need to maintain instance variables
3. **Constructor Logic** - Need to initialize common state
4. **Template Method Pattern** - Define algorithm structure with some steps implemented
5. **Related Classes** - Classes that form a natural hierarchy
6. **Partial Implementation** - Want to provide some default behavior

**Examples:**

- `AbstractList<E>` - Base for list implementations
- `InputStream` - Base for input stream implementations
- `AbstractButton` - Base for button implementations in Swing

---

### Real-world Examples

#### **Interface Example - Payment Processing:**

```java
interface PaymentProcessor {
    boolean processPayment(double amount, String currency);
    String getTransactionId();
    PaymentStatus getStatus();
    default void logTransaction() {
        System.out.println("Transaction logged: " + getTransactionId());
    }
}

class CreditCardProcessor implements PaymentProcessor {
    @Override
    public boolean processPayment(double amount, String currency) {
        // Credit card specific logic
        return true;
    }
    
    @Override
    public String getTransactionId() {
        return "CC_" + System.currentTimeMillis();
    }
    
    @Override
    public PaymentStatus getStatus() {
        return PaymentStatus.SUCCESS;
    }
}

class PayPalProcessor implements PaymentProcessor {
    @Override
    public boolean processPayment(double amount, String currency) {
        // PayPal specific logic
        return true;
    }
    
    @Override
    public String getTransactionId() {
        return "PP_" + System.currentTimeMillis();
    }
    
    @Override
    public PaymentStatus getStatus() {
        return PaymentStatus.SUCCESS;
    }
}
```

#### **Abstract Class Example - Database Connection:**

```java
abstract class DatabaseConnection {
    protected String url;
    protected String username;
    protected String password;
    protected boolean isConnected;
    
    public DatabaseConnection(String url, String username, String password) {
        this.url = url;
        this.username = username;
        this.password = password;
        this.isConnected = false;
    }
    
    // Template method pattern
    public final void connect() {
        if (validateConnection()) {
            establishConnection();
            isConnected = true;
            logConnection();
        }
    }
    
    public final void disconnect() {
        if (isConnected) {
            closeConnection();
            isConnected = false;
            logDisconnection();
        }
    }
    
    // Abstract methods that must be implemented
    protected abstract boolean validateConnection();
    protected abstract void establishConnection();
    protected abstract void closeConnection();
    
    // Concrete methods with default implementation
    protected void logConnection() {
        System.out.println("Connected to: " + url);
    }
    
    protected void logDisconnection() {
        System.out.println("Disconnected from: " + url);
    }
}

class MySQLConnection extends DatabaseConnection {
    public MySQLConnection(String url, String username, String password) {
        super(url, username, password);
    }
    
    @Override
    protected boolean validateConnection() {
        return url.startsWith("jdbc:mysql://");
    }
    
    @Override
    protected void establishConnection() {
        System.out.println("Establishing MySQL connection...");
    }
    
    @Override
    protected void closeConnection() {
        System.out.println("Closing MySQL connection...");
    }
}
```

---

### Best Practices

1. **Start with Interface** - Begin with interfaces for flexibility
2. **Use Abstract Class for Shared Code** - When you need to share implementation
3. **Composition over Inheritance** - Prefer composition when possible
4. **Keep Interfaces Focused** - Single responsibility principle
5. **Document Your Design** - Clearly explain why you chose one over the other

### Summary

- **Interfaces** are best for defining contracts and achieving multiple inheritance
- **Abstract Classes** are best for sharing implementation and maintaining state
- **Choose based on your specific needs** - don't force one approach over the other
- **Modern Java** (8+) makes interfaces more powerful with default and static methods

## What is a Functional Interface?

**Functional Interfaces** are interfaces that contain exactly one abstract method. They are a key concept introduced in Java 8 to support functional programming and lambda expressions. Functional interfaces enable you to treat functions as first-class citizens in Java.

### Key Characteristics of Functional Interfaces:

1. **Single Abstract Method (SAM)** - Must contain exactly one abstract method
2. **Lambda Expression Support** - Can be implemented using lambda expressions
3. **Default Methods Allowed** - Can have multiple default methods
4. **Static Methods Allowed** - Can have multiple static methods
5. **@FunctionalInterface Annotation** - Optional annotation for compile-time checking
6. **Method Reference Support** - Can use method references for implementation

### @FunctionalInterface Annotation:

The `@FunctionalInterface` annotation is optional but recommended. It provides compile-time checking to ensure the interface has exactly one abstract method.

```java
@FunctionalInterface
interface MyFunctionalInterface {
    void doSomething(); // Single abstract method
    
    // Default methods are allowed
    default void doSomethingElse() {
        System.out.println("Default implementation");
    }
    
    // Static methods are allowed
    static void utilityMethod() {
        System.out.println("Utility method");
    }
}
```

### Built-in Functional Interfaces in Java:

#### 1. **Function<T, R>**
Represents a function that takes one argument and produces a result.

```java
import java.util.function.Function;

public class FunctionExample {
    public static void main(String[] args) {
        // Lambda expression implementation
        Function<String, Integer> stringLength = str -> str.length();
        
        // Method reference implementation
        Function<String, String> toUpperCase = String::toUpperCase;
        
        // Usage
        System.out.println("Length: " + stringLength.apply("Hello")); // Output: 5
        System.out.println("Uppercase: " + toUpperCase.apply("hello")); // Output: HELLO
        
        // Function composition
        Function<String, Integer> composed = toUpperCase.andThen(stringLength);
        System.out.println("Composed result: " + composed.apply("hello")); // Output: 5
    }
}
```

#### 2. **Predicate<T>**
Represents a boolean-valued function of one argument.

```java
import java.util.function.Predicate;
import java.util.Arrays;
import java.util.List;

public class PredicateExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David", "Eve");
        
        // Lambda expression implementation
        Predicate<String> startsWithA = name -> name.startsWith("A");
        Predicate<String> hasLength5 = name -> name.length() == 5;
        
        // Combined predicates
        Predicate<String> startsWithAAndLength5 = startsWithA.and(hasLength5);
        Predicate<String> startsWithAOrLength5 = startsWithA.or(hasLength5);
        Predicate<String> notStartsWithA = startsWithA.negate();
        
        // Usage
        System.out.println("Names starting with 'A':");
        names.stream().filter(startsWithA).forEach(System.out::println);
        
        System.out.println("\nNames starting with 'A' and length 5:");
        names.stream().filter(startsWithAAndLength5).forEach(System.out::println);
        
        System.out.println("\nNames NOT starting with 'A':");
        names.stream().filter(notStartsWithA).forEach(System.out::println);
    }
}
```

#### 3. **Consumer<T>**
Represents an operation that accepts a single input argument and returns no result.

```java
import java.util.function.Consumer;
import java.util.Arrays;
import java.util.List;

public class ConsumerExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        
        // Lambda expression implementation
        Consumer<String> printName = name -> System.out.println("Hello, " + name);
        Consumer<String> printLength = name -> System.out.println("Length: " + name.length());
        
        // Combined consumers
        Consumer<String> printBoth = printName.andThen(printLength);
        
        // Usage
        System.out.println("Individual consumers:");
        names.forEach(printName);
        
        System.out.println("\nCombined consumer:");
        names.forEach(printBoth);
        
        // Method reference
        Consumer<String> printer = System.out::println;
        names.forEach(printer);
    }
}
```

#### 4. **Supplier<T>**
Represents a supplier of results.

```java
import java.util.function.Supplier;
import java.util.Random;

public class SupplierExample {
    public static void main(String[] args) {
        // Lambda expression implementation
        Supplier<Double> randomDouble = () -> Math.random();
        Supplier<Integer> randomInt = () -> new Random().nextInt(100);
        Supplier<String> currentTime = () -> java.time.LocalTime.now().toString();
        
        // Usage
        System.out.println("Random double: " + randomDouble.get());
        System.out.println("Random int: " + randomInt.get());
        System.out.println("Current time: " + currentTime.get());
        
        // Lazy evaluation
        Supplier<String> expensiveOperation = () -> {
            // Simulate expensive operation
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Expensive result";
        };
        
        // Operation is not executed until get() is called
        System.out.println("About to call expensive operation...");
        String result = expensiveOperation.get(); // Now it executes
        System.out.println("Result: " + result);
    }
}
```

### Custom Functional Interface Examples:

#### 1. **Simple Custom Functional Interface**
```java
@FunctionalInterface
interface StringProcessor {
    String process(String input);
    
    // Default method is allowed
    default String processWithPrefix(String input, String prefix) {
        return prefix + process(input);
    }
}

public class CustomFunctionalInterfaceExample {
    public static void main(String[] args) {
        // Lambda expression implementation
        StringProcessor reverse = str -> new StringBuilder(str).reverse().toString();
        StringProcessor toUpperCase = String::toUpperCase;
        StringProcessor addExclamation = str -> str + "!";
        
        // Usage
        System.out.println("Reversed: " + reverse.process("Hello"));
        System.out.println("Uppercase: " + toUpperCase.process("hello"));
        System.out.println("With exclamation: " + addExclamation.process("Hello"));
        
        // Using default method
        System.out.println("With prefix: " + reverse.processWithPrefix("Hello", "Reversed: "));
    }
}
```

#### 2. **Generic Functional Interface**
```java
@FunctionalInterface
interface Transformer<T, R> {
    R transform(T input);
    
    // Default method for chaining
    default <V> Transformer<T, V> andThen(Transformer<R, V> after) {
        return input -> after.transform(transform(input));
    }
}

public class GenericFunctionalInterfaceExample {
    public static void main(String[] args) {
        // String transformations
        Transformer<String, Integer> length = String::length;
        Transformer<Integer, String> doubleValue = i -> "Double: " + (i * 2);
        
        // Chained transformation
        Transformer<String, String> chained = length.andThen(doubleValue);
        
        System.out.println("Chained result: " + chained.transform("Hello"));
        
        // Number transformations
        Transformer<Integer, Double> square = i -> Math.pow(i, 2);
        Transformer<Double, String> formatted = d -> String.format("%.2f", d);
        
        Transformer<Integer, String> numberChain = square.andThen(formatted);
        System.out.println("Number chain: " + numberChain.transform(5));
    }
}
```

### Lambda Expressions with Functional Interfaces:

#### 1. **Basic Lambda Syntax**
```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}

public class LambdaExample {
    public static void main(String[] args) {
        // Lambda expressions
        Calculator add = (a, b) -> a + b;
        Calculator subtract = (a, b) -> a - b;
        Calculator multiply = (a, b) -> a * b;
        Calculator divide = (a, b) -> b != 0 ? a / b : 0;
        
        // Usage
        System.out.println("10 + 5 = " + add.calculate(10, 5));
        System.out.println("10 - 5 = " + subtract.calculate(10, 5));
        System.out.println("10 * 5 = " + multiply.calculate(10, 5));
        System.out.println("10 / 5 = " + divide.calculate(10, 5));
    }
}
```

#### 2. **Method References**
```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;
import java.util.function.Function;

public class MethodReferenceExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        
        // Method references
        Consumer<String> printer = System.out::println;
        Function<String, Integer> length = String::length;
        Function<String, String> upper = String::toUpperCase;
        
        // Usage
        names.forEach(printer);
        names.stream().map(length).forEach(System.out::println);
        names.stream().map(upper).forEach(printer);
        
        // Constructor reference
        Function<String, StringBuilder> stringBuilder = StringBuilder::new;
        StringBuilder sb = stringBuilder.apply("Hello");
        System.out.println(sb);
    }
}
```

### Real-world Usage Examples:

#### 1. **Event Handling**
```java
@FunctionalInterface
interface EventHandler<T> {
    void handle(T event);
}

class Button {
    private EventHandler<Button> clickHandler;
    
    public void setClickHandler(EventHandler<Button> handler) {
        this.clickHandler = handler;
    }
    
    public void click() {
        if (clickHandler != null) {
            clickHandler.handle(this);
        }
    }
}

public class EventHandlingExample {
    public static void main(String[] args) {
        Button button = new Button();
        
        // Lambda expression for event handling
        button.setClickHandler(btn -> System.out.println("Button clicked!"));
        
        // Simulate click
        button.click();
    }
}
```

#### 2. **Data Processing Pipeline**
```java
import java.util.Arrays;
import java.util.List;
import java.util.function.Function;
import java.util.function.Predicate;

public class DataProcessingExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // Processing pipeline
        Predicate<Integer> isEven = n -> n % 2 == 0;
        Predicate<Integer> isGreaterThan5 = n -> n > 5;
        Function<Integer, Integer> square = n -> n * n;
        Function<Integer, String> format = n -> "Result: " + n;
        
        // Process: filter even numbers > 5, square them, format as string
        List<String> results = numbers.stream()
            .filter(isEven.and(isGreaterThan5))
            .map(square)
            .map(format)
            .toList();
        
        results.forEach(System.out::println);
    }
}
```

### Best Practices:

1. **Use @FunctionalInterface Annotation** - Provides compile-time safety
2. **Keep Interfaces Simple** - Single responsibility principle
3. **Use Built-in Interfaces** - Leverage existing functional interfaces when possible
4. **Method References** - Use method references for simple operations
5. **Composition** - Use `andThen()` and `compose()` for function composition
6. **Meaningful Names** - Use descriptive names for custom functional interfaces

### Summary:

- **Functional Interfaces** have exactly one abstract method
- They enable **lambda expressions** and **functional programming** in Java
- **Built-in interfaces** like `Function`, `Predicate`, `Consumer`, `Supplier` cover common use cases
- **@FunctionalInterface** annotation provides compile-time checking
- They support **method references** and **function composition**
- Essential for **streams API** and **modern Java programming**

## What are Sealed Classes (Java 17)?

**Sealed Classes** in Java 17 are a new feature that allows you to control which classes can extend a given class. This is particularly useful for preventing unwanted inheritance and ensuring that only specific classes can be used in a given context.

### Key Characteristics of Sealed Classes:

1. **Permits** - Specifies which classes are allowed to extend the sealed class.
2. **Permits** - Specifies which classes are allowed to extend the sealed class.
3. **Permits** - Specifies which classes are allowed to extend the sealed class.
4. **Permits** - Specifies which classes are allowed to extend the sealed class.
5. **Permits** - Specifies which classes are allowed to extend the sealed class.
6. **Permits** - Specifies which classes are allowed to extend the sealed class.
7. **Permits** - Specifies which classes are allowed to extend the sealed class.
8. **Permits** - Specifies which classes are allowed to extend the sealed class.
9. **Permits** - Specifies which classes are allowed to extend the sealed class.
10. **Permits** - Specifies which classes are allowed to extend the sealed class.

### Example of Sealed Class:

```java
sealed class Vehicle permits Car, Motorcycle {
    // Common properties and methods
    protected String brand;
    protected String model;
    
    public Vehicle(String brand, String model) {
        this.brand = brand;
        this.model = model;
    }
    
    public void displayInfo() {
        System.out.println("This is a vehicle: " + brand + " " + model);
    }
}

final class Car extends Vehicle {
    public Car(String brand, String model) {
        super(brand, model);
    }
    
    @Override
    public void displayInfo() {
        System.out.println("This is a car: " + brand + " " + model);
    }
}

final class Motorcycle extends Vehicle {
    public Motorcycle(String brand, String model) {
        super(brand, model);
    }
    
    @Override
    public void displayInfo() {
        System.out.println("This is a motorcycle: " + brand + " " + model);
    }
}
```

### Benefits of Sealed Classes:

1. **Type Safety** - Prevents unwanted inheritance and ensures only specific classes can extend.
2. **Flexibility** - Allows you to specify which classes are allowed to extend.
3. **Maintainability** - Makes it clear which classes are intended to be extended.
4. **Security** - Prevents accidental inheritance and potential bugs.

### When to Use Sealed Classes:

1. **When you want to control inheritance** - e.g., a base class for a specific set of related classes.
2. **When you want to prevent unwanted extensions** - e.g., a sealed class for a framework's core components.
3. **When you want to ensure a specific class hierarchy** - e.g., a sealed class for a domain model.

### Best Practices:

1. **Use `permits` clause** - Clearly specify which classes are allowed to extend.
2. **Mark sealed classes with `final`** - Ensure they cannot be extended further.
3. **Consider `permits` for each subclass** - If a subclass is itself sealed, you might need to add `permits` for its subclasses.
4. **Documentation** - Clearly document why a class is sealed and which classes are allowed to extend it.

### Summary:

- **Sealed Classes** in Java 17 allow you to control which classes can extend a given class.
- They provide **type safety** and **flexibility** in class inheritance.
- Essential for **framework design** and **domain modeling** where you want to restrict inheritance.
- **Modern Java** (17+) makes this feature available.

## What is Fail-Fast Iteration & how to handle it?

**Fail-Fast Iteration** is a programming technique where an iterator or loop immediately throws an exception if it detects that the collection it is iterating over has been modified during the iteration. This is a common way to detect concurrent modification or unintended modifications during iteration.

### Key Characteristics of Fail-Fast Iteration:

1. **Immediate Detection** - The iterator or loop detects the modification immediately.
2. **Throws Exception** - It throws an exception like `ConcurrentModificationException` or `IllegalStateException`.
3. **Non-deterministic** - The exact exception thrown depends on the implementation.

### Example of Fail-Fast Iteration:

```java
import java.util.ArrayList;
import java.util.List;

public class FailFastExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        
        // Iterate and modify the list
        for (String item : list) {
            System.out.println(item);
            // Simulate modification during iteration
            if (item.equals("B")) {
                list.remove(item); // This will cause ConcurrentModificationException
            }
        }
    }
}
```

### Handling Fail-Fast Iteration:

1. **Use `Iterator` or `ListIterator`** - These provide methods to check for modification and throw exceptions.
2. **Copy the Collection** - Create a copy of the collection before iterating.
3. **Use `ConcurrentHashMap`** - For concurrent collections.
4. **Use `CopyOnWriteArrayList`** - For `List` collections.

### Example of Handling Fail-Fast:

```java
import java.util.ArrayList;
import java.util.List;

public class HandlingFailFastExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        
        // Iterate and modify the list
        for (String item : list) {
            System.out.println(item);
            // Simulate modification during iteration
            if (item.equals("B")) {
                list.remove(item); // This will cause ConcurrentModificationException
            }
        }
    }
}
```

### Best Practices:

1. **Always use `Iterator` or `ListIterator`** - They provide the most robust way to handle iteration.
2. **Copy Collections** - If you need to modify the collection during iteration, create a copy.
3. **Use `ConcurrentHashMap`** - For concurrent collections.
4. **Use `CopyOnWriteArrayList`** - For `List` collections.
5. **Document your code** - Clearly indicate when you are modifying collections during iteration.

### Summary:

- **Fail-Fast Iteration** is a technique to detect unintended modifications during iteration.
- It throws exceptions like `ConcurrentModificationException`.
- **Handling** involves using `Iterator`, copying collections, or using specialized collections.
- **Best practice**: Always use `Iterator` or `ListIterator` and be aware of potential modifications.

## What is ConcurrentModificationException? Fail safe and fail fast iterators?

**ConcurrentModificationException** is an `UnsupportedOperationException` that occurs when a collection is modified while it is being iterated. This is a common issue in concurrent programming.

### Fail-Fast Iterators:

- **Immediate Detection** - They throw `ConcurrentModificationException` immediately.
- **Non-deterministic** - The exact exception thrown depends on the implementation.
- **Common Causes**:
  - Modifying the collection during iteration.
  - Modifying the collection from multiple threads without proper synchronization.
  - Using `Iterator` or `ListIterator` and calling `remove()` on the collection.

### Example of Fail-Fast:

```java
import java.util.ArrayList;
import java.util.List;

public class FailFastExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        
        // Iterate and modify the list
        for (String item : list) {
            System.out.println(item);
            // Simulate modification during iteration
            if (item.equals("B")) {
                list.remove(item); // This will cause ConcurrentModificationException
            }
        }
    }
}
```

### Fail-Safe Iterators:

- **No ConcurrentModificationException** - They do not throw this exception.
- **Copy-on-Write** - They operate on a copy of the collection.
- **Example**: `CopyOnWriteArrayList` and `CopyOnWriteArraySet`.

### Example of Fail-Safe:

```java
import java.util.ArrayList;
import java.util.List;

public class FailSafeExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("C");
        
        // Iterate and modify the list
        for (String item : list) {
            System.out.println(item);
            // Simulate modification during iteration
            if (item.equals("B")) {
                list.remove(item); // This will NOT cause ConcurrentModificationException
            }
        }
    }
}
```

### Best Practices:

1. **Use `Iterator` or `ListIterator`** - They are the most robust way to iterate.
2. **Copy Collections** - If you need to modify the collection during iteration, create a copy.
3. **Use `ConcurrentHashMap`** - For concurrent collections.
4. **Use `CopyOnWriteArrayList`** - For `List` collections.
5. **Document your code** - Clearly indicate when you are modifying collections during iteration.

### Summary:

- **ConcurrentModificationException** is thrown when a collection is modified during iteration.
- **Fail-Fast** iterators throw this exception immediately.
- **Fail-Safe** iterators do not throw this exception and operate on copies.
- **Best practice**: Always use `Iterator` or `ListIterator` and be aware of potential modifications.

## Final, finally and finalize()?

### Final

**Final** is a keyword in Java that can be applied to classes, methods, and variables. It restricts the ability to inherit, override, or modify.

- **Final Classes** - Cannot be extended by other classes.
- **Final Methods** - Cannot be overridden by subclasses.
- **Final Variables** - Cannot be reassigned.

### Finally

**Finally** is a block in Java that is always executed after the `try` and `catch` blocks of a `try-catch-finally` statement. It is used for cleanup activities.

```java
public class FinallyExample {
    public static void main(String[] args) {
        try {
            // Code that might throw an exception
            int result = 10 / 0; // This will cause ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Arithmetic error: " + e.getMessage());
        } finally {
            // Code that will always execute, regardless of whether an exception occurred
            System.out.println("Finally block executed.");
        }
    }
}
```

### Finalize()

**Finalize()** is a method in Java that is called by the garbage collector before the object is destroyed. It is part of the `Object` class.

```java
public class FinalizeExample {
    public static void main(String[] args) {
        // Create an object
        FinalizeExample obj = new FinalizeExample();
        
        // Call finalize() - this is not guaranteed to be called
        // It depends on the garbage collector's timing
        obj.finalize();
        
        // Force garbage collection
        System.gc();
        
        // Call finalize() again - this might not be called if garbage collection happens quickly
        obj.finalize();
    }
    
    @Override
    protected void finalize() throws Throwable {
        System.out.println("Finalize method called for " + this);
        super.finalize();
    }
}
```

### Summary:

- **Final** restricts inheritance, overriding, and reassignment.
- **Finally** is used for cleanup activities.
- **Finalize()** is a method called by the garbage collector.
- **Best practice**: Use `final` for classes, methods, and variables. Use `finally` for cleanup.

## Autoboxing vs Unboxing

**Autoboxing** is the automatic conversion that the Java compiler makes between the primitive types and their corresponding object wrapper classes.

### Example of Autoboxing:

```java
public class AutoboxingExample {
    public static void main(String[] args) {
        // Primitive types
        int primitiveInt = 10;
        double primitiveDouble = 3.14;
        
        // Autoboxing to Integer and Double objects
        Integer autoboxedInt = primitiveInt;
        Double autoboxedDouble = primitiveDouble;
        
        System.out.println("Autoboxed Integer: " + autoboxedInt);
        System.out.println("Autoboxed Double: " + autoboxedDouble);
    }
}
```

**Unboxing** is the reverse of autoboxing. It is the automatic conversion that the Java compiler makes between the object wrapper classes and their corresponding primitive types.

### Example of Unboxing:

```java
public class UnboxingExample {
    public static void main(String[] args) {
        // Integer and Double objects
        Integer autoboxedInt = 10;
        Double autoboxedDouble = 3.14;
        
        // Unboxing to primitive types
        int primitiveInt = autoboxedInt;
        double primitiveDouble = autoboxedDouble;
        
        System.out.println("Unboxed Integer: " + primitiveInt);
        System.out.println("Unboxed Double: " + primitiveDouble);
    }
}
```

### Best Practices:

1. **Use autoboxing** when you need to convert a primitive to an object.
2. **Use unboxing** when you need to convert an object to a primitive.
3. **Be aware of potential `NullPointerException`** if you unbox a null value.
4. **Consider performance implications** if you autobox frequently.

### Summary:

- **Autoboxing** converts primitive types to their corresponding object wrapper classes.
- **Unboxing** converts object wrapper classes back to their corresponding primitive types.
- They are useful for interoperability between primitive types and objects.

## What is Cloneable? Deep clones vs shallow clones

**Cloneable** is an interface in Java that is used to indicate that an object can be cloned.

### Key Characteristics of Cloneable:

1. **Interface** - `Cloneable` is an interface.
2. **No Methods** - It contains no methods.
3. **Purpose** - It serves as a marker interface to indicate that an object can be cloned.

### Example of Cloneable:

```java
public class CloneableExample {
    public static void main(String[] args) {
        // Create an object
        CloneableExample obj = new CloneableExample();
        
        // Try to clone it
        try {
            CloneableExample clonedObj = (CloneableExample) obj.clone();
            System.out.println("Clone successful!");
            System.out.println("Original: " + obj);
            System.out.println("Cloned: " + clonedObj);
        } catch (CloneNotSupportedException e) {
            System.out.println("Cloning not supported or object not cloneable.");
            e.printStackTrace();
        }
    }
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
```

### Deep Cloning vs Shallow Cloning:

**Shallow Cloning** - A new object is created, but its fields are copied by reference. If the original object contains mutable objects, changes to those objects will reflect in both the original and the cloned object.

```java
public class ShallowCloneExample {
    public static void main(String[] args) {
        // Create an object
        Address address = new Address("123 Main St", "Anytown", "12345");
        Person person = new Person("John Doe", address);
        
        // Clone the object
        try {
            Person clonedPerson = (Person) person.clone();
            System.out.println("Shallow Clone Successful!");
            System.out.println("Original: " + person);
            System.out.println("Cloned: " + clonedPerson);
            
            // Modify the address in the original object
            person.getAddress().setStreet("456 Oak Ave");
            System.out.println("\nAfter modifying original address:");
            System.out.println("Original: " + person);
            System.out.println("Cloned: " + clonedPerson);
        } catch (CloneNotSupportedException e) {
            System.out.println("Cloning not supported or object not cloneable.");
            e.printStackTrace();
        }
    }
}

class Address implements Cloneable {
    private String street;
    private String city;
    private String zipCode;
    
    public Address(String street, String city, String zipCode) {
        this.street = street;
        this.city = city;
        this.zipCode = zipCode;
    }
    
    public String getStreet() {
        return street;
    }
    
    public void setStreet(String street) {
        this.street = street;
    }
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

class Person implements Cloneable {
    private String name;
    private Address address;
    
    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }
    
    public String getName() {
        return name;
    }
    
    public Address getAddress() {
        return address;
    }
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}
```

**Deep Cloning** - A new object is created, and all its fields are copied by value. This means that if the original object contains mutable objects, changes to those objects will not affect the cloned object.

```java
public class DeepCloneExample {
    public static void main(String[] args) {
        // Create an object
        Address address = new Address("123 Main St", "Anytown", "12345");
        Person person = new Person("John Doe", address);
        
        // Clone the object
        try {
            Person clonedPerson = (Person) person.clone();
            System.out.println("Deep Clone Successful!");
            System.out.println("Original: " + person);
            System.out.println("Cloned: " + clonedPerson);
            
            // Modify the address in the original object
            person.getAddress().setStreet("456 Oak Ave");
            System.out.println("\nAfter modifying original address:");
            System.out.println("Original: " + person);
            System.out.println("Cloned: " + clonedPerson);
        } catch (CloneNotSupportedException e) {
            System.out.println("Cloning not supported or object not cloneable.");
            e.printStackTrace();
        }
    }
}

class Address implements Cloneable {
    private String street;
    private String city;
    private String zipCode;
    
    public Address(String street, String city, String zipCode) {
        this.street = street;
        this.city = city;
        this.zipCode = zipCode;
    }
    
    public String getStreet() {
        return street;
    }
    
    public void setStreet(String street) {
        this.street = street;
    }
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

class Person implements Cloneable {
    private String name;
    private Address address;
    
    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }
    
    public String getName() {
        return name;
    }
    
    public Address getAddress() {
        return address;
    }
    
    @Override
    protected Object clone() throws CloneNotSupportedException {
        // Deep clone the address
        Address clonedAddress = (Address) address.clone();
        return new Person(name, clonedAddress);
    }
}
```

### Best Practices:

1. **Use `Cloneable`** - Mark classes that can be cloned.
2. **Implement `clone()`** - Override the `clone()` method to perform deep cloning.
3. **Be aware of `CloneNotSupportedException`** - Handle this exception appropriately.
4. **Consider performance** - Deep cloning can be more resource-intensive.

### Summary:

- **Shallow Cloning** copies fields by reference.
- **Deep Cloning** copies fields by value.
- **Cloneable** is a marker interface.
- **Best practice**: Use `Cloneable` and implement `clone()` for deep cloning.