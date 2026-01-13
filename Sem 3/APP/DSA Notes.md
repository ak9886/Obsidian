---
updated_at: 2025-11-03T20:34:06.257+05:30
edited_seconds: 120
---
#DSA 

# **UNIT 4 – TREES AND HASHING**

---

## **1. Introduction to Trees and Traversals**

### **1.1 Concept and Structure**

A **tree** is a non-linear hierarchical data structure that consists of nodes connected by edges. It represents relationships such as parent–child hierarchy.  
Each node stores **data** and pointers to its **child nodes**.

- **Root Node:** The topmost node of the tree.
    
- **Parent Node:** A node that has child nodes.
    
- **Child Node:** A node derived from a parent.
    
- **Leaf Node:** A node with no children.
    
- **Siblings:** Nodes having the same parent.
    
- **Edge:** Connection between two nodes.
    
- **Level:** Depth of a node from the root (root is level 0).
    
- **Height:** Maximum level in the tree.
    

#### **Tree Example (Text Representation)**

```
        A
       / \
      B   C
     / \   \
    D   E   F
```

- Root: A
    
- Height: 2
    
- Leaf nodes: D, E, F
    

---

### **1.2 Tree Terminology**

|Term|Description|
|---|---|
|Degree of node|Number of children a node has|
|Degree of tree|Maximum degree among all nodes|
|Height of node|Length of the longest path to a leaf|
|Depth of node|Length of the path from the root to that node|

---

### **1.3 Types of Trees**

- **General Tree:** Any number of children.
    
- **Binary Tree:** At most two children per node.
    
- **Complete Binary Tree (CBT):** All levels filled except possibly the last.
    
- **Full Binary Tree:** Every node has 0 or 2 children.
    
- **Binary Search Tree (BST):** Left child < parent < right child.
    

---

### **1.4 Tree Traversals**

Traversal means visiting every node exactly once.

#### **(a) Preorder Traversal (Root → Left → Right)**

```c
void preorder(struct Node* root) {
    if(root != NULL) {
        printf("%d ", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}
```

#### **(b) Inorder Traversal (Left → Root → Right)**

```c
void inorder(struct Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}
```

#### **(c) Postorder Traversal (Left → Right → Root)**

```c
void postorder(struct Node* root) {
    if(root != NULL) {
        postorder(root->left);
        postorder(root->right);
        printf("%d ", root->data);
    }
}
```

#### **(d) Level Order Traversal**

Uses a **queue** for breadth-first traversal.

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct Node {
    int data;
    Node *left, *right;
};

void levelOrder(Node* root) {
    if(root == NULL) return;
    queue<Node*> q;
    q.push(root);
    while(!q.empty()) {
        Node* temp = q.front();
        q.pop();
        cout << temp->data << " ";
        if(temp->left) q.push(temp->left);
        if(temp->right) q.push(temp->right);
    }
}
```

---

### **1.5 Traversal Applications**

|Traversal|Use Case|
|---|---|
|Preorder|Expression prefix form, copying tree|
|Inorder|Sorted order in BST|
|Postorder|Deletion, postfix evaluation|
|Level order|Shortest path, serialization|

---

## **2. Binary Tree, CBT, and BST**

### **2.1 Binary Tree**

A binary tree is a structure where every node has **at most two children**, labeled _left_ and _right_.

```c
struct Node {
    int data;
    struct Node *left, *right;
};
```

---

### **2.2 Properties**

1. Maximum nodes at level _i_:
    
    ```text
    2^i
    ```
    
2. Maximum nodes in height _h_:
    
    ```text
    2^(h+1) - 1
    ```
    
3. Minimum height for _n_ nodes:
    
    ```text
    ⌈log2(n+1)⌉ - 1
    ```
    

---

### **2.3 Complete Binary Tree (CBT)**

- All levels filled except possibly the last.
    
- Nodes are filled from **left to right**.
    
- Typically implemented using **arrays**.
    

#### **Array Representation**

For node index `i`:

```text
Left child = 2*i + 1
Right child = 2*i + 2
Parent = (i - 1)/2
```

---

### **2.4 Binary Search Tree (BST)**

A BST maintains elements in a **sorted hierarchical order**:

```
For every node N:
   Left subtree < N < Right subtree
```

#### **Insertion in BST**

```c
#include <stdio.h>
#include <stdlib.h>   
#include <stddef.h>   

struct Node {
    int data;
    struct Node* left;
    struct Node* right;
};

struct Node* insert(struct Node* node, int key) {
    if (node == NULL) {
        struct Node* temp = (struct Node*)malloc(sizeof(struct Node));
        temp->data = key;
        temp->left = temp->right = NULL;
        return temp;
    }

    if (key < node->data)
        node->left = insert(node->left, key);
    else if (key > node->data)
        node->right = insert(node->right, key);

    return node;
}

// Example test
int main() {
    struct Node* root = NULL;
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    printf("BST created successfully.\n");
    return 0;
}
```

#### **Search Operation**

```c
struct Node* search(struct Node* root, int key) {
    if (root == NULL || root->data == key)
        return root;
    if (key < root->data)
        return search(root->left, key);
    return search(root->right, key);
}
```

#### **Deletion in BST**

```cpp
Node* deleteNode(Node* root, int key) {
    if (!root) return root;
    if (key < root->data)
        root->left = deleteNode(root->left, key);
    else if (key > root->data)
        root->right = deleteNode(root->right, key);
    else {
        if (!root->left) return root->right;
        else if (!root->right) return root->left;
        Node* temp = minValueNode(root->right);
        root->data = temp->data;
        root->right = deleteNode(root->right, temp->data);
    }
    return root;
}
```

---

### **2.5 Advantages of BST**

- Efficient searching and sorting.
    
- Inorder traversal yields sorted sequence.
    
- Insertion, deletion, search all **O(log n)** average case.
    

---

## **3. AVL Trees**

### **3.1 Motivation**

BSTs can become **unbalanced**, leading to O(n) operations.  
An **AVL tree** (Adelson-Velsky and Landis tree) is a self-balancing BST that maintains balance after every insertion or deletion.

---

### **3.2 Balance Factor (BF)**

```text
BF(node) = height(left subtree) - height(right subtree)
```

|BF Value|Meaning|
|---|---|
|0|Perfectly balanced|
|+1|Left-heavy|
|-1|Right-heavy|

If |BF| > 1 → tree needs **rotation**.

---

### **3.3 Rotations**

#### **(a) LL Rotation (Right Rotation)**

Occurs when a node is inserted in the left subtree of the left child.

```c
Node* rightRotate(Node* y) {
    Node* x = y->left;
    Node* T2 = x->right;
    x->right = y;
    y->left = T2;
    return x;
}
```

#### **(b) RR Rotation (Left Rotation)**

```c
Node* leftRotate(Node* x) {
    Node* y = x->right;
    Node* T2 = y->left;
    y->left = x;
    x->right = T2;
    return y;
}
```

#### **(c) LR Rotation**

= Left rotation on left child → Right rotation on node.

#### **(d) RL Rotation**

= Right rotation on right child → Left rotation on node.

---

### **3.4 Insertion in AVL Tree**

```cpp
int height(Node* n) {
    if (!n) return 0;
    return 1 + max(height(n->left), height(n->right));
}

Node* insert(Node* node, int key) {
    if (!node) return newNode(key);

    if (key < node->data)
        node->left = insert(node->left, key);
    else if (key > node->data)
        node->right = insert(node->right, key);

    int balance = height(node->left) - height(node->right);

    if (balance > 1 && key < node->left->data)
        return rightRotate(node);
    if (balance < -1 && key > node->right->data)
        return leftRotate(node);
    if (balance > 1 && key > node->left->data) {
        node->left = leftRotate(node->left);
        return rightRotate(node);
    }
    if (balance < -1 && key < node->right->data) {
        node->right = rightRotate(node->right);
        return leftRotate(node);
    }
    return node;
}
```

---

## **4. Hashing**

### **4.1 Concept**

Hashing maps keys to indices in a fixed-size array called a **hash table**.  
It allows **constant-time access (O(1))** for search, insert, and delete operations in average case.

---

### **4.2 Hash Function**

A function that converts a key into a valid index.

```text
index = hash(key) % table_size
```

Common hash functions:

- Division method: `key % size`
    
- Multiplication method: `(key * A % 1) * size`
    
- Mid-square method
    

---

### **4.3 Collision Handling**

Two keys producing the same index = **collision**.

#### **(a) Separate Chaining**

Each index stores a linked list of entries.

```c
struct Node {
    int key;
    struct Node* next;
};

void insert(struct Node* hashTable[], int key, int size) {
    int index = key % size;
    struct Node* newNode = malloc(sizeof(struct Node));
    newNode->key = key;
    newNode->next = hashTable[index];
    hashTable[index] = newNode;
}
```

#### **(b) Open Addressing**

Stores all elements in the table itself.

**Linear Probing:**

```text
index = (hash(key) + i) % size
```

**Quadratic Probing:**

```text
index = (hash(key) + i*i) % size
```

**Double Hashing:**

```text
index = (hash1(key) + i * hash2(key)) % size
```

---

### **4.4 Load Factor**

Indicates how full the hash table is.

```text
α = n / m
```

where  
`n` = number of keys,  
`m` = table size.

---

### **4.5 Performance**

|Method|Average Case|Worst Case|
|---|---|---|
|Separate Chaining|O(1 + α)|O(n)|
|Linear Probing|O(1/(1 - α))|O(n)|

---

### **4.6 Example Implementation (Open Addressing)**

```cpp
#include <iostream>
using namespace std;

#define SIZE 10
int hashTable[SIZE];

int hashFunc(int key) { return key % SIZE; }

void insert(int key) {
    int index = hashFunc(key);
    while(hashTable[index] != 0)
        index = (index + 1) % SIZE;
    hashTable[index] = key;
}

void display() {
    for(int i = 0; i < SIZE; i++)
        cout << i << " -> " << hashTable[i] << endl;
}

int main() {
    insert(12);
    insert(22);
    insert(42);
    display();
    return 0;
}
```

---

### **4.7 Applications of Hashing**

- Symbol tables in compilers
    
- Password storage
    
- Data indexing in databases
    
- Caching and memory management
    

---

# **UNIT 5 – GRAPH ALGORITHMS**

---

## **1. Graph Introduction**

### **1.1 Definition**

A **graph** is a non-linear data structure consisting of a set of **vertices (nodes)** and **edges** connecting them.

```text
Graph G = (V, E)
where V = {set of vertices}, E = {set of edges connecting pairs of vertices}
```

Graphs represent relationships such as roads between cities, links in a network, or dependencies between tasks.

---

### **1.2 Terminology**

|Term|Description|
|---|---|
|Vertex|A node in the graph|
|Edge|Connection between two vertices|
|Degree|Number of edges incident to a vertex|
|Path|Sequence of vertices connected by edges|
|Cycle|Path that starts and ends at the same vertex|
|Connected Graph|Every vertex reachable from every other|
|Directed Graph|Edges have direction (A → B)|
|Undirected Graph|Edges have no direction|
|Weighted Graph|Each edge has a cost/weight|
|Adjacency|Two vertices connected by an edge|

---

### **1.3 Graph Representation**

#### **(a) Adjacency Matrix**

A 2D array `adj[n][n]` where:

```text
adj[i][j] = 1  if there is an edge from i to j
adj[i][j] = 0  otherwise
```

```c
#define V 4
int graph[V][V] = {
  {0, 1, 1, 0},
  {1, 0, 1, 1},
  {1, 1, 0, 0},
  {0, 1, 0, 0}
};
```

---

#### **(b) Adjacency List**

Each vertex has a list of adjacent vertices.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int V = 4;
    vector<int> adj[V];
    adj[0].push_back(1);
    adj[0].push_back(2);
    adj[1].push_back(0);
    adj[1].push_back(2);
    for (int i = 0; i < V; i++) {
        cout << i << ": ";
        for (int v : adj[i])
            cout << v << " ";
        cout << endl;
    }
}
```

---

### **1.4 Graph Traversals**

#### **(a) Depth First Search (DFS)**

Explores as far as possible along each branch before backtracking.

```cpp
void DFS(int v, vector<int> adj[], vector<bool>& visited) {
    visited[v] = true;
    cout << v << " ";
    for (int u : adj[v])
        if (!visited[u])
            DFS(u, adj, visited);
}
```

#### **(b) Breadth First Search (BFS)**

Explores all neighbors of a vertex before going deeper.

```cpp
#include <queue>

void BFS(int start, vector<int> adj[], int V) {
    vector<bool> visited(V, false);
    queue<int> q;
    visited[start] = true;
    q.push(start);
    while(!q.empty()) {
        int v = q.front();
        q.pop();
        cout << v << " ";
        for (int u : adj[v]) {
            if(!visited[u]) {
                visited[u] = true;
                q.push(u);
            }
        }
    }
}
```

---

### **1.5 Applications of Graphs**

- Networking and routing
    
- Social networks
    
- Compiler dependency resolution
    
- Map navigation
    
- Scheduling problems
    

---

## **2. Topological Sorting**

### **2.1 Definition**

**Topological Sort** of a **Directed Acyclic Graph (DAG)** is a linear ordering of vertices such that for every directed edge (u → v), vertex `u` appears before `v`.

---

### **2.2 Conditions**

- Works only on **DAGs** (no cycles).
    
- Multiple valid orders may exist.
    

---

### **2.3 Algorithm (Kahn’s Algorithm)**

```text
1. Compute in-degree of all vertices.
2. Push all vertices with in-degree 0 into a queue.
3. While queue not empty:
    a. Pop vertex v.
    b. Add v to result.
    c. For each neighbor u of v:
         - Decrement in-degree of u.
         - If in-degree(u) == 0, enqueue(u).
```

---

### **2.4 Implementation**

```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

void topoSort(int V, vector<int> adj[]) {
    vector<int> indeg(V, 0);
    for(int i=0; i<V; i++)
        for(int j : adj[i])
            indeg[j]++;
    
    queue<int> q;
    for(int i=0; i<V; i++)
        if(indeg[i] == 0) q.push(i);

    while(!q.empty()) {
        int v = q.front(); q.pop();
        cout << v << " ";
        for(int u : adj[v]) {
            indeg[u]--;
            if(indeg[u] == 0)
                q.push(u);
        }
    }
}
```

---

### **2.5 Applications**

- Scheduling tasks
    
- Build systems (resolving dependencies)
    
- Course prerequisite ordering
    

---

## **3. Prim’s Algorithm (Minimum Spanning Tree)**

### **3.1 Concept**

A **Minimum Spanning Tree (MST)** of a connected weighted graph is a subset of edges that connects all vertices with **minimum total weight** and **no cycles**.

Prim’s Algorithm grows the MST from a starting vertex by repeatedly adding the smallest weight edge connecting to an unvisited vertex.

---

### **3.2 Steps**

```text
1. Select any vertex as the starting node.
2. Mark it as part of MST.
3. Repeatedly choose the minimum weight edge that connects a new vertex.
4. Continue until all vertices are included.
```

---

### **3.3 Implementation**

```cpp
#include <iostream>
#include <vector>
#include <climits>
using namespace std;

int minKey(int key[], bool mstSet[], int V) {
    int min = INT_MAX, min_index;
    for(int v = 0; v < V; v++)
        if(!mstSet[v] && key[v] < min)
            min = key[v], min_index = v;
    return min_index;
}

void primMST(int graph[5][5], int V) {
    int parent[V];
    int key[V];
    bool mstSet[V];
    for(int i=0; i<V; i++)
        key[i] = INT_MAX, mstSet[i] = false;

    key[0] = 0;
    parent[0] = -1;

    for(int count=0; count < V-1; count++) {
        int u = minKey(key, mstSet, V);
        mstSet[u] = true;
        for(int v=0; v<V; v++)
            if(graph[u][v] && !mstSet[v] && graph[u][v] < key[v]) {
                parent[v] = u;
                key[v] = graph[u][v];
            }
    }

    cout << "Edge \tWeight\n";
    for(int i=1; i<V; i++)
        cout << parent[i] << " - " << i << "\t" << graph[i][parent[i]] << endl;
}
```

---

### **3.4 Time Complexity**

```text
O(V^2)
```

With Min-Heap:

```text
O(E log V)
```

---

## **4. Kruskal’s Algorithm**

### **4.1 Idea**

Kruskal’s algorithm constructs the MST by sorting all edges in increasing order of weight and adding them one by one, avoiding cycles.

---

### **4.2 Steps**

```text
1. Sort all edges by weight.
2. Pick the smallest edge that doesn’t form a cycle.
3. Use Disjoint Set Union (DSU) to detect cycles.
4. Repeat until (V - 1) edges are selected.
```

---

### **4.3 Implementation**

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

struct Edge {
    int u, v, w;
    bool operator<(Edge const& other) {
        return w < other.w;
    }
};

int find(int v, vector<int>& parent) {
    if (v == parent[v]) return v;
    return parent[v] = find(parent[v], parent);
}

void unite(int a, int b, vector<int>& parent, vector<int>& rank) {
    a = find(a, parent);
    b = find(b, parent);
    if (a != b) {
        if (rank[a] < rank[b]) swap(a, b);
        parent[b] = a;
        if (rank[a] == rank[b]) rank[a]++;
    }
}

int main() {
    int V = 4;
    vector<Edge> edges = {
        {0, 1, 10}, {0, 2, 6}, {0, 3, 5}, {1, 3, 15}, {2, 3, 4}
    };

    sort(edges.begin(), edges.end());
    vector<int> parent(V), rank(V, 0);
    for (int i = 0; i < V; i++) parent[i] = i;

    int cost = 0;
    for (Edge e : edges) {
        if (find(e.u, parent) != find(e.v, parent)) {
            cost += e.w;
            cout << e.u << " - " << e.v << " = " << e.w << endl;
            unite(e.u, e.v, parent, rank);
        }
    }
    cout << "Total cost = " << cost << endl;
}
```

---

### **4.4 Complexity**

```text
O(E log E)
```

---

### **4.5 Comparison with Prim’s**

|Feature|Prim’s|Kruskal’s|
|---|---|---|
|Data structure|Adjacency matrix / heap|Edge list + DSU|
|Works well on|Dense graphs|Sparse graphs|
|Complexity|O(E log V)|O(E log E)|

---

## **5. Dijkstra’s Algorithm**

### **5.1 Definition**

Dijkstra’s algorithm finds the **shortest path** from a **source vertex** to all other vertices in a **weighted graph** with non-negative weights.

---

### **5.2 Principle**

At each step, the algorithm picks the vertex with the **minimum distance value** and relaxes all its adjacent edges.

---

### **5.3 Steps**

```text
1. Initialize distances from source to all vertices as ∞.
2. Set distance[source] = 0.
3. Repeat until all vertices processed:
   a. Pick vertex u with minimum distance.
   b. For each neighbor v of u:
        if dist[u] + weight(u, v) < dist[v]:
            dist[v] = dist[u] + weight(u, v)
```

---

### **5.4 Implementation**

```cpp
#include <iostream>
#include <vector>
#include <climits>
using namespace std;

#define V 5

int minDistance(int dist[], bool sptSet[]) {
    int min = INT_MAX, min_index;
    for (int v = 0; v < V; v++)
        if (!sptSet[v] && dist[v] <= min)
            min = dist[v], min_index = v;
    return min_index;
}

void dijkstra(int graph[V][V], int src) {
    int dist[V];
    bool sptSet[V];

    for (int i = 0; i < V; i++)
        dist[i] = INT_MAX, sptSet[i] = false;

    dist[src] = 0;

    for (int count = 0; count < V - 1; count++) {
        int u = minDistance(dist, sptSet);
        sptSet[u] = true;
        for (int v = 0; v < V; v++)
            if (!sptSet[v] && graph[u][v] && dist[u] != INT_MAX &&
                dist[u] + graph[u][v] < dist[v])
                dist[v] = dist[u] + graph[u][v];
    }

    cout << "Vertex \tDistance from Source\n";
    for (int i = 0; i < V; i++)
        cout << i << " \t\t" << dist[i] << endl;
}

int main() {
    int graph[V][V] = {
        {0, 10, 0, 5, 0},
        {0, 0, 1, 2, 0},
        {0, 0, 0, 0, 4},
        {0, 3, 9, 0, 2},
        {7, 0, 6, 0, 0}
    };
    dijkstra(graph, 0);
}
```

---

### **5.5 Complexity**

- Using array: O(V²)
    
- Using priority queue: O(E log V)
    

---

### **5.6 Applications**

- GPS navigation
    
- Network routing (e.g., OSPF)
    
- Map software (Google Maps)
    
- Robot motion planning
    

---

