## 3.1 Introduction to Space Complexity

Space complexity measures the amount of memory an algorithm uses relative to its input size, a critical aspect of computational efficiency. This chapter introduces key concepts like deterministic and non-deterministic space complexity, focusing on how algorithms utilize memory on Turing Machines (TMs). It connects foundational theorems like Savitch’s and Immerman-Szelepcsényi’s to practical problems like 3SAT and TQBF, emphasizing their role in defining complexity classes.

### Defining Space Complexity

**Space complexity** quantifies the memory required by a Turing Machine (TM) to process an input of length $n$, denoted as $s_M(n)$. It is distinct from time complexity, as it focuses on memory cells used rather than computational steps. For deterministic TMs, space usage is measured by the maximum number of tape cells used across all inputs of length $n$. Non-deterministic TMs (NTMs) consider the worst-case space usage across all computation paths.

#### Space Complexity for Deterministic TMs

- A TM $M$ uses $O(s(n))$ space if its space complexity function $s_M(n)$ is of order $O(s(n))$, where $|w| = n$ is the input length.
- Example: A deterministic TM solving 3SAT in $\text{DSPACE}(n)$ reuses space for each of the $2^m$ truth assignments, achieving linear space but exponential time.

#### Space Complexity for Non-Deterministic TMs

- For NTMs, the **worst-case space complexity** accounts for the maximum space used across all computation branches, assuming every branch halts.
- Example: An NTM $M$ uses $O(s(n))$ space if $s_M(n) = O(s(n))$, as seen in problems like TQBF, which evaluates quantified Boolean formulas recursively.

### Space Complexity Classes

Space complexity classes categorize problems based on the memory required by TMs or NTMs. **DSPACE** and **NSPACE** denote deterministic and non-deterministic space classes, respectively, with specific bounds like $\text{DSPACE}(s(n))$ for languages decided by a deterministic TM using $O(s(n))$ space.

#### DSPACE and NSPACE Definitions

- **DSPACE($s(n)$)**: Set of languages decided by a deterministic TM using $O(s(n))$ space.
- **NSPACE($s(n)$)**: Set of languages decided by a non-deterministic TM using $O(s(n))$ space.
- Example: 3SAT is in $\text{DSPACE}(n)$, as it evaluates truth assignments in linear space by reusing memory.

#### PSPACE and NPSPACE

- **PSPACE** = $\bigcup\limits_k \text{DSPACE}(n^k)$: Languages decidable in polynomial space by deterministic TMs.
- **NPSPACE** = $\bigcup\limits_k \text{NSPACE}(n^k)$: Languages decidable in polynomial space by non-deterministic TMs.
- Key Insight: Savitch’s Theorem shows $\text{PSPACE} = \text{NPSPACE}$, implying non-determinism does not significantly expand polynomial space capabilities.

## 3.2 Savitch’s Theorem: Bridging PSPACE and NPSPACE

Savitch’s Theorem is a cornerstone of complexity theory, proving that deterministic and non-deterministic polynomial space classes are equivalent. It demonstrates that any problem solvable in non-deterministic space $s(n) \geq n$ can be solved deterministically in $s(n)^2$ space, impacting our understanding of space-efficient algorithms.

### Statement and Implications

- **Theorem (Savitch)**: If $s(n) \geq n$, then $\text{NSPACE}(s(n)) \subseteq \text{DSPACE}(s(n)^2)$.
- **Corollary**: $\text{PSPACE} = \text{NPSPACE}$, as any non-deterministic polynomial space algorithm can be simulated deterministically with a quadratic space increase.
- This implies that problems like TQBF and generalized geography, which are PSPACE-complete, can be solved deterministically with polynomial space.

#### Configuration Graph

- A **configuration graph** $G(N, w)$ represents all possible states of an NTM $N$ on input $w$, with nodes as configurations and edges as transitions.
- For an NTM using $O(s(n))$ space, the graph has at most $2^{O(s(n))}$ configurations, and paths are limited to $2^{O(s(n))}$ steps to avoid infinite loops.
- Example: Checking reachability in this graph is central to Savitch’s proof, using a procedure called **IsBereikbaar**.

#### IsBereikbaar Procedure

- **Procedure IsBereikbaar($c_1, c_2, t$)**: Determines if configuration $c_2$ is reachable from $c_1$ in at most $t$ steps.
- It recursively divides paths into two segments of length $t/2$, checking intermediate configurations.
- Space usage: Each recursive call stores $O(s(n))$ space, with $O(s(n))$ recursion depth, totaling $O(s(n)^2)$ space.
- Example: For an NTM deciding PATH, IsBereikbaar verifies if a path exists between nodes in logarithmic space, leveraging space reuse.

## 3.3 Time vs. Space Complexity

This chapter contrasts time and space complexity, highlighting their interplay in algorithm design. A TM using $O(s(n))$ space has $2^{O(s(n))}$ possible configurations, limiting its runtime to exponential time, which establishes relationships like $\text{PTIME} \subseteq \text{PSPACE} \subseteq \text{EXPTIME}$.

### Relationships Between Complexity Classes

- **PTIME $\subseteq$ PSPACE**: Polynomial-time TMs scan only a polynomial number of tape cells, fitting within polynomial space.
- **NP $\subseteq$ NPSPACE**: Non-deterministic polynomial-time problems are solvable in polynomial space, as verification paths are bounded.
- **PSPACE = NPSPACE**: Savitch’s Theorem ensures non-deterministic space advantages are nullified in polynomial bounds.
- Open Question: Whether these inclusions are strict remains a million-dollar problem in complexity theory.

#### Practical Implications

- Example: 3SAT runs in exponential time but linear space, illustrating that space-efficient algorithms may sacrifice time efficiency.
- Insight: Problems like TQBF, which are PSPACE-complete, often require exponential time due to their complex decision trees, despite polynomial space usage.

## 3.4 PSPACE-Completeness

PSPACE-complete problems characterize the hardest problems in PSPACE, requiring polynomial space and serving as benchmarks for complexity. This section explores problems like TQBF and generalized geography, which capture the essence of PSPACE through reductions.

### Defining PSPACE-Completeness

- A language $B$ is **PSPACE-complete** if:
  - $B \in \text{PSPACE}$, and
  - Every language $A \in \text{PSPACE}$ is polynomially reducible to $B$.
- **Reduction**: A polynomial-time computable function $f$ such that $w \in A \iff f(w) \in B$.
- Example: TQBF (True Quantified Boolean Formula) is PSPACE-complete, as it involves evaluating fully quantified Boolean formulas.

#### TQBF: True Quantified Boolean Formulas

- **Definition**: TQBF = $\{ \langle\phi\rangle \mid \phi \text{ is a fully quantified Boolean formula that is true} \}$.
- **Algorithm**: A TM $M$ evaluates $\phi = Q_1 x_1 Q_2 x_2 \ldots Q_k x_k \varphi$ recursively, using $O(k)$ space by reusing memory for each variable assignment.
- Example: For $\forall y \exists x (x \vee y) \wedge (\neg x \vee \neg y)$, $M$ checks all combinations, accepting if there exists an $x$ for every $y$, using linear space.
- **PSPACE-Hardness**: Any PSPACE language can be reduced to TQBF by encoding TM configurations as quantified variables, mirroring the Cook-Levin theorem for NP.

#### Generalized Geography as a Game

- **Definition**: GG = $\{ (G, b) \mid \text{Player I has a winning strategy in generalized geography on graph } G \text{ starting at node } b \}$.
- **Game Rules**: Players alternate choosing unvisited nodes in a directed graph; a player loses if no moves remain.
- **PSPACE-Completeness**: GG is in PSPACE (recursive algorithm with $O(m)$ space) and PSPACE-hard via reduction from TQBF, where the graph encodes variable assignments and clause evaluations.
- Example: A graph with “diamond” structures for variables allows Player I to set truth values, while Player II selects clauses, mirroring TQBF’s structure.

## 3.5 Logarithmic Space Complexity: LOGSPACE and NLOGSPACE

Logarithmic space classes focus on highly space-efficient algorithms, using TMs with read-only input tapes and work tapes. LOGSPACE and NLOGSPACE handle problems solvable with logarithmic memory, such as recognizing balanced strings or finding graph paths.

### Defining LOGSPACE and NLOGSPACE

- **LOGSPACE**: Languages decidable by a deterministic TM with a read-only input tape and a work tape using $O(\log n)$ space.
- **NLOGSPACE**: Languages decidable by a non-deterministic TM with similar constraints.
- Example: The language $\{ 0^k 1^k \mid k \geq 0 \}$ is in LOGSPACE, using two logarithmic-sized counters to verify equal counts of 0s and 1s.

#### Example: PATH in NLOGSPACE

- **Problem**: PATH = $\{ (G, s, t) \mid G \text{ has a directed path from } s \text{ to } t \}$.
- **Algorithm**: Non-deterministically guess a path of length at most $n$, using $O(\log n)$ space to store node pointers and a counter.
- Insight: PATH’s simplicity makes it a candidate for NLOGSPACE-completeness, as it can be reduced from other NLOGSPACE problems.

### NLOGSPACE-Complete Problems

- A language $B$ is **NLOGSPACE-complete** if:
  - $B \in \text{NLOGSPACE}$, and
  - Every $A \in \text{NLOGSPACE}$ is LOGSPACE-reducible to $B$.
- **LOGSPACE Reduction**: A function $f$ computable in $O(\log n)$ space, such that $w \in A \iff f(w) \in B$.

#### PATH is NLOGSPACE-Complete

- **Proof**: PATH is in NLOGSPACE (see above). For any $A \in \text{NLOGSPACE}$, construct a graph $G$ where nodes are configurations of the NTM deciding $A$, and edges are transitions. $w \in A \iff$ there is a path from the initial to the accepting configuration.
- Example: The reduction maps an NTM’s computation to a path-finding problem, using logarithmic space to generate configurations.

#### 2SAT is NLOGSPACE-Complete

- **Problem**: 2SAT = $\{ \phi \mid \phi \text{ is a 2-CNF formula that is satisfiable} \}$.
- **Algorithm**: Check if there exists a literal $x$ with paths to $\bar{x}$ and vice versa in the implication graph, using an NLOGSPACE path-finding algorithm.
- **NLOGSPACE-Hardness**: Reduce $\overline{\text{PATH}}$ to 2SAT by constructing clauses like $(\bar{a} \vee b)$ for edges $(a, b)$, ensuring satisfiability if no path exists.
- Example: For a graph with no path from $s$ to $t$, the formula $s \wedge \neg t \wedge \bigwedge\_{(a,b) \in E} (\bar{a} \vee b)$ is satisfiable.

## 3.6 Immerman-Szelepcsényi Theorem: NLOGSPACE = co-NLOGSPACE

The Immerman-Szelepcsényi Theorem proves that NLOGSPACE is closed under complementation, meaning the complement of any NLOGSPACE language is also in NLOGSPACE. This is significant for problems like $\overline{\text{PATH}}$, which can be solved efficiently in non-deterministic logarithmic space.

### Theorem Statement

- **Theorem**: $\text{NLOGSPACE} = \text{co-NLOGSPACE}$.
- **Proof Strategy**: Show that $\overline{\text{PATH}}$ is in NLOGSPACE, leveraging PATH’s NLOGSPACE-completeness to generalize the result.
- Key Insight: The algorithm counts reachable nodes non-deterministically, reusing space to stay within logarithmic bounds.

#### Algorithm for $\overline{\text{PATH}}$

- **Input**: Graph $G = (V, E)$, nodes $s, t$, with $|V| = m$.
- **Step 1: Compute $c$**, the number of nodes reachable from $s$:
  - Define $A_i$: Nodes reachable in at most $i$ steps, with $c_i = |A_i|$.
  - Compute $c*{i+1}$ from $c_i$: For each node $v$, check if $v \in A*{i+1}$ by guessing paths through nodes in $A_i$, using $O(\log m)$ space for counters and pointers.
- **Step 2: Verify No Path**: Use $c$ to check if $t$ is unreachable by guessing all reachable nodes and ensuring $t$ is not among them.
- Example: For a graph with 10 nodes, the algorithm iteratively builds $c_i$, storing only the current node, counter, and path pointers, all in logarithmic space.

#### Space Efficiency

- The work tape stores:
  - Current nodes $u, v$: $O(\log m)$ space.
  - Counters $c_i, d, i$: $O(\log m)$ space.
  - Path pointers: $O(\log m)$ space.
- Total: $O(\log m)$ space, ensuring the algorithm is in NLOGSPACE.

---

## Key Points to Remember

- **Space Complexity → Measuring Memory**: Space complexity $s_M(n)$ tracks the memory cells used by a TM, distinct from time complexity, with deterministic and non-deterministic variants. ★★★★☆
- **Savitch’s Theorem → PSPACE = NPSPACE**: Any NSPACE($s(n)$) problem can be solved in DSPACE($s(n)^2$), proving PSPACE equals NPSPACE. ★★★★★
- **PSPACE-Completeness → TQBF and GG**: TQBF and generalized geography are PSPACE-complete, representing the hardest problems in PSPACE via polynomial reductions. ★★★★☆
- **LOGSPACE and NLOGSPACE → Efficient Memory**: LOGSPACE and NLOGSPACE handle problems with logarithmic space, using read-only input and work tapes, as seen in $\{0^k 1^k\}$ and PATH. ★★★★☆
- **NLOGSPACE-Completeness → PATH and 2SAT**: PATH and 2SAT are NLOGSPACE-complete, with LOGSPACE reductions ensuring efficient transformations. ★★★★☆
- **Immerman-Szelepcsényi → NLOGSPACE Closure**: NLOGSPACE = co-NLOGSPACE, proven by an NLOGSPACE algorithm for $\overline{\text{PATH}}$, using non-deterministic counting. ★★★★★
- **Critical Distinction → Time vs. Space**: Space-efficient algorithms (e.g., 3SAT in linear space) may require exponential time, highlighting trade-offs in complexity classes. ★★★★☆
- **Common Pitfall → Assuming Strict Inclusions**: Relationships like PTIME $\subseteq$ PSPACE are known, but whether they are strict remains an open question. ★★★☆☆
