---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 11
topic: "Probabilistic Method in Ramsey Theory, Multicolor Ramsey R(3,3,3), Finiteness of Multicolor Ramsey, Extremal Graphs & Mantel Variants"
status: "To Solve"
solution_file: "[[Discrete Structures HW 11 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - probabilistic_method
  - ramsey_theory
  - mantel_theorem
  - extremal_graphs
---

# 📝 Discrete Structures — Homework Assignment 11

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Ramsey Lower Bounds via the Probabilistic Method, Multicolor Ramsey Number $R(3, 3, 3) \le 17$, Finiteness of $R(n_1, \dots, n_t)$, Diamond Graph $A$ in Graphs with $\lfloor n^2/4 \rfloor + 1$ Edges, Extremal Graphs Containing Exactly One Triangle.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 11 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise (including Mantel's Theorem and the standard Ramsey bounds).
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Probabilistic Method in Diagonal Ramsey Theory

Let $n, k, \ell$ be natural numbers. Suppose there exists a probability $p \in [0, 1]$ such that:
$$\binom{n}{k} p^{\binom{k}{2}} + \binom{n}{\ell} (1 - p)^{\binom{\ell}{2}} < 1$$
**Prove** that there exists a 2-coloring of the edges of the complete graph $K_n$ with colors **Red** and **Blue** such that:
- $K_n$ contains **no Red clique** of size $k$ ($K_k$), and
- $K_n$ contains **no Blue clique** of size $\ell$ ($K_\ell$).

> [!tip]- 💡 Hints & Strategy
> - Color each edge of $K_n$ Red with probability $p$ and Blue with probability $1 - p$, independently.
> - For each subset of $k$ vertices, what is the probability it forms a monochromatic Red clique? $p^{\binom{k}{2}}$.
> - For each subset of $\ell$ vertices, what is the probability it forms a monochromatic Blue clique? $(1 - p)^{\binom{\ell}{2}}$.
> - Apply the **Union Bound** over all $\binom{n}{k}$ subsets of size $k$ and all $\binom{n}{\ell}$ subsets of size $\ell$.
> - If the probability of having *at least one* monochromatic forbidden clique is $< 1$, what can you deduce about the complementary event?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Multicolor Ramsey Bound $R(3, 3, 3) \le 17$

**Theorem to Prove:**
In every 3-coloring of the edges of the complete graph $K_{17}$ with colors $\{1, 2, 3\}$, there exists at least one monochromatic triangle ($K_3$).
Consequently, the 3-color Ramsey number satisfies:
$$R(3, 3, 3) \le 17$$

> [!tip]- 💡 Hints & Strategy
> - Fix an arbitrary vertex $x \in V(K_{17})$. It is incident to $17 - 1 = 16$ edges.
> - Apply the **Generalized Pigeonhole Principle** to the 3 colors: $\lceil 16/3 \rceil = 6$.
> - Thus, $x$ has at least 6 edges of the same color, say color 1, leading to a subset of 6 neighbors $Y = \{y_1, \dots, y_6\}$.
> - If any edge between vertices in $Y$ has color 1, what triangle is formed with $x$?
> - If no edge in $Y$ has color 1, what colors do all edges in $Y$ use? What is the value of the 2-color Ramsey number $R(3, 3)$?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Finiteness of Multicolor Ramsey Numbers

For any integer $t \ge 2$ and positive integers $n_1, n_2, \dots, n_t$, define $R(n_1, n_2, \dots, n_t)$ to be the minimum integer $R$ such that every $t$-coloring of the edges of $K_R$ contains a monochromatic $K_{n_i}$ in color $i$ for some $i \in \{1, \dots, t\}$.

**Prove by induction on $t$** that $R(n_1, n_2, \dots, n_t)$ is **finite** for all $t \ge 2$ and all $n_1, \dots, n_t$, by establishing the recursive inequality:
$$R(n_1, n_2, \dots, n_t) \le R\big(R(n_1, n_2), \; n_3, \; \dots, \; n_t\big)$$

> [!tip]- 💡 Hints & Strategy
> - Base case $t = 2$: The classical Ramsey Theorem guarantees that $R(n_1, n_2)$ is finite.
> - Inductive step: Merge colors 1 and 2 into a single "pseudo-color". This transforms a $t$-coloring into a $(t-1)$-coloring!
> - If the $(t-1)$-coloring contains a monochromatic clique in the merged color of size $R(n_1, n_2)$, apply the 2-color Ramsey theorem on that clique.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Forcing the Diamond Subgraph $A$

Let $A$ be the **diamond graph** (two triangles sharing a common edge, i.e., $K_4$ minus one edge):
```
    u ----- w
    |\     /|
    | \   / |
    |  \ /  |
    |   x   |
    |  / \  |
    | /   \ |
    |/     \|
    v ----- y
```
*(Formally, $A = (\{u, v, w, x\}, \{\{u, v\}, \{u, w\}, \{v, w\}, \{u, x\}, \{v, x\}\})$, where $\{u, v\}$ is the shared base edge).*

**Prove** that if a graph $G = (V, E)$ on $n \ge 4$ vertices has:
$$m \ge \left\lfloor \frac{n^2}{4} \right\rfloor + 1$$
edges, then $G$ must contain $A$ as a subgraph.

> [!tip]- 💡 Hints & Strategy
> - By Mantel's Theorem, any graph with $m > \lfloor n^2/4 \rfloor$ edges must contain at least one triangle $T = \{u, v, w\}$.
> - Prove by induction on $n \ge 4$.
> - In the inductive step, if $G$ does not contain $A$, show that the remaining vertices in $V \setminus T$ can each be adjacent to at most one vertex of $T$. Bound the degrees and delete the vertex of minimum degree in $T$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Graphs with Exactly One Triangle

Let $G = (V, E)$ be a graph on $n \ge 3$ vertices that contains **exactly one triangle** ($C_3$).

### Part (a): Construction
Describe a graph on $n$ vertices containing **exactly one triangle** that has:
$$m = \left\lfloor \frac{(n - 1)^2}{4} \right\rfloor + 2$$
edges.

### Part (b): Tightness Proof
**Prove** that every graph on $n$ vertices containing exactly one triangle has at most:
$$m \le \left\lfloor \frac{(n - 1)^2}{4} \right\rfloor + 2$$
edges.

> [!tip]- 💡 Hints & Strategy
> - For (a): Start with the complete bipartite graph $K_{\lfloor (n-1)/2 \rfloor, \lceil (n-1)/2 \rceil}$, which has $\lfloor (n-1)^2/4 \rfloor$ edges and no triangles. Add an $n$-th vertex and connect it to one vertex on each side of the bipartite graph. How many edges does this add, and how many triangles does it create?
> - For (b): Let $T = \{u, v, w\}$ be the unique triangle. Remove $T$ to get $H = G \setminus T$ on $n - 3$ vertices.
>   - Why is $H$ completely triangle-free? What does Mantel's Theorem bound $|E(H)|$ by?
>   - Can any vertex $x \in V(H)$ be adjacent to more than one vertex in $T$? What would happen if $x$ were adjacent to two vertices of $T$?

> [!quote]- ✍️ Solution Workspace
> 
