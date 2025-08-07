# Java OOP Cheat Sheet
*August 07, 2025, 10:38 PM IST*

## Module 4: Object-Oriented Programming (OOP) in Java
OOP organizes software around objects, emphasizing data and behavior encapsulation. Java’s OOP principles include classes, objects, inheritance, polymorphism, encapsulation, and abstraction.

---

## Classes and Objects
**Class**: Blueprint defining attributes (fields) and behaviors (methods).  
**Object**: Instance of a class, occupying memory with specific state and behavior.

### Syntax
```java
class ClassName {
    // Attributes
    dataType attributeName;
    // Methods
    returnType methodName(parameters) { /* body */ }
}
// Creating object
ClassName objectName = new ClassName();
```

### Example
```java
class Car {
    String brand;
    String model;
    int year;
    void start() {
        System.out.println(brand + " " + model + " started.");
    }
}
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.brand = "Toyota";
        myCar.model = "Camry";
        myCar.year = 2022;
        myCar.start(); // Toyota Camry started.
    }
}
```

### Interview Questions
- **Q: Difference between class and object?**  
  A: A class is a template defining structure and behavior; it doesn’t use memory. An object is an instance of a class, occupying memory with specific attribute values.
- **Q: Create object without `new`?**  
  A: Typically, `new` is required. Exceptions: deserialization, cloning (`clone()`), factory methods, reflection, or String literals (via String Pool).

---

## Constructors (Default, Parameterized)
Special methods invoked during object creation to initialize state.

### Characteristics
- Same name as class, no return type.
- Types: **Default** (no-args, compiler-provided) and **Parameterized** (with args).

### Default Constructor
Initializes fields to defaults (e.g., `int`: 0, `Object`: null).
```java
class Dog {
    String name; // null
    int age;     // 0
}
Dog myDog = new Dog(); // Compiler adds: public Dog() {}
```

### Parameterized Constructor
Initializes fields with provided values.
```java
class Person {
    String name;
    int age;
    public Person(String n, int a) {
        name = n;
        age = a;
    }
}
Person p = new Person("Alice", 30);
```

### Constructor Overloading
Multiple constructors with different parameter lists.
```java
class Person {
    String name;
    int age;
    public Person(String n, int a) { name = n; age = a; }
    public Person() { this("Unknown", 0); }
}
```

### Interview Questions
- **Q: What is a constructor’s purpose?**  
  A: Initializes an object’s state during creation.
- **Q: Default vs. parameterized constructor?**  
  A: Default: No-args, compiler-provided, sets defaults. Parameterized: Takes args for custom initialization; suppresses default constructor if defined.
- **Q: Can constructors have return types or be static?**  
  A: No return type (not even `void`); not static, as they initialize object instances.

---

## `this` Keyword
Refers to the current object.

### Uses
- **Disambiguate variables**: Differentiate instance variables from parameters/local variables.
- **Invoke methods**: Call other methods of the same class (implicit).
- **Constructor chaining**: Call another constructor in the same class (`this()`).
- **Return current instance**: Enable method chaining.

### Example
```java
class Box {
    int width;
    public Box(int width) {
        this.width = width; // Disambiguates parameter
    }
    void setWidth(int width) {
        this.width = width;
    }
    Box chainMethod() {
        return this; // Method chaining
    }
}
```

### Interview Questions
- **Q: Uses of `this` keyword?**  
  A: Disambiguate variables, invoke class methods/constructors, return current instance.
- **Q: Where can `this()` be used?**  
  A: Only as the first statement in a constructor for constructor chaining.

---

## Inheritance (`extends`, `super`)
Subclasses inherit fields and methods from a superclass (`extends`). `super` accesses parent class members.

### Syntax
```java
class Parent { /* members */ }
class Child extends Parent { /* additional members */ }
```

### `super` Uses
- Access parent’s instance variables.
- Invoke parent’s methods.
- Call parent’s constructor (`super()`).

### Example
```java
class Animal {
    String color = "white";
    void move() { System.out.println("Animal moves."); }
}
class Dog extends Animal {
    String color = "black";
    void move() { System.out.println("Dog runs."); }
    void print() {
        System.out.println(color); // black
        System.out.println(super.color); // white
        move(); // Dog runs.
        super.move(); // Animal moves.
    }
}
```

### Inheritance Types
- **Single**: Class B extends A.
- **Multilevel**: C extends B, B extends A.
- **Hierarchical**: B and C extend A.
- **Multiple**: Via interfaces (not classes) to avoid Diamond Problem.

### Interview Questions
- **Q: What is inheritance? Benefits?**  
  A: Subclass inherits superclass members, promoting code reuse, extensibility, and polymorphism.
- **Q: Uses of `super`?**  
  A: Access parent variables/methods, invoke parent constructor.
- **Q: Does Java support multiple inheritance?**  
  A: Not for classes (avoids Diamond Problem); supported via interfaces.

---

## Polymorphism (Overloading & Overriding)
Objects exhibit multiple behaviors via a common interface.

### Method Overloading (Compile-time)
Same method name, different parameter lists; resolved at compile-time.
```java
class Calculator {
    int add(int a, int b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
    double add(double a, double b) { return a + b; }
}
```

### Method Overriding (Runtime)
Subclass redefines superclass method; resolved at runtime via dynamic dispatch.
```java
class Animal {
    void makeSound() { System.out.println("Animal sound."); }
}
class Cat extends Animal {
    @Override
    void makeSound() { System.out.println("Cat meows."); }
}
Animal cat = new Cat();
cat.makeSound(); // Cat meows.
```

### Rules for Overriding
- Same method name, parameters, return type (or covariant).
- Access modifier not more restrictive.
- Cannot override `private`, `static`, or `final` methods.

### Interview Questions
- **Q: What is polymorphism? Types?**  
  A: Objects take multiple forms. **Compile-time**: Overloading (same method, different parameters). **Runtime**: Overriding (subclass redefines method).
- **Q: Overloading vs. overriding?**  
  A: Overloading: Same class, different parameters, compile-time. Overriding: Subclass, same signature, runtime.
- **Q: Can static methods be overridden?**  
  A: No, static methods are class-bound; redefining them is method hiding, not overriding.

---

## Encapsulation
Bundles data and methods into a class, hiding internal state via `private` fields and public getters/setters.

### Example
```java
class Account {
    private String accountNumber;
    private double balance;
    public Account(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance > 0 ? balance : 0;
    }
    public String getAccountNumber() { return accountNumber; }
    public double getBalance() { return balance; }
    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }
}
```

### Benefits
- Data hiding, flexibility, maintainability, testability.

### Interview Questions
- **Q: What is encapsulation? How achieved?**  
  A: Bundles data and methods, hiding internals with `private` fields and public getters/setters.
- **Q: Benefits of encapsulation?**  
  A: Protects data, allows implementation changes without affecting clients, enhances maintainability.
- **Q: Always need getters and setters?**  
  A: No, depends on design. Read-only fields need only getters; immutable fields may need none.

---

## Abstraction (Abstract Class & Interface)
Hides implementation details, exposing only essential functionality.

### Abstract Class
Contains abstract (no body) and concrete methods; cannot be instantiated.
```java
abstract class Shape {
    String color;
    abstract double calculateArea();
    void displayColor() { System.out.println("Color: " + color); }
}
class Circle extends Shape {
    double radius;
    Circle(String color, double radius) { super(color); this.radius = radius; }
    @Override
    double calculateArea() { return Math.PI * radius * radius; }
}
```

### Interface
Defines a contract with abstract methods (and default/static since Java 8).
```java
interface Drivable {
    void drive();
    default void turn(String direction) { System.out.println("Turning " + direction); }
}
class Sedan implements Drivable {
    public void drive() { System.out.println("Sedan drives."); }
}
```

### Abstract Class vs. Interface
| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| **Keyword** | `abstract class` | `interface` |
| **Inheritance** | `extends` (single) | `implements` (multiple) |
| **Methods** | Abstract + concrete | Abstract, default, static (Java 8+) |
| **Variables** | Any type | `public static final` only |
| **Constructors** | Yes | No |

### Interview Questions
- **Q: What is abstraction? How achieved?**  
  A: Shows essential features, hides details using abstract classes and interfaces.
- **Q: Abstract class vs. interface?**  
  A: Abstract classes allow partial implementation; interfaces define contracts with multiple inheritance.
- **Q: When to use each?**  
  A: Abstract class for shared code in related classes; interface for unrelated classes or multiple behaviors.

---

## Access Modifiers
Control visibility of classes, fields, methods, and constructors.

### Types
- **public**: Accessible everywhere.
- **protected**: Same class, package, and subclasses (even cross-package).
- **default** (no modifier): Same class and package only.
- **private**: Same class only.

### Summary Table
| Modifier | Same Class | Same Package | Subclass (Diff Package) | Other Package |
|----------|------------|--------------|-------------------------|---------------|
| `private` | Yes | No | No | No |
| `default` | Yes | Yes | No | No |
| `protected` | Yes | Yes | Yes | No |
| `public` | Yes | Yes | Yes | Yes |

### Interview Questions
- **Q: List access modifiers and their scope.**  
  A: `public`: Everywhere; `protected`: Class, package, subclasses; `default`: Class, package; `private`: Class only.
- **Q: When to use `protected`?**  
  A: For members accessible to subclasses and same package, but not globally.
- **Q: Can top-level classes be `private`/`protected`?**  
  A: No, only `public` or `default`; nested classes can use all modifiers.

---

## `static` Keyword
Members belong to the class, not instances.

### Uses
- **Static Variable**: Shared across all instances.
- **Static Method**: Called via class name, cannot access non-static members.
- **Static Block**: Initializes static variables on class load.
- **Static Nested Class**: Accessed without outer class instance.

### Example
```java
class Employee {
    static String companyName = "Tech Inc.";
    static int add(int a, int b) { return a + b; }
    static { System.out.println("Static block executed."); }
}
```

### Interview Questions
- **Q: What is `static`? Uses?**  
  A: Makes members class-bound. Used for shared variables, utility methods, initialization blocks.
- **Q: Can static methods access non-static members?**  
  A: No, they exist before objects; need an object reference.
- **Q: When does a static block execute?**  
  A: Once, when the class is loaded into the JVM.

---

## `final` Keyword
Restricts modification.

### Uses
- **Final Variable**: Constant, initialized once.
- **Final Method**: Cannot be overridden.
- **Final Class**: Cannot be extended.

### Example
```java
final class Circle {
    final double PI = 3.14159;
    final void display() { System.out.println("PI: " + PI); }
}
```

### Interview Questions
- **Q: Uses of `final`?**  
  A: Variables: Constants; Methods: Prevent overriding; Classes: Prevent inheritance.
- **Q: Can final variables be initialized later?**  
  A: Yes, in constructors (instance) or static blocks (static).
- **Q: Why is `String` final?**  
  A: For security (immutability in APIs) and performance (String Pool, consistent hash codes).