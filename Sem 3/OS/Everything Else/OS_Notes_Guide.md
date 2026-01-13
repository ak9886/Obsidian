---
updated_at: 2025-09-02T12:42:48.519+05:30
edited_seconds: 150
---
# 📘 Operating Systems – Comprehensive Notes Guide

## 1. Introduction to OS
- **Definition:** An OS is a kernel that allows users to interact effectively with computer hardware.
- **Roles:**
  - Acts as an intermediary between user and hardware.
  - Provides services: process management, memory management, file systems, I/O, protection.

---

## 2. Basic Concepts
- **Program:** App that performs specific tasks.
- **Input/Output Examples:** Keyboard → Monitor, Mouse → Speaker.
- **Hardware vs Software:**
  - Hardware: CPU, GPU, RAM.
  - Software: Chrome, Edge, PowerPoint.

- **Memory Units:**  
  KB = 1024 B, MB = 1024² B, GB = 1024³ B.

---

## 3. System Structures
### Kernel Data Structures
- Singly/Doubly Linked Lists.
- Binary Search Trees (root, parent, child).
- Balanced BST: O(log n).
- Hash functions → hash maps.

### OS Structures
- **Monolithic:** Fast, less modular.
- **Layered:** Easier debugging, modular.
- **Microkernel:** Minimal kernel, modular, secure but overhead.

### Distributed Systems
- **Client-Server:** Centralized services.  
- **Peer-to-Peer (P2P):** Each node acts as client/server.  
- **Networks:** LAN, WAN, MAN, PAN.

---

## 4. Virtualization & System Calls
### Virtualization
- Enables multiple OS on one hardware.
- **Emulation:** When CPU types differ.
- **Interpretation:** When language not compiled.

### System Calls
- **Concept:** Bridge between user programs and kernel.
- **Types:**
  - File Operations: `open()`, `read()`, `write()`.
  - Process Operations: `fork()`, `exec()`, `wait()`.
  - Memory Operations: `malloc()`, `mmap()`.
- **APIs:** Win32 (Windows), POSIX (UNIX/Linux), Java API (JVM).

---

## 5. Process Management
### Process Concepts
- **Process:** Program in execution.
- **States:** New, Running, Waiting, Ready, Terminated.
- **PCB (Process Control Block):** Holds process state, registers, scheduling info, memory info.

### Process Scheduling
- **Schedulers:**
  - Long-term: Controls degree of multiprogramming.
  - Short-term: Chooses next process for CPU.
- **Queues:** Job queue, Ready queue, Device queue.

### Operations
- **Creation:** Parent creates child processes (tree).
- **Termination:** `exit()`, parent may use `abort()`.
- **Cascading termination**: If parent dies, children terminated.

### IPC (Interprocess Communication)
- **Independent vs Cooperating processes.**
- **Producer–Consumer Problem:** Bounded/unbounded buffer.
- **Direct Communication:** `send(P, msg)`, `receive(Q, msg)`.
- **Buffering:** Zero, bounded, unbounded capacity.
- **Pipes, Sockets, RPC, RMI.**

---

## 6. Threads & Concurrency
### Threads
- **Definition:** Smallest execution unit of a program.
- **Types:**
  - 1–1, many–1, many–many.
  - User vs Kernel threads.
  - Pthreads, Java Threads (Runnable, Thread class).
- **Thread Pools:** Pre-created threads for tasks.

### Concurrency vs Parallelism
- **Concurrency:** Single core, switching between tasks.
- **Parallelism:** Multiple cores, true parallel execution.

### Synchronization
- **Critical Section Problem:** Only one process in critical section at a time.
- **Solutions:**
  - Peterson’s Algorithm.
  - Locks (`acquire()` and `release()`).
  - Monitors with condition variables.

---

## 7. Storage & File Systems
- **Storage hierarchy:** Registers → Cache → RAM → Disk → Tape.
- **Cost vs Performance**
  - SSDs: High cost, high performance.
  - HDDs: Medium.
  - Tape/Cold Storage: Low cost, low performance.

- **File operations:** create, open, read, write, delete.
- **File attributes and permissions.**

---

## 8. OS Case Studies
- **MS-DOS:** Single tasking, single memory space.
- **Windows vs UNIX:** GUI vs CLI, NTFS vs ext4/XFS, licensing differences.
- **Google Chrome:** Multi-process (browser, renderer, plugin).

---

## 9. Important Formulas
- **Amdahl’s Law:**  
  $$
  {P} \leq \frac{1}{S + \frac{(1-S)}{N}}
  $$  where *S* = serial fraction, *N* = processors.

---

## 10. Sample Q&A Highlights (from CT1)
- **Fastest memory in hierarchy:** CPU registers.
- **Linux process control system call:** `fork()`.
- **Bootstrap loader location:** ROM.
- **Multithreading:** Multiple concurrent execution paths in a single process.
- **Suitable OS structure for loosely coupled system:** Layered OS.

---

