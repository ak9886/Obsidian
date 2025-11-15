---
updated_at: 2025-11-15T13:02:57.619+05:30
edited_seconds: 180
---
# **Unit 1 — Numerical Solutions of Algebraic & Transcendental Equations**

---

### **Bisection Method**

$$  
\huge{  
x_n = \frac{a_n + b_n}{2}  
}  
$$

---

### **False Position (Regula Falsi)**

$$  
\huge{  
x_n = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}  
}  
$$

---

### **Iteration (Fixed Point)**

$$  
\huge{  
x_{n+1} = g(x_n)  
}  
$$

---

### **Newton–Raphson Method**

$$  
\huge{  
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}  
}  
$$

---

### **Jacobi Method**

$$  
\huge{  
x_i^{(k+1)} =  
\frac{1}{a_{ii}} \left( b_i - \sum_{j\ne i} a_{ij} x_j^{(k)} \right)  
}  
$$

---

### **Gauss–Seidel Method**

$$  
\huge{  
x_i^{(k+1)} =  
\frac{1}{a_{ii}} \left( b_i - \sum_{j<i} a_{ij} x_j^{(k+1)}

- \sum_{j>i} a_{ij} x_j^{(k)} \right)  
    }  
    $$
    

---

#  **Unit 2 — Finite Differences & Interpolation**

---

### **Forward Difference**

$$  
\huge{  
\Delta f(x) = f(x+h) - f(x)  
}  
$$

---

### **Backward Difference**

$$  
\huge{  
\nabla f(x) = f(x) - f(x-h)  
}  
$$

---

### **Operator Relations**

$$  
\huge{  
\Delta = E - 1  
}  
$$  
$$  
\huge{  
\nabla = 1 - E^{-1}  
}  
$$

---

### **Newton Forward Interpolation**

$$  
\huge{  
f(x)=f_0+u\Delta f_0+\frac{u(u-1)}{2!}\Delta^2 f_0+\frac{u(u-1)(u-2)}{3!}\Delta^3 f_0+\cdots  
}  
$$

---

### **Newton Backward Interpolation**

$$  
\huge{  
f(x)=f_n+u\nabla f_n+\frac{u(u+1)}{2!}\nabla^2 f_n+\frac{u(u+1)(u+2)}{3!}\nabla^3 f_n+\cdots  
}  
$$

---

### **Divided Difference**

$$  
\huge{  
f[x_0,x_1]=\frac{f(x_1)-f(x_0)}{x_1-x_0}  
}  
$$

---

### **Newton Divided Difference Interpolation**

$$  
\huge{  
f(x)=f(x_0)+(x-x_0)f[x_0,x_1] +(x-x_0)(x-x_1)f[x_0,x_1,x_2]+\cdots  
}  
$$

---

### **Lagrange Interpolation**

$$  
\huge{  
f(x)=\sum_{i=0}^{n} f(x_i)\prod_{\substack{j=0 \ j\ne i}}^{n}  
\frac{x-x_j}{x_i-x_j}  
}  
$$

---

### **Inverse Lagrange**

$$  
\huge{  
x=\sum_{i=0}^{n} x_i\prod_{\substack{j=0 \ j\ne i}}^{n}  
\frac{f-f(x_j)}{f(x_i)-f(x_j)}  
}  
$$

---

#  **Unit 3 — Numerical Differentiation & Integration**

---

### **Forward Numerical Differentiation**

$$  
\huge{  
f'(x_0)=\frac{1}{h}\left(\Delta f_0 - \frac{1}{2}\Delta^2 f_0 + \frac{1}{3}\Delta^3 f_0 - \cdots\right)  
}  
$$

---

### **Backward Numerical Differentiation**

$$  
\huge{  
f'(x_n)=\frac{1}{h}\left(\nabla f_n + \frac{1}{2}\nabla^2 f_n + \frac{1}{3}\nabla^3 f_n + \cdots\right)  
}  
$$

---

### **Trapezoidal Rule**

$$  
\huge{  
\int_a^b f(x),dx  
= \frac{h}{2}\left[f_0 + 2(f_1 + f_2 + \cdots + f_{n-1}) + f_n\right]  
}  
$$

---

### **Simpson 1/3 Rule**

$$  
\huge{  
\int_a^b f(x),dx  
= \frac{h}{3}\left[f_0 + 4(f_1 + f_3 + \cdots) + 2(f_2 + f_4 + \cdots) + f_n\right]  
}  
$$

---

### **Simpson 3/8 Rule**

$$  
\huge{  
\int_a^b f(x),dx  
= \frac{3h}{8}\left[  
f_0 + 3(f_1+f_2+f_4+f_5+\cdots) + 2(f_3+f_6+\cdots) + f_n  
\right]  
}  
$$

---

#  **Unit 4 — Numerical ODE Methods**

---

### **Taylor Series**

$$  
\huge{  
y(x+h)=y(x)+hy'(x)+\frac{h^2}{2!}y''(x)+\frac{h^3}{3!}y'''(x)+\cdots  
}  
$$

---

### **Euler Method**

$$  
\huge{  
y_{n+1}=y_n+h,f(x_n,y_n)  
}  
$$

---

### **Improved Euler (Heun)**

$$  
\huge{  
y_{n+1}=y_n+\frac{h}{2}\left[f(x_n,y_n)+f(x_{n+1},y^*)\right]  
}  
$$

---

### **Modified Euler**

$$  
\huge{  
y_{n+1}=y_n+h,f!\left(x_n+\frac{h}{2},,y_n+\frac{h}{2}f(x_n,y_n)\right)  
}  
$$

---

### **RK2**

$$  
\huge{  
y_{n+1}=y_n+\frac{h}{2}(k_1+k_2)  
}  
$$

---

### **RK4**

$$  
\huge{  
y_{n+1}=y_n+\frac{h}{6}(k_1+2k_2+2k_3+k_4)  
}  
$$

---

#  **Unit 5 — Partial Differential Equations**

---

### **Standard 5-Point Laplace**

$$  
\huge{  
u_{i,j}=\frac{1}{4}(u_{i+1,j}+u_{i-1,j}+u_{i,j+1}+u_{i,j-1})  
}  
$$

---

### **Diagonal 5-Point**

$$  
\huge{  
u_{i,j}=\frac{1}{4}(u_{i+1,j+1}+u_{i+1,j-1}+u_{i-1,j+1}+u_{i-1,j-1})  
}  
$$

---

### **Liebmann Iteration**

$$  
\huge{  
u_{i,j}^{(k+1)}=\frac{1}{4}\left(  
u_{i+1,j}^{(k)} + u_{i-1,j}^{(k+1)} + u_{i,j+1}^{(k)} + u_{i,j-1}^{(k+1)}  
\right)  
}  
$$

---

### **Poisson Equation**

$$  
\huge{  
u_{i,j}=\frac{1}{4}\left(  
u_{i+1,j}+u_{i-1,j}+u_{i,j+1}+u_{i,j-1} - h^2 f_{i,j}  
\right)  
}  
$$

---

### **Bender–Schmidt**

$$  
\huge{  
u_i^{n+1}=(1-2\lambda)u_i^n+\lambda(u_{i-1}^n+u_{i+1}^n)  
}  
$$

---

### **Crank–Nicolson**

$$  
\huge{  
\frac{u_i^{n+1}-u_i^n}{k}  
=\frac{\alpha}{2}\left[  
\frac{u_{i+1}^{n+1}-2u_i^{n+1}+u_{i-1}^{n+1}}{h^2}  
+  
\frac{u_{i+1}^{n}-2u_i^{n}+u_{i-1}^{n}}{h^2}  
\right]  
}  
$$

---

