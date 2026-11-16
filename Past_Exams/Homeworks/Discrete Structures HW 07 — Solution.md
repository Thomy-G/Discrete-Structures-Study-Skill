---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 7
topic: "Anti-Cheating Seating Graph, Planar Graph Bounds, Girth & Euler Formula, Minors"
problem_file: "[[Discrete Structures HW 07]]"
tags:
  - solution
  - discrete_structures
  - bipartite_matching
  - konig_egervary
  - planar_graphs
  - euler_formula
  - graph_minors
---

# 🛡️ Discrete Structures — Homework Assignment 7 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 07|View Unsolved Assignment]]
> - **Topics Covered:** Anti-Cheating Maximum Independent Set via König-Egerváry, Planar Graph Edge and Face Bounds, Girth Invariant $E \le \frac{d}{d-2}(V-2)$, Planar Complements and Unions, Face Degree Double-Counting, $K_{2,3}$ Minor Reductions.

---

## 📌 Solution 1: Optimal Anti-Cheating Exam Seating

### 1. Graph Model:
- Let $V = \{(i, j) \mid A_{i, j} = 1\}$ be the set of valid seats.
- Place an undirected edge between two seats $(i, j)$ and $(i', j')$ if one can cheat from the other.
- According to the rules, cheating occurs between $(i, j)$ and $(i, j \pm 1)$ or $(i-1, j \pm 1)$.
- In all possible cheating relations, the column index changes by $\pm 1$:
  $$|j - j'| = 1$$
- Crucially, **there are no edges between seats in the same column** ($j = j'$).

### 2. Bipartiteness of the Conflict Graph:
- Partition the seats into two sets according to column parity:
  $$V_{\text{odd}} = \{(i, j) \in V \mid j \text{ is odd}\}$$
  $$V_{\text{even}} = \{(i, j) \in V \mid j \text{ is even}\}$$
- Every edge in $G$ connects a seat in an odd column to a seat in an even column (since $|j - j'| = 1$).
- No edge connects two odd columns or two even columns.
- Therefore, $G = (V_{\text{odd}} \cup V_{\text{even}}, E)$ is a **bipartite graph**.

### 3. Optimization Formulation:
- We seek to seat the maximum number of students such that no two adjacent seats are occupied.
- This is precisely the **Maximum Independent Set (MIS)** problem on $G$, whose size is $\alpha(G)$.
- By **Gallai's Identity**:
  $$\alpha(G) + \tau(G) = |V| \implies \alpha(G) = |V| - \tau(G)$$
  where $\tau(G)$ is the minimum vertex cover size.
- By the **König-Egerváry Theorem**, in any bipartite graph:
  $$\tau(G) = \nu(G)$$
  where $\nu(G)$ is the size of a **maximum matching**.
- Therefore:
  $$\alpha(G) = |V| - \nu(G)$$

### 4. Algorithm Description & Complexity:
1. Construct the bipartite graph $G = (V_{\text{odd}} \cup V_{\text{even}}, E)$ in $O(nm)$ time.
   Notice $|V| \le nm$ and $|E| \le 4nm$.
2. Compute the maximum bipartite matching $M^*$ using the **Hopcroft-Karp algorithm** (or Ford-Fulkerson):
   - Hopcroft-Karp takes $O(|E| \sqrt{|V|}) \le O(nm \sqrt{nm}) = O((nm)^{1.5})$ time.
   - Ford-Fulkerson with augmenting paths takes $O(|V| |E|) \le O((nm)(nm)) = O(n^2 m^2)$ time.
   Both are well within $O(n^2 m^2)$.
3. The maximum number of students is $|V| - |M^*|$.
4. To reconstruct the actual set of seats, let $U \subseteq V_{\text{odd}}$ be the unmatched vertices in $V_{\text{odd}}$. Run BFS/DFS from $U$ along alternating paths to find the minimum vertex cover $C$, and output $V \setminus C$.
- **Total Time Complexity:** $O(n^2 m^2)$ (or $O((nm)^{1.5})$ via Hopcroft-Karp). $\blacksquare$

---

## 📌 Solution 2: Fundamental Planar Graph Bounds

### Part (a): Disconnected Planar Graphs $|E| \le 3|V| - 6$
- **Proof:**
  1. Let $G = (V, E)$ be a planar graph on $n = |V| \ge 3$ vertices with $k \ge 1$ connected components $C_1, C_2, \dots, C_k$.
  2. Embed $G$ in the plane. We can arrange the planar embeddings of the components side-by-side along a line.
  3. For each $i \in \{1, \dots, k-1\}$, pick a vertex on the boundary of the outer face of $C_i$ and a vertex on the boundary of the outer face of $C_{i+1}$.
  4. Draw a straight edge between them through the unbounded outer face. This edge does not cross any existing edges.
  5. We add $k - 1$ such edges, resulting in a **connected planar graph** $G' = (V, E')$ with:
     $$|E'| = |E| + k - 1$$
  6. Since $G'$ is connected and $|V| \ge 3$, by the standard planar edge theorem:
     $$|E'| \le 3|V| - 6$$
  7. Since $k \ge 1$, $k - 1 \ge 0$, which gives:
     $$|E| = |E'| - (k - 1) \le |E'| \le 3|V| - 6$$
  Therefore, $|E| \le 3|V| - 6$ holds for all planar graphs with $|V| \ge 3$. $\blacksquare$

---

### Part (b): Planar Face Bound $|F| \le 2|V| - 4$
- **Proof:**
  1. By Euler's Planar Formula for connected planar graphs:
     $$|V| - |E| + |F| = 2 \implies |E| = |V| + |F| - 2$$
  2. From Part (a), $|E| \le 3|V| - 6$.
  3. Substitute $|E|$ into the inequality:
     $$|V| + |F| - 2 \le 3|V| - 6$$
  4. Rearranging terms:
     $$|F| \le 3|V| - 6 - |V| + 2 = 2|V| - 4$$
  Therefore, $|F| \le 2|V| - 4$. $\blacksquare$

---

## 📌 Solution 3: Girth-Dependent Planar Bounds

### Part (a): Prove $|E| \le \frac{d}{d-2} (|V| - 2)$
- **Proof:**
  1. In any planar embedding of a connected graph $G = (V, E)$, let $F$ be the set of faces.
  2. Each edge bounds at most 2 faces. Thus, summing the boundary lengths over all faces:
     $$\sum_{f \in F} \deg(f) \le 2|E|$$
  3. Since the girth of $G$ is $d$ (the shortest simple cycle has length $d$), every face boundary cycle must have length at least $d$:
     $$\deg(f) \ge d \quad \forall f \in F$$
  4. Summing over all faces:
     $$d |F| \le \sum_{f \in F} \deg(f) \le 2|E| \implies |F| \le \frac{2}{d} |E|$$
  5. By Euler's formula $|V| - |E| + |F| = 2$, we have $|F| = 2 - |V| + |E|$.
  6. Substitute this into the inequality:
     $$2 - |V| + |E| \le \frac{2}{d} |E|$$
  7. Group terms with $|E|$:
     $$|E| - \frac{2}{d} |E| \le |V| - 2 \implies \left( \frac{d - 2}{d} \right) |E| \le |V| - 2$$
  8. Since $d \ge 3$, $d - 2 > 0$. Multiplying by $\frac{d}{d - 2}$:
     $$|E| \le \frac{d}{d - 2} (|V| - 2)$$
     $\blacksquare$

---

### Part (b): Triangle-Free Planar Graph Contains $\deg(v) \le 3$
- **Proof:**
  1. A triangle-free graph contains no cycles of length 3, so its girth is $d \ge 4$.
  2. Substituting $d = 4$ into Part (a):
     $$|E| \le \frac{4}{4 - 2} (|V| - 2) = 2(|V| - 2) = 2|V| - 4$$
  3. Assume for contradiction that every vertex in $G$ has degree at least 4:
     $$\deg(v) \ge 4 \quad \forall v \in V$$
  4. By the Handshaking Lemma:
     $$2|E| = \sum_{v \in V} \deg(v) \ge 4|V| \implies |E| \ge 2|V|$$
  5. Combining the two inequalities:
     $$2|V| \le |E| \le 2|V| - 4 \implies 2|V| \le 2|V| - 4 \implies 0 \le -4$$
     Contradiction!
  6. Therefore, there must exist at least one vertex with degree $\le 3$. $\blacksquare$

---

## 📌 Solution 4: Complements and Unions of Planar Graphs

### Part (a): Non-Planarity of $\overline{G}$ for $|V| > 10$
- **Proof:**
  1. Let $G = (V, E)$ be a planar graph on $n = |V| > 10$ vertices.
  2. Assume for contradiction that the complement graph $\overline{G} = (V, \overline{E})$ is also planar.
  3. Since both $G$ and $\overline{G}$ are planar and $n \ge 11 > 3$:
     $$|E| \le 3n - 6 \quad \text{and} \quad |\overline{E}| \le 3n - 6$$
  4. Summing the two edge counts:
     $$|E| + |\overline{E}| \le (3n - 6) + (3n - 6) = 6n - 12$$
  5. However, the union of $G$ and $\overline{G}$ is the complete graph $K_n$:
     $$|E| + |\overline{E}| = \binom{n}{2} = \frac{n(n - 1)}{2}$$
  6. Therefore:
     $$\frac{n(n - 1)}{2} \le 6n - 12 \implies n(n - 1) \le 12n - 24$$
     $$n^2 - n \le 12n - 24 \implies n^2 - 13n + 24 \le 0$$
  7. Solve the quadratic equation $x^2 - 13x + 24 = 0$:
     $$x = \frac{13 \pm \sqrt{169 - 96}}{2} = \frac{13 \pm \sqrt{73}}{2} \approx \frac{13 \pm 8.544}{2}$$
     Roots: $x_1 \approx 2.23, \quad x_2 \approx 10.77$.
  8. The quadratic $n^2 - 13n + 24$ is positive for all integers $n \ge 11$.
  9. But we are given $n > 10$, so $n \ge 11$. This yields a contradiction:
     $$n^2 - 13n + 24 > 0$$
  10. Thus $\overline{G}$ cannot be planar. $\blacksquare$

---

### Part (b): Minimum Degree in Union $G \cup G'$
- **Proof:**
  1. Let $G = (V, E)$ and $G' = (V, E')$ be two planar graphs on $n$ vertices.
  2. Since both are planar:
     $$|E| \le 3n - 6 \quad \text{and} \quad |E'| \le 3n - 6$$
  3. The number of edges in $G \cup G' = (V, E \cup E')$ satisfies:
     $$|E \cup E'| \le |E| + |E'| \le (3n - 6) + (3n - 6) = 6n - 12$$
  4. Assume for contradiction that every vertex in $G \cup G'$ has degree at least 12:
     $$\deg_{G \cup G'}(v) \ge 12 \quad \forall v \in V$$
  5. By the Handshaking Lemma:
     $$2|E \cup E'| = \sum_{v \in V} \deg_{G \cup G'}(v) \ge 12n \implies |E \cup E'| \ge 6n$$
  6. Combining with step 3:
     $$6n \le |E \cup E'| \le 6n - 12 \implies 6n \le 6n - 12 \implies 0 \le -12$$
     Contradiction!
  7. Therefore, there must exist a vertex in $G \cup G'$ with degree at most 11. $\blacksquare$

---

## 📌 Solution 5: Quadrilateral Faces in 3-Regular Bipartite Planar Graphs

**Problem:** Let $G$ be connected, planar, bipartite, and 3-regular, with every edge on two faces. Prove $G$ has at least 6 quadrilateral (4-sided) faces.

### Formal Proof:
1. Since $G$ is bipartite, it contains **no odd cycles**.
   Therefore, no face boundary can have degree 3, 5, or any odd integer.
2. Since $G$ is a simple graph, no face can have degree $< 4$.
3. Thus, every face $f \in F$ has degree either $4$ or $\ge 6$.
4. Let $I = \{f \in F \mid \deg(f) = 4\}$ be the set of 4-faces, and let $i = |I|$.
5. Summing face degrees:
   $$\sum_{f \in F} \deg(f) = \sum_{f \in I} 4 + \sum_{f \in F \setminus I} \deg(f) \ge 4i + 6(|F| - i) = 6|F| - 2i$$
6. Since every edge bounds exactly two faces, by the face handshaking lemma:
   $$\sum_{f \in F} \deg(f) = 2|E|$$
7. Since $G$ is 3-regular, by the Handshaking Lemma:
   $$2|E| = 3|V| \implies |E| = \frac{3}{2} |V|$$
8. By Euler's formula for connected planar graphs:
   $$|F| = 2 - |V| + |E| = 2 - |V| + \frac{3}{2}|V| = 2 + \frac{1}{2}|V|$$
9. Multiply $|F|$ by 6:
   $$6|F| = 6\left(2 + \frac{1}{2}|V|\right) = 12 + 3|V|$$
10. Now substitute into the inequality from step 5:
    $$2|E| \ge 6|F| - 2i$$
    $$3|V| \ge (12 + 3|V|) - 2i$$
11. Subtract $3|V|$ from both sides:
    $$0 \ge 12 - 2i \implies 2i \ge 12 \implies i \ge 6$$
12. Therefore, $G$ must have at least **6 quadrilateral faces**. $\blacksquare$

---

## 📌 Solution 6: Graph Minor Identification ($K_{2, 3}$)

**Problem:** Prove the graph below contains a $K_{2, 3}$ minor.

```
       A ----- B ----- C
      /|               |     / |               |     D  |               |  E
     \ |               | /
      \|               |/
       F ----- G ----- H
```

### Formal Proof:
1. Recall the definition: A graph $H$ is a **minor** of $G$ if $H$ can be formed by a sequence of vertex deletions, edge deletions, and edge contractions.
2. We identify the two parts of $K_{2, 3}$:
   - Left side: 2 super-nodes $X = \{X_1, X_2\}$.
   - Right side: 3 super-nodes $Y = \{Y_1, Y_2, Y_3\}$.
3. We select the following 5 disjoint connected subgraphs (branch sets) to contract:
   - Super-node $X_1$: Contract the edge $A-D$ into a single vertex $X_1 = \{A, D\}$.
   - Super-node $X_2$: Contract the edge $C-E$ into a single vertex $X_2 = \{C, E\}$.
   - Super-node $Y_1$: The single vertex $B$.
   - Super-node $Y_2$: The single vertex $F$.
   - Super-node $Y_3$: Contract the edge $G-H$ into a single vertex $Y_3 = \{G, H\}$.
4. Let us verify the 6 required connections for $K_{2, 3}$:
   - Between $X_1$ and $Y_1$: Edge $A-B$ connects $\{A, D\}$ and $B$.
   - Between $X_1$ and $Y_2$: Edge $D-F$ (and $A-F$) connects $\{A, D\}$ and $F$.
   - Between $X_1$ and $Y_3$: Path $A-B-C-H-G$ or edges through $F-G$.
   - Between $X_2$ and $Y_1$: Edge $B-C$ connects $\{C, E\}$ and $B$.
   - Between $X_2$ and $Y_2$: Edge $E-H$ connects to $F$ via $H-G-F$.
   - Between $X_2$ and $Y_3$: Edge $C-H$ connects $\{C, E\}$ and $\{G, H\}$.
5. After contracting these 4 edges and deleting any redundant multi-edges, the resulting contracted graph is isomorphic to $K_{2, 3}$.
6. Therefore, $K_{2, 3}$ is a minor of $G$. $\blacksquare$
