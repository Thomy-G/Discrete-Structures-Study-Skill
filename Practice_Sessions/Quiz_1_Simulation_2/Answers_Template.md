# Answer Sheet — Quiz 1 Simulation 2
**Student:** Tomer  
**Course:** Discrete Structures (89-2197) — Dr. Arnold Filtser  
**Date:** 2026-11-16  
**Status:** 📝 Ready to Solve

---

## Part A: Multiple-Choice Questions (75 Points — 15 Points Each)
*Write down your chosen option (1 through 6) for each question:*

- **Question 1 (15 pts):** 2 ✅
- **Question 2 (15 pts):** 2 ✅
- **Question 3 (15 pts):** 3 ✅
- **Question 4 (15 pts):** 4 ✅
- **Question 5 (15 pts):** 3 ✅

<div align="right">
<table style="border: 1px solid #ddd; border-radius: 4px; background: rgba(130, 130, 130, 0.07); padding: 8px; font-size: 13px; font-family: system-ui; width: fit-content; text-align: left;">
  <tr><td><strong>Part A (Multiple-Choice) Score:</strong></td><td><strong style="color: #2e7d32;">75 / 75</strong></td></tr>
  <tr><td colspan="2" style="border-top: 1px dotted #ccc; padding-top: 4px; color: var(--text-muted);">Flawless performance! 5 out of 5 correct. Excellent mastery of poset extremes, complement graph diameter, forest edge formulas, and cardinal arithmetic.</td></tr>
</table>
</div>

---

## Part B: Open Proof Question (25 Points) — Question 6

### Part 1 (12 Points): Proving that a Tree with $\Delta(T) = k$ Has at Least $k$ Leaves [HW 01, Q4(b) / HW 03, Q2]
*Write your formal proof here:*

$$\displaylines{
\text{We will set an edge with the maximal degree of k as the root of the tree}\\
\text{After that we will remove said vertex, given that the vertex had k neighboors}\\
\text{and the graph is acyclic there will be k connected components in the resulting graph}\\
\text{If the component C is of size 1 (A single vertex) then the vertex is a leaf in the original graph}\\
\text{if the connected component is of size 2 or larger, we know its connected and acyclic, therefore a tree}\\
\text{We have proved that trees have at least 2 leaves, the original root is only connected to one of them}\\
\text{Therefore for each connected component on the resulting graph we have at least one leaf}\\
\text{Therefore the original graph has at least k leaves}
}$$

<div align="right">
<table style="border: 1px solid #ddd; border-radius: 4px; background: rgba(130, 130, 130, 0.07); padding: 8px; font-size: 13px; font-family: system-ui; width: fit-content; text-align: left;">
  <tr><td><strong>Part B — Question 6.1 Score:</strong></td><td><strong style="color: #2e7d32;">11 / 12</strong></td></tr>
  <tr><td colspan="2" style="border-top: 1px dotted #ccc; padding-top: 4px; color: var(--text-muted);">Excellent proof! Clean casework on component size ($|V(C)|=1$ vs $|V(C)| \ge 2$). Minor deduction (-1 pt): Watch the typo in line 33 ("edge" instead of "vertex"), and explicitly note that the root $r$ connects to at most one vertex in $C$ because the graph is acyclic.</td></tr>
</table>
</div>

---

### Part 2 (13 Points): Cantor's Diagonalization on Real Numbers Without Digit 7 [HW 04, Q2(a)]
*Write your formal diagonal proof here:*

$$\displaylines{
\text{Assume that S is countable, this means that we can list the elements on it}\\
\Set{ s_{1},s_{2},s_{3},\dots }\\
\text{We can make a function that modifies the digits of an elements as follows:}\\
f:\{0, 1, 2, 3, 4, 5, 6, 8, 9\} \to \Set{ 1,2 }\\
f(d) = \begin{cases}
1 & d\neq1 \\
2 & d=1
\end{cases}\\
\text{And we will use this function on the diagonal to make a new number}\\
s = \forall n: f(s_{nn})\\
\text{this number will have digits different than any other number, therefore making a different}\\
\text{number from all the countable numbers, in contradiction to the assumption that the set is countable}\\
\text{Therefore S is uncountable}
}$$

<div align="right">
<table style="border: 1px solid #ddd; border-radius: 4px; background: rgba(130, 130, 130, 0.07); padding: 8px; font-size: 13px; font-family: system-ui; width: fit-content; text-align: left;">
  <tr><td><strong>Part B — Question 6.2 Score:</strong></td><td><strong style="color: #2e7d32;">10 / 13</strong></td></tr>
  <tr><td colspan="2" style="border-top: 1px dotted #ccc; padding-top: 4px; color: var(--text-muted);">Great choice of digits $\{1, 2\}$! Deductions (-3 pts): (1) Crucial missing step: you did not explicitly write that $s \in S$ (verifying it is in $(0, 1)$, has no 7, and has no trailing 9s)—without $s \in S$, finding $s \notin \{s_1, s_2, \dots\}$ is not a contradiction; (2) Write $s = 0.y_1 y_2 \dots$ as a real number rather than just a digit stream.</td></tr>
</table>
</div>

---

## 📊 Exam Tally & Final Score

| Section | Points Scored | Max Points | Percentage |
| :--- | :--- | :--- | :--- |
| **Part A: Multiple-Choice (Q1–Q5)** | 75 | 75 | 100.0% |
| **Part B: Question 6.1 (Tree Leaves $\ge k$)** | 11 | 12 | 91.7% |
| **Part B: Question 6.2 (Cantor Diagonalization)** | 10 | 13 | 76.9% |
| **Total Final Score** | **96** | **100** | **96.0%** 🏆 |

