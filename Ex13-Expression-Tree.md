# Ex13 Expression Tree
## DATE: 12/03/2025
## AIM:
To write a C function to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order ,Pre-order and Post-order traversal.

## Algorithm
1. Create a stack to store tree nodes.
2. For each character in the given postfix expression:
   - If the character is an operand (number or variable), create a new tree node with the operand and push it onto the stack.
   - If the character is an operator, pop two operands from the stack, create a new node for the operator, and set the two operands as its left and right children.
3. After processing the postfix expression, the stack will contain the root of the expression tree.
4. Perform and print the In-order, Pre-order, and Post-order traversals of the tree.



## Program:
```
/*
Program to construct an Expression Tree for the given Postfix Expression and display the output in the format of In-order, Pre-order, and Post-order traversal.
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>

// Define the structure of a tree node
struct Node {
    char data;
    struct Node* left;
    struct Node* right;
};

// Function to create a new node
struct Node* createNode(char data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->left = newNode->right = NULL;
    return newNode;
}

// Function to perform pre-order traversal
void preOrder(struct Node* root) {
    if (root != NULL) {
        printf("%c ", root->data);  // Visit the root node
        preOrder(root->left);       // Traverse the left subtree
        preOrder(root->right);      // Traverse the right subtree
    }
}

// Function to perform in-order traversal
void inOrder(struct Node* root) {
    if (root != NULL) {
        inOrder(root->left);        // Traverse the left subtree
        printf("%c ", root->data);  // Visit the root node
        inOrder(root->right);       // Traverse the right subtree
    }
}

// Function to perform post-order traversal
void postOrder(struct Node* root) {
    if (root != NULL) {
        postOrder(root->left);      // Traverse the left subtree
        postOrder(root->right);     // Traverse the right subtree
        printf("%c ", root->data);  // Visit the root node
    }
}

// Function to check if a character is an operator
int isOperator(char c) {
    return (c == '+' || c == '-' || c == '*' || c == '/');
}

// Function to construct the expression tree from the postfix expression
struct Node* constructTree(char* postfix) {
    struct Node* stack[100];
    int top = -1;

    for (int i = 0; postfix[i] != '\0'; i++) {
        if (isalnum(postfix[i])) {
            stack[++top] = createNode(postfix[i]);  // Operand, push to stack
        } else if (isOperator(postfix[i])) {
            struct Node* operatorNode = createNode(postfix[i]);
            operatorNode->right = stack[top--];  // Pop right operand
            operatorNode->left = stack[top--];   // Pop left operand
            stack[++top] = operatorNode;         // Push the operator node to stack
        }
    }
    return stack[top];  // The root of the expression tree
}

int main() {
    char postfix[] = "ab+cde+**";  // Example postfix expression

    // Construct the expression tree
    struct Node* root = constructTree(postfix);

    // Display the traversals
    printf("Pre-order traversal: ");
    preOrder(root);
    printf("\n");

    printf("In-order traversal: ");
    inOrder(root);
    printf("\n");

    printf("Post-order traversal: ");
    postOrder(root);
    printf("\n");

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/df30f325-7e5e-4203-82cb-d5f01e6a414a)



## Result:
Thus, the C program to display the Expression Tree in the format of In-order ,Pre-order and Post-order traversal.
