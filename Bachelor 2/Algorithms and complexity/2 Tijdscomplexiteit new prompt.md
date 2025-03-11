## 2.1 Foundations of Polynomial Time Computation (PTIME)

### Defining Efficiency in Computation

**Polynomial time (PTIME)** classifies problems solvable by deterministic Turing machines in O(n^k) steps. Key distinction: Separates tractable (n^3) from intractable (2^n) problems. Why does this matter? Exponential time implies impractical resource growth for large inputs.

#### DTIME and Complexity Classes

- **DTIME(t(n))**: Languages decidable in O(t(n)) time. Example: Palindromes ∈ DTIME(n²) using a two-pointer approach.
- **PTIME = ∪ DTIME(n^k)**: Union over all polynomial time bounds. Represents "efficiently solvable" problems.

#### Practical Implications

- **CPU Time Table**: Shows drastic differences between polynomial (n³) and exponential (2ⁿ) runtimes. At n=100, 2ⁿ takes ~4e13 years vs. 1 ms for n³.
- **Key Insight**: Polynomial algorithms often have small exponents (n, n²), making them feasible in practice.

### PTIME Problem Examples

#### PATH Problem

- **Definition**: {(G,s,t) | G has a path from s to t}.
- **Algorithm**: Breadth-First Search (BFS) runs in O(m) time (m = edges). Steps: Mark nodes iteratively from s until reaching t.

#### RELPRIME Problem

- **Definition**: {(x,y) | gcd(x,y)=1}.
- **Algorithm**: Euclidean algorithm computes gcd in O(log max(x,y)) iterations. Each iteration reduces problem size by ~half.

## 2.2 Non-Deterministic Polynomial Time (NP)

### Verifiers and Certificates

**NP** contains problems with polynomial-time verifiable proofs (certificates). Example: SAT certificates are truth assignments validating formulas.

#### Formal Definition

- **Verifier**: TM V accepts (w,c) in poly-time if w ∈ L. Example: CLIQUE verifier checks if a k-node subgraph is fully connected.
- **NTM Connection**: NP = ∪ NTIME(n^k). NTMs "guess" certificates (e.g., paths for HAMPATH) followed by deterministic checks.

### NP-Complete Problems

#### Key Examples

- **SAT**: Boolean formula satisfiability. ↗ See Section 3.2 for Cook-Levin proof.
- **CLIQUE**: Existence of k-node complete subgraph. Reduces from 3SAT using graph construction.
- **HAMPATH**: Hamiltonian path existence. Reduces from 3SAT via diamond-structured graphs.

#### Implications of NP-Completeness

- **Hardness**: If any NP-complete problem is in PTIME, then P=NP. Current status: No poly-time algorithms found despite extensive research.

## 2.3 Reductions and Completeness

### Polynomial-Time Reductions

**Reduction (A ≤ₚ B)**: Transform A-instances to B-instances efficiently. Proves B is at least as hard as A.

#### Example: 3SAT ≤ₚ CLIQUE

- **Construction**: Convert clauses to graph groups. Edges connect non-conflicting literals across clauses.
- **Correctness**: Satisfying assignment ⇨ k-clique (one literal per clause). No edges between conflicting literals ensure validity.

### Cook-Levin Theorem

**SAT is NP-Complete**: Every NP problem reduces to SAT.

- **Proof Sketch**: Encode NTM computation as boolean formula (tableau). Variables represent cell states; clauses enforce legal transitions.

#### Tableau Construction

- **Rows**: Configurations of NTM on input w.
- **Windows**: 2x3 cell blocks ensuring local transition legality. Illegal windows ⇒ unsatisfiable formula.

### Other NP-Complete Problems

#### Vertex Cover

- **Reduction from CLIQUE**: Complement graph + size adjustment (k-clique ⇨ |V|-k vertex cover).

#### Travelling Salesman (TSP)

- **Reduction from HAMCIRCUIT**: Assign edge weights (0=exists, 1=missing). Hamiltonian cycle ⇨ TSP tour with cost 0.

#---

## Key Points to Remember

- **P vs NP**: Unsolved million-dollar question. PTIME ⊆ NP ⊆ EXPTIME. ★★★★★
- **Reduction Strategy**: 3SAT → CLIQUE → Vertex Cover → TSP forms a common proof chain. (Mnemonic: **"3CVT"**) ★★★★☆
- **Cook-Levin Insight**: Every NP computation can be encoded as SAT formula. Basis for all NP-completeness proofs. ★★★★☆
- **Critical Distinction**: PTIME (solve) vs NP (verify). Example: PATH ∈ PTIME vs HAMPATH ∈ NP. ★★★★☆
- **Common Pitfall**: Confusing NP-hard (hardness) with NP-complete (hardness + NP-membership). ↗ See Section 3.1 for clarification.
