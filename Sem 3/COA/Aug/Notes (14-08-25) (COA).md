---
updated_at: 2025-08-22T08:09:15.672+05:30
edited_seconds: 20
---
#COA 
# Tutorial 5
. Give a detailed description of the Functional Units of a Computer with a neat sketch.

2. 92 / 4 --> BCD Division

3. Differentiate Address Bus and Control Bus

4. A microprocessor-based system has:

• A 32-bit data bus
• A 20-bit address bus
• A clock speed of 25MHz

  The CPU needs to read 4KB of data from memory. 

How many unique memory addresses can this system access?


# ANS
# 1) Functional units of a computer (+ neat sketch)

**Core units**

- **Input Unit**: captures raw data/instructions (keyboard, mouse, sensors) and encodes them for the system.
    
- **Output Unit**: presents processed results (monitor, printer, actuators).
    
- **Memory (Storage)**
    
    - **Primary**:
        
        - **Registers** (in CPU): fastest, hold operands, addresses, status.
            
        - **Cache** (L1/L2/L3): hides main-memory latency.
            
        - **Main Memory (RAM)**: working store for programs/data.
            
    - **Secondary**: SSD/HDD; persistent program/data storage.
        
- **CPU = Control Unit (CU) + ALU + Registers**
    
    - **ALU**: arithmetic (add, sub, mul, div) and logic (AND/OR/XOR, shifts, compares).
        
    - **Control Unit**: fetch–decode–execute sequencing; generates control signals; coordinates data movement.
        
    - **Registers**: PC (program counter), IR (instruction register), MAR/MDR (address/data), general-purpose (R0…Rn), flags/status.
        

**Interconnect**

- **Buses**: **Address bus** (selects location), **Data bus** (moves data), **Control bus** (read/write/clock/interrupts/ack).
    

[[ExcaliNotes (14-8-25)]]
**Instruction cycle (concise)**

1. **Fetch**: CU puts address on address bus → memory → instruction on data bus → IR.
    
2. **Decode**: CU interprets opcode, sets control signals.
    
3. **Execute**: ALU/Memory/IO operation; results to registers/memory.
    
4. **Write-back / Update PC**: store results; PC to next instruction (or branch).
# 2) 92 ÷ 4 — BCD division
 
- Represent operands in packed BCD:
    
    - 92₁₀ → `1001 0010` (0x92)
        
    - 4₁₀ → `0100` (0x04)
        
- **Steps (decimal/BCD-aligned):**
    
    - 9 ÷ 4 → quotient digit 2, remainder 1
        
    - Bring down next BCD digit 2 → forms 12
        
    - 12 ÷ 4 → quotient digit 3, remainder 0
        
- **Result:** 23₁₀ → BCD `0010 0011` (0x23).  
    So, **92 ÷ 4 in BCD = 23 (BCD 0x23)**.
    

---

# 3) Address Bus vs Control Bus (differences)

|Aspect|Address Bus|Control Bus|
|---|---|---|
|**Purpose**|Selects the **source/destination** location in memory/IO|Orchestrates **operations** (e.g., Read/Write, clock, reset)|
|**Data carried**|Binary **addresses** (location identifiers)|**Signals** and **strobes** (timing and command)|
|**Direction**|Typically **unidirectional** from CPU → memory/IO|**Bidirectional/multidirectional** (CPU ↔ devices)|
|**Width impact**|Determines **addressable range** (2^N locations)|Determines **protocol richness & timing**, not address space|
|**Examples**|MAR → Address bus → Memory/IO|`RD#`, `WR#`, `MEMR#`, `MEMW#`, `IOR#`, `IOW#`, `INT`, `ACK`, `CLK`, `RESET`|
|**Scaling**|More lines → larger memory space|More lines → finer control/handshakes/interrupt vectors|

---

# 4) System with 32‑bit data bus, 20‑bit address bus, 25 MHz clock

**How many unique memory addresses can it access?**

- Address bus width = **20 bits** → **2²⁰ = 1,048,576 unique addresses**.
    
- If byte-addressable (typical), addressable memory size = **1,048,576 bytes = 1 MiB**.
    

_(Side note, not asked: reading 4 KiB over a 32‑bit data bus transfers 4096 B ÷ 4 B = 1024 bus reads; with one read per clock at 25 MHz, ideal time ≈ 40.96 µs.)