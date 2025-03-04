## 1.1 Foundations of Turing Machines

### Core Components

- **Structure**: Defined by a 7-tuple $(Q, \Sigma, \Gamma, \delta, q_0, q_{\text{accept}}, q_{\text{reject}})$:
  - $Q$: Finite set of states.
  - $\Sigma$: Input alphabet (excluding $\vdash$ and $\sqcup$).
  - $\Gamma$: Tape alphabet (includes $\Sigma \cup \{\vdash, \sqcup\}$).
  - $\delta$: Transition function (deterministic) or relation (non-deterministic).
  - $q_0, q_{\text{accept}}, q_{\text{reject}}$: Initial, accept, and reject states.
- **Tape**: Infinite, with symbols $\vdash$ (left end-marker) and $\sqcup$ (blank).
- **Head**: Reads/writes symbols and moves left ($\leftarrow$), right ($\rightarrow$), or stays ($\square$).

### Church-Turing Thesis

- **Key Assertion**: Any algorithm can be implemented by a Turing Machine (TM).
- **Implications**:
  - TMs formalize the intuitive notion of computation.
  - All computational models (e.g., lambda calculus, cellular automata) are equivalent to TMs.

## 1.2 Deterministic Turing Machines (DTMs)

### Configurations

- Represented as $C = \vdash u q v$, where:
  - $u, v$: Tape content left/right of the head.
  - $q$: Current state.
- **Start Configuration**: $\vdash q_0 w$ for input $w$.
- **Accept/Reject States**: Halt computation immediately.

### Transition Function

- $\delta(q, a) = (q', b, X)$:
  - In state $q$, read $a$, write $b$, move $X$, transition to $q'$.
- **Example**: Checking even number of 0s:
  - States alternate between $q_0$ (even) and $q_1$ (odd).
  - Transitions overwrite symbols with $\sqcup$ and count parity.

## 1.3 Language Acceptance and Decidability

### Definitions

- **Turing-Recognizable (Recursively Enumerable)**: A language $L$ is accepted by a TM that halts on inputs in $L$ (may loop otherwise).
- **Turing-Decidable (Recursive)**: A language $L$ is decided by a TM that halts on all inputs.
- **Example**: $A\_{\text{TM}} = \{(M, w) \mid M \text{ accepts } w\}$ is recognizable but undecidable.

### Deciders vs. Recognizers

- **Decider**: Halts on all inputs (algorithm).
- **Recognizer**: May loop on inputs not in the language.

## 1.4 Time Complexity and Asymptotic Analysis

### Key Concepts

- **Worst-Case Time**: $t_M(n) = \max\{\text{steps}(M) \text{ on inputs of length } n\}$.
- **Big-O Notation**: $f(n) = O(g(n))$ if $f$ grows at most as fast as $g$ asymptotically.
- **Example**: Palindrome checking on a 1-tape DTM has $O(n^2)$ time.

### Multi-Tape TM Simulation

- **Theorem**: A $k$-tape TM running in $O(t(n))$ time can be simulated by a 1-tape TM in $O(t(n)^2)$ time.
- **Proof Sketch**: Use a single tape with virtual tracks for each tape and marked head positions.

## 1.5 Non-Deterministic Turing Machines (NTMs)

### Definition

- **Transition Relation**: $\delta \subseteq Q \times \Gamma \times Q \times \Gamma \times \{\leftarrow, \square, \rightarrow\}$.
- **Computation Tree**: All possible runs branch non-deterministically.
- **Acceptance**: At least one path in the tree leads to $q\_{\text{accept}}$.

### Equivalence to DTMs

- **Theorem**: An NTM running in $O(t(n))$ time can be simulated by a DTM in $2^{O(t(n))}$ time.
- **Proof Sketch**: Use breadth-first search (BFS) over computation paths.

## 1.6 Key Decision Problems and Examples

### Palindrome Recognition

- **DTM Approach**: Compare symbols from both ends, overwriting matched symbols (time $O(n^2)$.
- **2-Tape DTM Optimization**: Copy input to second tape, compare in $O(n)$ time.

### SAT Problem

- **Definition**: Determine if a Boolean formula has a satisfying assignment.
- **Complexity**: NP-complete (efficiently solvable by NTMs, no known efficient DTM solution).

---

## Key Points to Remember

- **TM Components**: Infinite tape, finite control, read/write head, and halting states.
- **Church-Turing Thesis**: All computational models are equivalent to TMs.
- **Decidability**: A language is decidable if a TM halts on all inputs for it.
- **Time Complexity**:
  - Multi-tape TMs can be simulated with quadratic overhead.
  - Non-determinism introduces exponential time overhead in simulations.
- **Critical Problems**:
  - $A\_{\text{TM}}$ is recognizable but undecidable.
  - Palindromes are decidable in $O(n^2)$ time on 1-tape DTMs.
  - SAT is in NP, with no known polynomial-time DTM algorithm.
