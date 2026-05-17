---
updated_at: 2026-05-17T22:11:31.205+05:30
edited_seconds: 40
---
# Probability & Queueing Theory — Complete Formula Sheet

---

# UNIT 1 — Random Variables

- Mean
    

$$  
E(X)=\sum xP(x)  
$$

or

$$  
E(X)=\int xf(x),dx  
$$

- Variance
    

$$  
Var(X)=E(X^2)-[E(X)]^2  
$$

- Standard Deviation
    

$$  
\sigma=\sqrt{Var(X)}  
$$

- CDF
    

$$  
F(x)=P(X\le x)  
$$

- PDF from CDF
    

$$  
f(x)=\frac{dF(x)}{dx}  
$$

- MGF
    

$$  
M_X(t)=E(e^{tX})  
$$

- Mean using MGF
    

$$  
M'(0)  
$$

- Variance using MGF
    

$$  
M''(0)-[M'(0)]^2  
$$

- Transformation Formula
    

$$  
f_Y(y)=f_X(x)\left|\frac{dx}{dy}\right|  
$$

- Chebyshev’s Inequality
    

$$  
P(|X-\mu|\ge k\sigma)\le \frac{1}{k^2}  
$$




- Variance Rule
    

$$  
Var(aX+b)=a^2Var(X)  
$$

---

# UNIT 2 — Theoretical Distributions

- Binomial PMF
    

$$  
P(X=x)=\binom{n}{x}p^xq^{n-x}  
$$

- Binomial Mean
    

$$  
np  
$$

- Binomial Variance
    

$$  
npq  
$$

- Binomial MGF
    

$$  
(q+pe^t)^n  
$$

- Poisson PMF
    

$$  
P(X=x)=e^{-\lambda}\frac{\lambda^x}{x!}  
$$

- Poisson Mean and Variance
    

$$  
\lambda  
$$

- Poisson MGF
    

$$  
e^{\lambda(e^t-1)}  
$$

- Exponential PDF
    

$$  
f(x)=\lambda e^{-\lambda x},\quad x\ge0  
$$

- Exponential Mean
    

$$  
\frac{1}{\lambda}  
$$

- Exponential Variance
    

$$  
\frac{1}{\lambda^2}  
$$

- Exponential MGF
    

$$  
\frac{\lambda}{\lambda-t}  
$$

- Normal PDF
    

$$  
\frac{1}{\sigma\sqrt{2\pi}}  
e^{-\frac{(x-\mu)^2}{2\sigma^2}}  
$$

- Standard Normal Variable
    

$$  
Z=\frac{X-\mu}{\sigma}  
$$

- Normal MGF
    

$$  
e^{\mu t+\frac{\sigma^2t^2}{2}}  
$$

---

# UNIT 3 — Two Dimensional Random Variables

- Marginal PDF
    

$$  
f_X(x)=\int f(x,y),dy  
$$

- Conditional PDF
    

$$  
f(x|y)=\frac{f(x,y)}{f_Y(y)}  
$$

- Independence
    

$$  
f(x,y)=f_X(x)f_Y(y)  
$$

- Covariance
    

$$  
Cov(X,Y)=E(XY)-E(X)E(Y)  
$$

- Correlation Coefficient
    

$$  
\rho=\frac{Cov(X,Y)}{\sigma_X\sigma_Y}  
$$

- Variance of Sum
    

$$  
Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)  
$$

- Variance of Difference
    

$$  
Var(X-Y)=Var(X)+Var(Y)-2Cov(X,Y)  
$$

- Regression Line
    

$$  
Y-\bar{Y}=b_{yx}(X-\bar{X})  
$$

- Regression Coefficient
    

$$  
b_{yx}=r\left(\frac{\sigma_y}{\sigma_x}\right)  
$$

- Correlation from Regression
    

$$  
r=\sqrt{b_{xy}b_{yx}}  
$$

- Central Limit Theorem (CLT)
    

$$  
Z=\frac{\bar{X}-\mu}{\sigma/\sqrt{n}}  
$$

---

# UNIT 4 — Queueing Theory

- Traffic Intensity
    

$$  
\rho=\frac{\lambda}{\mu}  
$$

- Stability Condition
    

$$  
\lambda<\mu  
$$

- M/M/1 Probability
    

$$  
P_n=(1-\rho)\rho^n  
$$

- Average Customers in System
    

$$  
L_s=\frac{\lambda}{\mu-\lambda}  
$$

- Average Customers in Queue
    

$$  
L_q=\frac{\lambda^2}{\mu(\mu-\lambda)}  
$$

- Average Waiting Time in System
    

$$  
W_s=\frac{1}{\mu-\lambda}  
$$

- Average Waiting Time in Queue
    

$$  
W_q=\frac{\lambda}{\mu(\mu-\lambda)}  
$$

- Little’s Formula
    

$$  
L=\lambda W  
$$

- Little’s Queue Formula
    

$$  
L_q=\lambda W_q  
$$

- Idle Probability
    

$$  
P_0=1-\rho  
$$

---

# UNIT 5 — Markov Chains

- Transition Probability Matrix
    

$$  
P=[P_{ij}]  
$$

- Row Sum Property
    

$$  
\sum P_{ij}=1  
$$

- Chapman-Kolmogorov Equation
    

$$  
P^{(n+m)}=P^nP^m  
$$

- Steady State Condition
    

$$  
\pi P=\pi  
$$

- Absorbing State
    

$$  
P_{ii}=1  
$$

- Transient State
    

$$  
\text{May not return}  
$$

- Recurrent State
    

$$  
\text{Returns with probability 1}  
$$
