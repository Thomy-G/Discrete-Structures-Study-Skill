---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 7
topic: "Anti-Cheating Seating Graph, Planar Graph Bounds, Girth & Euler Formula, Minors"
status: "To Solve"
solution_file: "[[Discrete Structures HW 07 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - bipartite_matching
  - konig_egervary
  - planar_graphs
  - euler_formula
  - graph_minors
---

# 📝 Discrete Structures — Homework Assignment 7

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Maximum Independent Set in Bipartite Seating Grids, Planar Edge & Face Bounds ($|E| \le 3|V|-6$, $|F| \le 2|V|-4$), Girth Dependent Planar Bounds, Complement of Planar Graphs, Face Degrees in Regular Bipartite Planar Graphs, $K_{2,3}$ Graph Minors.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 07 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Optimal Anti-Cheating Exam Seating

An exam hall is represented by an $n \times m$ grid. The available seats are specified by a binary matrix $A \in \{0, 1\}^{n \times m}$, where $A_{i, j} = 1$ if position $(i, j)$ has a seat, and $0$ otherwise.
To prevent cheating, a student seated at $(i, j)$ can only copy from:
- Immediate left: $(i, j-1)$
- Immediate right: $(i, j+1)$
- Top-left diagonal: $(i-1, j-1)$
- Top-right diagonal: $(i-1, j+1)$
*(if those are valid coordinates in the room where a seat exists).*

No two students may be placed in positions where one can cheat from the other.
**Design an algorithm** running in time $O(n^2 m^2)$ that finds the maximum number of students that can be seated simultaneously without cheating. Prove its correctness and analyze its time complexity.

> [!tip]- 💡 Hints & Strategy
> - Construct a conflict graph $G = (V, E)$ where vertices are available seats. An edge exists if one seat can cheat from the other.
> - Notice the column structure: all conflict edges connect vertices in column $j$ to vertices in columns $j - 1$ or $j + 1$. There are **no edges within the same column**!
> - Partition vertices by column parity: $V_1 = \{\text{seats in odd columns}\}$, $V_2 = \{\text{seats in even columns}\}$. Is $G$ bipartite?
> - Placing the maximum number of students without cheating is equivalent to finding the **Maximum Independent Set** $\alpha(G)$.
> - How do you compute $\alpha(G)$ efficiently in a bipartite graph? Use Gallai's Theorem $\alpha(G) = |V| - \tau(G)$ and the König-Egerváry Theorem $\tau(G) = \nu(G)$ (Maximum Bipartite Matching).

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Fundamental Planar Graph Bounds

### Part (a): Disconnected Planar Graphs
Prove that for **every** planar graph $G = (V, E)$ (not necessarily connected) with $|V| \ge 3$:
$$|E| \le 3|V| - 6$$

### Part (b): Planar Face Bound
Prove that for every planar graph $G = (V, E)$ with $|V| \ge 3$, the number of faces $|F|$ in any planar embedding satisfies:
$$|F| \le 2|V| - 4$$

> [!tip]- 💡 Hints & Strategy
> - For (a): If $G$ has $k > 1$ components, can you add edges between the outer faces of adjacent components without violating planarity until $G$ becomes connected?
> - For (b): Combine Part (a) with Euler's Planar Formula $|V| - |E| + |F| = 2$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Girth-Dependent Planar Bounds

Let $G = (V, E)$ be a connected planar graph with $|V| \ge 3$ whose shortest simple cycle has length $d \ge 3$ (meaning the **girth** of $G$ is $d$).

### Part (a): General Edge Bound
**Prove** that:
$$|E| \le \frac{d}{d - 2} (|V| - 2)$$

### Part (b): Triangle-Free Low Degree Vertex
**Conclude** that every triangle-free planar graph ($d \ge 4$) contains a vertex of degree at most $3$:
$$\delta(G) \le 3$$

> [!tip]- 💡 Hints & Strategy
> - For (a): Double count the edge-face incidences $\sum_{f \in F} \deg(f) = 2|E|$. Since the shortest cycle has length $\ge d$, each face boundary must contain at least $d$ edges, so $d|F| \le 2|E|$. Substitute $|F| = 2 - |V| + |E|$ from Euler's Formula.
> - For (b): For $d = 4$, $|E| \le 2|V| - 4$. Assume $\deg(v) \ge 4$ for all $v$ and apply the Handshaking Lemma.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Complements and Unions of Planar Graphs

### Part (a): Non-Planarity of Complements for Large Graphs
**Prove** that for every planar graph $G = (V, E)$ with strictly more than 10 vertices ($|V| > 10$), the complement graph $\overline{G}$ is **non-planar**.

### Part (b): Union of Two Planar Graphs
Let $G = (V, E)$ and $G' = (V, E')$ be two planar graphs on the exact same vertex set $V$.
**Prove** that the union graph $G \cup G' = (V, E \cup E')$ must contain a vertex of degree at most $11$:
$$\delta(G \cup G') \le 11$$

> [!tip]- 💡 Hints & Strategy
> - For (a): Assume $\overline{G}$ is planar. Then $|E| \le 3n - 6$ and $|\overline{E}| \le 3n - 6$. But $|E| + |\overline{E}| = \binom{n}{2}$. Solve $\binom{n}{2} \le 6n - 12$ for $n$.
> - For (b): The total number of edges in $G \cup G'$ is at most $(3n - 6) + (3n - 6) = 6n - 12$. If every vertex had degree $\ge 12$, what would the Handshaking Lemma imply?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Quadrilateral Faces in 3-Regular Bipartite Planar Graphs

Let $G = (V, E)$ be a connected, planar, bipartite, and 3-regular graph where every edge is incident to exactly two distinct faces.
**Prove** that $G$ has at least $6$ quadrilateral faces (faces of degree 4).

> [!tip]- 💡 Hints & Strategy
> - Why can't $G$ have any triangular faces (degree 3) or pentagonal faces (degree 5)? (Because $G$ is bipartite, so all cycles and face boundaries have even length $\ge 4$).
> - Thus, all faces have degree 4 or $\ge 6$.
> - Let $i$ be the number of 4-faces. Express $\sum_{f \in F} \deg(f) \ge 4i + 6(|F| - i) = 6|F| - 2i$.
> - Use $2|E| = 3|V|$ and Euler's formula $|F| = 2 - |V| + |E|$ to solve for $i$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 6: Graph Minor Identification

Prove that the complete bipartite graph $K_{2, 3}$ is a **minor** of the graph shown below:
*(Recall: $H$ is a minor of $G$ if $H$ can be obtained from $G$ by edge deletions, vertex deletions, and edge contractions).*

```
       A ----- B ----- C
      /|               |     / |               |     D  |               |  E
     \ |               | /
      \|               |/
       F ----- G ----- H
```

> [!tip]- 💡 Hints & Strategy
> - Identify the two branch sets of sizes 2 and 3 that will form the vertices of $K_{2,3}$.
> - Contract appropriate edges to merge connected subsets into single super-nodes.

> [!quote]- ✍️ Solution Workspace
> 
