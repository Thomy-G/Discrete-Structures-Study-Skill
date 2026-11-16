---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 3
topic: "Forbidden Word Sequences, Tree Leaves, Regular Graphs, Bipartite Properties, Bridges"
status: "To Solve"
solution_file: "[[Discrete Structures HW 03 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - cardinality
  - trees
  - bipartite_graphs
  - regular_graphs
  - bridges
---

# 📝 Discrete Structures — Homework Assignment 3

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Cardinality of Substring-Free Sequences ($101$-free), Tree Leaves $\ge \Delta$, Odd-Degree Regular Component Parity, Bipartite Degree Bounds, Graph Diameter with Low Degree, Non-existence of Bridges in $k$-Regular Bipartite Graphs.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 03 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Cardinality of $101$-Free Infinite Binary Sequences

An infinite binary sequence is a function $f: \mathbb{N} \to \{0, 1\}$.
Let $A$ be the set of all infinite binary sequences that **do not contain** the substring $101$:
$$A = \left\{ f \in \{0, 1\}^\mathbb{N} \;\middle|\; \forall n \in \mathbb{N}: \Big( f(n) = 1 \land f(n+1) = 0 \implies f(n+2) = 0 \Big) \right\}$$
**Calculate the cardinality** $|A|$ and provide a complete formal proof.

> [!tip]- 💡 Hints & Strategy
> - Trivial upper bound: $A \subseteq \{0, 1\}^\mathbb{N}$, so $|A| \le 2^{\aleph_0} = \aleph$.
> - For the lower bound: Can you construct a family of sequences that never forms $10$ in the first place? For example, sequences made strictly of $00$ and $11$ blocks. How many such sequences are there? Apply Cantor-Schröder-Bernstein.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Leaves in a Tree with Maximum Degree $\Delta$

Let $T = (V, E)$ be a tree with maximum vertex degree $\Delta(T) = \Delta$.
**Prove** that $T$ contains at least $\Delta$ leaves (vertices of degree $1$).

> [!tip]- 💡 Hints & Strategy
> - Choose a vertex $v$ with $\deg(v) = \Delta$ as the root.
> - What happens when you remove $v$? How many components are formed, and what are their leaf properties?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Component Parity in Odd-Degree Regular Graphs

Let $G = (V, E)$ be a $k$-regular disconnected graph.
**Prove** that if $k$ is **odd**, then the number of vertices in **every** connected component of $G$ must be **even**.

> [!tip]- 💡 Hints & Strategy
> - What degree do vertices have within their own connected component?
> - Apply the Handshaking Lemma to an individual connected component.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: True / False Graph Theory Statements

**Prove or disprove** each of the following statements:

### Part (a): 2-Regular Graphs with Even Vertices
Let $G$ be a 2-regular graph with an even number of vertices. Then $G$ is bipartite.

### Part (b): High-Degree Vertex in Connected Bipartite Graphs
There exists a connected bipartite graph with $|V| > 4$ containing a vertex with degree $\deg(v) \ge \frac{3}{4}|V|$.

### Part (c): Cycle Existence Condition
In any graph with $n \ge 3$ vertices and $m \ge n$ edges, there exists at least one cycle.

> [!tip]- 💡 Hints & Strategy
> - For (a): What are the connected components of a 2-regular graph? Can a graph have even total order but be made of two disjoint odd cycles?
> - For (b): Think about complete bipartite graphs $K_{1, n-1}$ (stars).
> - For (c): What is the maximum number of edges in an acyclic graph (forest) on $n$ vertices?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 5: Degree Bounds in Bipartite Partitions

Let $G = (V = R \cup L, E)$ be a bipartite graph with vertex bipartition $(R, L)$.
Suppose that for every vertex $x \in R$, $\deg(x) \ge d$.
**Prove** that:
$$|L| \ge \frac{|R| \cdot d}{\Delta(L)}$$
where $\Delta(L) = \max_{y \in L} \deg(y)$ is the maximum degree among all vertices in $L$.

> [!tip]- 💡 Hints & Strategy
> - Count the total number of edges $|E|$ in two ways (double counting): by summing degrees in $R$ and by summing degrees in $L$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 6: Graph Diameter with Low Maximum Degree

Let $G = (V, E)$ be a connected simple graph on $n > 1$ vertices where every vertex $v \in V$ satisfies:
$$\deg(v) < \sqrt{n - 1}$$
**Prove** that the diameter of $G$ is at least $3$:
$$\operatorname{diam}(G) \ge 3$$

> [!tip]- 💡 Hints & Strategy
> - Assume for contradiction that $\operatorname{diam}(G) \le 2$.
> - For any vertex $u \in V$, all other $n-1$ vertices must lie at distance 1 or 2 from $u$.
> - Upper bound the number of vertices at distance 1 and distance 2 using the maximum degree $\Delta < \sqrt{n-1}$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 7: Non-Existence of Bridges in $k$-Regular Bipartite Graphs

### Definition:
An edge $e \in E$ in a graph $G$ is called a **bridge (cut-edge)** if the number of connected components in $G \setminus \{e\}$ is strictly greater than in $G$.

**Theorem to Prove:**
For any integer $k \ge 2$, every $k$-regular bipartite graph contains **no bridges**.

> [!tip]- 💡 Hints & Strategy
> - Assume for contradiction that $e = (u, v)$ is a bridge, where $u \in A$ and $v \in B$.
> - Removing $e$ breaks the component containing $e$ into two disjoint components $G_1, G_2$.
> - Let $A_1 = A \cap V(G_1)$ and $B_1 = B \cap V(G_1)$.
> - Count the sum of degrees in $A_1$ and $B_1$ inside $G_1$, and reach an arithmetic divisibility contradiction with $k \ge 2$.

> [!quote]- ✍️ Solution Workspace
> 
