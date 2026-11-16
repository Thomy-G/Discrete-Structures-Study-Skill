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
  - Directly based on (or a close parameterized variation of) a problem from **Homework 1–4**.
  - May be a single 25-point proof or split into two sub-parts (e.g., 12 + 13 points).
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

