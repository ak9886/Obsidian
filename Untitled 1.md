---
updated_at: 2026-03-02T18:39:38.836+05:30
edited_seconds: 190
---
#flashcards 
What is the first step in the process of using AI to solve a specific problem?::Problem formulation.

In AI problem solving, what does the 'search' process aim to identify?::A sequence of actions that leads from the initial state to a goal state.
<!--SR:!2026-03-05,3,250-->

What is a Toy Problem in AI?::A simplified benchmark problem used to test or illustrate AI algorithms (e.g., Tic-tac-toe).

Which classic AI toy problem involves moving characters across a river using a boat with limited capacity?::Missionaries and Cannibals Problem.

Which real-world AI problem focuses on finding the most efficient route for a salesman to visit each city exactly once?::Travelling Salesman Problem.
<!--SR:!2026-03-06,4,270-->

What is the 'problem space' in AI search?::The abstract environment representing all possible states and the actions that connect them.

Which data structure is typically used to implement Breadth First Search (BFS)?::A First-In-First-Out (FIFO) queue.
<!--SR:!2026-03-05,3,250-->

Which data structure is typically used to implement Depth First Search (DFS)?::A Last-In-First-Out (LIFO) stack.

How are search spaces in AI commonly represented?::Using trees or graphs.

What is Uninformed Search?::A blind search strategy that explores a state space without knowledge of the goal's location.

Which uninformed search method expands the shallowest unexpanded node first?::Breadth First Search (BFS).

How does Uniform Cost Search (UCS) choose the next node?::It expands the node with the lowest cumulative path cost from the root.

Which search method explores the deepest unexpanded node first?::Depth First Search (DFS).
<!--SR:!2026-03-06,4,270-->

What is the purpose of Depth Limited Search (DLS)?::To prevent DFS from following infinite paths by imposing a maximum depth limit.
<!--SR:!2026-03-06,4,270-->

What is Informed Search?::A search strategy that uses heuristics or domain knowledge to find solutions efficiently.

How does Generate and Test work?::It generates a possible solution and then tests it against goal criteria.
<!--SR:!2026-03-05,3,250-->

In Best First Search, how is the best node selected?::Using a heuristic evaluation function.

What is the evaluation function of A*?::f(n) = g(n) + h(n)

In A*, what does g(n) represent?::The actual cost from the start node to node n.

In A*, what does h(n) represent?::The estimated cost from node n to the goal.

What is the focus of adversarial search?::Competitive environments with conflicting agents (e.g., games).

What is the goal of the Mini-max algorithm?::To determine the optimal move assuming the opponent plays optimally.

What is the benefit of Alpha-beta pruning?::It eliminates branches that cannot affect the final decision.

In Alpha-beta pruning, what does α represent?::The best value found so far for the MAX player.
<!--SR:!2026-03-05,3,250-->

In Alpha-beta pruning, what does β represent?::The best value found so far for the MIN player.

What is a Constraint Satisfaction Problem (CSP)?::A problem where variables must satisfy specific constraints.

Crypt-arithmetic puzzles are examples of what type of AI problem?::Constraint Satisfaction Problems (CSP).

What is an Intelligent Agent?::An entity that perceives its environment and acts to maximize success.
<!--SR:!2026-03-03,1,230-->

What does rationality imply in agent theory?::Acting to achieve the best expected outcome based on performance measures.

What is a Performance Measure?::An objective criterion to evaluate agent success.
<!--SR:!2026-03-06,4,270-->

What is a Task Environment?::The external conditions and constraints under which an agent operates.

What is the role of a Knowledge-based Agent?::To use stored knowledge and logical reasoning to make decisions.

Which benchmark tests logical reasoning in an environment with hidden pits and a monster?::Wumpus World.

In logic, what is Syntax?::The formal rules used to construct valid logical sentences.

In logic, what is Semantics?::The meaning and truth of logical sentences in a model.

What does the Unification Algorithm do?::Finds substitutions that make logical expressions identical.

What is a Semantic Net?::A graphical representation of knowledge using nodes and relationships.

What are Frames in knowledge representation?::Data structures that organize properties into slots.
<!--SR:!2026-03-03,1,230-->

What problem does Uncertain Knowledge address?::Handling incomplete or unreliable information.

What is AI Planning?::Generating a sequence of actions to reach a goal state.
<!--SR:!2026-03-06,4,270-->

Which problem involves rearranging blocks to match a goal configuration?::Blocksworld problem.

What is Means-End Analysis?::A planning technique that reduces differences between current and goal states.

What is an Expert System?::A system that mimics human expert decision-making.
<!--SR:!2026-03-05,3,250-->

What are the two core components of an expert system?::Knowledge base and inference engine.

What does the Inference Engine do?::Applies logical rules to derive conclusions.
<!--SR:!2026-03-06,4,270-->

What distinguishes Predicate Logic from Propositional Logic?::Predicate logic uses variables and quantifiers; propositional logic uses simple true/false statements.
<!--SR:!2026-03-05,3,250-->

Solving a problem by assigning colors so adjacent regions differ is an example of the ==map coloring== problem.

Which search algorithm combines BFS advantages and heuristics?::Best First Search.
<!--SR:!2026-03-06,4,270-->

What is Data Acquisition in AI?::Collecting and preparing data for AI systems.
<!--SR:!2026-03-06,4,270-->

How does a Simple Planning Agent differ from a reflex agent?::It generates a complete action sequence before acting.

What is an Inference Pattern?::A logical rule like Modus Ponens used to derive conclusions.
<!--SR:!2026-03-05,3,250-->

What is Representation using rules?::Encoding knowledge as If-Then statements.

Why is Tic-tac-toe important in AI?::It is a basic toy problem for teaching search and game strategies.

Why identify Problem Types and Characteristics?::To select the appropriate AI technique.
<!--SR:!2026-03-06,4,270-->

What does the Learning Aspect of AI involve?::Improving performance through data and experience.
<!--SR:!2026-03-05,3,250-->

What is the objective of the MIN player in adversarial search?::To minimize the MAX player's gain.

What CSP example assigns digits to letters in arithmetic equations?::Crypt-Arithmetic Puzzles.
<!--SR:!2026-03-06,4,270-->

How are Syntax and Semantics related in knowledge-based agents?::Syntax defines language structure; semantics defines meaning.

What does a Simple Planning Agent do after generating actions?::Executes them sequentially.

Which AI concept mimics professional human decision-making?::Expert Systems.

What are Foundational Data Structures used for in AI search?::To represent the search space and frontier.

How does Uniform Cost Search differ from BFS?::UCS considers path costs; BFS assumes equal costs.
<!--SR:!2026-03-06,4,270-->

What is Reasoning in AI?::Using inference to derive new conclusions from knowledge.

What is the role of Machine Learning concepts?::To enable systems to improve through experience.
<!--SR:!2026-03-05,3,250-->

Which algorithm guarantees shortest path if the heuristic is admissible?::A* Algorithm.
<!--SR:!2026-03-03,1,230-->