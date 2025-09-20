---
updated_at: 2025-08-26T15:40:34.262+05:30
edited_seconds: 430
---
#OS 
- Thread is the smallest execution of a program
- Is managed by the JVM (Java Virtual Machine)
# Thread Pools
	- Create a number of threads in a pool where they await work
	- Advantages
		- Usually slightly faster to service a request with an existing thread than create a new thread
		- Allows the number of threads in the application(s) to be bound to the size of the pool
		- Seperating task to be performed from mechanics of creating task allows different strategies for running tasks
			- i.e. Tasks could be scheduled to run periodically
	- Windows API supports threads pools
```Java
DWORD WINAPI PoolFunction(AVOID Param){
	/*
	*this function runs as a seperate thread
	*/
}
```
# Threading Issues
	- Semantcs of fork() and exec() system calls
	- Signal handling
		- Sync and Async
	- Thread Cancellation of target thread
	- Scheduler Activations
# Operating Systems Threads
	- Windows Threads
	- Linux Threads
# Critical Section Problem
	- Mutual Exclusion - If process Pi is executing in its critical section, then no other processes can be executing in their critical points
# Peterson's Soln.
# acquire() and release()
```Java
acquire(){
	while (!available);
		/* busy wait */*
		available -false;
	}
}
release(){
	available = true;
}
do{
	acquire lock
		critical section
}
```

# Resuming Processing within a monitor
	- If several processes queued on condition x, and x. signal() executed, which should be resumed?
	- FCFS frequntly not adequate
	- conditional-wait construct of the form x.wait(c)
		- where c is priority number
		- Process with lowest number (highest proirity) is scheduled next
