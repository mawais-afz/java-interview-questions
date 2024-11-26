# Java Regex

1. **Name some classes present in java.util.regex package?**

   - MatchResult: Represents the result of a match operation
   - Pattern: Compiles a regular expression into a pattern
   - Matcher: Engine that performs match operations on a character sequence by interpreting a Pattern
   - PatternSyntaxException: Unchecked exception thrown to indicate a syntax error in a regular expression pattern

2. **How are metacharacters different from ordinary characters?**

   Metacharacters are special characters that have special meaning in regular expressions, while ordinary characters match themselves literally.

   - Ordinary characters: Letters (a-z, A-Z), digits (0-9), and some symbols that match exactly what they represent
   - Metacharacters: Special characters like ., \*, +, ?, ^, $, |, \, (), [], {} that have special meanings:
     - . matches any single character
     - - means zero or more occurrences
     - - means one or more occurrences
     - ? means zero or one occurrence
     - ^ matches beginning of line
     - $ matches end of line
     - | acts as OR operator
     - \ escapes special characters
     - () groups patterns
     - [] defines character classes
     - {} specifies occurrences

   To match metacharacters literally, they need to be escaped with a backslash (\).

3. **Write a regular expression to validate a password. A password must start with an alphabet and followed by alphanumeric characters; Its length must be in between 8 to 20.**

   The regular expression pattern would be:

   ```java
   ^[a-zA-Z][a-zA-Z0-9]{7,19}$
   ```

   Explanation:

   - `^` - Start of string
   - `[a-zA-Z]` - First character must be a letter (uppercase or lowercase)
   - `[a-zA-Z0-9]` - Followed by letters or numbers
   - `{7,19}` - Length of 7-19 for the second part (plus the first letter = 8-20 total)
   - `$` - End of string

4. **What is the output of the following Java program?**

   ```java
   import java.util.regex.*;
   class RegexExample2{
       public static void main(String args[]){
           System.out.println(Pattern.matches(".s", "as")); //line 4
           System.out.println(Pattern.matches(".s", "mk")); //line 5
           System.out.println(Pattern.matches(".s", "mst")); //line 6
           System.out.println(Pattern.matches(".s", "amms")); //line 7
           System.out.println(Pattern.matches("..s", "mas")); //line 8
       }
   }
   ```

   Output:

   ```
   true    // .s matches "as" since . matches 'a' and s matches 's'
   false   // .s doesn't match "mk" since k is not 's'
   false   // .s doesn't match "mst" since it has 3 characters
   false   // .s doesn't match "amms" since it has 4 characters
   true    // ..s matches "mas" since . matches 'm', . matches 'a', and s matches 's'
   ```

5. **What is a regular expression?**
6. **What is the difference between a regular expression and a pattern?**
7. **What is the difference between a character class and a character set?**
8. **What is the difference between a quantifier and a quantifier prefix?**
9. **What is the difference between a capturing group and a non-capturing group?**
10. **What is the difference between a backreference and a backreference prefix?**
11. **What is the difference between a boundary matcher and a boundary matcher prefix?**
12. **What is the difference between a flag and a flag prefix?**
13. **What is the difference between a pattern and a matcher?**
