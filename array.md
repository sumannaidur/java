
### Introduction to Java Arrays 

An array is a fundamental data structure in Java used to store a collection of elements.

-----

## What is an Array?

An **array** is a group or collection of similar data items stored in contiguous memory locations. A more formal definition is:

> An array is a **fixed**, **indexed**, **randomly accessed**, **contiguously allocated** collection of **homogeneous** data items.

### Key Properties of Arrays

  * **Homogeneous Data**: An array can only store elements of the **same data type**. For example, you can have an array of integers or an array of strings, but you cannot mix integers and strings in the same array.
  * **Fixed Size**: The size of an array is determined when it's created and **cannot be changed** later.
  * **Indexed**: Each element in an array is accessed using a numerical index. The index always starts at **0** and goes up to **`size - 1`**. For an array of size 10, the valid indices are 0 to 9.
  * **Random Access**: You can directly access any element in the array using its index, without needing to go through the elements sequentially.
  * **Contiguous Memory Allocation**: All elements of an array are stored in a continuous block of memory, one after another. If the first element is at memory address `2000` and it's an integer (which takes 4 bytes), the next element will be at address `2004`, the next at `2008`, and so on.
  * **Implicit Objects**: In Java, arrays are objects. This means they have properties, like the `length` attribute.

-----

## Declaring, Defining, and Initializing Arrays

Working with arrays involves three main steps: declaration, definition (creation), and initialization.

### 1\. Array Declaration

This step tells the compiler the array's name and the type of data it will hold. It doesn't allocate any memory.

**Syntax:**

  * **Java Style (Preferred):** `dataType[] arrayName;`
  * **C/C++ Style (Also works):** `dataType arrayName[];`

**Examples:**

```java
// Declares an array of integers
int[] arr;

// Declares an array of strings
String[] cities;
```

### 2\. Array Definition (Creation)

This step allocates memory for the array using the `new` keyword and specifies its size.

**Syntax:** `arrayName = new dataType[size];`

**Example:**

```java
// Defines the array 'arr' to hold 10 integers
arr = new int[10];
```

You can **combine declaration and definition** in a single line:

```java
// Declares and creates an array for 6 subject marks
int[] marks = new int[6];

// Creates an array for 5 city names
String[] cities = new String[5];
```

**Important:** In Java, you cannot specify the size in the declaration like in C/C++ (`int a[10];`). Memory must be allocated dynamically with the `new` operator.

### 3\. Array Initialization

This step involves assigning values to the array elements. You can do this at the time of declaration.

**Syntax:** `dataType[] arrayName = {value1, value2, ...};`

When you initialize an array this way, you **don't need the `new` keyword** or the size. The compiler automatically determines the size based on the number of elements you provide.

**Example:**

```java
// Initializes an integer array. The size is automatically set to 10.
int[] marks = {6, 7, 8, 9, 8, 10, 7, 6, 8, 9};

// Initializes a string array. The size is automatically set to 6.
String[] cities = {"Pune", "Hyderabad", "Chennai", "Bangalore", "Delhi", "Mumbai"};
```

-----

## Working with Arrays

### Finding the Size: The `length` Attribute

You can get the size of any array using its `length` attribute. Note that `length` is a property, **not a method**, so you don't use parentheses `()`.

```java
int[] marks = {6, 7, 8, 9, 8, 10, 7, 6, 8, 9};
System.out.println(marks.length); // Output: 10
```

### Accessing and Modifying Elements

You can access or change an element's value using its index.

```java
// Accessing the element at index 1 (the second element)
System.out.println(cities[1]); // Output: Hyderabad

// Modifying the element at index 0
cities[0] = "Pune City";
```

### Reading and Writing Array Data

#### Writing (Printing) Array Elements

You can print all elements of an array using a loop.

**Using a standard `for` loop:**

```java
// Prints all marks
for (int i = 0; i < marks.length; i++) {
    System.out.println(marks[i]);
}
```

**Using a `for-each` loop (Enhanced for loop):** This is a simpler way to iterate over collections like arrays.

```java
// Prints all city names
for (String city : cities) {
    System.out.println(city);
}
```

#### Reading Data into an Array

You can populate an array with data from various sources, like user input or by generating values. The transcript shows an example of filling an array with random numbers.

```java
// 1. Create a double array of size 10
double[] randomNumbers = new double[10];

// 2. Fill the array with random numbers using a loop
for (int i = 0; i < randomNumbers.length; i++) {
    // Math.random() generates a double between 0.0 and 1.0
    randomNumbers[i] = Math.random();
}
```

-----

## Common Errors: `ArrayIndexOutOfBoundsException`

If you try to access an element using an invalid index (i.e., a negative number or an index greater than or equal to the array's length), Java will throw an `ArrayIndexOutOfBoundsException`.

```java
String[] cities = new String[6]; // Valid indices are 0, 1, 2, 3, 4, 5

// This line will cause an error because index 6 does not exist!
System.out.println(cities[6]); // Throws ArrayIndexOutOfBoundsException
```


### Java Programming: Common Array Operations 

-----

## Finding Sum and Average

This is a basic operation where we iterate through the array and accumulate the values.

#### Logic:

1.  Initialize a variable, let's call it `sum`, to `0`.
2.  Loop through each element of the array.
3.  In each iteration, add the current array element to `sum`.
4.  After the loop finishes, `sum` will hold the total sum of all elements.
5.  The **average** can then be calculated by dividing the `sum` by the number of elements (`arr.length`).

#### Code Example:

```java
int[] arr = {24, 61, 55, 78, 43, 80}; // Example array
int sum = 0;

// Loop through the array to calculate sum
for (int i = 0; i < arr.length; i++) {
    sum += arr[i]; // This is shorthand for sum = sum + arr[i]
}

// Calculate average (note: integer division truncates decimals)
int average = sum / arr.length;

System.out.println("Sum of Array Elements: " + sum);
System.out.println("Average of Elements: " + average);
```

-----

## Finding Minimum and Maximum Elements

This algorithm finds the smallest and largest values in an array.

#### Logic:

1.  Assume the **first element** of the array (`arr[0]`) is both the **minimum (`min`)** and the **maximum (`max`)** value.
2.  Loop through the array (you can start from the second element, but starting from the first is also fine).
3.  For each element, compare it with the current `min` and `max`:
      * If the current element is **less than `min`**, update `min` to be this new element.
      * If the current element is **greater than `max`**, update `max` to be this new element.
4.  After the loop completes, the `min` and `max` variables will hold the true minimum and maximum values from the array.

#### Code Example:

```java
int[] arr = {93, 25, 71, 19, 86}; // Example array
int min = arr[0];
int max = arr[0];

for (int i = 0; i < arr.length; i++) {
    if (arr[i] < min) {
        min = arr[i]; // Found a new minimum
    }
    if (arr[i] > max) {
        max = arr[i]; // Found a new maximum
    }
}

System.out.println("Min: " + min); // Output: Min: 19
System.out.println("Max: " + max); // Output: Max: 93
```

-----

## Searching for an Element (Linear Search)

This algorithm checks if a given element exists in an array.

#### Logic:

1.  Get the element you want to search for (let's call it `x`).
2.  Use a **boolean flag** (e.g., `isFound`), initialized to `false`. This helps determine if the element was found.
3.  Loop through the array from the first element to the last.
4.  In each iteration, check if the current array element is equal to `x`.
      * If they match, print a "found" message with the index, set `isFound` to `true`, and use the `break` statement to exit the loop early since there's no need to search further.
5.  After the loop, check the value of the `isFound` flag. If it's still `false`, it means the loop completed without finding the element, so you can print a "not found" message.

#### Code Example:

```java
int[] arr = {18, 52, 86, 34, 66}; // Example array
int x = 34; // Element to search for
boolean isFound = false;

for (int i = 0; i < arr.length; i++) {
    if (x == arr[i]) {
        System.out.println(x + " is found at index " + i);
        isFound = true;
        break; // Exit the loop once found
    }
}

if (!isFound) { // Checks if isFound is still false
    System.out.println(x + " is not found.");
}
```

-----

## Sorting Array Elements

Sorting arranges the elements in a specific order, typically ascending. While you can write complex sorting algorithms like bubble sort or quick sort, Java provides a simple, built-in utility.

#### Using the `Arrays.sort()` Utility:

Java's `java.util.Arrays` class has a powerful static method called `sort()`. This is the easiest way to sort an array.

1.  **Import** the class: `import java.util.Arrays;`
2.  **Call the method**, passing your array as the argument: `Arrays.sort(arr);`
3.  The method sorts the array **in place** in ascending (natural) order.

#### Code Example:

```java
import java.util.Arrays; // Don't forget to import!

// ... inside a method
int[] arr = {86, 18, 52, 66, 34};

System.out.println("Array before sorting: " + Arrays.toString(arr));

// Sort the array
Arrays.sort(arr);

System.out.println("Array after sorting: " + Arrays.toString(arr));
// Output: [18, 34, 52, 66, 86]
```

-----

## Reading Array Elements from User Input

Instead of hard-coding array values, you can populate an array by reading input from the user's keyboard using the `Scanner` class.

#### Logic:

1.  **Import** the class: `import java.util.Scanner;`
2.  Create a `Scanner` object to read from the console: `Scanner input = new Scanner(System.in);`
3.  Prompt the user to enter the elements.
4.  Loop from `0` to `arr.length - 1`. In each iteration, use `input.nextInt()` to read an integer from the user and assign it to the current array position (`arr[i]`).

#### Code Example:

```java
import java.util.Scanner;

Scanner input = new Scanner(System.in);
int[] arr = new int[5]; // Create an empty array of size 5

System.out.println("Please enter " + arr.length + " integer elements:");

// Loop to read 5 integers from the user
for (int i = 0; i < arr.length; i++) {
    arr[i] = input.nextInt();
}

System.out.println("You entered: " + Arrays.toString(arr));
```


### Introduction to Java Programming: Arrays of Arrays 

-----

## Two-Dimensional (2D) Arrays

A 2D array is the simplest form of a multi-dimensional array. You can think of it as a table with **rows** and **columns**.

### Declaration, Definition, and Initialization

#### 1\. Declaration

Declares a reference to a 2D array. No memory is allocated.

```java
// Declares 'a' as a reference to a 2D integer array
int[][] a;
```

#### 2\. Definition (Creation)

Allocates memory using the `new` keyword and specifies the number of rows and columns.

```java
// Defines 'a' as a 3x4 array (3 rows, 4 columns)
a = new int[3][4];

// Declaration and definition can be combined
String[][] names = new String[10][20];
```

The `length` attribute on a 2D array gives you the **number of rows**.

```java
System.out.println(a.length); // Output: 3
```

#### 3\. Initialization

Assigns values at the time of declaration. Each inner set of curly braces `{}` represents a row.

```java
// Initializes a 3x3 integer matrix
int[][] x = {
    {1, 2, 3},  // Row 0
    {3, 4, 5},  // Row 1
    {5, 6, 7}   // Row 2
};
```

### Working with 2D Arrays

To access every element in a 2D array, you need **nested loops**: an outer loop for the rows and an inner loop for the columns.

  * The **outer loop** iterates through the rows (e.g., `for i`).
  * The **inner loop** iterates through the columns of the current row (e.g., `for j`).

#### Populating and Printing a 2D Array

The following example defines a 3x4 array, populates it with user input, and then prints it in a matrix format.

```java
import java.util.Scanner;

// ... inside main method
Scanner input = new Scanner(System.in);
int[][] arr = new int[3][4];

System.out.println("Please enter 12 integer items:");

// Use nested loops to read data
for (int i = 0; i < 3; i++) {       // Outer loop for rows
    for (int j = 0; j < 4; j++) {   // Inner loop for columns
        arr[i][j] = input.nextInt();
    }
}

System.out.println("Here is your matrix:");
// Use nested loops to print data
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 4; j++) {
        // Use print() to keep elements on the same line
        System.out.print(arr[i][j] + "\t"); // \t adds a tab for spacing
    }
    // Use println() to move to the next line after each row is printed
    System.out.println();
}
```

-----

## Arrays of Arrays of Varying Length (Jagged Arrays)

A powerful feature in Java is that each row in a 2D array can have a **different number of columns**. This is called a **jagged array**. This is possible because a 2D array is just an array of other arrays.

### Creating a Jagged Array

1.  Specify the number of rows, but leave the column size empty.
2.  Define each row (which is itself an array) individually with its desired size.

#### Example: Monitoring City Temperatures

Imagine you want to monitor temperatures for 5 cities, but for different durations:

  * City 0: 365 days (yearly)
  * City 1: 52 days (weekly)
  * City 2: 12 days (monthly)

<!-- end list -->

```java
// 1. Define the number of rows (cities), but not the columns
double[][] temp = new double[5][];

// 2. Define each row with a different length
temp[0] = new double[365]; // First city has 365 columns (days)
temp[1] = new double[52];  // Second city has 52 columns
temp[2] = new double[12];  // Third city has 12 columns
// temp[3] and temp[4] are currently null

// The length attribute works differently for rows and columns
System.out.println(temp.length);      // Output: 5 (number of rows)
System.out.println(temp[0].length);   // Output: 365 (columns in the first row)
System.out.println(temp[1].length);   // Output: 52 (columns in the second row)
```

-----

## N-Dimensional Arrays (3D and Beyond)

The concept of "arrays of arrays" can be extended to create 3D, 4D, or N-dimensional arrays. A 3D array is an array of 2D arrays.

#### Example: Farmer's Fields

Imagine a farmer has farms in multiple countries. Each country has multiple farms, and each farm has multiple fields. This can be modeled with a 3D array.

**Statement:** A farmer has farms in **5 countries**. Each country has **10 farms**, and each farm has **15 fields**.

```java
// This creates a fixed-size 3D array: 5 (countries) x 10 (farms) x 15 (fields)
int[][][] beans = new int[5][10][15];
```

This can also be a **jagged 3D array** where dimensions are defined step-by-step:

```java
// Step 1: The farmer has farms in 5 countries. We don't know how many farms or fields yet.
int[][][] beans = new int[5][][];

// Step 2: In the first country (index 0), the farmer has 10 farms.
beans[0] = new int[10][];

// Step 3: In the first country's fifth farm (index 4), there are 15 fields.
beans[0][4] = new int[15];

// You can now access an element like this:
// beans[countryIndex][farmIndex][fieldIndex]
```
