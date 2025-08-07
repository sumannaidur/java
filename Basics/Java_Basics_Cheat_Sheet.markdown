# Java Basics Cheat Sheet
*August 07, 2025, 10:23 PM IST*

## Module 1: Java Basics
This cheat sheet covers the core concepts of Java, including its history, features, setup, basic syntax, data handling, and operations.

---

## What is Java?
Java is a high-level, class-based, object-oriented programming (OOP) language designed for platform independence with the motto "Write Once, Run Anywhere" (WORA). Developed by James Gosling at Sun Microsystems (now Oracle) in 1995.

### Key Features
- **Object-Oriented**: Supports Encapsulation, Inheritance, Polymorphism, and Abstraction.
- **Platform Independent (WORA)**: Java code compiles to bytecode, executable on any platform with a Java Virtual Machine (JVM).
- **Simple**: Syntax similar to C++ but removes complex features like pointers and multiple inheritance.
- **Secure**: JVM's bytecode verifier, security manager, and classloader ensure a secure runtime environment.
- **Robust**: Strong memory management (garbage collection), exception handling, and type-checking.
- **Multithreaded**: Supports concurrent execution for better performance.
- **High Performance**: Just-In-Time (JIT) compiler converts bytecode to native machine code at runtime.
- **Distributed**: Designed for network applications.
- **Dynamic**: Adapts to evolving environments by dynamically linking new classes and methods.

### Interview Questions
- **Q: What is Java? Explain its key features.**  
  A: Java is a high-level, object-oriented, platform-independent language. Key features: Object-Oriented, Platform Independent, Simple, Secure, Robust, Multithreaded, High Performance, Distributed, Dynamic.
- **Q: How does Java achieve platform independence?**  
  A: Java compiles source code (.java) to bytecode (.class), which runs on any platform with a JVM, eliminating the need for recompilation.
- **Q: Differentiate between JDK, JRE, and JVM.**  
  A:  
  - **JVM**: Executes bytecode, enabling WORA.  
  - **JRE**: Includes JVM and core libraries for running Java applications.  
  - **JDK**: Includes JRE and development tools (e.g., javac, debugger) for building Java applications.

---

## Setting up Java
To develop Java applications, set up the Java Development Kit (JDK) and an Integrated Development Environment (IDE).

### Steps
1. **JDK Installation**: Download and install JDK from Oracle or OpenJDK.
2. **Environment Variables**:
   - Set `JAVA_HOME` to the JDK installation directory.
   - Add JDK's `bin` directory to the system `PATH`.
3. **IDE Setup**:
   - **IntelliJ IDEA**: Offers intelligent code completion, refactoring, and debugging. Community (free) and Ultimate (paid) editions.
   - **Eclipse**: Open-source, customizable with plugins.
   - **VS Code**: Lightweight editor with Java extensions.

### Interview Questions
- **Q: Why set JAVA_HOME and PATH?**  
  A: `JAVA_HOME` helps tools locate the JDK. Adding `bin` to `PATH` allows running Java commands (e.g., `javac`, `java`) from any directory.
- **Q: Benefits of using an IDE over a text editor?**  
  A: IDEs provide code completion, syntax highlighting, error checking, debugging, refactoring, and version control integration, boosting productivity.

---

## First Java Program
A "Hello World" program introduces Java's basic structure.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

### Explanation
- **public class HelloWorld**: Defines a class named `HelloWorld`. All Java code resides in classes.
- **public static void main(String[] args)**: Entry point for the program.  
  - `public`: Accessible from anywhere.
  - `static`: Callable without an object.
  - `void`: No return value.
  - `main`: JVM's starting point.
  - `String[] args`: Holds command-line arguments.
- **System.out.println("Hello, Java!")**: Prints to console with a newline.

### Interview Questions
- **Q: Explain the `public static void main(String[] args)` signature.**  
  A: It’s the program’s entry point. `public` allows JVM access, `static` enables calling without an object, `void` indicates no return, `main` is the JVM-recognized method name, and `String[] args` captures command-line arguments.
- **Q: Purpose of `System.out.println()`?**  
  A: Prints output to the console with a newline. `System` is a class, `out` is a `PrintStream` object, and `println()` is its method.

---

## Input and Output
Java handles console I/O using `System.out` for output and `java.util.Scanner` for input.

### Output
- `System.out.print()`: Prints without a newline.
- `System.out.println()`: Prints with a newline.
- `System.out.printf()`: Formats output (e.g., `printf("Value: %d", 10)`).

### Input
Use `Scanner` to read user input.

```java
import java.util.Scanner;

public class UserInputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your name: ");
        String name = scanner.nextLine();
        System.out.print("Enter your age: ");
        int age = scanner.nextInt();
        System.out.println("Hello, " + name + "! You are " + age + " years old.");
        scanner.close();
    }
}
```

### Explanation
- `import java.util.Scanner`: Imports Scanner class.
- `Scanner scanner = new Scanner(System.in)`: Creates Scanner for keyboard input.
- `nextLine()`: Reads a string until newline.
- `nextInt()`: Reads an integer.
- `scanner.close()`: Releases resources.

### Interview Questions
- **Q: Difference between `System.out.print()` and `System.out.println()`?**  
  A: `print()` keeps the cursor on the same line; `println()` adds a newline.
- **Q: How to read user input in Java?**  
  A: Use `java.util.Scanner`. Create a `Scanner` object with `System.in`, use methods like `nextLine()`, `nextInt()`, and close it with `scanner.close()`.

---

## Data Types & Variables
Java is statically typed, requiring variables to have a declared type.

### Data Types
#### Primitive Types
- **Integer**: 
  - `byte` (1 byte, -128 to 127)
  - `short` (2 bytes, -32,768 to 32,767)
  - `int` (4 bytes, ~±2 billion, most used)
  - `long` (8 bytes, ~±9 quintillion, suffix `L`)
- **Floating-Point**:
  - `float` (4 bytes, single-precision, suffix `f`)
  - `double` (8 bytes, double-precision, most used)
- **Character**: `char` (2 bytes, Unicode, e.g., `'A'`)
- **Boolean**: `boolean` (true/false, ~1 bit)

#### Non-Primitive (Reference) Types
- Store references to objects (e.g., `String`, arrays, classes, interfaces).

### Variables
- **Declaration**: `dataType variableName;` (e.g., `int age;`)
- **Initialization**: `variableName = value;` (e.g., `age = 30;`)
- **Combined**: `dataType variableName = value;` (e.g., `String name = "Alice";`)

### Scope
- **Local Variables**: Declared in methods/blocks, limited scope, must be initialized.
- **Instance Variables**: Declared in a class, belong to objects, get default values.
- **Class (Static) Variables**: Declared with `static`, shared across all instances.

### Interview Questions
- **Q: What are Java’s data types?**  
  A: **Primitive**: `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`. **Non-Primitive**: `String`, arrays, classes, interfaces.
- **Q: Default values for primitive types?**  
  A: Numeric: `0` or `0.0`, `char`: `\u0000`, `boolean`: `false`. Local variables need explicit initialization.
- **Q: Types of variables by scope?**  
  A: **Local**: Method/block scope, no default value. **Instance**: Object-specific, default values. **Static**: Class-shared, default values.

---

## Type Casting
Converts a value from one data type to another.

### Types
- **Widening (Implicit)**: Smaller to larger type, automatic, no data loss.  
  Order: `byte` → `short` → `char` → `int` → `long` → `float` → `double`.  
  Example: `int x = 10; double y = x; // y = 10.0`
- **Narrowing (Explicit)**: Larger to smaller type, manual with `(type)`, potential data loss.  
  Example: `double d = 9.78; int i = (int) d; // i = 9`

### Interview Questions
- **Q: What is type casting?**  
  A: Converting a value from one data type to another, used when assigning incompatible types.
- **Q: Widening vs. narrowing casting?**  
  A: **Widening**: Automatic, smaller to larger type (e.g., `int` to `double`). **Narrowing**: Manual, larger to smaller type with potential data loss (e.g., `double d = 10.75; int i = (int) d; // i = 10`).

---

## Operators
Symbols that perform operations on operands.

### Types
- **Arithmetic**: `+`, `-`, `*`, `/`, `%` (e.g., `int sum = 10 + 5;`)
- **Assignment**: `=`, `+=`, `-=`, `*=`, `/=`, `%=` (e.g., `x += 5; // x = x + 5`)
- **Relational**: `==`, `!=`, `>`, `<`, `>=`, `<=` (e.g., `boolean isEqual = (a == b);`)
- **Logical**: `&&` (AND), `||` (OR), `!` (NOT) (e.g., `if (age > 18 && hasLicense)`)
- **Unary**: `+`, `-`, `++`, `--` (e.g., `int x = 5; int y = ++x; // y = 6, x = 6`)
- **Bitwise**: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>` (e.g., `int result = 5 & 3; // 1`)
- **Ternary**: `condition ? valueIfTrue : valueIfFalse` (e.g., `String status = (age >= 18) ? "Adult" : "Minor";`)
- **instanceof**: Checks object type (e.g., `if (obj instanceof String)`)

### Precedence
Higher precedence: `*`, `/`, `%` > `+`, `-`. Use `()` to override.

### Interview Questions
- **Q: Difference between `==` and `.equals()`?**  
  A: `==` compares primitive values or object references. `.equals()` compares object content (e.g., `String` characters).
- **Q: Pre-increment vs. post-increment?**  
  A: `++x`: Increments first, then uses value. `x++`: Uses value, then increments.
- **Q: Purpose of the ternary operator?**  
  A: Concise if-else. Example: `String result = (score >= 60) ? "Pass" : "Fail";`
