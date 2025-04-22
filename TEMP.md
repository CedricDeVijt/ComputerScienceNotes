## 1.1 Introduction to Computational Complexity

Computational complexity theory analyzes the resources required to solve computational problems, focusing on **time complexity**. This guide explores key concepts like **PTIME**, **NP**, **reductions**, and **NP-completeness**, drawn from the provided document. Why do we distinguish between polynomial and exponential time? Understanding these classifications helps determine whether a problem is practically solvable.

### What is Time Complexity?

**Time complexity** measures the number of computational steps a Turing machine needs to solve a problem as a function of input size $n$. Efficient algorithms run in **polynomial time** ($O(n^k)$), while exponential time ($O(2^n)$) is often impractical. How does this distinction impact real-world applications like navigation or cryptography? It separates feasible computations from those requiring infeasible resources.

#### Polynomial vs. Exponential Time

- Polynomial time ($O(n^k)$) is considered efficient, as it scales reasonably with input size (e.g., $n^2, n^3$).
- Exponential time ($O(2^n)$) grows rapidly, making large inputs computationally infeasible.
- Example: A computer performing 100 million steps per second takes 0.1 microseconds for $t(n) = n$ at $n = 10$, but $4 \times 10^{13}$ years for $t(n) = 2^n$ at $n = 100$ (↗ See Section 2.2 for detailed table).

### Deterministic Time Complexity Class: DTIME

The **DTIME** class defines languages decided by a deterministic Turing machine in $O(t(n))$ time. For instance, the language of palindromes is in $\text{DTIME}(n^2)$. Why is this formalism useful? It provides a rigorous way to classify problems based on their computational requirements.

#### Definition of DTIME

- Formally, $\text{DTIME}(t(n)) = \{ L \mid L \text{ is decided by a } O(t(n))\text{-time deterministic Turing machine with one tape} \}$.
- Example: Checking if a string is a palindrome requires comparing characters from both ends, achievable in $O(n^2)$ time.

## 1.2 PTIME: Polynomial Time Complexity

**PTIME** encompasses problems solvable in polynomial time by a deterministic Turing machine, representing practically solvable problems. This section covers the definition, significance, and examples like **PATH** and **RELPRIME**. What makes PTIME a cornerstone of efficiency? Its problems are solvable within reasonable time bounds for large inputs.

### Definition of PTIME

**PTIME** is the union of all $\text{DTIME}(n^k)$ for some constant $k$, i.e., $\text{PTIME} = \bigcup_k \text{DTIME}(n^k)$. It focuses on decision problems, where the output is "yes" or "no." Why focus on decision problems? They provide a clear framework for complexity analysis.

#### Significance of PTIME

- Polynomial time is considered efficient because it scales manageably (e.g., $n, n^2, n^3$).
- All deterministic computational models are polynomially equivalent, meaning they can be transformed into each other in polynomial time.
- Most PTIME algorithms have small exponents (e.g., $n^2, n^3$), making them practical (↗ See Section 2.3 for examples).

### Real-World Time Complexity Insights

The document provides a table illustrating CPU time for different time complexities, assuming a computer performs 100 million steps per second. This highlights the stark contrast between polynomial and exponential growth. Why does this matter for algorithm design? It guides developers toward efficient solutions.

#### CPU Time Comparison Table

- For $n = 10$:
  - $t(n) = n$: 0.01 microseconds
  - $t(n) = n^2$: 0.1 microseconds
  - $t(n) = n^3$: 1 microsecond
  - $t(n) = 2^n$: 1 microsecond
- For $n = 100$:
  - $t(n) = n$: 0.1 microseconds
  - $t(n) = n^2$: 10 microseconds
  - $t(n) = n^3$: 1 millisecond
  - $t(n) = 2^n$: $4 \times 10^{13}$ years
- Conclusion: Polynomial time remains feasible, while exponential time becomes impractical for large $n$.

### PTIME Algorithms: PATH and RELPRIME

This subsection explores two problems in PTIME: **PATH** (finding a path in a directed graph) and **RELPRIME** (checking if two numbers are relatively prime). How do these algorithms achieve polynomial time? They leverage efficient techniques like breadth-first search and Euclid’s algorithm.

#### PATH Algorithm

- **Definition**: $\text{PATH} = \{ \langle G, s, t \rangle \mid G \text{ is a directed graph with a path from vertex } s \text{ to } t \}$.
- **Algorithm**: Uses breadth-first search (BFS):
  1. Mark start node $s$.
  2. Iterate up to $m$ times (where $m$ is the number of nodes), marking nodes reachable via edges from marked nodes.
  3. Accept if end node $t$ is marked; otherwise, reject.
- **Complexity**: Each step (marking, scanning edges) is polynomial, and the loop runs $m$ times, yielding $O(m + e)$ where $e$ is the number of edges.
- **Naïve Approach**: Trying all paths takes $O(m^m)$, which is exponential.

#### RELPRIME Algorithm

- **Definition**: $\text{RELPRIME} = \{ \langle x, y \rangle \mid x \text{ and } y \text{ are relatively prime} \}$, i.e., their greatest common divisor (GCD) is 1.
- **Algorithm**: Uses Euclid’s algorithm:
  1. While $y \neq 0$:
     - Compute $x \leftarrow x \mod y$.
     - Swap $x$ and $y$.
  2. Accept if $x = 1$; otherwise, reject.
- **Complexity**:
  - Modulo operation is polynomial.
  - The loop runs logarithmically ($O(\log(\max(x, y)))$) because each iteration halves the larger number (↗ See Section 2.4.2 for proof).
- **Naïve Approach**: Checking all divisors up to $\min(x, y)$ takes exponential time in the input size $n = O(\max(\log_2 x, \log_2 y))$.

#### Why RELPRIME Runs Logarithmically

- After $x \leftarrow x \mod y$, $x < y$.
- After swapping, the new $x$ (former $y$) is larger, but the next modulo reduces it by at least half.
- This halving ensures at most $\min(2 \log_2 x, 2 \log_2 y)$ iterations, making the algorithm logarithmic in the input size.

### Another PTIME Example: PRIMES

The **PRIMES** problem determines if a number is prime. Historically challenging, it was proven to be in PTIME in 2002. Why was this a significant breakthrough? It resolved a centuries-old question about efficient primality testing.

#### PRIMES Algorithm

- **Definition**: $\text{PRIMES} = \{ \langle x \rangle \mid x \text{ is a prime number} \}$.
- **Algorithm**: Developed by Agrawal, Kayal, and Saxena (AKS algorithm, 2002), it runs in polynomial time but requires advanced number theory.
- **Significance**: Proved primality testing is efficient, impacting cryptography (e.g., RSA).

## 1.3 Input Representation in Complexity

Representing inputs efficiently is crucial for complexity analysis. The document emphasizes encoding objects (e.g., numbers, graphs) as strings in polynomial time. Why is this important? Inefficient representations can artificially inflate complexity.

### Encoding Objects

- **Numbers**: Use binary representation (e.g., $\langle 10 \rangle = 1010$). Unary (e.g., $\langle 10 \rangle = 1111111111$) is inefficient, increasing input size exponentially.
- **Graphs**: Represent as edge lists (e.g., $\langle G \rangle = \{(a, b), (b, c), (c, a)\}$) or adjacency matrices.
- **Requirement**: Encoding and decoding must be polynomial-time reversible.

#### Graph Representations

- **Directed Graph**: Edge list like $\{(a, b), (b, c), (c, a)\}$ or adjacency matrix:
  $$
  \begin{bmatrix}
  0 & 1 & 0 \\
  0 & 0 & 1 \\
  1 & 0 & 0
  \end{bmatrix}
 $$
- **Undirected Graph**: Symmetric edge list or matrix, reflecting bidirectional edges.
- **Impact**: Choice affects algorithm efficiency but not PTIME classification, as conversions are polynomial.

## 1.4 Satisfiability Problems and Propositional Logic

**Satisfiability (SAT)** problems involve determining if a propositional formula can be made true by assigning truth values to variables. These problems are central to complexity theory due to their applications and NP-completeness. Why are SAT problems pivotal? They model diverse computational tasks, from circuit verification to AI planning.

### Propositional Formulas: Syntax

A **propositional formula** is defined inductively:

- A variable $x_i \in X = \{ x_1, x_2, \ldots, x_k \}$ is a formula.
- If $\varphi$ is a formula, then $\neg \varphi$ (negation) is a formula.
- If $\varphi_1, \varphi_2$ are formulas, then $\varphi_1 \wedge \varphi_2$ (conjunction) and $\varphi_1 \vee \varphi_2$ (disjunction) are formulas.
- Implication $\varphi_1 \rightarrow \varphi_2$ is shorthand for $\neg \varphi_1 \vee \varphi_2$.

#### Example Formulas

- $\Phi_1 = (x_1 \wedge x_2) \vee x_3$
- $\Phi_2 = [(\neg x_1 \vee \neg x_2) \wedge (x_1 \vee x_3)] \rightarrow (x_2 \vee \neg x_1)$
- Question: How would you construct a truth table for $\Phi_1$?

### Semantics of Propositional Formulas

A **truth assignment** $\nu: X \rightarrow \{0, 1\}$ assigns 0 (false) or 1 (true) to variables. A formula $\varphi$ is **satisfiable** if there exists a $\nu$ such that $\nu \vDash \varphi$. How do we evaluate $\nu \vDash \varphi$? We use inductive rules based on the formula’s structure.

#### Truth Assignment Rules

- For a variable $x$, $\nu \vDash x$ if $\nu(x) = 1$.
- For $\neg \psi$, $\nu \vDash \neg \psi$ if $\nu \nvDash \psi$.
- For $\varphi_1 \wedge \varphi_2$, $\nu \vDash \varphi_1 \wedge \varphi_2$ if $\nu \vDash \varphi_1$ and $\nu \vDash \varphi_2$.
- For $\varphi_1 \vee \varphi_2$, $\nu \vDash \varphi_1 \vee \varphi_2$ if $\nu \vDash \varphi_1$ or $\nu \vDash \varphi_2$.
- Example: For $\nu(x_1) = 1, \nu(x_2) = 0, \nu(x_3) = 0$, evaluate $\nu \nvDash \Phi_1$ and $\nu \vDash \Phi_2$ (↗ See Section 4.1 for formulas).

### Conjunctive Normal Form (CNF)

A formula is in **CNF** if it is a conjunction of clauses, where each clause is a disjunction of literals (variables or their negations). Why is CNF important? It standardizes SAT problems, facilitating algorithmic analysis.

#### CNF Definition

- Form: $\varphi = C_1 \wedge C_2 \wedge \cdots \wedge C_n$, where $C_i = \ell_1 \vee \ell_2 \vee \cdots \vee \ell_p$.
- **Literal**: Either $x$ (positive) or $\neg x$ (negative).
- **Theorem**: Every propositional formula is equivalent to a CNF formula.
- **Proof**: Use De Morgan’s laws to push negations inward and distribute $\vee$ over $\wedge$:
  $$
  \neg (\varphi_1 \wedge \varphi_2) = \neg \varphi_1 \vee \neg \varphi_2, \quad \neg (\varphi_1 \vee \varphi_2) = \neg \varphi_1 \wedge \neg \varphi_2
 $$
  $$
  \varphi_1 \vee (\varphi_2 \wedge \varphi_3) = (\varphi_1 \vee \varphi_2) \wedge (\varphi_1 \vee \varphi_3)
 $$

#### Efficient CNF Conversion

- Standard conversion may cause exponential growth (e.g., $(x_1 \wedge y_1) \vee \cdots \vee (x_k \wedge y_k)$ yields $O(2^k)$ clauses).
- Solution: Introduce new variables to create a polynomial-sized CNF:
  $$
  \text{cnf}(\varphi_1 \vee \varphi_2) = (z \vee \text{cnf}(\varphi_1)) \wedge (\neg z \vee \text{cnf}(\varphi_2))
 $$
- Example: For $\varphi = (x_1 \wedge y_1) \vee (x_2 \wedge y_2) \vee (x_3 \wedge y_3)$, the CNF is polynomial-sized with new variables $z_1, z_2$.

#### Applications of SAT

- **General SAT**: Used in circuit verification, AI planning, and error diagnosis.
- **2SAT**: Applied in diagram labeling and tournament scheduling.
- **HORN-SAT**: Used in logic puzzles and discrete system analysis (↗ See Section 7 for NP-completeness).

## 1.5 Non-Deterministic Polynomial Time: NP

**NP** includes problems where a solution can be verified in polynomial time by a deterministic Turing machine. This section introduces NP and contrasts it with PTIME. Why is NP significant? It includes many practical problems, but their solvability in PTIME remains an open question (P vs. NP).

### Definition of NP

- **NP** is the class of languages where a certificate (solution) can be verified in polynomial time.
- Formally, a language $L \in \text{NP}$ if there exists a polynomial-time verifier $V$ such that for $w \in L$, there is a certificate $c$ where $V(w, c)$ accepts, and for $w \notin L$, no $c$ causes acceptance.
- Example: For SAT, the certificate is a truth assignment $\nu$, verifiable in $O(n)$ time.

### NP vs. PTIME

- **PTIME $\subseteq$ NP**: Every problem solvable in polynomial time is verifiable in polynomial time.
- **Open Question**: Is $\text{P} = \text{NP}$? If $\text{P} = \text{NP}$, all NP problems would be efficiently solvable.
- **Implication**: Solving an NP-complete problem in PTIME would imply $\text{P} = \text{NP}$ (↗ See Section 7).

## 1.6 Reductions, Completeness, and Hardness

**Reductions** transform one problem into another to compare their complexity. **NP-completeness** identifies the hardest problems in NP, while **NP-hardness** applies to problems at least as hard as NP-complete ones. Why are reductions powerful? They establish relationships between seemingly unrelated problems.

### Polynomial-Time Reductions

- A problem $A$ is **polynomial-time reducible** to $B$ ($A \leq_p B$) if there exists a polynomial-time function $f$ such that $w \in A$ if and only if $f(w) \in B$.
- **Proposition**: If $A \leq_p B$ and $B \in \text{PTIME}$, then $A \in \text{PTIME}$.
- **Implication**: Reducing an NP-complete problem to a PTIME problem would prove $\text{P} = \text{NP}$.

### NP-Completeness

- A problem $A$ is **NP-complete** if:
  1. $A \in \text{NP}$.
  2. Every problem in NP is polynomial-time reducible to $A$.
- Solving an NP-complete problem in PTIME implies $\text{P} = \text{NP}$.

### Cook-Levin Theorem

The **Cook-Levin Theorem** states that **SAT** is NP-complete. Why is this theorem foundational? It establishes SAT as a benchmark for NP-completeness, enabling reductions to other problems.

#### Proof Sketch

- **SAT in NP**: A truth assignment can be verified in polynomial time.
- **NP-Hardness**: Any NP problem can be reduced to SAT by encoding the Turing machine’s computation as a propositional formula, ensuring satisfiability corresponds to acceptance.

## 1.7 NP-Complete Problems

This section covers key NP-complete problems, including **UHAMPATH**, **UHAMCIRCUIT**, **TSP**, **SUBSETSUM**, **PARTITION**, and **IP**. Each is proven NP-complete via reductions. Why study these problems? They represent diverse applications, and their NP-completeness suggests computational intractability unless $\text{P} = \text{NP}$.

### Undirected Hamiltonian Path (UHAMPATH)

- **Definition**: $\text{UHAMPATH} = \{ \langle G, s, t \rangle \mid G \text{ is an undirected graph with a Hamiltonian path from } s \text{ to } t \}$.
- **Theorem**: UHAMPATH is NP-complete.
- **Proof**:
  - **In NP**: Guess a path and verify it is Hamiltonian in polynomial time.
  - **NP-Hard**: Reduce from directed HAMPATH by transforming each node $u$ into $u^{\text{in}}, u^{\text{mid}}, u^{\text{out}}$, with edges ensuring a Hamiltonian path in the undirected graph $G'$ corresponds to one in $G$.

### Undirected Hamiltonian Circuit (UHAMCIRCUIT)

- **Definition**: $\text{UHAMCIRCUIT} = \{ \langle G \rangle \mid G \text{ is an undirected graph with a Hamiltonian cycle} \}$.
- **Theorem**: UHAMCIRCUIT is NP-complete.
- **Proof**:
  - **In NP**: Guess a cycle and verify it visits all nodes exactly once.
  - **NP-Hard**: Reduce from UHAMPATH by adding a node $x$ with edges to $s$ and $t$, forming a cycle if a path exists.

### Travelling Salesman Problem (TSP)

- **Definition**: $\text{TSP} = \{ \langle G, c, k \rangle \mid G \text{ is a complete weighted graph with a cycle visiting each node once, cost } \leq k \}$.
- **Theorem**: TSP is NP-complete.
- **Proof**:
  - **In NP**: Verify a cycle’s cost in polynomial time.
  - **NP-Hard**: Reduce from UHAMCIRCUIT by creating a complete graph $G'$ with edge costs 0 for edges in $G$ and 1 otherwise, setting $k = 0$.

### Subset Sum (SUBSETSUM)

- **Definition**: $\text{SUBSETSUM} = \{ \langle S, t \rangle \mid S = \{ x*1, \ldots, x_k \}, \exists T \subseteq S \text{ such that } \sum*{y \in T} y = t \}$.
- **Theorem**: SUBSETSUM is NP-complete.
- **Proof**:
  - **In NP**: Guess a subset and verify the sum.
  - **NP-Hard**: Reduce from 3SAT by constructing numbers $y_i, z_i$ for variables and $g_j, h_j$ for clauses, ensuring a sum of $t$ corresponds to a satisfying assignment (↗ See Section 7.4.1 for details).

#### SUBSETSUM Reduction Details

- For a 3CNF formula $\varphi$ with variables $x*1, \ldots, x*\ell$ and clauses $c_1, \ldots, c_k$:
  - Numbers $y_i, z_i$ encode variable assignments, with 1s indicating presence in clauses.
  - Numbers $g_j, h_j$ ensure each clause contributes 1–3 to the sum.
  - Target $t$ has $\ell$ ones followed by $k$ threes, ensuring a valid assignment satisfies all clauses.

### Partition (PARTITION)

- **Definition**: $\text{PARTITION} = \{ \langle S \rangle \mid S = \{ x*1, \ldots, x_k \}, \exists S_1, S_2 \text{ such that } \sum*{x \in S*1} x = \sum*{x \in S_2} x \}$.
- **Theorem**: PARTITION is NP-complete.
- **Proof**:
  - **In NP**: Guess two subsets and verify equal sums.
  - **NP-Hard**: Reduce from SUBSETSUM by adding numbers $y*1 = 2 \sum*{x \in S} x - t$ and $y*2 = \sum*{x \in S} x + t$, ensuring a partition balances the sums.

### Integer Programming (IP)

- **Definition**: $\text{IP} = \{ \langle A, b \rangle \mid A \cdot x = b \text{ has a binary solution } x \in \{0, 1\}^n \}$.
- **Theorem**: IP is NP-complete.
- **Proof**:
  - **In NP**: Verify a binary vector solution.
  - **NP-Hard**: Reduce from SUBSETSUM by representing $\sum\_{x_i \in T} x_i = t$ as a linear equation with binary variables.

## 1.8 Complement Complexity: coNP

**coNP** includes problems whose complements are in NP. For example, the complement of SAT is unsatisfiable formulas. Why study coNP? It provides insight into the symmetry of complexity classes, though its relationship with NP is unresolved.

### coNP Definition

- A problem is in **coNP** if its complement is in NP.
- **coPTIME = PTIME**, but it is unknown if $\text{NP} = \text{coNP}$.
- **Observation**: PTIME is in both NP and coNP, but NP and coNP may differ.

### Implications

- Problems like unsatisfiable SAT or no-clique graphs are in coNP.
- Some problems are complete for $\text{NP} \cap \text{coNP}$, but coNP is not covered further in the course.

## 1.9 PTIME-Completeness Challenges

Defining **PTIME-completeness** is problematic due to the power of polynomial reductions. Why does this definition fail? It makes nearly all non-trivial PTIME problems PTIME-complete, diluting its utility.

### Flawed Definition

- A problem $A$ is PTIME-complete if $A \in \text{PTIME}$ and every $B \in \text{PTIME}$ reduces to $A$.
- **Issue**: Any non-empty, non-universal language in PTIME is PTIME-complete under this definition, as reductions can map inputs arbitrarily in polynomial time.

### Alternative Approaches

- Weaker reduction types (e.g., log-space reductions) are needed to distinguish PTIME problems effectively.
- This topic is revisited in the course project (↗ See Section 8).

---

## Key Points to Remember

- **Critical Distinction: Polynomial vs. Exponential Time** ★★★★☆
  - Polynomial time ($O(n^k)$) is efficient, while exponential time ($O(2^n)$) is often infeasible for large inputs.
- **Core Concept: PTIME** ★★★★★
  - PTIME includes problems solvable in polynomial time, like PATH (BFS) and RELPRIME (Euclid’s algorithm).
- **Key Technique: Polynomial-Time Reductions** ★★★★☆
  - Reductions ($A \leq_p B$) show that solving $B$ solves $A$, crucial for proving NP-completeness.
- **Foundational Theorem: Cook-Levin** ★★★★★
  - SAT is NP-complete, serving as the basis for reductions to other NP-complete problems.
- **Common Pitfall: Input Representation** ★★★☆☆
  - Use efficient encodings (e.g., binary for numbers) to avoid artificially inflating complexity.
- **Advanced Insight: NP vs. coNP** ★★★☆☆
  - It’s unknown if NP equals coNP, but PTIME is in both, highlighting complexity class relationships.
- **Practical Application: NP-Complete Problems** ★★★★☆
  - Problems like TSP, SUBSETSUM, and UHAMPATH are NP-complete, with broad applications but potential intractability.
