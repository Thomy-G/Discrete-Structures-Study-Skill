---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 4
topic: "Cardinality Arithmetic under CH, Cantor's Diagonalization, Geometric Polygons and Hourglasses"
status: "To Solve"
solution_file: "[[Discrete Structures HW 04 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - cardinality
  - continuum_hypothesis
  - cantor_diagonalization
  - geometry_cardinality
---

# 📝 Discrete Structures — Homework Assignment 4

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים) — Semester A
> - **Topics:** Cardinality Arithmetic with the Continuum Hypothesis (CH), Cantor's Diagonal Argument (Sequences, Function Spaces, Unbounded Subsets), Geometric Polygons with Unique $\epsilon$-Area, Disjoint Hourglasses in the Plane.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 04 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- For Question 1, you may assume the **Continuum Hypothesis (CH)**.

---

## 📌 Question 1: Cardinality Arithmetic under CH

Let $X$ be a set with cardinality of the continuum:
$$X \sim \aleph$$
Assuming the Continuum Hypothesis (CH), calculate the exact cardinality of each of the following sets:

1. **Part (a):** $\mathbb{N} \times X$
2. **Part (b):** $\mathbb{N}^X = \{f \mid f: X \to \mathbb{N}\}$
3. **Part (c):** $X^\mathbb{N} = \{f \mid f: \mathbb{N} \to X\}$
4. **Part (d):** $\mathcal{P}(\mathbb{N})^X$
5. **Part (e):** $X^{\mathcal{P}(\mathbb{N})}$

---

## 📌 Question 2: Cantor's Diagonalization Method

Solve each of the following parts using **Cantor's Diagonal Argument**:

### Part (a): Ternary Sequences Without Consecutive Identical Digits
An infinite ternary sequence is an infinite sequence over $\{0, 1, 2\}$, formally $s \in \{0, 1, 2\}^\mathbb{N}$.
Let $X$ denote the set of all infinite ternary sequences in which no digit appears twice (or more) in a row:
$$X = \left\{ s \in \{0, 1, 2\}^\mathbb{N} \;\middle|\; \forall n \in \mathbb{N}: s(n) \ne s(n+1) \right\}$$
Prove using Cantor's diagonalization that $X$ is **uncountable**.

### Part (b): Functions from $\mathbb{R}$ to $(0, 1) \cap \mathbb{Q}$
Define the set:
$$\mathcal{F} = \left\{ f \in \mathbb{R}^\mathbb{R} \;\middle|\; f: \mathbb{R} \to (0, 1) \cap \mathbb{Q} \right\}$$
which is the set of all functions from the real numbers to the rational numbers in the open interval $(0, 1)$.
Prove using Cantor's diagonalization that $\mathcal{F}$ is **uncountable**.

### Part (c): Unbounded Subsets of $\mathbb{N}$
A subset $A \subseteq \mathbb{N}$ is called **unbounded (אינה חסומה)** if for every $n \in \mathbb{N}$ there exists an element $n' \in A$ such that $n' > n$.
Prove using Cantor's diagonalization that the set of all unbounded subsets of $\mathbb{N}$:
$$\mathcal{U} = \{A \subseteq \mathbb{N} \mid A \text{ is unbounded}\}$$
is **uncountable**.

### Part (d): Functions Vanishing on All Rationals
Define the set:
$$\mathcal{F} = \left\{ f \in \mathbb{R}^\mathbb{R} \;\middle|\; \forall q \in \mathbb{Q}: f(q) = 0 \right\}$$
Prove using Cantor's diagonalization that $\mathcal{F}$ is **uncountable**.

---

## 📌 Question 3: Polygons in $\mathbb{R}^2$ with Unique $\epsilon$-Area

Let $A$ be an infinite set of polygons in $\mathbb{R}^2$.
For each polygon $a' \in A$, suppose that:
$$a' \not\subseteq \bigcup_{a \in A, \, a \ne a'} a$$
such that the area of the unique region $\{a'\} \setminus \bigcup_{a \in A, a \ne a'} a$ is strictly greater than some $\epsilon > 0$ for all $a' \in A$ (meaning every polygon has an exclusive area of size at least $\epsilon$ that belongs solely to it).

1. **Part (a):** Prove or disprove: The set $A$ is countably infinite ($|A| \le \aleph_0$).
2. **Part (b):** Prove or disprove: There exists a set of polygons whose boundaries are mutually pairwise disjoint at every point, of cardinality $\aleph$.

> [!tip] Hint (from worksheet)
> You may use without proof the density of rational numbers in $\mathbb{R}$: every open interval $(a, b)$ contains a rational $c \in \mathbb{Q}$ such that $a < c < b$. Furthermore, you may assume that inside any region of positive area, one can inscribe a circle.

---

## 📌 Question 4: Disjoint Hourglasses in the Plane

Define an **hourglass ("שעון חול")** as a pair of identical isosceles triangles sharing a common apex (קודקוד משותף) and having parallel bases (בסיסים מקבילים).
Let $\mathcal{H}$ be an infinite collection of mutually disjoint hourglasses in the plane $\mathbb{R}^2$ (that is, no two distinct hourglasses intersect, though one hourglass may lie entirely inside the open region between the cones of another, as illustrated in the figure).

Prove that the cardinality of $\mathcal{H}$ is **countable** ($|\mathcal{H}| \le \aleph_0$).
