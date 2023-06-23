A collection is an object that groups multiple elements into a single unit. The Java Collections Framework is a unified architecture for representing and manipulating collections. It contains the interfaces, their implementations, and algorithms to process the data stored in a collection.

In Java, we have a **`Collection`** interface extended by other interfaces such as **`List`**, **`Set`**, and **`Queue`**. Apart from the **`Collection`** interface, we have a **`Map`** interface. The **`Map`** does not implement the **`Collection`** interface because it stores ***key-value pairs***, and the classes that come under the **`Collection`** interface store only values.

### Difference between `Collection` and `Collections`

The differences between a `Collection` and `Collections` are given below.

1. A `Collection` is an interface, whereas `Collections` is a class.
2. A `Collection` interface provides the standard functionality of a data structure to `List`, `Set`, and `Queue`. However, the `Collections` class provides the utility methods that can be used to *search*, *sort*, and *synchronize* collection elements.