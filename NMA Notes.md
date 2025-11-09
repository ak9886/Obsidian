---
updated_at: 2025-11-09T11:14:29.955+05:30
edited_seconds: 210
---
#Maths 


---

## **Bisection Method – Detailed Notes**

### **1. Introduction**

The **Bisection Method** is a numerical technique for finding the real root of a non-linear equation $$f(x) = 0$$. It is a **bracketing method**, meaning it starts with two initial guesses $$a$$ and $$b$$ such that $$f(a)$$ and $$f(b)$$ have opposite signs, i.e. $$f(a) \times f(b) < 0$$. By repeatedly halving the interval $$[a, b]$$, we narrow down the range where the root lies.

It is based on the **Intermediate Value Theorem**, which states that if a continuous function changes sign over an interval $$[a, b]$$, then there exists at least one real root in that interval.

---

### **2. Working Principle**

Let $$f(x)$$ be a continuous function on $$[a, b]$$ and $$f(a) \times f(b) < 0$$.

Define the midpoint:

$$x_m = \frac{a + b}{2}$$

Evaluate $$f(x_m)$$. There are three possible cases:

1. If $$f(x_m) = 0$$, then $$x_m$$ is the exact root.
    
2. If $$f(a) \times f(x_m) < 0$$, then the root lies between $$a$$ and $$x_m$$ → set $$b = x_m$$.
    
3. If $$f(x_m) \times f(b) < 0$$, then the root lies between $$x_m$$ and $$b$$ → set $$a = x_m$$.
    

This process is repeated until the **difference between successive midpoints** or **the function value** is smaller than a given tolerance $$\epsilon$$.

---

### **3. Algorithmic Steps**

Given a function $$f(x)$$ and an interval $$[a, b]$$ with $$f(a) \times f(b) < 0$$:

1. Compute the midpoint:  
    $$x_m = \frac{a + b}{2}$$
    
2. Evaluate $$f(x_m)$$.
    
3. Check the sign of $$f(a) \times f(x_m)$$:
    
    - If $$f(a) \times f(x_m) < 0$$, then the root lies between $$a$$ and $$x_m$$ → set $$b = x_m$$.
        
    - Else, the root lies between $$x_m$$ and $$b$$ → set $$a = x_m$$.
        
4. Compute the approximate error:  
    $$E = \left| \frac{b - a}{2} \right|$$
    
5. Repeat until $$E < \epsilon$$ or until $$|f(x_m)| < \epsilon$$.
    

---

### **4. Mathematical Derivation**

Let the function be $$f(x)$$ continuous in $$[a, b]$$ and $$f(a)f(b) < 0$$.  
After $$n$$ iterations, the interval length becomes:

$$L_n = \frac{b - a}{2^n}$$

The absolute error after $$n$$ iterations is approximately:

$$|x_r - x_m| \leq \frac{b - a}{2^n}$$

If we want the error less than a desired tolerance $$\epsilon$$, then:

$$\frac{b - a}{2^n} \leq \epsilon$$

Taking logarithms (base 2):

$$n \geq \log_2{\left( \frac{b - a}{\epsilon} \right)}$$

This gives the **minimum number of iterations** required to reach the desired accuracy.

---

### **5. Error Estimation**

At the end of each iteration, we can estimate the **approximate relative error**:

$$E_a = \left| \frac{x_{m}^{(i)} - x_{m}^{(i-1)}}{x_{m}^{(i)}} \right| \times 100%$$

Alternatively, the **absolute error** at the $$i^{th}$$ iteration is:

$$$$E_{abs}^{(i)} = \frac{b_i - a_i}{2}$$

---

### **6. Convergence**

The Bisection Method converges **linearly**.  
The **rate of convergence** is given as:

	$$|x_{i+1} - x^_| = \frac{1}{2} |x_i - x^_|$$

where $$x^*$$ is the true root.

Thus, the error reduces by half after each iteration, which is slower than methods like **Newton-Raphson** or **Secant**, but the method guarantees convergence if $$f(x)$$ is continuous and $$$$f(a) \times f(b) < 0$$.

---

### **7. Example**

Find the root of $$f(x) = x^3 - 4x - 9 = 0$$ between $$x = 2$$ and $$x = 3$$, correct up to $$\epsilon = 0.001$$.

**Step 1:**  
Compute $$f(2) = 2^3 - 4(2) - 9 = -9$$  
Compute $$f(3) = 3^3 - 4(3) - 9 = 6$$  
Since $$$$f(2)f(3) < 0$$, root lies between 2 and 3.

**Iteration 1:**  
$$x_m = \frac{2 + 3}{2} = 2.5$$  
$$f(2.5) = 2.5^3 - 4(2.5) - 9 = -3.375$$  
Since $$f(2)f(2.5) < 0$$ → set $$b = 2.5$$

**Iteration 2:**  
$$x_m = \frac{2 + 2.5}{2} = 2.25$$  
$$f(2.25) = 2.25^3 - 4(2.25) - 9 = -6.7969$$  
Still negative, so $$b = 2.25$$

**Iteration 3:**  
$$x_m = \frac{2.25 + 2.5}{2} = 2.375$$  
$$$$f(2.375) = 2.375^3 - 4(2.375) - 9 = -5.076$$  
Continue narrowing until $$$$|b - a| < 0.001$$.

The process yields a root near $$$$x = 2.915$$.

---

### **8. Termination Criteria**

The iteration continues until one of the following is satisfied:

1. $$|b - a| < \epsilon$$
    
2. $$|f(x_m)| < \epsilon$$
    
3. Maximum number of iterations reached $$n_{max}$$.
    

---

### **9. Flowchart**

1. Start
    
2. Input function $$f(x)$$, interval $$[a, b]$$, tolerance $$\epsilon$$.
    
3. Check $$f(a)f(b) < 0$$. If not, choose another interval.
    
4. Compute $$x_m = \frac{a + b}{2}$$.
    
5. Evaluate $$f(x_m)$$.
    
6. If $$f(x_m) = 0$$, print root.
    
7. Else, adjust $$a$$ or $$$$b$$ depending on the sign.
    
8. Repeat until desired accuracy.
    
9. Stop.
    

---

### **10. Advantages**

- Simple and robust method.
    
- Guaranteed convergence if function is continuous.
    
- Error bound known in advance.
    
- No need for derivative information.
    

---

### **11. Disadvantages**

- Convergence is **slow** (linear).
    
- Requires initial interval $$[a, b]$$ with opposite signs.
    
- Not suitable for multiple or closely spaced roots.
    
- Does not work if $$f(x)$$ does not change sign in interval.
    

---

### **12. Applications**

The Bisection Method is used for:

- Solving transcendental equations (e.g. $$\sin x = x$$).
    
- Engineering problems involving flow, equilibrium, and deflection where roots cannot be found analytically.
    
- Calibration of parameters when a known response (root) is targeted.
    
- Verification of other faster iterative methods like Newton-Raphson.
    

---

### **13. Generalized Formula Summary**

1. Midpoint at iteration $$i$$:  
    $$x_i = \frac{a_i + b_i}{2}$$
    
2. Function test condition:  
    $$f(a_i) \times f(x_i) < 0 \implies b_{i+1} = x_i$$  
    $$f(x_i) \times f(b_i) < 0 \implies a_{i+1} = x_i$$
    
3. Error per iteration:  
    $$E_i = \frac{b_i - a_i}{2}$$
    
4. Iteration estimate for accuracy $$\epsilon$$:  
    $$n \geq \log_2 \left( \frac{b - a}{\epsilon} \right)$$
    
5. Convergence:  
    $$|x_{i+1} - x^_| = \frac{1}{2}|x_i - x^_|$$
    
6. Approximate error percentage:  
    $$$$E_a = \left| \frac{x_i - x_{i-1}}{x_i} \right| \times 100%$$
    

---

### **14. Tabular Form of Iteration Example**

|Iteration|a|b|Midpoint $$x_m$$|$$f(a)$$|$$f(x_m)$$|Interval|Error $$$$E$$|
|---|---|---|---|---|---|---|---|
|1|2.0|3.0|2.5|-9|-3.375|[2, 2.5]|0.5|
|2|2.0|2.5|2.25|-9|-6.797|[2, 2.25]|0.25|
|3|2.25|2.5|2.375|-6.797|-5.076|[2.25, 2.5]|0.125|
|4|2.375|2.5|2.4375|-5.076|-4.072|[2.375, 2.5]|0.0625|
|...|...|...|...|...|...|...|...|

This tabulation continues until the tolerance criterion is met.

---

### **15. Pseudocode**

```
Input f(x), a, b, tolerance ε
If f(a)*f(b) > 0
    Print "Invalid interval"
Else
    Repeat
        x_m = (a + b) / 2
        If f(a)*f(x_m) < 0
            b = x_m
        Else
            a = x_m
        EndIf
    Until |b - a| < ε
EndIf
Output x_m as approximate root
```

---

### **16. Numerical Accuracy Discussion**

The Bisection Method provides a guaranteed error reduction. After each iteration:

$$E_{n+1} = \frac{E_n}{2}$$

Hence, after $$n$$ iterations:

$$E_n = \frac{E_0}{2^n}$$

If the initial interval length is $$E_0 = b - a$$, then:

$$E_n = \frac{b - a}{2^n}$$

For example, if $$b - a = 1$$ and $$\epsilon = 10^{-3}$$, then:

$$$$n = \log_2(1000) \approx 10$$ iterations.

---

### **17. Comparison with Other Methods**

|Method|Requirement|Order of Convergence|Speed|Guarantee|
|---|---|---|---|---|
|Bisection|$$f(a)f(b) < 0$$|1 (Linear)|Slow|Guaranteed|
|Regula-Falsi|$$f(a)f(b) < 0$$|1 (Slightly faster)|Moderate|Guaranteed|
|Newton-Raphson|Derivative $$$$
f'(x)$$ required|2 (Quadratic)|Fast|Not guaranteed|
|Secant|Two initial guesses|1.62|Faster|Not guaranteed|

---

### **18. Key Observations**

- Each iteration halves the interval → precision doubles.
    
- Accuracy can be pre-estimated before starting.
    
- Works best for single, simple roots.
    
- Suitable for computer implementation due to its predictable loop and logic.
    

---

### **19. Compact Formula Summary**

1. $$$$x_{mid} = \frac{a + b}{2}$$
    
2. $$$$f(a)f(x_{mid}) < 0 \implies b = x_{mid}$$
    
3. $$f(x_{mid})f(b) < 0 \implies a = x_{mid}$$
    
4. $$$$E = \frac{b - a}{2}$$
    
5. Stop when $$
$$E < \epsilon$$

---

### **20. Final Remarks**

The **Bisection Method** stands out as the most **reliable and systematic** bracketing technique in numerical computation. Despite being slower than open methods like Newton-Raphson, its **predictable convergence**, **error control**, and **independence from derivatives** make it the foundational approach for root-finding problems in computational mathematics and engineering.

---

**Q1:** What is the mathematical difference between linear and quadratic convergence in numerical methods?  
**Q2:** How does the Bisection Method’s error bound compare to that of Regula-Falsi?  
**Q3:** Why does the Bisection Method fail when $$f(a)f(b) > 0$$ even if $$f(x)$$ crosses zero between them?

