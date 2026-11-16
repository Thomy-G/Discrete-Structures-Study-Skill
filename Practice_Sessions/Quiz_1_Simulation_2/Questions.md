# Quiz 1 Simulation 2 — Discrete Structures (89-2197)
**Lecturer:** Dr. Arnold Filtser  
**Coverage:** Lectures 1–4, Recitations 1–4, and Homework Assignments 1–4  
**Time Limit:** 90 Minutes  
**Total Points:** 100 Points  

### Structure:
- **Part A (75 Points):** 5 Multiple-Choice Questions (15 points each). Exactly **one** correct answer per question. *(The 20% "I Don't Know" policy does not apply to multiple-choice questions).*
- **Part B (25 Points):** 1 Open Proof Question based directly on Homework Assignments 1–4. *(The 20% "I Don't Know" policy applies to the open question or to an entire sub-question).*
- Standard conventions: all graphs are finite, simple, and undirected unless stated otherwise. $\mathbb{N} = \{0, 1, 2, \dots\}$.

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Posets & Equivalence Relations [Lectures & Recitation 1 / HW 01]
Let $X = \{1, 2, 3, \dots, 8\}$. Let $\mathcal{E}$ be the set of all equivalence relations on $X$.  
We define a binary relation $\preceq$ on $\mathcal{E}$ as follows:
$$R_1 \preceq R_2 \iff (|X/R_1| < |X/R_2|) \;\lor\; (R_1 = R_2)$$
where $|X/R_i|$ denotes the number of distinct equivalence classes induced by $R_i$ on $X$.

Which of the following statements is **correct**?

1. $(\mathcal{E}, \preceq)$ is a total order, and the maximum element is the identity relation $R_{\text{id}} = \{(x, x) \mid x \in X\}$.
2. $(\mathcal{E}, \preceq)$ is a partial order but not a total order; it has a unique minimum element and a unique maximum element.
3. $(\mathcal{E}, \preceq)$ is a partial order but not a total order; it has multiple minimal elements and multiple maximal elements.
4. $(\mathcal{E}, \preceq)$ is an equivalence relation on $\mathcal{E}$, and its quotient set has size 8.
5. $(\mathcal{E}, \preceq)$ is not a partial order because antisymmetry fails.
6. None of the above answers is correct.

---

### Question 2 (15 Points) — Graph Degrees & Complements [Lectures & Recitation 2 / HW 02]
Let $G = (V, E)$ be a simple graph on $n = 9$ vertices.  
Suppose that the degree of every vertex $v \in V$ satisfies:
$$2 \le \deg_G(v) \le 4$$
Let $\overline{G}$ be the complement graph of $G$.

Which of the following statements is **guaranteed to be true**?

1. $G$ is disconnected, and $\operatorname{diam}(\overline{G}) = 2$.
2. $\overline{G}$ is connected, and $\operatorname{diam}(\overline{G}) \le 2$.
3. $\overline{G}$ must contain a vertex of degree 3.
4. $G$ cannot contain any cycle of length 3 ($C_3$).
5. $\overline{G}$ is bipartite.
6. None of the above answers is correct.

---

### Question 3 (15 Points) — Forests & Trees [Lectures & Recitation 3 / HW 02 & HW 03]
Let $F = (V, E)$ be a forest (an acyclic undirected graph) with $|V| = 20$ vertices and $|E| = 14$ edges.  
Let $k$ be the number of connected components of $F$, and let $\ell$ be the total number of leaves (vertices of degree 1) in $F$.

Which of the following statements is **correct**?

1. $k = 6$, and $\ell$ can be any integer such that $0 \le \ell \le 14$.
2. $k = 5$, and $F$ must contain at least 6 leaves.
3. $k = 6$, and if $F$ has no isolated vertices (no vertices of degree 0), then $\ell \ge 12$.
4. $k = 7$, and $F$ must contain a component that is a tree with at least 3 leaves.
5. $k = 6$, and every connected component of $F$ must have at least 2 leaves.
6. None of the above answers is correct.

---

### Question 4 (15 Points) — Cardinality & Set Operations [Lectures & Recitation 4 / HW 02 & HW 04]
Let $A, B, C, D$ be non-empty sets such that $|A| = |C| = \aleph_0$ and $|B| = |D| = \aleph$.  
Consider the following three assertions:
- **(I)** $|A \times B| = |C \times D|$
- **(II)** $|B \setminus A| = |D \setminus C|$
- **(III)** $|A \cup B| = |C \cup D|$

Which of these assertions are **always true**?

1. Only (I)
2. Only (I) and (III)
3. Only (II) and (III)
4. (I), (II), and (III) are all always true.
5. None of them is always true.
6. None of the above answers is correct.

---

### Question 5 (15 Points) — Cardinality Arithmetic & Function Spaces [Lectures & Recitation 4 / HW 04]
Let $X$ be a set with cardinality of the continuum: $|X| = 2^{\aleph_0} = \aleph$.  
Define the set of functions:
$$\mathcal{H} = \{f: X \to \mathbb{N} \mid |\operatorname{Im}(f)| < \infty\}$$
(the set of all functions from $X$ to $\mathbb{N}$ that have a **finite image**).

What is the cardinality of $\mathcal{H}$?

1. $\aleph_0$
2. $\aleph = 2^{\aleph_0}$
3. $2^\aleph$
4. $|\mathcal{P}_{\text{fin}}(X)| = \aleph$
5. It depends on whether the Continuum Hypothesis (CH) is assumed.
6. None of the above answers is correct.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

Answer **both** of the following two sub-questions:

#### Part 1 (12 Points) — Tree Leaves & Maximum Degree [Homework 1, Question 4(b) / Homework 3, Question 2]
Let $T = (V, E)$ be a tree with maximum vertex degree:
$$\Delta(T) = k \ge 2$$
**Prove formally** that $T$ contains at least $k$ leaves (vertices of degree 1).

*(Hint: Consider rooting the tree at a vertex $r$ with $\deg(r) = k$, or prune the vertex and analyze the connected components).*

---

#### Part 2 (13 Points) — Cantor's Diagonalization Technique [Homework 4, Question 2(a)]
Let $S \subset (0, 1)$ be the set of all real numbers in the open interval $(0, 1)$ whose standard decimal expansion contains **no occurrence of the digit 7**:
$$S = \left\{ x \in (0, 1) \;\middle|\; x = 0.d_1 d_2 d_3 \dots, \quad \forall i \ge 1: d_i \in \{0, 1, 2, 3, 4, 5, 6, 8, 9\} \right\}$$
*(To ensure unique decimal expansions, exclude expansions that end in an infinite sequence of trailing 9s).*

**Prove using Cantor's Diagonal Argument** that $S$ is **uncountable**.

*(Important: Your proof must explicitly assume $S$ is countable, construct a diagonal number $y$, prove that $y \in (0, 1)$, prove that $y$ has no digit 7 and does not end in trailing 9s, and prove that $y$ differs from every number in your list).*
