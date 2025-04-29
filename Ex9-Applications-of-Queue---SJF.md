# Ex9 Applications of Queue - SJF
## DATE: 26/02/2025
## AIM:
To incorporate the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
## Algorithm
1. Define the processes and their burst times.
2. Sort the processes in ascending order of burst times (Shortest Job First).
3. Calculate the waiting time for each process:
   - Waiting time for the first process is zero.
   - For other processes, waiting time is the sum of the burst times of the previous processes.
4. Calculate the total waiting time by summing all the individual waiting times.
5. Calculate the average waiting time by dividing the total waiting time by the number of processes.
6. Display the waiting time for each process, total waiting time, and average waiting time.


## Program:
```
/*
Program to find the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

void findWaitingTime(int processes[], int n, int bt[], int wt[]) {
    wt[0] = 0;  // Waiting time for the first process is 0

    for (int i = 1; i < n; i++) {
        wt[i] = bt[i - 1] + wt[i - 1];  // Waiting time is the sum of burst times of previous processes
    }
}

void findTurnaroundTime(int processes[], int n, int bt[], int wt[], int tat[]) {
    for (int i = 0; i < n; i++) {
        tat[i] = bt[i] + wt[i];  // Turnaround time = Burst time + Waiting time
    }
}

void findAverageTime(int processes[], int n, int bt[]) {
    int wt[n], tat[n];
    int total_wt = 0, total_tat = 0;

    findWaitingTime(processes, n, bt, wt);
    findTurnaroundTime(processes, n, bt, wt, tat);

    for (int i = 0; i < n; i++) {
        total_wt += wt[i];
        total_tat += tat[i];
    }

    printf("Process\tBurst Time\tWaiting Time\tTurnaround Time\n");
    for (int i = 0; i < n; i++) {
        printf("%d\t%d\t\t%d\t\t%d\n", processes[i], bt[i], wt[i], tat[i]);
    }

    printf("\nTotal Waiting Time: %d", total_wt);
    printf("\nAverage Waiting Time: %.2f", (float)total_wt / n);
    printf("\nAverage Turnaround Time: %.2f", (float)total_tat / n);
}

void sortProcesses(int processes[], int n, int bt[]) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (bt[i] > bt[j]) {
                // Swap burst times
                int temp = bt[i];
                bt[i] = bt[j];
                bt[j] = temp;

                // Swap corresponding process IDs
                temp = processes[i];
                processes[i] = processes[j];
                processes[j] = temp;
            }
        }
    }
}

int main() {
    int n;
    printf("Enter the number of processes: ");
    scanf("%d", &n);

    int processes[n], burst_time[n];

    printf("Enter the burst times for each process:\n");
    for (int i = 0; i < n; i++) {
        processes[i] = i + 1;  // Process IDs starting from 1
        printf("Process %d: ", processes[i]);
        scanf("%d", &burst_time[i]);
    }

    // Sort the processes based on burst time
    sortProcesses(processes, n, burst_time);

    // Calculate and display the average waiting time and turnaround time
    findAverageTime(processes, n, burst_time);

    return 0;
}

```

## Output:

![image](https://github.com/user-attachments/assets/3997f610-e45a-4120-b628-f64c98fb8697)


## Result:
Thus, the code to calculate the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm is implemented successfully.
