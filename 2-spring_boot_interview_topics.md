# Spring Boot Interview Topics Guide

## 1. Spring Boot Fundamentals

### What is Spring Boot?

- **Auto-configuration** - Automatic configuration based on classpath
- **Starter dependencies** - Pre-configured dependency bundles
- **Embedded servers** - Tomcat, Jetty, Undertow
- **Production-ready features** - Metrics, health checks, externalized configuration
- **Opinionated defaults** - Convention over configuration

### Spring Boot vs Spring Framework

- Reduced boilerplate configuration
- Embedded server support
- Auto-configuration capabilities
- Starter POMs for dependency management
- Production-ready features out of the box

### Spring Boot Architecture

- Spring Boot Application structure
- Main application class with @SpringBootApplication
- Component scanning and bean registration
- Configuration classes and properties

## 2. Core Annotations

### Primary Annotations

- **@SpringBootApplication** - Combines @Configuration, @EnableAutoConfiguration, @ComponentScan
- **@RestController** - Combines @Controller and @ResponseBody
- **@Service** - Service layer component
- **@Repository** - Data access layer component
- **@Component** - Generic stereotype annotation
- **@Configuration** - Configuration class
- **@Bean** - Method-level bean definition

### Request Mapping

- **@RequestMapping** - General purpose mapping
- **@GetMapping** - HTTP GET requests
- **@PostMapping** - HTTP POST requests
- **@PutMapping** - HTTP PUT requests
- **@DeleteMapping** - HTTP DELETE requests
- **@PatchMapping** - HTTP PATCH requests

### Parameter Binding

- **@RequestParam** - Query parameters
- **@PathVariable** - URI path variables
- **@RequestBody** - Request body binding
- **@RequestHeader** - HTTP headers
- **@CookieValue** - Cookie values

## 3. Dependency Injection & IoC

### Inversion of Control (IoC)

- IoC container and bean management
- Bean lifecycle and scopes
- Dependency injection types (constructor, setter, field)

### Bean Scopes

- **Singleton** - Default scope, one instance per container
- **Prototype** - New instance for each request
- **Request** - One instance per HTTP request
- **Session** - One instance per HTTP session
- **Application** - One instance per ServletContext

### Dependency Injection

- **@Autowired** - Automatic dependency injection
- **@Qualifier** - Bean selection when multiple candidates
- **@Primary** - Primary bean when multiple candidates
- **@Value** - Property value injection
- Constructor vs setter vs field injection

## 4. Configuration Management

### Application Properties

- application.properties vs application.yml
- Profile-specific configurations
- Property precedence and sources
- Environment-specific configurations

### Configuration Classes

- **@ConfigurationProperties** - Type-safe configuration properties
- **@EnableConfigurationProperties** - Enabling configuration properties
- **@PropertySource** - External property files
- Configuration validation with JSR-303

### Profiles

- **@Profile** - Profile-specific beans
- **spring.profiles.active** - Active profile configuration
- Profile-specific property files
- Conditional beans with @ConditionalOnProfile

## 5. Auto-Configuration

### Auto-Configuration Mechanism

- **@EnableAutoConfiguration** - Enabling auto-configuration
- **@ConditionalOnClass** - Conditional on classpath presence
- **@ConditionalOnMissingBean** - Conditional on bean absence
- **@ConditionalOnProperty** - Conditional on property values
- **@AutoConfigureAfter** - Ordering auto-configurations

### Custom Auto-Configuration

- Creating custom auto-configuration classes
- META-INF/spring.factories file
- Auto-configuration conditions
- Configuration properties for auto-configuration

### Excluding Auto-Configurations

- Using exclude parameter in @SpringBootApplication
- spring.autoconfigure.exclude property
- Debugging auto-configuration with --debug

## 6. Web Development

### REST API Development

- RESTful principles and best practices
- HTTP status codes and their usage
- Content negotiation
- HATEOAS (Hypermedia as the Engine of Application State)

### Request/Response Handling

- Request body validation with @Valid
- Custom validators and validation groups
- Error handling and exception mapping
- Response entity and HTTP status management

### CORS (Cross-Origin Resource Sharing)

- **@CrossOrigin** - Method/class level CORS
- Global CORS configuration
- CORS preflight requests

### Content Negotiation

- Producing JSON, XML responses
- **@JsonView** - Selective serialization
- Custom message converters

## 7. Data Access

### Spring Data JPA

- **@Entity** - JPA entity mapping
- **@Repository** - Data access layer
- **JpaRepository** interface and methods
- Custom query methods with method naming
- **@Query** - Custom JPQL/SQL queries
- **@Modifying** - Update/delete queries

### Database Configuration

- DataSource configuration
- Connection pooling (HikariCP, Tomcat JDBC)
- Multiple database configurations
- Transaction management

### Database Migrations

- Flyway integration
- Liquibase integration
- Schema initialization scripts

### Caching

- **@EnableCaching** - Enabling cache support
- **@Cacheable** - Method result caching
- **@CacheEvict** - Cache eviction
- **@CachePut** - Cache update
- Cache providers (Redis, EhCache, Caffeine)

## 8. Security

### Spring Security Integration

- Security starter dependency
- Default security configuration
- Custom security configuration
- Authentication vs Authorization

### Authentication

- In-memory authentication
- Database authentication
- LDAP authentication
- JWT (JSON Web Token) authentication
- OAuth2 integration

### Authorization

- Method-level security with @PreAuthorize/@PostAuthorize
- URL-based security configuration
- Role-based access control (RBAC)
- Expression-based access control

### Security Features

- CSRF protection
- Session management
- Password encoding (BCrypt)
- Security headers configuration

## 9. Testing

### Testing Framework Integration

- **@SpringBootTest** - Integration testing
- **@WebMvcTest** - Web layer testing
- **@DataJpaTest** - JPA repository testing
- **@JsonTest** - JSON serialization testing
- **@MockBean** - Mocking beans in tests

### Test Slices

- **@WebMvcTest** - Only web layer
- **@DataJpaTest** - Only JPA layer
- **@JsonTest** - Only JSON mapping
- **@TestConfiguration** - Test-specific configuration

### Testing Best Practices

- Unit vs integration testing
- Test profiles and configurations
- TestContainers for database testing
- MockMvc for web layer testing

## 10. Actuator & Monitoring

### Spring Boot Actuator

- **Health endpoints** - Application health monitoring
- **Metrics endpoints** - Application metrics
- **Info endpoints** - Application information
- **Environment endpoints** - Configuration properties

### Production Monitoring

- Custom health indicators
- Custom metrics with Micrometer
- Prometheus integration
- Application monitoring and alerting

### Endpoint Security

- Securing actuator endpoints
- Custom endpoint creation
- Endpoint configuration and exposure

## 11. Microservices with Spring Boot

### Service Discovery

- Eureka Server and Client
- Service registration and discovery
- Load balancing with Ribbon

### API Gateway

- Spring Cloud Gateway
- Routing and filtering
- Rate limiting and circuit breakers

### Communication Patterns

- **Synchronous** - RestTemplate, WebClient
- **Asynchronous** - Message queues, Event-driven
- Service-to-service communication
- Circuit breaker pattern with Hystrix/Resilience4j

### Configuration Management

- Spring Cloud Config Server
- Centralized configuration management
- Configuration refresh without restart

## 12. Message Queuing

### JMS Integration

- **@EnableJms** - Enabling JMS support
- **@JmsListener** - Message consumption
- **JmsTemplate** - Message production
- Message converters and serialization

### RabbitMQ Integration

- **@EnableRabbit** - Enabling RabbitMQ
- **@RabbitListener** - Message consumption
- **RabbitTemplate** - Message production
- Exchange, queue, and binding configuration

### Apache Kafka Integration

- **@EnableKafka** - Enabling Kafka support
- **@KafkaListener** - Message consumption
- **KafkaTemplate** - Message production
- Topic configuration and partitioning

## 13. Database Integration

### JPA/Hibernate Integration

- Entity mapping and relationships
- **@OneToOne, @OneToMany, @ManyToOne, @ManyToMany**
- Lazy vs eager loading
- Transaction management with @Transactional

### Database Migration Tools

- **Flyway** - Version-based migration
- **Liquibase** - Changeset-based migration
- Migration best practices
- Rollback strategies

### Connection Pooling

- HikariCP configuration
- Connection pool sizing
- Connection leak detection
- Performance tuning

## 14. Error Handling & Validation

### Global Exception Handling

- **@ControllerAdvice** - Global exception handler
- **@ExceptionHandler** - Method-level exception handling
- Custom error responses
- Error logging and monitoring

### Bean Validation

- **@Valid** - Triggering validation
- **@NotNull, @NotEmpty, @NotBlank** - Null/empty checks
- **@Size, @Min, @Max** - Size and range validation
- **@Pattern** - Regular expression validation
- Custom validators

### Error Response Standardization

- ErrorDetails and error response DTOs
- HTTP status code mapping
- Validation error aggregation

## 15. Performance & Optimization

### Application Performance

- Connection pool optimization
- Caching strategies
- Lazy loading optimization
- Query optimization

### Memory Management

- Heap and non-heap memory monitoring
- Garbage collection tuning
- Memory leak detection
- Profiling tools integration

### Database Performance

- Query optimization
- Index usage
- Connection pooling best practices
- Read/write splitting

## 16. DevOps & Deployment

### Containerization

- **Docker** integration and best practices
- Multi-stage Docker builds
- Container optimization for Spring Boot

### Cloud Deployment

- **AWS** deployment (EC2, ECS, Lambda)
- **Azure** Spring Cloud
- **Google Cloud Platform** integration
- **Kubernetes** deployment and configuration

### CI/CD Integration

- Maven/Gradle build optimization
- Jenkins pipeline integration
- GitHub Actions for Spring Boot
- Automated testing in pipelines

## 17. Security Best Practices

### Application Security

- Input validation and sanitization
- SQL injection prevention
- XSS protection
- Secure headers configuration

### Authentication & Authorization

- JWT token management
- Session security
- Password policies
- Multi-factor authentication

### Data Protection

- Encryption at rest and in transit
- Sensitive data handling
- Audit logging
- Compliance considerations (GDPR, etc.)

## 18. Common Interview Questions

### Conceptual Questions

1. What are the advantages of Spring Boot over Spring Framework?
2. Explain the concept of auto-configuration in Spring Boot
3. What is the difference between @Component, @Service, and @Repository?
4. How does Spring Boot handle embedded servers?
5. Explain the Spring Boot starter concept

### Technical Questions

1. How do you create a custom auto-configuration?
2. Explain the difference between @RequestParam and @PathVariable
3. How do you handle exceptions globally in Spring Boot?
4. What is the purpose of @ConfigurationProperties?
5. How do you implement caching in Spring Boot?

### Scenario-Based Questions

1. How would you implement security in a Spring Boot application?
2. Design a microservice architecture using Spring Boot
3. How would you handle database migrations in production?
4. Implement a health check for external service dependencies
5. How would you optimize a slow-performing Spring Boot application?

### Debugging Questions

1. How do you debug auto-configuration issues?
2. What tools would you use to monitor a Spring Boot application?
3. How do you handle circular dependency issues?
4. Debugging connection pool issues
5. Memory leak detection and resolution

## 19. Best Practices

### Code Organization

- Package structure conventions
- Separation of concerns
- Layered architecture implementation
- Clean code principles

### Configuration Management

- Externalized configuration
- Environment-specific properties
- Sensitive data handling
- Configuration validation

### Error Handling

- Consistent error response format
- Proper HTTP status codes
- Logging best practices
- Error monitoring and alerting

### Performance

- Database query optimization
- Caching strategies
- Connection pooling
- Asynchronous processing

## 20. Advanced Topics

### Custom Starters

- Creating custom Spring Boot starters
- Auto-configuration for custom starters
- Conditional beans and properties
- Documentation and usage examples

### Spring Boot Internals

- Application context initialization
- Bean lifecycle management
- Auto-configuration ordering
- Classpath scanning mechanism

### Advanced Testing

- Test slices and their purposes
- Integration testing strategies
- Contract testing with Spring Cloud Contract
- Performance testing approaches

---

## Preparation Strategy

### Study Approach

1. **Hands-on Practice** - Build projects using different features
2. **Understand Internals** - Know how auto-configuration works
3. **Real-world Scenarios** - Practice common use cases
4. **Code Reviews** - Analyze well-written Spring Boot applications
5. **Stay Current** - Follow Spring Boot releases and new features

### Common Pitfalls to Avoid

- Over-relying on auto-configuration without understanding
- Improper exception handling
- Security misconfigurations
- Performance issues with default settings
- Inadequate testing coverage

### Interview Tips

- Explain concepts with practical examples
- Discuss trade-offs and alternatives
- Demonstrate hands-on experience
- Show understanding of production concerns
- Be prepared for live coding exercises

---

*Master these topics to excel in your Spring Boot interviews!*
