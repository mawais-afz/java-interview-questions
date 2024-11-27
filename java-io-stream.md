# Java IO Streams

1.  **What do you understand by an IO stream?**

    An I/O (Input/Output) stream represents a sequence of data flowing between a source and a destination. In Java, streams are used to read data from a source (input stream) or write data to a destination (output stream). The source or destination can be files, network connections, memory buffers, or other devices.

    Key characteristics of I/O streams:

    - They are ordered sequences of data
    - They can be byte-based or character-based
    - They are unidirectional (either input or output)
    - They can be buffered or unbuffered
    - They follow a consistent abstraction regardless of the underlying data source/destination

2.  **Give the hierarchy of InputStream and OutputStream classes?**

    **InputStream Hierarchy:**

    - InputStream (abstract base class)
      - FileInputStream
      - ByteArrayInputStream
      - FilterInputStream
        - BufferedInputStream
        - DataInputStream
      - ObjectInputStream
      - PipedInputStream
      - SequenceInputStream
      - StringBufferInputStream (deprecated)
      - AudioInputStream

    **OutputStream Hierarchy:**

    - OutputStream (abstract base class)
      - FileOutputStream
      - ByteArrayOutputStream
      - FilterOutputStream
        - BufferedOutputStream
        - DataOutputStream
        - PrintStream
      - ObjectOutputStream
      - PipedOutputStream

3.  **What is the difference between the Reader/Writer class hierarchy and the InputStream/OutputStream class hierarchy?**

    | Aspect                 | Reader/Writer                                                                                        | InputStream/OutputStream                                                                                                                               |
    | ---------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | Data Type Handling     | Works with character data (Unicode)                                                                  | Works with byte data (raw binary)                                                                                                                      |
    | Use Cases              | Text files, character-based data, String manipulation                                                | Binary files, raw data, media files, network communication                                                                                             |
    | Character Encoding     | Handles character encoding/decoding automatically                                                    | Requires manual handling of character encoding                                                                                                         |
    | Base Classes           | Abstract base classes for character streams                                                          | Abstract base classes for byte streams                                                                                                                 |
    | Common Implementations | Reader: FileReader, BufferedReader, StringReader<br>Writer: FileWriter, BufferedWriter, StringWriter | InputStream: FileInputStream, BufferedInputStream, ByteArrayInputStream<br>OutputStream: FileOutputStream, BufferedOutputStream, ByteArrayOutputStream |

4.  **What are the super most classes for all the streams?**

    In Java IO, there are four abstract superclasses that form the foundation of all stream classes:

    - **InputStream**: The superclass of all byte-based input streams
    - **OutputStream**: The superclass of all byte-based output streams
    - **Reader**: The superclass of all character-based input streams
    - **Writer**: The superclass of all character-based output streams

    These abstract classes define the basic functionality and common methods that all stream subclasses inherit. The byte stream classes (InputStream/OutputStream) handle raw binary data, while the character stream classes (Reader/Writer) handle text data with proper character encoding.

5.  **What are the FileInputStream and FileOutputStream?**

    FileInputStream and FileOutputStream are byte stream classes used for reading from and writing to files respectively.

    **FileInputStream:**

    - Used to read bytes from a file
    - Creates an input stream connected to a file on disk
    - Common methods:
      - `read()`: Reads one byte
      - `read(byte[] b)`: Reads bytes into an array
      - `close()`: Closes the stream

    Example:

    ```java
    FileInputStream fis = new FileInputStream("input.txt");
    int data = fis.read(); // reads one byte
    fis.close();
    ```

    **FileOutputStream:**

    - Used to write bytes to a file
    - Creates an output stream connected to a file on disk
    - Can create new files or overwrite existing ones
    - Common methods:
      - `write(int b)`: Writes one byte
      - `write(byte[] b)`: Writes an array of bytes
      - `close()`: Closes the stream

    Example:

    ```java
    FileOutputStream fos = new FileOutputStream("output.txt");
    fos.write("Hello".getBytes());
    fos.close();
    ```

    Important notes:

    - Both classes work with raw bytes, not characters
    - Always close streams to prevent resource leaks
    - Use try-with-resources for automatic closing
    - For text files, FileReader/FileWriter are often better choices

6.  **What is the purpose of using BufferedInputStream and BufferedOutputStream classes?**

    BufferedInputStream and BufferedOutputStream are wrapper classes that add buffering functionality to byte streams for improved performance.

    **BufferedInputStream:**

    - Adds a buffer when reading data from the underlying input stream
    - Reduces the number of actual disk/network reads by reading larger chunks into memory
    - Default buffer size is 8KB, but can be customized
    - Significantly improves performance when reading data byte-by-byte

    Example:

    ```java
    BufferedInputStream bis = new BufferedInputStream(new FileInputStream("file.txt"));
    int data = bis.read(); // reads from buffer instead of disk
    bis.close();
    ```

    **BufferedOutputStream:**

    - Adds a buffer when writing data to the underlying output stream
    - Collects written data in memory before flushing to disk/network
    - Reduces number of actual I/O operations
    - Must call flush() to ensure all data is written

    Example:

    ```java
    BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("file.txt"));
    bos.write("Hello".getBytes()); // writes to buffer first
    bos.flush(); // ensures data is written to disk
    bos.close();
    ```

    Key benefits:

    - Improved performance through reduced I/O operations
    - More efficient memory usage
    - Particularly useful for large files or network streams
    - Can be wrapped around any InputStream/OutputStream

7.  **What are FilterStreams?**

    FilterInputStream and FilterOutputStream are abstract base classes that serve as wrappers for other input/output streams, allowing for additional functionality to be added.

    **Key characteristics:**

    - Act as base classes for other stream wrapper implementations
    - Follow the Decorator pattern to add features to existing streams
    - Don't modify the data, but provide a framework for subclasses

    Common subclasses include:

    - BufferedInputStream/BufferedOutputStream (adds buffering)
    - DataInputStream/DataOutputStream (reads/writes primitive data types)
    - PrintStream (adds printing functionality)

    Example:

    ```java
    // Creating a buffered stream using FilterOutputStream subclass
    FilterOutputStream fos = new BufferedOutputStream(
        new FileOutputStream("file.txt")
    );
    ```

    Benefits:

    - Enables modular enhancement of stream functionality
    - Allows for chaining of multiple filters
    - Maintains consistency with stream interface
    - Facilitates creation of custom stream filters

8.  **What is an I/O filter?**

    An I/O filter is a class that wraps an existing input or output stream to add functionality without modifying the underlying stream. It implements the Decorator pattern.

    Key points:

    - Sits between the application and the actual I/O stream
    - Can transform data as it passes through
    - Can add buffering, data conversion, or other features
    - Multiple filters can be chained together

    Common examples:

    - BufferedInputStream (adds buffering)
    - DataInputStream (reads primitive data types)
    - PrintStream (adds formatted output)
    - GZIPInputStream (decompresses data)

    Example:

    ```java
    // Chain of filters: buffering + data type handling
    DataInputStream dis = new DataInputStream(
        new BufferedInputStream(
            new FileInputStream("data.bin")
        )
    );
    ```

    Benefits:

    - Modular addition of features
    - Reusable components
    - Flexible stream processing
    - Clean separation of concerns

9.  **How many ways you can take input from the console?**

    There are several ways to read input from the console in Java:

    1. **Scanner class:**

    ```java
    Scanner scanner = new Scanner(System.in);
    String input = scanner.nextLine(); // read a line
    int number = scanner.nextInt();    // read an integer
    ```

    2. **BufferedReader with InputStreamReader:**

    ```java
    BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
    String line = reader.readLine();
    ```

    3. **Console class:**

    ```java
    Console console = System.console();
    String input = console.readLine();
    char[] password = console.readPassword(); // for secure password input
    ```

    4. **System.in directly:**

    ```java
    int byteRead = System.in.read(); // reads a single byte
    ```

    Key differences:

    - Scanner: Most convenient, includes parsing methods
    - BufferedReader: More efficient for reading large amounts of text
    - Console: Secure password reading, but not available in all environments
    - System.in: Low-level, rarely used directly

    Best practices:

    - Always close Scanner/BufferedReader when done
    - Use try-with-resources for automatic resource management
    - Choose method based on specific needs (parsing vs raw input)
