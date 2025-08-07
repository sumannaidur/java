# Java Collections Framework Cheat Sheet
*August 07, 2025, 10:46 PM IST*

## Module 6: Java Collections Framework
The Java Collections Framework (JCF) provides interfaces and classes for managing collections of objects, offering efficient data structures and algorithms.

### Core Interfaces
- **Collection**: Root interface for collections.
- **List**: Ordered, allows duplicates, indexed access.
- **Set**: No duplicates, no guaranteed order (except specific implementations).
- **Queue**: Holds elements for processing, typically FIFO.
- **Map**: Maps unique keys to values (not a `Collection`).

---

## List (ArrayList, LinkedList)
Ordered collections allowing duplicates and indexed access.

### ArrayList
- **Implementation**: Dynamic array.
- **Performance**: 
  - Random access: O(1).
  - Middle insertions/deletions: O(n) (shifting).
  - End additions: Amortized O(1).
- **Memory**: Higher due to array resizing.
- **Use Case**: Frequent random access, fewer middle modifications.

```java
import java.util.ArrayList;
import java.util.List;

List<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add(1, "Grape"); // Insert at index
fruits.set(0, "Orange"); // Update
fruits.remove("Grape"); // Remove by object
System.out.println(fruits); // [Orange]
```

### LinkedList
- **Implementation**: Doubly linked list.
- **Performance**: 
  - Random access: O(n) (traversal).
  - Insertions/deletions: O(1) (after finding position).
  - Head/tail operations: O(1).
- **Memory**: Higher per element (node pointers).
- **Use Case**: Frequent insertions/deletions, queue operations.

```java
import java.util.LinkedList;
import java.util.List;

List<String> colors = new LinkedList<>();
colors.add("Red");
colors.addFirst("Yellow");
colors.removeLast();
System.out.println(colors); // [Yellow, Red]
```

### Interview Questions
- **Q: List interface characteristics?**  
  A: Ordered, allows duplicates, indexed access.
- **Q: ArrayList vs. LinkedList?**  
  A: **ArrayList**: Fast random access (O(1)), slow middle modifications (O(n)). **LinkedList**: Fast insertions/deletions (O(1)), slow random access (O(n)).
- **Q: Why are middle insertions slow in ArrayList?**  
  A: Requires shifting elements in contiguous array, O(n).

---

## Set (HashSet, LinkedHashSet, TreeSet)
Collections with no duplicate elements.

### HashSet
- **Implementation**: Hash table (backed by `HashMap`).
- **Order**: No guaranteed order.
- **Performance**: O(1) average for add/remove/contains.
- **Null**: Allows one null element.
- **Use Case**: Fast operations, order unimportant.

```java
import java.util.HashSet;
import java.util.Set;

Set<String> names = new HashSet<>();
names.add("Alice");
names.add("Alice"); // Ignored
names.remove("Bob");
System.out.println(names); // [Alice] (order may vary)
```

### LinkedHashSet
- **Implementation**: Hash table + doubly linked list.
- **Order**: Maintains insertion order.
- **Performance**: Slightly slower than `HashSet` (O(1)).
- **Null**: Allows one null element.
- **Use Case**: Unique elements with insertion order.

```java
import java.util.LinkedHashSet;
import java.util.Set;

Set<String> fruits = new LinkedHashSet<>();
fruits.add("Apple");
fruits.add("Apple"); // Ignored
System.out.println(fruits); // [Apple]
```

### TreeSet
- **Implementation**: Red-Black Tree.
- **Order**: Sorted (natural or custom).
- **Performance**: O(log n) for operations.
- **Null**: No null elements.
- **Use Case**: Sorted unique elements.

```java
import java.util.TreeSet;
import java.util.Set;

Set<Integer> numbers = new TreeSet<>();
numbers.add(50);
numbers.add(10);
System.out.println(numbers); // [10, 50]
```

### Interview Questions
- **Q: Set vs. List?**  
  A: **Set**: No duplicates, no indexed access. **List**: Allows duplicates, indexed.
- **Q: When to use HashSet, LinkedHashSet, TreeSet?**  
  A: **HashSet**: Fastest, unordered. **LinkedHashSet**: Insertion order. **TreeSet**: Sorted order.
- **Q: Can Sets contain null?**  
  A: **HashSet/LinkedHashSet**: One null. **TreeSet**: No null (throws `NullPointerException`).

---

## Map (HashMap, TreeMap)
Key-value pair collections; keys are unique.

### HashMap
- **Implementation**: Hash table.
- **Order**: No guaranteed order.
- **Performance**: O(1) average for put/get/remove.
- **Null**: One null key, multiple null values.
- **Use Case**: Fast key-value operations.

```java
import java.util.HashMap;
import java.util.Map;

Map<String, Integer> scores = new HashMap<>();
scores.put("Alice", 95);
scores.put("Alice", 98); // Updates value
scores.remove("Bob");
System.out.println(scores.get("Alice")); // 98
```

### TreeMap
- **Implementation**: Red-Black Tree.
- **Order**: Sorted by keys (natural or custom).
- **Performance**: O(log n) for operations.
- **Null**: No null keys, allows null values.
- **Use Case**: Sorted key-value pairs.

```java
import java.util.TreeMap;
import java.util.Map;

Map<String, Integer> scores = new TreeMap<>();
scores.put("Charlie", 92);
scores.put("Alice", 95);
System.out.println(scores); // {Alice=95, Charlie=92}
```

### Interview Questions
- **Q: What is a Map?**  
  A: Stores unique keys mapped to values, like a dictionary.
- **Q: HashMap vs. TreeMap?**  
  A: **HashMap**: Unordered, O(1), allows null key. **TreeMap**: Sorted keys, O(log n), no null keys.
- **Q: Duplicate key in HashMap?**  
  A: Replaces old value with new; `put()` returns previous value or null.

---

## Stack & Queue
Data structures with specific access patterns.

### Stack
- **Principle**: LIFO (Last-In, First-Out).
- **Implementation**: Use `ArrayDeque` (preferred) or `Stack` (legacy, extends `Vector`).
- **Operations**: `push`, `pop`, `peek`, `empty`.

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<String> stack = new ArrayDeque<>();
stack.push("Action 1");
stack.push("Action 2");
System.out.println(stack.pop()); // Action 2
```

### Queue
- **Principle**: FIFO (First-In, First-Out).
- **Implementations**: `LinkedList`, `ArrayDeque`, `PriorityQueue`.
- **Operations**: `offer`, `poll`, `peek`.

```java
import java.util.LinkedList;
import java.util.Queue;

Queue<String> queue = new LinkedList<>();
queue.offer("Task A");
queue.offer("Task B");
System.out.println(queue.poll()); // Task A
```

### PriorityQueue
- **Order**: By natural ordering or `Comparator`.
- **Use Case**: Priority-based processing.

```java
import java.util.PriorityQueue;
import java.util.Queue;

Queue<Integer> pq = new PriorityQueue<>();
pq.add(5);
pq.add(1);
System.out.println(pq.poll()); // 1 (highest priority)
```

### Interview Questions
- **Q: LIFO vs. FIFO?**  
  A: **LIFO**: Stack (last added, first removed). **FIFO**: Queue (first added, first removed).
- **Q: Why prefer ArrayDeque over Stack?**  
  A: `ArrayDeque` is faster (no synchronization), more flexible (implements `Deque`).
- **Q: PriorityQueue vs. regular Queue?**  
  A: **PriorityQueue**: Orders by priority, not FIFO. **Queue**: FIFO ordering.

---

## Iterator, forEach
Mechanisms for traversing collections.

### Iterator
- **Interface**: `java.util.Iterator`.
- **Methods**: `hasNext()`, `next()`, `remove()` (safe removal).
- **Use Case**: Safe modification during iteration.

```java
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;

List<String> names = new ArrayList<>();
names.add("Alice");
names.add("Bob");
Iterator<String> iterator = names.iterator();
while (iterator.hasNext()) {
    String name = iterator.next();
    if (name.equals("Bob")) iterator.remove();
}
System.out.println(names); // [Alice]
```

### forEach Loop
- **Syntax**: Enhanced for loop for `Iterable` collections.
- **Limitation**: Cannot modify collection (throws `ConcurrentModificationException`).

```java
import java.util.ArrayList;
import java.util.List;

List<Integer> numbers = new ArrayList<>();
numbers.add(10);
numbers.add(20);
for (int num : numbers) {
    System.out.println(num);
}
numbers.forEach(n -> System.out.println(n)); // Lambda (Java 8+)
```

### Interview Questions
- **Q: What is Iterator? When useful?**  
  A: Standard traversal mechanism; useful for non-indexed collections (`Set`) and safe removal.
- **Q: forEach loop limitation?**  
  A: Cannot modify collection during iteration (causes `ConcurrentModificationException`).
- **Q: Avoid ConcurrentModificationException?**  
  A: Use `Iterator.remove()`, iterate over a copy, or use concurrent collections (e.g., `CopyOnWriteArrayList`).