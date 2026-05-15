---
updated_at: 2026-05-15T21:59:01.169+05:30
edited_seconds: 50
---
Here is the properly formatted version of your content, cleaned up with headings, equations, tables, and consistent structure .

# Unit 5: Markov Chains — 5 Questions with Full Solutions

## Before We Start

## The Golden Rule of Markov Chains

“The future depends only on the present, not on the past.”

Think of it like this: if you want to predict tomorrow’s weather, you only need to know today’s weather. It does not matter what the weather was last week.

## Basic Concepts You Need to Know

## What is a State?

A state is simply the current situation of a system.

- Example: Weather can be in state “Sunny” or “Rainy.”
    
- Example: A student can be in state “Studying” or “Not Studying.”
    

## What is a Transition Matrix?

It is a table that shows: “If I am here now, what is the probability I go there next?”

Example:

|Today \ Tomorrow|Sunny|Rainy|
|---|---|---|
|Sunny|0.7|0.3|
|Rainy|0.4|0.6|

Reading this: if it is Sunny today, there is a 70% chance of Sunny tomorrow and a 30% chance of Rainy tomorrow.

## Key Rules

- Every row must add up to 1.0.
    
- All probabilities must be between 0 and 1.
    
- P(n)P^{(n)}P(n) means the matrix after nnn steps, found by multiplying PPP by itself nnn times.
    

---

# Question 1 (Easy - Basic Transition Probability)

## The Problem

A college student named Arjun has the following study habits:

- If he studies one night, there is a 70% chance he studies the next night and a 30% chance he does not.
    
- If he does not study one night, there is a 60% chance he studies the next night and a 40% chance he does not.
    

On Monday night, Arjun studies.

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

P=[0.70.30.60.4]P = \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix}P=[0.70.6​0.30.4​]

Check:

- Row 1: 0.7+0.3=1.00.7 + 0.3 = 1.00.7+0.3=1.0
    
- Row 2: 0.6+0.4=1.00.6 + 0.4 = 1.00.6+0.4=1.0
    

## Step 3: Set Up the Initial State

Arjun studies on Monday, so the initial vector is:

[10]\begin{bmatrix}1 & 0\end{bmatrix}[1​0​]

## Step 4: Find Tuesday’s Probabilities

Multiply the initial vector by PPP:

[10][0.70.30.60.4]=[0.70.3]\begin{bmatrix}1 & 0\end{bmatrix} \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix} = \begin{bmatrix}0.7 & 0.3\end{bmatrix}[1​0​][0.70.6​0.30.4​]=[0.7​0.3​]

So on Tuesday:

- Studies: 0.7
    
- Does not study: 0.3
    

## Step 5: Find Wednesday’s Probabilities

Multiply Tuesday’s vector by PPP again:

[0.70.3][0.70.30.60.4]=[0.670.33]\begin{bmatrix}0.7 & 0.3\end{bmatrix} \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix} = \begin{bmatrix}0.67 & 0.33\end{bmatrix}[0.7​0.3​][0.70.6​0.30.4​]=[0.67​0.33​]

## Final Answers

- Transition matrix:
    

P=[0.70.30.60.4]P = \begin{bmatrix} 0.7 & 0.3 \\ 0.6 & 0.4 \end{bmatrix}P=[0.70.6​0.30.4​]

- Probability Arjun studies on Wednesday = 0.67 = 67%
    
- Probability Arjun does not study on Wednesday = 0.33 = 33%
    

---

# Question 2 (Medium - Finding Specific Path Probability)

## The Problem

A Markov chain has 3 states: 1, 2, 3 with transition matrix

P=[0.10.50.40.60.20.20.30.40.3]P = \begin{bmatrix} 0.1 & 0.5 & 0.4 \\ 0.6 & 0.2 & 0.2 \\ 0.3 & 0.4 & 0.3 \end{bmatrix}P=​0.10.60.3​0.50.20.4​0.40.20.3​​

The initial distribution is

P(0)=(0.7,0.2,0.1)P^{(0)} = (0.7, 0.2, 0.1)P(0)=(0.7,0.2,0.1)

Find:

1. P(X2=3,X1=3,X0=2)P(X_2 = 3, X_1 = 3, X_0 = 2)P(X2​=3,X1​=3,X0​=2)
    
2. P(X3=2,X2=3,X1=3,X0=2)P(X_3 = 2, X_2 = 3, X_1 = 3, X_0 = 2)P(X3​=2,X2​=3,X1​=3,X0​=2)
    

## Full Solution

## Step 1: Understand the Path

The first probability is for the path:

2→3→32 \to 3 \to 32→3→3

## Step 2: Use the Path Formula

P(X2=3,X1=3,X0=2)=P(X0=2)×P23×P33P(X_2=3, X_1=3, X_0=2) = P(X_0=2) \times P_{23} \times P_{33}P(X2​=3,X1​=3,X0​=2)=P(X0​=2)×P23​×P33​

## Step 3: Read Values

From the initial distribution:

- P(X0=2)=0.2P(X_0=2) = 0.2P(X0​=2)=0.2
    

From the matrix:

- P23=0.2P_{23} = 0.2P23​=0.2
    
- P33=0.3P_{33} = 0.3P33​=0.3
    

## Step 4: Calculate Part (i)

0.2×0.2×0.3=0.0120.2 \times 0.2 \times 0.3 = 0.0120.2×0.2×0.3=0.012

So,

P(X2=3,X1=3,X0=2)=0.012P(X_2=3, X_1=3, X_0=2) = 0.012P(X2​=3,X1​=3,X0​=2)=0.012

## Step 5: Calculate Part (ii)

Now the path is:

2→3→3→22 \to 3 \to 3 \to 22→3→3→2

So,

P(X3=2,X2=3,X1=3,X0=2)=P(X0=2)×P23×P33×P32P(X_3=2, X_2=3, X_1=3, X_0=2) = P(X_0=2) \times P_{23} \times P_{33} \times P_{32}P(X3​=2,X2​=3,X1​=3,X0​=2)=P(X0​=2)×P23​×P33​×P32​

From the matrix:

- P32=0.4P_{32} = 0.4P32​=0.4
    

Therefore:

0.2×0.2×0.3×0.4=0.00480.2 \times 0.2 \times 0.3 \times 0.4 = 0.00480.2×0.2×0.3×0.4=0.0048

## Final Answers

- P(X2=3,X1=3,X0=2)=0.012P(X_2=3, X_1=3, X_0=2) = 0.012P(X2​=3,X1​=3,X0​=2)=0.012
    
- P(X3=2,X2=3,X1=3,X0=2)=0.0048P(X_3=2, X_2=3, X_1=3, X_0=2) = 0.0048P(X3​=2,X2​=3,X1​=3,X0​=2)=0.0048
    

---

# Question 3 (Medium - Finding Limiting Probabilities)

## The Problem

A weather system can be in two states:

- State 1: Sunny
    
- State 2: Rainy
    

The transition matrix is

P=[0.80.20.50.5]P = \begin{bmatrix} 0.8 & 0.2 \\ 0.5 & 0.5 \end{bmatrix}P=[0.80.5​0.20.5​]

Find the long-run probabilities of Sunny and Rainy.

## Full Solution

## Step 1: Understand Long-Run Behavior

In the long run, the system settles into a stable pattern. These fixed percentages are called limiting probabilities or steady-state probabilities.

Let

π=[π1,π2]\pi = [\pi_1, \pi_2]π=[π1​,π2​]

where:

- π1\pi_1π1​ = probability of Sunny
    
- π2\pi_2π2​ = probability of Rainy
    

## Step 2: Set Up the Equation

The steady-state condition is:

πP=π\pi P = \piπP=π

## Step 3: Write the Equations

From

[π1,π2][0.80.20.50.5]=[π1,π2][\pi_1, \pi_2] \begin{bmatrix} 0.8 & 0.2 \\ 0.5 & 0.5 \end{bmatrix} = [\pi_1, \pi_2][π1​,π2​][0.80.5​0.20.5​]=[π1​,π2​]

we get:

0.8π1+0.5π2=π10.8\pi_1 + 0.5\pi_2 = \pi_10.8π1​+0.5π2​=π1​

This gives:

0.5π2=0.2π10.5\pi_2 = 0.2\pi_10.5π2​=0.2π1​

so

π2=0.4π1\pi_2 = 0.4\pi_1π2​=0.4π1​

Also,

π1+π2=1\pi_1 + \pi_2 = 1π1​+π2​=1

Substitute:

π1+0.4π1=1\pi_1 + 0.4\pi_1 = 1π1​+0.4π1​=1

1.4π1=11.4\pi_1 = 11.4π1​=1

π1=57≈0.714\pi_1 = \frac{5}{7} \approx 0.714π1​=75​≈0.714

Then

π2=1−0.714=0.286\pi_2 = 1 - 0.714 = 0.286π2​=1−0.714=0.286

## Final Answer

In the long run:

- Sunny = 0.714 = 71.4%
    
- Rainy = 0.286 = 28.6%
    

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

P=[0100010.50.50]P = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 0.5 & 0.5 & 0 \end{bmatrix}P=​000.5​100.5​010​​

## Step 3: Set Up Limiting Probability Equations

Let

π=[πA,πB,πC]\pi = [\pi_A, \pi_B, \pi_C]π=[πA​,πB​,πC​]

Then

πP=π\pi P = \piπP=π

## Step 4: Solve the System

From the equations:

0.5πC=πA0.5\pi_C = \pi_A0.5πC​=πA​

πA+0.5πC=πB\pi_A + 0.5\pi_C = \pi_BπA​+0.5πC​=πB​

πB=πC\pi_B = \pi_CπB​=πC​

and

πA+πB+πC=1\pi_A + \pi_B + \pi_C = 1πA​+πB​+πC​=1

From πB=πC\pi_B = \pi_CπB​=πC​, and πA=0.5πC\pi_A = 0.5\pi_CπA​=0.5πC​, substitute into the sum:

0.5πC+πC+πC=10.5\pi_C + \pi_C + \pi_C = 10.5πC​+πC​+πC​=1

2.5πC=12.5\pi_C = 12.5πC​=1

πC=0.4\pi_C = 0.4πC​=0.4

Therefore:

- πB=0.4\pi_B = 0.4πB​=0.4
    
- πA=0.2\pi_A = 0.2πA​=0.2
    

## Final Answer

In the long run:

- A holds the ball 20% of the time.
    
- B holds the ball 40% of the time.
    
- C holds the ball 40% of the time.
    

---

# Question 5 (Hard - Classification of States)

## The Problem

A Markov chain has transition matrix

P=[01012012010]P = \begin{bmatrix} 0 & 1 & 0 \\ \frac{1}{2} & 0 & \frac{1}{2} \\ 0 & 1 & 0 \end{bmatrix}P=​021​0​101​021​0​​

Classify all the states of this Markov chain:

- Transient or recurrent?
    
- Periodic or aperiodic?
    
- Ergodic?
    

## Full Solution

## Step 1: Read the Transitions

- State 1 goes to State 2 with probability 1.
    
- State 2 goes to State 1 with probability 1/2 and State 3 with probability 1/2.
    
- State 3 goes to State 2 with probability 1.
    

## Step 2: Check Communication

All states can reach each other, so they form one communicating class.

## Step 3: Recurrent or Transient

Because the chain is finite and all states communicate, all states are recurrent.

## Step 4: Find the Period

For State 1:

- It can return in 2 steps: 1→2→11 \to 2 \to 11→2→1
    
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

## Quick Summary of All 5 Questions

|Q|Topic|Key Skill|Difficulty|
|---|---|---|---|
|Q1|Basic Transitions|Multiply vector and matrix|Easy|
|Q2|Path Probability|Multiply along a path|Easy-Medium|
|Q3|2-State Limiting|Solve πP=π\pi P = \piπP=π|Medium|
|Q4|3-State Limiting|Solve 3 equations|Medium-Hard|
|Q5|Classification|Find communication and period|Hard|

## Exam Tips

1. Always check that rows of PPP add to 1.0.
    
2. For path probability, multiply the starting probability by the transition probabilities along the path.
    
3. For limiting probabilities, set up πP=π\pi P = \piπP=π and add the condition that all probabilities sum to 1.
    
4. For period, find the shortest return time and the GCD of all return times.
    
5. Ergodic means recurrent and aperiodic.
    

If you want, I can also convert this into a clean **exam-ready PDF style layout** with smaller formulas and better spacing.