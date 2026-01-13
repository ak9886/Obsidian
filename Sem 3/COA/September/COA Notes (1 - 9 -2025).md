---
updated_at: 2025-09-01T12:12:52.601+05:30
edited_seconds: 390
---
## How many segments are there in 8086?
> `From Google`
> The Intel 8086 microprocessor uses four segment registers at a time to access the 1 MB memory, which is logically divided into segments. These registers are the Code Segment (CS), Data Segment (DS), Stack Segment (SS), and Extra Segment (ES), each holding the starting address of a 64 KB segment for code, data, stack, and additional data, respectively.

![[Pasted image 20250901114156.png]]
`(Photo used in PPT)`
<span style="background:rgba(163, 67, 31, 0.2)">Size of the instruction byte is 6 bytes</span>
Arithmetic Logic Units : Does what the tin says
## Flag or Status Register
- 16 Bit Register
- Contains 9 flags
- Remaining 7 bits are idle in the register
- These flags tell us about the status of the processor after any arithmetic or logical operation
- IF the flag value is 1, the flag is set, and if it is 0, it is not set
```
#8086 Architecture
DATA SEGMENT
N1
3n2 DB 
```