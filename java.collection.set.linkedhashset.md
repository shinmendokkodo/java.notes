# LinkedHashSet in Java

A `LinkedHashSet` is an ordered version of `HashSet` that maintains a doubly-linked List across all elements. When the iteration order is needed to be maintained this class is used. When iterating through a `HashSet` the order is unpredictable, while a `LinkedHashSet` lets us iterate through the elements in the order in which they were inserted. When cycling through `LinkedHashSet` using an iterator, the elements will be returned in the order in which they were inserted.

**Syntax**:
```java
LinkedHashSet<String> hs = new LinkedHashSet<String>();
```
- Contains unique elements only like `HashSet`. It extends `HashSet` class and implements `Set` interface.
- Maintains insertion order.

### Example 1:

```java
// Java program to demonstrate
// working of LinkedHashSet
import java.util.*;

class Test {
    public static void main(String[] args) {
        LinkedHashSet<Integer> s = new LinkedHashSet<Integer>();

        // Adding keys into LinkedHashSet usind add()
        s.add(10);
        s.add(20);
        s.add(30);

        // Traversing the set
        for(Integer x: s) {
            System.out.print(x + " ");
        }
    }
}
```
```md
Output:
10 20 30
```

### Example 2: When duplicate elements are inserted.

```java
// Java program to demonstrate
// working of LinkedHashSet
import java.util.*;

class Test {
    public static void main(String[] args) {
        LinkedHashSet<Integer> s = new LinkedHashSet<Integer>();

        // Adding keys into HashSet usind add()
        s.add(10);
        s.add(20);
        s.add(30);

        // Addition of a duplicate element is
        // skipped and the order is maintained
        s.add(20);

        // Displaying the set
        System.out.println(s);
    }
}
```
```md
Output:
10 20 30
```

### Example 3: Showing the removal of elements.

```java
// Java program to demonstrate
// working of LinkedHashSet
import java.util.*;

class Test {
    public static void main(String[] args) {
        LinkedHashSet<Integer> s = new LinkedHashSet<Integer>();

        // Adding keys into HashSet usind add()
        s.add(10);
        s.add(20);
        s.add(30);

        s.remove(20);

        // Displaying the set
        System.out.println(s);
    }
}
```
```md
Output:
[10, 30]
```

> **Time Complexity**: All the above method takes `O(1)` time in worst case.

> **NOTE**: Keeping the insertion order in `LinkedHashset` have additional associated costs, both in terms of spending additional CPU cycles and needing more memory. If you do not need the insertion order maintained, it is recommended to use the lighter-weight `HashSet` instead.

---

# `HashSet` vs `TreeSet`

When it comes to discussing differences between `Set` the firstmost thing that comes into play is the insertion order and how elements will be processed. `HashSet` in java is a class implementing the `Set` interface, backed by a hash table which is actually a `HashMap` instance. This class permits the `null` element. The class also offers constant time performance for the basic operations like **add**, **remove**, **contains**, and **size** assuming the hash function disperses the elements properly among the buckets while `TreeSet` is an implementation of the `SortedSet` interface which as the name suggests uses the tree for storage purposes where here the ordering of the elements is maintained by a set using their natural ordering whether or not an explicit comparator is provided.

1. Speed and internal implementation
    For operations like search, insert, and delete `HashSet` takes constant time for these operations on average. `HashSet` is faster than `TreeSet`. `HashSet` is implemented using a hash table. `TreeSet` takes `O(log n)` for **search**, **insert** and **delete** which is higher than `HashSet`. But `TreeSet` keeps sorted data. Also, it supports operations like `higher()` (Returns least higher element), `floor()`, `ceiling()`, etc. These operations are also `O(log n)` in `TreeSet` and not supported in `HashSet`. `TreeSet` is implemented using a **self-balancing binary search tree (Red-Black Tree)**. `TreeSet` is backed by `TreeMap` in Java.

2. Ordering
    Elements in `HashSet` are not ordered. `TreeSet` maintains objects in sorted order defined by either `Comparable` or `Comparator` method in Java. `TreeSet` elements are sorted in ascending order by default. It offers several methods to deal with the ordered set like `first()`, `last()`, `headSet()`, `tailSet()`, etc.

3. Null Object
    `HashSet` allows `null` object. `TreeSet` doesn't allow null `Object` and throw `NullPointerException`, Why, because `TreeSet` uses `compareTo()` method to compare keys and `compareTo()` will throw `java.lang.NullPointerException`.

4. Comparison
    `HashSet` uses the `equals()` method to compare two objects in `Set` and for detecting duplicates. `TreeSet` uses `compareTo()` method for same purpose. If `equals()` and `compareTo()` are not consistent, i.e. for two equal objects `equals()` should return true while `compareTo()` should return zero, then it will break the contract of `Set` interface and will allow duplicates in `Set` implementations like `TreeSet`.

> **Note**: If you want a sorted Set then it is better to add elements to `HashSet` and then convert it into `TreeSet` rather than creating a `TreeSet` and adding elements to it.

## When to prefer TreeSet and HashSet?

When choosing between `HashSet` and `TreeSet` in Java, the decision depends on the specific requirements of your program. Both `HashSet` and `TreeSet` are implementations of the `Set` interface and have similar functionalities, but they differ in their characteristics and performance.

- `HashSet`:
    - **Unordered**: `HashSet` does not maintain any particular order of its elements. The elements are stored in an unordered manner, which means you cannot rely on a specific iteration order.
    - **Performance**: `HashSet` provides constant-time performance for basic operations like **add**, **remove**, and **contains** (assuming a good hash function). It is generally faster than `TreeSet`.
    - **Duplicates**: `HashSet` does not allow duplicate elements. If you try to add a duplicate element, it will be ignored.
    - **Implementation**: `HashSet` is implemented using a hash table data structure.

- Use `HashSet` when:
    - You don't require the elements to be ordered.
    - You need fast insertion, deletion, and lookup operations.
    - You want to ensure uniqueness of elements.

- `TreeSet`:
    - **Ordered**: `TreeSet` maintains its elements in sorted order according to their natural ordering or a custom `Comparator` implementation. The elements are sorted as you iterate through the set.
    - **Performance**: `TreeSet` provides logarithmic time complexity for basic operations like **add**, **remove**, and **contains**. It is generally slower than `HashSet` due to the additional overhead of maintaining the sorted order.
    - **No duplicates**: `TreeSet` does not allow duplicate elements. If you try to add a duplicate element, it will be ignored.
    - **Implementation**: `TreeSet` is implemented using a self-balancing binary search tree, usually a red-black tree.

- Use `TreeSet` when:

    - You need the elements to be stored in a sorted order.
    - You require operations like finding the minimum, maximum, or range of - elements efficiently.
    - You want to iterate through the elements in a specific order.

In summary, choose HashSet when you prioritize fast performance and uniqueness of elements, and choose TreeSet when you need elements to be sorted and require additional operations based on the sorted order.

