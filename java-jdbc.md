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

2. **What is the difference between Connection, Statement, PreparedStatement, and CallableStatement?**
3. **What is the difference between ResultSet and ResultSetMetaData?**
4. **What is the difference between Statement and PreparedStatement?**
5. **What is the difference between Statement and CallableStatement?**
6. **What is the difference between Statement and ResultSet?**
7. **What is the difference between PreparedStatement and CallableStatement?**
8. **What is the difference between PreparedStatement and ResultSet?**
9. **What is the difference between CallableStatement and ResultSet?**

10. **What are the different types of JDBC Driver?**
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
