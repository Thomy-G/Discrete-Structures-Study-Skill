---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 6
topic: "Regular Bipartite 1-Factorization, Hopcroft-Karp Augmenting Paths, Tutte's Condition on Trees"
status: "To Solve"
solution_file: "[[Discrete Structures HW 06 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - matchings
  - hall_theorem
  - hopcroft_karp
  - tutte_theorem
  - trees
---

# 📝 Discrete Structures — Homework Assignment 6

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** 1-Factorization of $k$-Regular Bipartite Graphs, Short Augmenting Paths in Hopcroft-Karp, Augmenting Path Length Invariants, Single-Vertex Tutte Condition for Trees.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 06 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: 1-Factorization of Regular Bipartite Graphs

Let $G = (V, E)$ be a $k$-regular bipartite graph with $k \ge 1$.
**Prove** that $G$ can be decomposed into $k$ pairwise edge-disjoint **perfect matchings** (1-factors):
$$E = M_1 \;\dot\cup\; M_2 \;\dot\cup\; \dots \;\dot\cup\; M_k$$

> [!tip]- 💡 Hints & Strategy
> - Use induction on $k$.
> - For the base case $k = 1$: Every vertex has degree 1, so $E$ is already a perfect matching.
> - For the induction step: Every regular bipartite graph satisfies Hall's Marriage Condition, hence contains at least one perfect matching $M$. What happens to the degrees of the vertices in $G \setminus M$?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Short Augmenting Paths in Hopcroft-Karp

Let $G = (V, E)$ be a graph, let $M$ be an arbitrary matching in $G$, and let $M^*$ be a maximum matching in $G$ with $|M^*| = k$.
**Prove** that if:
$$|M| < k - \sqrt{k}$$
then there exists an $M$-augmenting path of length at most:
$$2\sqrt{k} - 1$$

> [!tip]- 💡 Hints & Strategy
> - Consider the symmetric difference graph $H = G[M \oplus M^*]$.
> - Recall the structural properties of $M \oplus M^*$: all connected components are alternating paths and even alternating cycles.
> - How many vertex-disjoint $M$-augmenting paths must exist in $M \oplus M^*$? (Recall: exactly $|M^*| - |M| > \sqrt{k}$).
> - What is the total number of edges in $M \oplus M^*$? If every augmenting path had length $> 2\sqrt{k} - 1$, derive a contradiction on the total edge count.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Augmenting Path Length Dynamics

Let $G = (V, E)$ be a graph and let $M$ be a non-maximum matching.
Let $P$ be a **shortest** $M$-augmenting path, and let $P'$ be an $M'$-augmenting path with respect to the augmented matching $M' = M \oplus E(P)$.

### Part (a): Disjoint Augmenting Paths in $N \oplus M$
Consider the matching $N = M \oplus E(P) \oplus E(P')$.
**Show** that the subgraph $G' = (V, N \oplus M)$ contains at least two vertex-disjoint $M$-augmenting paths.

### Part (b): Length Lower Bound on $P'$
**Conclude** that:
$$|E(P')| \ge |E(P)| + 2|E(P) \cap E(P')|$$

> [!tip]- 💡 Hints & Strategy
> - For (a): Note that $|N| = |M| + 2$. By the symmetric difference decomposition theorem, $N \oplus M$ must contain at least $|N| - |M| = 2$ vertex-disjoint $M$-augmenting paths $P_1, P_2$.
> - For (b): Since $P$ was a shortest $M$-augmenting path, both $|E(P_1)| \ge |E(P)|$ and $|E(P_2)| \ge |E(P)|$. Sum their lengths and relate to $|E(P) \oplus E(P')|$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Characterization of Perfect Matchings in Trees

Let $T = (V, E)$ be a tree.
**Prove** that $T$ contains a **perfect matching** if and only if for every vertex $v \in V$, deleting $v$ leaves exactly one odd connected component:
$$\forall v \in V, \quad o(T \setminus \{v\}) = 1$$
*(where $o(H)$ denotes the number of connected components of $H$ having an odd number of vertices).*

> [!tip]- 💡 Hints & Strategy
> - $(\implies)$ If $T$ has a perfect matching, Tutte's Theorem gives $o(T \setminus \{v\}) \le |\{v\}| = 1$. Why can't it be $0$? (Consider the parity of $|V|$).
> - $(\impliedby)$ Prove by induction on even $|V| = n$. Pick a leaf $v$ with unique neighbor $u$. Show that $u$ can have no other leaf neighbors, that deleting $\{u, v\}$ leaves only even components, and that each component satisfies the condition.

> [!quote]- ✍️ Solution Workspace
> 
