---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 2
topic: "Graph Diameter of Complement, Forest Edges, Cardinality & Explicit Bijections, Disjoint Balls"
problem_file: "[[Discrete Structures HW 02]]"
tags:
  - solution
  - discrete_structures
  - graph_theory
  - graph_diameter
  - forests
  - cardinality
  - bijections
---

# 🛡️ Discrete Structures — Homework Assignment 2 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 02|View Unsolved Assignment]]
> - **Topics Covered:** Graph Diameter Bounds on Complements, Forest Edge Invariant $|E| = |V| - k$, Set Equipotence Counterexamples, Explicit Bijections (Hilbert Hotel, S1, Function Spaces), Density of Rationals & Disjoint Disks.

---

## 📌 Solution 1: Diameter of the Complement of a Disconnected Graph

**Problem:** Find a tight upper bound for $\operatorname{diam}(\overline{G})$ when $G$ is disconnected, prove it, and provide an example where the diameter is strictly smaller.

### 1. Tight Upper Bound: $\operatorname{diam}(\overline{G}) \le 2$

### 2. Formal Proof:
Let $G = (V, E)$ be a disconnected graph. Then $V$ is partitioned into $k \ge 2$ connected components $C_1, C_2, \dots, C_k$.
By definition of the complement graph $\overline{G} = (V, \overline{E})$, an edge $(x, y) \in \overline{E} \iff (x, y) \notin E$.

Let $u, v \in V$ be any two distinct vertices. We examine their locations in $G$:

- **Case 1: $u$ and $v$ belong to different components of $G$.**
  - Suppose $u \in C_i$ and $v \in C_j$ with $i \ne j$.
  - By definition of components, there is no path between $u$ and $v$ in $G$, so in particular $(u, v) \notin E$.
  - Therefore, $(u, v) \in \overline{E}$, which means:
    $$\operatorname{dist}_{\overline{G}}(u, v) = 1$$

- **Case 2: $u$ and $v$ belong to the same component $C_i$ of $G$.**
  - Since $G$ is disconnected, there exists at least one other component $C_j$ ($j \ne i$).
  - Choose any vertex $w \in C_j$.
  - Since $u \in C_i$ and $w \in C_j$, $(u, w) \notin E \implies (u, w) \in \overline{E}$.
  - Similarly, since $v \in C_i$ and $w \in C_j$, $(v, w) \notin E \implies (v, w) \in \overline{E}$.
  - Hence, the 2-edge path $u - w - v$ exists in $\overline{G}$.
  - Therefore:
    $$\operatorname{dist}_{\overline{G}}(u, v) \le 2$$

Since every pair of vertices satisfies $\operatorname{dist}_{\overline{G}}(u, v) \le 2$, we conclude:
$$\operatorname{diam}(\overline{G}) \le 2$$

### 3. Tightness & Example Where Diameter $< 2$:
- **Tightness:** Consider $G = K_2 \cup K_2$ (two disjoint edges, components $\{u_1, u_2\}$ and $\{v_1, v_2\}$).
  In $\overline{G}$, $(u_1, u_2) \notin \overline{E}$, so $\operatorname{dist}_{\overline{G}}(u_1, u_2) = 2$ via path $u_1 - v_1 - u_2$. Thus $\operatorname{diam}(\overline{G}) = 2$.
- **Strictly Smaller Example ($\diam = 1$):**
  Let $G = \overline{K_n}$ for $n \ge 2$ (the totally disconnected / empty graph with no edges).
  Then the complement graph is the complete graph:
  $$\overline{G} = K_n$$
  In $K_n$, every pair of vertices is directly adjacent, so $\operatorname{dist}_{K_n}(u, v) = 1$ for all $u \ne v$.
  Therefore, $\operatorname{diam}(\overline{G}) = 1 < 2$. $\blacksquare$

---

## 📌 Solution 2: Edge Count of a Forest

**Problem:** Let $G = (V, E)$ be an acyclic graph with $k$ connected components. Prove that $|E| = |V| - k$.

### Formal Proof:
1. Decompose the forest $G$ into its $k$ pairwise disjoint connected components:
   $$G = T_1 \cup T_2 \cup \dots \cup T_k$$
   where $V = V(T_1) \cup \dots \cup V(T_k)$ and $E = E(T_1) \cup \dots \cup E(T_k)$, with $V(T_i) \cap V(T_j) = \emptyset$ for $i \ne j$.
2. For each $i \in \{1, \dots, k\}$:
   - Component $T_i$ is connected by definition of connected components.
   - Component $T_i$ contains no cycles because any cycle in $T_i$ would be a cycle in $G$, which is acyclic.
   - Therefore, each component $T_i$ is a **tree**.
3. By the fundamental tree theorem, every tree on $n_i = |V(T_i)|$ vertices contains exactly $n_i - 1$ edges:
   $$|E(T_i)| = |V(T_i)| - 1$$
4. Summing the edges across all $k$ disjoint components:
   $$|E| = \sum_{i=1}^k |E(T_i)| = \sum_{i=1}^k (|V(T_i)| - 1) = \left( \sum_{i=1}^k |V(T_i)| \right) - \sum_{i=1}^k 1$$
5. Since the vertex sets are pairwise disjoint, $\sum_{i=1}^k |V(T_i)| = |V|$. Thus:
   $$|E| = |V| - k$$
   $\blacksquare$

---

## 📌 Solution 3: Equipotence Under Set Operations

Given $A \sim C$ and $B \sim D$:

### Part (a): $A \times B \sim C \times D$ (TRUE)
- **Proof:**
  Since $A \sim C$ and $B \sim D$, there exist bijections:
  $$f: A \to C \quad \text{and} \quad g: B \to D$$
  Define the product map $h: A \times B \to C \times D$ by:
  $$h(a, b) = (f(a), g(b))$$
  - **Injective:** If $h(a_1, b_1) = h(a_2, b_2)$, then $(f(a_1), g(b_1)) = (f(a_2), g(b_2))$, which means $f(a_1) = f(a_2)$ and $g(b_1) = g(b_2)$. Since $f$ and $g$ are injective, $a_1 = a_2$ and $b_1 = b_2$, so $(a_1, b_1) = (a_2, b_2)$.
  - **Surjective:** For any $(c, d) \in C \times D$, by surjectivity of $f$ and $g$, there exist $a \in A$ and $b \in B$ such that $f(a) = c$ and $g(b) = d$. Then $h(a, b) = (c, d)$.
  Hence $h$ is a bijection, so $A \times B \sim C \times D$. $\blacksquare$

---

### Part (b): $A \setminus B \sim C \setminus D$ (FALSE)
- **Counterexample:**
  Let:
  $$A = \{1, 2\}, \quad B = \{2\}$$
  $$C = \{1, 2\}, \quad D = \{3\}$$
  - Clearly $|A| = 2 = |C|$, so $A \sim C$.
  - Clearly $|B| = 1 = |D|$, so $B \sim D$.
  - However:
    $$A \setminus B = \{1, 2\} \setminus \{2\} = \{1\} \implies |A \setminus B| = 1$$
    $$C \setminus D = \{1, 2\} \setminus \{3\} = \{1, 2\} \implies |C \setminus D| = 2$$
  Since $1 \ne 2$, $A \setminus B \not\sim C \setminus D$. $\blacksquare$

---

### Part (c): $A \cup B \sim C \cup D$ (FALSE)
- **Counterexample:**
  Let:
  $$A = \{1\}, \quad B = \{2\}$$
  $$C = \{1\}, \quad D = \{1\}$$
  - $|A| = 1 = |C| \implies A \sim C$.
  - $|B| = 1 = |D| \implies B \sim D$.
  - However:
    $$A \cup B = \{1, 2\} \implies |A \cup B| = 2$$
    $$C \cup D = \{1\} \implies |C \cup D| = 1$$
  Since $2 \ne 1$, $A \cup B \not\sim C \cup D$. $\blacksquare$
  *(Note: The claim becomes true only if $A \cap B = \emptyset$ and $C \cap D = \emptyset$.)*

---

## 📌 Solution 4: Explicit Bijections Without Cantor-Schröder-Bernstein

### Part (a): $(0, 1) \sim [0, 1]$

#### Explicit Construction (Hilbert Hotel on Sequence):
Define the countably infinite sequence of distinct points inside $(0, 1)$:
$$S = \left\{ \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \frac{1}{5}, \dots \right\} = \left\{ \frac{1}{n} \;\middle|\; n \in \mathbb{N}, n \ge 2 \right\}$$
We construct the function $f: [0, 1] \to (0, 1)$ as follows:
$$f(x) = \begin{cases}
\frac{1}{2} & x = 0 \\[4pt]
\frac{1}{3} & x = 1 \\[4pt]
\frac{1}{n + 2} & x = \frac{1}{n} \quad (n \ge 2) \\[4pt]
x & x \notin \{0, 1\} \cup S
\end{cases}$$

- **Injectivity:**
  - Elements in $\{0, 1\} \cup S$ are mapped bijectively to $S = \{1/2, 1/3, 1/4, \dots\}$:
    $0 \mapsto 1/2$, $1 \mapsto 1/3$, $1/2 \mapsto 1/4$, $1/3 \mapsto 1/5$, etc. Each value in $S$ has a unique pre-image.
  - Elements outside $\{0, 1\} \cup S$ are mapped by the identity $x \mapsto x$, landing entirely outside $S$.
  - Therefore, no two distinct points have the same image.
- **Surjectivity:**
  - Any $y \in S$ has an explicit pre-image: $1/2 \leftarrow 0$, $1/3 \leftarrow 1$, and $1/(n+2) \leftarrow 1/n$ ($n \ge 2$).
  - Any $y \in (0, 1) \setminus S$ has pre-image $x = y \in [0, 1] \setminus (\{0, 1\} \cup S)$.
Thus $f$ is a direct, explicit bijection, proving $(0, 1) \sim [0, 1]$. $\blacksquare$

---

### Part (b): $A \times A \sim A^{\{1, 2\}}$

#### Explicit Construction:
Define $F: A \times A \to A^{\{1, 2\}}$ by:
$$F((a, b)) = f_{(a, b)} \quad \text{where} \quad f_{(a, b)}(1) = a, \; f_{(a, b)}(2) = b$$

- **Invertibility:**
  Define the inverse map $G: A^{\{1, 2\}} \to A \times A$ by:
  $$G(\varphi) = (\varphi(1), \varphi(2))$$
  - For any $(a, b) \in A \times A$:
    $$G(F((a, b))) = G(f_{(a, b)}) = (f_{(a, b)}(1), f_{(a, b)}(2)) = (a, b)$$
  - For any function $\varphi: \{1, 2\} \to A$:
    $$F(G(\varphi)) = F((\varphi(1), \varphi(2))) = f_{(\varphi(1), \varphi(2))}$$
    which evaluates to $f(1) = \varphi(1)$ and $f(2) = \varphi(2)$, so $f = \varphi$.
Since $F$ has a two-sided inverse $G$, $F$ is a bijection. $\blacksquare$

---

### Part (c): $\mathcal{P}(A) \sim \{0, 1\}^A$

#### Explicit Construction:
For each subset $S \subseteq A$, define its indicator function $\mathbf{1}_S \in \{0, 1\}^A$:
$$\mathbf{1}_S(x) = \begin{cases} 1 & x \in S \\[2pt] 0 & x \notin S \end{cases}$$
Define the mapping $\Phi: \mathcal{P}(A) \to \{0, 1\}^A$ by $\Phi(S) = \mathbf{1}_S$.

- **Invertibility:**
  Define $\Psi: \{0, 1\}^A \to \mathcal{P}(A)$ by taking the pre-image of $1$:
  $$\Psi(f) = f^{-1}(\{1\}) = \{x \in A \mid f(x) = 1\}$$
  - For any $S \subseteq A$:
    $$\Psi(\Phi(S)) = \Psi(\mathbf{1}_S) = \{x \in A \mid \mathbf{1}_S(x) = 1\} = S$$
  - For any $f: A \to \{0, 1\}$:
    $$\Phi(\Psi(f)) = \mathbf{1}_{f^{-1}(\{1\})}$$
    Since $f(x) \in \{0, 1\}$, $\mathbf{1}_{f^{-1}(\{1\})}(x) = 1 \iff f(x) = 1 \iff f(x) = \mathbf{1}(x)$. Thus $\Phi(\Psi(f)) = f$.
Since $\Phi$ is invertible, it is an explicit bijection. $\blacksquare$

---

### Part (d): $[0, 1] \sim S^1$

#### Explicit Construction:
1. First, establish a bijection between the half-open interval $[0, 1)$ and the unit circle $S^1$ via the standard trigonometric parametrization:
   $$\psi: [0, 1) \to S^1, \quad \psi(t) = (\cos(2\pi t), \sin(2\pi t))$$
   - $\psi$ is injective: $2\pi t_1 = 2\pi t_2 + 2\pi k \implies t_1 - t_2 = k \in \mathbb{Z}$. Since $t_1, t_2 \in [0, 1)$, $|t_1 - t_2| < 1$, so $k = 0 \implies t_1 = t_2$.
   - $\psi$ is surjective: Every point on the unit circle has a unique polar angle $\theta \in [0, 2\pi)$, giving $t = \frac{\theta}{2\pi} \in [0, 1)$.
2. Next, establish a bijection between $[0, 1]$ and $[0, 1)$ using the shift trick on $T = \{1, 1/2, 1/3, \dots\} = \{1/n \mid n \in \mathbb{N}\}$:
   $$\rho: [0, 1] \to [0, 1), \quad \rho(x) = \begin{cases}
   \frac{1}{n + 1} & x = \frac{1}{n} \quad (n \in \mathbb{N}) \\[4pt]
   x & x \notin T
   \end{cases}$$
   $\rho$ is a bijection (it shifts $1 \mapsto 1/2, 1/2 \mapsto 1/3, \dots$ leaving all other points fixed, freeing up the endpoint $1$).
3. The composition $h = \psi \circ \rho: [0, 1] \to S^1$ is a composition of two explicit bijections, hence an explicit bijection. $\blacksquare$

---

## 📌 Solution 5: Disjoint Geometric Sets in $\mathbb{R}^2$

### Part (a): Countability of Disjoint Closed Disks (TRUE)

**Claim:** Any collection $\mathcal{B}$ of mutually disjoint closed disks in $\mathbb{R}^2$ must be at most countable ($|\mathcal{B}| \le \aleph_0$).

#### Formal Proof:
1. Let $B_i = B(c_i, r_i) \in \mathcal{B}$ with center $c_i = (x_i, y_i)$ and radius $r_i > 0$.
2. The interior $\operatorname{int}(B_i)$ contains an open square centered at $c_i$ with side length $\frac{r_i}{\sqrt{2}}$:
   $$Q_i = \left( x_i - \frac{r_i}{2}, \; x_i + \frac{r_i}{2} \right) \times \left( y_i - \frac{r_i}{2}, \; y_i + \frac{r_i}{2} \right) \subset B_i$$
3. By the **density of the rational numbers** $\mathbb{Q}$ in $\mathbb{R}$:
   - There exists a rational number $q_{x, i} \in \mathbb{Q}$ such that $x_i - \frac{r_i}{2} < q_{x, i} < x_i + \frac{r_i}{2}$.
   - There exists a rational number $q_{y, i} \in \mathbb{Q}$ such that $y_i - \frac{r_i}{2} < q_{y, i} < y_i + \frac{r_i}{2}$.
4. Therefore, the point $p_i = (q_{x, i}, q_{y, i})$ belongs to $\mathbb{Q}^2$ and lies strictly inside the interior of $B_i$:
   $$p_i \in \operatorname{int}(B_i) \subset B_i$$
5. For each disk $B_i \in \mathcal{B}$, choose one such rational point $p_i$ (by the Axiom of Choice, or by taking the first point in a standard canonical enumeration of $\mathbb{Q}^2$).
   This defines a function:
   $$\phi: \mathcal{B} \to \mathbb{Q} \times \mathbb{Q}, \quad \phi(B_i) = p_i$$
6. **Injectivity of $\phi$:**
   Suppose $B_i \ne B_j$. Since the disks in $\mathcal{B}$ are mutually disjoint:
   $$B_i \cap B_j = \emptyset$$
   Since $p_i \in B_i$ and $p_j \in B_j$, $p_i$ cannot equal $p_j$ (as that would mean $p_i \in B_i \cap B_j$).
   Thus $\phi(B_i) \ne \phi(B_j)$, so $\phi$ is strictly injective.
7. Since $\mathbb{Q}$ is countable, $\mathbb{Q} \times \mathbb{Q}$ is countable ($|\mathbb{Q} \times \mathbb{Q}| = \aleph_0$).
8. Since there exists an injection from $\mathcal{B}$ into a countable set, $\mathcal{B}$ must be at most countable:
   $$|\mathcal{B}| \le |\mathbb{Q}^2| = \aleph_0$$
   $\blacksquare$

---

### Part (b): Continuum of Disjoint Circles in $\mathbb{R}^2$ (TRUE)

**Claim:** There exists a collection $\mathcal{C}$ of mutually disjoint circles in $\mathbb{R}^2$ with cardinality $|\mathcal{C}| = \aleph = 2^{\aleph_0}$.

#### Formal Construction:
1. Consider the family of **concentric circles** centered at the origin $(0, 0)$ with radii chosen from the open interval $(0, 1)$:
   $$\mathcal{C} = \{ C((0, 0), r) \mid r \in (0, 1) \}$$
   where $C((0, 0), r) = \{ (x, y) \in \mathbb{R}^2 \mid x^2 + y^2 = r^2 \}$.
2. **Mutual Disjointness:**
   Let $r_1, r_2 \in (0, 1)$ with $r_1 \ne r_2$.
   For any point $(x, y) \in C((0, 0), r_1)$, the Euclidean distance to the origin is $\sqrt{x^2 + y^2} = r_1$.
   For any point $(x', y') \in C((0, 0), r_2)$, the distance to the origin is $r_2$.
   Since $r_1 \ne r_2$, no point can simultaneously satisfy both equations.
   Therefore:
   $$C((0, 0), r_1) \cap C((0, 0), r_2) = \emptyset \quad \forall r_1 \ne r_2$$
3. **Cardinality Calculation:**
   Define the map $g: (0, 1) \to \mathcal{C}$ by $g(r) = C((0, 0), r)$.
   - $g$ is surjective by definition of $\mathcal{C}$.
   - $g$ is injective because different radii produce different sets of points.
   Therefore, $g$ is a bijection, which implies:
   $$|\mathcal{C}| = |(0, 1)| = \aleph$$
   Thus, there exists an uncountable family (of continuum cardinality $\aleph$) of pairwise disjoint circles in $\mathbb{R}^2$. $\blacksquare$
