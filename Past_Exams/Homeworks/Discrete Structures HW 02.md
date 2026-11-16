---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 2
topic: "Graph Diameter of Complement, Forest Edges, Cardinality & Explicit Bijections, Disjoint Balls"
status: "To Solve"
solution_file: "[[Discrete Structures HW 02 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - graph_theory
  - graph_diameter
  - forests
  - cardinality
  - bijections
---

# 📝 Discrete Structures — Homework Assignment 2

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Diameter of Complement Graph $\overline{G}$, Forest Edge Counting ($|E| = |V| - k$), Equipotence Operations, Explicit Bijections Without CSB, Countability of Disjoint Balls in $\mathbb{R}^2$ & Concentric Circles.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 02 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Diameter of the Complement of a Disconnected Graph

Let $G = (V, E)$ be a disconnected simple undirected graph.
1. **Find a tight upper bound** on the diameter of the complement graph $\overline{G}$.
   *(Recall: The diameter $\operatorname{diam}(H)$ is the maximum of the shortest path distances between any two vertices in $H$.)*
2. **Prove** that your upper bound is correct for all disconnected graphs $G$.
3. **Show a specific example** of a disconnected graph where the diameter of $\overline{G}$ is strictly less than this upper bound.

> [!tip]- 💡 Hints & Strategy
> - Let $u, v \in V$. If $u$ and $v$ belong to different components of $G$, what is their distance in $\overline{G}$?
> - If $u$ and $v$ belong to the same component of $G$, how can you use a third vertex $w$ from another component to form a path in $\overline{G}$?
> - When is $\operatorname{diam}(\overline{G}) = 1$?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Edge Count of a Forest

Let $G = (V, E)$ be an acyclic undirected graph (a forest) containing exactly $k$ connected components.
**Prove** that the number of edges in $G$ satisfies:
$$|E| = |V| - k$$

> [!tip]- 💡 Hints & Strategy
> - Decompose $G$ into its $k$ connected components $T_1, T_2, \dots, T_k$.
> - What kind of graph is each connected component of an acyclic graph?
> - Use the known edge formula for trees and sum over all components.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Equipotence Under Set Operations

Let $A, B, C, D$ be sets such that $A \sim C$ and $B \sim D$ (meaning $|A| = |C|$ and $|B| = |D|$).
**Prove or disprove** each of the following statements:

1. **Part (a):** $A \times B \sim C \times D$
2. **Part (b):** $A \setminus B \sim C \setminus D$
3. **Part (c):** $A \cup B \sim C \cup D$

> [!tip]- 💡 Hints & Strategy
> - For (a): If $f: A \to C$ and $g: B \to D$ are bijections, construct an explicit map for Cartesian products.
> - For (b) & (c): Can sets have the same size while their intersections with other sets differ completely? Test small finite sets like $A = \{1, 2\}, B = \{2\}, C = \{1, 2\}, D = \{3\}$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Explicit Bijections Without Cantor-Schröder-Bernstein

Prove the equipotence of the following sets by constructing an **explicit bijection** (do **not** use the Cantor-Schröder-Bernstein theorem):

### Part (a): Open Interval vs. Closed Interval
$$(0, 1) \sim [0, 1]$$
where $(0, 1) = \{x \in \mathbb{R} \mid 0 < x < 1\}$ and $[0, 1] = \{x \in \mathbb{R} \mid 0 \le x \le 1\}$.

### Part (b): Cartesian Product vs. Function Space
$$A \times A \sim A^{\{1, 2\}}$$
where $A$ is any arbitrary set, and $A^{\{1, 2\}} = \{f \mid f: \{1, 2\} \to A\}$.

### Part (c): Power Set vs. Characteristic Functions
$$\mathcal{P}(A) \sim \{0, 1\}^A$$
where $A$ is any arbitrary set, and $\{0, 1\}^A = \{f \mid f: A \to \{0, 1\}\}$.

### Part (d): Closed Interval vs. Unit Circle
$$[0, 1] \sim S^1$$
where $S^1 = \{(x, y) \in \mathbb{R}^2 \mid x^2 + y^2 = 1\}$ is the unit circle in the Euclidean plane.

> [!tip]- 💡 Hints & Strategy
> - For (a): Use the "Hilbert Hotel" trick on an infinite countable sequence inside $(0, 1)$, such as $\{1/2, 1/3, 1/4, \dots\}$. Shift elements to accommodate the two endpoints $0$ and $1$.
> - For (b): Map an ordered pair $(a_1, a_2)$ to the function $f(1)=a_1, f(2)=a_2$.
> - For (c): Use indicator functions $\mathbf{1}_S(x)$.
> - For (d): First map $[0, 1)$ bijectively to $S^1$ using angle parameterization $t \mapsto (\cos(2\pi t), \sin(2\pi t))$. Then compose with a bijection $[0, 1] \sim [0, 1)$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Disjoint Geometric Sets in $\mathbb{R}^2$

### Definitions:
- **Circle** of radius $r > 0$ centered at $(x, y)$:
  $$C((x, y), r) = \left\{(x', y') \in \mathbb{R}^2 \;\middle|\; (x - x')^2 + (y - y')^2 = r^2\right\}$$
- **Closed Disk (Ball)** of radius $r > 0$ centered at $(x, y)$:
  $$B((x, y), r) = \left\{(x', y') \in \mathbb{R}^2 \;\middle|\; (x - x')^2 + (y - y')^2 \le r^2\right\}$$

*(You may assume without proof that the rational numbers $\mathbb{Q}$ are dense in $\mathbb{R}$, meaning every open interval $(a, b)$ with $a < b$ contains a rational number $q \in \mathbb{Q}$.)*

### Part (a): Countability of Disjoint Closed Disks
Let $\mathcal{B}$ be an infinite collection of mutually disjoint closed disks in $\mathbb{R}^2$ (meaning no two disks share any point).
**Prove or disprove:** The collection $\mathcal{B}$ must be countable ($|\mathcal{B}| \le \aleph_0$).

### Part (b): Continuum of Disjoint Circles
**Prove or disprove:** There exists an infinite collection of mutually disjoint circles in $\mathbb{R}^2$ whose cardinality is the continuum ($|\mathcal{C}| = \aleph = 2^{\aleph_0}$).

> [!tip]- 💡 Hints & Strategy
> - For (a): Every disk contains an open interior. Can you place a rational point $(q_x, q_y) \in \mathbb{Q}^2$ inside each disk? Since the disks are disjoint, what does this say about the map $\mathcal{B} \to \mathbb{Q}^2$?
> - For (b): Do concentric circles around the origin intersect each other? What is the cardinality of the set of possible radii $r \in (0, 1)$?

> [!quote]- ✍️ Solution Workspace
> 
