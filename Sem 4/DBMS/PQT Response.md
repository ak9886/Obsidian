---
updated_at: 2026-05-15T20:43:27.340+05:30
edited_seconds: 110
---
# Introduction to Probability and Queueing Theory

This introduction to Probability and Queueing Theory (PQT) covers the core foundations found in Units 1 through 4 of your course. Since you are new to the subject, we will break down each major concept with a step-by-step example.

## Unit 1: Random Variables

A **random variable** is a rule that assigns a number to each outcome of an experiment.

### Problem: Finding a missing probability value

A discrete random variable \(X\) has the following probability mass function (PMF):

| \(X\) | 0 | 1 | 2 | 3 | 4 |
| --- | ---: | ---: | ---: | ---: | ---: |
| \(P(X)\) | \(k\) | \(2k\) | \(5k\) | \(7k\) | \(9k\) |

Find the value of \(k\).

### Step-by-step solution

1. Recall the rule: for any valid probability distribution, the sum of all probabilities must equal 1.
2. Set up the equation:
   \[$$
   k + 2k + 5k + 7k + 9k = 1
   $$\]
3. Solve for \(k\):
   \[$$
   24k = 1
   $$\]
   \[$$
   k = \frac{1}{24}
   $$\]

## Unit 2: Special Distributions

We use specific formulas when experiments follow a known pattern. One common example is the **binomial distribution**, used when there are \(n\) independent trials, each with only two outcomes: success \((p)\) or failure \((q)\).

### Problem: Calculating parameters

The mean of a binomial distribution is 20 and its standard deviation is 4. Find the parameters \(n\) and \(p\).

### Step-by-step solution

1. Identify the formulas:
   \[$$
   \text{Mean} = np = 20
   $$\]
   \[$$
   \text{Variance} = npq
   $$\]
   Since standard deviation \(= \sqrt{npq} = 4\), then:
   \[$$
   npq = 16
   $$\]
2. Find \(q\):
   \[$$
   \frac{npq}{np} = \frac{16}{20} = \frac{4}{5}
   $$\]
   So, \(q = 0.8\).
3. Find \(p\):
   \[$$
   p = 1 - q = 1 - 0.8 = 0.2
   $$\]
4. Find \(n\):
   \[$$
   n \times 0.2 = 20 \Rightarrow n = 100
   $$\]

### Answer

The parameters are \(n = 100\) and \(p = 0.2\).

## Unit 3: Two-Dimensional Random Variables

Sometimes we study two variables, like \(X\) and \(Y\), at once to see if they are related. This relationship is measured by the **correlation coefficient**.

### Problem: Analyzing a joint distribution

Given a table of probabilities for \((X, Y)\), how do we know if \(X\) and \(Y\) are independent?

### Step-by-step logic

1. Calculate the marginal probabilities by summing each row for \(X\) and each column for \(Y\).
2. Test independence using:
   \[$$
   P(X \cap Y) = P(X)\times P(Y)
   $$\]
   for every cell in the table.
3. If even one cell fails this test, the variables are **dependent**.

## Unit 4: Random Processes and Markov Chains

A **Markov chain** is a process that moves between states over time. Its key rule is the Markov property: the next state depends only on the current state, not the past.

### Problem: State transitions

You are given a transition probability matrix \(P\) and an initial state distribution \(P^{(0)}\):

\[$$
P =$$$$
\begin{bmatrix}
0.1 & 0.5 & 0.4 \\
0.6 & 0.2 & 0.2 \\
0.3 & 0.4 & 0.3
\end{bmatrix},
\quad
P^{(0)} = (0.7, 0.2, 0.1)
$$$$\]

Find the probability of being in specific states after one step.

### Step-by-step solution

1. Understand the matrix: the value in row 1, column 2 \((0.5)\) is the probability of moving from State 1 to State 2 in one step.
2. Calculate the next state:
   \[$$$$
   P^{(1)} = P^{(0)} \times P
   $$$$\]
3. Interpret the result: the resulting vector gives the probability of the system being in State 1, 2, or 3 after the first transition.