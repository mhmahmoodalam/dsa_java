# Set

There are three implementations of the set interface in Java, which are as follows:

## HashSet

This is the most commonly used implementation of the set. Here, the elements are stored randomly, and duplicates are not allowed.

### Characteristics of HashSet

- **Implementation**: Uses a hash table.
- **Order**: Does not guarantee any specific iteration order.
- **Performance**:
    - Time Complexity: Average O(1) for add, remove, and contains operations.
    - Worst-Case Complexity: O(n) in case of hash collisions.
- Null Elements: Allows a single null element.

### Use Cases of HashSet

When you need a set that offers the best performance in terms of add, remove, and contains operations, and the order of elements is not important.

## LinkedHashSet

Here, the order of the elements is maintained based on their insertion order, and no duplicates are allowed.

### Characteristics  Of LinkedHashSet

- **Implementation**: Extends HashSet and uses a doubly-linked list to maintain insertion order.
- **Order**: Iterates in the order elements were inserted.
- **Performance**:
    - Time Complexity: Average O(1) for add, remove, and contains operations, similar to HashSet.
    - Memory Overhead: Slightly higher than HashSet due to the linked list for maintaining order.
- Null Elements: Allows a single null element.

### Use Cases Of LinkedHashSet

When you need a set that maintains insertion order with relatively fast performance similar to HashSet.

## TreeSet

Here, the order of the elements is maintained by inbuilt ordering or by the explicit comparator (which can arrange it in any sorted order) of TreeSet. Duplicates are not allowed in this either.

### Characteristics Of TreeSet

- **Implementation**: Uses a Red-Black tree (a type of self-balancing binary search tree).
- **Order**: Maintains elements in their natural order (if they implement Comparable) or according to a specified Comparator.
- **Performance**:
    - Time Complexity: O(log n) for add, remove, and contains operations.
- Null Elements: Does not allow null elements (throws NullPointerException).

### Use Cases Of TreeSet

When you need a sorted set where elements are maintained in a specific order, and you are okay with slightly lower performance compared to HashSet or LinkedHashSet.

## Notes

Comparison Summary

|-- Feature --|-- HashSet --|-- LinkedHashSet --|-- TreeSet --|
|------------|-----------|-----------|---------|
| Implementation | Hash table | Hash table + Linked list | Red-Black tree |
| Order | No guaranteed order | Insertion order | Natural/specified order |
| Add/Remove/Contains Time Complexity | O(1) average, O(n) worst | O(1) average, O(n) worst | O(log n) |
| Null Elements | Allows one null element | Allows one null element | Does not allow null elements |
| Memory Overhead | Low | Moderate | Moderate to high |

### Practical Example

```java
import java.util.HashSet;
import java.util.LinkedHashSet;
import java.util.TreeSet;

public class SetExample {
    public static void main(String[] args) {
        // HashSet
        HashSet<String> hashSet = new HashSet<>();
        hashSet.add("B");
        hashSet.add("A");
        hashSet.add("C");
        System.out.println("HashSet: " + hashSet);

        // LinkedHashSet
        LinkedHashSet<String> linkedHashSet = new LinkedHashSet<>();
        linkedHashSet.add("B");
        linkedHashSet.add("A");
        linkedHashSet.add("C");
        System.out.println("LinkedHashSet: " + linkedHashSet);

        // TreeSet
        TreeSet<String> treeSet = new TreeSet<>();
        treeSet.add("B");
        treeSet.add("A");
        treeSet.add("C");
        System.out.println("TreeSet: " + treeSet);
    }
}

Output:

HashSet: [A, B, C] // Note: Actual order may vary
LinkedHashSet: [B, A, C]
TreeSet: [A, B, C]

```