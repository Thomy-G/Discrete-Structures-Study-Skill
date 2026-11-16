# Complete Solutions — Quiz 1 Simulation 3
**Course:** Discrete Structures (89-2197) — Dr. Arnold Filtser  
**Coverage:** Lectures 1–4, Recitations 1–4, and Homework 1–4  
**Max Score:** 100 Points (Part A: 75 Points, Part B: 25 Points)

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Componentwise Partial Order on $\mathbb{R}^n$ [HW 01, Q1(c)]
**Correct Answer: 2** (`For n = 1, it is a total order; for every n >= 2, it is a partial order but not a total order`).

#### Detailed Explanation:
1. **Case $n = 1$:**  
   When $n = 1$, the relation is simply the standard less-than-or-equal relation $\le$ on the real line $\mathbb{R}$, which is well-known to be a total (linear) order.
2. **Case $n \ge 2$:**  
   - **Reflexivity:** For any $\vec{v} \in \mathbb{R}^n$, $v_i \le v_i$ for all $1 \le i \le n$, so $\vec{v} \le \vec{v}$.
   - **Antisymmetry:** If $\vec{v} \le \vec{u}$ and $\vec{u} \le \vec{v}$, then for every coordinate $i$, $v_i \le u_i \le v_i \implies v_i = u_i$. Thus $\vec{v} = \vec{u}$.
   - **Transitivity:** If $\vec{v} \le \vec{u}$ and $\vec{u} \le \vec{w}$, then for every coordinate $i$, $v_i \le u_i \le w_i \implies v_i \le w_i$. Thus $\vec{v} \le \vec{w}$.  
   Therefore, for every $n \ge 2$, $(\mathbb{R}^n, \le)$ is a valid partial order.
   - **Totality Fails:** For any $n \ge 2$, consider the vectors $\vec{v} = (1, 0, 0, \dots, 0)$ and $\vec{u} = (0, 1, 0, \dots, 0)$.  
     We have $v_1 = 1 > 0 = u_1$, so $\vec{v} \not\le \vec{u}$.  
     We have $u_2 = 1 > 0 = v_2$, so $\vec{u} \not\le \vec{v}$.  
     Since $\vec{v}$ and $\vec{u}$ are incomparable, the relation is **not** a total order for any $n \ge 2$.

---

### Question 2 (15 Points) — Mantel's Theorem & Triangle-Free Bounds [HW 01, Q5]
**Correct Answer: 1** (`max |E| = 36, and chi(G) = 2`).

#### Detailed Explanation:
1. **Mantel's Theorem (HW 01, Q5 / Turán's Theorem for $r = 2$):**  
   In any simple graph $G = (V, E)$ on $n$ vertices with no triangles ($C_3$), the maximum number of edges is:
   $$|E| \le \left\lfloor \frac{n^2}{4} \right\rfloor$$
   For $n = 12$:
   $$\max |E| = \frac{12^2}{4} = \frac{144}{4} = 36$$
2. **Extremal Graph Structure & Chromatic Number:**  
   The unique graph on 12 vertices that contains no triangles and achieves exactly 36 edges is the complete balanced bipartite graph:
   $$G \cong K_{6, 6}$$
   Because $K_{6, 6}$ is a bipartite graph (and non-empty), its vertices can be partitioned into 2 independent sets, so its chromatic number is strictly:
   $$\chi(K_{6, 6}) = 2$$
   Hence, Option 1 is correct.

---

### Question 3 (15 Points) — 2-Regular Graphs & Bipartition [HW 03, Q4]
**Correct Answer: 3** (`Only (II) and (III)`).

#### Detailed Explanation:
1. **Statement (I) is FALSE:**  
   A 2-regular graph is a disjoint union of cycles. Consider $G = C_3 \cup C_3$ (two disjoint triangles).  
   - Total number of vertices is $|V| = 3 + 3 = 6$ (an **even** number of vertices).  
   - Every vertex has degree 2 (it is 2-regular).  
   - However, $G$ contains odd cycles ($C_3$). By König's Theorem, a graph is bipartite if and only if it contains no odd cycles. Thus $G$ is **not bipartite**.
2. **Statement (II) is TRUE:**  
   In any simple graph on $n$ vertices, an acyclic graph (a forest) with $k \ge 1$ connected components has $|E| = n - k \le n - 1$ edges.  
   Therefore, any graph with $m \ge n$ edges has strictly more edges than any forest on $n$ vertices can possibly have, which guarantees the existence of at least one cycle.
3. **Statement (III) is TRUE:**  
   Consider the star graph $G = K_{1, n-1}$ on $n = 8$ vertices.  
   - It is a tree, hence connected and bipartite.  
   - $|V| = 8 > 4$.  
   - The central vertex has degree $\deg(v) = n - 1 = 7$.  
   - We check: $\frac{3}{4}|V| = \frac{3}{4}(8) = 6$. Since $7 \ge 6$, this vertex satisfies the condition.  
Thus, statements (II) and (III) are true, while (I) is false.

---

### Question 4 (15 Points) — Disjoint Geometric Sets in $\mathbb{R}^2$ [HW 02, Q5]
**Correct Answer: 3** (`D must be countable, but C can be uncountable with cardinality of the continuum`).

#### Detailed Explanation:
1. **Disjoint Closed Disks $\mathcal{D}$:**  
   Every closed disk $B((x, y), r)$ contains an open ball of radius $r > 0$ as its interior.  
   Since the rational points $\mathbb{Q}^2 = \{(q_1, q_2) \mid q_1, q_2 \in \mathbb{Q}\}$ are dense in $\mathbb{R}^2$, every open region in $\mathbb{R}^2$ contains at least one rational point $(q_x, q_y) \in \mathbb{Q}^2$.  
   For each disk $D \in \mathcal{D}$, choose a rational point $q_D \in \mathbb{Q}^2$ in its interior.  
   Since all disks in $\mathcal{D}$ are mutually disjoint, if $D_1 \ne D_2$, their interiors are disjoint, so $q_{D_1} \ne q_{D_2}$.  
   This defines an injection $\psi: \mathcal{D} \to \mathbb{Q}^2$.  
   Since $\mathbb{Q}^2$ is countably infinite ($|\mathbb{Q}^2| = \aleph_0$), we have $|\mathcal{D}| \le \aleph_0$. $\mathcal{D}$ must be countable.
2. **Disjoint Circles $\mathcal{C}$:**  
   Consider a family of concentric circles centered at the origin $(0, 0)$ with radii chosen from the open interval $(0, 1)$:
   $$\mathcal{C} = \{C((0, 0), r) \mid r \in (0, 1)\}$$
   If $r_1 \ne r_2$, the distance from any point on $C((0, 0), r_1)$ to the origin is $r_1$, while for $C((0, 0), r_2)$ it is $r_2 \ne r_1$. Thus, no two circles share any common points; they are mutually disjoint.  
   The set of available radii is the interval $(0, 1)$, which has cardinality of the continuum: $|(0, 1)| = \aleph = 2^{\aleph_0}$.  
   Hence, $|\mathcal{C}| = \aleph$.

---

### Question 5 (15 Points) — Cardinal Arithmetic under CH [HW 04, Q1]
**Correct Answer: 2** (`|F1| = 2^\aleph and |F2| = \aleph`).

#### Detailed Explanation:
We are given $|X| = \aleph = 2^{\aleph_0}$ and $2^{\aleph_0} = \aleph_1$.
1. **Cardinality of $F_1 = \mathbb{N}^X$:**  
   $$|F_1| = |\mathbb{N}|^{|X|} = \aleph_0^\aleph$$
   Since $2 \le \aleph_0 \le 2^{\aleph_0} = \aleph$, we sandwich:
   $$2^\aleph \le \aleph_0^\aleph \le (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
   Therefore, $|F_1| = 2^\aleph$ (this holds even without CH!).
2. **Cardinality of $F_2 = X^\mathbb{N}$:**  
   $$|F_2| = |X|^{|\mathbb{N}|} = \aleph^{\aleph_0} = (2^{\aleph_0})^{\aleph_0} = 2^{\aleph_0 \cdot \aleph_0} = 2^{\aleph_0} = \aleph$$
   Hence, $|F_2| = \aleph$.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

---

### Part 1 (12 Points) — Characterization of Trees by Unique Paths [HW 01, Q3]

#### Theorem:
Let $G = (V, E)$ be an undirected graph on $|V| = n$ vertices.  
Then $|E| = n - 1$ and $G$ is acyclic if and only if there exists a unique simple path between every pair of vertices in $G$.

#### Formal Proof:

##### Direction 1 ($\implies$): Assume $|E| = n - 1$ and $G$ is acyclic.
1. **Connectivity:**  
   Since $G$ is acyclic, it is a forest. Let $k$ be the number of connected components of $G$.  
   By the forest edge formula (HW 02, Q2), $|E| = |V| - k$.  
   Substituting the given $|E| = n - 1$ and $|V| = n$:
   $$n - 1 = n - k \implies k = 1$$
   Thus, $G$ has exactly 1 connected component, meaning $G$ is **connected**.  
   Being connected and acyclic, $G$ is a **tree**.
2. **Existence of Paths:**  
   Since $G$ is connected, for any two vertices $u, v \in V$, there exists at least one simple path between $u$ and $v$.
3. **Uniqueness of Paths:**  
   Assume for contradiction that there exist two distinct simple paths between $u$ and $v$, say:
   $$P_1 = (u = x_0, x_1, \dots, x_p = v) \quad \text{and} \quad P_2 = (u = y_0, y_1, \dots, y_q = v)$$
   Since $P_1 \ne P_2$, let $x_i$ be the first vertex where the two paths diverge (so $x_i = y_i$, but the next edge $x_i x_{i+1} \ne y_i y_{i+1}$).  
   Let $x_j$ (with $j > i$) be the first vertex after $x_i$ along $P_1$ that also appears on $P_2$, say $x_j = y_m$.  
   Then the subpath of $P_1$ from $x_i$ to $x_j$ and the subpath of $P_2$ from $y_m$ to $y_i$ meet only at their endpoints $x_i$ and $x_j$.  
   Their concatenation forms a simple cycle of length at least 3:
   $$C = (x_i, x_{i+1}, \dots, x_j = y_m, y_{m-1}, \dots, y_i = x_i)$$
   This directly contradicts the given condition that $G$ is acyclic.  
   Therefore, the path between every pair of vertices is unique.

---

##### Direction 2 ($\impliedby$): Assume there exists a unique simple path between every pair of vertices.
1. **Connectivity:**  
   Since a path exists between every pair of vertices $u, v \in V$, the graph $G$ is connected.
2. **Acyclicity:**  
   Assume for contradiction that $G$ contains a cycle:
   $$C = (v_1, v_2, \dots, v_r, v_1) \quad (r \ge 3)$$
   Consider the two adjacent vertices $v_1$ and $v_2$.  
   - There is a simple path of length 1 between them: $P_1 = (v_1, v_2)$.  
   - There is another simple path of length $r - 1 \ge 2$ between them along the rest of the cycle: $P_2 = (v_1, v_r, v_{r-1}, \dots, v_2)$.  
   Since $r \ge 3$, these are two distinct simple paths between $v_1$ and $v_2$, which directly contradicts the assumption that simple paths between any pair of vertices are unique.  
   Therefore, $G$ contains no cycles (it is acyclic).
3. **Edge Count:**  
   Since $G$ is connected and acyclic, $G$ is a tree.  
   A standard theorem of graph theory (proved by induction on $n$ via leaf pruning) establishes that every tree on $n$ vertices has exactly:
   $$|E| = n - 1$$
   edges.

Combining both directions, the equivalence is proved. $\blacksquare$

---

### Part 2 (13 Points) — Explicit Bijection $\mathcal{P}(A) \sim \{0, 1\}^A$ without CSB [HW 02, Q4(c)]

*(This exact problem appeared as Question 1 on the 2026 Quiz 1!)*

#### Theorem:
For any set $A$, there exists an explicit bijection between the power set $\mathcal{P}(A)$ and the function space $\{0, 1\}^A$.

#### Formal Proof:
1. **Construction of the Mapping $\Phi$:**  
   Define $\Phi: \mathcal{P}(A) \to \{0, 1\}^A$ by sending each subset $S \subseteq A$ to its **characteristic function** (indicator function) $\mathbf{1}_S$:
   $$\Phi(S) = \mathbf{1}_S : A \to \{0, 1\}$$
   where for all $x \in A$:
   $$\mathbf{1}_S(x) = \begin{cases} 1 & \text{if } x \in S \\ 0 & \text{if } x \notin S \end{cases}$$

2. **Well-Definedness:**  
   For any subset $S \in \mathcal{P}(A)$ and any element $x \in A$, either $x \in S$ or $x \notin S$ (by excluded middle).  
   Thus $\mathbf{1}_S(x)$ is uniquely defined and takes a value strictly in $\{0, 1\}$.  
   Hence $\mathbf{1}_S$ is a valid function from $A$ to $\{0, 1\}$, so $\Phi(S) \in \{0, 1\}^A$.

3. **Injectivity of $\Phi$:**  
   Let $S_1, S_2 \in \mathcal{P}(A)$ such that $S_1 \ne S_2$.  
   By definition of set inequality, their symmetric difference is non-empty: $S_1 \Delta S_2 \ne \emptyset$.  
   Without loss of generality, there exists some element $a \in S_1 \setminus S_2$.  
   Evaluating their characteristic functions at $a$:
   - Since $a \in S_1$, we have $\Phi(S_1)(a) = \mathbf{1}_{S_1}(a) = 1$.  
   - Since $a \notin S_2$, we have $\Phi(S_2)(a) = \mathbf{1}_{S_2}(a) = 0$.  
   Since $\Phi(S_1)(a) \ne \Phi(S_2)(a)$, the two functions are not identical:
   $$\Phi(S_1) \ne \Phi(S_2)$$
   Thus $\Phi$ is injective.

4. **Surjectivity of $\Phi$:**  
   Let $f \in \{0, 1\}^A$ be an arbitrary function from $A$ to $\{0, 1\}$.  
   We must find a subset $S \in \mathcal{P}(A)$ such that $\Phi(S) = f$.  
   Define:
   $$S = \{x \in A \mid f(x) = 1\} = f^{-1}(\{1\})$$
   Clearly, $S \subseteq A$, so $S \in \mathcal{P}(A)$.  
   We now check that $\Phi(S) = f$ by evaluating both functions on an arbitrary element $x \in A$:
   - If $f(x) = 1$: then by definition of $S$, $x \in S$, which implies $\Phi(S)(x) = \mathbf{1}_S(x) = 1 = f(x)$.  
   - If $f(x) = 0$: then since the codomain is $\{0, 1\}$, $f(x) \ne 1$, so $x \notin S$. This implies $\Phi(S)(x) = \mathbf{1}_S(x) = 0 = f(x)$.  
   In both cases, $\Phi(S)(x) = f(x)$ for all $x \in A$.  
   Therefore, $\Phi(S) = f$, which proves that $\Phi$ is surjective.

5. **Conclusion:**  
   Since $\Phi$ is both injective and surjective, it is an explicit bijection between $\mathcal{P}(A)$ and $\{0, 1\}^A$.  
   Hence:
   $$\mathcal{P}(A) \sim \{0, 1\}^A \quad \blacksquare$$
