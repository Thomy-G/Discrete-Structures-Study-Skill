# Quiz 1 Simulation 3 — Discrete Structures (89-2197)
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

### Question 1 (15 Points) — Componentwise Partial Order on $\mathbb{R}^n$ [Lectures & Recitation 1 / HW 01]
Define a binary relation $\le$ on $\mathbb{R}^n$ by componentwise comparison:
$$\vec{v} \le \vec{u} \iff \forall i \in \{1, 2, \dots, n\}: v_i \le u_i$$
where $v_i \le u_i$ denotes the standard less-than-or-equal ordering on the real numbers $\mathbb{R}$.

Which of the following statements is **correct**?

1. For all $n \ge 1$, $(\mathbb{R}^n, \le)$ is a total order.
2. For $n = 1$, it is a total order; for every $n \ge 2$, it is a partial order but not a total order.
3. For every $n \ge 2$, it fails transitivity and therefore is not a partial order.
4. For every $n \ge 2$, it fails antisymmetry because distinct vectors can have the same component sum.
5. For all $n \ge 1$, $(\mathbb{R}^n, \le)$ is a well-ordered set.
6. None of the above answers is correct.

---

### Question 2 (15 Points) — Graph Degrees & Triangle-Free Bounds (Mantel) [Lectures & Recitation 2 / HW 01 & HW 02]
Let $G = (V, E)$ be a simple undirected graph on $|V| = 12$ vertices containing **no triangles** ($C_3$ subgraphs).  
What is the **maximum possible number of edges** $|E|$ in $G$, and what is the chromatic number $\chi(G)$ of the graph attaining this maximum?

1. $\max |E| = 36$, and $\chi(G) = 2$.
2. $\max |E| = 33$, and $\chi(G) = 3$.
3. $\max |E| = 66$, and $\chi(G) = 12$.
4. $\max |E| = 36$, and $\chi(G) = 3$.
5. $\max |E| = 30$, and $\chi(G) = 2$.
6. None of the above answers is correct.

---

### Question 3 (15 Points) — 2-Regular Graphs & Bipartition [Lectures & Recitation 3 / HW 03]
Consider the following three assertions regarding simple graphs:
- **(I)** Every 2-regular graph with an even number of vertices is bipartite.
- **(II)** In any graph with $n \ge 3$ vertices and $m \ge n$ edges, there exists at least one cycle.
- **(III)** There exists a connected bipartite graph with $|V| > 4$ containing a vertex of degree $\deg(v) \ge \frac{3}{4}|V|$.

Which of these assertions are **true**?

1. Only (II)
2. Only (I) and (II)
3. Only (II) and (III)
4. (I), (II), and (III) are all true.
5. Only (III)
6. None of the above answers is correct.

---

### Question 4 (15 Points) — Disjoint Geometric Sets in $\mathbb{R}^2$ [Lectures & Recitation 4 / HW 02]
Consider the Euclidean plane $\mathbb{R}^2$.
- Let $\mathcal{D}$ be an infinite collection of mutually disjoint **closed disks** in $\mathbb{R}^2$ (where each disk $B((x, y), r) = \{(x', y') \mid (x - x')^2 + (y - y')^2 \le r^2\}$ with $r > 0$).
- Let $\mathcal{C}$ be an infinite collection of mutually disjoint **circles** in $\mathbb{R}^2$ (where each circle $C((x, y), r) = \{(x', y') \mid (x - x')^2 + (y - y')^2 = r^2\}$ with $r > 0$).

Which of the following statements is **correct**?

1. $\mathcal{D}$ can be uncountable ($|\mathcal{D}| = \aleph$), and $\mathcal{C}$ can be uncountable ($|\mathcal{C}| = \aleph$).
2. $\mathcal{D}$ must be countable ($|\mathcal{D}| \le \aleph_0$), and $\mathcal{C}$ must be countable ($|\mathcal{C}| \le \aleph_0$).
3. $\mathcal{D}$ must be countable ($|\mathcal{D}| \le \aleph_0$), but $\mathcal{C}$ can be uncountable with cardinality of the continuum ($|\mathcal{C}| = \aleph$).
4. $\mathcal{D}$ can be uncountable ($|\mathcal{D}| = \aleph$), but $\mathcal{C}$ must be countable ($|\mathcal{C}| \le \aleph_0$).
5. Both $\mathcal{D}$ and $\mathcal{C}$ must be finite.
6. None of the above answers is correct.

---

### Question 5 (15 Points) — Cardinal Arithmetic under CH [Lectures & Recitation 4 / HW 04]
Let $X$ be a set with cardinality of the continuum: $|X| = \aleph = 2^{\aleph_0}$.  
Assume the **Continuum Hypothesis (CH)**: $2^{\aleph_0} = \aleph_1$.  
Consider the two sets of functions:
- $F_1 = \mathbb{N}^X = \{f \mid f: X \to \mathbb{N}\}$
- $F_2 = X^\mathbb{N} = \{g \mid g: \mathbb{N} \to X\}$

What are the cardinalities of $F_1$ and $F_2$?

1. $|F_1| = \aleph$ and $|F_2| = \aleph$
2. $|F_1| = 2^\aleph$ and $|F_2| = \aleph$
3. $|F_1| = 2^\aleph$ and $|F_2| = 2^\aleph$
4. $|F_1| = \aleph_0$ and $|F_2| = \aleph$
5. $|F_1| = \aleph$ and $|F_2| = 2^\aleph$
6. None of the above answers is correct.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

Answer **both** of the following two sub-questions:

#### Part 1 (12 Points) — Characterization of Trees by Unique Paths [Homework 1, Question 3]
Let $G = (V, E)$ be a simple undirected graph on $|V| = n$ vertices.  
**Prove that** $G$ has $n-1$ edges and contains no cycles if and only if there exists a unique simple path between every pair of vertices in $G$:
$$\Big(|E| = n - 1 \;\land\; G \text{ is acyclic}\Big) \iff \Big(\forall u, v \in V, \; \exists! \text{ simple path between } u \text{ and } v\Big)$$

*(Make sure to prove both directions $\implies$ and $\impliedby$, explicitly addressing existence and uniqueness of the paths).*

---

#### Part 2 (13 Points) — Explicit Bijection between Power Set and Characteristic Functions [Homework 2, Question 4(c)]
Let $A$ be an arbitrary set. Let $\{0, 1\}^A$ denote the set of all functions from $A$ to $\{0, 1\}$.  
**Prove without using the Cantor-Schröder-Bernstein (CSB) theorem** that:
$$\mathcal{P}(A) \sim \{0, 1\}^A$$

*(Important: Your proof must construct an explicit function $\Phi: \mathcal{P}(A) \to \{0, 1\}^A$, prove that $\Phi$ is well-defined, prove that $\Phi$ is injective, and prove that $\Phi$ is surjective).*
