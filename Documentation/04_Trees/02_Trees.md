# Tree

## Tree Vocabulary

```graph

           1
         / | \
        2  3  4
       / \     \
      5   6     7

```

All the elements in a tree are called **nodes**. In the tree given above, the nodes are the ones with the values 1, 2, 3, 4, 5, 6 and 7.

Nodes can be of different types. The topmost node in a tree is called the **root node**.

From the root node, descend some other nodes. The root node is called a parent if there is at least one or more node descending from it directly. In that case, we can call root node 1 as the parent node having node 2 as a child node. Node 1 is also the parent of nodes 3 and 4. Similarly, node 2 is the parent of nodes 5 and 6, and node 4 is the parent of node 7.

A node that does not have any child is called a **leaf node**. In the tree given above, nodes 3, 5, 6 and 7 are called leaf nodes.

The nodes at the same level descending from the same parent are called **siblings**. In the tree given above, nodes 2, 3 and 4 are siblings.

Following is the vocabulary for the tree given above: \
Nodes: 1, 2, 3, 4, 5, 6, 7

Root Node: 1 \
Parent Nodes & their Children Nodes: \
Parent - 1, Children - 2, 3, 4 \
Parent - 2, Children - 5, 6 \
Parent - 4, Child - 7

Leaf Nodes: 3, 5, 6, 7 \
Sibling Nodes: (2, 3, 4), (5, 6)

- Edge: The link between two nodes. Each edge connects a parent node to a child node.

```graph
Parent --(edge)--> Child
```

- Parent: A node that has one or more child nodes. Here B is the parent

```graph
  B
 / \
D   E

```

- Child: A node that is a descendant of another node. In other words, a node linked to a parent node by an edge. Here D & E are children of B.

```graph
  B
 / \
D   E

```

- Sibling: Nodes that share the same parent. D & E are siblings

```graph
  B
 / \
D   E

```

- Leaf: A node that does not have any children. Leaf nodes are also known as terminal nodes. Here B & E are leaf nodes

```graph
  A
 / \
B   C
   /
  E
```

- Internal Node: A node that has at least one child. These are the opposite of leaf nodes. Here A & C

```graph
  A
 / \
B   C
   /
  E
```

- Subtree: A tree consisting of a node and its descendants. Any node in a tree can be considered the root of a subtree.

- Level: The level of a node is defined by 1 + the number of edges between the node and the root. The root is at level 1.

```graph
  A       (level 1)
 / \
B   C     (level 2)

```

- Height: The height of a tree is the length of the longest path from the root to a leaf. The height of a node is the length of the longest path from that node to a leaf. The height of single node tree is 1

```graph
   A       (height 2)
  / \
 B   C     (height 1)
    /
   D       (height 0)
```

- Height of node : The height of a node is the number of edges present in the longest path connecting that node to a leaf node. Height of C in above tree is 1 and 0 for B.

- Depth: The depth of a node is the number of edges from the root to that node. It is similar to the level of the node.

```graph
   A       (depth 0)
  / \
 B   C     (depth 1)
    /
   D       (depth 2)
```

- Degree: The degree of a node is the number of children of that node. The degree of a tree is the maximum degree of any node in the tree. Node "A" has a degree of 2, while node "C" has a degree of 1.

```graph
  A
 / \
B   C
   /
  E
```


## Tree Properties

### No Cycle in Tree

An important point to remember is that a tree cannot have any cycle. A cycle means that in a tree, a child node cannot have two parent nodes. Take a look at the figure given below.

```graph
  1
 / \
2   3
\  /
  4
```

You can see that the child node 4 has two parents–node 2 and node 3–which builds a cycle in the figure given above. Thus, the above figure cannot be considered to be a tree.

### Number of edges = Number of nodes - 1

An edge is a line connecting two nodes in a tree. Every node except the root has a unique edge from its parent to the node. Thus, if there are N nodes in the tree, the number of edges would be N-1, i.e., one per node except for the root. Thus, if there are N nodes in a tree, the number of edges will be equal to N-1.
