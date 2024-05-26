# Topological Sorting

Topological sorting for a directed acyclic graph (DAG) is a linear ordering of vertices such that for every directed edge u v, vertex u comes before v in the ordering. Topological sorting for a graph is not possible if the graph is not a DAG. Your task is to find out whether the topological sorting is done correctly or not.

## Description

Given a Directed Graph, find any Topological Sorting of that Graph. 

> There can be more than one topological sorting for a graph.
> The first vertex in a topological sorting is always a vertex with an in-degree as 0 (a vertex with no incoming edges).

## Pseudocode

```pseudocode

topological_sort(n,adj[n][n]):

    t = []

    visited = []

    in_degree = []

    for i = 0 to n

        in _degree[i] = visited[i] = 0

    for i = 0 to n

        for j = 0 to n

            If adj[i][j] is True

                in_degree+=1

    for i = 0 to n

        If in_degree is 0

            enqueue(Queue,I)

            visited[i] = True    

    while Queue is not Empty

        vertex = get_front(Queue)

        dequeue(Queue)

        t.append(vertex)

        for j = 0 to n

            if adj[vertex] is True and visited is False

                in_degree -=1

                if in_degree is 0

                    enqueue(Queue,j)

                    visited[j] = True

    return t 

```

## Input Output

Input Format:

The first line contains a number T as test cases.

The first line of each test case contains two integers E and V representing no of edges and the number of vertices. Then the next line contains E pairs of integers u, v representing an edge from u to v in the graph.

For example if E is 2 and V is 2 then it requires 2*2 = 4 inputs in the next line.

Output Format:

For each test case print 1 if the topological sort is done correctly, otherwise print 0.

Sample Test Cases:

Input

2

6 6

5 0 5 2 2 3 4 0 4 1 1 3

3 4

3 0 1 0 2 0

Output

1

1

### Solution

```java
import java.util.*;
import java.io.*;
import java.lang.*;


public class Source {
    public static void main(String[] args) throws IOException {
        BufferedReader read = new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(read.readLine());

        while (t-- > 0) {
            ArrayList<ArrayList<Integer>> list = new ArrayList<>();
            String st[] = read.readLine().trim().split("\\s+");
            int edg = Integer.parseInt(st[0]);
            int nov = Integer.parseInt(st[1]);

            for (int i = 0; i < nov + 1; i++)
                list.add(i, new ArrayList<Integer>());

            String s[] = read.readLine().trim().split("\\s+");
            int p = 0;
            for (int i = 1; i <= edg; i++) {
                int u = Integer.parseInt(s[p++]);
                int v = Integer.parseInt(s[p++]);
                list.get(u).add(v);
            }

            int[] res = new TopologicalSort().topoSort(list, nov);

            if (check(list, nov, res) == true)
                System.out.println("0");
            else
                System.out.println("1");
        }
    }
    static boolean check(ArrayList<ArrayList<Integer>> list, int V, int[] res) {
        int[] map = new int[V];
        for (int i = 0; i < V; i++) {
            map[res[i]] = i;
        }
        for (int i = 0; i < V; i++) {
            for (int v : list.get(i)) {
                if (map[i] > map[v]) return false;
            }
        }
        return true;
    }
}
/*Complete the function below

ArrayList<ArrayList<>Integer>adj: to represent graph containing 'N' vertices and edges between them N: represent number of vertices

*/


class TopologicalSort {
    static int[] topoSort(ArrayList<ArrayList<Integer>> list, int N) {
      // Add code here
    }
    
   
    private static void dfs(ArrayList<ArrayList<Integer>> list, int u, Set<Integer> visited, Deque<Integer> dq) {
        // Add code here
    }
}


```
