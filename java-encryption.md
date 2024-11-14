# Java Encryption

1. **What is JCA in Java?**

    JCA (Java Cryptography Architecture) is a framework for working with cryptography using Java programming language. It's part of the Java Security API and provides a set of APIs for various security services including:

    - Digital signatures
    - Message digests (hashes)
    - Certificates and certificate validation
    - Encryption (symmetric and asymmetric)
    - Key generation and key management
    - Secure random number generation

    Key features of JCA:

    1. **Provider-based architecture**: 
    - Allows for multiple interchangeable cryptographic implementations
    - Default provider is "SunJCE" (Sun's implementation)
    - Can add third-party providers

    2. **Algorithm independence**:
    - Applications can be written independent of cryptographic algorithms
    - Algorithms can be changed without modifying application code

    3. **Implementation independence**:
    - Applications can be written independent of specific implementations
    - Different providers can be plugged in seamlessly

    Example usage:
