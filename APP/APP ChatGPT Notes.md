---
updated_at: 2025-11-01T20:50:52.326+05:30
edited_seconds: 20
---
#APP 


# **21CSC203P – Advanced Programming Practice**

---

## **UNIT 3 – Advanced Java Programming Paradigms**

### **Concurrent Programming Paradigm**

- **Multithreading:** Multiple threads execute concurrently within a single program.
    
- **Multitasking Types:**
    
    - _Process-based:_ Each process runs independently.
        
    - _Thread-based:_ A program runs multiple threads concurrently.
        

### **Threading in Java**

- **Main Thread:** Automatically created at program start.
    
    - Controlled using `Thread.currentThread()`.
        
- **Creating Threads:**
    
    1. Implement `Runnable` interface.
        
    2. Extend `Thread` class.
        
- **Thread Methods:**
    
    - `start()`, `run()`, `sleep()`, `isAlive()`, `join()`, `setPriority()`, `getPriority()`.
        

### **Thread Lifecycle**

- **States:** New → Runnable → Running → Waiting/Sleeping → Dead.
    

### **JDBC (Java Database Connectivity)**

- Java API to connect with relational databases.
    
- **6 Basic Steps:**
    
    1. Import packages (`java.sql`, `javax.sql`).
        
    2. Load driver (`Class.forName()` or `DriverManager.registerDriver()`).
        
    3. Establish connection (`DriverManager.getConnection()`).
        
    4. Create statement (`Statement`, `PreparedStatement`, `CallableStatement`).
        
    5. Execute query (`executeQuery`, `executeUpdate`, `execute`).
        
    6. Close connection (`conn.close()` or try-with-resources).
        
- **JDBC Objects:**
    
    - `Connection`, `Statement`, `ResultSet`.
        
    - **ResultSet Methods:** `next()`, `getInt()`, `getString()`, etc.
        

### **Sample JDBC Example (MySQL)**

```java
Class.forName("com.mysql.cj.jdbc.Driver");
Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/mydb","user","pass");
Statement st = con.createStatement();
ResultSet rs = st.executeQuery("SELECT * FROM designation");
while(rs.next()) {
    System.out.println(rs.getInt("code") + " " + rs.getString("title"));
}
```

### **Java Applets**

- Small Java programs embedded in HTML.
    
- **Applets vs Applications:**
    
    - No `main()` method.
        
    - Runs inside a browser or applet viewer.
        
- **Applet Lifecycle:**
    
    1. `init()` – Initialize applet.
        
    2. `start()` – Start applet execution.
        
    3. `paint(Graphics g)` – Draw output.
        
    4. `stop()` – Pause execution.
        
    5. `destroy()` – Cleanup before termination.
        
- **Applet Example:**
    

```java
import java.applet.*;
import java.awt.*;
public class FirstApplet extends Applet {
    public void paint(Graphics g) {
        g.drawString("Welcome to my first applet!", 50, 50);
    }
}
```

HTML:

```html
<applet code="FirstApplet.class" width="300" height="200"></applet>
```

- **Run Methods:**
    
    - Using HTML file.
        
    - Using `appletviewer` tool.
        

### **AWT (Abstract Window Toolkit)**

- GUI framework in Java for creating windows, buttons, and labels.
    
- **Hierarchy:** Object → Component → Container → Panel → Window → Frame.
    
- **Common Classes:** `Button`, `Label`, `TextField`, `Frame`, `Panel`.
    

### **Sample AWT Applet**

```java
import java.applet.*;
import java.awt.*;
public class LoginPage extends Applet {
    TextField uname, pass;
    Button b1, b2;
    public void init() {
        uname = new TextField(20);
        pass = new TextField(20);
        b1 = new Button("Submit");
        b2 = new Button("Cancel");
        add(uname); add(pass); add(b1); add(b2);
    }
}
```

---

## **UNIT 4 – Pythonic Programming Paradigm**

### **Functional Programming (FP)**

- Focuses on _what to solve_ instead of _how to solve_.
    
- Uses **pure functions**, **expressions**, and **recursion**.
    
- **Data is immutable** and supports **higher-order functions**.
    

### **Core Concepts**

- **Pure Functions:** Same input → same output; no side effects.
    
- **Recursion:** Used instead of loops.
    
- **Referential Transparency:** Expression can be replaced by its value.
    
- **Immutability:** Data can’t be modified after creation.
    
- **First-Class Functions:** Functions treated as objects.
    
- **Higher-Order Functions:** Accept functions as arguments or return them.
    

### **Examples**

```python
def inc(x): return x + 1
nums = [8, 3, 7]
print(list(map(inc, nums)))  # [9, 4, 8]
```

### **Built-in Higher-Order Functions**

|Function|Description|Example|
|---|---|---|
|`map()`|Apply function to each item|`map(lambda x: x*x, [1,2,3])`|
|`filter()`|Select items meeting a condition|`filter(lambda x: x>5, [1,6,8])`|
|`reduce()`|Combine items into one value|`reduce(lambda x,y:x+y, [1,2,3])`|

### **Lambda Functions**

- Anonymous functions with single expression.
    

```python
square = lambda x: x*x
print(square(5))  # 25
```

### **Closure**

- Function remembers values from enclosing scope.
    

```python
def counter(start=0):
    x = [start]
    def inc():
        x[0] += 1
        return x[0]
    return inc
```

### **Lazy (Non-Strict) Evaluation**

- Arguments evaluated only when needed.
    
- Example:
    
    ```python
    0 and print("right")  # won't execute print
    True and print("right")  # executes print
    ```
    

### **Partial Functions**

- Fix some parameters using `functools.partial`.
    

```python
from functools import partial
def multiply(a,b): return a*b
double = partial(multiply, 2)
print(double(5))  # 10
```

### **Comparison Paradigms**

|Functional|Procedural|Object-Oriented|
|---|---|---|
|Immutable data|Mutable data|Mutable data|
|Declarative style|Imperative style|Imperative style|
|Recursion|Loops|Loops, conditionals|
|Stateless|Stateful|Stateful|
|No side effects|Possible side effects|Methods have side effects|

### **Logic Programming Paradigm**

- Uses **facts, rules, and queries**.
    
- Based on **predicate logic**.
    
- **Fact:** Basic true statement.  
    Example: `parent(john, mary).`
    
- **Rule:** Defines relationship.  
    Example: `grandparent(X, Z) :- parent(X, Y), parent(Y, Z).`
    
- **Query:** Used to test a fact or rule.  
    Example: `?- grandparent(john, Z).`
    

### **Parallel Programming**

- **Shared Memory:** Threads share common variables.
    
- **Distributed Memory:** Each node has its own memory.
    
- **Multiprocessing:** Using multiple CPUs for concurrent execution.
    
- **Network Programming:** Using sockets (TCP/UDP).
    

