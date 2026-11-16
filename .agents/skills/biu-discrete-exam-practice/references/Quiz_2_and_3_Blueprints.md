# Quizzes 2 & 3 Blueprints (HW 05 – HW 13)

This reference outlines the scope, topics, and question formats for **Quiz 2** and **Quiz 3** as the semester progresses.
- **Format (90 Minutes):** **5 Multiple-Choice Questions** (single correct answer each, 15 pts $\times$ 5 = 75 pts) + **1 Open Proof Question** based on the tier's Homework exercises (25 pts).

---

## 🎯 Quiz 2 Blueprint (Weeks 5–8 / HW 05 – HW 08)

### Focus Topics:
1. **Eulerian & Hamiltonian Graphs (HW 05):**
   - **Eulerian Circuit:** Connected undirected graph has an Euler circuit $\iff$ all vertices have even degrees.
   - **Directed Euler Circuit:** Strongly connected digraph has an Euler circuit $\iff \forall v : \deg_{\text{in}}(v) = \deg_{\text{out}}(v)$.
   - **Hamiltonian Cycles:** Dirac's Theorem ($\min \deg \ge n/2$) and Ore's Theorem ($\deg(u) + \deg(v) \ge n$ for all non-adjacent $u, v$).
2. **Matchings in Graphs (HW 06):**
   - **Berge's Lemma:** A matching $M$ is maximum $\iff$ there is no $M$-augmenting path.
   - **Hall's Marriage Theorem:** Bipartite graph $G = (A \cup B, E)$ has a matching saturating $A \iff \forall S \subseteq A : |N(S)| \ge |S|$.
   - **$k$-Regular Bipartite Graphs:** Every $k$-regular bipartite graph ($k \ge 1$) has a 1-factorization (decomposes into $k$ disjoint perfect matchings).
   - **Tutte's Theorem:** General graphs have a perfect matching $\iff \forall U \subseteq V : o(G - U) \le |U|$.
3. **Planar Graphs & Euler's Formula (HW 07):**
   - **Euler's Polyhedral Formula:** For connected planar graphs: $V - E + F = 2$.
   - **Edge Bounds:** If $g(G) \ge 3 \implies E \le 3V - 6$. If bipartite / triangle-free ($g \ge 4$) $\implies E \le 2V - 4$.
   - **Kuratowski's & Wagner's Theorems:** $G$ is planar $\iff G$ does not contain a subgraph homeomorphic to (or minor of) $K_5$ or $K_{3, 3}$.
4. **Graph Coloring (HW 08):**
   - **Chromatic Number $\chi(G)$:** Greedy bound $\chi(G) \le \Delta(G) + 1$.
   - **Brooks' Theorem:** $\chi(G) \le \Delta(G)$ unless $G$ is a complete graph or an odd cycle.
   - **Four Color Theorem & Five Color Theorem:** Every planar graph is 4-colorable (5-colorable proof using Kempe chains / Euler formula).

---

## 🎯 Quiz 3 Blueprint (Weeks 9–13 / HW 09 – HW 13)

### Focus Topics:
1. **Recurrence Relations & Generating Functions (HW 09):**
   - Linear homogeneous recurrence relations with constant coefficients (characteristic roots, multiplicities).
   - Non-homogeneous recurrences via particular solutions ($a_n = a_n^{(h)} + a_n^{(p)}$).
   - Generating functions: $A(x) = \sum_{n=0}^\infty a_n x^n$, partial fraction decomposition, and coefficient extraction.
2. **Extremal Graph Theory & Ramsey Theory (HW 10):**
   - **Ramsey's Theorem:** $R(s, t) \le R(s - 1, t) + R(s, t - 1)$. Specific bounds for $R(3, 3) = 6$.
   - **Mantel's Theorem & Turán's Theorem:** Maximum edges in a graph with no $K_{r+1}$ is attained by the complete multipartite Turán graph $T(n, r)$.
3. **The Probabilistic Method (HW 11):**
   - Erdős lower bound for Ramsey numbers: $R(k, k) > 2^{k/2}$.
   - Linearity of expectation: $\mathbb{E}[X] = \sum \mathbb{E}[X_i]$ even without independence.
   - Existence proofs: If $\mathbb{P}(A) > 0$, then there exists an instance satisfying event $A$.
4. **Trees, Prüfer Sequences & Stable Matchings (HW 12 – HW 13):**
   - **Cayley's Formula:** Exactly $n^{n-2}$ labeled trees on $n$ vertices.
   - **Prüfer Code:** Bijection between labeled trees on $\{1, \dots, n\}$ and sequences of length $n - 2$ from $\{1, \dots, n\}$.
   - **Stable Marriage / Gale-Shapley Algorithm:** Existence of stable matchings, proposer-optimality, and termination in $\le n^2$ steps.

