# Ex24 – Topological Sort

## DATE: 03-04-2025

---

## AIM:
To compose the code to determine whether the topological ordering for the following graph is possible or not.

![image](https://github.com/user-attachments/assets/c74a7111-9b59-475c-aad4-9baf23d50ec0)

---

## Algorithm

1. Create a graph using an adjacency list representation.
2. Calculate the in-degree (number of incoming edges) for all vertices.
3. Use a queue to enqueue vertices with 0 in-degree.
4. Perform the topological sort using Kahn's Algorithm:
   - Dequeue vertex, print/store it.
   - Decrease in-degree of adjacent vertices.
   - If in-degree becomes 0, enqueue them.
5. If the number of visited nodes equals the total vertices, topological order is possible. Else, the graph has a cycle.

---

## Program:

```c
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int adj[MAX][MAX], indegree[MAX], queue[MAX];
int front = -1, rear = -1;

void enqueue(int value) {
    if (rear == MAX - 1)
        return;
    queue[++rear] = value;
    if (front == -1)
        front = 0;
}

int dequeue() {
    if (front == -1 || front > rear)
        return -1;
    return queue[front++];
}

int isQueueEmpty() {
    return (front == -1 || front > rear);
}

void topologicalSort(int vertices) {
    int i, j, count = 0;

    for (i = 0; i < vertices; i++) {
        if (indegree[i] == 0)
            enqueue(i);
    }

    printf("Topological Ordering: ");
    while (!isQueueEmpty()) {
        int node = dequeue();
        printf("%d ", node);
        count++;

        for (j = 0; j < vertices; j++) {
            if (adj[node][j]) {
                indegree[j]--;
                if (indegree[j] == 0)
                    enqueue(j);
            }
        }
    }

    if (count != vertices)
        printf("\nTopological ordering not possible (Graph has a cycle).\n");
    else
        printf("\nTopological ordering is possible.\n");
}

int main() {
    int vertices, edges, i, src, dest;

    printf("Enter number of vertices: ");
    scanf("%d", &vertices);
    printf("Enter number of edges: ");
    scanf("%d", &edges);

    for (i = 0; i < edges; i++) {
        printf("Enter edge %d (src dest): ", i + 1);
        scanf("%d%d", &src, &dest);
        adj[src][dest] = 1;
        indegree[dest]++;
    }

    topologicalSort(vertices);

    return 0;
}
```
## Output:
```
Enter number of vertices: 6
Enter number of edges: 6
Enter edge 1 (src dest): 5 2
Enter edge 2 (src dest): 5 0
Enter edge 3 (src dest): 4 0
Enter edge 4 (src dest): 4 1
Enter edge 5 (src dest): 2 3
Enter edge 6 (src dest): 3 1

Topological Ordering: 4 5 0 2 3 1 
Topological ordering is possible.
```
## Result:
Thus, the C program for determining whether the topological ordering for the given graph is possible or not is implemented successfully.
