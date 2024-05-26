# Problem Statement

## Description

You are given a binary tree and are expected to print the spiral order traversal of the tree, which is equivalent to the level order traversal of the tree in a zig-zag order. For the tree given below, the spiral order traversal is 1, 2, 3, 7, 6, 5, 4, 8, 9.

```graph

            1
         /     \
        2        3
       / \      / \
      4   5    6   7
    /         /
    8        9

```

## Pseudocode

```pseudocode
    
```

## Input Output

The input will be in the following format:

- The first line should be the number ‘n’. Here, the number ‘n’ is the total number of nodes present in the binary tree.
- The second line contains space-separated ‘n’ values. This is the level-order traversal of the tree. The code for inserting the values in the tree for the given level-order traversal has been addressed in the code.

Output:

The output should be the spiral level-order traversal of the tree with the nodes separated by spaces.

Sample Input: \
5 \
1 2 3 4 5

Sample Output: \
1 2 3 5 4

Sample Input: \
4 \
8 2 5 6

Sample Output: \
8 2 5 6

### Solution

```java

import java.util.*;

class Node {
    int data;
 Node left, right;
 
 Node(int value) {
  data = value;
  left = right = null;
 }
}

class Tree {
 Node root;
 
 Tree() {
  root = null;
 }
 
 // Method to construct a binary tree from the given array
 public Node insertNode(int[] elementsArr, Node node, int i) {
  if(i < elementsArr.length){
   node = new Node(elementsArr[i]);
   node.left = insertNode(elementsArr,node.left,2 * i + 1);
   node.right = insertNode(elementsArr,node.right,2 * i + 2);
  }
  return node;
 }
 
 public int level(Node node){
     if(node ==null) return 0;
     
     int leftLevel = 1 + level(node.left);
     int rightLevel = 1 + level(node.right);
     
     return Math.max(leftLevel,rightLevel);
 }
 // Method to traverse the elements of a tree using BFS (level-order traversal) in the spiral order
    public void spiralOrder() {
        // Write your code here
        int levels = level(this.root);
        for(int i=0;i<=levels;i++){
            printNodes(this.root,i,1);
        }
    }
    
    public void printNodes(Node node,int level,int currentLevel){
        if(node ==null) return;
        if(currentLevel ==level){
            System.out.print(node.data + " ");
            return;
        }else if(level%2 ==1){
            printNodes(node.right,level, currentLevel+1);
             printNodes(node.left,level, currentLevel+1);
        }else {
            printNodes(node.left,level, currentLevel+1);
            printNodes(node.right,level, currentLevel+1);
        }
        
    }
}

// WARNING: Do not edit the code given below; otherwise the test cases might fail
class Source {
 public static void main(String[] x) {
  Tree tree = new Tree();
  
  int size;
  Scanner sc = new Scanner(System.in);
  size = sc.nextInt();
  if (size < 0){
      System.out.println("Size should be a positive integer");
  }
  
  else{
      int[] elementsArr = new int[size];
      for(int i = 0; i < size; i++) {
       elementsArr[i] = sc.nextInt();
      }
      
      tree.root = tree.insertNode(elementsArr, tree.root, 0);
      
      tree.spiralOrder();
  }
 }
}

```
