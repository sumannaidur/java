# Java Exception Handling Cheat Sheet
*August 07, 2025, 10:40 PM IST*

## Module 5: Exception Handling
Exception handling in Java manages runtime errors, preventing program crashes and enabling graceful recovery.

---

## try-catch-finally
Core mechanism for handling exceptions.

### try Block
Contains code that might throw an exception. If an exception occurs, execution stops, and control moves to a matching `catch` block.

### catch Block
Handles specific exceptions. Multiple `catch` blocks can follow a `try`, ordered from specific to general.

### finally Block
Executes regardless of exception occurrence, used for cleanup (e.g., closing resources). Skipped only if JVM exits or a fatal error occurs.

### Syntax
```java
try {
    // Code that might throw an exception
} catch (ExceptionType1 e1) {
    // Handle ExceptionType1
} catch (ExceptionType2 e2) {
    // Handle ExceptionType2
} finally {
    // Cleanup code
}
```

### Example
```java
import java.io.FileReader;
import java.io.IOException;
import java.util.InputMismatchException;
import java.util.Scanner;

public class ExceptionHandlingExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        FileReader reader = null;
        try {
            System.out.print("Enter a number: ");
            int num = scanner.nextInt(); // InputMismatchException
            int result = 100 / num; // ArithmeticException
            System.out.println("Result: " + result);
            reader = new FileReader("nonexistent_file.txt"); // IOException
        } catch (InputMismatchException e) {
            System.out.println("Invalid input. Enter an integer.");
            scanner.nextLine();
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero.");
        } catch (IOException e) {
            System.out.println("File error: " + e.getMessage());
        } finally {
            if (scanner != null) scanner.close();
            if (reader != null) {
                try {
                    reader.close();
                } catch (IOException e) {
                    System.out.println("Error closing FileReader.");
                }
            }
            System.out.println("Finally block executed.");
        }
    }
}
```

### Interview Questions
- **Q: What is an exception? Why is exception handling important?**  
  A: An exception is a runtime event disrupting normal program flow. Handling prevents crashes, enables recovery, and ensures resource cleanup.
- **Q: Purpose of try, catch, finally?**  
  A: **try**: Encloses risky code. **catch**: Handles specific exceptions. **finally**: Executes cleanup code regardless of exceptions.
- **Q: Does finally always execute?**  
  A: Almost always, except if JVM exits (`System.exit()`) or a fatal error occurs (e.g., `OutOfMemoryError`).

---

## throw and throws
Keywords for managing exceptions.

### throw
Explicitly throws an exception object.
```java
throw new ArithmeticException("Divide by zero");
```

### throws
Declares checked exceptions a method might throw, requiring callers to handle or re-declare.
```java
public void readFile() throws IOException {
    // Code
}
```

### Checked vs. Unchecked Exceptions
- **Checked**: Subclasses of `Exception` (not `RuntimeException`). Must be caught or declared (e.g., `IOException`).
- **Unchecked**: Subclasses of `RuntimeException`. Optional to handle (e.g., `NullPointerException`).

### Example
```java
import java.io.FileNotFoundException;

public class ThrowThrowsExample {
    public void processFile(String fileName) throws FileNotFoundException {
        if (!fileName.endsWith(".txt")) {
            throw new IllegalArgumentException("File must be .txt");
        }
        if (!fileName.equals("data.txt")) {
            throw new FileNotFoundException("File not found: " + fileName);
        }
        System.out.println("File processed.");
    }
    public static void main(String[] args) {
        ThrowThrowsExample example = new ThrowThrowsExample();
        try {
            example.processFile("image.jpg");
        } catch (FileNotFoundException | IllegalArgumentException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

### Interview Questions
- **Q: Difference between throw and throws?**  
  A: **throw**: Explicitly throws an exception. **throws**: Declares checked exceptions in method signature.
- **Q: Checked vs. unchecked exceptions?**  
  A: **Checked**: Compiler enforces handling (e.g., `IOException`). **Unchecked**: Optional handling, typically coding errors (e.g., `NullPointerException`).
- **Q: Can a method throw multiple exceptions?**  
  A: Yes, declare with `throws Exception1, Exception2`.

---

## Custom Exceptions
User-defined exceptions for specific error conditions.

### Why Use
- Specific error representation.
- Improved debugging and maintainability.

### Creation
- Extend `Exception` (checked) or `RuntimeException` (unchecked).
- Provide constructors: no-arg, message, cause.

### Example
```java
class InsufficientFundsException extends Exception {
    private double amount;
    public InsufficientFundsException(String message, double amount) {
        super(message);
        this.amount = amount;
    }
    public double getAmount() { return amount; }
}

class BankAccount {
    private double balance;
    public BankAccount(double balance) { this.balance = balance; }
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount <= 0) throw new IllegalArgumentException("Invalid amount");
        if (balance < amount) throw new InsufficientFundsException("Insufficient funds", amount);
        balance -= amount;
        System.out.println("Withdrew: " + amount);
    }
}

public class CustomExceptionExample {
    public static void main(String[] args) {
        BankAccount account = new BankAccount(500.0);
        try {
            account.withdraw(800.0);
        } catch (InsufficientFundsException e) {
            System.out.println(e.getMessage() + ": " + e.getAmount());
        }
    }
}
```

### Interview Questions
- **Q: When to create custom exceptions?**  
  A: For specific, domain-related errors to enhance clarity and error handling.
- **Q: Extend Exception or RuntimeException?**  
  A: **Exception** for checked exceptions (must handle). **RuntimeException** for unchecked (optional handling, coding errors).