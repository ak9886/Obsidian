---
updated_at: 2025-11-15T13:00:22.550+05:30
edited_seconds: 100
---

---

# Numerical Methods – Formula Cheat Sheet 

---

## **Unit 1 — Numerical Solutions of Algebraic & Transcendental Equations**

### **1. Bisection Method**

**Iteration:**  
$$ x_{n} = \frac{a_n + b_n}{2} $$

**Root interval update:**

- If $( f(a_n)f(x_n) < 0 \Rightarrow b_{n+1} = x_n )$
    
- Else $( a_{n+1} = x_n )$
    

---

### **2. False Position (Regula Falsi) Method**

$$ x_{n} = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)} $$

---

### **3. Iteration (Fixed Point) Method**

$$ x_{n+1} = g(x_n) $$

**Convergence condition:**  
$$ |g'(x)| < 1 $$

---

### **4. Newton–Raphson Method**

$$ x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)} $$

**Rate of convergence:** Quadratic.

---

### **5. Gauss Elimination**

Forward elimination → back substitution:

Back substitution:  
$$ x_n = \frac{b_n - \sum_{j=n+1}^{m} a_{nj} x_j}{a_{nn}} $$

---

### **6. Gauss–Jordan Method**

Reduced row-echelon form:

Pivot step:  
$$ a_{ij}^{(new)} = a_{ij}^{(old)} - \frac{a_{ik}, a_{kj}}{a_{kk}} $$

---

### **7. Jacobi Method**

$$ x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right) $$

---

### **8. Gauss–Seidel Method**

$$ x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j<i} a_{ij} x_j^{(k+1)} - \sum_{j>i} a_{ij} x_j^{(k)} \right) $$

---

---

## **Unit 2 — Finite Differences & Interpolation**

### **1. Forward Difference**

$$ \Delta f(x) = f(x+h) - f(x) $$

### **2. Backward Difference**

$$ \nabla f(x) = f(x) - f(x-h) $$

### **3. Relation Between Operators**

$$ \Delta = E - 1 $$  
$$ \nabla = 1 - E^{-1} $$  
$$ E f(x) = f(x+h) $$

---

### **4. Newton's Forward Interpolation**

For equal intervals, ( $u = \frac{x - x_0}{h}$ ):

$$ f(x) = f_0 + u \Delta f_0 + \frac{u(u-1)}{2!}\Delta^2 f_0 + \frac{u(u-1)(u-2)}{3!}\Delta^3 f_0 + \cdots $$

---

### **5. Newton's Backward Interpolation**

( u = \frac{x - x_n}{h} ):

$$ f(x) = f_n + u \nabla f_n + \frac{u(u+1)}{2!}\nabla^2 f_n + \frac{u(u+1)(u+2)}{3!}\nabla^3 f_n + \cdots $$

---

### **6. Divided Differences**

$$ f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0} $$

General:  
$$ f[x_0, x_1, \dots, x_n] = \frac{f[x_1, \dots, x_n] - f[x_0, \dots, x_{n-1}]}{x_n - x_0} $$

---

### **7. Newton's Divided Difference Interpolation**

$$ f(x) = f(x_0) + (x - x_0)f[x_0,x_1] + (x - x_0)(x - x_1)f[x_0,x_1,x_2] + \dots $$

---

### **8. Lagrange Interpolation**

$$ f(x) = \sum_{i=0}^{n} f(x_i) \prod_{\substack{j=0 \ j\ne i}}^{n}  
\frac{x - x_j}{x_i - x_j} $$

---

### **9. Inverse Lagrange Interpolation**

$$ x = \sum_{i=0}^n x_i \prod_{\substack{j=0 \ j\ne i}}^{n}  
\frac{f - f(x_j)}{f(x_i) - f(x_j)} $$

---

---

## **Unit 3 — Numerical Differentiation & Integration**

### **1. Numerical Differentiation (Forward)**

$$ f'(x_0) = \frac{1}{h}\left( \Delta f_0 - \frac{1}{2}\Delta^2 f_0 + \frac{1}{3}\Delta^3 f_0 - \cdots \right) $$

---

### **2. Numerical Differentiation (Backward)**

$$ f'(x_n) = \frac{1}{h}\left( \nabla f_n + \frac{1}{2}\nabla^2 f_n + \frac{1}{3}\nabla^3 f_n + \cdots \right) $$

---

### **3. Trapezoidal Rule**

$$ \int_a^b f(x),dx = \frac{h}{2}\left[f_0 + 2(f_1 + f_2 + \dots + f_{n-1}) + f_n\right] $$

---

### **4. Simpson’s 1/3 Rule**

$$ \int_a^b f(x),dx = \frac{h}{3}\left[f_0 + 4(f_1 + f_3 + \dots) + 2(f_2 + f_4 + \dots) + f_n\right] $$

---

### **5. Simpson’s 3/8 Rule**

$$ \int_a^b f(x),dx = \frac{3h}{8}\left[f_0

- 3(f_1+f_2 + f_4+f_5 + \dots)
    
- 2(f_3 + f_6 + \dots)
    
- f_n \right] $$
    

---

---

## **Unit 4 — Numerical Solution of ODEs**

### **1. Taylor Series Method**

$$ y(x+h) = y(x) + hy'(x) + \frac{h^2}{2!}y''(x) + \frac{h^3}{3!}y'''(x) + \cdots $$

---

### **2. Euler Method**

$$ y_{n+1} = y_n + h f(x_n, y_n) $$

---

### **3. Improved Euler (Heun’s) Method**

Predictor:  
$$ y^{*} = y_n + h f(x_n, y_n) $$

Corrector:  
$$ y_{n+1} = y_n + \frac{h}{2} \left[f(x_n, y_n) + f(x_{n+1}, y^{*}) \right] $$

---

### **4. Modified Euler Method**

$$ y_{n+1} = y_n + h, f!\left(x_n + \frac{h}{2},, y_n + \frac{h}{2} f(x_n,y_n)\right) $$

---

### **5. Runge–Kutta 2nd Order**

General form:  
$$ k_1 = f(x_n, y_n) $$  
$$ k_2 = f(x_n + h,, y_n + hk_1) $$  
$$ y_{n+1} = y_n + \frac{h}{2}(k_1 + k_2) $$

---

### **6. Runge–Kutta 4th Order**

$$ k_1 = f(x_n, y_n) $$  
$$ k_2 = f(x_n + \frac{h}{2},, y_n + \frac{h}{2}k_1) $$  
$$ k_3 = f(x_n + \frac{h}{2},, y_n + \frac{h}{2}k_2) $$  
$$ k_4 = f(x_n + h,, y_n + h k_3) $$

Final:  
$$ y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4) $$

---

---

## **Unit 5 — Numerical Solutions of PDEs**

### **1. Standard Five-Point Formula (Laplace)**

For ( u_{xx} + u_{yy} = 0 ):  
$$ u_{i,j} = \frac{1}{4}(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1}) $$

---

### **2. Diagonal Five-Point Formula**

$$ u_{i,j} = \frac{1}{4}(u_{i+1,j+1} + u_{i+1,j-1} + u_{i-1,j+1} + u_{i-1,j-1}) $$

---

### **3. Liebmann (Iterative) Method**

$$ u_{i,j}^{(k+1)} = \frac{1}{4}\left(u_{i+1,j}^{(k)} + u_{i-1,j}^{(k+1)} + u_{i,j+1}^{(k)} + u_{i,j-1}^{(k+1)}\right) $$

---

### **4. Poisson Equation**

For ( u_{xx} + u_{yy} = f(x,y) ):  
$$ u_{i,j} = \frac{1}{4}\left(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1} - h^2 f_{i,j} \right) $$

---

### **5. Bender–Schmidt (Parabolic 1D)**

Heat equation ( u_t = \alpha u_{xx} ):

Coefficient:  
$$ \lambda = \frac{\alpha k}{h^2} $$

Update:  
$$ u_{i}^{n+1} = (1 - 2\lambda)u_i^n + \lambda (u_{i-1}^n + u_{i+1}^n) $$

---

### **6. Crank–Nicolson Scheme**

$$ \frac{u_i^{n+1} - u_i^n}{k} =  
\alpha\frac{1}{2}\left( \frac{u_{i+1}^{n+1} - 2u_i^{n+1} + u_{i-1}^{n+1}}{h^2} +  
\frac{u_{i+1}^{n} - 2u_i^{n} + u_{i-1}^{n}}{h^2} \right) $$

---

