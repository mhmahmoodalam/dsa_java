# Implementing a graph

## Explanation

Dijkstra's algorithm is a popular algorithm used to find the shortest paths from a single source vertex to all other vertices in a weighted graph. The graph must have non-negative edge weights.

Steps:

- Initialization:
  - Set the distance to the source vertex to 0 and the distance to all other vertices to infinity.
  - Create a priority queue (or min-heap) and insert the source vertex with a distance of 0.
  - Maintain a set of visited vertices to avoid reprocessing vertices.
- Main Loop:
  - While the priority queue is not empty:
  - Extract the vertex 𝑢 with the minimum distance from the priority queue.
  - Mark 𝑢  as visited.
  - For each neighbor 𝑣 of 𝑢 :
    - If 𝑣 has not been visited:
      - Calculate the alternative path distance through 𝑢 to 𝑣 (i.e., 𝑑𝑖𝑠𝑡𝑎𝑛𝑐𝑒[𝑢] + 𝑤𝑒𝑖𝑔ℎ𝑡(𝑢,𝑣)).
      - If this alternative path distance is less than the current known distance to 𝑣, update the distance to 𝑣 and insert or update 𝑣 in the priority queue with the new distance.
- Termination:
  - The algorithm terminates when the priority queue is empty, and the shortest path distances from the source to all vertices have been determined.

Properties:

- Time Complexity: The time complexity of Dijkstra's algorithm is 𝑂((𝑉+𝐸)log⁡𝑉) when implemented with a priority queue (min-heap), where 𝑉 is the number of vertices and 𝐸 is the number of edges.
- Space Complexity: The space complexity is 𝑂(𝑉)for storing the distances and the priority queue.

## Notes

> Dijkstra's algorithm efficiently finds the shortest paths from a single source vertex to all other vertices in a weighted graph with non-negative edge weights. It uses a priority queue to always extend the shortest known path, ensuring optimal solutions.

### Pseudocode

```pseudocode

Procedure Dijkstra(graph, node)
Perform edge relaxation for all the outgoing edges from the starting node
  While Q is not empty
      Dequeue the first element from priority queue
      nextNode ← front element of queue after previous deque
      if nextNode is not null
        Relax the edges if necessary
      end if
   end while
end procedure


```

```graph
  
  
```
