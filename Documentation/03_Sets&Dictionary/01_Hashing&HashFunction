# Hashing and Hash Function

## Explanation

A hash table is a data structure that stores records (or elements) according to its associated 'keys'. This is done by designing a hash function that takes the given keys as input and outputs array indices at which the records are stored. In other words, each record is stored using the array index obtained by hashing its key.

Hash tables store data in the form of key and value. Each array contains a hashed key along with a pointer that tells you the location at which the associated record is stored.

Java provides two APIs for implementing hash tables, which are Hashtable and HashMap. They are extremely similar in terms of functionality, except that Hashtable does not support null values, and HashMap is not synchronized.

Additional Reading Links for Hashtable and HashMap in Java API are provided below:

[Hashtable in Java](https://www.geeksforgeeks.org/java-util-hashtable-class-java/)
[HashMap in Java](https://www.geeksforgeeks.org/java-util-hashmap-in-java/)
[Open Addressing in Hashing](https://www.geeksforgeeks.org/hashing-set-3-open-addressing/)


## Notes

- hash table is mainly used to achieve a constant run-time complexity O(1).
- it must compute fast because a time-expensive hash function would defeat the overall purpose of fast retrieval of a hash table
- Cardinality is a measure of a set's size or the number of elements in a set. For example, if you are given a set A {1,3,4,3,2,5}, the cardinality of set A is 6.
- The chosen size of a hash table cannot be extremely small because it will result in a collision

## Collision in hash Tables

The chosen size of a hash table cannot be extremely small because it will result in a collision
The phenomenon of two distinct keys, K1 and K2, getting hashed to the same index is known as a ‘collision’ in hash tables. So, for two keys where K1≠ K2 , if H(K1)=H(K2), collisions occur. Collisions cannot be avoided completely, but they may be reduced to a great extent by choosing good hash functions

### Handling collision

There are two approaches two handle collisions
    - closed hashing or linear probing
    - open hashing or chaining

#### Open hashing or chaining

In this mechanism in case of collision, all the keys that get hashed to the same index are stored in a linked list that is maintained at the particular index

for example:

if we have to store Avi, Bob, Chandler, Dev, Eva, Alex based on first character
A - 0 -> Alex --> Avi --> NULL
B - 1 -> Bob --> NULL
C - 2 -> Chandler --> Null
D - 3 -> Dev --> Null
E - 4 -> Eva --> Null

> We must ensure that the hash function causes less collision other wise the linked list size will too high and thus increasing the retrieval time

#### Designing a Hash Function

There is no single hash function that is universally applicable. For a given application, a good hash function should be designed with the following characteristics in mind:
    - The hash function should use all the keys.
    - The hash function should distribute the keys uniformly across the array indices.
    - The hash function should output different hash values for similar yet unequal keys.

## Hash Table Api functions

- Add ( put, insert)
- lookup (search, get, find)
