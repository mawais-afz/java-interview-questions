# Java JSP & Servlet

## JSP

1. **What is a JSP page?**

   A JSP (JavaServer Pages) page is a text document that contains two types of text:

   - Static data (like HTML, XML, or other text formats)
   - Dynamic content (JSP elements that can generate content dynamically)

   Key characteristics:

   - Extension is typically .jsp
   - Gets converted to a servlet behind the scenes
   - Allows embedding Java code within HTML
   - Provides built-in objects like request, response, session
   - Supports custom tag libraries
   - Part of Java EE specification
   - Primarily used for presentation layer in web applications

1. **Explain the lifecycle of JSP**

   1. **Translation Phase:**

      - JSP page is translated into servlet source code
      - Happens when JSP is first accessed or when modified
      - Container checks if JSP needs recompilation

   2. **Compilation Phase:**

      - Generated servlet source code is compiled into class file
      - Results in executable servlet class
      - Only occurs after translation if needed

   3. **Loading Phase:**

      - Compiled servlet class is loaded into memory
      - Class loader loads any dependent classes

   4. **Instantiation Phase:**

      - Single instance of servlet class is created
      - Happens only once in servlet's lifecycle

   5. **Initialization Phase:**

      - `jspInit()` method is called
      - One-time initialization of resources
      - Happens after instantiation

   6. **Request Processing Phase:**

      - `_jspService()` method handles client requests
      - Executes for each client request
      - Contains the actual JSP page logic

   7. **Destruction Phase:**
      - `jspDestroy()` method is called
      - Cleanup of resources
      - Happens when container shuts down or unloads JSP

1. **Brief the life cycle of an applet:**

   1. **Initialization (`init()`):**

      - Called when applet is first loaded
      - Initializes variables and resources
      - Runs only once in applet's lifetime

   2. **Starting (`start()`):**
      - Called after initialization
      - Also called when applet is revisited in browser
      - Starts any threads or animations
   3. **Running (`paint()`):**

      - Called to draw/render the applet
      - Can be called multiple times
      - Handles display updates and user interaction

   4. **Stopping (`stop()`):**

      - Called when user leaves applet's page
      - Suspends threads and animations
      - Can be restarted with `start()`

   5. **Destruction (`destroy()`):**
      - Final method called before applet is unloaded
      - Cleanup of resources
      - Happens when browser closes or navigates away

1. **Explain the various directives in JSP:**

   1. **Page Directive (`<%@ page ... %>`)**:

      - Defines page-specific attributes
      - Controls page properties like language, content type, error page, etc.
      - Example: `<%@ page language="java" contentType="text/html; charset=UTF-8" %>`

   2. **Include Directive (`<%@ include ... %>`)**:

      - Includes contents of another file at compilation time
      - Static inclusion - content becomes part of current JSP
      - Example: `<%@ include file="header.jsp" %>`

   3. **Taglib Directive (`<%@ taglib ... %>`)**:

      - Declares a tag library for use in the JSP
      - Enables use of custom tags
      - Example: `<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>`

   4. **Attribute Directive (`<%@ attribute ... %>`)**:

      - Defines an attribute for tag files
      - Used in custom tag development
      - Example: `<%@ attribute name="username" required="true" %>`

   5. **Variable Directive (`<%@ variable ... %>`)**:
      - Declares scripting variables
      - Used in tag files
      - Example: `<%@ variable name-given="user" variable-class="com.example.User" %>`

1. **Explain the lifecycle of Servlet:**

   1. **Loading and Instantiation:**

      - Servlet class is loaded by container
      - Instance is created using default constructor
      - Happens only once when first request arrives or at startup

   2. **Initialization:**

      - `init()` method is called by container
      - One-time initialization of resources
      - Called only once after instantiation
      - Parameters from web.xml are available

   3. **Request Handling:**

      - `service()` method handles client requests
      - Called for each client request
      - Dispatches to appropriate HTTP method (doGet, doPost etc.)
      - Multiple threads can execute concurrently

   4. **Destruction:**
      - `destroy()` method called before servlet unloaded
      - Clean up resources (close DB connections etc.)
      - Called only once at end of servlet lifecycle
      - Container handles garbage collection

1. **Different Authentication Methods in Java Servlets:**

   1. **Form-Based Authentication:**

      - Uses HTML forms to collect credentials
      - Credentials sent via POST request
      - Custom login/error pages can be configured
      - Most flexible and commonly used method

   2. **Basic Authentication:**

      - Browser displays built-in login dialog
      - Credentials sent in Base64 encoding
      - Simple but less secure as credentials are easily decoded
      - Supported by all browsers

   3. **Digest Authentication:**

      - Similar to Basic but more secure
      - Credentials are hashed before transmission
      - Prevents man-in-the-middle attacks
      - Not widely supported by modern browsers

   4. **Client Certificate Authentication:**

      - Uses SSL/TLS certificates for authentication
      - Most secure method
      - Requires proper SSL setup
      - Complex to implement and manage

   5. **Custom Authentication:**

   - Implement custom authentication logic
   - Complete control over authentication process
   - Can integrate with any authentication system
   - Requires careful security consideration

1. **What are the different tags provided in JSTL?**

   JSTL (JavaServer Pages Standard Tag Library) provides several core tag libraries to simplify JSP development:

   1. **Core Tags (c prefix)**

      - `<c:out>`: Displays content
      - `<c:set>`: Sets variable values
      - `<c:remove>`: Removes variables
      - `<c:if>`: Conditional processing
      - `<c:choose>`: Multi-conditional processing
      - `<c:when>`: Condition within choose
      - `<c:otherwise>`: Default condition
      - `<c:forEach>`: Iteration
      - `<c:forTokens>`: Token iteration
      - `<c:import>`: Includes content from other sources
      - `<c:url>`: URL generation with context path

   2. **Formatting Tags (fmt prefix)**

      - `<fmt:formatNumber>`: Number formatting
      - `<fmt:formatDate>`: Date formatting
      - `<fmt:parseNumber>`: Number parsing
      - `<fmt:parseDate>`: Date parsing
      - `<fmt:setLocale>`: Sets locale
      - `<fmt:timeZone>`: Specifies time zone
      - `<fmt:setBundle>`: Resource bundle configuration

   3. **SQL Tags (sql prefix)**

      - `<sql:setDataSource>`: Configures database connection
      - `<sql:query>`: Executes SQL SELECT queries
      - `<sql:update>`: Executes SQL update queries
      - `<sql:param>`: Sets query parameters
      - `<sql:transaction>`: Manages database transactions

   4. **XML Tags (x prefix)**

      - `<x:parse>`: Parses XML documents
      - `<x:transform>`: Applies XSLT transformations
      - `<x:set>`: Sets XML-related variables
      - `<x:out>`: Outputs XML content
      - `<x:forEach>`: Iterates over XML nodes

   5. **Functions Tags (fn prefix)**
      - `${fn:length()}`: Returns string/collection length
      - `${fn:toUpperCase()}`: Converts to uppercase
      - `${fn:toLowerCase()}`: Converts to lowercase
      - `${fn:trim()}`: Removes whitespace
      - `${fn:substring()}`: Extracts substring
      - `${fn:replace()}`: Replaces text
      - `${fn:contains()}`: Checks string containment
      - `${fn:startsWith()}`: Checks string prefix
      - `${fn:endsWith()}`: Checks string suffix

   Best Practices:

   - Use appropriate tag libraries
   - Minimize scriptlet usage
   - Keep logic in backing beans/servlets
   - Validate and sanitize input
   - Handle exceptions gracefully

1. **How to disable session in JSP?**

   - Use the `session` directive with `false` attribute:
     ```jsp
     <%@ page session="false" %>
     ```
   - Prevents automatic session creation
   - Useful when you don't need session tracking
   - Reduces server memory usage
   - Can still manually create session if needed using `request.getSession(true)`

   Key points:

   - `session="false"` does NOT delete existing session
   - It prevents creating a new session automatically
   - Helps optimize performance for stateless pages

1. **How to delete a Cookie in a JSP?**

   - To delete a cookie, set its maximum age to 0 and add it back to the response
   - Example:
     ```jsp
     <%
     // Create a cookie with the same name and path as the original cookie
     Cookie cookie = new Cookie("cookieName", "");
     cookie.setMaxAge(0);  // Set max age to 0 to delete the cookie
     cookie.setPath("/");  // Use the same path as the original cookie
     response.addCookie(cookie);
     %>
     ```

   Key points:

   - Setting `setMaxAge(0)` instructs the browser to immediately remove the cookie
   - Specify the same path used when creating the original cookie
   - If the cookie was created with a specific domain, set the domain accordingly
   - Recommended to delete cookies with the same path and domain they were created with

## Servlet

1. **What is a Servlet?**

   - A Java class that extends the capabilities of a web server
   - Handles client requests and generates dynamic responses
   - Runs on the server-side within a web container/servlet container
   - Part of Java EE (Enterprise Edition) specification
   - Follows request-response programming model
   - Can handle multiple concurrent requests
   - Commonly used to implement web applications

2. **What are the differences between Get and Post methods?**

   1. **GET Method:**

      - Data sent as query parameters in URL
      - Limited data size (URL length restrictions)
      - Data is visible in browser URL
      - Bookmarkable and cacheable
      - Idempotent (multiple identical requests should have same effect)
      - Used for retrieving data
      - Not secure for sensitive information
      - Faster than POST

   2. **POST Method:**
      - Data sent in request body
      - No size limitation on data
      - Data not visible in URL
      - Not bookmarkable or cacheable by default
      - Not idempotent (multiple requests may have different effects)
      - Used for submitting data
      - More secure for sensitive information
      - Slightly slower than GET

3. **What is Request Dispatcher?**

   - An interface to forward/include requests to other resources
   - Resources can be servlets, JSP pages, or HTML files
   - Two main methods:
     - forward(): Forwards request to another resource
     - include(): Includes content of another resource
   - Useful for:
     - Implementing MVC pattern
     - Code reusability
     - Request routing
   - Can pass request/response objects between resources
   - Maintains request scope attributes
   - More efficient than redirects (single request)

4. **What are the differences between forward() method and sendRedirect() methods?**

   1. **forward() Method:**

      - Server-side operation
      - Single request/response cycle
      - URL doesn't change in browser
      - More efficient (no extra round trip)
      - Preserves request attributes
      - Same request and response objects
      - Can only forward within same application
      - Uses RequestDispatcher interface

   2. **sendRedirect() Method:**
      - Client-side redirection
      - Two request/response cycles
      - URL changes in browser
      - Less efficient (requires round trip)
      - Request attributes are lost
      - New request and response objects
      - Can redirect to any URL
      - Uses HttpServletResponse interface

5. **What is the life-cycle of a servlet?**

   - A servlet goes through the following lifecycle phases:

   1. **Loading and Instantiation:**

      - Servlet class is loaded
      - Servlet instance is created using default constructor
      - Done only once when first request arrives

   2. **Initialization (init()):**

      - init() method is called once after instantiation
      - Used for one-time initialization
      - Takes ServletConfig parameter
      - Throws ServletException if fails

   3. **Request Handling (service()):**

      - Called for each client request
      - Reads request data
      - Processes request
      - Generates response
      - Main business logic happens here
      - Dispatches to doGet(), doPost() etc.

   4. **Destruction (destroy()):**
      - Called when servlet is being taken out of service
      - Used for cleanup activities
      - Close resources, save state etc.
      - Called only once at end of life

   Key Points:

   - init() and destroy() called only once
   - service() called multiple times
   - Servlet instance persists between requests
   - Single instance serves multiple requests
   - Thread-safe handling required

6. **How do cookies work in Servlets?**

   - Cookies are small pieces of data stored on client browser
   - Used to maintain session data and user preferences

   Key Concepts:

   - Created using Cookie class
   - Set using response.addCookie()
   - Retrieved using request.getCookies()
   - Has name-value pairs, expiry, domain etc.

   Cookie Operations:

   1. **Creating/Setting Cookies:**

      - Create new Cookie object
      - Set attributes (max age, domain, path)
      - Add to response using addCookie()

   2. **Reading Cookies:**

      - Get cookies array from request
      - Iterate to find desired cookie
      - Read value using getValue()

   3. **Modifying/Deleting:**
      - Set new value or max age=0 to delete
      - Add modified cookie to response

   Best Practices:

   - Use secure cookies when possible
   - Set appropriate expiry time
   - Validate cookie data
   - Consider cookie size limits

7. **What are the differences between ServletContext vs ServletConfig?**

   ServletContext:

   - Shared across all servlets in web application
   - One per web application
   - Set in web.xml using <context-param>
   - Access using getServletContext()
   - Useful for application-wide data
   - Available throughout application lifecycle

   ServletConfig:

   - Specific to individual servlet
   - One per servlet instance
   - Set in web.xml using <init-param>
   - Access using getServletConfig()
   - Contains servlet initialization parameters
   - Available after servlet initialization

   Key Differences:

   - Scope: Application-wide vs Servlet-specific
   - Lifetime: Full application vs Servlet instance
   - Configuration: Context-param vs Init-param
   - Usage: Shared resources vs Init parameters
   - Access: All servlets vs Single servlet

8. **What are the different methods of session management in servlets?**

   1. **HttpSession Interface:**
      - Built-in session management
      - Created using request.getSession()
      - Automatically generates session ID
      - Can store objects using setAttribute()
      - Configurable timeout
   2. **URL Rewriting:**
      - Appends session ID to URL
      - Format: URL;jsessionid=xyz123
      - Useful when cookies disabled
      - Manual implementation needed
   3. **Hidden Form Fields:**
      - Embed session data in HTML forms
      - Passed between pages via POST
      - Requires form submission
      - Limited to form interactions
   4. **Cookies:**
      - Store session ID in browser
      - Created using Cookie class
      - Sent with each request
      - Can set expiration time
   5. **SSL Sessions:**
      - Secure session management
      - Uses HTTPS protocol
      - Client authentication
      - Encrypted communication

   Best Practices:

   - Use HttpSession when possible
   - Implement proper timeout
   - Validate session data
   - Consider security implications
   - Handle session expiration
