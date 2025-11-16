---
updated_at: 2025-11-16T19:13:04.638+05:30
edited_seconds: 20
---
#Maths 
Each question from your uploaded question paper (21MAB206T – Numerical Methods and Analysis, Dec 2024) is explained below, referencing the matching answer provided in your answer key.

---

## PART A (MCQs) Explanations

|Qn|Question (Shortened for Clarity)|Correct Option|Explanation|
|---|---|---|---|
|1|Gauss-Jordan – matrix reduced to?|D|The coefficient matrix is reduced to an identity matrix in Gauss-Jordan elimination. 21MAB206T-Dec-24-Answer-Key.PDF​|
|2|Newton-Raphson also called?|A|It is called the method of tangents, since it uses tangent lines for root-finding. 21MAB206T-Dec-24-Answer-Key.PDF​|
|3|x - 2x = 50, negative root lies between?|C|The negative root lies between -2 and -3, verified by checking signs of function values. 21MAB206T-Dec-24-Answer-Key.PDF​|
|4|Sufficient condition for convergence?|B|Sufficient condition: absolute value of the iteration function’s derivative is less than 1: $$|
|5|Δf(x)\Delta f(x)Δf(x) for f(x)=x2−3x+1f(x) = x^2 - 3x + 1f(x)=x2−3x+1, h=1h=1h=1?|C|Δf(x)=f(x+1)−f(x)\Delta f(x) = f(x+1) - f(x)Δf(x)=f(x+1)−f(x); for this quadratic difference, result simplifies to 2. 21MAB206T-Dec-24-Answer-Key.PDF​|
|6|Relation between E and V?|C|V=E−1V = E - 1V=E−1, where EEE is the shift operator and VVV is the backward operator. 21MAB206T-Dec-24-Answer-Key.PDF​|
|7|Unequally spaced values – which interpolation?|D|Lagrange’s interpolation is suitable for unequally spaced data points. 21MAB206T-Dec-24-Answer-Key.PDF​|
|8|First divided difference formula?|A|Defined as f[x0,x1]=f(x1)−f(x0)x1−x0f[x_0, x_1] = \frac{f(x_1) - f(x_0)}{x_1 - x_0}f[x0,x1]=x1−x0f(x1)−f(x0). 21MAB206T-Dec-24-Answer-Key.PDF​|
|9|Trapezoidal rule accuracy improved by?|C|Increasing number of intervals and decreasing step size hhh, i.e., more but finer intervals. 21MAB206T-Dec-24-Answer-Key.PDF​|
|10|Simpson’s 1/3 rule formula?|A|∫abf(x)dx≈h3[y0+4y1+y2]\int_a^b f(x)dx \approx \frac{h}{3}[y_0 + 4y_1 + y_2]∫abf(x)dx≈3h[y0+4y1+y2] for three equally spaced ordinates. 21MAB206T-Dec-24-Answer-Key.PDF​|
|11|Simpson’s 3/8 rule applicable when n is?|D|Number of intervals must be a multiple of 3. 21MAB206T-Dec-24-Answer-Key.PDF​|
|12|Error order in Simpson’s 1/3 rule?|B|Order of error is h4h^4h4. 21MAB206T-Dec-24-Answer-Key.PDF​|
|13|In 4th order Runge-Kutta, Δy\Delta yΔy stands for?|D|The weighted sum in Runge-Kutta: Δy=16(k1+2k2+2k3+k4)\Delta y = \frac{1}{6}(k_1 + 2k_2 + 2k_3 + k_4)Δy=61(k1+2k2+2k3+k4). 21MAB206T-Dec-24-Answer-Key.PDF​|
|14|Improved Euler’s method formula?|B|It is based on the average of slopes: yn+1=yn+h2[f(xn,yn)+f(xn+1,yn+1)]y_{n+1} = y_n + \frac{h}{2}[f(x_n, y_n) + f(x_{n+1}, y_{n+1})]yn+1=yn+2h[f(xn,yn)+f(xn+1,yn+1)]. 21MAB206T-Dec-24-Answer-Key.PDF​|
|15|Improved Euler’s method is based on averages of?|B|Slopes. 21MAB206T-Dec-24-Answer-Key.PDF​|
|16|Best method among: Taylor, Euler, Improved Euler, 4th order RK?|D|4th order Runge-Kutta is generally most accurate. 21MAB206T-Dec-24-Answer-Key.PDF​|
|17|∂u∂x2+∂u∂y2=f(x,y)\frac{\partial u}{\partial x^2} + \frac{\partial u}{\partial y^2} = f(x, y)∂x2∂u+∂y2∂u=f(x,y) is?|D|Poisson equation. 21MAB206T-Dec-24-Answer-Key.PDF​|
|18|Bender-Schmidt scheme converges for?|B|Converges for λ≤12\lambda \leq \frac{1}{2}λ≤21. 21MAB206T-Dec-24-Answer-Key.PDF​|
|19|Δxxu−4u+8x=0\Delta_{xx}u - 4u + 8x = 0Δxxu−4u+8x=0 – name?|B|Bender-Schmidt formula. 21MAB206T-Dec-24-Answer-Key.PDF​|
|20|Error in diagonal five point formula is ___ times that of standard formula?|C|Four times. 21MAB206T-Dec-24-Answer-Key.PDF​|

---

Here is a detailed explanation of Parts B and C from the question paper 21MAB206T Numerical Methods and Analysis, along with the corresponding solution approach from the answer key:

---

## Part B - Detailed Solutions and Explanations

**21a. Finding the Positive Root of x3−2x−50=0x^3 - 2x - 50 = 0x3−2x−50=0 Using Iteration**

- The function f(x)=x3−2x−50f(x) = x^3 - 2x - 50f(x)=x3−2x−50.
    
- The root lies between 2 and 3 (by evaluating f(2)f(2)f(2) and f(3)f(3)f(3)).
    
- Iterative values calculated: x0=2.0x_0 = 2.0x0=2.0, x1=2.0801x_1 = 2.0801x1=2.0801, x2=2.0924x_2 = 2.0924x2=2.0924, x3=2.0942x_3 = 2.0942x3=2.0942, x4=2.0945x_4 = 2.0945x4=2.0945, x5=2.0945x_5 = 2.0945x5=2.0945.
    
- The root converges to approximately **2.0945**.
    

**21b. Solving System of Equations Using Gauss-Seidel Method**

- Given equations:
    
    10x−5y−2z=3,4x−10y+3z=−3,x+6y+10z=−810x - 5y - 2z = 3, \quad 4x - 10y + 3z = -3, \quad x + 6y + 10z = -810x−5y−2z=3,4x−10y+3z=−3,x+6y+10z=−8
- Initial values chosen for y0,z0y_0, z_0y0,z0.
    
- Iterative values for each variable calculated stepwise with convergence shown in values of x,y,zx, y, zx,y,z for several iterations.
    
- Approximate final solution values after convergence given.
    

**22a. Applying Lagrange’s Interpolation**

- For given data points (xi,yi)(x_i, y_i)(xi,yi), the interpolating polynomial is constructed using:
    

y=∑yi∏j≠ix−xjxi−xjy = \sum y_i \prod_{j \neq i} \frac{x - x_j}{x_i - x_j}y=∑yij=i∏xi−xjx−xj

- Use degree n=3n = 3n=3, substitute to find yyy for required xxx.
    

**22b. Newton’s Forward Difference Interpolation for Population Estimation**

- Population data of years is tabulated with forward differences.
    
- Formula for interpolation:
    

P(x)=P0+uΔP0+u(u−1)2!Δ2P0+⋯P(x) = P_0 + u \Delta P_0 + \frac{u(u-1)}{2!} \Delta^2 P_0 + \cdotsP(x)=P0+uΔP0+2!u(u−1)Δ2P0+⋯

where u=x−x0hu = \frac{x-x_0}{h}u=hx−x0.

- Compute interpolated population for year 1946.
    

**23a. Computation of Angular Velocity and Acceleration**

- Angular position data θ(t)\theta(t)θ(t) given at specific time steps.
    
- Use finite difference methods:
    
    - Velocity v=ΔθΔtv = \frac{\Delta \theta}{\Delta t}v=ΔtΔθ
        
    - Acceleration a=Δ2θΔt2a = \frac{\Delta^2 \theta}{\Delta t^2}a=Δt2Δ2θ
        
- Tabulate velocity and acceleration values at t=0.2t=0.2t=0.2 seconds.
    

**23b. Calculating Time Using Simpson’s 1/3 and 3/8 Rules**

- Velocity data over distance used to calculate time to travel 60 feet.
    
- Use numerical integration formulas for:
    
    - Simpson’s 1/3 rule
        
    - Simpson’s 3/8 rule
        
- Results compared for accuracy.
    

**24a. Solving ODE Using Taylor Series**

- Given dydx=x2−y\frac{dy}{dx} = x^2 - ydxdy=x2−y, y(0)=1y(0) = 1y(0)=1.
    
- Taylor expansion around x=0x = 0x=0 computes yyy at 0.10.10.1 and 0.20.20.2.
    
- Steps involve recursive computation of higher derivatives for series terms.
    

**24b. Improved Euler (Heun’s) Method Application**

- For dydx=y+ex\frac{dy}{dx} = y + e^xdxdy=y+ex, y(0)=0y(0)=0y(0)=0.
    
- Step size h=0.2h=0.2h=0.2, compute y(0.2)y(0.2)y(0.2) and y(0.4)y(0.4)y(0.4) using:
    

yn+1=yn+h2(f(xn,yn)+f(xn+1,yn∗))y_{n+1} = y_n + \frac{h}{2}(f(x_n,y_n) + f(x_{n+1}, y^*_n))yn+1=yn+2h(f(xn,yn)+f(xn+1,yn∗))

where yn∗y^*_nyn∗ is predictor.

**25a. Bender-Schmidt Explicit Scheme for Heat Equation**

- PDE with boundary & initial conditions applied.
    
- Time step k=1/2k=1/2k=1/2, step size h=1h=1h=1.
    
- Numerical solution developed to compute uuu values for mesh points up to t=5t=5t=5 seconds.
    

**25b. Applying Five-point Formula for Laplace’s Equation**

- Using discrete Laplace operator to approximate uuu at grid points.
    
- Formula considers neighboring points in 2D grid with appropriate weights.
    
- Solve to get approximate values ui,ju_{i,j}ui,j.
    

---

## Part C - Detailed Solutions and Explanations

**26. Gauss-Jordan Method for System of Linear Equations**

- System:
    

{x+y+z=92x−3y+4z=133x+4y+5z=40\begin{cases} x + y + z = 9 \\ 2x - 3y + 4z = 13 \\ 3x + 4y + 5z = 40 \end{cases}⎩⎨⎧x+y+z=92x−3y+4z=133x+4y+5z=40

- Form augmented matrix and apply row operations to reduce to:
    

[100a010b001c]\begin{bmatrix} 1 & 0 & 0 & a \\ 0 & 1 & 0 & b \\ 0 & 0 & 1 & c \end{bmatrix}100010001abc

- Solution x=a,y=b,z=cx = a, y = b, z = cx=a,y=b,z=c.
    

**26. Crank-Nicholson Method for Heat Equation**

- Implicit finite difference method averaging explicit and implicit schemes.
    
- For heat equation discretized in time and space.
    
- Compute uij+1u^{j+1}_iuij+1 values for next time step using previous time step and space neighbors.
    
- Stability and accuracy improved for time-stepping.
    

**27. Runge-Kutta 4th Order Method for ODE**

- Solving dydx=x−y,y(0)=1\frac{dy}{dx} = x - y, y(0) = 1dxdy=x−y,y(0)=1.
    
- At each step compute:
    
    k1=hf(xn,yn),k2=hf(xn+h2,yn+k12),k3=hf(xn+h2,yn+k22),k4=hf(xn+h,yn+k3)k_1 = h f(x_n, y_n), \quad k_2 = h f(x_n + \frac{h}{2}, y_n + \frac{k_1}{2}), \quad k_3 = h f(x_n + \frac{h}{2}, y_n + \frac{k_2}{2}), \quad k_4 = h f(x_n + h, y_n + k_3)k1=hf(xn,yn),k2=hf(xn+2h,yn+2k1),k3=hf(xn+2h,yn+2k2),k4=hf(xn+h,yn+k3)
- Next value:
    

yn+1=yn+16(k1+2k2+2k3+k4)y_{n+1} = y_n + \frac{1}{6}(k_1 + 2k_2 + 2k_3 + k_4)yn+1=yn+61(k1+2k2+2k3+k4)

- Compute values at x=0.1x=0.1x=0.1 and x=0.2x=0.2x=0.2.
    

---

