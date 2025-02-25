## 2.1 Algorithms and Deciders

### Definition of an Algorithm

- An **algorithm** is a Turing machine that **halts on every input**.
- A TM is called a **decider** if it halts on all inputs.

### Decidable Languages

- A language $L$ is **Turing-decidable (recursive)** if there exists a decider TM $M$ such that $L(M) = L$.
- **Example**:
  $L = \{ w \in \{0,1\}^* \mid w \text{ has an even number of 0s} \}$ is decidable.
  $A_{TM}$ (Acceptance Problem) is **not decidable**.

### Language Hierarchy

- **Regular Languages**: Recognized by finite automata.
- **Context-Free Languages (CFLs)**: Defined by context-free grammars (CFGs).
- **Decidable Languages**: Solved by decider TMs.
- **Recognizable Languages**: Accepted by TMs (may not halt on all inputs).
- **Undecidable/Unrecognizable Languages**: No TM exists (e.g., $A_{TM}$).

## 2.2 Example of a Decider: Palindrome Recognition

### Machine $M_p$

- **Input**: A string $w \in \{0,1\}^*$.
- **Language**: $L(M_p) = \{ w \mid w \text{ is a palindrome} \}$.

### Steps of $M_p$

1. **Empty input**: Accept immediately.
2. **Non-empty input**:
   - Replace the first symbol (0 or 1) with a blank ($\sqcup$) and move to the end.
   - Check if the last symbol matches the original first symbol. If not, reject.
   - Replace the last symbol with $\sqcup$.
   - Repeat until all symbols are checked or mismatched.
3. **Acceptance**: If all symbol pairs match, accept; otherwise, reject.

### Key Mechanism

- Symmetry check by erasing matching symbols from both ends.
- Halts on all inputs, confirming $L(M_p)$ is decidable.

## 2.3 Time Complexity and Asymptotic Analysis

- **Time complexity** measures the number of steps a TM takes relative to input size.
- **Asymptotic notation** (e.g., $O, \Theta, \Omega$) classifies runtime efficiency.

## 2.4 Decision Problems

- Problems framed as "yes/no" questions. A decider solves a decision problem if it halts with the correct answer.

## Key Points to Remember

- **Decider**: A TM that halts on all inputs.
- **Turing-decidable language**: A language for which a decider exists.
- **Example decidable languages**:
  - Strings with even 0s.
  - Palindromes over $\{0,1\}$.
- **Undecidable problems**: $A_{TM}$ (no decider exists).
- **Algorithm**: Synonymous with a decider TM.
- **Multi-tape TMs**: Equivalent in power to single-tape TMs but more efficient for specific tasks.
- **Non-deterministic TMs**: Can simulate deterministic TMs with a time overhead.
- **Language hierarchy**: Regular ⊂ CFLs ⊂ Decidable ⊂ Recognizable.
