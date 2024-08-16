## 1. Eliminate ε-productions
- Find `nullable(G)` of grammar G, which is the set of all nullable symbols in G.
- For each rule, generate new rules by eliminating nullable variables from the right-hand side of the production.
- Remove all ε-productions.
## 2. Eliminate Unit Productions
- Identify all unit productions, which are rules of the form `A → B` where both A and B are variables.
- For each unit production `A → B`, replace it by adding all rules of the form `B → u` to the grammar (unless this introduces new unit productions).
- Repeat the process until no unit productions remain.

## 3. Eliminate Useless Symbols
- Compute the set of generating symbols `generating(G)` which can derive terminal strings.
  - Remove all productions that involve non-generating symbols.
- Compute the set of reachable symbols `reachable(G)` from the start variable.
  - Remove all productions that involve non-reachable symbols.

## 4. Convert the Remaining Rules into CNF
- Ensure that every production is in one of the forms: `A → BC` or `A → a`.
- For each production with a terminal on the right-hand side that appears in a body of length ≥ 2, replace the terminal with a new variable, and add a rule defining this variable.
- For bodies of length 3 or more, break them into a cascade of two-variable productions.
