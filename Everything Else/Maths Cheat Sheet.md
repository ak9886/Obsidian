---
updated_at: 2025-08-18T19:41:22.607+05:30
edited_seconds: 10
---
#Maths
# 📘 UNIT I – Numerical Solution of Equations & Linear Systems

## 🔹 PART A: CHEAT-SHEET (Formulas & Quick Reference)

### 1. Root-Finding Methods
- **Bisection Method**  
  Formula: xr = (a + b) / 2  
  Convergence: Linear (slow)  
  Condition: f(a) * f(b) < 0  

- **Newton-Raphson Method**  
  Formula: x(r+1) = xr - f(xr) / f'(xr)  
  Convergence: Quadratic (fast)  
  Needs derivative of function  
  Sensitive to initial guess  

- **Regula Falsi Method (False Position)**  
  Formula: xn = (a*f(b) - b*f(a)) / (f(b) - f(a))  
  Convergence: Order ≈ 1.618  
  Condition: f(a) * f(b) < 0  

---

### 2. System of Linear Equations
- **Gauss Elimination** → Upper triangular form, then back substitution  
- **Gauss-Jordan** → Diagonal (unit matrix), direct solution  
- **Gauss-Jacobi** → Iterative, update all variables simultaneously  
- **Gauss-Seidel** → Iterative, update immediately with new values, faster than Jacobi  

---

## 🔹 PART B: DETAILED EXPLANATION WITH EXAMPLES

### 1. Bisection Method
Equation: f(x) = x - cos(x) = 0  
- f(0) = -1, f(1) = 0.4596 → root in [0,1]  
- Midpoint = 0.5, f(0.5) = -0.3776 → new interval [0.5,1]  
- Continue halving until accuracy  
- Final result: Root ≈ 0.7391  

---

### 2. Newton-Raphson Method
Equation: f(x) = 3x - cos(x) - 1 = 0  
- Formula: x(r+1) = xr - f(xr)/f'(xr)  
- Start with x0 = 0.5  
- Converges quickly → Root ≈ 0.60710  

---

### 3. Regula Falsi Method
Equation: f(x) = x - cos(x)  
- f(0) = -1, f(1) = 0.4596  
- First approximation: x1 = 0.68507  
- Converges to root ≈ 0.7391  

---

### 4. Linear Systems Example
System:  
x + 2y + z = 3  
2x + 3y + 3z = 10  
3x - y + 2z = 13  

- **Gauss Elimination:** → z=3, y=-1, x=2  
- **Gauss-Jordan:** → Same result directly  
- **Jacobi vs Seidel:** Seidel converges faster  

---

✅ **Unit I Key Idea:** Pick method based on speed, stability, and ease  

---

# 📘 UNIT II – Finite Differences & Interpolation

## 🔹 PART A: CHEAT-SHEET (Formulas & Quick Reference)

### 1. Operators
- Forward difference: Δf(x) = f(x+h) - f(x)  
- Backward difference: ∇f(x) = f(x) - f(x-h)  
- Shift operator: E f(x) = f(x+h)  
- Central difference: δf(x) = f(x+h/2) - f(x-h/2)  
- Relation: E = 1 + Δ  

---

### 2. Interpolation (Equal Interval)
- **Newton Forward:**  
  f(x) = f(x0) + pΔf(x0) + p(p-1)/2! * Δ²f(x0) + ...  
  where p = (x - x0)/h  

- **Newton Backward:**  
  f(x) = f(xn) + p∇f(xn) + p(p+1)/2! * ∇²f(xn) + ...  
  where p = (x - xn)/h  

---

### 3. Interpolation (Unequal Interval)
- **Divided Difference Formula:**  
  f(x) = f(x0) + (x-x0)f[x0,x1] + (x-x0)(x-x1)f[x0,x1,x2] + ...  

- **Lagrange’s Formula:**  
  f(x) = Σ [ f(xi) * Π ( (x - xj) / (xi - xj) ) ]  
  (j ≠ i)  

---

## 🔹 PART B: DETAILED EXPLANATION WITH EXAMPLES

### 1. Operators
Example: f(x) = x²  
Δf(x) = (x+h)² - x² = 2xh + h²  
Each difference reduces degree by 1  

---

### 2. Newton’s Forward Interpolation
- Best when x near start of table  
- Build difference table  
- Use formula with computed p  

---

### 3. Newton’s Backward Interpolation
- Best when x near end of table  
- Uses backward differences  

---

### 4. Divided Differences
Example: Points at (1, f(1)), (2, f(2)), (4, f(4))  
f[x0,x1] = (f(x1) - f(x0)) / (x1 - x0)  
Continue recursively  

---

### 5. Lagrange’s Formula
Example: f(1)=1, f(2)=4, f(3)=9  
f(x) = 1 * (x-2)(x-3)/((1-2)(1-3))  
     + 4 * (x-1)(x-3)/((2-1)(2-3))  
     + 9 * (x-1)(x-2)/((3-1)(3-2))  
Simplifies to f(x) = x²  

---

✅ **Unit II Key Idea:** Interpolation estimates unknown values from discrete data. Choose method depending on data spacing.  

---

# 🔑 GRAND TAKEAWAY
- **Unit I:** Root-finding + solving linear systems (Bisection, Newton-Raphson, Regula Falsi, Gauss methods)  
- **Unit II:** Finite differences + interpolation (Forward, Backward, Divided, Lagrange)  

---

### ❓ Follow-up Questions
- **Q1:** Should I create a comparison table (advantages/disadvantages)?  
- **Q2:** Do you want exam-style practice problems with detailed solutions?  
- **Q3:** Would a single-page revision handout (formula + example) help for quick prep?  
