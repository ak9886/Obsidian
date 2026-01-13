---
updated_at: 2025-09-08T15:44:53.546+05:30
edited_seconds: 220
---


---

# Content from DSA (Notes 20-08-2025).md
---
- The insertion into a singly linked list can be performed at different positions. Based on the position of the new node being inserted

```c
while (temp!=val){
	newnode = temp->next
}
```

---

# Content from `DSA Notes (11-8-25).md`

#DSA 
## Linked List
	- A linked list is a linear data structure
	- A list can be defined as an ordered collection
	- A node contains two fields, i.e, data stored at that particular address and the pointer which contains the address of the next node in the memory
## Deletion
```c
#include <stdio.h>
void main(){
	int LA[] = {1,3,5,7,8};
	int k = 3;
	int j;
	printf("the original array elements are: \n");
	for (int i = 0; i<n; i++){
		printf("");
	}
}
```
## Searching
	- Search for an array element based on its value or its index
## Algorithm
	- Start
	- Set j=0
	- Repeat steps 4 and 5 while J<N
	- if LA[J] is equal to item, then go to step 6
	- Set J=J+1
	- print J,item
	- Stop
## Code
```c
#include <stdio.h>
int main(){
	int LA[] = {1,3,5,7,8};
	int n;
	printf("Enter Number: ");
	scanf("%d",&n);
	for (int j=0; j<n;j++){
		if (LA[j]==n){
			d=j+1
			printf("Found at %d th Position",d);	
		}
		else{
			pass;
		}
	}
}
```
[[ExcaliNotes (13-08-25)]]


---

# Content from DSA Notes (21 Aug 2025).md

---
updated_at: 2025-08-21T16:10:01.781+05:30
edited_seconds: 20
---
#DSA 
# Deletion


---

# Content from DSA Notes (28-08-2025).md

---
updated_at: 2025-08-28T09:26:38.034+05:30
edited_seconds: 970
---
### What is a polynomial
- A polynomial p(x) is the expression in variable x which is in the form (ax<sup>n</sup> +bx<sup>n-1</sup> +....+ jx+k)
- We can use polynomials for linked lists
- [[ExcaliNotes-1 DSA (28-08-2025)]]
- For 5x<sup>2</sup>+11x+2
- [[ExcaliNotes-2 (DSA) (28-08-2025)]]
---

# Cursor Based Implementation
## Methodology
- Pointers **Store** the memory address of another variable
## What is a Cursor List?
- A CursorList is an array version of a linked list
- It is an array of list nodes but instead of each node containing a pointer to the next item in the linked list.

| Slot | Element | Next |
| ---- | ------- | ---- |
| 0    | header  | 1    |
| 1    |         | 3    |
| 2    | header  | 0    |
| 3    |         | 4    |
| 4    |         | 5    |
| 5    |         | 6    |
| 6    |         | 8    |
| 7    | header  | 0    |
| 8    |         | 9    |
| 9    |         | 10   |
| 10   |         | 0    |

| Slot | Element | Next                            |
| ---- | ------- | ------------------------------- |
| 0    | header  | 3                               |
| 1    | 10      | <font color='#fe2345' >0</font> |
| 2    | header  | 1                               |
| 3    |         | 4                               |
| 4    |         | 5                               |
| 5    |         | 6                               |
| 6    |         | 8                               |
| 7    | header  | 0                               |
| 8    |         | 9                               |
| 9    |         | 10                              |
| 10   |         | 0                               |
# Doubly Linked Lists
- Doubly Lined lists
	- Each node points to not only successor but the predecessor
	- There are two <font color="#c0504d">NULL</font>: At the first and last nodes in the list
	- Advantage: given a node, it is east to visit its predecessor. convenient to traverse lists backwards.
# Operations
- Create a node
- Insertion at beginning of a list
- Insertion at end of the list
- Insertion at any given position
- Delete a node from beginning
- Delete a node from the end
- Delete a node from any given position
- temp --> next = head
- head --> prev = temp
- temp --> prev = NULL
-               head= temp


---

# Content from Questions (DSA).md

# What will be the output of this question?
```Python
n=10
print("Number: ",n)
n=n+10
n=n-20
#n=n+30
print("New Number: ",n)
```

```Python
Number:  10
New Number:  0
```

```Python
Number: 10
New Number: 4
```

```Python
Number: 10
New Number: 11
```

```Python
Number: 10
New Number: 14
```

# What is the output for this question>
```Python

```

---

# Content from Notes (24-7-25).md

#DSA
Two types of commands: Primitive and Non-primitive
Non-primitive: User-defined and derived
You can access the member of the structure if you can access the variable of the structure

**Self referential Structure**
```cpp

struct Node
{
	int value;
	int a;
} s1,s2;
```

```cpp
s1.value = 5;
s1.a = 4;
s1.next = &s2;
s1.next.value = s2;
```
 
 ↑ **IMPORTANT**

```cpp
Struct Node
{
	int a = 5;
} S2;
```

```cpp
Struct Node
{
	Struct Node *next;
	
} s1,s2;
s1.next.next.a;
```
