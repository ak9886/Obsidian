

---

## 🔋 DC Circuit with Voltage Sources and Resistors (KVL/KCL)

### Kirchhoff's Voltage Law (KVL)

KVL states that the sum of all voltages around any closed loop in a circuit is zero.  
This is based on the principle of energy conservation.

As you traverse a loop, the energy gained (from sources like batteries) is exactly balanced by the energy lost (across components like resistors).

**Mathematically:**


∑V = 0


This law is crucial for analyzing circuits, ensuring that all voltage drops and rises in a loop are accounted for.

---

### Kirchhoff's Current Law (KCL)

KCL asserts that the total current entering a junction equals the total current leaving it.  
This is derived from the conservation of charge.

**At any node:**

∑I<sub><i>in</i></sub> = ∑I<sub><i>out</i></sub>

This law helps in determining unknown currents in complex circuits by analyzing the flow at junctions.

---

### Example

Consider a simple loop with a 10V battery and two resistors:

- R<sub>1</sub> = 2Ω  
- R<sub>2</sub> = 3Ω  
- Series connected

**Using KVL:**


10V - (I × 2Ω) - (I × 3Ω) = 0  
=> 10 - 5I = 0  
=> I = 2A


---

## 🔁 Mesh Analysis Circuit with Labeled Loops

### Mesh Analysis

Mesh analysis is a method that uses KVL to determine the currents flowing in the loops (meshes) of a circuit.

Assign loop currents and apply KVL to each loop to get equations. Solve the system to find unknown currents.

**Example Concept:**

- Loop 1: Current I<sub>1</sub>  
- Loop 2: Current I<sub>2</sub>  
- Shared resistor between loops = Voltage drop due to (I<sub>1</sub> - I<sub>2</sub>) or (I<sub>2</sub> - I<sub>1</sub>)

---

## 🔗 Nodal Analysis Circuit with Nodes Marked

### Nodal Analysis

Nodal analysis uses KCL to find node voltages.

Pick a reference node (usually ground), then apply KCL to each non-reference node.

**Steps:**

1. Label node voltages V<sub>1</sub>, V<sub>2</sub>, etc.
2. Express currents leaving the node as (V<sub>node</sub> - V<sub>other</sub>)/R
3. Solve system of equations

---

## 🔄 Star (Y) and Delta (Δ) Network Conversion Diagrams

### Purpose

In complex resistor networks, converting between star (Y) and delta (Δ) makes circuit analysis easier.

### Star (Y) to Delta (Δ) Conversion

Given resistors:  
- R<sub>1</sub>, R<sub>2</sub>, R<sub>3</sub> in star connection

You can convert to delta with equivalent resistors using standard formulas.

> Diagram-wise:  
> Star = 3 resistors connected to a central point  
> Delta = 3 resistors forming a triangle

---

## 📈 Half-Wave Rectifier Circuit with Input/Output Waveforms

### Function

A half-wave rectifier converts AC to DC by allowing only one half of the cycle (positive or negative) to pass.

### Circuit:

- 1 Diode + 1 Load Resistor

### Waveform:

- **Input:** Full sine wave  
- **Output:** Only positive half-cycles

### Operation:

- Positive half-cycle: diode conducts  
- Negative half-cycle: diode blocks

---

## 🔄 Full-Wave Bridge Rectifier Circuit with Waveforms

### Function

A full-wave bridge rectifier uses 4 diodes to convert both halves of the AC input to DC.

### Circuit:

- 4 Diodes in bridge configuration  
- Load resistor connected across bridge output

### Waveform:

- **Input:** Full sine wave  
- **Output:** Full-wave rectified (both halves appear as positive)

### Operation:

- Each half-cycle: 2 diodes conduct, current flows in same direction through load

---
