---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 4
topic: "Cardinality Arithmetic under CH, Cantor's Diagonalization, Geometric Polygons and Hourglasses"
problem_file: "[[Discrete Structures HW 04]]"
tags:
  - solution
  - discrete_structures
  - cardinality
  - continuum_hypothesis
  - cantor_diagonalization
  - geometry_cardinality
---

# 🛡️ Discrete Structures — Homework Assignment 4 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים) — Semester A
> - **Unsolved Worksheet:** [[Discrete Structures HW 04|View Unsolved Assignment]]
> - **Topics Covered:** Cardinal Arithmetic under CH, Cantor's Diagonalization (Ternary sequences, Function spaces, Unbounded subsets, Rationally vanishing functions), Density of $\mathbb{Q}^2$ in Geometric Polygons, Planar Disjoint Hourglass Countability.

---

## 📌 Solution 1: Cardinality Arithmetic under CH

Let $X$ be a set with $|X| = \aleph = 2^{\aleph_0}$, and assume the Continuum Hypothesis (CH). We compute the exact cardinality of each set:

### Part (a): Cardinality of $\mathbb{N} \times X$
- By cardinal multiplication:
  $$|\mathbb{N} \times X| = |\mathbb{N}| \cdot |X| = \aleph_0 \cdot \aleph$$
- By the absorption law for infinite cardinals:
  $$\aleph_0 \cdot \aleph = \max(\aleph_0, \aleph) = \aleph$$
- Alternatively, via sandwiching:
  $$\aleph \le |\mathbb{N} \times X| \le |\mathbb{R} \times \mathbb{R}| = \aleph \cdot \aleph = \aleph$$
  Hence, $|\mathbb{N} \times X| = \aleph$. $\blacksquare$

### Part (b): Cardinality of $\mathbb{N}^X$
- By cardinal exponentiation:
  $$|\mathbb{N}^X| = |\mathbb{N}|^{|X|} = \aleph_0^\aleph$$
- Since $2 \le \aleph_0 \le 2^{\aleph_0} = \aleph$:
  $$2^\aleph \le \aleph_0^\aleph \le (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
- By Cantor-Schröder-Bernstein (CSB):
  $$|\mathbb{N}^X| = 2^\aleph$$
  $\blacksquare$

### Part (c): Cardinality of $X^\mathbb{N}$
- By cardinal exponentiation:
  $$|X^\mathbb{N}| = |X|^{|\mathbb{N}|} = \aleph^{\aleph_0} = (2^{\aleph_0})^{\aleph_0} = 2^{\aleph_0 \cdot \aleph_0}$$
- Since $\aleph_0 \cdot \aleph_0 = \aleph_0$:
  $$|X^\mathbb{N}| = 2^{\aleph_0} = \aleph$$
  $\blacksquare$

### Part (d): Cardinality of $\mathcal{P}(\mathbb{N})^X$
- Since $|\mathcal{P}(\mathbb{N})| = 2^{\aleph_0} = \aleph$:
  $$|\mathcal{P}(\mathbb{N})^X| = (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
  $\blacksquare$

### Part (e): Cardinality of $X^{\mathcal{P}(\mathbb{N})}$
- Using $|\mathcal{P}(\mathbb{N})| = 2^{\aleph_0} = \aleph$:
  $$|X^{\mathcal{P}(\mathbb{N})}| = \aleph^\aleph$$
- Sandwiched via $2 \le \aleph \le 2^\aleph$:
  $$2^\aleph \le \aleph^\aleph \le (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
  Therefore, $|X^{\mathcal{P}(\mathbb{N})}| = 2^\aleph$. $\blacksquare$

---

## 📌 Solution 2: Cantor's Diagonalization Method

### Part (a): Ternary Sequences Without Consecutive Identical Digits
Let $X \subset \{0, 1, 2\}^\mathbb{N}$ be the set of infinite ternary sequences where no digit repeats consecutively.

#### Proof via Diagonalization:
1. Assume for contradiction that $X$ is countable. Then there exists a surjective mapping $F: \mathbb{N} \to X$, meaning all sequences in $X$ can be enumerated:
   $$X = \{F(1), F(2), F(3), \dots, F(n), \dots\}$$
   where $F(n) = (F(n)_1, F(n)_2, F(n)_3, \dots) \in X$.
2. We construct a sequence $a = (a_1, a_2, a_3, \dots)$ recursively to ensure:
   - $a \in X$ (no consecutive digits repeat: $a_n \ne a_{n-1}$ for all $n \ge 2$).
   - $a \ne F(n)$ for all $n \in \mathbb{N}$ (by ensuring $a_n \ne F(n)_n$).
3. **Recursive Construction of $a$:**
   - **Base Step ($n = 1$):**
     $$a_1 = \begin{cases} 0 & \text{if } F(1)_1 \ne 0 \\ 1 & \text{if } F(1)_1 = 0 \end{cases}$$
     Clearly $a_1 \in \{0, 1, 2\}$ and $a_1 \ne F(1)_1$.
   - **Inductive Step ($n > 1$):**
     To choose $a_n$, we must forbid at most two values from $\{0, 1, 2\}$:
     1. $a_{n-1}$ (to prevent consecutive repeating digits in $a$).
     2. $F(n)_n$ (to differ from the $n$-th sequence along the diagonal).
     
     Since $|\{0, 1, 2\}| = 3$ and $|\{a_{n-1}, F(n)_n\}| \le 2$:
     $$\{0, 1, 2\} \setminus \{a_{n-1}, F(n)_n\} \ne \emptyset$$
     We define $a_n = \min\big(\{0, 1, 2\} \setminus \{a_{n-1}, F(n)_n\}\big)$.
4. **Verification:**
   - By construction, $a_n \ne a_{n-1}$ for all $n \ge 2$, so $a \in X$.
   - For every $n \in \mathbb{N}$, $a_n \ne F(n)_n$, so the sequence $a$ differs from $F(n)$ at the $n$-th coordinate.
   - Hence $a \ne F(n)$ for every $n \in \mathbb{N}$, so $a$ has no pre-image under $F$, contradicting surjectivity!
5. Therefore, $X$ is **uncountable**. $\blacksquare$

---

### Part (b): Functions from $\mathbb{R}$ to $(0, 1) \cap \mathbb{Q}$
Let $\mathcal{F} = \{f \in \mathbb{R}^\mathbb{R} \mid f: \mathbb{R} \to (0, 1) \cap \mathbb{Q}\}$.

#### Proof via Diagonalization:
1. Assume for contradiction that $\mathcal{F}$ is countable. Then there exists an enumeration:
   $$\mathcal{F} = \{f_1, f_2, f_3, \dots, f_n, \dots\}$$
2. We construct a diagonal function $g: \mathbb{R} \to (0, 1) \cap \mathbb{Q}$ that differs from each $f_n$ on the input $n \in \mathbb{N}$:
   $$g(x) = \begin{cases}
   \frac{1}{2} & \text{if } x \in \mathbb{R} \setminus \mathbb{N} \\[4pt]
   \frac{1}{3} & \text{if } x = n \in \mathbb{N} \text{ and } f_n(n) \ne \frac{1}{3} \\[4pt]
   \frac{1}{4} & \text{if } x = n \in \mathbb{N} \text{ and } f_n(n) = \frac{1}{3}
   \end{cases}$$
3. **Verification:**
   - For every $x \in \mathbb{R}$, $g(x) \in \{\frac{1}{2}, \frac{1}{3}, \frac{1}{4}\} \subset (0, 1) \cap \mathbb{Q}$, so $g \in \mathcal{F}$.
   - For every $n \in \mathbb{N}$:
     - If $f_n(n) \ne \frac{1}{3}$, then $g(n) = \frac{1}{3} \ne f_n(n)$.
     - If $f_n(n) = \frac{1}{3}$, then $g(n) = \frac{1}{4} \ne f_n(n)$.
     In both cases, $g(n) \ne f_n(n)$, meaning $g \ne f_n$ for all $n \in \mathbb{N}$.
4. Thus $g \in \mathcal{F}$ was omitted from the list, contradicting countability.
5. Therefore, $\mathcal{F}$ is **uncountable**. $\blacksquare$

---

### Part (c): Unbounded Subsets of $\mathbb{N}$
Let $\mathcal{U} = \{A \subseteq \mathbb{N} \mid A \text{ is unbounded}\}$.

#### Proof via Diagonalization:
1. Assume for contradiction that $\mathcal{U}$ is countable. Then there exists an enumeration:
   $$\mathcal{U} = \{S_1, S_2, S_3, \dots, S_n, \dots\}$$
2. We construct a subset $A \subseteq \mathbb{N}$ designed to be both unbounded and distinct from each $S_n$:
   - Include all even natural numbers: $2\mathbb{N} \subseteq A$.
   - On the odd natural numbers, diagonalize against $S_n$:
     $$A = 2\mathbb{N} \cup \big\{ 2n - 1 \mid n \in \mathbb{N}, \; (2n - 1) \notin S_n \big\}$$
3. **Verification:**
   - Since $2\mathbb{N} \subseteq A$, $A$ contains arbitrarily large even integers, so $A$ is **unbounded** ($A \in \mathcal{U}$).
   - For every $n \in \mathbb{N}$, consider the odd element $2n - 1$:
     - If $2n - 1 \notin S_n$, then by definition $2n - 1 \in A$.
     - If $2n - 1 \in S_n$, then by definition $2n - 1 \notin A$.
     Therefore, $A$ and $S_n$ disagree on the membership of $2n - 1$, so $A \ne S_n$ for all $n \in \mathbb{N}$.
4. Hence $A \in \mathcal{U}$ was not in the enumeration, a contradiction.
5. Thus, $\mathcal{U}$ is **uncountable**. $\blacksquare$

---

### Part (d): Functions Vanishing on All Rationals
Let $\mathcal{F} = \{f \in \mathbb{R}^\mathbb{R} \mid \forall q \in \mathbb{Q}: f(q) = 0\}$.

#### Proof via Diagonalization:
1. Assume for contradiction that $\mathcal{F}$ is countable, enumerated as:
   $$\mathcal{F} = \{g_1, g_2, g_3, \dots, g_n, \dots\}$$
2. Pick an irrational number $\pi$. Note that $n\pi \notin \mathbb{Q}$ for all $n \in \mathbb{N}^+$, and the numbers $\{n\pi\}_{n=1}^\infty$ are pairwise distinct irrationals.
3. Define the function $f: \mathbb{R} \to \mathbb{R}$ by:
   $$f(x) = \begin{cases}
   1 & \text{if } x = n\pi \text{ for some } n \in \mathbb{N}^+ \text{ and } g_n(n\pi) \ne 1 \\[4pt]
   0 & \text{otherwise}
   \end{cases}$$
4. **Verification:**
   - For every $q \in \mathbb{Q}$, since $q \ne n\pi$ for all $n$, $f(q) = 0$. Thus $f \in \mathcal{F}$.
   - For every $n \in \mathbb{N}^+$, evaluating at $x = n\pi$:
     - If $g_n(n\pi) \ne 1$, then $f(n\pi) = 1 \ne g_n(n\pi)$.
     - If $g_n(n\pi) = 1$, then $f(n\pi) = 0 \ne g_n(n\pi)$.
     In either case, $f(n\pi) \ne g_n(n\pi)$, so $f \ne g_n$ for every $n \in \mathbb{N}^+$.
5. Thus $f \in \mathcal{F}$ has no index in the enumeration, a contradiction.
6. Therefore, $\mathcal{F}$ is **uncountable**. $\blacksquare$

---

## 📌 Solution 3: Polygons in $\mathbb{R}^2$ with Unique $\epsilon$-Area

### Part (a): Proof that $|A|$ is Countable ($|A| \le \aleph_0$)

#### Formal Proof:
1. By the problem statement, for each polygon $a \in A$, there is a unique region:
   $$U_a = a \setminus \bigcup_{a' \in A, a' \ne a} a'$$
   with area $\text{Area}(U_a) \ge \epsilon > 0$.
2. By the given geometric lemma, inside any planar region of positive area, one can inscribe a non-empty open disk $D_a \subseteq U_a$.
3. Inside the disk $D_a$, consider an axis-aligned open square $S_a \subseteq D_a$ of positive width.
4. Let the projection of $S_a$ onto the $x$-axis be the open interval $(x_1, x_2)$, and onto the $y$-axis be $(y_1, y_2)$.
   By the density of $\mathbb{Q}$ in $\mathbb{R}$:
   $$\exists q_x \in \mathbb{Q} \cap (x_1, x_2) \quad \text{and} \quad \exists q_y \in \mathbb{Q} \cap (y_1, y_2)$$
   Therefore, the point $p_a = (q_x, q_y) \in \mathbb{Q}^2$ lies inside $S_a \subseteq U_a$.
5. **Injectivity:**
   Since each $U_a$ is the exclusive region of polygon $a$, the regions $\{U_a\}_{a \in A}$ are pairwise disjoint:
   $$\forall a \ne a' \in A : \quad U_a \cap U_{a'} = \emptyset$$
   Because $p_a \in U_a$, the rational point $p_a$ cannot belong to $U_{a'}$ for any $a' \ne a$.
   Hence, the mapping:
   $$\Phi: A \to \mathbb{Q} \times \mathbb{Q}, \quad \Phi(a) = p_a$$
   is strictly **injective** (חד-חד-ערכית).
6. Since $\mathbb{Q} \times \mathbb{Q}$ is countably infinite ($|\mathbb{Q} \times \mathbb{Q}| = \aleph_0 \cdot \aleph_0 = \aleph_0$), the domain $A$ must be at most countable:
   $$|A| \le |\mathbb{Q} \times \mathbb{Q}| = \aleph_0$$
   $\blacksquare$

---

### Part (b): Existence of $\aleph$ Polygons with Mutually Disjoint Boundaries

**Statement:** True (הוכחה שקיימת קבוצה כזו בעוצמה $\aleph$).

#### Formal Proof:
1. For each positive real number $r \in \mathbb{R}^+ = (0, \infty)$, define the axis-aligned square centered at the origin:
   $$Q_r = \left\{ (x, y) \in \mathbb{R}^2 \;\middle|\; \max(|x|, |y|) = r \right\}$$
   which is the boundary of the square $[-r, r] \times [-r, r]$.
2. **Boundary Disjointness:**
   For any two distinct radii $r_1 \ne r_2$:
   $$Q_{r_1} \cap Q_{r_2} = \emptyset$$
   because for any $(x, y) \in Q_{r_1}$, $\max(|x|, |y|) = r_1 \ne r_2$.
3. **Cardinality:**
   The family of polygons $\mathcal{Q} = \{Q_r \mid r \in \mathbb{R}^+\}$ has an obvious bijection $r \leftrightarrow Q_r$ with the set $\mathbb{R}^+$.
   Since $|\mathbb{R}^+| = \aleph$, we have:
   $$|\mathcal{Q}| = \aleph$$
4. Thus, there exists a family of polygons with mutually disjoint boundaries of continuum cardinality $\aleph$. $\blacksquare$

---

## 📌 Solution 4: Disjoint Hourglasses in the Plane

**Problem:** Let $\mathcal{H}$ be an infinite collection of mutually disjoint hourglasses in $\mathbb{R}^2$. Prove that $\mathcal{H}$ is countable ($|\mathcal{H}| \le \aleph_0$).

#### Formal Proof:
1. Each hourglass $H \in \mathcal{H}$ consists of two non-degenerate isosceles triangles $T_1(H)$ and $T_2(H)$ meeting at an apex $c(H)$, with interiors $\text{int}(T_1(H))$ and $\text{int}(T_2(H))$ having positive area.
2. By the density of $\mathbb{Q}^2$ in $\mathbb{R}^2$ (as in Solution 3), inside each triangle of hourglass $H$, there exists at least one rational point:
   $$q_1(H) \in \text{int}(T_1(H)) \cap \mathbb{Q}^2 \quad \text{and} \quad q_2(H) \in \text{int}(T_2(H)) \cap \mathbb{Q}^2$$
   Define the map $\Psi: \mathcal{H} \to \mathbb{Q}^2 \times \mathbb{Q}^2$ by:
   $$\Psi(H) = \big( q_1(H), \, q_2(H) \big)$$
3. **Injectivity of $\Psi$ (No Two Distinct Hourglasses Share Both Points):**
   Assume for contradiction that two distinct hourglasses $A, B \in \mathcal{H}$ share the same pair of rational points:
   $$\Psi(A) = \Psi(B) = (p_1, p_2)$$
   where $p_1 \in \text{int}(T_1(A)) \cap \text{int}(T_1(B))$ and $p_2 \in \text{int}(T_2(A)) \cap \text{int}(T_2(B))$.
   - Consider the apex (נקודת ההשקה) $c(A)$ of hourglass $A$:
     - **Case 1: $c(A)$ lies inside one of the triangles of $B$** (say $T_1(B)$).
       Since the hourglasses are mutually disjoint (no boundary crossings), the entire hourglass $A$ would have to be contained within $T_1(B)$. But then both triangles $T_1(A)$ and $T_2(A)$ would lie inside $T_1(B)$, which contradicts the fact that $T_2(A)$ contains $p_2 \in \text{int}(T_2(B))$ (since $T_1(B) \cap T_2(B) = \{c(B)\}$).
     - **Case 2: $c(A)$ lies outside both triangles of $B$.**
       By symmetry, for $p_1 \in \text{int}(T_1(B))$ to be inside $T_1(A)$, triangle $T_1(B)$ must be contained in $T_1(A)$. But the apex of $B$ is outside $A$, forcing a boundary intersection between the triangles, contradicting disjointness!
   - Therefore, no two distinct hourglasses can contain the same pair of rational points.
4. Hence, $\Psi: \mathcal{H} \to \mathbb{Q}^2 \times \mathbb{Q}^2$ is strictly **injective**.
5. Since $\mathbb{Q}^2 \times \mathbb{Q}^2 \sim \mathbb{N}^4$ is countably infinite ($|\mathbb{Q}^2 \times \mathbb{Q}^2| = \aleph_0$):
   $$|\mathcal{H}| \le \aleph_0$$
   Thus, the set of pairwise disjoint hourglasses is **countable**. $\blacksquare$
