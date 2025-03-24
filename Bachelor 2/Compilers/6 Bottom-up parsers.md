## 6.1 Principles of Bottom-Up Parsing

- **Definition**: Bottom-up parsers construct parse trees starting from leaves (input tokens) and moving upward to the root (start symbol). They reverse the derivation process using **shift-reduce** actions.
- **Key Actions**:
  - **Shift**: Move a terminal from the input to the stack.
  - **Reduce**: Replace a handle (sequence matching a production rule’s RHS) on the stack with the corresponding non-terminal.
- **Goal**: End with only the start symbol on the stack and empty input.
- **Rightmost Derivation**: Bottom-up parsers build a rightmost derivation in reverse.

## 6.2 Shift-Reduce Parsers and Conflicts

- **Shift-Reduce Workflow**:
  - **Shift** terminals to the stack until a handle is identified.
  - **Reduce** the handle to a non-terminal using grammar rules.
- **Conflicts**:
  - **Reduce-Reduce**: Multiple rules can reduce the same handle.
  - **Shift-Reduce**: Ambiguity between shifting a terminal or reducing a handle.
- **Example**: Parsing `id + id * id` requires resolving conflicts by prioritizing reductions for operator precedence.

## 6.3 Canonical Finite State Machine (CFSM)

- **Purpose**: Recognizes **viable prefixes** (stack contents that can lead to successful parsing).
- **Construction**:
  - **Items**: Grammar rules with a dot (·) indicating parsing progress (e.g., `A → α·β`).
  - **Closure Operation**: Adds items for all productions of non-terminals following the dot.
  - **Successor Function**: Moves the dot past a symbol to form new states.
- **Example**: For the grammar `S → A$ | aCD | ab`, the CFSM tracks progress through rules and resolves conflicts via state transitions.

![[Bachelor 2/Compilers/Pasted image 20250324170916.png]]

## 6.4 LR(0) Parsers

- **Features**:
  - No look-ahead; decisions based solely on the current state.
  - **Action Table**: Maps states to shift/reduce/accept actions.
- **Limitations**:
  - Fails on grammars with conflicts (e.g., overlapping handles).
- **Example**: The grammar `S → ε | SaSb` is LR(0) because reductions are unambiguous.

## 6.5 SLR(1) Parsers

- **Improvement over LR(0)**:
  - Uses **Follow sets** to resolve conflicts with 1-symbol look-ahead.
  - Reduces ambiguity by checking if the next symbol is in the Follow set of the non-terminal.
- **Example**: In `Exp → Exp + Prod | Prod`, Follow(Prod) = {+, \*, $} ensures reductions occur only when valid.

## 6.6 LR(k) Parsers

- **Generalization**:
  - Uses **k symbols of look-ahead** to resolve conflicts.
  - **LR(1) Items**: Augmented with look-ahead tokens (e.g., `A → α·β, a`).
- **Construction**:
  - **Closure with Look-Ahead**: Computes expected terminals after reducing a rule.
  - **Action Table**: Combines shift/reduce actions based on look-ahead.
- **Example**: The grammar `S → L=R | R` requires LR(1) to distinguish between `=` and `$` in look-ahead.

## 6.7 LALR(k) Parsers

- **Optimization**:
  - Merges LR(k) states with identical **hearts** (LR(0) items) but different look-aheads.
  - Reduces table size while retaining most LR(k) power.
- **Trade-off**: May introduce conflicts not present in LR(k).
- **Example**: Merging states in `S → aAd | aBe` reduces the parser’s size but risks unresolved ambiguities.

## 6.8 Hierarchy of Grammars and Languages

- **Grammar Classes**:
  - **LR(0) ⊂ SLR(1) ⊂ LALR(1) ⊂ LR(1) ⊂ ...**: Increasing look-ahead improves coverage.
  - **LL(k) ⊂ LR(k)**: Bottom-up parsers handle more grammars than top-down.
- **Language Classes**:
  - **DCFL (Deterministic CFL)**: All LR(k) languages fall into this category.
  - **Practical Relevance**: Most programming languages are LALR(1).

## 6.9 Practical Considerations

- **Parser Generators**: Tools like Yacc/Bison generate LALR(1) parsers due to efficiency.
- **End-of-File Marker ($)**: Simplifies parsing by ensuring unambiguous termination.

---

## Key Points to Remember

- **Shift-Reduce Actions**: Core mechanism for bottom-up parsing.
- **Viable Prefixes**: Valid stack contents tracked by the CFSM.
- **Conflicts**:
  - **Reduce-Reduce**: Multiple valid reductions.
  - **Shift-Reduce**: Ambiguity between shifting and reducing.
- **LR Hierarchy**: LR(0) < SLR(1) < LALR(1) < LR(1).
- **Look-Ahead**: Critical for resolving conflicts (SLR uses Follow sets; LR(k) uses k symbols).
- **DCFL**: All LR(k) languages are deterministic context-free.
- **Practical Use**: LALR(1) balances power and efficiency, making it standard in tools.
