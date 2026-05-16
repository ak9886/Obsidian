---
updated_at: 2026-05-16T07:56:10.177+05:30
edited_seconds: 380
---
Here is the Obsidian-friendly version with display math for multi-line formulas and inline math for single-line formulas. In Obsidian, `$\huge $\huge  ... $\huge $\huge ` is used for displayed equations, while `$\huge ...$\huge ` is used for inline math without extra spaces.obsidian+1

# Unit 5: Markov Chains — 5 Questions with Full Solutions

## Before We Start

## The Golden Rule of Markov Chains

“The future depends only on the present, not on the past.”

Think of it like this: if you want to predict tomorrow’s weather, you only need to know today’s weather. It does not matter what the weather was last week.

## Basic Concepts You Need to Know

## What is a State?

A state is simply the current situation of a system.

- Example: Weather can be in state “Sunny” or “Rainy”.
    
- Example: A student can be in state “Studying” or “Not Studying”.
    

## What is a Transition Matrix?

It is a table that shows: “If I’m here now, what is the probability I go there next?”

Example:

|Today \ Tomorrow|Sunny|Rainy|
|---|---|---|
|Sunny|0.7|0.3|
|Rainy|0.4|0.6|

Reading this: if it is Sunny today, there is a 70% chance of Sunny tomorrow and a 30% chance of Rainy tomorrow.

## Key Rules

- Every row must add up to 1.0.
    
- All probabilities must be between 0 and 1.
    
- $P(n)P^{(n)}P(n)$ means the matrix after nnn steps, found by multiplying PPP by itself nnn times.
    

---

# Question 1 (Easy - Basic Transition Probability)

## The Problem

A college student named Arjun has the following study habits:

> If he studies one night, there is a 70% chance he studies the next night and a 30% chance he does not.
  If he does not study one night, there is a 60% chance he studies the next night and a 40% chance he does not.  
>  
> On Monday night, Arjun studies.

Find:

1. The transition probability matrix.
    
2. The probability that Arjun studies on Wednesday night.
    
3. The probability that Arjun does not study on Wednesday night.
    

## Full Solution

## Step 1: Understand the States

We have 2 states:

- State 1 = Studies (S)
    
- State 2 = Does not study (D)
    

## Step 2: Write the Transition Probability Matrix

From the problem:

$\huge P=[0.70.30.60.4]P = \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix}P=[0.70.6​0.30.4​]$\huge 

Check:

- Row 1: $\huge 0.7 + 0.3 = 1.0$\huge 
    
- Row 2: $\huge 0.6 + 0.4 = 1.0$\huge 
    

## Step 3: Set Up the Initial State

Arjun studies on Monday, so the initial vector is:

$\huge $\huge \begin{bmatrix}1 & 0\end{bmatrix}$\huge $\huge 

## Step 4: Find Tuesday’s Probabilities

Multiply the initial vector by $\huge P$\huge :

$\huge [0.70.30.60.4]=[0.70.3]\begin{bmatrix}1 & 0\end{bmatrix} \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix} = \begin{bmatrix}0.7 & 0.3\end{bmatrix}[1​0​][0.70.6​0.30.4​]=[0.7​0.3​]$\huge 

So on Tuesday:

- Studies: $\huge 0.7$\huge 
    
- Does not study: $\huge 0.3$\huge 
    

## Step 5: Find Wednesday’s Probabilities

Multiply Tuesday’s vector by $\huge P$\huge  again:

$\huge [0.70.3][0.70.30.60.4]=[0.670.33]\begin{bmatrix}0.7 & 0.3\end{bmatrix} \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix} = \begin{bmatrix}0.67 & 0.33\end{bmatrix}[0.7​0.3​][0.70.6​0.30.4​]=[0.67​0.33​]$\huge 

## Final Answers

- Transition matrix:
    

$\huge P=[0.70.30.60.4]P = \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix}P=[0.70.6​0.30.4​]$\huge 

- Probability Arjun studies on Wednesday = $\huge 0.67 = 67%$\huge 
    
- Probability Arjun does not study on Wednesday = $\huge 0.33 = 33%$\huge 
    

---

# Question 2 (Medium - Finding Specific Path Probability)

## The Problem

A Markov chain has 3 states: 1, 2, 3 with transition matrix

$\huge P=[0.10.50.40.60.20.20.30.40.3]P = \begin{bmatrix} 0.1 & 0.5 & 0.4 \\ 0.6 & 0.2 & 0.2 \\ 0.3 & 0.4 & 0.3 \end{bmatrix}P=​0.10.60.3​0.50.20.4​0.40.20.3​​$\huge 

The initial distribution is

$\huge P(0)=(0.7,0.2,0.1)P^{(0)} = (0.7, 0.2, 0.1)P(0)=(0.7,0.2,0.1)$\huge 

Find:

1. $\huge P(X_2 = 3, X_1 = 3, X_0 = 2)$\huge 
    
2. $\huge P(X_3 = 2, X_2 = 3, X_1 = 3, X_0 = 2)$\huge 
    

## Full Solution

## Step 1: Understand the Path

The first probability is for the path:

$\huge 2→3→32 \to 3 \to 32→3→3$\huge 

## Step 2: Use the Path Formula

$\huge P(X2=3,X1=3,X0=2)=P(X0=2)×P23×P33P(X_2=3, X_1=3, X_0=2) = P(X_0=2) \times P_{23} \times P_{33}P(X2​=3,X1​=3,X0​=2)=P(X0​=2)×P23​×P33​$\huge 

## Step 3: Read Values

From the initial distribution:

- $\huge P(X_0=2) = 0.2$\huge 
    

From the matrix:

- $\huge P_{23} = 0.2$\huge 
    
- $\huge P_{33} = 0.3$\huge 
    

## Step 4: Calculate Part (i)

$\huge 0.2×0.2×0.3=0.0120.2 \times 0.2 \times 0.3 = 0.0120.2×0.2×0.3=0.012$\huge 

So,

$\huge P(X2=3,X1=3,X0=2)=0.012P(X_2=3, X_1=3, X_0=2) = 0.012P(X2​=3,X1​=3,X0​=2)=0.012$\huge 

## Step 5: Calculate Part (ii)

Now the path is:

$\huge 2→3→3→22 \to 3 \to 3 \to 22→3→3→2$\huge 

So,

$\huge P(X3=2,X2=3,X1=3,X0=2)=P(X0=2)×P23×P33×P32P(X_3=2, X_2=3, X_1=3, X_0=2) = P(X_0=2) \times P_{23} \times P_{33} \times P_{32}P(X3​=2,X2​=3,X1​=3,X0​=2)=P(X0​=2)×P23​×P33​×P32​$\huge 

From the matrix:

- $\huge P_{32} = 0.4$\huge 
    

Therefore:

$\huge 0.2×0.2×0.3×0.4=0.00480.2 \times 0.2 \times 0.3 \times 0.4 = 0.00480.2×0.2×0.3×0.4=0.0048$\huge 

## Final Answers

- $\huge P(X_2=3, X_1=3, X_0=2) = 0.012$\huge 
    
- $\huge P(X_3=2, X_2=3, X_1=3, X_0=2) = 0.0048$\huge 
    

---

# Question 3 (Medium - Finding Limiting Probabilities)

## The Problem

A weather system can be in two states:

- State 1: Sunny
    
- State 2: Rainy
    

The transition matrix is

$\huge P=[0.80.20.50.5]P = \begin{bmatrix} 0.8 & 0.2 \\ 0.5 & 0.5 \end{bmatrix}P=[0.80.5​0.20.5​]$\huge 

Find the long-run probabilities of Sunny and Rainy.

## Full Solution

## Step 1: Understand Long-Run Behavior

In the long run, the system settles into a stable pattern. These fixed percentages are called limiting probabilities or steady-state probabilities.

Let

$\huge π=[π1,π2]\pi = [\pi_1, \pi_2]π=[π1​,π2​]$\huge 

where:

- $\huge \pi_1$\huge  = probability of Sunny
    
- $\huge \pi_2$\huge  = probability of Rainy
    

## Step 2: Set Up the Equation

The steady-state condition is:

$\huge πP=π\pi P = \piπP=π$\huge 

## Step 3: Write the Equations

From

$\huge [π1,π2][0.80.20.50.5]=[π1,π2][\pi_1, \pi_2] \begin{bmatrix} 0.8 & 0.2 \\ 0.5 & 0.5 \end{bmatrix} = [\pi_1, \pi_2][π1​,π2​][0.80.5​0.20.5​]=[π1​,π2​]$\huge 

we get:

$\huge 0.8π1+0.5π2=π10.8\pi_1 + 0.5\pi_2 = \pi_10.8π1​+0.5π2​=π1​$\huge 

This gives:

$\huge 0.5π2=0.2π10.5\pi_2 = 0.2\pi_10.5π2​=0.2π1​$\huge 

so

$\huge π2=0.4π1\pi_2 = 0.4\pi_1π2​=0.4π1​$\huge 

Also,

$\huge π1+π2=1\pi_1 + \pi_2 = 1π1​+π2​=1$\huge 

Substitute:

$\huge π1+0.4π1=1\pi_1 + 0.4\pi_1 = 1π1​+0.4π1​=1$\huge 

$\huge 1.4π1=11.4\pi_1 = 11.4π1​=1$\huge 

$\huge π1=57≈0.714\pi_1 = \frac{5}{7} \approx 0.714π1​=75​≈0.714$\huge 

Then

$\huge π2=1−0.714=0.286\pi_2 = 1 - 0.714 = 0.286π2​=1−0.714=0.286$\huge 

## Final Answer

In the long run:

- Sunny = $\huge 0.714 = 71.4%$\huge 
    
- Rainy = $\huge 0.286 = 28.6%$\huge 
    

---

# Question 4 (Medium-Hard - 3 State Limiting Probability)

## The Problem

Three boys A, B, C are throwing a ball to each other.

- A always throws to B.
    
- B always throws to C.
    
- C is equally likely to throw to A or B.
    

Find:

1. The transition probability matrix.
    
2. The limiting probabilities.
    

## Full Solution

## Step 1: Understand the States

The states are:

- A has the ball
    
- B has the ball
    
- C has the ball
    

## Step 2: Build the Transition Matrix

After one throw:

- From A: goes to B with probability 1.
    
- From B: goes to C with probability 1.
    
- From C: goes to A with probability 0.5 and B with probability 0.5.
    

So,

$\huge P=[0100010.50.50]P = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 0.5 & 0.5 & 0 \end{bmatrix}P=​000.5​100.5​010​​$\huge 

## Step 3: Set Up Limiting Probability Equations

Let

$\huge π=[πA,πB,πC]\pi = [\pi_A, \pi_B, \pi_C]π=[πA​,πB​,πC​]$\huge 

Then

$\huge πP=π\pi P = \piπP=π$\huge 

## Step 4: Solve the System

From the equations:

$\huge 0.5πC=πA0.5\pi_C = \pi_A0.5πC​=πA​$\huge 

$\huge πA+0.5πC=πB\pi_A + 0.5\pi_C = \pi_BπA​+0.5πC​=πB​$\huge 

$\huge πB=πC\pi_B = \pi_CπB​=πC​$\huge 

and

$\huge πA+πB+πC=1\pi_A + \pi_B + \pi_C = 1πA​+πB​+πC​=1$\huge 

From $\huge \pi_B = \pi_C$\huge , and $\huge \pi_A = 0.5\pi_C$\huge , substitute into the sum:

$\huge 0.5πC+πC+πC=10.5\pi_C + \pi_C + \pi_C = 10.5πC​+πC​+πC​=1$\huge 

$\huge 2.5πC=12.5\pi_C = 12.5πC​=1$\huge 

$\huge πC=0.4\pi_C = 0.4πC​=0.4$\huge 

Therefore:

- $\huge \pi_B = 0.4$\huge 
    
- $\huge \pi_A = 0.2$\huge 
    

## Final Answer

In the long run:

- A holds the ball 20% of the time.
    
- B holds the ball 40% of the time.
    
- C holds the ball 40% of the time.
    

---

# Question 5 (Hard - Classification of States)

## The Problem

A Markov chain has transition matrix

$\huge P=[01012012010]P = \begin{bmatrix} 0 & 1 & 0 \\ \frac{1}{2} & 0 & \frac{1}{2} \\ 0 & 1 & 0 \end{bmatrix}P=​021​0​101​021​0​​$\huge 

Classify all the states of this Markov chain:

- Transient or recurrent?
    
- Periodic or aperiodic?
    
- Ergodic?
    

## Full Solution

## Step 1: Read the Transitions

- State 1 goes to State 2 with probability 1.
    
- State 2 goes to State 1 with probability $\huge 1/2$\huge  and State 3 with probability $\huge 1/2$\huge .
    
- State 3 goes to State 2 with probability 1.
    

## Step 2: Check Communication

All states can reach each other, so they form one communicating class.

## Step 3: Recurrent or Transient

Because the chain is finite and all states communicate, all states are recurrent.

## Step 4: Find the Period

For State 1:

- It can return in 2 steps: $\huge 1 \to 2 \to 1$\huge 
    
- It can return in 4 steps as well.
    

So the period is 2.

The same applies to States 2 and 3, so all states have period 2.

## Step 5: Ergodicity

A state is ergodic if it is recurrent and aperiodic. Since the period is 2, none of the states are ergodic.

## Final Answer

- All 3 states are recurrent.
    
- All 3 states have period 2.
    
- No state is ergodic.
    
- All states form one communicating class.
    

---

