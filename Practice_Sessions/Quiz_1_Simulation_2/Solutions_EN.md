# Complete Solutions — Quiz 1 Simulation 2
**Course:** Discrete Structures (89-2197) — Dr. Arnold Filtser  
**Coverage:** Lectures 1–4, Recitations 1–4, and Homework 1–4  
**Max Score:** 100 Points (Part A: 75 Points, Part B: 25 Points)

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)

### Question 1 (15 Points) — Posets & Equivalence Relations [HW 01, Q1(b)]
**Correct Answer: 2** (`(E, <=) is a partial order but not a total order; it has a unique minimum element and a unique maximum element`).

#### Detailed Explanation:
1. **Partial Order Axioms:**
   - **Reflexivity:** For any $R \in \mathcal{E}$, $R = R$, so $R \preceq R$ holds trivially.
   - **Antisymmetry:** If $R_1 \preceq R_2$ and $R_2 \preceq R_1$: if $R_1 \ne R_2$, then by definition $|X/R_1| < |X/R_2|$ and $|X/R_2| < |X/R_1|$, a contradiction. Thus $R_1 = R_2$.
   - **Transitivity:** If $R_1 \preceq R_2$ and $R_2 \preceq R_3$: if any equality holds, it is trivial; otherwise $|X/R_1| < |X/R_2| < |X/R_3| \implies |X/R_1| < |X/R_3| \implies R_1 \preceq R_3$.  
   Thus, $(\mathcal{E}, \preceq)$ is a valid partial order.
2. **Not a Total Order:**  
   To be a total order, every two distinct relations must be comparable.  
   However, consider two distinct equivalence relations that partition $X = \{1, \dots, 8\}$ into the exact same number of classes (say, 7 classes):
   - $R_1$ with classes $\{1, 2\}, \{3\}, \{4\}, \{5\}, \{6\}, \{7\}, \{8\}$
   - $R_2$ with classes $\{1, 3\}, \{2\}, \{4\}, \{5\}, \{6\}, \{7\}, \{8\}$  
   Here $R_1 \ne R_2$ and $|X/R_1| = |X/R_2| = 7$.  
   Therefore, neither $R_1 \preceq R_2$ nor $R_2 \preceq R_1$ holds. Hence, $(\mathcal{E}, \preceq)$ is **not** a total order.
3. **Unique Minimum & Maximum Elements:**
   - **Minimum Element:** For any partition of an 8-element set, $1 \le |X/R| \le 8$.  
     There is exactly **one** equivalence relation with $|X/R| = 1$: the universal relation $R_{\text{univ}} = X \times X$. For any other $R \ne R_{\text{univ}}$, $|X/R| > 1$, so $R_{\text{univ}} \preceq R$. Thus, $R_{\text{univ}}$ is the unique minimum.
   - **Maximum Element:** There is exactly **one** equivalence relation with $|X/R| = 8$: the identity relation $R_{\text{id}} = \{(x, x) \mid x \in X\}$. For any other $R \ne R_{\text{id}}$, $|X/R| < 8$, so $R \preceq R_{\text{id}}$. Thus, $R_{\text{id}}$ is the unique maximum.

---

### Question 2 (15 Points) — Graph Degrees & Complements [HW 02, Q1]
**Correct Answer: 2** (`The complement graph is connected, and diam(G_bar) <= 2`).

#### Detailed Explanation:
1. **Degrees in the Complement Graph:**  
   In any simple graph on $n = 9$ vertices, the degree of every vertex in the complement graph $\overline{G}$ is:
   $$\deg_{\overline{G}}(v) = (n - 1) - \deg_G(v) = 8 - \deg_G(v)$$
   Since $2 \le \deg_G(v) \le 4$, we have:
   $$8 - 4 \le \deg_{\overline{G}}(v) \le 8 - 2 \implies 4 \le \deg_{\overline{G}}(v) \le 6$$
   In particular, the minimum degree of $\overline{G}$ satisfies $\delta(\overline{G}) \ge 4$.
2. **Shortest Path Distances in $\overline{G}$:**  
   Let $u, w \in V$ be any two distinct vertices in $\overline{G}$.
   - **Case 1:** If $\{u, w\} \in E(\overline{G})$, then $\operatorname{dist}_{\overline{G}}(u, w) = 1$.
   - **Case 2:** If $\{u, w\} \notin E(\overline{G})$, we examine their neighborhoods $N_{\overline{G}}(u)$ and $N_{\overline{G}}(w)$.  
     Both neighborhoods lie within the remaining $n - 2 = 9 - 2 = 7$ vertices of the graph.  
     Since $|N_{\overline{G}}(u)| \ge 4$ and $|N_{\overline{G}}(w)| \ge 4$, by the Pigeonhole Principle (or inclusion-exclusion):
     $$|N_{\overline{G}}(u) \cap N_{\overline{G}}(w)| = |N_{\overline{G}}(u)| + |N_{\overline{G}}(w)| - |N_{\overline{G}}(u) \cup N_{\overline{G}}(w)| \ge 4 + 4 - 7 = 1$$
     Therefore, $u$ and $w$ must share at least one common neighbor $z \in V$ in $\overline{G}$.  
     This forms a 2-hop path $u - z - w$ in $\overline{G}$, proving that $\operatorname{dist}_{\overline{G}}(u, w) \le 2$.
3. Since every pair of vertices in $\overline{G}$ has distance at most 2, $\overline{G}$ is connected and $\operatorname{diam}(\overline{G}) \le 2$.

---

### Question 3 (15 Points) — Forest Edge Formula & Leaves [HW 02, Q2 & HW 03, Q2]
**Correct Answer: 3** (`k = 6, and if F has no isolated vertices (no vertices of degree 0), then l >= 12`).

#### Detailed Explanation:
1. **Number of Connected Components $k$:**  
   By the forest edge formula (HW 02, Q2), any acyclic graph with $n$ vertices, $m$ edges, and $k$ connected components satisfies:
   $$|E| = |V| - k \implies 14 = 20 - k \implies k = 6$$
   Thus, $F$ has exactly 6 connected components (each being a tree $T_1, \dots, T_6$).
2. **Leaf Count Bound:**  
   If $F$ contains no isolated vertices ($\deg(v) \ge 1$ for all $v$), then every component $T_i$ must have at least 2 vertices ($|V(T_i)| \ge 2$).  
   As proved in course lectures and HW 01, **every tree on $\ge 2$ vertices has at least 2 leaves**.  
   Since the 6 components are vertex-disjoint, the total number of leaves $\ell$ in $F$ must be at least:
   $$\ell = \sum_{i=1}^6 \ell(T_i) \ge 6 \times 2 = 12$$
   This matches Option 3 precisely.

---

### Question 4 (15 Points) — Cardinality & Set Operations [HW 02, Q3 & HW 04]
**Correct Answer: 4** (`(I), (II), and (III) are all always true`).

#### Detailed Explanation:
We are given $|A| = |C| = \aleph_0$ and $|B| = |D| = \aleph$.
1. **Assertion (I):**  
   $$|A \times B| = \aleph_0 \cdot \aleph = \max(\aleph_0, \aleph) = \aleph$$
   $$|C \times D| = \aleph_0 \cdot \aleph = \max(\aleph_0, \aleph) = \aleph$$
   Both products have cardinality $\aleph$, so $|A \times B| = |C \times D|$ is always true.
2. **Assertion (II):**  
   Since $B = (B \setminus A) \cup (B \cap A)$, we have $|B| \le |B \setminus A| + |B \cap A|$.  
   Notice that $B \cap A \subseteq A$, so $|B \cap A| \le |A| = \aleph_0$.  
   If $|B \setminus A|$ were strictly less than $\aleph$ (i.e. finite or countable), then $B$ would be the union of two at-most-countable sets, forcing $|B| \le \aleph_0$, which contradicts $|B| = \aleph$.  
   Therefore, removing any countable set $A$ from a continuum-sized set $B$ strictly preserves the continuum:
   $$|B \setminus A| = \aleph \quad \text{and} \quad |D \setminus C| = \aleph$$
   Thus $|B \setminus A| = |D \setminus C| = \aleph$ is always true.
3. **Assertion (III):**  
   $$|A \cup B| = \max(|A|, |B|) = \max(\aleph_0, \aleph) = \aleph$$
   $$|C \cup D| = \max(|C|, |D|) = \max(\aleph_0, \aleph) = \aleph$$
   Both unions have cardinality $\aleph$, so $|A \cup B| = |C \cup D|$ is always true.  
All three statements are unconditionally true.

---

### Question 5 (15 Points) — Cardinality of Finite-Image Functions [HW 04]
**Correct Answer: 3** ($2^\aleph$).

#### Detailed Explanation:
1. **Upper Bound:**  
   Every function in $\mathcal{H}$ is a mapping from $X$ to $\mathbb{N}$. Therefore, $\mathcal{H} \subseteq \mathbb{N}^X$, which gives:
   $$|\mathcal{H}| \le |\mathbb{N}^X| = |\mathbb{N}|^{|X|} = \aleph_0^\aleph$$
   Using standard cardinal arithmetic:
   $$\aleph_0^\aleph \le (2^{\aleph_0})^\aleph = 2^{\aleph_0 \cdot \aleph} = 2^\aleph$$
   Hence, $|\mathcal{H}| \le 2^\aleph$.
2. **Lower Bound:**  
   Consider the subset of functions whose image is restricted to $\{0, 1\} \subset \mathbb{N}$:
   $$\{0, 1\}^X = \{f: X \to \{0, 1\}\}$$
   For every such function $f$, its image $\operatorname{Im}(f) \subseteq \{0, 1\}$ is finite ($|\operatorname{Im}(f)| \le 2 < \infty$).  
   Therefore, $\{0, 1\}^X \subseteq \mathcal{H}$, which yields:
   $$|\{0, 1\}^X| = 2^{|X|} = 2^\aleph \le |\mathcal{H}|$$
3. **Conclusion by Cantor-Schröder-Bernstein:**  
   Since $2^\aleph \le |\mathcal{H}| \le 2^\aleph$, we conclude $|\mathcal{H}| = 2^\aleph$.

---

## Part B: Open Proof Question (25 Points) — Drawn from HW 01–04

### Question 6 (25 Points)

---

### Part 1 (12 Points) — A Tree with $\Delta(T) = k$ Has at Least $k$ Leaves [HW 01, Q4(b) / HW 03, Q2]

#### Formal Proof:
1. Let $T = (V, E)$ be a tree with maximum vertex degree $\Delta(T) = k \ge 2$.  
   Let $r \in V$ be a vertex achieving this maximum degree: $\deg(r) = k$.
2. Consider removing the vertex $r$ from $T$.  
   Since $T$ is connected and acyclic (a tree), deleting $r$ breaks $T$ into exactly $k = \deg(r)$ connected components:
   $$T \setminus \{r\} = T_1 \cup T_2 \cup \dots \cup T_k$$
   where each $T_i$ is itself a tree, and $r$ has exactly one incident edge connecting it to each component $T_i$ (say to vertex $u_i \in V(T_i)$).
3. We examine each component $T_i$ ($1 \le i \le k$):
   - **Case 1: $|V(T_i)| = 1$.**  
     In this case, $V(T_i) = \{u_i\}$. In the original tree $T$, the only neighbor of $u_i$ is $r$. Thus $\deg_T(u_i) = 1$, meaning $u_i$ is a leaf of $T$.
   - **Case 2: $|V(T_i)| \ge 2$.**  
     Since $T_i$ is a tree with at least 2 vertices, it must contain at least 2 leaves in $T_i$ (vertices of degree 1 in $T_i$).  
     At most one of these leaves can be $u_i$ (the vertex adjacent to $r$ in $T$).  
     Therefore, there exists at least one other leaf $v_i \in V(T_i)$ such that $v_i \ne u_i$.  
     Since $v_i \ne u_i$, $v_i$ is not adjacent to $r$ in $T$, which means its degree in $T$ is identical to its degree in $T_i$:
     $$\deg_T(v_i) = \deg_{T_i}(v_i) = 1$$
     Hence, $v_i$ is a leaf of the original tree $T$.
4. In both cases, every component $T_i$ contains at least one leaf of $T$.
5. Since the components $T_1, T_2, \dots, T_k$ are mutually disjoint and none of them contains $r$ (and $\deg_T(r) = k \ge 2$, so $r$ itself is not a leaf), all of these leaves are distinct.
6. Therefore, $T$ contains at least $k$ distinct leaves. $\blacksquare$

---

### Part 2 (13 Points) — Cantor's Diagonalization on Real Numbers Without Digit 7 [HW 04, Q2(a)]

#### Problem:
Let $S \subset (0, 1)$ be the set of all real numbers in $(0, 1)$ whose standard decimal expansion contains no occurrence of the digit 7:
$$S = \left\{ x \in (0, 1) \;\middle|\; x = 0.d_1 d_2 d_3 \dots, \quad \forall i \ge 1: d_i \in \{0, 1, 2, 3, 4, 5, 6, 8, 9\} \right\}$$
Prove using Cantor's Diagonal Argument that $S$ is uncountable.

#### Formal Proof:
1. **Assumption for Contradiction:**  
   Assume that $S$ is countable.  
   Since $S$ is clearly infinite (e.g. $0.1, 0.11, 0.111, \dots \in S$), it must be countably infinite.  
   Therefore, its elements can be completely enumerated in a sequence:
   $$S = \{x_1, x_2, x_3, \dots\}$$
2. **Decimal Representation:**  
   Every number $x_n \in S$ has a unique decimal expansion that does not end in trailing 9s:
   $$x_n = 0.d_{n,1} d_{n,2} d_{n,3} \dots d_{n,k} \dots$$
   where $d_{n,k} \in \{0, 1, 2, 3, 4, 5, 6, 8, 9\}$ for all $n, k \ge 1$.
3. **Construction of the Diagonal Number $y$:**  
   We construct a real number $y = 0.y_1 y_2 y_3 \dots$ by defining each digit $y_n$ based on the diagonal digit $d_{n,n}$:
   $$y_n = \begin{cases} 1 & \text{if } d_{n,n} \ne 1 \\ 2 & \text{if } d_{n,n} = 1 \end{cases}$$
4. **Verification that $y \in S$:**
   - **Range:** Since every digit $y_n \in \{1, 2\}$, we have $0.111\dots \le y \le 0.222\dots$, so $0 < y < 1$, meaning $y \in (0, 1)$.
   - **Forbidden Digit:** Every digit of $y$ is either 1 or 2. Since neither 1 nor 2 equals 7, $y$ contains no occurrence of the digit 7.
   - **Uniqueness of Expansion:** The decimal expansion of $y$ consists strictly of digits 1 and 2. Therefore, it does not end in trailing 9s (nor trailing 0s). Thus, this decimal representation is unique.  
   Consequently, $y$ satisfies all defining conditions of $S$, so $y \in S$.
5. **Deducing the Contradiction:**  
   Since $S = \{x_1, x_2, x_3, \dots\}$ was assumed to be an exhaustive list of all elements in $S$, there must exist some positive integer $m \ge 1$ such that:
   $$y = x_m$$
   However, comparing the $m$-th decimal digits of $y$ and $x_m$:
   - By definition of $y$: if $d_{m,m} = 1$, then $y_m = 2 \ne 1$; and if $d_{m,m} \ne 1$, then $y_m = 1 \ne d_{m,m}$.
   - Thus, $y_m \ne d_{m,m}$.  
   Since neither representation has trailing 9s, two real numbers with differing decimal expansions are distinct. Therefore:
   $$y \ne x_m$$
   This contradicts $y = x_m$.
6. **Conclusion:**  
   Our assumption that $S$ is countable must be false. Hence, $S$ is **uncountable**. $\blacksquare$
