---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 4
topic: "Cardinality Arithmetic under CH, Cantor's Diagonalization"
problem_file: "[[Discrete Structures HW 04]]"
tags:
  - solution
  - discrete_structures
  - cardinality
  - continuum_hypothesis
  - cantor_diagonalization
---

# 🛡️ Discrete Structures — Homework Assignment 4 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 04|View Unsolved Assignment]]
> - **Topics Covered:** Cardinal Exponentiation and Products under CH, Cantor Diagonalization Constructions, Finite and Infinite Subset Cardinality Decomposition.

---

## 📌 Solution 1: Cardinality Arithmetic under CH

Given $|X| = \aleph = 2^{\aleph_0}$, and assuming the Continuum Hypothesis (CH) where $\aleph_1 = 2^{\aleph_0} = \aleph$:

### Part (a): Cardinality of $\mathbb{N} \times X$
- **Calculation:**
  $$|\mathbb{N} \times X| = |\mathbb{N}| \cdot |X| = \aleph_0 \cdot \aleph$$
- By the absorption law for infinite cardinals, for any infinite cardinals $\kappa, \lambda$:
  $$\kappa \cdot \lambda = \max(\kappa, \lambda)$$
- Since $\aleph_0 < \aleph$:
  $$|\mathbb{N} \times X| = \max(\aleph_0, \aleph) = \aleph$$
- **Alternative Verification:**
  $\aleph = 1 \cdot \aleph \le \aleph_0 \cdot \aleph \le \aleph \cdot \aleph = \aleph^2 = (2^{\aleph_0})^2 = 2^{2\aleph_0} = 2^{\aleph_0} = \aleph$.
  Thus $|\mathbb{N} \times X| = \aleph$. $\blacksquare$

---

### Part (b): Cardinality of $\mathbb{N}^X$
- **Calculation:**
  $$|\mathbb{N}^X| = |\mathbb{N}|^{|X|} = \aleph_0^\aleph$$
- Since $2 \le \aleph_0 \le 2^{\aleph_0} = \aleph$:
  $$2^\aleph \le \aleph_0^\aleph \le (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph}$$
- By cardinal multiplication, $\aleph_0 \cdot \aleph = \aleph$. Thus:
  $$2^\aleph \le \aleph_0^\aleph \le 2^\aleph$$
- By the Sandwich Theorem (or CSB):
  $$|\mathbb{N}^X| = 2^\aleph$$
  $\blacksquare$

---

### Part (c): Cardinality of $X^\mathbb{N}$
- **Calculation:**
  $$|X^\mathbb{N}| = |X|^{|\mathbb{N}|} = \aleph^{\aleph_0}$$
- Substituting $\aleph = 2^{\aleph_0}$:
  $$\aleph^{\aleph_0} = (2^{\aleph_0})^{\aleph_0} = 2^{\aleph_0 \cdot \aleph_0}$$
- Since $\aleph_0 \cdot \aleph_0 = \aleph_0$:
  $$|X^\mathbb{N}| = 2^{\aleph_0} = \aleph$$
  $\blacksquare$

---

### Part (d): Cardinality of $\mathcal{P}(\mathbb{N})^X$
- **Calculation:**
  $$|\mathcal{P}(\mathbb{N})^X| = |\mathcal{P}(\mathbb{N})|^{|X|} = (2^{\aleph_0})^\aleph$$
- Using power properties:
  $$(2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
  Therefore:
  $$|\mathcal{P}(\mathbb{N})^X| = 2^\aleph$$
  $\blacksquare$

---

### Part (e): Cardinality of $X^{\mathcal{P}(\mathbb{N})}$
- **Calculation:**
  $$|X^{\mathcal{P}(\mathbb{N})}| = |X|^{|\mathcal{P}(\mathbb{N})|} = \aleph^{2^{\aleph_0}} = \aleph^\aleph$$
- Since $2 \le \aleph \le 2^\aleph$:
  $$2^\aleph \le \aleph^\aleph \le (2^\aleph)^\aleph = 2^{\aleph \cdot \aleph} = 2^\aleph$$
- Therefore:
  $$|X^{\mathcal{P}(\mathbb{N})}| = 2^\aleph$$
  $\blacksquare$

---

## 📌 Solution 2: Cantor's Diagonalization Method

### Part (a): Real Numbers in $(0, 1)$ Without the Digit 7

**Problem:** Prove by Cantor diagonalization that $S = \{x \in (0, 1) \mid \text{decimal of } x \text{ has no digit } 7\}$ is uncountable.

#### Proof:
1. Clearly $S$ is infinite (e.g. $0.1, 0.11, 0.111, \dots \in S$).
2. Assume for contradiction that $S$ is countably infinite. Then its elements can be listed exhaustively in a sequence:
   $$S = \{x_1, x_2, x_3, \dots, x_n, \dots\}$$
3. Write the unique non-terminating decimal expansion of each number (using digits from $\{0, 1, 2, 3, 4, 5, 6, 8, 9\}$ with no trailing 9s):
   $$x_1 = 0.d_{11} d_{12} d_{13} d_{14} \dots$$
   $$x_2 = 0.d_{21} d_{22} d_{23} d_{24} \dots$$
   $$x_3 = 0.d_{31} d_{32} d_{33} d_{34} \dots$$
   $$\vdots$$
   $$x_n = 0.d_{n1} d_{n2} d_{n3} d_{n4} \dots$$
4. Construct a new number $y = 0.y_1 y_2 y_3 \dots$ digit by digit using the diagonal entries $d_{nn}$:
   $$y_n = \begin{cases}
   1 & \text{if } d_{nn} \ne 1 \\[3pt]
   2 & \text{if } d_{nn} = 1
   \end{cases}$$
5. **Properties of $y$:**
   - Every digit $y_n \in \{1, 2\}$. In particular, $y_n \ne 7$ for all $n$, and $y$ contains no trailing 0s or 9s.
   - Therefore, $y \in (0, 1)$ and $y \in S$.
   - For every $k \in \mathbb{N}$, the $k$-th decimal digit of $y$ is $y_k$, whereas the $k$-th decimal digit of $x_k$ is $d_{kk}$.
   - By construction, $y_k \ne d_{kk}$, so $y \ne x_k$ for every $k \in \mathbb{N}$.
6. This contradicts the assumption that the enumeration $\{x_n\}_{n=1}^\infty$ contained all elements of $S$.
7. Therefore, $S$ must be **uncountable**. $\blacksquare$

---

### Part (b): The Function Space $\mathcal{F} = \mathbb{N}^\mathbb{N}$

**Problem:** Prove by Cantor diagonalization that $\mathbb{N}^\mathbb{N}$ is uncountable.

#### Proof:
1. Assume for contradiction that $\mathcal{F} = \{f \mid f: \mathbb{N} \to \mathbb{N}\}$ is countable.
2. Then there exists an enumeration of all functions in $\mathcal{F}$:
   $$\mathcal{F} = \{f_1, f_2, f_3, \dots, f_n, \dots\}$$
3. Construct a function $g: \mathbb{N} \to \mathbb{N}$ defined by modifying the diagonal value:
   $$g(n) = f_n(n) + 1 \quad \forall n \in \mathbb{N}$$
4. Clearly, $g$ is a well-defined function from $\mathbb{N}$ to $\mathbb{N}$, so $g \in \mathcal{F}$.
5. However, for every index $k \in \mathbb{N}$:
   $$g(k) = f_k(k) + 1 \ne f_k(k)$$
   Since $g$ differs from $f_k$ at input $k$, $g \ne f_k$ for all $k \in \mathbb{N}$.
6. This contradicts the assumption that $\{f_n\}$ was an exhaustive enumeration of $\mathcal{F}$.
7. Thus, $\mathbb{N}^\mathbb{N}$ is **uncountable**. $\blacksquare$

---

### Part (c): Finite vs. Infinite Subsets of $\mathbb{N}$

#### 1. Finite Subsets: $|\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$
- For each integer $k \ge 0$, let $\mathcal{P}_k(\mathbb{N}) = \{S \subseteq \mathbb{N} \mid |S| = k\}$ be the family of subsets of size $k$.
- For each $k$, we can inject $\mathcal{P}_k(\mathbb{N})$ into $\mathbb{N}^k$ by listing the $k$ elements in strictly increasing order:
  $$\{s_1 < s_2 < \dots < s_k\} \mapsto (s_1, s_2, \dots, s_k) \in \mathbb{N}^k$$
- Since $\mathbb{N}^k$ is countably infinite ($|\mathbb{N}^k| = \aleph_0^k = \aleph_0$), each $\mathcal{P}_k(\mathbb{N})$ is at most countable.
- The set of all finite subsets is the countable union of these sets:
  $$\mathcal{P}_{\text{fin}}(\mathbb{N}) = \bigcup_{k=0}^\infty \mathcal{P}_k(\mathbb{N})$$
- A countable union of countable sets is countable. Since $\mathcal{P}_1(\mathbb{N}) = \{\{n\} \mid n \in \mathbb{N}\}$ is infinite, $|\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$. $\blacksquare$

#### 2. Infinite Subsets: $|\mathcal{P}_{\infty}(\mathbb{N})| = \aleph$
- Every subset of $\mathbb{N}$ is either finite or infinite, and these two classes are disjoint:
  $$\mathcal{P}(\mathbb{N}) = \mathcal{P}_{\text{fin}}(\mathbb{N}) \;\dot\cup\; \mathcal{P}_{\infty}(\mathbb{N})$$
- By Cantor's Theorem, $|\mathcal{P}(\mathbb{N})| = 2^{\aleph_0} = \aleph$.
- If $|\mathcal{P}_{\infty}(\mathbb{N})|$ were countable ($< \aleph$), then $\mathcal{P}(\mathbb{N})$ would be the union of two countable sets, which would make $\mathcal{P}(\mathbb{N})$ countable, contradicting Cantor's Theorem!
- By cardinal arithmetic:
  $$\aleph = |\mathcal{P}(\mathbb{N})| = \max\big(|\mathcal{P}_{\text{fin}}(\mathbb{N})|, \; |\mathcal{P}_{\infty}(\mathbb{N})|\big) = \max\big(\aleph_0, \; |\mathcal{P}_{\infty}(\mathbb{N})|\big)$$
  Therefore, $|\mathcal{P}_{\infty}(\mathbb{N})| = \aleph = 2^{\aleph_0}$. $\blacksquare$
