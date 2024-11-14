
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

