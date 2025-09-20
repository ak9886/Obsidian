---
updated_at: 2025-09-04T08:39:56.160+05:30
edited_seconds: 900
---
# Circular Linked List

- A linked list that is circular, i.e., it can relate to itself
[[ExcaliNotes (4-9-2025)]]


# Inserting a new Node at beginning
Steps:
- Step 1: Create a `newNode` with given value
- Step 2: Check whether list is Empty (`head==NULL`)
- Step 3: If it is `Empty`, then set head =`newNode` and `newNode -> next = head`
- Step 4: If it is not `Empty`, then define a node pointer temp and initialize with head
- Step 5: Keep moving the temp to its next node until it reaches to the last node in the list (until temp -> next == head)
- Step 6: Set `temp -> next = newNode` and `newNode -> next = head`

# Inserting at a specific point
- ## Step 1: 
	- ##### Create a `newNode` with given value
- ## Step 2: 
	- ##### Check whether list is empty `(head == NULL)`
- ## Step 3:
	- ##### Initialize `temp` and `temp1` and set `temp = head` and `temp1= temp -> next`

# Deletion of a value in CLL
- ## Step 1:
	- `temp = head`
- ## Step 2:
	- `head = head->next`
- ## Step 3:
	- `free(temp)` (<font color="#ff0000">Dynamic Memory Allocation Method</font>)
- ## Step 4:
	- `temp - head
- ## Step 5:
	- `while (temp -> next !=head)`
	-       `temp = temp -> next`
	-       `temp1 -> next = head`
	-       `free(temp)`

```C Language
/* See Josephus Problem*/
```
