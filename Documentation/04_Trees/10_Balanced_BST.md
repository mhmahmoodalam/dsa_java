# Balanced Binary Search Tree

While storing a dataset in a BST it is very important that the data is sanitized a little bit. Otherwise the tree could be unbalanced and thus end up being a linked list

For example:

Imagine adding the values 1, 2, 3, 4 and 5 in this order to create a binary search tree. The final tree will look like a linked list.

> If data used to create a tree that has values in the increasing or decreasing order, the resultant tree will effectively be a linked list, and the efficiency of the search operation will become $O(n)$. So, preprocessing data can improve the search efficiency of binary search trees.

## Analysis

Storing the data that will produce balanced binary search trees and, will enhance the efficiency of the search process to $O(logn)$, as it reduces the number of comparisons required in the trees.

There are self-balancing BSTs that will attempt to balance themselves when new nodes are added to the trees.

- Red-Black trees
- AVL Trees

## Psedocode

The algorithm given below can be followed to create a balanced BST from the elements in a sorted array:

- Get the middle element of the sorted array and make it the root of the BST.
- Recursively repeat the same for the left half and the right half of the array.
      - Get the middle of the left half and make it the left child of the root created in Step 1.
      - Get the middle of the right half and make it the right child of the root created in Step 1.

## Description

Given a binary tree, construct a balanced binary search tree consisting of the sum of each node and its children (Note: All its children and not immediate children). The output should be the postOrder traversal of the new binary search tree.

## Input Output

In the input, the first value 6 is the size of the tree. The values in the second line correspond to the inorder traversal of the given binary tree, and the last line corresponds to the pre-order traversal of the given binary tree.

The output is the post-order traversal of the new binary search tree that is supposed to be constructed with node values separated by spaces.

Sample Input: \
6 \
6 10 20 1 51 43 \
1 10 6 20 43 51

Sample Output: \
20 6 51 131 94 36

Sample Input: \
5 \
40 60 30 20 50 \
50 20 30 60 40

Sample Output: \
100 40 200 150 130

### Solution

```java
import java.util.Scanner;
import java.util.Arrays;
class Node 
{
    int value;
    Node leftchild, rightchild;
  
    Node(int item) 
    {
        value = item;
        leftchild = rightchild = null;
    }
}
  
class BinaryTree 
{
    Node root;
    static int preIndex = 0;
    static int index=0;
    
    Node constructTree(int in[], int pre[], int inStrt, int inEnd) 
    {
        if (inStrt > inEnd) 
            return null;
  
        Node tNode = new Node(pre[preIndex++]);
  
        if (inStrt == inEnd)
            return tNode;
  
        int inIndex = search(in, inStrt, inEnd, tNode.value);
  
        tNode.leftchild = constructTree(in, pre, inStrt, inIndex - 1);
        tNode.rightchild = constructTree(in, pre, inIndex + 1, inEnd);
  
        return tNode;
    }
     
    int search(int arr[], int strt, int end, int value) 
    {
        int i;
        for (i = strt; i <= end; i++) 
        {
            if (arr[i] == value)
                return i;
        }
        return i;
    }
    
    int sumBinaryTree(Node node)
    {   
        // Write the logic to recursively create Binary Tree consisting of sum of all its children
        if(node ==null) return 0;
        node.value = node.value +sumBinaryTree(node.leftchild)+sumBinaryTree(node.rightchild);
        return node.value;
    }
    
    void printPostorder(Node node)
    {
        if (node == null)
            return;
 
        // first recur on left subtree
        printPostorder(node.leftchild);
 
        // then recur on right subtree
        printPostorder(node.rightchild);
 
        // now deal with the node
        System.out.print(node.value + " ");
    }
    
    void inOrder(Node node, int array[])
    {
        if (node == null)
            return;
        inOrder(node.leftchild, array);
        array[index++] = node.value;
        inOrder(node.rightchild, array);
        
    }
    
    Node ArrayToBST(int arr[], int start, int end) {
        // Write logic to convert the array representing Binary Tree to Binary Search Tree
        if( start<=end){
            int mid = start +(end -start)/2;
            Node node = new Node(arr[mid]);
            node.leftchild = ArrayToBST(arr,start,mid-1);
            node.rightchild=ArrayToBST(arr,mid+1,end);
            return node;
        }else return null;
        
    }
}
class Source{
  
    // driver program to test above functions
    public static void main(String args[]) 
    {
        Scanner scanner = new Scanner(System.in);
        int len = scanner.nextInt();
        int in[] = new int[len];
        int pre[] = new int[len];
        for(int i=0;i<len;i++){
            in[i] = scanner.nextInt();            
        }
        for(int i=0;i<len;i++){
            pre[i] = scanner.nextInt();
        }
        BinaryTree tree = new BinaryTree();
        Node root = tree.constructTree(in, pre, 0, len - 1);
        tree.sumBinaryTree(root);
        int inSumTree[] = new int[len];
        tree.inOrder(root, inSumTree);
        Arrays.sort(inSumTree);
        Node bstRoot = tree.ArrayToBST(inSumTree, 0, len-1);
        tree.printPostorder(bstRoot);
        
    }
}



```
