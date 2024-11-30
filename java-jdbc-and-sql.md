# JDBC & SQL

## JDBC

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

15. **What is the difference between execute, executeQuery, executeUpdate?**

    These are three different methods in JDBC Statement interface for executing SQL statements:

    1. **executeQuery()**

       - Used for SELECT statements that return data
       - Returns a ResultSet object containing the query results
       - Example:

       ```java
       String sql = "SELECT * FROM employees";
       ResultSet rs = statement.executeQuery(sql);
       ```

    2. **executeUpdate()**

       - Used for INSERT, UPDATE, DELETE statements and DDL statements
       - Returns an int representing number of rows affected
       - Does not return any data
       - Example:

       ```java
       String sql = "UPDATE employees SET salary = 50000 WHERE id = 1";
       int rowsAffected = statement.executeUpdate(sql);
       ```

    3. **execute()**
       - General purpose method that can execute any SQL statement
       - Returns boolean: true if result is a ResultSet, false if row count/no result
       - Used when statement type is unknown or for multiple results
       - Example:
       ```java
       String sql = "CREATE TABLE employees (id INT, name VARCHAR(100))";
       boolean hasResultSet = statement.execute(sql);
       ```

## SQL

1. **What is SQL and NoSQL?**

   | Aspect         | SQL                                        | NoSQL                                                         |
   | -------------- | ------------------------------------------ | ------------------------------------------------------------- |
   | Structure      | Relational database with predefined schema | Various data models (document, key-value, wide-column, graph) |
   | Schema         | Fixed schema, structured data              | Dynamic/flexible schema                                       |
   | Scaling        | Vertical scaling (scale-up)                | Horizontal scaling (scale-out)                                |
   | ACID           | Strong ACID compliance                     | Usually sacrifices ACID for performance/scalability           |
   | Query Language | Standard SQL                               | Database specific query languages                             |
   | Data Model     | Tables with rows and columns               | Depends on database type (documents, key-value pairs, etc.)   |
   | Use Cases      | Complex queries, transactions              | Large scale, rapid changes, unstructured data                 |
   | Examples       | MySQL, PostgreSQL, Oracle                  | MongoDB, Cassandra, Redis                                     |

2. **What are the advantages of SQL compared to NoSQL?**

   SQL databases offer several key advantages:

   1. **ACID Compliance**

      - Ensures data integrity and consistency
      - Reliable transaction processing
      - Better for financial and critical systems

   2. **Structured Data**

      - Enforced schema ensures data quality
      - Consistent data format
      - Prevents data inconsistencies

   3. **Complex Queries**

      - Powerful JOIN operations
      - Advanced querying capabilities
      - Better for complex reporting

   4. **Standardization**

      - Standard query language (SQL)
      - Easier to learn and use
      - Portable skills across databases

   5. **Mature Ecosystem**

      - Well-established tools and support
      - Rich feature set
      - Proven reliability

   6. **Referential Integrity**
      - Foreign key constraints
      - Data relationships enforced
      - Prevents orphaned records

3. **Why do you consider SQL more suitable for certain cases compared to NoSQL?**

   SQL databases are more suitable in certain scenarios due to:

   1. **Data Relationships**

      - Better for complex relationships between data
      - Enforces referential integrity
      - Efficient JOIN operations for related data

   2. **Transaction Requirements**

      - Strong ACID compliance for critical transactions
      - Ensures data consistency and reliability
      - Essential for financial and banking systems

   3. **Fixed Schema Applications**

      - When data structure is stable and well-defined
      - Enforces data validation and consistency
      - Better for applications with strict data requirements

   4. **Complex Querying**

      - Advanced querying capabilities
      - Aggregations and analytics
      - Complex reporting requirements

   5. **Data Integrity**

      - Built-in data validation
      - Constraints enforcement
      - Prevents invalid or inconsistent data

   6. **Compliance Requirements**
      - Better audit trails
      - Data consistency guarantees
      - Regulatory compliance needs

4. **What disadvantages of SQL and NoSQL could impact your project?**

   SQL Disadvantages:

   1. **Scalability Challenges**

      - Vertical scaling can be expensive
      - Horizontal scaling is complex
      - Performance bottlenecks at high loads

   2. **Schema Rigidity**

      - Schema changes require migrations
      - Less flexible for evolving data
      - Development can be slower

   3. **Cost Considerations**
      - Licensed versions can be expensive
      - Hardware requirements for scaling
      - Operational overhead

   NoSQL Disadvantages:

   1. **Consistency Tradeoffs**

      - Eventually consistent by default
      - Complex consistency patterns
      - Potential data conflicts

   2. **Limited Query Capabilities**

      - Less powerful querying than SQL
      - No standardized query language
      - Complex reporting is harder

   3. **Learning Curve**
      - Different paradigm from SQL
      - Team training requirements
      - Less standardization

5. **What are the primary SQL commands you are familiar with, and how are they used?**

   The main SQL commands (often called DML and DDL) are:

   1. **SELECT**

      - Retrieves data from database tables
      - Supports filtering, sorting, joining
      - Core command for querying data

   2. **INSERT**

      - Adds new records to tables
      - Can insert single or multiple rows
      - Supports different value formats

   3. **UPDATE**

      - Modifies existing records
      - Can update multiple columns
      - Uses WHERE for targeting rows

   4. **DELETE**

      - Removes records from tables
      - Usually with WHERE conditions
      - Can affect multiple rows

   5. **CREATE**

      - Makes new database objects
      - Creates tables, views, indexes
      - Defines schema structure

   6. **ALTER**

      - Modifies existing objects
      - Changes table structure
      - Adds/removes constraints

   7. **DROP**

      - Removes database objects
      - Deletes tables, views, indexes
      - Permanent deletion action

   8. **TRUNCATE**
      - Removes all records from table
      - Faster than DELETE
      - Resets auto-increment

6. **Can you provide examples of using the SELECT, INSERT, UPDATE, and DELETE commands in SQL?**

   Here are examples of the main SQL data manipulation commands:

   1. **SELECT Examples**

   ```sql
   -- Basic SELECT
   SELECT * FROM employees;

   -- SELECT with conditions
   SELECT first_name, last_name, salary
   FROM employees
   WHERE department = 'Sales'
   ORDER BY salary DESC;

   -- SELECT with JOIN
   SELECT e.name, d.department_name
   FROM employees e
   JOIN departments d ON e.dept_id = d.id;
   ```

   2. **INSERT Examples**

   ```sql
   -- Single row INSERT
   INSERT INTO employees (first_name, last_name, salary)
   VALUES ('John', 'Smith', 50000);

   -- Multiple row INSERT
   INSERT INTO employees (first_name, last_name, salary)
   VALUES
       ('Jane', 'Doe', 55000),
       ('Bob', 'Wilson', 45000);
   ```

   3. **UPDATE Examples**

   ```sql
   -- Update single column
   UPDATE employees
   SET salary = 60000
   WHERE employee_id = 101;

   -- Update multiple columns
   UPDATE employees
   SET salary = salary * 1.1,
       last_updated = CURRENT_TIMESTAMP
   WHERE department = 'Sales';
   ```

   4. **DELETE Examples**

   ```sql
   -- Delete specific records
   DELETE FROM employees
   WHERE department = 'Marketing';

   -- Delete with subquery
   DELETE FROM employees
   WHERE salary < (SELECT AVG(salary) FROM employees);

   -- Delete all records
   DELETE FROM employees;
   ```

7. **Utilizing Conditional Operators in SQL Queries with WHERE Clause**

   Conditional operators in SQL's WHERE clause allow precise filtering of query results based on specific conditions:

   1. **Comparison Operators**

   ```sql
   -- Equal to
   SELECT * FROM employees WHERE department = 'Sales';

   -- Not equal to
   SELECT * FROM products WHERE price != 0;

   -- Greater than
   SELECT * FROM orders WHERE total_amount > 1000;

   -- Less than or equal to
   SELECT * FROM employees WHERE salary <= 50000;
   ```

   2. **Logical Operators**

   ```sql
   -- AND: Multiple conditions must be true
   SELECT * FROM employees
   WHERE department = 'Sales' AND salary > 60000;

   -- OR: At least one condition must be true
   SELECT * FROM products
   WHERE category = 'Electronics' OR price < 100;

   -- NOT: Negates a condition
   SELECT * FROM customers
   WHERE NOT country = 'USA';
   ```

   3. **Pattern Matching with LIKE**

   ```sql
   -- Starts with 'John'
   SELECT * FROM users WHERE name LIKE 'John%';

   -- Contains 'smith'
   SELECT * FROM employees WHERE last_name LIKE '%smith%';

   -- Specific pattern (exactly 5 characters)
   SELECT * FROM codes WHERE code LIKE '_____';
   ```

   4. **Range and IN Conditions**

   ```sql
   -- BETWEEN range
   SELECT * FROM orders
   WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';

   -- IN multiple specific values
   SELECT * FROM products
   WHERE category IN ('Electronics', 'Clothing', 'Books');
   ```

   5. **NULL Handling**

   ```sql
   -- Find records with NULL values
   SELECT * FROM employees WHERE manager_id IS NULL;

   -- Find records without NULL values
   SELECT * FROM customers WHERE phone IS NOT NULL;
   ```

   Conditional operators provide powerful ways to filter and retrieve precisely the data you need from database tables.

8. **What are CRUD operations in the context of databases, and how are they utilized?**

   CRUD is an acronym that stands for the four fundamental operations performed on database records:

   1. **Create (INSERT)**

   - Adds new records to a database table
   - Allows insertion of single or multiple rows
   - Example:
     ```sql
     INSERT INTO users (username, email, registration_date)
     VALUES ('johndoe', 'john@example.com', CURRENT_DATE);
     ```

   2. **Read (SELECT)**

   - Retrieves data from database tables
   - Allows filtering, sorting, and joining data
   - Example:
     ```sql
     SELECT * FROM users
     WHERE registration_date > '2023-01-01'
     ORDER BY username;
     ```

   3. **Update (UPDATE)**

   - Modifies existing records in a database table
   - Can update single or multiple columns
   - Example:
     ```sql
     UPDATE users
     SET email = 'newemail@example.com',
         last_login = CURRENT_TIMESTAMP
     WHERE username = 'johndoe';
     ```

   4. **Delete (DELETE)**

   - Removes records from a database table
   - Can delete specific or all records
   - Example:
     ```sql
     DELETE FROM users
     WHERE inactive = TRUE;
     ```

   These operations form the core of data manipulation in relational databases, providing a standard way to interact with and manage data across various database systems.

9. **What is the difference between the GROUP BY and HAVING clauses?**

- **GROUP BY Clause:**

  - Used to group rows that have the same values in specified columns
  - Allows aggregating data within those groups
  - Typically used with aggregate functions like COUNT(), SUM(), AVG()
  - Example:
    ```sql
    SELECT department, AVG(salary) as avg_salary
    FROM employees
    GROUP BY department;
    ```

- **HAVING Clause:**
  - Filters groups created by GROUP BY
  - Applied after grouping and aggregation
  - Similar to WHERE, but works on grouped data
  - Allows filtering based on aggregate function results
  - Example:
    ```sql
    SELECT department, AVG(salary) as avg_salary
    FROM employees
    GROUP BY department
    HAVING AVG(salary) > 50000;
    ```

Key Differences:

- WHERE filters rows before grouping
- HAVING filters groups after grouping and aggregation
- WHERE cannot use aggregate functions, HAVING can
- GROUP BY is required to use HAVING

11. **Can you explain what a SQL join is and how it's used?**

A SQL JOIN is a powerful operation that allows combining rows from two or more tables based on a related column between them. It enables retrieving data from multiple tables in a single query by establishing relationships between tables.

Key Types of JOINs:

1.  **INNER JOIN**

    - Returns only matching rows from both tables
    - Most common type of join
    - Example:
      ```sql
      SELECT employees.name, departments.department_name
      FROM employees
      INNER JOIN departments ON employees.dept_id = departments.id;
      ```

2.  **LEFT JOIN (LEFT OUTER JOIN)**

    - Returns all rows from the left table and matching rows from the right table
    - If no match exists, NULL values are returned for right table columns
    - Example:
      ```sql
      SELECT customers.name, orders.order_date
      FROM customers
      LEFT JOIN orders ON customers.id = orders.customer_id;
      ```

3.  **RIGHT JOIN (RIGHT OUTER JOIN)**

    - Returns all rows from the right table and matching rows from the left table
    - If no match exists, NULL values are returned for left table columns
    - Example:
      ```sql
      SELECT products.name, order_items.quantity
      FROM order_items
      RIGHT JOIN products ON order_items.product_id = products.id;
      ```

4.  **FULL JOIN (FULL OUTER JOIN)**
    - Returns all rows when there is a match in either left or right table
    - Combines results of both LEFT and RIGHT joins
    - Example:
      ```sql
      SELECT students.name, courses.course_name
      FROM students
      FULL JOIN courses ON students.course_id = courses.id;
      ```

Benefits of JOINs:

- Retrieve related data from multiple tables
- Reduce data redundancy
- Create complex queries with interconnected data
- Perform advanced data analysis

12. **When would you use an INNER JOIN versus an OUTER JOIN?**

    - **INNER JOIN**: Use when you only want to retrieve rows that have matching values in both tables

      - Ideal for finding exact relationships between tables
      - Example scenarios:
        - Matching employees to their departments
        - Linking orders to specific customers
        - Connecting products to their sales records

    - **OUTER JOIN**: Use when you want to include all rows from one or both tables, even without matches

      - **LEFT JOIN**: When you want all records from the first (left) table, with optional matching data from the second table

        - Useful for finding customers with no orders
        - Listing all employees, including those without assigned departments

      - **RIGHT JOIN**: When you want all records from the second (right) table, with optional matching data from the first table

        - Showing all products, even those not yet ordered
        - Displaying all courses, including those without enrolled students

      - **FULL JOIN**: When you want to see all records from both tables, regardless of matches
        - Comprehensive view of relationships
        - Identifying both matched and unmatched records across tables

13. **What are aggregate operators in SQL, and how are they used?**

    Aggregate operators are SQL functions that perform calculations on sets of rows, returning a single summarized result. They are commonly used with the GROUP BY clause to perform calculations on grouped data.

    Key aggregate functions include:

    1. **COUNT()**

       - Counts the number of rows or non-null values
       - Examples:

         ```sql
         -- Count total number of employees
         SELECT COUNT(*) FROM employees;

         -- Count employees in each department
         SELECT department, COUNT(*) AS employee_count
         FROM employees
         GROUP BY department;
         ```

    2. **SUM()**

       - Calculates the total sum of numeric values
       - Examples:

         ```sql
         -- Total sales amount
         SELECT SUM(total_amount) FROM orders;

         -- Total sales per product category
         SELECT category, SUM(price) AS total_category_value
         FROM products
         GROUP BY category;
         ```

    3. **AVG()**

       - Calculates the average of numeric values
       - Examples:

         ```sql
         -- Average employee salary
         SELECT AVG(salary) FROM employees;

         -- Average salary by department
         SELECT department, AVG(salary) AS avg_department_salary
         FROM employees
         GROUP BY department;
         ```

    4. **MAX() and MIN()**

       - Find the maximum and minimum values in a column
       - Examples:

         ```sql
         -- Highest and lowest product prices
         SELECT MAX(price) AS highest_price, MIN(price) AS lowest_price
         FROM products;

         -- Highest salary in each department
         SELECT department, MAX(salary) AS max_salary
         FROM employees
         GROUP BY department;
         ```

    5. **HAVING Clause**
       - Filters groups after aggregation
       - Examples:
         ```sql
         -- Departments with average salary over $50,000
         SELECT department, AVG(salary) AS avg_salary
         FROM employees
         GROUP BY department
         HAVING AVG(salary) > 50000;
         ```

    Benefits of Aggregate Operators:

    - Summarize large datasets quickly
    - Perform complex statistical calculations
    - Enable data analysis and reporting
    - Provide insights into grouped data

14. **What are indexes in databases, and what are they used for?**

    - A database index is a data structure that improves the speed of data retrieval operations on a database table
    - Similar to an index in a book, it allows faster lookup of rows without scanning the entire table
    - Key characteristics:
      - Creates a separate structure that references the original table's data
      - Allows quick searching, sorting, and accessing of records
      - Trades additional storage space for faster query performance

    Primary Uses:

    - Accelerate `SELECT`, `WHERE`, and `JOIN` query performance
    - Enforce uniqueness of values
    - Support efficient sorting and filtering

    Types of Indexes in SQL:

    1. Structural Indexes:

       - **Clustered Index**: Determines the physical order of data in a table
       - **Non-Clustered Index**: Creates a separate structure pointing to the original data

    2. Uniqueness Indexes:

       - **Unique Index**: Ensures no duplicate values in a column
       - **Composite Unique Index**: Prevents duplicate combinations across multiple columns

    3. Multi-Column Indexes:

       - **Composite Index**: Created on multiple columns
       - **Covering Index**: Includes all indexed columns in the SELECT statement

    4. Specialized Indexes:

       - **Filtered Index**: Applies a filter condition to reduce the number of rows indexed
       - **Spatial Index**: Optimizes spatial data types
       - **Hash Index**: Uses a hash function for fast lookups
       - **Bitmap Index**: Optimizes for low-cardinality columns

    5. Advanced Indexing Techniques:

       - **Function-Based Index**: Indexes the result of a function applied to a column
       - **Expression Index**: Indexes the result of an expression
       - **Partial Index**: Indexes only a subset of rows in a table
       - **Inverted Index**: Stores the indexed column values in a separate structure
       - **Reverse Index**: Stores the indexed column values in reverse order

    Example:

    ```sql
    -- Creating an index on an employee email column
    CREATE INDEX idx_employee_email
    ON employees (email);

    -- Creating a unique index
    CREATE UNIQUE INDEX idx_product_code
    ON products (product_code);
    ```

    Considerations:

    - Indexes speed up read operations
    - Can slow down write operations (INSERT, UPDATE, DELETE)
    - Should be used selectively on columns frequently used in queries

15. **How do indexes impact query performance?**

    Indexes significantly influence query performance in several key ways:

    1. **Read Performance Improvement**:

       - Dramatically reduces the number of data pages scanned
       - Enables faster data retrieval by creating a sorted, searchable structure
       - Can reduce query execution time from O(n) to O(log n)

    2. **Search Optimization**:

       - Allows database to quickly locate specific rows without full table scan
       - Particularly effective for WHERE, JOIN, and ORDER BY clauses
       - Minimizes disk I/O operations

    3. **Performance Trade-offs**:

       - Accelerates read operations
       - Introduces overhead for write operations (INSERT, UPDATE, DELETE)
       - Each index requires additional storage and maintenance

    4. **Query Execution Strategy**:
       - Database query optimizer uses indexes to determine most efficient query plan
       - Can choose between index scan and table scan based on data distribution
       - More indexes don't always mean better performance

    Example of performance impact:

    ```sql
    -- Without index: Full table scan
    SELECT * FROM large_table WHERE email = 'user@example.com';  -- Slow

    -- With index: Rapid lookup
    CREATE INDEX idx_email ON large_table(email);  -- Faster retrieval
    ```

16. **What are the advantages of using transactions in a database?**

    Transactions provide critical data integrity and reliability mechanisms in database management:

    1. **ACID Properties**:

       - **Atomicity**: Ensures all operations in a transaction complete or none do
       - **Consistency**: Maintains database in a valid state before and after transaction
       - **Isolation**: Prevents interference between concurrent transactions
       - **Durability**: Guarantees committed changes are permanently recorded

    2. **Data Integrity**:

       - Protects against partial updates during complex operations
       - Prevents data corruption in multi-step processes
       - Allows rollback of entire operation if any step fails

    3. **Concurrency Control**:

       - Manages simultaneous database access by multiple users
       - Prevents race conditions and conflicting modifications
       - Ensures predictable and reliable database state

    4. **Error Handling**:
       - Enables automatic rollback of failed operations
       - Maintains database consistency during unexpected errors
       - Provides a mechanism to revert unintended changes

    Example demonstrating transaction usage:

    ```sql
    BEGIN TRANSACTION;

    -- Transfer funds between accounts
    UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
    UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

    COMMIT;  -- Only if both updates succeed
    ```

17. **How can SQL queries be optimized to improve database performance?**

    SQL query optimization is crucial for maintaining efficient database operations:

    1. **Indexing Strategies**:

       - Create indexes on frequently queried columns
       - Use composite indexes for multi-column searches
       - Avoid over-indexing, as it can slow down write operations

    2. **Query Efficiency Techniques**:

       - Use specific column selection instead of SELECT \*
       - Minimize the use of wildcard searches
       - Avoid complex calculations in WHERE clauses
       - Use JOIN instead of subqueries when possible

    3. **Filtering and Limiting Results**:

       - Apply WHERE conditions to reduce result set early
       - Use LIMIT to restrict returned rows
       - Push filtering logic to the database level

    4. **Avoiding Performance Anti-Patterns**:
       - Minimize use of OR conditions
       - Avoid functions on indexed columns in WHERE clauses
       - Use EXISTS instead of IN for large datasets

    Example of query optimization:

    ```sql
    -- Less Efficient Query
    SELECT * FROM orders
    WHERE YEAR(order_date) = 2023;

    -- Optimized Query
    SELECT order_id, customer_id, total_amount
    FROM orders
    WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31'
    LIMIT 1000;
    ```

    5. **Analyzing Query Performance**:
       - Use EXPLAIN to understand query execution plan
       - Monitor slow query logs
       - Regularly update database statistics
       - Consider denormalization for read-heavy applications

    Best practices for maintaining query performance:

    - Regularly review and update indexes
    - Use database profiling tools
    - Cache frequently accessed query results
    - Consider database-specific optimization techniques

18. **Views in SQL: Virtual Tables for Simplified Data Access**

    Views are virtual tables in SQL that:

    - Represent a stored query result set
    - Do not physically store data
    - Provide a layer of abstraction over underlying tables

    Key characteristics and uses of views:

    1. **Data Abstraction**:

       - Hide complex query logic from end-users
       - Simplify complex joins and calculations
       - Provide a consistent interface to data

    2. **Security and Access Control**:

       - Restrict access to specific columns or rows
       - Implement row-level security
       - Limit direct table access for users

    3. **Query Simplification**:
       - Encapsulate complex queries
       - Create reusable query templates
       - Reduce repetitive query writing

    Example of creating and using a view:

    ```sql
    -- Create a view of active customer orders
    CREATE VIEW active_customer_orders AS
    SELECT c.customer_id, c.name, o.order_id, o.total_amount
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    WHERE o.status = 'ACTIVE';

    -- Query the view like a regular table
    SELECT * FROM active_customer_orders
    WHERE total_amount > 1000;
    ```

    Types of Views:

    - Simple Views: Based on single table
    - Complex Views: Involve multiple tables, joins
    - Materialized Views: Physically cached query results
    - Updatable Views: Allow INSERT, UPDATE, DELETE operations

    Considerations:

    - Views can impact performance for complex queries
    - Not all views support data modifications
    - Regularly review and optimize view definitions

19. **What methods can be used to ensure database security?**

    Database security is critical for protecting sensitive information and preventing unauthorized access. Key methods include:

    1. **Authentication and Access Control**:

       - Implement strong user authentication
       - Use role-based access control (RBAC)
       - Create least-privilege user accounts
       - Enforce strong password policies

    2. **Encryption Techniques**:

       - Encrypt data at rest
       - Use SSL/TLS for data in transit
       - Implement column-level encryption
       - Utilize database-specific encryption features

    3. **Network Security**:

       - Configure firewall rules
       - Restrict database network access
       - Use VPNs for remote connections
       - Implement IP whitelisting

    4. **Input Validation and Sanitization**:

       - Prevent SQL injection attacks
       - Use parameterized queries
       - Validate and sanitize user inputs
       - Implement stored procedures

    5. **Auditing and Monitoring**:

       - Enable database audit logs
       - Track user activities
       - Set up real-time monitoring
       - Configure alerts for suspicious activities

    6. **Regular Security Practices**:

       - Keep database software updated
       - Apply security patches promptly
       - Perform regular security assessments
       - Conduct penetration testing

    7. **Data Masking and Anonymization**:
       - Protect sensitive information
       - Use data masking techniques
       - Implement anonymization for non-production environments
       - Limit exposure of personal or confidential data

    Example of implementing role-based access:

    ```sql
    -- Create roles with specific permissions
    CREATE ROLE read_only_user;
    CREATE ROLE admin_user;

    -- Grant specific privileges to roles
    GRANT SELECT ON customers TO read_only_user;
    GRANT SELECT, INSERT, UPDATE, DELETE ON customers TO admin_user;

    -- Create users and assign roles
    CREATE USER john_doe WITH PASSWORD 'secure_password';
    GRANT read_only_user TO john_doe;
    ```

    Comprehensive database security requires a multi-layered approach, combining technical controls, policies, and ongoing vigilance.

20. **What are the Concurrency Control Strategies in Databases**:

    Concurrency control is crucial for maintaining data integrity and performance in multi-user database systems. Key strategies include:

    1. **Locking Mechanisms**:

       - **Shared Locks (Read Locks)**: Multiple transactions can read data simultaneously
       - **Exclusive Locks (Write Locks)**: Prevent other transactions from reading or writing
       - **Two-Phase Locking (2PL)**: Ensures serializability of transactions

    2. **Isolation Levels**:

       - **Read Uncommitted**: Lowest isolation, allows dirty reads
       - **Read Committed**: Prevents dirty reads
       - **Repeatable Read**: Ensures consistent reads within a transaction
       - **Serializable**: Highest isolation level, prevents all concurrency anomalies

    3. **Optimistic Concurrency Control**:

       - Assumes conflicts are rare
       - Allows transactions to proceed without locking
       - Validates conflicts at commit time
       - Rolls back if conflicts detected

    4. **Pessimistic Concurrency Control**:
       - Locks resources before transaction begins
       - Prevents potential conflicts proactively
       - Reduces potential for concurrent updates

    Example of transaction isolation in SQL:

    ```sql
    -- Set transaction isolation level
    SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
    BEGIN TRANSACTION;
    -- Perform database operations
    COMMIT;
    ```

    Effective concurrency control balances data consistency, performance, and system responsiveness.

21. **What are Stored Procedures and how can they optimize database operations?**

    Stored procedures are powerful database objects that can significantly enhance performance and efficiency:

    1. **Performance Optimization Techniques**:

       - Reduce network traffic by executing multiple SQL statements in a single call
       - Precompile execution plans for faster query processing
       - Minimize round trips between application and database server

    2. **Example of Performance-Optimized Stored Procedure**:

       ```sql
       CREATE PROCEDURE GetCustomerOrderSummary(IN customer_id INT)
       BEGIN
           -- Combine multiple queries into a single procedure
           SELECT
               c.customer_name,
               COUNT(o.order_id) AS total_orders,
               SUM(o.order_total) AS total_spend
           FROM
               customers c
           LEFT JOIN
               orders o ON c.customer_id = o.customer_id
           WHERE
               c.customer_id = customer_id
           GROUP BY
               c.customer_name;
       END;
       ```

    3. **Key Optimization Strategies**:

       - Use parameterized queries to prevent SQL injection
       - Implement complex logic directly in the database
       - Cache frequently used data within the procedure
       - Minimize data transfer by selecting only necessary columns

    4. **Caching and Reusability**:

       - Stored procedures are compiled and cached by the database engine
       - Subsequent executions use the cached execution plan
       - Reduces parsing and optimization overhead

    5. **Transaction Management**:
       - Encapsulate multiple database operations in a single atomic transaction
       - Ensure data consistency and integrity
       - Rollback entire operation if any step fails

    Stored procedures provide a robust mechanism for improving database performance, security, and maintainability.

22. **How do you prevent SQL Injection Attacks? List comprehensive security strategies**

    Preventing SQL injection attacks is crucial for database security. Here are comprehensive strategies:

    1. **Use Prepared Statements**

       - Parameterized queries separate SQL logic from data
       - Automatically escape and sanitize input

       ```java
         PreparedStatement stmt = connection.prepareStatement("SELECT * FROM users WHERE username = ?");
         stmt.setString(1, username);
         ResultSet rs = stmt.executeQuery();
       ```

    2. **Input Validation**

       - Validate and sanitize all user inputs

         - Use whitelisting for allowed characters
         - Implement strict input type and length checks

         ```java
         if (!username.matches("[A-Za-z0-9_]+")) {
            throw new IllegalArgumentException("Invalid username format");
         }
         ```

    3. **Least Privilege Principle**

       - Use database accounts with minimal required permissions
       - Create specific roles with restricted access rights
       - Avoid using admin or root-level database credentials

    4. **Stored Procedures with Parameter Binding**

       - Use parameterized stored procedures
       - Provides an additional layer of protection

       ```java
       CallableStatement stmt = connection.prepareCall("{call getUserDetails(?)}");
       stmt.setInt(1, userId);
       ResultSet rs = stmt.executeQuery();
       ```

    5. **ORM Frameworks**

       - Utilize Object-Relational Mapping (ORM) tools
       - Leverage built-in protection mechanisms

       ```java
       // Example with JPA
       Query query = entityManager.createQuery("FROM User WHERE username = :username");
       query.setParameter("username", username);
       ```

    6. **Additional Defensive Techniques**

       - Escape special characters
       - Use stored procedures with strict parameter typing
       - Implement web application firewalls (WAF)
       - Regular security audits and penetration testing
       - Avoid exposing detailed database error messages
       - Log errors securely for debugging

       Key Principle: Never trust user input and always use parameterized queries or prepared statements.

23. **What are the Database Backup and Recovery Strategies**:

    - **Regular Backup Scheduling**:

      - Implement automated full and incremental backups
      - Use built-in database backup tools (e.g., mysqldump, pg_dump)
      - Schedule backups during low-traffic periods

    - **Backup Types**:

      - **Full Backups**: Complete database snapshot
      - **Incremental Backups**: Only changes since last backup
      - **Differential Backups**: Changes since last full backup

    - **Backup Storage**:

      - Multiple storage locations
      - Off-site and cloud storage
      - Encrypted backup repositories
      - Retention policies (e.g., 30-day, 90-day archives)

    - **Recovery Strategies**:

      - Point-in-Time Recovery (PITR)
      - Transaction log preservation
      - Standby/Replica databases
      - Failover and high availability configurations

    - **Best Practices**:
      - Test backup restoration regularly
      - Validate backup integrity
      - Automate monitoring and alerting
      - Document recovery procedures
      - Maintain comprehensive disaster recovery plan

24. **Database Performance Monitoring and Tuning Tools**:

    - **Built-in Database Monitoring Tools**:

      - MySQL Performance Schema
      - PostgreSQL pg_stat_statements
      - Oracle Enterprise Manager
      - SQL Server Dynamic Management Views (DMVs)

    - **Open-Source Monitoring Tools**:

      - Prometheus
      - Grafana
      - Zabbix
      - Nagios

    - **Commercial Performance Monitoring Solutions**:

      - New Relic Database Monitoring
      - SolarWinds Database Performance Analyzer
      - Datadog Database Monitoring
      - AppDynamics

    - **Key Performance Metrics to Monitor**:

      - Query execution time
      - CPU and memory usage
      - I/O operations
      - Connection pool statistics
      - Cache hit rates
      - Slow query logs

    - **Performance Tuning Techniques**:
      - Index optimization
      - Query plan analysis
      - Connection pooling
      - Caching strategies
      - Hardware resource allocation
      - Query rewriting and optimization

25. **What is a primary key in a database table, and why is it important?**

    A primary key is a unique identifier for each record in a database table that ensures data integrity and establishes a way to uniquely identify each row. Key characteristics and importance include:

    1. **Unique Identification**

       - Guarantees each record can be uniquely identified
       - No two rows can have the same primary key value
       - Prevents duplicate entries in the table

    2. **Data Integrity**

       - Enforces data consistency
       - Ensures each record is distinctly identifiable
       - Prevents null or duplicate values

    3. **Relationship Establishment**

       - Enables creation of relationships between tables
       - Used as a reference for foreign key constraints
       - Supports complex database relationships and joins

    4. **Indexing and Performance**

       - Automatically creates a clustered index
       - Improves query performance
       - Allows faster data retrieval and searching

    5. **Examples of Primary Keys**

       ```sql
       -- Numeric auto-increment primary key
       CREATE TABLE users (
           user_id INT PRIMARY KEY AUTO_INCREMENT,
           username VARCHAR(50),
           email VARCHAR(100)
       );

       -- Composite primary key
       CREATE TABLE order_items (
           order_id INT,
           product_id INT,
           quantity INT,
           PRIMARY KEY (order_id, product_id)
       );
       ```

    6. **Best Practices**
       - Choose immutable values
       - Keep primary keys as small as possible
       - Use natural or surrogate keys appropriately
       - Avoid using sensitive or changing data as primary keys

26. **What types of relationships exist between tables in databases?**

    Database table relationships define how data is connected between different tables. The primary types of relationships are:

    1. **One-to-One (1:1) Relationship**

    - Each record in one table is related to exactly one record in another table
    - Least common relationship type
    - Example: A person and their passport details

    ```sql
    CREATE TABLE persons (
        person_id INT PRIMARY KEY,
        name VARCHAR(100)
    );

    CREATE TABLE passports (
        passport_id INT PRIMARY KEY,
        person_id INT UNIQUE,
        passport_number VARCHAR(20),
        FOREIGN KEY (person_id) REFERENCES persons(person_id)
    );
    ```

    2. **One-to-Many (1:N) Relationship**

    - A record in one table can be related to multiple records in another table
    - Most common type of relationship
    - Example: A department with multiple employees

    ```sql
    CREATE TABLE departments (
        dept_id INT PRIMARY KEY,
        dept_name VARCHAR(50)
    );

    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        name VARCHAR(100),
        dept_id INT,
        FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
    );
    ```

    3. **Many-to-Many (M:N) Relationship**

    - Multiple records in one table can be related to multiple records in another table
    - Requires a junction/bridge table to resolve the relationship
    - Example: Students enrolled in multiple courses

    ```sql
    CREATE TABLE students (
        student_id INT PRIMARY KEY,
        student_name VARCHAR(100)
    );

    CREATE TABLE courses (
        course_id INT PRIMARY KEY,
        course_name VARCHAR(100)
    );

    CREATE TABLE enrollments (
        student_id INT,
        course_id INT,
        enrollment_date DATE,
        PRIMARY KEY (student_id, course_id),
        FOREIGN KEY (student_id) REFERENCES students(student_id),
        FOREIGN KEY (course_id) REFERENCES courses(course_id)
    );
    ```

    4. **Self-Referencing Relationship**

    - A table has a relationship with itself
    - Useful for hierarchical or recursive data structures
    - Example: Employee reporting structure

    ```sql
    CREATE TABLE employees (
        employee_id INT PRIMARY KEY,
        name VARCHAR(100),
        manager_id INT,
        FOREIGN KEY (manager_id) REFERENCES employees(employee_id)
    );
    ```

    These relationships are crucial for:

    - Maintaining data integrity
    - Preventing data redundancy
    - Enabling complex queries and data analysis
    - Establishing logical connections between different entities in a database

27. **What Data Types are Used in SQL, and How Do They Differ from Each Other?**

    SQL provides several fundamental data types to store different kinds of information:

    1. **Numeric Types**

    - `INT` / `INTEGER`: Whole numbers (-2,147,483,648 to 2,147,483,647)
    - `SMALLINT`: Smaller range whole numbers
    - `BIGINT`: Larger range whole numbers
    - `DECIMAL` / `NUMERIC`: Exact precision for financial calculations
    - `FLOAT` / `REAL`: Approximate decimal numbers with floating point

    2. **String Types**

    - `VARCHAR(n)`: Variable-length character strings with maximum length
    - `CHAR(n)`: Fixed-length character strings
    - `TEXT`: Large text storage without a predefined length

    3. **Date and Time Types**

    - `DATE`: Stores date (YYYY-MM-DD)
    - `TIME`: Stores time of day
    - `DATETIME`: Stores both date and time
    - `TIMESTAMP`: Date and time with timezone information

    4. **Boolean Type**

    - `BOOLEAN`: Stores true/false values

    5. **Binary Types**

    - `BLOB`: Binary Large Object for storing files or images

    Key Differences:

    - Numeric types differ in precision, storage size, and decimal handling
    - String types vary in length constraints and storage efficiency
    - Date types provide different levels of temporal precision
    - Choice depends on data requirements, storage efficiency, and query performance

28. **How do you define and use a primary key in a table?**

    A primary key is a column or combination of columns that uniquely identifies each row in a table. Here's how to define and use primary keys:

    1. **Single Column Primary Key**

    ```sql
    CREATE TABLE users (
        user_id INT PRIMARY KEY,
        username VARCHAR(50),
        email VARCHAR(100)
    );
    ```

    2. **Composite Primary Key**

    ```sql
    CREATE TABLE order_items (
        order_id INT,
        product_id INT,
        quantity INT,
        PRIMARY KEY (order_id, product_id)
    );
    ```

    3. **Using CONSTRAINT Keyword**

    ```sql
    CREATE TABLE employees (
        emp_id INT,
        name VARCHAR(100),
        CONSTRAINT pk_employee PRIMARY KEY (emp_id)
    );
    ```

    Key characteristics:

    - Must contain unique values
    - Cannot contain NULL values
    - Should be immutable
    - Can be referenced by foreign keys
    - Typically auto-incrementing for single-column keys

    Best practices:

    - Choose meaningful primary keys
    - Use simple and stable values
    - Consider using surrogate keys (auto-incrementing IDs)
    - Avoid using natural keys that might change

29. **How do you create a relationship between two tables in a database?**

    Relationships between tables are primarily created using foreign keys. Here's how to establish different types of relationships:

    1. **One-to-Many Relationship**

    ```sql
    CREATE TABLE departments (
        dept_id INT PRIMARY KEY,
        dept_name VARCHAR(50)
    );

    CREATE TABLE employees (
        emp_id INT PRIMARY KEY,
        name VARCHAR(100),
        dept_id INT,
        FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
    );
    ```

    2. **Many-to-Many Relationship**

    ```sql
    CREATE TABLE students (
        student_id INT PRIMARY KEY,
        name VARCHAR(100)
    );

    CREATE TABLE courses (
        course_id INT PRIMARY KEY,
        course_name VARCHAR(100)
    );

    CREATE TABLE enrollments (
        student_id INT,
        course_id INT,
        enrollment_date DATE,
        PRIMARY KEY (student_id, course_id),
        FOREIGN KEY (student_id) REFERENCES students(student_id),
        FOREIGN KEY (course_id) REFERENCES courses(course_id)
    );
    ```

    3. **One-to-One Relationship**

    ```sql
    CREATE TABLE users (
        user_id INT PRIMARY KEY,
        username VARCHAR(50)
    );

    CREATE TABLE user_profiles (
        user_id INT PRIMARY KEY,
        address VARCHAR(200),
        phone VARCHAR(20),
        FOREIGN KEY (user_id) REFERENCES users(user_id)
    );
    ```

    Key considerations:

    - Foreign keys must reference unique keys (typically primary keys)
    - Consider ON DELETE and ON UPDATE actions
    - Maintain referential integrity
    - Index foreign key columns for better performance
    - Use appropriate relationship type for your data model

30. **What is the difference between WHERE and HAVING clause?**

    The `WHERE` and `HAVING` clauses are both used for filtering in SQL, but they have key differences:

    1.  **WHERE Clause**:

        - Filters individual rows before any grouping occurs
        - Used with non-aggregated columns
        - Applied to individual records in the original table
        - Comes before the `GROUP BY` clause
        - Example:

        ```sql
        SELECT department, COUNT(*)
        FROM employees
        WHERE salary > 50000
        GROUP BY department
        ```

    2.  **HAVING Clause**:

        - Filters groups after grouping and aggregation
        - Used with aggregated columns (COUNT, SUM, AVG, etc.)
        - Applied to grouped results
        - Comes after the `GROUP BY` clause
        - Example:

        ```sql
        SELECT department, COUNT(*) as emp_count
        FROM employees
        GROUP BY department
        HAVING emp_count > 5
        ```

    **Key Differences**:

    - `WHERE` filters rows before grouping
    - `HAVING` filters groups after grouping
    - `WHERE` works with individual column values
    - `HAVING` works with aggregate function results

31. **What are transactions? What is ACID?**

    A transaction is a sequence of database operations that are treated as a single, atomic unit of work. Transactions ensure data integrity and reliability in database systems by following the ACID properties:

    1. **Atomicity (A)**:

       - Ensures that a transaction is treated as a single, indivisible unit of work
       - Either all operations in a transaction are completed successfully, or none are
       - If any part of the transaction fails, the entire transaction is rolled back
       - Prevents partial updates that could leave the database in an inconsistent state

    2. **Consistency (C)**:

       - Guarantees that a transaction brings the database from one valid state to another
       - All data integrity constraints must be satisfied before and after the transaction
       - Ensures that the database remains in a consistent state throughout the transaction

    3. **Isolation (I)**:

       - Ensures that concurrent transactions do not interfere with each other
       - Transactions are executed as if they are the only transaction running
       - Prevents issues like dirty reads, non-repeatable reads, and phantom reads
       - Different isolation levels provide varying degrees of protection

    4. **Durability (D)**:
       - Guarantees that once a transaction is committed, its changes are permanent
       - Committed data is saved to persistent storage
       - Survives system crashes, power failures, or other unexpected events
       - Ensures that completed transactions are not lost

    **Example of a Transaction in SQL**:

    ```sql
    BEGIN TRANSACTION;

    UPDATE accounts SET balance = balance - 100 WHERE account_id = 1;
    UPDATE accounts SET balance = balance + 100 WHERE account_id = 2;

    COMMIT;
    ```

    In this example, both updates must succeed, or neither will be applied, maintaining data integrity during a fund transfer.

32. **Difference between truncate, delete, and drop clause in SQL?**

    | Operation    | DELETE                        | TRUNCATE                     | DROP                           |
    | ------------ | ----------------------------- | ---------------------------- | ------------------------------ |
    | Purpose      | Removes specific rows         | Removes all rows             | Removes entire table structure |
    | Rollback     | Can be rolled back            | Cannot be rolled back        | Cannot be rolled back          |
    | Performance  | Slower for large datasets     | Faster, minimal logging      | Fastest, removes entire table  |
    | Triggers     | Activates row-level triggers  | Does not activate triggers   | Removes all triggers           |
    | Space        | Retains table structure       | Resets table, reclaims space | Removes table completely       |
    | Where Clause | Supports conditional deletion | No conditional deletion      | No deletion, removes table     |
    | Logging      | Logs each row deletion        | Minimal logging              | Minimal logging                |
    | Constraints  | Preserves table constraints   | Preserves table constraints  | Removes all constraints        |

33. **What are window functions? How do they work?**

    Window functions perform calculations across a set of table rows related to the current row. They operate on a "window" (set of rows) defined by the OVER clause.

    **Key characteristics:**

    - Process rows that are related to the current row
    - Don't collapse results into a single row like regular aggregates
    - Keep all rows in the result set
    - Allow calculations using values from multiple rows simultaneously

    **Common window functions:**

    - ROW_NUMBER(): Assigns unique row numbers
    - RANK(): Assigns ranks with gaps for ties
    - DENSE_RANK(): Assigns ranks without gaps
    - LAG/LEAD(): Access previous/next row values
    - FIRST_VALUE/LAST_VALUE: Get first/last value in window

    **Example:**

    ```sql
    SELECT
        employee_name,
        department,
        salary,
        AVG(salary) OVER (PARTITION BY department) as dept_avg,
        RANK() OVER (ORDER BY salary DESC) as salary_rank
    FROM employees;
    ```

    This query shows each employee's salary alongside their department's average salary and their overall salary rank.

## Object Relational Mapping (ORM) (Hibernate & JPA)

1. **What is ORM (Object-Relational Mapping)?**

   ORM is a programming technique that converts data between incompatible type systems in object-oriented programming languages and relational databases. Key aspects include:

   1. **Core Functionality**:

      - Maps database tables to classes
      - Converts database records to objects
      - Handles data type conversions
      - Manages relationships between objects

   2. **Benefits**:

      - Reduces boilerplate database code
      - Provides database independence
      - Simplifies data access logic
      - Enables object-oriented design

   3. **Popular Java ORM Frameworks**:
      - Hibernate
      - JPA (Java Persistence API)
      - EclipseLink
      - MyBatis

   Example using JPA annotations:

   ```java
   @Entity
   @Table(name = "users")
   public class User {
       @Id
       @GeneratedValue(strategy = GenerationType.AUTO)
       private Long id;

       @Column(name = "username")
       private String username;

       @OneToMany(mappedBy = "user")
       private List<Order> orders;
   }
   ```

   4. **Key Features**:
      - Automatic CRUD operations
      - Relationship management
      - Caching capabilities
      - Transaction management
      - Query language support (e.g., JPQL, HQL)

2. **What is Hibernate?**

   Hibernate is the most popular Java ORM framework that implements JPA specifications. Key aspects include:

   1. **Core Features**:

      - Full JPA implementation
      - Powerful query languages (HQL/JPQL)
      - Automatic DDL generation
      - Connection pooling integration
      - First and second-level caching

   2. **Key Components**:
      - SessionFactory (thread-safe factory for Session objects)
      - Session (represents a database connection)
      - Transaction (unit of work with the database)
      - Query (for executing database queries)
   3. **Basic Example**:

   ```java
   @Entity
   public class Employee {
       @Id
       @GeneratedValue
       private Long id;

       private String name;
       private Double salary;

       // Getters and setters
   }

   // Using Hibernate Session
   Session session = sessionFactory.openSession();
   Transaction tx = session.beginTransaction();

   Employee emp = new Employee();
   emp.setName("John");
   emp.setSalary(50000.0);

   session.save(emp);
   tx.commit();
   session.close();
   ```

   4. **Advantages**:
      - Reduces development time
      - Database independence
      - Automatic versioning and timestamp
      - Complex associations handling
      - Lazy and eager loading strategies

3. **What is JPA?**
   JPA (Java Persistence API) is a Java specification that provides a standardized approach for ORM (Object-Relational Mapping) and managing relational data in Java applications. Key aspects include:

   1. **Core Concepts**:

      - Entity management
      - Object-relational mapping through annotations
      - Standard query language (JPQL)
      - Persistence context management
      - Transaction handling

   2. **Key Components**:
      - EntityManagerFactory: Creates EntityManager instances
      - EntityManager: Manages persistence operations
      - Entity: Java objects mapped to database tables
      - EntityTransaction: Manages transactions
   3. **Basic Example**:

      ```java
      @Entity
      public class User {
         @Id
         @GeneratedValue
         private Long id;
         private String name;

         // Getters and setters
      }

      EntityManager em = emf.createEntityManager();
      em.getTransaction().begin();

      User user = new User();
      user.setName("Alice");
      em.persist(user);

      em.getTransaction().commit();
      em.close();
      ```

   4. **Benefits**:
      - Standard Java ORM specification
      - Vendor independence
      - Simplified database operations
      - Reduced boilerplate code
      - Automatic dirty checking

4. **What is the difference between Hibernate and JPA?**

   | Aspect             | JPA                                         | Hibernate                                |
   | ------------------ | ------------------------------------------- | ---------------------------------------- |
   | Type               | Specification/Standard                      | Implementation                           |
   | Scope              | Defines standard interfaces and annotations | Provides complete ORM solution           |
   | Portability        | Vendor independent                          | Specific to Hibernate implementation     |
   | Features           | Core persistence features only              | Additional features beyond JPA spec      |
   | Configuration      | Standard JPA annotations                    | Hibernate-specific annotations available |
   | Query Language     | JPQL only                                   | Supports JPQL and HQL                    |
   | Caching            | Basic caching support                       | Advanced caching mechanisms              |
   | Performance Tuning | Limited options                             | Extensive optimization options           |
   | Learning Curve     | Simpler standard API                        | More complex with additional features    |
   | Vendor Lock-in     | No vendor lock-in                           | Some Hibernate-specific dependencies     |

5. **What is the difference between @Entity and @Table annotations?**
6. **When is it better to use plain SQL instead of ORM?**
   Plain SQL may be preferable over ORM in several scenarios:

   1. **Complex Queries**:

      - When dealing with complex joins, subqueries, or analytical functions
      - For queries requiring specific database optimizations
      - When fine-tuning query performance is critical

   2. **Bulk Operations**:

      - Mass updates or deletes
      - Batch processing large datasets
      - ETL (Extract, Transform, Load) operations

   3. **Performance-Critical Applications**:

      - When you need complete control over query execution
      - To avoid ORM overhead in high-performance scenarios
      - For real-time applications with strict latency requirements

   4. **Database-Specific Features**:

      - When using specialized database features not supported by ORM
      - For stored procedures and functions
      - When working with legacy database schemas

   5. **Simple Applications**:
      - Small applications with few entities
      - When ORM configuration overhead outweighs benefits
      - Projects with simple CRUD operations only

7. **What is second level cache? How does it work?**

   Second-level cache is a global cache in Hibernate that stores entity data across multiple sessions and transactions. Unlike first-level cache which is session-scoped, second-level cache is SessionFactory-scoped and shared by all sessions.

   Key aspects of second-level cache:

   1. **Purpose and Benefits**:

      - Reduces database hits by caching data globally
      - Improves application performance
      - Shares cached data across sessions
      - Helps with read-heavy applications

   2. **How it Works**:

      - When an entity is requested, Hibernate first checks the first-level cache
      - If not found, it checks the second-level cache
      - If still not found, database query is executed
      - Retrieved data is stored in both cache levels
      - Subsequent requests from any session can use cached data

   3. **Implementation**:

      - Uses cache providers like EHCache, Redis, Infinispan
      - Configured at SessionFactory level
      - Can be enabled/disabled per entity
      - Supports different concurrency strategies
      - Handles cache invalidation and updates

   4. **Best Practices**:
      - Cache read-mostly data
      - Configure appropriate time-to-live
      - Choose suitable cache provider
      - Monitor cache hit/miss ratios
      - Consider memory constraints

8. **What is the difference between save() and persist() in Hibernate?**

   The save() and persist() methods in Hibernate are used to persist entities but have some key differences:

   1. **Return Value**:

      - save() returns the generated identifier (Serializable object)
      - persist() returns void

   2. **Identifier Generation**:

      - save() generates and assigns ID immediately
      - persist() delays ID generation until flush/commit

   3. **Persistence Context**:

      - save() doesn't guarantee entity is in persistence context
      - persist() ensures entity enters persistence context

   4. **Usage Outside Transaction**:

      - save() can be used outside transaction
      - persist() requires active transaction

   5. **JPA Compatibility**:
      - save() is Hibernate-specific
      - persist() is JPA standard method

   Best Practice: Use persist() when working with JPA and for better transactional behavior. Use save() only in Hibernate-specific applications where immediate ID generation is needed.

9. **What is the difference between Hibernate and MyBatis?**

   | Aspect          | Hibernate                             | MyBatis                                |
   | --------------- | ------------------------------------- | -------------------------------------- |
   | Type            | Full ORM framework                    | SQL mapping framework                  |
   | Learning Curve  | Steeper learning curve                | Easier to learn                        |
   | SQL Control     | Generates SQL automatically           | Manual SQL writing required            |
   | Performance     | May have overhead for complex queries | Better performance for complex queries |
   | Database Schema | Can generate/update schema            | Manual schema management               |
   | Query Writing   | Uses HQL/JPQL, criteria queries       | Uses XML/annotations for SQL mapping   |
   | Caching         | Sophisticated multi-level caching     | Basic caching support                  |
   | Object Mapping  | Automatic object-relational mapping   | Manual mapping configuration           |
   | Flexibility     | Less flexible for complex queries     | More flexible SQL control              |
   | JPA Compliance  | Fully JPA compliant                   | Not JPA compliant                      |

10. **A table name user_addesses contains columns id, user_id, address, is_primary(0/1) Every user must have only one primary address. There is lots of data dumped in this table now some users do not have a primary address, write a query to find these records?**

    Table Schema:

    ```sql
    user_addresses (
        id INT,
        user_id INT,
        address VARCHAR,
        is_primary BIT(1)  -- 0/1 flag
    )
    ```

    Query to find users without any primary address:

    ```sql
    SELECT DISTINCT ua.user_id
    FROM user_addresses ua
    WHERE NOT EXISTS (
        SELECT 1
        FROM user_addresses ua2
        WHERE ua2.user_id = ua.user_id
        AND ua2.is_primary = 1
    );
    ```

    This query:

    - Uses EXISTS to check if a user has any primary address
    - Returns distinct user_ids that have no matching primary address record
    - Works efficiently even with large datasets

    Or using a more efficient approach:

      ```sql
      SELECT user_id
      FROM user_addresses
      GROUP BY user_id
      HAVING SUM(CASE WHEN is_primary = 1 THEN 1 ELSE 0 END) = 0;
      ```

    This query:

      - Groups by user_id
      - Uses SUM and CASE to count primary addresses
      - Filters users with no primary addresses
      - More efficient for large datasets
