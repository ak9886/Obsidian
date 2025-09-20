---
updated_at: 2025-09-20T14:29:14.407+05:30
edited_seconds: 30
---
## **Unit 2 – Java Basics & Core Programming Paradigms**

### 1. Java Platform Features

- **Compiled + Interpreted**: Java first compiles source code to **bytecode**, then the **JVM interpreter** executes it. Provides portability and runtime safety.
    
- **Platform Independence**: "Write Once, Run Anywhere" – bytecode runs on any machine with a JVM.
    
- **Object-Oriented**: Everything is within **classes**; supports **encapsulation, reusability, maintainability**.
    
- **Robust & Secure**: Strong type checking, garbage collection, no pointers, runtime security checks.
    
- **Distributed**: Networking support via libraries (HTTP, FTP, TCP/IP).
    
- **Simple & Familiar**: Based on C/C++, but without complexities (pointers, multiple inheritance, goto).
    
- **Multithreaded & Interactive**: Enables concurrent execution; user-interactive.
    
- **Dynamic & Extensible**: Supports runtime linking of classes, reflection, and use of external libraries.
    
- **Architectural Neutral & Portable**: Same data type sizes across platforms.
    
- **High Performance**: JIT compilation boosts execution speed.
    

---

### 2. Objects and Classes

- **Object** = state (variables) + behavior (methods).
    
- **Class** = blueprint/template for objects.
    
- **Object Lifecycle**:
    
    - **Creation** → `new` keyword
        
    - **Usage** → invoking methods/variables
        
    - **Destruction** → automatic via **Garbage Collector**.
        

---

### 3. Constructors

- **Purpose**: Initialize objects.
    
- Same name as class, no return type.
    
- **Default Constructor**: Implicitly provided if none defined.
    
- **Parameterized Constructor**: Allows passing initial values.
    
- **this keyword**: Resolves variable shadowing, constructor chaining, refers to current object.
    

---

### 4. Encapsulation & Access Control

- Encapsulation = **data hiding** using classes.
    
- **Access Modifiers**:
    
    - `public`: visible everywhere
        
    - `private`: visible only inside class
        
    - `protected`: visible in same package + subclasses
        
    - _default_: package-private
        

---

### 5. Data Types & Variables

- **Primitive Types**: byte, short, int, long, float, double, char, boolean.
    
- **Reference Types**: Classes, Arrays, Interfaces.
    
- **Variables**: Must be declared with type.
    
- Constants = values that never change (often `final`).
    

---

### 6. Operators

- **Arithmetic**: +, -, *, /, %
    
- **Relational**: ==, !=, <, >, <=, >=
    
- **Logical**: &&, ||, !
    
- **Assignment**: =, +=, -=, etc.
    
- **Increment/Decrement**: ++, -- (pre/post forms).
    
- **Precedence**: Determines evaluation order; parentheses override.
    

---

### 7. Control Flow

- **Branching**: if-else, switch, conditional operator (?:).
    
- **Looping**: while, for, do-while, enhanced for.
    
- **Compound Statements**: nested if, multi-branch structures.
    
- **Short-circuit Evaluation**: in `&&`, `||` only evaluates second operand if needed.
    

---

### 8. Strings and Comparisons

- **Equality**:
    
    - `==` → reference comparison
        
    - `.equals()` → value comparison
        
    - `.equalsIgnoreCase()` → ignores case.
        
- **Lexicographic Order**: `compareTo()` returns <0, 0, >0.
    

---

---

## **Unit 3 – Advanced Java Programming Paradigms**

### 1. Concurrent Programming

- **Concept**: Multiple tasks executing independently but may interact.
    
- **Models**:
    
    - **Shared Memory** → tasks access shared variables (must ensure synchronization).
        
    - **Message Passing** → tasks communicate by sending messages.
        
- **Issues**:
    
    - Resource sharing
        
    - Synchronization (mutexes, semaphores, events, timers).
        

---

### 2. Multithreading

- **Thread** = smallest unit of execution.
    
- **Multitasking Types**:
    
    - Process-based → multiple programs
        
    - Thread-based → multiple parts of a single program
        
- **Thread Lifecycle**: New → Runnable → Running → Waiting/Sleeping → Dead.
    
- **Creating Threads**:
    
    - Extend `Thread` class, override `run()`
        
    - Implement `Runnable` interface
        
- **Thread Control**: `start()`, `sleep()`, `join()`, `isAlive()`.
    
- **Thread Priorities**: `setPriority(int level)` [1–10].
    

---

### 3. JDBC (Java Database Connectivity)

- **Purpose**: Connect Java programs to relational databases.
    
- **Steps**:
    
    1. Import packages (`java.sql.*`, `javax.sql.*`).
        
    2. Load driver (`Class.forName` or `DriverManager.registerDriver`).
        
    3. Establish connection (`DriverManager.getConnection`).
        
    4. Create statement (`createStatement`, `prepareStatement`, `CallableStatement`).
        
    5. Execute query (`executeQuery`, `executeUpdate`).
        
    6. Process results (`ResultSet`).
        
    7. Close connection (`conn.close()`).
        
- **PreparedStatement**: Compiled once, allows parameters.
    
- **CallableStatement**: Executes stored procedures with IN/OUT parameters.
    

---

### 4. GUI Programming

- **CUI (Character UI)**: Command-line, less user-friendly.
    
- **GUI (Graphical UI)**: User interacts with windows, buttons, fields.
    
- **AWT (Abstract Window Toolkit)**: Older, basic GUI toolkit.
    
- **Swing**: Advanced GUI toolkit (lightweight, platform-independent).
    
- **MVC Architecture**: Separates **Model** (data), **View** (UI), **Controller** (logic).
    

---

### 5. Java Applets

- **Applet** = small Java program embedded in a web page.
    
- **Lifecycle**: init() → start() → stop() → destroy().
    
- **Advantages**: Easy distribution, secure sandbox, cross-platform.
    
- **Disadvantages**: Outdated, security restrictions, requires browser/JVM plugin.
    

---
