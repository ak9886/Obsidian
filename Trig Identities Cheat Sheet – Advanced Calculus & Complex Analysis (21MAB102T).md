# Trig Identities Cheat Sheet – Advanced Calculus & Complex Analysis (21MAB102T)

Nov 3, 2026 · @No thank you

Memorise three seeds, then derive everything else in seconds. The unit table shows exactly where each identity earns marks in this paper.

## The three seeds

**1. Compound angle**: the only formulas you truly memorise.

```latex
\begin{aligned}
\sin(A \pm B) &= \sin A\cos B \pm \cos A\sin B \\
\cos(A \pm B) &= \cos A\cos B \mp \sin A\sin B
\end{aligned}
```

Sine **mixes** the functions (sin cos, cos sin) and **keeps** the sign. Cosine pairs **like with like** (cos cos, sin sin) and **flips** the sign.

**2. Pythagoras**

```latex
\sin^2\theta + \cos^2\theta = 1
```

**3. Euler's formula**: carries Units 3, 4 and 5.

```latex
e^{i\theta} = \cos\theta + i\sin\theta \quad\Rightarrow\quad \cos\theta = \frac{e^{i\theta}+e^{-i\theta}}{2}, \qquad \sin\theta = \frac{e^{i\theta}-e^{-i\theta}}{2i}
```

## Derivation tree

&#91;embedded content: derivation tree · 3 seeds, 6 families of identities\]

If you can regrow this tree from the seeds, you never need to memorise the leaves. For the triple angle, cos 3A starts with the cube and sin 3A ends with it.

## Hyperbolic and complex forms

**Osborn's rule:** change sin → sinh and cos → cosh, then flip the sign of every term holding a product of two sinh's (sinh², tanh², sinh A sinh B).

| Trig identity | Hyperbolic version |
| --- | --- |
| cos²x + sin²x = 1 | cosh²x − sinh²x = 1 |
| sin 2x = 2 sin x cos x | sinh 2x = 2 sinh x cosh x |
| cos 2x = 1 − 2sin²x | cosh 2x = 1 + 2sinh²x |
| cos(A + B) = cosA cosB − sinA sinB | cosh(A + B) = coshA coshB + sinhA sinhB |

```latex
\cosh x = \frac{e^{x}+e^{-x}}{2}, \qquad \sinh x = \frac{e^{x}-e^{-x}}{2}
```

**The bridge** (why Osborn works: sinh · sinh picks up i · i = −1):

```latex
\cos(ix) = \cosh x, \quad \sin(ix) = i\sinh x, \quad \cosh(ix) = \cos x, \quad \sinh(ix) = i\sin x
```

Put the bridge into compound angle and you get the Unit 4 results:

```latex
\begin{aligned}
\sin(x+iy) &= \sin x\cosh y + i\cos x\sinh y \\
\cos(x+iy) &= \cos x\cosh y - i\sin x\sinh y
\end{aligned}
```

## Where each identity shows up in the paper

| Unit | Typical question | Identities you need |
| --- | --- | --- |
| 1. Integral calculus | Polar double integrals, cardioid areas | x = r cosθ, y = r sinθ, x² + y² = r²; power reduction for sin²θ, cos²θ; 1 + cosθ = 2cos²(θ/2); Wallis' formula |
| 2. Vector calculus | Green's / Stokes' verification on a circle | x = a cos t, y = a sin t; sin t cos t = ½ sin 2t; power reduction |
| 3. Laplace transform | L{sin2t cos3t}, L{cos²t}, L{sin³t} | Product to sum; power and cube reduction; sinh, cosh as exponentials |
| 4. Analytic functions | Milne-Thomson, w = sin z mapping | sin(x+iy), cos(x+iy); the cos(ix), sin(ix) bridge; cos 0 = 1, sinh 0 = 0 |
| 5. Complex integration | ∫₀^{2π} dθ / (a + b cosθ) on the unit circle | z = e^{iθ}: cosθ, sinθ, cos nθ in terms of z; dθ = dz / (iz) |

## Standard results to keep handy

**Wallis' formula (Unit 1).** Step down by 2 until you reach 1 or 2; multiply by π/2 only when the power is even.

```latex
\int_0^{\pi/2} \sin^n\theta\,d\theta = \int_0^{\pi/2} \cos^n\theta\,d\theta = \frac{(n-1)(n-3)\cdots}{n(n-2)\cdots} \times \begin{cases} \pi/2 & n \text{ even} \\ 1 & n \text{ odd} \end{cases}
```

```latex
\int_0^{\pi/2} \sin^m\theta\cos^n\theta\,d\theta = \frac{[(m-1)(m-3)\cdots]\,[(n-1)(n-3)\cdots]}{(m+n)(m+n-2)\cdots} \times \begin{cases} \pi/2 & m, n \text{ both even} \\ 1 & \text{otherwise} \end{cases}
```

**Laplace transforms (Unit 3).** Sine has **a** on top, cosine has **s** on top; the hyperbolic pair flips + to − (Osborn again).

```latex
L\{\sin at\} = \frac{a}{s^2+a^2}, \quad L\{\cos at\} = \frac{s}{s^2+a^2}, \quad L\{\sinh at\} = \frac{a}{s^2-a^2}, \quad L\{\cosh at\} = \frac{s}{s^2-a^2}
```

Worked examples, identity first, then transform:

```latex
\begin{aligned}
L\{\sin 2t\cos 3t\} &= \tfrac12 L\{\sin 5t - \sin t\} = \tfrac12\left[\frac{5}{s^2+25} - \frac{1}{s^2+1}\right] \\
L\{\sin^3 2t\} &= \tfrac14 L\{3\sin 2t - \sin 6t\} = \tfrac32\left[\frac{1}{s^2+4} - \frac{1}{s^2+36}\right]
\end{aligned}
```

**Unit-circle substitution (Unit 5).** Put z = e^{iθ}, so the integral over 0 to 2π becomes a contour integral round |z| = 1.

```latex
\cos\theta = \frac{z+z^{-1}}{2}, \quad \sin\theta = \frac{z-z^{-1}}{2i}, \quad \cos n\theta = \frac{z^n+z^{-n}}{2}, \quad d\theta = \frac{dz}{iz}
```

## Seven-day routine

Each day, rebuild the derivation tree on a blank page from the three seeds (about 3 minutes), then solve one question of that day's type.

- [ ] Day 1: tree + one polar double integral using sin²θ or cos²θ
- [ ] Day 2: tree + one Laplace transform using product to sum
- [ ] Day 3: tree + one Laplace transform of sin³ or cos³
- [ ] Day 4: tree + hyperbolic table from memory via Osborn's rule
- [ ] Day 5: tree + one Milne-Thomson problem using sin(x+iy) or cos(x+iy)
- [ ] Day 6: tree + one unit-circle contour integral ∫ dθ / (a + b cosθ)
- [ ] Day 7: tree + one Green's theorem verification on a circle
