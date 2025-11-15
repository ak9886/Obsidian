---
updated_at: 2025-11-15T13:28:54.510+05:30
edited_seconds: 190
---
```markdown
Iteration formula for Bisection Method?
$$\huge{x_n = \frac{a_n + b_n}{2}}$$

Bisection Method: Root interval update (left)?
$$\huge{a_{n+1} = x_n \text{ if } f(a_n)f(x_n) > 0}$$

Bisection Method: Root interval update (right)?
$$\huge{b_{n+1} = x_n \text{ if } f(a_n)f(x_n) < 0}$$

False Position (Regula Falsi) formula?
$$\huge{x_n = \frac{a_n f(b_n) - b_n f(a_n)}{f(b_n) - f(a_n)}}$$

Iteration (Fixed Point) formula?
$$\huge{x_{n+1} = g(x_n)}$$

Fixed Point: Convergence condition?
$$\huge{|g'(x)| < 1}$$

Newton–Raphson iteration formula?
$$\huge{x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}}$$

Gauss Elimination: Back Substitution?
$$\huge{x_n = \frac{b_n - \sum_{j=n+1}^{m} a_{nj} x_j}{a_{nn}}}$$

Gauss–Jordan pivot step formula?
$$\huge{a_{ij}^{(new)} = a_{ij}^{(old)} - \frac{a_{ik} a_{kj}}{a_{kk}}}$$

Jacobi iteration formula?
$$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right)}$$

Gauss–Seidel iteration formula?
$$\huge{x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j<i} a_{ij} x_j^{(k+1)} - \sum_{j>i} a_{ij} x_j^{(k)} \right)}$$

Forward Difference formula?
$$\huge{\Delta f(x) = f(x+h) - f(x)}$$

Second Forward Difference formula?
$$\huge{\Delta^2 f(x) = \Delta f(x+h) - \Delta f(x)}$$

Third Forward Difference formula?
$$\huge{\Delta^3 f(x) = \Delta^2 f(x+h) - \Delta^2 f(x)}$$

Backward Difference formula?
$$\huge{\nabla f(x) = f(x) - f(x-h)}$$

Second Backward Difference formula?
$$\huge{\nabla^2 f(x) = \nabla f(x) - \nabla f(x-h)}$$

Third Backward Difference formula?
$$\huge{\nabla^3 f(x) = \nabla^2 f(x) - \nabla^2 f(x-h)}$$

Operator relation: Delta?
$$\huge{\Delta = E - 1}$$

Operator relation: Nabla?
$$\huge{\nabla = 1 - E^{-1}}$$

Shift operator formula?
$$\huge{E f(x) = f(x+h)}$$

Newton's Forward Interpolation formula (first term)?
$$\huge{f(x) = f_0}$$

Newton's Forward Interpolation formula (second term)?
$$\huge{+ u \Delta f_0}$$

Newton's Forward Interpolation formula (third term)?
$$\huge{+ \frac{u(u-1)}{2!} \Delta^2 f_0}$$

Newton's Forward Interpolation formula (fourth term)?
$$\huge{+ \frac{u(u-1)(u-2)}{3!} \Delta^3 f_0}$$

Newton's Backward Interpolation formula (first term)?
$$\huge{f(x) = f_n}$$

Newton's Backward Interpolation formula (second term)?
$$\huge{+ u \nabla f_n}$$

Newton's Backward Interpolation formula (third term)?
$$\huge{+ \frac{u(u+1)}{2!} \nabla^2 f_n}$$

Newton's Backward Interpolation formula (fourth term)?
$$\huge{+ \frac{u(u+1)(u+2)}{3!} \nabla^3 f_n}$$

Divided Difference (2 points)?
$$\huge{f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0}}$$

Divided Difference (3 points)?
$$\huge{f[x_0, x_1, x_2] = \frac{f[x_1, x_2] - f[x_0, x_1]}{x_2 - x_0}}$$

Newton’s Divided Difference Interpolation formula (first term)?
$$\huge{f(x) = f(x_0)}$$

Newton’s Divided Difference Interpolation formula (second term)?
$$\huge{+ (x - x_0) f[x_0,x_1]}$$

Newton’s Divided Difference Interpolation formula (third term)?
$$\huge{+ (x - x_0)(x - x_1) f[x_0,x_1,x_2]}$$

Lagrange Interpolation formula (general)?
$$\huge{f(x) = \sum_{i=0}^{n} f(x_i) \prod_{\substack{j=0 \\ j\ne i}}^{n} \frac{x - x_j}{x_i - x_j}}$$

Inverse Lagrange Interpolation formula (general)?
$$\huge{x = \sum_{i=0}^{n} x_i \prod_{\substack{j=0 \\ j\ne i}}^{n} \frac{f - f(x_j)}{f(x_i) - f(x_j)}}$$

Forward Difference Derivative (first order)?
$$\huge{f'(x_0) = \frac{1}{h} \Delta f_0}$$

Forward Difference Derivative (second order correction)?
$$\huge{- \frac{1}{2h} \Delta^2 f_0}$$

Forward Difference Derivative (third order correction)?
$$\huge{+ \frac{1}{3h} \Delta^3 f_0}$$

Backward Difference Derivative (first order)?
$$\huge{f'(x_n) = \frac{1}{h} \nabla f_n}$$

Backward Difference Derivative (second order correction)?
$$\huge{+ \frac{1}{2h} \nabla^2 f_n}$$

Backward Difference Derivative (third order correction)?
$$\huge{+ \frac{1}{3h} \nabla^3 f_n}$$

Trapezoidal Rule: First term?
$$\huge{\frac{h}{2} f_0}$$

Trapezoidal Rule: Middle terms sum?
$$\huge{+ \frac{h}{2} \cdot 2(f_1 + f_2 + \dots + f_{n-1})}$$

Trapezoidal Rule: Last term?
$$\huge{+ \frac{h}{2} f_n}$$

Simpson's 1/3 Rule: First term?
$$\huge{\frac{h}{3} f_0}$$

Simpson's 1/3 Rule: Odd terms sum?
$$\huge{+ \frac{h}{3} \cdot 4(f_1 + f_3 + f_5 + \dots)}$$

Simpson's 1/3 Rule: Even terms sum?
$$\huge{+ \frac{h}{3} \cdot 2(f_2 + f_4 + \dots)}$$

Simpson's 1/3 Rule: Last term?
$$\huge{+ \frac{h}{3} f_n}$$

Simpson's 3/8 Rule: First term?
$$\huge{\frac{3h}{8} f_0}$$

Simpson's 3/8 Rule: Terms with coefficient 3?
$$\huge{+ \frac{3h}{8} (f_1 + f_2 + f_4 + f_5 + \dots)}$$

Simpson's 3/8 Rule: Terms with coefficient 2?
$$\huge{+ \frac{3h}{8} (f_3 + f_6 + \dots)}$$

Simpson's 3/8 Rule: Last term?
$$\huge{+ \frac{3h}{8} f_n}$$

Taylor Series Method: First term?
$$\huge{y(x+h) = y(x)}$$

Taylor Series Method: First derivative term?
$$\huge{+ h y'(x)}$$

Taylor Series Method: Second derivative term?
$$\huge{+ \frac{h^2}{2!} y''(x)}$$

Taylor Series Method: Third derivative term?
$$\huge{+ \frac{h^3}{3!} y'''(x)}$$

Euler Method formula?
$$\huge{y_{n+1} = y_n + h f(x_n, y_n)}$$

Improved Euler (Heun’s) Method: Predictor?
$$\huge{y^* = y_n + h f(x_n, y_n)}$$

Improved Euler (Heun’s) Method: Corrector first part?
$$\huge{y_{n+1} = y_n + \frac{h}{2} f(x_n, y_n)}$$

Improved Euler (Heun’s) Method: Corrector second part?
$$\huge{+ \frac{h}{2} f(x_{n+1}, y^*)}$$

Modified Euler Method formula?
$$\huge{y_{n+1} = y_n + h f(x_n + \frac{h}{2}, y_n + \frac{h}{2} f(x_n,y_n))}$$

Runge–Kutta 2nd Order: k1?
$$\huge{k_1 = f(x_n, y_n)}$$

Runge–Kutta 2nd Order: k2?
$$\huge{k_2 = f(x_n + h, y_n + h k_1)}$$

Runge–Kutta 2nd Order: y_{n+1}?
$$\huge{y_{n+1} = y_n + \frac{h}{2} (k_1 + k_2)}$$

Runge–Kutta 4th Order: k1?
$$\huge{k_1 = f(x_n, y_n)}$$

Runge–Kutta 4th Order: k2?
$$\huge{k_2 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2} k_1)}$$

Runge–Kutta 4th Order: k3?
$$\huge{k_3 = f(x_n + \frac{h}{2}, y_n + \frac{h}{2} k_2)}$$

Runge–Kutta 4th Order: k4?
$$\huge{k_4 = f(x_n + h, y_n + h k_3)}$$

Runge–Kutta 4th Order: y_{n+1}?
$$\huge{y_{n+1} = y_n + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k_4)}$$

Standard Five-Point Formula (Laplace): u_{i,j}?
$$\huge{u_{i,j} = \frac{1}{4}(u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1})}$$

Diagonal Five-Point Formula: u_{i,j}?
$$\huge{u_{i,j} = \frac{1}{4}(u_{i+1,j+1} + u_{i+1,j-1} + u_{i-1,j+1} + u_{i-1,j-1})}$$

Liebmann Method: u_{i,j}^{(k+1)} first part?
$$\huge{u_{i,j}^{(k+1)} = \frac{1}{4} u_{i+1,j}^{(k)}}$$

Liebmann Method: u_{i,j}^{(k+1)} second part?
$$\huge{+ \frac{1}{4} u_{i-1,j}^{(k+1)}}$$

Liebmann Method: u_{i,j}^{(k+1)} third part?
$$\huge{+ \frac{1}{4} u_{i,j+1}^{(k)}}$$

Liebmann Method: u_{i,j}^{(k+1)} fourth part?
$$\huge{+ \frac{1}{4} u_{i,j-1}^{(k+1)}}$$

Poisson Equation update formula: u_{i,j}?
$$\huge{u_{i,j} = \frac{1}{4} \left( u_{i+1,j} + u_{i-1,j} + u_{i,j+1} + u_{i,j-1} - h^2 f_{i,j} \right)}$$

Bender–Schmidt Coefficient λ?
$$\huge{\lambda = \frac{\alpha k}{h^2}}$$

Bender–Schmidt update formula: u_i^{n+1} first part?
$$\huge{u_i^{n+1} = (1 - 2\lambda) u_i^n}$$

Bender–Schmidt update formula: u_i^{n+1} second part?
$$\huge{+ \lambda (u_{i-1}^n + u_{i+1}^n)}$$

Crank–Nicolson Scheme: Left-hand side?
$$\huge{\frac{u_i^{n+1} - u_i^n}{k}}$$

Crank–Nicolson Scheme: Right-hand side first part?
$$\huge{\alpha \frac{1}{2} \frac{u_{i+1}^{n+1} - 2 u_i^{n+1} + u_{i-1}^{n+1}}{h^2}}$$

Crank–Nicolson Scheme: Right-hand side second part?
$$\huge{+ \alpha \frac{1}{2} \frac{u_{i+1}^{n} - 2 u_i^{n} + u_{i-1}^{n}}{h^2}}$$

```
