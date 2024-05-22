# Linear vs Non-Linear Data Structure

- What if there exists a relation between data points that are not linear?
- What if the data has a hierarchical structure?
- How will you store such data?

> In such a case, you need to use a non-linear data structure. 

## The Difference

| Criteria | Linear Data Structure | Non-Linear Data Structure |
| ---------| --------------------- | ------------------------- |
| Sequence/Arrangement | The elements in a linear data structure exhibit some sort of sequence or that the elements are arranged in a linear order. | The elements in a non-linear data structure do not exhibit any sequence and are not arranged in any linear order. |
| Number of Levels | In a linear data structure, there is a single level, and all the elements that are present on this level. | In a non-linear data structure, there are multiple levels, and the elements are distributed across levels. |
| Traversals | In a linear data structure, it is possible to traverse through all the elements in a single pass. | In a non-linear data structure, it is not possible to traverse through all the elements in a single pass. Multiple passes/runs are needed for this purpose. |
| Examples | Arrays, stacks, queues, linked lists, etc. | Trees, graphs, etc. |

The non-linearity of data has led to the evolution of non-linear data structures such as trees. The tree data structure connects every data point to several other data points in such a way that the connection between the different points and the structure of the tree represent a specific relation with the connected points. Also, as you have seen, trees convey the natural flow of information of a particular set of data.

## Trees vs arrays vs linked lists

| Criteria | Comparison | Justification |
| ---------| --------------------- | ------------------------- |
| Access (or Search) | Linked lists < trees < arrays | Accessing (or searching) an element in a tree is quicker than accessing linked lists but slower than accessing arrays. |
| Insertion / Deletion | Arrays < trees < linked lists (Unordered) | Inserting or deleting an element from a tree is quicker than arrays but slower than unordered linked lists. |
| Number of Elements | Linked lists = trees ≠ arrays |  Like linked lists and unlike arrays, trees can consist of as many number of elements as needed on the run time. |
