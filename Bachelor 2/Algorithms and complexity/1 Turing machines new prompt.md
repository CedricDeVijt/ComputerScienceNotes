## 1.1 Foundations of Turing Machines

### Why Turing Machines?

**Turing Machines (TMs)** formalize computation by modeling:

- Finite control (states)
- Infinite tape with read/write head
- Acceptance/rejection states
  **Key principle**: Church-Turing Thesis ("Algorithm = TM implementation").

#### Core Components

Components of a deterministic TM $(Q, \Sigma, \Gamma, \delta, q_0, q_{accept}, q_{reject})$:

- $Q$: Finite states
- $\Gamma$: Tape alphabet (includes $\vdash$, $\sqcup$)
- $\delta$: Transition function $Q \times \Gamma \to Q \times \Gamma \times \{\leftarrow, \square, \rightarrow\}$

#### Limitations of Simpler Models

Pushdown automata and finite automata are **too restrictive** for general computation:

- Stack-based memory (PDA) ≠ arbitrary tape access
- Can't model recursive languages (e.g., $\{0^n1^n0^n\}$)

## 1.2 Computation and Configurations

### Tape Initialization Rules

- Input $w \in \Sigma^*$ starts at tape position 1
- All positions $>|w|$ contain $\sqcup$ (blank)
- Head starts at position 1

### Configurations

A configuration $C = \vdash u q v$ represents:

- Current state $q$
- Tape content $uv$ (with head on first symbol of $v$)
  **Example**: $\vdash 101q_3001$ indicates head at position 4.

#### Transition Rules

For $\delta(q, a) = (q', b, X)$:

- **Write** $b$, **move** $X$, **transition** to $q'$
- Special handling for $\vdash$: Can't overwrite or move left

## 1.3 Language Recognition vs. Decision

### Turing-Recognizable Languages

A language $L$ is **recognizable** if some TM halts on all $w \in L$.

- Example: $A_{TM} = \{(M,w) \mid M \text{ accepts } w\}$
- **Critical gap**: Recognizable ≠ Decidable (e.g., $\overline{A_{TM}}$ isn't recognizable)

### Deciders and Algorithms

A **decider** is a TM that halts on all inputs.

- Example: TM for $\{w \mid w \text{ has even 0s}\}$ is a decider
- Non-decider example: TMs for $A_{TM}$ may loop

## 1.4 Time Complexity Analysis

### Measuring Complexity

- **Time$_M(w)$**: Steps taken by TM $M$ on input $w$
- **Worst-case complexity**: $t_M(n) = \max\{\text{Time}_M(w) \mid |w|=n\}$

#### Asymptotic Notation

- $f(n) = \mathcal{O}(g(n))$: Upper bound
- $f(n) = \Omega(g(n))$: Lower bound
  **Example**: Palindrome-checking TM runs in $\mathcal{O}(n^2)$.

### Crossing Sequences & Lower Bounds

For 1-tape TMs recognizing palindromes:

- Requires $\Omega(n^2)$ time due to **back-and-forth head movements**
- Proof uses counting of state transitions across tape positions

## 1.5 Multi-Tape and Non-Deterministic TMs

### Multi-Tape TMs

**Definition**: $k$-tape TM with transition function $\delta: Q \times \Gamma^k \to Q \times \Gamma^k \times \{\leftarrow, \square, \rightarrow\}^k$

- **Simulation**: 1-tape TM can simulate $k$-tape TM with $\mathcal{O}(t(n)^2)$ overhead

### Non-Deterministic TMs (NTM)

**Definition**: Transition **relation** allows branching computations.

- Accepts $w$ if **any** computation path accepts
- **Simulation cost**: Deterministic TM requires $2^{\mathcal{O}(t(n))}$ time

---

## Key Points to Remember

- **Church-Turing Thesis → Universality**: All computational models reduce to TMs ★★★★★
- **Decidable vs. Recognizable**: Deciders always halt; recognizers may loop on rejects ★★★★☆
- **Time Complexity Tradeoffs**:
  - Multi-tape → Single-tape: Quadratic overhead ★★★☆☆
  - Non-deterministic → Deterministic: Exponential overhead ★★★★☆
- **Palindrome Lower Bound**: 1-tape TMs require $\Omega(n^2)$ time (TRAP mnemonic: **T**ape **R**estrictions **A**ffect **P**erformance) ★★★★☆
- **Configuration Encoding**: $\vdash u q v$ format captures state, tape, and head position ★★★☆☆
- **Asymptotic Analysis**: Use Big-O/Ω for scalability, not exact step counts ★★★★☆
