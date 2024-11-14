# Java Miscellaneous

## Serialization

1. **What is serialization?**
   Serialization is the process of converting an object into a byte stream that can be:

   - Saved to a file
   - Sent over a network
   - Stored in a database

   Key points about serialization:

   - Implements the Serializable interface
   - Allows object persistence and transmission
   - Maintains object state and relationships
   - Used for deep copying objects

   Example of serialization:

   ```java
   // Serializing
   FileOutputStream file = new FileOutputStream("object.ser");
   ObjectOutputStream out = new ObjectOutputStream(file);
   out.writeObject(myObject);

   // Deserializing
   FileInputStream file = new FileInputStream("object.ser");
   ObjectInputStream in = new ObjectInputStream(file);
   MyClass myObject = (MyClass) in.readObject();
   ```

2. **How to not allow serialization of attributes of a class in Java?**
   There are several ways to prevent serialization of class attributes:

   1. **Using transient keyword:**

   - Mark fields with `transient` to exclude them from serialization
   - During deserialization, transient fields get default values

   ```java
   class User implements Serializable {
       private String name;     // will be serialized
       transient private String password;  // won't be serialized
   }
   ```

   1. **Static fields:**

      - Static fields are not serialized by default
      - They belong to class, not instance

      ```java
      class Config implements Serializable {
          static String apiKey;  // won't be serialized
      }
      ```

   2. **Custom serialization:**

      - Implement writeObject() and readObject() methods
      - Explicitly control what gets serialized

      ```java
      private void writeObject(ObjectOutputStream out) throws IOException {
          // Custom serialization logic
      }
      ```

   3. **Using SerialVersionUID:**
      - While not preventing serialization, helps control versioning
      ```java
      private static final long serialVersionUID = 1L;
      ```

3. **Explain the Externalizable interface.**

   The Externalizable interface provides a way to customize the serialization process with more control than Serializable. Key points:

   - It extends Serializable interface
   - Requires implementing two methods:
     - writeExternal(ObjectOutput out)
     - readExternal(ObjectInput in)
   - Gives complete control over serialization format
   - Requires a no-arg constructor
   - Generally performs better than Serializable

   Example:

   ```java
   public class User implements Externalizable {
       private String name;
       private transient String password;

       // Required no-arg constructor
       public User() {}

       @Override
       public void writeExternal(ObjectOutput out) throws IOException {
           out.writeObject(name);
           // password not written - sensitive data
       }

       @Override
       public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
           name = (String) in.readObject();
           password = null; // explicitly set sensitive data
       }
   }
   ```

   Key differences from Serializable:

   - More explicit control over serialization process
   - Better performance (no reflection used)
   - Requires manual implementation of serialization logic
   - Must have public no-arg constructor
