---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 4
topic: "Cardinality Arithmetic under CH, Cantor's Diagonalization"
status: "To Solve"
solution_file: "[[Discrete Structures HW 04 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - cardinality
  - continuum_hypothesis
  - cantor_diagonalization
---

# 📝 Discrete Structures — Homework Assignment 4

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Cardinality Arithmetic with the Continuum Hypothesis (CH), Power Set Cardinalities, Cantor's Diagonal Argument Applications, Finite vs. Infinite Subsets of $\mathbb{N}$.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 04 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- For Question 1, you may assume the **Continuum Hypothesis (CH)**: $2^{\aleph_0} = \aleph_1 = \aleph$.

---

## 📌 Question 1: Cardinality Arithmetic under CH

Let $X$ be a set with cardinality of the continuum:
$$|X| = \aleph = 2^{\aleph_0}$$
Assuming the Continuum Hypothesis (CH), calculate the exact cardinality of each of the following sets. Provide complete formal justifications for each result:

1. **Part (a):** $\mathbb{N} \times X$
2. **Part (b):** $\mathbb{N}^X = \{f \mid f: X \to \mathbb{N}\}$
3. **Part (c):** $X^\mathbb{N} = \{f \mid f: \mathbb{N} \to X\}$
4. **Part (d):** $\mathcal{P}(\mathbb{N})^X$
5. **Part (e):** $X^{\mathcal{P}(\mathbb{N})}$

> [!tip]- 💡 Hints & Strategy
> - Recall standard cardinal arithmetic laws: $(\kappa^\lambda)^\mu = \kappa^{\lambda \cdot \mu}$, $\kappa \le \lambda \implies \kappa^\mu \le \lambda^\mu$, and for infinite cardinals $\max(\kappa, \lambda) = \kappa \cdot \lambda = \kappa + \lambda$.
> - For (b): Sandwiched between $2^X$ and $(2^{\aleph_0})^X$.
> - For (c): Rewrite $X^\mathbb{N}$ as $(2^{\aleph_0})^{\aleph_0} = 2^{\aleph_0 \cdot \aleph_0}$.
> - For (d) & (e): Note that $|\mathcal{P}(\mathbb{N})| = 2^{\aleph_0} = \aleph$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Cantor's Diagonalization Method

Solve each of the following parts using **Cantor's Diagonal Argument**:

### Part (a): Real Numbers Without Digit 7
Let $S \subset (0, 1)$ be the set of all real numbers in $(0, 1)$ whose decimal expansion contains **no occurrence of the digit 7**:
$$S = \left\{ x \in (0, 1) \;\middle|\; x = 0.d_1 d_2 d_3 \dots, \; \forall i \in \mathbb{N}: d_i \in \{0, 1, 2, 3, 4, 5, 6, 8, 9\} \right\}$$
*(To ensure unique decimal expansions, exclude expansions ending in trailing 9s).*
**Prove using Cantor's diagonalization** that $S$ is **uncountable**.

### Part (b): The Set of Functions $\mathbb{N} \to \mathbb{N}$
Let $\mathcal{F} = \mathbb{N}^\mathbb{N} = \{f \mid f: \mathbb{N} \to \mathbb{N}\}$ be the set of all functions from the natural numbers to the natural numbers.
**Prove using Cantor's diagonalization** that $\mathcal{F}$ is **uncountable**.

### Part (c): Finite vs. Infinite Subsets of $\mathbb{N}$
1. Prove that the set of all **finite subsets** of $\mathbb{N}$, denoted $\mathcal{P}_{\text{fin}}(\mathbb{N}) = \{S \subseteq \mathbb{N} \mid |S| < \infty\}$, is **countably infinite** ($|\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$).
2. Conclude the cardinality of the set of all **infinite subsets** of $\mathbb{N}$:
   $$\mathcal{P}_{\infty}(\mathbb{N}) = \{S \subseteq \mathbb{N} \mid |S| = \infty\}$$

> [!tip]- 💡 Hints & Strategy
> - For (a): Assume $S$ is countable and listed as $x_1, x_2, x_3, \dots$. Construct a diagonal number $y = 0.y_1 y_2 y_3 \dots$ where $y_n \ne 7$ and $y_n \ne$ the $n$-th digit of $x_n$.
> - For (b): If $\mathcal{F} = \{f_1, f_2, \dots\}$, define $g(n) = f_n(n) + 1$.
> - For (c): $\mathcal{P}_{\text{fin}}(\mathbb{N}) = \bigcup_{k=0}^\infty \mathcal{P}_k(\mathbb{N})$. A countable union of finite/countable sets is countable. Then use $\mathcal{P}(\mathbb{N}) = \mathcal{P}_{\text{fin}}(\mathbb{N}) \cup \mathcal{P}_{\infty}(\mathbb{N})$.

> [!quote]- ✍️ Solution Workspace
> 
