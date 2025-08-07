# Java Control Statements Cheat Sheet
*August 07, 2025, 10:30 PM IST*

## Module 2: Control Statements
Control statements in Java manage the flow of program execution, enabling decisions, repetition, and jumps based on conditions.

---

## if, if-else, Nested if
Conditional statements execute code based on boolean conditions.

### if Statement
Executes a block if the condition is true.
```java
int score = 75;
if (score >= 60) {
    System.out.println("You passed the exam!");
}
```

### if-else Statement
Executes one block if true, another if false.
```java
int temperature = 28;
if (temperature > 25) {
    System.out.println("It's hot outside.");
} else {
    System.out.println("It's not too hot.");
}
```

### if-else if-else Ladder
Checks multiple conditions sequentially; executes the first true block.
```java
int marks = 85;
if (marks >= 90) {
    System.out.println("Grade: A");
} else if (marks >= 80) {
    System.out.println("Grade: B");
} else if (marks >= 70) {
    System.out.println("Grade: C");
} else {
    System.out.println("Grade: D");
}
```

### Nested if
An if statement inside another if or else block for complex logic.
```java
boolean hasLicense = true;
int age = 20;
if (age >= 18) {
    if (hasLicense) {
        System.out.println("You can drive.");
    } else {
        System.out.println("You are old enough, but need a license.");
    }
} else {
    System.out.println("You are too young to drive.");
}
```

### Interview Questions
- **Q: When to use an if-else if-else ladder vs. multiple if statements?**  
  A: Use an if-else if-else ladder for mutually exclusive conditions where only one block should execute. Multiple if statements allow multiple blocks to execute if their conditions are true, which may not be desired for sequential checks.
- **Q: Explain nested if with a real-world example.**  
  A: A nested if is an if statement inside another if/else. Example: Checking discount eligibility requires first verifying a purchase amount (>100), then checking loyalty status.
  ```java
  double purchaseAmount = 120.0;
  boolean isLoyaltyMember = true;
  if (purchaseAmount > 100) {
      if (isLoyaltyMember) {
          System.out.println("Eligible for 15% discount!");
      } else {
          System.out.println("Eligible for 10% discount!");
      }
  } else {
      System.out.println("No discount applied.");
  }
  ```

---

## switch-case
Tests a variable against multiple values for cleaner multi-condition checks.

### Syntax
Supports `byte`, `short`, `char`, `int`, `String`, `enum`, or wrappers. `break` prevents fall-through; `default` handles unmatched cases.
```java
int dayOfWeek = 3;
switch (dayOfWeek) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    case 4:
        System.out.println("Thursday");
        break;
    case 5:
        System.out.println("Friday");
        break;
    case 6:
    case 7:
        System.out.println("Weekend!");
        break;
    default:
        System.out.println("Invalid day");
}
```

### Interview Questions
- **Q: Purpose of the `break` keyword in a switch statement?**  
  A: `break` terminates the switch block, preventing execution of subsequent cases (fall-through). Omitting it causes all cases after a match to execute until a `break` or end of block.
- **Q: When to use switch over if-else if-else?**  
  A: Use switch for a single variable with discrete values (e.g., integers, strings). It’s more readable and efficient than a long if-else if-else ladder. Use if-else for range-based or complex conditions.

---

## for, while, do-while Loops
Loops execute code repeatedly based on conditions.

### for Loop
Best for known iteration counts. Includes initialization, condition, and update.
```java
// Standard for loop
for (int i = 1; i <= 5; i++) {
    System.out.println(i); // Prints 1, 2, 3, 4, 5
}

// Enhanced for loop (for-each)
int[] numbers = {10, 20, 30};
for (int num : numbers) {
    System.out.println(num); // Prints 10, 20, 30
}
```

### while Loop
Executes while a condition is true; may not run if condition is initially false.
```java
int count = 1;
while (count <= 5) {
    System.out.println("Count: " + count);
    count++;
}
```

### do-while Loop
Executes at least once; checks condition after each iteration.
```java
int i = 1;
do {
    System.out.println("Value of i: " + i);
    i++;
} while (i <= 0); // Prints "Value of i: 1" (runs once)
```

### Interview Questions
- **Q: Differences between for, while, and do-while loops? When to use each?**  
  A:  
  - **for**: Known iteration count (e.g., array traversal, counting).  
  - **while**: Unknown iterations, condition-based (e.g., reading input until done).  
  - **do-while**: At least one execution needed (e.g., menu display).  
- **Q: Can a for loop be infinite? How?**  
  A: Yes, by omitting the condition or using a always-true condition.  
  ```java
  for ( ; ; ) { // Infinite
      System.out.println("Infinite loop!");
  }
  ```

---

## break & continue
Jump statements to control loop execution.

### break
Terminates the innermost loop or switch.
```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // Exits loop
    }
    System.out.println(i); // Prints 1, 2, 3, 4
}
```

### continue
Skips the rest of the current iteration, proceeds to the next.
```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue; // Skips i=3
    }
    System.out.println(i); // Prints 1, 2, 4, 5
}
```

### Labeled break/continue
Controls specific outer loops in nested structures.
```java
outerLoop:
for (int i = 1; i <= 3; i++) {
    innerLoop:
    for (int j = 1; j <= 3; j++) {
        if (i == 2 && j == 2) {
            break outerLoop; // Exits outer loop
        }
        System.out.println("i: " + i + ", j: " + j);
    }
}
// Output: i: 1, j: 1 to 3; i: 2, j: 1
```

### Interview Questions
- **Q: Difference between break and continue?**  
  A: **break**: Terminates the loop entirely. **continue**: Skips the current iteration, continues with the next.
- **Q: When to use labeled break or continue?**  
  A: Use in nested loops to break or continue a specific outer loop, providing precise control over complex loop structures.