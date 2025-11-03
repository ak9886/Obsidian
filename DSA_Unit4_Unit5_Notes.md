# Data Structures and Algorithms Notes  

## Unit 4 – Trees and Hashing  

### 1. Introduction to Trees  
A **tree** is a hierarchical data structure consisting of nodes connected by edges. It represents parent–child relationships.  
- The **topmost node** is the *root*.  
- Nodes without children are *leaves*.  
- Each edge represents a *link* from parent to child.  
- Trees are **non-linear** structures, unlike arrays or linked lists.  

**Terminology:**  
- **Root:** The starting node (no parent).  
- **Child:** Node directly connected below a parent.  
- **Parent:** Node having children.  
- **Siblings:** Nodes with the same parent.  
- **Level:** Depth from the root.  
- **Height:** Longest path from root to a leaf.  

**Applications:**  
- Hierarchical file systems  
- Expression evaluation  
- Decision trees in AI  
- Compiler syntax trees  

---  

### 2. Binary Trees  
A **binary tree** is a tree in which each node has at most two children, named *left* and *right*.  

**Types:**  
- **Full Binary Tree:** Every node has 0 or 2 children.  
- **Complete Binary Tree:** All levels filled except possibly the last, filled left to right.  
- **Perfect Binary Tree:** All internal nodes have two children, all leaves at same level.  
- **Degenerate Tree:** Each parent has only one child.  

**Properties:**  
- Max nodes at level `i` = `2^i`  
- Max nodes in tree of height `h` = `2^(h+1) - 1`  
- Minimum height = `log₂(n+1) - 1`  

**Applications:**  
- Hierarchical data representation  
- Priority queues (Heaps)  
- Binary search operations  

---  

### 3. Binary Search Trees (BST)  
A **BST** is a binary tree where:  
- Left child < Root < Right child  
- Each subtree is also a BST  

**Operations:**  
- **Search:** Traverse left if key < root, else right.  
- **Insertion:** Recursively find correct position maintaining order.  
- **Deletion:**  
  - Case 1: No child → delete directly.  
  - Case 2: One child → replace with child.  
  - Case 3: Two children → replace with inorder successor.  

**Pseudocode (Search in BST):**  
```python
def searchBST(root, key):
    if root is None or root.data == key:
        return root
    if key < root.data:
        return searchBST(root.left, key)
    else:
        return searchBST(root.right, key)
```  

**Applications:**  
- Symbol tables in compilers  
- Auto-completion and searching  

---  

### 4. Tree Traversals  
Tree traversals visit nodes systematically.  

**Types:**  
1. **Inorder (L, Root, R)** → Left → Root → Right  
2. **Preorder (Root, L, R)** → Root → Left → Right  
3. **Postorder (L, R, Root)** → Left → Right → Root  
4. **Level-order:** Breadth-first traversal using queues  

**Example:**  
For tree `(A, B, C, D, E, F, G)`  

```
       A
     /   \
    B     C
   / \   / \
  D   E F   G
```  

| Traversal Type | Order     |
|----------------|------------|
| Preorder       | A B D E C F G |
| Inorder        | D B E A F C G |
| Postorder      | D E B F G C A |  

**Applications:**  
- Expression evaluation (Postorder)  
- Expression generation (Inorder)  
- Tree copy and deletion operations  

---  

### 5. AVL Trees  
An **AVL Tree** is a self-balancing BST. Named after Adelson-Velsky and Landis.  
For every node, the **balance factor** = `height(left) - height(right)` must be -1, 0, or +1.  

**Rotations:**  
- **LL Rotation** – Right rotation  
- **RR Rotation** – Left rotation  
- **LR Rotation** – Left-Right rotation  
- **RL Rotation** – Right-Left rotation  

**Pseudocode (Insertion with Rotation):**  
```python
def insertAVL(root, key):
    if not root:
        return Node(key)
    if key < root.key:
        root.left = insertAVL(root.left, key)
    else:
        root.right = insertAVL(root.right, key)

    updateHeight(root)
    balance = getBalance(root)

    # Left Heavy
    if balance > 1 and key < root.left.key:
        return rotateRight(root)
    # Right Heavy
    if balance < -1 and key > root.right.key:
        return rotateLeft(root)
    # Left-Right
    if balance > 1 and key > root.left.key:
        root.left = rotateLeft(root.left)
        return rotateRight(root)
    # Right-Left
    if balance < -1 and key < root.right.key:
        root.right = rotateRight(root.right)
        return rotateLeft(root)

    return root
```  

**Applications:**  
- Databases for fast lookup and insertion  
- Memory indexing systems  

---  

### 6. Hashing  
Hashing converts keys into indices using a **hash function**. It ensures fast insertion, deletion, and search.  

**Hash Function:** `h(k) = k mod m`  
- `k`: key value  
- `m`: table size  

**Collision Resolution:**  
- **Open Addressing:** Linear, Quadratic probing, Double hashing  
- **Chaining:** Linked lists store multiple keys at the same index  

**Example:**  
Table size = 10, keys = [12, 22, 32]  
`h(k) = k mod 10` → all hash to index 2.  

Using **chaining**, they form a linked list at slot 2.  

**Applications:**  
- Hash maps, dictionaries, symbol tables  
- Password verification (MD5, SHA)  

---  

## Unit 5 – Graph Algorithms  

### 1. Introduction to Graphs  
A **graph** is a collection of *vertices (nodes)* and *edges (connections)*.  
`G = (V, E)` where V = vertices, E = edges  

**Types:**  
- **Undirected Graph:** Edges have no direction.  
- **Directed Graph (Digraph):** Edges have direction (arrows).  
- **Weighted Graph:** Each edge has an associated cost/weight.  
- **Connected Graph:** All vertices reachable from one another.  
- **Cyclic / Acyclic:** Contains or lacks cycles.  

**Representations:**  
- **Adjacency Matrix:** 2D array; space O(V²)  
- **Adjacency List:** List of linked lists; space O(V+E)  

**Applications:**  
- Social networks, road maps, dependency resolution  

---  

### 2. Graph Traversal Algorithms  

#### Depth First Search (DFS)  
Recursively explores as far as possible before backtracking.  

**Pseudocode:**  
```python
def DFS(node, visited):
    visited.add(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            DFS(neighbor, visited)
```  

#### Breadth First Search (BFS)  
Visits all neighbors first using a queue.  

**Pseudocode:**  
```python
def BFS(start):
    visited = set()
    queue = [start]
    while queue:
        vertex = queue.pop(0)
        if vertex not in visited:
            visited.add(vertex)
            queue.extend(graph[vertex] - visited)
```  

**Applications:**  
- Network analysis  
- Finding connected components  
- Shortest path (unweighted graphs)  

---  

### 3. Topological Sorting  
Applicable to **Directed Acyclic Graphs (DAGs)** only.  
Orders vertices so that every directed edge (u → v), *u* comes before *v*.  

**Pseudocode:**  
```python
def topoSort(graph):
    visited, stack = set(), []
    def dfs(v):
        visited.add(v)
        for n in graph[v]:
            if n not in visited:
                dfs(n)
        stack.insert(0, v)
    for v in graph:
        if v not in visited:
            dfs(v)
    return stack
```  

**Applications:**  
- Task scheduling  
- Course prerequisite ordering  

---  

### 4. Shortest Path Algorithms  

#### Dijkstra’s Algorithm  
Finds the shortest path from a source to all vertices in a **weighted, non-negative** graph.  

**Steps:**  
1. Initialize distance[source] = 0, others = ∞  
2. Pick vertex with minimum distance not yet visited  
3. Update distances to adjacent vertices  
4. Repeat until all vertices processed  

**Pseudocode:**  
```python
def dijkstra(graph, source):
    dist = {v: float('inf') for v in graph}
    dist[source] = 0
    visited = set()
    while len(visited) < len(graph):
        u = min((v for v in graph if v not in visited), key=lambda v: dist[v])
        visited.add(u)
        for neighbor, weight in graph[u].items():
            if dist[u] + weight < dist[neighbor]:
                dist[neighbor] = dist[u] + weight
    return dist
```  

**Applications:**  
- GPS routing  
- Network latency optimization  

---  

#### Bellman-Ford Algorithm  
Works with **negative weights** (unlike Dijkstra). Repeats edge relaxation |V|-1 times.  

**Applications:**  
- Currency arbitrage detection  
- Routing in communication networks  

---  

### 5. Minimum Spanning Tree (MST) Algorithms  

A **spanning tree** connects all vertices with minimum possible total edge weight.  

#### Kruskal’s Algorithm  
- Sort edges by weight  
- Add smallest edge that doesn’t form a cycle  
- Use Disjoint Set (Union-Find) to detect cycles  

**Pseudocode:**  
```python
def kruskal(graph):
    edges = sorted(graph['edges'], key=lambda e: e[2])
    parent = {}
    def find(v):
        if parent[v] != v:
            parent[v] = find(parent[v])
        return parent[v]
    def union(u, v):
        parent[find(u)] = find(v)
    for v in graph['vertices']:
        parent[v] = v
    mst = []
    for u, v, w in edges:
        if find(u) != find(v):
            union(u, v)
            mst.append((u, v, w))
    return mst
```  

#### Prim’s Algorithm  
Starts from any node, grows MST by repeatedly adding the least-weight edge connecting to a new vertex.  

**Applications of MSTs:**  
- Network cable layout optimization  
- Electrical grid design  
- Cluster analysis in machine learning  

---  

### 6. Complexity Overview  

| Algorithm | Time Complexity | Space Complexity |
|------------|----------------|------------------|
| BFS / DFS | O(V + E) | O(V) |
| Dijkstra | O(V²) or O((V+E)logV) with heap | O(V) |
| Bellman-Ford | O(VE) | O(V) |
| Kruskal | O(E log E) | O(V) |
| Prim | O(V²) or O(E log V) | O(V) |

---  

### 7. Real-World Graph Applications  
- Google Maps (shortest path)  
- Facebook (friend suggestion graph)  
- Compiler optimization (dependency resolution)  
- Computer networks (packet routing)  

---  

**End of Notes**  
