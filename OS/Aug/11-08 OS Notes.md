#OS 
# Process Management
## Processes
	- Process Concept
	- Process Scheduling
	- Operations on Processes
	- Interprocess Communication (IPC)
	- Examples of IPC System
	- Communication in Client-Server Systems
## Objectives
	- To introduce the notion of a process - a program in execution, which forms the basis of all computation
	- To describe the various features of processes, including scheduling, creation and termination, and communication
	- To explore interprocess communication using shared memory and message passing
	- To descirbe communication in client-server systems
## Process Concept
	- An operating system executes a variety of programs:
		- Batch system - jobs
		- Time-shared systems - user programs or tasks
	- Textbooks use the term *job* and *process*
	- Process - a program in execution; process execution must progress in sequential fashion
	- Multiple parts
		- The program code, also called text selection
		- Current activity including program counter, processor registers
		- Stack containing temporary data
			- Function parameters, return address, local variables
		- Data section containing global variables 
		- Heap
		- Program is stored passively in the desk (executable file), process is active
			- Program becomes process when execitable file is loaded into memory
## Process State
	- New       : Process is being created
	- Running   : Instruction to be executed
	- Waiting   : The process if waiting for some event to occur
	- Ready     : The process is waiting to be assigned to a processor
	- Terminated: The process finished execution
## Process Control Block (PCB)
	- Process State         : Running, waiting, etc
	- Program Counter       : Location of instruction to next execute
	- CPU Registers         : Contents of all process centric registers
	- CPU Scheduling Info   : Priorities, Scheduling queue pointers
	- Memory-management Info: Memory allocated to the process
	- Accounting Info       : CPU used, clock time elapsed since start,time limits 
	- I/O Status Info       : I/O Devices allocated to process, list of open files
## Threads
	- So far, process has a single thread of execution
	- Consider having multiplie program counters per process
	- Multiple locations can execute at once
		- Multiple threads of control -> threads
	- Must then have storage of thread details, multiple program counters in PCB 
	- See next chapter
## Process Scheduling
	- Maximize CPU use, quickly switching processes onto CPU for time sharing
	- Process Scheduler selects among available processes for next execution on CPU
	- Maintains scheduling queue of processes
		- Job Queue    - Set of all processes in the system
		- Ready Queue  - Set of all processes residing in main memory, ready and waiting to be executed
		- Device Queue - Set of processes waiting for an I/O Device
		- Processes migrate among the various queues
## Schedulers
	- Short-term Schedulers (or CPU-Schedulers) - selects which process should be executed next and allocates CPU
		- Sometimes the only scheduler in a system
		- Short-term scheduler is invoked frequently (in milliseconds) => (Must be fast)
	- Long-term Schedulers (or Job-Schedulers) - selects which processes should be brought to the ready queue
		- Long-term scheduler is invoked infrequently (seconds, minutes) => May be slow
		- The long-term scheduler controls the degree of multi-programming
	- Processes can be dexribed as either:
		- I/O bound process - Spends more time doing I/O than computations, many short CPU bursts
		- CPU bound process - Spends more time doing computations; very few long CPU bursts
		- Long-term Scheduler strives for good process mix