---
updated_at: 2025-09-18T14:30:09.085+05:30
edited_seconds: 240
---
## 1) Process states, schedulers, creation & termination

**Frequency:** 3

**Full question (standardized):**  
_With the help of a neat process-state diagram, explain how an operating system manages multiple processes. Describe the roles of the long-term, short-term, and medium-term schedulers. Also explain process creation and termination events._

**Step-by-step answer:**

1. **Process states & diagram**
    
    - States: **New → Ready → Running → Waiting → Terminated** (with possible Suspended-Ready / Suspended-Waiting).
        
    - **Transitions:**
        
        - New→Ready (admitted by long-term scheduler)
            
        - Ready→Running (CPU dispatch by short-term scheduler)
            
        - Running→Waiting (I/O or event wait)
            
        - Waiting→Ready (event completes / I/O done)
            
        - Running→Ready (preemption—time slice expires or higher priority ready)
            
        - Running→Terminated (normal exit or fatal error)
            
2. **Schedulers**
    
    - **Long-term (job scheduler):** Controls _degree of multiprogramming_ (how many jobs admitted).
        
    - **Short-term (CPU scheduler/dispatcher):** Picks next ready process frequently; implements policy (FCFS, SJF, RR, Priority, MLFQ).
        
    - **Medium-term (swapper):** Temporarily removes processes from memory (suspend) and re-admits them to balance memory/CPU.
        
3. **Process creation**
    
    - Allocate **PCB** (PID, state, PC, registers, page tables, open files, accounting).
        
    - Initialize address space (load program), set **PC** to entry, place in **Ready** queue.
        
    - Examples: **UNIX** `fork()` (copy PCB/VM) + `exec()` (overlay image); **Windows** `CreateProcess`.
        
4. **Process termination**
    
    - **Normal exit** (status), **error/abort**, **killed** by another process/OS, or **parent exit** cascading to children (policy-dependent).
        
    - OS deallocates resources, closes files, frees memory, removes PCB.
        

---

## 2) Multithreading in multicore + thread models + web-server example

**Frequency:** 3

**Full question (standardized):**  
_Discuss the importance of multithreading for multicore systems. Compare the many-to-one, one-to-one, and many-to-many thread models. Using a web server as an example, contrast single-threaded and multithreaded designs._

**Step-by-step answer:**

1. **Why threads on multicore:**
    
    - Exploit **parallelism** across cores; hide I/O latency; improve **throughput** and **responsiveness**; reduce per-unit memory vs processes.
        
2. **Thread models:**
    
    - **Many-to-One (user->one kernel thread):** Very low overhead; **no true parallelism**; a blocking system call stalls all threads.
        
    - **One-to-One:** Each user thread maps to a kernel thread; **true parallelism**; higher create/switch overhead and limits may apply.
        
    - **Many-to-Many:** Many user threads multiplexed over a pool of kernel threads; balances parallelism and overhead; more complex runtime.
        
3. **Web server design:**
    
    - **Single-threaded:** One request at a time; simple but poor concurrency (CPU idle during I/O).
        
    - **Multithreaded:** One thread per connection or a worker pool; overlaps disk/network I/O; scales with cores; careful **synchronization** needed for shared caches/logs.
        
4. **Key trade-offs:** scheduling control, blocking behavior, context-switch cost, and runtime complexity.
    

---

## 3) Producer–Consumer (bounded buffer) with semaphores

**Frequency:** 2

**Full question (standardized):**  
_Write the pseudocode for the bounded-buffer producer–consumer problem using semaphores, ensuring mutual exclusion and avoidance of buffer overflow/underflow._

**Step-by-step answer (classical solution):**

```pseudocode
// buffer size = N 
semaphore empty = N;   
// count of empty slots semaphore full  = 0;   
// count of full  slots semaphore mutex = 1;   
// binary, guards buffer  producer() {   
	while (true) {     i
		tem x = produce();     
		wait(empty);       
		// wait for an empty slot     
		wait(mutex);       
		// enter critical section     
		insert(x);         
		// put x into buffer     
		signal(mutex);     
		// leave critical section
		     signal(full);      
		     // one more full slot
	   }
	}  consumer() {   
		while (true) {     
			wait(full);        
			// wait for a full slot     
			wait(mutex);       
			// enter critical section     
			item y = remove(); 
			// take from buffer     
			signal(mutex);     
			// leave critical section     
			signal(empty);     
			// one more empty slot     
			consume(y);   
		} 
	}
```

- **Correctness:** `mutex` ensures **mutual exclusion**; `empty/full` enforce **bounds** (no overflow/underflow); absence of deadlock since ordering of waits/signals is consistent.
    

---

## 4) Context switching between two processes

**Frequency:** 2

**Full question (standardized):**  
_A system alternates between two processes, P1 and P2. Explain why context switches occur, enumerate the steps of a context switch, and discuss overhead and its impact on CPU utilization._

**Step-by-step answer:**

1. **Why switches occur:**
    
    - **Preemption** (time slice ends / higher priority ready), **blocking** (I/O wait), or **synchronization** events.
        
2. **Steps of a context switch:**
    
    - Save running process **CPU context** (PC, registers, flags) into its **PCB**.
        
    - Update its state (**Running→Ready** or **Running→Waiting**).
        
    - Choose next process from **Ready** queue (scheduler policy).
        
    - Load next process context from its PCB; set **MMU** state (page tables); **dispatch**.
        
3. **Overhead & impact:**
    
    - Time with **no useful work**; too-small quanta increase overhead; tune via **time slice** and scheduler policy.
        
    - Reduce switch cost: minimize kernel crossing, avoid unnecessary preemptions, favor cache locality.
        

---

## 5) IPC: message passing vs shared memory (+ pitfalls)

**Frequency:** 2

**Full question (standardized):**  
_Explain interprocess communication via message passing and shared memory. Compare them and discuss issues such as message loss, blocking vs non-blocking semantics, and buffer overflow, and how to mitigate them._

**Step-by-step answer:**

1. **Message passing:**
    
    - **send/receive** via OS; can be **direct** (to PID) or **indirect** (mailboxes/ports).
        
    - **Blocking (sync)** simplifies flow control; **non-blocking (async)** improves overlap but needs app-level buffering.
        
    - **Mitigations:** acknowledgments/retries (loss), bounded mailbox + back-pressure (overflow), timeouts/select (deadlock avoidance).
        
2. **Shared memory:**
    
    - Processes map a **common region**; data exchange is memory speed.
        
    - Requires **synchronization** (mutexes/semaphores/monitors) to prevent races.
        
    - **Mitigations:** design lock protocol (e.g., producer–consumer), use **lock-free** structures when appropriate.
        
3. **Trade-offs:**
    
    - Message passing: simpler isolation, higher OS overhead.
        
    - Shared memory: fastest data path, but correctness relies on robust locking.
        

---

## 6) PCB contents + Amdahl’s Law

**Frequency:** 1

**Full question (standardized):**  
_(a) List the contents of a Process Control Block (PCB) and explain how the PCB supports context switching. (b) State Amdahl’s Law and compute speedup for a given parallel fraction and number of cores, interpreting the result._

**Step-by-step answer:**

1. **PCB contents:** PID, state, **PC**, registers, stack pointer, **MMU** data (page table base), scheduling info (priority, CPU time), open-file table pointers, signals, accounting/quotas.
    
    - **Role:** The OS saves/restores this context during a switch, making execution resumable.
        
2. **Amdahl’s Law:**
    
    - **Speedup** $$
S(N) = \frac{1}{(1 - P) + \frac{P}{N}}
​$$, where PPP is parallel fraction, NNN cores.
        
    - **Example:** P=0.9P=0.9P=0.9, N=4N=4N=4 → S=1/(0.1+0.9/4)=1/(0.1+0.225)=1/0.325≈3.08S = 1 / (0.1 + 0.9/4) = 1 / (0.1 + 0.225) = 1 / 0.325 \approx 3.08S=1/(0.1+0.9/4)=1/(0.1+0.225)=1/0.325≈3.08.
        
    - **Interpretation:** Diminishing returns due to the serial part 1−P1-P1−P.
        

---

## 7) Peterson’s solution (2-process mutual exclusion)

**Frequency:** 1

**Full question (standardized):**  
_Present Peterson’s algorithm for two processes and prove that it satisfies mutual exclusion, progress, and bounded waiting. State its assumptions._

**Step-by-step answer:**

1. **Algorithm (for processes `i` and `j`, `i≠j`):**
    

`// shared bool flag[2] = {false, false}; int turn = 0;  do {   flag[i] = true;   turn = j;   while (flag[j] && turn == j) { /* busy wait */ }   // critical section   flag[i] = false;   // remainder section } while (true);`

2. **Assumptions:** atomic reads/writes to `flag` and `turn`; strict alternation not required; only **two** processes.
    
3. **Mutual exclusion:** Both cannot be in CS simultaneously: if both want CS, `turn` equals one of them; that one waits while the other enters (contradiction if both inside).
    
4. **Progress:** If one not interested (`flag[j]=false]`), the other doesn’t wait.
    
5. **Bounded waiting:** Turn variable ensures each waiting process will eventually proceed after the other resets `flag`.
    

---

## 8) Quad-core utilization, mutex locks, and Test-and-Set implementation

**Frequency:** 1

**Full question (standardized):**  
_(a) Explain how to exploit a quad-core CPU using multithreading. (b) Define a mutex lock and implement a simple spinlock using an atomic Test-and-Set (or Compare-and-Swap). (c) Discuss busy waiting vs blocking and how to reduce contention._

**Step-by-step answer:**

1. **Exploiting 4 cores:** decompose work into ≥4 runnable threads; avoid serial bottlenecks; partition data to improve cache locality; minimize false sharing; use work-stealing pools for imbalance.
    
2. **Mutex & TAS spinlock:**
    

`// Atomic primitive (conceptual) bool TestAndSet(bool *addr) {   bool old = *addr;   *addr = true;   return old; }  // Spinlock bool lock = false;  void acquire() {   while (TestAndSet(&lock) == true) { /* spin */ } }  void release() {   lock = false; }`

- **CAS version (pseudo):**
    

`// while(!CAS(&lock, false, true)) { /* spin */ }`

3. **Busy waiting vs blocking:**
    
    - **Spin**: good for very short critical sections under light contention; wastes CPU if waits are long.
        
    - **Blocking** (`futex`, semaphores, condition variables): OS parks the thread; better under heavy contention/long waits.
        
    - **Contention reduction:** backoff (TTAS + exponential backoff), sharded locks, finer-grained locking, lock-free structures, critical-section shortening.
        

---

# Frequency summary (most → least)

1. Process states/schedulers/creation-termination — **3**
    
2. Multithreading + models + web-server — **3**
    
3. Producer–Consumer (bounded buffer) — **2**
    
4. Context switching — **2**
    
5. IPC: message passing vs shared memory — **2**
    
6. PCB + Amdahl’s Law — **1**
    
7. Peterson’s solution — **1**
    
8. Quad-core + mutex + Test-and-Set — **1**