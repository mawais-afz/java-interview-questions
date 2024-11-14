# Spring Framework

## Basics

1. **Briefly explain the term Spring Framework**

   Spring Framework is a comprehensive, lightweight, and widely-used open-source application framework for Java. It provides infrastructure support for developing Java applications, offering features like dependency injection (DI), aspect-oriented programming (AOP), transaction management, and MVC web framework. Spring simplifies enterprise Java development by promoting loose coupling through its core IoC (Inversion of Control) container.

2. **What is the best way to inject dependency? Also, state the reason.**

   Constructor injection is generally considered the best way to inject dependencies for several reasons:

   1. **Promotes Immutability**

      - Dependencies can be marked as final
      - Objects are always in a valid state after construction

   2. **Makes Dependencies Explicit**

      - Required dependencies are clearly visible in the constructor signature
      - Easier to understand class requirements

   3. **Easier Testing**

      - Facilitates unit testing as dependencies can be easily mocked
      - No need for reflection or complex test setup

   4. **Prevents Circular Dependencies**
      - Helps identify circular dependency issues at compile-time
      - Forces better design decisions

   Example:

   ```java
   @Service
   public class UserService {
       private final UserRepository userRepository;

       @Autowired // Optional in newer Spring versions
       public UserService(UserRepository userRepository) {
           this.userRepository = userRepository;
       }
   }
   ```

   While setter injection and field injection are alternatives, they have drawbacks:

   - Setter injection doesn't ensure dependency initialization
   - Field injection makes testing harder and hides dependencies

## Spring MVC

1. **How to handle exceptions in Spring MVC Framework?**

   Spring MVC provides several ways to handle exceptions:

   1. **@ExceptionHandler annotation**

      - Handles exceptions at the controller level
      - Can be applied to methods in @Controller classes

      ```java
      @ExceptionHandler(value = Exception.class)
      public String handleException(Exception e) {
          // Handle exception
          return "error";
      }
      ```

   2. **@ControllerAdvice**

      - Global exception handling across controllers
      - Centralizes exception handling logic

      ```java
      @ControllerAdvice
      public class GlobalExceptionHandler {
          @ExceptionHandler(value = Exception.class)
          public ResponseEntity<Object> handleException(Exception e) {
              return new ResponseEntity<>("Error occurred", HttpStatus.INTERNAL_SERVER_ERROR);
          }
      }
      ```

   3. **SimpleMappingExceptionResolver**

      - Maps exception classes to view names
      - Configured in XML or Java configuration

      ```java
      @Configuration
      public class WebConfig extends WebMvcConfigurationSupport {
          @Bean
          public SimpleMappingExceptionResolver exceptionResolver() {
              SimpleMappingExceptionResolver resolver = new SimpleMappingExceptionResolver();
              Properties mappings = new Properties();
              mappings.put("Exception", "error");
              resolver.setExceptionMappings(mappings);
              return resolver;
          }
      }
      ```

   4. **ResponseStatusException**
      - Built-in exception type in Spring 5
      - Allows throwing HTTP status codes programmatically
      ```java
      throw new ResponseStatusException(
          HttpStatus.NOT_FOUND, "Resource not found"
      );
      ```

   Best Practices:

   - Use @ControllerAdvice for global exception handling
   - Create custom exceptions for specific business cases
   - Provide meaningful error messages
   - Log exceptions appropriately
   - Consider security implications when exposing error details

## Spring Beans

1. **What is a Spring Bean? Understanding the Core Component**

   - A Spring Bean is an instance of a class managed by the Spring IoC container
   - Beans are created, configured, and managed by the Spring IoC container
   - They are the fundamental components in a Spring application

2. **How to Set Spring Bean Scope**

   - Bean scope can be set using:
     - @Scope annotation: `@Scope("scopeName")`
     - XML configuration: `<bean scope="scopeName">`

   Supported Scopes:

   - singleton (default)
     - One instance per Spring IoC container
     - Shared across all requests
   - prototype
     - New instance created for each request
     - Not managed after creation
   - request
     - New instance per HTTP request
     - Web-aware Spring ApplicationContext only
   - session
     - New instance per HTTP session
     - Web-aware Spring ApplicationContext only
   - application
     - One instance per ServletContext
     - Web-aware Spring ApplicationContext only
   - websocket
     - New instance per WebSocket session
     - Web-aware Spring ApplicationContext only

   Example:

   ```java
   @Component
   @Scope("prototype")
   public class MyBean { }
   ```

## Spring JPA

1. **Explain JPA in Java**
   - JPA (Java Persistence API) is a Java specification for managing relational data in Java applications
   - It provides a standardized way to map Java objects to database tables (Object-Relational Mapping)
   - Key features:
     - Entity mapping using annotations like @Entity, @Table, @Column
     - JPQL (Java Persistence Query Language) for database queries
     - EntityManager API for persistence operations
     - Support for relationships (@OneToMany, @ManyToOne, etc.)
   - Popular implementations include:
     - Hibernate (most widely used)
     - EclipseLink
     - OpenJPA
   - Benefits:
     - Reduces boilerplate JDBC code
     - Database vendor independence
     - Automatic transaction management
     - Caching capabilities
