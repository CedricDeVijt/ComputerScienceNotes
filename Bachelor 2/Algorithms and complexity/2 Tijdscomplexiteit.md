## 2.1 Deterministic Polynomial Time (PTIME)

### Definition and Importance

- **PTIME**: Class of problems solvable by deterministic Turing machines in polynomial time $O(n^k)$.
- **Practical relevance**:
  - Polynomial-time algorithms (e.g., $n^3$) are considered efficient; exponential algorithms (e.g., $2^n$) are impractical for large inputs.
  - All deterministic computational models are polynomially equivalent.

### Examples of PTIME Problems

- **PATH**: Determining if a path exists between nodes $s$ and $t$ in a graph (solved via BFS in $O(m)$ time).
- **RELPRIME**: Checking if two numbers are coprime (solved via the Euclidean algorithm in $O(\log n)$ time).
- **PRIMES**: Prime number testing (proven in PTIME in 2002).

### Complexity Classes

- **DTIME(t(n))**: Problems decidable in $O(t(n))$ time by a single-tape Turing machine.
- **PTIME**: Union of all $DTIME(n^k)$ for $k \geq 1$.

## 2.2 Satisfiability Problems

### Propositional Logic Basics

- **SAT**: Decision problem for satisfiable propositional formulas.
- **CNF-SAT**: SAT restricted to conjunctive normal form (CNF) formulas.
- **3SAT/2SAT**: CNF formulas with clauses of exactly 3/2 literals.
- **HORN-SAT**: CNF formulas with ≤1 positive literal per clause.

### Algorithms for Specific Cases

- **2SAT**: Solved using implication graphs and checking for contradictory paths (e.g., $x \leftrightarrow \neg x$).
- **HORN-SAT**: Solved via unit propagation and clause simplification in linear time.

### Key Theorems

- **CNF Conversion**: Any formula can be converted to CNF in polynomial time using auxiliary variables.
- **Exponential Growth Avoidance**: Introducing new variables prevents clause explosion during CNF conversion.

## 2.3 Non-Deterministic Polynomial Time (NP)

### Definition and Verifiers

- **NP**: Class of problems verifiable in polynomial time by a deterministic Turing machine.
- **Examples**:
  - **HAMPATH**: Existence of Hamiltonian paths.
  - **CLIQUE**: Finding $k$-node complete subgraphs.
  - **SAT**: Verifying truth assignments.

### NP via Non-Deterministic TMs

- A language $L \in \text{NP}$ iff it is decidable by a non-deterministic Turing machine in polynomial time.
- **Key Insight**: "Guessing" a solution (e.g., a path or assignment) followed by a polynomial check.

### PTIME vs NP

- **Open Question**: Whether PTIME = NP (one of the Millennium Prize Problems).
- **Known Relationships**:
  - $\text{PTIME} \subseteq \text{NP} \subseteq \text{EXPTIME}$.

## 2.4 Reductions, Completeness, and Hardness

### Polynomial-Time Reductions

- **Reduction $A \leq_P B$**: Transforming problem $A$ to $B$ in polynomial time.
- **Transitivity**: If $A \leq_P B$ and $B \leq_P C$, then $A \leq_P C$.

### NP-Hardness and Completeness

- **NP-Hard**: A problem is NP-hard if all NP problems reduce to it.
- **NP-Complete**: A problem is NP-complete if it is NP-hard and in NP.
- **Examples**:
  - **3SAT**: First proven NP-complete via the Cook-Levin theorem.
  - **CLIQUE**: Shown NP-complete by reducing 3SAT to CLIQUE.

## 2.5 Cook-Levin Theorem

### Core Statement

- **SAT is NP-Complete**: Every NP problem reduces to SAT in polynomial time.

### Proof Outline

1. **Tableau Representation**: Encode non-deterministic TM computations as an $n^k \times n^k$ grid.
2. **Formula Construction**:
   - **Cell Consistency**: Each cell contains exactly one symbol.
   - **Initial Configuration**: Encodes the starting state of the TM.
   - **Legal Transitions**: Ensures adjacent rows follow TM transition rules.
   - **Acceptance**: Requires at least one accepting state in the tableau.

## 2.6 NP-Complete Problems

### Classic Examples

- **CLIQUE**: Reduced from 3SAT using implication graphs.
- **VERTEX-COVER**: Complement of CLIQUE in the graph’s edge set.
- **HAMPATH**: Reduced from 3SAT using diamond-shaped variable structures and clause nodes.
- **TSP**: Reduced from Hamiltonian cycle problems.

### Numerical Problems

- **SUBSET-SUM**: Determine if a subset of numbers sums to $t$ (reduced from 3SAT).
- **PARTITION**: Special case of SUBSET-SUM where the target is half the total sum.

---

## Key Points to Remember

- **PTIME**: Efficiently solvable problems (e.g., BFS, Euclidean algorithm).
- **NP**: Problems with efficiently verifiable solutions (e.g., SAT, HAMPATH).
- **Reductions**: Tool to prove hardness; e.g., 3SAT ≤ₚ CLIQUE.
- **Cook-Levin Theorem**: SAT is NP-complete, forming the foundation for NP-completeness proofs.
- **NP-Complete Problems**:
  - Include CLIQUE, VERTEX-COVER, HAMPATH, TSP, SUBSET-SUM.
  - All are equally hard; solving one in PTIME would solve all.
- **Practical Implications**:
  - Exponential time algorithms are infeasible for large inputs.
  - No known PTIME solutions for NP-complete problems; reliance on heuristics or approximations.
