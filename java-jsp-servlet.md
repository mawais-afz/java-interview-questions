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
  
2. **Brief the life cycle of an applet:**

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

2. **Explain the various directives in JSP:**

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

3. **Explain the lifecycle of Servlet:**

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

4. **Different Authentication Methods in Java Servlets:**

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
