---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 1
topic: "Order Relations, Graph Degrees, Trees & Leaves, Mantel's Theorem"
status: "To Solve"
solution_file: "[[Discrete Structures HW 01 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - order_theory
  - graph_theory
  - trees
  - extremal_graphs
---

# 📝 Discrete Structures — Homework Assignment 1

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Posets & Total Orders, Degree Handshaking & Pigeonhole, Characterization of Trees, Full Binary Trees & Leaves, Mantel's Theorem ($m \le n^2/4$).
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 01 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- Unless stated otherwise, all graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Order Relations & Posets

### Part (a): Lexicographic Order on $A^n$
Let $A$ be a set equipped with a total order $\le$ on its elements. Define the relation $R$ on $A^n \times A^n$ as follows:
For any $\vec{a} = (a_1, \dots, a_n) \in A^n$ and $\vec{a}' = (a'_1, \dots, a'_n) \in A^n$:
$$(\vec{a}, \vec{a}') \in R \iff \Big(\forall 1 \le i \le n: a_i = a'_i\Big) \;\lor\; \bigvee_{k=1}^n \left( \forall 1 \le i \le k-1: a_i = a'_i \;\land\; a_k < a'_k \right)$$
where $a < a'$ is defined as $a \le a' \land a \ne a'$.

**Prove** that $R$ is a **total order** (linear order) on $A^n$.

> [!tip]- 💡 Hints & Strategy
> - Verify all four conditions: Reflexivity, Antisymmetry, Transitivity, and Totality (strongly connected).
> - For antisymmetry and transitivity: If $\vec{a} \ne \vec{b}$, consider the minimal index $i \in \{1, \dots, n\}$ where $a_i \ne b_i$.
> - For totality: Use the fact that $\le$ is a total order on $A$, meaning for any two distinct elements $a_i \ne b_i$, either $a_i < b_i$ or $b_i < a_i$.

> [!quote]- ✍️ Solution Workspace (Part a)
> 

---

### Part (b): Poset of Equivalence Relations by Class Count
Let $X = \{1, 2, 3, \dots, 10\}$. Let $O$ be the set of all equivalence relations on $X$. Define a relation $\le$ on $O$ by the rule:
$$R_1 \le R_2 \iff (|X/R_1| < |X/R_2|) \;\lor\; (R_1 = R_2)$$
where $|X/R_i|$ denotes the number of equivalence classes induced by $R_i$ on $X$.

1. **Prove** that $\le$ is a **partial order** on $O$.
2. **Prove or disprove:** Is $(O, \le)$ a **total order**?
3. **Find**, if they exist, the **least element** (minimum) in $(O, \le)$ and the **greatest element** (maximum) in $(O, \le)$.

> [!tip]- 💡 Hints & Strategy
> - For (1): Use the strict ordering $<$ on the natural numbers $\mathbb{N}$ to establish antisymmetry and transitivity.
> - For (2): Can you find two *distinct* equivalence relations $R_1 \ne R_2$ that divide $\{1, \dots, 10\}$ into the exact same number of classes (e.g., both having 9 classes)? If so, can either $R_1 \le R_2$ or $R_2 \le R_1$ hold?
> - For (3): What are the minimum and maximum possible values of $|X/R|$ for an equivalence relation on a 10-element set? Which specific relations achieve these extreme counts?

> [!quote]- ✍️ Solution Workspace (Part b)
> 

---

### Part (c): Componentwise Vector Order on $\mathbb{R}^n$
Define a relation $\le$ on $\mathbb{R}^n$ by componentwise comparison:
$$\vec{v} \le \vec{u} \iff \forall i \in \{1, \dots, n\}, \; v_i \le u_i$$

**Prove whether** this relation is a **partial order** or a **total order** on $\mathbb{R}^n$.

> [!tip]- 💡 Hints & Strategy
> - Reflexivity, antisymmetry, and transitivity hold coordinate-by-coordinate from $(\mathbb{R}, \le)$.
> - For totality: What happens when $n \ge 2$? Consider $(1, 2)$ and $(2, 1)$.

> [!quote]- ✍️ Solution Workspace (Part c)
> 

---

## 📌 Question 2: Pigeonhole Principle on Vertex Degrees

**Theorem to Prove:**
In every simple undirected graph $G = (V, E)$ with $|V| = n \ge 2$ vertices, there exist at least two vertices with the exact same degree:
$$\exists u, v \in V, \; u \ne v \quad \text{such that} \quad \deg(u) = \deg(v)$$

> [!tip]- 💡 Hints & Strategy
> - What are the theoretically possible degree values for a vertex in a simple graph on $n$ vertices? $\{0, 1, \dots, n-1\}$.
> - Can a graph simultaneously contain an isolated vertex (degree $0$) and a dominating vertex (degree $n-1$)?
> - Count the available pigeonholes vs. the $n$ vertices.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Characterization of Trees by Unique Paths

Let $G = (V, E)$ be an undirected graph on $|V| = n$ vertices.
**Prove** that $G$ has $n-1$ edges and contains no cycles if and only if there exists a unique simple path between every pair of vertices in $G$.

$$\Big(|E| = n-1 \;\land\; G \text{ is acyclic}\Big) \iff \Big(\forall u, v \in V, \; \exists! \text{ simple path between } u \text{ and } v\Big)$$

> [!tip]- 💡 Hints & Strategy
> - $(\implies)$ Recall that acyclic + $(n-1)$ edges implies connected, and hence a tree. In any connected acyclic graph, existence of paths comes from connectivity; uniqueness comes from acyclicity (assume two paths and trace their symmetric difference/cycle).
> - $(\impliedby)$ Unique path $\implies$ connected and acyclic $\implies$ tree $\implies |E| = n-1$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Full Binary Trees & Leaf Counts

### Definition
A **full binary rooted tree** is a rooted tree where:
- The root vertex has degree $2$.
- Every internal vertex (neither the root nor a leaf) has degree $3$.
- Leaves are vertices of degree $1$.

### Part (a): Leaf Formula
Prove that the number of leaves in a full binary rooted tree with $n$ vertices is:
$$\ell = \frac{n + 1}{2}$$

### Part (b): Tree Leaves and Maximum Degree
Let $T = (V, E)$ be any tree with maximum degree $\Delta(T) = k$.
**Prove** that $T$ contains at least $k$ leaves.

> [!tip]- 💡 Hints & Strategy
> - For Part (a): Method 1 (Sum of degrees / Handshaking): Let $\ell$ be leaves, $i$ be internal vertices. Total vertices $n = 1 + i + \ell$. Sum of degrees is $2(n-1) = 2 \cdot 1 + 3i + 1 \cdot \ell$. Solve for $\ell$! Method 2: Induction by pruning two sibling leaves.
> - For Part (b): Root the tree at the vertex $r$ of maximum degree $\deg(r) = k$. How many disjoint subtrees branch out from $r$? Does each non-trivial branch contain at least one leaf?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Mantel's Theorem & Triangle-Free Graphs (Challenging)

Let $G = (V, E)$ be a simple undirected graph on $n > 1$ vertices with $m = |E|$ edges containing **no triangle** ($C_3$ subgraph). Assume $n$ is **even**.

### Part (a): Upper Bound on Edges
**Prove** that:
$$m \le \frac{n^2}{4}$$
*(Hint: Use mathematical induction on even $n$.)*

### Part (b): Extremal Graph Structure
Describe the exact structure of the graph achieving the equality $m = \frac{n^2}{4}$, and verify that it contains no triangles.

### Part (c): Triangle Forced by $k^2 + 1$ Edges
**Without using Part (a)**, prove by induction on $k \ge 2$ that if a graph contains $n = 2k$ vertices and:
$$m = k^2 + 1$$
edges, then $G$ must contain at least one triangle ($C_3$).

> [!tip]- 💡 Hints & Strategy
> - For Part (a): Base case $n=2$: $m \le 1 = 2^2/4$. Inductive step: Pick two adjacent vertices $u, v \in V$. Since there are no triangles, $N(u) \cap N(v) = \emptyset$, so the number of edges incident to $\{u, v\}$ is $1 + (\deg(u)-1) + (\deg(v)-1) \le 1 + (n-2) = n-1$. Remove $u$ and $v$ and apply the induction hypothesis to the remaining $n-2$ vertices.
> - For Part (b): Consider the complete bipartite graph $K_{n/2, n/2}$.
> - For Part (c): Base case $k=2$: $n=4, m = 2^2+1 = 5$. Since $K_4$ has 6 edges, removing 1 edge leaves $K_4 \setminus e$, which has two triangles. For the inductive step, remove an edge $(u, v)$ and bound the edges lost when deleting $\{u, v\}$.

> [!quote]- ✍️ Solution Workspace
> 
