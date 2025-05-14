# Ex22 – Breadth First Graph

## DATE: 01-04-2025

---

## AIM:
To write a `printQueue` C function of the given graph that is to be traversed in the breadth first manner.

![image](https://github.com/user-attachments/assets/f483f48c-6af0-4027-a993-01c108a50933)

---

## Algorithm

1. Start by initializing the visited array to track visited nodes.
2. Initialize a queue and enqueue the starting node.
3. Mark the starting node as visited.
4. While the queue is not empty:
   - Dequeue the front element and print it.
   - For every adjacent unvisited node, mark it as visited and enqueue it.
5. Repeat until the queue is empty.

---

## Program:

```c
/*
Program to traverse graph using BFS
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#define SIZE 100

int adj[10][10], visited[10], queue[SIZE];
int front = 0, rear = -1;

void enqueue(int value) {
    rear++;
    queue[rear] = value;
}

int dequeue() {
    int value = queue[front];
    front++;
    return value;
}

int isQueueEmpty() {
    return front > rear;
}

void BFS(int start, int n) {
    int i, current;
    enqueue(start);
    visited[start] = 1;

    printf("BFS Traversal: ");
    while (!isQueueEmpty()) {
        current = dequeue();
        printf("%d ", current);

        for (i = 0; i < n; i++) {
            if (adj[current][i] == 1 && !visited[i]) {
                enqueue(i);
                visited[i] = 1;
            }
        }
    }
}

int main() {
    int n, i, j, edges, u, v, start;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    printf("Enter number of edges: ");
    scanf("%d", &edges);

    for (i = 0; i < n; i++)
        for (j = 0; j < n; j++)
            adj[i][j] = 0;

    printf("Enter %d edges (u v):\n", edges);
    for (i = 0; i < edges; i++) {
        scanf("%d%d", &u, &v);
        adj[u][v] = 1;
        adj[v][u] = 1; // remove for directed graph
    }

    for (i = 0; i < n; i++)
        visited[i] = 0;

    printf("Enter the starting vertex: ");
    scanf("%d", &start);

    BFS(start, n);
    return 0;
}
```
## Output:
```
Enter number of vertices: 6
Enter number of edges: 7
Enter 7 edges (u v):
0 1
0 2
1 3
1 4
2 4
3 5
4 5
Enter the starting vertex: 0
BFS Traversal: 0 1 2 3 4 5
```
## Result:
Thus, the code for the printQueue function of the graph that is to be traversed in the breadth first manner is implemented successfully.
