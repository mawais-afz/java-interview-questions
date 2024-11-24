1. **What is JDBC?**
   JDBC (Java Database Connectivity) is a Java API that enables Java applications to interact with databases. Key points about JDBC:

   - It provides a standard interface for connecting to and executing queries on relational databases
   - Consists of JDBC API (java.sql package) and JDBC Driver Manager
   - Supports common database operations like:
     - Establishing connections
     - Executing SQL queries
     - Processing results
     - Managing transactions

   The typical JDBC workflow involves:

   1. Loading the JDBC driver
   2. Establishing a connection
   3. Creating and executing statements
   4. Processing results
   5. Closing connections

   Example of basic JDBC usage:

   ```java
   Connection conn = DriverManager.getConnection(url, username, password);
   Statement stmt = conn.createStatement();
   ResultSet rs = stmt.executeQuery("SELECT * FROM users");
   ```

2. **What are the core components of JDBC?**
   The core components of JDBC include:

   1. **JDBC API (java.sql package)**

      - Provides interfaces and classes for database connectivity
      - Key interfaces: Connection, Statement, PreparedStatement, CallableStatement
      - Handles database operations and result processing

   2. **JDBC Driver Manager**

      - Manages database drivers
      - Establishes connections between Java applications and databases
      - Loads and registers appropriate JDBC drivers

   3. **Connection**

      - Represents a database connection session
      - Enables communication between Java application and database
      - Used to create statements and manage transactions

   4. **Statement Types**

      - **Statement**: For basic SQL queries
      - **PreparedStatement**: For parameterized and precompiled queries
      - **CallableStatement**: For executing stored procedures

   5. **ResultSet**
      - Represents data returned from a database query
      - Allows traversing and processing query results
      - Provides methods to retrieve and manipulate data

   These components work together to provide a comprehensive database connectivity solution in Java.

3. **How do you connect to a database in Java?**
   To connect to a database in Java using JDBC, follow these key steps:

   1. **Load the JDBC Driver**

      ```java
      // For MySQL
      Class.forName("com.mysql.cj.jdbc.Driver");
      // For PostgreSQL
      Class.forName("org.postgresql.Driver");
      ```

   2. **Establish a Database Connection**

      ```java
      // Connection parameters
      String url = "jdbc:mysql://localhost:3306/mydatabase";
      String username = "your_username";
      String password = "your_password";

      // Establish connection
      Connection connection = DriverManager.getConnection(url, username, password);
      ```

   3. **Connection Best Practices**
      - Always use try-with-resources or explicitly close connections
      - Handle potential `SQLException`
      - Use connection pooling for better performance in production

   Example with error handling:

   ```java
   try (Connection conn = DriverManager.getConnection(url, username, password)) {
       // Perform database operations
   } catch (SQLException e) {
       e.printStackTrace();
   }
   ```

   Key connection parameters typically include:

   - JDBC URL (protocol, host, port, database name)
   - Username
   - Password
   - Optional connection properties

4. **What is the difference between Statement, PreparedStatement, and CallableStatement?**

   | Component             | Purpose                            | Key Characteristics                         | Use Case                                       | Performance                      | SQL Injection Risk                 |
   | --------------------- | ---------------------------------- | ------------------------------------------- | ---------------------------------------------- | -------------------------------- | ---------------------------------- |
   | **Statement**         | Executes static SQL queries        | Simple query execution without parameters   | Basic, unchanging SQL statements               | Lowest performance               | High - vulnerable to SQL injection |
   | **PreparedStatement** | Executes parameterized SQL queries | Precompiles SQL, supports parameter binding | Dynamic queries with input parameters          | Better performance (precompiled) | Low - prevents SQL injection       |
   | **CallableStatement** | Executes stored procedures         | Supports calling database stored procedures | Complex database operations, stored procedures | Moderate performance             | Low - supports parameter binding   |

5. **What is the difference between ResultSet and ResultSetMetaData?**
6. **What is the difference between Statement and PreparedStatement?**
7. **What is the difference between Statement and CallableStatement?**
8. **What is the difference between Statement and ResultSet?**
9. **What is the difference between PreparedStatement and CallableStatement?**
10. **What is the difference between PreparedStatement and ResultSet?**
11. **What is the difference between CallableStatement and ResultSet?**

12. **What are the different types of JDBC Driver?**
    There are 4 types of JDBC drivers:

    1. **Type 1: JDBC-ODBC Bridge Driver**

       - Translates JDBC calls to ODBC calls
       - Requires ODBC driver to be installed on client machine
       - Not recommended for production use
       - Deprecated since Java 8

    2. **Type 2: Native-API Driver**

       - Converts JDBC calls into database-specific native calls
       - Requires database native client library
       - Better performance than Type 1
       - Platform dependent

    3. **Type 3: Network Protocol Driver (Middleware Driver)**

       - Uses middleware server to convert JDBC calls to database protocol
       - Platform independent
       - Requires additional network hop
       - Flexible but can have performance overhead

    4. **Type 4: Pure Java Driver (Thin Driver)**
       - Written entirely in Java
       - Converts JDBC calls directly to database-specific protocol
       - Most commonly used driver type
       - Platform independent
       - Best performance
       - Examples: MySQL Connector/J, PostgreSQL JDBC Driver

13. **What do you mean by batch processing in JDBC?**

    Batch processing in JDBC is a technique that allows multiple SQL statements to be grouped and sent to the database server in a single batch, instead of executing them one by one. This approach offers significant performance improvements, especially when dealing with large numbers of similar database operations.

    Key characteristics of batch processing include:

    - **Performance Optimization**: Reduces network roundtrips between the application and database
    - **Efficiency**: Minimizes overhead of individual statement executions
    - **Atomic Operations**: Can commit or rollback entire batch of statements

    Example of batch processing using PreparedStatement:

    ```java
    Connection conn = null;
    PreparedStatement pstmt = null;
    try {
        conn = DriverManager.getConnection(url, user, password);
        pstmt = conn.prepareStatement("INSERT INTO users (name, email) VALUES (?, ?)");

        // Adding multiple statements to batch
        pstmt.setString(1, "John Doe");
        pstmt.setString(2, "john@example.com");
        pstmt.addBatch();

        pstmt.setString(1, "Jane Smith");
        pstmt.setString(2, "jane@example.com");
        pstmt.addBatch();

        // Execute the batch
        int[] updateCounts = pstmt.executeBatch();
    } catch (SQLException e) {
        // Handle exceptions
    }
    ```

    Benefits:

    - Reduces database load
    - Improves application performance
    - Ideal for bulk insert, update, or delete operations

14. **What is Connection Pooling?**

    Connection pooling is a technique used in database programming to efficiently manage and reuse database connections, significantly improving application performance and resource utilization.

    Key aspects of connection pooling include:

    - **Connection Reuse**: Instead of creating a new connection for each database request, a pool of pre-established connections is maintained
    - **Resource Efficiency**: Reduces overhead of creating and closing database connections
    - **Performance Optimization**: Minimizes connection establishment time and system resource consumption

    How Connection Pooling Works:

    - A pool of database connections is created and maintained in advance
    - When an application needs a connection, it requests one from the pool
    - If a connection is available, it's immediately provided
    - After use, the connection is returned to the pool, not closed
    - If no connections are available, the application may wait or create a new connection

    Popular Connection Pool Libraries:

    - Apache DBCP (Database Connection Pool)
    - HikariCP
    - C3P0
    - Tomcat Connection Pool

    Example using HikariCP:

    ```java
    HikariConfig config = new HikariConfig();
    config.setJdbcUrl("jdbc:mysql://localhost:3306/mydb");
    config.setUsername("user");
    config.setPassword("password");
    config.setMaximumPoolSize(10);  // Maximum number of connections in the pool

    HikariDataSource dataSource = new HikariDataSource(config);
    Connection conn = dataSource.getConnection();  // Get connection from pool
    // Use connection
    conn.close();  // Returns connection to the pool, not actually closing it
    ```

    Benefits:

    - Reduces connection creation overhead
    - Improves application scalability
    - Manages database connection resources more effectively
