---
updated_at: 2026-03-02T18:54:34.974+05:30
edited_seconds: 240
---
#flashcards  
#AI #FullSet

---

What is the first step in solving an AI problem?::Problem formulation, which involves defining the initial state, goal state, possible actions, constraints, and performance measure so the problem can be represented in a structured computational form.

In AI problem solving, what does the search process aim to identify?::The search process aims to explore the problem space and generate a valid sequence of actions that transforms the initial state into the goal state.

What is a Toy Problem in AI?::A toy problem is a simplified benchmark problem used to test and demonstrate AI algorithms in a controlled and fully analyzable environment such as Tic-tac-toe.

What is the Missionaries and Cannibals problem?::A classical AI problem where missionaries and cannibals must cross a river using a limited-capacity boat while ensuring cannibals never outnumber missionaries on either side.

What is the Travelling Salesman Problem?::An optimization problem in which a salesman must visit each city exactly once and return to the starting city while minimizing total travel cost; it is NP-hard.

What is the problem space in AI?::The problem space is the complete set of possible states, including the initial state, goal state, and all intermediate states connected by actions, typically represented as a graph or tree.

What is Breadth First Search?::Breadth First Search is an uninformed search algorithm that expands the shallowest unexpanded node first using a FIFO queue and guarantees completeness and optimality for equal step-cost problems.

What is Depth First Search?::Depth First Search is an uninformed search algorithm that expands the deepest unexpanded node first using a LIFO stack and is memory efficient but not guaranteed to be optimal.

What is Uniform Cost Search?::Uniform Cost Search expands the node with the lowest cumulative path cost using a priority queue and guarantees completeness and optimality for weighted graphs.

What is Depth Limited Search?::Depth Limited Search is a modified version of DFS that imposes a maximum depth limit to prevent infinite exploration in deep or cyclic search spaces.

What is Informed Search?::Informed search is a strategy that uses heuristic functions or domain knowledge to estimate closeness to the goal and reduce unnecessary exploration.

What is Generate and Test?::Generate and Test is a problem-solving method that systematically generates possible solutions and tests each against the goal criteria until a valid solution is found.

What is Best First Search?::Best First Search is a heuristic search algorithm that selects and expands the most promising node based on an evaluation function.

What is the A* algorithm?::A* is an informed search algorithm defined by f(n) = g(n) + h(n), where g(n) is the actual path cost and h(n) is the heuristic estimate, guaranteeing optimality if the heuristic is admissible.

What is adversarial search?::Adversarial search deals with competitive multi-agent environments such as games where one agent maximizes utility while another minimizes it.

What is the Mini-max algorithm?::Mini-max is a decision-making algorithm for two-player games that assumes the opponent plays optimally and selects the move that maximizes the minimum possible gain.

What is Alpha-Beta pruning?::Alpha-Beta pruning is an optimization of the Mini-max algorithm that eliminates branches of the search tree that cannot influence the final decision, improving efficiency.

What does alpha represent in Alpha-Beta pruning?::Alpha represents the best value found so far for the MAX player and serves as a lower bound during search.

What does beta represent in Alpha-Beta pruning?::Beta represents the best value found so far for the MIN player and serves as an upper bound during search.

What is a Constraint Satisfaction Problem?::A Constraint Satisfaction Problem consists of variables with domains and constraints, where the goal is to assign values to variables such that all constraints are satisfied.

What is an Intelligent Agent?::An Intelligent Agent is an autonomous entity that perceives its environment, takes actions, and aims to maximize its performance measure.

What is Rationality in agent theory?::Rationality refers to selecting actions that maximize expected performance based on available information and the defined performance measure.

What is a Performance Measure?::A performance measure is an objective criterion used to evaluate how successfully an agent achieves its goals.

What is a Task Environment?::A task environment includes the external conditions, constraints, and variables under which an intelligent agent operates.

What is a Knowledge-Based Agent?::A Knowledge-Based Agent stores facts in a knowledge base and uses logical inference to derive conclusions and make rational decisions.

What is Wumpus World?::Wumpus World is a grid-based logical reasoning environment containing pits and a monster, used to test inference and knowledge-based agent behavior.

What is Syntax in logic?::Syntax refers to the formal structure and rules used to construct valid logical sentences.

What is Semantics in logic?::Semantics refers to the meaning and truth value of logical statements within a given model or interpretation.

What is the Unification Algorithm?::The Unification Algorithm finds substitutions that make two predicate logic expressions identical, enabling logical inference.

What is a Semantic Net?::A Semantic Net is a graphical knowledge representation model consisting of nodes representing objects and arcs representing relationships.

What are Frames in knowledge representation?::Frames are structured data representations that organize knowledge into slots and attributes describing stereotypical objects or situations.

What is Uncertain Knowledge in AI?::Uncertain knowledge refers to handling incomplete, noisy, or probabilistic information using reasoning methods such as Bayesian inference.

What is AI Planning?::AI Planning is the process of generating a sequence of actions that transforms the current state into a desired goal state.

What is Blocksworld?::Blocksworld is a classical AI planning problem involving rearranging blocks to achieve a specified target configuration.

What is Means-End Analysis?::Means-End Analysis is a planning technique that reduces the difference between the current state and the goal state by selecting appropriate operators.

What is an Expert System?::An Expert System is a computer system that emulates the decision-making ability of a human expert using a knowledge base and inference engine.

What are the components of an Expert System?::The two core components are the Knowledge Base, which stores domain knowledge, and the Inference Engine, which applies logical rules to derive conclusions.

What distinguishes Predicate Logic from Propositional Logic?::Predicate Logic uses variables and quantifiers to express relationships between objects, whereas Propositional Logic deals only with simple true or false statements.

What is the Map Coloring problem?::The Map Coloring problem is a CSP where regions must be assigned colors such that no two adjacent regions share the same color.

What is Data Acquisition in AI?::Data Acquisition is the process of collecting, cleaning, and preparing raw data for use in AI systems and learning models.

What is a Simple Planning Agent?::A Simple Planning Agent generates a complete sequence of actions before execution and then performs those actions sequentially to reach the goal.

What is an Inference Pattern?::An Inference Pattern is a logical rule such as Modus Ponens used to derive new conclusions from known premises.

What is Representation using Rules?::Representation using rules encodes knowledge in If-Then statements that allow automated reasoning in knowledge-based systems.

Why is Tic-tac-toe important in AI?::Tic-tac-toe serves as a foundational toy problem used to teach search algorithms, game trees, and Mini-max strategy.

Why identify problem types and characteristics?::Identifying problem types helps determine the most appropriate AI algorithm or technique for efficient problem solving.

What is the Learning Aspect of AI?::The learning aspect involves improving performance or knowledge automatically through data, experience, and model adjustments.

What is the objective of the MIN player in adversarial search?::The MIN player aims to minimize the utility value and reduce the potential gain of the MAX player.

What are Crypt-Arithmetic puzzles?::Crypt-Arithmetic puzzles are CSPs where digits are assigned to letters to satisfy arithmetic equations.

How are Syntax and Semantics related?::Syntax defines the formal structure of knowledge representation, while semantics provides meaning and truth interpretation to those structured statements.

What are Foundational Data Structures in AI search?::Foundational data structures include stacks, queues, priority queues, and graphs, which are used to manage the frontier and represent state space.

How does Uniform Cost Search differ from BFS?::Uniform Cost Search considers cumulative path costs and works with weighted graphs, while BFS assumes equal step costs and explores level by level.

What is Reasoning in AI?::Reasoning in AI involves applying logical inference rules to existing knowledge in order to derive new conclusions.

What is the role of Machine Learning concepts in AI?::Machine Learning enables systems to improve performance automatically through experience by learning patterns from data.

Which algorithm guarantees the shortest path when the heuristic is admissible?::The A* algorithm guarantees the shortest path if the heuristic function is admissible and never overestimates the true cost.