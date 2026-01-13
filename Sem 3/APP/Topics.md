---
updated_at: 2025-11-02T22:00:26.576+05:30
edited_seconds: 30
---
#APP 


---

## **UNIT 3 – Advanced Java Programming Paradigms**

### **Concurrent Programming Paradigm**

- Concept of concurrency and multitasking
    
- Process-based vs Thread-based multitasking
    
- Advantages of multithreading
    
- Java support for multithreading
    
- Main thread and child threads
    

### **Thread Class and Methods**

- Creating threads
    
    - Implementing `Runnable` interface
        
    - Extending `Thread` class
        
- Lifecycle and states: New → Runnable → Running → Waiting → Dead
    
- Methods: `start()`, `run()`, `sleep()`, `join()`, `isAlive()`, `setPriority()`
    
- Thread synchronization and communication
    
- Example programs for main thread and multiple threads
    

---

### **Declarative Programming – JDBC**

- Definition and purpose of JDBC
    
- **Steps in JDBC Programming**
    
    1. Import packages (`java.sql`, `javax.sql`)
        
    2. Load/Register driver (`Class.forName`)
        
    3. Establish connection (`DriverManager.getConnection`)
        
    4. Create `Statement` / `PreparedStatement` / `CallableStatement`
        
    5. Execute SQL queries (`executeQuery`, `executeUpdate`, `execute`)
        
    6. Retrieve results (`ResultSet`)
        
    7. Close connection
        
- JDBC Driver Types: Bridge, Native API, Network, Thin
    
- Connection handling and try-with-resources
    

---

### **Graphical User Interface (GUI) Programming**

- **CUI vs GUI**
    
- **AWT – Abstract Window Toolkit**
    
    - Hierarchy: Object → Component → Container → Panel → Frame
        
    - Components: `Label`, `Button`, `TextField`, `Checkbox`, `Frame`
        
    - Graphics class methods: `drawRect`, `fillOval`, `setColor`, etc.
        

---

### **Applets**

- Definition and difference from applications
    
- Lifecycle: `init()`, `start()`, `paint()`, `stop()`, `destroy()`
    
- Embedding in HTML and running via `appletviewer`
    
- Example: Login form applet
    

---

### **MVC Pattern and Widgets**

- Model–View–Controller architecture in GUI design
    
- Widgets as View elements
    
- Event handling and controller logic
    

---

## **UNIT 4 – Pythonic Programming Paradigm**

### **Functional Programming (FP)**

- Declarative style focusing on _what_ to compute
    
- **Key Concepts**
    
    - Pure functions (no side effects)
        
    - Recursion instead of loops
        
    - Referential transparency
        
    - Immutability
        
    - First-class and higher-order functions
        

#### **Higher-Order Built-ins**

|Function|Description|Example|
|---|---|---|
|`map()`|Apply function to iterable|`map(lambda x:x*x, lst)`|
|`filter()`|Filter items by predicate|`filter(lambda x:x>0, lst)`|
|`reduce()`|Combine values iteratively|`reduce(lambda x,y:x+y, lst)`|

#### **Lambda Expressions**

`square = lambda x: x*x print(square(5))  # 25`

#### **Closures**

`def counter(start=0):     x = [start]     def inc(): x[0]+=1; return x[0]     return inc`

#### **Lazy Evaluation & Partial Functions**

- Short-circuit evaluation (`and`, `or`)
    
- `functools.partial` to preset arguments
    

#### **Paradigm Comparison**

|Feature|Functional|Procedural|OOP|
|---|---|---|---|
|Data|Immutable|Mutable|Mutable|
|Control Flow|Recursion|Loops|Loops/Methods|
|State|Stateless|Stateful|Stateful|
|Side Effects|None|Possible|Frequent|

---

### **Logic Programming Paradigm**

- Computation through facts, rules & queries
    
- Predicates and clauses (Prolog style)
    

`parent(john, mary). grandparent(X,Z) :- parent(X,Y), parent(Y,Z).`

---

### **Parallel Programming Paradigm**

- Shared vs Distributed Memory models
    
- Python `multiprocessing` module
    
- Network Programming using Sockets (TCP/UDP)
    

---

## **UNIT 5 – Formal and Symbolic Programming Paradigm**

### **Automata-Based Programming**

- Concept of Automata Theory in programming
    
- Alphabets, strings, and languages
    
- **Finite Automata**
    
    - Deterministic Finite Automaton (DFA)
        
    - Nondeterministic Finite Automaton (NFA)
        
    - Transition functions and tables
        
    - Accepting states and regular languages
        
- **Python Implementation**
    
    - Using `automata.fa.dfa` and `automata.fa.nfa` modules
        
- **Exercises**
    
    - DFA for strings containing `001`
        
    - DFA for even number of 1s
        
    - NFA for strings ending with `01`
        
    - Converting regular expressions to FA
        

---

### **Symbolic Programming Paradigm**

- Programs that manipulate their own expressions
    
- Used in AI, expert systems, NLP, game AI
    
- Languages: **LISP**, **Prolog**
    

---

### **SymPy – Symbolic Mathematics in Python**

- Install: `pip install sympy`
    
- Symbol declaration using `symbols()`
    
- Constants: `pi`, `e`, `oo`
    
- **Mathematical Operations**
    
    - `Rational()` class
        
    - Limits (`limit()`), Derivatives (`diff()`), Integrals (`integrate()`)
        
    - Series expansion (`series()`)
        
    - Algebraic manipulations (`expand`, `simplify`, `trigsimp`)
        
    - Equation solving (`solve`, `solveset`)
        
    - Matrix operations (`Matrix()`)
        

---

### **Event-Driven Programming Paradigm**

- Flow of control determined by events (user actions, messages)
    
- Event loop and callback functions
    
- **Components**
    
    - Event handlers
        
    - Trigger functions
        
    - Mouse/keyboard/UI events
        

---

### **GUI Programming with Tkinter**

- Python GUI toolkits: Tkinter, wxPython, PyQt, JPython
    
- Steps to build a GUI: `Tk()`, widgets, event loop
    
- **Geometry Managers**
    
    - `pack()`, `grid()`, `place()`
        
- **Widgets**
    
    - `Label`, `Button`, `Entry`, `Canvas`, `Checkbutton`, `Radiobutton`, `Scale`, `Spinbox`, `Menubutton`
        
- **Widget Properties**
    
    - Color, font, size, cursor, anchor, relief
        
- **Examples**
    
    - Message box event handling
        
    - Canvas drawing
        
    - Scale slider and Spinbox value selection
        

---

## **Summary of All Paradigms**

| Paradigm           | Language Focus  | Core Concepts                     |
| ------------------ | --------------- | --------------------------------- |
| Concurrent         | Java            | Threads, Synchronization          |
| Declarative (JDBC) | Java            | Database connectivity             |
| GUI/Applet         | Java            | AWT, Applets, MVC                 |
| Functional         | Python          | Pure functions, map/filter/reduce |
| Logic              | Python / Prolog | Facts, rules, queries             |
| Parallel           | Python          | Multiprocessing, sockets          |
| Automata-Based     | Python          | DFA, NFA, Regex conversion        |
| Symbolic           | Python / LISP   | Algebraic manipulation, SymPy     |
| Event-Driven       | Python          | Tkinter widgets, event loop       |
