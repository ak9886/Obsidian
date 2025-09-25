---
updated_at: 2025-09-25T19:39:38.810+05:30
edited_seconds: 30
---
Absolutely! Here’s your **SRM DSA Exam Notes** fully formatted in **Obsidian Markdown** for easy use:

# SRM DSA Exam Notes

## Portions Covered
- **Unit 1:** Lists, Arrays, Linked Lists
- **Unit 2:** Stacks, Queues, Recursion
- **Unit 3:** Trees, Graphs, Hashing

---

# Unit 1: Lists, Arrays, and Linked Lists

## 1.1 Lists
**Definition:** Collection of elements organized sequentially.  

**Types:**  
- Ordered vs. Unordered  
- Static (Array) vs. Dynamic (Linked List)  

**Advantages:**  
- Efficient insertion/deletion  
- Flexible for complex structures  
- Scalable for large datasets  

**Challenges:**  
- Memory vs. performance trade-off  
- Edge cases: empty list, index out-of-bounds, circular references  

**Applications:**  
- Database indexing  
- File system management  
- Navigation/history/bookmarks  

**Python Example: Array List**
```python
class ArrayList:
    def __init__(self):
        self.data = []
    def add(self, item):
        self.data.append(item)
    def get(self, index):
        return self.data[index]

list1 = ArrayList()
list1.add(1)
list1.add(2)
print(list1.get(0))  # 1
````

---

## 1.2 Arrays

- Fixed-size sequences in contiguous memory.
    
- Fast access, but insertion/deletion costly.
    

**C Example: Array Operations**

```c
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    for (int i=0; i<5; i++) printf("%d ", arr[i]);
    printf("\n");
    return 0;
}
```

**Insertion:** Shift elements to make space.  
**Deletion:** Shift elements to fill gap.

---

## 1.3 Linked Lists

- Dynamic sequences of nodes with `data` + `next` pointer.
    

**Advantages:** Flexible size, efficient insertion/deletion  
**Disadvantages:** Slower access, extra memory

**Java Example: Node**

```java
public class ListNode {
    int value;
    ListNode next;
    public ListNode(int val) {
        value = val;
        next = null;
    }
}
```

**Circular Linked List (C Example):**

```c
Node* createCircularList(int val) {
    Node* head = malloc(sizeof(Node));
    head->value = val;
    head->next = head;
    return head;
}
```

---

# Unit 2: Stacks, Queues, and Recursion

## 2.1 Stacks

- **LIFO** (Last-In, First-Out)
    
- Operations: `push`, `pop`, `peek`, `isEmpty`
    
- Applications: Expression evaluation, undo features
    

**Python Example:**

```python
stack = []
stack.append(10)  # push
stack.append(20)
print(stack.pop()) # 20
```

## 2.2 Queues

- **FIFO** (First-In, First-Out)
    
- Types: Simple, Circular, Priority
    
- Operations: `enqueue`, `dequeue`, `peek`
    

**Python Example:**

```python
from collections import deque
queue = deque()
queue.append(1)
queue.append(2)
print(queue.popleft())  # 1
```

## 2.3 Recursion

- Function calling itself
    
- Base case + recursive step essential
    
- Applications: Factorial, Fibonacci, Tree Traversals
    

**Python Example: Factorial**

```python
def factorial(n):
    if n==0: return 1
    return n*factorial(n-1)

print(factorial(5))  # 120
```

---

# Unit 3: Trees, Graphs, and Hashing

## 3.1 Trees

- Hierarchical structure: nodes with parent/child relationships
    
- **Binary Tree:** Each node has ≤2 children
    
- **Binary Search Tree (BST):** Left < root < right
    

**Operations:** Traversal (Inorder, Preorder, Postorder), Insertion, Deletion

**C Example: BST Node**

```c
typedef struct Node {
    int data;
    struct Node* left;
    struct Node* right;
} Node;
```

**Traversal (Inorder Recursive Example):**

```c
void inorder(Node* root) {
    if(root != NULL) {
        inorder(root->left);
        printf("%d ", root->data);
        inorder(root->right);
    }
}
```

---

## 3.2 Graphs

- Set of vertices + edges
    
- Representations: Adjacency Matrix, Adjacency List
    
- Traversals: BFS, DFS
    

**Key Concepts:** Connected components, cycles, weighted/unweighted, directed/undirected

---

## 3.3 Hashing

- Maps keys → indices in array
    
- Collision handling: chaining or open addressing
    
- Fast search, insertion, deletion
    

**Python Example: Dictionary (Hash Table)**

```python
hash_map = {}
hash_map['a'] = 10
hash_map['b'] = 20
print(hash_map['a'])  # 10
```

---

# Exam-Oriented Tips

1. Remember **time complexity** for each operation: insert, delete, access.
    
2. Understand **traversal orders** for trees and graphs.
    
3. Know **stack/queue applications** (expression evaluation, BFS).
    
4. Practice **edge cases**: empty list, single-node tree, circular references.
    
5. Implement both **array-based** and **linked implementations**.
    
