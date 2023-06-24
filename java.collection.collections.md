# Collection class in Java

Any group of individual objects which are represented as a single unit is known as the collection of the objects. In Java, a separate framework named the “**Collection Framework**” has been defined in JDK 1.2 which holds all the collection classes and interface in it.

The `Collection` interface (`java.util.Collection`) and `Map` interface (`java.util.Map`) are the two main “***root***” interfaces of Java Collection classes. All the methods present in the collection class are static, thus there is no requirement of creating any other instance to call those methods, thus saving the extra effort.

Let's take a look at some most important methods of the `Collection` class.

**Collection Methods**: These are applied to things implementing collection interface.

- `min(C)`: This is used to return the minimum element of the given collection, according to the natural ordering of its elements.

- `min(Collections, Comparator)`: This is used to return the minimum element of the given collection, according to the order induced by the specified comparator.

- `max(C)`: This is used to return the maximum element of the given collection, according to the natural ordering of its elements.

- `max(Collections, Comparator)`: This is used to return the maximum element of the given collection, according to the order induced by the specified comparator.

- `disjoint(c1, c2)`: It is used to check whether two specified collections are disjoint or not. More formally, two collections are disjoint if they have no elements in common. This returns true if the two specified collections have no elements in common.

- `frequency(c, Obj)`: It is used to get the frequency of an object Obj present in the specified list of `Collection` c. More formally, it returns the number of elements Obj in the collection.


**List Methods**: These are applied to things implementing `List` interface.
- `binarySearch(l, key)`: This method returns the position of a `key` in a sorted list `l`. If the `key` is not present, it returns "`-(insertion_point + 1)`".
    > The insertion point is defined as the point at which the key would be inserted into the list.

    It has two versions, one to implement the `Comparable` interface and the other to implement a `Comparator` interface.

- `copy(dest, src)`: is used to copy all of the elements from the source list(`src`) to a destination list(`dest`). The destination list must be at least as long as the source list. If it is longer, the remaining elements in the destination list are unaffected.

- `fill(l, obj)`: This is used to replace all of the elements of the specified list(`l`) with the specified object(`obj`).

- `indexOfSubList(srcL, targetL)`: This is used to return the starting position of the first occurrence of the specified target list within the specified source list, or `-1` if there is no such occurrence. More formally, returns the lowest index `i` such that `source.subList(i, i+target.size()).equals(target)`, or `-1` if there is no such index. (Returns `-1` if `target.size() > source.size()`).

- `lastIndexOfSubList(srcL, targetL)`: This is used to return the last position of the first occurrence of the specified target list within the specified source list, or `-1` if there is no such occurrence.

- `replaceAll(l, old, new)`: This is used to Replaces all occurrences of an old value in a list with another new value.

 - `reverse()`: This simply reverses all the element in a list.

- `rotate(l, dist)`: It is used to rotate the elements present in the specified list of `Collection` by a given distance in a clockwise manner.

- `sort(l)`: This sorts the given list. It has two versions, one to implement the `Comparable` interface and the other to implement a `Comparator` interface.

- `swap(l, i, j)`: This swaps the element present in position `i` and `j` in a specified list `l`.


**Other Methods**:

- `reverseOrder()`: This method reverses the natural ordering. We can provide a `Comparator` that imposes reverse order of a passed `Comparator` object. We can use this method to sort a list in reverse order of user-defined `Comparator`.

- `synchronizedList(l)`: is used to return a synchronized (thread-safe) list backed by the specified list. They provide a better implementation in a multi-threaded environment than the vector which is a legacy class. This method takes the list as a parameter to be “wrapped” in a synchronized list. Here it is not recommended to make changes to the original collection.

- `synchronizedMap(m)`: is used to return a synchronized (thread-safe) map backed by the specified map. This method takes the map as a parameter to be “wrapped” in a synchronized map. Being modern methods, they provide a better implementation in a multi-threaded environment. Here it is not recommended to make changes to the original collection.

- `synchronizedSet(s)`: is used to return a synchronized (thread-safe) set backed by the specified set. This method takes the set as a parameter to be “wrapped” in a synchronized set. Being modern methods, they provide a better implementation in a multi-threaded environment. Here it is not recommended to make changes to the original collection.

- `unmodifiableList(l)`: This is used to return an unmodifiable or immutable view of the specified list. This method allows modules to provide users with “read-only” access to internal lists. Query operations on the returned list “read through” to the specified list and any attempt to modify the returned list, whether direct or via its iterator, result in an `UnsupportedOperationException`.

- `unmodifiableMap(m)`: This is used to return an unmodifiable or immutable view of the specified map. This method allows modules to provide users with “read-only” access to internal map. Query operations on the returned map “read through” to the specified map and any attempt to modify the returned map, whether direct or via its iterator, result in an `UnsupportedOperationException`.

- `unmodifiableSet(s)`: This is used to return an unmodifiable or immutable view of the specified set. This method allows modules to provide users with “read-only” access to the internal set. Query operations on the returned set “read through” to the specified set and any attempt to modify the returned set, whether direct or via its iterator, result in an `UnsupportedOperationException`.


**Example**:

```java
// Java code to illustrate working
// of few methods of Collections class
import java.util.*;

class GfG {
    public static void main (String[] args) {
        // Creating a list of ArrayList type
        List<Integer> l = new ArrayList<>();

        // Adding element to the lisusing add() method
        l.add(10);
        l.add(5);
        l.add(30);

        // Sorting the list in the natural order
        Collections.sort(l);
        System.out.println(l);

        // Reversing the content of the list
        Collections.reverse(l);
        System.out.println(l);
    }
}
```
```md
Output:
[5, 10, 30]
[30, 10, 5]
```

## `Collections.fill()`

The `fill()` method of `java.util.Collections` class is used to replace all of the elements of the specified list with the specified element.

**Function Declaration**:
```java
public static<T> void fill(List<?super T> list, T obj)
```

This is a generic function declaration signified by `<T>` with the following content.
- `obj` - The element with which to fill the specified list. It is of `T` type
- `list` - The list to be filled with the specified element. The type of the list is dependent on the type of `obj` i.e., `T`. If an object is of type `T` then the list type must be of type `T` or an ancestor of `T`. This is understood by the `super` keyword.
- The `?` denotes the wildcard in generic programming. It represents an unknown type. The wildcard can be used in a variety of situations such as the type of a parameter, field, or local variable; sometimes as a return type.


**Example**:

```java
// Java program to demonstrate
// fill() method
// for Integer value

import java.util.*;

public class GFG {
    public static void main(String[] args) {

        // creating object of List<Integer>
        List<Integer> al = new ArrayList<Integer>();

        // Adding element to srclst
        al.add(10);
        al.add(20);
        al.add(30);

        // fill the list
        Collections.fill(al, 5);

        // print the elements
        System.out.println(al);
    }
}
```
```md
Output:
[5, 5, 5]
```

## `Collections.reverse()`

`Collections.reverse()` method is a `java.util.Collections` class method. It reverses the order of elements in a list passed as an argument.

### Reversing an ArrayList or LinkedList.

```java
// Java program to demonstrate
// Collections.reverse() method
import java.util.*;

public class GFG {
    public static void main(String[] args) {

        // creating object of List<Integer>
        List<Integer> list = new ArrayList<Integer>();

        // For a linked list
        // List<Integer> list = new LinkedList<Integer>();

        // Adding element to list
        list.add(10);
        list.add(20);
        list.add(30);

        // print the elements
        System.out.println(list);

        // Reversing the list
        Collections.reverse(list);

        // print the elements
        System.out.println(list);
    }
}
```
```md
Output:
[10, 20, 30]
[30, 20, 10]
```

> **Note**: For Linkedlist, we just need to replace ArrayList with LinkedList in the declaration part `List mylist = new ArrayList();` as commented in the code.

**Reversing an Array**: Arrays class in Java doesn't have reverse method. We can use `Collections.reverse()` to reverse an array also by using `asList()` method.

```java
// Java program to reverse an array
// with Collections.reverse()
import java.util.*;

public class GfG {
    public static void main(String[] args) {
        // Create an array of integers
        Integer arr[] = {10, 20, 30};

        // creating List<Integer>
        List<Integer> list = Arrays.asList(arr);

        // Printing array
        System.out.println(Arrays.toString(arr));

        // Reversing the list
        Collections.reverse(list);

        // Printing array
        System.out.println(Arrays.toString(arr));
    }
}
```
```md
Output:
[10, 20, 30]
[30, 20, 10]
```

## `Collections.binarySearch()`

`Collections.binarySearch()` method is a `java.util.Collections` class method that returns the position of an object in a sorted list. If the key is not present, it returns "`-(insertion_point + 1)`". The insertion point is defined as the point at which the key would be inserted into the list.

### Searching an integer key in a list sorted in ascending order:

```java
// Java program to demonstrate working of Collections.
// binarySearch()
import java.util.List;
import java.util.ArrayList;
import java.util.Collections;

public class GFG {
    public static void main(String[] args) {
        List al = new ArrayList();
        al.add(1);
        al.add(2);
        al.add(3);
        al.add(10);
        al.add(20);

        // 10 is present at index 3.
        int index = Collections.binarySearch(al, 10);
        System.out.println(index);

        // 13 is not present. 13 would have been inserted
        // at position 4. So the function returns (-4-1)
        // which is -5.
        index = Collections.binarySearch(al, 13);
        System.out.println(index);
    }
}
```
```md
Output:
3
-5
```

### Important points related to `Collections.binarySearch()` and `Arrays.binarySearch()`

- Unlike the `Arrays.binarySearch()` the `Collections.binarySearch()` does not take any ranges. It just takes the element to be searched.
- If the input list is not sorted, the results are undefined.
- If there are duplicates, there is no guarantee which one will be found.
- `Arrays.binarySearch()` works for arrays which can be of primitive data type also. `Collections.binarySearch()` works for objects `Collections` like `ArrayList` and `LinkedList`.
- List or any java `Collections` is only for non-primitive types.
    ```java
    List list = new ArrayList();
    ```
- The class must either implement `Comparable` or we must provide an object of the class that implements the `Comparator`.
- Since a linked list does not have random access thus performing the binary search operation will take `O(n)` for `O(log n)` object comparisons because the middle point needs to be found which takes linear time in a linked list.
- If `Collections.binarySearch()` is used for `ArrayList`, then the time complexity will be `O(log n)` for `O(log n)` object comparisons because of direct access.
- There are just ***two*** binary search declarations in `Collections` class and ***multiple*** binary search declarations in `Arrays` class.

## `Collections.max()` and `Collections.min()`

`Collections.max()`: The `max()` method of `java.util.Collections` class is used to return the maximum element of the given collection, according to the natural ordering of its elements. This method can implement collection interfaces like `LinkedList`, `ArrayList`, `HashSet`, `ArrayDeque` etc. All elements in the collection must implement the `Comparable` interface. Furthermore, all elements in the collection must be mutually comparable (that is, `e1.compareTo(e2)` must not throw a `ClassCastException` for any elements `e1` and `e2` in the collection).

### Example 1:

```java
// Java program to demonstrate
// max() method
import java.util.*;

public class GFG {
    public static void main(String[] args) {

        // creating object of LinkedList
        List<Integer> list = new ArrayList<Integer>();

        // Adding element to list
        list.add(10);
        list.add(5);
        list.add(20);

        // prining the max value
        // using max() method
        System.out.println(Collections.max(list));
    }
}
```
```md
Output:
20
```

`Collections.min()`: The `min()` method of `java.util.Collections` class is used to return the minimum element of the given collection, according to the natural ordering of its elements. All elements in the collection must implement the `Comparable` interface. Furthermore, all elements in the collection must be mutually comparable (that is, `e1.compareTo(e2)` must not throw a `ClassCastException` for any elements `e1` and `e2` in the collection).

### Example 2:

```java
// Java program to demonstrate
// min() method
import java.util.*;

public class GFG {
    public static void main(String[] args) {

        // creating object of LinkedList
        List<Integer> list = new ArrayList<Integer>();

        // Adding element to list
        list.add(10);
        list.add(5);
        list.add(20);

        // prining the min value
        // using min() method
        System.out.println(Collections.min(list));
    }
}
```
```md
Output:
5
```


## Example 3: Applying `Collections.max()` for a list containing user-defined objects.

```java
// Java program to demonstrate
// max() method
import java.util.*;
import java.lang.*;
import java.io.*;

// A user-defined Point class implementing
// Comparable interface
class Point implements Comparable<Point> {
    int x, y;
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // compareTo() function defining the
    // nature of order i.e., according to
    // x-coordinate
    public int compareTo(Point p) {
        return this.x - p.x;
    }
}

class GFG {
    public static void main(String[] args) {
        // creating object of ArrayList
        List<Point> list = new ArrayList<Point>();

        // Adding element to list
        list.add(new Point(5, 20));
        list.add(new Point(25, 10));
        list.add(new Point(10, 40));

        Point p = Collections.max(list);

        // Replacing the above with this
        // Point p = Collections.min(list);
        // gives the minimum pair

        // prining the max value
        // using max() method
        System.out.println(p.x + " " + p.y);
    }
}
```
```md
Output:
25 10
```

### Example 4: Applying `Collections.max()` for a list containing user-defined objects but not the `Comparable` interface. Instead we will be using a `Comparator` function.

```java
// Java program to demonstrate
// max() method
import java.util.*;
import java.lang.*;
import java.io.*;

// Point class which does not implement
// Comparable interface. Thus the objects
// of this class are not comparable.
class Point {
    int x, y;
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

// This class implements
// Comparator interface
class MyCmp implements Comparator<Point> {
    // Sorts the Point objects according
    // to x-coordinates in natural order
    public int compare(Point p1, Point p2) {
        return p1.x - p2.x;
    }
}

class GFG {
    public static void main(String[] args) {
        // creating object of LinkedList
        List<Point> list = new ArrayList<Point>();

        // Adding element to list
        list.add(new Point(5, 20));
        list.add(new Point(25, 10));
        list.add(new Point(10, 40));

        // To get the maximum elements
        Point p = Collections.max(list, new MyCmp());

        // For minimum elements
        // Point p = Collections.min(list, MyCmp())

        // prining the max value
        // using max() method
        System.out.println(p.x + " " + p.y);
    }
}
```
```md
Output:
25 10
```

### Example 5:Finding maximum in an array using a Wrapper Class which are of Non-Primitive types. As this `max()` or `min()` method cannot be used for Primitive data types.

```java
// Java program to demonstrate
// max() method
import java.util.*;
import java.lang.*;
import java.io.*;

class GFG {
    public static void main(String[] args) {
        // Array of numbers
        Integer[] arr = {10, 20, 40, 15};

        // First converting array to list
        // Then getting the max item
        Integer res = Collections.max(Arrays.asList(arr));

        // prining the max value
        // using max() method
        System.out.println(res);
    }
}
```
```md
Output:
40
```

## `Collections.frequency()`

`Collections.frequency()` method is present in `java.util.Collections` class. It is used to get the frequency of an element present in the specified list of `Collection`. More formally, it returns the number of elements in the collection. It works for collections that implement collection interface like `ArrayList`, `LinkedList`, `ArrayDeque` etc.

- **Declaration**:
    ```java
    public static int frequency(Collection<?> c, Object o)
    ```


- **Parameters**:
    - `c` - the collection in which to determine the frequency of `o`
    - `o` - the object whose frequency is to be determined


- **Returns**: Returns the number of elements in the specified collection equal to the specified object.

### Example 1:

```java
// Java program to demonstrate working of
// Collections.frequency()
import java.util.*;

public class GfG {
    public static void main(String[] args) {
        // Let us create a list of strings
        List<Integer> list = new ArrayList<Integer>();
        list.add(10);
        list.add(20);
        list.add(10);

        // Count the frequency of 10
        System.out.println(Collections.frequency(list, 10));
    }
}
```
```md
Output:
2
```

### Example 2:

This discusses the implementation of `frequency()` method using a user-defined type. In this `Collections.frequency()` uses equal function internally. The `equals()` method returns true if both the string refers to the same in object. If they don't refer to the same object then the equal function returns `false`. This is the reason why we get `0` for the above code as all of the created objects using new operator refers to different locations of reference.

```java
// Java program to demonstrate
// frequency() method for a user
// defined type
import java.util.*;

class Point {
    int x, y;
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}

public class GFG {
    public static void main(String[] args) {
        // creating object of LinkedList
        List<Point> list = new ArrayList<Point>();

        // Adding element to list
        list.add(new Point(10, 20));
        list.add(new Point(5, 25));
        list.add(new Point(10, 20));

        Point p = new Point(10, 20);

        int freq = Collections.frequency(list, p);

        // printing the frequency
        System.out.println(freq);
    }
}
```
```md
Output:
0
```

To get the correct output as `2`, we need to override the equal function.
Let's look at the implementation:

```java
// Java program to demonstrate
// frequency() method for a user
// defined type
import java.util.*;

class Point {
    int x, y;
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    @Override
    public boolean equals(Object o) {
        if (o == this)
            return true;
        if (!o instanceof Point)
            return false;
        Point p = (Point)o;
        return p.x == x && p.y == y;
    }
}

class GFG {
    public static void main(String[] args) {
        // creating object of LinkedList
        List<Point> list = new ArrayList<Point>();

        // Adding element to list
        list.add(new Point(10, 20));
        list.add(new Point(5, 25));
        list.add(new Point(10, 20));

        Point p = new Point(10, 20);

        int freq = Collections.frequency(list, p);

        // prining the frequency
        System.out.println(freq);
    }
}
```
```md
Output:
2
```

### Example 2: Using `Collection.frequency()` to count frequencies of an element in normal Array by using `asList()`.

```java
// Java program to demonstrate working of
// Collections.frequency()
import java.util.*;

class GfG {
    public static void main(String[] args) {
        // Array of Integer type
        Integer arr[] = { 10, 15, 10, 20 };

        // asList() is efficient as it just creates
        // a wrapper over the same array and coverts the
        // array to a list
        int res = Collections.frequency(Arrays.asList(arr), 10);

        // Count the frequency of 10
        System.out.println(res);
    }
}
```
```md
Output:
2
```

---

## Finding the minimum element in a Collection

The `min(Collection c)` method can be used to find the minimum element in a `Collection`. The elements present in the `Collection` must implement the `Comparable` interface. If the elements do not implement the `Comparable` interface, we can use another overloaded method, `min(Collection c, Comparator comp)`. This method takes a `Comparator` as an argument that is used to compare the elements. This method iterates over the entire collection; hence it requires time proportional to the size of the collection.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ArrayListDemo {
	public static void main(String args[]) {
		List<Integer> list = new ArrayList<>();
		list.add(34);
		list.add(12);
		list.add(9);
		list.add(76);
		list.add(29);
		list.add(75);

		System.out.println("The minimum element in the List is: " + Collections.min(list));
	}
}
```

## Finding the maximum element in a Collection

The `max(Collection c)` method can be used to find the maximum element in a `Collection`. The elements present in the `Collection` must implement the `Comparable` interface. If the elements do not implement the `Comparable` interface, we can use another overloaded method `max(Collection c, Comparator comp)`. This method takes a `Comparator` as an argument that is used to compare the elements. This method iterates over the entire `Collection`; hence it requires time proportional to the size of the `Collection`.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ArrayListDemo {
	public static void main(String args[]) {
		List<Integer> list = new ArrayList<>();
		list.add(34);
		list.add(12);
		list.add(9);
		list.add(76);
		list.add(29);
		list.add(75);

		System.out.println("The maximum element in the List is: " + Collections.max(list));
	}
}
```

## Finding the frequency of elements in a Collection

There is a `frequency(Collection c, object o)` method that can be used to find the frequency of a given element in the `Collection`. This method iterates the entire Collection so the time complexity is proportional to the size of the collection.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ArrayListDemo {

	public static void main(String args[]) {
		List<Integer> list = new ArrayList<>();
		list.add(9);
		list.add(12);
		list.add(9);
		list.add(76);
		list.add(9);
		list.add(75);

		System.out.println("Total number of times,9 is present in the List is: " + Collections.frequency(list, 9));
	}
}
```
```md
Total number of times,9 is present in the List is: 3
```

## Searching an element in a Collection

The `binarySearch(List list, T key)` method searches the specified list for the specified object using the binary search algorithm. The elements added in the `List` must implement the `Comparable` interface, and the list must be sorted into ascending order before making this call. If it is not sorted, the results are undefined. If the list contains multiple elements equal to the specified object, there is no guarantee which one will be found.

If the elements added to our List do not implement the `Comparable` interface, then we can use another overloaded version of `binarySearch(List list, T key, Comparator comp)`, which takes a `Comparator` for the input as well. The list must be sorted into ascending order according to the specified comparator.

If the element is not present in the list, then this method returns a position where the element can be inserted.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionsDemo {
	public static void main(String args[]) {
		List<Integer> list = new ArrayList<>();
		list.add(9);
		list.add(12);
		list.add(34);
		list.add(54);
		list.add(66);
		list.add(76);

		System.out.println("The minimum element in the List is: " + Collections.binarySearch(list, new Integer(222)));
	}
}
```
```md
The minimum element in the List is: -7
```

## Copying a list into another list

The `copy(List dest, List src)` method is used to copy all the elements from a source list to a destination list. If the size of the destination list is smaller than the source list, then `IndexOutOfBoundsException` is thrown. After the operation, the index of each copied element in the destination list will be identical to its index in the source list.

Let’s consider an example to understand this.

```java
List dest = 10,20,30,40,50,60;
List src = 1,2,3;
Collections.copy(dest, src);
```

After doing the above operation, the dest list will become:

```md
{1,2,3,40,50,60}
```

So the `copy()` method does not merge the elements of the two lists. It replaces the elements in the destination list from the elements in the source list.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class CollectionsDemo {
	public static void main(String args[]) {
		List<Integer> list1 = new ArrayList<>();
		list1.add(9);
		list1.add(12);
		list1.add(34);
		list1.add(54);
		list1.add(66);
		list1.add(76);

		List<Integer> list2 = new ArrayList<>();
		list2.add(90);
		list2.add(12);
		list2.add(98);
		list2.add(43);

		Collections.copy(list1, list2);

		System.out.println(list1);
	}
}
```
```md
[90, 12, 98, 43, 66, 76]
```

## Filling a list with a default value

The `fill(List list, Object obj)` method replaces all of the elements of the specified list with the specified element. This method is very useful if we want to reset our `List` to a default value.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class ArrayListDemo {

	public static void main(String args[]) {
		List<Integer> list = new ArrayList<>();
		list.add(34);
		list.add(45);

		Collections.fill(list, 10);

		System.out.println(list);
	}
}
```
```md
[10, 10]
```

## Making Collections Unmodifiable

Let’s say we have created a collection where we have added some important data. We want others to read this data, but they should not be allowed to modify the data in this `Collection`. The `Collections` class provides certain methods that can be used to make our `Collection` unmodifiable. These methods return a collection in which if someone tries to add or remove an element, then `UnsupportedOperationException` is thrown.

This feature is particularly useful if our `Collection` contains some sensitive data. We need to only give read access to our data, but we don’t want others to accidentally modify it.

Following is the list of methods available to make Collections unmodifiable:
1. `unmodifiableList(List<? extends T> list)`
2. `unmodifiableSet(Set<? extends T> s)`
3. `unmodifiableMap(Map<? extends K, ? extends V> m)`
4. `unmodifiableCollection(Collection<? extends T> c)`
5. `unmodifiableSortedMap(SortedMap<K,? extends V> m)`
6. `unmodifiableSortedSet(SortedSet<T> s)`

We will not look at examples of each of these methods, as they are essentially the same. We will only look at `unmodifiableList()`.

### Making `ArrayList` unmodifiable

Any `List` implementation such as an `ArrayList` or `LinkedList` can be made unmodifiable by using the `unmodifiableList(List list)` method of the `Collections` class. If we try to add or remove elements from the returned list, then `UnsupportedOperationException` will be thrown as shown in the below example.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class UnmodifiableArrayList {
	public static void main(String args[]) {
		List<String> list = new ArrayList<String>();
		list.add("India");
		list.add("USA");
		list.add("Russia");

		List<String> unmodifiableList = Collections.unmodifiableList(list);
		// This will throw exception because element can't be added to unmodifiable list.
		unmodifiableList.add("China");
	}
}
```
```md
Exception in thread "main" java.lang.UnsupportedOperationException
	at java.util.Collections$UnmodifiableCollection.add(Collections.java:1057)
	at UnmodifiableArrayList.main(UnmodifiableArrayList.java:15)
```

Let’s discuss briefly how the `unmodifiableList()` method works. Basically, the `Collections` class has a static inner class called `UnmodifiableList`. When we call the `unmodifiableList()` method, a new instance of `UnmodifiableList` is returned. This class implements the `List` interface and overrides the operations like add and remove to throw `UnsupportedOperationException`.

Some snippets of the actual code are shown below for your understanding.

```java
static class UnmodifiableList<E> extends UnmodifiableCollection<E>
        implements List<E> {

    private static final long serialVersionUID = -283967356065247728L;

    final List<? extends E> list;

    UnmodifiableList(List<? extends E> list) {
        super(list);
        this.list = list;
    }

    public boolean equals(Object o) {
        return o == this || list.equals(o);
    }

    public int hashCode() {
        return list.hashCode();
    }

    public E get(int index) {
        return list.get(index);
    }

    public E set(int index, E element) {
        throw new UnsupportedOperationException();
    }

    public void add(int index, E element) {
        throw new UnsupportedOperationException();
    }

    public E remove(int index) {
        throw new UnsupportedOperationException();
    }

    public int indexOf(Object o) {
        return list.indexOf(o);
    }

    public int lastIndexOf(Object o) {
        return list.lastIndexOf(o);
    }

    public boolean addAll(int index, Collection<? extends E> c) {
        throw new UnsupportedOperationException();
    }

    @Override
    public void replaceAll(UnaryOperator<E> operator) {
        throw new UnsupportedOperationException();
    }

    @Override
    public void sort(Comparator<? super E> c) {
        throw new UnsupportedOperationException();
    }
}
```

## Making Collections thread-safe

Most of the collections such as `ArrayList`, `LinkedList`, `HashSet`, `HashMap`, etc., are not thread-safe. If two parallel threads modify any of these collections parallelly, the user can get stale data or `ConcurrentModificationException`.

We can use thread-safe alternatives such as `CopyOnWriteArrayList`, `ConcurrentHashMap`, etc., but what if we don’t want to use these alternatives? What if we have already created an `ArrayList`, and now we want to make it thread-safe.

The `Collections` class provides us with the following methods that can be used to make our existing collection thread-safe.

1. `synchronizedCollection(Collection<T> c)`
2. `synchronizedList(List<T> list)`
3. `synchronizedMap(Map<K,V> m)`
4. `synchronizedSet(Set<T> s)`
5. `synchronizedSortedMap(SortedMap<K,V> m)`
6. `synchronizedSortedSet(SortedSet<T> s)`

### Making an ArrayList thread-safe

To make an `ArrayList` thread-safe we can use the `synchronizedList()` method. Let’s see how this method works internally. The `Collections` class contains a static inner class called `SynchronizedList`. The `synchronizedList()` method is called when the object of this class is returned. If you look at the implementation of this class below, then you can see that all the methods have been synchronized.

Since all the methods are synchronized, this makes it very slow. So, we should always try to use the thread-safe implementations instead of making a collection thread-safe using this method.

```java
static class SynchronizedList<E> extends SynchronizedCollection<E>
        implements List<E> {

    private static final long serialVersionUID = -7754090372962971524L;

    final List<E> list;

    SynchronizedList(List<E> list) {
        super(list);
        this.list = list;
    }

    SynchronizedList(List<E> list, Object mutex) {
        super(list, mutex);
        this.list = list;
    }

    public boolean equals(Object o) {
        if (this == o) {
            return true;
        }

        synchronized (mutex) {
            return list.equals(o);
        }
    }

    public int hashCode() {
        synchronized (mutex) {
            return list.hashCode();
        }
    }

    public E get(int index) {
        synchronized (mutex) {
            return list.get(index);
        }
    }

    public E set(int index, E element) {
        synchronized (mutex) {
            return list.set(index, element);
        }
    }

    public void add(int index, E element) {
        synchronized (mutex) {
            list.add(index, element);
        }
    }

    public E remove(int index) {
        synchronized (mutex) {
            return list.remove(index);
        }
    }
}
```