---
updated_at: 2025-11-15T13:23:25.945+05:30
edited_seconds: 160
---
```markdown
Iteration formula for Bisection Method?
$$\huge{x_n = \frac{a_n + b_n}{2}}$$

False Position (Regula Falsi) formula?
$$\huge{x_n = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}}$$

Iteration (Fixed Point) formula?
$$\huge{x_{n+1} = g(x_n)}$$

Newton–Raphson iteration formula?
$$\huge{x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}}$$

Gauss Elimination (Back Substitution) formula?
$$\huge{x_n = \frac{b_n - \sum_{j=n+1}^{m} a_{nj} x_j}{a_{nn}}}$$

Gauss–Jordan pivot step formula?
$$\huge{a_{ij}^{(new)} = a_{ij}^{(old)} - \frac{a_{ik} a_{kj}}{a_{kk}}}$$

Jacobi iteration formula?
$$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right)}$$

Gauss–Seidel iteration formula?
$$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j<i} a_{ij} x_j^{(k+1)} - \sum_{j>i} a_{ij} x_j^{(k)} \right)}$$

Forward Difference formula?
$$\huge{\Delta f(x) = f(x+h) - f(x)}$$

Backward Difference formula?
$$\huge{\nabla f(x) = f(x) - f(x-h)}$$

Operator relations?
$$\huge{\Delta = E - 1, \quad \nabla = 1 - E^{-1}, \quad E f(x) = f(x+h)}$$

Newton's Forward Interpolation (equal intervals)?
$$\huge{f(x) = f_0 + u \Delta f_0 + \frac{u(u-1)}{2!}\Delta^2 f_0 + \frac{u(u-1)(u-2)}{3!}\Delta^3 f_0 + \dots}$$

Newton's Backward Interpolation (equal intervals)?
$$\huge{f(x) = f_n + u \nabla f_n + \frac{u(u+1)}{2!}\nabla^2 f_n + \frac{u(u+1)(u+2)}{3!}\nabla^3 f_n + \dots}$$

Divided Difference (2 points)?
$$\huge{f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0}}$$

General Divided Difference formula?
$$\huge{f[x_0, x_1, \dots, x_n] = \frac{f[x_1, \dots, x_n] - f[x_0, \dots, x_{n-1}]}{x_n - x_0}}$$

Newton’s Divided Difference Interpolation?
$$\huge{f(x) = f(x_0) + (x - x_0)f[x_0,x_1] + (x - x_0)(x - x_1)f[x_0,x_1,x_2] + \dots}$$

Lagrange Interpolation formula?
$$\huge{f(x) = \sum_{i=0}^{n} f(x_i) \prod_{\substack{j=0 \\ j\ne i}}^{n} \frac{x - x_j}{x_i - x_j}}$$

Inverse Lagrange Interpolation formula?
$$\huge{x = \sum_{i=0}^{n} x_i \prod_{\substack{j=0 \\ j\ne i}}^{n} \frac{f - f(x_j)}{f(x_i) - f(x_j)}}$$

Numerical Differentiation (Forward) formula?
$$\huge{f'(x_0) = \frac{1}{h}\left( \Delta f_0 - \frac{1}{2}\Delta^2 f_0 + \frac{1}{3}\Delta^3 f_0 - \dots \right)}$$

Numerical Differentiation (Backward) formula?
$$\huge{f'(x_n) = \frac{1}{h}\left( \nabla f_n + \frac{1}{2}\nabla^2 f_n + \frac{1}{3}\nabla^3 f_n + \dots \right)}$$

Trapezoidal Rule formula?
$$\huge{\int_a^b f(x) dx = \frac{h}{2}\left[f_0 + 2(f_1 + f_2 + \dots + f_{n-1}) + f_n\right]}$$

Simpson’s 1/3 Rule formula?
$$\huge{\int_a^b f(x) dx = \frac{h}{3}\left[f_0 + 4(f_1 + f_3 + \dots) + 2(f_2 + f_4 + \dots) + f_n\right]}$$

Simpson’s 3/8 Rule formula?
$$\huge{\int_a^b f(x) dx = \frac{3h}{8}\left[f_0 + 3(f_1+f_2 + f_4+f_5 + \dots) + 2(f_3 + f_6 + \dots) + f_n \right]}$$

Taylor Series Method for ODEs?
$$\huge{y(x+h) = y(x) + hy'(x) + \frac{h^2}{2!}y''(x) + \frac{h^3}{3!}y'''(x) + \dots}$$

Euler Method formula?
$$\huge{y_{n+1} = y_n + h f(x_n, y_n)}$$

Improved Euler (Heun’s) Method formula?
$$\huge{y^{*} = y_n + h f(x_n, y_n)}$$
$$\huge{y_{n+1} = y_n + \frac{h}{2} \left[f(x_n, y_n) + f(x_{n+1}, y^{*}) \right]}$$

Modified Euler Method formula?
$$\huge{y_{n+1} = y_n + h f\left(x_n + \frac{h}{2}, y_n + \frac{h}{2} f(x_n,y_n)\right)}$$

Runge–Kutta 2nd Order formula?
$$\huge{k_1 = f(x_n, y_n)}$$
$$\huge{k_2 = f(x_n + h, y_n + hk_1)}$$
$$\huge{y_{n+1} = y_n + \frac{h}{2}(k_1 + k_2)}$$

Runge–Kutta 4th Order formula?
$$\huge{k_1 = f(x_n, y_n)}$$
$$\huge{k_2 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2}k_1)}$$
$$\huge{k_3 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2}k_2)}$$
$$\huge{k_4 = f(x_n + h, y_n + h k_3)}$$
$$\huge{y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)}$$

Standard Five-Point Formula (Laplace Equation)?
$$\huge{u_{i,j} = \frac{1}{4}(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1})}$$

Diagonal Five-Point Formula?
$$\huge{u_{i,j} = \frac{1}{4}(u_{i+1,j+1} + u_{i+1,j-1} + u_{i-1,j+1} + u_{i-1,j-1})}$$

Liebmann (Iterative) Method formula?
$$\huge{u_{i,j}^{(k+1)} = \frac{1}{4}\left(u_{i+1,j}^{(k)} + u_{i-1,j}^{(k+1)} + u_{i,j+1}^{(k)} + u_{i,j-1}^{(k+1)}\right)}$$

Poisson Equation formula?
$$\huge{u_{i,j} = \frac{1}{4}\left(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1} - h^2 f_{i,j} \right)}$$

Bender–Schmidt Scheme (1D Parabolic Equation)?
$$\huge{\lambda = \frac{\alpha k}{h^2}}$$
$$\huge{u_{i}^{n+1} = (1 - 2\lambda)u_i^n + \lambda (u_{i-1}^n + u_{i+1}^n)}$$

Crank–Nicolson Scheme formula?
$$\huge{\frac{u_i^{n+1} - u_i^n}{k} = \alpha \frac{1}{2} \left( \frac{u_{i+1}^{n+1} - 2u_i^{n+1} + u_{i-1}^{n+1}}{h^2} + \frac{u_{i+1}^{n} - 2u_i^{n} + u_{i-1}^{n}}{h^2} \right)}$$

```
