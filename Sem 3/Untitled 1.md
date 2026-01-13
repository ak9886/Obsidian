---
updated_at: 2025-11-16T09:08:26.821+05:30
edited_seconds: 240
---
# Question
![[WhatsApp Image 2025-11-16 at 01.35.21_32ba9acb.jpg]]
# **Answer**

## **1. Data Setup**

|Year (x)|Population (y)|
|---|---|
|1941|20|
|1951|24|
|1961|29|
|1971|36|
|1981|46|
|1991|51|

- $( x_0 = 1941 )$
    
- $( y_0 = 20 )$
    
- $( h = 10 )$
    
- We want ( $y(1946)$)
    

Compute:

$$[  
u = \frac{1946 - 1941}{10} = 0.5  
]$$

---

## **2. Forward Difference Table (Unified + Correct)**

This table merges both of your versions, fixes inconsistencies, and presents all orders cleanly.

| ($x$) index | Year | ($y$) | $(\Delta y)$ | $(\Delta^2 y$) | $(\Delta^3 y)$ | $(\Delta^4 y)$ | $(\Delta^5 y)$ |
| ----------- | ---- | ----- | ------------ | -------------- | -------------- | -------------- | -------------- |
| 0           | 1941 | 20    | 4            | 1              | 1              | 0              | -9             |
| 1           | 1951 | 24    | 5            | 2              | 1              | -9             |                |
| 2           | 1961 | 29    | 7            | 3              | -8             |                |                |
| 3           | 1971 | 36    | 10           | -5             |                |                |                |
| 4           | 1981 | 46    | 5            |                |                |                |                |
| 5           | 1991 | 51    |              |                |                |                |                |

### **Difference relations**

$$[  
\Delta y_i = y_{i+1} - y_i  
]$$  
$$[  
\Delta^2 y_i = \Delta y_{i+1} - \Delta y_i  
]$$  
$$[  
\Delta^3 y_i = \Delta^2 y_{i+1} - \Delta^2 y_i  
]$$  
And so on.

---

## **3. Newton Forward Formula**

$$[  
y(x)=y_0  
+u\Delta y_0  
+\frac{u(u-1)}{2!}\Delta^2 y_0  
+\frac{u(u-1)(u-2)}{3!}\Delta^3 y_0  
+\frac{u(u-1)(u-2)(u-3)}{4!}\Delta^4 y_0  
+\cdots  
]$$

Plug in known values from the unified table:

- $(y_0 = 20)$
    
- $(\Delta y_0 = 4)$
    
- $(\Delta^2 y_0 = 1)$
    
- $(\Delta^3 y_0 = 1)$
    
- $(\Delta^4 y_0 = 0)$
    
- (so the 4th-order term contributes zero)
    

---

## **4. Evaluate Each Term (Merged Version)**

### **Term 1**

$$[  
20  
]$$

### **Term 2**

$$[  
u\Delta y_0 = 0.5 \times 4 = 2  
]$$

### **Term 3**

$$[  
\frac{u(u-1)}{2} \Delta^2 y_0  
= \frac{0.5(-0.5)}{2} \times 1  
= -0.125  
]$$

### **Term 4**

$$[  
\frac{u(u-1)(u-2)}{6} \Delta^3 y_0  
= \frac{0.5(-0.5)(-1.5)}{6} \times 1  
]$$

Compute numerator:
$$
(0.5 \times -0.5 = -0.25)
$$    
$$ (-0.25 \times -1.5 = 0.375)
    
$$
Then:

$$[  
\frac{0.375}{6} = 0.0625  
]$$

### **Term 5**

$$[  
\Delta^4 y_0 = 0 \quad \Rightarrow \quad \text{term } = 0  
]$$

---

## **5. Sum Everything (Unified Final)**

$$[  
y(1946)  
= 20 + 2 - 0.125 + 0.0625  
]$$

$$[  
= 21.9375  
]$$

Rounded:

## **$\boxed{21.94\text{ lakhs}}$**


---
