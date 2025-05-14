# Ex25 – Adjacency List Representation

## DATE: 04-04-2025

---

## AIM:
To write a C program to represent the given graph using the adjacency list.

---

## Algorithm

1. Define a structure for a node in the adjacency list.
2. Create an array of pointers for each vertex.
3. For each edge (u, v), create a node for `v` and add it to the adjacency list of `u`.
4. Repeat for all edges.
5. Display the adjacency list for all vertices.

---

## Program:
```c
/*
Program to represent the given graph using the adjacency list.
Developed by: Vishwaraj G.
RegisterNumber: 212223220125
*/

#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int vertex;
    struct Node* next;
} Node;

Node* createNode(int v) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->vertex = v;
    newNode->next = NULL;
    return newNode;
}

void addEdge(Node* adjList[], int src, int dest) {
    Node* newNode = createNode(dest);
    newNode->next = adjList[src];
    adjList[src] = newNode;

    // If the graph is undirected, add an edge from dest to src also
    // Uncomment the following lines if undirected:
    // newNode = createNode(src);
    // newNode->next = adjList[dest];
    // adjList[dest] = newNode;
}

void printGraph(Node* adjList[], int vertices) {
    for (int i = 0; i < vertices; i++) {
        Node* temp = adjList[i];
        printf("Vertex %d: ", i);
        while (temp) {
            printf("-> %d ", temp->vertex);
            temp = temp->next;
        }
        printf("\n");
    }
}

int main() {
    int vertices, edges, src, dest;

    printf("Enter number of vertices: ");
    scanf("%d", &vertices);

    Node* adjList[vertices];
    for (int i = 0; i < vertices; i++)
        adjList[i] = NULL;

    printf("Enter number of edges: ");
    scanf("%d", &edges);

    for (int i = 0; i < edges; i++) {
        printf("Enter edge %d (src dest): ", i + 1);
        scanf("%d%d", &src, &dest);
        addEdge(adjList, src, dest);
    }

    printf("\nAdjacency List of the Graph:\n");
    printGraph(adjList, vertices);

    return 0;
}
```
## Output:
```
Enter number of vertices: 4
Enter number of edges: 4
Enter edge 1 (src dest): 0 1
Enter edge 2 (src dest): 0 2
Enter edge 3 (src dest): 1 2
Enter edge 4 (src dest): 2 3

Adjacency List of the Graph:
Vertex 0: -> 2 -> 1 
Vertex 1: -> 2 
Vertex 2: -> 3 
Vertex 3: 
```
## Result:
Thus, the C program to represent the given graph using the adjacency list is implemented successfully.
