A class implements `Comparable` means that the objects of the class is comparable or ordered. This interface has only one method which is:

```java
public interface Comparable
{
     public int compareTo(T o);
}
```


## Important points under Comparable class.
- `Comparable` is used to decide the ordering of the objects of the class. It is meant for objects with natural ordering which means the object itself must know how it is to be ordered.
- The important Wrapper Classes that implement this interface are `Integer`, `Boolean`, `Byte`, `Character`, `Double`, `Float`, `Long`, `BigInteger` etc.
- Therefore, if any class implements `Comparable` interface in Java then collection of that object either `List` or `Array` can be sorted automatically by using `Collections.sort()` or `Arrays.sort()` method and objects will be sorted based on there natural order defined by `compareTo` method.
- Other classes that implement this interface are `String`, `Date`, `Time` etc.

## Comparable V/S Comparator

If any class does not implement `Comparable` interface, then a separate class can be written which implements its own `Comparator` interface. Unlike `Comparable`, `Comparator` is external to the element type we are comparing. It’s a separate class. We create multiple separate classes (that implement `Comparator`) to compare by different members. If sorting of objects needs to be based on natural order then use `Comparable` whereas if your sorting needs to be done on attributes of different objects, then use `Comparator` in Java.

For example, sorting of students according to there roll number follows a natural order, hence `Comparable` can be used. But if there are a set of points with coordinates x and y, then a `Comparator` can be arranged with an explicit class to decide the order of sorting.

Example: In the following class the students need to be arranged according to there roll number which is a natural order, hence a `Comparable` interface can be used. If Collections like `PriorityQueue`, `TreeSet`, `TreeMap`, etc needs to be created of this class, then no extra things are needed to be done because the class is `Comparable`.

```java
class Student implements Comparable
{
    String name;
    int rollNo;

    // Comparing the current this object
    // with the object s
    public int compareTo(Student s)
    {
        return (this.rollNo - s.rollNo);
    }
}
```


When two objects are compared as shown above then three possibilities arise:
- A negative value is returned when the current object is smaller.
- 0 is returned when both the objects are the same.
- A positive value is returned when the current object is greater.


Following this, any method such as `sort(arr)` can be called to sort the students according to the natural order. Also a `TreeMap` or `TreeSet` or any collection interface can be created using increasing order or `sort(arr)` or reverse order of sorting using `sort(arr, Collections.reverseOrder())`.