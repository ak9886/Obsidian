---
updated_at: 2025-09-04T09:34:07.964+05:30
edited_seconds: 810
---
# Unit 3: Stacks
## What is a stack?
- Stack works on "Last In First Out"[LIFO] or "First In Last Out"[FILO] principle
- E.g.: Plates placed over one another
	- The plate at the top is removed first and the bottom most, the last
	- So it follows LIFO/ FILO
## Stack Operations
- Two of them
- ### Push
	- Pushing (storing) an element on the stack
	- If the stack is full, it will "Overflow" if the Overflow condition is enabled
- ### Pop
	- Removing (Accessing) an element from the stack
	- the elements are popped in the decreasing order.
	- if the stack is empty, Underflow condition will be enabled
## Stack Operation example
- [[Stack Operations Example]]
	- Input:    ABCDE
	- Output: EDCBA
```C
if (stack : full)
	print ("Stack Overflow")
else
	top = top + 1
	Stack[top] = val
```


```C
if (stack [top]==-1) /* TO CHECK IF THE STACK IS EMPTY */
	"Stack Underlow"
	val = Stack[top]
	top = top-1
printf("id" ,Stack[top])```
## Stack Applications
1. Infix to Postfix Conversion
2. Postfix Eval
3. Balancing Symbols
4. Nested Functions
5. Tower of Hanol

$$A + (B \times C) + D$$
## Question: 
1. (A+B) * C
2. (A + B) * (C -D)