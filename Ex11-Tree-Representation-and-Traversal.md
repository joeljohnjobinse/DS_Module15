# Ex11 Tree Representation and Traversal
## DATE: 12/02/2025
## AIM:
To write a C function to perform post order traversal of a binary tree.

## Algorithm
1. Create a binary tree structure with a root node.
2. Define a recursive function that performs post-order traversal (Left, Right, Root).
3. Traverse the left subtree, then the right subtree, and then process the current root node.
4. Print the data stored in each node during the traversal.

## Program:
```
/*
Program to perform post order traversal of a binary tree.
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

// Structure for tree node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to perform post-order traversal
void postOrderTraversal(struct Node* root) {
    if (root == NULL) {
        return;
    }

    // Traverse the left subtree
    postOrderTraversal(root->left);

    // Traverse the right subtree
    postOrderTraversal(root->right);

    // Print the root node
    printf("%d ", root->data);
}

// Function to create a new node
struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

int main() {
    // Creating a simple binary tree
    struct Node* root = createNode(1);
    root->left = createNode(2);
    root->right = createNode(3);
    root->left->left = createNode(4);
    root->left->right = createNode(5);

    printf("Post-order traversal of the binary tree: \n");
    postOrderTraversal(root);
    printf("\n");

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/84a26165-8be8-4f26-bf66-74472a36ee48)


## Result:
Thus, the function to perform post order traversal of a binary tree is implemented successfully
