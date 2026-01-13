---
updated_at: 2025-11-04T12:34:41.213+05:30
edited_seconds: 30
---

```dataviewjs
// --- DataviewJS: Shuffle quiz and render interactive buttons ---
// Requirements: Dataview plugin enabled. View this note in Preview/Reading mode.

const questions = [
  {
    q: "Which of the following best describes the fundamental property of a Binary Search Tree (BST)?",
    options: [
      "A. Every node must have either zero or two children, and all leaf nodes must be at the same level.",
      "B. The height of the left and right subtrees of any node can differ by at most one.",
      "C. All nodes in the left subtree have values less than the root's value, and all nodes in the right subtree have values greater than the root's value.",
      "D. All levels of the tree are completely filled, except possibly the last level, which is filled from left to right."
    ],
    answer: "C. All nodes in the left subtree have values less than the root's value, and all nodes in the right subtree have values greater than the root's value."
  },
  {
    q: "In the context of hashing, what is the primary purpose of a collision-resolution technique like Chaining?",
    options: [
      "A. To handle the situation where multiple keys map to the same index in the hash table.",
      "B. To dynamically increase the size of the hash table when it becomes too full.",
      "C. To re-calculate the index for a key if the initial index is already occupied.",
      "D. To ensure the hash function produces a unique index for every possible key."
    ],
    answer: "A. To handle the situation where multiple keys map to the same index in the hash table."
  },
  {
    q: "Topological sorting is an algorithm that can only be applied to which type of graph?",
    options: [
      "A. Connected Unweighted Graphs",
      "B. Directed Acyclic Graphs (DAGs)",
      "C. Undirected Cyclic Graphs",
      "D. Weighted Undirected Graphs"
    ],
    answer: "B. Directed Acyclic Graphs (DAGs)"
  },
  {
    q: "Which shortest path algorithm is appropriate for a weighted graph that contains negative edge weights (no negative cycles)?",
    options: [
      "A. Dijkstra's Algorithm",
      "B. Prim's Algorithm",
      "C. Breadth-First Search (BFS)",
      "D. Bellman-Ford Algorithm"
    ],
    answer: "D. Bellman-Ford Algorithm"
  },
  {
    q: "What is the primary role of the Disjoint Set Union (DSU) in Kruskal’s algorithm for finding a Minimum Spanning Tree (MST)?",
    options: [
      "A. To calculate the shortest path from the starting node to all other nodes.",
      "B. To efficiently check if adding a new edge will create a cycle in the forming tree.",
      "C. To store the final set of edges that constitute the Minimum Spanning Tree.",
      "D. To maintain a priority queue of edges sorted by weight."
    ],
    answer: "B. To efficiently check if adding a new edge will create a cycle in the forming tree."
  },
  {
    q: "Given a binary tree with height h, what is the formula for the maximum number of nodes it can contain?",
    options: [
      "A. 2^(h+1) − 1",
      "B. log2(h + 1)",
      "C. h^2 + 1",
      "D. 2h"
    ],
    answer: "A. 2^(h+1) − 1"
  },
  {
    q: "If you visit the left child, then the root, and finally the right child, which traversal order is this?",
    options: [
      "A. Inorder",
      "B. Postorder",
      "C. Level-order",
      "D. Preorder"
    ],
    answer: "A. Inorder"
  },
  {
    q: "What distinguishes Prim’s algorithm from Kruskal’s when constructing a Minimum Spanning Tree (MST)?",
    options: [
      "A. Kruskal's is better for dense graphs, while Prim's is better for sparse graphs.",
      "B. Prim's algorithm can handle negative edge weights, while Kruskal's cannot.",
      "C. Kruskal's is a greedy algorithm, while Prim's is based on dynamic programming.",
      "D. Prim's algorithm builds the MST by growing a single tree, while Kruskal's can form a forest of trees that later merge."
    ],
    answer: "D. Prim's algorithm builds the MST by growing a single tree, while Kruskal's can form a forest of trees that later merge."
  },
  {
    q: "In an AVL tree, what condition must hold for every node?",
    options: [
      "A. The height difference between its left and right subtrees (balance factor) must be −1, 0, or +1.",
      "B. Every node must have exactly two children.",
      "C. The tree must be a complete binary tree after every operation.",
      "D. The value of the left child must be half the value of the root."
    ],
    answer: "A. The height difference between its left and right subtrees (balance factor) must be −1, 0, or +1."
  },
  {
    q: "What is the key difference in the output of Dijkstra’s vs. Kruskal’s algorithm?",
    options: [
      "A. Dijkstra’s outputs a sorted list of all edges, while Kruskal’s outputs an adjacency list.",
      "B. Dijkstra’s produces a single path, while Kruskal’s produces a full tree.",
      "C. Dijkstra’s finds the longest path in a DAG, while Kruskal’s finds the shortest path.",
      "D. Dijkstra’s output is a set of distances from a source node, while Kruskal’s output is a set of edges forming a minimum spanning tree."
    ],
    answer: "D. Dijkstra’s output is a set of distances from a source node, while Kruskal’s output is a set of edges forming a minimum spanning tree."
  },
  {
    q: "Which data structure is most commonly used to implement a Level-order traversal of a tree?",
    options: [
      "A. Queue",
      "B. Priority Queue",
      "C. Stack",
      "D. Hash Table"
    ],
    answer: "A. Queue"
  },
  {
    q: "Which graph representation is most space-efficient for a sparse graph?",
    options: [
      "A. Adjacency List",
      "B. Adjacency Matrix",
      "C. Incidence Matrix",
      "D. Edge List"
    ],
    answer: "A. Adjacency List"
  }
];

// Fisher–Yates shuffle
for (let i = questions.length - 1; i > 0; i--) {
  const j = Math.floor(Math.random() * (i + 1));
  [questions[i], questions[j]] = [questions[j], questions[i]];
}

// Create container
const container = dv.container;
container.innerHTML = ""; // clear

// Add simple styling container
const style = document.createElement("style");
style.textContent = `
.quiz-card { background:#2b2b2b; padding:12px; border-radius:8px; margin:10px 0; color:var(--text-normal); }
.quiz-button { background:var(--interactive-accent); color:var(--text-on-accent); border:0; padding:6px 8px; border-radius:6px; cursor:pointer; margin-top:8px; }
.quiz-answer { display:none; margin-top:8px; padding:8px; background:#222; border-radius:6px; }
`;
document.head.appendChild(style);

// Render questions with DOM API and attach listeners (works after export to HTML)
questions.forEach((item, idx) => {
  const card = document.createElement("div");
  card.className = "quiz-card";
  const qh = document.createElement("h3");
  qh.textContent = `${idx + 1}. ${item.q}`;
  card.appendChild(qh);

  const ul = document.createElement("ul");
  item.options.forEach(opt => {
    const li = document.createElement("li");
    li.textContent = opt;
    ul.appendChild(li);
  });
  card.appendChild(ul);

  const btn = document.createElement("button");
  btn.className = "quiz-button";
  btn.textContent = "Show Answer";

  const ans = document.createElement("div");
  ans.className = "quiz-answer";
  ans.textContent = `Answer: ${item.answer}`;

  btn.addEventListener("click", () => {
    const nowShown = ans.style.display === "block";
    ans.style.display = nowShown ? "none" : "block";
    btn.textContent = nowShown ? "Show Answer" : "Hide Answer";
  });

  card.appendChild(btn);
  card.appendChild(ans);
  container.appendChild(card);
});
```
