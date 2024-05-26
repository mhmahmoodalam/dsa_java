# Problem Statement

The lowest common ancestor of nodes n1 and n2 is the lowest possible node in the tree whose descendants include nodes n1 and n2.

Note:

- Descendants of a node are all the nodes that are derived from that node.
- Consider that the node is a descendant of itself.
- LCA = n1 when n2 descends from n1

```graph

                15
         /           \
        10             20
      /   \          /    \
    5      13       17      6
  /  \    /  \     /  \    /  \
 3   7   12  14   16  18  24  27

```

If this BST is given, then the common ancestor of nodes 5 and 13 is 10 because 10 is the lowest possible node in the tree wherein its descendants include node 5 and node 13.

The lowest common ancestor of nodes 20 and 24 is 20 because node 20 is a descendant of itself, 24 is a descendant of 20 and node 20 is the lowest possible node in the tree whose descendants are node 20 and node 24.

so what is the LCA of 5 & 14?

- Traverse through the root node of the tree.
- The root node 15 is the common ancestor of 5 and 14 because the descendants of 15 contain nodes 5 and 14, but it is not the lowest common ancestor of node 5 and node 14. (Here, you can observe that 5 and 14 are less than node 15.)
- Based on the property of BST, you need to traverse through the left subtree of the root node, as both nodes 5 and 14 are less than 15 (root node). The first left descendant of the root node is node 10.
- Node 10 is the common ancestor of nodes 5 and 14. To get the lowest common ancestor. you can traverse through the tree further, but it does not give you the common ancestor of nodes 5 and 14; hence, the traversal stops here. (Also, you can observe that 10 is not greater than both 5 and 14, and 10 is not less than both 5 and 14.)
    - Since it is not possible to go further below, return 10 as the LCA of nodes 5 and 14.

## Description

## Pseudocode

Suppose we want to find the lowest common ancestor of nodes n1 and n2.

Let's assume the root node as 'root'.

- Recursively traverse through the BST from the root node.
- If the root is greater than both n1 and n2, then recursively traverse through the left subtree of the root node to find out the LCA of the two given nodes because the LCA  of the given nodes lies in the left subtree.
- If the root node is less than both n1 and n2, then recursively traverse through the right subtree of the root node to find out the LCA of the two given nodes because the LCA of the given nodes lies in the right subtree.
- Otherwise, the root itself is the lowest common ancestor of the binary search tree.

```pseudocode
if n1 n2 < node -> traverse left to find the ancestor
else if n1 n2 > node -> traverse right
else if n1<node and n2> node -> return node

```

## Input Output

Input: The input will be in the following format:

- The first line will be ‘n’, which represents the number of elements to be inserted into the BST.
- The next line will be n elements separated by spaces, which represents the elements to be inserted into the BST. The code for inserting the values in the tree has been addressed in the code.
- The next line will be the value of node n1.
- The next line will be the value of node n2.

Output: The output should be in the following format:

The value of the lowest common ancestor of nodes n1 and n2

Sample Input: \
15 \
12 6 18 3 9 15 20 1 11 19 10 18 31 4 21 \
3 \
10

Sample Output: \
6

Sample Input: \
5 \
8 7 15 2 20 \
7 \
2

Sample Output: \
7

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

class BST {
 Node root;
 
 BST() {
  root = null;
 }
 
 // Method to construct a binary tree from the given array
 void insert(int key) { 
       root = insertRec(root, key); 
    } 
      
    // A recursive function to insert a new key in BST
    Node insertRec(Node root, int key) { 
  
        if (root == null) { 
            root = new Node(key); 
            return root; 
        } 
  
        if (key < root.data) 
            root.left = insertRec(root.left, key); 
        else if (key > root.data) 
            root.right = insertRec(root.right, key); 
  
        return root; 
    }
 
 // Method to find the lowest common ancestor of two nodes - n1 and n2
    Node lca(Node node, int n1, int n2) {
        if(node ==null) return null;
        if( n1 >node.data &&n2> node.data) return lca(node.right,n1,n2);
        else if(n1<node.data && n2<node.data) return lca(node.left,n1,n2);
        return node;
    }
}

// WARNING: Do not edit the code given below; otherwise the test cases might fail
public class Source {
 public static void main(String[] x) {
  BST bst = new BST();
  
  int size;
  Scanner sc = new Scanner(System.in);
  size = sc.nextInt();
  
  if(size>0){
      int[] elementsArr = new int[size];
      for(int i = 0; i < size; i++) {
       elementsArr[i] = sc.nextInt();
       bst.insert(elementsArr[i]);
      }
      
         int n1 = sc.nextInt();
      int n2 = sc.nextInt();
      
            Node lca = bst.lca(bst.root, n1, n2);
            System.out.print(lca.data);
     }
     else
         System.out.println("Size should be a positive integer");
 }
}


```
