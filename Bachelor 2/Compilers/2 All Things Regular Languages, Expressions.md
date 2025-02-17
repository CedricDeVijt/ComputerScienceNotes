## 2.1 Regular Languages

### Definition and Properties

- A language $L$ is **regular** iff it can be defined recursively using:
  - Base cases: $\emptyset$, $\{\epsilon\}$, or $\{a\}$ for $a \in \Sigma$.
  - Operations: Union ($L_1 \cup L_2$), concatenation ($L_1 \cdot L_2$), Kleene closure ($L_1^\*$).
- **Examples**:
  - All binary words ($\{0,1\}^\*$).
  - Finite languages (e.g., $\{\text{abc}, \text{def}\}$).
  - Non-regular languages: Well-parenthesized strings (require unbounded counting).

### Key Observations

- Regular languages are closed under union, concatenation, Kleene star, intersection, and complement.
- Non-regular languages often involve balancing or counting (e.g., $0^n1^n$).

## 2.2 Regular Expressions (RE)

### Syntax and Semantics

- **Syntax**:
  - Base: $\phi$ (empty), $\epsilon$, $a \in \Sigma$.
  - Operators: $+$ (union), $\cdot$ (concatenation), $\*$ (Kleene star).
- **Semantics**:
  - $L(r_1 + r_2) = L(r_1) \cup L(r_2)$.
  - $L(r_1 \cdot r_2) = L(r_1) \cdot L(r_2)$.
  - $L(r^_) = (L(r))^_$.

### Extended Regular Expressions (ERE)

- Practical extensions (e.g., in Unix tools):
  - `[a-z]` (character ranges), `^` (start of line), `$` (end of line), `?` (optional), `+` (one or more), `{m,n}` (repetition bounds).

## 2.3 Finite Automata

### Types of Automata

- **Deterministic Finite Automaton (DFA)**:
  - Tuple $\langle Q, \Sigma, \delta, q_0, F \rangle$.
  - $\delta: Q \times \Sigma \to Q$, complete transitions.
- **Non-deterministic Finite Automaton (NFA)**:
  - $\delta: Q \times (\Sigma \cup \{\epsilon\}) \to 2^Q$.
  - Allows ε-transitions and multiple next states.
- **ε-NFA**: Includes ε-transitions.

### Acceptance Criteria

- A word $w$ is accepted by an automaton if there exists a run from $q_0$ to an accepting state $q_f \in F$.
- **Configuration**: $(q, w)$ where $q$ is the current state and $w$ is the remaining input.

## 2.4 Equivalence Between Automata and Regular Expressions

### Kleene’s Theorem

- Every regular language is accepted by a DFA/NFA/ε-NFA, and vice versa.
- **Conversion Methods**:
  - **RE → ε-NFA**: Thompson’s construction (recursive, preserves structure).
  - **ε-NFA → DFA**: Subset construction (track possible states via $\epsilon$-closure).
  - **DFA → RE**: State elimination (replace transitions with RE labels).

### Determinization (Subset Construction)

- Given an ε-NFA $A$, build a DFA $D$ where:
  - States of $D$ are subsets of $A$’s states.
  - $\delta_D(S, a) = \epsilon\text{-closure}(\delta_A(S, a))$.
  - **Example**: Exponential blowup possible (e.g., $L_n$ requiring $2^{n+1}$ states).

## 2.5 Minimization of DFAs

### Myhill-Nerode Theorem

- A language $L$ is regular iff it has finitely many equivalence classes under the relation $\equiv$, where $x \equiv y$ iff $\forall z, xz \in L \Leftrightarrow yz \in L$.
- **Minimal DFA**: Unique and has the fewest states among all DFAs for $L$.

### Partition Refinement Algorithm

- **Steps**:
  1. Initialize partitions: Separate accepting/non-accepting states.
  2. Refine partitions until no further splits occur.
  3. Merge equivalent states.
- **Key Insight**: Two states are equivalent if their transitions for all symbols lead to the same partition.

## 2.6 Operations on Regular Languages

### Union, Intersection, Complement

- **Union**: Combine automata using ε-transitions from a new initial state.
- **Intersection**: Product automaton $A_1 \times A_2$ tracks states of both automata.
- **Complement**: Swap accepting/non-accepting states in a **DFA**.

### Decision Problems

- **Emptiness**: Check reachability of an accepting state (BFS/DFS).
- **Inclusion**: $L(A_1) \subseteq L(A_2)$ iff $L(A_1) \cap \overline{L(A_2)} = \emptyset$.
- **Equality**: Check mutual inclusion.

## 2.7 Extended Regular Expressions (ERE) in Practice

### Common Constructs

- Character classes: `[a-zA-Z]`, `[^0-9]`.
- Anchors: `^` (start), `$` (end).
- Quantifiers: `*`, `+`, `?`, `{m,n}`.
- Escaping: `\` to match operators (e.g., `\.` matches a literal dot).

### Applications

- **Lexical Analysis**: Token recognition in compilers (e.g., identifiers, numbers).
- **Text Processing**: Pattern matching in Unix tools (e.g., `grep`, `sed`).

---

## Key Points to Remember

- **Regular Languages**: Defined via finite syntax (RE/automata) and closed under standard operations.
- **Kleene’s Theorem**: REs, DFAs, NFAs, and ε-NFAs describe the same class of languages.
- **Determinization**: Subset construction converts ε-NFA to DFA, potentially with exponential state blowup.
- **Minimization**: Myhill-Nerode theorem ensures a unique minimal DFA; use partition refinement.
- **Non-Regular Languages**: Require unbounded counting (e.g., balanced parentheses).
- **Practical EREs**: Extend theoretical REs with syntax for compact pattern matching.
- **Operations**: Complement requires determinism; intersection uses product automata.
