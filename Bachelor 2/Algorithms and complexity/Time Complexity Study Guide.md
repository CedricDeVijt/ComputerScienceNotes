## 1.1 Introduction to Time Complexity Theory

Time complexity theory examines the resources, particularly time, required to solve computational problems. This chapter introduces methods to measure and classify the time complexity of algorithms, focusing on deterministic and nondeterministic Turing machines. It establishes foundational concepts like **Big-O notation**, **small-o notation**, and **time complexity classes**, which are critical for understanding computational efficiency. The material also explores practical implications, such as why some decidable problems remain computationally infeasible due to excessive time requirements.

### Measuring Time Complexity
**Time complexity** quantifies the time an algorithm takes as a function of input size, typically measured in steps on a Turing machine. The chapter uses the language $A = \{0^k 1^k \mid k \geq 0\}$ to illustrate how to compute the running time of a Turing machine. **Worst-case analysis** considers the maximum steps for inputs of length $n$, while **average-case analysis** averages over all inputs. This distinction is crucial for evaluating algorithm efficiency in practical scenarios.

#### Single-Tape Turing Machine Example: $M_1$
- **Algorithm Description**: $M_1$ decides $A$ by scanning the tape to ensure the input is of the form $0^* 1^*$, then repeatedly crosses off one 0 and one 1 until none remain or a mismatch is detected.
- **Time Analysis**:
  - Stage 1 (verify $0^* 1^*$): $O(n)$ steps for scanning and repositioning.
  - Stages 2-3 (cross off 0s and 1s): Each scan is $O(n)$, with at most $n/2$ scans, yielding $O(n^2)$.
  - Stage 4 (final check): $O(n)$.
  - **Total**: $O(n^2)$, placing $A \in \operatorname{TIME}(n^2)$.
- **Connection**: This quadratic time reflects the iterative nature of single-tape operations, which later sections improve upon with multi-tape or optimized algorithms.

### Asymptotic Analysis with Big-O and Small-O Notation
**Asymptotic analysis** simplifies running time expressions by focusing on the **highest-order term**, ignoring constants and lower-order terms. **Big-O notation** ($f(n) = O(g(n))$) provides an upper bound, while **small-o notation** ($f(n) = o(g(n))$) indicates stricter dominance, where $f(n)$ grows slower than $g(n)$. These notations enable comparisons of algorithm efficiency for large inputs.

#### Big-O Notation
- **Definition**: $f(n) = O(g(n))$ if there exist constants $c, n_0$ such that $f(n) \leq c g(n)$ for all $n \geq n_0$.
- **Example**: For $f_1(n) = 5n^3 + 2n^2 + 22n + 6$, the highest-order term is $5n^3$, so $f_1(n) = O(n^3)$. This is verified by choosing $c = 6, n_0 = 10$.
- **Logarithmic Simplification**: $\log_b n = \frac{\log_2 n}{\log_2 b}$, so base changes are constant factors, and $O(\log n)$ omits the base.
- **Arithmetic**: In expressions like $O(n^2) + O(n)$, the dominant term prevails, so $O(n^2)$.

#### Small-O Notation
- **Definition**: $f(n) = o(g(n))$ if $\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0$.
- **Examples**:
  - $\sqrt{n} = o(n)$, as $\frac{\sqrt{n}}{n} = \frac{1}{\sqrt{n}} \to 0$.
  - $n \log \log n = o(n \log n)$, reflecting slower growth.
- **Key Insight**: Small-o denotes functions that are asymptotically negligible compared to the upper bound, unlike Big-O, which allows equality up to a constant.

### Optimizing Algorithms for $A$
The chapter explores faster algorithms for deciding $A$, demonstrating how design choices impact time complexity. By modifying the single-tape approach and introducing a multi-tape model, significant improvements are achieved, highlighting the influence of computational models on efficiency.

#### Improved Single-Tape Turing Machine: $M_2$
- **Algorithm**: $M_2$ checks input format, then repeatedly halves the number of 0s and 1s by crossing off every other symbol, rejecting if the count is odd.
- **Time Analysis**:
  - Stages 1, 5: $O(n)$ each, executed once.
  - Stages 2-4: Each iteration takes $O(n)$, with at most $1 + \log_2 n$ iterations, yielding $O(n \log n)$.
  - **Total**: $O(n \log n)$, so $A \in \operatorname{TIME}(n \log n)$.
- **Significance**: This is optimal for single-tape Turing machines, as any language decidable in $o(n \log n)$ is regular (Problem 7.49).

#### Two-Tape Turing Machine: $M_3$
- **Algorithm**: $M_3$ copies 0s to a second tape, then matches them against 1s, rejecting if counts mismatch.
- **Time Analysis**: Each of four stages is $O(n)$, totaling $O(n)$.
- **Implication**: Linear time is achievable with additional tapes, showing model-dependent complexity.

### Complexity Relationships Among Models
The choice of computational model (single-tape, multi-tape, or nondeterministic Turing machine) affects time complexity. **Polynomial equivalence** among deterministic models ensures robustness in complexity classifications, while nondeterministic models introduce exponential gaps, critical for understanding classes like **P** and **NP**.

#### Multi-Tape vs. Single-Tape Turing Machines
- **Theorem 7.8**: A $t(n)$-time multi-tape Turing machine can be simulated by a single-tape Turing machine in $O(t^2(n))$ time.
- **Proof Idea**: The single-tape machine encodes multiple tapes on one tape, with each step of the multi-tape machine requiring $O(t(n))$ steps to scan and update, leading to a quadratic slowdown.
- **Example**: $M_3$'s $O(n)$ on two tapes becomes $O(n^2)$ on a single tape.

#### Nondeterministic vs. Deterministic Turing Machines
- **Definition 7.9**: Nondeterministic running time is the maximum steps on any computation branch.
- **Theorem 7.11**: A $t(n)$-time nondeterministic single-tape Turing machine can be simulated deterministically in $2^{O(t(n))}$ time.
- **Proof**: Simulates all branches via breadth-first search, with up to $b^{t(n)}$ nodes, each taking $O(t(n))$ to process, yielding exponential time.
- **Implication**: Nondeterministic efficiency may vastly outstrip deterministic, motivating the study of **NP**.

## 1.2 The Class P: Polynomial Time Problems

The class **P** encompasses languages decidable in **polynomial time** on a deterministic single-tape Turing machine, representing problems considered practically solvable. This section defines **P**, discusses its robustness across models, and provides examples like **PATH**, **RELPRIME**, and context-free language recognition to illustrate polynomial-time algorithms.

### Definition and Significance of P
- **Definition 7.12**: $\mathrm{P} = \bigcup_k \operatorname{TIME}(n^k)$, the set of languages decidable in $O(n^k)$ time for some constant $k$.
- **Robustness**: **P** is invariant across polynomially equivalent models (e.g., single-tape vs. multi-tape), as per Theorem 7.8.
- **Practicality**: Polynomial time (e.g., $n^3$) is manageable for reasonable inputs, unlike exponential time (e.g., $2^n$), which is often infeasible.
- **Connection**: **P** serves as a benchmark for efficient computation, contrasting with **NP**’s potentially harder problems.

### Examples of Problems in P
These examples demonstrate how clever algorithm design avoids brute-force exponential approaches, achieving polynomial time through techniques like breadth-first search, the Euclidean algorithm, and dynamic programming.

#### PATH: Directed Graph Path Existence
- **Problem**: $\text{PATH} = \{\langle G, s, t \rangle \mid G \text{ has a directed path from } s \text{ to } t\}$.
- **Algorithm**: Uses breadth-first search to mark nodes reachable from $s$, accepting if $t$ is marked.
- **Time Analysis**:
  - Stages 1, 4: $O(1)$ and $O(m)$, where $m$ is the number of nodes.
  - Stage 3: Runs $O(m)$ times, each scanning edges in $O(m + e)$, where $e$ is the number of edges.
  - **Total**: $O(m^2)$, polynomial in the graph’s size.
- **Theorem 7.14**: $\text{PATH} \in \mathrm{P}$.

#### RELPRIME: Testing Relatively Prime Numbers
- **Problem**: $\text{RELPRIME} = \{\langle x, y \rangle \mid x \text{ and } y \text{ are relatively prime}\}$.
- **Algorithm**: Uses the Euclidean algorithm to compute $\gcd(x, y)$, accepting if $\gcd = 1$.
- **Time Analysis**:
  - Each iteration reduces $x$ or $y$ by at least half, requiring $O(\log x + \log y) = O(n)$ iterations.
  - Each iteration is polynomial, so total time is $O(n)$.
- **Theorem 7.15**: $\text{RELPRIME} \in \mathrm{P}$.

#### Context-Free Language Recognition
- **Problem**: Decide if a string $w$ is in a context-free language $L$.
- **Algorithm**: Uses dynamic programming to build a table of variables generating substrings of $w$.
- **Time Analysis**:
  - Table has $O(n^2)$ entries, filled in $O(n^3)$ steps due to $O(n)$ splits per substring.
  - Each step is constant time (fixed grammar rules).
  - **Total**: $O(n^3)$.
- **Theorem 7.16**: Every context-free language is in **P**.

## 1.3 The Class NP and NP-Completeness

The class **NP** includes problems where solutions can be verified in polynomial time, potentially harder than **P** but central to complexity theory. **NP-complete** problems are the hardest in **NP**, where a polynomial-time solution for one would solve all **NP** problems. This section introduces **NP**, polynomial verifiability, and proves **NP-completeness** for problems like **HAMPATH**, **VERTEX-COVER**, and **SUBSET-SUM**.

### Defining NP and Polynomial Verifiability
- **Definition**: **NP** is the class of languages with polynomial-time verifiable certificates (e.g., a Hamiltonian path for **HAMPATH**).
- **Key Feature**: Verification is fast (polynomial), but finding solutions may be slow (exponential).
- **Examples**:
  - **HAMPATH**: Verify a path visits all nodes exactly once in $O(n)$.
  - **COMPOSITES**: Verify factors $p, q$ by checking $x = p \cdot q$.
- **Relation to P**: $\mathrm{P} \subseteq \mathrm{NP}$, but whether $\mathrm{P} = \mathrm{NP}$ is unknown, a central open question.

### NP-Complete Problems
**NP-complete** problems are in **NP** and as hard as any problem in **NP** via polynomial-time reductions. The Cook-Levin theorem establishes **SAT** as **NP-complete**, serving as a foundation for proving other problems’ **NP-completeness**.

#### Cook-Levin Theorem and SAT
- **Theorem**: **SAT** (satisfiability of Boolean formulas) is **NP-complete**.
- **Proof Idea**: Encode any **NP** problem’s nondeterministic Turing machine computation as a Boolean formula, satisfiable if the machine accepts.
- **Implication**: **SAT** is a universal problem for **NP**, used to prove other **NP-completeness** results.

#### VERTEX-COVER
- **Problem**: $\text{VERTEX-COVER} = \{\langle G, k \rangle \mid G \text{ has a vertex cover of size } k\}$.
- **Proof (Theorem 7.44)**:
  - **In NP**: Verify a set of $k$ nodes covers all edges in $O(m + e)$.
  - **Reduction from 3SAT**: Constructs a graph with variable gadgets (edges for true/false) and clause gadgets (triples requiring at least two nodes), setting $k = m + 2l$.
  - **Time**: Polynomial, as graph construction is $O(m + l)$.
- **Significance**: Links logical satisfiability to graph problems.

#### HAMPATH
- **Problem**: $\text{HAMPATH} = \{\langle G, s, t \rangle \mid G \text{ has a Hamiltonian path from } s \text{ to } t\}$.
- **Proof (Theorem 7.46)**:
  - **In NP**: Verify a path in $O(n)$.
  - **Reduction from 3SAT**: Builds a graph with diamond structures for variables and nodes for clauses, where paths encode satisfying assignments.
  - **Time**: Polynomial, with $O(k + l)$ nodes and edges.
- **Extension (Theorem 7.55)**: **UHAMPATH** (undirected) is **NP-complete** via reduction from **HAMPATH**.

#### SUBSET-SUM
- **Problem**: $\text{SUBSET-SUM} = \{\langle S, t \rangle \mid S \text{ has a subset summing to } t\}$.
- **Proof (Theorem 7.56)**:
  - **In NP**: Verify a subset sum in $O(k)$.
  - **Reduction from 3SAT**: Constructs numbers $y_i, z_i$ for variables and $g_j, h_j$ for clauses, with target $t$ ensuring one number per variable and clause satisfaction.
  - **Time**: $O((k + l)^2)$.
- **Insight**: Numeric constraints mimic logical constraints.

---

## Key Points to Remember
- **Time Complexity → Worst-Case Analysis**: Measure maximum steps for input length $n$, critical for practical feasibility. ★★★★☆
- **Asymptotic Notation → Big-O vs. Small-O**: Big-O provides upper bounds ($O(n^2)$), small-o indicates stricter dominance ($o(n^2)$). ★★★★☆
- **Model Impact → Single vs. Multi-Tape**: Multi-tape Turing machines reduce time (e.g., $O(n)$ for $A$), but single-tape simulation squares it ($O(n^2)$). ★★★☆☆
- **P vs. NP → Polynomial Verifiability**: **P** problems are solvable in polynomial time; **NP** problems are verifiable in polynomial time, with **NP-complete** problems linking their complexity. ★★★★★
- **NP-Completeness → Reductions**: Use **3SAT** reductions to prove **NP-completeness** (e.g., **VERTEX-COVER**, **HAMPATH**), showing interconnected hardness. ★★★★★
- **Common Pitfall → Brute-Force Inefficiency**: Avoid exponential brute-force (e.g., $m^m$ for **PATH**); use techniques like dynamic programming or breadth-first search. ★★★★☆
- **Critical Distinction → Polynomial Equivalence**: Deterministic models are polynomially equivalent, but nondeterministic models may require exponential time deterministically. ★★★★☆
