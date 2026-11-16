---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 11
topic: "Probabilistic Method in Ramsey Theory, Multicolor Ramsey R(3,3,3), Finiteness of Multicolor Ramsey, Extremal Graphs & Mantel Variants"
problem_file: "[[Discrete Structures HW 11]]"
tags:
  - solution
  - discrete_structures
  - probabilistic_method
  - ramsey_theory
  - mantel_theorem
  - extremal_graphs
---

# 🛡️ Discrete Structures — Homework Assignment 11 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 11|View Unsolved Assignment]]
> - **Topics Covered:** Erdős Probabilistic Method in Off-Diagonal Ramsey Theory, Strict Pigeonhole Proof for $R(3,3,3) \le 17$, Color-Merging Reduction for Multicolor Ramsey Finiteness, Diamond Subgraph Induction, Extremal Triangle Counting via Mantel Reduction.

---

## 📌 Solution 1: Probabilistic Method in Diagonal Ramsey Theory

**Problem:** Prove that if $\exists p \in [0, 1]$ such that $\binom{n}{k} p^{\binom{k}{2}} + \binom{n}{\ell} (1 - p)^{\binom{\ell}{2}} < 1$, then there exists a 2-coloring of $E(K_n)$ with no red $K_k$ and no blue $K_\ell$.

### Formal Proof:
1. Consider the complete graph $K_n$ on $n$ vertices, having $N = \binom{n}{2}$ edges.
2. Color each edge $e \in E(K_n)$ independently at random:
   $$\Pr(e \text{ is Red}) = p, \quad \Pr(e \text{ is Blue}) = 1 - p$$
3. For each subset $S \subseteq V$ of size $|S| = k$:
   - The induced subgraph $K_n[S]$ contains $\binom{k}{2}$ edges.
   - Let $A_S$ be the bad event that all $\binom{k}{2}$ edges in $S$ are colored **Red**.
   - By independence:
     $$\Pr(A_S) = p^{\binom{k}{2}}$$
4. For each subset $T \subseteq V$ of size $|T| = \ell$:
   - The induced subgraph $K_n[T]$ contains $\binom{\ell}{2}$ edges.
   - Let $B_T$ be the bad event that all $\binom{\ell}{2}$ edges in $T$ are colored **Blue**.
   - By independence:
     $$\Pr(B_T) = (1 - p)^{\binom{\ell}{2}}$$
5. The coloring fails to have the desired property if and only if **at least one** bad event occurs:
   $$\mathcal{E} = \left( \bigcup_{S \in \binom{V}{k}} A_S \right) \cup \left( \bigcup_{T \in \binom{V}{\ell}} B_T \right)$$
6. By the **Union Bound** (Boole's Inequality):
   $$\Pr(\mathcal{E}) \le \sum_{S \in \binom{V}{k}} \Pr(A_S) + \sum_{T \in \binom{V}{\ell}} \Pr(B_T)$$
   $$\Pr(\mathcal{E}) \le \binom{n}{k} p^{\binom{k}{2}} + \binom{n}{\ell} (1 - p)^{\binom{\ell}{2}}$$
7. We are given that this sum is strictly less than 1:
   $$\Pr(\mathcal{E}) < 1$$
8. Therefore, the probability of the complementary event (that **no** red $K_k$ and **no** blue $K_\ell$ exists) is strictly positive:
   $$\Pr(\mathcal{E}^c) = 1 - \Pr(\mathcal{E}) > 0$$
9. Since the probability is strictly positive, there must exist at least one specific deterministic 2-coloring of $E(K_n)$ with neither a red $K_k$ nor a blue $K_\ell$. $\blacksquare$

---

## 📌 Solution 2: Multicolor Ramsey Bound $R(3, 3, 3) \le 17$

**Theorem:** $R(3, 3, 3) \le 17$.

### Formal Proof:
1. Consider any arbitrary 3-coloring of the edges of $K_{17}$ using colors $\{1, 2, 3\}$.
2. Choose an arbitrary vertex $x \in V(K_{17})$.
3. Vertex $x$ is incident to $|V| - 1 = 17 - 1 = 16$ edges.
4. By the **Generalized Pigeonhole Principle**, when 16 items are partitioned into 3 color classes, at least one color class must contain at least:
   $$\left\lceil \frac{16}{3} \right\rceil = \lceil 5.333 \rceil = 6 \text{ edges}$$
5. Without loss of generality, assume that color 1 contains at least 6 edges incident to $x$.
   Let $Y = \{y_1, y_2, y_3, y_4, y_5, y_6\}$ be 6 neighbors of $x$ such that each edge $\{x, y_j\}$ has color 1.
6. Now consider the edges between vertices in the set $Y$:
   - **Case 1: There exists an edge $\{y_j, y_k\}$ with color 1.**
     Then the triangle formed by $\{x, y_j, y_k\}$ has all three edges colored 1:
     - $\{x, y_j\}$ is color 1.
     - $\{x, y_k\}$ is color 1.
     - $\{y_j, y_k\}$ is color 1.
     This forms a **monochromatic triangle in color 1**!
   - **Case 2: No edge between vertices in $Y$ has color 1.**
     Then every edge between the 6 vertices of $Y$ must be colored with either **color 2** or **color 3**.
     The induced subgraph $K_{17}[Y]$ is a complete graph $K_6$ whose edges are colored with 2 colors.
     Recall the classic 2-color Ramsey number:
     $$R(3, 3) = 6$$
     By the definition of $R(3, 3) = 6$, every 2-coloring of $K_6$ must contain a monochromatic triangle!
     Therefore, there exists a monochromatic triangle in $Y$ of color 2 or color 3.
7. In both cases, a monochromatic triangle is guaranteed to exist.
8. Therefore, $R(3, 3, 3) \le 17$. $\blacksquare$

---

## 📌 Solution 3: Finiteness of Multicolor Ramsey Numbers

**Theorem:** For all $t \ge 2$ and positive integers $n_1, \dots, n_t$, $R(n_1, \dots, n_t)$ is finite.

### Formal Proof (by Induction on $t$):
- **Base Case ($t = 2$):**
  For $t = 2$, the standard 2-color Ramsey Theorem states that $R(n_1, n_2) \le \binom{n_1 + n_2 - 2}{n_1 - 1} < \infty$, which is finite for all $n_1, n_2$.
- **Induction Hypothesis:**
  Assume that for any $t - 1$ positive integers $m_1, \dots, m_{t-1}$, the multicolor Ramsey number $R(m_1, \dots, m_{t-1})$ is finite.
- **Induction Step ($t$):**
  Let $n_1, n_2, \dots, n_t$ be given.
  1. Define:
     $$N = R\big(R(n_1, n_2), \; n_3, \; n_4, \; \dots, \; n_t\big)$$
     By the induction hypothesis, $R(n_1, n_2)$ is a finite integer, and this is a Ramsey number with $t - 1$ parameters, so $N$ is **finite**.
  2. Consider any arbitrary $t$-coloring $\chi: E(K_N) \to \{1, 2, 3, \dots, t\}$ of the edges of $K_N$.
  3. Define a merged $(t-1)$-coloring $\psi: E(K_N) \to \{C_{1,2}, \; 3, \; 4, \; \dots, \; t\}$ by:
     $$\psi(e) = \begin{cases}
     C_{1,2} & \text{if } \chi(e) \in \{1, 2\} \\[2pt]
     \chi(e) & \text{if } \chi(e) \in \{3, \dots, t\}
     \end{cases}$$
  4. By definition of $N = R(R(n_1, n_2), n_3, \dots, n_t)$, under the coloring $\psi$, $K_N$ must contain either:
     - A monochromatic clique of size $n_i$ in color $i$ for some $i \in \{3, \dots, t\}$.
       In this case, all edges in this clique have color $i$ under the original coloring $\chi$, so we have found our monochromatic $K_{n_i}$!
     - OR, a monochromatic clique $S$ of size $R(n_1, n_2)$ in the merged color $C_{1,2}$.
  5. In the second case, every edge in the induced subgraph $K_N[S]$ has color $1$ or color $2$ under the original coloring $\chi$.
     Since $|S| = R(n_1, n_2)$, the induced subgraph $K_N[S]$ is a 2-colored complete graph on $R(n_1, n_2)$ vertices.
     By definition of $R(n_1, n_2)$, this clique must contain either:
     - A monochromatic clique of size $n_1$ in color 1, OR
     - A monochromatic clique of size $n_2$ in color 2.
  6. In all possibilities, a monochromatic $K_{n_i}$ in color $i$ is guaranteed.
  7. Therefore:
     $$R(n_1, n_2, \dots, n_t) \le R\big(R(n_1, n_2), \; n_3, \; \dots, \; n_t\big) < \infty$$
  This completes the induction. $\blacksquare$

---

## 📌 Solution 4: Forcing the Diamond Subgraph $A$

**Problem:** Prove that if $G = (V, E)$ has $n \ge 4$ vertices and $m \ge \lfloor n^2/4 \rfloor + 1$ edges, then $G$ contains the diamond graph $A$ (two triangles sharing an edge).

### Formal Proof:
1. By **Mantel's Theorem**, any graph on $n$ vertices with $m > \lfloor n^2/4 \rfloor$ edges must contain at least one triangle $T = \{u, v, w\}$.
2. We prove by induction on $n \ge 4$ that if $G$ does not contain $A$, then $m \le \lfloor n^2/4 \rfloor$:
   - **Base Case ($n = 4$):**
     $G$ has 4 vertices and contains a triangle $T = \{u, v, w\}$.
     Let $z$ be the fourth vertex.
     If $z$ is adjacent to 2 or 3 vertices of $T$, then $z$ together with those vertices forms a second triangle sharing an edge with $T$, which is the diamond graph $A$!
     Therefore, to avoid $A$, $z$ can be adjacent to at most 1 vertex in $T$.
     The maximum number of edges without creating $A$ is:
     $$m = |E(T)| + \deg(z) \le 3 + 1 = 4$$
     Notice $\lfloor 4^2/4 \rfloor = 4$. Thus $m \le \lfloor n^2/4 \rfloor$.
   - **Inductive Step ($n \ge 5$):**
     Assume that any graph on $n - 1$ vertices without $A$ has at most $\lfloor (n-1)^2/4 \rfloor$ edges.
     Let $G$ be a graph on $n$ vertices containing no $A$. Since $G$ contains a triangle $T = \{u, v, w\}$:
     - For any vertex $z \in V \setminus T$, $z$ cannot be adjacent to two vertices of $T$ (otherwise $z$ and those two vertices would form a triangle sharing an edge with $T$, creating $A$).
     - Thus, every $z \in V \setminus T$ has at most 1 neighbor in $T$.
     - Summing the neighborhoods of the triangle vertices into $V \setminus T$:
       $$(\deg(u) - 2) + (\deg(v) - 2) + (\deg(w) - 2) \le |V \setminus T| = n - 3$$
       $$\deg(u) + \deg(v) + \deg(w) \le n - 3 + 6 = n + 3$$
     - By the Pigeonhole Principle, the vertex of minimum degree in $T$, say $v$, satisfies:
       $$\deg(v) \le \frac{n + 3}{3} \le \left\lfloor \frac{n}{2} \right\rfloor \quad (\text{for } n \ge 5)$$
     - Delete vertex $v$. The graph $G \setminus \{v\}$ has $n - 1$ vertices and contains no $A$.
     - By the induction hypothesis:
       $$|E(G \setminus \{v\})| \le \left\lfloor \frac{(n - 1)^2}{4} \right\rfloor$$
     - Re-inserting $v$:
       $$m = |E(G \setminus \{v\})| + \deg(v) \le \left\lfloor \frac{(n-1)^2}{4} \right\rfloor + \left\lfloor \frac{n}{2} \right\rfloor = \left\lfloor \frac{n^2}{4} \right\rfloor$$
3. Therefore, if $m \ge \lfloor n^2/4 \rfloor + 1$, $G$ must contain $A$. $\blacksquare$

---

## 📌 Solution 5: Graphs with Exactly One Triangle

### Part (a): Construction Achieving $\lfloor (n-1)^2/4 \rfloor + 2$ Edges
1. Take the complete bipartite graph on $n - 1$ vertices with balanced parts:
   $$H = K_{\lfloor (n-1)/2 \rfloor, \; \lceil (n-1)/2 \rceil}$$
   The number of edges in $H$ is $\lfloor \frac{(n-1)^2}{4} \rfloor$.
   Since $H$ is bipartite, it contains **zero triangles**.
2. Add an $n$-th vertex $z$.
3. Pick one vertex $x$ from the left partition of $H$ and one vertex $y$ from the right partition of $H$.
4. Connect $z$ to $x$ and to $y$:
   $$E(G) = E(H) \cup \{\{z, x\}, \; \{z, y\}\}$$
   This adds exactly 2 edges, so:
   $$|E(G)| = \left\lfloor \frac{(n-1)^2}{4} \right\rfloor + 2$$
5. **Triangle Count:**
   - Since $x$ and $y$ are on opposite sides of the bipartite graph, the edge $\{x, y\}$ already exists in $H$.
   - Together with $\{z, x\}$ and $\{z, y\}$, the vertices $\{z, x, y\}$ form a triangle!
   - Since $z$ has degree 2, any triangle involving $z$ must use both neighbors $x$ and $y$. Thus this is the only triangle involving $z$.
   - Since $H$ contains no triangles, this is the **unique triangle** in the entire graph $G$. $\blacksquare$

---

### Part (b): Proof of the Upper Bound
1. Let $G = (V, E)$ be a graph on $n$ vertices containing **exactly one triangle** $T = \{u, v, w\}$.
2. Delete the 3 vertices of $T$ to form $H = G \setminus T$.
   The number of vertices in $H$ is $n - 3$.
3. Since the unique triangle of $G$ was $T$, the graph $H$ is completely **triangle-free**.
4. By **Mantel's Theorem**:
   $$|E(H)| \le \left\lfloor \frac{(n - 3)^2}{4} \right\rfloor$$
5. Now consider the edges incident to $T$:
   - The triangle $T$ itself contains 3 edges.
   - For any vertex $z \in V(H)$, $z$ cannot be adjacent to two or more vertices in $T$ (otherwise, $z$ would form another triangle with those vertices in $T$, contradicting uniqueness).
   - Therefore, every vertex in $V(H)$ is adjacent to at most 1 vertex of $T$:
     $$e(T, V(H)) = \sum_{z \in V(H)} |N(z) \cap T| \le |V(H)| = n - 3$$
6. Summing all edges in $G$:
   $$m = |E(H)| + e(T, V(H)) + |E(T)| \le \left\lfloor \frac{(n-3)^2}{4} \right\rfloor + (n - 3) + 3$$
   $$m \le \left\lfloor \frac{n^2 - 6n + 9}{4} \right\rfloor + n = \left\lfloor \frac{n^2 - 6n + 9 + 4n}{4} \right\rfloor = \left\lfloor \frac{n^2 - 2n + 9}{4} \right\rfloor$$
   $$m \le \left\lfloor \frac{(n^2 - 2n + 1) + 8}{4} \right\rfloor = \left\lfloor \frac{(n-1)^2}{4} + 2 \right\rfloor = \left\lfloor \frac{(n-1)^2}{4} \right\rfloor + 2$$
Therefore, $m \le \lfloor (n-1)^2/4 \rfloor + 2$. $\blacksquare$
