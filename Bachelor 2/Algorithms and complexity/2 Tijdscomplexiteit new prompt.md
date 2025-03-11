## 2.1 Deterministic Polynomial Time (PTIME)

### Definition and Core Concepts

**PTIME** ($DTIME(n^k)$) represents problems solvable by deterministic Turing machines in polynomial time. It's considered the class of "efficiently solvable" problems. Key distinctions:

- Polynomial vs exponential growth: $O(n^3)$ vs $O(2^n)$ (Page 5 table shows $2^n$ becomes impractical for $n=100$)
- All deterministic computation models are polynomially equivalent

### PTIME Algorithms in Practice

#### Example 1: PATH Problem

**Problem**: Determine if path exists from $s$ to $t$ in directed graph
**Algorithm**: Breadth-First Search (BFS)

- Marks nodes reachable from $s$ in $O(m)$ steps ($m$ = nodes)
- Proof: Pages 9-10 show step-by-step marking process

#### Example 2: RELPRIME

**Problem**: Check if $x$ and $y$ are coprime
**Algorithm**: Euclidean GCD

- Time complexity: $O(\log \max(x,y))$ due to halving property
- Key insight: $\gcd(x,y) = \gcd(y, x \mod y)$

### Polynomial Equivalence

- Unary vs binary encoding matters: Binary avoids exponential input bloat
- All "reasonable" encoding schemes are polynomially convertible

## 2.2 Non-Deterministic Polynomial Time (NP)

### Definition and Verification

**NP** contains problems where solutions can be **verified** in polynomial time. Two equivalent characterizations:

1. Languages with polynomial-time verifiers
2. Decidable by non-deterministic TM in poly-time

### Key NP Problems

#### HAMPATH (Hamiltonian Path)

- Verification: Check path visits all nodes exactly once
- Non-deterministic algorithm: Guess permutation + validate

#### CLIQUE

- Verification: Check $k$-node subgraph is fully connected
- Reduction from 3SAT shown

### NP vs PTIME Relationship

- Million-dollar question: $\text{PTIME} = \text{NP}$?
- Known: $\text{PTIME} \subseteq \text{NP} \subseteq \text{EXPTIME}$

## 2.3 Reductions and Completeness

### Polynomial-Time Reductions

**Key Principle**: If $A \leq_p B$ and $B \in \text{PTIME}$, then $A \in \text{PTIME}$

- Transitivity property: $A \leq_p B \leq_p C \Rightarrow A \leq_p C$

### NP-Completeness Framework

1. **NP-Hard**: All NP problems reduce to it
2. **NP-Complete**: NP-Hard + $\in \text{NP}$

#### Cook-Levin Theorem

- **SAT is NP-Complete**: Proof via tableau construction
- Encodes TM computation as Boolean formula variables:
  - $x_{ijs} = \text{"Cell (i,j) contains symbol s"}$
  - Four formula components: cell, start, move, accept

### Reduction Examples

#### 3SAT → CLIQUE

- Clause groups become graph nodes
- Edges represent non-conflicting literals
- $k$-clique $\Rightarrow$ satisfiable assignment

#### HAMPATH → UHAMPATH (Undirected)

- Node splitting: $u \rightarrow \{u^{in}, u^{mid}, u^{out}\}$

## 2.4 NP-Complete Problem Landscape

### Key Problems and Reductions

| Problem      | Reduction From | Key Technique          |
| ------------ | -------------- | ---------------------- |
| 3SAT         | SAT            | Clause gadgets         |
| VERTEX-COVER | CLIQUE         | Complement graph       |
| TSP          | HAMCIRCUIT     | Weight encoding        |
| SUBSET-SUM   | 3SAT           | Base-10 digit encoding |

### Special Cases in P

- **2SAT**: Solvable via implication graph + SCC analysis
- **HORN-SAT**: Unit propagation algorithm

---

## Key Points to Remember

- **PTIME vs NP** ★★★★★
  - PTIME: Efficiently solvable | NP: Efficiently verifiable
  - Mnemonic: "P = Problems we can Polish off quickly"
- **Reduction Strategy** ★★★★☆
  - To prove NP-hardness: Reduce from known NP-complete problem
  - TRAP Method: Transitive Reduction Analysis Protocol
- **Cook-Levin Insight** ★★★★☆
  - Any NP problem → Boolean formula structure
  - Critical concept: Computation as formula
- **2SAT Exception** ★★★☆☆
  - In P despite being SAT variant
  - Key structure: Implication graph acyclicity
- **Encodings Matter** ★★☆☆☆
  - Binary vs unary impacts complexity
  - Example: RELPRIME input size = $O(\log \max(x,y))$
- **Common Pitfall**
  - Confusing PTIME-completeness (trivial) with NP-completeness
