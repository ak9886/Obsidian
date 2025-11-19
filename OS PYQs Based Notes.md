---
updated_at: 2025-11-19T21:33:00.759+05:30
edited_seconds: 160
---
##OS 

## Process Management (Topic 1)

### 1. What is a Process?

A **process** is a program that is *currently running*.  
A program is a *recipe*, but a process is the *act of cooking the dish*.

A process contains:
- Program code  
- Data it is working with  
- Temporary storage (stack)  
- Expandable memory (heap)  
- Registers and state information  

---

### 2. Process States

A process moves through different states like a student throughout a day:

| State | Meaning | Analogy |
|-------|---------|---------|
| New | Process is being created | Student joining a course |
| Ready | Waiting for CPU | Student waiting for their turn |
| Running | Currently executing | Student presenting in class |
| Waiting | Blocked for I/O | Student waiting for professor’s email reply |
| Terminated | Finished execution | Student leaving after task is done |

**Transitions happen when:**
- CPU gives a turn → Ready → Running  
- I/O needed → Running → Waiting  
- I/O finishes → Waiting → Ready  
- Time slice ends → Running → Ready  
- Process completes → Running → Terminated  

---

### 3. Process Control Block (PCB)

Think of the PCB as a **profile file** the OS keeps for every process.

It stores:
- Process ID (PID)
- Program Counter  
- CPU registers  
- Scheduling information  
- Memory allocation info  
- List of open files  
- Accounting and security information  

Whenever the CPU switches from one process to another, it updates and reads these PCBs.

---

### 4. Context Switching

When the CPU switches from one process to another:

1. Save current process’s state into its PCB  
2. Load next process’s state from its PCB  
3. Resume execution  

It’s like a teacher switching attention between two students — they must remember what each student last said.

**Context switching takes time** (overhead), because nothing useful happens during the switch.

---

### 5. Threads

A process = **whole application**  
A thread = **one path of execution inside the application**

Example analogy:  
A restaurant (process) has multiple cooks (threads) working on different tasks simultaneously.

###### Types:
- **User-level threads**  
  - Managed by user libraries  
  - Very fast, no kernel involvement  
- **Kernel-level threads**  
  - Managed by OS  
  - Slower but more reliable  
  - If a thread blocks, kernel can schedule another

---

### 6. Process Creation

A process creates another process → parent & child.

Parent passes:
- Code  
- Resources  
- Some privileges  

Child may:
- Use same program as parent  
- Load a new program  

**Termination happens when:**
- Execution completes  
- Error occurs  
- Killed by parent  
- Parent itself dies (some OS kill child processes automatically)

---

### 7. Why Process Management Matters

Efficient process management ensures:
- Fair use of CPU  
- Fast switching  
- No starvation  
- Smooth multitasking  
- Isolation and safety between applications  

It forms the backbone of any multitasking operating system.

---
# CPU Scheduling (Topic 2)

## 1. Why Scheduling Exists

Your CPU can work on only **one thing at a time** (ignoring multi-core complications).  
But your OS pretends your system can run many tasks simultaneously.

To achieve this illusion, the OS must:
- Decide **which process gets the CPU next**
- For **how long**
- In **what order**

This decision-making process is CPU scheduling.

Analogy:  
Imagine a single doctor and many patients waiting. The doctor must pick who to see next — that’s scheduling.

---

## 2. Goals of CPU Scheduling

Good scheduling aims to:
- Improve CPU utilization  
- Reduce waiting time  
- Reduce turnaround time  
- Minimize response time (for interactive systems)
- Avoid starvation  
- Balance fairness and efficiency  

---

## 3. Key Scheduling Algorithms

Below are the major algorithms you must master, along with simple analogies.

---

### **a. FCFS (First Come, First Served)**

**Description:**  
The first process to arrive gets the CPU first.

**Analogy:**  
A queue at a bakery: the first person in line gets served first.

**Pros:**  
- Simple to implement  
- Fair in a basic sense  

**Cons:**  
- Long processes delay short ones → **convoy effect**  
- Poor average waiting time  

---

### **b. SJF (Shortest Job First)**

**Description:**  
The process with the **shortest execution time** runs first.

**Analogy:**  
At a café, the barista serves quick orders (espresso) before long ones (frappuccino).

**Pros:**  
- Optimal average waiting time  
- Highly efficient  

**Cons:**  
- Requires knowing job length (estimation needed)  
- Long jobs may starve  

---

### **c. SRTF (Shortest Remaining Time First)**

**Description:**  
A preemptive version of SJF.  
If a new process arrives with shorter time than the running one, **it interrupts**.

**Analogy:**  
Someone with a “very quick” request jumps ahead even if the barista already started another order.

**Pros:**  
- Even better response for short tasks  

**Cons:**  
- High overhead  
- Starvation possible  

---

### **d. Priority Scheduling**

**Description:**  
CPU is given to the process with the highest priority.

**Analogy:**  
At a hospital, critical patients get treatment before stable ones.

**Pros:**  
- Useful when some tasks deserve more attention  
- Good for real-time systems  

**Cons:**  
- Starvation for low-priority processes  
- Solution: **aging** (gradually increase waiting process’s priority)

---

### **e. Round Robin (RR)**

**Description:**  
Each process gets a fixed time slice (quantum).  
After the quantum ends, the CPU switches to the next process.

**Analogy:**  
Every player in a game gets their turn for the same fixed time.

**Pros:**  
- Best for time-sharing systems  
- Fair for all processes  

**Cons:**  
- Too small quantum → many context switches  
- Too large quantum → behaves like FCFS  

---

### **f. Multilevel Queue Scheduling**

**Description:**  
Processes are grouped into queues based on type (foreground, background, system, user).

Each queue has **its own scheduling algorithm**.

**Analogy:**  
Different counters in a government office:  
- VIP counter  
- General counter  
- Online counter  

Each counter follows its own rules.

---

### **g. Multilevel Feedback Queue (MLFQ)**

**Description:**  
Processes can **move between queues** based on behavior.

If a process uses too much CPU, it is moved to a lower-priority queue.  
Interactive processes stay in high-priority queues.

**Analogy:**  
A teacher moves students between fast-learning and slow-learning groups depending on performance.

**Pros:**  
- Very flexible  
- Adapts to process behavior  

**Cons:**  
- Complex to configure  
- Many parameters (quantum size, queue count, rules)

---

## 4. Important Terms

### **Burst Time**
How long a process needs the CPU.

### **Waiting Time**
Total time a process waits in the ready queue.

### **Turnaround Time**
Time from arrival → completion.

### **Response Time**
Time until first execution.

---

## 5. Exam-Focused Practice

You must be able to:
- Draw Gantt charts  
- Calculate waiting and turnaround time  
- Identify preemptive vs. non-preemptive behavior  
- Compare algorithm strengths and weaknesses  

---

# Synchronization (Topic 3)

## 1. Why Synchronization is Needed

When multiple processes or threads work together, they often need access to the same data or resources.  
Without rules, they collide — like many people trying to grab the same door handle at once.

This leads to:
- Inconsistent data  
- Lost updates  
- Deadlocks (everyone blocks everyone)  
- Race conditions (output depends on unpredictable timing)

Synchronization provides the “traffic rules” for shared access.

---

## 2. Critical Section Problem

A **critical section** is a part of the program where shared data is accessed.

Only **one** process/thread should enter a critical section at a time.

A valid solution must guarantee:
1. **Mutual Exclusion**  
   Only one can be inside the critical section at once.
2. **Progress**  
   If nobody is inside, someone must be allowed to enter.
3. **Bounded Waiting**  
   Every thread gets a fair turn (no starvation).

Analogy:  
Think of a **single-stall bathroom** in a hostel.  
Only one person can enter → Mutual Exclusion  
If it’s empty, someone should go in → Progress  
Everyone waiting will eventually get a turn → Bounded Waiting

---

## 3. Race Condition

Occurs when two threads read/update shared data at the same time, causing unpredictable outcomes.

Example:  
Two people adding ₹100 each to the same wallet at the same time.  
Depending on timing, final balance may become:
- +₹100  
- +₹200  
- or something entirely wrong  
because updates overlapped.

---

## 4. Peterson’s Solution

A classical software solution for **two-process** mutual exclusion.

Variables used:
- `flag[i]`: true → process i wants to enter  
- `turn`: decides whose turn it is  

Shows:
- Pure software can solve synchronization (but inefficient)
- Useful for theoretical understanding

---

## 5. Synchronization Primitives

### **5.1 Semaphores**
A semaphore is basically a **special integer variable** with controlled operations.

Two operations:
- `wait()` → decrease value  
- `signal()` → increase value  

Types:
- **Binary semaphore** → only 0 or 1 (like a lock)
- **Counting semaphore** → allows multiple entries (e.g., parking lot spaces)

Analogy:  
Parking lot with 10 spaces → semaphore = 10  
Each car entering → wait()  
Each car leaving → signal()

---

### **5.2 Mutex Locks**
A mutex is a **lock**.  
Only one thread can own the lock at a time.

Easy analogy:  
A key hanging outside the bathroom.  
Take key → lock acquired → enter  
Return key → lock released

---

### **5.3 Monitors**
A monitor is a high-level abstraction that:
- Automatically ensures mutual exclusion  
- Contains shared data + procedures to access it  

Languages like Java and Python internally use monitors.

Analogy:  
A receptionist (monitor) that lets only one student at a time approach the counter.

---

## 6. Deadlocks

A deadlock occurs when two or more processes wait forever for resources held by each other.

Analogy:  
Two people trying to move past a narrow corridor but blocking each other — neither can move.

---

## 7. Producer–Consumer Problem

Two types of threads:
- **Producer** creates items  
- **Consumer** takes items  

They use:
- A buffer (shared space)  
- Semaphores or mutexes to avoid conflict

Example:  
A cook (producer) and waiter (consumer) sharing a counter.

---

## 8. Reader–Writer Problem

Multiple readers can read simultaneously, **but** writers require exclusive access.

Analogy:  
Many students can read a library book at once (photocopies),  
but only one librarian can edit the master copy.

---

## 9. Dining Philosophers Problem

Five philosophers need two forks to eat.  
If all pick one fork at the same time → deadlock.

This problem illustrates:
- Resource sharing  
- Deadlocks  
- Starvation  
- Synchronization strategies  

---

# Deadlock (Topic 4)

## 1. What is a Deadlock?

A **deadlock** happens when a group of processes end up waiting for each other forever.  
None of them can continue, because each one is holding a resource the other needs.

Analogy:  
Two friends trying to exchange pens — each one says:  
“I’ll give you mine only after you give me yours.”  
Result: nobody moves.

---

## 2. Conditions for Deadlock (Coffman Conditions)

A deadlock can occur **only if all four** conditions hold at the same time:

1. **Mutual Exclusion**  
   Resource can be held by one process at a time.  
   Example: a printer.

2. **Hold and Wait**  
   Process holds one resource and waits for another.  
   Like holding one fork and waiting for the second.

3. **No Preemption**  
   Resource cannot be forcibly taken away — process must release it voluntarily.

4. **Circular Wait**  
   A chain of processes hold resources that the next one in line needs.  
   Example:  
   P1 waits for P2  
   P2 waits for P3  
   P3 waits for P1  

If you break **any one** of these conditions, deadlock becomes impossible.

---

## 3. Resource Allocation Graph (RAG)

A graph to visualize resource usage:

- Circles → processes  
- Squares → resources  
- Arrow from process → resource = request  
- Arrow from resource → process = allocated  

If the graph has a **cycle**:
- Single instance per resource → deadlock guaranteed  
- Multiple instances → deadlock *possible*

---

## 4. Ways to Handle Deadlock

There are three major strategies:

---

### **4.1 Deadlock Prevention**
Prevent at least one Coffman condition.

Examples:
- Don’t allow Hold and Wait → force processes to request all resources at once  
- Break Circular Wait → impose ordering on resource requests  

Trade-off:  
System becomes safer but less efficient.

---

### **4.2 Deadlock Avoidance**
Here the OS dynamically checks if granting a resource request will lead to an unsafe state.

The most famous algorithm:  
### **Banker’s Algorithm**

Idea:  
OS acts like a banker — only gives loans (resources) if it knows it can satisfy all maximum demands later.

Needs information such as:
- Maximum resources a process may request  
- Currently allocated resources  
- Currently available resources  

Creates a **safe sequence** to ensure everyone eventually gets what they need.

---

### **4.3 Deadlock Detection and Recovery**
Let deadlocks happen, then detect and fix them.

#### Detection:
- Algorithm checks for cycles in the Resource Allocation Graph  
- For multiple instances, uses matrix-based detection

#### Recovery options:
1. Terminate one or more processes  
2. Preempt resources (forcefully take them back)  
3. Rollback process to a safe checkpoint  

Trade-off:  
Easier but disruptive — like breaking traffic rules and later clearing jams.

---

## 5. Safe vs Unsafe State

- **Safe State**  
  OS can find a sequence where all processes can complete.

- **Unsafe State**  
  Not necessarily a deadlock, but **deadlock is possible**.

Analogy:  
Safe — enough chairs in a musical-chairs game  
Unsafe — maybe enough chairs, maybe not, depending on how people move

---

## 6. Starvation vs Deadlock

These two are often confused:

- **Deadlock**: processes wait forever because of circular resource dependency  
- **Starvation**: a process waits forever because the scheduler keeps skipping it  

Starvation can occur even without deadlock.

---




