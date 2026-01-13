---
updated_at: 2025-08-26T14:34:35.142+05:30
edited_seconds: 890
---
#OS 

# Direct Communication
	- Processes must name each other explicitly
		- send (P, message) - send a message to Process P
		- recieve (Q, message) - recieve a message from Process Q
	- Properties of communication link
		- Links are established automatically
# Buffering 
	- Queue is made in 3 ways
		- Zero Capacity      - No messages wait in the queue (Sender must wait for reciever [Rendezvous])
		- Bounded Capacity   - finite length of "n" messages (sender might have to wait if queue is full)
		- Unbounded Capacity - infinite length (sender never waits)
# Communication in Client and Server
	- Sockets:                         End-point Connectivity [uses IP and MAC Address]
	- Remote Procedure Calls:          Server location is not made available; server sends data after initialization
	- Remote Method Invocation (Java): Invokes the Remote Method
# Sockets
	- A Socket is defined as an endpoint for connectivity
# Remote Procedure Calls
	- RPC abstracts procedure calls b/w processes on networked systems
		- Again, uses ports for service differentiation
	- Stubs - client-side proxy for the actual procedure on the server
	- The client - side stub locates the server and marshalls the parameters
	- the server-side stub recieves this message
# Pipes
	- Acts as a conduit allowing 2 processes to communicate
	- Issues: 
		- Is communication uni-or bi-directional?
		- In the case of 2-way communication, is it half or full-duplex?
		- Must there exist a relationship (i.e, parent-child) b/w the communication processes?
		- Can pipes be used over a network?
	- Ordinary Pipes - Cannot be accessed through different networks
	- 2 types of Pipes - Read and Write Pipes
# Threads
	- Threads are light-weight
	- 3 types: 1-1, many-1, many-many
# Multi-core Programming
	- Multi-core ro multi-processor systems putting pressure on programmers, challenges include:
		- Dividing activities
		- Balance
		- Data Splitting
	- Types of parallelism -Data Parallelism - Distributes subsets of the same data across multiple cores, each thread performing unique operation
# Concurrency vs Parallelism
	- Concurrent execution on single core system:
	- Parallelism on a multi-core system:
![[Drawing 2025-08-25 15.40.14.excalidraw]]



# Amdahl's Law
	- speedup <= 1/(s+(1-S)/N)
# User Threads and Kernel Threads
	- User threads - Management done by user-level threads library 
# Pthreads
	- May be provided as user or kernel level
	- POSIX (IEEE 100.3 IE)
# Java Threads
	- Java threads threads are managed by the JVM
	- Typically implemented using the threads model
	- Java threads may be created by
```Java
public interface Runnable{
	public abstract void run();
}
```
	- Extending Thread Class
	- Implementing the runnable interface
# Implicit Threading
	- Growing in popularity as numbers of threads increase, program corrrectness more difficult with explicit threads
	- Creation and management of threads done by compilers and run-time libraries rather than programmers
	- Three methods explored
		- Thread pools
		- OpenMP
		- Grand Central Dispatch
	- Other methods include Microsoft Threading Building Blocks (TBB), java.util.concurrent package
# What the AI spat out
Here's a structured explanation:

## I. Process Communication

1.  **Direct Communication:**
    *   This refers to methods where processes explicitly call functions on each other to send or receive messages.
    *   **Key Points:** It requires processes to know each other's identifiers (names).
        *   `send(P, message)`: The calling process sends a message directly to process P. Synchronization happens here.
        *   `receive(Q, message)`: A process receives a message from another specific process Q. This operation often blocks until a message arrives.
    *   **Simplicity vs Complexity:** It's conceptually simpler than using intermediaries (like mailboxes), but it ties processes directly together.

2.  **Buffering:**
    *   Buffering manages the flow of messages between communicating processes, addressing potential mismatches in speed or availability (sender busy).
    *   The document mentions three ways this is done:
        *   `Zero Capacity`: No buffer exists. Sender sends a message and immediately waits for the receiver to acknowledge it (`receive`). This ensures immediate receipt but requires coordination.
        *   `Bounded Capacity`: A fixed-size queue holds messages between sender and receiver (n messages). If the queue is full, the sender may be blocked until space is available.
        *   `Unbounded Capacity`: Theoretically infinite capacity for the message buffer. Sender can always send without waiting; however, this might hide performance issues or lead to resource exhaustion if not managed properly.

3.  **Client-Server Communication:**
    *   Sockets and RPC are two common models discussed.
    *   **Sockets:** Provide network endpoint connectivity (using IP addresses) but don't inherently dictate the communication model beyond that basic connection. They allow processes on different machines to communicate.
    *   **Remote Procedure Calls (RPC):** This is a specific mechanism for client-server interaction where:
        *   The server's location isn't explicitly told the client; instead, it uses its network address.
        *   When the client makes an RPC call ("call procedure X"), it sends a request to the server. The server executes the procedure (or invokes a remote method) and sends back the result.

## II. Specific Communication Models

4.  **Sockets:**
    *   Clarified definition: A socket is indeed one or more communication endpoints, typically providing two-way connections over networks.
    *   It uses protocols like TCP/IP for reliable communication (establishing a connection first) and UDP for unreliable but faster communication.

5.  **Remote Procedure Calls (RPC):**
    *   Explained the abstraction (`receive message → procedure execution`).
    *   Mentioned stubs: Client-side code that mimics the server's function call, handles network details like locating the server and formatting data.
    *   Server-side stub: Receives the formatted request from the client, executes the actual procedure, and sends back the result.

6.  **Pipes:**
    *   A conduit (channel) for communication between two processes.
    *   The questions raised are crucial:
        *   `Uni or Bi-directional?`: Pipes can be half-duplex (one-way flow in one direction at a time, like reading from stdin while writing to stdout on the same pipe) or sometimes used unidirectionally. Rarely truly bidirectional simultaneously.
        *   `Half or Full Duplex?`: Half-duplex allows only one way of communication at a time over the single channel (like a chat). Full duplex would allow simultaneous sending and receiving, but standard pipes don't support this well unless using two separate pipe pairs.
        *   `Parent-child relationship?`: Traditionally, Unix pipes are used between parent and child processes. However, named pipes can be accessed by unrelated processes on the same system if they agree on the name.
        *   `Can pipes be used over a network?`: Standard unnamed pipes (like `/pipe`) cannot travel across networks. Network communication requires Sockets or other inter-process communication mechanisms designed for it.

## III. Process Models and Concurrency

7.  **Threads:**
    *   Defined as lightweight processes, sharing the same memory space.
    *   Less overhead than creating separate kernel-level processes compared to using `fork()` in Unix-like systems (if context switching is considered).
    *   Mentioned thread models:
        *   Many-to-One (`many-1`): Multiple user threads map to a single kernel thread. Good for I/O bound tasks but can be blocked if the single kernel thread gets stuck.
        *   One-to-One: Each user thread corresponds directly to one kernel thread (good isolation, full parallelism on multi-core systems). Can lead to high overhead and resource usage.
        *   One-to-Many (`1-many`): Many kernel threads map to a single process. Useful for I/O multiplexing but can saturate the system with too many kernel threads.

8.  **Multi-core Programming:**
    *   Discusses challenges when designing software for systems with multiple processing cores.
        *   `Dividing activities`: Splitting tasks into pieces that can be run concurrently (this is parallelism).
        *   `Balance`: Distributing the workload evenly across all available cores to avoid bottlenecks.
        *   `Data Splitting`: Breaking data sets so different threads/cores work on disjoint parts simultaneously.

9.  **Types of Parallelism:**
    *   Explicitly mentions Data Parallelism, where identical operations are performed concurrently by multiple processes/threads on different subsets (or copies) of the same dataset. This is a common approach for tasks like image processing or matrix multiplication.
    *   `Task Parallelism`: Performing different operations concurrently is also important, though less explicitly mentioned here.

## IV. Concurrency vs Parallelism

10. **Concurrency:** The ability to deal with multiple activities at once (they overlap in time). On a single-core machine, this typically involves rapidly switching between tasks (`Time-sharing`). It ensures responsiveness and resource sharing even if the core is still executing one task at a fundamental level.
11. **Parallelism:** Performing computations or operations simultaneously using two or more processors/cores (`True parallel execution`).
    *   Concurrency can exist on single-core systems (managing multiple I/O requests, user interactions), while Parallelism requires multi-core hardware.

## V. Performance Law

12. **Amdahl's Law:**
    *   This law provides a theoretical speedup limit for a task when parts of it are parallelized.
    *   Formula breakdown:
        *   `S`: Fraction of the original execution time that is serial (non-parallelizable). Closer to 0% allows greater potential speedup. Higher `%` means less benefit from parallelism.
        *   `(1-S)`: Fraction that can be parallelized (`Parallelizable fraction`). A larger portion makes Parallelism more impactful.
        *   `N`: Number of processors or cores used in the parallel part. More cores (or faster ones) improve speedup, but it's limited by `(1-S)`.

## VI. Implementation Models

13. **Pthreads:**
    *   The POSIX standard for threads (`IEEE 1003`). It allows C/C++ programs to create and manage threads.
    *   Can be implemented as user-level threads (handled entirely by the Pthread library without kernel involvement) or as a combination of user and kernel threads.

14. **Java Threads:**
    *   Java manages its own threads within the `JVM`.
    *   The standard way involves creating separate kernel threads for each Java thread, enabling true OS-level parallelism if multiple cores exist (One-to-One model).

## VII. Implicit Threading

15. **Growth and Challenge:** This is a trend where systems manage concurrency automatically or through higher-level libraries/compilers (`Time-sharing`). While this simplifies programming, it can make correctness harder to grasp when threads are managed implicitly rather than explicitly by the programmer.

    *   `Thread pools`: Reuse a set of pre-created threads for managing tasks submitted to them. The programmer doesn't create and destroy threads.
    *   `OpenMP`: An API for multi-platform shared-memory parallel programming, often used with pragmas in C/C++/Fortran code to indicate parallel regions or loops.
    *   `Grand Central Dispatch (GCD)`: An Apple framework that manages a pool of OS-managed threads and allows programmers to submit tasks to be scheduled automatically.

## VIII. Other Models Mentioned

16. **Microsoft TBB** (Threading Building Blocks): A C++ library for task-based parallelism, often used implicitly by the programmer.
17. **Java `util.concurrent` package**: Provides a wide range of classes and interfaces supporting multi-threading in Java.

## Summary

The notes provide an overview of different ways processes communicate directly or indirectly (via buffering/queues). They then differentiate between concurrency (managing multiple tasks sequentially) and parallelism (executing multiple tasks truly at the same time on distinct processors). Various threading models (`User`, `Kernel`) are described, along with how they map onto operating system resources. The challenges of multi-core programming are acknowledged, leading to an explanation of data parallelism as one solution. Finally, Amdahl's Law quantifies the maximum speedup achievable by parallelization, and several ways programs can utilize threads (including user-level libraries like Pthreads/Java, kernel interaction via JVM on Java, explicit thread management APIs like OpenMP/GCD) are outlined.

The header (`---`) indicates this was an updated markdown file ("OS Notes") with metadata about the last update time.