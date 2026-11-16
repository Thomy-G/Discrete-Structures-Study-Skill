---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 8
topic: "Graph Colorings, Four Color Theorem, Odd Cycle Intersections, Nordhaus-Gaddum, Coprime Graphs, Product Colorings"
status: "To Solve"
solution_file: "[[Discrete Structures HW 08 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - graph_coloring
  - planar_graphs
  - four_color_theorem
  - nordhaus_gaddum
  - chromatic_index
  - vizing_theorem
---

# 📝 Discrete Structures — Homework Assignment 8

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Independent Sets in Planar Graphs via Four-Color Theorem, 3-Colorability of Odd Cycles Sharing a Common Vertex, Nordhaus-Gaddum Bound ($\chi(G) + \chi(\overline{G}) \le n+1$), Chromatic Number of Coprime Graphs $\operatorname{Coprime}(n)$, Cartesian Product Vertex & Edge Colorings ($\chi(G \square H)$ and $\chi'(G \square K_2)$).
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 08 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations unless explicitly instructed otherwise (including the Four-Color Theorem and Vizing's Theorem).
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Chromatic Bounds & Structural Colorings

**Prove each of the following independent statements:**

### Part (a): Large Independent Set in Planar Graphs
Let $G = (V, E)$ be a planar graph. Prove that $G$ contains an independent set $A \subseteq V$ of size at least:
$$|A| \ge \frac{|V|}{4}$$

### Part (b): Common Intersection of All Odd Cycles
Let $G = (V, E)$ be a graph in which **all odd cycles share at least one common vertex** $v \in V$ (meaning every odd cycle passes through $v$).
**Prove** that $G$ is 3-colorable:
$$\chi(G) \le 3$$

> [!tip]- 💡 Hints & Strategy
> - For (a): Use the **Four-Color Theorem**: $V = V_1 \;\dot\cup\; V_2 \;\dot\cup\; V_3 \;\dot\cup\; V_4$. Apply the Pigeonhole Principle to the sizes of the 4 color classes.
> - For (b): What kind of graph is $G \setminus \{v\}$? Does it contain any odd cycles? What does König's Bipartite Theorem tell you about $G \setminus \{v\}$? Color $G \setminus \{v\}$ with 2 colors, and assign a 3rd distinct color to $v$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Nordhaus-Gaddum Sum Bound

**Theorem to Prove:**
For every simple graph $G = (V, E)$ on $|V| = n$ vertices, the sum of the chromatic number of $G$ and that of its complement graph $\overline{G}$ satisfies:
$$\chi(G) + \chi(\overline{G}) \le n + 1$$

> [!tip]- 💡 Hints & Strategy
> - Prove by induction on $n$.
> - For the inductive step $n-1 \to n$: Delete an arbitrary vertex $v$ to obtain $G' = G \setminus \{v\}$.
> - Notice that $\deg_G(v) + \deg_{\overline{G}}(v) = n - 1$.
> - Distinguish two cases: either $\deg_G(v) < \chi(G')$ (meaning $v$ can reuse an existing color in $G'$), or both degrees are large.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: The Coprime Graph $\operatorname{Coprime}(n)$

### Definition:
The **Coprime Graph** on $n$ vertices, denoted $\operatorname{Coprime}(n)$, has vertex set:
$$V = \{1, 2, \dots, n\}$$
and an edge exists between $a \ne b$ if and only if they are relatively prime:
$$\{a, b\} \in E \iff \gcd(a, b) = 1$$

Let $\pi(n)$ denote the number of prime numbers less than or equal to $n$.
1. **Find a valid vertex coloring** of $\operatorname{Coprime}(n)$.
2. **Determine the exact chromatic number** $\chi(\operatorname{Coprime}(n))$ as a function of $\pi(n)$, and prove your answer.

> [!tip]- 💡 Hints & Strategy
> - Lower bound: Notice that $\gcd(1, k) = 1$ for all $k$, so vertex 1 is adjacent to all other vertices. Furthermore, any two distinct primes $p \ne q$ satisfy $\gcd(p, q) = 1$. What size clique does $\{1\} \cup \{p \le n \mid p \text{ is prime}\}$ form?
> - Upper bound: Give color 0 to 1. Give colors $1, \dots, \pi(n)$ to each prime. For any composite number $m$, color it with the color of its smallest prime factor! Show no two multiples of the same prime factor can share an edge.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Vertex and Edge Colorings of Cartesian Products

Recall the definition of the Cartesian product $G \square H$.

### Part (a): Vertex Chromatic Number of $G \square H$
**Prove** that for any two graphs $G$ and $H$:
$$\chi(G \square H) = \max\{\chi(G), \; \chi(H)\}$$

### Part (b): Edge Chromatic Index of the Prism $G \square K_2$
**Prove** that for every graph $G$, the prism graph $G \square K_2$ is **Class 1**:
$$\chi'(G \square K_2) = \Delta(G \square K_2) = \Delta(G) + 1$$
*(where $\chi'(H)$ is the edge chromatic index of $H$, and $K_2$ is the single-edge graph on 2 vertices).*

> [!tip]- 💡 Hints & Strategy
> - For (a): Lower bound $\ge \max(\chi(G), \chi(H))$ is immediate because $G \square H$ contains copies of $G$ and $H$ as induced subgraphs. For upper bound $\le k = \max(\chi(G), \chi(H))$, define $c(g, h) = (c_G(g) + c_H(h)) \pmod k$. Check that adjacent vertices always receive different colors.
> - For (b): $G \square K_2$ consists of two identical copies of $G$ connected by a matching of vertical edges $\{(g, 1), (g, 2)\}$. By Vizing's Theorem, $G$ has an edge coloring with $\Delta(G) + 1$ colors. Color both copies with the same scheme. Each vertex $g$ has at least one "missing" color among its incident edges in $G$. Can you color the vertical edge $\{(g, 1), (g, 2)\}$ with that missing color?

> [!quote]- ✍️ Solution Workspace
> 
