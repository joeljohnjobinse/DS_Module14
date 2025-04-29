# Ex6 Dequeue Elements from Circular Queue
## DATE: 26/02/2025
## AIM:
To write a C program to delete three elements from the filled circular queue.

## Algorithm
1. Start the program and define a circular queue with size MAX, and initialize front and rear to -1.
2. Create enqueue() function to insert elements into the circular queue:
   - If queue is full, display overflow message.
   - Else, update rear and insert the element.
3. Create dequeue() function to remove an element from the circular queue:
   - If the queue is empty, display underflow message.
   - Else, delete the element and update front.
4. Fill the circular queue with initial elements using enqueue().
5. Call dequeue() three times to delete three elements.
6. Display the final queue contents.
7. End the program.


## Program:
```
/*
Program to delete three elements from the filled circular queue
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#define SIZE 5

int queue[SIZE];
int front = -1, rear = -1;

void enqueue(int value) {
    if ((rear + 1) % SIZE == front) {
        printf("Queue is full (Overflow)\n");
        return;
    }
    if (front == -1)
        front = rear = 0;
    else
        rear = (rear + 1) % SIZE;
    queue[rear] = value;
}

void dequeue() {
    if (front == -1) {
        printf("Queue is empty (Underflow)\n");
        return;
    }
    printf("Deleted element: %d\n", queue[front]);
    if (front == rear)
        front = rear = -1;
    else
        front = (front + 1) % SIZE;
}

void display() {
    if (front == -1) {
        printf("Queue is empty\n");
        return;
    }

    int i = front;
    printf("Current Queue: ");
    while (1) {
        printf("%d ", queue[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }
    printf("\n");
}

int main() {
    // Filling the queue
    enqueue(10);
    enqueue(20);
    enqueue(30);
    enqueue(40);
    enqueue(50); // This one won't be inserted as size is 5 and circular logic allows SIZE - 1

    display();

    // Delete 3 elements
    dequeue();
    dequeue();
    dequeue();

    display();

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/b58d758d-4a08-4d77-984f-d9e9171aa22b)


## Result:
Thus, the C program to delete three elements from the filled circular queue is implemented successfully.
