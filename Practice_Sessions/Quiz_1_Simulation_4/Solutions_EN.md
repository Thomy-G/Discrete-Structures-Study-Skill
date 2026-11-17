# Complete Solutions — Quiz 1 Simulation 4
**Course:** Discrete Structures (89-2197) — Dr. Arnold Filtser  
**Coverage:** Lectures 1–4, Recitations 1–4, and Homework 1–4  
**Max Score:** 100 Points (Part A: 75 Points, Part B: 25 Points)

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Lexicographical Order on Binary Sequences [HW 01, Q1(a)]
**Correct Answer: 2** (`(S, <=_lex) is a total order with minimum element (0,0,0,...) and maximum element (1,1,1,...), but it is not a well-ordered set`).

#### Detailed Explanation:
1. **Total Order:**  
   Let $s, t \in S = \{0, 1\}^\mathbb{N}$ be any two distinct sequences ($s \ne t$).  
   There exists a well-defined minimal index $i \in \mathbb{N}$ where they differ: $i = \min \{j \in \mathbb{N} \mid s_j \ne t_j\}$.  
   Since $A = \{0, 1\}$ has a total order ($0 < 1$), either $s_i = 0 < 1 = t_i$ (in which case $s <_{\text{lex}} t$) or $t_i = 0 < 1 = s_i$ (in which case $t <_{\text{lex}} s$).  
   Along with standard reflexivity, antisymmetry, and transitivity, this proves that $(S, \le_{\text{lex}})$ is a **total order**.
2. **Extreme Elements:**  
   - $\vec{0} = (0, 0, 0, \dots)$ satisfies $\vec{0} \le_{\text{lex}} s$ for all $s \in S$, because at the first non-zero bit of $s$, $\vec{0}$ has a 0 while $s$ has a 1. Thus $\vec{0}$ is the unique minimum.  
   - $\vec{1} = (1, 1, 1, \dots)$ similarly satisfies $s \le_{\text{lex}} \vec{1}$ for all $s \in S$, so $\vec{1}$ is the unique maximum.
3. **Not a Well-Ordered Set:**  
   A set is well-ordered if every non-empty subset has a minimum element (which is equivalent to having no infinite strictly descending chains).  
   Consider the subset $U = \{u_1, u_2, u_3, \dots\} \subset S$ defined by:
   $$u_1 = (0, 1, 0, 0, 0, \dots)$$
   $$u_2 = (0, 0, 1, 0, 0, \dots)$$
   $$u_3 = (0, 0, 0, 1, 0, \dots)$$
   $$u_k = (\underbrace{0, \dots, 0}_{k \text{ zeros}}, 1, 0, 0, \dots)$$
   Notice that $u_1 >_{\text{lex}} u_2 >_{\text{lex}} u_3 >_{\text{lex}} \dots$. This is an **infinite strictly descending chain**.  
   The subset $U$ has no minimum element in $U$ (for any $u_k \in U$, $u_{k+1} \in U$ is strictly smaller).  
   Therefore, $(S, \le_{\text{lex}})$ is **not** a well-ordered set.

---

### Question 2 (15 Points) — Graph Degree Parity & Components [HW 02 & HW 03, Q3]
**Correct Answer: 1** (`Every connected component C_i must contain an even number of vertices, and k <= 5`).

#### Detailed Explanation:
1. **Component Parity:**  
   Let $C_i$ be any connected component of $G$. Since $G$ is 3-regular and no edges exist between distinct components, every vertex in $C_i$ has degree 3 in $C_i$.  
   By the Handshaking Lemma applied to the component $C_i$:
   $$\sum_{v \in V(C_i)} \deg(v) = 2 |E(C_i)| \implies 3 |V(C_i)| = 2 |E(C_i)|$$
   The right-hand side is an even integer, which forces $3 |V(C_i)|$ to be even. Since 3 is odd, $|V(C_i)|$ must be an **even integer**.
2. **Bound on the Number of Components $k$:**  
   In any simple graph that is 3-regular, each vertex in $C_i$ must have 3 distinct neighbors in $C_i$.  
   Thus, every component must contain at least $1 + 3 = 4$ vertices:
   $$|V(C_i)| \ge 4 \quad (\forall 1 \le i \le k)$$
   Since the components partition the 20 vertices:
   $$20 = \sum_{i=1}^k |V(C_i)| \ge 4k \implies k \le \frac{20}{4} = 5$$
   Hence, $k \le 5$, and every component is of even order. (Option 1 is correct).

---

### Question 3 (15 Points) — Bipartite Graphs & Double Counting [HW 03, Q5]
**Correct Answer: 2** (`|B| >= 12`).

#### Detailed Explanation:
1. In any bipartite graph $G = (A \cup B, E)$, every edge has one endpoint in $A$ and one endpoint in $B$.  
   Therefore, counting the edges from the $A$-side:
   $$|E| = \sum_{x \in A} \deg(x)$$
   Since $\deg(x) \ge 4$ for all $x \in A$ and $|A| = 15$:
   $$|E| \ge 4 \cdot |A| = 4 \cdot 15 = 60$$
2. Counting the same set of edges from the $B$-side:
   $$|E| = \sum_{y \in B} \deg(y)$$
   Since $\deg(y) \le 5$ for all $y \in B$:
   $$|E| \le 5 \cdot |B|$$
3. Combining both inequalities:
   $$5 |B| \ge |E| \ge 60 \implies 5 |B| \ge 60 \implies |B| \ge 12$$
   Hence, $|B|$ must be at least 12.

---

### Question 4 (15 Points) — Full Binary Trees & Leaves [HW 01, Q4(a)]
**Correct Answer: 2** (`l = 16 leaves, and 14 internal vertices`).

#### Detailed Explanation:
1. Let $\ell$ be the number of leaves (degree 1), and let $i$ be the number of internal vertices (degree 3).  
   The root is a single vertex of degree 2.  
   The total number of vertices is:
   $$n = 1 + i + \ell = 31 \implies i + \ell = 30$$
2. A tree on $n$ vertices has $|E| = n - 1 = 30$ edges.  
   By the Handshaking Lemma:
   $$\sum_{v \in V} \deg(v) = 2|E| \implies 2 \cdot 1 + 3i + 1\ell = 2(30) = 60$$
   $$3i + \ell = 58$$
3. Substituting $\ell = 30 - i$:
   $$3i + (30 - i) = 58 \implies 2i = 28 \implies i = 14$$
   $$\ell = 30 - 14 = 16$$
   (Alternatively, using the formula proved in HW 01 Q4a: $\ell = \frac{n+1}{2} = \frac{31+1}{2} = 16$).  
   Thus, there are $\ell = 16$ leaves and $i = 14$ internal vertices.

---

### Question 5 (15 Points) — Subsets of $\mathbb{N}$ with Infinite Components [HW 04, Q2(c)]
**Correct Answer: 2** ($\aleph = 2^{\aleph_0}$).

#### Detailed Explanation:
1. The total power set $\mathcal{P}(\mathbb{N})$ partitions into three mutually disjoint collections:
   $$\mathcal{P}(\mathbb{N}) = \mathcal{P}_{\text{fin}}(\mathbb{N}) \cup \mathcal{P}_{\text{co-fin}}(\mathbb{N}) \cup \mathcal{S}$$
   where:
   - $\mathcal{P}_{\text{fin}}(\mathbb{N}) = \{A \subseteq \mathbb{N} \mid |A| < \infty\}$ (finite subsets),
   - $\mathcal{P}_{\text{co-fin}}(\mathbb{N}) = \{A \subseteq \mathbb{N} \mid |\mathbb{N} \setminus A| < \infty\}$ (cofinite subsets),
   - $\mathcal{S}$ is the collection of subsets where both $A$ and $\mathbb{N} \setminus A$ are infinite.
2. In HW 04 Q2(c), we proved that the collection of all finite subsets of $\mathbb{N}$ is countably infinite:
   $$|\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$$
   The map $A \mapsto \mathbb{N} \setminus A$ is a bijection between $\mathcal{P}_{\text{fin}}(\mathbb{N})$ and $\mathcal{P}_{\text{co-fin}}(\mathbb{N})$, so:
   $$|\mathcal{P}_{\text{co-fin}}(\mathbb{N})| = \aleph_0$$
3. The union of the finite and cofinite subsets is countable:
   $$|\mathcal{P}_{\text{fin}}(\mathbb{N}) \cup \mathcal{P}_{\text{co-fin}}(\mathbb{N})| = \aleph_0 + \aleph_0 = \aleph_0$$
4. Since $|\mathcal{P}(\mathbb{N})| = 2^{\aleph_0} = \aleph$ and removing a countable set from a continuum-sized set preserves the continuum:
   $$|\mathcal{S}| = |\mathcal{P}(\mathbb{N}) \setminus (\mathcal{P}_{\text{fin}}(\mathbb{N}) \cup \mathcal{P}_{\text{co-fin}}(\mathbb{N}))| = \aleph$$
   Thus $|\mathcal{S}| = \aleph$.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

---

### Part 1 (12 Points) — Graph Diameter with Low Maximum Degree [HW 03, Q6 / 2026 Quiz 1, Q2]

#### Theorem:
Let $G = (V, E)$ be a connected simple graph on $n > 1$ vertices where every vertex $v \in V$ satisfies:
$$\deg(v) < \sqrt{n - 1}$$
Then $\operatorname{diam}(G) \ge 3$.

#### Formal Proof:
1. **Assumption for Contradiction:**  
   Assume for contradiction that $\operatorname{diam}(G) \le 2$.
2. **Vertex Partition by Distance:**  
   Choose an arbitrary vertex $u \in V$.  
   Since $G$ is connected and $n > 1$, for every other vertex $v \in V \setminus \{u\}$, the distance $\operatorname{dist}(u, v)$ is a finite positive integer.  
   Under our assumption that $\operatorname{diam}(G) \le 2$, every vertex in $V \setminus \{u\}$ must be at distance 1 or distance 2 from $u$:
   $$V \setminus \{u\} = N_1(u) \cup N_2(u)$$
   where:
   $$N_1(u) = \{v \in V \mid \operatorname{dist}(u, v) = 1\} = N(u)$$
   $$N_2(u) = \{v \in V \mid \operatorname{dist}(u, v) = 2\}$$
3. **Bounding $|N_1(u)|$:**  
   By definition, the number of vertices at distance 1 from $u$ is its degree:
   $$|N_1(u)| = \deg(u) < \sqrt{n - 1}$$
4. **Bounding $|N_2(u)|$:**  
   Every vertex $w \in N_2(u)$ must have at least one neighbor in $N_1(u)$.  
   For any vertex $x \in N_1(u)$, its total neighbors in $G$ is $\deg(x)$. One of its neighbors is $u \notin N_2(u)$.  
   Therefore, $x$ can have at most $\deg(x) - 1$ neighbors inside $N_2(u)$.  
   Summing over all vertices in $N_1(u)$:
   $$|N_2(u)| \le \sum_{x \in N_1(u)} (\deg(x) - 1)$$
   Using the given bound $\deg(x) < \sqrt{n - 1} \implies \deg(x) - 1 < \sqrt{n - 1} - 1$:
   $$|N_2(u)| \le |N_1(u)| \cdot (\sqrt{n - 1} - 1) < \sqrt{n - 1} \cdot (\sqrt{n - 1} - 1) = (n - 1) - \sqrt{n - 1}$$
5. **Summing the Vertices:**  
   The total number of vertices in $V \setminus \{u\}$ is $|N_1(u)| + |N_2(u)|$:
   $$|V \setminus \{u\}| = |N_1(u)| + |N_2(u)| < \sqrt{n - 1} + \Big((n - 1) - \sqrt{n - 1}\Big) = n - 1$$
   This yields:
   $$|V \setminus \{u\}| < n - 1$$
6. **Contradiction:**  
   Since $|V| = n$, the set $V \setminus \{u\}$ contains exactly $n - 1$ vertices.  
   Thus we have obtained the impossible statement:
   $$n - 1 < n - 1$$
   which is a contradiction.
7. **Conclusion:**  
   Our assumption that $\operatorname{diam}(G) \le 2$ must be false. Therefore:
   $$\operatorname{diam}(G) \ge 3 \quad \blacksquare$$

---

### Part 2 (13 Points) — Explicit Bijection $(0, 1) \sim [0, 1]$ Without CSB [HW 02, Q4(a)]

#### Theorem:
There exists an explicit bijection $f: [0, 1] \to (0, 1)$.

#### Formal Proof:
1. **Isolating an Infinite Countable Sequence (Hilbert's Hotel):**  
   We need to map the closed interval $[0, 1]$ into the open interval $(0, 1)$, absorbing the two endpoints $0$ and $1$.  
   Define the infinite sequence of points:
   $$A = \left\{0, 1, \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \dots, \frac{1}{n}, \dots\right\} \subset [0, 1]$$
   More precisely, index this sequence as $(a_0, a_1, a_2, \dots)$ where:
   $$a_0 = 0, \quad a_1 = 1, \quad a_n = \frac{1}{n} \quad (\forall n \ge 2)$$

2. **Defining the Function $f: [0, 1] \to (0, 1)$:**  
   Define $f$ piecewise by shifting the elements of $A$ forward by two positions, and leaving all other points fixed:
   $$f(x) = \begin{cases}
   \frac{1}{2} & \text{if } x = 0 \\
   \frac{1}{3} & \text{if } x = 1 \\
   \frac{1}{n+2} & \text{if } x = \frac{1}{n} \text{ for some } n \ge 2 \\
   x & \text{if } x \in [0, 1] \setminus A
   \end{cases}$$

3. **Well-Definedness ($\operatorname{Im}(f) \subseteq (0, 1)$):**
   - If $x = 0 \implies f(x) = 1/2 \in (0, 1)$.
   - If $x = 1 \implies f(x) = 1/3 \in (0, 1)$.
   - If $x = 1/n$ ($n \ge 2$) $\implies f(x) = 1/(n+2) \in (0, 1)$.
   - If $x \in [0, 1] \setminus A$: since $0 \in A$ and $1 \in A$, we have $x \ne 0$ and $x \ne 1$. Therefore $0 < x < 1$, so $f(x) = x \in (0, 1)$.  
   Thus, for every $x \in [0, 1]$, $f(x) \in (0, 1)$.

4. **Injectivity of $f$:**  
   Notice that the image of $A$ under $f$ is:
   $$f(A) = \left\{\frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \dots\right\} = A \setminus \{0, 1\} \subset A$$
   The image of $[0, 1] \setminus A$ under $f$ is:
   $$f([0, 1] \setminus A) = [0, 1] \setminus A$$
   Since $f(A) \subseteq A$ and $[0, 1] \setminus A$ is disjoint from $A$, the two images are disjoint:
   $$f(A) \cap f([0, 1] \setminus A) = \emptyset$$
   Now suppose $f(x) = f(y)$:
   - **Case 1: Both $x, y \in [0, 1] \setminus A$.** Then $x = f(x) = f(y) = y$, so $x = y$.
   - **Case 2: Both $x, y \in A$.** The map on $A$ shifts the index $k \mapsto k+2$ in the distinct sequence $(a_0, a_1, a_2, \dots)$. Since all elements in $A$ are pairwise distinct, $a_{k+2} = a_{j+2} \implies k+2 = j+2 \implies k = j \implies x = y$.
   - **Case 3: One in $A$ and one outside $A$.** Impossible, because their images lie in disjoint sets.  
   Therefore, $f$ is strictly injective.

5. **Surjectivity of $f$:**  
   Let $y \in (0, 1)$ be arbitrary. We show that there exists $x \in [0, 1]$ such that $f(x) = y$:
   - **Case 1: $y \in f(A) = \{1/2, 1/3, 1/4, \dots\}$.**  
     - If $y = 1/2$, then $f(0) = 1/2$.
     - If $y = 1/3$, then $f(1) = 1/3$.
     - If $y = 1/k$ for some $k \ge 4$, then $f(1/(k-2)) = 1/k = y$, and $1/(k-2) \in A \subset [0, 1]$.
   - **Case 2: $y \notin f(A)$.**  
     Since $y \in (0, 1)$, $y \ne 0$ and $y \ne 1$.  
     Since $y \notin f(A) = \{1/2, 1/3, \dots\}$, we also have $y \notin A$.  
     Therefore $y \in [0, 1] \setminus A$.  
     By definition, for any point in $[0, 1] \setminus A$, $f(y) = y$.  
   In all cases, every $y \in (0, 1)$ has a preimage in $[0, 1]$. Thus, $f$ is surjective.

6. **Conclusion:**  
   Since $f: [0, 1] \to (0, 1)$ is an explicit bijection, we have:
   $$[0, 1] \sim (0, 1) \quad \blacksquare$$
