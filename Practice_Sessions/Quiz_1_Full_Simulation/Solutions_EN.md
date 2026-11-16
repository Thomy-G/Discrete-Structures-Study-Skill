# Full Solutions — Quiz 1 Simulation (2026/2027 Format)
**Course:** Discrete Structures (89-2197) — Dr. Arnold Filtser  
**Topics Covered:** Lectures 1–4, Recitations 1–4, Homework 1–4  
**Max Score:** 100 Points (Part A: 75 Points, Part B: 25 Points)

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Posets, Minimal/Maximal Elements
**Correct Answer: 2** (`|M| = 6, |m| = 6, and there is neither a maximum nor a minimum in F`).

#### Detailed Explanation:
1. **Definition of the Poset:**  
   The ground set is $\mathcal{F} = \mathcal{P}(A) \setminus \{\emptyset, A\}$ where $A = \{1, 2, 3, 4, 5, 6\}$, ordered by standard subset inclusion $\subseteq$.  
   Therefore, $\mathcal{F}$ contains all proper, non-empty subsets of $A$, meaning all subsets $X \subseteq A$ with sizes $1 \le |X| \le 5$.
2. **Minimal Elements ($m$):**  
   An element $X \in \mathcal{F}$ is minimal if there is no $Y \in \mathcal{F}$ strictly contained in $X$ ($Y \subsetneq X$).  
   Since $\emptyset \notin \mathcal{F}$, the smallest possible subsets are the singletons $\{x\}$ for $x \in A$.  
   There are $\binom{6}{1} = 6$ such singletons: $\{1\}, \{2\}, \{3\}, \{4\}, \{5\}, \{6\}$.  
   None of these contains another element in $\mathcal{F}$, so $|m| = 6$.
3. **Maximal Elements ($M$):**  
   An element $Y \in \mathcal{F}$ is maximal if there is no $Z \in \mathcal{F}$ strictly containing $Y$ ($Y \subsetneq Z$).  
   Since $A \notin \mathcal{F}$, the largest possible subsets are those containing exactly 5 elements (of the form $A \setminus \{x\}$).  
   There are $\binom{6}{5} = 6$ such subsets.  
   None of these is contained in any other element of $\mathcal{F}$, so $|M| = 6$.
4. **Minimum / Maximum Elements:**  
   In any poset, if a minimum (or maximum) exists, it must be the **unique** minimal (or maximal) element.  
   Since there are $6 > 1$ minimal elements and $6 > 1$ maximal elements, neither a minimum nor a maximum exists in $\mathcal{F}$.

---

### Question 2 (15 Points) — Graph Diameter of the Complement Graph
**Correct Answer: 2** ($\operatorname{diam}(\overline{G}) = 2$).

#### Detailed Explanation:
1. **General Bound for Disconnected Graphs (HW 02, Q1):**  
   For any disconnected simple graph $G = (V, E)$, the complement graph $\overline{G}$ is connected, and its diameter satisfies:
   $$\operatorname{diam}(\overline{G}) \le 2$$
   - Any two vertices $x, y$ in different connected components of $G$ have no edge between them in $G$, so $\{x, y\} \in E(\overline{G})$, which means $\operatorname{dist}_{\overline{G}}(x, y) = 1$.
   - Any two vertices $x, y$ in the same connected component of $G$ can be connected via any third vertex $z$ belonging to another component of $G$ (as $\{x, z\} \in E(\overline{G})$ and $\{z, y\} \in E(\overline{G})$), which gives a path $x - z - y$ of length 2 in $\overline{G}$. Thus, $\operatorname{dist}_{\overline{G}}(x, y) \le 2$.
2. **Ruling out $\operatorname{diam}(\overline{G}) = 1$:**  
   A graph has diameter 1 if and only if every pair of distinct vertices is adjacent (i.e., it is the complete graph $K_n$).  
   Here, $G$ has two components $C_1$ (size 4) and $C_2$ (size 6). In particular, component $C_1$ has at least one edge (in fact, we are given $\deg_G(u) = 2$ for some $u \in V(C_1)$, so $u$ has a neighbor $v \in V(C_1)$ with $\{u, v\} \in E(G)$).  
   Since $\{u, v\} \in E(G)$, the edge $\{u, v\}$ is **missing** from $\overline{G}$.  
   Hence, $\operatorname{dist}_{\overline{G}}(u, v) \ne 1$. Combined with $\operatorname{dist}_{\overline{G}}(u, v) \le 2$, we strictly have $\operatorname{dist}_{\overline{G}}(u, v) = 2$.  
   Therefore, $\operatorname{diam}(\overline{G}) = 2$.

---

### Question 3 (15 Points) — Handshaking in Trees & Bipartite Bounds
**Correct Answer: 1** (`There are exactly 13 leaves in T; it can be guaranteed that for every such tree max(|A|, |B|) >= 13`).

#### Detailed Explanation:
1. **Finding the Number of Leaves $k$:**  
   Let $k$ denote the number of leaves (vertices of degree 1).  
   The given degree distribution is:
   - 4 vertices of degree 4
   - 3 vertices of degree 3
   - 5 vertices of degree 2
   - $k$ vertices of degree 1
   
   The total number of vertices is:
   $$n = |V| = 4 + 3 + 5 + k = 12 + k$$
   In any tree, the number of edges is $|E| = n - 1 = 11 + k$.  
   Applying the Handshaking Lemma ($\sum_{v \in V} \deg(v) = 2|E|$):
   $$4(4) + 3(3) + 5(2) + 1(k) = 2(11 + k)$$
   $$16 + 9 + 10 + k = 22 + 2k$$
   $$35 + k = 22 + 2k \implies k = 13$$
   Hence, the tree has exactly **13 leaves**.
2. **Bipartite Partition Bound:**  
   The total vertex count is $n = 12 + 13 = 25$.  
   Since every tree is acyclic, it contains no odd cycles, and thus every tree is a bipartite graph ($V = A \cup B$ where $A \cap B = \emptyset$).  
   Because $|A| + |B| = 25$, by the Pigeonhole Principle:
   $$\max(|A|, |B|) \ge \left\lceil \frac{25}{2} \right\rceil = 13$$
   This matches Option 1.

---

### Question 4 (15 Points) — Countable vs. Uncountable Sets
**Correct Answer: 3** (`A is countably infinite, B is uncountable`).

#### Detailed Explanation:
1. **Cardinality of Set $A$:**  
   $$A = \{S \subseteq \mathbb{N} \mid \mathbb{N} \setminus S \text{ is finite}\}$$
   Every set $S \in A$ is uniquely determined by its complement $F = \mathbb{N} \setminus S$, which is a finite subset of $\mathbb{N}$.  
   Consider the mapping $\phi: A \to \mathcal{P}_{\text{fin}}(\mathbb{N})$ defined by $\phi(S) = \mathbb{N} \setminus S$.  
   - $\phi$ is well-defined because $\mathbb{N} \setminus S$ is finite by definition of $A$.  
   - $\phi$ is a bijection, with inverse $\phi^{-1}(F) = \mathbb{N} \setminus F$.  
   As proved in HW 04 (Q2c), the set of all finite subsets of $\mathbb{N}$, $\mathcal{P}_{\text{fin}}(\mathbb{N}) = \bigcup_{k=0}^\infty \mathcal{P}_k(\mathbb{N})$, is a countable union of countable sets, and hence countably infinite ($|\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$).  
   Therefore, $|A| = |\mathcal{P}_{\text{fin}}(\mathbb{N})| = \aleph_0$ (**countably infinite**).
2. **Cardinality of Set $B$:**  
   $$B = \{f: \mathbb{N} \to \mathbb{N} \mid \forall n \in \mathbb{N} : f(n) \le f(n+1)\}$$
   - Clearly $B \subseteq \mathbb{N}^\mathbb{N}$, so $|B| \le |\mathbb{N}^\mathbb{N}| = \aleph_0^{\aleph_0} = 2^{\aleph_0} = \aleph$.  
   - To show $\aleph \le |B|$, construct an injection from $\{0, 1\}^\mathbb{N}$ (the set of infinite binary sequences, which has cardinality $\aleph$) into $B$.  
     For any binary sequence $b = (b_0, b_1, b_2, \dots) \in \{0, 1\}^\mathbb{N}$, define the sequence of partial sums:
     $$f_b(n) = \sum_{i=0}^n b_i$$
     Since each $b_i \in \{0, 1\} \ge 0$, we have $f_b(n+1) = f_b(n) + b_{n+1} \ge f_b(n)$, so $f_b \in B$.  
     Moreover, if $b \ne b'$, let $k$ be the minimal index where $b_k \ne b'_k$. Then $f_b(k) \ne f_{b'}(k)$, so $f_b \ne f_{b'}$. The mapping $b \mapsto f_b$ is strictly injective.  
   By the Cantor-Schröder-Bernstein (CSB) Theorem, $|B| = \aleph$ (**uncountable**).

---

### Question 5 (15 Points) — Cardinality via Involution Functions
**Correct Answer: 3** ($2^{\aleph_0}$).

#### Detailed Explanation:
1. **Definition of Set $A$:**  
   $$A = \{f: \mathbb{N} \to \mathbb{N} \mid \forall n \in \mathbb{N} : f(f(n)) = n\}$$
   These are all permutations of $\mathbb{N}$ that are involutions (their cycle decomposition consists entirely of fixed points and 2-cycles).
2. **Upper Bound ($|A| \le 2^{\aleph_0}$):**  
   Every function in $A$ is a function from $\mathbb{N}$ to $\mathbb{N}$, so:
   $$|A| \le |\mathbb{N}^\mathbb{N}| = \aleph_0^{\aleph_0} = 2^{\aleph_0}$$
3. **Lower Bound ($2^{\aleph_0} \le |A|$):**  
   Partition $\mathbb{N}$ into infinitely many disjoint adjacent pairs:
   $$\{0, 1\}, \{2, 3\}, \{4, 5\}, \dots, \{2k, 2k+1\}, \dots$$
   For any subset $S \subseteq \mathbb{N}$, define a function $f_S: \mathbb{N} \to \mathbb{N}$ by choosing whether to swap each pair or leave it fixed:
   $$f_S(2k) = \begin{cases} 2k+1 & \text{if } k \in S \\ 2k & \text{if } k \notin S \end{cases}, \qquad f_S(2k+1) = \begin{cases} 2k & \text{if } k \in S \\ 2k+1 & \text{if } k \notin S \end{cases}$$
   - **Well-defined in $A$:** For every $k \in \mathbb{N}$, if $k \notin S$, both $2k$ and $2k+1$ are fixed points; if $k \in S$, $f_S$ transposes $2k \leftrightarrow 2k+1$. In either case, applying $f_S$ twice yields $f_S(f_S(n)) = n$ for all $n \in \mathbb{N}$. Thus $f_S \in A$.
   - **Injective:** If $S_1 \ne S_2$, there exists an index $k$ in their symmetric difference $S_1 \Delta S_2$. Without loss of generality, let $k \in S_1 \setminus S_2$. Then $f_{S_1}(2k) = 2k+1 \ne 2k = f_{S_2}(2k)$, so $f_{S_1} \ne f_{S_2}$.  
   This establishes an explicit injection $\mathcal{P}(\mathbb{N}) \to A$, so:
   $$2^{\aleph_0} = |\mathcal{P}(\mathbb{N})| \le |A|$$
4. **Conclusion by CSB:**  
   Since $2^{\aleph_0} \le |A| \le 2^{\aleph_0}$, by CSB we have $|A| = 2^{\aleph_0} = \aleph$.

---

## Part B: Open Proof Question (25 Points) — Based on HW 01–04

### Question 6 (25 Points)

---

### Part 1 (12 Points): Proving That $k$-Regular Bipartite Graphs ($k \ge 2$) Have No Bridges (HW 03, Q7)

#### Theorem:
For any integer $k \ge 2$, every $k$-regular bipartite graph contains **no bridges** (cut-edges).

#### Formal Proof:
1. Let $G = (V = L \cup R, E)$ be a $k$-regular bipartite graph with bipartition $(L, R)$ and $k \ge 2$.
2. Assume for contradiction that there exists an edge $e = \{u, v\} \in E$ that is a **bridge** in $G$.  
   Since $G$ is bipartite, its vertices are partitioned into $L$ and $R$. Without loss of generality, assume $u \in L$ and $v \in R$.
3. By definition of a bridge, removing $e$ splits the connected component of $G$ containing $e$ into two separate connected components in $G \setminus \{e\}$.  
   Let $C$ denote the connected component of $G \setminus \{e\}$ that contains vertex $u$ (which does not contain $v$, since otherwise $u$ and $v$ would still be connected in $G \setminus \{e\}$, contradicting the fact that $e$ is a bridge).
4. Define the vertex sets of component $C$ on each side of the bipartition:
   $$L_C = V(C) \cap L, \qquad R_C = V(C) \cap R$$
   Since $G$ is bipartite and no edges exist between $C$ and the rest of the graph in $G \setminus \{e\}$, the subgraph induced by $V(C)$ in $G \setminus \{e\}$ is itself a bipartite graph with bipartition $(L_C, R_C)$.
5. Let us determine the degrees of vertices within $C$ (in the graph $G \setminus \{e\}$):
   - Vertex $u \in L_C$ lost exactly one incident edge ($e = \{u, v\}$ to $v \notin V(C)$). Since its degree in $G$ was $k$, its degree in $C$ is:
     $$\deg_C(u) = k - 1$$
   - For every other vertex $x \in L_C \setminus \{u\}$, none of its incident edges was removed (the only removed edge was $e=\{u, v\}$). Furthermore, since $C$ is a connected component of $G \setminus \{e\}$, all $k$ of $x$'s neighbors in $G$ must belong to $R_C$. Thus:
     $$\deg_C(x) = k \quad (\forall x \in L_C \setminus \{u\})$$
   - For every vertex $y \in R_C$, since $v \notin R_C$, none of $y$'s incident edges was removed, and all $k$ of its neighbors must lie in $L_C$. Thus:
     $$\deg_C(y) = k \quad (\forall y \in R_C)$$
6. We now count the total number of edges $|E(C)|$ in the bipartite graph $C$ by summing degrees on both sides:
   - Summing degrees in $L_C$:
     $$\sum_{x \in L_C} \deg_C(x) = \deg_C(u) + \sum_{x \in L_C \setminus \{u\}} \deg_C(x) = (k - 1) + (|L_C| - 1)k = |L_C| \cdot k - 1$$
   - Summing degrees in $R_C$:
     $$\sum_{y \in R_C} \deg_C(y) = |R_C| \cdot k$$
7. In any bipartite graph, the sum of degrees in one part equals the sum of degrees in the other part (both equal the total number of edges). Equating the two sums:
   $$|L_C| \cdot k - 1 = |R_C| \cdot k \implies (|L_C| - |R_C|) \cdot k = 1$$
8. Since $|L_C|$ and $|R_C|$ are non-negative integers, their difference $(|L_C| - |R_C|)$ is an integer.  
   Therefore, $k$ must be a positive integer divisor of $1$, which forces:
   $$k = 1$$
   This directly contradicts the given condition that $k \ge 2$!
9. Consequently, our assumption that $G$ contains a bridge was false. Every $k$-regular bipartite graph with $k \ge 2$ has no bridges. $\blacksquare$

---

### Part 2 (13 Points): Cardinality of $101$-Free Binary Sequences (HW 03, Q1)

#### Problem:
Let $A$ be the set of all infinite binary sequences $f: \mathbb{N} \to \{0, 1\}$ that do not contain the substring $101$:
$$A = \left\{ f \in \{0, 1\}^\mathbb{N} \;\middle|\; \forall n \in \mathbb{N}: \Big(f(n) = 1 \land f(n+1) = 0 \implies f(n+2) = 0\Big) \right\}$$
Calculate $|A|$ and provide a complete formal proof.

#### Formal Proof:
**Claim:** The cardinality of $A$ is the continuum: $|A| = 2^{\aleph_0} = \aleph$.  
We prove this using the Cantor-Schröder-Bernstein (CSB) Theorem:

1. **Upper Bound ($|A| \le \aleph$):**  
   By definition, $A \subseteq \{0, 1\}^\mathbb{N}$.  
   The inclusion map $i: A \to \{0, 1\}^\mathbb{N}$ defined by $i(f) = f$ is trivially injective.  
   Since $|\{0, 1\}^\mathbb{N}| = 2^{\aleph_0} = \aleph$, we obtain:
   $$|A| \le \aleph$$
2. **Lower Bound ($\aleph \le |A|$):**  
   We construct an explicit injection $\Phi: \{0, 1\}^\mathbb{N} \to A$.  
   For any infinite binary sequence $g = (g_0, g_1, g_2, \dots) \in \{0, 1\}^\mathbb{N}$, we construct a new sequence $f_g = \Phi(g)$ by duplicating each bit: replacing $0 \mapsto 00$ and $1 \mapsto 11$.  
   Formally, for every $k \in \mathbb{N}$:
   $$f_g(2k) = g(k), \qquad f_g(2k+1) = g(k)$$
   - **Proof that $\Phi$ is well-defined ($\operatorname{Im}(\Phi) \subseteq A$):**  
     We must show that for any sequence $g$, $f_g$ never contains the substring $101$.  
     Assume for contradiction that there exists an index $n \in \mathbb{N}$ such that:
     $$f_g(n) = 1, \quad f_g(n+1) = 0, \quad f_g(n+2) = 1$$
     We analyze the parity of the index $n$:
     - **Case 1: $n$ is even ($n = 2k$).**  
       Then by definition, $f_g(2k) = g(k)$ and $f_g(2k+1) = g(k)$, which implies $f_g(n) = f_g(n+1)$.  
       However, $f_g(n) = 1 \ne 0 = f_g(n+1)$, a contradiction.
     - **Case 2: $n$ is odd ($n = 2k+1$).**  
       Then $n+1 = 2(k+1)$ and $n+2 = 2(k+1)+1$.  
       By definition, $f_g(2(k+1)) = g(k+1)$ and $f_g(2(k+1)+1) = g(k+1)$, which implies $f_g(n+1) = f_g(n+2)$.  
       However, $f_g(n+1) = 0 \ne 1 = f_g(n+2)$, a contradiction.  
     In both cases, we reach a contradiction. Therefore, $f_g$ contains no $101$ substring, so $f_g \in A$.
   - **Proof that $\Phi$ is injective:**  
     Let $g_1, g_2 \in \{0, 1\}^\mathbb{N}$ such that $\Phi(g_1) = \Phi(g_2)$, meaning $f_{g_1} = f_{g_2}$.  
     Then for every $k \in \mathbb{N}$, looking at the even indices:
     $$g_1(k) = f_{g_1}(2k) = f_{g_2}(2k) = g_2(k)$$
     Since $g_1(k) = g_2(k)$ for all $k \in \mathbb{N}$, we have $g_1 = g_2$.  
     Hence, $\Phi$ is an injection, which proves:
     $$\aleph = |\{0, 1\}^\mathbb{N}| \le |A|$$
3. **Conclusion by Cantor-Schröder-Bernstein:**  
   Since $|A| \le \aleph$ and $\aleph \le |A|$, by the CSB theorem:
   $$|A| = \aleph = 2^{\aleph_0} \quad \blacksquare$$
