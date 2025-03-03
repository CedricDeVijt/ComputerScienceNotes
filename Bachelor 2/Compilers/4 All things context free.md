## 4.1 Context-Free Grammars (CFGs)

### Derivation and Ambiguity

- **Derivations**: A CFG generates strings by replacing variables with production rules.
  - **Leftmost/Rightmost Derivations**: Always expand the leftmost/rightmost variable first.
  - **Derivation Trees**: Hierarchical structures showing rule applications. Multiple trees for the same word indicate ambiguity.
- **Ambiguity**: A grammar is ambiguous if a word has ≥2 derivation trees. Example: `Id + Id * Id` in arithmetic grammars.

### Chomsky Normal Form (CNF)

- **Rules**: All productions are of the form:
  - $A \rightarrow BC$ (two variables)
  - $A \rightarrow a$ (terminal)
  - $S \rightarrow \varepsilon$ (if empty string is in the language).
- **Conversion**: Eliminate ε-rules, unit productions, and introduce variables for terminals/long rules.

### Membership Problem and CYK Algorithm

- **CYK Algorithm**: Dynamic programming approach to check if $w \in L(G)$:
  1. Build a table where $Tab[i][j]$ contains variables generating substring $w_i...w_j$.
  2. Fill for substrings of increasing length, using CNF rules.
- **Complexity**: $O(n^3)$ time, $O(n^2)$ space for input length $n$.

## 4.2 Pushdown Automata (PDAs)

### Definition and Semantics

- **Components**:
  - States $Q$, input alphabet $\Sigma$, stack alphabet $\Gamma$, transition function $\delta$.
  - Transitions: $\delta(q, a, \gamma) \rightarrow (q', \gamma')$ (read $a$, pop $\gamma$, push $\gamma'$).
- **Acceptance Modes**:
  - **By Final State**: Reach an accepting state after reading the input.
  - **By Empty Stack**: Empty the stack after processing.

### Equivalence to CFGs

- **CFG → PDA**: Simulate derivations using a stack. For each rule $A \rightarrow \alpha$, push $\alpha$ when $A$ is on the stack.
- **PDA → CFG**: Construct variables $[p\gamma q]$ representing paths from state $p$ to $q$ with stack symbol $\gamma$.

### Deterministic PDAs (DPDAs)

- **Limitations**: Cannot recognize all CFLs (e.g., $L\_{pal} = \{ww^R \mid w \in \{0,1\}^*\}$ requires non-determinism).
- **DCFL**: Languages recognized by DPDAs. Strict subset of CFLs.

## 4.3 Closure Properties and Deterministic CFLs

### Closure Properties

- **Closed Under**: Union, concatenation, Kleene star.
- **Not Closed Under**: Intersection, complement. Example: $L\_{abc} = \{a^n b^n c^n\}$ is not a CFL, but $L_1 = \{a^n b^n c^k\}$ and $L_2 = \{a^k b^n c^n\}$ are CFLs.

### Deterministic Context-Free Languages (DCFLs)

- **Definition**: Recognized by DPDAs.
- **Example**: $L = \{(ab)^n c (de)^n\}$ is a DCFL.

## 4.4 Grammar Transformations

### Removing Useless Symbols

1. **Unproductive Symbols**: Variables that cannot derive terminal strings.
2. **Unreachable Symbols**: Symbols not reachable from the start variable.
3. **Procedure**: Remove unproductive symbols first, then unreachable ones.

### Left Recursion and Factoring

- **Left Recursion Removal**:
  - Replace $A \rightarrow A\alpha \mid \beta$ with:
    - $A \rightarrow \beta A'$
    - $A' \rightarrow \alpha A' \mid \varepsilon$.
- **Factoring**: Eliminate common prefixes in rules. Example:
  - Original: $V \rightarrow a\beta_1 \mid a\beta_2$
  - Transformed: $V \rightarrow aV'$, $V' \rightarrow \beta_1 \mid \beta_2$.

### Operator Precedence and Associativity

- **Priority**: Define grammar hierarchy (e.g., atoms → products → expressions).
- **Associativity**: Use left recursion for left associativity (e.g., $Exp \rightarrow Exp + Prod$).

---

## Key Points to Remember

- **CFGs** model nested structures (e.g., arithmetic expressions). Ambiguity arises from multiple derivations.
- **CNF** simplifies parsing; CYK uses CNF for membership checks.
- **PDAs** extend finite automata with a stack. Equivalence to CFGs bridges automata and grammars.
- **DCFLs** ⊂ CFLs; not all CFLs are deterministic.
- **Closure**: CFLs closed under union/concatenation/Kleene star but not intersection/complement.
- **Grammar Transformations**:
  - Remove ambiguity via precedence/associativity rules.
  - Eliminate left recursion and factor common prefixes.
  - Remove useless symbols to simplify grammars.
