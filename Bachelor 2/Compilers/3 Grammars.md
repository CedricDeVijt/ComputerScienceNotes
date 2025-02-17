## 3.1 Limitations of Regular Languages

### Intuition on Unbounded Memory

- Regular languages cannot recognize languages requiring unbounded memory (e.g., balanced parentheses).
- **Example**: The language $L_0$ (well-parenthesized expressions) needs an unbounded counter to track open/close parentheses, which finite automata lack.

### Proof of Non-Regularity for $L_0$

- **Theorem 3.1**: $L_0$ is not regular.
- **Proof Strategy**:
  1. Assume $L_0$ is regular; let $A_0$ be an ε-NFA with $n$ states recognizing $L_0$.
  2. Consider the word $w = (^n )^n$. An accepting run of $w$ must revisit a state due to the pigeonhole principle.
  3. Repeating the loop in the run generates invalid words (e.g., $(^{n+k} )^n$), contradicting $L_0$'s definition.

## 3.2 Grammars: Syntax and Semantics

### Definition of Grammars

A grammar $G = \langle V, T, P, S \rangle$ consists of:

- **Variables (V)**: Non-terminal symbols (e.g., `Exp`).
- **Terminals (T)**: Alphabet symbols (e.g., `(`, `)`, `Id`).
- **Production Rules (P)**: Rewrite rules of the form $\alpha \rightarrow \beta$, where $\alpha$ contains at least one variable.
- **Start Symbol (S)**: Initial variable.

### Derivations and Sentential Forms

- **Derivation**: $\alpha \Rightarrow \beta$ if $\alpha = \gamma \theta \delta$, $\beta = \gamma \psi \delta$, and $\theta \rightarrow \psi \in P$.
- **Sentential Form**: Any string derivable from $S$.
- **Language of Grammar**: $L(G) = \{ w \in T \mid S \Rightarrow w \}$.

### Example Grammars

- **Expression Grammar**:
  Exp → Exp + Exp | Exp \* Exp | (Exp) | Id | Cst
- **Context-Sensitive Grammar** (equal numbers of a, b, c):
  S → ABCS' | ε, ABC → BAC | BCA | ... (permutation rules), A → a, B → b, C → c

## 3.3 The Chomsky Hierarchy

### Hierarchy Classes

1. **Class 0 (Unrestricted Grammars)**: All grammars. Recognize recursively enumerable (RE) languages.
2. **Class 1 (Context-Sensitive Grammars)**:
   - Rules: $\alpha \rightarrow \beta$ with $|\alpha| \leq |\beta|$.
   - Recognize context-sensitive languages (CSL).
3. **Class 2 (Context-Free Grammars)**:
   - Rules: $A \rightarrow \beta$ (single variable on left).
   - Recognize context-free languages (CFL).
4. **Class 3 (Regular Grammars)**:
   - Rules: $A \rightarrow wB$ or $A \rightarrow w$ (right/left-linear).
   - Recognize regular languages (Reg).

### Relationships Between Classes

- **Theorem 3.2**:
  $\text{Reg} \subsetneq \text{CFL} \subsetneq \text{CSL} \subsetneq \text{RE}$
- **Examples**:
  - $L_0$ (balanced parentheses) is CFL but not Reg.
  - $\{ a^n b^n c^n \mid n \geq 1 \}$ is CSL but not CFL.

## 3.4 Key Concepts and Proof Techniques

### Pumping Lemma Applications

- Used to prove non-regularity (e.g., $L_0$) and non-context-freeness.

### Transformations Between Grammar Types

- **Removing ε-Rules**: For converting CFG to context-sensitive form.
- **Handling Start Symbol**: Ensuring $S$ does not appear in right-hand sides.

---

## Key Points to Remember

- **Regular Languages**: Limited to finite memory; cannot handle balanced parentheses.
- **Context-Free Grammars**: Use single-variable rules; define languages like arithmetic expressions.
- **Chomsky Hierarchy**:
  $\text{Reg} \subset \text{CFL} \subset \text{CSL} \subset \text{RE}$.
- **Proof Techniques**: Pumping lemma for regularity/context-freeness; state repetition in automata.
- **Grammar Transformations**: Removing ε-rules, ensuring context-sensitive constraints.
- **Critical Languages**:
  - $L_0$: CFL, not Reg.
  - $\{ a^n b^n c^n \}$: CSL, not CFL.
  - $\{ a^{2^n} \}$: RE, not CSL.
