---
updated_at: 2025-11-03T12:08:02.087+05:30
edited_seconds: 330
---
#COA 
# Parallelism: Needs, types, applications and challenges
- Executing 2 or more operations at the same time
2 types:
- Hardware Parallelism
- Software Parallelism
## Hardware Parallelism
- One way to characterize the parallelism in a processor is by the number of instruction issues per machine cycle.
- using 2 issue processor:
	- The processor can execute one memory access (load or store) and 1 arithmetic operation (multiply , add, subtract) simultaneously.
	- The Program must execute in 7 cycles.
	- The h/w parallelism average is 8/7 = 1.14

## Software Parallelism
- It is defined by the control and data dependence of programs.
- It varies based on the complexity of the program
Types:
- Instruction level parallelism