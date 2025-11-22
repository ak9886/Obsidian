---
updated_at: 2025-11-22T14:12:40.964+05:30
edited_seconds: 10
---
# DSA NOTES — FULLY EXPANDED (TOPICS 1–7)

---

# **Topic 1 — Dynamic Memory Allocation (DMA) in C**

_(malloc, calloc, realloc, free)_

Dynamic Memory Allocation allows programs to request memory at runtime instead of compile time.  
This enables flexible structures like linked lists, trees, graphs, dynamic arrays, etc.

## **Why DMA is Needed**

- Static arrays have fixed size.
    
- Data requirements are often unknown.
    
- Memory should grow/shrink as needed.
    

## **Functions**

### **malloc()**

- Allocates `n * sizeof(type)` bytes.
    
- Uninitialized memory.
    

```c
ptr = (int*) malloc(n * sizeof(int));
```

### **calloc()**

- Allocates multiple blocks.
    
- Initializes to 0.
    

```c
ptr = (int*) calloc(n, sizeof(int));
```

### **realloc()**

- Resizes memory.
    

```c
ptr = realloc(ptr, new_size);
```

### **free()**

- Releases allocated memory.
    

```c
free(ptr);
ptr = NULL;
```

## **Common Mistakes**

- Memory leaks
    
- Dangling pointers
    
- Double free
    
- Forgetting `sizeof`
    

---

# **Topic 2 — Self-Referential Structures**

A self-referential structure contains a pointer to another variable of the same structure.  
Essential for linked lists, trees, graphs.

```c
typedef struct node {
    int data;
    struct node *next;
} Node;
```

## **Why Useful**

- Enables chaining
    
- Dynamic growth
    
- Memory-efficient
    

## **Applications**

- Linked lists
    
- Stacks/queues using nodes
    
- Trees (left/right pointers)
    

---

# **Topic 3 — Singly Linked List (SLL)**

A Singly Linked List is a dynamic data structure where each node points to the next node.

```c
typedef struct node {
    int data;
    struct node *next;
} Node;
```

## **Operations**

### **Insert at Beginning**

```c
new->next = head;
head = new;
```

### **Insert at End**

```c
temp = head;
while(temp->next) temp = temp->next;
temp->next = new;
```

### **Delete Node**

```c
prev->next = curr->next;
free(curr);
```

---

# **Topic 4 — Doubly Linked List (DLL)**

Nodes contain both `next` and `prev` pointers.

```c
typedef struct node {
    int data;
    struct node *prev, *next;
} Node;
```

## **Advantages**

- Bidirectional traversal
    
- Faster deletion
    
- Efficient for navigation
    

## **Insertion (Example)**

```c
new->next = head;
head->prev = new;
head = new;
```

---

# **Topic 5 — Circular Linked List (CLL)**

Last node points back to the first node.  
Eliminates NULL references.

## **Benefits**

- Great for round-robin scheduling
    
- Efficient looping
    

## **Insertion at End**

```c
new->next = head;
temp->next = new;
```

---

# **Topic 6 — Stack Using Arrays**

A stack follows **LIFO** (Last In, First Out).  
Array-based stacks are simple and fast but have fixed size.

## **Operations**

### **push()**

```c
stack[++top] = val;
```

### **pop()**

```c
val = stack[top--];
```

### **peek()**

```c
return stack[top];
```

## **Overflow / Underflow**

- Overflow: `top == size-1`
    
- Underflow: `top == -1`
    

---

# **Topic 7 — Stack Using Linked List**

Linked-list-based stacks are dynamic.

## **push()**

```c
new->next = top;
top = new;
```

## **pop()**

```c
temp = top;
top = top->next;
free(temp);
```

## **Advantages**

- No fixed size
    
- Grows as needed
    

---

**Topics 1–7 successfully regenerated into the Markdown file.**

Ready for **Topic 8**.

# **TOPIC 8 — Queues (Linear Queue, Circular Queue, Priority Queue)**

**Unit:** 2 — Linear Data Structures  
**Recurrence Level:** Very High  
**Weightage:** Always tested (5–10 mark + tracing)

---

## **1. What a Queue Is (Core Idea)**

A **queue** follows the rule:

**FIFO — First In, First Out**

Analogy: people standing in a line at 600042 bus stand — the first person in the queue is the first to board.

Used when order must be preserved.

---

## **2. Basic Queue Operations**

### **(a) enqueue(x)** → insert at **rear**

### **(b) dequeue()** → remove from **front**

### **(c) front()** → value at the beginning

### **(d) rear()** → value at the end

### **(e) isFull()**

### **(f) isEmpty()**

---

## **3. Linear Queue (Using Array)**

Representation:

```
front → [10, 20, 30, __, __] ← rear
```

### **Problem: Wasted Space (Exam Favourite)**

After multiple dequeues:

```
[__, __, 30, 40, 50]
```

Even though there is space at the front, `rear` has reached array end → described as **Queue Overflow**.

This leads to **Circular Queue**.

---

## **4. Circular Queue (Fix for Wasted Space)**

Uses modulo arithmetic.  
Rear wraps around:

```
rear = (rear + 1) % size
front = (front + 1) % size
```

Diagram:

```
Index: 0   1   2   3   4
Value: 40  50  __  10  20
            ↑       ↑
          front    rear
```

### **Condition for Full Queue:**

```
(front == (rear + 1) % size)
```

### **Condition for Empty Queue:**

```
(front == -1)
```

---

## **5. Queue Pseudocode (Exam Standard)**

### **(a) enqueue(x)**

```
function enqueue(x):
    if (front == -1 and rear == -1):
        front = rear = 0
        queue[rear] = x
    else if ((rear + 1) % size == front):
        print "Overflow"
    else:
        rear = (rear + 1) % size
        queue[rear] = x
```

### **(b) dequeue()**

```
function dequeue():
    if (front == -1):
        print "Underflow"
    else if (front == rear):
        value = queue[front]
        front = rear = -1
        return value
    else:
        value = queue[front]
        front = (front + 1) % size
        return value
```

---

## **6. Priority Queue (Concept Only)**

Element with **highest priority** is removed first.

Used in:

- CPU scheduling
    
- Dijkstra’s algorithm
    
- A* pathfinding
    

### **Types:**

1. **Ascending Priority Queue** — smallest value removed first
    
2. **Descending Priority Queue** — largest value removed first
    

Usually implemented with **heaps**.

---

## **7. Queue Questions in Exams**

Expect:

- Write enqueue/dequeue operations
    
- Trace circular queue states
    
- Identify overflow/underflow
    
- Difference: linear vs circular
    
- Priority queue explanation
    
- Draw queue after operations
    

---

# **Topic 8 Complete — Ready for Topic 9**

# **TOPIC 9 — Circular Queue (Using Array)**

**Unit:** 2 — Linear Data Structures  
**Recurrence Level:** Very High  
**Weightage:** Frequently tested in tracing, overflow/underflow conditions, and implementation logic

---

## **1. What Problem Circular Queue Solves**

A normal queue using arrays suffers from **false overflow**:

Example (size = 5):

```
Front → 3
Rear  → 4
Queue: [_, _, _, A, B]
```

If two elements were removed earlier, empty spaces exist, but `rear == size−1` makes the queue look full.

A circular queue **wraps around**, reusing empty space.

---

## **2. Circular Queue Principle**

Indices wrap using:

```
(index + 1) % size
```

This makes the array behave like a ring.

---

## **3. Structure of Circular Queue (C Implementation)**

```c
#define SIZE 5
int queue[SIZE];
int front = -1;
int rear = -1;
```

---

## **4. When is the Queue Empty?**

```
front == -1
```

---

## **5. When is the Queue Full? (Important MCQ)**

```
(front == (rear + 1) % SIZE)
```

This condition is asked very frequently.

---

## **6. Enqueue Operation (Insert) — Pseudocode**

```
function enqueue(x):
    if ( (rear + 1) % SIZE == front ):
        print "Queue Full"
        return

    if (front == -1):
        front = 0

    rear = (rear + 1) % SIZE
    queue[rear] = x
```

---

## **7. Dequeue Operation (Delete) — Pseudocode**

```
function dequeue():
    if front == -1:
        print "Queue Empty"
        return

    x = queue[front]

    if front == rear:
        front = rear = -1
    else:
        front = (front + 1) % SIZE

    return x
```

---

## **8. Display Operation (Frequently Asked)**

```
function display():
    if front == -1:
        print "Empty"
        return

    i = front
    while True:
        print queue[i]
        if i == rear:
            break
        i = (i + 1) % SIZE
```

---

## **9. Example Trace (Exam Favourite)**

Operations:

```
enqueue(10)
enqueue(20)
enqueue(30)
dequeue()
enqueue(40)
enqueue(50)
```

Final representation:

```
Front → 1
Rear  → 0
Queue: [50, 20, 30, 40, _]
```

Wrap‑around must be shown in exams.

---

## **10. Common Exam Mistakes**

### **(i) Using normal full condition**

```
rear == SIZE - 1   // WRONG for circular queue
```

### **(ii) Not resetting front and rear on last deletion**

Causes traversal errors.

### **(iii) Forgetting modulo operation**

Without `% SIZE`, wrap-around never happens.

---

## **11. Typical Exam Questions**

- Write enqueue/dequeue pseudocode for circular queue.
    
- Trace the queue after a series of operations.
    
- State the condition for FULL and EMPTY.
    
- Implement circular queue using arrays.
    

---

# **Topic 9 Complete — Ready for Topic 10**

# **TOPIC 10 — Array Implementation of List ADT**

**Unit:** 2 — Linear Data Structures  
**Recurrence Level:** Medium  
**Weightage:** Common for 5–10 mark questions (definitions, operations, pros/cons, tracing)

---

## **1. What a List ADT Actually Represents**

A **List ADT** is simply an ordered collection of elements with positions:

- Insert
    
- Delete
    
- Retrieve
    
- Update
    
- Traverse
    

When implemented using arrays, you get:

- Continuous memory
    
- Fixed maximum size
    
- Index-based access (O(1))
    

---

## **2. Structure of Array-Based List (Core Exam Definition)**

```c
#define MAX 100

typedef struct {
    int data[MAX];
    int size;      // current number of elements
} List;
```

Key points:

- `data[]` stores elements.
    
- `size` keeps count of active elements.
    
- Valid indices: `0` to `size-1`.
    

---

## **3. Basic Operations (Core Exam Area)**

### **(a) Insertion at a Position**

Steps:

1. Check overflow (`size == MAX`).
    
2. Shift all elements from position `pos` to the right.
    
3. Insert new element.
    
4. Increment size.
    

**Pseudocode:**

```
function insert(list, pos, value):
    if list.size == MAX:
        return OVERFLOW

    for i = list.size - 1 down to pos:
        list.data[i+1] = list.data[i]

    list.data[pos] = value
    list.size = list.size + 1
```

Time complexity: **O(n)** (because of shifting).

---

### **(b) Deletion at a Position**

Steps:

1. Check underflow (`size == 0`).
    
2. Shift all elements from `pos+1` left.
    
3. Reduce size.
    

**Pseudocode:**

```
function delete(list, pos):
    if list.size == 0:
        return UNDERFLOW

    for i = pos to list.size - 2:
        list.data[i] = list.data[i+1]

    list.size = list.size - 1
```

Time complexity: **O(n)**.

---

### **(c) Searching**

Simple linear search.

```
function search(list, value):
    for i = 0 to list.size - 1:
        if list.data[i] == value:
            return i
    return -1
```

Time complexity: **O(n)**.

---

### **(d) Update / Replace**

```
list.data[pos] = newValue
```

Time complexity: **O(1)**.

---

## **4. Example Trace (Common 5-Mark Question)**

Initial list:

```
[10, 20, 30, 40]   size = 4
```

Operation: Insert 25 at position 2

```
Shift 30 → position 3
Shift 40 → position 4
Insert 25 at position 2
```

Result:

```
[10, 20, 25, 30, 40]  size = 5
```

---

## **5. Advantages of Array Implementation**

- Very fast random access → O(1)
    
- Good cache locality → faster iterations
    
- Easier to implement than linked lists
    
- Memory overhead is minimal
    

---

## **6. Disadvantages (Exam Favourite)**

- Fixed size (no dynamic growth)
    
- Insertion/deletion expensive (O(n)) due to shifting
    
- Wastage if declared with large MAX but few elements used
    

Exam questions frequently ask:  
**“Why are array-based lists inefficient for insert/delete in the middle?”**  
Answer: Because of shifting of elements.

---

## **7. Typical Exam Questions**

- Write the array representation of List ADT.
    
- Insert/delete at specific position with tracing.
    
- Advantages and disadvantages.
    
- Compare List ADT (Array) vs Linked List.
    
- Why insertion in arrays is O(n)?
    

---

# **Topic 10 Complete — Ready for Topic 11**