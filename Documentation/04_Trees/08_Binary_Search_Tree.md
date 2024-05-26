# Binary Search Tree

A binary search tree is also called an ordered binary tree because of the following properties:

- The values of all the nodes in the left subtree are lower than those of the root node.
- The values of all the nodes in the right subtree are greater than those of the root node.
- Each subtree in the binary search tree is itself a binary search tree.

> [Use this interactive platform for BST operations](http://btv.melezinek.cz/binary-search-tree.html)

## Analysis

### searching in BST

While searching for an element X, you first compare it with the root node. If the element is less than the value of the root node, you move on to the left subtree. In case the element is greater than the value of the root node, you move on to the right subtree. In either of the cases, you are reducing your search space by half. When you move on to either child of the root node, you compare X with it, and again, you move to its left or right depending on whether the value to be searched for is less than or greater than the value of the child node. Once again, the other half is ignored. So, at every step, one half of the sample space is ignored, which makes the operation an O(log n) operation.

```java
boolean search(Node node, int key) {
    if (node == null)
        return false;

    if (key == node.data)
        return true;

    if (key < node.data)
        return search(node.left, key);
    else
        return search(node.right, key);
}
```

- time complexity of serching a key in BST is $O(logn)$
- This works on the divide and conquer searching algorithm

### Adding to a BST

- The adding starts at the root node
- it checks if the value is less than or greater than the node, accordingly it is added to left or right subtree
- Whenever a new node is added to a BST, it has to be added as a leaf node. It cannot be an internal node.
- it works the same as finding a node
- it takes $O(logn)$ for addition

```java

Node insert(Node node, int key) {
    if (node == null) {
        node = new Node(key);
        return node;
    }

    if (key < node.data)
        node.left = insert(node.left, key);
    else if (key > node.data)
        node.right = insert(node.right, key);

    return node;
}

```

### Deleting a node from a BST

The deletion of data from binary search trees can be carried out in the following three ways:

- If the node to be deleted is a leaf node, it is directly removed from the tree.
- If the node has one child, the node itself is deleted, and its child node is connected to its parent node.
- If the node has two children, you find its successor to replace it. The successor node is the minimum node in the right subtree or the maximum node in the left subtree.

```java

class TreeNode {
    int val;
    TreeNode left, right;

    public TreeNode(int item) {
        val = item;
        left = right = null;
    }
}

public class BST {
    TreeNode root;

    public BST() {
        root = null;
    }

    // Method to delete a node in BST
    TreeNode deleteNode(TreeNode root, int key) {
        // Base case: If the tree is empty
        if (root == null) return root;

        // Recur down the tree
        if (key < root.val)
            root.left = deleteNode(root.left, key);
        else if (key > root.val)
            root.right = deleteNode(root.right, key);
        else {
            // Node with only one child or no child
            if (root.left == null)
                return root.right;
            else if (root.right == null)
                return root.left;

            // Node with two children: Get the inorder successor (smallest in the right subtree)
            root.val = minValue(root.right);

            // Delete the inorder successor
            root.right = deleteNode(root.right, root.val);
        }

        return root;
    }

    // Method to find the minimum value node in the given tree
    int minValue(TreeNode root) {
        int minv = root.val;
        while (root.left != null) {
            minv = root.left.val;
            root = root.left;
        }
        return minv;
    }

    // Utility function to insert a new node with the given key
    void insert(int key) {
        root = insertRec(root, key);
    }

    // A recursive function to insert a new key in BST
    TreeNode insertRec(TreeNode root, int key) {
        if (root == null) {
            root = new TreeNode(key);
            return root;
        }

        if (key < root.val)
            root.left = insertRec(root.left, key);
        else if (key > root.val)
            root.right = insertRec(root.right, key);

        return root;
    }

    // This method mainly calls deleteNode()
    void delete(int key) {
        root = deleteNode(root, key);
    }

    // A utility function to do inorder traversal of BST
    void inorder() {
        inorderRec(root);
    }

    // A recursive function to do inorder traversal of BST
    void inorderRec(TreeNode root) {
        if (root != null) {
            inorderRec(root.left);
            System.out.print(root.val + " ");
            inorderRec(root.right);
        }
    }

    public static void main(String[] args) {
        BST tree = new BST();

        /* Let us create following BST
              50
           /     \
          30      70
         /  \    /  \
       20   40  60   80 */
        tree.insert(50);
        tree.insert(30);
        tree.insert(20);
        tree.insert(40);
        tree.insert(70);
        tree.insert(60);
        tree.insert(80);

        System.out.println("Inorder traversal of the given tree");
        tree.inorder();

        System.out.println("\n\nDelete 20");
        tree.delete(20);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder();

        System.out.println("\n\nDelete 30");
        tree.delete(30);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder();

        System.out.println("\n\nDelete 50");
        tree.delete(50);
        System.out.println("Inorder traversal of the modified tree");
        tree.inorder();
    }
}


```
