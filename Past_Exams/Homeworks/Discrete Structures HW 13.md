---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 13
topic: "Prüfer Codes & Labeled Tree Enumeration, Prescribed Leaves, Inclusion-Exclusion, Degree-Restricted Trees"
status: "To Solve"
solution_file: "[[Discrete Structures HW 13 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - trees
  - prufer_codes
  - cayley_theorem
  - inclusion_exclusion
---

# 📝 Discrete Structures — Homework Assignment 13

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Prüfer Sequence Bijection, Enumeration of Labeled Trees with Prescribed Leaves, Exact Leaf Sets via Principle of Inclusion-Exclusion, Enumeration of Trees with Degrees Restricted to 1 and 3.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 13 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any theorem proved in lectures or recitations regarding Cayley's Formula and Prüfer codes.
- All graphs are assumed to be **finite, simple, and undirected**.

---

## 📌 Question 1: Labeled Trees with Prescribed Leaf Sets

Let $V = \{1, 2, \dots, n\}$ be the vertex labels, where $n \ge 3$ and $1 \le k \le n - 1$.

### Part (a): Trees Where $\{1, \dots, k\}$ are Leaves
How many labeled trees on vertex set $\{1, 2, \dots, n\}$ have the property that the specific vertices $\{1, 2, \dots, k\}$ are **leaves** (meaning $\deg(v) = 1$ for all $v \in \{1, \dots, k\}$)?
*(Note: other vertices in $\{k+1, \dots, n\}$ may also be leaves).*

### Part (b): Trees Where ONLY $\{1, \dots, k\}$ are Leaves
How many labeled trees on vertex set $\{1, 2, \dots, n\}$ have the property that the set of leaves is **precisely** $\{1, 2, \dots, k\}$ (meaning no vertex in $\{k+1, \dots, n\}$ is a leaf)?

> [!tip]- 💡 Hints & Strategy
> - Recall the fundamental property of Prüfer sequences: for any tree $T$ on $n$ vertices with Prüfer code $P(T) \in \{1, \dots, n\}^{n-2}$, the degree of every vertex satisfies:
>   $$\deg(v) = \text{occurrences of } v \text{ in } P(T) + 1$$
> - Therefore, $v$ is a leaf ($\deg(v) = 1$) if and only if $v$ **does not appear** in the Prüfer sequence!
> - For (a): The sequence of length $n - 2$ can only use characters from the alphabet $\{k+1, \dots, n\}$.
> - For (b): The sequence of length $n - 2$ must be formed from $\{k+1, \dots, n\}$ such that **every** element of $\{k+1, \dots, n\}$ appears **at least once** (surjective word count / Principle of Inclusion-Exclusion).

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Trees with Degrees Restricted to 1 and 3

Let $n = 2k$ be an even integer ($k \ge 2$).
How many labeled trees on $n$ vertices have the property that **every vertex has degree either 1 or 3**?

> [!tip]- 💡 Hints & Strategy
> - Use the Handshaking Lemma: $\sum_{v \in V} \deg(v) = 2(n - 1) = 2(2k - 1) = 4k - 2$.
> - Let $\ell$ be the number of degree 1 vertices (leaves), and $m$ be the number of degree 3 vertices.
>   Solve the linear system:
>   $$\ell + m = 2k$$
>   $$\ell + 3m = 4k - 2$$
>   to determine the exact count of internal vertices $m$ and leaves $\ell$.
> - In the Prüfer code of length $n - 2 = 2k - 2$, how many times does each of the $m$ internal vertices appear? (Each appears $3 - 1 = 2$ times).
> - First choose which $m$ vertices have degree 3, then count the permutations of the multiset where each chosen vertex appears twice!

> [!quote]- ✍️ Solution Workspace
> 
