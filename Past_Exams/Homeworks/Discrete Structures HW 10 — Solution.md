---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 10
topic: "Petersen Graph Class 2, Random Graphs Cycles & Markov, Probabilistic Method Subgraphs, Choice Number"
problem_file: "[[Discrete Structures HW 10]]"
tags:
  - solution
  - discrete_structures
  - chromatic_index
  - petersen_graph
  - random_graphs
  - probabilistic_method
  - list_coloring
---

# 🛡️ Discrete Structures — Homework Assignment 10 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 10|View Unsolved Assignment]]
> - **Topics Covered:** 1-Factor / 2-Factor Parity Contradiction on Petersen Graph, Erdős-Rényi Cycle Counting Expectation & Tail Bounds, First Moment Existence of $k$-Partite Subgraphs, Probabilistic List Coloring Bound ($ch(G) \le \lceil \chi \ln n \rceil$).

---

## 📌 Solution 1: Chromatic Index of the Petersen Graph

**Theorem:** The Petersen graph $P$ is Class 2: $\chi'(P) = \Delta(P) + 1 = 4$.

### Formal Proof:
1. The Petersen graph $P$ has $|V| = 10$ vertices and is 3-regular: $\Delta(P) = 3$.
   By the Handshaking Lemma, the number of edges is:
   $$|E| = \frac{10 \times 3}{2} = 15$$
2. By **Vizing's Theorem**, the chromatic index satisfies:
   $$\Delta(P) \le \chi'(P) \le \Delta(P) + 1 \implies \chi'(P) \in \{3, 4\}$$
3. Assume for contradiction that $\chi'(P) = 3$.
4. Then $E$ can be partitioned into 3 edge-disjoint matchings:
   $$E = M_1 \;\dot\cup\; M_2 \;\dot\cup\; M_3$$
5. In any graph, each matching can contain at most $\lfloor |V|/2 \rfloor = \lfloor 10/2 \rfloor = 5$ edges.
   Since $|M_1| + |M_2| + |M_3| = 15$, we must have:
   $$|M_1| = |M_2| = |M_3| = 5$$
   Thus, every color class $M_i$ must be a **perfect matching** (1-factor).
6. Consider the subgraph formed by removing $M_1$ from $P$:
   $$H = P \setminus M_1 = (V, M_2 \cup M_3)$$
   Since $P$ is 3-regular and $M_1$ touches every vertex exactly once, $H$ is a **2-regular graph** on 10 vertices.
7. Every 2-regular graph is a disjoint union of simple cycles.
8. Recall that the **girth** (shortest cycle length) of the Petersen graph is $5$.
   Therefore, no cycle in $H$ can have length $3$ or $4$.
9. The only partitions of $10$ into integers $\ge 5$ are:
   - **Case 1: A single cycle of length 10.**
     This would mean $H$ is a Hamiltonian cycle of $P$.
     However, it is a well-known classical theorem that the **Petersen graph is non-Hamiltonian** (it contains no 10-cycle). Contradiction.
   - **Case 2: Two disjoint cycles of length 5 ($C_5 \cup C_5$).**
     In this case, $H$ is the union of two 5-cycles.
     The edges of $H$ are partitioned into $M_2$ and $M_3$, so $H$ is properly 2-edge-colorable.
     However, an odd cycle $C_5$ has chromatic index $\chi'(C_5) = 3$, meaning it **cannot** be 2-edge colored!
     (In any 2-edge coloring of an alternating cycle, the length must be even). Contradiction.
10. Since both cases lead to a contradiction, no proper 3-edge coloring can exist.
11. Therefore, $\chi'(P) = 4$, confirming that the Petersen graph is **Class 2**. $\blacksquare$

---

## 📌 Solution 2: Simple Cycles in the Erdős-Rényi Random Graph $G(n, p)$

### Part (a): Expected Number of $k$-Cycles $\mathbb{E}[X(k)]$
1. Let $k \ge 3$. A potential simple $k$-cycle is determined by a subset of $k$ vertices and a cyclic ordering of them.
2. The number of ordered sequences of $k$ distinct vertices chosen from $n$ vertices is:
   $$\frac{n!}{(n - k)!}$$
3. Two sequences describe the exact same unoriented cycle if and only if they differ by:
   - A cyclic rotation (there are $k$ cyclic shifts).
   - A reversal of orientation (there are 2 directions).
   Thus, each distinct cycle corresponds to $2k$ sequences.
4. The total number of potential $k$-cycles in $K_n$ is:
   $$N(k) = \frac{n!}{2k(n - k)!} = \frac{1}{2k} \binom{n}{k} k!$$
5. Let $C_1, C_2, \dots, C_{N(k)}$ be an enumeration of all potential $k$-cycles.
   Define the indicator random variable:
   $$I_i = \begin{cases} 1 & \text{if all } k \text{ edges of } C_i \text{ exist in } G \\[2pt] 0 & \text{otherwise} \end{cases}$$
6. Since each edge appears independently with probability $p$:
   $$\Pr(I_i = 1) = p^k \implies \mathbb{E}[I_i] = p^k$$
7. The total number of $k$-cycles is $X(k) = \sum_{i=1}^{N(k)} I_i$.
   By **Linearity of Expectation**:
   $$\mathbb{E}[X(k)] = \sum_{i=1}^{N(k)} \mathbb{E}[I_i] = N(k) \cdot p^k = \frac{n! \cdot p^k}{2k (n - k)!}$$
- **Boundary Checks:**
  - If $p = 0$: $\mathbb{E}[X(k)] = 0$, correct (empty graph has no cycles).
  - If $p = 1$: $\mathbb{E}[X(k)] = \frac{n!}{2k(n-k)!}$, which is the exact number of $k$-cycles in the complete graph $K_n$. Correct! $\blacksquare$

---

### Part (b): Markov Bound on Having $\ge s$ Cycles
By **Markov's Inequality**, for any non-negative integer-valued random variable $X$ and $s > 0$:
$$\Pr(X(k) \ge s) \le \frac{\mathbb{E}[X(k)]}{s} = \frac{n! \cdot p^k}{2k \cdot s \cdot (n - k)!}$$
$\blacksquare$

---

### Part (c): Markov Bound on Hamiltonicity
1. A Hamiltonian cycle is a simple cycle of length $k = n$.
2. The number of Hamiltonian cycles in $G(n, p)$ is $X(n)$.
3. Its expectation is:
   $$\mathbb{E}[X(n)] = \frac{n! \cdot p^n}{2n (n - n)!} = \frac{n! \cdot p^n}{2n} = \frac{(n - 1)! \cdot p^n}{2}$$
4. The event that $G$ is Hamiltonian is the event $X(n) \ge 1$.
5. Applying Markov's Inequality:
   $$\Pr(G \text{ is Hamiltonian}) = \Pr(X(n) \ge 1) \le \mathbb{E}[X(n)] = \frac{(n - 1)! \cdot p^n}{2}$$
   *(Remark: This shows that if $p < \frac{1}{n}$, $\Pr(\text{Hamiltonian}) \to 0$ extremely rapidly as $n \to \infty$).* $\blacksquare$

---

## 📌 Solution 3: Probabilistic Method: Large $k$-Colorable Subgraphs

**Problem:** Prove that every graph $G = (V, E)$ contains a $k$-colorable subgraph $G' = (V, E')$ with $|E'| \ge |E|\left(1 - \frac{1}{k}\right)$.

### Formal Proof:
1. Let $V = \{v_1, \dots, v_n\}$. We assign each vertex $v \in V$ a color chosen **uniformly and independently at random** from the set of $k$ colors $\{1, 2, \dots, k\}$:
   $$\Pr(c(v) = i) = \frac{1}{k} \quad \forall i \in \{1, \dots, k\}$$
2. For each edge $e = \{u, v\} \in E$, the vertices $u$ and $v$ receive independent random colors.
   The probability that $u$ and $v$ receive the **same** color is:
   $$\Pr(c(u) = c(v)) = \sum_{i=1}^k \Pr(c(u) = i \land c(v) = i) = \sum_{i=1}^k \frac{1}{k} \cdot \frac{1}{k} = k \cdot \frac{1}{k^2} = \frac{1}{k}$$
3. Therefore, the probability that the edge $e = \{u, v\}$ is **properly colored** (different endpoint colors) is:
   $$\Pr(c(u) \ne c(v)) = 1 - \frac{1}{k}$$
4. Define the indicator random variable for each edge $e \in E$:
   $$X_e = \begin{cases} 1 & \text{if } c(u) \ne c(v) \\[2pt] 0 & \text{if } c(u) = c(v) \end{cases}$$
   Then $\mathbb{E}[X_e] = \Pr(X_e = 1) = 1 - \frac{1}{k}$.
5. Let $X = \sum_{e \in E} X_e$ denote the total number of properly colored edges under this random coloring.
   By **Linearity of Expectation**:
   $$\mathbb{E}[X] = \sum_{e \in E} \mathbb{E}[X_e] = \sum_{e \in E} \left(1 - \frac{1}{k}\right) = |E| \left(1 - \frac{1}{k}\right)$$
6. Since the expectation of the random variable $X$ is $|E|\left(1 - \frac{1}{k}\right)$, there must exist at least one specific deterministic coloring $c^*$ for which the number of properly colored edges is at least the expectation:
   $$X(c^*) \ge \mathbb{E}[X] = |E| \left(1 - \frac{1}{k}\right)$$
7. Let $E' \subseteq E$ be the set of edges properly colored by $c^*$.
   By construction, $c^*$ is a proper $k$-coloring of the subgraph $G' = (V, E')$.
   Therefore, $G'$ is a $k$-colorable subgraph satisfying:
   $$|E'| \ge |E| \left(1 - \frac{1}{k}\right)$$
   $\blacksquare$

---

## 📌 Solution 4: List Chromatic Number Bound $ch(G) \le \lceil \chi(G) \ln n \rceil$

**Theorem:** For any graph $G$ on $n$ vertices, $ch(G) \le \lceil \chi(G) \ln n \rceil$.

### Formal Proof:
1. Let $k = \chi(G)$ be the chromatic number of $G$.
   Fix a proper $k$-coloring of $G$, which partitions $V$ into $k$ independent sets:
   $$V = C_1 \;\dot\cup\; C_2 \;\dot\cup\; \dots \;\dot\cup\; C_k$$
2. Let $m = \lceil k \ln n \rceil$.
   Suppose every vertex $v \in V$ is assigned an arbitrary list of colors $L_v$ of size $|L_v| = m$.
   We must show there exists a proper choice of $c(v) \in L_v$ for all $v$.
3. Let $\mathcal{U} = \bigcup_{v \in V} L_v$ be the universe of all colors appearing in the lists.
4. **Randomized Coloring Procedure:**
   For each color $\ell \in \mathcal{U}$:
   - Independently choose one of the $k$ independent sets $C_{I_\ell}$ uniformly at random:
     $$\Pr(I_\ell = i) = \frac{1}{k} \quad \forall i \in \{1, \dots, k\}$$
   - For every vertex $v \in C_{I_\ell}$ that has $\ell \in L_v$, assign color $\ell$ to $v$ (if $v$ receives multiple colors, pick any one arbitrarily).
5. **Properness:**
   Any two vertices assigned the same color $\ell$ must both belong to $C_{I_\ell}$.
   Since each $C_i$ is an independent set, no two adjacent vertices ever receive the same color!
   Thus, whenever a vertex is assigned a color from its list, the coloring is guaranteed to be **proper**.
6. **Probability of a Vertex Remaining Uncolored:**
   Consider a fixed vertex $v \in C_i$.
   The vertex $v$ remains uncolored if and only if for **every** color $\ell \in L_v$, the independent set chosen for $\ell$ was **not** $C_i$ (meaning $I_\ell \ne i$).
   Since the choices $I_\ell$ are mutually independent for each of the $m$ colors in $L_v$:
   $$\Pr(v \text{ is uncolored}) = \prod_{\ell \in L_v} \Pr(I_\ell \ne i) = \left(1 - \frac{1}{k}\right)^m$$
7. Using the standard inequality $1 - x \le e^{-x}$ for all $x \ge 0$:
   $$\left(1 - \frac{1}{k}\right)^m \le \left(e^{-1/k}\right)^m = e^{-m/k}$$
   Since $m = \lceil k \ln n \rceil \ge k \ln n$:
   $$\Pr(v \text{ is uncolored}) \le e^{-(k \ln n)/k} = e^{-\ln n} = \frac{1}{n}$$
   Since $1 - 1/k < 1$ and $m > k \ln n$ strictly whenever $k \ln n$ is not an integer, $\Pr(v \text{ is uncolored}) < \frac{1}{n}$.
8. Let $Y$ be the random variable counting the number of vertices in $V$ that remain uncolored.
   By Linearity of Expectation:
   $$\mathbb{E}[Y] = \sum_{v \in V} \Pr(v \text{ is uncolored}) < n \cdot \frac{1}{n} = 1$$
9. Since $Y$ is a non-negative integer-valued random variable and $\mathbb{E}[Y] < 1$:
   $$\Pr(Y = 0) > 0$$
   Therefore, there exists a coloring from the lists that leaves **zero uncolored vertices**!
10. Thus, $G$ is $m$-choosable, proving:
    $$ch(G) \le \lceil \chi(G) \ln n \rceil$$
    $\blacksquare$
