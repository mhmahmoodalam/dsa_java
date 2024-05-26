# Binary Tree Traversal

## Explanation

The two ways of traversing a tree are as follows:

- Depth-first search (DFS)
- Breadth-first search (BFS)

### Depth-first search (DFS)

Depth of tree is the maximum of all teh level of the tree. So for below tree the depth would be 3.

```graph
           1 (0)
         /  \
       6(1)   8(1)   Depth(tree) = max (level(n))
       /  \     \
   (2)2   5(2)   7(2)  
          / \
      (3)4   3(3)
  
```

DFS using siblings - depth first traversal says before $n^{'}$ we should have traversed all child nodes of n

```graph

         root
         /  \
        n    n'
       / \    
     n'  n"    

```

DFS using Depth - We proceed towards the left until we reach the leaf and then backtrack and proceed towards the next child

```graph
          (0) 1 (10) (14)
         /         \
     (1)6(3)(9)   (11)8(13) 
       /  \            \
   (2)2  (4)5(6)(8)   (12)7
           / \
        (5)4   3(7)

depth traversal -> 1 -> 6 -> 2 -> 5 -> 4 -> 3 -> 5 -> 8 -> 7
  
```

### Variant of DFS

Based on which stage we are performing any action during the traversal there are different variants of DFS

- stage 1 : when none of the child nodes are visited
- stage 2 : when the left child is visited but right is not
- stage 3 : when the both child is visited

```graph
                1 (stage 1)
            /            \
   ---------------       ---------
  |     6(1)      |     |  8(1)   |
  |     /  \      |     |    \    |
  | (2)2   5(2)   |     |    7(2) |
  |        / \    |     ----------
  |    (3)4   3(3)|      (stage 3)
  |               |
  ----------------
   (stage 2)

Preorder - stage 1
Inorder - stage 2
Postorder - stage 3

```

- Preorder (stage 1, stage 2, stage 3)  : 1,6,2,5,4,3,8,7
- Inorder (stage 2, stage 1, stage 3)   : 2,6,4,5,3,1,8,7
- Postorder (stage 2, stage 3, stage 1) : 2,4,3,5,6,7,8,1

## DFS Pseudo code

```java
class Node {
    int data; // value contained inside a node
    Node left, right; // left & right children of a node

    // constructor to set the data of a node to the passed value and make it a leaf node
    Node(int value) {
        data = value;
        left = right = null;
    }
}

void preOrderDFS(Node node) {
    if (node == null)
        return;

    // visit the parent node (parent of left & right children)
    System.out.print(node.data + " ");

    // recursively go to left subtree
    preOrderDFS(node.left);

    // recursively go to right subtree
    preOrderDFS(node.right);
}

// Method to print the tree in in-order traversal
void inOrderDFS(Node node) {
    if (node == null)
        return;

    // recursively go to left subtree
    inOrderDFS(node.left);

    // visit the parent node (parent of left & right children)
    System.out.print(node.data + " ");

    // recursively go to right subtree
    inOrderDFS(node.right);
}

// Method to print the tree in post-order traversal
void postOrderDFS(Node node) {
    if (node == null)
        return;

    // recursively go to left subtree
    postOrderDFS(node.left);

    // recursively go to right subtree
    postOrderDFS(node.right);

    // visit the parent node (parent of left & right children)
    System.out.print(node.data + " ");
}


```

### Problem Statement(1)

#### find the multiple nodes

You are given a binary tree. You need to print all the nodes that are multiples of the root node. The nodes that are multiples of the root node should be printed using in-order traversal.

```graph

           5
         /   \
        10    15
       / \    / \
      20 25  12  30

```

#### Input Output(1)

Input:

- The first line should be the number ‘n’. Here, ‘n’ represents the number of nodes present in the binary tree.
- The second line contains space-separated ‘n’ values. These are the values of respective nodes. The code for inserting the values in the tree has already been addressed in the code.

Output:

The output should be all the nodes that are multiples of the root node. Note: Print the nodes using inorder traversal separated by spaces.

Sample Input: \
5 \
3 4 5 6 7

Sample Output: \
6 3

Sample Input: \
4 \
0 1 2 3

Sample Output:
Division by zero is undefined

#### Solution(1)

```java
import java.util.*;
class Node{
 int data;
 Node left,right;
 
 Node(int value) {
  data = value;
  left = right = null;
 }
}

class Tree{
 Node root;
 
 Tree() {
  root = null;
 }
 
 // Method to construct a binary tree from the given array (Do not edit the code given below)
 public Node insertNode(int[] elementsArr, Node node, int i){
  if(i < elementsArr.length){
   node = new Node(elementsArr[i]);
   node.left = insertNode(elementsArr,node.left,2 * i + 1);
   node.right = insertNode(elementsArr,node.right,2 * i + 2);
  }
  return node;
 }
 
 // Method to print nodes that are multiple of root node
 public void printNodes(Node node){
  if(this.root.data==0){
      System.out.println("Division by zero is undefined");
      return;
  }
  if(node ==null)return;
  printNodes(node.left);
  if(node.data % this.root.data==0){
      System.out.print(node.data +" ");
  }
  printNodes(node.right);
 }
}

// WARNING: Do not edit the code given below, otherwise the test cases might fail
class Source{
 public static void main(String[] x){
  Tree tree = new Tree();
 
  Scanner sc = new Scanner(System.in);
     
     int size; 
  size = sc.nextInt();
  
  if(size<= 0){
      System.out.println("Size should be a positive integer");
  }
  
  else{
      int[] elementsArr = new int[size];
      for(int i = 0; i < size; i++){
       elementsArr[i] = sc.nextInt();
      }
      tree.root = tree.insertNode(elementsArr,tree.root,0);
      tree.printNodes(tree.root);
  }
 }
}


```

### Problem Statement(2)

#### Find Height of Binary Tree

You are given a binary tree. You need to print the maximum height of the binary tree. If the tree is NULL (empty tree), print the height of the tree as 0.


```graph

           1
         /   \
        2     3
       / \    
      4  5  

```

#### Input Output(2)

Input:

- The first line should be the number ‘n’. Here, the number ‘n’ is the total number of nodes present in the binary tree.
- The second line contains space-separated ‘n’ values. The code for inserting the values in the tree has been addressed in the code.

Output:

The output should be the height of the tree keeping in mind that the root node is at level 1.

Sample Input: \
5 \
1 2 3 4 5

Sample Output: \
3

Sample Input: \
0 \

Sample Output:
0

#### Solution(2)

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
 
 // Method to find the height of a binary tree
 public int findHeight(Node node,int height) {
  // Write your code here
  if(this.root ==null) return 0;
  if(node ==null) return height;
  height++;
  int leftHeight =findHeight(node.left,height);
  int rightHeight =findHeight(node.right,height);
  return Math.max(leftHeight,rightHeight);
 }
}

// WARNING: Do not edit the code given below; otherwise the test cases might fail
public class Source {
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
      
      System.out.println(tree.findHeight(tree.root,0));
     }
 }
}

```

## BFS (Breadth First Traversal)

The breadth first traversal follows the level order traversal and it says that the nodes at lower level should be visited first before the higher level nodes

```graph

            1 (0)
         /         \
        6(1)        8(1) 
       /  \            \
   (2)2  (2)5         (2)7
           / \
        (3)4   3(3)

levels of the tree. Root is considered at level 0 here

--------- Traversal order --------

          (0) 1 
         /      \
     (1)6        8(2)
       /  \        \
   (3)2  (4)5       7(5)
           / \
        (6)4   3(7)

breadth traversal -> 1 -> 6 -> 8 -> 2 -> 5 -> 7 -> 4 -> 3
  
```

### BFS traversal

there  are two ways that we can traverse through BFS

- recursive approach
- iterative approach

#### Recursive approach

```java

int height(Node root) {
    if (root == null)
        return 0;
    int leftHeight = height(root.left);
    int rightHeight = height(root.right);

    if (leftHeight > rightHeight)
        return leftHeight + 1;
    else
        return rightHeight + 1;
}

// Method to traverse the elements of a tree using BFS (level-order traversal) in recursive way
void levelOrderOrBFS() {
    int h = height(root);
    for (int i = 1; i <= h; i++)
        printNodesAtLevel(root, i, 1);
}

// Method to print nodes at the given level
void printNodesAtLevel (Node root, int level, int currentLevel) {
    if (root == null)
        return;
    if (level == currentLevel)
        System.out.print(root.data + " ");
    else {
        printNodesAtLevel(root.left, level, currentLevel + 1);
        printNodesAtLevel(root.right, level, currentLevel + 1);
    }
}
```

#### iterative approach

```java
void levelOrderOrBFS() {
    Queue<Node> queue = new LinkedList<Node>();
    queue.add(root);

    while (!queue.isEmpty()) {
        Node temp = queue.peek();
        queue.remove();
        System.out.print(temp.data + " ");

        // enqueue left child into queue
        if (temp.left != null)
            queue.add(temp.left);

        // enqueue right child into queue
        if (temp.right != null)
        queue.add(temp.right);
    }
}

```

#### Problem Statement (Print Maximum Value)

You are given a binary tree. You need to print the node that has the highest value in the binary tree using the BFS (Iterative) approach. If the tree is empty, the output should be -1.

```graph

           2
         /   \
        8     10
       / \    /  \
      1   5  9    3

```

#### Input output

- The first line should be the number ‘n’. Here, the number ‘n’ is the total number of nodes present in the binary tree.
- The second line contains space-separated ‘n’ values. No value should be equal to -1. The code for inserting the values in the tree has already been taken care of in the code.

Output:
The output should be the maximum value among all nodes in the tree.

Sample Input: \
5 \
1 2 3 4 5

Sample Output: \
5

Sample Input: \
0

Sample Output: \
-1

```java 
import java.util.*;


class Node { 
 int data; 
 Node left, right; 

 public Node(int value) { 
  data = value; 
  left = right = null; 
 } 
} 

class BinaryTree { 

 Node root; 

    BinaryTree(){
        root = null;
    } 
    
    // Method to construct a binary tree from the given array
 public Node insertNode(int[] elementsArr, Node node, int i){
  if(i < elementsArr.length){
   node = new Node(elementsArr[i]);
   
   node.left = insertNode(elementsArr,node.left,2 * i + 1);
   node.right = insertNode(elementsArr,node.right,2 * i + 2);
  }
  return node;
 }
 
 // Method to find the largest value in the tree
 public int findMax(Node node) 
 { 
  if(node ==null)return -1;
  Queue<Node> queue = new LinkedList<Node>();
  queue.add(node);
  int max= Integer.MIN_VALUE;
  while(!queue.isEmpty()){
      Node temp = queue.peek();
      queue.remove();
      if(temp.data > max) max =temp.data;
      if (temp.left != null) queue.add(temp.left);
            if (temp.right != null)queue.add(temp.right);
      
  }
  
  return max;
  
 } 
}
// WARNING: Do not edit the code given below; otherwise the test cases might fail
public class Source{
 public static void main(String[] x){
  BinaryTree tree = new BinaryTree();
  
  int size;
  Scanner sc = new Scanner(System.in);
  size = sc.nextInt();
  
  if(size == 0){
      System.out.println("-1");
  }
  
  else if (size < 0){
      System.out.println("Size should be a positive integer");
  }
  
  else{
          int[] elementsArr = new int[size];
          for(int i = 0; i < size; i++){
           elementsArr[i] = sc.nextInt();
          }
          
          tree.root = tree.insertNode(elementsArr,tree.root,0);
          
          System.out.println(tree.findMax(tree.root));
      }
 }
}
```
