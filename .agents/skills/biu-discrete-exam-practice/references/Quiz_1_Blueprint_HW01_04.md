# Quiz 1 Blueprint & Proof Checklist (Lectures, Recitations & HW 01 – 04)

This blueprint outlines the exact structural patterns, typical trap conditions, and rigorous proof standards expected for **Quiz 1** in Dr. Arnold Filtser's Discrete Structures course.

## 📋 Official Quiz 1 Structure (90 Minutes, 100 Points)
- **Part A — 5 Multiple-Choice Questions (שאלות אמריקאיות, 15 pts each = 75 pts):**
  - 5–6 options per question with **strictly one correct answer** (Dr. Filtser style, often including *"אף אחת מהתשובות אינה נכונה"*).
  - Covers Lectures 1–4, Recitations 1–4, and Exercises 1–4:
    1. **Relations & Posets:** Properties of relations (reflexive, symmetric, antisymmetric, transitive), counting relations/equivalence classes, minimal/maximal vs. minimum/maximum elements, lexicographic order properties.
    2. **Graph Foundations & Degrees:** Handshaking lemma, degree sequences, complement graph $\overline{G}$ connectivity and diameter bounds ($\operatorname{diam}(\overline{G})$), induced vs. spanning subgraphs.
    3. **Trees & Bipartite Graphs:** Counting leaves given degree sequences, tree characterizations ($|E| = |V| - 1$), tree centers (Jordan's theorem), bipartite graph characterizations (odd cycles / closed walks).
    4. **Cardinality ($\aleph_0, \aleph, 2^\aleph$):** Determining exact cardinalities of intricate sets (e.g., $\{S \subseteq \mathbb{N} \mid X \Delta S \text{ is finite}\}$, bijections/injections from $\mathbb{N} \to \mathbb{N}$, equivalences with $\mathcal{P}(\mathbb{N})$).
- **Part B — 1 Open Proof Question (שאלה פתוחה, 25 pts):**
  - Directly based on (or a slight variation of) a problem from **`Past_Exams/Homeworks/Discrete Structures HW 01.md` through `HW 04.md`**.
  - **Exact Pool of HW 01–04 Problems (High-Probability Open Question Candidates):**
    - **From [Discrete Structures HW 01.md](file:///c:/Users/thomy/University/Discrete%20Structures/Past_Exams/Homeworks/Discrete%20Structures%20HW%2001.md):**
      - **Q1(a):** Prove lexicographic order on $A^n$ is a total order.
      - **Q1(b):** Equivalence relations on $X = \{1,\dots,10\}$ ordered by number of classes $|X/R_1| < |X/R_2|$ (partial order, not total, min/max elements).
      - **Q2:** Pigeonhole principle on vertex degrees ($\exists u \neq v, \deg(u) = \deg(v)$).
      - **Q3:** Tree characterization: $|E| = n-1$ and acyclic $\iff \forall u, v \; \exists!$ simple path.
      - **Q4(a)-(b):** Full binary rooted tree leaf count $\ell = \frac{n+1}{2}$; Tree with maximum degree $\Delta(T) = k$ has at least $k$ leaves.
      - **Q5(a)-(c):** Mantel's Theorem ($m \le n^2/4$ for triangle-free graphs on even $n$, extremal graph $K_{n/2, n/2}$, induction for $m = k^2 + 1$).
    - **From [Discrete Structures HW 02.md](file:///c:/Users/thomy/University/Discrete%20Structures/Past_Exams/Homeworks/Discrete%20Structures%20HW%2002.md):**
      - **Q1:** Disconnected graph $G \implies$ tight upper bound $\operatorname{diam}(\overline{G}) \le 2$.
      - **Q2:** Forest with $k$ connected components satisfies $|E| = |V| - k$.
      - **Q3:** Equipotence under set operations ($A \times B \sim C \times D$ true; $A \setminus B$ and $A \cup B$ false).
      - **Q4(a)-(d):** Explicit bijections **without CSB**: $(0,1) \sim [0,1]$, $A \times A \sim A^{\{1,2\}}$, $\mathcal{P}(A) \sim \{0,1\}^A$ *(appeared verbatim on 2026 Quiz 1!)*, $[0,1] \sim S^1$.
      - **Q5(a)-(b):** Disjoint closed disks in $\mathbb{R}^2$ are countable ($\le \aleph_0$ via $\mathbb{Q}^2$ density); disjoint concentric circles can have cardinality $\aleph$.
    - **From [Discrete Structures HW 03.md](file:///c:/Users/thomy/University/Discrete%20Structures/Past_Exams/Homeworks/Discrete%20Structures%20HW%2003.md):**
      - **Q1:** Cardinality of $101$-free infinite binary sequences is $\aleph$ (via CSB with $00/11$ blocks).
      - **Q2:** Tree with maximum degree $\Delta$ has at least $\Delta$ leaves.
      - **Q3:** $k$-regular disconnected graph with odd $k \implies$ every connected component has an even number of vertices.
      - **Q5:** Bipartite degree bound $|L| \ge \frac{|R| \cdot d}{\Delta(L)}$ via double-counting edges.
      - **Q6:** Connected graph with $\forall v, \deg(v) < \sqrt{n-1} \implies \operatorname{diam}(G) \ge 3$ *(appeared verbatim on 2026 Quiz 1!)*.
      - **Q7:** For $k \ge 2$, every $k$-regular bipartite graph contains **no bridges** (cut-edges).
    - **From [Discrete Structures HW 04.md](file:///c:/Users/thomy/University/Discrete%20Structures/Past_Exams/Homeworks/Discrete%20Structures%20HW%2004.md):**
      - **Q1(a)-(e):** Cardinality arithmetic with $|X| = \aleph$: $\mathbb{N} \times X$, $\mathbb{N}^X$, $X^\mathbb{N}$, $\mathcal{P}(\mathbb{N})^X$, $X^{\mathcal{P}(\mathbb{N})}$.
      - **Q2(a)-(c):** Cantor's Diagonalization: reals in $(0,1)$ without digit $7$ are uncountable; $\mathbb{N}^\mathbb{N}$ is uncountable; $\mathcal{P}_{\text{fin}}(\mathbb{N})$ is countable ($\aleph_0$) and $\mathcal{P}_\infty(\mathbb{N})$ has cardinality $\aleph$ *(a variant on unbounded subsets of $\mathbb{N}$ appeared on 2026 Quiz 1!)*.
  - Supports the 20% *"לא יודעים"* policy on the full open question or a full sub-part.

---

## 🏛️ Topic 1: Order Theory & Equivalence Relations (HW 01)

### Common Exam Patterns:
1. **Lexicographic Orders on $A^k$:**
   - *Task:* Given that $(A, \le)$ has a certain property (total order, well-order), prove that $(A^k, \le_{\text{lex}})$ inherits that property.
   - *Key Rigor Step:* Clearly isolate the *first index of difference* $i = \min \{j \mid x_j \neq y_j\}$.
2. **Equivalence & Partition Quotients:**
   - *Task:* Define a relation $x \sim y \iff \dots$ on functions, subsets, or graphs. Prove it is an equivalence relation and determine the cardinality of the quotient set $A/\sim$.
   - *Key Rigor Step:* Explicitly verify all 3 properties: Reflexivity ($x \sim x$), Symmetry ($x \sim y \implies y \sim x$), and Transitivity ($x \sim y \land y \sim z \implies x \sim z$).
3. **Extreme Elements in Posets:**
   - *Task:* Find all minimal, maximal, minimum, and maximum elements in a given poset, or prove their existence/uniqueness.
   - *Trap:* Confusing *maximal* (no element is strictly greater) with *maximum* (greater than or equal to all elements).

---

## 🏛️ Question 2: Graph Foundations, Trees & Bipartition (HW 02 & HW 03)

### Common Exam Patterns:
1. **Degree Sequences & Handshaking Parity:**
   - *Task:* Prove that a graph satisfying certain degree constraints cannot exist, or prove that two vertices must have the same degree (Pigeonhole on $n-1$ degrees).
   - *Formula:* $\sum_{v \in V} \deg(v) = 2|E| \implies$ count of odd-degree vertices is strictly even.
2. **Tree Induction & Leaf Deletion:**
   - *Task:* Prove a structural property of trees or forests (e.g., number of vertices of degree $k$, bound on diameter).
   - *Key Rigor Step:* Base case $n=1, 2$. Inductive step: delete a leaf $v$ ($\deg(v) = 1$). Show $T - v$ is still a tree on $n-1$ vertices, invoke induction, and restore $v$.
3. **Bipartite Graphs & Closed Walks:**
   - *Task:* Prove a graph is bipartite by showing all its cycles are even, or by explicitly constructing the 2-partition $(A, B)$ using distances from a root:
     $$A = \{v \mid \text{dist}(r, v) \text{ is even}\}, \quad B = \{v \mid \text{dist}(r, v) \text{ is odd}\}$$
   - *Trap:* Assuming walks cannot repeat vertices. If a walk repeats a vertex, use the **Cycle Extraction Lemma** to split it into two smaller walks.

---

## 🏛️ Question 3: Cardinality & Cantor-Schröder-Bernstein (HW 04)

### Common Exam Patterns:
1. **CSB Sandwich Construction:**
   - *Task:* Prove that a complex set $S$ has cardinality $\aleph$ or $\aleph_0$ using the Cantor-Schröder-Bernstein Theorem.
   - *Pattern:*
     1. Construct an explicit injection $f: S \to B$ into a known set (e.g., $\{0, 1\}^\mathbb{N}$ or $\mathbb{R}$).
     2. Construct an explicit injection $g: A \to S$ from a known set of the same target cardinality.
     3. Prove both $f$ and $g$ are well-defined and strictly injective:
        $$\forall x_1, x_2 : f(x_1) = f(x_2) \implies x_1 = x_2$$
     4. Conclude by CSB: $|S| = |A| = |B|$.
2. **Cantor's Diagonalization Technique:**
   - *Task:* Prove that a specific subset of functions or infinite sequences is uncountable without using CSB.
   - *Pattern:* Assume an enumeration $s_1, s_2, s_3, \dots$. Construct a diagonal sequence $d$ that differs from $s_n$ at position $n$, while ensuring $d$ satisfies all constraints of the set!
3. **Dyadic Fraction Avoidance:**
   - *Trap:* Never map $\{0, 1\}^\mathbb{N}$ directly to real numbers via $\sum \frac{b_i}{2^i}$ because $0.0111\dots_2 = 0.1000\dots_2$. Use base 3 with digits $\{0, 2\}$, or restrict to sequences with infinitely many $1$s.

