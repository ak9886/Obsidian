---
updated_at: 2025-11-14T16:19:29.345+05:30
edited_seconds: 50
---
#COA 

---

## COA Study Guide: Understand Every Core Concept

---

## Functional Units of a Computer

- **Core Units**:
    
    - **Input Unit**: Captures raw data or instructions (keyboard, mouse, sensors) and encodes them electrically for processing.
        
    - **Output Unit**: Displays final results (monitor, printer, actuator).
        
    - **Memory Storage**:
        
        - **Registers**: Fastest, inside the CPU; holds addresses, operands, results.
            
        - **Cache (L1/L2/L3)**: Buffers to hide slow main memory.
            
        - **Main Memory (RAM)**: Working area for programs and data.
            
        - **Secondary Storage**: SSD/HDD for persistent storage.
            
    - **CPU Components**:
        
        - **Control Unit (CU)**: Orchestrates fetch-decode-execute cycle, generates system control signals.
            
        - **ALU (Arithmetic Logic Unit)**: Performs arithmetic (add, sub, mul, div) and logic (AND, OR, NOT, XOR, shifts, compares) operations.
            
        - **Registers**: Program Counter (PC), Instruction Register (IR), Memory Address/Data Registers (MAR/MDR), general-purpose (R0-Rn), flags/status.COA-List-of-Videos.md+1​
            
- **Interconnects**:
    
    - **Address Bus**: Selects memory/IO location.
        
    - **Data Bus**: Moves bytes/words.
        
    - **Control Bus**: Sends commands/timing (Read/Write/Clock/Interrupt/Reset).Notes-14-08-25-COA.md+1​
        

---

## Number Systems and Data Representation

- **Types of Number Systems**:
    
    - **Binary**: Only 0 and 1, Base 2.
        
    - **Octal**: 0–7, Base 8.
        
    - **Decimal**: 0–9, Base 10.
        
    - **Hexadecimal**: 0–F (0–15), Base 16.COA-List-of-Videos.md​
        
- **Conversions**:
    
    - **Decimal <-> Binary/Octal/Hex**: Understand both directions.COA-List-of-Videos.md​
        
    - **Signed Numbers**:
        
        - **Two's Complement**: Most common for signed integers. E.g., −5-5−5 in 8-bits: 111110111111101111111011.
            
        - **Sign-Magnitude**: Less common, separate sign bit.COA-List-of-Videos.md​
            
    - **Floating Point**:
        
        - **IEEE 754**: 1 bit sign, 8 bit exponent, 23 bit mantissa (for 32-bit single precision).
            
- **Other Codes**:
    
    - **Gray Code**: Useful for error correction.
        
    - **BCD (Binary Coded Decimal)**: 4 bits per decimal digit.
        
    - **ASCII**: Character encoding (e.g., K = 01001011 in 7-bits).Tutorial-COA.md+1​
        
- **Tutorial Section**:  
    See the **Tutorial-COA.md** file for step-by-step worked conversions:
    
    - E.g., Convert Binary to Gray Code, Gray to Binary, Decimal to BCD, Excess-3 Code, finding ASCII codes, and more. These “Conversion Questions” present a direct, solution-oriented tutorial section.Tutorial-COA.md​
        

---

## Basic Processing Unit and Instruction Cycle

- **What is the Basic Processing Unit?**
    
    - The unit that performs the arithmetic, logic, movement, and control operations for instruction execution.Unit-4.pdf+2​
        
- **Instruction Cycle Steps**:
    
    1. **Fetch**: Get instruction from memory (PC -> MAR, read to IR).
        
    2. **Decode**: CU interprets opcode, sets up for execution.
        
    3. **Execute**: ALU performs operation, data moves as needed.
        
    4. **Write-back**: Store result, update PC for next instruction.COA-Notes.md+2​
        
- **ALU Operations**: Arithmetic (ADD, SUB), Logic (AND, OR), Shift, comparisons.
    
- **Registers in Flow**: Data transferred between registers, memory, ALU using buses and control signals. (R1out, R4in means contents of R1 are moved to R4).Unit-4.pdf+1​
    

---

## Memory and Bus Organization

- **Registers**: Store temporary data/operands.COA-Notes.md+1​
    
- **Buses**:
    
    - **Address Bus**: Unidirectional, selects location (Width = how many unique addresses CPU can access: 2width2^{\text{width}}2width).Notes-14-08-25-COA.md​
        
    - **Data Bus**: Carries data.
        
    - **Control Bus**: Carries timing/command (Read/Write/CLK/Reset).
        
- **Single Bus vs Multi-Bus**:
    
    - **Single Bus**: Simpler, only one transfer at a time.
        
    - **Multi-Bus**: Faster, supports parallel transfers (most commercial CPUs use this).Unit-4.pdf+1​
        

---

## Instruction Set, Formats, and Addressing Modes

- **Instruction Types**:
    
    - **Data Transfer**: MOV, IN, OUT
        
    - **Arithmetic/Logic**: ADD, SUB, AND, OR, MUL, DIV
        
    - **Control**: JMP, CALL (branches), loops
        
    - **String Operations**: (LEA, LODS, STOS in assembly).COA-Study-Notes.md+1​
        
- **Instruction Format**: Opcode, source/destination, immediate values, mode.
    
- **Addressing Modes**:
    
    - **Immediate**: Data embedded in instruction (e.g., MOV R1, 5).
        
    - **Register**: Operand is in a register.
        
    - **Direct/Indirect**: Uses memory address or pointer in memory/register.
        
    - **Relative/Indexed**: Useful for loops/arrays (base + offset).Unit-4.pdf+1​
        

---

## Control Unit Design

- **Hardwired Control**: Uses logic gates, is extremely fast, best for RISC, but inflexible if you want to change instruction set.
    
- **Microprogrammed Control**: Uses microinstructions stored in control memory (like a tiny ROM). Flexible, easier to update, more common in CISC, but slightly slower.COA-Notes.md+2​
    

---

## Pipelining and Pipeline Hazards

- **Pipelining**: Overlapping execution of instructions to boost throughput (like an assembly line). E.g., while one instruction is being fetched, another is being decoded.COA-Notes.md+2​
    
    - **4-Stage pipeline**: Fetch, Decode, Execute, Write-back.
        
- **Pipeline Hazards**:
    
    - **Structural**: Hardware resource conflict.
        
    - **Data**: Results not ready from prior instruction.
        
    - **Control**: Branch changes flow unexpectedly.
        
- **Mitigation Strategies**:
    
    - **Forwarding**/Bypassing,
        
    - **Stalling**,
        
    - **Branch Prediction** (static/dynamic/two-state/four-state),
        
    - **Delayed Branch** (run useful instructions during delay).Unit-4.pdf+1​
        

---

## Memory Hierarchy and Effective Access

- **Why a Memory Hierarchy?** Balances speed, cost, and size.
    
    - **Registers**: Fastest, very limited.
        
    - **Cache (L1, L2, L3)**: Fast/expensive/medium size.
        
    - **Main Memory (DRAM)**: Slower/larger.
        
    - **Secondary Storage (HDD/SSD)**: Huge/slowest.
        
- **Important Terms**:
    
    - **Memory Access Time (MAT)**
        
    - **Wait States** (CPU stalls waiting for slow memory)
        
    - **Effective Access Time (EAT)**: EAT=(hit rate)×cache access time+(miss rate)×main memory timeEAT = \text{(hit rate)} \times \text{cache access time} + \text{(miss rate)} \times \text{main memory time}EAT=(hit rate)×cache access time+(miss rate)×main memory time.COA-List-of-Videos.md​
        
- **Tutorial Note**:  
    Refer to diagrams and example questions in your notes to deeply understand cache and memory hierarchy calculations.COA-List-of-Videos.md​
    

---

## Parallelism and Flynn's Classification

- **Parallelism**: Performing multiple tasks at once to increase speed and throughput.
    
    - **Hardware Parallelism**: Multiple cores, threads—e.g., k-issue processor can execute k instructions per cycle.
        
    - **Software Parallelism**: Control/data dependencies in algorithm design.Unit-5.pdf+2​
        
- **Types of Parallelism**:
    
    - **Instruction-Level (ILP)**: Independent instructions overlap.
        
    - **Data-Level (DLP)**: Same operation on multiple data—used in GPUs, SIMD.
        
    - **Task-Level (TLP)**: Independent tasks.Unit-5.pdf+2​
        
- **Flynn’s Classification**:
    
    - **SISD**: Single Instruction, Single Data (classic CPU, no parallelism).
        
    - **SIMD**: Single Instruction, Multiple Data (vector processors, GPUs).
        
    - **MISD**: Multiple Instruction, Single Data (rare).
        
    - **MIMD**: Multiple Instruction, Multiple Data (multi-core, clusters).Unit-5.pdf+1​
        

---

## ARM Processor Architecture (Case Study)

- **ARM (Advanced RISC Machine)**:
    
    - 32-bit RISC design, ultra-efficient and widely used in embedded/mobile.
        
    - Multiple operating modes: User, FIQ, IRQ, Supervisor, Abort, Undefined, System.
        
    - 37 registers: R0–R12 (general), R13 (SP), R14 (LR), R15 (PC), CPSR/SPSR (status).ARM-Processor.md+2​
        
    - **Load-Store Architecture**: Operations only on registers, memory access only via LDR/STR.
        
- **Instruction Set**:
    
    - **Thumb**: 16-bit compressed instructions for high code density; BX instruction switches between ARM/Thumb.
        
    - **Conditional Execution**: Most instructions can be executed conditionally (EQ, NE, GT…).ARM-Processor.md+2​
        
- **Key ARM Features**:
    
    - High performance with low power.
        
    - Uniform, fixed instruction length.
        
    - Barrel shifter for flexible operand handling.
        
    - Efficient context switching in interrupts via banked registers.
        
    - AMBA bus for communication (AHB, APB).ARM-Processor.md+2​
        

---

## Tutorials and Worked Examples

- **Look for anything marked as a "tutorial" or "tutorial question" in the files for step-by-step working**:
    
    - These sections offer guided walkthroughs on tricky topics like conversions, BCD division, assembly instructions, address decoding, and practical use of buses.Tutorial-COA.md+3​
        
- For every such section, revisit in-depth to gain not just knowledge but exam-level confidence.
    

---

## Summary Table: Address Bus vs Control Bus

|Aspect|Address Bus|Control Bus|
|---|---|---|
|Purpose|Selects memory/IO location|Handles control/timing signals|
|Data Carried|Binary addresses|Read/Write/Reset/CLK/Interrupt, etc.|
|Direction|Unidirectional (CPU→Memory/IO)|Bidirectional/multidirectional|
|Width Impact|Sets addressable range|Not directly address space, but protocol richness and timing accuracyCOA-List-of-Videos.md+2​|

---

## Tips & Exam Strategy

- Make sure you can draw and identify block diagrams (e.g., functional units, buses, ARM dataflow).
    
- Practice ALL tutorial conversions and show every single calculation step.
    
- Understand, don’t just memorize, the purpose behind every control signal and bus.
    
- For ARM and Flynn’s types, visualize with real-world processor or cluster examples.Unit-5.pdf+2​
    
- Grasp hazards and pipelining not only by their names, but by understanding how they impact the flow of instructions in actual hardware.
    

---
