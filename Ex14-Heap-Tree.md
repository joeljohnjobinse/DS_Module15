# Ex14 Heap Tree
## DATE: 12/03/2025
## AIM:
To write a C function to delete an element in a Heap Tree.

## Algorithm
1. Store the element to be deleted (typically the root element in a max heap or min heap).
2. Replace the root with the last element in the heap.
3. Reduce the heap size by 1.
4. Perform heapify (down-heap bubbling) from the root to maintain the heap property.
5. Repeat until the heap property is restored.


## Program:
```
/*
Program to delete an element in a Heap Tree
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

// Function to heapify the node at index i
void heapify(int heap[], int n, int i) {
    int largest = i;           // Initialize largest as root
    int left = 2 * i + 1;      // left child
    int right = 2 * i + 2;     // right child

    // If left child is larger than root
    if (left < n && heap[left] > heap[largest])
        largest = left;

    // If right child is larger than largest so far
    if (right < n && heap[right] > heap[largest])
        largest = right;

    // If largest is not root
    if (largest != i) {
        int temp = heap[i];
        heap[i] = heap[largest];
        heap[largest] = temp;

        // Recursively heapify the affected sub-tree
        heapify(heap, n, largest);
    }
}

// Function to delete the root from the max heap
int deleteRoot(int heap[], int n) {
    if (n <= 0) {
        printf("Heap is empty.\n");
        return n;
    }

    printf("Deleted element: %d\n", heap[0]);

    // Replace root with last element
    heap[0] = heap[n - 1];
    n--; // Reduce heap size

    // Heapify root element to maintain heap property
    heapify(heap, n, 0);

    return n;
}

// Function to print heap elements
void printHeap(int heap[], int n) {
    for (int i = 0; i < n; ++i)
        printf("%d ", heap[i]);
    printf("\n");
}

int main() {
    // Sample max heap
    int heap[] = {50, 30, 40, 10, 5, 20, 30};
    int n = sizeof(heap) / sizeof(heap[0]);

    printf("Original Heap: ");
    printHeap(heap, n);

    // Delete the root element
    n = deleteRoot(heap, n);

    printf("Heap after deletion: ");
    printHeap(heap, n);

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/5221d1c1-ece0-4453-a8f0-da6f3379dbab)


## Result:
Thus, the function to delete an element in a Heap Tree is implemented successfully.
