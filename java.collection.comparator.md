`Comparator` interface is used to order the objects of user-defined classes. A comparator object is capable of comparing two objects of two different classes.

This is one of the most used interfaces in Java. It is useful when there is no natural order or when we wish to compare in a different order.

A `Comparator` interface can be used as a parameter in many standard libraries `sort()`, `binarySearch()`, `min()`, `max()`, `TreeSet()`, `TreeMap()`, `PrioityQueue()` etc.
It can also be used in stream functions like `sorted()`, `min()`, `max()` etc.


A `Comparator` function is used in 2 cases:
1. When the class does not implement `Comparable` interface but you need to sort them in a particular order.
2. When you need to sort the elements in an order which is different than the natural order of sorting.

`Comparator` interface is a functional interface and also of a generic type. Being a functional interface it has only one abstract function:

```java
interface Comparator
{
     .......
     public int compare(T t1, T t2)
     .......
}
```

When two objects are compared as shown above then three possibilities arise:
- A negative value is returned when the `t1` object is smaller.
- 0 is returned when both the objects are the same.
- A positive value is returned when the `t1` object is greater.


### Example 1: Working of the `Comparator` interface to sort the points according to the x-coordinates.

```java
// A sample Java program to implementing
// Comparator alongside Arrays.sort().
import java.util.*;
import java.lang.*;
import java.io.*;

// Point class which does not implement
// Comparable interface. Thus the objects
// of this class are not comparable.
class Point
{
    int x, y;
    Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    // This method is used to return the
    // string version of the point
    public String toString()
    {
        return "(" + x + ", " + y + ")";
    }
}

// This class implements
// Comparator interface to compare
class MyCmp implements Comparator<Point>
{
    // Sorts the Point objects according
    // to x-coordinates in natural order
    public int compare(Point p1, Point p2)
    {
        return p1.x - p2.x;
    }
}

// Main class
class Test
{
    public static void main(String[] args)
    {
        // Array of 3 objects
        Point arr[] = {
            new Point(10, 20),
            new Point(5, 45),
            new Point(25, 35) };

        // Sorting the object containing the array
        // by passing the array and object MyCmp
        Arrays.sort(arr, new MyCmp());

        // Displaying the sorted points
            System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[(5, 45), (10, 20), (25, 35)]
```

### Example 2: A better way to solve this can be to using a lambda expression which do not require the use of creating a different comparator class or object to sort the items.

```java
// A sample Java program to implementing
// Comparator alongside Arrays.sort().
import java.util.*;
import java.lang.*;
import java.io.*;

// Point class which does not implement
// Comparable interface. Thus the objects
// of this class are not comparable.
class Point
{
    int x, y;
    Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    // This method is used to return the
    // string version of the point
    public String toString()
    {
        return "(" + x + ", " + y + ")";
    }
}

// Main class
class Test
{
    public static void main(String[] args)
    {
        // Array of 3 objects
        Point arr[] = {
            new Point(10, 20),
            new Point(5, 45),
            new Point(25, 35) };

        // Instead of creating an object we pass
        // a lambda expression implementing
        // the comparator interface
        Arrays.sort(arr,(p1, p2)-> (p1.x - p2.x));

        // Displaying the sorted points
            System.out.println(Arrays.toString(arr));
    }
}
```

```md
Output:
[(5, 45), (10, 20), (25, 35)]
```

### Example 3: Implementation of a method reference in a `Comparator` interface. This example sorts the array of strings in an unnatural order where the lexicographic order is not followed. Here we have ignored the cases while sorting the strings.

```java
// Java code to apply method reference
// while implementing comparator interface
import java.util.*;
import java.lang.*;

class GfG
{
    public static void main(String args[])
    {
        // Array of strings to be sorted
        String arr[] = {"gfg", "IDE", "GFG"};

        // Arrays.sort() takes the array and
        // a method reference to sort the array
        // Here we have ignored the cases while sorting
        Arrays.sort(arr, String::compareToIgnoreCase);

        // We get gfg before GFG as working on
        // non-primitive types gives a stable algorithm
        // where the order is maintained
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[gfg, GFG, IDE]
```

## Comparator Methods and Examples

- `int compare(t1, t2)`: Compares its two arguments for order.
- `Comparator comparing(KeyExtractor)`: Accepts a function that extracts a `Comparable` sort key from a type T, and returns a `Comparator` that compares by that sort key. For eg, Sorting the Students according to the name by passing a function of getName().
- `Comparator thenComparator(KeyExtractor)`: It returns a lexicographic-order comparator with another comparator. For eg, sorting a Student first by name and then by the roll no.
- `Comparator naturalOrder()`: Returns a comparator that compares `Comparable` objects in a natural order.
- `Comparator reversed()`: Returns a comparator that imposes the reverse ordering of this comparator.
- `Comparator reverseOrder()`: Returns a comparator that imposes the reverse of the natural ordering.
- `Comparator nullFirst(Comparator)`: Returns a null-friendly comparator that considers null to be less than non-null.
- `Comparator nullLast(Comparator)`: Returns a null-friendly comparator that considers null to be greater than non-null.


### Example 1: Working of `nullFirst()` and `naturalOrder()` in Comparator.

```java
// Java program to demonstrate
// Comparator.nullsFirst(java.util.Comparator) method
// and Comparator.naturalOrder() method
import java.util.Arrays;
import java.util.Comparator;

public class GfG
{
    public static void main (String[] args) {
        // Arrays of string
        String[] arr = {"gfg", null, "ide", null};

        // apply nullsFirst method
        // and sort the array in a natural order
        Arrays.sort(arr, Comparator.nullsFirst(Comparator.naturalOrder()));

        // Displaying the Arrays
        System.out.println(Arrays.toString(arr));
    }

}
```
```md
Output:
[null, null, gfg, ide]
```

```java
### Example 2: Working of reverseOrder() in Comparator.

// Java program to demonstrate
// Comparator.nullsFirst(java.util.Comparator) method
// and Comparator.naturalOrder() method
import java.util.Arrays;
import java.util.Comparator;

public class GfG
{
    public static void main (String[] args) {
        // Arrays of string
        String[] arr = {"gfg", "course", "ide"};

        // Sorting the array in reverse order
        Arrays.sort(arr, Comparator.reverseOrder());

        // Displaying the Arrays
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[ide, gfg, course]
```

### Example 3: Sorting the array first by name and then by roll number.

```java
// Java program to demonstrate
// thenComparing()
import java.util.Arrays;
import java.util.Comparator;

// Student class
class Student
{
    // Having name and roll number
    String name;
    int rollNo;

    // Constructor
    Student(String n, int r)
    {
        name = n;
        rollNo = r;
    }

    String getName()
    {
        return name;
    }
    int getRoll()
    {
        return rollNo;
    }
    public String toString()
    {
        return "(" + name + ", " + rollNo + ")";
    }
}
class GfG
{
    public static void main (String[] args) {
        // Arrays of Students with name and rollNo
        Student arr[] = {
            new Student("abc", 120),
            new Student("xyz", 110),
            new Student("abc", 101)
        };

        // Sorting first by name and then by rollNo
        Arrays.sort(arr,
            Comparator.comparing(Student::getName).thenComparing(Student::getRoll));

        // Displaying the Arrays
        System.out.println(Arrays.toString(arr));
    }

}
```
```md
Output:
[(abc, 101), (abc, 120), (xyz, 110)]
```