#COA 
## Three Address Instruction
ADD A, B, R<sub>1</sub> : R<sub>1</sub> <- A+B
ADD C, D, R<sub>2</sub>: R<sub>2</sub> <- C+D
MUL R<sub>1</sub>, R<sub>2</sub>, Y  : Y <- R<sub>1</sub> * R<sub>2</sub>

---

### <u>Two AI</u>

LOAD A, R<sub>1</sub> : R<sub>1</sub> <- A
LOAD B, R<sub>1</sub> : R<sub>1</sub> <- R<sub>1</sub> +B
MOV C, R<sub>2</sub>  : 
MUL R<sub>1</sub>, R<sub>2</sub> : 

---

## One Address Instruction
LOAD A  : AC <- A
ADD B    : AC <- AC + B
STORE T :     T<- AC
LOAD C  :  AC <- C
ADD D   :  AC <- AC+D
MUL T   : AX  <-AC * T
STORE Y:    Y <-AC

---

### <u>Zero AI</u>
<center>TOS = TOP OF STACK</center>
PUSH A: TOS <-A
PUSH B: TOS<- B
ADD     : TOS<- A+B
PUSH C: TOS<- C
PUSH D: TOS <-D
ADD     : TOS <-C+D
	MUL     : TOS<-(C+D) * (A+B)

---
