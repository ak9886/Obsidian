---
updated_at: 2025-11-09T11:23:45.460+05:30
edited_seconds: 430
---
#Maths 


---

## **Bisection Method**

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
$$
\lvert x_{i+1} - x^{*} \rvert \le \tfrac{1}{2} \lvert x_i - x^{*} \rvert
$$

where $$x^*$$ is the true root.

Thus, the error reduces by half after each iteration, which is slower than methods like **Newton-Raphson** or **Secant**, but the method guarantees convergence if $$f(x)$$ is continuous and $$$$$$f(a) \times f(b) < 0$$.

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
Since $$f(2)f(2.5) < 0$$ → set $$$$b = 2.5$$

**Iteration 2:**  
$$x_m = \frac{2 + 2.5}{2} = 2.25$$  
$$f(2.25) = 2.25^3 - 4(2.25) - 9 = -6.7969$$  
Still negative, so $$b = 2.25$$

**Iteration 3:**  
$$x_m = \frac{2.25 + 2.5}{2} = 2.375$$  
$$$$$$f(2.375) = 2.375^3 - 4(2.375) - 9 = -5.076$$  
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
    
7. Else, adjust $$a$$ or $$$$$$b$$ depending on the sign.
    
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
    $$
\lvert x_{i+1} - x^{*} \rvert \le \tfrac{1}{2} \lvert x_i - x^{*} \rvert
$$

6. Approximate error percentage:  
    $$$$$$E_a = \left| \frac{x_i - x_{i-1}}{x_i} \right| \times 100%
    
$$
---

### **14. Tabular Form of Iteration Example**

|Iteration|a|b|Midpoint$$x_m$$|$$f(a)$$|$$f(x_m)$$|Interval|Error $$$$E$$|
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

$$$$$$n = \log_2(1000) \approx 10$$ iterations.

---

### **17. Comparison with Other Methods**

|Method|Requirement|Order of Convergence|Speed|Guarantee|
|---|---|---|---|---|
|Bisection|$$f(a)f(b) < 0$$|1 (Linear)|Slow|Guaranteed|
|Regula-Falsi|$$f(a)f(b) < 0$$|1 (Slightly faster)|Moderate|Guaranteed|
|Newton-Raphson|Derivative $$$$
$$f'(x)$$ required|2 (Quadratic)|Fast|Not guaranteed|
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

## **Regula–Falsi Method**

### **1. Introduction**

The **Regula–Falsi Method**, also known as the **Method of False Position**, is a bracketing technique used to determine the root of a nonlinear equation  
$$  
f(x) = 0  
$$  
It combines the reliability of the **Bisection Method** with the faster convergence tendency of **linear interpolation**.

Unlike the Bisection Method, which simply halves the interval each time, Regula–Falsi estimates the root by drawing a **secant line** between two points on the curve and using the **x-intercept of that line** as the next approximation.

---

### **2. Geometrical Concept**

Consider two points on the function curve:  
$$  
(x_0, f(x_0)) \quad \text{and} \quad (x_1, f(x_1))  
$$  
such that $$f(x_0)f(x_1) < 0$$, meaning the root lies between them.

A straight line joining these points intersects the x-axis at some point $$x_2$$. This intersection is a better estimate of the actual root.

The equation of the line passing through these two points is:  
$$  
y - f(x_0) = \frac{f(x_1) - f(x_0)}{x_1 - x_0} (x - x_0)  
$$

Setting $$y = 0$$ to find where the line crosses the x-axis gives:  
$$  
0 - f(x_0) = \frac{f(x_1) - f(x_0)}{x_1 - x_0} (x_2 - x_0)  
$$

Solving for $$x_2$$:  
$$  
x_2 = x_0 - f(x_0) \frac{x_1 - x_0}{f(x_1) - f(x_0)}  
$$

This is the **main formula of the Regula–Falsi Method**.

---

### **3. Iterative Formula**

For subsequent iterations, the formula generalizes as:  
$$  
x_{i+1} = x_i - f(x_i) \frac{x_{i-1} - x_i}{f(x_{i-1}) - f(x_i)}  
$$

Each iteration uses the two most recent points that bracket the root.

---

### **4. Step-by-Step Algorithm**

1. Choose two initial approximations $$x_0$$ and $$x_1$$ such that $$f(x_0)f(x_1) < 0$$.
    
2. Compute:  
    $$  
    x_2 = x_0 - f(x_0)\frac{x_1 - x_0}{f(x_1) - f(x_0)}  
    $$
    
3. Evaluate $$f(x_2)$$.
    
4. If $$f(x_0)f(x_2) < 0$$, then set $$x_1 = x_2$$ (root lies between $$x_0$$ and $$x_2$$).  
    If $$f(x_1)f(x_2) < 0$$, then set $$x_0 = x_2$$ (root lies between $$x_2$$ and $$x_1$$).
    
5. Repeat steps 2–4 until:  
    $$  
    \lvert f(x_2) \rvert < \epsilon \quad \text{or} \quad \lvert x_{i+1} - x_i \rvert < \epsilon  
    $$
    

---

### **5. Derivation of the Formula**

The slope of the secant joining the two points is:  
$$  
m = \frac{f(x_1) - f(x_0)}{x_1 - x_0}  
$$

Equation of the secant line:  
$$  
y - f(x_0) = m(x - x_0)  
$$

Setting $$y = 0$$ gives:  
$$  
x = x_0 - \frac{f(x_0)}{m}  
$$

Substituting for $$m$$:  
$$  
x_2 = x_0 - f(x_0)\frac{x_1 - x_0}{f(x_1) - f(x_0)}  
$$

This formula effectively replaces the midpoint formula of the Bisection Method with a **weighted linear interpolation**, giving faster convergence.

---

### **6. Error and Convergence**

Let the true root be $$x^{*}$$.  
The error after the $$i^{th}$$ iteration is:  
$$  
E_i = \lvert x_{i} - x^{} \rvert  
$$

The convergence rate is **super-linear**, slower than Newton–Raphson but faster than Bisection.  
Empirically, the rate of convergence is approximately between **1.2 and 1.4**.

---

### **7. Iteration Termination**

The process stops when:  
$$  
\lvert f(x_{i+1}) \rvert < \epsilon \quad \text{or} \quad \lvert x_{i+1} - x_i \rvert < \epsilon  
$$  
where $$\epsilon$$ is a small positive tolerance.

Alternatively, a fixed maximum iteration count $$n_{max}$$ may be set.

---

### **8. Example**

Find the root of:  
$$  
f(x) = x^3 - 5x + 1 = 0  
$$  
using Regula–Falsi, correct to three decimal places.

**Step 1:**  
Choose $$x_0 = 0$$ and $$x_1 = 1$$.

$$f(0) = 1, \quad f(1) = -3$$  
Since $$f(0)f(1) < 0$$, the root lies between 0 and 1.

**Iteration 1:**  
$$  
x_2 = 0 - 1 \times \frac{1 - 0}{-3 - 1} = 0.25  
$$  
$$f(0.25) = 0.25^3 - 5(0.25) + 1 = -0.9375$$  
Now, $$f(0)f(0.25) < 0$$ → new interval is [0, 0.25].

**Iteration 2:**  
$$  
x_3 = 0 - 1 \times \frac{0.25 - 0}{-0.9375 - 1} = 0.117  
$$  
$$f(0.117) = 0.117^3 - 5(0.117) + 1 = 0.415$$  
Root lies between $$x_2 = 0.117$$ and $$x_1 = 0.25$$.

Continue iterations until:  
$$  
\lvert x_{i+1} - x_i \rvert < 0.001  
$$

Final result:  
$$x \approx 0.202$$

---

### **9. Graphical Interpretation**

- In each iteration, Regula–Falsi draws a **secant** through the two current points on $$f(x)$$.
    
- The point where the secant cuts the x-axis is used as the new estimate of the root.
    
- Only **one endpoint** is updated each time — the one that has the same sign as the new $$f(x)$$ value.
    

This makes the interval **shrink asymmetrically**, unlike in the Bisection Method.

---

### **10. Flow of Computation**

1. Start
    
2. Input $$f(x)$$, $$x_0$$, $$x_1$$, $$\epsilon$$
    
3. Check $$f(x_0)f(x_1) < 0$$
    
4. Compute $$x_2 = x_0 - f(x_0)\frac{x_1 - x_0}{f(x_1) - f(x_0)}$$
    
5. Evaluate $$f(x_2)$$
    
6. If $$f(x_0)f(x_2) < 0$$ → set $$x_1 = x_2$$  
    Else → set $$x_0 = x_2$$
    
7. Check for convergence
    
8. Repeat until condition met
    
9. Output $$x_2$$
    

---

### **11. Formula Summary**

1. **Main Iteration:**  
    $$  
    x_{i+1} = x_i - f(x_i)\frac{x_{i-1} - x_i}{f(x_{i-1}) - f(x_i)}  
    $$
    
2. **Error:**  
    $$  
    E_i = \lvert x_{i+1} - x_i \rvert  
    $$
    
3. **Stopping Criterion:**  
    $$  
    E_i < \epsilon \quad \text{or} \quad \lvert f(x_{i+1}) \rvert < \epsilon  
    $$
    

---

### **12. Comparison with Bisection**

|Property|Bisection|Regula–Falsi|
|---|---|---|
|Basis|Interval halving|Linear interpolation|
|Speed|Slower|Faster|
|Convergence|Linear|Super-linear|
|Derivatives|Not required|Not required|
|Guarantee|Always convergent|Convergent but slower if slope imbalance|
|Error formula|$$E_n = \frac{b - a}{2^n}$$|Variable, depends on function curvature|

---

### **13. Accuracy and Limitations**

Although faster than Bisection, Regula–Falsi can **stall** when $$f(x)$$ is highly nonlinear or one endpoint remains fixed for many iterations. This occurs because:

- One function value remains large in magnitude.
    
- The secant line repeatedly passes close to the same endpoint.
    

To mitigate this, a **Modified Regula–Falsi** (Illinois Method) can be used, where the function value of the stagnant endpoint is halved after repeated use.

---

### **14. Advantages**

- Faster than Bisection.
    
- Requires only function evaluations (no derivatives).
    
- Simple to implement on a computer.
    
- Guaranteed convergence (for continuous $$f(x)$$ with sign change).
    

---

### **15. Disadvantages**

- May converge slowly if one endpoint dominates.
    
- Can stagnate for certain function shapes.
    
- Slightly more computational effort per iteration (needs both function values).
    
- Still slower than derivative-based methods (e.g., Newton–Raphson).
    

---

### **16. Example 2**

Find the root of:  
$$  
f(x) = x e^x - 1 = 0  
$$  
using Regula–Falsi with $$x_0 = 0$$, $$x_1 = 1$$, $$\epsilon = 0.001$$.

Compute:  
$$f(0) = -1, \quad f(1) = 1.718$$  
Since $$f(0)f(1) < 0$$, proceed.

**Iteration 1:**  
$$  
x_2 = 0 - (-1)\frac{1 - 0}{1.718 - (-1)} = 0.368  
$$  
$$f(0.368) = 0.368e^{0.368} - 1 = 0.108$$  
Root lies between 0 and 0.368.

**Iteration 2:**  
$$  
x_3 = 0 - (-1)\frac{0.368 - 0}{0.108 - (-1)} = 0.332  
$$  
$$f(0.332) = -0.006$$  
Since $$\lvert f(0.332) \rvert < 0.001$$ → Stop.

Hence, $$x \approx 0.332$$.

---

### **17. Estimation of Iterations**

No exact iteration count formula like in Bisection exists, but roughly:  
$$  
E_{n+1} \approx C E_n^{p}  
$$  
where $$1 < p < 2$$ indicates **super-linear convergence** and $$C$$ is a constant depending on $$f(x)$$ near the root.

---

### **18. Pseudocode**

```
Input f(x), x0, x1, ε
If f(x0)*f(x1) > 0
    Print "Invalid interval"
Else
    Repeat
        x2 = x0 - f(x0)*(x1 - x0)/(f(x1) - f(x0))
        If f(x0)*f(x2) < 0
            x1 = x2
        Else
            x0 = x2
        EndIf
    Until |f(x2)| < ε or |x1 - x0| < ε
EndIf
Output x2 as approximate root
```

---

### **19. Example Table**

|Iter|$$x_0$$|$$x_1$$|$$f(x_0)$$|$$f(x_1)$$|$$x_2$$|$$f(x_2)$$|$$E$$|
|---|---|---|---|---|---|---|---|
|1|0.0|1.0|-1|1.718|0.368|0.108|0.368|
|2|0.0|0.368|-1|0.108|0.332|-0.006|0.036|
|3|0.332|0.368|-0.006|0.108|0.333|-0.001|0.001|

Root ≈ **0.333**.

---

### **20. Final Remarks**

The **Regula–Falsi Method** provides a useful balance between **robustness and efficiency**. It improves upon Bisection by incorporating **linear interpolation**, leading to fewer iterations for well-behaved functions.  
However, in cases where the function is highly nonlinear, convergence may slow down, requiring modifications like the **Illinois** or **Anderson–Björck** variants.

Despite these limitations, Regula–Falsi remains a cornerstone method in numerical root-finding — simple, reliable, and still widely used in engineering computations.

---


