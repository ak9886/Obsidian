---
updated_at: 2025-11-03T19:53:12.061+05:30
edited_seconds: 50
---
#DSA 

Source: [[unit]]
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
struct Node* insert(struct Node* node, int key) {
    if (node == NULL) {
        struct Node* temp = malloc(sizeof(struct Node));
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
