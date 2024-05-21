# DataStrcuture

## Explanation

In old java devs use dto use hashTable. In the modern java HashMaps are used instead.

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
