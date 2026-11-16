---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 6
topic: "Regular Bipartite 1-Factorization, Hopcroft-Karp Augmenting Paths, Tutte's Condition on Trees"
problem_file: "[[Discrete Structures HW 06]]"
tags:
  - solution
  - discrete_structures
  - matchings
  - hall_theorem
  - hopcroft_karp
  - tutte_theorem
  - trees
---

# 🛡️ Discrete Structures — Homework Assignment 6 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 06|View Unsolved Assignment]]
> - **Topics Covered:** 1-Factorization Induction in Bipartite Graphs, Hopcroft-Karp Augmenting Path Bound, Double Augmentation Geometry, Tutte Parity Invariant for Trees.

---

## 📌 Solution 1: 1-Factorization of Regular Bipartite Graphs

**Theorem:** Every $k$-regular bipartite graph $G = (V, E)$ can be factored into $k$ pairwise edge-disjoint perfect matchings.

### Formal Proof (by Induction on $k$):
- **Base Case ($k = 1$):**
  Every vertex has degree $1$. Thus, every vertex is incident to exactly one edge, and no two edges share a vertex.
  The edge set $E$ is itself a perfect matching. The claim holds with $M_1 = E$.
- **Induction Hypothesis:**
  Assume that every $(k-1)$-regular bipartite graph can be decomposed into $k-1$ edge-disjoint perfect matchings.
- **Induction Step ($k$):**
  1. Let $G = (A \cup B, E)$ be a $k$-regular bipartite graph with $k \ge 2$.
  2. By the Handshaking Lemma on bipartite graphs, $k|A| = |E| = k|B| \implies |A| = |B|$.
  3. We verify **Hall's Marriage Condition** for $G$:
     Let $S \subseteq A$ be any non-empty subset.
     - The number of edges leaving $S$ is $k|S|$.
     - All these edges enter the neighborhood set $N(S) \subseteq B$.
     - Since each vertex in $N(S)$ has degree $k$, the maximum number of edges entering $N(S)$ is $k|N(S)|$.
     - Therefore:
       $$k|S| = e(S, N(S)) \le \sum_{y \in N(S)} \deg(y) = k|N(S)|$$
     - Dividing by $k > 0$ yields:
       $$|N(S)| \ge |S|$$
  4. By Hall's Marriage Theorem, $G$ contains a matching covering all vertices of $A$. Since $|A| = |B|$, this matching is a **perfect matching**, which we denote $M_k$.
  5. Consider the remaining graph:
     $$G' = (V, E \setminus M_k)$$
     - In $G'$, every vertex $v \in V$ loses exactly one incident edge (the edge belonging to $M_k$).
     - Thus, for every $v \in V$:
       $$\deg_{G'}(v) = k - 1$$
     - Furthermore, $G'$ remains bipartite.
  6. By the induction hypothesis, $G'$ can be decomposed into $k - 1$ edge-disjoint perfect matchings:
     $$E(G') = M_1 \;\dot\cup\; M_2 \;\dot\cup\; \dots \;\dot\cup\; M_{k-1}$$
  7. Since $M_k$ was disjoint from $E(G')$, the full set of $k$ matchings:
     $$E = M_1 \;\dot\cup\; M_2 \;\dot\cup\; \dots \;\dot\cup\; M_{k-1} \;\dot\cup\; M_k$$
     forms an edge-disjoint decomposition of $G$ into $k$ perfect matchings. $\blacksquare$

---

## 📌 Solution 2: Short Augmenting Paths in Hopcroft-Karp

**Problem:** Let $M$ be a matching and $M^*$ a maximum matching with $|M^*| = k$. Prove that if $|M| < k - \sqrt{k}$, there exists an $M$-augmenting path of length $\le 2\sqrt{k} - 1$.

### Formal Proof:
1. Consider the symmetric difference graph:
   $$H = G[M \oplus M^*]$$
   where $M \oplus M^* = (M \setminus M^*) \cup (M^* \setminus M)$.
2. As established in Berge's theorem, every connected component of $H$ is one of the following:
   - An isolated vertex.
   - An even alternating cycle (with equal edges from $M$ and $M^*$).
   - An alternating path of even length (with equal edges from $M$ and $M^*$).
   - An alternating path of odd length with more edges from $M^*$ than $M$ (an **$M$-augmenting path**).
   - An alternating path of odd length with more edges from $M$ than $M^*$ (an $M^*$-augmenting path; impossible since $M^*$ is maximum).
3. Let $p$ be the number of $M$-augmenting paths in $H$. Each such path contains exactly one more edge from $M^*$ than from $M$. Every other component contains an equal number of edges from $M$ and $M^*$.
   Therefore:
   $$|M^*| - |M| = p$$
   Since $|M| < k - \sqrt{k}$, the number of vertex-disjoint $M$-augmenting paths satisfies:
   $$p = k - |M| > k - (k - \sqrt{k}) = \sqrt{k}$$
4. Let $P_1, P_2, \dots, P_p$ denote these $p$ vertex-disjoint $M$-augmenting paths in $H$.
5. The total number of edges in $H$ is bounded by:
   $$|E(H)| = |M \oplus M^*| \le |M| + |M^*| = |M| + k$$
6. Since the paths $P_1, \dots, P_p$ are edge-disjoint subgraphs of $H$:
   $$\sum_{i=1}^p |E(P_i)| \le |E(H)| \le |M| + k$$
7. Now, assume for contradiction that **every** $M$-augmenting path has length strictly greater than $2\sqrt{k} - 1$.
   Since augmenting paths have odd length, this means:
   $$|E(P_i)| \ge 2\sqrt{k} \quad \forall i \in \{1, \dots, p\}$$
8. Summing the lengths of all $p$ paths:
   $$\sum_{i=1}^p |E(P_i)| > p \cdot (2\sqrt{k} - 1) > \sqrt{k} \cdot (2\sqrt{k} - 1) = 2k - \sqrt{k}$$
9. Combining the upper and lower bounds:
   $$2k - \sqrt{k} < \sum_{i=1}^p |E(P_i)| \le |M| + k$$
   Rearranging:
   $$|M| > 2k - \sqrt{k} - k = k - \sqrt{k}$$
10. This directly contradicts the given condition $|M| < k - \sqrt{k}$!
11. Therefore, our assumption was false: there must exist at least one $M$-augmenting path $P^*$ with:
    $$|E(P^*)| \le 2\sqrt{k} - 1$$
    $\blacksquare$

---

## 📌 Solution 3: Augmenting Path Length Dynamics

### Part (a): Disjoint Augmenting Paths in $N \oplus M$
- **Proof:**
  1. Let $M' = M \oplus E(P)$. Since $P$ is an $M$-augmenting path, $|M'| = |M| + 1$.
  2. Let $N = M' \oplus E(P') = M \oplus E(P) \oplus E(P')$. Since $P'$ is an $M'$-augmenting path, $|N| = |M'| + 1 = |M| + 2$.
  3. Now consider the symmetric difference graph $G' = (V, N \oplus M)$.
  4. Both $N$ and $M$ are matchings in $G$. Thus, the connected components of $G'$ are paths and cycles.
  5. The difference in size between the two matchings is:
     $$|N| - |M| = 2$$
  6. Each alternating path in $N \oplus M$ that has more edges in $N$ than in $M$ is an **$M$-augmenting path** and contributes $+1$ to $|N| - |M|$.
  7. All other components (cycles, even paths) contribute $0$, and any path with more edges in $M$ contributes $-1$.
  8. Therefore, $G'$ must contain at least:
     $$|N| - |M| = 2$$
     vertex-disjoint $M$-augmenting paths. $\blacksquare$

---

### Part (b): Length Inequality $|E(P')| \ge |E(P)| + 2|E(P) \cap E(P')|$
- **Proof:**
  1. Let $P_1, P_2$ be two vertex-disjoint $M$-augmenting paths in $G'$ from Part (a).
  2. Since $P$ is a **shortest** $M$-augmenting path in $G$:
     $$|E(P_1)| \ge |E(P)| \quad \text{and} \quad |E(P_2)| \ge |E(P)|$$
  3. Since $P_1$ and $P_2$ are edge-disjoint subgraphs of $G' = (V, N \oplus M)$:
     $$|E(G')| \ge |E(P_1)| + |E(P_2)| \ge 2|E(P)|$$
  4. On the other hand, $N = M \oplus E(P) \oplus E(P')$, so:
     $$N \oplus M = \big(M \oplus E(P) \oplus E(P')\big) \oplus M = E(P) \oplus E(P')$$
  5. The size of the symmetric difference of two sets is:
     $$|E(P) \oplus E(P')| = |E(P)| + |E(P')| - 2|E(P) \cap E(P')|$$
  6. Substituting this into the inequality from step 3:
     $$|E(P)| + |E(P')| - 2|E(P) \cap E(P')| \ge 2|E(P)|$$
  7. Rearranging terms:
     $$|E(P')| \ge |E(P)| + 2|E(P) \cap E(P')|$$
     $\blacksquare$

---

## 📌 Solution 4: Characterization of Perfect Matchings in Trees

**Theorem:** A tree $T = (V, E)$ has a perfect matching $\iff \forall v \in V, \; o(T \setminus \{v\}) = 1$.

### Proof $(\implies)$:
1. Suppose $T$ contains a perfect matching $M$.
2. By **Tutte's Theorem**, for any subset $S \subseteq V$:
   $$o(T \setminus S) \le |S|$$
   In particular, setting $S = \{v\}$ for any $v \in V$:
   $$o(T \setminus \{v\}) \le |\{v\}| = 1$$
3. Since $T$ has a perfect matching, $|V|$ must be **even**.
4. When we remove a single vertex $v$, the remaining graph $T \setminus \{v\}$ has $|V| - 1$ vertices, which is **odd**.
5. The sum of the number of vertices across all connected components of $T \setminus \{v\}$ is odd.
   An odd number cannot be partitioned entirely into even components. Therefore, $T \setminus \{v\}$ must contain at least one odd component:
   $$o(T \setminus \{v\}) \ge 1$$
6. Combining $o(T \setminus \{v\}) \le 1$ and $o(T \setminus \{v\}) \ge 1$, we obtain:
   $$o(T \setminus \{v\}) = 1 \quad \forall v \in V$$

---

### Proof $(\impliedby)$:
1. Suppose $\forall v \in V, \; o(T \setminus \{v\}) = 1$.
2. **Parity of $|V|$:**
   - If $|V| = 1$, $T \setminus \{v\} = \emptyset$, so $o(T \setminus \{v\}) = 0 \ne 1$, contradiction.
   - If $|V| \ge 3$ and odd, let $v$ be a leaf. Then $T \setminus \{v\}$ is a connected tree on an even number of vertices, so $o(T \setminus \{v\}) = 0 \ne 1$, contradiction.
   - Thus, $|V| = n$ must be **even** and $n \ge 2$.
3. We proceed by **induction on even $n = |V|$**:
   - **Base Case ($n = 2$):** $T = K_2$, which has a unique perfect matching (its single edge).
   - **Inductive Step ($n \ge 4$):**
     1. In any tree on $n \ge 4$ vertices, there exists a leaf $v$ (degree 1). Let $u$ be the unique neighbor of $v$.
     2. Can $u$ have another neighbor $w$ that is also a leaf?
        If so, in $T \setminus \{u\}$, both $\{v\}$ and $\{w\}$ would be isolated vertices (odd components of size 1), which would imply $o(T \setminus \{u\}) \ge 2$, contradicting our condition $o(T \setminus \{u\}) = 1$.
        Thus, $v$ is the **unique** leaf neighbor of $u$.
     3. Consider $T \setminus \{u\}$. By assumption, $o(T \setminus \{u\}) = 1$.
        Since $\{v\}$ is an isolated vertex of size 1, $\{v\}$ is the unique odd component of $T \setminus \{u\}$!
        All other components of $T \setminus \{u\}$ must have **even** size.
     4. Now remove both $u$ and $v$ from $T$:
        $$T' = T \setminus \{u, v\}$$
        The connected components of $T'$ are precisely the other components of $T \setminus \{u\}$.
        Let these components be $C_1, C_2, \dots, C_k$.
        Each $C_i$ is a tree with an even number of vertices, and $|V(C_i)| \le n - 2$.
     5. For each component $C_i$ and any vertex $x \in V(C_i)$, removing $x$ from $C_i$ yields:
        $$o(C_i \setminus \{x\}) = 1$$
        (because $u, v$ form an even block of 2 vertices connected to $C_i$, so the component parity inside $C_i$ is unchanged).
     6. By the induction hypothesis, each component $C_i$ has a perfect matching $M_i$.
     7. The union:
        $$M = \{ \{u, v\} \} \cup M_1 \cup M_2 \cup \dots \cup M_k$$
        is a valid perfect matching for $T$.
   This completes the induction. $\blacksquare$
