# Networking

1. **Give a brief description of Java socket programming?**

   Java socket programming enables communication between applications over a network. It provides a way for programs to establish connections and exchange data across machines. The java.net package contains key classes like Socket (for client-side connections) and ServerSocket (for server-side connections) that handle the low-level details of network communication. Using these, developers can create client-server applications where data can be sent and received through input/output streams.

2. **What is Socket?**

   A Socket is a software endpoint that establishes bidirectional communication between two computers over a network. It represents one end of a two-way communication link between programs running on a network, combining an IP address and a port number. In Java, the Socket class from java.net package implements this concept, providing methods to connect to a remote machine, send data through OutputStream, and receive data through InputStream.

3. **What are the steps that are followed when two computers connect through TCP?**

   The TCP three-way handshake process establishes a connection between two computers:

   1. **SYN (Synchronize):**

      - Client sends SYN packet to server
      - Includes initial sequence number
      - Indicates client wants to establish connection

   2. **SYN-ACK (Synchronize-Acknowledge):**
      - Server responds with SYN-ACK packet
      - Acknowledges client's sequence number
      - Includes server's own sequence number
   3. **ACK (Acknowledge):**
      - Client sends ACK packet to server
      - Acknowledges server's sequence number
      - Connection is now established

   After connection establishment:

   - Both sides can begin sending data
   - Data packets are acknowledged
   - Flow control and error checking are handled
   - Connection remains until explicitly closed

   Connection termination follows a four-way handshake:

   1. Client sends FIN packet
   2. Server sends ACK
   3. Server sends FIN
   4. Client sends final ACK

4. **Write a program in Java to establish a connection between client and server?**

   Here is a simple example of a Java program that establishes a connection between a client and a server using sockets:

   **Server Code:**

   ```java
   import java.io.*;
   import java.net.*;

   public class SimpleServer {
       public static void main(String[] args) {
           try (ServerSocket serverSocket = new ServerSocket(12345)) {
               System.out.println("Server is listening on port 12345");
               Socket socket = serverSocket.accept();
               System.out.println("Client connected");

               // Input and output streams
               InputStream input = socket.getInputStream();
               OutputStream output = socket.getOutputStream();
               BufferedReader reader = new BufferedReader(new InputStreamReader(input));
               PrintWriter writer = new PrintWriter(output, true);

               // Communication
               writer.println("Hello from server!");
               String message = reader.readLine();
               System.out.println("Received from client: " + message);

           } catch (IOException e) {
               e.printStackTrace();
           }
       }
   }
   ```

   **Client Code:**

   ```java
   import java.io.*;
   import java.net.*;

   public class SimpleClient {
       public static void main(String[] args) {
           try (Socket socket = new Socket("localhost", 12345)) {
               System.out.println("Connected to the server");

               // Input and output streams
               InputStream input = socket.getInputStream();
               OutputStream output = socket.getOutputStream();
               BufferedReader reader = new BufferedReader(new InputStreamReader(input));
               PrintWriter writer = new PrintWriter(output, true);

               // Communication
               String response = reader.readLine();
               System.out.println("Received from server: " + response);
               writer.println("Hello from client!");

           } catch (IOException e) {
               e.printStackTrace();
           }
       }
   }
   ```

5. **How do I convert a numeric IP address like 192.18.97.39 into a hostname like java.sun.com?**
   You can use the `InetAddress` class in Java to perform this conversion. Here’s an example:
   ```java
   try {
       InetAddress inetAddress = InetAddress.getByName("192.18.97.39");
       String hostname = inetAddress.getHostName();
       System.out.println("Hostname: " + hostname);
   } catch (UnknownHostException e) {
       e.printStackTrace();
   }
   ```