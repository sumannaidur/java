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
  - `main`: JVM's starting point