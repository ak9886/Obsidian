---
updated_at: 2025-11-03T22:34:32.188+05:30
edited_seconds: 100
---


---


##  Data Structure Quiz (Toggle Version)

---

### Q1
Which of the following best describes the fundamental property of a Binary Search Tree (BST)?

A. Every node must have either zero or two children  
B. The height of the left and right subtrees can differ by at most one  
C. All nodes in the left subtree have values less than the root's, and all nodes in the right subtree have values greater than the root's  
D. All levels of the tree are completely filled, except possibly the last level, which is filled from left to right  

```dataviewjs
let q1 = dv.el("div","");
let a1 = dv.el("div","");
let shown1 = false;
let btn1 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown1 = !shown1;
        btn1.innerText = shown1 ? "Hide Answer" : "Show Answer";
        a1.innerHTML = shown1 ? "✅ Correct Answer: C — Left subtree < Root < Right subtree." : "";
    }
});
````

---

### Q2

In the context of hashing, what is the primary purpose of a collision-resolution technique like Chaining?

A. To handle the situation where multiple keys map to the same index in the hash table.  
B. To dynamically increase the size of the hash table when it becomes too full.  
C. To re-calculate the index for a key if the initial index is already occupied.  
D. To ensure the hash function produces a unique index for every possible key.

```dataviewjs
let q2 = dv.el("div","");
let a2 = dv.el("div","");
let shown2 = false;
let btn2 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown2 = !shown2;
        btn2.innerText = shown2 ? "Hide Answer" : "Show Answer";
        a2.innerHTML = shown2 ? "✅ Correct Answer: A — Chaining handles collisions when multiple keys map to the same index." : "";
    }
});
```

---

### Q3

Topological sorting can only be applied to which type of graph?

A. Connected Unweighted Graphs  
B. Directed Acyclic Graphs (DAGs)  
C. Undirected Cyclic Graphs  
D. Weighted Undirected Graphs

```dataviewjs
let a3 = dv.el("div","");
let shown3 = false;
let btn3 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown3 = !shown3;
        btn3.innerText = shown3 ? "Hide Answer" : "Show Answer";
        a3.innerHTML = shown3 ? "✅ Correct Answer: B — Only Directed Acyclic Graphs (DAGs) can be topologically sorted." : "";
    }
});
```

---

### Q4

Which shortest path algorithm is appropriate for a weighted graph that contains negative edge weights (no negative cycles)?

A. Dijkstra's Algorithm  
B. Prim's Algorithm  
C. Breadth-First Search (BFS)  
D. Bellman-Ford Algorithm

```dataviewjs
let a4 = dv.el("div","");
let shown4 = false;
let btn4 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown4 = !shown4;
        btn4.innerText = shown4 ? "Hide Answer" : "Show Answer";
        a4.innerHTML = shown4 ? "✅ Correct Answer: D — Bellman-Ford works with negative edge weights." : "";
    }
});
```

---

### Q5

What is the primary role of the Disjoint Set Union (DSU) in Kruskal’s algorithm for finding a Minimum Spanning Tree?

A. To calculate the shortest path from the starting node to all other nodes.  
B. To efficiently check if adding a new edge will create a cycle.  
C. To store the final set of edges that constitute the MST.  
D. To maintain a priority queue of edges sorted by weight.

```dataviewjs
let a5 = dv.el("div","");
let shown5 = false;
let btn5 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown5 = !shown5;
        btn5.innerText = shown5 ? "Hide Answer" : "Show Answer";
        a5.innerHTML = shown5 ? "✅ Correct Answer: B — DSU checks for cycles efficiently in Kruskal’s algorithm." : "";
    }
});
```

---

### Q6

Given a binary tree with a height _h_, what is the formula for the maximum number of nodes it can contain?

A. 2^(h+1) − 1  
B. log₂(h + 1)  
C. h² + 1  
D. 2h

```dataviewjs
let a6 = dv.el("div","");
let shown6 = false;
let btn6 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown6 = !shown6;
        btn6.innerText = shown6 ? "Hide Answer" : "Show Answer";
        a6.innerHTML = shown6 ? "✅ Correct Answer: A — Max nodes = 2^(h+1) − 1." : "";
    }
});
```

---

### Q7

If you visit the left child, then the root, and finally the right child, which traversal order is this?

A. Inorder  
B. Postorder  
C. Level-order  
D. Preorder

```dataviewjs
let a7 = dv.el("div","");
let shown7 = false;
let btn7 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown7 = !shown7;
        btn7.innerText = shown7 ? "Hide Answer" : "Show Answer";
        a7.innerHTML = shown7 ? "✅ Correct Answer: A — Inorder traversal visits Left → Root → Right." : "";
    }
});
```

---

### Q8

What distinguishes Prim’s algorithm from Kruskal’s when constructing a Minimum Spanning Tree (MST)?

A. Kruskal’s is better for dense graphs, while Prim’s is better for sparse ones.  
B. Prim’s can handle negative edge weights, Kruskal’s cannot.  
C. Kruskal’s is greedy, while Prim’s is dynamic programming.  
D. Prim’s grows a single tree, while Kruskal’s builds a forest that merges.

```dataviewjs
let a8 = dv.el("div","");
let shown8 = false;
let btn8 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown8 = !shown8;
        btn8.innerText = shown8 ? "Hide Answer" : "Show Answer";
        a8.innerHTML = shown8 ? "✅ Correct Answer: D — Prim’s builds one growing tree, Kruskal’s merges multiple." : "";
    }
});
```

---

### Q9

In an AVL tree, what condition must hold for every node?

A. Height difference between left and right subtrees must be −1, 0, or +1.  
B. Every node must have exactly two children.  
C. Tree must be complete after every operation.  
D. Left child’s value must be half the root’s.

```dataviewjs
let a9 = dv.el("div","");
let shown9 = false;
let btn9 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown9 = !shown9;
        btn9.innerText = shown9 ? "Hide Answer" : "Show Answer";
        a9.innerHTML = shown9 ? "✅ Correct Answer: A — Balance factor must be −1, 0, or +1." : "";
    }
});
```

---

### Q10

What is the key difference in the output of Dijkstra’s vs. Kruskal’s algorithm?

A. Dijkstra’s outputs sorted edges; Kruskal’s outputs adjacency list.  
B. Dijkstra’s produces a single path; Kruskal’s a full tree.  
C. Dijkstra’s finds the longest path; Kruskal’s the shortest path.  
D. Dijkstra’s gives distances from source; Kruskal’s gives MST edges.

```dataviewjs
let a10 = dv.el("div","");
let shown10 = false;
let btn10 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown10 = !shown10;
        btn10.innerText = shown10 ? "Hide Answer" : "Show Answer";
        a10.innerHTML = shown10 ? "✅ Correct Answer: D — Dijkstra gives shortest distances; Kruskal gives MST edges." : "";
    }
});
```

---

### Q11

Which data structure is most commonly used for Level-order traversal of a tree?

A. Queue  
B. Priority Queue  
C. Stack  
D. Hash Table

```dataviewjs
let a11 = dv.el("div","");
let shown11 = false;
let btn11 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown11 = !shown11;
        btn11.innerText = shown11 ? "Hide Answer" : "Show Answer";
        a11.innerHTML = shown11 ? "✅ Correct Answer: A — Level-order uses a queue." : "";
    }
});
```

---

### Q12

Which graph representation is most space-efficient for a sparse graph?

A. Adjacency List  
B. Adjacency Matrix  
C. Incidence Matrix  
D. Edge List

```dataviewjs
let a12 = dv.el("div","");
let shown12 = false;
let btn12 = dv.el("button","Show Answer",{
    onclick:()=>{
        shown12 = !shown12;
        btn12.innerText = shown12 ? "Hide Answer" : "Show Answer";
        a12.innerHTML = shown12 ? "✅ Correct Answer: A — Adjacency List uses less space for sparse graphs." : "";
    }
});
```

