# Ex12 Binary Search Tree
## DATE: 12/03/2025
## AIM:
To write a C function to insert the elements in the binary search tree

## Algorithm
1. Define a structure for the binary search tree node, which contains data, left and right pointers.
2. Create a function to insert elements in the binary search tree following the BST property:
   - If the new data is less than the current node’s data, insert it in the left subtree.
   - If the new data is greater than the current node’s data, insert it in the right subtree.
3. Create a function to traverse and print the tree in an order of your choice (e.g., in-order traversal).
4. Test the insertion function by inserting multiple elements and displaying the tree. 

## Program:
```
/*
Program to insert the elements in the binary search tree
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

// Define the structure for the binary search tree node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

// Function to insert a node in the binary search tree
struct Node* insert(struct Node* root, int data) {
    // If the tree is empty, return a new node
    if (root == NULL) {
        return createNode(data);
    }

    // Otherwise, recur down the tree
    if (data < root->data) {
        root->left = insert(root->left, data);  // Insert in the left subtree
    } else {
        root->right = insert(root->right, data);  // Insert in the right subtree
    }

    // Return the (unchanged) node pointer
    return root;
}

// In-order traversal function to print the tree
void inOrderTraversal(struct Node* root) {
    if (root != NULL) {
        inOrderTraversal(root->left);  // Traverse the left subtree
        printf("%d ", root->data);     // Print the node's data
        inOrderTraversal(root->right); // Traverse the right subtree
    }
}

int main() {
    struct Node* root = NULL;  // Start with an empty tree

    // Insert nodes into the binary search tree
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 20);
    insert(root, 40);
    insert(root, 70);
    insert(root, 60);
    insert(root, 80);

    // Print the tree using in-order traversal
    printf("In-order traversal of the binary search tree:\n");
    inOrderTraversal(root);  // Should print the elements in sorted order
    printf("\n");

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/84e2ac45-1b6c-4cb4-9f3e-6188f96d8b77)



## Result:
Thus, the C function to insert the elements in the binary search tree is implemented successfully.
