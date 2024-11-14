# Problem Solving

1. **Write a program to Reverse a String**

   ```java
   // Approach 1: Using StringBuilder
   public String reverseString(String str) {
       return new StringBuilder(str).reverse().toString();
   }

   // Approach 2: Using char array
   public String reverseString2(String str) {
       char[] chars = str.toCharArray();
       int left = 0, right = chars.length - 1;
       while (left < right) {
           char temp = chars[left];
           chars[left] = chars[right];
           chars[right] = temp;
           left++;
           right--;
       }
       return new String(chars);
   }

   // Approach 3: Using recursion
   public String reverseString3(String str) {
       if (str.length() <= 1) return str;
       return reverseString3(str.substring(1)) + str.charAt(0);
   }

   // Approach 4: Using stack
   public String reverseString4(String str) {
       Stack<Character> stack = new Stack<>();
       for (char c : str.toCharArray()) {
           stack.push(c);
       }
       StringBuilder sb = new StringBuilder();
       while (!stack.isEmpty()) {
           sb.append(stack.pop());
       }
       return sb.toString();
   }
   ```

   Example:

   ```
   Input: "hello"
   Output: "olleh"
   ```

   Time Complexity: O(n) for all approaches
   Space Complexity: O(n) for all approaches

2. **Find the word count in a string using HashMap Collection.**

   ```java
   public Map<String, Integer> getWordCount(String str) {
       // Handle null or empty string
       if (str == null || str.trim().isEmpty()) {
           return new HashMap<>();
       }

       // Split string into words and create HashMap
       Map<String, Integer> wordCount = new HashMap<>();
       String[] words = str.trim().split("\\s+");

       // Count occurrences of each word
       for (String word : words) {
           wordCount.put(word, wordCount.getOrDefault(word, 0) + 1);
       }

       return wordCount;
   }
   ```

   Example:

   ```
   Input: "hello world hello"
   Output: {hello=2, world=1}
   ```

   Time Complexity: O(n) where n is the number of words
   Space Complexity: O(k) where k is the number of unique words

3. **Write a Program to remove duplicates in an ArrayList.**

   ```java
   public ArrayList<Integer> removeDuplicates(ArrayList<Integer> list) {
       // Handle null or empty list
       if (list == null || list.isEmpty()) {
           return new ArrayList<>();
       }

       // Use LinkedHashSet to maintain order while removing duplicates
       LinkedHashSet<Integer> set = new LinkedHashSet<>(list);

       // Convert back to ArrayList
       return new ArrayList<>(set);
   }

   // Alternative approach using Stream API
   public ArrayList<Integer> removeDuplicatesStream(ArrayList<Integer> list) {
       if (list == null || list.isEmpty()) {
           return new ArrayList<>();
       }

       return new ArrayList<>(list.stream()
                                .distinct()
                                .collect(Collectors.toList()));
   }
   ```

   Example:

   ```
   Input: [1, 3, 5, 3, 7, 1, 9, 3]
   Output: [1, 3, 5, 7, 9]
   ```

   Time Complexity: O(n)
   Space Complexity: O(n)

4. **Write a program that detects the duplicate characters in a string.**

   ```java
   public Map<Character, Integer> findDuplicateChars(String str) {
       // Handle null or empty string
       if (str == null || str.isEmpty()) {
           return new HashMap<>();
       }

       // Create map to store character counts
       Map<Character, Integer> charCount = new HashMap<>();

       // Count occurrences of each character
       for (char c : str.toCharArray()) {
           charCount.put(c, charCount.getOrDefault(c, 0) + 1);
       }

       // Filter to only keep duplicates
       return charCount.entrySet().stream()
           .filter(entry -> entry.getValue() > 1)
           .collect(Collectors.toMap(
               Map.Entry::getKey,
               Map.Entry::getValue
           ));
   }
   ```

   Example:

   ```
   Input: "hello world"
   Output: {l=3, o=2}
   ```

   Time Complexity: O(n) where n is the length of the string
   Space Complexity: O(k) where k is the number of unique characters

5. **Write a program to find the square root of a number.**

   ```java
   public double sqrt(double number) {
       // Handle negative numbers
       if (number < 0) {
           throw new IllegalArgumentException("Cannot find square root of negative number");
       }

       // Handle 0 and 1 special cases
       if (number == 0 || number == 1) {
           return number;
       }

       // Use Newton's method for approximation
       double precision = 0.00001;
       double guess = number / 2.0;

       while (Math.abs(guess * guess - number) > precision) {
           guess = (guess + number / guess) / 2.0;
       }

       return guess;
   }
   ```

   Example:

   ```
   Input: 16.0
   Output: 4.0

   Input: 2.0
   Output: 1.4142135623730951
   ```

   Time Complexity: O(log n)
   Space Complexity: O(1)

6. **Write a Java program for solving the Tower of Hanoi Problem.**

   ```java
   public void towerOfHanoi(int n, char source, char auxiliary, char destination) {
       // Base case: if only 1 disk, move it directly
       if (n == 1) {
           System.out.println("Move disk 1 from " + source + " to " + destination);
           return;
       }

       // Move n-1 disks from source to auxiliary using destination as helper
       towerOfHanoi(n - 1, source, destination, auxiliary);

       // Move the nth disk from source to destination
       System.out.println("Move disk " + n + " from " + source + " to " + destination);

       // Move n-1 disks from auxiliary to destination using source as helper
       towerOfHanoi(n - 1, auxiliary, source, destination);
   }
   ```

   Example:

   ```
   Input: n = 3, source = 'A', auxiliary = 'B', destination = 'C'
   Output:
   Move disk 1 from A to C
   Move disk 2 from A to B
   Move disk 1 from C to B
   Move disk 3 from A to C
   Move disk 1 from B to A
   Move disk 2 from B to C
   Move disk 1 from A to C
   ```

   Time Complexity: O(2^n) where n is the number of disks
   Space Complexity: O(n) due to recursive call stack

7. **Write a java program to check if any number given as input is the sum of 2 prime numbers.**

   ```java
   public class SumOfPrimes {
       // Check if a number is prime
       private static boolean isPrime(int n) {
           if (n <= 1) return false;
           for (int i = 2; i <= Math.sqrt(n); i++) {
               if (n % i == 0) return false;
           }
           return true;
       }

       // Check if number can be expressed as sum of two primes
       public static boolean isSumOfTwoPrimes(int num) {
           // Check all numbers from 2 to num/2
           for (int i = 2; i <= num/2; i++) {
               // If both i and (num-i) are prime, return true
               if (isPrime(i) && isPrime(num - i)) {
                   System.out.println(num + " = " + i + " + " + (num-i));
                   return true;
               }
           }
           return false;
       }

       public static void main(String[] args) {
           int num = 34;  // Example input
           if (isSumOfTwoPrimes(num)) {
               System.out.println(num + " can be expressed as sum of two prime numbers");
           } else {
               System.out.println(num + " cannot be expressed as sum of two prime numbers");
           }
       }
   }
   ```

   Example:

   ```
   Input: 34
   Output:
   34 = 3 + 31
   34 can be expressed as sum of two prime numbers

   Input: 11
   Output:
   11 = 2 + 9
   11 can be expressed as sum of two prime numbers
   ```

   Time Complexity: O(n \* sqrt(n)) where n is the input number
   Space Complexity: O(1)

8. **Write a Java program to rotate arrays 90 degree clockwise by taking matrices from user input**

   ```java
   import java.util.Scanner;

   public class MatrixRotation {
       // Function to rotate matrix 90 degrees clockwise
       private static void rotateMatrix(int[][] matrix, int n) {
           // First transpose the matrix
           for (int i = 0; i < n; i++) {
               for (int j = i; j < n; j++) {
                   int temp = matrix[i][j];
                   matrix[i][j] = matrix[j][i];
                   matrix[j][i] = temp;
               }
           }

           // Then reverse each row
           for (int i = 0; i < n; i++) {
               for (int j = 0; j < n/2; j++) {
                   int temp = matrix[i][j];
                   matrix[i][j] = matrix[i][n-1-j];
                   matrix[i][n-1-j] = temp;
               }
           }
       }

       // Function to print matrix
       private static void printMatrix(int[][] matrix, int n) {
           for (int i = 0; i < n; i++) {
               for (int j = 0; j < n; j++) {
                   System.out.print(matrix[i][j] + " ");
               }
               System.out.println();
           }
       }

       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);

           System.out.print("Enter the size of the square matrix (n): ");
           int n = scanner.nextInt();

           int[][] matrix = new int[n][n];

           System.out.println("Enter the matrix elements:");
           for (int i = 0; i < n; i++) {
               for (int j = 0; j < n; j++) {
                   matrix[i][j] = scanner.nextInt();
               }
           }

           System.out.println("\nOriginal Matrix:");
           printMatrix(matrix, n);

           rotateMatrix(matrix, n);

           System.out.println("\nMatrix after 90 degree clockwise rotation:");
           printMatrix(matrix, n);

           scanner.close();
       }
   }
   ```

   Example:

   ```
   Input:
   Enter the size of the square matrix (n): 3
   Enter the matrix elements:
   1 2 3
   4 5 6
   7 8 9

   Output:
   Original Matrix:
   1 2 3
   4 5 6
   7 8 9

   Matrix after 90 degree clockwise rotation:
   7 4 1
   8 5 2
   9 6 3
   ```

   Time Complexity: O(n²) where n is the size of the matrix
   Space Complexity: O(1) as we are rotating the matrix in-place

9. **Write a Java program to rotate arrays 90 degree anti-clockwise by taking matrices from user input**

   ```java
   import java.util.Scanner;

   public class MatrixRotation {
       public static void rotateMatrixAntiClockwise(int[][] matrix, int n) {
           // First transpose the matrix
           for (int i = 0; i < n; i++) {
               for (int j = i; j < n; j++) {
                   int temp = matrix[i][j];
                   matrix[i][j] = matrix[j][i];
                   matrix[j][i] = temp;
               }
           }

           // Then reverse each row
           for (int i = 0; i < n/2; i++) {
               for (int j = 0; j < n; j++) {
                   int temp = matrix[i][j];
                   matrix[i][j] = matrix[n-1-i][j];
                   matrix[n-1-i][j] = temp;
               }
           }
       }

       public static void printMatrix(int[][] matrix, int n) {
           for (int i = 0; i < n; i++) {
               for (int j = 0; j < n; j++) {
                   System.out.print(matrix[i][j] + " ");
               }
               System.out.println();
           }
       }

       public static void main(String[] args) {
           Scanner scanner = new Scanner(System.in);

           System.out.print("Enter the size of the square matrix (n): ");
           int n = scanner.nextInt();

           int[][] matrix = new int[n][n];

           System.out.println("Enter the matrix elements:");
           for (int i = 0; i < n; i++) {
               for (int j = 0; j < n; j++) {
                   matrix[i][j] = scanner.nextInt();
               }
           }

           System.out.println("\nOriginal Matrix:");
           printMatrix(matrix, n);

           rotateMatrixAntiClockwise(matrix, n);

           System.out.println("\nMatrix after 90 degree anti-clockwise rotation:");
           printMatrix(matrix, n);

           scanner.close();
       }
   }
   ```

   Example:

   ```
   Input:
   Enter the size of the square matrix (n): 3
   Enter the matrix elements:
   1 2 3
   4 5 6
   7 8 9

   Output:
   Original Matrix:
   1 2 3
   4 5 6
   7 8 9

   Matrix after 90 degree anti-clockwise rotation:
   3 6 9
   2 5 8
   1 4 7
   ```

   Time Complexity: O(n²) where n is the size of the matrix
   Space Complexity: O(1) as we are rotating the matrix in-place

10. **Write a Java program to create and throw custom exceptions.**

    ```java
    // Custom exception class
    class InvalidAgeException extends Exception {
        public InvalidAgeException(String message) {
            super(message);
        }
    }

    public class CustomExceptionDemo {
        public static void validateAge(int age) throws InvalidAgeException {
            if (age < 0) {
                throw new InvalidAgeException("Age cannot be negative");
            }
            if (age < 18) {
                throw new InvalidAgeException("Age must be 18 or older");
            }
            System.out.println("Valid age: " + age);
        }

        public static void main(String[] args) {
            try {
                validateAge(15);  // This will throw an exception
            } catch (InvalidAgeException e) {
                System.out.println("Caught exception: " + e.getMessage());
            }

            try {
                validateAge(-5);  // This will throw an exception
            } catch (InvalidAgeException e) {
                System.out.println("Caught exception: " + e.getMessage());
            }

            try {
                validateAge(20);  // This will be valid
            } catch (InvalidAgeException e) {
                System.out.println("Caught exception: " + e.getMessage());
            }
        }
    }
    ```

    Example Output:

    ```
    Caught exception: Age must be 18 or older
    Caught exception: Age cannot be negative
    Valid age: 20
    ```

    This program demonstrates:

    1. Creating a custom exception class by extending Exception
    2. Throwing custom exceptions with meaningful messages
    3. Using try-catch blocks to handle exceptions
    4. Multiple validation checks throwing different exception messages

11. **Given an array of non-duplicating numbers from 1 to n where one number is missing, write an efficient java program to find that missing number.**

    ```java
    public class MissingNumber {
        public static int findMissingNumber(int[] nums) {
            int n = nums.length + 1; // Since one number is missing

            // Calculate expected sum of numbers from 1 to n
            int expectedSum = (n * (n + 1)) / 2;

            // Calculate actual sum of array
            int actualSum = 0;
            for (int num : nums) {
                actualSum += num;
            }

            // Missing number is the difference
            return expectedSum - actualSum;
        }

        public static void main(String[] args) {
            int[] arr = {1, 2, 4, 6, 3, 7, 8}; // 5 is missing
            System.out.println("Missing number is: " + findMissingNumber(arr));
        }
    }
    ```

    Output:

    ```
    Missing number is: 5
    ```

    This solution has:

    - Time Complexity: O(n)
    - Space Complexity: O(1)

    The program uses the mathematical formula for sum of first n natural numbers: n\*(n+1)/2
    By subtracting the actual sum of array from expected sum, we get the missing number.

12. **Write a Java Program to find the factorial of a given number.**

    ```java
    public class Factorial {
        public static long factorial(int n) {
            if (n < 0) {
                throw new IllegalArgumentException("Factorial is not defined for negative numbers");
            }
            if (n == 0 || n == 1) {
                return 1;
            }
            return n * factorial(n - 1);
        }

        public static void main(String[] args) {
            try {
                int number = 5;
                System.out.println("Factorial of " + number + " is: " + factorial(number));

                number = 0;
                System.out.println("Factorial of " + number + " is: " + factorial(number));

                number = -1;
                System.out.println("Factorial of " + number + " is: " + factorial(number));
            } catch (IllegalArgumentException e) {
                System.out.println("Error: " + e.getMessage());
            }
        }
    }
    ```

    Output:

    ```
    Factorial of 5 is: 120
    Factorial of 0 is: 1
    Error: Factorial is not defined for negative numbers
    ```

    This solution demonstrates:

    - Recursive approach to calculate factorial
    - Error handling for negative numbers
    - Base cases for 0 and 1
    - Time Complexity: O(n)
    - Space Complexity: O(n) due to recursive call stack

13. **Write a Java program to check if the two strings are anagrams**

    ```java
    public class AnagramChecker {
        public static boolean areAnagrams(String str1, String str2) {
            // Remove spaces and convert to lowercase for comparison
            str1 = str1.replaceAll("\\s", "").toLowerCase();
            str2 = str2.replaceAll("\\s", "").toLowerCase();

            // If lengths are different, they can't be anagrams
            if (str1.length() != str2.length()) {
                return false;
            }

            // Convert strings to char arrays and sort them
            char[] charArray1 = str1.toCharArray();
            char[] charArray2 = str2.toCharArray();
            Arrays.sort(charArray1);
            Arrays.sort(charArray2);

            // Compare sorted arrays
            return Arrays.equals(charArray1, charArray2);
        }

        public static void main(String[] args) {
            String s1 = "listen";
            String s2 = "silent";
            System.out.println("Are '" + s1 + "' and '" + s2 + "' anagrams? " +
                             areAnagrams(s1, s2));

            s1 = "hello";
            s2 = "world";
            System.out.println("Are '" + s1 + "' and '" + s2 + "' anagrams? " +
                             areAnagrams(s1, s2));
        }
    }
    ```

    Output:

    ```
    Are 'listen' and 'silent' anagrams? true
    Are 'hello' and 'world' anagrams? false
    ```

    This solution demonstrates:

    - String manipulation (removing spaces, converting to lowercase)
    - Character array sorting approach
    - Time Complexity: O(n log n) due to sorting
    - Space Complexity: O(n) for creating char arrays
    - Handles case-insensitive comparison
    - Handles spaces in strings

14. **Write a Java Program to print Fibonacci Series with/without Recursion**

    ```java
    public class FibonacciSeries {
        // Method to calculate nth Fibonacci number using recursion
        public static int fibonacciRecursive(int n) {
            if (n <= 1) return n;
            return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
        }

        // Method to calculate Fibonacci series iteratively
        public static void fibonacciIterative(int n) {
            int first = 0, second = 1;
            System.out.print(first + " " + second + " ");
            
            for (int i = 2; i < n; i++) {
                int next = first + second;
                System.out.print(next + " ");
                first = second;
                second = next;
            }
        }

        public static void main(String[] args) {
            int n = 10; // Number of terms to print
            
            System.out.println("Fibonacci Series (Recursive) up to " + n + " terms:");
            for (int i = 0; i < n; i++) {
                System.out.print(fibonacciRecursive(i) + " ");
            }
            
            System.out.println("\n\nFibonacci Series (Iterative) up to " + n + " terms:");
            fibonacciIterative(n);
        }
    }
    ```

    Output:
    ```
    Fibonacci Series (Recursive) up to 10 terms:
    0 1 1 2 3 5 8 13 21 34 

    Fibonacci Series (Iterative) up to 10 terms:
    0 1 1 2 3 5 8 13 21 34
    ```

    This solution demonstrates:
    - Both recursive and iterative approaches to generate Fibonacci numbers
    - Recursive approach: Time Complexity O(2^n), Space Complexity O(n)
    - Iterative approach: Time Complexity O(n), Space Complexity O(1)
    - Recursive approach to generate Fibonacci numbers
    - Time Complexity: O(2^n) due to recursive calls
    - Space Complexity: O(n) due to recursive call stack
    - Simple and elegant implementation
    - Base cases handling (n <= 1)

14. **Write a program to find the Second Highest number in an ArrayList**
15. **Check if a String is Palindrome**
16. **Find the Length of the Longest Substring Without Repeating Characters**
17. **Find the First Non-Repeating Character in a String**
18. **Find the Missing Number in an Array**
19. **Find the Maximum Subarray Sum**
20. **Find the Prime Numbers in a Given Range**
21. **Find the Fibonacci Numbers in a Given Range**
22. **Find the Factorial of a Number**
23. **Find the Greatest Common Divisor (GCD) of Two Numbers**
24. **Find the Least Common Multiple (LCM) of Two Numbers**
25. **Find the Number of Ways to Climb Stairs**
26. **Find the Number of Islands**
27. **Find the Number of Connected Components in an Undirected Graph**
28. **Find the Number of Ways to Traverse a Grid**
29. **Find the Maximum Product Subarray**
30. **Find the Maximum Depth of a Binary Tree**
31. **Find the Minimum Path Sum in a Triangle**
32. **Find the Number of Ways to Make Change**
33. **Find the Number of Ways to Represent a Number**
