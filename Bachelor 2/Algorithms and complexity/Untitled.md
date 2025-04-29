## Introduction to Time Complexity

Time complexity theory investigates the **resources** (time, memory) required to solve computational problems, focusing on **time** as the primary metric. This chapter introduces how to measure and classify the time needed for algorithms, particularly using **Turing machines**, and explores the implications of problems requiring excessive time. Why is time complexity critical for practical solvability? Understanding it helps distinguish between theoretically solvable problems and those feasible in real-world applications.

### Measuring Time Complexity

**Time complexity** quantifies the number of steps an algorithm takes as a function of input size, denoted ( n ). For a deterministic Turing machine, the **running time** ( f(n) ) is the maximum steps taken on any input of length ( n ). How does this differ across inputs? **Worst-case analysis** considers the longest running time for inputs of size ( n ), while **average-case** looks at the average, though worst-case is more common in this context.

#### Example: Analyzing Language ( A = {0^k 1^k \mid k \geq 0} )

Consider a single-tape Turing machine ( M_1 ) deciding the language ( A = {0^k 1^k \mid k \geq 0} ). Its algorithm scans the tape to ensure ( 0 )'s precede ( 1 )'s, crosses off matching pairs, and checks for equality. Each scan takes ( O(n) ) steps, with at most ( n/2 ) scans, yielding a total time of ( O(n^2) ). Can we do better? ↗ See Section 1.3 for faster approaches.

### Big-O and Small-O Notation

**Asymptotic analysis** simplifies running time expressions by focusing on the **highest-order term**, ignoring constants and lower-order terms. **Big-O notation** (( f(n) = O(g(n)) )) indicates ( f(n) ) is bounded by a constant multiple of ( g(n) ) for large ( n ). **Small-O notation** (( f(n) = o(g(n)) )) is stricter, requiring ( f(n)/g(n) \to 0 ). Why use these? They provide a standardized way to compare algorithm efficiency.

#### Formal Definitions

- **Big-O**: ( f(n) = O(g(n)) ) if there exist constants ( c, n_0 ) such that ( f(n) \leq c g(n) ) for all ( n \geq n_0 ).
- **Small-O**: ( f(n) = o(g(n)) ) if ( \lim_{n \to \infty} f(n)/g(n) = 0 ).
- **Example**: For ( f(n) = 5n^3 + 2n^2 + 22n + 6 ), the highest-order term is ( 5n^3 ), so ( f(n) = O(n^3) ). Is ( f(n) = O(n^2) )? No, as lower-order terms cannot bound it.

#### Logarithmic Interactions

Logarithms in big-O notation ignore the base due to the identity ( \log_b n = \log_2 n / \log_2 b ), a constant factor. For ( f(n) = 3n \log_2 n + 5n \log_2 \log_2 n + 2 ), the dominant term is ( 3n \log_2 n ), so ( f(n) = O(n \log n) ). Why is the base irrelevant? Constant factors are suppressed in asymptotic analysis.

### Optimizing Algorithms for Language ( A )

The single-tape Turing machine ( M_1 ) for ( A ) runs in ( O(n^2) ), but a more efficient machine ( M_2 ) achieves ( O(n \log n) ) by halving the number of ( 0 )'s and ( 1 )'s per scan. A two-tape machine ( M_3 ) further reduces this to ( O(n) ) by copying ( 0 )'s to a second tape and matching them against ( 1 )'s. Why does the model matter? Different Turing machine configurations impact time complexity significantly.

#### Analysis of ( M_2 )

( M_2 ) checks input format, verifies even/odd parity of remaining symbols, and crosses off every other ( 0 ) and ( 1 ). Each stage takes ( O(n) ), with at most ( 1 + \log_2 n ) iterations, resulting in ( O(n \log n) ). This is optimal for single-tape machines, as any language decidable in ( o(n \log n) ) is regular (Problem 7.49). What limits further improvement? The need to scan the entire tape repeatedly.

#### Analysis of ( M_3 )

( M_3 ) uses two tapes: one for input, another to store ( 0 )'s. Each of its four stages—checking format, copying ( 0 )'s, matching ( 1 )'s, and verifying—takes ( O(n) ), totaling ( O(n) ). Why is this linear time optimal? Reading the input alone requires ( n ) steps.

## Complexity Relationships Among Computational Models

The choice of computational model affects time complexity, unlike in computability theory where models are equivalent per the **Church-Turing thesis**. This chapter explores how **single-tape**, **multitape**, and **nondeterministic Turing machines** relate in terms of time efficiency. How do these models compare? Polynomial differences exist between deterministic models, but exponential gaps separate deterministic and nondeterministic ones.

### Single-Tape vs. Multitape Turing Machines

**Theorem 7.8** states that a multitape Turing machine running in ( t(n) \geq n ) time can be simulated by a single-tape machine in ( O(t^2(n)) ). The single-tape machine represents all tapes consecutively, scanning and updating them in ( O(t(n)) ) per step, with ( t(n) ) steps total. Why the quadratic increase? Simulating multiple tape heads requires repeated tape traversals.

#### Proof Details

A ( k )-tape machine ( M ) is simulated by a single-tape machine ( S ). ( S ) formats its tape to mimic ( M )'s tapes, with each step requiring two scans and possible shifts, each ( O(t(n)) ). Total time is ( O(n) + t(n) \cdot O(t(n)) = O(t^2(n)) ). How does this impact language ( A )? ↗ See Section 1.3 for ( M_3 )'s linear time on two tapes.

### Deterministic vs. Nondeterministic Turing Machines

**Theorem 7.11** shows that a nondeterministic Turing machine (NTM) running in ( t(n) \geq n ) time can be simulated by a deterministic single-tape machine in ( 2^{O(t(n))} ). The NTM’s **running time** is the maximum steps on any branch. The deterministic machine explores the NTM’s computation tree breadth-first, with up to ( b^{t(n)} ) nodes, where ( b ) is the branching factor. Why the exponential blowup? All possible branches must be checked.

#### Proof Details

For an NTM ( N ), a deterministic machine ( D ) simulates all branches. The computation tree has ( O(b^{t(n)}) ) nodes, each visited in ( O(t(n)) ), yielding ( O(t(n) b^{t(n)}) = 2^{O(t(n))} ). Converting ( D ) to a single-tape machine squares this, but remains ( 2^{O(t(n))} ). What does this imply for NP problems? ↗ See Section 3.1 for NP definitions.

## The Class P: Polynomial Time Problems

The class **P** encompasses languages decidable in **polynomial time** (( O(n^k) )) on a deterministic single-tape Turing machine. It’s robust across polynomially equivalent models and represents problems practically solvable. Why is P significant? It captures algorithms efficient enough for real-world applications, unlike exponential-time brute-force methods.

### Defining P

Formally, ( \mathbf{P} = \bigcup_k \operatorname{TIME}(n^k) ), where ( \operatorname{TIME}(t(n)) ) is the set of languages decidable in ( O(t(n)) ) time. Polynomial differences between models don’t affect P’s membership, making it model-invariant. What problems are in P? Examples include pathfinding, primality testing, and context-free language recognition.

#### Robustness of P

All reasonable deterministic models are **polynomially equivalent**, meaning a polynomial-time algorithm on one can be converted to another with polynomial overhead (e.g., Theorem 7.8). Why ignore polynomial differences? It focuses on fundamental properties, not model-specific details. ↗ See Section 2.1 for model comparisons.

### Examples of Problems in P

To show a problem is in P, provide a polynomial-time algorithm with a polynomial number of stages, each implementable in polynomial time. Encoding must be **reasonable** (e.g., binary, not unary) to avoid exponential blowup. What makes an algorithm polynomial? Careful stage design and efficient subproblem handling.

#### PATH: Finding Directed Paths

**PATH** = ( {\langle G, s, t \rangle \mid G \text{ has a directed path from } s \text{ to } t} ) is in P. A breadth-first search algorithm marks reachable nodes iteratively, running in ( O(m) ) stages (where ( m ) is the number of nodes), each polynomial. Why avoid brute force? Checking all paths yields ( m^m ), which is exponential. ↗ See Section 4.2 for Hamiltonian paths.

#### RELPRIME: Testing Relative Primality

**RELPRIME** = ( {\langle x, y \rangle \mid x \text{ and } y \text{ are relatively prime}} ) uses the **Euclidean algorithm**to compute ( \gcd(x, y) ). It reduces ( x ) by at least half every other iteration, running in ( O(\log x) ), proportional to input length, hence polynomial. Why not search divisors? That’s exponential in the number’s magnitude.

#### Context-Free Language Recognition

Every **context-free language** (CFL) is in P via a **dynamic programming** algorithm. For a string ( w ) of length ( n ) and a CFG in Chomsky normal form, it builds an ( n \times n ) table to check if variables generate substrings, running in ( O(n^3) ). Why dynamic programming? It avoids exponential derivation checks. ↗ See Section 5.2 for exercise solutions.

## The Class NP: Polynomially Verifiable Problems

**NP** includes languages where a solution can be **verified** in polynomial time by a deterministic Turing machine, even if finding the solution is hard. Problems like **HAMPATH** and **COMPOSITES** are in NP due to their verifiable certificates. Why study NP? It includes many practical problems where verification is easier than computation.

### Defining NP

A language is in NP if there exists a polynomial-time verifier that accepts a string and a **certificate** (proof of membership). Formally, a nondeterministic Turing machine can decide it in polynomial time. How does this relate to P? ( \mathbf{P} \subseteq \mathbf{NP} ), but whether ( \mathbf{P} = \mathbf{NP} ) is unknown.

#### Polynomial Verifiability

For **HAMPATH**, a certificate is the path itself, verifiable in ( O(m) ) by checking node visits. For **COMPOSITES**, factors ( p, q ) verify ( x = pq ). Why is verification fast? Certificates encode the solution directly, bypassing search.

### NP-Complete Problems

A problem is **NP-complete** if it is in NP and every NP problem is **polynomial-time reducible** to it. **3SAT** is NP-complete, serving as a benchmark for reductions. Why are NP-complete problems critical? Solving one in polynomial time would imply ( \mathbf{P} = \mathbf{NP} ).

#### 3SAT and Reductions

**3SAT** involves 3-CNF formulas (e.g., ( (x_1 \vee \bar{x_2} \vee x_3) \wedge \ldots )). A certificate is a satisfying assignment, verifiable in ( O(n) ). Reductions from 3SAT to other problems (e.g., **VERTEX-COVER**, **HAMPATH**) establish their NP-completeness. How do reductions work? They transform instances while preserving solvability.

## Additional NP-Complete Problems

This chapter details reductions proving NP-completeness for **VERTEX-COVER**, **HAMPATH**, **UHAMPATH**, and **SUBSET-SUM**. Each uses gadgets to simulate 3SAT’s structure. Why are these reductions complex? They must preserve satisfiability in a different problem domain.

### VERTEX-COVER

**VERTEX-COVER** = ( {\langle G, k \rangle \mid G \text{ has a vertex cover of size } k} ) is NP-complete. A reduction from 3SAT creates variable gadgets (edges for true/false) and clause gadgets (triples requiring two nodes unless a true literal helps). Total nodes = ( 2m + 3l ), ( k = m + 2l ). Why does this work? The cover size enforces clause satisfaction.

#### Reduction Details

For a 3SAT formula with ( m ) variables and ( l ) clauses, the graph has ( 2m + 3l ) nodes. Variable gadgets ensure one node per variable, clause gadgets need two unless a true literal covers an edge. If satisfiable, a cover of size ( k ) exists; if a cover exists, a satisfying assignment follows. ↗ See Section 5.5 for exercise solutions.

### HAMPATH

**HAMPATH** = ( {\langle G, s, t \rangle \mid G \text{ has a Hamiltonian path from } s \text{ to } t} ) is NP-complete. A reduction from 3SAT uses diamond structures for variables (zig-zag for true, zag-zig for false) and nodes for clauses. Detours to clause nodes ensure satisfaction. Why normal paths? Non-normal paths violate edge constraints.

#### Reduction Details

The graph has diamonds with ( 3k + 1 ) horizontal nodes per variable, plus clause nodes. A satisfiable formula yields a path via detours; a path implies a satisfying assignment by observing zig-zags. The reduction is polynomial, computing edges in ( O(n^2) ). ↗ See Section 4.1 for PATH contrast.

### UHAMPATH

**UHAMPATH**, the undirected version, is NP-complete via reduction from HAMPATH. Each node ( u ) (except ( s, t )) becomes a triple ( u^{\text{in}}, u^{\text{mid}}, u^{\text{out}} ), with edges enforcing directed path structure. Why does this preserve Hamiltonian property? The triple forces sequential traversal.

### SUBSET-SUM

**SUBSET-SUM** = ( {\langle S, t \rangle \mid S \text{ has a subset summing to } t} ) is NP-complete. A reduction from 3SAT creates numbers ( y_i, z_i ) for variables and ( g_j, h_j ) for clauses, with a target ( t ) of ( l ) 1’s and ( k ) 3’s. The subset encodes a satisfying assignment. Why no carries? Digits are 0 or 1, limiting sums.

#### Reduction Details

The table has ( l + k ) columns, with ( y_i, z_i ) ensuring one choice per variable, and ( g_j, h_j ) adjusting clause digits to 3. A satisfiable formula yields a subset summing to ( t ); a subset implies a satisfying assignment. The table is computed in ( O((k+l)^2) ). ↗ See Section 5.5 for unary variant.

## Exercises and Solutions

This chapter covers selected exercises and solutions, reinforcing time complexity concepts through practical problems. Solving these builds intuition for P, NP, and reductions. Why practice these? They test understanding of asymptotic analysis, algorithm design, and NP-completeness proofs.

### Asymptotic Analysis Exercises

- **7.1**: Determine if statements like ( 2n = O(n) ) (TRUE) or ( n^2 = O(n \log^2 n) ) (FALSE) hold. Use Definition 7.2 to verify bounds.
- **7.2**: Check small-o relations, e.g., ( n = o(n) ) (FALSE, as ( n/n \to 1 )).

### Algorithm Design Exercises

- **7.4**: Fill a dynamic programming table for CFL recognition on ( w = \text{baba} ) with given CFG. The table tracks variables generating substrings, computed in ( O(n^3) ).
- **7.8**: Show **CONNECTED** is in P using a graph traversal algorithm, running in ( O(m) ).

### NP-Completeness Exercises

- **7.16**: Prove NP is closed under star operation. An NTM guesses string divisions and verifies each piece, running in polynomial time.
- **7.23**: Reduce **CLIQUE** to **HALF-CLIQUE**. Adjust node counts to ensure a ( k )-clique in ( G ) matches a half-sized clique in ( H ).
- **7.33**: Reduce 3SAT to **SOLITAIRE**. A ( k \times m ) board with blue/red stones encodes variables and clauses, solvable if satisfiable.

## Key Points to Remember

- **Time Complexity → Measure Steps**: Use ( f(n) ) as the maximum steps for input length ( n ). ★★★★☆
- **Asymptotic Analysis → Big-O/Small-O**: Focus on highest-order terms; ( f(n) = O(g(n)) ) bounds by constant, ( o(g(n)) ) by diminishing ratio. ★★★★☆
- **Model Impact → Single vs. Multitape**: Multitape to single-tape simulation squares time (( O(t^2(n)) )); nondeterministic to deterministic is exponential (( 2^{O(t(n))} )). ★★★★★
- **P Class → Polynomial Time**: ( \mathbf{P} = \bigcup_k \operatorname{TIME}(n^k) ), robust and practical. ★★★★★
- **NP Class → Verifiable**: Problems with polynomial-time certificates; NP-complete if all NP problems reduce to it. ★★★★★
- **Reductions → Prove NP-Completeness**: 3SAT reduces to VERTEX-COVER, HAMPATH, etc., using gadgets to mimic logic. ★★★★★
- **Common Pitfall → Brute Force**: Avoid exponential searches (e.g., ( m^m ) for PATH); use techniques like dynamic programming. ★★★★☆
- **Critical Distinction → P vs. NP**: If ( \mathbf{P} = \mathbf{NP} ), NP-complete problems like HAMPATH would be in P, revolutionizing computation. ★★★★★