---
updated_at: 2025-10-11T20:35:23.359+05:30
edited_seconds: 50
---
#Maths 
# Unit 3: Numerical Differentiation and Integration

**Forward Difference**
$$
\text{\huge $f'(x_i) \approx \frac{f(x_{i+1}) - f(x_i)}{h}$}
$$

**Backward Difference**
$$
\text{\huge $f'(x_i) \approx \frac{f(x_i) - f(x_{i-1})}{h}$}
$$

**Central Difference**
$$
\text{\huge $f'(x_i) \approx \frac{f(x_{i+1}) - f(x_{i-1})}{2h}$}
$$

**Newton Forward Difference Formula**
$$
\text{\huge $f'(x_0) \approx \frac{\Delta y_0}{h} - \frac{\Delta^2 y_0}{2h} + \frac{\Delta^3 y_0}{3h} - \dots$}
$$

**Newton Backward Difference Formula**
$$
\text{\huge $f'(x_n) \approx \frac{\nabla y_n}{h} + \frac{\nabla^2 y_n}{2h} + \frac{\nabla^3 y_n}{3h} + \dots$}
$$

**Trapezoidal Rule**
$$
\text{\huge $\int_{x_0}^{x_n} f(x)\,dx \approx \frac{h}{2} \Big[ f(x_0) + 2 \sum_{i=1}^{n-1} f(x_i) + f(x_n) \Big]$}
$$

**Simpson's 1/3 Rule**
$$
\text{\huge $\int_{x_0}^{x_n} f(x)\,dx \approx \frac{h}{3} \Big[ f(x_0) + 4 \sum_{i=1,3,5}^{n-1} f(x_i) + 2 \sum_{i=2,4,6}^{n-2} f(x_i) + f(x_n) \Big]$}
$$

**Simpson's 3/8 Rule**
$$
\text{\huge $\int_{x_0}^{x_n} f(x)\,dx \approx \frac{3h}{8} \Big[ f(x_0) + 3 \sum_{i=1,2,4,5,\dots}^{n-1} f(x_i) + 2 \sum_{i=3,6,9,\dots}^{n-3} f(x_i) + f(x_n) \Big]$}
$$

# Unit 4: Numerical Solutions of ODEs

**Euler Method**
$$
\text{\huge $y_{n+1} = y_n + h f(x_n, y_n)$}
$$

**Improved Euler (Heun's) Method**
$$
\text{\huge $y_{n+1} = y_n + \frac{h}{2} \Big[ f(x_n, y_n) + f(x_{n+1}, y_n + h f(x_n, y_n)) \Big]$}
$$

**Taylor Series Method**
$$
\text{\huge $y_{n+1} = y_n + h y'_n + \frac{h^2}{2} y''_n + \frac{h^3}{6} y'''_n + \dots$}
$$

**Runge-Kutta 4th Order Method**
$$
\text{\huge $\begin{aligned}
k_1 &= h f(x_n, y_n) \\
k_2 &= h f\Big(x_n + \frac{h}{2}, y_n + \frac{k_1}{2}\Big) \\
k_3 &= h f\Big(x_n + \frac{h}{2}, y_n + \frac{k_2}{2}\Big) \\
k_4 &= h f(x_n + h, y_n + k_3) \\
y_{n+1} &= y_n + \frac{1}{6}(k_1 + 2 k_2 + 2 k_3 + k_4)
\end{aligned}$}
$$

**Milne's Predictor-Corrector Method**
$$
\text{\huge $\begin{aligned}
y_{n+1}^{(p)} &= y_{n-3} + \frac{4h}{3} (2 f_n - f_{n-1} + 2 f_{n-2}) \quad \text{(Predictor)}\\
y_{n+1} &= y_{n-1} + \frac{h}{3} (f_{n+1}^{(p)} + 4 f_n + f_{n-1}) \quad \text{(Corrector)}
\end{aligned}$}
$$
