---
updated_at: 2025-11-15T18:35:47.236+05:30
edited_seconds: 10
---
# Numerical Methods Key Formulas

## Root Finding Methods

- **Regula Falsi:**

  \[
  x_{n+1} = \frac{a f(b) - b f(a)}{f(b) - f(a)}
  \]

- **Newton-Raphson:**

  \[
  x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
  \]

## Linear Systems

- **Gauss-Seidel Iteration:**

  \[
  x_i^{(k+1)} = \frac{1}{a_{ii}} \left( b_i - \sum_{j=1}^{i-1} a_{ij} x_j^{(k+1)} - \sum_{j=i+1}^n a_{ij} x_j^{(k)} \right)
  \]

## Interpolation

- **Lagrange Interpolation:**

  \[
  P(x) = \sum_{j=0}^n y_j \prod_{\substack{m=0 \\ m \neq j}}^n \frac{x - x_m}{x_j - x_m}
  \]

- **Newton Forward Difference:**

  \[
  P_n(x) = y_0 + u \Delta y_0 + \frac{u(u-1)}{2!} \Delta^2 y_0 + \cdots \quad \text{where } u = \frac{x - x_0}{h}
  \]

## Numerical Integration

- **Trapezoidal Rule:**

  \[
  \int_a^b f(x) dx \approx \frac{h}{2} \left( y_0 + y_n + 2 \sum_{i=1}^{n-1} y_i \right)
  \]

- **Simpson’s 1/3 Rule:**

  \[
  \int_a^b f(x) dx \approx \frac{h}{3} \left( y_0 + y_n + 4 \sum_{\text{odd } i} y_i + 2 \sum_{\text{even } i} y_i \right)
  \]

## Numerical Differentiation

- **Newton’s Forward Difference for first derivative:**

  \[
  f'(x_0) \approx \frac{1}{h} \left( \Delta y_0 - \frac{1}{2} \Delta^2 y_0 + \frac{1}{3} \Delta^3 y_0 - \cdots \right)
  \]

## ODE Solving

- **Taylor Series Method:**  
  \( y_{n+1} = y_n + h y\_prime\_n + \frac{h^2}{2!} y\_double\_prime\_n + \frac{h^3}{3!} y\_triple\_prime\_n + \cdots \)

- **Euler’s Method:**

  \[
  y_{n+1} = y_n + h f(x_n, y_n)
  \]

- **Improved Euler Method:**

  \[
  y^* = y_n + h f(x_n, y_n)
  \]

  \[
  y_{n+1} = y_n + \frac{h}{2} \left( f(x_n, y_n) + f(x_{n+1}, y^*) \right)
  \]

- **Runge-Kutta 4th order:**

  \[
  k_1 = h f(x_n, y_n)
  \]

  \[
  k_2 = h f\left(x_n + \frac{h}{2}, y_n + \frac{k_1}{2}\right)
  \]

  \[
  k_3 = h f\left(x_n + \frac{h}{2}, y_n + \frac{k_2}{2}\right)
  \]

  \[
  k_4 = h f(x_n + h, y_n + k_3)
  \]

  \[
  y_{n+1} = y_n + \frac{1}{6}(k_1 + 2k_2 + 2k_3 + k_4)
  \]

## PDE Solving

- **Bender-Schmidt Explicit Formula:**

  \[
  u_{i,j+1} = \frac{k}{2h^2} \left( u_{i+1,j} - 2 u_{i,j} + u_{i-1,j} \right) + u_{i,j}
  \]

- **Crank-Nicholson Scheme:**

  \[
  \frac{u_i^{j+1} - u_i^j}{k} = \frac{1}{2h^2} \left( u_{i+1}^j - 2 u_i^j + u_{i-1}^j + u_{i+1}^{j+1} - 2 u_i^{j+1} + u_{i-1}^{j+1} \right)
  \]

---

I will now generate a Markdown file with this content for you.
