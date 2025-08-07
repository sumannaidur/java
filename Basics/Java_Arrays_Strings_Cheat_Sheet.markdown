# Java Arrays & Strings Cheat Sheet
*August 07, 2025, 10:35 PM IST*

## Module 3: Arrays & Strings
This module covers arrays for storing collections of elements and strings for handling character sequences in Java.

---

## 1D and 2D Arrays
Arrays store a fixed number of elements of the same type. Their size is immutable once created.

### 1D Arrays
Linear collection of elements.

#### Declaration
```java
dataType[] arrayName; // Preferred
// OR
dataType arrayName[];
```

#### Instantiation
```java
arrayName = new dataType[size];
```

#### Initialization
```java
// Method 1: Assign values
int[] numbers = new int[5];
numbers[0] = 10;
numbers[1] = 20;

// Method 2: Array literal
int[] scores = {90, 85, 92, 78, 95};
```

#### Accessing Elements
Zero-indexed. Use `array.length` for size.
```java
System.out.println(scores[0]); // 90
System.out.println(scores[scores.length - 1]); // 95
```

### 2D Arrays
Array of arrays, forming a table-like structure (rows × columns).

#### Declaration and Instantiation
```java
dataType[][] arrayName = new dataType[rows][columns];
```

#### Initialization
```java
// Method 1: Assign values
int[][] matrix = new int[2][3];
matrix[0][0] = 1;
matrix[1][2] = 6;

// Method 2: Array literal
int[][] grid = {{1, 2, 3}, {4, 5, 6}};
```

#### Accessing Elements
```java
System.out.println(grid[0][1]); // 2 (row 0, column 1)
```

### Jagged Arrays
2D arrays with rows of different lengths.
```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[2]; // 2 columns
jaggedArray[1] = new int[4]; // 4 columns
jaggedArray[2] = new int[3]; // 3 columns
jaggedArray[0][0] = 10;
jaggedArray[1][3] = 40;
```

### Interview Questions
- **Q: What is an array in Java? What are its limitations?**  
  A: An array is a fixed-size, contiguous collection of elements of the same type. Limitation: Fixed size, requiring a new array for resizing, which is inefficient.
- **Q: How to declare, instantiate, and initialize a 1D array?**  
  A: Declare: `int[] arr;` Instantiate: `arr = new int[5];` Initialize: `arr[0] = 10;` or use literal: `int[] arr = {10, 20, 30};`.
- **Q: What is a jagged array? When to use it?**  
  A: A 2D array with rows of varying lengths. Use for data with non-uniform sub-groups, like student test scores or sparse matrices.

---

## Array Operations (Sort, Search, Insert, Delete)
Operations for manipulating arrays.

### Sorting
Use `Arrays.sort()` for ascending order.
```java
import java.util.Arrays;
int[] nums = {5, 2, 8, 1, 9};
Arrays.sort(nums);
System.out.println(Arrays.toString(nums)); // [1, 2, 5, 8, 9]
```

### Searching
- **Linear Search**: Checks each element. O(n) complexity, works on unsorted arrays.
- **Binary Search**: Requires sorted array, divides search space. O(log n) complexity.
```java
import java.util.Arrays;
int[] sortedNums = {1, 2, 5, 8, 9};
int index = Arrays.binarySearch(sortedNums, 5); // Returns 2
int notFound = Arrays.binarySearch(sortedNums, 7); // Returns negative
```

### Insertion
Create a new array, copy elements, and insert the new element.
```java
int[] original = {10, 20, 30};
int element = 25, position = 1;
int[] newArray = new int[original.length + 1];
for (int i = 0; i < position; i++) {
    newArray[i] = original[i];
}
newArray[position] = element;
for (int i = position; i < original.length; i++) {
    newArray[i + 1] = original[i];
}
// newArray: [10, 25, 20, 30]
```

### Deletion
Create a new array, skip the element to delete.
```java
int[] original = {10, 20, 30, 40};
int indexToDelete = 1;
int[] newArray = new int[original.length - 1];
for (int i = 0, k = 0; i < original.length; i++) {
    if (i == indexToDelete) continue;
    newArray[k++] = original[i];
}
// newArray: [10, 30, 40]
```

### Interview Questions
- **Q: How to sort an array in Java?**  
  A: Use `Arrays.sort(arrayName)` for ascending order. Custom sorting requires manual algorithms or a `Comparator` for objects.
- **Q: Linear vs. binary search?**  
  A: **Linear**: O(n), works on unsorted arrays. **Binary**: O(log n), requires sorted arrays. Use linear for small/unsorted arrays, binary for large/sorted ones.
- **Q: Why are insertion and deletion inefficient?**  
  A: Arrays have fixed size, requiring new arrays and element copying, which is time-consuming (O(n) for shifting).

---

## String Class & Methods
`String` is a class representing immutable character sequences.

### Creating Strings
```java
String s1 = "Hello"; // String Pool
String s2 = new String("World"); // Heap
```

### Key Methods
- `length()`: Returns string length (`"Java".length() // 4`).
- `charAt(int index)`: Gets character at index (`"Java".charAt(0) // 'J'`).
- `concat(String)` / `+`: Concatenates strings (`"Hello".concat(" World") // "Hello World"`).
- `equals(Object)`: Compares content (`"apple".equals("Apple") // false`).
- `equalsIgnoreCase(String)`: Case-insensitive comparison (`"apple".equalsIgnoreCase("Apple") // true`).
- `compareTo(String)`: Lexicographical comparison.
- `indexOf(char/String)`: First occurrence index.
- `lastIndexOf(char/String)`: Last occurrence index.
- `substring(int begin)` / `substring(int begin, int end)`: Extracts substring.
- `toLowerCase()` / `toUpperCase()`: Case conversion.
- `trim()`: Removes leading/trailing whitespace.
- `startsWith(String)` / `endsWith(String)`: Checks prefix/suffix.
- `contains(CharSequence)`: Checks for substring.
- `replace(char/String, char/String)`: Replaces characters/substrings.
- `split(String regex)`: Splits into array.
  ```java
  String data = "apple,banana,cherry";
  String[] fruits = data.split(",");
  // fruits: ["apple", "banana", "cherry"]
  ```
- `valueOf(...)`: Converts data to String (`String.valueOf(123) // "123"`).

### String Pool
Stores string literals in heap to optimize memory. Literals reuse existing objects; `new String()` creates new heap objects.

### Interview Questions
- **Q: Is String a primitive type? Explain immutability.**  
  A: No, `String` is a class. Immutability means a `String`’s content cannot change; modifications create new objects, ensuring thread safety.
- **Q: What is the String Pool?**  
  A: A heap area storing unique string literals. Literals like `"hello"` reuse pool objects, reducing memory usage.
- **Q: Difference between `==` and `.equals()` for Strings?**  
  A: `==` compares references; `.equals()` compares content.
  ```java
  String s1 = "hello";
  String s2 = "hello";
  String s3 = new String("hello");
  System.out.println(s1 == s2); // true (same pool object)
  System.out.println(s1 == s3); // false (different heap object)
  System.out.println(s1.equals(s3)); // true (same content)
  ```

---

## StringBuilder & StringBuffer
Mutable alternatives to `String` for efficient modifications.

### StringBuffer
- Introduced in Java 1.0.
- Mutable, thread-safe (synchronized), slower due to synchronization.

### StringBuilder
- Introduced in Java 5.
- Mutable, not thread-safe, faster.

### Key Methods (Both)
- `append(...)`: Adds content.
- `insert(int, ...)`: Inserts at position.
- `delete(int start, int end)`: Deletes range.
- `reverse()`: Reverses sequence.
- `replace(int start, int end, String)`: Replaces range.
- `length()` / `capacity()`: Returns length/allocated space.
- `toString()`: Converts to `String`.
```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // Hello World
sb.insert(6, "Java "); // Hello Java World
sb.delete(0, 6); // Java World
String finalString = sb.toString();
```

### When to Use
- **String**: Fixed content, immutable.
- **StringBuilder**: Single-threaded, frequent modifications.
- **StringBuffer**: Multi-threaded, thread-safe modifications.

### Interview Questions
- **Q: String vs. StringBuilder vs. StringBuffer?**  
  A: **String**: Immutable, thread-safe. **StringBuilder**: Mutable, not thread-safe, fast. **StringBuffer**: Mutable, thread-safe, slower.
- **Q: When to use StringBuilder over StringBuffer?**  
  A: Use `StringBuilder` for single-threaded environments for better performance. Use `StringBuffer` for multi-threaded environments needing thread safety.
- **Q: How to convert StringBuilder to String?**  
  A: Use `toString()`: `String str = myStringBuilder.toString();`.