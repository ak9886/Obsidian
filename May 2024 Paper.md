---
updated_at: 2025-11-16T19:24:04.306+05:30
edited_seconds: 140
---
---

## **PART A (MCQs) – LaTeX Version**

|Qn|Question (Shortened)|Correct|Explanation|
|---|---|---|---|
|1|Gauss–Jordan reduces matrix to?|D|Coefficient matrix → identity matrix.|
|2|Newton–Raphson is also called?|A|Called the _method of tangents_.|
|3|Negative root of (x^3 - 2x = 50) lies between?|C|Sign check shows root ∈ ($$[-3,-2]$$).|
|4|Sufficient condition for convergence?|B|$$\left|
|5|(\Delta f(x)) for (f(x)=x^2 - 3x + 1,; h=1)?|C|$$\Delta f(x)=f(x+1)-f(x)=2$$|
|6|Relation between (E) and (V)?|C|$$V = E^{-1}$$|
|7|Interpolation for unequal spacing?|D|Lagrange interpolation.|
|8|First divided difference?|A|$$f$$[x_0,x_1]$$=\frac{f(x_1)-f(x_0)}{x_1-x_0}$$|
|9|Trapezoidal rule accuracy improves by?|C|More intervals → smaller (h).|
|10|Simpson’s (1/3) rule?|A|$$\int_a^b f(x)dx \approx \frac{h}{3}(y_0+4y_1+y_2)$$|
|11|Simpson’s (3/8) rule valid when (n) is?|D|Multiple of 3.|
|12|Error order of Simpson’s (1/3) rule?|B|Order: (h^4).|
|13|Meaning of (\Delta y) in RK4?|D|$$\Delta y=\frac{1}{6}(k_1 + 2k_2 + 2k_3 + k_4)$$|
|14|Improved Euler formula?|B|$$y_{n+1}=y_n+\frac{h}{2}\left$$[f(x_n,y_n)+f(x_{n+1},y_{n+1})\right]$$$$|
|15|Improved Euler averages what?|B|Slopes.|
|16|Most accurate method?|D|Fourth-order RK.|
|17|Equation (\frac{\partial^2 u}{\partial x^2}+\frac{\partial^2 u}{\partial y^2}=f(x,y))?|D|Poisson equation.|
|18|Bender–Schmidt converges for?|B|$$\lambda \le \frac{1}{2}$$|
|19|(\Delta_{xx}u - 4u + 8x = 0) is called?|B|Bender–Schmidt formula.|
|20|Diagonal 5-point formula error vs standard?|C|Four times greater.|

---

# **PART B – 

## **21(a) Iteration Method – Root of (x^3 - 2x - 50 = 0)**

Given  
$$f(x)=x^3-2x-50$$

Values show the root is between 2 and 3.

Iterations:

$$[  
x_0=2.0,; x_1=2.0801,; x_2=2.0924,; x_3=2.0942,; x_4=2.0945,; x_5=2.0945  
]$$

$$[  
\text{Root} \approx 2.0945  
]$$

---

## **21(b) Gauss–Seidel Method**

Equations:

$$[  
\begin{aligned}  
10x - 5y - 2z &= 3\  
4x - 10y + 3z &= -3\  
x + 6y + 10z &= -8  
\end{aligned}  
]$$

Gauss–Seidel updates:

$$[  
x^{(k+1)} = \frac{3 + 5y^{(k)} + 2z^{(k)}}{10}  
]$$

$$[  
y^{(k+1)} = \frac{-3 - 4x^{(k+1)} - 3z^{(k)}}{-10}  
]$$

$$[  
z^{(k+1)} = \frac{-8 - x^{(k+1)} - 6y^{(k+1)}}{10}  
]$$

Iterations → convergent solution.

---

## **22(a) Lagrange Interpolation**

$$[  
P(x)=\sum_{i=0}^{n} y_i  
\prod_{j\ne i}\frac{x-x_j}{x_i-x_j}  
]$$

Use given 4 points ((n=3)) and evaluate required (P(x)).

---

## **22(b) Newton Forward Interpolation**

$$[  
P(x)=P_0 + u\Delta P_0 + \frac{u(u-1)}{2!}\Delta^2 P_0+\cdots  
]$$

with

$$[  
u=\frac{x-x_0}{h}  
]$$

Used to estimate population for year 1946.

---

## **23(a) Angular Velocity & Acceleration**

$$[  
v=\frac{\Delta \theta}{\Delta t},\qquad  
a=\frac{\Delta^2\theta}{\Delta t^2}  
]$$

Compute at (t = 0.2,\text{s}).

---

## **23(b) Simpson’s Rules for Time Computation**

Simpson (1/3):

$$[  
\int f(x),dx\approx \frac{h}{3}(y_0+4y_1+y_2)  
]$$

Simpson (3/8):

$$[  
\int f(x),dx\approx \frac{3h}{8}(y_0+3y_1+3y_2+y_3)  
]$$

---

## **24(a) Taylor Series Method**

ODE:

$$[  
\frac{dy}{dx}=x^2-y,\qquad y(0)=1  
]$$

Expand:

$$[  
y(x)=y_0 + y_0'x + \frac{y_0''}{2!}x^2 + \cdots  
]$$

Compute (y(0.1)) and (y(0.2)).

---

## **24(b) Improved Euler (Heun’s Method)**

ODE:

$$[  
\frac{dy}{dx}=y+e^x,\qquad y(0)=0,\qquad h=0.2  
]$$

Predictor:

$$[  
y_n^* = y_n + h f(x_n,y_n)  
]$$

Corrector:

$$[  
y_{n+1} = y_n + \frac{h}{2}\big]$$$$[f(x_n,y_n)+f(x_{n+1},y_n^*)\big]$$  


Compute $(y(0.2)), (y(0.4))$.

---

## **25(a) Bender–Schmidt Scheme**

Heat equation:

$$[  
u_i^{j+1} = (1-2\lambda)u_i^j + \lambda (u_{i-1}^j + u_{i+1}^j)  
]$$

with (k=\frac{1}{2}), (h=1).

Compute up to (t=5).

---

## **25(b) Five-Point Laplace Formula**

$$[  
u_{i,j} = \frac{1}{4},(u_{i+1,j}+u_{i-1,j}+u_{i,j+1}+u_{i,j-1})  
]$$

Solve grid values.

---

# **PART C – LaTeX Version**

## **26(a) Gauss–Jordan Method**

System:

$$[  
\begin{cases}  
x + y + z = 9\  
2x - 3y + 4z = 13\  
3x + 4y + 5z = 40  
\end{cases}  
]$$

Augmented matrix → RREF:

$$[  
\begin{bmatrix}  
1 & 0 & 0 & a\  
0 & 1 & 0 & b\  
0 & 0 & 1 & c  
\end{bmatrix}  
]$$

Solution: (x=a,; y=b,; z=c).

---

## **26(b) Crank–Nicolson Method**

General form:

$$[
\frac{u_i^{j+1} - u_i^{j}}{k}
= \frac{1}{2}\left(
\frac{u_{i+1}^{j} - 2u_i^{j} + u_{i-1}^{j}}{h^2}
+
\frac{u_{i+1}^{j+1} - 2u_i^{j+1} + u_{i-1}^{j+1}}{h^2}
\right)
]$$
$$[  
\frac{u_{i+1}^j - 2u_i^j + u_{i-1}^j}{h^2} ]$$
+  
\frac{u_{i+1}^{j+1} - 2u_i^{j+1} + u_{i-1}^{j+1}}{h^2}  
\right]$$  
]$$

Solve tridiagonal system for each time step.

---

## **27. Runge–Kutta 4th Order**

ODE:

$$[  
\frac{dy}{dx}=x-y,\qquad y(0)=1  
]$$

$$[  
\begin{aligned}  
k_1 &= h f(x_n,y_n)\  
k_2 &= h f\left(x_n+\frac{h}{2},, y_n+\frac{k_1}{2}\right)\  
k_3 &= h f\left(x_n+\frac{h}{2},, y_n+\frac{k_2}{2}\right)\  
k_4 &= h f(x_n+h,, y_n+k_3)  
\end{aligned}  
]$$

$$[  
y_{n+1}=y_n+\frac{1}{6}(k_1+2k_2+2k_3+k_4)  
]$$

Evaluate at (x=0.1) and (0.2).

---

