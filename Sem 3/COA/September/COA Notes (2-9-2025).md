---
updated_at: 2025-09-02T14:42:39.943+05:30
edited_seconds: 250
---
### Add 2 8-Bit No.
==Data== Segment
- We're storing `03H` in <font color="#ffc000">N<sub>1</sub>DB</font>
- We're storing `04H` in <font color="#ffc000">N<sub>2</sub>DB</font>
- We're storing `Nothing`  in<font color="#ffc000"> ResDB</font> (No values, just allocated/ initialized)
- Assume: DS: Data, CS: Code
	-> START: MOV AX, Data
		    MOV DS, AX
		    MOV AL, N<sub>1</sub>
		    MOV BL, N<sub>2</sub>
		    ADD AL, BL
		    MOV RES, AL