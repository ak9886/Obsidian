---
updated_at: 2025-11-15T13:12:01.254+05:30
edited_seconds: 20
---
Great — generating the **full spaced-repetition flashcard deck now**, with:

- **One formula per card**
    
- **Descriptive fronts**
    
- **Obsidian SR plugin–compatible**
    
- **No blank lines inside cards**
    
- **All formulas wrapped in `\huge{…}`**
    
- **All formulas inside `$$ … $$`**
    
- **100% safe to paste directly into Obsidian**
    

---

# ✅ **UNIT 1 — Numerical Solutions of Algebraic & Transcendental Equations**

```
Iteration formula for the Bisection method:: $$\huge{x_n = \frac{a_n + b_n}{2}}$$
```

```
Left interval update condition in Bisection method:: $$\huge{f(a_n)f(x_n) < 0 \Rightarrow b_{n+1} = x_n}$$
```

```
Right interval update condition in Bisection method:: $$\huge{f(a_n)f(x_n) > 0 \Rightarrow a_{n+1} = x_n}$$
```

```
Iteration formula for the False Position (Regula Falsi) method:: $$\huge{x_n = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}}$$
```

```
Iteration formula for the Fixed Point (Iteration) method:: $$\huge{x_{n+1} = g(x_n)}$$
```

```
Convergence condition for the Fixed Point method:: $$\huge{|g'(x)| < 1}$$
```

```
Iteration formula for the Newton–Raphson method:: $$\huge{x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}}$$
```

```
Back substitution formula for Gauss Elimination:: $$\huge{x_n = \frac{b_n - \sum_{j=n+1}^{m} a_{nj}x_j}{a_{nn}}}$$
```

```
Pivot update formula in Gauss–Jordan method:: $$\huge{a_{ij}^{new} = a_{ij}^{old} - \frac{a_{ik}a_{kj}}{a_{kk}}}$$
```

```
Iteration formula for the Jacobi method:: $$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}}(b_i - \sum_{j\ne i} a_{ij}x_j^{(k)})}$$
```

```
Iteration formula for the Gauss–Seidel method:: $$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}}(b_i - \sum_{j<i} a_{ij}x_j^{(k+1)} - \sum_{j>i} a_{ij}x_j^{(k)})}$$
```

---

# ✅ **UNIT 2 — Finite Differences & Interpolation**

```
Formula for the Forward Difference operator:: $$\huge{\Delta f(x) = f(x+h) - f(x)}$$
```

```
Formula for the Backward Difference operator:: $$\huge{\nabla f(x) = f(x) - f(x-h)}$$
```

```
Relation between ∆ and shift operator E:: $$\huge{\Delta = E - 1}$$
```

```
Relation between ∇ and shift operator E:: $$\huge{\nabla = 1 - E^{-1}}$$
```

```
Action of the shift operator on a function:: $$\huge{E f(x) = f(x+h)}$$
```

```
Newton's forward interpolation formula:: $$\huge{f(x)=f_0+u\Delta f_0+\frac{u(u-1)}{2!}\Delta^2 f_0+\frac{u(u-1)(u-2)}{3!}\Delta^3 f_0+\cdots}$$
```

```
Newton's backward interpolation formula:: $$\huge{f(x)=f_n+u\nabla f_n+\frac{u(u+1)}{2!}\nabla^2 f_n+\frac{u(u+1)(u+2)}{3!}\nabla^3 f_n+\cdots}$$
```

```
First divided difference formula:: $$\huge{f[x_0,x_1]=\frac{f(x_1)-f(x_0)}{x_1-x_0}}$$
```

```
General divided difference formula:: $$\huge{f[x_0,\dots,x_n] = \frac{f[x_1,\dots,x_n]-f[x_0,\dots,x_{n-1}]}{x_n-x_0}}$$
```

```
Newton’s divided difference interpolation formula:: $$\huge{f(x)=f(x_0)+(x-x_0)f[x_0,x_1]+(x-x_0)(x-x_1)f[x_0,x_1,x_2]+\cdots}$$
```

```
Lagrange interpolation formula:: $$\huge{f(x)=\sum_{i=0}^n f(x_i)\prod_{j\ne i}\frac{x-x_j}{x_i-x_j}}$$
```

```
Inverse Lagrange interpolation formula:: $$\huge{x=\sum_{i=0}^n x_i\prod_{j\ne i}\frac{f-f(x_j)}{f(x_i)-f(x_j)}}$$
```

---

# ✅ **UNIT 3 — Numerical Differentiation & Integration**

```
Forward formula for first derivative:: $$\huge{f'(x_0)=\frac{1}{h}(\Delta f_0-\frac{1}{2}\Delta^2 f_0+\frac{1}{3}\Delta^3 f_0-\cdots)}$$
```

```
Backward formula for first derivative:: $$\huge{f'(x_n)=\frac{1}{h}(\nabla f_n+\frac{1}{2}\nabla^2 f_n+\frac{1}{3}\nabla^3 f_n+\cdots)}$$
```

```
Composite Trapezoidal Rule:: $$\huge{\int_a^b f(x)\,dx=\frac{h}{2}[f_0+2(f_1+f_2+\cdots+f_{n-1})+f_n]}$$
```

```
Simpson's 1/3 Rule:: $$\huge{\int_a^b f(x)\,dx=\frac{h}{3}[f_0 + 4(f_1+f_3+\cdots)+2(f_2+f_4+\cdots)+f_n]}$$
```

```
Simpson's 3/8 Rule:: $$\huge{\int_a^b f(x)\,dx=\frac{3h}{8}[f_0+3(f_1+f_2+f_4+\cdots)+2(f_3+f_6+\cdots)+f_n]}$$
```

---

# ✅ **UNIT 4 — Numerical Solutions of ODEs**

```
Taylor series method formula:: $$\huge{y(x+h)=y(x)+hy'(x)+\frac{h^2}{2!}y''(x)+\frac{h^3}{3!}y'''(x)+\cdots}$$
```

```
Euler method formula:: $$\huge{y_{n+1}=y_n+hf(x_n,y_n)}$$
```

```
Predictor step in Improved Euler method:: $$\huge{y^*=y_n+h f(x_n,y_n)}$$
```

```
Corrector step in Improved Euler method:: $$\huge{y_{n+1}=y_n+\frac{h}{2}[f(x_n,y_n)+f(x_{n+1},y^*)]}$$
```

```
Modified Euler method formula:: $$\huge{y_{n+1}=y_n+h f(x_n+\frac{h}{2},y_n+\frac{h}{2}f(x_n,y_n))}$$
```

```
Runge–Kutta 2nd order method formula:: $$\huge{y_{n+1}=y_n+\frac{h}{2}(k_1+k_2)}$$
```

```
First RK2 stage k1:: $$\huge{k_1=f(x_n,y_n)}$$
```

```
Second RK2 stage k2:: $$\huge{k_2=f(x_n+h,y_n+hk_1)}$$
```

```
RK4 final update formula:: $$\huge{y_{n+1}=y_n+\frac{h}{6}(k_1+2k_2+2k_3+k_4)}$$
```

```
RK4 k1 definition:: $$\huge{k_1=f(x_n,y_n)}$$
```

```
RK4 k2 definition:: $$\huge{k_2=f(x_n+\frac{h}{2},y_n+\frac{h}{2}k_1)}$$
```

```
RK4 k3 definition:: $$\huge{k_3=f(x_n+\frac{h}{2},y_n+\frac{h}{2}k_2)}$$
```

```
RK4 k4 definition:: $$\huge{k_4=f(x_n+h,y_n+h k_3)}$$
```

---

# ✅ **UNIT 5 — Numerical Solutions of PDEs**

```
Standard five-point Laplace formula:: $$\huge{u_{i,j}=\frac{1}{4}(u_{i+1,j}+u_{i-1,j}+u_{i,j+1}+u_{i,j-1})}$$
```

```
Diagonal five-point formula:: $$\huge{u_{i,j}=\frac{1}{4}(u_{i+1,j+1}+u_{i+1,j-1}+u_{i-1,j+1}+u_{i-1,j-1})}$$
```

```
Liebmann iterative update formula:: $$\huge{u_{i,j}^{(k+1)}=\frac{1}{4}(u_{i+1,j}^{(k)}+u_{i-1,j}^{(k+1)}+u_{i,j+1}^{(k)}+u_{i,j-1}^{(k+1)})}$$
```

```
Poisson equation finite difference formula:: $$\huge{u_{i,j}=\frac{1}{4}(u_{i+1,j}+u_{i-1,j}+u_{i,j+1}+u_{i,j-1}-h^2 f_{i,j})}$$
```

```
Definition of lambda in Bender–Schmidt method:: $$\huge{\lambda=\frac{\alpha k}{h^2}}$$
```

```
Bender–Schmidt update formula:: $$\huge{u_i^{n+1}=(1-2\lambda)u_i^n+\lambda(u_{i-1}^n+u_{i+1}^n)}$$
```

```
Crank–Nicolson scheme formula:: $$\huge{\frac{u_i^{n+1}-u_i^{n}}{k}=\alpha\frac{1}{2}\left(\frac{u_{i+1}^{n+1}-2u_i^{n+1}+u_{i-1}^{n+1}}{h^2}+\frac{u_{i+1}^{n}-2u_i^{n}+u_{i-1}^{n}}{h^2}\right)}$$
```

---

