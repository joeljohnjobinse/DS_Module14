# Ex7 Priority Queue
## DATE: 26/02/2025
## AIM:
To formulate the C code to display the elements of the priority queue after insertion and deletion operation.

## Algorithm
1. Start the program and define a structure for a priority queue element (data and priority).
2. Define an array to represent the priority queue and variables for tracking size.
3. Insertion:
   - Insert the new element based on its priority.
   - Higher priority elements (smaller priority value) come first.
   - Shift elements as necessary to maintain order.
4. Deletion:
   - Remove the element with the highest priority (the first element).
   - Shift the remaining elements forward.
5. After each operation, display the current elements of the priority queue.
6. End the program.


## Program:
```
/*
Program to display the elements of the priority queue after insertion and deletion operation
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

#define SIZE 10

typedef struct {
    int data;
    int priority;
} Element;

Element pq[SIZE];
int n = 0;

void insert(int data, int priority) {
    if (n == SIZE) {
        printf("Priority Queue is full!\n");
        return;
    }

    int i = n - 1;
    while (i >= 0 && pq[i].priority > priority) {
        pq[i + 1] = pq[i];
        i--;
    }
    pq[i + 1].data = data;
    pq[i + 1].priority = priority;
    n++;
}

void deleteHighestPriority() {
    if (n == 0) {
        printf("Priority Queue is empty!\n");
        return;
    }
    printf("Deleted element: %d with priority: %d\n", pq[0].data, pq[0].priority);
    for (int i = 0; i < n - 1; i++) {
        pq[i] = pq[i + 1];
    }
    n--;
}

void display() {
    if (n == 0) {
        printf("Priority Queue is empty!\n");
        return;
    }
    printf("Priority Queue Elements:\n");
    for (int i = 0; i < n; i++) {
        printf("Data: %d, Priority: %d\n", pq[i].data, pq[i].priority);
    }
}

int main() {
    // Inserting elements
    insert(10, 2);
    insert(30, 1);
    insert(20, 3);

    printf("\nAfter Insertions:\n");
    display();

    // Deleting an element
    deleteHighestPriority();

    printf("\nAfter Deletion:\n");
    display();

    return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/c0cf92fb-d8e7-4316-8d37-20b04da77c7c)



## Result:
Thus, the C program to display the elements of the priority queue after insertion and deletion operation is implemented successfully
