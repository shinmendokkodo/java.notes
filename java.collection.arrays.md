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


We can fill a multidimensional array
We can use a loop to fill a multidimensional array.
1)Fill 2D Array

// Java program to fill a multidimensional array with
// given value.
import java.util.Arrays;

public class Main
{
    public static void main(String[] args)
    {
        int [][]ar = new int [3][4];

        // Fill each row with 10.
        for (int[] row : ar)
            Arrays.fill(row, 10);

        System.out.println(Arrays.deepToString(ar));
    }
}
Output:
[[10, 10, 10, 10], [10, 10, 10, 10], [10, 10, 10, 10]]


2) Fill 3D Array


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

Output:
[[[-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1]], [[-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1]], [[-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1], [-1, -1, -1, -1, -1]]]

