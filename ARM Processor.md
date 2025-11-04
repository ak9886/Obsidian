---
updated_at: 2025-11-04T14:41:12.917+05:30
edited_seconds: 510
---
#COA 
# ARM Core Dataflow Model
## Introduction
- An ARM Core has functional units connected by data buses.
- Data enters the processor core through the _data_ bus. the data may be an instruction to execute or a data item.

## ARM Registers
- General purpose registers hold either data or an address.
- Protected mode usually used when executing applications
- The ARM Processor has 3 registers assigned to a particular task or special function: *r13, r14* and *r15*. They are frequently given different labels to differentiate them from the other registers
- Shaded Registers usually identify the assigned applets
## Multi-core CPU Chip
- Cores run in parallel
- Threads are parallel
- Within each core, threads are time-spaced
## Instruction Encoding
- Remember that in a stored program computer, instructions are stored in memory (just like data)
- Each instruction is fetched (according to the address specifiecd in the PC), decoded and executed in the CPU.
- The ISA Defines the format of an instruction (syntax) and its meaning
- An ISA will define a number of different instruction formats.
- Each format has different fields
- 
### MIPS Instruction Encoding
- All instructions are thee same size (32 bits = 1 word)
- 
