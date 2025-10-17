---
updated_at: 2025-10-17T11:55:05.494+05:30
edited_seconds: 50
---
#COA 
### ✅ **Part 1: Calibrated Output with Two's Complement**
- **Gain factor**: -11  
- **Sensor value**: 27  
- **Operation**: Multiply 27 × (-11)

#### Step 1: Convert to binary
- 27 = `00011011` (8-bit)
- -11 in 8-bit two's complement:
  - 11 = `00001011`
  - Invert + 1 → `11110101`

#### Step 2: Multiply in binary
We perform **binary multiplication** of:
```
00011011 (27)
× 11110101 (-11)
```

This is **signed multiplication**, but we can treat it as **unsigned** and then interpret the result in two's complement.

**27 × 11 = 297**  
Then apply sign:  
**27 × (-11) = -297**

#### Step 3: Represent -297 in 16-bit two's complement
- 297 = `0000000100101001`
- -297 = invert + 1 → `1111111011010111`

✅ **Result**:  
**-297**  
**Binary**: `1111111011010111` (16-bit two's complement)

---

### ✅ **Part 2: 5-bit Unsigned Binary Multiplication via Shift-and-Add**
Let’s pick:
- X = `01101` (13)
- Y = `01011` (11)

We simulate the **shift-and-add** algorithm:

| Step | Y LSB | Action | Accumulator (5-bit) |
| ---- | ----- | ------ | ------------------- |
| 1    | 1     | Add X  | `01101`             |
| 2    | 1     | Add X  | `11010`             |
| 3    | 0     | No add | `01101` (shifted)   |
| 4    | 1     | Add X  | `11010`             |
| 5    | 0     | No add | `01101` (shifted)   |

But this is **not accurate** — we need to **accumulate and shift** properly.

#### Proper Shift-and-Add Algorithm:
We use a 10-bit accumulator (5 + 5 bits):

```
X = 01101 (13)
Y = 01011 (11)

Initial: ACC = 00000 00000

Step 1: Y[0] = 1 → ACC += X → 00000 01101
Step 2: Shift right → 00000 00110 1
Step 3: Y[1] = 1 → ACC += X → 00000 10011
Step 4: Shift right → 00000 01001 1
Step 5: Y[2] = 0 → No add
Step 6: Shift right → 00000 00100 1
Step 7: Y[3] = 1 → ACC += X → 00000 10001
Step 8: Shift right → 00000 01000 1
Step 9: Y[4] = 0 → No add
Step 10: Shift right → 00000 00100 1

Final 10-bit result: `0000110111` = 143
```

✅ **Result**:  
**143**  
**Binary**: `0000110111` (10-bit)

---

### ✅ **Part 3: Fast Add with Carry-Save Addition (45 + 63)**
We use **carry-save addition** to add **45 and 63** without carry propagation.

#### Step 1: Convert to binary
- 45 = `00101101`
- 63 = `00111111`

#### Step 2: Carry-save addition
We compute:
- **Sum bits** = XOR of bits
- **Carry bits** = AND of bits, shifted left

```
  00101101 (45)
+ 00111111 (63)
-----------
  01001100 (sum)
  00101110 (carry)
```

Now add sum and carry:
```
  01001100
+ 00101110
-----------
  01111010 = 122
```

✅ **Result**:  
**122**  
**Binary**: `01111010`

---

### ✅ **Part 4: Divide 217 bytes into 16-byte segments**
We need:
- **Full segments**: 217 ÷ 16 = 13 full segments
- **Leftover**: 217 mod 16 = 9 bytes

#### Binary:
- 217 = `11011001`
- 16 = `00010000`

#### Division in binary:
```
217 ÷ 16 = 13 remainder 9
```

✅ **Result**:
- **Full segments**: 13 → `00001101`
- **Leftover**: 9 → `00001001`

---

### ✅ Final Summary

| Part | Description          | Result                  | Binary                 |
| ---- | -------------------- | ----------------------- | ---------------------- |
| 1    | 27 × (-11)           | **-297**                | `1111111011010111`     |
| 2    | 13 × 11 (5-bit)      | **143**                 | `0000110111`           |
| 3    | 45 + 63 (carry-save) | **122**                 | `01111010`             |
| 4    | 217 ÷ 16             | **13 full, 9 leftover** | `00001101`, `00001001` |
