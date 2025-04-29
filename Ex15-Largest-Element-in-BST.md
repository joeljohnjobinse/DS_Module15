# Ex15 Largest Element in BST
## DATE: 12/03/2025
## AIM:
To Write a c program to find the largest value in a Binary Search Tree.

## Algorithm
1. Start from the root of the Binary Search Tree.
2. Traverse the tree by repeatedly moving to the right child (since the largest element in a BST is always in the rightmost node).
3. Continue until the rightmost node is reached (i.e., a node with no right child).
4. Return or print the value of that node as the largest element.

## Program:
```
/*
Program to find the largest value in a Binary Search Tree
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

// Define a structure for tree node
struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* newNode(int value) {
    struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
    temp->data = value;
    temp->left = temp->right = NULL;
    return temp;
}

// Function to insert a node in BST
struct Node* insert(struct Node* root, int value) {
    if (root == NULL)
        return newNode(value);

    if (value < root->data)
        root->left = insert(root->left, value);
    else
        root->right = insert(root->right, value);

    return root;
}

// Function to find the largest element
int findLargest(struct Node* root) {
    if (root == NULL) {
        printf("Tree is empty.\n");
        return -1;
    }

    struct Node* current = root;
    while (current->right != NULL)
        current = current->right;

    return current->data;
}

int main() {
    struct Node* root = NULL;

    // Sample BST insertion
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    printf("Largest value in the BST: %d\n", findLargest(root));

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/0d22c29e-afb5-4cea-aac4-805697e3210c)


## Result:
Thus, the C program to find the largest value in a Binary Search Tree is implemented successfully.
