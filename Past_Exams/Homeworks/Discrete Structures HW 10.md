---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 10
topic: "Petersen Graph Class 2, Random Graphs Cycles & Markov, Probabilistic Method Subgraphs, Choice Number"
status: "To Solve"
solution_file: "[[Discrete Structures HW 10 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - chromatic_index
  - petersen_graph
  - random_graphs
  - probabilistic_method
  - list_coloring
---

# 📝 Discrete Structures — Homework Assignment 10

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Petersen Graph is Class 2 ($\chi'(P) = 4$), Cycle Expectation & Markov Bounds in $G(n, p)$, Probabilistic Method for $k$-Colorable Subgraphs ($|E'| \ge |E|(1 - 1/k)$), List Chromatic Bound ($ch(G) \le \lceil \chi(G) \ln n \rceil$).
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 10 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use linearity of expectation, Markov's Inequality, and standard graph theory theorems seen in class.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Chromatic Index of the Petersen Graph

Prove that the **Petersen graph** $P$ is **Class 2**:
$$\chi'(P) = \Delta(P) + 1 = 3 + 1 = 4$$

> [!tip]- 💡 Hints & Strategy
> - By Vizing's Theorem, $\chi'(P) \in \{3, 4\}$.
> - Assume for contradiction that $\chi'(P) = 3$.
> - Then the 15 edges of $P$ can be partitioned into 3 matchings of size 5. Each is a **perfect matching**.
> - What happens when you remove a 1-factor (perfect matching) from a 3-regular graph? You get a 2-factor (a union of 2-regular cycles).
> - Since $P$ has girth 5 and order 10, what are the possible cycle lengths in a 2-factor? (Either a 10-cycle, which is impossible since $P$ is non-Hamiltonian, or two 5-cycles).
> - Can a 5-cycle be edge-colored with 2 colors?

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Simple Cycles in the Erdős-Rényi Random Graph $G(n, p)$

Let $G \sim G(n, p)$ be a random graph on $n$ vertices where each edge appears independently with probability $p \in [0, 1]$.

### Part (a): Expected Number of $k$-Cycles
For any integer $k \ge 3$, determine the exact expectation of the number of simple $k$-cycles:
$$\mathbb{E}[X(k)]$$
*(Verify that your formula behaves correctly for $p = 0$ and $p = 1$).*

### Part (b): Markov Bound on Having $\ge s$ Cycles
Using **Markov's Inequality**, give an upper bound on the probability that $G$ contains at least $s$ simple $k$-cycles:
$$\Pr(X(k) \ge s)$$

### Part (c): Markov Bound on Hamiltonicity
Using your result, find an upper bound on the probability that $G(n, p)$ contains a **Hamiltonian cycle**.

> [!tip]- 💡 Hints & Strategy
> - For (a): How many ordered sequences of $k$ distinct vertices are there? $\frac{n!}{(n-k)!}$. How many such sequences describe the exact same unoriented cycle? ($2k$ ways: $k$ cyclic shifts $\times$ 2 traversal directions). Thus there are $\frac{n!}{2k(n-k)!}$ potential $k$-cycles. Each appears with probability $p^k$.
> - For (b): Markov's inequality: $\Pr(X \ge s) \le \frac{\mathbb{E}[X]}{s}$.
> - For (c): A Hamiltonian cycle is a simple cycle of length $k = n$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Probabilistic Method: Large $k$-Colorable Subgraphs

**Theorem to Prove:**
For every graph $G = (V, E)$ and every integer $k \ge 2$, there exists a $k$-colorable subgraph $G' = (V, E')$ such that:
$$|E'| \ge |E| \left(1 - \frac{1}{k}\right)$$

> [!tip]- 💡 Hints & Strategy
> - Assign each vertex $v \in V$ a color uniformly and independently at random from $\{1, 2, \dots, k\}$.
> - For each edge $e = \{u, v\} \in E$, what is the probability that $u$ and $v$ receive different colors?
> - Define an indicator variable $X_e = 1$ if $e$ is properly colored, $0$ otherwise.
> - Calculate $\mathbb{E}\left[ \sum_{e \in E} X_e \right]$ using Linearity of Expectation.
> - Conclude using the fundamental principle of the probabilistic method: there exists a coloring achieving at least the expected value!

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: List Chromatic Number Bound

Let $G = (V, E)$ be a graph on $n$ vertices. Recall that $ch(G)$ denotes the **list chromatic number** (choice number) of $G$, and $\chi(G)$ denotes the standard chromatic number.
**Prove** that:
$$ch(G) \le \lceil \chi(G) \ln n \rceil$$

> [!tip]- 💡 Hints & Strategy
> - Let $k = \chi(G)$. Partition $V$ into $k$ independent sets $C_1, \dots, C_k$ using a proper $k$-coloring.
> - Let each vertex $v$ be assigned a list $L(v)$ of size $m = \lceil k \ln n \rceil$.
> - For each color $c$ in the palette, pick one of the $k$ color classes uniformly at random with probability $1/k$, and color every vertex in that class whose list contains $c$ with color $c$.
> - What is the probability that a vertex $v$ remains uncolored after all colors in its list have been processed? Use $(1 - 1/k)^m \le e^{-m/k} < 1/n$.
> - Use linearity of expectation to show the expected number of uncolored vertices is $< 1$.

> [!quote]- ✍️ Solution Workspace
> 
