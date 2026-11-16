---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 13
topic: "Prüfer Codes & Labeled Tree Enumeration, Prescribed Leaves, Inclusion-Exclusion, Degree-Restricted Trees"
problem_file: "[[Discrete Structures HW 13]]"
tags:
  - solution
  - discrete_structures
  - trees
  - prufer_codes
  - cayley_theorem
  - inclusion_exclusion
---

# 🛡️ Discrete Structures — Homework Assignment 13 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 13|View Unsolved Assignment]]
> - **Topics Covered:** Prüfer Code Bijective Invariants, Leaf Non-Occurrence Criterion, Inclusion-Exclusion for Exact Leaf Sets, Multiset Permutations for Degree-Constrained Tree Enumeration.

---

## 📌 Solution 1: Labeled Trees with Prescribed Leaf Sets

### Background & The Prüfer Bijection:
By **Cayley's Tree Enumeration Theorem**, there is a bijection between labeled trees on $V = \{1, 2, \dots, n\}$ and sequences of length $n - 2$ over the alphabet $\{1, 2, \dots, n\}$ (known as **Prüfer codes**).
Under this bijection, the degree of every vertex $v \in V$ satisfies:
$$\deg(v) = \operatorname{count}(v) + 1$$
where $\operatorname{count}(v)$ is the number of times vertex $v$ appears in the Prüfer sequence.
Consequently:
$$v \text{ is a leaf} \iff \deg(v) = 1 \iff \operatorname{count}(v) = 0$$
That is, **a vertex is a leaf if and only if it never appears in the Prüfer sequence**.

---

### Part (a): Trees Where $\{1, \dots, k\}$ are Leaves
1. The condition requires that vertices $1, 2, \dots, k$ are all leaves.
2. By the criterion above, this means that none of the numbers $1, 2, \dots, k$ can appear anywhere in the Prüfer sequence.
3. Thus, the Prüfer sequence of length $n - 2$ must be composed entirely of elements from the remaining set:
   $$\{k + 1, \; k + 2, \; \dots, \; n\}$$
4. The size of this allowed alphabet is:
   $$n - k$$
5. Any sequence of length $n - 2$ chosen from an alphabet of size $n - k$ forms a valid Prüfer sequence where $\{1, \dots, k\}$ are guaranteed to be leaves (other vertices in $\{k+1, \dots, n\}$ may or may not also be leaves).
6. The total number of such sequences is:
   $$(n - k)^{n - 2}$$
Therefore, the number of such labeled trees is $(n - k)^{n - 2}$. $\blacksquare$

---

### Part (b): Trees Where ONLY $\{1, \dots, k\}$ are Leaves
1. The condition requires that:
   - Vertices $1, 2, \dots, k$ are leaves (so they appear **0 times** in the Prüfer sequence).
   - No other vertex in $\{k + 1, \dots, n\}$ is a leaf (so every vertex in $\{k + 1, \dots, n\}$ must appear **at least once** in the Prüfer sequence).
2. Let $\Sigma = \{k + 1, \dots, n\}$ with $|\Sigma| = n - k$.
   We must count the number of sequences of length $n - 2$ over alphabet $\Sigma$ that contain **every** element of $\Sigma$ at least once (i.e. surjective words $\{1, \dots, n-2\} \twoheadrightarrow \Sigma$).
3. We solve this using the **Principle of Inclusion-Exclusion (PIE)**:
   - Let $S$ be the set of all $(n - k)^{n - 2}$ sequences over $\Sigma$.
   - For each element $x \in \Sigma$, let $A_x$ be the bad property that $x$ does **not** appear in the sequence.
   - For any subset of $i$ elements $J \subseteq \Sigma$ ($|J| = i$), the number of sequences that avoid all elements of $J$ is $(|\Sigma| - i)^{n - 2} = (n - k - i)^{n - 2}$.
   - The number of ways to choose $i$ excluded elements from $\Sigma$ is $\binom{n - k}{i}$.
4. By the Principle of Inclusion-Exclusion, the number of valid sequences is:
   $$N = \sum_{i=0}^{n - k} (-1)^i \binom{n - k}{i} (n - k - i)^{n - 2}$$
   *(Note: If $n - 2 < n - k \iff k < 2$, this sum is 0, which correctly reflects that a tree on $n \ge 2$ vertices must have at least 2 leaves).* $\blacksquare$

---

## 📌 Solution 2: Trees with Degrees Restricted to 1 and 3

**Problem:** Find the number of labeled trees on $n = 2k$ vertices where every vertex has degree 1 or 3.

### Step 1: Determine the Number of Degree-1 and Degree-3 Vertices
1. Let $T = (V, E)$ be a tree on $n = 2k$ vertices ($k \ge 2$).
   The total number of edges is:
   $$|E| = n - 1 = 2k - 1$$
2. By the **Handshaking Lemma**:
   $$\sum_{v \in V} \deg(v) = 2|E| = 2(2k - 1) = 4k - 2$$
3. Let $\ell$ be the number of vertices of degree 1 (leaves), and let $m$ be the number of vertices of degree 3.
   Every vertex has degree 1 or 3, so:
   $$\ell + m = n = 2k$$
4. Substituting into the degree sum:
   $$\ell \cdot 1 + m \cdot 3 = 4k - 2$$
   $$\ell + 3m = 4k - 2$$
5. Subtract the vertex equation from the degree equation:
   $$(\ell + 3m) - (\ell + m) = (4k - 2) - 2k$$
   $$2m = 2k - 2 \implies m = k - 1$$
6. Now solve for the number of leaves $\ell$:
   $$\ell = 2k - m = 2k - (k - 1) = k + 1$$
Thus, **every such tree must contain exactly $k - 1$ vertices of degree 3 and $k + 1$ vertices of degree 1**.

---

### Step 2: Use Prüfer Codes to Count the Trees
1. The Prüfer sequence of any tree on $n = 2k$ vertices has length:
   $$L = n - 2 = 2k - 2$$
2. Recall that the number of appearances of vertex $v$ in the Prüfer sequence is:
   $$\operatorname{count}(v) = \deg(v) - 1$$
   - Each of the $k + 1$ leaves has degree 1, so it appears $1 - 1 = 0$ times.
   - Each of the $k - 1$ vertices of degree 3 has degree 3, so it appears $3 - 1 = 2$ times.
3. Notice that the total number of entries in the Prüfer code accounted for by the $k - 1$ degree-3 vertices is:
   $$(k - 1) \times 2 = 2k - 2$$
   This exactly fills the entire Prüfer sequence of length $2k - 2$!
4. Therefore, constructing a valid tree corresponds uniquely to:
   - **Step 2a:** Choosing which $k - 1$ vertices out of the $2k$ labeled vertices will have degree 3:
     $$\binom{2k}{k - 1} \text{ choices}$$
   - **Step 2b:** Arranging these $k - 1$ distinct elements into a sequence of length $2k - 2$ such that each chosen element appears **exactly twice**.
5. The number of such sequences is given by the multiset permutation formula:
   $$\frac{(2k - 2)!}{2! \cdot 2! \dots 2!} = \frac{(2k - 2)!}{(2!)^{k - 1}} = \frac{(2k - 2)!}{2^{k - 1}}$$

---

### Conclusion:
Multiplying the two stages gives the total number of labeled trees:
$$\mathcal{T}(2k) = \binom{2k}{k - 1} \frac{(2k - 2)!}{2^{k - 1}}$$

**Alternative Algebraic Form:**
$$\mathcal{T}(2k) = \frac{(2k)!}{(k - 1)! \cdot (k + 1)!} \cdot \frac{(2k - 2)!}{2^{k - 1}}$$
$\blacksquare$
