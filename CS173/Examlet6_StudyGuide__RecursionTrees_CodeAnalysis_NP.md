# CS 173 Examlet 6 Study Guide: Recursion Trees, Code Analysis & NP

Spring, 2025

**Examlet 6 Skills:**

---

<aside>
📌

**Quizlet Flashcards:** [https://quizlet.com/1033386586/cs-173-examlet-6-study-guide-recursion-and-np-concepts-flash-cards/](https://quizlet.com/1033386586/cs-173-examlet-6-study-guide-recursion-and-np-concepts-flash-cards/)

</aside>

<aside>
📌

**Notion Website:** [https://therapeutic-profit-af7.notion.site/CS-173-Examlet-6-Study-Guide-Recursion-Trees-Code-Analysis-NP-1da42e50f1858048ade6f51bdae09889?pvs=4](https://www.notion.so/CS-173-Examlet-6-Study-Guide-Recursion-Trees-Code-Analysis-NP-1da42e50f1858048ade6f51bdae09889?pvs=21)

</aside>

---

# (Recap) Earlier Algorithms & Big O Content

<aside>
📌

### Review the earlier Algorithms and Big-O analysis content From Examlet 5:

</aside>

Action: Recap the Algorithms I, II, and III lecture notes from [the lecture schedule](https://courses.grainger.illinois.edu/cs173/sp2025/ALL-lectures/lecture-schedule.html)

- The Primitive function relationships

$\ll$ - strictly asymptotically less than

$O$ - asymptotically less than or equal to

$\approx \text{ or } \Theta$ - asymptotically similar

- Skill: Be able to prove a primitive function relationship (using inequalities & induction)

- Three main patterns requiring analysis
    - nested loops
    - while loops
    - recursive

---

# Recursion Trees

<aside>
📌

### Finding the closed form using a recursion tree.

Skill: Given a recursively defined function, find its closed form by drawing a recursion tree and adding up the work at all levels. (Examples would look like those presented in the textbook, e.g. the level sums are constant or increase in a pattern based on the key summations given above.)

</aside>

To find the closed form of a recursively defined function using a hand-drawn recursion tree you want to set up three columns alongside the drawing of your tree (column 4).

1. The column that you will write the height of your tree at each level
2. The column that you will write the node count at each level in your tree
3. The column that you will write the problem size at each level in your tree (problem size is the input into your recursively defined function at that level i.e n is the p-size at the first level)
4. **The Drawing**: A visual representation of the nodes at each level in the tree.
    1. The key is to remember that each node represents a call of your recursive function.
        1. So it should be labeled with the amount of work done during that call of the function. (all of the non-recursive terms of that function definition). if the non-recursive term includes n, then you plug in the problem size at height k for n and use that to label each node at height k.

| 1. height (k) | 2. node count - $f(bf,k)$ | 3. problem size | 4) tree visual |
| --- | --- | --- | --- |
| 0 | 1 | n | draw one node and label it with work done on first call |
| 1 | $(branching factor)^{1}$ | i.e (n - 1) | for each parent draw $bf$ number of nodes beneath it |
| 2 | $(branching factor)^2$ | i.e $(n-2)$ |  |
| … | … | … | … |
| k | $(branching factor)^k$ [this will be the node count at level k] | $(n - k )$ [this will be the p-size as a function of k] | draw leaf level nodes and work at height k |

<aside>
📌

### Find a big-O solution for simple recursive definitions

Skill: Find a big-O solution for a simple recursive definition, of the types that we've seen as examples of unrolling and recursion trees.

</aside>

You find the big-O solution *from memory*, by *unrolling* or by *drawing a recursion tree*.

Professor says it’s worth memorizing the big-O running times of common routines so you can use them quickly in higher-level analysis.

Examples of simple recursive definitions that we’ve seen:

**Tower of Hanoi:**

- $T(1) = c$
- $T(n) = 2T(n-1) + d$

Runtime: $O(2^n)$

**Merging two Sorted Lists:**

- $T(1) = c$
- $T(n) = T(n-1) + d$

Runtime: $O(n)$

**Divide and Conquer/ Binary Search:**

- $T(1) = c$
- $T(n) = T(n/2) + d$

Runtime: $O(\log n)$

**Mergesort:**

- $T(1) = c$
- $T(2) = 2T(n/2) + d$

Runtime: $O(n \log n)$

# Algorithms

<aside>
📌

### Towers of Hanoi & Karatsuba’s algorithm

- Be familiar with the overall structure and big-O running times of the following algorithms.
    - Towers of Hanoi solver
    - Karatsuba's algorithm (you won't have to reproduce all the details)
</aside>

**Towers of hanoi solver:**

![Screenshot 2025-04-19 at 4.55.44 PM.png](CS%20173%20Examlet%206%20Study%20Guide%20Recursion%20Trees,%20Code%201da42e50f1858048ade6f51bdae09889/Screenshot_2025-04-19_at_4.55.44_PM.png)

- $T(1) = c$
- $T(n) = 2T(n-1) + d$

Runtime: $O(2^n)$

**Karatsuba’s algorithm:**

- $T(1) = c$
- $T(n) = 3T(n/2) + dn$

Runtime: $O(n^{\log_3 2})$ 

[Solution uses change of base formula]

<aside>
📌

### Find a big-O solution requiring use of the change of base formula

- Find a big-O solution for slightly harder recursive definitions than the ones for Examlet 5, e.g. requiring use of the change of base formula.
</aside>

An example of a recursive definition whose analysis requires the change of base formula is Karatsuba’s algorithm. It has the form $T(n) = 3 T(n/2) + O(n)$.

**Solving for the work at leaf nodes:**

The **tree height** is $\log_2n$

*The **number of leaves*** is the branching factor (3) to the power of the height ($\log_2n)$

$= 3^{log_2n}$

multiply by c

**Solving for the work at non-leaf nodes:**

…

[See mfleck’s “Algorithms 4” notes for visuals and what karatsuba's algo. is for.](https://courses.grainger.illinois.edu/cs173/sp2025/ALL-lectures/Lectures/algorithms4.html)

**Change of base formula:**

- $\log_ab = \log_ac* \log_cb$

<aside>
📌

### Analyze Big-O of unfamiliar but fairly simple functions in pseudo-code

Skill: Given an unfamiliar but fairly simple function in pseudo-code, analyze how long it takes using big-O notation. You should be able to analyze nested for loops, recursive functions, and simple examples of while loops.

</aside>

For analyzing big-O runtime of simple functions it’s helpful to know the runtimes of common routines such as (but not limited to) *nested loops, linear search (list traversal), binary search, sorted list merge, mergesort.* 

You want to identify the ***dominant term*** of a routine by identifying the big-O running times of each of the code’s sub-routines. The dominant term is its big-O running time.

<aside>
📌

### Express algorithms involving loops (possibly nested) using summations

Skill: For an algorithm involving loops (perhaps nested), express its running time using summations.

</aside>

**Nested loop Example**:

![Screenshot 2025-04-19 at 6.23.46 PM.png](CS%20173%20Examlet%206%20Study%20Guide%20Recursion%20Trees,%20Code%201da42e50f1858048ade6f51bdae09889/Screenshot_2025-04-19_at_6.23.46_PM.png)

**Running time Expressed using summations:**

$\sum_{i=1}^{n}\sum_{j=1}^nd$, where d is some constant work from lines 07-11

= $n(\sum_{j=1}^nd) = n*(n*d) = n^2d$

[Recall that the sum from 1 to n of any constant c is $nc$]

So a 2-D nested loop is $O(n^2)$

<aside>
📌

### Express a recursive algorithm’s running time as a recursive definition

Skill: Given a recursive algorithm (familiar or unfamiliar) express its running time as a recursive definition.

</aside>

You’d want to write a recursive definition representative of the pseudo code like:

$T(z) = c$

$T(p_0) = bT(p_1) + w$

$p_0 = n$. z is the base case, b is the branching factor, $p_k$ is the problem size at tree level k. $w$ is the work done at each calling of $T(n)$

To find the closed form using a recursion tree, 

You want to :

- identify the base case, z
- identify the height of the algorithm’s recursion tree k, by solving $p_k = z$
- identify w (the work done at each call of $T(n)$
    - by analyzing the pseudo-code’s structure and sub-components
        
        [$w$ could be a function of n and/or include other recursive terms]
        
- Finally you’d find The sum of the work $w$, done at
    - the leaf level
    - + internal levels of the tree

# NP

<aside>
📌

### Certain sentences have exponentially many parse trees

</aside>

- Know that certain classes of sentences have exponentially many parse trees. (And thus producing all parses of a sentence requires exponential time.)

For example sentences with many prepositional statements. (subject-ambiguous descriptive statements)

I saw a unicorn in the shed, by the apple tree with a red hat.

<aside>
📌

### Tower of Hanoi puzzle is in EXP

</aside>

- Know that the Towers of Hanoi puzzle has been proved to require exponential time.

<aside>
📌

### NP is the set of problems for which we can easily prove the answer is “yes”

</aside>

- Know that **NP** is the set of problems for which we can quickly (polynomial time) justify "yes" answers.

(P, NP, EXP) technically contain only "decision problems." A decision problem is a problem where you are given some input and asked to produce a yes/no answer. Informally, people extend this idea to other sorts of problems, because an algorithm that delivers more interesting answer (e.g. the chromatic number of a graph) can typically be built on top of an algorithm for the corresponding decision problem.

<aside>
📌

### co-NP is the set of problems for which we can easily prove the answer is “no”

</aside>

- Know that **co-NP** is the set of problems for which we can quickly (polynomial time) justify "no" answers.

<aside>
📌

### NP problems can be solved in EXP, but may also be polynomial (P) time solvable

</aside>

- Skill: Know that problems in NP can be solved in exponential time, but it's not known whether they can be solved in polynomial time.

the existence of Polynomial time solutions for them have not yet been disproven.

<aside>
📌

### An “NP-complete” problem solved in polynomial time would imply that any problem in NP can be solved in polynomial time.

</aside>

- Skill: Know what an NP-complete problem is: a problem in NP for which a polynomial-time algorithm would imply that **any** problem in NP can be solved in polynomial time.

that is NP and P would be equal.

<aside>
📌

### Know common examples of NP-complete problems

</aside>

- Skill: Know some examples of NP-complete problems: graph colorability, circuit satisfiability (Circuit SAT), propositional logic satisfiability, marker making, the travelling salesman problem.

<aside>
📌

### Bipartite graphs are 2-colorable (Polynomial time solution)

</aside>

- Skill: Know that you can decide in polynomial time whether a graph is 2-colorable (aka bipartite).

# Proof by contradiction

- Skill: Understand proof by contradiction and when it’s useful (i.e to prove existential claims)
