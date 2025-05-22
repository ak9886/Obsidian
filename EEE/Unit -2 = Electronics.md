

---

## 🔘 PN Junction Diode Structure and Depletion Region

### Structure

A PN junction diode is formed by joining P-type and N-type semiconductor materials. At the junction of these materials, a **depletion region** forms, which is devoid of free charge carriers.

- **P-type region:** Contains holes (positive charge carriers)
- **N-type region:** Contains electrons (negative charge carriers)
- **Depletion region:** Neutral zone due to recombination of electrons and holes near the junction

### Key Points

- The junction creates an electric field that opposes further movement of carriers.
- No current flows until an external voltage is applied.

---

## Diode V–I Characteristics (Forward and Reverse Bias)

### Forward Bias

- Positive terminal of the battery is connected to the P-side, and the negative to the N-side.
- Reduces the width of the depletion region.
- Current flows after the threshold voltage (~0.7V for silicon).

### Reverse Bias

- Positive terminal connected to the N-side, negative to the P-side.
- Increases the depletion width, blocks current flow.
- Only a small leakage current flows until breakdown voltage.

---

## BJT Circuit Diagram (NPN/PNP Biasing)

### NPN Transistor

- Current flows from **collector to emitter** when base is positive relative to emitter.
- Majority charge carriers are electrons.

### PNP Transistor

- Current flows from **emitter to collector** when base is negative relative to emitter.
- Majority charge carriers are holes.

### Biasing

- Proper voltage at base-emitter junction is needed to turn on the transistor.
- E<sub>B</sub>, C<sub>C</sub>, and B<sub>B</sub> are emitter, collector, and base terminals respectively.

---

## BJT Output Characteristics Graph

### Graph Details

- Plot of collector current **I<sub>C</sub>** vs. collector-emitter voltage **V<sub>CE</sub>** for various base currents **I<sub>B</sub>**
- Shows regions of operation:
  - **Cut-off:** Transistor OFF
  - **Active:** Linear amplification
  - **Saturation:** Transistor fully ON

---

## Basic Logic Gates

- **AND Gate:** Output is high only if all inputs are high.
- **OR Gate:** Output is high if any input is high.
- **NOT Gate:** Inverts input signal.
- **NAND Gate:** NOT of AND.
- **NOR Gate:** NOT of OR.
- **XOR Gate:** Output is high when inputs are different.
- **XNOR Gate:** Output is high when inputs are the same.

### Truth Table Notation

- 1 = HIGH, 0 = LOW

---

## 2-variable K-Map

- A 2-variable K-map has 4 cells representing all combinations of two binary variables.
- Helps simplify Boolean expressions.

| A | B | Output |
|---|---|--------|
| 0 | 0 |        |
| 0 | 1 |        |
| 1 | 0 |        |
| 1 | 1 |        |

---

## 3-variable K-Map

- A 3-variable K-map has 8 cells (2 rows × 4 columns).
- Used to group minterms and simplify Boolean logic.

---

##  4-variable K-Map

- A 4-variable K-map has 16 cells arranged in a 4×4 grid.
- Used for simplifying large Boolean expressions.

---

## Diode Rectifier Circuit (AC to DC)

### Function

- Converts alternating current (AC) to direct current (DC).

### Components

- Diodes arranged to allow current in one direction.
- Typically includes filter capacitors to smooth output.

### Types

- Half-wave: Uses one diode
- Full-wave: Uses two diodes and center tap transformer or four-diode bridge

---

##  Chopper Circuit (DC to DC)

- A **chopper** is an electronic switch that rapidly turns on and off to convert fixed DC to variable DC.
- Used in motor speed control and power supplies.

### Components

- Semiconductor switch (e.g., MOSFET, IGBT)
- Control circuitry

---

##  Inverter Block Diagram (DC to AC)

- An **inverter** converts DC input to AC output.

### Block Diagram

1. DC Source
2. Inverter Bridge (with transistors)
3. Output AC waveform (sine or square)

Applications include UPS, solar systems, and electric drives.

---

## Cycloconverter and AC Voltage Regulator Diagram

### Cycloconverter

- Converts AC power at one frequency directly to a lower or higher frequency.
- Used in variable-speed AC motor drives.

### AC Voltage Regulator

- Regulates output voltage by adjusting conduction angle of thyristors.
- Maintains desired voltage despite input fluctuation.