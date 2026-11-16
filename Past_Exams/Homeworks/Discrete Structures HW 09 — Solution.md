---
type: uni_course_assignment_solution
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 9
topic: "Linear Recurrence Relations, Non-Homogeneous Systems, Walk Counting in Symmetric Graphs"
problem_file: "[[Discrete Structures HW 09]]"
tags:
  - solution
  - discrete_structures
  - recurrence_relations
  - characteristic_roots
  - non_homogeneous
  - walk_counting
---

# 🛡️ Discrete Structures — Homework Assignment 9 Solutions

> [!info] Solution Guide Overview
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Unsolved Worksheet:** [[Discrete Structures HW 09|View Unsolved Assignment]]
> - **Topics Covered:** Linear Homogeneous Recurrences with Real and Radical Roots, Tribonacci Subset Patterns, Non-Homogeneous Degree-3 Characteristic Polynomials, Graph Walk Spectral & Symmetry Decomposition.

---

## 📌 Solution 1: Homogeneous Linear Recurrences

### Part (a): $a_n = 2a_{n-1} + a_{n-2}$ with $a_0 = 0, a_1 = 1$
1. **Characteristic Equation:**
   $$r^2 - 2r - 1 = 0$$
   Using the quadratic formula:
   $$r = \frac{2 \pm \sqrt{4 - 4(1)(-1)}}{2} = \frac{2 \pm \sqrt{8}}{2} = 1 \pm \sqrt{2}$$
2. **General Solution:**
   $$a_n = A(1 + \sqrt{2})^n + B(1 - \sqrt{2})^n$$
3. **Determining Constants $A, B$:**
   - For $n = 0$: $a_0 = A + B = 0 \implies B = -A$.
   - For $n = 1$:
     $$a_1 = A(1 + \sqrt{2}) + B(1 - \sqrt{2}) = A(1 + \sqrt{2} - 1 + \sqrt{2}) = A(2\sqrt{2}) = 1$$
     $$A = \frac{1}{2\sqrt{2}} = \frac{\sqrt{2}}{4}, \quad B = -\frac{\sqrt{2}}{4}$$
4. **Particular Closed-Form:**
   $$a_n = \frac{(1 + \sqrt{2})^n - (1 - \sqrt{2})^n}{2\sqrt{2}}$$
   *(These are the celebrated Pell numbers).* $\blacksquare$

---

### Part (b): $a_n = (2 + 2\sqrt{3})a_{n-1} - (3 + 4\sqrt{3})a_{n-2} + 6a_{n-3}$
1. **Characteristic Equation:**
   $$r^3 - (2 + 2\sqrt{3})r^2 + (3 + 4\sqrt{3})r - 6 = 0$$
2. Given that $r = 2$ is a root, divide the polynomial by $(r - 2)$:
   $$\frac{r^3 - (2 + 2\sqrt{3})r^2 + (3 + 4\sqrt{3})r - 6}{r - 2} = r^2 - 2\sqrt{3}r + 3$$
3. Factor the remaining quadratic:
   $$r^2 - 2\sqrt{3}r + 3 = (r - \sqrt{3})^2 = 0$$
   This gives a repeated root $r = \sqrt{3}$ with multiplicity 2!
4. **Roots:**
   $$r_1 = 2, \quad r_{2, 3} = \sqrt{3} \text{ (multiplicity 2)}$$
5. **General Solution:**
   $$a_n = A \cdot 2^n + (B + C n)(\sqrt{3})^n$$
   where $A, B, C \in \mathbb{R}$. $\blacksquare$

---

### Part (c): $a_n = -a_{n-2}$
1. **Characteristic Equation:**
   $$r^2 + 1 = 0 \implies r = \pm i$$
2. In polar form, $i = e^{i\pi/2}$ and $-i = e^{-i\pi/2}$.
   $$r^n = (\pm i)^n = \cos\left(\frac{n\pi}{2}\right) \pm i\sin\left(\frac{n\pi}{2}\right)$$
3. **General Real Solution:**
   $$a_n = A \cos\left(\frac{n\pi}{2}\right) + B \sin\left(\frac{n\pi}{2}\right)$$
   Equivalently, in terms of values:
   $$a_n = \begin{cases}
   A & n \equiv 0 \pmod 4 \\[2pt]
   B & n \equiv 1 \pmod 4 \\[2pt]
   -A & n \equiv 2 \pmod 4 \\[2pt]
   -B & n \equiv 3 \pmod 4
   \end{cases}$$
   $\blacksquare$

---

## 📌 Solution 2: Ternary Sequences & Consecutive Patterns

### Part (a): Ternary Strings Without Consecutive Zeros
1. Let $t_n$ be the number of valid strings of length $n$ over $\{0, 1, 2\}$.
2. Condition on the last digit of the string:
   - If the string ends in $1$ or $2$ (2 choices), the prefix of length $n-1$ can be any valid string. This contributes $2 t_{n-1}$ possibilities.
   - If the string ends in $0$, the $(n-1)$-th digit cannot be $0$, so it must be $1$ or $2$ (2 choices). The preceding prefix of length $n-2$ can be any valid string. This contributes $2 t_{n-2}$ possibilities.
3. **Recurrence Relation:**
   $$t_n = 2t_{n-1} + 2t_{n-2} \quad \text{for } n \ge 2$$
4. **Initial Conditions:**
   - $t_1 = 3$ (strings: $0, 1, 2$).
   - $t_2 = 3^2 - 1 = 8$ (all 9 strings of length 2 except $00$).
5. **Characteristic Equation:**
   $$r^2 - 2r - 2 = 0 \implies r = 1 \pm \sqrt{3}$$
6. **General Solution:**
   $$t_n = A(1 + \sqrt{3})^n + B(1 - \sqrt{3})^n$$
   Using $t_1 = 3, t_2 = 8$:
   $$A = \frac{2 + \sqrt{3}}{2\sqrt{3}} = \frac{3 + 2\sqrt{3}}{6}, \quad B = \frac{\sqrt{3} - 2}{2\sqrt{3}} = \frac{3 - 2\sqrt{3}}{6}$$
   $$t_n = \frac{2+\sqrt{3}}{2\sqrt{3}}(1+\sqrt{3})^n + \frac{\sqrt{3}-2}{2\sqrt{3}}(1-\sqrt{3})^n$$
   $\blacksquare$

---

### Part (b): Subsets of $\{1, \dots, n\}$ Without Three Consecutive Integers
1. Let $a_n$ be the number of subsets of $\{1, \dots, n\}$ containing no three consecutive elements.
2. We partition all valid subsets $S$ based on whether the largest elements belong to $S$:
   - **Case 1: $n \notin S$.**
     Then $S$ is simply a valid subset of $\{1, \dots, n-1\}$. There are $a_{n-1}$ such subsets.
   - **Case 2: $n \in S$ but $n - 1 \notin S$.**
     Then $S \setminus \{n\}$ is a valid subset of $\{1, \dots, n-2\}$. There are $a_{n-2}$ such subsets.
   - **Case 3: $n \in S$ and $n - 1 \in S$.**
     To avoid three consecutive integers, we must have $n - 2 \notin S$.
     Then $S \setminus \{n, n-1\}$ is a valid subset of $\{1, \dots, n-3\}$. There are $a_{n-3}$ such subsets.
3. These cases are mutually exclusive and exhaustive. Therefore:
   $$a_n = a_{n-1} + a_{n-2} + a_{n-3} \quad \text{for } n \ge 4$$
4. **Initial Conditions:**
   - $n = 1$: Subsets of $\{1\}$ are $\emptyset, \{1\} \implies a_1 = 2$.
   - $n = 2$: Subsets of $\{1, 2\}$ are all 4 subsets $\implies a_2 = 4$.
   - $n = 3$: Subsets of $\{1, 2, 3\}$ are all $2^3 = 8$ subsets except $\{1, 2, 3\} \implies a_3 = 7$.
   *(This is the Tribonacci sequence).* $\blacksquare$

---

## 📌 Solution 3: Non-Homogeneous Recurrence with Repeated Roots

Solve $a_n = 9a_{n-1} - 27a_{n-2} + 27a_{n-3} - 8$ with $a_0 = 2, a_1 = -2, a_2 = 19$.

### Step 1: Find a Particular Solution $b_n$
The non-homogeneous term is the constant $-8$.
We guess a constant solution $b_n = \mu$:
$$\mu = 9\mu - 27\mu + 27\mu - 8$$
$$\mu = 9\mu - 8 \implies 8\mu = 8 \implies \mu = 1$$
Thus, $b_n = 1$ is a particular solution.

### Step 2: Solve the Associated Homogeneous Equation
The homogeneous equation is:
$$a_n - 9a_{n-1} + 27a_{n-2} - 27a_{n-3} = 0$$
Characteristic equation:
$$r^3 - 9r^2 + 27r - 27 = 0$$
Notice that this is a perfect cube:
$$(r - 3)^3 = 0$$
Thus $r = 3$ is a root of multiplicity 3.
The homogeneous general solution is:
$$c_n = (A + Bn + Cn^2) \cdot 3^n$$

### Step 3: Combine and Apply Initial Conditions
The full general solution is:
$$a_n = c_n + b_n = (A + Bn + Cn^2)3^n + 1$$

We use the given initial conditions:
1. **$n = 0$:**
   $$a_0 = (A + 0 + 0)3^0 + 1 = A + 1 = 2 \implies A = 1$$
   *(Wait: earlier scrap had $A+1=3$, let's check: $a_0 = 2 \implies A + 1 = 2 \implies A = 1$).*
   Let's check $a_1 = -2$:
   $$a_1 = (A + B + C)3^1 + 1 = 3(1 + B + C) + 1 = -2$$
   $$3(1 + B + C) = -3 \implies 1 + B + C = -1 \implies B + C = -2 \implies B = -C - 2$$
   Let's check $a_2 = 19$:
   $$a_2 = (A + 2B + 4C)3^2 + 1 = 9(1 + 2B + 4C) + 1 = 19$$
   $$9(1 + 2B + 4C) = 18 \implies 1 + 2B + 4C = 2 \implies 2B + 4C = 1$$
   Substitute $B = -C - 2$:
   $$2(-C - 2) + 4C = 1 \implies -2C - 4 + 4C = 1 \implies 2C = 5 \implies C = \frac{5}{2}$$
   $$B = -\frac{5}{2} - 2 = -\frac{9}{2}$$

Thus the exact unique solution is:
$$a_n = \left(1 - \frac{9}{2}n + \frac{5}{2}n^2\right) 3^n + 1$$
$\blacksquare$

---

## 📌 Solution 4: Walk Counting in a Symmetric Graph

### 1. Classification by Symmetry:
Partition the 7 vertices into three symmetry equivalence classes:
- Class 1: Hub vertex $v_0$. Let $a_n$ be the number of walks of length $n$ starting at $v_0$.
- Class 2: Four symmetrical inner vertices $\{v_2, v_3, v_5, v_6\}$. Let $b_n$ be the number of walks of length $n$ starting at any one of these vertices.
- Class 3: Two symmetrical outer vertices $\{v_1, v_4\}$. Let $c_n$ be the number of walks of length $n$ starting at one of these vertices.

### 2. Transition System:
From the graph adjacency:
- From $v_0$, the 4 incident edges go to $\{v_2, v_3, v_5, v_6\}$. Thus:
  $$a_n = 4 b_{n-1} \quad (n \ge 1)$$
- From each vertex of $\{v_2, v_3, v_5, v_6\}$ (e.g. $v_5$), the 3 neighbors are $v_0$ (Class 1), $v_6$ (Class 2), and $v_4$ (Class 3). Thus:
  $$b_n = a_{n-1} + b_{n-1} + c_{n-1} \quad (n \ge 1)$$
- From each vertex of $\{v_1, v_4\}$ (e.g. $v_1$), the 2 neighbors are $v_2, v_6$ (both in Class 2). Thus:
  $$c_n = 2 b_{n-1} \quad (n \ge 1)$$

### 3. Deriving a Single Recurrence for $b_n$:
Substitute $a_{n-1} = 4 b_{n-2}$ and $c_{n-1} = 2 b_{n-2}$ into the equation for $b_n$:
$$b_n = (4 b_{n-2}) + b_{n-1} + (2 b_{n-2})$$
$$b_n = b_{n-1} + 6 b_{n-2} \quad \text{for } n \ge 2$$

### 4. Solving the Recurrence for $b_n$:
- **Characteristic Equation:**
  $$r^2 - r - 6 = 0 \implies (r - 3)(r + 2) = 0$$
  Roots: $r_1 = 3, \; r_2 = -2$.
- **General Form:**
  $$b_n = A \cdot 3^n + B \cdot (-2)^n$$
- **Initial Values:**
  - $b_0 = 1$ (the walk of length 0 consists solely of the vertex).
  - $b_1 = 3$ (walks of length 1 to its 3 neighbors).
- Solve for $A, B$:
  $$A + B = 1$$
  $$3A - 2B = 3 \implies 3A - 2(1 - A) = 3 \implies 5A - 2 = 3 \implies 5A = 5 \implies A = 1, \; B = 0$$
- Remarkably, $B = 0$! Therefore:
  $$b_n = 3^n \quad \forall n \ge 0$$

### 5. Computing $a_n$:
Using $a_n = 4 b_{n-1}$:
$$a_n = 4 \cdot 3^{n-1} \quad \text{for all } n \ge 1$$
*(For $n = 0$, $a_0 = 1$).*

**Verification:**
- $a_1 = 4 \cdot 3^0 = 4$ (edges from $v_0$ to $v_2, v_3, v_5, v_6$). Correct!
- $a_2 = 4 \cdot 3^1 = 12$ (each of the 4 neighbors has 3 outgoing edges). Correct! $\blacksquare$
