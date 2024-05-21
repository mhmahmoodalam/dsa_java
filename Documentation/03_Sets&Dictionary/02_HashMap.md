# DataStrcuture

## Explanation

In old java devs used to use hashTable. In the modern java HashMaps are used instead.

We declare the HashMap in Java using the instruction given below:

```java
HashMap<keyDataType, valueDataType> hashMapName = new HashMap<keyDataType, valueDataType>();
```

The similarities between Hashtable and HashMap are as follows:
    - Both are the implementations of the Map interface in Java.
    - Both of them perform similar functions.
    - Neither of them maintain any order of elements.


Differences between Hashtable and HashMap are as follows:

| Hashtable | HashMap |
| --------- | ------- |
| It is used in the older versions of Java. | It exists only in newer versions of Java, i.e., it is part of Java since version 1.2 |
| It does not allow a key to be null | It allows at the most one key to be null. |
| It does not allow to store a null value.| It allows storage of any number of null values. |
| It is a bit slower. | It is faster. |

Some of the commonly used methods of HashMap are as follows:

| Methods | Operations |
| ------- | ---------- |
| put(key,value) | This method adds the specified key with the specified value to the HashMap. |
| remove(key) | If the key is present in the HashMap, it removes the key along with the value mapped to it. |
| containsKey(key) | If there is any mapping to the specified key, then it returns true. |
| size() | This returns the number of key-value mappings present in the HashMap. |
| isEmpty() | If there is no key-value mapping present in the HashMap, it returns true. |
| clear() | It removes all mappings present in the HashMap. |
| get(key) | It returns the value mapped to the specified key in the HashMap. |
| keySet() | It returns the set of keys present in the HashMap. |

## Notes

- HashMap should be used when the dataset is too large
- the hash function impacts the overall performance eof the hashMap
- LinkedHashMap is a special type of hashmap that maintains the insertion order

Characteristics

- Implementation: Uses a hash table where the keys are hashed to determine their indices in an underlying array.
- Order: Does not guarantee any specific iteration order of keys or values.
- Capacity and Load Factor:
    - Initial Capacity: The initial size of the hash table (default is 16).
    - Load Factor: The measure of how full the hash table can get before it is resized (default is 0.75).
- Performance:
    - Time Complexity: 
        - Average Case:
            - put(key, value): O(1)
            - get(key): O(1)
            - remove(key): O(1)
            - containsKey(key): O(1)
            - containsValue(value): O(n) - Needs to iterate over all entries.
            - Iteration over entries, keys, or values: O(n) - Where n is the number of entries.
        - Worst Case:
            All operations can degrade to O(n) if many keys have the same hash code and are placed in the same bucket (hash collisions). However, Java’s HashMap uses a balanced tree (Red-Black tree) to handle such collisions efficiently (from Java 8 onwards) once the number of items in a bucket exceeds a certain threshold (typically 8).
    - Space Complexity
        - The space complexity is O(n + m), where n is the number of entries, and m is the capacity of the hash table. This accounts for the entries themselves and the array used for the buckets.

- Null Elements: Does not allow null elements (throws NullPointerException).

Use Cases:

When you need a sorted set where elements are maintained in a specific order, and you are okay with slightly lower performance compared to HashSet or LinkedHashSet.

### Internal Mechanism

- Hash Function:

Converts the key into a hash code, which is then used to compute the index in the array (bucket).
index = hash(key) & (n - 1) where n is the length of the array.

- Collision Resolution:

Initially uses a singly linked list to store multiple entries in the same bucket.
Converts to a Red-Black tree if the number of entries in a bucket exceeds a threshold (typically 8).

- Rehashing:

When the number of entries exceeds the product of the load factor and current capacity, the HashMap resizes by doubling its capacity and rehashing all entries.

