---
updated_at: 2025-11-03T19:41:45.047+05:30
edited_seconds: 100
---
#COA 
Source: [[Unit 4.pdf]] and [[Unit 5.pdf]]

## **UNIT 4 – BASIC PROCESSING UNIT AND PIPELINING**

The **basic processing unit** of a computer performs arithmetic, logic, data movement, and control operations necessary for instruction execution. It is made up of components like the **Arithmetic Logic Unit (ALU)**, **registers**, **buses**, and **control logic**. Together, these elements manage the **fetch–decode–execute cycle**, which forms the heart of all CPU activity.

### 1. **Instruction Execution Cycle**

Every program is a sequence of machine instructions. The **processor** executes one instruction at a time by fetching it from memory, decoding it, executing the required operation, and storing the result. The **Program Counter (PC)** holds the address of the next instruction to be fetched. The **Instruction Register (IR)** temporarily stores the current instruction being executed.

The execution involves:

- **Fetch:** The processor reads the instruction from memory into IR.
    
- **Decode:** The control unit interprets the instruction.
    
- **Execute:** The ALU performs the operation using registers and memory operands.
    
- **Store:** The result is written back to the destination register or memory.
    

---

### 2. **Single-Bus Organization**

In a simple processor, all data transfers take place over a **single bus** shared among components such as:

- **Registers (R0–Rn):** General-purpose and special-purpose registers.
    
- **MAR (Memory Address Register):** Holds the address to access memory.
    
- **MDR (Memory Data Register):** Temporarily stores data read from or written to memory.
    
- **ALU:** Performs arithmetic and logical operations.
    
- **Control Logic:** Generates control signals for data movement.
    

The single bus introduces sequential data transfers — only one transfer can happen per clock cycle. Control signals like _Riin_, _Riout_, _Add_, _Read_, and _Write_ coordinate this process.

Example:  
To transfer data from R1 to R4,

```
R1out = 1, R4in = 1
```

This places R1’s contents on the bus and loads it into R4.

---

### 3. **ALU Operations**

The **ALU** is a combinational circuit with no storage of its own. It takes two inputs (A and B), performs an operation (Add, Subtract, AND, OR, etc.), and outputs the result into a temporary register, usually **Z**.  
For example, to compute R3 = R1 + R2:

1. `R1out, Yin`
    
2. `R2out, SelectY, Add, Zin`
    
3. `Zout, R3in`
    

Here, **Y** temporarily holds one operand, and **Z** stores the result of ALU operations.

---

### 4. **Memory Operations**

**Fetching a word** from memory involves these steps:

1. MAR ← [R1]
    
2. Initiate memory read
    
3. Wait for **Memory Function Complete (MFC)** signal
    
4. MDR ← Data from memory bus
    
5. R2 ← [MDR]
    

**Storing a word** reverses this process:

1. MAR ← [R1]
    
2. MDR ← [R2]
    
3. Issue write command
    

These operations synchronize using control signals like `Read`, `Write`, and `WMFC` (Wait for MFC).

---

### 5. **Branch Instructions**

A **branch** modifies the **Program Counter** to jump to a non-sequential memory address.  
If the offset is X,  
`PC ← PC + X`  
Branches can be **conditional** (executed only if a condition is true) or **unconditional** (always executed).

---

### 6. **Multiple Bus Organization**

While a single-bus system is simple, it allows only one transfer per cycle. To increase speed, processors adopt **multi-bus architectures**, commonly three buses:

- **Bus A & B:** Supply operands to the ALU.
    
- **Bus C:** Carries the result back to registers.
    

This allows simultaneous register read and write in one cycle, greatly improving throughput. A **register file** with multiple ports supports this design.

---

### 7. **Control Unit Design**

The **control unit** generates control signals to manage data flow and operation sequencing.

#### (a) **Hardwired Control**

- Uses combinational logic and finite state machines.
    
- Very fast but inflexible.
    
- Ideal for RISC systems.
    

Control signals depend on:

- Current micro-step (from a step counter)
    
- Instruction bits (from IR)
    
- Condition flags
    
- External inputs (like MFC)
    

#### (b) **Microprogrammed Control**

- Control signals are stored as **microinstructions** in a **Control Store**.
    
- Each instruction’s execution sequence is a **micro-routine**.
    
- Controlled by a **microprogram counter (µPC)**.
    
- Easier to modify but slower than hardwired.
    

Each **Control Word (CW)** specifies which signals should be active during that micro-step. This modular approach simplifies complex instruction sets (CISC).

---

### 8. **Pipelining Concepts**

**Pipelining** is a performance optimization that overlaps instruction execution phases.  
Instead of completing one instruction before starting the next, multiple instructions are processed concurrently in different stages.

#### 4-Stage Pipeline:

1. **Fetch (F)** – Get instruction from memory.
    
2. **Decode (D)** – Interpret and identify operands.
    
3. **Execute (E)** – Perform the operation.
    
4. **Write Back (W)** – Store results.
    

Each stage uses dedicated hardware and runs in parallel, so a new instruction enters the pipeline each clock cycle. Ideally, an n-stage pipeline yields a **speedup factor of n**.

---

### 9. **Pipeline Hazards**

Pipelines are efficient only if uninterrupted. Hazards cause **pipeline stalls**:

1. **Structural Hazards:** Hardware resource conflicts (e.g., shared memory access).
    
2. **Data Hazards:** One instruction depends on another’s result.
    
    - Resolved by _forwarding_ (bypassing) or _stalling_.
        
3. **Control Hazards:** Caused by branch or jump instructions that alter control flow.
    

A **pipeline bubble** (NOP) is inserted to handle these hazards.

---

### 10. **Branch Penalty and Prediction**

Branches disturb the instruction stream and introduce delay.  
**Branch penalty** is the number of cycles lost due to incorrect or delayed branch decisions.

Mitigation strategies:

- **Delayed Branch:** Execute one or more useful instructions after the branch.
    
- **Branch Prediction:** Guess whether a branch will be taken.
    

Prediction types:

- **Static:** Compiler assumes a fixed direction (always taken or not taken).
    
- **Dynamic:** Processor learns from past outcomes using **two-state** or **four-state** algorithms (Strongly Taken, Likely Taken, Likely Not Taken, Strongly Not Taken).
    

---

### 11. **Influence on Instruction Set Design**

- **Simple addressing modes** (register, immediate, base-index) reduce stalls.
    
- **Load/store architectures** (like RISC) separate memory access and computation.
    
- **Conditional flags** should only be modified when necessary to enable instruction reordering by compilers.
    

Complex addressing (like indirect or auto-increment modes) can cause longer pipeline stalls.

---

### 12. **Pipeline Performance**

If the pipeline has _n_ stages, the ideal execution time for _k_ instructions is approximately:

```
T = n + (k – 1)
```

Throughput improves roughly _n_ times, but only if the pipeline remains full and free of hazards.  
Cache memory plays a key role in keeping the pipeline fed with instructions and data at processor speed.

---

## **UNIT 5 – PARALLELISM AND ARM ARCHITECTURE**

### 1. **Introduction to Parallelism**

Parallelism means executing multiple operations simultaneously to increase computational performance. It enhances:

- **Speed** (reduces execution time)
    
- **Throughput** (increases instructions per second)
    
- **Scalability** (enables large problem-solving)
    

Applications include weather forecasting, AI, simulations, genetic engineering, and defense systems.

---

### 2. **Types of Parallelism**

#### (a) **Hardware Parallelism**

Depends on system architecture.

- **Processor Parallelism:** Multiple cores, threads, or CPUs working concurrently.
    
- **Memory Parallelism:** Shared/distributed memory allowing simultaneous access by processors.
    

A _k-issue processor_ can issue _k_ instructions per clock. Multiple such processors in a system create massive parallel instruction streams.

#### (b) **Software Parallelism**

Refers to algorithmic design allowing concurrent task execution.  
Types include:

- **Instruction-level parallelism (ILP)**
    
- **Data-level parallelism (DLP)**
    
- **Task-level parallelism (TLP)**
    
- **Transaction-level parallelism**
    

ILP is achieved via **superscalar** architectures that issue multiple independent instructions per clock cycle.

---

### 3. **Data-Level Parallelism**

DLP distributes data across multiple processors performing the same operation on different data points.  
Example: Summing an array of n elements on 4 processors reduces computation time to roughly `(n/4)*Ta + merge_overhead`.

Applications: Vector processing, SIMD arrays, GPU programming.

---

### 4. **Flynn’s Classification**

Proposed by Michael J. Flynn (1966), it categorizes systems based on instruction and data streams:

|Type|Instruction Stream|Data Stream|Example|
|---|---|---|---|
|SISD|Single|Single|Conventional CPU|
|SIMD|Single|Multiple|Vector processors, GPUs|
|MISD|Multiple|Single|Rare, used in fault-tolerant systems|
|MIMD|Multiple|Multiple|Multiprocessor systems, clusters|

MIMD is most prevalent today—each processor executes its own instruction stream independently.

---

### 5. **ARM Processor Overview**

The **ARM** (Advanced RISC Machine) is a 32-bit **RISC** architecture emphasizing high performance per watt. It’s widely used in embedded systems and mobile processors.

#### Features:

- Load/store architecture
    
- 32-bit data path and instruction set
    
- 16-bit Thumb mode for higher code density
    
- Multiple operating modes (User, FIQ, IRQ, Supervisor, Abort, Undefined, System)
    
- Conditional execution of most instructions
    

ARM architectures are categorized (e.g., ARM5, ARM7, ARM9, ARM11) with incremental enhancements like DSP extensions, Jazelle Java execution, and SIMD support.

---

### 6. **Registers and Modes**

ARM has **37 registers** (all 32-bit):

- **General-purpose (R0–R12)**
    
- **SP (R13): Stack Pointer**
    
- **LR (R14): Link Register**
    
- **PC (R15): Program Counter**
    
- **CPSR/SPSR:** Status registers holding flags (N, Z, C, V), mode bits, and interrupt controls.
    

Each processor mode has its own _banked registers_ for fast context switching during interrupts.

---

### 7. **Thumb Instruction Set**

The **Thumb** mode provides a 16-bit compressed instruction set that improves memory efficiency while retaining most ARM functionalities.  
Switching between ARM and Thumb is done via the **BX instruction**.

---

### 8. **Instruction Encoding and Conditional Execution**

ARM instructions follow this general format:

```
<opcode>{condition}{S} Rd, Rn, Operand2
```

Conditional codes (e.g., EQ, NE, GT, LT, AL) allow selective execution, avoiding unnecessary branches.

Example:

```
CMP R0, #0
MOVEQ R1, #1
```

---

### 9. **Memory Access Instructions**

- **LDR/STR:** Load and store words or bytes.
    
- **LDRH/LDRB/LDRSH:** Halfword and signed byte variants.
    
- **Addressing modes:** Immediate, register, pre/post-indexed.
    
- **Block transfer:** `LDM` / `STM` enable multiple register transfers in one instruction.
    

---

### 10. **Program Status Registers**

- **CPSR (Current Program Status Register):** Holds current state (flags, interrupt masks, mode bits).
    
- **SPSR (Saved PSR):** Stores the previous state on exception entry.
    

Flags:

- N: Negative
    
- Z: Zero
    
- C: Carry
    
- V: Overflow
    
- T: Thumb state indicator
    

---

### 11. **Arithmetic, Logical & Data Processing**

Operations include ADD, SUB, AND, ORR, EOR, CMP, MOV, MVN, and RSB.  
The **barrel shifter** enables operand shifting or rotation within a single instruction, enhancing ILP.

For larger constants, pseudo-instructions like `LDR r0,=value` are used.

---

### 12. **Multiply and Load-Store Multiple**

- **MUL, MLA:** Multiply and multiply-accumulate.
    
- **LDM/STM:** Enable efficient register stack manipulation, essential in function calls and context saving.
    

---

### 13. **Software Interrupt (SWI)**

SWI triggers system calls, allowing user programs to request kernel-level services. Syntax:

```
SWI <number>
```

---

### 14. **Memory-Mapped vs I/O-Mapped I/O**

|Feature|Memory-Mapped|I/O-Mapped|
|---|---|---|
|Address Space|Shared with memory|Separate|
|Access Instructions|MOV, LDR, STR|IN, OUT|
|Instruction Count|One|Two|
|Speed|Faster|Slower|

Program-controlled I/O relies on CPU polling device status, suitable for low-speed systems.

---

### 15. **Case Study: ARM5 and ARM7**

- **ARM5:** Introduced Thumb instruction set, system mode, and halfword data support.
    
- **ARM7TDMI:** Enhanced with Debug (D), Multiplier (M), and ICE (I) extensions.
    
- **ARM9/11:** Added improved pipeline, DSP instructions, and SIMD support.
    

ARM’s evolution maintained backward compatibility while improving efficiency and performance per watt.

---

### 16. **AMBA Bus Architecture**

ARM processors use **AMBA (Advanced Microcontroller Bus Architecture)** for on-chip communication. It includes:

- **AHB/ASB:** High-performance system buses.
    
- **APB:** Peripheral bus for low-speed devices.
    
- **Bridge units** connect buses and manage arbitration.
    

---

### 17. **Summary**

Unit 5 unifies **parallelism principles** and **ARM architecture design**.  
Key takeaways:

- Parallelism improves computation by concurrency in hardware and software.
    
- Flynn’s classification helps categorize system designs.
    
- ARM embodies efficiency through RISC simplicity and conditional execution.
    
- Thumb instruction set enhances code density.
    
- Memory and I/O management follow standardized load/store mechanisms.
    
- Modern ARM cores integrate parallelism via multicore and SIMD extensions.
    

---

**Q1:** How does instruction-level parallelism differ from data-level parallelism in terms of architecture requirements?  
**Q2:** Why is conditional execution an essential feature in ARM architecture?  
**Q3:** How does Flynn’s classification influence modern multicore processor design?