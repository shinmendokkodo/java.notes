The Arrays class in `java.util` package is a part of the Java Collection Framework. This class provides static methods that implement basic algorithms to dynamically create and access normal Java arrays and not collections. It consists of only static methods and the methods of `Object` class. The methods of this class can be used by the class name itself.

**Example**: Demonstrate the working of `Arrays` class along with `equals()` and `toString()` method.

```java
// Java program to demonstrate
// Arrays class
import java.util.Arrays;

public class GfG {
    public static void main(String[] args) {
        // Get the Arrays
        int a[] = { 10, 20, 30 };

        // Get the second Arrays
        int b[] = { 10, 20, 30 };

        // To compare both arrays
        System.out.println(Arrays.equals(a, b));

        // To represent integers as a string
        System.out.println(Arrays.toString(a));
    }
}
```
```md
true
[10, 20, 30]
```

- `asList()`: This is used to return a fixed-size list backed by the specified array. This is just a wrapper list over an existing collection and does not take any extra space. It supports all the functionalities of the list.
- `static int binarySearch(elementToBeSearched)`: This method search for the specified element in the array with the help of Binary Search algorithm.
- `equals(array1, array2)`: This method checks if both the arrays are equal or not.
- `mismatch(array1, array2)`: This method finds and returns the index of the first unmatched element between the two specified arrays.
- `compare(array 1, array 2)`: This method compares two arrays passed as parameters lexicographically.
- `fill(originalArray, fillValue)`: This method assigns this fillValue to each index of this `Arrays`.
- `sort(originalArray)`: This method sorts the complete array in ascending order.
- `stream(originalArray)`: This method returns a sequential stream with the specified array as its source.
- `toString(originalArray)`: This method returns a `String` representation of the contents of this `Arrays`. The string representation consists of a list of the array’s elements, enclosed in square brackets **(“[]”)**. Adjacent elements are separated by the characters a comma followed by a space. Elements are converted to strings as by `String.valueOf()` function.

## `Arrays.fill()` in Java with Examples

`java.util.Arrays.fill()` method is in `java.util.Arrays` class. This method assigns the specified data type value to each element of the specified range of the specified array.

Syntax:
```java
// Makes all elements of a[] equal to "val"
public static void fill(int[] a, int val)

// Makes elements from from_Index (inclusive)
// to to_Index (exclusive) equal to "val"
public static void fill(int[] a, int from_Index, int to_Index, int val)
```
This method doesn't return any value.

```md
Exceptions it Throws:
IllegalArgumentException - if from_Index > to_Index
ArrayIndexOutOfBoundsException - if from_Index >= a.length
```

Examples:

We can fill entire array.

```java
// Java program to fill a subarray of given array
import java.util.Arrays;

public class Main
{
    public static void main(String[] args)
    {
        int ar[] = {2, 2, 1, 8, 3, 2, 2, 4, 2};
        // To fill complete array with a particular
        // value
        Arrays.fill(ar, 10);
        System.out.println("Array completely filled" +
                  " with 10\n" + Arrays.toString(ar));
    }
}
```
```md
Output:
Array completely filled with 10
[10, 10, 10, 10, 10, 10, 10, 10, 10]
```

We can fill part of array.
```java
// Java program to fill a subarray array with
// given value.
import java.util.Arrays;

public class Main
{
    public static void main(String[] args)
    {
        int ar[] = {2, 2, 2, 2, 2, 2, 2, 2, 2};
        // Fill from index 1 to index 4.
        Arrays.fill(ar, 1, 5, 10);
        System.out.println(Arrays.toString(ar));
    }
}
```
```md
Output:
[2, 10, 10, 10, 10, 2, 2, 2, 2]
```

We can fill a multidimensional array.
We can use a loop to fill a multidimensional array.

1. Fill 2D Array
```java
// Java program to fill a multidimensional array with
// given value.
import java.util.Arrays;

public class Main
{
    public static void main(String[] args)
    {
        int[][] ar = new int[3][4];
        // Fill each row with 10.
        for (int[] row : ar)
            Arrays.fill(row, 10);
        System.out.println(Arrays.deepToString(ar));
    }
}
```
```md
Output:
[
    [10, 10, 10, 10],
    [10, 10, 10, 10],
    [10, 10, 10, 10]
]
```

2. Fill 3D Array
```java
// Java program to fill a multidimensional array with
// given value.

import java.util.Arrays;

class GFG {
    public static void main(String[] args) {
        int[][][] ar = new int[3][4][5];

        // Fill each row with -1.
        for (int[][] row : ar) {
            for (int[] rowColumn : row) {
                Arrays.fill(rowColumn, -1);
            }
        }

        System.out.println(Arrays.deepToString(ar));
    }
}
```
```md
Output:
[
    [
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1]
    ],
    [
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1]
    ],
    [
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1]
    ]
]
```

## Binary Search in Java

`Arrays.binarySearch()` is the simplest and most efficient method to find an element in a sorted array in Java. This is different from the `Collections.binarySearch()` as `Arrays.binarysearch()` works for arrays which can be of primitive data type also but `Collections.binarysearch()` works for objects Collections like `ArrayList` and `LinkedList`.

### It is of two types:
1. Type 1:
    - Declaration:
    ```java
    public static int binarySearch(data_type arr, data_type key)
    ```
    where `data_type` can be any of the primitive data types: `byte`, `char`, `double`, `int`, `float`, `short`, `long` and `Object` as well.

Parameters:
- `arr` – the array to be searched
- `key` – the value to be searched for


2. Type 2:
    - Declaration:
    ```java
    public static int binarySearch(data_type[] arr, int fromIndex, int toIndex, data_type key)
    ```
    where `data_type` can be any of the primitive data types: `byte`, `char`, `double`, `int`, `float`, `short`, `long` and `Object` as well.

Parameters:
- `arr` – the array to be searched
- `fromIndex` – the index of the first element (inclusive) to be searched
- `toIndex` - the index of the last element (exclusive) to be searched
- `key` – the value to be searched for


### Return Values for both the Types
The index of the specified key in the array or if found within the specified range in the specified array.
Otherwise `(-(insertion point + 1))`.

The insertion point is defined as a point at which the specified key would be inserted: the index of the first element in the range greater than the key, or `toIndex` if all elements in the range are less than the specified key.
> Note: This guarantees that the return value will be >= 0 if and only if the key is found.

**Note**: The range within which the specified key to be searched must be sorted (as by the Arrays.sort() method) prior to making this call. Otherwise, the result would be undefined. If the specified array contains multiple values same as the specified key, there is no guarantee which one will be found.

### Example 1: Implementation of `binarySearch()` for a primitive type.

```java
// Java program to demonstrate
// Arrays.binarySearch() method
import java.util.Arrays;

public class GfG {
    public static void main(String[] args)
    {

        // Get the Arrays
        int arr[] = { 10, 20, 25, 40, 40 };

        // Find 20 inside arr
        System.out.println(Arrays.binarySearch(arr, 20));

        // Find 25 inside arr[0, 2]
        System.out.println(Arrays.binarySearch(arr, 0, 3, 25));

        System.out.println(Arrays.binarySearch(arr, 22));
    }
}
```
```md
Output:
1
2
-3
```

### binarySearch() for Non-Primitive types
This is implemented by using a `Comparable` class or a `Comparator` class.

### Example 2: Implementation of `binarySearch()` in a `Comparable` class.

```java
// A sample Java program to implement
// Arrays.binarySearch() for non-primitive types
import java.util.Arrays;

// A user-defined Point class implementing
// Comparable interface
class Point implements Comparable<Point>
{
    int x, y;

    // Costructor intialising x & y
    Point(int x, int y)
    {
        this.x = x;
        this.y = y;
    }

    // compareTo() function defining the
    // nature of sorting i.e., according to
    // x-coordinate
    public int compareTo(Point P)
    {
        // Comparing two objects by
        // Subtracting the passed object
        // from current object
        // This compares the passed element
        // with the middle element and decides
        // whether to go left or right of the array
        return this.x - P.x;
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
            new Point(20, 15),
            new Point(25, 5),
            new Point(40, 100)};

        Point p = new Point(25, 5);

        System.out.println(Arrays.binarySearch(arr, p));
    }
}
```
```md
Output:
2
```

### Example 3: Here the class does not implement `Comparable` interface so we create our own class defining a `Comparator` interface.

```java
// A sample Java program to implement
// Arrays.binarySearch() for non-primitive types
import java.util.*;

// Point class which does not implement
// Comparable interface. Thus the objects
// of this class are not comparable.
class Point
{
    int x, y;

    // Costructor intialising x & y
    Point(int x, int y)
    {
        this.x = x;
        this.y = y;
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
        // Considered the natural order
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
            new Point(20, 15),
            new Point(25, 5),
            new Point(40, 100)};

        Point p = new Point(25, 5);

        // An extra parameter is passed with the
        // object of MyCmp class
        System.out.println(Arrays.binarySearch(
            arr, p, new MyCmp()));
    }
}
```
```md
Output:
2
```

## `Arrays.equals()`

The `Arrays.equals()` method is used to check whether two arrays are equal or not. Two arrays are considered equal if both arrays contain the same number of elements, and all the corresponding pairs of elements in the two arrays are equal. In other words, two arrays are equal if they contain the same elements in the same order. Also, two array references are considered equal if both are null.

### Type 1: Prior to Java 1.9, we only had support of this type with two parameters
1. Declaration:
    ```java
    public static boolean equals(a[], b[])
    ```

2. Parameters:
    - `a[]` - one array to be tested for equality
    - `b[]` - the other array to be tested for equality


### Type 2: After Java 1.9, we had an additional `equals()` method with more parameters.
1. Declaration:
    ```java
    public static boolean equals(a[], aStart, aEnd, b[], bStart, bEnd)
    ```

2. Parameters:
    - `a[]` - one array to be tested for equality
    - `aStart` - Denotes the start position(included) of first array a[]
    - `aEnd` - Denotes the end position(excluded) of the first array a[]
    - `b[]` - the other array to be tested for equality.
    - `bStart` - Denotes the start position(included) of second array b[].
    - `bEnd` - Denotes the end position(excluded) of second array b[].


### Example 1: This program demonstrate the working of `equals()` method.

```java
// Java program to demonstrate
// working of Arrays.equals()
import java.util.Arrays;

public class GfG
{
    public static void main(String[] args)
    {
        // Let us create different integers arrays
        int[] a = {10, 15, 20};
        int[] b = {10, 15, 20};
        int[] c = {15, 10, 20};

        // Compares the arrays a and b
        if (Arrays.equals(a, b))
            System.out.println("Yes");
        else
            System.out.println("No");

        // Compares the arrays a and c
        if (Arrays.equals(a, c))
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
Yes
No
```

### Other Variants of Arrays.equals() method:
```java
public static boolean equals(byte[] a, byte[] a2)
public static boolean equals(short[] a, short[] a2)
public static boolean equals(long[] a, long[] a2)
public static boolean equals(float[] a, float[] a2)
public static boolean equals(double[] a, double[] a2)
public static boolean equals(char[] a, char[] a2)
public static boolean equals(boolean[] a, boolean[] a2)
public static boolean equals(Object[] a, Object[] a2)
```

### Example 2: This program demonstrate the working of `equals()` method in a null condition.

```java
// Java program to demonstrate
// working of Arrays.equals()
import java.util.Arrays;

public class GfG
{
    public static void main(String[] args)
    {
        // Let us create different arrays
        // of Integer wrapper class
        Integer a[] = {10, 15, null, 30};
        Integer b[] = {10, 15, null, 30};

        // Compares the arrays a and b
        if (Arrays.equals(a, b))
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
Yes
```

### Example 3: This program demonstrate the working of `equals()` method in a null condition.

```java
// Java program to demonstrate
// working of Arrays.equals()
import java.util.Arrays;

public class GfG
{
    public static void main(String[] args)
    {
        // Let us create different arrays
        // of Integer wrapper class
        Integer a[] = {10, 15, 30, null};
        Integer b[] = {10, 15, null, 30};

        // Compares the arrays a and b
        if (Arrays.equals(a, b))
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
No
```

### Example 4: This demonstrates the Type 2 of the `equals()` method where we can compare the subarray within two arrays.

```java
// Java program to demonstrate
// working of Arrays.equals()
import java.util.Arrays;

public class GfG
{
    public static void main(String[] args)
    {
        // Let us create different arrays
        // of Integer wrapper class
        Integer a[] = {10, 20, 30, 40, 60};
        Integer b[] = {30, 40, 60, 5, 8};

        // Compares the arrays a[2, 3, 4] and b[0, 1, 2]
        if (Arrays.equals(a, 2, 5, b, 0, 3))
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
Yes
```

In addition to the above two versions, we have two more versions where a comparator can be passed added to Java 9 and above.
- `boolean equals(a[], b[], Comparator)`: Simply matches two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered.
- `boolean equals(a[], aStart, aEnd, b[], bStart, bEnd, Comparator)`: Simply matches two sub-arrays within two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered. Here the start index is inclusive and the end ended is exclusive.

### Example 5: Demonstrating the working of `equals()` method in Java for non-primitive types.
The `Comparator` is a functional interface. Therefore using this we don't need to create a separate class or instance, instead, we can simply pass a lambda expression or a method reference to make the operation run.

```java
// Java code to demonstrate
// equals() method in java
import java.util.*;

class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays of
        // non-primitive types
        String a[] = {"GFG", "IDE"};
        String b[] = {"Gfg", "ide"};

        // Comparing using our own comparator
        // where we have ignored the cases
        // A method reference is passed
        if(Arrays.equals(a, b, String::compareToIgnoreCase))
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
Yes
```

## Arrays.mismatch()

The `mismatch()` finds and returns the index of the first unmatched element between the two specified arrays. It returns `-1` if both the specified arrays are same. This was introduced in Java 9.

### We have 4 versions of `mismatch()` method in Java:
- `int mismatch(a[], b[])`: Simply matches two arrays of primitive types.
- `int mismatch(a[], aStart, aEnd, b[], bStart, bEnd)`: Simply matches two subarrays within two arrays of primitive types. Here the start index is inclusive and the end ended is exclusive.
- `int mismatch(a[], b[], Comparator)`: Simply matches two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered.
- `int mismatch(a[], aStart, aEnd, b[], bStart, bEnd, Comparator)`: Simply matches two sub-arrays within two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered. Here the start index is inclusive and the end ended is exclusive.

### Example 1: Demonstrating the working of `mismatch()` method in Java

```java
// Java code to demonstrate
// mismatch() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays
        int a[] = {10, 20, 30};
        int b[] = {10, 20, 30};
        int c[] = {10, 20, 40, 30};

        // Matching a and b
        System.out.println(Arrays.mismatch(a, b));

        // Matching a and c
        System.out.println(Arrays.mismatch(a, c));

        // Matching a and b subarrays
        System.out.println(Arrays.mismatch(
            a, 0, 2, b, 0, 2));
    }
}
```
```md
Output:
-1
2
-1
```

> **Note**: For non-primitive types the `mismatch()` method uses the `equal()` method internally to compare the objects.

### Example 2: Demonstrating the working of `mismatch()` method in Java for non-primitive types.

The `Comparator` is a functional interface. Therefore using this we don't need to create a separate class or instance, instead, we can simply pass a lambda expression or a method reference to make the operation run.

```java
// Java code to demonstrate
// mismatch() method in java
import java.util.*;

class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays of
        // non-primitive types
        String a[] = {"GeeksforGeeks", "IDE"};
        String b[] = {"geeksforgeeks", "Courses"};

        // Comparing using our own comparator
        // where we have ignored the cases
        // A method reference is passed
        System.out.println(
            Arrays.mismatch(
                a, b, String::compareToIgnoreCase));
    }
}
```
```md
Output:
1
```

## `Arrays.compare()`

The `compare()` method in Java lexicographically compares two class specific objects (`x`, `y`) given as parameters. It returns the value:
- 0: if (x == y)
- -1: if (x < y)
- 1: if (x > y)


### We have 4 versions of `compare()` method in Java:
- `int compare(a[], b[])`: Simply compares two arrays of primitive types.
- `int compare(a[], aStart, aEnd, b[], bStart, bEnd)`: Simply compare two subarrays within two arrays of primitive types. Here the start index is inclusive and the end ended is exclusive.
- `int compare(a[], b[], Comparator)`: Simply compares two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered.
- `int compare(a[], aStart, aEnd, b[], bStart, bEnd, Comparator)`: Simply compares two sub-arrays within two arrays of non-primitive types or where a user-defined `Comparator` case of generic type is needed to be considered. Here the start index is inclusive and the end ended is exclusive.


### Example 1: Demonstrating the working of `compare()` method in Java

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays
        int a[] = {10, 20, 15};
        int b[] = {10, 20, 30};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
a is smaller
```

### Example 2: Demonstrating the working of `compare()` method in Java

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays
        int a[] = {10, 20, 40};
        int b[] = {10, 20, 30};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
a is greater
```

### Example 3: Demonstrating the working of `compare()` method in Java

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays
        int a[] = {10, 20, 30, 40};
        int b[] = {10, 20, 30};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
a is greater
```

### Example 4: Demonstrating the working of `compare()` method in Java

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays
        int a[] = {10, 20, 15};
        int b[] = {10, 200, 30};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
a is smaller
```

### Example 5: Demonstrating the working of `compare()` method in Java in Non-primitive type.

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays of
        // non-primitive types
        Integer a[] = {10, 20, null, 15};
        Integer b[] = {10, 20, -30, 40};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
a is smaller
```

### Example 6: Demonstrating the working of `compare()` method in Java in Non-primitive type.

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays of
        // non-primitive types
        Integer a[] = {10, 20, 30};
        Integer b[] = {10, 20, 30};

        // Comparing both the Arrays
        int res = Arrays.compare(a, b);

        // Checking them lexicographically
        if (res == 0)
            System.out.println("Same");
        else if (res > 0)
            System.out.println("a is greater");
        else
            System.out.println("a is smaller");

    }
}
```
```md
Output:
Same
```

### Example 7: Demonstrating the third version of `compare()` method where we pass our own `Comparator`.
The `Comparator` is a functional interface. Therefore using this we don't need to create a separate class or instance, instead, we can simply pass a lambda expression or a method reference to make the operation run.

```java
// Java code to demonstrate
// compare() method in java
import java.util.*;

public class Test
{
    public static void main (String[] args)
    {
        // Intializing the arrays of
        // non-primitive types
        String a[] = {"GfG", "IDE"};
        String b[] = {"gfg", "ide"};

        // Comparing using our own comparator
        // where we have ignored the cases
        if(compare(a, b, String::compareToIgnoreCase) == 0)
            System.out.println("Yes");
        else
            System.out.println("No");
    }
}
```
```md
Output:
Yes
```

## `Arrays.asList()`

The `asList()` method of `java.util.Arrays` class is used to return a fixed-size list backed by the specified array. This method acts as bridge between array-based and collection-based APIs, in combination with `Collection.toArray()`. The returned list is serializable and implements `RandomAccess`.

**Syntax**:
```java
public static List asList(T... a)
```


**Parameters**: This method takes the array a which is required to be converted into a **`List`**.

**Return Value**: This method returns a list view of the specified array.


### Example 1: Working of `asList()` method in Java

```java
// Java program to demonstrate
// asList() method for String value
import java.util.*;

public class GFG {

    public static void main(String[] args) {
        // creating Arrays of String type
        String arr[] = { "GfG", "IDE", "Courses"};

        // getting the list view of Array
        List<String> list = Arrays.asList(arr);

        // printing the list
        System.out.println(list);
    }
}
```
```md
Output:
[GfG, IDE, Courses]
```

### Example 2: Internal working of `asList()` method in Java

```java
// Java program to demonstrate modifications
// through asList() method
import java.util.*;

public class GFG {
    public static void main(String[] args) {
        // creating Arrays of String type
        String arr[] = {"GfG", "IDE", "Courses"};

        // getting the list view of Array
        List<String> list = Arrays.asList(arr);

        // Modifying the array gets reflected
        // in the list
        arr[0] = "Practice";

        // printing the list
        // "GfG" is replaced by "Practice"
        System.out.println(list);

        // Modifying the list reflect changes
        // in the array
        list.set(1, "Premium");

        // "IDE" is replaced by "Premium"
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[Practice, IDE, Courses]
[Practice, Premium, Courses]
```

> **NOTE**: Since the list is a fixed size and it is just working on the created array, nothing can be added or removed from the list in Java.

### Application of `asList()` in Java

#### Reversing a list.

```java
// Java program to demonstrate reversing
// a list
import java.util.*;

public class GFG {
    public static void main(String[] argv)
    {
        // creating Arrays of String type
        String arr[] = {"GfG", "IDE", "Courses"};

        // Reversing the list
        // In-place conversion
        Collections.reverse(Arrays.asList(arr));

        // Printing the array
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[Courses, IDE, GfG]
```

#### Creating a Collection from the array elements
```java
// Java program to demonstrate
// creating of any collection using list
import java.util.*;

public class GFG {
    public static void main(String[] args) {
        // creating Arrays of String type
        String arr[] = {"GfG", "IDE", "Courses"};

        // Creating a collection out of a list
        // Any collection within the collection
        // interface can be created from a list
        HashSet<String> s = new HashSet<String>(Arrays.asList(arr));

        // Printing the HashSet
        System.out.println(s);
    }
}
```
```md
Output:
[GfG, Courses, IDE]
```
> Note 1: Similarly any other collection like a `PriorityQueue` can also be quickly created without taking the overheads of traversing the array and adding every element one by one to the queue. Therefore creating a list using `asList()` method and converting them to a collection is a faster way of getting a collection with the same content.

> Note 2: The order of output may vary as `HashSet` follows random order of storage.

## `Arrays.toString()`

The `Arrays.toString()` method in Java is used to return a string representation of the contents of the specified array.


### Example 1:

```java
// Java Program Demonstrate
// toString() method in Java
import java.util.Arrays;

class GFG {
    public static void main(String[] args)
    {
        // This is a primitive array
        int arr[] = {10, 20, 30};

        // Normal printing of the array
        System.out.println(arr);

        // Converts th arrays to String and the print
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[I@232204a1
[10, 20, 30]
```

> Note 1: The function can take an array of primitive type as an argument or an array of Object type where object is the root of everything.

> Note 2: If an array of character type is printed normally without using the `toString()` method, then it displays the array fine. However, for any other data type, we need to use the `toString()` method.

## Example 2: Let's look at an array of non-primitive type and how can it be represented using a user-defined class.

```java
// Java Program Demonstrate
// stream in Java
import java.util.*;
import java.lang.*;

// user-defined class
class Point {
    int x, y;

    // constructor to assign values
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // toString() method to print
    // string in comma representation
    public String toString() {
        return "(" + x + ", " + y + ")";
    }
}

// Main class
class GFG {
    public static void main(String[] args) {
        // This is a non-primitive
        // array of Point type
        Point arr[] = {
            new Point(10, 20),
            new Point(5, 30)
        };

        // Converts th arrays using user-defined class
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[(10, 20), (5, 30)]
```