Below is a **very detailed** set of notes based on the provided document, covering every topic comprehensively without omitting any content. The notes are structured for clarity, with in-depth explanations, examples, and additional context to ensure a thorough understanding. The content is organized hierarchically, with clear headings, subheadings, and code snippets where applicable.

---

# Comprehensive Java Programming Notes

## 1. Setting Up the Java Development Environment

### 1.1 Where to Write Java Programs
Java programs can be written using various tools, each suited to different levels of complexity and user expertise:

- **Text Editors**:
  - Basic tools that accept plain text input, including uppercase/lowercase letters, numbers, and special symbols.
  - **Examples**:
    - **Notepad**: Default text editor on Windows, simple but lacks advanced features.
    - **TextEdit**: Default on Mac OS, suitable for basic coding but not optimized for programming.
  - Suitable for beginners or quick edits but lacks syntax highlighting or debugging support.

- **Rich Text Editors**:
  - Enhanced editors with language-specific features like syntax highlighting, code completion, and error detection.
  - Differentiate keywords, variables, and other components with colors for better readability.
  - **Examples**:
    - **Notepad++**: Popular on Windows, lightweight, supports multiple languages.
    - **Sublime Text**: Cross-platform, highly customizable, fast, and widely used.
    - **Atom**: Open-source, modern, with extensive plugin support for Java development.
  - Ideal for intermediate users who need more features than basic text editors but prefer lightweight tools.

- **Integrated Development Environments (IDEs)**:
  - Comprehensive tools used by professional developers, offering advanced features like code debugging, project management, and integrated testing.
  - **Popular IDEs for Java**:
    - **Eclipse**: Most popular in this course, open-source, robust, with extensive plugins for Java development.
    - **IntelliJ IDEA**: Industry-standard, known for intelligent code assistance and productivity features.
    - **VS Code (Visual Studio Code)**: Lightweight, highly customizable with Java extensions.
    - **NetBeans**: Open-source, user-friendly, with built-in support for Java projects.
  - Recommended for large projects or professional development due to their all-in-one capabilities.

### 1.2 Saving Java Programs
- **File Extension**: Java source files must be saved with the `.java` extension (e.g., `First.java`).
  - The file name must exactly match the name of the `public class` defined in the file (case-sensitive).
- **Storage Location**: Saved in secondary memory (e.g., hard drive, SSD) on your machine for persistence.
  - Can be stored in any directory, but the directory path is needed for compilation and execution.
- **Example**: A program with `public class First` must be saved as `First.java`.

### 1.3 Installing Java
- **Authentic Source**:
  - Java is owned by Oracle.
  - Download from [oracle.com/java](http://oracle.com/java).
- **Java Development Kit (JDK)**:
  - Essential for Java development, includes:
    - **Java Compiler** (`javac`): Converts source code to bytecode.
    - **Java Interpreter** (`java`): Runs bytecode via the JVM.
    - **Java Runtime Environment (JRE)**: Includes JVM and Java API.
    - Tools like `javap` (bytecode viewer), debugger, and documentation generators.
  - **Versions**:
    - Common versions include Java 20, Java 17 (Long-Term Support), Java 11, Java 8.
    - New versions released every six months (e.g., Java 21 in September 2023, Java 22 in March 2024).
  - **Installation**:
    - Download the installer for your operating system (Linux, Mac, Windows).
    - The installer typically sets the system path automatically, allowing commands like `javac` and `java` to work globally.
- **Verifying Installation**:
  - Open Terminal (Mac/Linux) or Command Prompt (Windows).
  - Check compiler: `javac -version` (e.g., outputs `javac 17`).
  - Check runtime: `java -version` (e.g., outputs `openjdk 17.0.x`).
  - If commands fail, ensure the JDK’s `bin` directory is added to the system’s PATH environment variable.

### 1.4 Executing Java Programs
Java programs undergo a two-step process: **compilation** and **interpretation**.

- **Compilation**:
  - **Purpose**: Translates high-level Java source code (`.java` file) into platform-independent bytecode (`.class` file).
  - **Command**: `javac YourProgramName.java` (e.g., `javac First.java`).
  - **Process**:
    - The Java compiler (`javac`) checks for syntax errors.
    - If no errors, it generates a `.class` file in the same directory.
    - The `.class` file contains bytecode, an intermediate representation executable by the JVM.
  - **Example**: `javac First.java` produces `First.class`.

- **Interpretation**:
  - **Purpose**: The Java Virtual Machine (JVM) executes the bytecode line by line.
  - **Command**: `java YourProgramName` (e.g., `java First`).
    - Do not include the `.class` extension in the command.
  - **Process**:
    - The JVM’s interpreter component reads the `.class` file and executes it.
    - Requires the JRE to be installed on the target machine.
  - **Output**: Displays the program’s result (e.g., `Hello World` on the console).

- **Viewing Bytecode (Optional)**:
  - **Command**: `javap YourProgramName.class` (e.g., `javap First.class`).
    - Displays class details like methods and constructors.
  - **Detailed Bytecode**: `javap -c YourProgramName.class`.
    - Shows low-level bytecode instructions, useful for debugging or understanding JVM operations.
  - **Use Case**: Inspect default constructors, `main` method structure, or other class details.

## 2. Anatomy of a First Java Program
Here’s a detailed breakdown of a simple Java program:
```java
public class First {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

### 2.1 Components
- **Class Declaration**:
  - `public class First`:
    - `public`: Access modifier, makes the class accessible everywhere.
    - `class`: Keyword to define a class.
    - `First`: Class name, must match the file name (`First.java`).
  - A Java program is a collection of classes; at least one must be `public` and contain the `main` method.

- **Main Method**:
  - `public static void main(String[] args)`:
    - **Entry Point**: The JVM starts execution here.
    - `public`: Ensures the JVM can access the method from any location.
    - `static`: Method belongs to the class, not an object; no instantiation needed.
    - `void`: Indicates the method returns no value.
    - `main`: Required name for the program’s entry point.
    - `String[] args`: Parameter to accept command-line arguments as an array of strings.
  - Without a `main` method, the program cannot execute.

- **Print Statement**:
  - `System.out.println("Hello World")`:
    - `System`: A predefined class in the `java.lang` package (automatically imported).
    - `out`: A static `PrintStream` object in `System`, representing the console.
    - `println()`: A method of `PrintStream` that prints a string followed by a newline.
    - `"Hello World"`: A string literal enclosed in double quotes.

### 2.2 Key Points
- **Class Structure**: Every Java program consists of one or more classes.
- **Main Requirement**: At least one class must contain a `main` method to serve as the program’s entry point.
- **String Literals**: Enclosed in double quotes (`"..."`).
- **Naming Conventions**:
  - **Classes/Interfaces**: CamelCase with initial uppercase (e.g., `HelloWorld`).
  - **Methods/Variables**: CamelCase with initial lowercase (e.g., `calculateSum`, `firstName`).
- **Code Blocks**: Defined by curly braces `{}` for classes, methods, etc.
- **Parentheses**: Used for method arguments (e.g., `main(String[] args)`).
- **Square Brackets**: Used for arrays (e.g., `String[]`).
- **Semicolon**: Terminates statements (not blocks).
- **Comments**:
  - Single-line: `// comment`.
  - Multi-line: `/* comment */`.
- **Packages**: Organize classes (e.g., `java.lang` for `System`, `String`).
  - `java.lang` is auto-imported; others require explicit `import` statements.

### 2.3 Steps to Run a Java Program
1. **Write Code**: Use a text editor, rich text editor, or IDE.
2. **Save File**: Save as `ProgramName.java`, matching the `public class` name.
3. **Open Terminal/Command Prompt**: Navigate to the file’s directory using `cd`.
4. **Compile**: Run `javac ProgramName.java` to generate `ProgramName.class`.
5. **Execute**: Run `java ProgramName` to display output (e.g., `Hello World`).

## 3. Java Execution Flow
Java’s platform-independent execution model involves compilation and interpretation:

- **Source Code (`.java`)**:
  - Written in high-level, human-readable Java.
  - Created using text editors, rich text editors, or IDEs.
  - Saved with `.java` extension, matching the `public class` name.

- **Compilation**:
  - **Tool**: `javac` compiler.
  - **Process**:
    - Checks for syntax errors (e.g., missing semicolons, incorrect declarations).
    - Translates `.java` file to `.class` bytecode.
    - Bytecode is platform-independent, enabling Java’s "Write Once, Run Anywhere" (WORA) principle.
  - **Output**: A `.class` file in the same directory.

- **Bytecode (`.class`)**:
  - Optimized binary code, executable on any machine with a JVM.
  - Allows code compiled on one OS (e.g., Mac) to run on another (e.g., Windows).

- **Interpretation**:
  - **Tool**: JVM’s interpreter (via `java` command).
  - **Process**:
    - Reads and executes `.class` bytecode line by line.
    - Requires JRE (JVM + Java API) on the target machine.
  - **Output**: Program results displayed on the console.

### 3.1 JDK vs. JRE
- **Java Development Kit (JDK)**:
  - Complete development kit for programmers.
  - Includes:
    - **Language & Tools**: Compiler (`javac`), interpreter (`java`), `javap`, debugger, etc.
    - **JRE**: For running Java applications.
  - Required for compiling, running, testing, and debugging.

- **Java Runtime Environment (JRE)**:
  - Subset of JDK, for end-users to run Java programs.
  - Includes:
    - **JVM**: Executes bytecode.
    - **Java API**: Pre-written classes/libraries (e.g., `System`, `String`).
  - Does not include development tools like `javac`.

### 3.2 Main Method Signature Breakdown
```java
public static void main(String[] args)
```
- **public**: Allows JVM to call `main` from any location.
- **static**: Enables direct invocation without creating a class instance.
  - Without `static`, the JVM would need an object, complicating startup.
- **void**: No return value; `main` simply executes.
- **main**: Standard name for the program’s entry point.
- **String[] args**: Array to capture command-line arguments.
  - `String[]`: Array of strings.
  - `args`: Conventional name (can be any valid identifier).

### 3.3 System.out.println
- **System**: Class in `java.lang`, providing I/O utilities.
- **out**: Static `PrintStream` object for console output.
- **println()**: Prints argument and adds a newline.
- **java.lang**: Automatically imported, contains core classes like `System`, `String`.

### 3.4 Additional Program Elements
- **Blocks**: `{}` group statements for classes, methods, etc.
- **Parentheses**: `()` enclose method parameters.
- **Square Brackets**: `[]` denote arrays.
- **Semicolon**: `;` terminates statements (not required for blocks).
- **Keywords**: 53 reserved words (e.g., `public`, `class`, `static`, `void`).
  - Cannot be used as identifiers.
- **Comments**:
  - Improve code readability, ignored by compiler.
  - Single-line: `// This is a comment`.
  - Multi-line: `/* This spans multiple lines */`.
- **Packages**:
  - Group related classes/interfaces to avoid naming conflicts.
  - Example: `java.lang` for `System`, `String`.
  - Explore Java API at [oracle.com/java](http://oracle.com/java) for package details.

## 4. Command-Line Arguments
- **Definition**: Values passed to a program at runtime via the command line.
  - Example: `java First Asdf 123 456` passes `Asdf`, `123`, `456` as arguments.
- **Access**: Captured in `main`’s `String[] args` parameter.
  - `args[0]`: First argument (`Asdf`).
  - `args[1]`: Second argument (`123`), etc.
  - `args.length`: Number of arguments passed.

### 4.1 Example: Reading a Name
```java
public class Name {
    public static void main(String[] args) {
        if (args.length > 0) {
            System.out.println("Your good name is: " + args[0]);
        } else {
            System.out.println("Please provide your name as a command-line argument.");
        }
    }
}
```
- **Compile**: `javac Name.java`
- **Run**:
  - `java Name John` → `Your good name is: John`
  - `java Name` → `Please provide your name as a command-line argument.`

### 4.2 Handling Multiple Arguments
- Arguments are `String`; convert for numeric operations.
- **Example**: Sum two numbers.
```java
public class Add {
    public static void main(String[] params) {
        int num1 = Integer.parseInt(params[0]);
        int num2 = Integer.parseInt(params[1]);
        int sum = num1 + num2;
        System.out.println("Sum of " + num1 + " and " + num2 + " is: " + sum);
    }
}
```
- **Run**: `java Add 123 321` → `Sum of 123 and 321 is: 444`.
- **Notes**:
  - `Integer.parseInt()`: Converts `String` to `int`.
  - Concatenation: `args[0] + args[1]` joins strings (e.g., `"10" + "20" = "1020"`).
  - Other conversions: `Double.parseDouble()`, `Float.parseFloat()`.

### 4.3 Variable Number of Arguments
- Use `args.length` to handle any number of arguments.
- **Example**: Sum multiple numbers.
```java
public class Add {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 0; i < args.length; i++) {
            sum += Integer.parseInt(args[i]);
        }
        System.out.println("Sum of all " + args.length + " numbers is: " + sum);
    }
}
```
- **Run**:
  - `java Add 1 2 3 4 5` → `Sum of all 5 numbers is: 15`
  - `java Add 100 200 300` → `Sum of all 3 numbers is: 600`
  - `java Add` → `Sum of all 0 numbers is: 0`
- **Error Handling**:
  - Accessing `args[i]` beyond `args.length` causes `ArrayIndexOutOfBoundsException`.
  - Validate `args.length` before accessing elements.

## 5. Basic Programming Constructs
### 5.1 Analogy: Natural vs. Programming Language
| Feature | Natural Language (e.g., English) | Programming Language (e.g., Java) |
|---------|----------------------------------|------------------------------------|
| Basic Units | Alphabets (A-Z, a-z, 0-9) | Character Set (Unicode) |
| Words | Words (e.g., Apple, Dog) | Identifiers |
| Grammar | Sentence formation rules | Operators & Expressions |
| Sentences | Meaningful sentences | Statements/Instructions |
| Paragraphs | Group of sentences | Programs (Sequential code) |
| Flow Control | N/A | Control Statements (Selection, Looping, Jump) |

### 5.2 Constructs Overview
1. **Character Set**: Defines valid characters.
2. **Identifiers**: Named program elements.
3. **Operators & Expressions**: Perform operations.
4. **Control Statements**: Manage execution flow (selection, looping, jump).

## 6. Character Set in Java
- **Definition**: The set of valid characters for Java source code.
- **Java’s Charset**: 16-bit Unicode, supporting 65,536 characters (indices 0 to 65,535).
  - Enables multilingual support (e.g., Hindi, Arabic, Chinese).
  - Includes:
    - Uppercase letters (A-Z).
    - Lowercase letters (a-z).
    - Digits (0-9).
    - Special symbols (e.g., `@`, `#`, `$`, `%`, `&`, `*`, `_`, etc.).
  - Unicode standard ensures consistent text encoding across languages.

- **Comparison with C**:
  - C uses 7-bit ASCII (128 characters, 0-127).
  - Extended ASCII (8-bit, 256 characters) is non-standard.
  - Unicode preserves ASCII values (0-127 identical in both).

- **ASCII Breakdown** (0-127):
  - **Alphabets** (52):
    - Uppercase: A-Z (65-90).
    - Lowercase: a-z (97-122).
  - **Digits** (10): 0-9 (48-57).
  - **Printable Special Characters** (32): `!` (33), `@` (64), `#`, `$`, etc.
  - **Non-Printable Control Characters** (34): NULL (0), Tab (9), Newline (10), etc.
  - Total: 52 + 10 + 32 + 34 = 128.

### 6.1 Example: Printing ASCII/Unicode Characters
```java
public class Ascii {
    public static void main(String[] args) {
        // Capital Alphabets
        System.out.println("Capital Alphabets (A-Z):");
        for (int i = 65; i <= 90; i++) {
            System.out.print((char) i + " ");
        }
        // Lowercase Alphabets
        System.out.println("\nSmall Alphabets (a-z):");
        for (int i = 97; i <= 122; i++) {
            System.out.print((char) i + " ");
        }
        // Digits
        System.out.println("\nDigits (0-9):");
        for (int i = 48; i <= 57; i++) {
            System.out.print((char) i + " ");
        }
        // Printable ASCII
        System.out.println("\nPrintable ASCII (33-126):");
        for (int i = 33; i <= 126; i++) {
            System.out.print(i + ":" + (char) i + "   ");
            if ((i - 32) % 10 == 0) System.out.println();
        }
    }
}
```
- **Output**:
  ```
  Capital Alphabets (A-Z):
  A B C ... Z
  Small Alphabets (a-z):
  a b c ... z
  Digits (0-9):
  0 1 2 ... 9
  Printable ASCII (33-126):
  33:!   34:"   35:#   ... (formatted in rows)
  ```
- **Notes**:
  - `(char) i`: Casts integer to corresponding Unicode/ASCII character.
  - Non-printable characters (0-32, 127) may appear as blanks or symbols.

## 7. Identifiers in Java
- **Definition**: Named tokens used to label program elements (e.g., variables, classes, methods).
- **Examples** (from `public class First`):
  - Keywords: `public`, `class`, `static`, `void`.
  - Class name: `First`.
  - Method name: `main`.
  - Variable: `args`.
  - Classes: `System`, `String`.
  - Field: `out`.
  - Method: `println`.
  - Literal: `"Hello Java"`.

### 7.1 Types of Identifiers
- **Variables**: Store mutable data (e.g., `int x = 10`).
- **Constants**: Store immutable data (e.g., `final double PI = 3.14`).
- **Keywords**: 53 reserved words with predefined meanings (e.g., `public`, `if`, `final`).
- **Data Types**: `int`, `double`, `boolean`, etc.
- **Classes/Methods/Interfaces/Packages/Enums**: User-defined or predefined names.
- **Literals**: Fixed values (e.g., `"Hello"`, `10`).

### 7.2 Rules for Identifiers
1. **Allowed Characters**:
   - Letters (A-Z, a-z), digits (0-9), underscore (`_`), dollar sign (`$`).
   - No other special characters (e.g., `@`, `#`, `%`).
2. **Starting Character**: Must begin with a letter, `_`, or `$` (not a digit).
   - Valid: `_name`, `$price`, `data123`.
   - Invalid: `1name`.
3. **No White Spaces**: Use camelCase or underscores (e.g., `firstName`, `first_name`).
   - Invalid: `first name`.
4. **Case-Sensitivity**: `age`, `Age`, `AGE` are distinct.
5. **No Keywords**: Cannot use reserved words (e.g., `class`, `public`).
6. **Length**: No practical limit.
- **Valid Examples**: `myVariable`, `user_id`, `$amount`, `_temp`.
- **Invalid Examples**: `1stName`, `my variable`, `total-price`, `public`.

### 7.3 Variables
- **Purpose**: Store data that can change during execution.
- **Type Requirement**: Java is strongly-typed; variables must have a declared type.
  - Example: `int age;`, `double salary;`, `String name;`.
- **Operations**:
  - **Declaration**: Define name and type (e.g., `int age;`).
  - **Initialization**: Assign initial value (e.g., `int age = 21;`).
  - **Assignment**: Update value (e.g., `age = 18;`).
- **Mutability**: Variables can change (e.g., `x = 10; x = x + 5;`).

### 7.4 Constants
- **Purpose**: Store data that remains unchanged.
- **Declaration**: Use `final` keyword (e.g., `final double PI = 3.14159;`).
  - Attempting to modify a `final` variable causes a compile-time error.
- **Naming Convention**: Uppercase with underscores (e.g., `MAX_AGE`, `INTEREST_RATE`).
- **Example**:
```java
public class MyConstants {
    public static void main(String[] args) {
        final double PI = 3.14159;
        System.out.println("Value of PI: " + PI);
        // PI = 3.14; // Error: cannot assign to final variable
    }
}
```

## 8. Data Types in Java
- **Categories**:
  - **Primitive**: Basic types, not objects.
  - **Reference**: Class-based types (e.g., `String`), store memory addresses.

### 8.1 Primitive Data Types
Java defines eight primitive types, categorized by data kind:

| Category | Type | Size (Bytes) | Bits | Range | Default Value | Default Literal Type |
|----------|------|--------------|------|-------|---------------|---------------------|
| **Integer** | `byte` | 1 | 8 | -128 to 127 | 0 | `int` |
| | `short` | 2 | 16 | -32,768 to 32,767 | 0 | `int` |
| | `int` | 4 | 32 | ±2.1 billion | 0 | `int` |
| | `long` | 8 | 64 | ±9 quintillion | 0L | `int` (use `L`) |
| **Floating-Point** | `float` | 4 | 32 | ±3.4×10³⁸ (7 digits precision) | 0.0f | `double` (use `f`) |
| | `double` | 8 | 64 | ±1.7×10³⁰⁸ (15 digits precision) | 0.0d | `double` |
| **Character** | `char` | 2 | 16 | 0 to 65,535 (Unicode) | `` | N/A |
| **Boolean** | `boolean` | ~1 | ~1 | `true`, `false` | `false` | N/A |

### 8.2 Key Characteristics
- **Signed**: All numeric types (except `char`) are signed, using one bit for sign.
- **Fixed Size**: Ensures platform independence (unlike C/C++).
- **Default Values**:
  - Integers: `0`.
  - Floating-point: `0.0`.
  - `char`: `` (null character).
  - `boolean`: `false`.
- **Default Literal Types**:
  - Integer literals (e.g., `100`) are `int`.
  - Floating-point literals (e.g., `3.14`) are `double`.
- **Conversions**:
  - **Implicit Narrowing**: Allowed for literals within range (e.g., `byte b = 100;`).
  - **Explicit Casting**: Required for operations producing larger types (e.g., `byte b = (byte)(100 + 25);`).
  - **Example**:
```java
public class IntegerTypes {
    public static void main(String[] args) {
        byte b = 100; // OK: within range
        byte b2 = (byte)(b + 25); // Cast required: int to byte
        System.out.println("b2: " + b2); // 125
    }
}
```
```java
public class FloatDoubleTypes {
    public static void main(String[] args) {
        float f = 3.14f; // 'f' required
        double d = 3.14; // OK
        f = f + 0.5f; // OK
        System.out.println("f: " + f); // 3.64
    }
}
```

## 9. Operators in Java
- **Definition**: Symbols that perform operations on operands (data).
- **Example**: In `C = A + B;`, `+` and `=` are operators; `A`, `B`, `C` are operands.

### 9.1 Categories by Operands
1. **Unary**: One operand (e.g., `++x`, `!flag`).
2. **Binary**: Two operands (e.g., `A + B`, `x == y`).
3. **Ternary**: Three operands (e.g., `x > y ? x : y`).

### 9.2 Properties
- **Precedence**: Determines evaluation order.
  - Highest: Parentheses `()`.
  - Order: Unary > Multiplicative (`*`, `/`, `%`) > Additive (`+`, `-`) > Relational > Equality > Bitwise > Logical > Ternary > Assignment.
- **Associativity**: Direction for same-precedence operators.
  - **Left-to-Right**: Most operators (e.g., `A + B - C` → `(A + B) - C`).
  - **Right-to-Left**: Assignment (`=`), unary, ternary.

### 9.3 Types of Operators
1. **Assignment**: `=`, `+=`, `-=`, `*=`, `/=`, `%=`.
2. **Arithmetic**: `+`, `-`, `*`, `/`, `%`.
3. **Relational**: `>`, `<`, `>=`, `<=`, `==`, `!=`.
4. **Logical**: `&&`, `||`, `!`.
5. **Bitwise**: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`.
6. **Increment/Decrement**: `++`, `--`.
7. **Ternary**: `?:`.

### 9.4 Arithmetic Operators
- **Multiplicative** (`*`, `/`, `%`): Higher precedence, left-to-right.
- **Additive** (`+`, `-`): Lower precedence, left-to-right.
- **Integer Division**: Truncates decimal (e.g., `10 / 3 = 3`).
- **Modulus**: Returns remainder (e.g., `10 % 3 = 1`).
- **Division by Zero**:
  - Integer: Throws `ArithmeticException`.
  - Floating-point: Returns `Infinity` or `NaN`.
- **Example**:
```java
public class TestOperators {
    public static void main(String[] args) {
        int x = 10, y = 3;
        if (y != 0) {
            System.out.println("x / y: " + (x / y)); // 3
            System.out.println("x % y: " + (x % y)); // 1
        }
        double fX = 10.0, fY = 0.0;
        System.out.println("fX / fY: " + (fX / fY)); // Infinity
    }
}
```

### 9.5 Relational Operators
- Return `boolean` (`true`/`false`).
- **Comparison**: `>`, `<`, `>=`, `<=`.
- **Equality**: `==`, `!=`.
- **Use Case**: Conditions in `if`, `while`, etc.

### 9.6 Assignment Operators
- **Simple**: `=` (e.g., `x = 5`).
- **Compound**: `+=`, `-=`, `*=`, `/=`, `%=` (e.g., `x += 3` → `x = x + 3`).

### 9.7 Increment/Decrement Operators
- **Increment**: `++` (e.g., `x++`, `++x`).
- **Decrement**: `--` (e.g., `x--`, `--x`).
- **Prefix**: Changes value before use (e.g., `++x`).
- **Postfix**: Uses value, then changes (e.g., `x++`).
- **Example**:
```java
public class IncDecDemo {
    public static void main(String[] args) {
        int x = 5;
        System.out.println("x++: " + (x++)); // 5
        System.out.println("x: " + x); // 6
        System.out.println("++x: " + (++x)); // 7
    }
}
```

### 9.8 Ternary Operator
- Syntax: `condition ? valueIfTrue : valueIfFalse`.
- **Example**:
```java
int max = (a > b) ? a : b; // Assigns larger value to max
```

### 9.9 Logical Operators
- **Short-Circuit**:
  - `&&`: True if both operands are true; skips second if first is false.
  - `||`: True if either operand is true; skips second if first is true.
- **NOT**: `!` (inverts boolean).
- **Example**:
```java
boolean a = true, b = false;
System.out.println(a && b); // false
System.out.println(a || b); // true
System.out.println(!a); // false
```

### 9.10 Bitwise Operators
- Operate on bits of integers:
  - `&` (AND), `|` (OR), `^` (XOR), `~` (NOT).
  - `<<` (Left Shift), `>>` (Signed Right Shift), `>>>` (Unsigned Right Shift).
- **Example**:
```java
int a = 5; // 0101
int b = 3; // 0011
System.out.println("a & b: " + (a & b)); // 0001 = 1
System.out.println("a << 1: " + (a << 1)); // 1010 = 10
```

## 10. Control Statements
Control statements manage program flow through selection, looping, and jumps.

### 10.1 Selection Statements
#### 10.1.1 if Statement
- **Purpose**: Executes code based on a boolean condition.
- **Forms**:
  - **Simple if**:
```java
if (a > b) {
    System.out.println("A is greater");
}
```
  - **if-else**:
```java
if (number >= 0) {
    System.out.println("Positive or Zero");
} else {
    System.out.println("Negative");
}
```
  - **Nested if-else**:
```java
if (score >= 90) {
    System.out.println("Grade A");
} else if (score >= 80) {
    System.out.println("Grade B");
} else {
    System.out.println("Grade C");
}
```
  - **else-if Ladder**:
    - Checks multiple conditions sequentially.
    - Executes first true block, skips rest; optional `else` for no matches.
```java
import java.util.Random;
public class GradeCalculator {
    public static void main(String[] args) {
        Random random = new Random();
        int marks = random.nextInt(100) + 1;
        System.out.println("Marks Generated: " + marks);
        if (marks >= 85) {
            System.out.println("Grade: A+");
        } else if (marks >= 70) {
            System.out.println("Grade: A");
        } else if (marks >= 60) {
            System.out.println("Grade: B");
        } else if (marks >= 50) {
            System.out.println("Grade: C");
        } else if (marks >= 40) {
            System.out.println("Grade: D");
        } else {
            System.out.println("Grade: Fail");
        }
    }
}
```

#### 10.1.2 switch Statement
- **Purpose**: Multi-way selection based on a single expression.
- **Expression Types**: `byte`, `short`, `int`, `char`, `String` (since Java 7), `enum`.
- **Keywords**:
  - `case`: Matches specific value.
  - `break`: Exits switch to prevent fall-through.
  - `default`: Handles unmatched cases (optional).
- **Fall-through**: Without `break`, execution continues to next case.
- **Example**: Day name converter (integer).
```java
public class DayNameConverter {
    public static void main(String[] args) {
        if (args.length == 0) {
            System.out.println("Provide a day number (1-7).");
            return;
        }
        int dayNumber = Integer.parseInt(args[0]);
        System.out.print("Day " + dayNumber + " is: ");
        switch (dayNumber) {
            case 1: System.out.println("Monday"); break;
            case 2: System.out.println("Tuesday"); break;
            case 3: System.out.println("Wednesday"); break;
            case 4: System.out.println("Thursday"); break;
            case 5: System.out.println("Friday"); break;
            case 6: System.out.println("Saturday"); break;
            case 7: System.out.println("Sunday"); break;
            default: System.out.println("Enter 1-7 only.");
        }
    }
}
```
- **Example**: Favorite color (String).
```java
public class FavoriteColor {
    public static void main(String[] args) {
        if (args.length == 0) {
            System.out.println("Provide a color (red, green, blue).");
            return;
        }
        String color = args[0].toLowerCase();
        System.out.print("You entered '" + args[0] + "'. ");
        switch (color) {
            case "red": System.out.println("Roses are red!"); break;
            case "green": System.out.println("Earth is green!"); break;
            case "blue": System.out.println("Sky is blue!"); break;
            default: System.out.println("Enter RGB colors only.");
        }
    }
}
```
- **Example**: Grading with fall-through.
```java
import java.util.Random;
public class GradeCalculatorSwitch {
    public static void main(String[] args) {
        Random random = new Random();
        int marks = random.nextInt(101);
        System.out.println("Marks: " + marks);
        int marksForSwitch = marks / 10;
        System.out.print("Grade: ");
        switch (marksForSwitch) {
            case 10: case 9: System.out.println("A+"); break;
            case 8: case 7: System.out.println("A"); break;
            case 6: System.out.println("B"); break;
            case 5: System.out.println("C"); break;
            case 4: System.out.println("D"); break;
            case 3: case 2: case 1: case 0: System.out.println("Fail"); break;
            default: System.out.println("Invalid Marks");
        }
    }
}
```

### 10.2 Looping Statements
#### 10.2.1 while Loop (Entry-Controlled)
- **Syntax**:
```java
initialization;
while (condition) {
    // body
    update;
}
```
- **Characteristics**:
  - Checks condition before body execution.
  - May execute zero times if condition is initially false.
  - Risk of infinite loop if update doesn’t make condition false.
- **Example**: Print 1 to 10.
```java
public class LoopDemo {
    public static void main(String[] args) {
        int i = 1;
        while (i <= 10) {
            System.out.println(i);
            i++;
        }
    }
}
```

#### 10.2.2 do-while Loop (Exit-Controlled)
- **Syntax**:
```java
initialization;
do {
    // body
    update;
} while (condition);
```
- **Characteristics**:
  - Executes body at least once.
  - Checks condition after body.
  - Requires semicolon after `while`.
- **Example**: Print 10 to 1.
```java
int x = 10;
do {
    System.out.println(x);
    x--;
} while (x >= 1);
```

#### 10.2.3 for Loop (Entry-Controlled)
- **Syntax**:
```java
for (initialization; condition; update) {
    // body
}
```
- **Characteristics**:
  - Combines initialization, condition, and update in one line.
  - Ideal for known iteration counts.
- **Example**: Even/odd numbers.
```java
public class ForLoopDemo {
    public static void main(String[] args) {
        System.out.println("Even Numbers (0-50):");
        for (int i = 0; i <= 50; i += 2) {
            System.out.print(i + " ");
        }
        System.out.println("\nOdd Numbers (1-50):");
        for (int x = 1; x <= 50; x += 2) {
            System.out.print(x + " ");
        }
    }
}
```
- **Example**: Multiplication table.
```java
import java.util.Random;
public class MathTableGenerator {
    public static void main(String[] args) {
        Random rand = new Random();
        int number = rand.nextInt(90) + 11;
        System.out.println("Table for: " + number);
        for (int i = 1; i <= 10; i++) {
            System.out.println(number + " * " + i + " = " + (number * i));
        }
    }
}
```

#### 10.2.4 for-each Loop (Enhanced for Loop)
- **Syntax**:
```java
for (DataType item : collectionOrArray) {
    // body
}
```
- **Characteristics**:
  - Simplifies iteration over arrays/collections.
  - No explicit index; cannot skip/reverse.
- **Example**: Array iteration.
```java
public class ForEachDemo {
    public static void main(String[] args) {
        int[] numbers = {10, 25, 30, 45, 50, 65, 70, 85, 90, 100};
        System.out.println("Array Size: " + numbers.length);
        for (int num : numbers) {
            System.out.print(num + " ");
        }
    }
}
```

#### 10.2.5 Prime Number Check (while)
```java
import java.util.Random;
public class PrimeNumberChecker {
    public static void main(String[] args) {
        Random rand = new Random();
        int number = rand.nextInt(99) + 2;
        System.out.println("Checking: " + number);
        int i = 1, count = 0;
        while (i <= number) {
            if (number % i == 0) count++;
            i++;
        }
        if (count == 2) {
            System.out.println(number + " is prime.");
        } else {
            System.out.println(number + " is NOT prime.");
        }
    }
}
```

### 10.3 Jump Statements
#### 10.3.1 break
- **Purpose**:
  - Exits innermost loop or switch.
  - Prevents fall-through in switch.
- **Example**: Stop at 50.
```java
public class BreakDemo {
    public static void main(String[] args) {
        for (int i = 5; i <= 100; i += 5) {
            if (i >= 50) break;
            System.out.print(i + " ");
        }
    }
}
```
- **Example**: Optimized prime check.
```java
import java.util.Random;
public class OptimizedPrimeChecker {
    public static void main(String[] args) {
        Random rand = new Random();
        int number = rand.nextInt(99) + 2;
        System.out.println("Checking: " + number);
        int count = 0;
        for (int i = 2; i <= number / 2; i++) {
            if (number % i == 0) {
                count++;
                break;
            }
        }
        if (number > 1 && count == 0) {
            System.out.println(number + " is prime.");
        } else {
            System.out.println(number + " is NOT prime.");
        }
    }
}
```

#### 10.3.2 continue
- **Purpose**: Skips rest of current loop iteration, proceeds to next.
- **Example**: Skip 26-40.
```java
public class ContinueDemo {
    public static void main(String[] args) {
        for (int i = 1; i <= 50; i++) {
            if (i > 25 && i <= 40) continue;
            System.out.print(i + " ");
        }
    }
}
```
- **Example**: Print alphabets, skip special characters.
```java
public class AlphaPrinter {
    public static void main(String[] args) {
        for (int i = 65; i <= 122; i++) {
            if (i > 90 && i < 97) continue;
            System.out.print((char) i + " ");
        }
    }
}
```

#### 10.3.3 return
- **Purpose**:
  - Exits method, optionally returns value.
  - In `main`, exits program.
- **Example**: Prevent division by zero.
```java
import java.util.Random;
public class ReturnDemo {
    public static void main(String[] args) {
        Random rand = new Random();
        int n1 = rand.nextInt(10);
        int n2 = rand.nextInt(10);
        System.out.println("N1=" + n1 + ", N2=" + n2);
        if (n2 == 0) {
            System.err.println("Cannot divide by zero.");
            return;
        }
        int result = n1 / n2;
        System.out.println("Result: " + result);
    }
}
```

## 11. Conclusion
- **Foundation**: These notes cover the essentials of Java programming, including environment setup, program structure, execution flow, command-line arguments, character set, identifiers, data types, operators, and control statements.
- **Control Flow**: Selection (`if`, `switch`), looping (`while`, `do-while`, `for`, `for-each`), and jump statements (`break`, `continue`, `return`) enable dynamic program behavior.
- **Practical Applications**: Examples like prime number checking, grading systems, and multiplication tables illustrate real-world use.
- **Next Steps**: Future topics include arrays, object-oriented programming, and advanced Java features.

---
