# Ex21 – Representation of Graph

## DATE:
31-03-2025

---

## AIM:
To write a C program to display the adjacency matrix of the given graph by supplying the edges and the number of vertices.

---

## Algorithm:

1. Start the program and input the number of vertices and edges.
2. Initialize an adjacency matrix with all elements set to 0.
3. For each edge, input the pair of vertices (source and destination).
4. Set the corresponding matrix entries to 1 (for undirected graph, mark both [i][j] and [j][i]).
5. Print the final adjacency matrix.

---

## Program:

```c
/*
Program to display the adjacency matrix of the given graph
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>

int main() {
    int vertices, edges;
    int i, j, u, v;

    printf("Enter the number of vertices: ");
    scanf("%d", &vertices);

    printf("Enter the number of edges: ");
    scanf("%d", &edges);

    int adj[vertices][vertices];

    // Initialize all elements to 0
    for (i = 0; i < vertices; i++) {
        for (j = 0; j < vertices; j++) {
            adj[i][j] = 0;
        }
    }

    printf("Enter %d pairs of edges (u v):\n", edges);
    for (i = 0; i < edges; i++) {
        scanf("%d%d", &u, &v);
        adj[u][v] = 1;
        adj[v][u] = 1; // Remove this line if it's a directed graph
    }

    printf("Adjacency Matrix:\n");
    for (i = 0; i < vertices; i++) {
        for (j = 0; j < vertices; j++) {
            printf("%d ", adj[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```
## Output:
```
Enter the number of vertices: 4
Enter the number of edges: 4
Enter 4 pairs of edges (u v):
0 1
0 2
1 2
2 3
Adjacency Matrix:
0 1 1 0
1 0 1 0
1 1 0 1
0 0 1 0
```
## Result:
Thus, the C program to print the adjacency matrix of the given graph is implemented successfully.
