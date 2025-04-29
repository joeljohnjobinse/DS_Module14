# Ex8 Deque
## DATE: 26/02/2025
## AIM:
To write a C function to count the number of elements present in the deque.

## Algorithm
1. Define a structure for the deque that contains the array and front, rear indices.
2. Create a function countElements() that calculates the number of elements in the deque by checking the difference between the front and rear pointers.
3. Ensure proper handling of the circular nature of the deque while counting.
4. The function should return the count of elements in the deque.
5. Implement insertion and deletion operations (insertFront, insertRear, deleteFront, deleteRear) to manage the deque.
6. End the program.


## Program:
```
/*
Program to count the number of elements present in the deque
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#define SIZE 5

int deque[SIZE];
int front = -1, rear = -1;

int countElements() {
    if (front == -1) {
        return 0; // Deque is empty
    }
    if (rear >= front) {
        return rear - front + 1; // Normal case
    } else {
        return SIZE - front + rear + 1; // Circular case
    }
}

void insertFront(int value) {
    if ((front == 0 && rear == SIZE - 1) || (front == rear + 1)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) {
        front = rear = 0;
    } else if (front == 0) {
        front = SIZE - 1;
    } else {
        front--;
    }
    deque[front] = value;
}

void insertRear(int value) {
    if ((front == 0 && rear == SIZE - 1) || (front == rear + 1)) {
        printf("Deque is full!\n");
        return;
    }
    if (front == -1) {
        front = rear = 0;
    } else if (rear == SIZE - 1) {
        rear = 0;
    } else {
        rear++;
    }
    deque[rear] = value;
}

void deleteFront() {
    if (front == -1) {
        printf("Deque is empty!\n");
        return;
    }
    printf("Deleted element: %d\n", deque[front]);
    if (front == rear) {
        front = rear = -1; // Deque is empty after deletion
    } else if (front == SIZE - 1) {
        front = 0;
    } else {
        front++;
    }
}

void deleteRear() {
    if (front == -1) {
        printf("Deque is empty!\n");
        return;
    }
    printf("Deleted element: %d\n", deque[rear]);
    if (front == rear) {
        front = rear = -1; // Deque is empty after deletion
    } else if (rear == 0) {
        rear = SIZE - 1;
    } else {
        rear--;
    }
}

void display() {
    if (front == -1) {
        printf("Deque is empty!\n");
        return;
    }
    printf("Deque elements: ");
    if (rear >= front) {
        for (int i = front; i <= rear; i++) {
            printf("%d ", deque[i]);
        }
    } else {
        for (int i = front; i < SIZE; i++) {
            printf("%d ", deque[i]);
        }
        for (int i = 0; i <= rear; i++) {
            printf("%d ", deque[i]);
        }
    }
    printf("\n");
}

int main() {
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertRear(30);
    insertFront(2);
    
    display();
    
    printf("Number of elements in deque: %d\n", countElements());
    
    deleteFront();
    deleteRear();
    
    display();
    
    printf("Number of elements in deque: %d\n", countElements());
    
    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/12b5ff35-02ff-4e18-bdd4-182ecfe38532)



## Result:
Thus, the C code to count the number of elements present in the deque is implemented successfully.
