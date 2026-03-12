---
updated_at: 2026-03-12T08:09:48.210+05:30
edited_seconds: 10
---
## Master’s Theorem Analysis (Step-by-Step)

### Step 1 — Write the Recurrence Relation

The divide-and-conquer duplicate detection algorithm splits the dataset into two halves and processes them recursively before merging results.

[
T(n) = 2T(n/2) + O(n)
]

Where:

* **2T(n/2)** → recursive duplicate detection on two halves
* **O(n)** → comparisons during the merge step

---

### Step 2 — Identify the Parameters

From the recurrence:

[
T(n) = aT(n/b) + f(n)
]

We identify:

* (a = 2) (number of subproblems)
* (b = 2) (input divided into halves)
* (f(n) = n) (work done outside recursion)

---

### Step 3 — Compute (n^{\log_b a})

[
n^{\log_b a} = n^{\log_2 2}
]

[
\log_2 2 = 1
]

[
n^{\log_b a} = n^1 = n
]

---

### Step 4 — Compare (f(n)) with (n^{\log_b a})

[
f(n) = n
]

[
n^{\log_b a} = n
]

Therefore:

[
f(n) = Θ(n^{\log_b a})
]

This corresponds to **Case 2 of the Master Theorem**.

---

### Step 5 — Apply Master Theorem Case 2

Case 2 states:

If

[
f(n) = Θ(n^{\log_b a})
]

then

[
T(n) = Θ(n^{\log_b a} \log n)
]

Substitute values:

[
T(n) = Θ(n \log n)
]

---

### Final Result

[
T(n) = Θ(n \log n)
]

This means the divide-and-conquer duplicate detection algorithm runs in **O(n log n)** time, which is significantly more efficient than the **O(n²)** complexity of naive pairwise image comparisons.

---

**Q1:** Want a **recursion tree diagram that visually proves the Master Theorem result for your poster**?
**Q2:** Want a **short 4-line version of this Master Theorem proof that fits perfectly on a poster**?
**Q3:** Want a **comparison slide showing O(n²) vs O(n log n) with a graph for your presentation**?
