# Graphs

## Explanation

A graph is an abstract data structure that represents the relationship between multiple nodes (entities) by connecting the nodes with edges.

G = (V, E). Here, G is a graph, which is a pair of two sets, where:

- V is a finite set of vertices (nodes), and
- E is a finite set of an ordered pair of the form (u, v), called an edge. The pair (u, v) indicates that there is an edge from vertex u to vertex v.

Graphs play a critical role in the application of social networks, transportation networks, etc. Certain applications of the graph data structure include the following:

- Graphs help with identifying contacts on social networking websites, such as Facebook; the nodes can be different users and the edges represent the relationships between them.
- Graphs help with finding the shortest distance between any two given locations; the nodes can be the different locations in a city and the edges represent the routes available between the locations.

Graph data structures do not have any restrictions like those of the tree data structure on the way different nodes are connected to each other. Tree data structures have usage restrictions in representing real-world scenarios, as each child node can have one parent node only. Let’s take a look at the two data structures in the diagram given below.

| Tree | Graph |
| ---- | ----- |
| Trees consist of only one root node, and only one parent node can be assigned to each child node. | Graphs do not have any specific root node and there is no such parent-child relation. Nodes are connected via edges wherever there is a relation between two nodes. |
| The tree data structure is a restricted form of graphs and does not contain any cycles or self-loops. | Graphs can be either cyclic or acyclic. |
| The number of edges in a tree is always n-1, where n indicates the number of nodes. | There is no restriction on the number of edges connecting the nodes, and the number of edges depends upon the graph’s structure. |

```graph

        Tree             Graph     

           1              1
         /  \           /  \
        2    3         2    3
       / \    \         \  /
      4   5    6          4

```

The chart given below shows the classification of graphs.

```graph

                Graphs
                  |
    -----------------------------
    |                           |
Undirected Graphs           Directed Graphs
                                |
            --------------------------------------
            |                                     |
    Directed Acyclic Graphs          Directed Cyclic Graphs
            |
          Tree
            |
     ----------------
    |               |
K-ary Trees      Binary Trees
  k != 2          k==2

```

### Undirected graphs

Graphs that show a symmetrical relationship between two connected nodes that are paired by an edge that represents a simple line are called undirected graphs.

```graph

  A -- B
  |    |
  C -- D

Vertices: {A, B, C, D}
Edges: {(A-B), (A-C), (B-D), (C-D)}

```

### Directed Graph (Digraph)

Graphs that show an asymmetrical relationship between two connected nodes that are paired by an edge that indicates the direction of the relationship from one node to the other are called directed graphs.

```graph

  A → B
  ^    ↓
  C <- D

Vertices: {A, B, C, D}
Edges: {(A→B), (B→D), (C→D), (D→A)}

```

### Directed Acyclic Graph (DAG)

These graphs fall under the sub-category of directed graphs. The only difference between a directed graph and a DAG (a directed acyclic graph) is that DAGs do not have cycles; this means if you start from any node in the graph and traverse through its connecting edges, then you can never return to the same node where you started.

```graph

  A → B
  ↓    ↓
  C → D

Vertices: {A, B, C, D}
Edges: {(A→B), (A→C), (B→D), (C→D)}

```

### Trees

These are restricted forms of graphs, and they fit the category of directed acyclic graphs with the restriction that each child node can have only one parent node in the structure.

```graph

           1
         /  \
        2    3
       / \    \
      4   5    6

Vertices: {1, 2, 3, 4, 5, 6}
Edges: {(1→2), (1→3), (2→4), (2→5),(3->6)}

```

### Connected graph

A graph is connected if a path exists from every vertex to every other vertex.

```graph

  A -- B
  |    |
  C -- D

Vertices: {A, B, C, D}
Edges: {(A-B), (A-C), (B-D), (C-D)}

```

### Disconnected graph

A graph is disconnected if there exist at least two nodes such that there is no path connecting them.

```graph

  A -- B   D -- E
  |    
  C

Vertices: {A, B, C, D, E}
Edges: {(A-B), (A-C), (B-C), (D-E)}

```

### Weighted Graph

A weighted graph is a graph where each edge has a weight or cost associated with it. These weights can represent various factors such as distance, time, or any other quantitative measure.

```graph

  A --5-- B
  |       |
  3       7
  |       |
  C --4-- D


Vertices: {A, B, C, D}
Edges with weights: {(A-B, 5), (A-C, 3), (B-D, 7), (C-D, 4)}

```

### Unweighted Graph

An unweighted graph is a graph where each edge has the same weight, usually considered as 1. In an unweighted graph, the focus is on connectivity rather than specific distances or costs between vertices.

```graph

  A -- B
  |    |
  C -- D

Vertices: {A, B, C, D}
Edges: {(A-B), (A-C), (B-D), (C-D)}

```

### Dense Graph

A graph is considered dense if the number of edges is close to the maximum number of edges. In other words, a dense graph has a large number of edges connecting its vertices.

- For an undirected graph with 𝑉  vertices, the maximum number of edges is 𝑉(𝑉−1) / 2 .
- For a directed graph, the maximum number of edges is 𝑉(𝑉−1).
- If the number of edges 𝐸 is close to these maximum values, the graph is dense.

```graph

    A --- B
    | \  / |
    |  X   |
    | /  \ |
    C --- D

Vertices (V): 4
Edges (E): 6 (maximum for an undirected graph with 4 vertices)

```

### Sparse Graphs

Definition:
A graph is considered sparse if the number of edges is much less than the maximum possible number of edges. Sparse graphs have relatively few edges compared to the number of vertices.

Characteristics:

- The number of edges 𝐸 is much less than
𝑉(𝑉−1) / 2  for an undirected graph or
𝑉(𝑉−1) for a directed graph.
- Many vertices have only a few connections.

```graph

A - B
|   |
C   D

```

### Graph Terminology

- **Neighbours**: If two nodes are adjacent to each other and connected by an edge, then those nodes are called neighbours.

- **Degree**: The number of edges that are connected to a node is called the degree of the node.

  - In the case of directed graphs, degree can be classified as:
    - In-degree: The number of incoming edges to a node
    - Out-degree: The number of outgoing edges from a node
  - For a directed graph:
    - Degree = In-degree (Edges pointing to the vertex) + Out-degree (Edges pointing away from the vertex).

- **Path**: When a series of vertices are connected by a sequence of edges between two specific nodes in a graph, the sequence is called a path. For example, in the graph above, {2, 1, 4, 5} indicates the path between nodes 2 and 5, and the intermediate nodes are 1 and 4.
