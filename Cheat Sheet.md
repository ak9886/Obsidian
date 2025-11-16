---
updated_at: 2025-11-16T13:19:18.496+05:30
edited_seconds: 60
---
Here’s the reformatted cheat-sheet using `$$ $$` for multi-line math and `$ $` for inline expressions:

---

# **Numerical Methods Cheat Sheet**

## **1. Bisection Method**

Iteration formula:  
$$x_n = \frac{a_n + b_n}{2}$$

Left interval update:  
$$a_{n+1} = x_n \quad \text{if } f(a_n)f(x_n) > 0$$

Right interval update:  
$$b_{n+1} = x_n \quad \text{if } f(a_n)f(x_n) < 0$$

---

## **2. False Position (Regula Falsi)**

$$x_n = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}$$

---

## **3. Fixed Point Iteration**

Iteration:  
$$x_{n+1} = g(x_n)$$

Convergence:  
$$|g'(x)| < 1$$

---

## **4. Newton–Raphson**

$$x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

---

## **5. Gauss Elimination / Gauss–Jordan**

Back substitution:  
$$x_n = \frac{b_n - \sum_{j=n+1}^{m} a_{nj} x_j}{a_{nn}}$$

Gauss–Jordan pivot:  
$$a_{ij}^{(new)} = a_{ij}^{(old)} - \frac{a_{ik} a_{kj}}{a_{kk}}$$

---

## **6. Jacobi Method**

$$x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right)$$

---

## **7. Gauss–Seidel Method**

$$x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j<i} a_{ij} x_j^{(k+1)} - \sum_{j>i} a_{ij} x_j^{(k)} \right)$$

---

## **8. Finite Differences**

Forward:  
$$\Delta f(x) = f(x+h) - f(x)$$  
$$\Delta^2 f(x) = \Delta f(x+h) - \Delta f(x)$$  
$$\Delta^3 f(x) = \Delta^2 f(x+h) - \Delta^2 f(x)$$

Backward:  
$$\nabla f(x) = f(x) - f(x-h)$$  
$$\nabla^2 f(x) = \nabla f(x) - \nabla f(x-h)$$  
$$\nabla^3 f(x) = \nabla^2 f(x) - \nabla^2 f(x-h)$$

Operators:  
$$\Delta = E - 1$$  
$$\nabla = 1 - E^{-1}$$  
$$E f(x) = f(x+h)$$

---

## **9. Newton’s Forward Interpolation**

$$f(x) = f_0 + u \Delta f_0 + \frac{u(u-1)}{2!} \Delta^2 f_0 + \frac{u(u-1)(u-2)}{3!} \Delta^3 f_0$$

---

## **10. Newton’s Backward Interpolation**

$$f(x) = f_n + u \nabla f_n + \frac{u(u+1)}{2!} \nabla^2 f_n + \frac{u(u+1)(u+2)}{3!} \nabla^3 f_n$$

---

## **11. Divided Differences**

Two points:  
$$f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0}$$

Three points:  
$$f[x_0, x_1, x_2] = \frac{f[x_1, x_2] - f[x_0, x_1]}{x_2 - x_0}$$

Newton Divided Difference Polynomial:  
$$f(x) = f(x_0) + (x - x_0)f[x_0,x_1] + (x - x_0)(x - x_1)f[x_0,x_1,x_2]$$

---

## **12. Lagrange Interpolation**

General:  
$$f(x) = \sum_{i=0}^{n} f(x_i) \prod_{\substack{j=0 \ j\ne i}}^{n} \frac{x - x_j}{x_i - x_j}$$

Inverse:  
$$x = \sum_{i=0}^{n} x_i \prod_{\substack{j=0 \ j\ne i}}^{n} \frac{f - f(x_j)}{f(x_i) - f(x_j)}$$

---

## **13. Numerical Differentiation**

Forward:  
$$f'(x_0) = \frac{1}{h} \Delta f_0 - \frac{1}{2h} \Delta^2 f_0 + \frac{1}{3h} \Delta^3 f_0$$

Backward:  
$$f'(x_n) = \frac{1}{h} \nabla f_n + \frac{1}{2h} \nabla^2 f_n + \frac{1}{3h} \nabla^3 f_n$$

---

## **14. Numerical Integration**

### Trapezoidal Rule:

$$\frac{h}{2} \left[f_0 + 2(f_1 + \dots + f_{n-1}) + f_n\right]$$

### Simpson’s 1/3:

$$\frac{h}{3}\left[f_0 + 4(f_1 + f_3 + \dots) + 2(f_2 + f_4 + \dots) + f_n\right]$$

### Simpson’s 3/8:

$$\frac{3h}{8}\left[f_0 + 3(f_1 + f_2 + f_4 + \dots) + 2(f_3 + f_6 + \dots) + f_n\right]$$

---

## **15. Taylor Series Method**

$$y(x+h) = y(x) + h y'(x) + \frac{h^2}{2!} y''(x) + \frac{h^3}{3!} y'''(x)$$

---

## **16. Euler & Improved Euler**

Euler:  
$$y_{n+1} = y_n + h f(x_n, y_n)$$

Heun Predictor:  
$$y^* = y_n + h f(x_n, y_n)$$

Heun Corrector:  
$$y_{n+1} = y_n + \frac{h}{2} \left[f(x_n,y_n) + f(x_{n+1}, y^*)\right]$$

Modified Euler:  
$$y_{n+1} = y_n + h f\left(x_n + \frac{h}{2}, y_n + \frac{h}{2} f(x_n,y_n)\right)$$

---

## **17. Runge–Kutta Methods**

### RK2:

$$k_1 = f(x_n, y_n)$$  
$$k_2 = f(x_n + h, y_n + h k_1)$$  
$$y_{n+1} = y_n + \frac{h}{2}(k_1 + k_2)$$

### RK4:

$$k_1 = f(x_n,y_n)$$  
$$k_2 = f(x_n + \tfrac{h}{2}, y_n + \tfrac{h}{2}k_1)$$  
$$k_3 = f(x_n + \tfrac{h}{2}, y_n + \tfrac{h}{2}k_2)$$  
$$k_4 = f(x_n + h, y_n + h k_3)$$  
$$y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)$$

---

## **18. PDE Numerical Methods**

Standard 5-Point Laplace:  
$$u_{i,j} = \frac{1}{4}(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1})$$

Diagonal 5-Point:  
$$u_{i,j} = \frac{1}{4}(u_{i+1,j+1} + u_{i+1,j-1} + u_{i-1,j+1} + u_{i-1,j-1})$$

Liebmann:  
$$u_{i,j}^{(k+1)} = \frac{1}{4}(u_{i+1,j}^{(k)} + u_{i-1,j}^{(k+1)} + u_{i,j+1}^{(k)} + u_{i,j-1}^{(k+1)})$$

Poisson:  
$$u_{i,j} = \frac{1}{4} \left( u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1} - h^2 f_{i,j} \right)$$

Bender–Schmidt:  
$$\lambda = \frac{\alpha k}{h^2}$$  
$$u_i^{n+1} = (1 - 2\lambda)u_i^n + \lambda(u_{i-1}^n + u_{i+1}^n)$$

Crank–Nicolson:  
$$\frac{u_i^{n+1} - u_i^n}{k}  
= \alpha \frac{1}{2} \frac{u_{i+1}^{n+1} - 2 u_i^{n+1} + u_{i-1}^{n+1}}{h^2}

- \alpha \frac{1}{2} \frac{u_{i+1}^{n} - 2 u_i^{n} + u_{i-1}^{n}}{h^2}$$
    

---

