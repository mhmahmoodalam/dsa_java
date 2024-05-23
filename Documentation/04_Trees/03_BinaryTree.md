# Binary Tree

A binary tree is a tree that has at most two children. In other words, each node can have either 0 or 1 or 2 children.

## Tree Vocabulary

When it comes to the vocabulary of binary tree that can have a maximum of two children, we call the child on the left side–the left child–and the child on the right side–the right child.

```graph

           1
         /  \
        2    3
       / \    \
      4   5    6

```

In the binary tree given above, the root node 1 is a parent that has two child nodes - 2 and 3. 2 is the left child of 1, and 3 is the right child of 1. 4 is the left child of parent node 2 and 5 is the right child of parent node 2. 3 has the right child as 6.

## Binary Tree Properties

- The maximum number of nodes $n$ at level $l$  of binary tree is $2^{l - 1}$ . In some books, the level of the root is considered as 0. In this convention, the above formula becomes $2^{l}$

- The maximum number of nodes $n$ in a binary tree of height $h$ is $2^{h} - 1$ . In some books, the height of the root is considered as 0. In this convention, the above formula becomes $2^{h+1} – 1$

- The minimum height $h$  of a binary tree with $n$  nodes is $log_{2}(n + 1)$

- The minimum levels $l$ in a binary tree with $L$ leaves is $log_{2}L + 1$

## Types of Binary Trees

### On the basis of Number of Children

- Full Binary Tree : A full binary tree is a binary tree with either zero or two child nodes for each node.

- Degenerate Binary Tree : Every non-leaf node has just one child in a binary tree known as a Degenerate Binary tree. The tree effectively transforms into a linked list as a result, with each node linking to its single child.
    - left skewed
    - right skewed

### On the basis of Completion of Levels

- Complete Binary Tree : A complete binary tree is a special type of binary tree where all the levels of the tree are filled completely except the lowest level nodes which are filled from as left as possible.

- Perfect Binary Tree : A perfect binary tree is a special type of binary tree in which all the leaf nodes are at the same depth, and all non-leaf nodes have two children. In simple terms, this means that all leaf nodes are at the maximum depth of the tree, and the tree is completely filled with no gaps.
  - Balanced Binary Tree: A binary tree is balanced if the height of the tree is O(Log n) where n is the number of nodes.
    - The height of the left and right tree for any node does not differ by more than 1.
    - The left subtree of that node is also balanced.
    - The right subtree of that node is also balanced.

- Complete Binary Tree: A binary tree in which all levels are fully filled except possibly for the last level, which is filled from left to right. In other words, a node in the second-last level cannot have a right child without having all the nodes in its left side.

    - Key Points
        - Left-to-Right Order: All nodes on the last level must be filled from left to right. Missing nodes on the left with nodes present on the right invalidate the tree as complete.
        - Balanced Levels: All levels before the last must be fully filled.Missing nodes in intermediate levels invalidate the tree.
        - Sequential Filling: Nodes must be filled sequentially from top to bottom, left to right. Any deviation invalidates the completeness.

    - Applications
        - Heap Trees: Complete binary trees are often used to implement binary heaps, where the tree structure is used to maintain the heap property.
        - Array Representation: Complete binary trees are easy to represent in arrays, as the parent-child relationships can be easily calculated using indices.
        - Priority Queues: They are used in implementing priority queues where elements are added or removed based on priority.

    ```graph

            1           
           / \          
          2   3         
         / \ / \            
        4  5 6  7     
    ```

    In below tree, the last level is not fully filled, but all nodes are as far left as possible.

    ```graph

            1           
           / \          
          2   3         
         / \ /             
        4  5 6       
    ```

    Below, the last level is partially filled from  left to right.

    ```graph

            1
           / \
          2   3
         / \ / \
        4  5 6  7
       / \
      8   9

    ```

    Left skewed

    ```graph
            1
           / \
          2   3
         / \
        4   5
       / \
      6   7


    ```

    Invalid Complete binary trees

    ```graph

            1
           / \
          2   3
             / \
            4   5

            1
           / \
          2   3
         /   / \
        4   5   6


            1
           / \
          2   3
         / \   \
        4   5   6
           / \
          7   8


    ```

- Full Binary Tree: A binary tree where every node other than the leaves has exactly two children. Each Node has either zero or two child nodes .

    ```graph

            1           
           / \          
          2   3         
         / \ / \            
        4  5 6  7     
    ```

    Below tree is full binary tree all the nodes    have two children except the leaf nodes–node 2,    node 5 and the nodes at the last level. Remember   that a node is a leaf node if it does not have    any child. A leaf node is not necessarily needed   to be present at the last level.

    ```graph
             1
           /   \
          2     3
               / \
              4   5
            /   \
           6     7


    ```

- Perfect Binary Tree: A binary tree where all internal nodes have exactly two children and all leaves are at the same level.

  - Symmetry: All internal nodes have exactly two children.
  - Equal Levels: All leaf nodes are at the same level.
  - Node Count: For a tree of height $ℎ$, the total number of nodes is $2^{h+1} - 1$
    - Balance: Perfect binary trees are perfectly balanced, making them ideal for scenarios requiring efficient searches and insertions.

    ```graph

              Root
             /    \
         Left1    Right1
         /  \      /   \
      L2    L3   R2    R3


            1
           / \
          2   3
         / \ / \
        4  5 6  7

              A
             / \
            B   C
           / \ / \
          D  E F  G


    ```

### On the basis of Node Values

- Binary Search Tree (BST)
A binary search tree is a binary tree where each node has a value, and the left child's value is less than the parent's value, while the right child's value is greater than the parent's value. This property holds for every node in the tree.

    ```graph
    
            8
           / \
          3   10
         / \    \
        1   6    14
           / \   /
          4   7 13

    Node 8: Left child (3) < 8, Right child (10) > 8
    Node 3: Left child (1) < 3, Right child (6) > 3
    Node 10: Right child (14) > 10
    Node 6: Left child (4) < 6, Right child (7) > 6
    Node 14: Left child (13) < 14

    ```

- AVL Tree: An AVL tree defined as a self-balancing Binary Search Tree (BST) where the difference between heights of left and right subtrees for any node cannot be more than one.

    ```graph
            30
           /  \
         20    40
        /  \     \
       10   25    50
    
    The heights of the left and right subtrees of   every node differ by at most 1, ensuring  balanced tree structure.
    
    ```

- Red Black Tree: A red-black tree is a self-balancing binary search tree where each node contains an extra bit for denoting the color of the node, either red or black. This tree ensures the tree remains balanced with a set of rules. 

    ```graph
            10 (B)
           /  \
         5 (R)  15 (B)
        / \      / \
       3 (B)  7 (B) 12 (R) 18 (B)

    - Red nodes cannot have red children (no two    consecutive red nodes).
    - Every path from a node to its descendant NULL     nodes has the same number of black nodes.
    
    ```

- B Tree: A B-tree is a self-balancing search tree in which nodes can have more than two children. It is designed to work well on systems that read and write large blocks of data. B-trees are used in databases and file systems to maintain sorted data and allow searches, sequential access, insertions, and deletions in logarithmic time.

    - Properties of B-tree
        - Order: A B-tree of order 𝑚 (also known       an    m-ary tree) is defined as     ows:
            - Every node can have at most 𝑚     children.
            - Every internal node (non-leaf and         non-root)   has at least ⌈ 𝑚 / 2 ⌉  children.
            - The root has at least 2 children if it    is     not     a leaf node.
            - A non-empty tree has at least ⌈m/2⌉−1     keys    and    at most m−1 keys.
            - All leaves appear on the same level.

        - Keys and Children:
            - Each internal node contains a certain     number     of keys.
            - The keys act as separation values     which  divide the range of the values in    the subtrees.

        B-tree of Order 3 (T=2)
        ```graph
                    [  10 , 20  ]
                   /     |        \
            [1, 5, 7] [15, 17] [25, 30, 35]

        The root has two keys (10, 20) and three        children.
        Each child node has between 1 and 3 keys.

        ```


- B+ Tree: B + Tree is a variation of the B-tree data structure. In a B + tree, data pointers are stored only at the leaf nodes of the tree. In a B+ tree structure of a leaf node differs from the structure of internal nodes. The leaf nodes have an entry for every value of the search field, along with a data pointer to the record (or to the block that contains this record). The leaf nodes of the B+ tree are linked together to provide ordered access to the search field to the records. Internal nodes of a B+ tree are used to guide the search. Some search field values from the leaf nodes are repeated in the internal nodes of the B+ tree.

    ```graph

    Internal Nodes:

                [20, 40]
               /    |    \
          [10]   [30]   [50]

    Leaf Nodes:
    Linked List: [10] <-> [20, 30] <-> [40, 50]

    - The internal nodes contain keys for navigation.

    - The leaf nodes contain actual data and are linked for efficient traversal.
    ```

    - Properties of B+ Tree
        - Internal Nodes: Only store keys and pointers to  child nodes.
        - Leaf Nodes: Store keys and associated data  pointers. All leaf nodes are linked to form a  doubly linked list.
        - Order: Similar to B-trees, the order of a B+  tree defines the maximum number of children a node can have.
        - Height: The height of a B+ tree is relatively small compared to the number of keys stored, providing efficiency in search operations.
- Segment Tree: Segment Tree is a versatile data structure used in computer science and data structures that allows efficient querying and updating of intervals or segments of an array. It is particularly useful for problems involving range queries, such as finding the sum, minimum, maximum, or any other operation over a specific range of elements in an array. The tree is built recursively by dividing the array into segments until each segment represents a single element. This structure enables fast query and update operations with a time complexity of O(log n), making it a powerful tool in algorithm design and optimization.

    ```graph

                    [36]
                 /        \
             [16]          [20]
           /    \         /     \
        [4]      [12]    [16]    [4]
       /  \     /  \     /  \    / \
     [1]  [3] [5]  [7] [9] [11]

    Each node represents a segment of the array, and the value of the node is the sum of the elements in that segment.
    
    ```
- Heap Tree : A heap tree is a special tree-based data structure that satisfies the heap property. It can be a max heap (parent nodes are greater than or equal to child nodes) or a min heap (parent nodes are less than or equal to child nodes).

    - Max Heap Tree

        ```graph
                 50
                /  \
              30    40
             / \    / \
            10 20  35 38

        Every parent node is greater than or equal to its child nodes.
        ```
    - Min Heap Tree

        ```graph
                    10
                   /  \
                 20    30
                / \    / \
               25 35  40 50


        Every parent node is less than or equal to its child nodes.
        ```
- Trie (prefix Tree): A trie is a type of search tree used to store a dynamic set of strings, where the keys are usually strings. Nodes are arranged in a way that common prefixes of the strings are stored only once.

    ```graph
  
            (root)
           /  |  \
          t   b   c
         /   / \   \
        o   a   e   a
       /     \   \   \
      p       t   r   t
               \   \
                t   s

    This trie represents the words: "top", "bat", "bar", "car", "cat".
    ```
- Binary Indexed Tree (Fenwick Tree): A binary indexed tree is a data structure that provides efficient methods for calculation and manipulation of the prefix sums of a table of numbers.

    ```graph
    Representation of BIT:
    Index: 1  2  3  4  5  6  7  8  9  10 11
    BIT:  [3, 5, -1, 10, 5, 9, -3, 24, 7, 9, 3]    
    ```

