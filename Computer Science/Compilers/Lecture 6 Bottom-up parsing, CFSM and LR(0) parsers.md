### Required and Target Competences
- **Tools Needed**: Formal language theory encompassing languages and machines, machines and computability.
- **Skills Acquired**: Understanding canonical finite automaton theory and implementing LR parsers.
- **Usefulness**: Facilitates comprehension of older or alternative parser generator implementations.
### Key Terms and Definitions
- *Canonical finite automaton (CFA)*: also known as the minimal DFA, is a type of finite automaton that recognises a regular language and has a unique minimal representation.
## Differences with Top-down Parsing
### Top-down Parsing
- **Actions**: Produce and Match
- **Operation**: Derivation tree unfolds top to bottom, left to right.
### Bottom-up Parsing
- **Actions**: Shift and Reduce
- **Operation**: Derivation tree unfolds bottom to top, right to left.
## From CFG to Bottom-up Parser
### The PDA
- **Shift**: Reads terminals and pushes into stack.
- **Reduce**: Populates stack with handle, transitioning without reading input.
- **Challenge**: Non-deterministic handle selection leads to conflicts.
## Why Non-determinism?
**Reduce-Reduce Conflicts**: Arise when stack top corresponds to handles of different rules.
**Shift-Reduce Conflicts**: Occur when stack top allows both shifting and reducing.
**Consideration**: Ensuring a shift won't inhibit subsequent reductions is crucial.
## Prefixes on the Stack
### Viable Prefixes on the Stack
#### Definitions
- **Right-sentential form**: Derivable via a right-most derivation.
- **Viable prefix**: Precedes a right-sentential form on the stack during an accepting run.
### Recognizing Viable Prefixes
#### Definition
- **Canonical Finite-State Machine (CFSM)**: A type of finite machine that recognises a regular language and has a unique minimal representation.
## Items and Their Closures
### Definitions
- **Item**: Grammar rule with a marker indicating a position in the RHS.
- **Closure of an Item**: Set of all items derived from the original item.

### Application
- CFSM states are sets of items; closures determine state transitions.

## The CFSM

### CFSM States
- Represented as sets of items; transitions governed by a-successors.

### Definition
- **The CFSM**: DFA mapping subsets of items to closures, facilitating viable prefix recognition.

## CFSM Properties

### Theorem
- The CFSM accurately identifies all viable prefixes.

### Exercise
- Construct the CFSM for a given grammar.

## LR(0) Parsers

### Overview
- **Definition**: Left scanning, Right parsing parsers.
- **Main Intuition**: Simulate bottom-up PDA, resolving conflicts with CFSM.

## CFSM-based Stack and Action Table

### Exercise
- Simulate LR(0) parser for a given input string and grammar.

### Parsing Mechanics
- CFSM guides parsing decisions: Shift, Reduce, or Accept.

### Conflicts Resolution
- Conflicts in CFSM states inform parser actions.

## Action Table for LR(0) Parsers

### Construction
- Indexes grammar rules and CFSM states; maps to corresponding actions.

### Determinism
- Parser is deterministic if each cell in the table has a single entry.

## Action Table with a Stack of States

### Algorithm
- Outline for parsing using CFSM-based stack and action table.
- Steps involve state transitions and stack operations.