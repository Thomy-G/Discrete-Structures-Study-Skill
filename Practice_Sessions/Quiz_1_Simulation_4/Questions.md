# Quiz 1 Simulation 4 — Discrete Structures (89-2197)
**Lecturer:** Dr. Arnold Filtser  
**Coverage:** Lectures 1–4, Recitations 1–4, and Homework Assignments 1–4  
**Time Limit:** 90 Minutes  
**Total Points:** 100 Points  

### Structure:
- **Part A (75 Points):** 5 Multiple-Choice Questions (15 points each). Exactly **one** correct answer per question. *(The 20% "I Don't Know" policy does not apply to multiple-choice questions).*
- **Part B (25 Points):** 1 Open Proof Question drawn directly from Homework Assignments 1–4. *(The 20% "I Don't Know" policy applies to the open question or to an entire sub-question).*
- Standard conventions: all graphs are finite, simple, and undirected unless stated otherwise. $\mathbb{N} = \{0, 1, 2, \dots\}$.

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Lexicographical Order on Binary Sequences [Lectures & Recitation 1 / HW 01]
Let $A = \{0, 1\}$ with the standard order $0 < 1$.  
Let $S = \{0, 1\}^\mathbb{N}$ be the set of all infinite binary sequences $s = (s_0, s_1, s_2, \dots)$.  
We define the lexicographical order $\le_{\text{lex}}$ on $S$ as follows:
$$s \le_{\text{lex}} t \iff (s = t) \;\lor\; \Big(\exists i \in \mathbb{N}: s_i < t_i \;\land\; \forall j < i: s_j = t_j\Big)$$

Which of the following statements is **correct**?

1. $(S, \le_{\text{lex}})$ is a well-ordered set because $A$ is finite.
2. $(S, \le_{\text{lex}})$ is a total order with minimum element $(0, 0, 0, \dots)$ and maximum element $(1, 1, 1, \dots)$, but it is **not** a well-ordered set.
3. $(S, \le_{\text{lex}})$ is a partial order but not a total order because infinite sequences cannot be compared in finite steps.
4. $(S, \le_{\text{lex}})$ has no minimum element and no maximum element.
5. $(S, \le_{\text{lex}})$ fails antisymmetry because different sequences can have identical initial prefixes.
6. None of the above answers is correct.

---

### Question 2 (15 Points) — Graph Degree Parity & Components [Lectures & Recitation 2 / HW 02 & HW 03]
Let $G = (V, E)$ be a 3-regular graph with $|V| = 20$ vertices.  
Suppose $G$ is disconnected and has exactly $k$ connected components $C_1, C_2, \dots, C_k$.

Which of the following statements is **guaranteed to be true**?

1. Every connected component $C_i$ must contain an **even** number of vertices, and $k \le 5$.
2. There exists a connected component $C_i$ with an odd number of vertices, provided $k$ is even.
3. $G$ must be bipartite because 3 is an odd degree.
4. $k$ can be equal to 6.
5. Every connected component $C_i$ must have $|V(C_i)| \ge 6$.
6. None of the above answers is correct.

---

### Question 3 (15 Points) — Bipartite Graphs & Double Counting [Lectures & Recitation 3 / HW 03, Q5]
Let $G = (V = A \cup B, E)$ be a bipartite graph with bipartition $(A, B)$.  
Suppose that:
- $|A| = 15$,
- Every vertex in $A$ has degree at least 4 (i.e., $\forall x \in A: \deg_G(x) \ge 4$),
- Every vertex in $B$ has degree at most 5 (i.e., $\Delta(B) = \max_{y \in B} \deg_G(y) \le 5$).

What is the **minimum possible number of vertices** in $B$?

1. $|B| \ge 10$
2. $|B| \ge 12$
3. $|B| \ge 15$
4. $|B| \ge 16$
5. $|B| \ge 20$
6. None of the above answers is correct.

---

### Question 4 (15 Points) — Full Binary Trees & Leaves [Lectures & Recitation 3 / HW 01, Q4(a)]
Recall that a **full binary rooted tree** is a rooted tree where:
- The root vertex has degree 2,
- Every internal vertex (neither root nor leaf) has degree 3,
- Leaves are vertices of degree 1.

Suppose a full binary rooted tree $T$ has a total of $n = 31$ vertices.  
How many leaves $\ell$ does $T$ have, and how many internal vertices (excluding the root)?

1. $\ell = 15$ leaves, and 15 internal vertices.
2. $\ell = 16$ leaves, and 14 internal vertices.
3. $\ell = 16$ leaves, and 15 internal vertices.
4. $\ell = 14$ leaves, and 16 internal vertices.
5. A full binary rooted tree cannot have an odd number of vertices.
6. None of the above answers is correct.

---

### Question 5 (15 Points) — Subsets of $\mathbb{N}$ with Infinite Components [Lectures & Recitation 4 / HW 04, Q2(c)]
Define the set:
$$\mathcal{S} = \{A \subseteq \mathbb{N} \mid |A| = \aleph_0 \;\land\; |\mathbb{N} \setminus A| = \aleph_0\}$$
(the collection of all subsets of the natural numbers that are infinite and whose complement in $\mathbb{N}$ is also infinite).

What is the cardinality of $\mathcal{S}$?

1. $\aleph_0$
2. $\aleph = 2^{\aleph_0}$
3. $2^\aleph$
4. Finite
5. It cannot be determined without the Continuum Hypothesis.
6. None of the above answers is correct.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

Answer **both** of the following two sub-questions:

#### Part 1 (12 Points) — Graph Diameter with Low Maximum Degree [HW 03, Q6 / 2026 Quiz 1, Q2]
Let $G = (V, E)$ be a connected simple graph on $n > 1$ vertices where every vertex $v \in V$ satisfies:
$$\deg(v) < \sqrt{n - 1}$$
**Prove that** the diameter of $G$ is at least 3:
$$\operatorname{diam}(G) \ge 3$$

*(Hint: Assume for contradiction that $\operatorname{diam}(G) \le 2$. Fix an arbitrary vertex $u \in V$, and bound the maximum number of vertices that can lie at distance 1 and distance 2 from $u$).*

---

#### Part 2 (13 Points) — Explicit Bijection Between Open and Closed Intervals [HW 02, Q4(a)]
**Prove that** the open interval $(0, 1)$ and the closed interval $[0, 1]$ have the same cardinality:
$$(0, 1) \sim [0, 1]$$
by constructing an **explicit bijection** $f: [0, 1] \to (0, 1)$.  
**Do NOT use the Cantor-Schröder-Bernstein (CSB) theorem.**

*(Important: Your proof must explicitly define the mapping $f(x)$ for all $x \in [0, 1]$, prove that $\operatorname{Im}(f) \subseteq (0, 1)$, prove that $f$ is injective, and prove that $f$ is surjective).*
