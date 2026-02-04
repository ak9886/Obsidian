---
updated_at: 2026-02-04T22:05:41.397+05:30
edited_seconds: 100
---
## **A1. Caesar Cipher**

### **1(a) Encrypt “SECURITY” with key = 4**

Caesar Cipher rule:  
[  
C = (P + k) \bmod 26  
]

|Plain|Position|+4|Cipher|
|---|---|---|---|
|S|18|22|W|
|E|4|8|I|
|C|2|6|G|
|U|20|24|Y|
|R|17|21|V|
|I|8|12|M|
|T|19|23|X|
|Y|24|2|C|

**Encrypted text:**  
$[\boxed{\text{WIGYVMXC}}]$

---

### **1(b) Decrypt “WKHQ”**

Decryption rule:  
[  
P = (C - k) \bmod 26  
]

|Cipher|−4|Plain|
|---|---|---|
|W|S||
|K|G||
|H|D||
|Q|M||

**Decrypted text:**  
$\boxed{\text{SGDM}}$

---

## **A2. Playfair Cipher**

### **2(a) Playfair Matrix using keyword: MONARCHY**

Rules:

- Combine **I/J**
    
- Remove duplicates
    

**Matrix:**

|M|O|N|A|R|
|---|---|---|---|---|
|C|H|Y|B|D|
|E|F|G|I|K|
|L|P|Q|S|T|
|U|V|W|X|Z|

---

### **Encrypt “INSTRUMENT”**

Prepare digraphs:

```
IN ST RU ME NT
```

Apply Playfair rules:

|Digraph|Rule|Cipher|
|---|---|---|
|IN|Rectangle|GA|
|ST|Same row|TL|
|RU|Rectangle|MX|
|ME|Rectangle|CE|
|NT|Rectangle|RQ|

**Ciphertext:**  
$\boxed{\text{GATLMXCERQ}}$

---

### **2(b) Encrypt “BALLOON” (digraph formation)**

Step 1: Split and insert filler **X**

```
BA LX LO ON
```

Encrypt each digraph:

|Digraph|Cipher|
|---|---|
|BA|DB|
|LX|SU|
|LO|PM|
|ON|NA|

**Ciphertext:**  
$\boxed{\text{DBSUPMNA}}$

---

## **A3. Hill Cipher**

### **3(a) Encrypt “HELP”**

Key matrix:  
$$$$$


Plaintext values:

```
H=7, E=4, L=11, P=15
```

Vectors:  
[  
\begin{bmatrix}7\4\end{bmatrix},  
\begin{bmatrix}11\15\end{bmatrix}  
]

# **First block:**  
[  
\begin{bmatrix}  
3 & 3\  
2 & 5  
\end{bmatrix}  
\begin{bmatrix}  
7\4  
\end{bmatrix}

# \begin{bmatrix}  
33\34  
\end{bmatrix}  
\bmod 26

\begin{bmatrix}  
7\8  
\end{bmatrix}  
\Rightarrow HI  
]

**Second block:**  
[  
\Rightarrow \begin{bmatrix}6\19\end{bmatrix} = GT  
]

**Ciphertext:**  
[  
\boxed{\text{HIGT}}  
]

---

### **3(b) Validity of key matrix**

Determinant:  
[  
\det(K) = (3×5 - 3×2) = 9  
]

[  
\gcd(9,26) = 1  
]

✅ **Valid Hill Cipher key**

---

## **A4. Modular Arithmetic**

### **4(a)**

[  
(17 + 20) \bmod 26 = \boxed{11}  
]

### **4(b)**

[  
(7 × 9) \bmod 26 = \boxed{11}  
]

---

### **Multiplicative inverse of 5 mod 7**

Trial method:

[  
5 × 3 = 15 \equiv 1 \pmod{7}  
]

[  
\boxed{5^{-1} \equiv 3 \pmod{7}}  
]

---

## **A5. Euclidean Algorithm**

### **Find GCD**

[  
26 = 7×3 + 5  
]  
[  
7 = 5×1 + 2  
]  
[  
5 = 2×2 + 1  
]

[  
\boxed{\gcd(26,7)=1}  
]

---

### **Extended Euclidean Algorithm**

Back-substitution:  
[  
1 = 5 - 2×2  
]  
[  
= 5 - (7 - 5)×2  
]  
[  
= 3×5 - 2×7  
]

Since:  
[  
5 = 26 - 7×3  
]

[  
1 = 3×26 - 11×7  
]

[  
\boxed{7^{-1} \equiv 15 \pmod{26}}  
]

---

## **A6. Finite Fields**

### **Multiply in GF(2³)**

Given:  
[  
(101) × (011)  
]

Binary multiplication:  
[  
= 1111  
]

Reduce using irreducible polynomial:  
[  
x^3 + x + 1  
]

Final result:  
[  
\boxed{010}  
]

---

# **SECTION B — THEORY**

---

## **B1. Classical Ciphers**

### **Why Hill Cipher is more secure than Caesar**

- Caesar uses **single-letter substitution**
    
- Hill uses **matrix-based polygraphic substitution**
    
- Frequency analysis fails in Hill Cipher
    

---

### **Monoalphabetic vs Polygraphic**

|Feature|Mono|Poly|
|---|---|---|
|Unit|Single letter|Letter blocks|
|Example|Caesar|Hill|
|Security|Low|High|

---

## **B2. Playfair Cipher**

### **Role of digraph substitution**

- Hides letter frequencies
    
- Prevents simple frequency attacks
    
- Each letter depends on its pair
    

---

### **Why I/J combined**

- 5×5 matrix limitation
    
- Slight ambiguity, negligible security loss
    

---

## **B3. Hill Cipher & Linear Algebra**

### **Why determinant condition is mandatory**

Decryption requires:  
[  
K^{-1} \bmod 26  
]

Exists **only if**:  
[  
\gcd(\det(K),26)=1  
]

---

### **If determinant not coprime**

- No inverse exists
    
- Decryption becomes impossible
    
- Cipher collapses
    

---

## **B4. Number Theory**

### **Why modular inverse exists only when**

[  
\boxed{\gcd(a,n)=1}  
]

---

### **Why modular arithmetic is a ring**

- Closed under + and ×
    
- Additive inverses exist
    
- Multiplicative inverses **don’t always exist**
    

So it’s **not always a field**.

---

## **B5. Finite Fields**

### **Why irreducible polynomials are required**

- Ensure **every non-zero element has an inverse**
    
- Maintain field properties
    

❌ Reducible polynomial ⇒ zero divisors ⇒ not a field

---

If you want:

- **Exam-format PDF**
    
- **Handwritten-style solution**
    
- **Marks breakdown**
    
- **Short answers only**
    

say the word.

**Q1:** **Which of these answers would lose marks if written without steps?**  
**Q2:** **Do you want the same answers compressed into 2-mark / 5-mark versions?**  
**Q3:** **Should I generate a mock CNS question paper using these exact concepts?**