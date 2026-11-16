---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 5
topic: "Directed Eulerian Circuits, Matching Unions, Dirac's Theorem, Ore's Theorem, Graph Cartesian Products"
problem_file: "[[Discrete Structures HW 05]]"
tags:
  - solution
  - discrete_structures
  - eulerian_circuits
  - hamiltonian_cycles
  - matchings
  - dirac_theorem
  - cartesian_product
---

# 🛡️ Discrete Structures — Homework Assignment 5 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 05|View Unsolved Assignment]]
> - **Topics Covered:** Directed Eulerian Invariants, Bipartite Matching Alternation, Degree Inclusion-Exclusion & Dirac's Theorem, Ore's Theorem Edge Extremals, Cartesian Product ($G \square H$) Properties.

---

## 📌 Solution 1: Directed Eulerian Circuits in Pseudo-Graphs

**Theorem:** A strongly connected directed pseudo-graph $D = (V, E)$ has an Eulerian circuit $\iff \forall v \in V: \operatorname{deg}_{\text{in}}(v) = \operatorname{deg}_{\text{out}}(v)$.

### Proof $(\implies)$:
1. Suppose $D$ contains an Eulerian circuit $C = (e_1, e_2, \dots, e_m)$.
2. The circuit visits every edge $e \in E$ exactly once.
3. Every time the walk visits a vertex $v$, it enters $v$ via some incoming edge and immediately departs $v$ via some outgoing edge.
4. If $v$ is the start/end vertex, the initial departure is paired with the final entrance.
5. Thus, each visit accounts for exactly 1 in-edge and 1 out-edge incident to $v$.
6. Since every edge is traversed once, $\operatorname{deg}_{\text{in}}(v) = \operatorname{deg}_{\text{out}}(v)$ for all $v \in V$.

### Proof $(\impliedby)$:
1. Assume $D$ is strongly connected and $\operatorname{deg}_{\text{in}}(v) = \operatorname{deg}_{\text{out}}(v) = d(v)$ for all $v$.
2. If $|E| = 0$, trivial. Otherwise, since $D$ is strongly connected, each $d(v) \ge 1$.
3. **Existence of a directed cycle:**
   Start at any vertex $v_0$ and follow directed edges. Since out-degree equals in-degree at every vertex, we can never get stuck at any vertex other than $v_0$, and once we return to $v_0$ we have closed a directed cycle $C_1$.
4. **Inductive Cycle Splice (Hierholzer's Algorithm):**
   - Remove the edges of $C_1$ from $D$, yielding a subgraph $D' = (V, E \setminus E(C_1))$.
   - In $C_1$, each vertex has exactly 1 incoming edge and 1 outgoing edge.
   - Thus, in $D'$, $\operatorname{deg}_{D', \text{in}}(v) = \operatorname{deg}_{D', \text{out}}(v)$ still holds for every vertex $v \in V$.
   - Each connected component of $D'$ that has edges satisfies the in-degree = out-degree condition and, by strong connectivity of $D$, intersects $C_1$ at least at one vertex.
   - By induction on $|E|$, each component of $D'$ has a directed Eulerian circuit.
   - We splice each of these Eulerian circuits into $C_1$ at their respective intersection vertices to form a single master directed Eulerian circuit of $D$. $\blacksquare$

---

## 📌 Solution 2: The Union of Two Matchings is Bipartite

**Problem:** Let $M_1, M_2$ be two matchings in $G = (V, E)$. Prove $G' = (V, M_1 \cup M_2)$ is bipartite.

### Formal Proof:
1. Recall the fundamental characterization: **A graph is bipartite if and only if it contains no odd cycles.**
2. Let $v \in V$ be any vertex in $G'$.
   - Since $M_1$ is a matching, $v$ is incident to at most one edge in $M_1$.
   - Since $M_2$ is a matching, $v$ is incident to at most one edge in $M_2$.
   - Therefore, the degree of $v$ in $G'$ satisfies:
     $$\deg_{G'}(v) \le 1 + 1 = 2$$
3. A graph with maximum degree $\Delta \le 2$ is a disjoint union of isolated vertices, simple paths, and simple cycles.
4. If $G'$ contains no cycles, it is a forest, hence bipartite.
5. Suppose $G'$ contains a cycle $C = (v_1, v_2, \dots, v_k, v_1)$ of length $k \ge 3$.
   - Consider any vertex $v_i$ on $C$. Its two incident edges in $C$ are $e = (v_{i-1}, v_i)$ and $e' = (v_i, v_{i+1})$.
   - Since $M_1$ is a matching, $e$ and $e'$ cannot both belong to $M_1$.
   - Since $M_2$ is a matching, $e$ and $e'$ cannot both belong to $M_2$.
   - Therefore, one edge must belong to $M_1$ and the other must belong to $M_2$.
6. This means the edges of $C$ must strictly **alternate** between $M_1$ and $M_2$:
   $$(v_1, v_2) \in M_1, \quad (v_2, v_3) \in M_2, \quad (v_3, v_4) \in M_1, \quad \dots$$
7. For the cycle to close back at $v_1$, the final edge $(v_k, v_1)$ must belong to $M_2$.
8. Consequently, the edges of $C$ can be partitioned into two sets of equal size: $|E(C) \cap M_1| = |E(C) \cap M_2|$.
9. Hence, the length of the cycle is $k = 2 \cdot |E(C) \cap M_1|$, which is **even**.
10. Since every cycle in $G'$ has even length, $G'$ contains no odd cycles, and is therefore bipartite. $\blacksquare$

---

## 📌 Solution 3: Cyclic Ordering via Dirac's Theorem

**Problem:** $A = \{1, \dots, 165\}$, $a R b \iff a \equiv b \pmod 3 \lor a \equiv b \pmod 5 \lor a \equiv b \pmod{11}$. Prove $A$ can be ordered cyclically with $a_i R a_{i+1}$.

### Formal Proof:
1. Define a simple graph $G = (V, E)$ where $V = A = \{1, 2, \dots, 165\}$ and:
   $$\{a, b\} \in E \iff a \ne b \;\land\; a R b$$
   A circular sequence $(a_1, a_2, \dots, a_{165})$ satisfying the condition is precisely a **Hamiltonian cycle** in $G$.
2. To prove $G$ has a Hamiltonian cycle, we compute the degree $\deg(v)$ of an arbitrary vertex $v \in V$.
3. For $m \in \{3, 5, 11\}$, let $R_m(v) = \{u \in A \setminus \{v\} \mid u \equiv v \pmod m\}$.
   The number of integers in $\{1, \dots, 165\}$ that are congruent to $v \pmod m$ is $\frac{165}{m}$ (since $m$ divides 165).
   Excluding $v$ itself:
   $$|R_3(v)| = \frac{165}{3} - 1 = 55 - 1 = 54$$
   $$|R_5(v)| = \frac{165}{5} - 1 = 33 - 1 = 32$$
   $$|R_{11}(v)| = \frac{165}{11} - 1 = 15 - 1 = 14$$
4. Similarly, by the Chinese Remainder Theorem:
   - For $u \equiv v \pmod 3$ and $u \equiv v \pmod 5 \iff u \equiv v \pmod{15}$:
     $$|R_3(v) \cap R_5(v)| = \frac{165}{15} - 1 = 11 - 1 = 10$$
   - For $u \equiv v \pmod 3$ and $u \equiv v \pmod{11} \iff u \equiv v \pmod{33}$:
     $$|R_3(v) \cap R_{11}(v)| = \frac{165}{33} - 1 = 5 - 1 = 4$$
   - For $u \equiv v \pmod 5$ and $u \equiv v \pmod{11} \iff u \equiv v \pmod{55}$:
     $$|R_5(v) \cap R_{11}(v)| = \frac{165}{55} - 1 = 3 - 1 = 2$$
   - For $u \equiv v \pmod{165}$:
     Since $u \in A = \{1, \dots, 165\}$, only $u = v$ satisfies this, which is excluded. Thus:
     $$|R_3(v) \cap R_5(v) \cap R_{11}(v)| = 0$$
5. By the **Principle of Inclusion-Exclusion**:
   $$\deg(v) = |R_3 \cup R_5 \cup R_{11}| = (54 + 32 + 14) - (10 + 4 + 2) + 0 = 100 - 16 = 84$$
6. Notice that every vertex $v \in V$ has degree $\deg(v) = 84$.
7. Total vertices $|V| = 165$. We check **Dirac's Condition**:
   $$\deg(v) = 84 \ge \frac{165}{2} = 82.5 \quad \forall v \in V$$
8. By **Dirac's Theorem**, any simple graph with $|V| \ge 3$ and $\delta(G) \ge \frac{|V|}{2}$ contains a **Hamiltonian cycle**.
9. The vertices along this Hamiltonian cycle provide the desired circular ordering $(a_1, a_2, \dots, a_{165}, a_1)$. $\blacksquare$

---

## 📌 Solution 4: Edge Bound Forcing a Hamiltonian Cycle

**Theorem:** Let $G = (V, E)$ be a simple graph on $n \ge 3$ vertices with $|E| > \binom{n-1}{2} + 1$. Then $G$ is Hamiltonian.

### Formal Proof:
1. Recall **Ore's Theorem**: If for every pair of non-adjacent vertices $u, v \in V$,
   $$\deg(u) + \deg(v) \ge n$$
   then $G$ contains a Hamiltonian cycle.
2. We prove the contrapositive: Suppose $G$ contains **no Hamiltonian cycle**.
3. By Ore's Theorem, there must exist at least one pair of non-adjacent vertices $u, v \in V$ (so $\{u, v\} \notin E$) such that:
   $$\deg(u) + \deg(v) \le n - 1$$
4. Let us upper-bound the total number of edges $|E|$ in such a graph:
   - Partition the edges into two sets:
     1. Edges incident to $u$ or $v$.
     2. Edges whose endpoints both lie in $V \setminus \{u, v\}$.
   - Since $u$ and $v$ are not adjacent, every edge incident to $u$ or $v$ goes to the remaining $n - 2$ vertices. The number of such edges is precisely:
     $$\deg(u) + \deg(v) \le n - 1$$
   - The remaining vertices $V \setminus \{u, v\}$ have size $n - 2$. The maximum number of edges between them is at most the complete graph on $n - 2$ vertices:
     $$\binom{n - 2}{2}$$
5. Summing these two bounds:
   $$|E| \le \binom{n - 2}{2} + (\deg(u) + \deg(v)) \le \frac{(n-2)(n-3)}{2} + (n - 1)$$
6. Simplify the algebra:
   $$\frac{n^2 - 5n + 6}{2} + \frac{2n - 2}{2} = \frac{n^2 - 3n + 4}{2} = \frac{(n-1)(n-2) + 2}{2} = \binom{n-1}{2} + 1$$
7. Thus, any non-Hamiltonian graph on $n$ vertices satisfies:
   $$|E| \le \binom{n - 1}{2} + 1$$
8. Therefore, if $|E| > \binom{n-1}{2} + 1$, $G$ must contain a Hamiltonian cycle. $\blacksquare$

---

## 📌 Solution 5: Cartesian Product of Graphs ($G \square H$)

### Part (a): $G, H$ Connected $\implies G \square H$ Connected
- **Proof:**
  Let $(g_1, h_1)$ and $(g_2, h_2)$ be any two vertices in $V(G \square H)$.
  1. Since $G$ is connected, there exists a path in $G$ from $g_1$ to $g_2$:
     $$(x_0 = g_1, x_1, x_2, \dots, x_k = g_2)$$
     By definition of Cartesian product, for fixed $h_1$, $\{(x_i, h_1), (x_{i+1}, h_1)\} \in E(G \square H)$.
     Thus, there is a path from $(g_1, h_1)$ to $(g_2, h_1)$ in $G \square H$.
  2. Since $H$ is connected, there exists a path in $H$ from $h_1$ to $h_2$:
     $$(y_0 = h_1, y_1, y_2, \dots, y_m = h_2)$$
     For fixed $g_2$, $\{(g_2, y_j), (g_2, y_{j+1})\} \in E(G \square H)$.
     Thus, there is a path from $(g_2, h_1)$ to $(g_2, h_2)$ in $G \square H$.
  3. Concatenating these two paths yields a walk from $(g_1, h_1)$ to $(g_2, h_2)$.
  Hence $G \square H$ is connected. $\blacksquare$

---

### Part (b): Eulerian Circuit in $K_m \square K_n \iff m \equiv n \pmod 2$
- **Lemma (Degree in Product):**
  For any $(g, h) \in V(G \square H)$:
  $$\deg_{G \square H}((g, h)) = \deg_G(g) + \deg_H(h)$$
  *(Follows immediately from the definition: neighbors of $(g, h)$ are $(g', h)$ for $g' \in N_G(g)$ plus $(g, h')$ for $h' \in N_H(h)$).*
- In $K_m \square K_n$:
  Every vertex $g \in K_m$ has $\deg(g) = m - 1$.
  Every vertex $h \in K_n$ has $\deg(h) = n - 1$.
  Therefore, every vertex in $K_m \square K_n$ has degree:
  $$\deg((g, h)) = (m - 1) + (n - 1) = m + n - 2$$
- Euler's Theorem states that a connected graph has an Eulerian circuit $\iff$ every vertex has even degree.
- The degree $m + n - 2$ is even if and only if $m + n$ is even, which occurs if and only if $m$ and $n$ have the same parity:
  $$m \equiv n \pmod 2$$
  $\blacksquare$

---

### Part (c): Hamiltonicity Preservation
- **Proof:**
  Let $C_G = (g_1, g_2, \dots, g_m, g_1)$ and $C_H = (h_1, h_2, \dots, h_n, h_1)$ be Hamiltonian cycles in $G$ and $H$.
  Since $C_G$ and $C_H$ are subgraphs, $C_G \square C_H$ is a subgraph of $G \square H$. It suffices to show that the grid torus $C_m \square C_n$ is Hamiltonian.
  - **Case 1: At least one of $m, n$ is even (say $n$ is even):**
    Traverse the copy of $C_G$ at layer $h_1$: $(g_1, h_1) \to (g_2, h_1) \to \dots \to (g_m, h_1)$.
    Step up to $(g_m, h_2)$, then traverse $C_G$ backwards: $(g_m, h_2) \to (g_{m-1}, h_2) \to \dots \to (g_1, h_2)$.
    Continue this serpentine/boustrophedon pattern for all $n$ layers. Since $n$ is even, layer $n$ ends at $(g_1, h_n)$.
    From $(g_1, h_n)$, follow the vertical edge back to $(g_1, h_1)$ to close the Hamiltonian cycle!
  - **Case 2: Both $m, n$ are odd:**
    Traverse $(g_1, h_1) \to \dots \to (g_m, h_1)$, then go along the perimeter of the grid $(g_m, h_1) \to (g_m, h_n)$, then zigzag across the remaining $(m-1) \times (n-1)$ grid (which has an even dimension $m-1$), finally returning to $(g_1, h_1)$.
  In both cases, a Hamiltonian cycle exists in $G \square H$. $\blacksquare$

---

### Part (d): Hypercube Hamiltonicity
1. **Isomorphism $Q_n \square Q_m \cong Q_{n+m}$:**
   - Vertices of $Q_{n+m}$ are binary words of length $n+m$: $V = \{0, 1\}^{n+m}$.
   - Vertices of $Q_n \square Q_m$ are pairs of words $(u, v) \in \{0, 1\}^n \times \{0, 1\}^m$.
   - The concatenation map $(u, v) \mapsto u \circ v$ is a bijection between vertex sets.
   - Two vertices in $Q_n \square Q_m$ are adjacent $\iff u = u'$ and $v, v'$ differ by 1 bit, OR $v = v'$ and $u, u'$ differ by 1 bit. This corresponds exactly to $u \circ v$ and $u' \circ v'$ differing by exactly 1 bit in $\{0, 1\}^{n+m}$.
   - Hence $Q_n \square Q_m \cong Q_{n+m}$.
2. **Hamiltonicity for all $n \ge 2$:**
   - Base case $n = 2$: $Q_2 \cong C_4$, which is a 4-cycle (Hamiltonian).
   - Base case $n = 3$: $Q_3$ has the Gray code cycle $(000, 001, 011, 010, 110, 111, 101, 100, 000)$ (Hamiltonian).
   - Inductive step: For $n \ge 4$, $Q_n \cong Q_{n-2} \square Q_2$.
     By the induction hypothesis, $Q_{n-2}$ is Hamiltonian, and $Q_2$ is Hamiltonian.
     By Part (c), their Cartesian product $Q_n$ is Hamiltonian.
   Thus, $Q_n$ is Hamiltonian for all $n \ge 2$. $\blacksquare$
