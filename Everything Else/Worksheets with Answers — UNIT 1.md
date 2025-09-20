**SRM Institute of Science and Technology — School of Computing**  
**Course:** 21CSC201J – Data Structures and Algorithms

---

## Topic: General Rules for C Programming and Primitive Data Types  

**Activity: Match the following**

1. `int` — A. Format specifier for float  
2. `float` — B. Format specifier for integers  
3. `char` — C. Preprocessor directive  
4. `main()` — D. Statement terminator  
5. `return 0;` — E. Format specifier for characters  
6. `#include<stdio.h>` — F. Keyword to start main function  
7. `;` (semicolon) — G. Used to store whole numbers  
8. `%d` — H. Used to print characters  
9. `%f` — I. Floating-point data type  
10. `%c` — J. Ends a function and returns value to OS  

**Answers:**  
1 - G  
2 - I  
3 - H  
4 - F  
5 - J  
6 - C  
7 - D  
8 - B  
9 - A  
10 - E

---

## Topic: Define, Declare and Access the Structure  

**Activity: Fill in the Blanks**

1. A structure in C is defined using the `struct` keyword.  
2. Syntax: `struct StructName { members };`  
3. Declare variable at definition: `struct StructName { members } varName;`  
4. Access with variable: dot (`.`) operator  
5. Access with pointer: arrow (`->`) operator  
6. Declare after definition: `struct StructName varName;`  
7. Pointer to structure: `struct StructName *ptr;`  
8. Assign address: `ptr = &varName;`  
9. Structures group variables into a single user-defined type.  
10. Structure definitions end with a semicolon (`;`).

---

### Practice Code — Define, Declare, Access Structure

```c
#include <stdio.h>

struct Student {
    char name[50];
    int rollNumber;
    float marks;
};

int main() {
    struct Student s1 = {"John", 101, 87.5};
    printf("Name: %s\n", s1.name);
    printf("Roll Number: %d\n", s1.rollNumber);
    printf("Marks: %.2f\n", s1.marks);
    return 0;
}
```

---

## Topic: Array of Structures  

**Activity: Fill in the Blanks**

1. Store multiple structure variables of the same type.  
2. Syntax: `struct StructName arrayName[size];`  
3. Access: `arrayName[index].memberName`  
4. Example: `struct Student s[5];` = 5 structure variables.  
5. Used for student records, employee details, etc.  
6. Usually read values with a loop.  
7. Access 3rd element’s `name`: `emp[2].name`  
8. Each element is accessed like a normal array element.  
9. Pointer to structure array: `struct StructName *ptr = arrayName;`  
10. Print details with a loop and dot operator.

---

### Practice Code — Array of Structures

```c
#include <stdio.h>

struct Car {
    char model[30];
    int year;
};

int main() {
    struct Car cars[3] = {
        {"Toyota", 2015},
        {"Honda", 2018},
        {"Ford", 2020}
    };
    for (int i = 0; i < 3; i++) {
        printf("Car %d: %s (%d)\n", i+1, cars[i].model, cars[i].year);
    }
    return 0;
}
```

---

## Topic: Nested Structures  

**Activity: Fill in the Blanks**

1. Nested structure = structure inside another structure.  
2. Keyword: `struct`  
3. Access syntax: `outer.inner.member`  
4. Dot (`.`) operator used multiple times.  
5. Inner structure = nested structure.  
6. Memory allocated during variable declaration.  
7. Inner structure = structure contained inside.  
8. Groups related sets of information.  
9. Example: `student.address.age` — **False**  
10. Correct: `outerStruct.innerStruct.member`

---

### Practice Code — Nested Structures

```c
#include <stdio.h>

struct Date {
    int day, month, year;
};

struct Employee {
    char name[50];
    struct Date joiningDate;
};

int main() {
    struct Employee e1 = {"David", {15, 5, 2023}};
    printf("Employee Name: %s\n", e1.name);
    printf("Joining Date: %02d-%02d-%04d\n",
           e1.joiningDate.day, e1.joiningDate.month, e1.joiningDate.year);
    return 0;
}
```

---

## Topic: Implementation of Structures using C Program  

**Activity: Match the Following**  
*(Abbreviated mapping for reference; see PDF for all 20)*  

1 - O  
2 - M  
3 - T  
4 - K  
5 - P  
6 - R  
7 - S  
8 - N  
9 - L  
10 - Q  
11 - D  
12 - I  
13 - B  
14 - H  
15 - A  
16 - E  
17 - J  
18 - F  
19 - G  
20 - C

---

## Topic: Self-referential Structure and Structure Pointer  

**Activity: Match the Following**  
*(Abbreviated mapping for reference)*  

1 - P  
2 - O  
3 - L  
4 - R  
5 - M  
6 - T  
7 - N  
8 - K  
9 - Q  
10 - S  
11 - H  
12 - C  
13 - E  
14 - G  
15 - B  
16 - A  
17 - I  
18 - D  
19 - J  
20 - F

---

## Topic: Implementation of Structures using Pointers  

**Activity: Fill in the Blanks**

1. Structure pointer declared with asterisk (`*`).  
2. Arrow operator (`->`) accesses members via pointer.  
3. Stores **address** of structure variable.  
4. Assign address: `ptr = &var;`  
5. Enables indirect access.  
6. Must allocate memory before use.  
7. Passing pointer allows in-place changes.  
8. `(*ptr).member` same as `ptr->member`.  
9. Reduces data copying.  
10. Allocate with `malloc()`.  
11. Use `sizeof(struct)` with `malloc`.  
12. Free unused pointers.  
13. Enables dynamic structures (linked lists).  
14. Must initialize to avoid segmentation fault.  
15. Arrow operator combines dereference + member access.

---

## Topic: Dynamic Memory Allocation  

**Activity: Fill in the Blanks**

1. Allocated at run time.  
2. `malloc()` allocates memory.  
3. `free()` deallocates memory.  
4. `calloc()` allocates + initializes to zero.  
5. `realloc()` resizes memory.  
6. `sizeof()` gives size.  
7. Memory leak if not freed.  
8. `malloc()` returns `void*`.  
9. Type cast in C for `malloc`.  
10. Returns `NULL` if allocation fails.  
11. `(int*) malloc(5 * sizeof(int))` → 5 integers.  
12. Access with pointer dereference.  
13. Dynamic arrays use heap.  
14. Static arrays use stack.  
15. Using memory after free = dangling pointer.

---

### Practice Code — Dynamic Memory Allocation

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr = (int*) malloc(10 * sizeof(int));
    if (arr == NULL) {
        printf("Allocation failed.");
        return 1;
    }
    for (int i = 0; i < 10; i++) arr[i] = i * 2;
    arr = (int*) realloc(arr, 20 * sizeof(int));
    free(arr);
    return 0;
}
```

---

## Topic: Matrix Multiplication (Dynamic Memory Allocation)

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int r1, c1, r2, c2;
    int **mat1, **mat2, **res;
    int i, j, k;

    scanf("%d %d", &r1, &c1);
    scanf("%d %d", &r2, &c2);

    if (c1 != r2) {
        printf("Invalid Order of matrix");
        return 0;
    }

    mat1 = (int**) malloc(r1 * sizeof(int*));
    for (i = 0; i < r1; i++)
        mat1[i] = (int*) malloc(c1 * sizeof(int));

    mat2 = (int**) malloc(r2 * sizeof(int*));
    for (i = 0; i < r2; i++)
        mat2[i] = (int*) malloc(c2 * sizeof(int));

    res = (int**) calloc(r1, sizeof(int*));
    for (i = 0; i < r1; i++)
        res[i] = (int*) calloc(c2, sizeof(int));

    for (i = 0; i < r1; i++)
        for (j = 0; j < c1; j++)
            scanf("%d", &mat1[i][j]);

    for (i = 0; i < r2; i++)
        for (j = 0; j < c2; j++)
            scanf("%d", &mat2[i][j]);

    for (i = 0; i < r1; i++)
        for (j = 0; j < c2; j++)
            for (k = 0; k < c1; k++)
                res[i][j] += mat1[i][k] * mat2[k][j];

    printf("\nResult:\n");
    for (i = 0; i < r1; i++) {
        for (j = 0; j < c2; j++)
            printf("%d\t", res[i][j]);
        printf("\n");
    }

    return 0;
}
```

---

## Topic: Data Structure — Definition, Types  

**Activity: Fill in the Blanks**

1. Data Structure = way to organize/store data for efficient access & modification.  
2. Types: Linear, Non-linear.  
3. Linear = sequential arrangement.  
4. Queue = FIFO example.  
5. Tree = hierarchical structure.  
6. Graph = network-like structure.  
7. Stack ops = Push, Pop.  
8. Array = indexed collection.  
9. Linked List = nodes linked by pointers.  
10. Importance = efficient storage & retrieval.

---

## Topic: Data Structure Operations & ADT  

**Activity: Fill in the Blanks**

- Insertion = add element  
- Deletion = remove element  
- Traversal = access all elements  
- Searching = find element  
- Sorting = arrange order  
- Stack insert = Push  
- Stack delete = Pop  
- Queue insert = Enqueue  
- Queue delete = Dequeue  
- Linked list traversal = visit each node once  
- Binary search = sorted array only  
- Copying = duplicate data structure  
- Queue insert end = Rear  
- Queue delete end = Front  
- Stack = LIFO

---

## Topic: Mathematical & Asymptotic Notations  

- Big O = Upper bound (worst)  
- Big Ω = Lower bound (best)  
- Big Θ = Tight bound (avg)  
- Linear Search: O(n)  
- Binary Search: O(log n)  
- Bubble Sort worst: O(n²)  
- Ignore constants & lower terms in Big O.  
- O(1) = constant time

---

## Topic: Complexity — Time, Space Trade-off  

- Time complexity = runtime  
- Space complexity = memory usage  
- Trade-off = balance time vs. space  
- More memory → faster  
- Less memory → slower  
- Memoization = save results to speed up  
- Recursive → uses more space  
- Goal = optimal balance
