# Discrete Mathematics — Assignment I

The answers below follow the **exact questions in the uploaded assignment**, with the LaTeX formatted using `$$ ... $$` for display equations and `\\` correctly separating matrix rows. The assignment contains four answer sections: Q1, Q2, Q3(i), and Q3(ii).

---

# Question 1

Given

$$  
A={1,2,3}  
$$

and

$$  
R={(1,1),(2,2),(3,3),(1,2),(2,3),(1,3)}.  
$$

## 1. Properties Analysis

### Reflexive

A relation $R$ on a set $A$ is **reflexive** if

$$  
(x,x)\in R \qquad \forall x\in A.  
$$

Here,

$$  
(1,1),(2,2),(3,3)\in R.  
$$

Therefore,

$$  
\boxed{\text{R is Reflexive}}  
$$

---

### Irreflexive

A relation $R$ is **irreflexive** if

$$  
(x,x)\notin R \qquad \forall x\in A.  
$$

Since

$$  
(1,1)\in R,  
$$

the relation is not irreflexive.

Therefore,

$$  
\boxed{\text{R is Not Irreflexive}}  
$$

---

### Symmetric

A relation is **symmetric** if

$$  
(x,y)\in R\implies(y,x)\in R.  
$$

Here,

$$  
(1,2)\in R,  
$$

but

$$  
(2,1)\notin R.  
$$

Therefore,

$$  
\boxed{\text{R is Not Symmetric}}  
$$

---

### Antisymmetric

A relation is **antisymmetric** if

$$  
(x,y)\in R\land(y,x)\in R\implies x=y.  
$$

The ordered pairs where $x\neq y$ are

$$  
(1,2),\quad(2,3),\quad(1,3).  
$$

Their reversals,

$$  
(2,1),\quad(3,2),\quad(3,1),  
$$

are not present in $R$.

Therefore,

$$  
\boxed{\text{R is Antisymmetric}}  
$$

---

### Transitive

A relation is **transitive** if

$$  
(x,y)\in R\land(y,z)\in R\implies(x,z)\in R.  
$$

Consider

$$  
(1,2)\in R  
$$

and

$$  
(2,3)\in R.  
$$

Then,

$$  
(1,3)\in R,  
$$

which is present in $R$.

All other combinations also satisfy the transitivity condition.

Therefore,

$$  
\boxed{\text{R is Transitive}}  
$$

---

### Equivalence Relation

An equivalence relation must be:

1. Reflexive
    
2. Symmetric
    
3. Transitive
    

Here, $R$ is not symmetric.

Therefore,

$$  
\boxed{\text{R is Not an Equivalence Relation}}  
$$

---

### Partial Order Relation

A partial order relation must be:

1. Reflexive
    
2. Antisymmetric
    
3. Transitive
    

Since $R$ satisfies all three conditions,

$$  
\boxed{\text{R is a Partial Order Relation}}  
$$

Hence,

$$  
\boxed{(A,R)\text{ is a Poset}}  
$$

---

## 2. Digraph

The vertices are

$$  
V={1,2,3}.  
$$

The directed edges are

$$  
1\to1,\qquad  
2\to2,\qquad  
3\to3,  
$$

$$  
1\to2,\qquad  
2\to3,\qquad  
1\to3.  
$$

Ignoring the self-loops, the digraph can be represented as:

```text
        ┌───────────────┐
        ↓               │
      (1) ───────────> (2)
       │                │
       │                │
       └──────────────> (3)
```

There is also a **self-loop at each vertex** $1$, $2$, and $3$.

---

# Question 2

Given

$$  
A={1,2,3,4,5}  
$$

with adjacency matrix

$$  
M_R=  
\begin{bmatrix}  
0 & 1 & 0 & 1 & 0 \  
1 & 0 & 0 & 0 & 0 \  
0 & 1 & 0 & 0 & 1 \  
0 & 0 & 1 & 0 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

Using **Warshall's Algorithm**, the transitive closure $R^*$ is determined using

# $$  
W^{(k)}[i,j]

W^{(k-1)}[i,j]  
\lor  
\left(  
W^{(k-1)}[i,k]\land W^{(k-1)}[k,j]  
\right).  
$$

---

## Step 1: $k=1$

Using vertex $1$ as the intermediate vertex.

Column $1$ has a $1$ at row $2$:

$$  
W^{(0)}[2,1]=1.  
$$

Row $1$ has $1$'s at columns $2$ and $4$:

$$  
W^{(0)}[1,2]=1,  
\qquad  
W^{(0)}[1,4]=1.  
$$

Therefore,

$$  
W^{(1)}[2,2]=1,  
\qquad  
W^{(1)}[2,4]=1.  
$$

Hence,

# $$  
W^{(1)}

\begin{bmatrix}  
0 & 1 & 0 & 1 & 0 \  
1 & 1 & 0 & 1 & 0 \  
0 & 1 & 0 & 0 & 1 \  
0 & 0 & 1 & 0 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

---

## Step 2: $k=2$

Using vertex $2$ as the intermediate vertex.

Column $2$ has $1$'s at rows

$$  
1,;2,;3.  
$$

Row $2$ has $1$'s at columns

$$  
1,;2,;4.  
$$

Therefore, paths through vertex $2$ give

$$  
W^{(2)}[1,1]=1,  
\qquad  
W^{(2)}[1,2]=1,  
\qquad  
W^{(2)}[1,4]=1,  
$$

$$  
W^{(2)}[2,1]=1,  
\qquad  
W^{(2)}[2,2]=1,  
\qquad  
W^{(2)}[2,4]=1,  
$$

and

$$  
W^{(2)}[3,1]=1,  
\qquad  
W^{(2)}[3,2]=1,  
\qquad  
W^{(2)}[3,4]=1.  
$$

Thus,

# $$  
W^{(2)}

\begin{bmatrix}  
1 & 1 & 0 & 1 & 0 \  
1 & 1 & 0 & 1 & 0 \  
1 & 1 & 0 & 1 & 1 \  
0 & 0 & 1 & 0 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

---

## Step 3: $k=3$

Using vertex $3$ as the intermediate vertex.

Column $3$ has a $1$ at row $4$:

$$  
W^{(2)}[4,3]=1.  
$$

Row $3$ has $1$'s at columns

$$  
1,;2,;4,;5.  
$$

Therefore, paths through vertex $3$ give

$$  
W^{(3)}[4,1]=1,  
$$

$$  
W^{(3)}[4,2]=1,  
$$

$$  
W^{(3)}[4,4]=1,  
$$

and

$$  
W^{(3)}[4,5]=1.  
$$

Hence,

# $$  
W^{(3)}

\begin{bmatrix}  
1 & 1 & 0 & 1 & 0 \  
1 & 1 & 0 & 1 & 0 \  
1 & 1 & 0 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

---

## Step 4: $k=4$

Using vertex $4$ as the intermediate vertex.

Column $4$ has $1$'s at rows

$$  
1,;2,;3,;4.  
$$

Row $4$ has $1$'s at columns

$$  
1,;2,;3,;4,;5.  
$$

Therefore, vertices $1$, $2$, $3$, and $4$ can all reach every vertex from $1$ through $5.

Thus,

# $$  
W^{(4)}

\begin{bmatrix}  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

---

## Step 5: $k=5$

Using vertex $5$ as the intermediate vertex.

Vertex $5$ has only a self-loop:

$$  
W^{(4)}[5,5]=1.  
$$

Therefore, no new paths are created.

Hence,

# $$  
W^{(5)}

W^{(4)}.  
$$

Therefore,

# $$  
W^{(5)}

\begin{bmatrix}  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}.  
$$

---

## Final Transitive Closure

Therefore, the transitive closure $R^*$ is represented by

# $$  
\boxed{  
M_{R^*}

\begin{bmatrix}  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
1 & 1 & 1 & 1 & 1 \  
0 & 0 & 0 & 0 & 1  
\end{bmatrix}  
}  
$$

Hence,

# $$  
\boxed{  
R^*

{(i,j)\mid i,j\in{1,2,3,4}}  
\cup  
{(5,5)}  
}  
$$

---

# Question 3(i)

Given

$$  
A={1,2,3,4,6,12}  
$$

and

$$  
aRb\iff a\mid b,  
$$

where $a\mid b$ means "$a$ divides $b$."

## (a) Show that $R$ is a Partial Order Relation

To prove that $R$ is a partial order, we must prove that $R$ is:

1. Reflexive
    
2. Antisymmetric
    
3. Transitive
    

---

### Reflexive

For every $a\in A$,

$$  
a\mid a  
$$

because

$$  
a=a\cdot1.  
$$

Therefore,

$$  
(a,a)\in R  
$$

for every $a\in A$.

Hence,

$$  
\boxed{R\text{ is Reflexive}}  
$$

---

### Antisymmetric

Suppose

$$  
a\mid b  
$$

and

$$  
b\mid a.  
$$

Then there exist positive integers $m,n$ such that

$$  
b=am  
$$

and

$$  
a=bn.  
$$

Substituting,

$$  
a=(am)n=amn.  
$$

Since $a>0$,

$$  
mn=1.  
$$

Therefore,

$$  
m=n=1.  
$$

Hence,

$$  
a=b.  
$$

Therefore,

$$  
\boxed{R\text{ is Antisymmetric}}  
$$

---

### Transitive

Suppose

$$  
a\mid b  
$$

and

$$  
b\mid c.  
$$

Then there exist integers $k_1,k_2$ such that

$$  
b=k_1a  
$$

and

$$  
c=k_2b.  
$$

Substituting,

$$  
c=k_2(k_1a).  
$$

Therefore,

$$  
c=(k_1k_2)a.  
$$

Hence,

$$  
a\mid c.  
$$

Therefore,

$$  
\boxed{R\text{ is Transitive}}  
$$

Since $R$ is reflexive, antisymmetric, and transitive,

$$  
\boxed{R\text{ is a Partial Order Relation}}  
$$

Thus,

$$  
\boxed{(A,R)\text{ is a Poset}}  
$$

---

## (b) Hasse Diagram

The covering relations are

$$  
1\prec2,  
\qquad  
1\prec3,  
$$

$$  
2\prec4,  
\qquad  
2\prec6,  
$$

$$  
3\prec6,  
$$

$$  
4\prec12,  
\qquad  
6\prec12.  
$$

Therefore, the Hasse diagram is:

```text
             12
            /  \
           4    6
           |   / \
           |  /   \
           2       3
            \     /
             \   /
               1
```

Here,

$$  
\boxed{1\text{ is the minimum element}}  
$$

and

$$  
\boxed{12\text{ is the maximum element}}.  
$$

---

# Question 3(ii)

Given the function

$$  
f:\mathbb{R}\setminus{2}  
\to  
\mathbb{R}\setminus{3}  
$$

defined by

$$  
f(x)=\frac{3x-1}{x-2}.  
$$

## (a) Prove that $f$ is Bijective

To prove that $f$ is bijective, we show that it is:

1. Injective
    
2. Surjective
    

---

### 1. Injective

Assume

$$  
f(x_1)=f(x_2)  
$$

for

$$  
x_1,x_2\in\mathbb{R}\setminus{2}.  
$$

Then,

# $$  
\frac{3x_1-1}{x_1-2}

\frac{3x_2-1}{x_2-2}.  
$$

Cross-multiplying,

# $$  
(3x_1-1)(x_2-2)

(3x_2-1)(x_1-2).  
$$

Expanding,

# $$  
3x_1x_2-6x_1-x_2+2

3x_1x_2-6x_2-x_1+2.  
$$

Canceling the common terms,

# $$  
-6x_1-x_2

-6x_2-x_1.  
$$

Therefore,

$$  
5x_2=5x_1.  
$$

Hence,

$$  
x_1=x_2.  
$$

Therefore,

$$  
\boxed{f\text{ is Injective}}  
$$

---

### 2. Surjective

Let

$$  
y\in\mathbb{R}\setminus{3}.  
$$

We need to find an $x\in\mathbb{R}\setminus{2}$ such that

$$  
f(x)=y.  
$$

Starting with

$$  
y=\frac{3x-1}{x-2},  
$$

we get

$$  
y(x-2)=3x-1.  
$$

Expanding,

$$  
yx-2y=3x-1.  
$$

Rearranging,

$$  
yx-3x=2y-1.  
$$

Factoring $x$,

$$  
x(y-3)=2y-1.  
$$

Since

$$  
y\neq3,  
$$

we have

$$  
y-3\neq0.  
$$

Therefore,

$$  
x=\frac{2y-1}{y-3}.  
$$

We must verify that $x\neq2$.

Suppose

$$  
\frac{2y-1}{y-3}=2.  
$$

Then,

$$  
2y-1=2(y-3).  
$$

Therefore,

$$  
2y-1=2y-6.  
$$

This gives

$$  
-1=-6,  
$$

which is a contradiction.

Hence,

$$  
x\neq2.  
$$

Therefore, for every

$$  
y\in\mathbb{R}\setminus{3},  
$$

there exists an

$$  
x\in\mathbb{R}\setminus{2}  
$$

such that

$$  
f(x)=y.  
$$

Thus,

$$  
\boxed{f\text{ is Surjective}}  
$$

Since $f$ is both injective and surjective,

$$  
\boxed{f\text{ is Bijective}}  
$$

---

## (b) Find the Inverse of the Function

Starting with

$$  
y=\frac{3x-1}{x-2},  
$$

we obtain

$$  
x=\frac{2y-1}{y-3}.  
$$

Replacing $y$ by $x$,

$$  
\boxed{  
f^{-1}(x)=\frac{2x-1}{x-3}  
}  
$$

Therefore,

$$  
\boxed{  
f^{-1}:  
\mathbb{R}\setminus{3}  
\to  
\mathbb{R}\setminus{2}  
}  
$$

Hence, the inverse function is

$$  
\boxed{  
f^{-1}(x)=\frac{2x-1}{x-3}  
}  
$$