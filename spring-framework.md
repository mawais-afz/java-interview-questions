# Spring Framework

## Basics

1. **What is Spring Framework and what are its core modules?**

   Spring Framework is a comprehensive open-source Java application framework that provides infrastructure support and tools for building enterprise applications. It was created by Rod Johnson in 2003 and has since become one of the most popular Java frameworks.

   Core features of Spring Framework include:

   - Dependency Injection (DI) - Manages object dependencies and promotes loose coupling
   - Inversion of Control (IoC) - Transfers control of object creation and lifecycle to the container
   - Aspect-Oriented Programming (AOP) - Enables cross-cutting concerns to be separated from business logic

   The framework is organized into several core modules:

   - Spring Core Container - Provides the fundamental IoC and DI functionality
   - Spring AOP - Implements aspect-oriented programming capabilities
   - Spring JDBC/ORM - Offers database access and ORM integration
   - Spring MVC - Framework for building web applications
   - Spring Security - Handles authentication, authorization and other security features
   - Spring Test - Supports unit and integration testing of Spring components
   - Spring Data - Simplifies data access for various databases
   - Spring Boot - Provides rapid application development with auto-configuration

   Each module can be used independently, making Spring highly modular and flexible. The framework emphasizes convention over configuration, testability, and enterprise-ready features while reducing boilerplate code.

2. **Briefly explain the term Spring Framework**

   Spring Framework is a comprehensive, lightweight, and widely-used open-source application framework for Java. It provides infrastructure support for developing Java applications, offering features like dependency injection (DI), aspect-oriented programming (AOP), transaction management, and MVC web framework. Spring simplifies enterprise Java development by promoting loose coupling through its core IoC (Inversion of Control) container.

3. **What is the best way to inject dependency? Also, state the reason.**

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

4. **How to handle exceptions in Spring MVC Framework?**

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

5. **What is the difference between @Controller and @RestController?**

   - `@Controller`
     - Traditional Spring MVC controller
     - Returns view names that resolve to templates/views
     - Requires `@ResponseBody` to return data directly
     - Typically used for web applications serving HTML pages

   Example:

   ```java
   @Controller
   public class UserController {
       @GetMapping("/user")
       public String getUser(Model model) {
           model.addAttribute("user", user);
           return "user-view"; // Returns view name
       }
   }
   ```

   - `@RestController`
     - Combines `@Controller` and `@ResponseBody`
     - Automatically serializes return values to JSON/XML
     - Designed for RESTful web services
     - Every method returns data directly, not view names

   Example:

   ```java
   @RestController
   public class UserRestController {
       @GetMapping("/api/user")
       public User getUser() {
           return user; // Directly returns object
       }
   }
   ```

6. **List some of the important annotations in annotation-based Spring configuration.**
   Core Annotations:

   - `@Configuration`: Indicates that a class declares one or more @Bean methods
   - `@ComponentScan`: Configures component scanning directives
   - `@Bean`: Declares a method as a bean producer
   - `@Component`: Generic stereotype annotation for Spring-managed components
   - `@Service`: Indicates that a class is a service layer component
   - `@Repository`: Indicates that a class is a data access layer component
   - `@Controller`: Marks a class as Spring MVC controller
   - `@RestController`: Combines @Controller and @ResponseBody

   Dependency Injection:

   - `@Autowired`: Marks a dependency to be automatically injected
   - `@Qualifier`: Specifies which bean should be injected when multiple options exist
   - `@Value`: Injects values from properties files
   - `@Resource`: Java standard annotation for dependency injection
   - `@Inject`: Java standard annotation alternative to @Autowired

   AOP and Transaction:

   - `@Aspect`: Declares a class as an aspect
   - `@Transactional`: Declares transactional boundaries and behavior
   - `@EnableTransactionManagement`: Enables Spring's transaction management

   Web and REST:

   - `@RequestMapping`: Maps web requests to handler methods
   - `@PathVariable`: Binds URI template variables to method parameters
   - `@RequestBody`: Binds HTTP request body to method parameter
   - `@ResponseBody`: Indicates that return value should be bound to web response body
   - `@Valid`: Triggers validation of an annotated argument
   - `@ResponseBody`: Indicates that return value should be bound to web response body

7. **What is a Spring Bean? Understanding the Core Component**

   - A Spring Bean is an instance of a class managed by the Spring IoC container
   - Beans are created, configured, and managed by the Spring IoC container
   - They are the fundamental components in a Spring application

8. **How to Set Spring Bean Scope**

   - Bean scope can be set using:
     - @Scope annotation: `@Scope("scopeName")`
     - XML configuration: `<bean scope="scopeName">`

   Supported Scopes:

   - `singleton` (default)
     - One instance per Spring IoC container
     - Shared across all requests
   - `prototype`
     - New instance created for each request
     - Not managed after creation
   - `request`
     - New instance per HTTP request
     - Web-aware Spring ApplicationContext only
   - `session`
     - New instance per HTTP session
     - Web-aware Spring ApplicationContext only
   - `application`
     - One instance per ServletContext
     - Web-aware Spring ApplicationContext only
   - `websocket`
     - New instance per WebSocket session
     - Web-aware Spring ApplicationContext only

   Example:

   ```java
   @Component
   @Scope("prototype")
   public class MyBean { }
   ```

9. **Explain JPA in Java**

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

10. **Explain the role of DispatcherServlet and ContextLoaderListener**

- DispatcherServlet:

  - Front Controller pattern implementation in Spring MVC
  - Central servlet that handles all HTTP requests and responses
  - Responsibilities:
    - Receives incoming requests
    - Maps requests to appropriate handlers/controllers
    - Resolves views
    - Returns responses to client
  - Creates its own WebApplicationContext containing web-related beans

- ContextLoaderListener:
  - Creates and manages the root ApplicationContext
  - Loads application-wide configurations (services, repositories, etc.)
  - Parent context for DispatcherServlet's context
  - Responsibilities:
    - Initializes root context before DispatcherServlet
    - Ties Spring context lifecycle to ServletContext
    - Loads non-web beans and infrastructure configurations
    - Ensures proper context hierarchy

11. **What is the best way to inject dependency? Also, state the reason**

    Constructor Injection is considered the best practice for dependency injection in Spring

    Reasons:

    - Ensures mandatory dependencies are available at object creation time
    - Promotes immutability by allowing final fields
    - Makes dependencies explicit and clear
    - Facilitates easier unit testing
    - Supports dependency inversion principle
    - Prevents circular dependencies at compile-time

      Example:

      ```java
      @Service
      public class UserService {
         private final UserRepository userRepository;

         @Autowired
         public UserService(UserRepository userRepository) {
            this.userRepository = userRepository;
         }
      }
      ```

      Key Benefits:

      - Compile-time safety
      - Clear dependency requirements
      - Easier to understand and maintain
      - Supports dependency inversion principle
      - Allows for easier mocking in unit tests

12. **What are the differences between constructor injection and setter injection?**

    Constructor Injection and Setter Injection are two primary methods of dependency injection in Spring, each with distinct characteristics:

    Constructor Injection:

    - Dependencies are set through a class constructor
    - Makes dependencies mandatory and ensures they are available at object creation
    - Supports immutability by allowing final fields
    - Prevents partial initialization of objects
    - Provides compile-time safety
    - Better for required dependencies

    Setter Injection:

    - Dependencies are set through setter methods
    - Allows optional dependencies
    - Enables changing dependencies after object creation
    - More flexible for optional or changeable dependencies
    - Supports runtime configuration changes
    - Allows for lazy initialization of dependencies

    Example Comparison:

    ```java
    // Constructor Injection
    @Service
    public class UserService {
        private final UserRepository userRepository;

        @Autowired
        public UserService(UserRepository userRepository) {
            this.userRepository = userRepository;
        }
    }

    // Setter Injection
    @Service
    public class NotificationService {
        private EmailService emailService;

        @Autowired
        public void setEmailService(EmailService emailService) {
            this.emailService = emailService;
        }
    }
    ```

    Recommendation:

    - Prefer Constructor Injection for mandatory dependencies
    - Use Setter Injection for optional or configurable dependencies

13. **What is Autowiring in Spring?**

    Autowiring is a powerful dependency injection mechanism in the Spring Framework that automatically resolves and injects dependencies without explicit configuration. It simplifies bean wiring by allowing the Spring container to automatically connect beans based on type, name, or other criteria.

    **Autowiring Modes**:

    1. **no (Default)**:

       - Manual bean configuration required
       - No automatic dependency injection
       - Provides maximum control and explicit configuration
       - Most verbose approach

    2. **byType**:

       - Automatically wires beans by matching their type
       - Requires unique bean types in the context
       - Throws an exception if multiple beans of the same type exist
       - Matches based on type compatibility

    3. **byName**:

       - Matches beans by their name
       - Looks for a bean with a name matching the target property
       - Relies on consistent and predictable bean naming conventions
       - Useful for clear, name-based dependency resolution

    4. **constructor**:

       - Specifically for constructor-based dependency injection
       - Matches constructor arguments by type
       - Similar to byType, but focused on constructor parameters
       - Ensures dependencies are available during object creation

    5. **@Autowired (Annotation-based)**:
       - Modern, recommended approach for dependency injection
       - Flexible annotation-driven autowiring
       - Applicable to constructors, methods, and fields
       - Supports fine-grained control with @Qualifier annotations
       - Provides type-safe and convenient dependency injection

14. **How to handle exceptions in Spring MVC Framework?**

    Spring MVC provides multiple robust mechanisms for exception handling:

    1. **@ExceptionHandler Annotation**

       - Handles exceptions at the controller level
       - Allows specific exception handling within a controller
       - Provides granular control over exception responses

       ```java
       @RestController
       public class UserController {
           @ExceptionHandler(ResourceNotFoundException.class)
           public ResponseEntity<ErrorResponse> handleResourceNotFound(ResourceNotFoundException ex) {
               ErrorResponse error = new ErrorResponse(
                   HttpStatus.NOT_FOUND.value(),
                   ex.getMessage()
               );
               return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
           }
       }
       ```

    2. **@ControllerAdvice Global Exception Handling**

       - Centralized exception management across all controllers
       - Handles exceptions application-wide
       - Supports multiple exception types

       ```java
       @ControllerAdvice
       public class GlobalExceptionHandler {
           @ExceptionHandler(Exception.class)
           public ResponseEntity<ErrorResponse> handleGeneralException(Exception ex) {
               ErrorResponse error = new ErrorResponse(
                   HttpStatus.INTERNAL_SERVER_ERROR.value(),
                   "An unexpected error occurred"
               );
               return new ResponseEntity<>(error, HttpStatus.INTERNAL_SERVER_ERROR);
           }

           @ExceptionHandler(ValidationException.class)
           public ResponseEntity<ErrorResponse> handleValidationException(ValidationException ex) {
               ErrorResponse error = new ErrorResponse(
                   HttpStatus.BAD_REQUEST.value(),
                   ex.getMessage()
               );
               return new ResponseEntity<>(error, HttpStatus.BAD_REQUEST);
           }
       }
       ```

    3. **ResponseEntityExceptionHandler**

       - Provides a base class for global exception handling
       - Handles standard Spring MVC exceptions
       - Offers extensive customization options

       ```java
       @ControllerAdvice
       public class CustomResponseEntityExceptionHandler extends ResponseEntityExceptionHandler {
           @Override
           protected ResponseEntity<Object> handleMethodArgumentNotValid(
               MethodArgumentNotValidException ex,
               HttpHeaders headers,
               HttpStatus status,
               WebRequest request
           ) {
               List<String> errors = ex.getBindingResult()
                   .getFieldErrors()
                   .stream()
                   .map(FieldError::getDefaultMessage)
                   .collect(Collectors.toList());

               ErrorResponse errorResponse = new ErrorResponse(
                   HttpStatus.BAD_REQUEST.value(),
                   "Validation failed",
                   errors
               );

               return new ResponseEntity<>(errorResponse, HttpStatus.BAD_REQUEST);
           }
       }
       ```

    4. **Custom Error Pages**

       - Configure custom error pages for different HTTP status codes
       - Provides user-friendly error handling
       - Can be configured in `application.properties` or `web.xml`

       ```properties
       # Spring Boot application.properties
       server.error.whitelabel.enabled=false
       spring.mvc.throw-exception-if-no-handler-found=true
       spring.web.resources.add-mappings=false
       ```

    Best Practices:

    - Use specific exception types
    - Log exceptions for debugging
    - Return meaningful error responses
    - Handle both expected and unexpected exceptions
    - Avoid exposing sensitive system details in error messages

15. **Integrating Spring and Hibernate Frameworks**

    Key Integration Steps:

    1. **Add Dependencies**

       - Include Spring ORM and Hibernate dependencies in `pom.xml`

       ```xml
       <dependency>
           <groupId>org.springframework</groupId>
           <artifactId>spring-orm</artifactId>
       </dependency>
       <dependency>
           <groupId>org.hibernate</groupId>
           <artifactId>hibernate-core</artifactId>
       </dependency>
       ```

    2. **Configure Hibernate SessionFactory**

       - Use `LocalSessionFactoryBean` in Spring configuration

       ```java
       @Configuration
       public class HibernateConfig {
           @Bean
           public LocalSessionFactoryBean sessionFactory(DataSource dataSource) {
               LocalSessionFactoryBean sessionFactory = new LocalSessionFactoryBean();
               sessionFactory.setDataSource(dataSource);
               sessionFactory.setPackagesToScan("com.yourpackage.model");
               sessionFactory.setHibernateProperties(hibernateProperties());
               return sessionFactory;
           }

           private Properties hibernateProperties() {
               Properties properties = new Properties();
               properties.setProperty("hibernate.dialect", "org.hibernate.dialect.MySQL5Dialect");
               properties.setProperty("hibernate.show_sql", "true");
               return properties;
           }
       }
       ```

    3. **Transaction Management**

       - Enable declarative transaction management

       ```java
       @Configuration
       @EnableTransactionManagement
       public class TransactionConfig {
           @Bean
           public PlatformTransactionManager transactionManager(SessionFactory sessionFactory) {
               return new HibernateTransactionManager(sessionFactory);
           }
       }
       ```

    4. **DAO Layer Implementation**

       - Use Hibernate with Spring's `@Repository`

       ```java
       @Repository
       public class UserDaoImpl implements UserDao {
           @Autowired
           private SessionFactory sessionFactory;

           @Override
           @Transactional
           public void saveUser(User user) {
               sessionFactory.getCurrentSession().save(user);
           }
       }
       ```

    Best Practices:

    - Use `@Transactional` for managing database transactions
    - Configure connection pooling
    - Use Hibernate validation annotations
    - Leverage Spring's dependency injection
    - Separate concerns between layers

16. **What is Hibernate Framework?**

    Hibernate is an open-source Object-Relational Mapping (ORM) tool for Java that simplifies database interaction by mapping Java objects to database tables and vice versa. Key features include:

    - Abstracts complex SQL operations
    - Provides automatic table creation and mapping
    - Supports multiple database systems
    - Reduces boilerplate database code
    - Implements Java Persistence API (JPA)
    - Offers caching mechanisms for improved performance
    - Supports both XML and annotation-based configurations

    Hibernate allows developers to work with Java objects directly, eliminating the need to write low-level database access code, thus improving productivity and maintainability of database-driven applications.

17. **Key Benefits of Hibernate Framework**

    Hibernate offers several critical benefits for Java developers:

    1. **Object-Relational Mapping (ORM)**

       - Seamlessly maps Java objects to database tables
       - Eliminates complex SQL writing and database interaction code
       - Provides a high-level abstraction of database operations

    2. **Productivity and Maintainability**

       - Reduces boilerplate database access code
       - Simplifies database operations with intuitive object-oriented approach
       - Allows developers to focus on business logic instead of database mechanics

    3. **Database Independence**

       - Supports multiple database systems
       - Provides database portability
       - Allows easy switching between different database platforms with minimal code changes

    4. **Performance Optimization**

       - Built-in first and second-level caching mechanisms
       - Lazy loading of database entities
       - Efficient query optimization techniques
       - Minimizes database round trips

    5. **Advanced Features**

       - Supports both XML and annotation-based configurations
       - Implements Java Persistence API (JPA)
       - Provides robust transaction management
       - Offers automatic schema generation
       - Supports complex querying with HQL (Hibernate Query Language)

    6. **Validation and Integrity**

       - Supports database constraint validations
       - Ensures data integrity through ORM mappings
       - Provides built-in validation annotations

    7. **Open-Source and Community Support**
       - Actively maintained open-source project
       - Large community and extensive documentation
       - Regular updates and improvements

18. **Explain Hibernate Architecture?**

    Hibernate's architecture is designed to provide a robust and flexible Object-Relational Mapping (ORM) solution with multiple layers of abstraction:

    1. **Core Components**

       - **Configuration**: Reads mapping and configuration files
       - **SessionFactory**: Thread-safe object that creates Session instances
       - **Session**: Single-threaded unit of work with the database
       - **Transaction**: Manages database transaction boundaries

    2. **Architectural Layers**

       ```
       +----------------------------+
       | Application Layer          |
       | (Java Objects/Entities)    |
       +----------------------------+
       | Hibernate ORM Layer        |
       | (Mapping & Persistence)    |
       +----------------------------+
       | Database Layer             |
       | (Relational Database)      |
       +----------------------------+
       ```

    3. **Key Architectural Elements**

       - **Persistent Objects**: Java classes mapped to database tables
       - **Hibernate Session**: Manages CRUD operations
       - **Transaction Management**: Ensures data integrity
       - **Connection Pooling**: Efficiently manages database connections

    4. **Data Access Process**

       1. Configure Hibernate with database settings
       2. Create SessionFactory
       3. Open a Session
       4. Begin a transaction
       5. Perform database operations
       6. Commit or rollback transaction
       7. Close the Session

    5. **Abstraction Levels**
       - **Low-level**: Direct JDBC connection management
       - **Mid-level**: Session and Transaction management
       - **High-level**: Object-oriented data manipulation

    The architecture provides a flexible, performant approach to database interactions, abstracting complex database operations into simple, manageable Java interfaces.

19. **How Spring Boot Manages Application Properties?**

    Spring Boot provides a flexible and hierarchical system for managing application properties:

    1. **Property Sources**

       - application.properties/application.yml files
       - Environment variables
       - Command-line arguments
       - Cloud configuration
       - Profile-specific properties (application-{profile}.properties)

    2. **Property Hierarchy (Highest to Lowest Priority)**

       1. Command-line arguments
       2. SPRING_APPLICATION_JSON properties
       3. ServletConfig init parameters
       4. ServletContext init parameters
       5. JNDI attributes
       6. Java System properties
       7. OS environment variables
       8. Profile-specific properties
       9. Application properties
       10. Default properties

    3. **Common Locations (Searched in Order)**

       - File in ./config subdirectory
       - File in current directory
       - Classpath /config package
       - Classpath root

    4. **Key Features**

       - Property placeholder resolution (${property.name})
       - YAML support
       - Type-safe configuration properties (@ConfigurationProperties)
       - Environment-specific profiles
       - Property validation
       - Relaxed binding (property.name = propertyName = PROPERTY_NAME)

    5. **Best Practices**
       - Use meaningful property namespaces
       - Leverage profile-specific configurations
       - Document configuration properties
       - Use configuration metadata
       - Implement property validation when necessary

    This system allows for flexible, environment-specific configuration management while maintaining clear precedence rules and easy overrides.

20. **What is difference between Authorization & Authentication?**

    | Aspect            | Authentication                         | Authorization                                                     |
    | ----------------- | -------------------------------------- | ----------------------------------------------------------------- |
    | Definition        | Process of verifying who someone is    | Process of verifying what specific resources a user has access to |
    | Purpose           | Validates user identity                | Validates user permissions                                        |
    | Timing            | Done before authorization              | Done after successful authentication                              |
    | Example           | Verifying username/password            | Checking if user can access admin page                            |
    | Data Needed       | Credentials (username, password, etc.) | Privileges, roles, and permissions                                |
    | Error Message     | "Invalid credentials"                  | "Access denied"                                                   |
    | Security Level    | First level of security                | Second level of security                                          |
    | Protocol Examples | OAuth, OpenID, SAML                    | RBAC, ABAC                                                        |
    | Risk on Failure   | Prevents access to system              | Prevents access to specific resources                             |
    | User Awareness    | User actively participates             | Happens in background                                             |

21. **A user is login with a username and password now another user login with the same username and password now you have to show a session expiration notification to the first user. What will be the approach?**

    1. **Session Management**
       - Use Spring Session to manage user sessions
       - Store session information in a centralized store (Redis/Database)
       - Track active sessions per user
       - Generate unique session IDs for each login

    2. **Concurrent Session Control**
       - Implement ConcurrentSessionControlAuthenticationStrategy
       - Set maximum sessions allowed per user (e.g., maxSessionsPreventsLogin=false)
       - Configure session registry to track session information

    3. **Session Invalidation**
       - When new login occurs, identify existing sessions for the user
       - Mark previous session as expired in session registry
       - Invalidate the old session

    4. **User Notification**
       - Implement WebSocket/Server-Sent Events for real-time communication
       - Send session expiration message to previous session
       - Display notification using JavaScript on client side
       - Redirect to login page after acknowledgment

    5. **Security Considerations**
       - Implement proper session timeout
       - Use secure session IDs
       - Encrypt session data if sensitive
       - Implement proper logout mechanisms

22. **Two users concurrently login using the same credentials. How to manage their sessions?**

    There are several approaches to handle concurrent logins with the same credentials:

    1. **First-In-First-Out (FIFO) Strategy**
       - Allow new login but terminate oldest session
       - Configure ConcurrentSessionControlAuthenticationStrategy
       - Set maximumSessions=1 in Spring Security config
       - Notify terminated user via WebSocket/SSE

    2. **Last-In-First-Out (LIFO) Strategy**
       - Prevent new login attempts when session exists
       - Set maxSessionsPreventsLogin=true
       - Return error message to new login attempt
       - Keep existing session active

    3. **Allow Multiple Sessions**
       - Track all active sessions per user
       - Use Spring Session with Redis/Database backend
       - Implement custom SessionRegistry
       - Allow configured maximum number of sessions

    4. **Implementation Steps**
       - Configure session management in SecurityConfig
       - Implement SessionInformationExpiredStrategy
       - Set up real-time notifications
       - Handle session timeouts appropriately
       - Log session events for auditing

    5. **Best Practices**
       - Use secure session IDs
       - Implement proper session timeout
       - Store session data securely
       - Provide clear user feedback
       - Monitor concurrent sessions
