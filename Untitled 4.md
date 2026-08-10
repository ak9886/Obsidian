# Discrete Mathematics — Assignment I

---

# Question 1

**Given:** $A = \{1,2,3\}$, and
$$
R = \{(1,1),(2,2),(3,3),(1,2),(2,3),(1,3)\}.
$$

### Reflexive

A relation $R$ on a set $A$ is reflexive if
$$
(x,x)\in R \qquad \forall x\in A.
$$

Here $A=\{1,2,3\}$, and we check:
$$
(1,1)\in R,\quad (2,2)\in R,\quad (3,3)\in R.
$$

All three pairs are present.

$$
\boxed{\text{R is Reflexive}}
$$

### Irreflexive

A relation $R$ is irreflexive if
$$
(x,x)\notin R \qquad \forall x\in A.
$$

Since $(1,1),(2,2),(3,3)$ **are** all present in $R$, this condition fails completely.

$$
\boxed{\text{R is NOT Irreflexive}}
$$

### Symmetric

A relation $R$ is symmetric if
$$
(a,b)\in R \implies (b,a)\in R \qquad \forall a,b\in A.
$$

Consider $(1,2)\in R$. For symmetry we would need $(2,1)\in R$, but
$$
(2,1)\notin R.
$$

$$
\boxed{\text{R is NOT Symmetric}}
$$

### Antisymmetric

A relation $R$ is antisymmetric if
$$
(a,b)\in R \ \text{and}\ (b,a)\in R \implies a=b.
$$

The non-diagonal pairs in $R$ are $(1,2),(2,3),(1,3)$. Checking their reverses:
$$
(2,1)\notin R,\quad (3,2)\notin R,\quad (3,1)\notin R.
$$

There is no pair $(a,b)$ with $a\neq b$ such that both $(a,b)$ and $(b,a)$ lie in $R$. Hence the condition holds vacuously.

$$
\boxed{\text{R is Antisymmetric}}
$$

### Transitive

A relation $R$ is transitive if
$$
(a,b)\in R \ \text{and}\ (b,c)\in R \implies (a,c)\in R.
$$

Checking all applicable chains:

| $(a,b)$ | $(b,c)$ | Required $(a,c)$ | Present? |
|---|---|---|---|
| $(1,1)$ | $(1,2)$ | $(1,2)$ | Yes |
| $(1,2)$ | $(2,2)$ | $(1,2)$ | Yes |
| $(1,2)$ | $(2,3)$ | $(1,3)$ | Yes |
| $(2,2)$ | $(2,3)$ | $(2,3)$ | Yes |
| $(2,3)$ | $(3,3)$ | $(2,3)$ | Yes |
| $(1,3)$ | $(3,3)$ | $(1,3)$ | Yes |
| $(1,1)$ | $(1,3)$ | $(1,3)$ | Yes |
| $(1,1)$ | $(1,1)$ | $(1,1)$ | Yes |
| $(2,2)$ | $(2,2)$ | $(2,2)$ | Yes |
| $(3,3)$ | $(3,3)$ | $(3,3)$ | Yes |

Every required pair is present.

$$
\boxed{\text{R is Transitive}}
$$

### Equivalence Relation

A relation is an equivalence relation if it is reflexive, symmetric, and transitive. Since $R$ **fails symmetry**,

$$
\boxed{\text{R is NOT an Equivalence Relation}}
$$

### Partial Order

A relation is a partial order if it is reflexive, antisymmetric, and transitive. All three hold here.

$$
\boxed{\text{R is a Partial Order}}
$$

### Digraph of $R$

Vertices: $1,2,3$.

Self-loops (from reflexivity): at $1$, at $2$, at $3$.

Directed edges: $1\to 2,\ 2\to 3,\ 1\to 3$.

    (1) ──────► (2) ──────► (3)
     ⟲  \                    ⟲
     |    \_________________►|
     |                       |
    loop                   loop
                (2 also has a self-loop)

Explicit description of the digraph:

- Self-loop at vertex $1$
- Self-loop at vertex $2$
- Self-loop at vertex $3$
- Edge $1 \to 2$
- Edge $2 \to 3$
- Edge $1 \to 3$

---

# Question 2

**Given:** $A = \{1,2,3,4,5\}$ with adjacency matrix

$$
W^{(0)} = M_R =
\begin{bmatrix}
0 & 1 & 0 & 1 & 0 \\
1 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 1 \\
0 & 0 & 1 & 0 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

**Warshall's recurrence:**
$$
W^{(k)}[i,j] = W^{(k-1)}[i,j] \lor \left( W^{(k-1)}[i,k] \land W^{(k-1)}[k,j] \right).
$$

### Step $k=1$

Column 1 of $W^{(0)}$: entries $(1,1)=0,(2,1)=1,(3,1)=0,(4,1)=0,(5,1)=0$.
Row 1 of $W^{(0)}$: $0\ 1\ 0\ 1\ 0$.

Only row $2$ has $W[i,1]=1$, so row $2$ is updated as (row 2) OR (row 1):
$$
\text{Row 2}: (1,0,0,0,0) \lor (0,1,0,1,0) = (1,1,0,1,0).
$$

All other rows are unchanged since their entry in column $1$ is $0$.

$$
W^{(1)} =
\begin{bmatrix}
0 & 1 & 0 & 1 & 0 \\
1 & 1 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 & 1 \\
0 & 0 & 1 & 0 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

### Step $k=2$

Column 2 of $W^{(1)}$: $(1,2)=1,(2,2)=1,(3,2)=1,(4,2)=0,(5,2)=0$.
Row 2 of $W^{(1)}$: $1\ 1\ 0\ 1\ 0$.

Rows $1,2,3$ have a $1$ in column $2$, so each is updated as (row) OR (row 2):

$$
\text{Row 1}: (0,1,0,1,0)\lor(1,1,0,1,0) = (1,1,0,1,0)
$$
$$
\text{Row 2}: (1,1,0,1,0)\lor(1,1,0,1,0) = (1,1,0,1,0)
$$
$$
\text{Row 3}: (0,1,0,0,1)\lor(1,1,0,1,0) = (1,1,0,1,1)
$$

Rows $4,5$ unchanged (column $2$ entry is $0$).

$$
W^{(2)} =
\begin{bmatrix}
1 & 1 & 0 & 1 & 0 \\
1 & 1 & 0 & 1 & 0 \\
1 & 1 & 0 & 1 & 1 \\
0 & 0 & 1 & 0 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

### Step $k=3$

Column 3 of $W^{(2)}$: $(1,3)=0,(2,3)=0,(3,3)=0,(4,3)=1,(5,3)=0$.
Row 3 of $W^{(2)}$: $1\ 1\ 0\ 1\ 1$.

Only row $4$ has a $1$ in column $3$:
$$
\text{Row 4}: (0,0,1,0,1)\lor(1,1,0,1,1) = (1,1,1,1,1).
$$

All other rows unchanged.

$$
W^{(3)} =
\begin{bmatrix}
1 & 1 & 0 & 1 & 0 \\
1 & 1 & 0 & 1 & 0 \\
1 & 1 & 0 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

### Step $k=4$

Column 4 of $W^{(3)}$: $(1,4)=1,(2,4)=1,(3,4)=1,(4,4)=1,(5,4)=0$.
Row 4 of $W^{(3)}$: $1\ 1\ 1\ 1\ 1$.

Rows $1,2,3,4$ all have a $1$ in column $4$, so each is updated as (row) OR (row 4):

$$
\text{Row 1}: (1,1,0,1,0)\lor(1,1,1,1,1) = (1,1,1,1,1)
$$
$$
\text{Row 2}: (1,1,0,1,0)\lor(1,1,1,1,1) = (1,1,1,1,1)
$$
$$
\text{Row 3}: (1,1,0,1,1)\lor(1,1,1,1,1) = (1,1,1,1,1)
$$
$$
\text{Row 4}: (1,1,1,1,1)\lor(1,1,1,1,1) = (1,1,1,1,1)
$$

Row $5$ unchanged (column $4$ entry is $0$).

$$
W^{(4)} =
\begin{bmatrix}
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

### Step $k=5$

Column 5 of $W^{(4)}$: $(1,5)=1,(2,5)=1,(3,5)=1,(4,5)=1,(5,5)=1$.
Row 5 of $W^{(4)}$: $0\ 0\ 0\ 0\ 1$.

Every row has a $1$ in column $5$, so every row is OR-ed with row $5$. Since row $5$ only contributes a $1$ in position $5$, and rows $1$–$4$ already have a $1$ there, and row $5$ OR itself is unchanged, **no entry changes**.

$$
W^{(5)} =
\begin{bmatrix}
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

### Final Transitive Closure

$$
R^{*} = W^{(5)} =
\begin{bmatrix}
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
1 & 1 & 1 & 1 & 1 \\
0 & 0 & 0 & 0 & 1
\end{bmatrix}
$$

**Verification by path tracing.** From the original edges $1\to2,\ 1\to4,\ 2\to1,\ 3\to2,\ 3\to5,\ 4\to3,\ 4\to5,\ 5\to5$:

- Vertex $1$: $1\to2\to1$, $1\to4\to3\to2$, $1\to4\to5$ ⟹ reaches $\{1,2,3,4,5\}$.
- Vertex $2$: $2\to1\to4\to3$, $2\to1\to4\to5$ ⟹ reaches $\{1,2,3,4,5\}$.
- Vertex $3$: $3\to2\to1\to4$, $3\to5$ ⟹ reaches $\{1,2,3,4,5\}$.
- Vertex $4$: $4\to3\to2\to1$, $4\to5$ ⟹ reaches $\{1,2,3,4,5\}$.
- Vertex $5$: only $5\to5$, no outgoing edge elsewhere ⟹ reaches only $\{5\}$.

This exactly matches $R^{*}$ above, confirming the result.

$$
\boxed{R^{*}: \text{rows } 1,2,3,4 \text{ connect to all of } \{1,2,3,4,5\};\ \text{row } 5 \text{ connects only to } \{5\}}
$$

---

# Question 3(i)

**Given:** $A = \{1,2,3,4,6,12\}$, with $aRb \iff a \mid b$.

### (a) $R$ is a Partial Order

**Reflexive:** For every $a\in A$, $a \mid a$ (any integer divides itself).
$$
\boxed{R \text{ is Reflexive}}
$$

**Antisymmetric:** If $a\mid b$ and $b\mid a$ for positive integers $a,b$, then $a=b$. This is a standard property of divisibility on positive integers.
$$
\boxed{R \text{ is Antisymmetric}}
$$

**Transitive:** If $a\mid b$ and $b\mid c$, then $b=a k_1$ and $c = b k_2$ for integers $k_1,k_2$, so $c = a k_1 k_2$, giving $a\mid c$.
$$
\boxed{R \text{ is Transitive}}
$$

Since $R$ is reflexive, antisymmetric, and transitive:

$$
\boxed{(A,R) \text{ is a Partial Order (poset)}}
$$

### (b) Hasse Diagram

List all divisibility pairs (excluding equalities) within $A=\{1,2,3,4,6,12\}$:

$$
1\mid 2,\ 1\mid3,\ 1\mid4,\ 1\mid6,\ 1\mid12,\ 2\mid4,\ 2\mid6,\ 2\mid12,\ 3\mid6,\ 3\mid12,\ 4\mid12,\ 6\mid12.
$$

A pair $a \lessdot b$ (covering relation) is kept only if **no** intermediate $c\in A$ satisfies $a\mid c\mid b$ with $c \neq a,b$.

- $1\to2$: nothing between → **covering**
- $1\to3$: nothing between → **covering**
- $1\to4$: $1\mid2\mid4$ exists → not covering
- $1\to6$: $1\mid2\mid6$ exists → not covering
- $1\to12$: $1\mid2\mid12$ exists → not covering
- $2\to4$: nothing between → **covering**
- $2\to6$: nothing between → **covering**
- $2\to12$: $2\mid4\mid12$ exists → not covering
- $3\to6$: nothing between → **covering**
- $3\to12$: $3\mid6\mid12$ exists → not covering
- $4\to12$: nothing between → **covering**
- $6\to12$: nothing between → **covering**

$$
\boxed{\text{Covering relations: } 1\lessdot2,\ 1\lessdot3,\ 2\lessdot4,\ 2\lessdot6,\ 3\lessdot6,\ 4\lessdot12,\ 6\lessdot12}
$$

**Hasse diagram** (levels arranged by divisor chain length):

                      12
                     /  \
                    4    6
                    |   / \
                    2  /   \
                     \/     3
                     2      |
                      \    /
                       \  /
                        1

A clearer level-by-level layout:

    Level 3:            12
                        /  \
    Level 2:           4    6
                       |   / \
    Level 1:           2--/   3
                        \     /
    Level 0:             1

Edges present: $1$–$2$, $1$–$3$, $2$–$4$, $2$–$6$, $3$–$6$, $4$–$12$, $6$–$12$, drawn bottom-to-top with $1$ at the bottom and $12$ at the top.

---

# Question 3(ii)

**Given:** $f:\mathbb{R}\setminus\{2\} \to \mathbb{R}\setminus\{3\}$ defined by
$$
f(x) = \dfrac{3x-1}{x-2}.
$$

## (a) Bijectivity

### Injectivity

Assume
$$
f(x_1) = f(x_2).
$$

Then
$$
\frac{3x_1-1}{x_1-2} = \frac{3x_2-1}{x_2-2}.
$$

Cross-multiplying (valid since $x_1,x_2 \neq 2$):
$$
(3x_1-1)(x_2-2) = (3x_2-1)(x_1-2).
$$

Expanding both sides:
$$
3x_1x_2 - 6x_1 - x_2 + 2 = 3x_1x_2 - 6x_2 - x_1 + 2.
$$

Cancel $3x_1x_2$ and $2$ from both sides:
$$
-6x_1 - x_2 = -6x_2 - x_1.
$$

Rearranging:
$$
-6x_1 + x_1 = -6x_2 + x_2 \implies -5x_1 = -5x_2.
$$

$$
x_1 = x_2.
$$

$$
\boxed{f\text{ is Injective}}
$$

### Surjectivity

Let $y \in \mathbb{R}\setminus\{3\}$ be arbitrary. Set
$$
f(x) = y \implies \frac{3x-1}{x-2} = y.
$$

Solving for $x$:
$$
3x - 1 = y(x-2) = yx - 2y,
$$
$$
3x - yx = -2y + 1,
$$
$$
x(3-y) = 1 - 2y,
$$
$$
x(y-3) = 2y - 1,
$$
$$
x = \frac{2y-1}{y-3}.
$$

This is well defined since $y \neq 3$. We must also confirm $x \neq 2$ (so that $x$ lies in the domain $\mathbb{R}\setminus\{2\}$). Suppose $x=2$:
$$
\frac{2y-1}{y-3} = 2 \implies 2y-1 = 2y-6 \implies -1 = -6,
$$
which is false. Hence $x \neq 2$ always, so $x \in \mathbb{R}\setminus\{2\}$ is a valid preimage for every $y \in \mathbb{R}\setminus\{3\}$.

$$
\boxed{f\text{ is Surjective}}
$$

Since $f$ is both injective and surjective:

$$
\boxed{f\text{ is Bijective}}
$$

## (b) Inverse Function

From the surjectivity derivation:
$$
x = \frac{2y-1}{y-3}.
$$

Renaming $y \to x$ to express the inverse as a function of $x$:

$$
\boxed{f^{-1}(x) = \dfrac{2x-1}{x-3}}
$$

**Domain and codomain of $f^{-1}$:**
$$
f^{-1} : \mathbb{R}\setminus\{3\} \to \mathbb{R}\setminus\{2\},
$$

which is the exact reverse of the domain and codomain of $f$, as expected for an inverse of a bijection.