---
updated_at: 2025-11-20T08:19:01.221+05:30
edited_seconds: 280
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





# Memory Management (Topic 5)

## 1. Why Memory Management Matters

An operating system must keep track of:
- **Which parts of memory are free**
- **Which parts are occupied**
- **Which process owns which memory**
- **How to efficiently allocate and reclaim memory**

Analogy:  
Think of RAM as a **hotel**. Memory management is the reception desk:
- Assigning rooms  
- Keeping track of which room is occupied  
- Moving guests when needed  
- Cleaning rooms for new guests  

---

## 2. Address Spaces: Logical vs Physical

### Logical Address
Generated by the **CPU** during execution.  
Analogy: “The room number written on your keycard.”

### Physical Address
Actual location in **RAM**.  
Analogy: “The actual physical room in the hotel.”

Memory Management Unit (MMU) converts logical → physical.

---

## 3. Paging

Paging divides memory into fixed-size blocks.

### Key terms:
- **Page** → block of logical memory  
- **Frame** → block of physical memory  
- **Page Table** → maps each page to a frame  

Analogy:  
Imagine your notes split into identical-sized chapters (pages), and the shelves in the library (frames) hold them in any order. The index (page table) tells you where each chapter is stored.

### Why Paging is useful
- Eliminates **external fragmentation**  
- Simple allocation  
- Easy sharing between processes  

---

## 4. Segmentation

Segmentation divides memory based on **logical divisions**:
- Code segment  
- Data segment  
- Stack segment  

Analogy:  
Instead of equal-sized chapters, you group content by meaning:
- One folder for diagrams  
- One for solved problems  
- One for definitions  

Segments can be different sizes.

### Downside:
- Causes **external fragmentation**  
- Harder to manage than paging

---

## 5. Paging + Segmentation (Combined)

Modern OS often combine both:
- Program divided into segments  
- Each segment is further divided into pages  

Best of both worlds.

---

## 6. Fragmentation

### **Internal Fragmentation**
Wasted space *inside* allocated blocks.  
Cause → Fixed-size allocation.

Analogy:  
Booking a 3-bed room when you only need 2 beds.

### **External Fragmentation**
Free memory exists but is split into small pieces.  
Cause → Variable-size allocation.

Analogy:  
A hotel has free rooms, but all are scattered — no continuous stretch is available.

---

## 7. Memory Allocation Methods

### **First-Fit**
Take the first free block large enough.  
Fast, but can cause fragmentation.

### **Best-Fit**
Choose the smallest possible block that fits.  
Less waste, slower search.

### **Worst-Fit**
Allocate the largest free block.  
Leaves bigger gaps later.

Analogy:  
Choosing rental rooms:
- First-fit → first available  
- Best-fit → perfect size  
- Worst-fit → largest villa “just in case”

---

## 8. Page Replacement Algorithms

When RAM is full, the OS must remove a page to bring in a new one.

### **FIFO (First-In First-Out)**
Remove the oldest page.  
Simple but not always good.

### **LRU (Least Recently Used)**
Remove the page that was least recently accessed.  
Very effective in most cases.

### **OPT (Optimal)**
Replace the page that will not be used for the longest time in the future.  
Impossible in real life — used only for comparison.

Analogy:  
A small fridge:
- FIFO → throw out the oldest container  
- LRU → throw out what you haven’t eaten recently  
- OPT → throw out what you won’t need for the longest time (you can’t know this in real life)

---

## 9. Thrashing

Thrashing occurs when the system spends **more time swapping pages** in and out of disk than executing processes.

Cause:
- Insufficient frames  
- Too many processes running  
- Poor locality of reference  

Analogy:  
Trying to study 10 subjects with 1 notebook → constantly erasing pages instead of learning.

---

## 10. Compaction

A technique to reduce external fragmentation by shifting processes to make large continuous free memory blocks.

Analogy:  
Moving guests in a hotel so all empty rooms are next to each other.

Downside:  
Takes time and CPU work.

---

## 11. Swapping

Moving entire processes between RAM and disk to free up space.

Analogy:  
If the hotel is full, move some guests temporarily to another building (disk).

---

# Storage and File Management (Topic 6)

## 1. Why Storage Management Matters (Topic 7)

RAM is fast but temporary.  
Storage (like HDD/SSD) is slower but permanent.

The OS must manage:
- How files are stored  
- How free space is tracked  
- How fast data can be retrieved  
- How disks move their read/write heads  

Analogy:  
Think of storage as a **giant library**.  
The OS is the librarian who decides:
- Where to place books (files)  
- How to arrange shelves (blocks)  
- How to quickly find a book  
- How to track empty shelves  

---

## 2. Disk Structure Basics

### Seek Time
Time taken for the disk head to move to the correct track.  
Analogy: walking to the correct shelf.

### Rotational Latency
Waiting for the correct sector to rotate under the head.  
Analogy: waiting for the book to face you on a rotating shelf.

### Transfer Time
Actual reading/writing of data.

---

## 3. Disk Scheduling Algorithms

When many processes request disk access, the OS decides the order.

Goal: **minimize seek time** → faster performance.

---

### **3.1 FCFS (First Come First Serve)**
Serve requests in arrival order.

Pros: simple, fair  
Cons: slow, high seek time

Analogy:  
Everyone stands in a queue, regardless of distance.

---

### **3.2 SSTF (Shortest Seek Time First)**
Pick the request closest to the current head position.

Pros: faster than FCFS  
Cons: can cause starvation (far-away requests may never get served)

Analogy:  
Helping the nearest person first, even if someone far away arrived earlier.

---

### **3.3 SCAN (Elevator Algorithm)**
Disk arm moves like an elevator:
- Moves in one direction, servicing all requests  
- Then reverses direction  

Pros: fair, predictable  
Cons: middle tracks get more benefit

Analogy:  
Elevator serves all floors going up → then all floors going down.

---

### **3.4 C-SCAN (Circular SCAN)**
Moves in one direction only:
- Serves requests  
- Jumps back to the starting end without serving  

More uniform wait times.

Analogy:  
Bus picks up passengers only going forward.  
Returns empty to the start point.

---

### **3.5 LOOK Algorithm**
Optimized SCAN:  
Only goes as far as the last request in each direction—doesn't go to the end if unnecessary.

Analogy:  
Elevator only goes to the highest floor requested, not the top floor.

---

### **3.6 C-LOOK Algorithm**
Optimized C-SCAN:
- Moves in one direction only  
- Goes only as far as last request  
- Jumps back  

Analogy:  
Bus picks up passengers only up to the last stop requested.

---

## 4. File Organization Methods

Defines how file data is stored on disk.

### **4.1 Contiguous Allocation**
File stored in continuous blocks.

Pros: fast reading  
Cons: external fragmentation

Analogy:  
Booking pages 1–20 of a notebook without any gap.

---

### **4.2 Linked Allocation**
Each block points to the next.

Pros: no fragmentation  
Cons: slow random access

Analogy:  
Treasure map: each clue tells you where the next one is.

---

### **4.3 Indexed Allocation**
Central index block stores pointers to all file blocks.

Pros: fast random access  
Cons: index block can become large

Analogy:  
Contents page of a book telling page numbers for each chapter.

---

## 5. Free Space Management

OS must know which blocks are free.

### Common techniques:
- **Bit vector** (0 = free, 1 = used)  
- **Linked list of free blocks**  
- **Grouping method**  
- **Counting method** (store starting block + count)

Analogy:  
Library marks empty shelves using a list or colored stickers.

---

## 6. Swap Space Management

Swap space = extension of RAM on disk.

Used for:
- Paging  
- Storing idle processes  
- Managing memory overflow  

Analogy:  
Overflow room where the hotel keeps extra luggage when all normal closets are full.

---

## 7. RAID (Redundant Array of Independent Disks)

RAID uses multiple disks to improve:
- Speed  
- Reliability  
- Fault tolerance  

### **RAID Levels:**

- **RAID 0**: Striping (fast, no redundancy)  
- **RAID 1**: Mirroring (high reliability)  
- **RAID 5**: Distributed parity (balance of speed + safety)  
- **RAID 6**: Double parity (can survive 2 disk failures)  
- **RAID 10**: Mirroring + striping (speed + redundancy, expensive)

Analogy:  
Saving your assignment:
- RAID 0 → split across multiple computers (fast but risky)  
- RAID 1 → duplicate copies on two computers  
- RAID 5 → use math to rebuild missing data  
- RAID 10 → duplicate + split across many computers

---

# Operating System Structures and Types (Topic 7)

## 1. Why OS Structure Matters

An OS is not a single giant program.  
It’s a **collection of modules** doing different jobs:
- Process handling  
- Memory management  
- File systems  
- Device drivers  
- Security  

How these modules are arranged → **the OS structure**.

A good structure makes the OS:
- Easier to modify  
- More secure  
- Faster  
- More reliable  

Analogy:  
Think of the OS like a building:
- Structure determines how strong, maintainable, and safe it is.

---

## 2. Operating System Structures

### **2.1 Monolithic Kernel**
All OS services run in **kernel mode**.

Examples:  
- Traditional UNIX  
- Linux  

Characteristics:
- All components share the same memory  
- Fast because everything is close together  
- Hard to maintain (changing a small part can break everything)

Analogy:  
A huge open hall where everyone works together.  
Fast communication, but chaos if something goes wrong.

---

### **2.2 Layered Architecture**
OS is divided into multiple layers:
1. Hardware  
2. Kernel core  
3. Device management  
4. File systems  
5. Applications  

Each layer can only use the layer below.

Pros:
- Easy debugging  
- More structured  

Cons:
- Slower due to strict layer rules

Analogy:  
Multi-storey building: each floor has a job, and you can only go one floor down at a time.

---

### **2.3 Microkernel**
Only essential services run inside the kernel:
- Interprocess communication (IPC)  
- Basic scheduling  
- Low-level memory management  

Everything else runs in **user mode**:
- Device drivers  
- File system  
- Network stack  

Pros:
- High security  
- Stable (bugs in user-mode services don’t crash whole OS)

Cons:
- More overhead due to extra communication

Example:  
- Minix  
- QNX  
- Early versions of Mac OS X  

Analogy:  
A small control room (kernel) with essential staff; everyone else works in separate rooms (user mode).  
More organized, less risky.

---

### **2.4 Modular Kernel (Hybrid Kernel)**
A combination of monolithic + microkernel design.

Most modern OS use this.

Example:
- Modern Linux  
- Windows NT architecture  

Kernel is monolithic but supports loadable modules:
- Device drivers  
- File systems  
- Network protocols  

Pros:
- Performance of monolithic  
- Flexibility of microkernel  

Analogy:  
A big hall (monolithic) but with plug-and-play teams that can be added/removed without shutting the system.

---

### 3. Operating System Types

#### **3.1 Batch Operating System**
Jobs are submitted in batches; no user interaction during execution.

Example:  
Early IBM mainframes

Analogy:  
Submitting assignments to a teacher who checks them in bulk at the end.

---

#### **3.2 Time-Sharing OS**
CPU time is divided among users/programs using small time slices.

Example:
- UNIX/Linux  
- Windows  

Analogy:  
A single waiter serving many tables quickly by giving each table a few seconds at a time.

---

#### **3.3 Real-Time Operating System (RTOS)**
Used where timing is critical.

Two types:
- **Hard RTOS** → deadlines must never be missed  
- **Soft RTOS** → rare deadline misses are acceptable  

Examples:
- Aircraft systems  
- Industrial robots  
- Medical monitoring devices  

Analogy:  
A heart surgeon — must react at precise times.

---

#### **3.4 Embedded Operating System**
Used in appliances.

Examples:
- Smartwatches  
- Microwave ovens  
- Smart TVs  

Analogy:  
A highly specialized employee who is trained to do only one type of job, very efficiently.

---

#### **3.5 Multiprogramming OS**
Multiple programs loaded into memory; OS decides which to run.

Goal: maximize CPU utilization.

Analogy:  
Chef cooking multiple dishes in parallel, switching when one is waiting to boil.

---

#### **3.6 Multitasking OS**
Allows a user to run several applications at once.

Analogy:  
Using WhatsApp, Spotify, and Chrome together.

---

#### **3.7 Multiprocessing OS**
Multiple CPUs working together.

Analogy:  
Having multiple cooks in the kitchen to complete tasks faster.

---

#### **3.8 Distributed OS**
Multiple computers appear as one system.

Example:
- Google clusters  
- Hadoop  

Analogy:  
A team of people working together so well that you think it's one single person.

---

# Interrupts and I/O Management (Topic 8)

## 1. Why Interrupts and I/O Matter

Your CPU is extremely fast.  
Your I/O devices (keyboard, mouse, disk, printer) are much slower.

If the CPU had to “wait” for I/O, it would waste huge amounts of time.

Interrupts + I/O management solve this by:
- Allowing devices to notify the CPU when needed
- Allowing the CPU to work on other tasks meanwhile
- Improving overall efficiency

Analogy:  
Instead of staring at the microwave waiting for it to finish, you go do something else until it beeps (interrupts you).

---

## 2. What is an Interrupt?

An interrupt is a **signal** sent to the CPU that something needs attention.

When an interrupt occurs:
1. CPU pauses its current task  
2. Saves its state (in PCB)  
3. Executes interrupt handler  
4. Returns to previous task  

Analogy:  
You’re studying, and your phone buzzes.  
You pause, check the message, then return to studying.

---

## 3. Types of Interrupts

### **3.1 Hardware Interrupts**
Generated by hardware devices.

Examples:
- Keyboard key pressed  
- Mouse moved  
- Disk I/O completed  

Analogy:  
The doorbell rings — an external event interrupts you.

---

### **3.2 Software Interrupts**
Triggered by CPU instructions.

Example:
- System calls (e.g., read/write)  
- Exceptions (divide-by-zero)

Analogy:  
You interrupt yourself because you need something — like pausing study to get water.

---

### **3.3 Internal Interrupts (Exceptions)**
Caused by errors:
- Overflow  
- Invalid memory access  
- Illegal instruction  

Analogy:  
Making a mistake while solving a problem so you stop and correct it.

---

## 4. Interrupt Handling (Interrupt Service Routine – ISR)

Steps:
1. Device sends interrupt request  
2. CPU stops current task  
3. Saves program counter  
4. Jumps to ISR  
5. Handles device request  
6. Restores previous state  
7. Continues normal work  

This is similar to how context switching works.

Analogy:  
A firefighter drops whatever he's doing, responds to the alarm, fixes the issue, and returns.

---

## 5. Maskable vs Non-Maskable Interrupts

### **Maskable Interrupts**
Can be ignored (masked) by CPU if needed.

Example:
- Keyboard

### **Non-Maskable Interrupts**
Cannot be ignored. Usually critical.

Example:
- Hardware failure  
- Power failure alerts

Analogy:  
Ignoring a phone notification vs. having a fire alarm that cannot be turned off.

---

## 6. I/O Techniques

How the CPU interacts with devices.

---

### **6.1 Programmed I/O**
CPU actively checks device status (polling).

Pros:
- Simple

Cons:
- CPU wasteful, frequently checking

Analogy:  
Constantly checking the microwave every 5 seconds.

---

### **6.2 Interrupt-Driven I/O**
Device sends an interrupt when ready.

Pros:
- CPU free for other work  
- Much faster in practice

Cons:
- Interrupt overhead

Analogy:  
Microwave beeps when done — no need to check.

---

### **6.3 Direct Memory Access (DMA)**
DMA controller transfers data directly between memory and device  
**without involving the CPU**.

CPU only gives:
- Starting address  
- Length  
- Direction  

Then switches to other tasks.

Pros:
- Fastest method  
- Minimal CPU involvement  

Analogy:  
You ask a helper to move 20 books from one room to another.  
You don’t do it yourself — you give instructions and go do something else.

---

## 7. Disk Structure Concepts

### **Tracks**
Circular paths on disk surfaces.

### **Sectors**
Smallest storage unit inside a track.

### **Cylinders**
Vertical stack of tracks across disks.

Analogy:  
Imagine a layered cake:
- Each layer = track  
- Each slice = sector  
- Stack of slices across layers = cylinder

---

## 8. Seek Time, Rotational Latency, Transfer Time

### **Seek Time**
Moving the disk head to the correct track.

### **Rotational Latency**
Waiting for the sector to rotate under the head.

### **Transfer Time**
Reading data after alignment.

Analogy:  
Finding a page in a book (seek), turning it to face you (latency), then reading it (transfer).

---

