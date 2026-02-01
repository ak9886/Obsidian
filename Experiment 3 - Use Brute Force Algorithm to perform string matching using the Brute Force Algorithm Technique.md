---
updated_at: 2026-02-01T22:11:17.595+05:30
edited_seconds: 40
---
## **Aim**

To develop and implement a program that performs **string matching using the Brute Force algorithm**, identify all starting indices where a given pattern occurs in a text, and understand the algorithm’s working through direct character comparisons.

---

## **Algorithm**

```
Input: text, pattern
Let n = length of text
Let m = length of pattern
Set found = false

For i from 0 to (n - m):
    Set j = 0
    While j < m AND text[i + j] == pattern[j]:
        j = j + 1
    If j == m:
        Print "Pattern found at index i"
        found = true

If found == false:
    Print "Pattern not found"
```

---

## **Code**

```c
#include <stdio.h>
#include <string.h>

int main() {
    char text[100], pattern[100];
    int i, j;
    int found = 0;

    printf("Enter the main string (text): ");
    scanf("%s", text);

    printf("Enter the pattern string: ");
    scanf("%s", pattern);

    int n = strlen(text);
    int m = strlen(pattern);

    for (i = 0; i <= n - m; i++) {
        for (j = 0; j < m; j++) {
            if (text[i + j] != pattern[j]) {
                break;
            }
        }

        if (j == m) {
            printf("Pattern found at index %d\n", i);
            found = 1;
        }
    }

    if (!found) {
        printf("Pattern not found in the given text.\n");
    }

    return 0;
}
```

---

## **Output**

### **Sample Input**

```
Enter the main string (text): AABAACAADAABAABA
Enter the pattern string: AABA
```

### **Sample Output**

```
Pattern found at index 0
Pattern found at index 9
Pattern found at index 12
```

---

### **Sample Input (Pattern Not Found)**

```
Enter the main string (text): ABCDEFG
Enter the pattern string: HIJ
```

### **Sample Output**

```
Pattern not found in the given text.
```

