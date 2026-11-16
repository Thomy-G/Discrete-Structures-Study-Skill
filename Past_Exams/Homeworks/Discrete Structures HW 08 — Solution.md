---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 8
topic: "Graph Colorings, Four Color Theorem, Odd Cycle Intersections, Nordhaus-Gaddum, Coprime Graphs, Product Colorings"
problem_file: "[[Discrete Structures HW 08]]"
tags:
  - solution
  - discrete_structures
  - graph_coloring
  - planar_graphs
  - four_color_theorem
  - nordhaus_gaddum
  - chromatic_index
  - vizing_theorem
---

# 🛡️ Discrete Structures — Homework Assignment 8 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 08|View Unsolved Assignment]]
> - **Topics Covered:** Four-Color Theorem Independent Set Bound, Vertex Destruction of Odd Cycles, Nordhaus-Gaddum Inductive Proof, Coprime Clique & Prime Factor Coloring, Modular Cartesian Vertex Coloring, Vizing Prism Class 1 Decomposition.

---

## 📌 Solution 1: Chromatic Bounds & Structural Colorings

### Part (a): Large Independent Set $|A| \ge |V|/4$ in Planar Graphs
- **Proof:**
  1. Let $G = (V, E)$ be any planar graph.
  2. By the **Four-Color Theorem** (Appel & Haken), every planar graph is 4-colorable:
     $$\chi(G) \le 4$$
  3. Therefore, the vertex set $V$ can be partitioned into 4 disjoint independent sets (color classes):
     $$V = V_1 \;\dot\cup\; V_2 \;\dot\cup\; V_3 \;\dot\cup\; V_4$$
     where each $V_i$ contains no adjacent vertices.
  4. The total number of vertices satisfies:
     $$|V| = |V_1| + |V_2| + |V_3| + |V_4|$$
  5. By the **Pigeonhole Principle** (or by average), at least one color class $V_k$ must have size at least the average:
     $$|V_k| \ge \frac{|V|}{4}$$
  6. Setting $A = V_k$, $A$ is an independent set with $|A| \ge \frac{|V|}{4}$. $\blacksquare$

---

### Part (b): Common Intersection of All Odd Cycles $\implies \chi(G) \le 3$
- **Proof:**
  1. Let $v \in V$ be the common vertex shared by all odd cycles in $G$.
  2. Consider the induced subgraph formed by deleting $v$:
     $$G' = G \setminus \{v\} = G[V \setminus \{v\}]$$
  3. Any odd cycle in $G'$ would be an odd cycle in $G$ that does **not** contain $v$.
  4. But by assumption, every odd cycle in $G$ passes through $v$.
  5. Therefore, $G'$ contains **no odd cycles**.
  6. By **König's Bipartite Characterization Theorem**, a graph is bipartite if and only if it has no odd cycles.
     Thus, $G'$ is a bipartite graph, which implies:
     $$\chi(G') \le 2$$
  7. There exists a valid 2-coloring $c': V \setminus \{v\} \to \{1, 2\}$ of $G'$.
  8. We extend $c'$ to a coloring $c$ of the entire graph $G$ by assigning a third distinct color to $v$:
     $$c(u) = \begin{cases} c'(u) & u \in V \setminus \{v\} \\[2pt] 3 & u = v \end{cases}$$
  9. For any edge $\{u, w\} \in E(G)$:
     - If both $u, w \ne v$, $c(u) = c'(u) \ne c'(w) = c(w)$ because $c'$ was a valid coloring of $G'$.
     - If one endpoint is $v$ (say $u = v$), then $c(u) = 3$ while $c(w) \in \{1, 2\}$. Thus $c(u) \ne c(w)$.
  10. Therefore, $c$ is a valid 3-coloring of $G$, proving:
      $$\chi(G) \le 3$$
      $\blacksquare$

---

## 📌 Solution 2: Nordhaus-Gaddum Sum Bound $\chi(G) + \chi(\overline{G}) \le n + 1$

**Theorem:** For any simple graph $G$ on $n$ vertices, $\chi(G) + \chi(\overline{G}) \le n + 1$.

### Formal Proof (by Induction on $n$):
- **Base Case ($n = 1$):**
  $G = K_1$, so $\chi(G) = 1$ and $\overline{G} = \overline{K_1} = K_1$, so $\chi(\overline{G}) = 1$.
  Sum: $1 + 1 = 2 \le 1 + 1 = 2$. Holds with equality.
- **Induction Hypothesis:**
  Assume the claim holds for all graphs with $n - 1$ vertices:
  $$\chi(G') + \chi(\overline{G}') \le n$$
- **Induction Step ($n$):**
  Let $G$ be a graph on $n$ vertices. Choose an arbitrary vertex $v \in V$, and define:
  $$G' = G \setminus \{v\} \quad \text{and} \quad \overline{G}' = \overline{G} \setminus \{v\}$$
  Both are graphs on $n - 1$ vertices. By the induction hypothesis:
  $$\chi(G') + \chi(\overline{G}') \le n$$

  Now examine the degrees of $v$ in $G$ and in $\overline{G}$:
  Notice that $v$ has $\deg_G(v)$ neighbors in $G$ and $\deg_{\overline{G}}(v)$ neighbors in $\overline{G}$.
  Every other vertex of $V \setminus \{v\}$ is adjacent to $v$ in either $G$ or $\overline{G}$, but not both:
  $$\deg_G(v) + \deg_{\overline{G}}(v) = n - 1$$

  We consider two cases:
  - **Case 1: $\deg_G(v) < \chi(G')$ or $\deg_{\overline{G}}(v) < \chi(\overline{G}')$.**
    Without loss of generality, assume $\deg_G(v) < \chi(G')$.
    - In any valid coloring of $G'$ with $\chi(G')$ colors, the neighbors of $v$ in $G'$ can occupy at most $\deg_G(v)$ distinct colors.
    - Since $\deg_G(v) < \chi(G')$, there is at least one color class in $G'$ that contains **no neighbor of $v$**.
    - We can assign this unused color to $v$, giving a valid coloring of $G$ with the **same** number of colors:
      $$\chi(G) = \chi(G')$$
    - For $\overline{G}$, adding $v$ requires at most one new color:
      $$\chi(\overline{G}) \le \chi(\overline{G}') + 1$$
    - Summing the two:
      $$\chi(G) + \chi(\overline{G}) \le \chi(G') + \chi(\overline{G}') + 1 \le n + 1$$

  - **Case 2: $\deg_G(v) \ge \chi(G')$ and $\deg_{\overline{G}}(v) \ge \chi(\overline{G}')$.**
    - Adding these two inequalities together:
      $$\chi(G') + \chi(\overline{G}') \le \deg_G(v) + \deg_{\overline{G}}(v) = n - 1$$
    - In the worst case, adding $v$ to $G'$ and to $\overline{G}'$ increases each chromatic number by at most 1:
      $$\chi(G) \le \chi(G') + 1 \quad \text{and} \quad \chi(\overline{G}) \le \chi(\overline{G}') + 1$$
    - Summing them:
      $$\chi(G) + \chi(\overline{G}) \le (\chi(G') + 1) + (\chi(\overline{G}') + 1) = (\chi(G') + \chi(\overline{G}')) + 2 \le (n - 1) + 2 = n + 1$$

  In both cases, $\chi(G) + \chi(\overline{G}) \le n + 1$. $\blacksquare$

---

## 📌 Solution 3: The Coprime Graph $\operatorname{Coprime}(n)$

**Problem:** Determine $\chi(\operatorname{Coprime}(n))$ on $V = \{1, \dots, n\}$ where $a \sim b \iff \gcd(a, b) = 1$.

### 1. Lower Bound via Maximum Clique $\omega(G)$:
- The number $1$ satisfies $\gcd(1, k) = 1$ for all $k \in \{2, \dots, n\}$. Thus $1$ is adjacent to every vertex in $V$.
- Let $P = \{p_1, p_2, \dots, p_{\pi(n)}\}$ be the set of all primes $\le n$.
- For any two distinct primes $p_i \ne p_j$, $\gcd(p_i, p_j) = 1$, so they are connected by an edge.
- Furthermore, for each prime $p_i$, $\gcd(1, p_i) = 1$, so $1$ is connected to all primes.
- Therefore, the subset:
  $$K = \{1\} \cup P$$
  forms a **complete subgraph (clique)** in $\operatorname{Coprime}(n)$.
- The size of this clique is:
  $$\omega(G) \ge |K| = 1 + \pi(n)$$
- Since the chromatic number is at least the clique number:
  $$\chi(\operatorname{Coprime}(n)) \ge \omega(G) \ge \pi(n) + 1$$

### 2. Upper Bound via Valid $(\pi(n) + 1)$-Coloring:
We construct an explicit valid coloring using $\pi(n) + 1$ colors, labeled $\{c_0, c_1, c_2, \dots, c_{\pi(n)}\}$:
1. **Color vertex 1:** Assign $c(1) = c_0$.
2. **Color the primes:** For each prime $p_i \in P$, assign $c(p_i) = c_i$.
3. **Color the composite numbers:** For any composite integer $m \in \{2, \dots, n\}$, consider its unique prime factorization $m = p_{i_1}^{e_1} \dots p_{i_k}^{e_k}$.
   Let $p_{\text{min}}(m)$ be the **smallest prime factor** of $m$.
   Assign to $m$ the color of its smallest prime factor:
   $$c(m) = c(p_{\text{min}}(m)) = c_i$$

### 3. Verification of Validity:
Let $u, v \in V$ be two vertices with the same color $c(u) = c(v)$. We show they cannot be adjacent ($\{u, v\} \notin E$):
- If the shared color is $c_0$, only $u = 1$ has color $c_0$, so no two vertices share $c_0$.
- If the shared color is $c_i$ ($i \ge 1$):
  By construction, every vertex colored $c_i$ is divisible by the prime $p_i$:
  $$p_i \mid u \quad \text{and} \quad p_i \mid v$$
  Therefore:
  $$\gcd(u, v) \ge p_i > 1$$
- By definition of the Coprime Graph, an edge exists only when $\gcd(u, v) = 1$.
  Since $\gcd(u, v) \ge p_i > 1$, $\{u, v\} \notin E$.
Thus, no two vertices with the same color share an edge. The coloring is valid!

### Conclusion:
$$\chi(\operatorname{Coprime}(n)) = \pi(n) + 1$$
$\blacksquare$

---

## 📌 Solution 4: Vertex and Edge Colorings of Cartesian Products

### Part (a): Vertex Chromatic Number $\chi(G \square H) = \max\{\chi(G), \chi(H)\}$
- **Lower Bound:**
  Let $h_0 \in V(H)$ be any fixed vertex. The induced subgraph $G \square \{h_0\}$ is isomorphic to $G$.
  Therefore, $\chi(G \square H) \ge \chi(G)$.
  Similarly, fixing $g_0 \in V(G)$ yields an induced subgraph isomorphic to $H$, so $\chi(G \square H) \ge \chi(H)$.
  Thus:
  $$\chi(G \square H) \ge \max\{\chi(G), \; \chi(H)\}$$

- **Upper Bound:**
  Let $k = \max\{\chi(G), \chi(H)\}$.
  There exist valid vertex colorings:
  $$c_G: V(G) \to \mathbb{Z}_k \quad \text{and} \quad c_H: V(H) \to \mathbb{Z}_k$$
  Define the coloring $c: V(G \square H) \to \mathbb{Z}_k$ by:
  $$c(g, h) = \big(c_G(g) + c_H(h)\big) \pmod k$$
  We show that $c$ is a valid coloring. Let $(g_1, h_1)$ and $(g_2, h_2)$ be adjacent in $G \square H$:
  - **Case 1: $h_1 = h_2$ and $\{g_1, g_2\} \in E(G)$.**
    Then $c_G(g_1) \ne c_G(g_2)$ because $c_G$ is a valid coloring of $G$.
    $$c(g_1, h_1) - c(g_2, h_2) \equiv c_G(g_1) - c_G(g_2) \not\equiv 0 \pmod k$$
    Thus $c(g_1, h_1) \ne c(g_2, h_2)$.
  - **Case 2: $g_1 = g_2$ and $\{h_1, h_2\} \in E(H)$.**
    Then $c_H(h_1) \ne c_H(h_2)$ because $c_H$ is a valid coloring of $H$.
    $$c(g_1, h_1) - c(g_2, h_2) \equiv c_H(h_1) - c_H(h_2) \not\equiv 0 \pmod k$$
    Thus $c(g_1, h_1) \ne c(g_2, h_2)$.
  In both cases, adjacent vertices receive different colors.
  Thus $\chi(G \square H) \le k = \max\{\chi(G), \chi(H)\}$.
  Combining both bounds: $\chi(G \square H) = \max\{\chi(G), \chi(H)\}$. $\blacksquare$

---

### Part (b): Edge Chromatic Index $\chi'(G \square K_2) = \Delta(G \square K_2)$
- **Lemma:**
  For any vertex $(g, i) \in V(G \square K_2)$ (where $i \in \{1, 2\}$):
  $$\deg((g, i)) = \deg_G(g) + \deg_{K_2}(i) = \deg_G(g) + 1$$
  Thus the maximum degree is $\Delta(G \square K_2) = \Delta(G) + 1$.
- **Lower Bound:** Always $\chi'(H) \ge \Delta(H)$, so $\chi'(G \square K_2) \ge \Delta(G) + 1$.
- **Upper Bound:**
  1. By **Vizing's Theorem**, the edges of $G$ can be properly colored using $\Delta(G) + 1$ colors:
     $$\mathcal{C} = \{1, 2, \dots, \Delta(G) + 1\}$$
     Let $\psi: E(G) \to \mathcal{C}$ be this valid edge coloring.
  2. The graph $G \square K_2$ consists of two copies of $G$:
     - $G_1$ at layer 1, with edges $\{(u, 1), (v, 1)\}$.
     - $G_2$ at layer 2, with edges $\{(u, 2), (v, 2)\}$.
     plus vertical edges $\{(u, 1), (u, 2)\}$ for each $u \in V(G)$.
  3. Color both $G_1$ and $G_2$ with the **identical** coloring $\psi$:
     $$\Psi(\{(u, 1), (v, 1)\}) = \psi(\{u, v\}), \quad \Psi(\{(u, 2), (v, 2)\}) = \psi(\{u, v\})$$
  4. Now we color the vertical edges: For each vertex $u \in V(G)$, its degree in $G$ is $\deg_G(u) \le \Delta(G)$.
     Therefore, the incident edges to $u$ in $G$ use at most $\Delta(G)$ colors from the palette $\mathcal{C}$.
     Since $|\mathcal{C}| = \Delta(G) + 1$, there exists **at least one color** $c_u \in \mathcal{C}$ that is **missing** at $u$ (i.e. not used by any edge incident to $u$).
  5. Assign this missing color $c_u$ to the vertical edge $e_u = \{(u, 1), (u, 2)\}$:
     $$\Psi(e_u) = c_u$$
  6. **Validity Check:**
     - In layer 1, all edges incident to $(u, 1)$ have colors from $\psi(E(G)) \setminus \{c_u\}$, so none has color $c_u$.
     - In layer 2, all edges incident to $(u, 2)$ also use colors distinct from $c_u$.
     - The vertical edges form a matching, so no two vertical edges touch each other.
  7. Therefore, $\Psi$ is a proper edge coloring of $G \square K_2$ using exactly $\Delta(G) + 1 = \Delta(G \square K_2)$ colors.
  Thus $\chi'(G \square K_2) = \Delta(G \square K_2)$, meaning every prism $G \square K_2$ is **Class 1**. $\blacksquare$
