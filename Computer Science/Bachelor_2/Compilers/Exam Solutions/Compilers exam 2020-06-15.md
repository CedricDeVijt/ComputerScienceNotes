### 4. (20 points) Consider the following grammar G and the language L it defines.

| (1) | S   | abc |
| ---: | :---: | :--- |
| (2) |     | ac  |
| (3) |     | ba  |
| (4) |     | bc  |
Which of the following are true? (Several may be true!)
- [ ] G is LL(1)
- [x] G is strongly LL(2)
- [x] G is LL(2)
- [x] L is LL(3)

Strong Determinism: The grammar must be strongly deterministic with respect to two symbols of lookahead. This means that the decision of which production to apply must be uniquely determined by the current non-terminal and the next two input symbols.
### LL(1) Analysis
A grammar is LL(1) if, given the first symbol (lookahead) of the input string, we can uniquely determine the production to use.
**First sets**:
- $\text{First}(abc) = \{a\}$
- $\text{First}(ac) = \{a\}$
- $\text{First}(ba) = \{b\}$
- $\text{First}(bc) = \{b\}$
**Follow sets**:
Since $S$ is the start symbol and no further context is provided, the follow set does not help in distinguishing productions uniquely in this simplified case.
### Analysis of LL(1):
- $\text{First}(abc) \cap \text{First}(ac) = \{a\}$
- $\text{First}(ba) \cap \text{First}(bc) = \{b\}$
There are conflicts in choosing between productions based on the first symbol:
- If the lookahead is $a$, we can't distinguish between $S \rightarrow abc$ and $S \rightarrow ac$.
- If the lookahead is $b$, we can't distinguish between $S \rightarrow ba$ and $S \rightarrow bc$.
Thus, the grammar $G$ is **not** LL(1).
### LL(2) Analysis
A grammar is LL(2) if we can distinguish productions using two symbols of lookahead.
**Lookahead pairs**:
- For $S \rightarrow abc$: Lookahead pairs are $(a, b)$
- For $S \rightarrow ac$: Lookahead pairs are $(a, c)$
- For $S \rightarrow ba$: Lookahead pairs are $(b, a)$
- For $S \rightarrow bc$: Lookahead pairs are $(b, c)$
### Analysis of LL(2):
- For $a$ followed by $b$ (from $abc$), we can distinguish it from $a$ followed by $c$ (from $ac$).
- For $b$ followed by $a$ (from $ba$), we can distinguish it from $b$ followed by $c$ (from $bc$).
Thus, using two symbols of lookahead, we can uniquely determine which production to use. Therefore, the grammar $G$ is **LL(2)**.
### Strongly LL(2) Analysis
A grammar is strongly LL(2) if it can be parsed using two symbols of lookahead in a way that doesn't rely on the parse stack or context from previous derivations. This analysis often overlaps with LL(2) but requires a more rigorous formalism. However, from our previous analysis:
- The given grammar differentiates productions with two symbols of lookahead without context issues or dependencies.
Thus, the grammar $G$ is **strongly LL(2)**.
### LL(3) Analysis
If a grammar is LL(2), it can naturally be parsed with three symbols of lookahead (i.e., it will also be LL(3)). Since $G$ is LL(2):
Thus, the grammar $G$ is **LL(3)**.
### 6. (20 points) The closure of {S → ∘aA, S → a ∘ B} includes:

S → ∘aA
S → a ∘ B
A → ∘Aa
B → ∘b
The closure of a set of string rewriting rules is the smallest superset of that set that is closed under three operations: concatenation, substitution, and epsilon-removal.
1. Concatenation: If A → α and B → β are in the closure, then A → αβ is also in the closure.
2. Substitution: If A → αBγ and B → β are in the closure, then A → αβγ is also in the closure.
3. Epsilon-removal: If A → ε and B → β are in the closure, then B → Aβ and B → βA are also in the closure.
Given the initial set {S → ∘aA, S → a ∘ B}, we can derive the following rules using the closure operations:
S → ∘aA (given)
S → a ∘ B (given)
A → ε (using rule 3 in the grammar)
A → Aa (using rule 4 in the grammar)
B → b (using rule 5 in the grammar)
B → a (using rule 6 in the grammar)

By substitution (operation 2), we can derive:
A → ∘Aa (substitute A → Aa into S → ∘aA)
B → ∘b (substitute B → b into S → a ∘ B)

Therefore, the closure of {S → ∘aA, S → a ∘ B} includes the rules S → ∘aA, S → a ∘ B, A → ∘Aa, and B → ∘b.
