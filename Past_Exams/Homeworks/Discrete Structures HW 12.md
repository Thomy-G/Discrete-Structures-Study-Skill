---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 12
topic: "Trees from Edge Deletion, Uniqueness of Perfect Matchings in Trees, Stable Marriage MPDA, Lattice Property, Triangle Deletion Method"
status: "To Solve"
solution_file: "[[Discrete Structures HW 12 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - trees
  - matchings
  - stable_matching
  - gale_shapley
  - probabilistic_method
---

# 📝 Discrete Structures — Homework Assignment 12

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Characterization of Simple Cycles (Edge Deletion Yields a Tree), Uniqueness of Perfect Matching in Trees, Stable Marriage Algorithm Rounds (MPDA), Men-Optimal Lattice Property, Erdős Alteration Method for Triangle-Free Subgraphs.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 12 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Edge-Pruning Characterization of Cycles

Let $G = (V, E)$ be a connected graph with $|V| > 1$.
Suppose that for **every** edge $e \in E$, the graph obtained by deleting $e$:
$$G' = (V, E \setminus \{e\})$$
is a **tree**.
**Prove** that every vertex in $G$ has degree 2 (meaning $G$ is a simple cycle $C_n$).

> [!tip]- 💡 Hints & Strategy
> - First show that no vertex can have degree 1 in $G$ (what happens to connectivity when an edge incident to a leaf is removed?).
> - Next, pick any edge $e = \{u, v\}$. In the tree $T = G \setminus \{e\}$, how many leaves are there?
> - Notice that deleting $e$ only changes the degrees of $u$ and $v$. All other vertices keep their original degree $\ge 2$.
> - What does this imply about the degrees of $u$ and $v$ in $T$, and therefore in $G$?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Uniqueness of Perfect Matchings in Trees

Let $T = (V, E)$ be a tree.
**Prove** that $T$ contains **at most one** perfect matching.

> [!tip]- 💡 Hints & Strategy
> - Assume for contradiction that $T$ has two distinct perfect matchings $M_1 \ne M_2$.
> - Examine the symmetric difference $M_1 \oplus M_2$.
> - What kind of subgraphs form in the symmetric difference of two distinct perfect matchings?
> - Can a tree contain a cycle?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Dynamics of the Men-Proposing Gale-Shapley Algorithm (MPDA)

Consider the Stable Marriage Problem with $n$ men and $n$ women.

### Part (a): Multiplicity of Stable Matchings
Provide an explicit instance with $n = 2$ men and $n = 2$ women that has **strictly more than one** stable matching. Prove why each matching is stable.

### Part (b): Distinct Top Choices
Suppose that every man has a different top-choice woman.
How many rounds does the MPDA algorithm take to terminate?

### Part (c): Identical Preferences
Suppose that all $n$ men have the **exact same preference ranking** over all $n$ women.
How many rounds does the MPDA algorithm take to terminate?

> [!tip]- 💡 Hints & Strategy
> - For (a): Set up symmetric opposing preferences (e.g., Alon prefers Shiri to Miri, Ron prefers Miri to Shiri, while Miri prefers Alon and Shiri prefers Ron).
> - For (b): Can any woman receive more than one proposal in round 1?
> - For (c): In round 1, who do all men propose to? Who is rejected? In round 2, who do the rejected men propose to?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Lattice Property of Stable Matchings

Let $M_1$ and $M_2$ be two valid stable matchings for a given instance of the Stable Marriage Problem.
Define $M$ to be the assignment where **every man is paired with his preferred choice** between his partners in $M_1$ and $M_2$:
$$\mu_M(m) = \max_{\succ_m}\big(\mu_{M_1}(m), \; \mu_{M_2}(m)\big)$$
**Prove** that $M$ is a valid matching, and furthermore, that $M$ is a **stable matching**.

> [!tip]- 💡 Hints & Strategy
> - Part 1 (Valid matching): Assume for contradiction that two men $m, m'$ are matched with the same woman $w$. Then one was matched to $w$ under $M_1$ and the other under $M_2$. Show that $(m, w)$ or $(m', w)$ would form a blocking pair in $M_1$ or $M_2$.
> - Part 2 (Stability): Assume $(m, w)$ is a blocking pair for $M$. Relate this to $M_1$ and $M_2$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Probabilistic Alteration Method for Triangle-Free Subgraphs

Let $G = (V, E)$ be a simple graph on $n$ vertices containing **at most $48n$ triangles**.
**Prove** that $G$ contains a triangle-free induced subgraph on at least:
$$\frac{n}{18}$$
vertices.

> [!tip]- 💡 Hints & Strategy
> - Sample a random subset of vertices $S \subseteq V$ by including each vertex independently with probability $p \in (0, 1)$.
> - Let $X = |S|$ be the number of chosen vertices, $\mathbb{E}[X] = np$.
> - Let $Y$ be the number of triangles that have all 3 vertices in $S$. Show $\mathbb{E}[Y] \le 48n p^3$.
> - Destroy every surviving triangle by deleting one vertex from it. The remaining vertex set has size at least $X - Y$ and is triangle-free.
> - Calculate $\mathbb{E}[X - Y] \ge np - 48np^3$. Optimize over $p$ using calculus!

> [!quote]- ✍️ Solution Workspace
> 
