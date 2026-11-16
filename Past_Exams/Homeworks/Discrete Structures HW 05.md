---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 5
topic: "Directed Eulerian Circuits, Matching Unions, Dirac's Theorem, Ore's Theorem, Graph Cartesian Products"
status: "To Solve"
solution_file: "[[Discrete Structures HW 05 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - eulerian_circuits
  - hamiltonian_cycles
  - matchings
  - dirac_theorem
  - cartesian_product
---

# 📝 Discrete Structures — Homework Assignment 5

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Directed Eulerian Circuits (In-degree = Out-degree), Union of Two Matchings is Bipartite, Cyclic Ordering via Dirac's Theorem, Edge Density Forcing Hamiltonian Cycles (Ore's Theorem), Cartesian Products of Graphs ($G \square H$).
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 05 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- Unless stated otherwise, all graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Directed Eulerian Circuits in Pseudo-Graphs

Let $D = (V, E)$ be a finite, strongly connected directed pseudo-graph (loops and multiple directed edges allowed).
**Prove** that $D$ contains an **Eulerian circuit** (a closed directed walk that traverses every directed edge in $E$ exactly once) if and only if for every vertex $v \in V$, the in-degree equals the out-degree:
$$\operatorname{deg}_{\text{in}}(v) = \operatorname{deg}_{\text{out}}(v) \quad \forall v \in V$$

> [!tip]- 💡 Hints & Strategy
> - $(\implies)$ Every time an Eulerian walk enters a vertex along an in-edge, it must leave along an out-edge.
> - $(\impliedby)$ Adapt the standard undirected algorithm (Euler/Hierholzer): start a directed walk; since in-degree = out-degree, you can never get stuck until returning to the start, forming a simple directed cycle $C$. Remove $E(C)$ and apply induction or splice cycles together using strong connectivity.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: The Union of Two Matchings is Bipartite

Let $G = (V, E)$ be an undirected graph, and let $M_1, M_2 \subseteq E$ be two matchings in $G$.
Consider the subgraph formed by the union of both matchings:
$$G' = (V, M_1 \cup M_2)$$
**Prove** that $G'$ is a **bipartite graph**.

> [!tip]- 💡 Hints & Strategy
> - Recall König's theorem: A graph is bipartite $\iff$ it contains no odd cycles.
> - What is the maximum degree of any vertex in $G'$? Since each vertex is incident to at most one edge from $M_1$ and at most one edge from $M_2$, $\deg_{G'}(v) \le 2$.
> - What do the connected components of a graph with maximum degree $\le 2$ look like? If there is a cycle, how do the edges alternate between $M_1$ and $M_2$?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Cyclic Ordering via Dirac's Theorem

Let $A = \{1, 2, \dots, 165\}$. Define a binary relation $R$ on $A$ by:
$$a R b \iff a \equiv b \pmod 3 \;\lor\; a \equiv b \pmod 5 \;\lor\; a \equiv b \pmod{11}$$
**Prove** that the elements of $A$ can be arranged in a circular sequence $(a_1, a_2, \dots, a_{165})$ such that:
$$a_i R a_{i+1} \quad \forall 1 \le i < 165, \quad \text{and} \quad a_{165} R a_1$$

> [!tip]- 💡 Hints & Strategy
> - Model this as a graph problem: Let $V = A$, and put an edge between $a \ne b$ if and only if $a R b$.
> - What does a circular sequence visiting each vertex exactly once correspond to in graph theory? (A **Hamiltonian cycle**!)
> - Calculate the minimum degree $\delta(G)$ using the **Principle of Inclusion-Exclusion** on the multiples of 3, 5, and 11 within $\{1, \dots, 165\}$.
> - If $\delta(G) \ge |V|/2 = 165/2 = 82.5$, apply **Dirac's Theorem**!

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Edge Bound Forcing a Hamiltonian Cycle

Let $G = (V, E)$ be a simple undirected graph on $|V| = n \ge 3$ vertices.
Suppose that the number of edges satisfies:
$$|E| > \binom{n - 1}{2} + 1$$
**Prove** that $G$ contains a **Hamiltonian cycle**.

> [!tip]- 💡 Hints & Strategy
> - Recall **Ore's Theorem**: If for every pair of non-adjacent vertices $u, v \in V$, $\deg(u) + \deg(v) \ge n$, then $G$ contains a Hamiltonian cycle.
> - Assume for contradiction that $G$ does not satisfy Ore's condition. Then there exist non-adjacent vertices $u, v$ with $\deg(u) + \deg(v) \le n - 1$.
> - Bound the maximum possible number of edges in a graph with such a pair $u, v$: all other edges must lie within $V \setminus \{u, v\}$, plus edges incident to $u$ and $v$. Show $|E| \le \binom{n-1}{2} + 1$, reaching a contradiction.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Cartesian Product of Graphs ($G \square H$)

### Definition:
The **Cartesian product** of two graphs $G$ and $H$, denoted $G \square H$, has vertex set:
$$V(G \square H) = V(G) \times V(H)$$
and edge set:
$$E(G \square H) = \left\{ \{(g_1, h_1), (g_2, h_2)\} \;\middle|\; (g_1 = g_2 \land \{h_1, h_2\} \in E(H)) \;\lor\; (h_1 = h_2 \land \{g_1, g_2\} \in E(G)) \right\}$$

### Part (a): Connectivity
**Prove** that if $G$ and $H$ are connected, then $G \square H$ is connected.

### Part (b): Eulerian Characterization of $K_m \square K_n$
Let $m, n > 1$. **Prove** that $K_m \square K_n$ contains an **Eulerian circuit** if and only if $m \equiv n \pmod 2$.

### Part (c): Hamiltonian Property Preservation
**Prove** that if both $G$ and $H$ contain a Hamiltonian cycle, then $G \square H$ contains a Hamiltonian cycle.

### Part (d): Hypercube Decomposition & Hamiltonicity
1. For the hypercube graph $Q_n$, show that $Q_n \square Q_m \cong Q_{n+m}$.
2. Conclude by induction that the hypercube graph $Q_n$ contains a Hamiltonian cycle for all $n \ge 2$.

> [!tip]- 💡 Hints & Strategy
> - For (a): Connect $(g_1, h_1)$ to $(g_2, h_1)$ using a path in $G$, then to $(g_2, h_2)$ using a path in $H$.
> - For (b): First show $\deg_{G \square H}((g, h)) = \deg_G(g) + \deg_H(h)$. In $K_m \square K_n$, this is $(m-1) + (n-1) = m + n - 2$.
> - For (c): Snake through the grid of the two cycles $C_m \square C_n$. If one order is even, traverse copies in alternating directions.
> - For (d): $Q_1 = K_2$, $Q_2 = C_4$ (Hamiltonian). Use $Q_n \cong Q_{n-2} \square Q_2$ or induction with Part (c).

> [!quote]- ✍️ Solution Workspace
> 
