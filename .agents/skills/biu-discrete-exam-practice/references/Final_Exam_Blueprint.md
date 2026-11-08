# Bar-Ilan University Discrete Structures (89-2197)
## Official Final Exam Structure & Grading Rubric (מבנה המבחן הסופי הרשמי)

**Lecturer:** Dr. Arnold Filtser  
**Course:** Discrete Structures (89-2197)  
**Standard Exam Format (from official 2024–2026 Moed A / B exams):**
- **Part A (שאלות אמריקאיות):** 4 multiple-choice questions (mandatory, 5 points each, total 20 points).
- **Part B (שאלות פתוחות):** 5 in-depth proof questions (20 points each) $\implies$ **Student chooses 4 out of 5** (total 80 points).
- **Total Points:** 100 points (often with bonus up to 104–106).
- **Duration:** 3 hours (180 minutes).
- **The 20% "I Don't Know" Policy:** Writing **"לא יודעים"** grants 20% credit on any chosen open question (or full sub-question). Cannot be used on multiple-choice questions.

---

## 🏛️ Part B: Canonical Open Question Archetypes (from Archive):

Based on official solutions (2024–2026):
1. **Extremal Graph Theory & Ramsey Bounds (שאלה 1):**
   - E.g., Proving the Erdős-Szekeres Theorem for Ramsey numbers: $R(s, t) \le R(s - 1, t) + R(s, t - 1)$.
   - Common Pitfall: Incorrect induction base cases.
2. **Planar Graphs & Girth Bounds (שאלה 2):**
   - E.g., Proving that a simple planar graph with $\delta(G) \ge 4$ contains a cycle of length $\le 4$ using face bounds $5|F| \le \sum t(f_i) \le 2|E|$ and Euler's formula $V - E + F = 2$.
3. **Graph Cycles & Edge Covers / Metrics (שאלה 3):**
   - Minimum cycle edge covers, complement diameters, or tree path metrics.
4. **Matchings & Symmetric Difference (שאלה 4):**
   - E.g., Parity of perfect matchings in symmetric difference graphs $G[M \Delta M^*]$ and Berge's augmenting path theorem.
5. **The Probabilistic Method / Kraft-McMillan / Prefix Codes (שאלה 5):**
   - E.g., Prefix-free binary string sets proving $\sum 2^{-\text{len}(w)} \le 1$ using independent random bit sequences and disjoint event bounds.

---

## 🏛️ Comprehensive Final Exam Blueprint

A full final exam tests cross-module synthesis. The 5 canonical question sections are:

### Part 1: Cardinality, Infinite Sets & Order Theory (20–25 Points)
- **Combinations:** Posets / Well-ordering on product sets + Equinumerosity / CSB.
- **Classic Styles:**
  - Proving $|S| = \aleph$ or $|S| = 2^\aleph$ for intricate function sets or subset lattices.
  - Dedekind-infinite extensions and Cantor diagonal constructions with structural constraints.

### Part 2: Graph Anatomy, Trees & Bipartition (20–25 Points)
- **Combinations:** Degrees / Handshaking + Trees + Distance / Metric invariants.
- **Classic Styles:**
  - Proving structural properties under edge/vertex deletion (minimally connected / maximally acyclic).
  - Odd cyclic walk cycle-extraction and 2-coloring distance partitions.
  - Girth $g(G)$, diameter bounds on graph complements ($\operatorname{diam}(\overline{G}) \le 2$).

### Part 3: Matchings, Connectivity & Traversals (20–25 Points)
- **Combinations:** Euler/Hamilton cycles + Hall's Marriage Theorem + Berge's Lemma.
- **Classic Styles:**
  - $k$-regular bipartite graphs factorizing into 1-factors.
  - Tutte's condition $o(G - U) \le |U|$ applied to specific graph topologies (e.g., trees or hypercubes).
  - Dirac's and Ore's degree-sum conditions in modified graphs.

### Part 4: Planarity & Graph Coloring (20–25 Points)
- **Combinations:** Euler's formula $V - E + F = 2$ + Girth bounds + Chromatic number $\chi(G)$.
- **Classic Styles:**
  - Proving non-planarity via edge-face inequalities ($E \le 3V - 6$ or $E \le 2V - 4$ for triangle-free) or Kuratowski minors.
  - Finding or bounding $\chi(G)$ and $\chi'(G)$ (Vizing's theorem) using Brooks' theorem or Kempe chains.

### Part 5: Counting, Recurrences, Ramsey & Extremal Graphs (20–25 Points)
- **Combinations:** Linear recurrences / Generating functions + Turán's theorem / Probabilistic method.
- **Classic Styles:**
  - Deriving closed forms for sequences via generating functions $A(x) = \sum a_n x^n$.
  - Erdős probabilistic lower bounds: showing $\mathbb{P}(\text{property}) > 0$.
  - Turán graphs $T(n, r)$ maximizing edge counts without containing $K_{r+1}$.
  - Prüfer sequences encoding tree structures.

