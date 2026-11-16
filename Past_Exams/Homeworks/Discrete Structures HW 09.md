---
type: uni_course_assignment
course: "[[Discrete Structures MOC|Discrete Structures]]"
course_code: "89-2197"
assignment_num: 9
topic: "Linear Recurrence Relations, Non-Homogeneous Systems, Walk Counting in Symmetric Graphs"
status: "To Solve"
solution_file: "[[Discrete Structures HW 09 — Solution]]"
tags:
  - assignment
  - discrete_structures
  - recurrence_relations
  - characteristic_roots
  - non_homogeneous
  - walk_counting
---

# 📝 Discrete Structures — Homework Assignment 9

> [!info] Assignment Details
> - **Course:** 89-2197 (Discrete Structures / מבנים בדידים)
> - **Topics:** Second and Third-Order Linear Homogeneous Recurrences, Complex Roots and Radical Conjugates, Non-Homogeneous Recurrences with Repeated Roots, Walk Enumeration in Symmetric Graphs via Linear Systems.
> - **Status:** ⏳ Unsolved
> - **Full Worked Solutions:** [[Discrete Structures HW 09 — Solution|View Complete Step-by-Step Solutions]]

---

### Instructions
- You may use any algebraic theorem regarding characteristic polynomials and recurrence solution forms seen in class.

---

## 📌 Question 1: Homogeneous Linear Recurrences (Warm-Up)

Find the **general solutions** for each of the following recurrence relations:

### Part (a): Quadratic Characteristic with Real Roots
$$a_n = 2a_{n-1} + a_{n-2}$$
Also, find the **particular solution** satisfying the initial conditions:
$$a_0 = 0, \quad a_1 = 1$$

### Part (b): Cubic Characteristic with Radical Roots
$$a_n = (2 + 2\sqrt{3})a_{n-1} - (3 + 4\sqrt{3})a_{n-2} + 6a_{n-3}$$
*(Hint: $r = 2$ is a root of the characteristic polynomial).*

### Part (c): Recurrence with Purely Imaginary Roots
$$a_n = -a_{n-2}$$
Express the general real solution in terms of trigonometric functions or real linear combinations.

> [!tip]- 💡 Hints & Strategy
> - For (a): Characteristic equation $r^2 - 2r - 1 = 0 \implies r = 1 \pm \sqrt{2}$. General solution $a_n = A(1+\sqrt{2})^n + B(1-\sqrt{2})^n$.
> - For (b): Factor out $(r - 2)$ by polynomial division. The remaining quadratic is $r^2 - 2\sqrt{3}r + 3 = (r - \sqrt{3})^2 = 0$. Note the repeated root $\sqrt{3}$!
> - For (c): $r^2 + 1 = 0 \implies r = \pm i = e^{\pm i\pi/2}$. General solution $a_n = A\cos(n\pi/2) + B\sin(n\pi/2)$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 2: Ternary Sequences & Consecutive Patterns

### Part (a): Ternary Strings Without Consecutive Zeros
Find a recurrence relation and initial conditions for the number $t_n$ of ternary strings of length $n$ (over alphabet $\{0, 1, 2\}$) that contain **no two consecutive zeros** ($00$).
Solve the recurrence to find a closed-form expression for $t_n$.

### Part (b): Subsets of $\{1, \dots, n\}$ Without Three Consecutive Integers
Let $a_n$ denote the number of subsets of $\{1, 2, \dots, n\}$ that contain **no three consecutive integers** (meaning no $\{x, x+1, x+2\} \subseteq S$).
1. Derive a recurrence relation for $a_n$.
2. State the initial conditions for $a_1, a_2, a_3$.

> [!tip]- 💡 Hints & Strategy
> - For (a): Condition on whether the $n$-th symbol is $1, 2$ (giving $2t_{n-1}$) or $0$ (which forces the previous symbol to be $1$ or $2$, giving $2t_{n-2}$). Thus $t_n = 2t_{n-1} + 2t_{n-2}$.
> - For (b): Partition according to whether $n \notin S$ (gives $a_{n-1}$), $n \in S, n-1 \notin S$ (gives $a_{n-2}$), or $n, n-1 \in S$ (forces $n-2 \notin S$, giving $a_{n-3}$). Thus $a_n = a_{n-1} + a_{n-2} + a_{n-3}$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 3: Non-Homogeneous Recurrence with Repeated Roots

Solve the following non-homogeneous recurrence relation:
$$a_n = 9a_{n-1} - 27a_{n-2} + 27a_{n-3} - 8$$
subject to the initial conditions:
$$a_0 = 2, \quad a_1 = -2, \quad a_2 = 19$$

> [!tip]- 💡 Hints & Strategy
> - Step 1: Guess a constant particular solution $b_n = \mu$. Substitute $\mu = 9\mu - 27\mu + 27\mu - 8 \implies 8\mu = 8 \implies \mu = 1$.
> - Step 2: Solve the homogeneous part: $r^3 - 9r^2 + 27r - 27 = (r - 3)^3 = 0$. Since $r = 3$ is a triple root, the homogeneous solution is $c_n = (A + Bn + Cn^2)3^n$.
> - Step 3: General solution $a_n = (A + Bn + Cn^2)3^n + 1$. Substitute $a_0, a_1, a_2$ to solve the linear system for $A, B, C$.

> [!quote]- ✍️ Solution Workspace
> 

---

## 📌 Question 4: Walk Counting in a Symmetric Graph

Consider the undirected graph $G$ on $7$ vertices with central hub $v_0$ and symmetric cycles:
- Central vertex $v_0$ is connected to $\{v_2, v_3, v_5, v_6\}$.
- Peripheral vertices form cycles: $\{v_1, v_2\}, \{v_1, v_6\}, \{v_2, v_3\}, \{v_3, v_4\}, \{v_4, v_5\}, \{v_5, v_6\}$.

Find a recurrence relation and initial conditions for $a_n$, the number of walks of length $n$ starting at the central vertex $v_0$.
**Solve the recurrence** to find an explicit closed-form formula for $a_n$.

> [!tip]- 💡 Hints & Strategy
> - Partition vertices by symmetry:
>   - $a_n$: walks of length $n$ starting at $v_0$.
>   - $b_n$: walks of length $n$ starting at one of $\{v_2, v_3, v_5, v_6\}$.
>   - $c_n$: walks of length $n$ starting at one of $\{v_1, v_4\}$.
> - Express transitions:
>   $$a_n = 4b_{n-1}, \quad b_n = a_{n-1} + b_{n-1} + c_{n-1}, \quad c_n = 2b_{n-1}$$
> - Substitute $a_{n-1}$ and $c_{n-1}$ into the equation for $b_n$ to get a single second-order recurrence in $b_n$.

> [!quote]- ✍️ Solution Workspace
> 
