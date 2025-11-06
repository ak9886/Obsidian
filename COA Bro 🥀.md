---
updated_at: 2025-11-06T21:09:45.817+05:30
edited_seconds: 20
---
#COA 
## 💻 Computer Organization and Architecture (COA) Notes

These notes cover the main topics discussed in the playlist: Basic Structure, CPU Design, Memory Hierarchy, and Pipelining.

### 1. Basic Computer Organization & CPU Structure

|**Module**|**Key Concepts & Components**|**Details**|
|---|---|---|
|**Von Neumann Architecture**|Stored Program Concept, Functional Units|Both **instructions** and **data** are stored in the same memory space. The main functional units are **Input, Output, Memory, ALU,** and the **Control Unit**.|

|

| Registers | PC, IR, MAR, MDR, AC, General Registers | Program Counter (PC): Stores the address of the next instruction. Instruction Register (IR): Holds the instruction currently being executed. Memory Address Register (MAR): Holds the address for memory read/write. Memory Data Register (MDR): Holds the data to be written to/read from memory. |

| Bus System | Address Bus, Data Bus, Control Bus | Address Bus: Unidirectional, specifies the memory/I/O address. Data Bus: Bidirectional, transfers data. Control Bus: Transfers control signals (e.g., Read/Write). |

| Instruction Formats | 0-Address, 1-Address, 2-Address, 3-Address | Defines the number of explicit addresses/operands in an instruction, influencing the CPU organization (e.g., Stack-based (0-Address) vs. General Register (2/3-Address)). |

---

### 2. Addressing Modes

Addressing modes define **how the address of the operand is calculated** from the information in the instruction's address field.

|**Addressing Mode**|**How the Effective Address (EA) is Calculated**|**Use Case**|
|---|---|---|
|**Immediate**|$EA = \text{Operand itself}$|Loading a constant value into a register (fastest).|
|**Direct**|$EA = \text{Address field}$|Simple access to fixed memory locations.|
|**Indirect**|$EA = \text{Memory}[\text{Address field}]$|Accessing large address spaces; pointers.|
|**Register**|$EA = \text{Register identifier}$|Operand is in a CPU register (very fast).|
|**Register Indirect**|$EA = \text{Contents of Register}$|Implementing pointers and loops.|
|**Indexed**|$EA = \text{Address field} + \text{Index Register}$|Accessing elements in an array.|
|**Relative**|$EA = \text{PC} + \text{Address field}$|Implementing position-independent code (e.g., Jump instructions).|

---

### 3. Memory Hierarchy & Cache Mapping

The **Memory Hierarchy** is organized by **Speed** (fastest at the top) and **Size** (smallest at the top): **Registers > Cache > Main Memory (RAM) > Secondary Storage.**

#### Cache Mapping Techniques

These techniques determine how a block from main memory is placed into a cache line, leveraging the **Principle of Locality** (**Temporal** - reuse recently accessed data; **Spatial** - reuse data near recently accessed data).

1. **Direct Mapping:**
    
    - **Placement:** Each memory block has **only one** possible location in the cache.
        
    - **Formula:** $\text{Cache Line} = \text{Main Memory Block Number} \pmod{\text{Number of Cache Lines}}$
        
    - **Drawback:** High **conflict misses** (two frequently used blocks map to the same line).
        
2. **Fully Associative Mapping:**
    
    - **Placement:** A memory block can be placed in **any available** cache line.
        
    - **Drawback:** Slow search time (must check _all_ cache tags simultaneously) and complex hardware.
        
3. **Set Associative Mapping:**
    
    - **Placement:** A memory block maps to a specific **set** in the cache, but can be placed in **any line within that set** (e.g., 2-way or 4-way set associative).
        
    - **Benefit:** A good balance between the speed of Direct Mapping and the flexibility of Fully Associative Mapping.
        

#### Cache Replacement Algorithms

Used when a cache set is full and a new block needs to be brought in: **LRU (Least Recently Used)**, **FIFO (First In, First Out)**, or **Random**.

---

### 4. Pipelining

**Pipelining** is a technique that allows a CPU to fetch, decode, and execute multiple instructions concurrently by dividing instruction processing into stages.

|**Concept**|**Description**|**Performance Metric**|
|---|---|---|
|**Ideal Pipelining**|Increases **throughput** (instructions completed per unit time) by completing one instruction per clock cycle after the initial pipeline fill.|**Speedup:** $\text{Time (Non-Pipelined)} / \text{Time (Pipelined)}$|
|**Pipeline Hazards**|Conditions that prevent the pipeline from completing an instruction on its next clock cycle, causing stalls.|**Stall Cycles:** Extra clock cycles added to execution time due to hazards.|
|**Types of Hazards**|**1. Structural:** Resource conflict (e.g., two instructions need the same memory port). **2. Data:** An instruction needs the result of a _previous_ instruction that hasn't finished writing back yet. **3. Control:** Branch/Jump instructions disrupt the sequential flow.|**Efficiency:** $\text{Speedup} / \text{Number of Stages}$|

---
