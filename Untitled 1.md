---
updated_at: 2026-03-02T18:49:04.417+05:30
edited_seconds: 210
---
#flashcards  
#AI #Unit1

---

What is the first step in solving an AI problem?::  
Problem formulation. It involves:

- Defining the initial state
    
- Defining the goal state
    
- Identifying possible actions
    
- Specifying constraints
    
- Choosing a performance measure  
    This structured representation allows the problem to be solved computationally.
    

---

In AI problem solving, what does the search process aim to identify?::  
The search process aims to:

- Explore the problem space
    
- Identify valid successor states
    
- Construct a sequence of actions
    
- Reach from the initial state to the goal state
    

---

What is a Toy Problem in AI?::  
A Toy Problem is:

- A simplified benchmark problem
    
- Used to test AI algorithms
    
- Small enough to analyze fully
    
- Example: Tic-tac-toe
    

---

What is the Missionaries and Cannibals problem?::  
It is a classic AI toy problem involving:

- Three missionaries and three cannibals
    
- A boat with limited capacity
    
- Constraint: Cannibals must never outnumber missionaries
    
- Goal: Safely transport all across the river
    

---

What is the Travelling Salesman Problem (TSP)?::  
A real-world optimization problem where:

- A salesman must visit each city exactly once
    
- Return to the starting city
    
- Minimize total travel cost
    
- It is NP-hard
    

---

What is the problem space in AI?::  
The problem space is:

- The abstract representation of all possible states
    
- Includes initial state and goal state
    
- Contains operators/actions
    
- Represented as a graph or tree
    

---

What is Breadth First Search (BFS)?::  
BFS is an uninformed search algorithm that:

- Expands the shallowest unexpanded node first
    
- Uses a FIFO queue
    
- Is complete
    
- Is optimal for equal step-cost problems
    
- Requires high memory
    

---

What is Depth First Search (DFS)?::  
DFS is an uninformed search algorithm that:

- Expands the deepest unexpanded node first
    
- Uses a LIFO stack
    
- Requires less memory than BFS
    
- Is not optimal
    
- May get stuck in infinite paths
    

---

What is Uniform Cost Search (UCS)?::  
UCS is a search algorithm that:

- Expands the node with lowest cumulative cost
    
- Uses a priority queue
    
- Is complete
    
- Is optimal
    
- Handles varying edge costs
    

---

What is Informed Search?::  
Informed search:

- Uses domain knowledge (heuristics)
    
- Estimates closeness to goal
    
- Reduces search space
    
- Improves efficiency
    

---

What is Best First Search?::  
Best First Search:

- Expands node with best heuristic value
    
- Uses evaluation function
    
- Faster than uninformed search
    
- May not always be optimal
    

---

What is the A* algorithm?::  
A* is an informed search algorithm defined by:

- f(n) = g(n) + h(n)  
    Where:
    
- g(n) = actual cost from start
    
- h(n) = estimated cost to goal  
    Properties:
    
- Complete
    
- Optimal if heuristic is admissible
    

---

What is adversarial search?::  
Adversarial search:

- Involves multiple competing agents
    
- Used in games
    
- One agent maximizes utility
    
- Other agent minimizes it
    

---

What is the Mini-max algorithm?::  
Mini-max:

- Used in two-player games
    
- Assumes opponent plays optimally
    
- MAX tries to maximize value
    
- MIN tries to minimize value
    
- Generates optimal decision
    

---

What is Alpha-Beta pruning?::  
Alpha-Beta pruning:

- Optimizes Mini-max
    
- Prunes branches that cannot influence outcome
    
- Uses alpha (best MAX value so far)
    
- Uses beta (best MIN value so far)
    
- Reduces computation
    

---

What is a Constraint Satisfaction Problem (CSP)?::  
A CSP:

- Has variables
    
- Each variable has a domain
    
- Has constraints restricting values
    
- Goal: Assign values satisfying all constraints
    

---

What is an Intelligent Agent?::  
An Intelligent Agent:

- Perceives environment
    
- Takes actions
    
- Maximizes performance measure
    
- Operates autonomously
    

---

What is a Knowledge-Based Agent?::  
A Knowledge-Based Agent:

- Stores knowledge in a knowledge base
    
- Uses logical inference
    
- Updates knowledge with new information
    
- Makes rational decisions
    

---

What is AI Planning?::  
AI Planning:

- Generates sequence of actions
    
- Achieves a goal state
    
- Uses current state + operators
    
- Often uses Means-End Analysis
    

---

What is an Expert System?::  
An Expert System:

- Mimics human expert reasoning
    
- Contains knowledge base
    
- Uses inference engine
    
- Provides domain-specific decisions
    

---

What distinguishes Predicate Logic from Propositional Logic?::  
Predicate Logic:

- Uses variables
    
- Uses quantifiers
    
- Expresses relationships
    

Propositional Logic:

- Uses simple true/false statements
    
- No internal structure
    

