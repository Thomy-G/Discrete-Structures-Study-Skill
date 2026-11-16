---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 1
topic: "Order Relations, Graph Degrees, Trees & Leaves, Mantel's Theorem"
problem_file: "[[Discrete Structures HW 01]]"
tags:
  - solution
  - discrete_structures
  - order_theory
  - graph_theory
  - trees
  - extremal_graphs
---

# 🛡️ Discrete Structures — Homework Assignment 1 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 01|View Unsolved Assignment]]
> - **Topics Covered:** Lexicographic Total Order, Equivalence Class Count Poset, Vector Componentwise Order, Degree Pigeonhole, Tree Path Characterization, Full Binary Tree Invariants, Mantel's Theorem.

---

## 📌 Solution 1: Order Relations & Posets

### Part (a): Lexicographic Order on $A^n$ is a Total Order

Let $A$ be a set with a total order $\le$. We are given the relation $R$ on $A^n$:
For $\vec{a} = (a_1, \dots, a_n), \vec{a}' = (a'_1, \dots, a'_n) \in A^n$:
$$(\vec{a}, \vec{a}') \in R \iff (\vec{a} = \vec{a}') \;\lor\; \left( \exists k \in \{1, \dots, n\} \text{ s.t. } a_k < a'_k \;\land\; \forall 1 \le i < k: a_i = a'_i \right)$$

To prove that $R$ is a **total order**, we verify the four required axioms:

#### 1. Reflexivity
- For every $\vec{a} \in A^n$, clearly $\forall 1 \le i \le n: a_i = a_i$ holds.
- By the first disjunct in the definition, $(\vec{a}, \vec{a}) \in R$. Thus $R$ is reflexive.

#### 2. Antisymmetry
- Let $\vec{a}, \vec{b} \in A^n$ such that $(\vec{a}, \vec{b}) \in R$ and $(\vec{b}, \vec{a}) \in R$.
- Assume for contradiction that $\vec{a} \ne \vec{b}$.
- Since $\vec{a} \ne \vec{b}$, the set $\{i \in \{1, \dots, n\} \mid a_i \ne b_i\}$ is non-empty. Let $k$ be its minimum element (the first coordinate where $\vec{a}$ and $\vec{b}$ differ):
  $$k = \min \{i \in \{1, \dots, n\} \mid a_i \ne b_i\}$$
- Because $(\vec{a}, \vec{b}) \in R$ and $\vec{a} \ne \vec{b}$, the first difference must satisfy:
  $$a_k < b_k$$
- Symmetrically, because $(\vec{b}, \vec{a}) \in R$ and $\vec{b} \ne \vec{a}$, the first difference between $\vec{b}$ and $\vec{a}$ (which occurs at the exact same index $k$) must satisfy:
  $$b_k < a_k$$
- But $a_k < b_k$ and $b_k < a_k$ implies $a_k \le b_k$ and $b_k \le a_k$, which by antisymmetry of $\le$ on $A$ gives $a_k = b_k$, directly contradicting $a_k \ne b_k$ (since $a < a'$ means $a \le a' \land a \ne a'$).
- Therefore, our assumption was false, so $\vec{a} = \vec{b}$. $R$ is antisymmetric.

#### 3. Transitivity
- Let $\vec{a}, \vec{b}, \vec{c} \in A^n$ such that $(\vec{a}, \vec{b}) \in R$ and $(\vec{b}, \vec{c}) \in R$.
- If $\vec{a} = \vec{b}$, then $(\vec{a}, \vec{c}) = (\vec{b}, \vec{c}) \in R$.
- If $\vec{b} = \vec{c}$, then $(\vec{a}, \vec{c}) = (\vec{a}, \vec{b}) \in R$.
- Now suppose $\vec{a} \ne \vec{b}$ and $\vec{b} \ne \vec{c}$.
  - Let $i$ be the smallest index where $a_i \ne b_i$. Then $a_1 = b_1, \dots, a_{i-1} = b_{i-1}$ and $a_i < b_i$.
  - Let $j$ be the smallest index where $b_j \ne c_j$. Then $b_1 = c_1, \dots, b_{j-1} = c_{j-1}$ and $b_j < c_j$.
- We consider three cases:
  1. **Case $i < j$:** For all $k < i$, $a_k = b_k = c_k$. At coordinate $i$, since $i < j$, we have $b_i = c_i$, and hence $a_i < b_i = c_i \implies a_i < c_i$. The first difference between $\vec{a}$ and $\vec{c}$ occurs at index $i$, where $a_i < c_i$. Thus $(\vec{a}, \vec{c}) \in R$.
  2. **Case $j < i$:** For all $k < j$, $a_k = b_k = c_k$. At coordinate $j$, since $j < i$, we have $a_j = b_j$, and hence $a_j = b_j < c_j \implies a_j < c_j$. The first difference between $\vec{a}$ and $\vec{c}$ occurs at index $j$, where $a_j < c_j$. Thus $(\vec{a}, \vec{c}) \in R$.
  3. **Case $i = j$:** For all $k < i$, $a_k = b_k = c_k$. At coordinate $i$, $a_i < b_i$ and $b_i < c_i$. By transitivity of the strict order $<$ on $A$, $a_i < c_i$. Thus the first difference between $\vec{a}$ and $\vec{c}$ occurs at index $i$, where $a_i < c_i$. Thus $(\vec{a}, \vec{c}) \in R$.
- In all cases, $(\vec{a}, \vec{c}) \in R$. $R$ is transitive.

#### 4. Totality (Strongly Connected / Comparability)
- Let $\vec{a}, \vec{b} \in A^n$.
- If $\vec{a} = \vec{b}$, then $(\vec{a}, \vec{b}) \in R$ by reflexivity.
- If $\vec{a} \ne \vec{b}$, let $k = \min\{i \in \{1, \dots, n\} \mid a_i \ne b_i\}$.
  - For all $i < k$, $a_i = b_i$.
  - At coordinate $k$, $a_k \ne b_k$. Since $(A, \le)$ is a **total order**, every pair of distinct elements is comparable: either $a_k < b_k$ or $b_k < a_k$.
  - If $a_k < b_k$, then by definition $(\vec{a}, \vec{b}) \in R$.
  - If $b_k < a_k$, then by definition $(\vec{b}, \vec{a}) \in R$.
- Therefore, for every pair $\vec{a}, \vec{b} \in A^n$, at least one of $(\vec{a}, \vec{b}) \in R$ or $(\vec{b}, \vec{a}) \in R$ holds.
- Since $R$ satisfies reflexivity, antisymmetry, transitivity, and totality, $R$ is a **total order** on $A^n$. $\blacksquare$

---

### Part (b): Poset of Equivalence Relations by Class Count

Let $X = \{1, 2, \dots, 10\}$. $O$ is the set of all equivalence relations on $X$.
The relation $\le$ on $O$ is defined by:
$$R_1 \le R_2 \iff (|X/R_1| < |X/R_2|) \;\lor\; (R_1 = R_2)$$

#### 1. Proof that $(O, \le)$ is a Partial Order
We verify the three poset axioms:
1. **Reflexivity:** For any $R \in O$, $R = R$ is true, so by the second disjunct, $R \le R$.
2. **Antisymmetry:** Let $R_1, R_2 \in O$ such that $R_1 \le R_2$ and $R_2 \le R_1$.
   - Suppose for contradiction that $R_1 \ne R_2$.
   - Then by the definition of $\le$:
     $$R_1 \le R_2 \land R_1 \ne R_2 \implies |X/R_1| < |X/R_2|$$
     $$R_2 \le R_1 \land R_2 \ne R_1 \implies |X/R_2| < |X/R_1|$$
   - This implies $|X/R_1| < |X/R_2| < |X/R_1|$, which is impossible for integers $|X/R_1|, |X/R_2| \in \mathbb{N}$.
   - Contradiction. Hence $R_1 = R_2$.
3. **Transitivity:** Let $R_1, R_2, R_3 \in O$ such that $R_1 \le R_2$ and $R_2 \le R_3$.
   - If $R_1 = R_2$, then $R_1 \le R_3$ immediately.
   - If $R_2 = R_3$, then $R_1 \le R_3$ immediately.
   - If $R_1 \ne R_2$ and $R_2 \ne R_3$, then $|X/R_1| < |X/R_2|$ and $|X/R_2| < |X/R_3|$.
   - By transitivity of $<$ on $\mathbb{N}$, $|X/R_1| < |X/R_3|$.
   - By the first disjunct, $R_1 \le R_3$.
Therefore, $\le$ is a partial order on $O$. $\blacksquare$

#### 2. Disproof: $(O, \le)$ is NOT a Total Order
- To disprove totality, we must find two equivalence relations $R_1, R_2 \in O$ such that neither $R_1 \le R_2$ nor $R_2 \le R_1$ holds.
- By definition, two relations are incomparable if and only if:
  $$|X/R_1| = |X/R_2| \quad \text{and} \quad R_1 \ne R_2$$
- **Counterexample:**
  - Let $R_1$ be the equivalence relation corresponding to the partition:
    $$\mathcal{P}_1 = \big\{ \{1, 2\}, \{3\}, \{4\}, \{5\}, \{6\}, \{7\}, \{8\}, \{9\}, \{10\} \big\}$$
  - Let $R_2$ be the equivalence relation corresponding to the partition:
    $$\mathcal{P}_2 = \big\{ \{1, 3\}, \{2\}, \{4\}, \{5\}, \{6\}, \{7\}, \{8\}, \{9\}, \{10\} \big\}$$
  - Both partitions have exactly 9 equivalence classes: $|X/R_1| = |\mathcal{P}_1| = 9$ and $|X/R_2| = |\mathcal{P}_2| = 9$.
  - However, $R_1 \ne R_2$ because $(1, 2) \in R_1$ but $(1, 2) \notin R_2$.
  - Evaluating comparability:
    - $|X/R_1| \not< |X/R_2|$ (since $9 \not< 9$) and $R_1 \ne R_2 \implies R_1 \not\le R_2$.
    - $|X/R_2| \not< |X/R_1|$ (since $9 \not< 9$) and $R_2 \ne R_1 \implies R_2 \not\le R_1$.
  - Thus, $R_1$ and $R_2$ are incomparable. Hence $(O, \le)$ is **not a total order**. $\blacksquare$

#### 3. Extremal Elements in $(O, \le)$
For any equivalence relation $R$ on a 10-element set $X$, the number of equivalence classes satisfies:
$$1 \le |X/R| \le 10$$

1. **Least Element (Minimum):**
   - The minimum possible number of equivalence classes is 1.
   - $|X/R| = 1$ occurs if and only if all 10 elements are placed into a single equivalence class.
   - This uniquely identifies the **universal relation**:
     $$R_{\min} = X \times X$$
   - For every other equivalence relation $R \ne R_{\min}$, we have $|X/R| \ge 2 > 1 = |X/R_{\min}|$, which implies $R_{\min} \le R$.
   - Thus, **$R_{\min} = X \times X$ is the unique least element (minimum)** in $(O, \le)$.

2. **Greatest Element (Maximum):**
   - The maximum possible number of equivalence classes is 10.
   - $|X/R| = 10$ occurs if and only if each of the 10 elements forms its own singleton class $\{x\}$.
   - This uniquely identifies the **identity (equality) relation**:
     $$R_{\max} = \Delta_X = \{(x, x) \mid x \in X\}$$
   - For every other equivalence relation $R \ne R_{\max}$, we have $|X/R| \le 9 < 10 = |X/R_{\max}|$, which implies $R \le R_{\max}$.
   - Thus, **$R_{\max} = \Delta_X$ is the unique greatest element (maximum)** in $(O, \le)$. $\blacksquare$

---

### Part (c): Componentwise Vector Order on $\mathbb{R}^n$
- **Claim:** Componentwise comparison $\vec{v} \le \vec{u} \iff \forall i \in \{1, \dots, n\}, v_i \le u_i$ is a **partial order** on $\mathbb{R}^n$ for all $n \ge 1$. For $n = 1$ it is a total order, but for all $n \ge 2$ it is **not a total order**.
- **Proof of Partial Order:**
  1. **Reflexivity:** For all $\vec{v} \in \mathbb{R}^n$, $v_i \le v_i$ for each $i \in \{1, \dots, n\} \implies \vec{v} \le \vec{v}$.
  2. **Antisymmetry:** If $\vec{v} \le \vec{u}$ and $\vec{u} \le \vec{v}$, then $v_i \le u_i$ and $u_i \le v_i$ for each coordinate $i$, so $v_i = u_i$ for all $i \in \{1, \dots, n\}$, which means $\vec{v} = \vec{u}$.
  3. **Transitivity:** If $\vec{v} \le \vec{u}$ and $\vec{u} \le \vec{w}$, then $v_i \le u_i \le w_i \implies v_i \le w_i$ for each coordinate $i$, so $\vec{v} \le \vec{w}$.
  Hence, $(\mathbb{R}^n, \le)$ is always a partial order.
- **Totality Analysis:**
  - For $n = 1$: $\mathbb{R}^1 \cong \mathbb{R}$ with standard order $\le$, which is a total order.
  - For $n \ge 2$: It is **not a total order**.
    Consider $\vec{v} = (1, 2, 0, \dots, 0)$ and $\vec{u} = (2, 1, 0, \dots, 0)$.
    - At coordinate 1: $v_1 = 1 \le 2 = u_1$, but at coordinate 2: $v_2 = 2 \not\le 1 = u_2$. Hence $\vec{v} \not\le \vec{u}$.
    - Symmetrically, at coordinate 1: $u_1 = 2 \not\le 1 = v_1$. Hence $\vec{u} \not\le \vec{v}$.
    Neither $\vec{v} \le \vec{u}$ nor $\vec{u} \le \vec{v}$ holds, so they are incomparable. $\blacksquare$

---

## 📌 Solution 2: Pigeonhole Principle on Vertex Degrees

**Problem:** Prove that every simple graph $G = (V, E)$ with $|V| = n \ge 2$ has at least two vertices of identical degree.

### Formal Proof:
1. In any simple graph on $n$ vertices, each vertex can be adjacent to at most $n-1$ other vertices, and at least $0$ vertices. Thus, the possible degrees belong to the set:
   $$D = \{0, 1, 2, \dots, n - 1\}$$
   The cardinality of this set is $|D| = n$.
2. **Key Observation:** The degrees $0$ and $n-1$ **cannot coexist** in the same simple graph $G$:
   - If there is a vertex $u$ with $\deg(u) = n - 1$, then $u$ is adjacent to **every other vertex** in $V$.
   - Consequently, every other vertex $v \in V \setminus \{u\}$ has at least one neighbor (namely $u$), meaning $\deg(v) \ge 1$.
   - Thus, no vertex can have degree $0$.
3. Therefore, the actual set of degrees present in $G$ must be a subset of either:
   $$D_1 = \{1, 2, \dots, n - 1\} \quad \text{or} \quad D_2 = \{0, 1, \dots, n - 2\}$$
   In either case, the number of possible degree values (pigeonholes) is at most $n - 1$.
4. Since there are $n$ vertices (pigeons) mapped to at most $n - 1$ possible degree values, by the **Pigeonhole Principle**, there must exist at least two distinct vertices $u, v \in V$ with:
   $$\deg(u) = \deg(v)$$
   $\blacksquare$

---

## 📌 Solution 3: Characterization of Trees by Unique Paths

**Problem:** Prove that $G = (V, E)$ with $|V| = n$ satisfies $|E| = n - 1$ and has no cycles $\iff$ there is a unique simple path between every pair of vertices.

### Proof $(\implies)$:
1. A graph with no cycles is a **forest**.
2. A known theorem states that a forest with $k$ connected components has $|E| = n - k$ edges.
3. Here, $|E| = n - 1$, which forces $n - k = n - 1 \implies k = 1$.
4. Thus, $G$ is a connected acyclic graph, which is the definition of a **tree**.
5. **Path Existence:** Since $G$ is connected, between any two vertices $u, v \in V$ there exists at least one simple path.
6. **Path Uniqueness:** Suppose for contradiction there exist two distinct simple paths $P_1 \ne P_2$ between $u$ and $v$.
   - Trace $P_1$ and $P_2$ from $u$ until the first vertex $x$ where they diverge, and follow them until the first vertex $y$ where they meet again.
   - The subpath of $P_1$ from $x$ to $y$ together with the subpath of $P_2$ from $y$ back to $x$ forms a simple cycle in $G$.
   - This contradicts the assumption that $G$ has no cycles.
   Therefore, the path between $u$ and $v$ is unique.

### Proof $(\impliedby)$:
1. **Connectivity:** Since a path exists between every pair of vertices, $G$ is connected.
2. **Acyclicity:** If $G$ contained a simple cycle $C = (v_1, v_2, \dots, v_k, v_1)$ ($k \ge 3$), then between $v_1$ and $v_2$ there would be two distinct simple paths:
   - Path 1: the single edge $(v_1, v_2)$.
   - Path 2: the path $(v_1, v_k, v_{k-1}, \dots, v_2)$.
   This contradicts path uniqueness. Thus $G$ has no cycles.
3. Since $G$ is connected and acyclic, it is a tree. By standard tree induction, every tree on $n$ vertices has exactly $|E| = n - 1$ edges. $\blacksquare$

---

## 📌 Solution 4: Full Binary Trees & Leaf Counts

### Part (a): Leaf Formula $\ell = \frac{n+1}{2}$

#### Algebraic Proof via Degree Sum (Handshaking Lemma):
1. Let $T$ have $n$ vertices, partitioned into:
   - $1$ root vertex $r$ with $\deg(r) = 2$.
   - $i$ internal vertices, each with degree $3$.
   - $\ell$ leaf vertices, each with degree $1$.
   Total vertices:
   $$n = 1 + i + \ell \implies i = n - \ell - 1$$
2. Since $T$ is a tree, $|E| = n - 1$. By the Handshaking Lemma:
   $$\sum_{v \in V} \deg(v) = 2|E| = 2(n - 1)$$
3. Substitute the degree contributions:
   $$2(n - 1) = 1 \cdot \deg(r) + i \cdot 3 + \ell \cdot 1$$
   $$2n - 2 = 2 + 3(n - \ell - 1) + \ell$$
   $$2n - 2 = 2 + 3n - 3\ell - 3 + \ell = 3n - 2\ell - 1$$
4. Rearrange terms to solve for $\ell$:
   $$2\ell = 3n - 1 - (2n - 2) = n + 1$$
   $$\ell = \frac{n + 1}{2}$$
   $\blacksquare$

*(Note: This also proves that in any full binary tree, $n$ must be odd, so $\frac{n+1}{2}$ is an integer!)*

---

### Part (b): Tree with Maximum Degree $k$ has at least $k$ Leaves

#### Proof:
1. Let $T = (V, E)$ be a tree, and let $r \in V$ be a vertex of maximum degree $\deg(r) = \Delta(T) = k$.
2. If $k = 1$, the tree is $K_2$, which has $2 \ge 1$ leaves.
3. For $k \ge 2$: Designate $r$ as the root of $T$.
   - The root $r$ has $k$ distinct neighbors: $u_1, u_2, \dots, u_k$.
   - Removing $r$ from $T$ splits the tree into exactly $k$ connected components: $T_1, T_2, \dots, T_k$, where $u_i \in T_i$.
4. Each component $T_i$ is a connected acyclic graph, hence a tree in its own right.
5. In each subtree $T_i$:
   - If $T_i$ consists of just the single vertex $u_i$, then in the original tree $T$, $\deg_T(u_i) = 1$, so $u_i$ is a leaf of $T$.
   - If $|V(T_i)| \ge 2$, the tree $T_i$ contains at least two leaves of its own. At most one of them can be $u_i$ (which had an edge to $r$). The other leaf $w_i \in T_i$ ($w_i \ne u_i$) has $\deg_{T_i}(w_i) = 1$, and since $w_i$ has no edge to $r$, $\deg_T(w_i) = 1$. Thus $w_i$ is a leaf in $T$.
6. Therefore, each of the $k$ components contains at least one leaf of $T$. Since the components are mutually disjoint, $T$ contains at least $k$ distinct leaves. $\blacksquare$

---

## 📌 Solution 5: Mantel's Theorem & Triangle-Free Graphs

### Part (a): Prove $m \le \frac{n^2}{4}$ for even $n$

#### Inductive Proof on $k = n/2$:
- **Base Case ($k = 1 \implies n = 2$):**
  $G$ has 2 vertices. The maximum number of edges is $1$.
  Bound check: $\frac{n^2}{4} = \frac{2^2}{4} = 1$. The bound holds: $m \le 1$.
- **Inductive Hypothesis:**
  Assume that every triangle-free graph on $n$ vertices ($n$ even) has at most $\frac{n^2}{4}$ edges.
- **Inductive Step ($n + 2$ vertices):**
  Let $G$ be a triangle-free graph on $n + 2$ vertices. If $G$ has no edges, $m = 0 \le \frac{(n+2)^2}{4}$ trivially.
  Otherwise, choose any edge $e = (u, v) \in E$.
  1. Define $A = \{u, v\}$ and $B = V \setminus A$. Thus $|B| = n$.
  2. Because $G$ contains **no triangle**, $u$ and $v$ cannot share any common neighbor in $B$:
     $$N(u) \cap N(v) = \emptyset$$
  3. Consequently, every vertex $w \in B$ is connected to **at most one** of $\{u, v\}$.
  4. The number of cut edges between $A$ and $B$, denoted $e(A, B)$, satisfies:
     $$e(A, B) = \sum_{w \in B} |N(w) \cap \{u, v\}| \le |B| = n$$
  5. The sub-graph $G[B]$ induced by $B$ has $n$ vertices and is still triangle-free.
     By the inductive hypothesis:
     $$|E(G[B])| \le \frac{n^2}{4}$$
  6. Summing all edges in $G$:
     $$m = |E(G[A])| + e(A, B) + |E(G[B])| \le 1 + n + \frac{n^2}{4}$$
     Rewrite:
     $$1 + n + \frac{n^2}{4} = \frac{n^2 + 4n + 4}{4} = \frac{(n+2)^2}{4}$$
  Therefore, $m \le \frac{(n+2)^2}{4}$, completing the induction. $\blacksquare$

---

### Part (b): Extremal Graph Structure

- The equality $m = \frac{n^2}{4}$ is achieved by the **complete bipartite graph** with equal partitions:
  $$G \cong K_{n/2, \; n/2}$$
- **Verification:**
  1. **Bipartite property:** A bipartite graph contains no odd cycles, hence no $C_3$ (triangles).
  2. **Edge count:** Partitions $V_1, V_2$ each have $|V_1| = |V_2| = n/2$. Every vertex in $V_1$ is connected to every vertex in $V_2$:
     $$|E| = |V_1| \cdot |V_2| = \frac{n}{2} \cdot \frac{n}{2} = \frac{n^2}{4}$$
  This is the unique maximal triangle-free graph on $n$ vertices (by Turán's Theorem for $r = 2$). $\blacksquare$

---

### Part (c): Triangle Forced by $k^2 + 1$ Edges ($n = 2k$)

**Problem:** Without using Part (a), prove by induction on $k \ge 2$ that if $|V| = 2k$ and $m = k^2 + 1$, then $G$ contains a triangle.

#### Proof:
- **Base Case ($k = 2 \implies n = 4$):**
  $m = 2^2 + 1 = 5$ edges on 4 vertices.
  The complete graph $K_4$ has $\binom{4}{2} = 6$ edges.
  Any graph on 4 vertices with 5 edges is obtained by removing a single edge from $K_4$.
  $K_4$ has $\binom{4}{3} = 4$ triangles. Removing one edge destroys at most 2 triangles, leaving at least $4 - 2 = 2$ triangles.
  Thus, $G$ contains a triangle.

- **Inductive Step ($k \to k+1$):**
  Suppose the claim holds for $k \ge 2$. Consider a graph $G$ on $n = 2(k+1) = 2k+2$ vertices with:
  $$m = (k+1)^2 + 1 = k^2 + 2k + 2 \text{ edges}$$
  Assume for contradiction that $G$ contains **no triangle**.
  1. Since $m > 0$, choose an adjacent pair $(u, v) \in E$.
  2. Let $A = \{u, v\}$ and $B = V \setminus A$. Then $|B| = 2k$.
  3. Because $G$ is triangle-free, $u$ and $v$ have no common neighbor in $B$. Thus, each vertex in $B$ is connected to at most one vertex in $A$.
  4. The number of edges touching $A$ is:
     $$e(A) + e(A, B) = 1 + e(A, B) \le 1 + |B| = 1 + 2k$$
  5. The remaining graph $G[B]$ has $2k$ vertices, and its edge count satisfies:
     $$|E(G[B])| = m - (1 + e(A, B)) \ge (k^2 + 2k + 2) - (2k + 1) = k^2 + 1$$
  6. But $G[B]$ has $2k$ vertices and at least $k^2 + 1$ edges. By the inductive hypothesis, $G[B]$ must contain a triangle!
  7. Since any triangle in $G[B]$ is also a triangle in $G$, $G$ contains a triangle, contradicting our assumption that $G$ was triangle-free.
  Therefore, $G$ must contain a triangle. $\blacksquare$
