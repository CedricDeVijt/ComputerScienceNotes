## 3.1 Definitions and Basic Concepts

### Space Complexity of Algorithms

- **Deterministic Turing Machine (DTM):**
  Space complexity $space_M(w)$ = number of tape cells scanned by TM $M$ on input $w$.
  Worst-case space complexity: $s_M(n) = \max\{space_M(w) | |w|=n\}$.
- **Non-deterministic Turing Machine (NTM):**
  Space complexity = maximum cells scanned in any computation branch.

### Space Complexity Classes

- **DSPACE(s(n)):** Languages decidable by a DTM using $O(s(n))$ space.
- **NSPACE(s(n)):** Languages decidable by an NTM using $O(s(n))$ space.
- **PSPACE:** $⋃_k DSPACE(n^k)$.
- **NPSPACE:** $⋃_k NSPACE(n^k)$.
- **LOGSPACE:** $DSPACE(\log n)$.
- **NLOGSPACE:** $NSPACE(\log n)$.

## 3.2 Key Theorems and Results

### Savitch’s Theorem

- **Statement:** If $s(n) ≥ n$, then $NSPACE(s(n)) \subseteq DSPACE(s^2(n))$.
- **Corollary:** $PSPACE = NPSPACE$.
- **Proof Idea:** Simulate NTM paths using a recursive $IsReachable$ procedure with $O(s^2(n))$ space.

### Immerman-Szelepcsényi Theorem

- **Statement:** $NLOGSPACE = co-NLOGSPACE$ (non-deterministic logarithmic space is closed under complement).
- **Implications:** PATH (graph reachability) is in NLOGSPACE, and so is its complement.

## 3.3 Examples and Applications

### 3SAT in DSPACE(n)

- **Algorithm:** Enumerate all $2^m$ truth assignments for $m$ variables, reusing space.
- **Space Usage:** Linear in input size.

### PATH Problem

- **Definition:** Decide if a path exists from $s$ to $t$ in a directed graph.
- **NLOGSPACE Algorithm:**
  1. Track current node and a counter (logarithmic space).
  2. Non-deterministically guess the next node in the path.

### TQBF (True Quantified Boolean Formulas)

- **Definition:** Decide if a fully quantified Boolean formula is true.
- **PSPACE-Completeness:**
  - **Proof:** Recursive evaluation of quantifiers with $O(n)$ stack depth.
  - **Example:** $\forall y\exists x(x∨y)∧(¬x∨¬y)$ evaluates via backtracking.

### ALLₙꜰₐ (Universality of NFA)

- **Reduction to Emptiness Check:**
  1. Convert NFA to DFA (exponential blowup).
  2. Check reachability of non-accepting states.
- **Space Complexity:** Naïve method uses exponential space; optimized non-deterministic method uses polynomial space.

## 3.4 Relationships Between Complexity Classes

1. **Hierarchy:**
   $PTIME \subseteq NP \subseteq PSPACE = NPSPACE \subseteq EXPTIME$.
2. **LOGSPACE vs. NLOGSPACE:**
   - $LOGSPACE \subseteq NLOGSPACE \subseteq PTIME$.
   - It is unknown if $LOGSPACE = NLOGSPACE$.
3. **PSPACE vs. EXPTIME:**
   $PSPACE \subseteq EXPTIME$ due to the exponential time required to explore all configurations.

## 3.5 Completeness and Reductions

### PSPACE-Completeness

- **Definition:** A language $B$ is PSPACE-complete if:
  1. $B \in PSPACE$.
  2. Every $A \in PSPACE$ is polynomial-time reducible to $B$.
- **Examples:**
  - **TQBF:** PSPACE-complete.
  - **Formula Game (GG):** PSPACE-complete via reduction from TQBF.

### NLOGSPACE-Completeness

- **Definition:** A language $B$ is NLOGSPACE-complete if:
  1. $B \in NLOGSPACE$.
  2. Every $A \in NLOGSPACE$ is LOGSPACE-reducible to $B$.
- **Examples:**
  - **PATH:** NLOGSPACE-complete.
  - **2SAT:** NLOGSPACE-complete via reduction from PATH.

## 3.6 Advanced Topics

### LOGSPACE Reductions

- **Definition:** A function $f$ is LOGSPACE-computable if a 3-tape TM computes it using $O(log n)$ work tape.
- **Key Property:** LOGSPACE reductions preserve membership in complexity classes (e.g., $LOGSPACE$, $NLOGSPACE$).

### Space vs. Time

- **Configurations:** A TM using $O(s(n))$ space has $2^O(s(n))$ configurations.
- **Time Bound:** Such a TM halts in $2^O(s(n))$ time to avoid cycles.

---

## Key Points to Remember

- **Savitch’s Theorem:** Non-deterministic space can be simulated deterministically with quadratic space.
- **Immerman-Szelepcsényi:** NLOGSPACE is closed under complement.
- **PSPACE-Completeness:** TQBF and games like Geography are canonical PSPACE-complete problems.
- **NLOGSPACE-Completeness:** PATH is the fundamental NLOGSPACE-complete problem.
- **Hierarchy Inclusions:**
  - $PTIME \subseteq NP \subseteq PSPACE \subseteq EXPTIME$.
  - $LOGSPACE \subseteq NLOGSPACE \subseteq PTIME$.
- **Reductions:** LOGSPACE reductions are critical for defining completeness in logarithmic space classes.
- **Key Problems:**
  - **3SAT \in DSPACE(n)** (linear space).
  - **PATH \in NLOGSPACE** (logarithmic space).
