#OS 
# Operations on Processes
	- System must provide mechanisms for:
		- Process Creation
		- Process Termination
		- and so on as detailed next
# Process Creation
	- Parent process create child processes, which in turn create other processes, forming a tree of processes
	- Generally, process identified and managed bau a process identifier (pid)
	- Resource sharing Options
		- Parent and children share all resources
		- Children share subset of parents' resources
		- Parent and Child share no resources
	- Execution Options
		- Parent and children execute immediately
		- Parent and children execute seperately
		- Tree of Parent Process ---> looks like Factor Tree
		- C Program for forking Seperate Processes
# Process Termination
	- Process executes last statement and then asks the operating system to delete it using the exit() system call.
		- Returns status data from child to parent (via wait() )
		- Process' resources are deallocatedly by operating system
	- Parent may terminate the execution of children processes using abort()
	- Some opersting Systems don't allow the parent process to be terminated without the children processes being terminated FIRST.
		- Cascading termiation
		- Termination is initiated by OS
# Multi-Process Architecture - Google Chrome Browser
	- Mant Web Browsers ran as single process (some still do)
		- If one web site causes trouble, entire browsers can hang or crash
	- Google Chrome is a multi-process with 3 different types of processes
		- Browser process manages user interface, disk and network I/O
		- Renderer Process renders web pages, deals with HTML, JavaScript. A new renderer created for each website opened
		- Runs in Sandbox restricting disk and network I/O, minimizing effect of security exploits
# Inter-Process Communication
	- Process within a system may be independent or cooperating
	- Co-op Process can affect or be affected by other processes, including sharing data.
	- Independent Process cannot be affected or be affected by execution of another process
	- Advantages of Process Co-op
		- Information Sharing
		- Computation Speed-Up
		- Modularity
		- Convenience
# Producer-Consumer Problem
	- Paradigm for co-op processes, producer produces information thst is consumed by a consumer process
		- Unbounded-buffer places no practical limit on the size of the buffer
		- Bounded-buffer assumes that there is a fixed biffer size
# Bounded-Buffer - Producer
```c
item next_produced;
while (true){
	/*Produce an item in next oroduced */
	while ((in+1))
}
```

