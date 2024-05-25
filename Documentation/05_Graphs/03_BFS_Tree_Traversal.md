# DFS Tree Traversal

## Explanation

Breadth-First Search (BFS) is a graph traversal algorithm that explores vertices in the order of their distance from the starting vertex. It explores all the vertices at the present "depth" level before moving on to vertices at the next depth level.

To implement a BFS, you need to consider the stage of each node. Nodes, in general, are considered to be in the following three different stages:

- Not visited
- Visited
- Completed.

In the BFS algorithm, nodes are marked as visited during traversal, in order to avoid the infinite loops caused due to the possibilities of cycles in a graph structure.

Steps:
- Initialize:
    - Start with a queue and enqueue the starting vertex.
    - Mark the starting vertex as visited.
- Traversal:
    - While the queue is not empty:
        - Dequeue a vertex from the queue.
        - Process the dequeued vertex (e.g., print it, store it).
        - For each adjacent (neighbor) vertex of the dequeued vertex:
            - If the adjacent vertex has not been visited:
                - Mark it as visited.
                -Enqueue it.

Properties:

- BFS visits each vertex once, making its time complexity O(V + E) for a graph with V vertices and E edges.
- It finds the shortest path (minimum number of edges) from the starting vertex to any other vertex in an unweighted graph.
- BFS is particularly useful for finding the shortest path in unweighted graphs and for exploring all vertices at the present depth level before moving on to vertices at the next depth level. 
- The algorithm uses a queue to manage the order of exploration and ensures that each vertex is processed once, making it efficient for large graphs.

## Pseudocode

```pseudocode

BFS(Graph, start_vertex):
    # Initialize an empty queue
    queue = new Queue()
    
    # Initialize a set to keep track of visited vertices
    visited = new Set()
    
    # Enqueue the start vertex and mark it as visited
    queue.enqueue(start_vertex)
    visited.add(start_vertex)
    
    # While the queue is not empty, continue the traversal
    while not queue.is_empty():
        # Dequeue a vertex from the queue
        current_vertex = queue.dequeue()
        
        # Process the current vertex (e.g., print it)
        print(current_vertex)
        
        # Get all adjacent vertices (neighbors) of the current vertex
        for neighbor in Graph.get_neighbors(current_vertex):
            # If the neighbor has not been visited, mark it as visited and enqueue it
            if neighbor not in visited:
                visited.add(neighbor)
                queue.enqueue(neighbor)


```