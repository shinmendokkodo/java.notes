Java `HashSet` class implements the `Set` interface, backed by a hash table which is actually a `HashMap` instance.

No guarantee is made as to the iteration order of the hash sets which means that the class does not guarantee the constant order of elements over time.

This class permits the null element. The class also offers constant time performance for the basic operations like add, remove, contains, and size assuming the hash function disperses the elements properly among the buckets.

## Java HashSet Features

A few important features of `HashSet` are mentioned below:

- Implements Set Interface.
- The underlying data structure for HashSet is Hashtable.
- As it implements the Set Interface, duplicate values are not allowed.
- Objects that you insert in HashSet are not guaranteed to be inserted in the same order. Objects are inserted based on their hash code.
- NULL elements are allowed in HashSet.
- HashSet also implements Serializable and Cloneable interfaces.

### Declaration of `HashSet`
```java
public class HashSet<E> extends AbstractSet<E> implements Set<E>, Cloneable, Serializable
```
where `E` is the type of elements stored in a `HashSet`.
HashSet Java Example

```java
// Java program to illustrate the concept
// of Collection objects storage in a HashSet
import java.io.*;
import java.util.*;

class CollectionObjectStorage {

    public static void main(String[] args)
    {
        // Instantiate an object of HashSet
        HashSet<ArrayList> set = new HashSet<>();

        // create ArrayList list1
        ArrayList<Integer> list1 = new ArrayList<>();

        // create ArrayList list2
        ArrayList<Integer> list2 = new ArrayList<>();

        // Add elements using add method
        list1.add(1);
        list1.add(2);
        list2.add(1);
        list2.add(2);
        set.add(list1);
        set.add(list2);

        // print the set size to understand the
        // internal storage of ArrayList in Set
        System.out.println(set.size());
    }
}
```
```md
Output:
1
```
Before storing an Object, HashSet checks whether there is an existing entry using `hashCode()` and `equals()` methods. In the above example, two lists are considered equal if they have the same elements in the same order. When you invoke the `hashCode()` method on the two lists, they both would give the same hash since they are equal.

> **Note**: `HashSet` does not store duplicate items,  if you give two `Objects` that are equal then it stores only the first one, here it is `list1`.

## Internal Working of a HashSet

All the classes of the `Set` interface are internally backed up by `Map`. `HashSet` uses `HashMap` for storing its object internally. You must be wondering that to enter a value in `HashMap` we need a key-value pair, but in `HashSet`, we are passing only one value.

Storage in `HashMap`: Actually the value we insert in `HashSet` acts as a key to the map `Object` and for its value, java uses a constant variable. So in the key-value pair, all the values will be the same.

### Implementation of HashSet in Java doc

```java
private transient HashMap map;

// Constructor - 1
// All the constructors are internally creating HashMap Object.
public HashSet() {
    // Creating internally backing HashMap object
    map = new HashMap();
}

// Constructor - 2
public HashSet(int initialCapacity) {
    // Creating internally backing HashMap object
    map = new HashMap(initialCapacity);
}

// Dummy value to associate with an Object in Map
private static final Object PRESENT = new Object();
```

If we look at the `add()` method of the HashSet class:

```java
public boolean add(E e) {
   return map.put(e, PRESENT) == null;
}
```
We can notice that `add()` method of the `HashSet` class internally calls the `put()` method of backing the `HashMap` object by passing the element you have specified as a key and constant **`PRESENT`** as its value. `remove()` method also works in the same manner. It internally calls the `remove` method of the `Map` interface.

```java
public boolean remove(Object o) {
  return map.remove(o) == PRESENT;
}
```

HashSet not only stores unique Objects but also a unique `Collection` of Objects like `ArrayList<E>`, `LinkedList<E>`, `Vector<E>`,..etc.

## Constructors of HashSet class

To create a `HashSet`, we need to create an object of the `HashSet` class. The `HashSet` class consists of various constructors that allow the possible creation of the `HashSet`. The following are the constructors available in this class.

1. `HashSet()`:
    This constructor is used to build an empty `HashSet` object in which the default initial capacity is **16** and the default load factor is **0.75**. If we wish to create an empty HashSet with the name hs, then, it can be created as:

    ```java
    HashSet<E> hs = new HashSet<E>();
    ```

2. `HashSet(int initialCapacity)`
    This constructor is used to build an empty `HashSet` object in which the `initialCapacity` is specified at the time of object creation. Here, the default loadFactor remains **0.75**.
    ```java
    HashSet<E> hs = new HashSet<E>(int initialCapacity);
    ```

3. `HashSet(int initialCapacity, float loadFactor)`
    This constructor is used to build an empty `HashSet` object in which the `initialCapacity` and `loadFactor` are specified at the time of object creation.
    ```java
    HashSet<E> hs = new HashSet<E>(int initialCapacity, float loadFactor);
    ```

4. HashSet(Collection)
    This constructor is used to build a `HashSet` object containing all the elements from the given collection. In short, this constructor is used when any conversion is needed from any `Collection` object to the `HashSet` object. If we wish to create a `HashSet` with the name `hs`, it can be created as:
    ```java
    HashSet<E> hs = new HashSet<E>(Collection C);
    ```

### Below is the implementation of the above topics:

```java
// Java program to Demonstrate Working
// of HashSet Class

// Importing required classes
import java.util.*;

// Main class
// HashSetDemo
class GFG {

    // Main driver method
    public static void main(String[] args) {

        // Creating an empty HashSet
        HashSet<String> h = new HashSet<String>();

        // Adding elements into HashSet
        // using add() method
        h.add("India");
        h.add("Australia");
        h.add("South Africa");

        // Adding duplicate elements
        h.add("India");

        // Displaying the HashSet
        System.out.println(h);
        System.out.println("List contains India or not:" + h.contains("India"));

        // Removing items from HashSet
        // using remove() method
        h.remove("Australia");
        System.out.println("List after removing Australia:" + h);

        // Display message
        System.out.println("Iterating over list:");

        // Iterating over hashSet items
        Iterator<String> i = h.iterator();

        // Holds true till there is single element remaining
        while (i.hasNext()) {

            // Iterating over elements
            // using next() method
            System.out.println(i.next());
        }
    }
}
```
```md
Output:
[South Africa, Australia, India]
List contains India or not:true
List after removing Australia:[South Africa, India]
Iterating over list:
South Africa
India
```

## Methods in HashSet

| METHOD | DESCRIPTION |
| --------------- | --- |
| `add(E e)`     | Used to add the specified element if it is not present, if it is present then return false. |
| `clear()` | Used to remove all the elements from the set. |
| `contains(Object o)` | Used to return true if an element is present in a set. |
| `remove(Object o)` | Used to remove the element if it is present in set. |
| `iterator()` | Used to return an iterator over the element in the set. |
| `isEmpty()` | Used to check whether the set is empty or not. Returns true for empty and false for a non-empty condition for set. |
| `size()` | Used to return the size of the set. |
| `clone()` | Used to create a shallow copy of the set. |

## Performing Various Operations on HashSet

Let’s see how to perform a few frequently used operations on the `HashSet`.
1. Adding Elements in `HashSet`
    To add an element to the `HashSet`, we can use the `add()` method. However, the insertion order is not retained in the `HashSet`.  We need to keep a note that duplicate elements are not allowed and all duplicate elements are ignored.

2. Removing Elements in HashSet
    The values can be removed from the `HashSet` using the `remove()` method.


3. Iterating through the HashSet
    Iterate through the elements of `HashSet` using the `iterator()` method.

### Time Complexity of HashSet Operations:
The underlying data structure for HashSet is hashtable. So amortize (average or usual case) time complexity for ***add***, ***remove*** and ***look-up*** (contains method) operation of HashSet takes `O(1)` time.

### Performance of HashSet

`HashSet` extends `Abstract Set<E>` class and implements `Set<E>`, `Cloneable`, and `Serializable` interfaces where `E` is the type of elements maintained by this set. The directly known subclass of `HashSet` is `LinkedHashSet`.

Now for the maintenance of constant time performance, iterating over `HashSet` requires time proportional to the sum of the HashSet instance’s size (the number of elements) plus the “capacity” of the backing `HashMap` instance (the number of buckets). Thus, it’s very important not to set the initial capacity too high (or the load factor too low) if iteration performance is important.

- **Initial Capacity**: The initial capacity means the number of buckets when the hashtable (HashSet internally uses hashtable data structure) is created. The number of buckets will be automatically increased if the current size gets full.

- **Load Factor**: The load factor is a measure of how full the HashSet is allowed to get before its capacity is automatically increased. When the number of entries in the hash table exceeds the product of the load factor and the current capacity, the hash table is rehashed (that is, internal data structures are rebuilt) so that the hash table has approximately twice the number of buckets.

```md
                  Number of stored elements in the table
Load Factor = -----------------------------------------
                        Size of the hash table
```

> Example: If internal capacity is 16 and the load factor is 0.75 then the number of buckets will automatically get increased when the table has 12 elements in it.

### Effect on performance:

**Load factor** and **initial capacity** are two main factors that affect the performance of `HashSet` operations. A load factor of 0.75 provides very effective performance with respect to time and space complexity. If we increase the load factor value more than that then memory overhead will be reduced (because it will decrease internal rebuilding operation) but, it will affect the add and search operation in the hashtable. To reduce the rehashing operation we should choose initial capacity wisely. If the initial capacity is greater than the maximum number of entries divided by the load factor, no rehash operation will ever occur.

> Note: The implementation in a `HashSet` is not synchronized, in the sense that if multiple threads access a hash set concurrently, and at least one of the threads modifies the set, it must be synchronized externally. This is typically accomplished by synchronizing on some object that naturally encapsulates the set. If no such object exists, the set should be “wrapped” using the `Collections.synchronizedSet` method. This is best done at creation time, to prevent accidental unsynchronized access to the set as shown below:

```java
Set s = Collections.synchronizedSet(new HashSet(…));
```

Methods Used with `HashSet`

1. Methods inherited from class java.util.AbstractSet

| Method | Description |
| ------ | ------- |
| `equals()` | Used to verify the equality of an `Object` with a `HashSet` and compare them. The list returns true only if both `HashSet` contains the same elements, irrespective of order. |
| `hashcode()` | Returns the hash code value for this set. |
| `removeAll(collection)` | This method is used to remove all the elements from the collection which are present in the set. This method returns `true` if this set changes as a result of the call. |

2. Methods inherited from class `java.util.AbstractCollection`

| METHOD | DESCRIPTION |
| ------ | ----------- |
| `addAll(collection)` | This method is used to append all of the elements from the mentioned collection to the existing set. The elements are added randomly without following any specific order. |
| `containsAll(collection)` | This method is used to check whether the set contains all the elements present in the given collection or not. This method returns true if the set contains all the elements and returns false if any of the elements are missing. |
| `retainAll(collection)` | This method is used to retain all the elements from the set which are mentioned in the given collection. This method returns true if this set changed as a result of the call. |
| `toArray()` | This method is used to form an array of the same elements as that of the `Set`. |
| `toString()` | The `toString()` method of Java `HashSet` is used to return a string representation of the elements of the `HashSet` Collection. |

3. Methods declared in interface `java.util.Collection`

| METHOD | DESCRIPTION |
| ------ | ----------- |
| `parallelStream()` | Returns a possibly parallel Stream with this collection as its source. |
| `removeIf​(Predicate<? super E> filter)` | Removes all of the elements of this collection that satisfy the given predicate. |
| `stream()` | Returns a sequential Stream with this collection as its source. |
| `toArray​(IntFunction<T[]> generator)` | Returns an array containing all of the elements in this collection, using the provided generator function to allocate the returned array. |

4. Methods declared in interface `java.lang.Iterable`

| METHOD | DESCRIPTION |
| ------ | ----------- |
| `forEach​(Consumer<? super T> action)` | Performs the given action for each element of the `Iterable` until all elements have been processed or the action throws an exception. |

5. Methods declared in `interface java.util.Set`

| METHOD | DESCRIPTION |
| ------ | ----------- |
| `addAll​(Collection<? extends E> c)` | Adds all of the elements in the specified collection to this set if they’re not already present (optional operation). |
| `containsAll​(Collection<?> c)` | Returns true if this set contains all of the elements of the specified collection. |
| `equals​(Object o)` | Compares the specified object with this set for equality. |
| `hashCode()` | Returns the hash code value for this set. |
| `removeAll​(Collection<?> c)` | Removes from this set all of its elements that are contained in the specified collection (optional operation). |
| `retainAll​(Collection<?> c)` | Retains only the elements in this set that are contained in the specified collection (optional operation). |
| `toArray()` | Returns an array containing all of the elements in this set. |
| `toArray​(T[] a)` | Returns an array containing all of the elements in this set; the runtime type of the returned array is that of the specified array. |

Q1. What is `HashSet` in Java?
> `HashSet` is a type of class, which extends `AbstractSet` and implements `Set` interfaces.

Q2. Why is `HashSet` used?
> `HashSet` is used for avoiding duplicate data and to find value with the fast method.

## Differences between HashSet and HashMap.



| Basis | HashSet | HashMap |
| ---- | ---- | ---- |
| Implementation | `HashSet` implements a `Set` interface. | `HashMap` implements a `Map` interface. |
| Duplicates | `HashSet` doesn’t allow duplicate values. | HashMap stores the key and value pairs and it does not allow duplicate keys. If the key is duplicate then the old key is replaced with the new value. |
| Number of objects during storing objects | `HashSet` requires only one object `add(Object o)`. | `HashMap` requires two objects `put(K key, V Value)` to add an element to the `HashMap` object. |
| Dummy value | `HashSet` internally uses `HashMap` to add elements. In `HashSet`, the argument passed in `add(Object)` method serves as `key` `K`. Java internally associates a dummy value for each value passed in `add(Object)` method. | `HashMap` does not have any concept of dummy value. |
| Storing or Adding a mechanism | `HashSet` internally uses the `HashMap` object to store or add the objects. | `HashMap` internally uses hashing to store or add objects |
| Faster | `HashSet` is slower than `HashMap`. | `HashMap` is faster than `HashSet`. |
| Insertion | `HashSet` uses the `add()` method for adding or storing data. | HashMap uses the `put()` method for storing data. |

## Differences between HashSet and TreeSet in Java.

| Basis | HashSet | TreeSet |
| ---- | ---- | ---- |
| Speed and internal implemention | For operations like search, insert, and delete, it takes constant time for these operations on average. `HashSet` is faster than `TreeSet`. `HashSet` is implemented using a hash table. | TreeSet takes O`(log n)` for search, insert and delete which is higher than `HashSet`. But `TreeSet` keeps sorted data. Also, it supports operations like `higher()` (Returns least higher element), floor(), ceiling(), etc. These operations are also O(log n) in `TreeSet` and not supported in `HashSet`. `TreeSet` is implemented using a self-balancing binary search tree (Red-Black Tree). `TreeSet` is backed by `TreeMap` in Java. |
| Ordering | Elements in `HashSet` are not ordered. | `TreeSet` maintains objects in Sorted order defined by either the `Comparable` or `Comparator` method in Java. `TreeSet` elements are sorted in ascending order by default. It offers several methods to deal with the ordered set like `first()`, `last()`, `headSet()`, `tailSet()`, etc.
| Null Object | `HashSet` allows the null object. | `TreeSet` doesn’t allow null `Object` and throws ``NullPointerException``, Why, is because TreeSet uses `compareTo()` method to compare keys, and `compareTo()` will throw `java.lang.NullPointerException`. |
| Comparison | `HashSet` uses the `equals()` method to compare two objects in the `Set` and for detecting duplicates. | `TreeSet` uses `compareTo()` method for the same purpose. If `equals()` and `compareTo()` are not consistent, i.e. for two equal objects equals should return **true** while `compareTo()` should return **zero**, then it will break the contract of the `Set` interface and will allow duplicates in `Set` implementations like `TreeSet`

---

# HashSet: Creation and Insertion

`HashSet` is a class in the `java.utils` package which implements the `Set` interface. Some of the features of HashSet are:

- `HashSet` does not allow duplicate elements.
- `HashSet` allows only one null element.
- The elements are inserted in random order in a `HashSet`.
- A `HashSet` is internally backed by a `HashMap`.

## Creating a `HashSet`

There are four different constructors available to create a HashSet in Java:

### Using the no-arg constructor
The simplest way to create a `HashSet` is by using the no-arg constructor. This constructor creates a `HashSet` with an initial capacity of **16** and a load factor of **0.75**.

Below is the code syntax to create a `HashSet`.
```java
Set<Integer> set= new HashSet<>();
```

> Load factor is a number that defines when a `Set` should be resized. If the load factor is **0.75**, then the Set should be resized when it is 75% full.

### Using the Constructor that takes initial capacity

We can also provide the initial capacity while creating the `HashSet`. If we are already aware that our `HashSet` will contain more than **16** elements, then it is better to provide some initial capacity as it reduces the number of resizes. In this case, also, the default load factor (**0.75**) is used.

### Using the constructor that takes initial capacity and load factor

We can also provide initial capacity along with the load factor while creating the `HashSet`. If we don’t want frequent resizing, we can set the load factor to a higher number.

### Using the constructor that takes another Set as a parameter

We can also create a `HashSet` using another `Set` by passing it to the constructor. The newly created `HashSet` will have the same size as that of the passed Set, whereas the load factor will default to **0.75**.

## Inserting an element into a HashSet

There is an `add(E e)` method available that inserts an element into the `HashSet`. If the element is not already present, then this method puts the element and returns `true`. If the element is already present, then it returns `false`.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		System.out.println("Inserting 23 in the HashSet:  " + set.add(23));
		System.out.println("Inserting 34 in the HashSet:  " + set.add(34));
		System.out.println("Inserting 23 in the HashSet:  " + set.add(23));
		System.out.println(set);

	}
}
```
```md
Inserting 23 in the HashSet:  true
Inserting 34 in the HashSet:  true
Inserting 23 in the HashSet:  false
[34, 23]
```

## Fetching an element from a HashSet

Unlike `ArrayList`, there is no `get()` method in a `HashSet` because a `HashSet` is not backed by an array. The elements are stored in random order in a `HashSet`, and we can’t get a particular element. If we want to check whether a particular element is in the `HashSet` or not, then we can use the `contains()` method.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		System.out.println(set.contains(23));
	}
}
```
```md
true
```

# HashSet: Operations

## Removing an element from a HashSet

Below are the ways that we can remove an element from the `HashSet`.

### Using the `remove(Object o)` method
We can use the `remove(Object o)` method to remove an element from `HashSet`. This method takes an object that needs to be removed as a parameter. If the element is removed, then this method returns `true`. If the element is not present, then it returns `false`.

### Using the `clear()` method
We can use the `clear()` method to remove all the elements from a `HashSet`.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		set.remove(23);
		System.out.println("HashSet after removing one element" + set);
		set.clear();
		System.out.println("HashSet after removing all elements" + set);
	}
}
```
```md
HashSet after removing one element[34, 56]
HashSet after removing all elements[]
```

### Checking if the `HashSet` is empty
We can check if the `HashSet` is empty using the `isEmpty()` method. This method returns `true` if the `Set` does not have any elements and returns `false` if the `Set` has some elements.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		System.out.println(set.isEmpty());
	}
}
```
```md
false
```

# HashSet: Iteration and Sorting

## Iterating a HashSet#

Below are the different methods to iterate over a `HashSet`.

### Using `for` loop

A `HashSet` can be easily iterated using an enhanced for loop as shown below.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		for(int i : set) {
			System.out.println(i);
		}
	}
}
```
```md
34
23
56
```

### Using `Iterator`

`HashSet` can also be iterated using an iterator as shown in the below example.

```java
import java.util.HashSet;
import java.util.Iterator;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		Iterator<Integer> itr = set.iterator();
		while(itr.hasNext()) {
			System.out.println(itr.next());
		}
	}
}
```
```md
34
23
56
```

### Using forEach() method

We can use the `forEach(Consumer<? super T> action)` method defined in the `Iterable` class. This method was introduced in Java 8. It accepts an action that needs to be performed for each element as a parameter.

```java
import java.util.HashSet;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		set.forEach(System.out::println);
	}
}
```
```md
34
23
56
```

## Sorting a HashSet

Since a `HashSet` stores the elements in random order, it is not possible to store the elements in a `HashSet` in sorted order. If we want to sort the elements of a `HashSet`, then we should convert it into some other `Collection` such as a `List`, `TreeSet`, or `LinkedHashSet`.

Here we will see how we can convert a `HashSet` to an `ArrayList`, and then we can use the elements from the `List`. We can create an `ArrayList` by sending another collection to its constructor. We can sort this `ArrayList` using the `sort()` method of the `Collections` class.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.List;
import java.util.Set;

public class HashSetDemo {
	public static void main(String args[]) {
		Set<Integer> set = new HashSet<>();
		set.add(23);
		set.add(34);
		set.add(56);
		// Creating an ArrayList from existing set.
		List<Integer> list = new ArrayList<>(set);
		// Sorting the list.
		Collections.sort(list);
		list.forEach(System.out::println);
	}
}
```
```md
23
34
56
```
