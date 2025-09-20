

**SRM Institute of Science and Technology**  
_Full Visual + Code Flow Study Guide_

---

## 1. General Rules for C Programming

_(Already covered in previous section)_

---

## 2. Structure Access Workflow

mermaid

CopyEdit

`flowchart TD     A[Start Program] --> B[Define Structure using struct]     B --> C[Declare Structure Variable or Pointer]     C --> D{Access Type?}     D -->|Variable| E[Use Dot Operator: var.member]     D -->|Pointer| F[Use Arrow Operator: ptr->member]     E --> G[Process / Print Data]     F --> G     G --> H[End Program]`

**Example**:

c

CopyEdit

`struct Student {     char name[50];     int roll;     float marks; };  struct Student s1 = {"John", 101, 87.5}; printf("%s", s1.name);  // Dot operator  struct Student *ptr = &s1; printf("%s", ptr->name); // Arrow operator`

---

## 3. Matrix Multiplication – Algorithm Flow

mermaid

CopyEdit

`flowchart TD     A[Start] --> B[Input r1, c1, r2, c2]     B --> C{Check if c1 == r2?}     C -->|No| D[Invalid Order, Exit]     C -->|Yes| E[Allocate Memory for mat1, mat2, res]     E --> F[Input mat1 values]     F --> G[Input mat2 values]     G --> H[Initialize res to 0]     H --> I[Triple Nested Loop: i, j, k]     I --> J[Multiply mat1[i][k] * mat2[k][j]]     J --> K[Add to res[i][j]]     K --> L[End Loops]     L --> M[Print Result]     M --> N[Free Memory]     N --> O[End]`

---

## 4. Linked List – Basic Operations

### Creation + Traversal

mermaid

CopyEdit

`flowchart TD     A[Start] --> B[Create Head Node using malloc]     B --> C[Assign Data to Head]     C --> D{More Nodes?}     D -->|Yes| E[Allocate New Node]     E --> F[Assign Data]     F --> G[Link Prev Node to New Node]     G --> D     D -->|No| H[Traverse from Head]     H --> I[Print Data]     I --> J[End]`

---

### Insertion at Head

mermaid

CopyEdit

`flowchart TD     A[Start] --> B[Create New Node]     B --> C[Assign Data]     C --> D[Point New Node's Next to Current Head]     D --> E[Set Head to New Node]     E --> F[End]`

---

### Deletion of a Node

mermaid

CopyEdit

`flowchart TD     A[Start] --> B[Find Node to Delete]     B --> C[Adjust Pointers to Skip Node]     C --> D[Free Node Memory]     D --> E[End]`

---

## 5. Structure Pointer Access – Workflow

mermaid

CopyEdit

`flowchart TD     A[Declare Structure] --> B[Declare Pointer to Structure]     B --> C[Assign Address using &]     C --> D[Access Members using ->]     D --> E[Process Data]`

---

## 6. Time–Space Trade-off – Workflow

mermaid

CopyEdit

`flowchart LR     A[Algorithm Design] --> B{Need Faster?}     B -->|Yes| C[Use More Memory: Memoization, Precomputation]     B -->|No| D[Optimize for Less Memory]     C --> E[Balance Achieved]     D --> E`