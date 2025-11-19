---
updated_at: 2025-11-19T21:27:51.931+05:30
edited_seconds: 10
---
#OS 
# Process Management

## 1. What is a Process?

A **process** is a program that is *currently running*.  
A program is a *recipe*, but a process is the *act of cooking the dish*.

A process contains:
- Program code  
- Data it is working with  
- Temporary storage (stack)  
- Expandable memory (heap)  
- Registers and state information  

---

## 2. Process States

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

## 3. Process Control Block (PCB)

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

## 4. Context Switching

When the CPU switches from one process to another:

1. Save current process’s state into its PCB  
2. Load next process’s state from its PCB  
3. Resume execution  

It’s like a teacher switching attention between two students — they must remember what each student last said.

**Context switching takes time** (overhead), because nothing useful happens during the switch.

---

## 5. Threads

A process = **whole application**  
A thread = **one path of execution inside the application**

Example analogy:  
A restaurant (process) has multiple cooks (threads) working on different tasks simultaneously.

### Types:
- **User-level threads**  
  - Managed by user libraries  
  - Very fast, no kernel involvement  
- **Kernel-level threads**  
  - Managed by OS  
  - Slower but more reliable  
  - If a thread blocks, kernel can schedule another

---

## 6. Process Creation

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

## 7. Why Process Management Matters

Efficient process management ensures:
- Fair use of CPU  
- Fast switching  
- No starvation  
- Smooth multitasking  
- Isolation and safety between applications  

It forms the backbone of any multitasking operating system.

---
