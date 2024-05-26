# Shortest Distance Between Two Cells in Matrix

## Description

Given a matrix of N*M, find the shortest distance from a source cell to a destination cell on traversing through limited cells only, also you can move only up, down, left and right. If found print the distance else -1.

Where,

s represents ‘source’.

d represents ‘destination’.

* represents the cell where you can travel.

0 represents cells where you can not travel.

For example:

Input

4 4

0 * 0 s

* 0 **

0 ** *

d ** *

Output

6

Note: You cannot traverse ‘*’ on the route (If ‘*’ is found on the route, then it means that at that position, the route will get blocked).

The steps involved in the solution approach are as follows:

1. Store each cell as a tuple with its row, column values and distance from the source cell.

2. Start the BFS traversal from the source cell by pushing it in a queue.

3. Make a visited array with all having ‘1’ at place stores 'false' in the visited array and for all indexes whose value is ‘0’ assigned 'true' values in the visited array. This array will help you know which elements are already traversed and also help you by not solving the same problem again and again.

4. While the queue is not empty, keep popping the front of the queue. If the popped cell is the destination, then print the distance and return else; if its adjacent cells have '*', then add an adjacent cell in the queue (since it is reachable) with distance +1.

In the above example,‘s’ is at (0,3) and ‘d’ is at (3,0).

Here, the possible traversing routes between ‘s’ and ‘d are as follows:

(1,3),(2,3),(3,3),(3,2),(3,1),(3,0)

(1,3),(2,3),(2,2),(3,2),(3,1),(3,0)

(1,3),(1,2),(2,2),(3,2),(3,1),(3,0)

(1,3),(1,2),(2,2),(2,1),(3,1),(3,0)

Breadth-first search will always give the shortest distance because it traverses in level-order. So, the destination would be reached in the shortest distance possible.

## Input Output

Input Format:

First line contains two values rows and columns as numbers.

Next line is followed by the number of rows and columns as char array input.  

Output Format:

Print the distance if possible else print -1.

Sample Test Cases:

Input

4 4

0 * 0 s

* 0 **

0 ** *

d ** *

Output

6

### Solution

```java

import java.util.*;

class QItem {
 public int row;
 public int col;
 public int dist;
 public QItem(int x, int y, int w) {
  this.row = x;
  this.col = y;
  this.dist = w;
 }
}

class DefineConstants {
 public static int N;
 public static int M;
}


public class Source {
 public static int minDistance(char[][] grid) {
        // Add code here
    }

 public static void main(String[] args) {
     Scanner sc = new Scanner(System.in);
     int rows = sc.nextInt();
     int cols = sc.nextInt();
     DefineConstants.N = rows;
     DefineConstants.M = cols;
     char inputArray[][] = new char[rows][cols];

        for (int i = 0; i < rows; i++) { 
            for (int j = 0; j < cols; j++) { 
                inputArray[i][j] = sc.next().charAt(0);
            } 
        } 
  System.out.print(minDistance(inputArray));
 }
}

```
