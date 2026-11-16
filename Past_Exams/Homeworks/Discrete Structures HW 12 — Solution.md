---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 12
topic: "Trees from Edge Deletion, Uniqueness of Perfect Matchings in Trees, Stable Marriage MPDA, Lattice Property, Triangle Deletion Method"
problem_file: "[[Discrete Structures HW 12]]"
tags:
  - solution
  - discrete_structures
  - trees
  - matchings
  - stable_matching
  - gale_shapley
  - probabilistic_method
---

# 🛡️ Discrete Structures — Homework Assignment 12 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 12|View Unsolved Assignment]]
> - **Topics Covered:** Universal Tree Pruning & Cycle Reconstruction, Tree Matching Uniqueness via Symmetric Difference Acyclicity, Gale-Shapley Convergence Bounds, Stable Marriage Lattice Join Theorem, Erdős Deletion Method.

---

## 📌 Solution 1: Edge-Pruning Characterization of Cycles

**Theorem:** Let $G = (V, E)$ be connected with $|V| > 1$. If $\forall e \in E$, $G \setminus \{e\}$ is a tree, then $\forall v \in V, \; \deg(v) = 2$ (so $G \cong C_n$).

### Formal Proof:
1. **Minimum Degree Bound ($\deg(v) \ge 2$):**
   - Suppose for contradiction that there exists a vertex $v \in V$ with $\deg(v) \le 1$.
   - Since $G$ is connected and $|V| > 1$, we cannot have $\deg(v) = 0$.
   - Thus $\deg(v) = 1$. Let $e = \{v, u\}$ be the unique edge incident to $v$.
   - Consider the graph $G' = G \setminus \{e\}$.
   - In $G'$, vertex $v$ has degree $0$, making it an isolated vertex.
   - Since $|V| > 1$, $G'$ contains at least two vertices and an isolated vertex $v$, so $G'$ is **disconnected**.
   - But a tree is connected by definition! Contradiction.
   - Therefore, every vertex in $G$ must satisfy:
     $$\deg_G(v) \ge 2 \quad \forall v \in V$$

2. **Maximum Degree Bound ($\deg(v) \le 2$):**
   - Let $e = \{u, v\} \in E$ be an arbitrary edge in $G$.
   - By assumption, $T = G \setminus \{e\}$ is a tree on $|V| \ge 2$ vertices.
   - Every tree with at least 2 vertices contains at least two leaves (vertices of degree 1):
     $$|\{x \in V \mid \deg_T(x) = 1\}| \ge 2$$
   - Now consider how degrees change when deleting the edge $e = \{u, v\}$:
     - For $x \notin \{u, v\}$: $\deg_T(x) = \deg_G(x) \ge 2$.
       Thus, no vertex outside $\{u, v\}$ can be a leaf in $T$!
     - Therefore, the **only** vertices in $T$ that can possibly have degree 1 are $u$ and $v$.
   - Since $T$ must have at least two leaves, both $u$ and $v$ **must be leaves** in $T$:
     $$\deg_T(u) = 1 \quad \text{and} \quad \deg_T(v) = 1$$
   - Since $\deg_G(u) = \deg_T(u) + 1$:
     $$\deg_G(u) = 1 + 1 = 2 \quad \text{and} \quad \deg_G(v) = 1 + 1 = 2$$

3. **Conclusion:**
   Since every edge has both endpoints of degree 2, and every vertex is incident to at least one edge, every vertex in $G$ has degree exactly 2:
   $$\deg_G(v) = 2 \quad \forall v \in V$$
   A connected 2-regular graph is a simple cycle $C_n$. $\blacksquare$

---

## 📌 Solution 2: Uniqueness of Perfect Matchings in Trees

**Theorem:** Every tree $T = (V, E)$ contains at most one perfect matching.

### Formal Proof:
1. Assume for contradiction that $T$ contains two distinct perfect matchings:
   $$M_1 \ne M_2$$
2. Consider the symmetric difference graph:
   $$H = (V, \; M_1 \oplus M_2)$$
   where $M_1 \oplus M_2 = (M_1 \setminus M_2) \cup (M_2 \setminus M_1)$.
3. Since $M_1 \ne M_2$, the edge set $M_1 \oplus M_2$ is non-empty: $|E(H)| \ge 1$.
4. Now analyze the degree of an arbitrary vertex $v \in V$ in $H$:
   - Since $M_1$ is a perfect matching, $v$ is incident to exactly one edge in $M_1$.
   - Since $M_2$ is a perfect matching, $v$ is incident to exactly one edge in $M_2$.
   - If that edge is shared ($e \in M_1 \cap M_2$), then $e \notin M_1 \oplus M_2$, so $\deg_H(v) = 0$.
   - If the edges are distinct ($e_1 \in M_1 \setminus M_2$ and $e_2 \in M_2 \setminus M_1$), both belong to $H$, so $\deg_H(v) = 2$.
5. Thus, every vertex in $H$ has degree either $0$ or $2$.
6. A non-empty graph in which every non-isolated vertex has degree 2 is a disjoint union of **cycles**.
7. Therefore, $H$ contains at least one simple cycle $C$.
8. However, $E(H) \subseteq M_1 \cup M_2 \subseteq E(T)$, which means the cycle $C$ is a subgraph of the tree $T$:
   $$C \subseteq T$$
9. This directly contradicts the defining property of a tree, which is that $T$ contains no cycles!
10. Therefore, the assumption $M_1 \ne M_2$ was false, so $T$ can have **at most one perfect matching**. $\blacksquare$

---

## 📌 Solution 3: Dynamics of the Men-Proposing Gale-Shapley Algorithm (MPDA)

### Part (a): Multiple Stable Matchings
Consider $n = 2$ men $\{m_1, m_2\}$ and $n = 2$ women $\{w_1, w_2\}$:
- Preferences:
  $$m_1: w_1 \succ w_2, \quad m_2: w_2 \succ w_1$$
  $$w_1: m_2 \succ m_1, \quad w_2: m_1 \succ m_2$$
- **Matching $M_A = \{(m_1, w_1), (m_2, w_2)\}$:**
  Every man is matched to his 1st choice. Since no man wants to deviate, no blocking pair can exist. $M_A$ is stable!
- **Matching $M_B = \{(m_1, w_2), (m_2, w_1)\}$:**
  Every woman is matched to her 1st choice. Since no woman wants to deviate, no blocking pair can exist. $M_B$ is stable!
Both $M_A$ and $M_B$ are valid, distinct stable matchings. $\blacksquare$

---

### Part (b): Distinct Top Choices
- **Result:** The algorithm terminates in exactly **1 round**.
- **Proof:**
  In Round 1, each man proposes to his 1st choice woman.
  Since all men have pairwise distinct 1st choices, every woman receives exactly one proposal.
  Each woman holds her unique suitor.
  Since no man is rejected, the algorithm terminates immediately in Round 1. $\blacksquare$

---

### Part (c): Identical Preference Lists
- **Result:** The algorithm terminates in exactly **$n$ rounds**.
- **Proof:**
  Assume all men share the preference order $w_1 \succ w_2 \succ \dots \succ w_n$.
  - **Round 1:** All $n$ men propose to $w_1$. Woman $w_1$ keeps her favorite man $m_{(1)}$ and rejects the other $n - 1$ men.
  - **Round 2:** The $n - 1$ rejected men all propose to their second choice $w_2$. Woman $w_2$ keeps her favorite among them $m_{(2)}$ and rejects the remaining $n - 2$ men.
  - **Round $k$:** The $n - k + 1$ rejected men propose to $w_k$, which keeps 1 man and rejects $n - k$ men.
  - This process continues for $n$ rounds until the last remaining man proposes to $w_n$.
  Thus, exactly $n$ rounds are required. $\blacksquare$

---

## 📌 Solution 4: Lattice Property of Stable Matchings

**Problem:** Let $M_1, M_2$ be stable matchings. Define $\mu(m) = \max_{\succ_m}(\mu_1(m), \mu_2(m))$. Prove $M$ is a stable matching.

### 1. $M$ is a Valid Matching:
Assume for contradiction that two distinct men $m, m'$ are assigned to the same woman $w$:
$$\mu(m) = \mu(m') = w$$
- This means $w$ was matched to $m$ under one matching and to $m'$ under the other. Without loss of generality:
  $$\mu_1(m) = w \quad \text{and} \quad \mu_2(m') = w$$
- By definition of $\mu$, each man preferred $w$ over his other partner:
  $$w \succ_m \mu_2(m) \quad \text{and} \quad w \succ_{m'} \mu_1(m')$$
- Now look at woman $w$'s preference between $m$ and $m'$:
  - If $m \succ_w m'$: In matching $M_2$, $m'$ is matched to $w$ (so $\mu_2(w) = m'$), but $m$ prefers $w$ to $\mu_2(m)$ AND $w$ prefers $m$ to $\mu_2(w) = m'$.
    Thus, $(m, w)$ forms a **blocking pair** for $M_2$, contradicting the stability of $M_2$!
  - If $m' \succ_w m$: In matching $M_1$, $m$ is matched to $w$ (so $\mu_1(w) = m$), but $m'$ prefers $w$ to $\mu_1(m')$ AND $w$ prefers $m'$ to $\mu_1(w) = m$.
    Thus, $(m', w)$ forms a **blocking pair** for $M_1$, contradicting the stability of $M_1$!
- In both cases we reach a contradiction. Hence $M$ is a valid matching.

### 2. $M$ is a Stable Matching:
Assume for contradiction that $(m, w)$ is a **blocking pair** for $M$:
$$w \succ_m \mu(m) \quad \text{and} \quad m \succ_w \mu(w)$$
- Since $\mu(m) \succeq_m \mu_1(m)$ and $\mu(m) \succeq_m \mu_2(m)$:
  $$w \succ_m \mu_1(m) \quad \text{and} \quad w \succ_m \mu_2(m)$$
- Woman $w$ is matched in $M$ to $\mu(w)$, who is one of $\mu_1(w)$ or $\mu_2(w)$.
  Say $\mu(w) = \mu_1(w)$ (or $\mu_2(w)$).
  Then $m \succ_w \mu_1(w)$.
- Combining this with $w \succ_m \mu_1(m)$, $(m, w)$ forms a blocking pair for $M_1$!
- This contradicts the stability of $M_1$.
Therefore, $M$ contains no blocking pairs, so $M$ is a **stable matching**. $\blacksquare$

---

## 📌 Solution 5: Probabilistic Alteration Method for Triangle-Free Subgraphs

**Problem:** Let $G = (V, E)$ have $|V| = n$ and at most $48n$ triangles. Prove that $G$ has an induced triangle-free subgraph of size at least $\frac{n}{18}$.

### Formal Proof:
1. Let $p \in (0, 1)$ be a parameter to be determined later.
2. Form a random subset of vertices $S \subseteq V$ by including each vertex $v \in V$ independently with probability $p$:
   $$\Pr(v \in S) = p \quad \forall v \in V$$
3. Let $X = |S|$ be the number of vertices chosen into $S$.
   By Linearity of Expectation:
   $$\mathbb{E}[X] = \sum_{v \in V} \Pr(v \in S) = n \cdot p$$
4. Let $\mathcal{T}$ be the set of all triangles in $G$. We are given that $|\mathcal{T}| \le 48n$.
   For each triangle $T = \{u, v, w\} \in \mathcal{T}$, the triangle appears in the induced subgraph $G[S]$ if and only if all three vertices $u, v, w \in S$.
   By independence:
   $$\Pr(T \subseteq S) = p^3$$
5. Let $Y$ be the random variable counting the number of triangles in the induced subgraph $G[S]$.
   By Linearity of Expectation:
   $$\mathbb{E}[Y] = \sum_{T \in \mathcal{T}} \Pr(T \subseteq S) = |\mathcal{T}| \cdot p^3 \le 48n \cdot p^3$$
6. **The Alteration (Deletion) Step:**
   For each triangle remaining in $G[S]$, remove one vertex arbitrarily from $S$.
   Removing at most $Y$ vertices destroys all triangles in $G[S]$.
   The resulting vertex set $S' \subset S$ induces a subgraph $G[S']$ that is **completely triangle-free**.
7. The number of vertices remaining in $S'$ satisfies:
   $$|S'| \ge X - Y$$
8. By Linearity of Expectation:
   $$\mathbb{E}[|S'|] \ge \mathbb{E}[X - Y] = \mathbb{E}[X] - \mathbb{E}[Y] \ge n p - 48n p^3 = n(p - 48p^3)$$
9. **Optimizing $p$:**
   Consider the function $f(p) = p - 48p^3$ for $p \in (0, 1)$.
   Differentiating with respect to $p$:
   $$f'(p) = 1 - 144p^2$$
   Setting $f'(p) = 0$:
   $$144p^2 = 1 \implies p^2 = \frac{1}{144} \implies p = \frac{1}{12}$$
10. Evaluating $f(1/12)$:
    $$f\left(\frac{1}{12}\right) = \frac{1}{12} - 48 \left(\frac{1}{12}\right)^3 = \frac{1}{12} - \frac{48}{1728} = \frac{1}{12} - \frac{1}{36} = \frac{3 - 1}{36} = \frac{2}{36} = \frac{1}{18}$$
11. Therefore:
    $$\mathbb{E}[|S'|] \ge n \cdot f\left(\frac{1}{12}\right) = \frac{n}{18}$$
12. By the fundamental principle of the probabilistic method, there must exist at least one deterministic choice of vertices yielding an induced triangle-free subgraph of size at least $\frac{n}{18}$. $\blacksquare$
