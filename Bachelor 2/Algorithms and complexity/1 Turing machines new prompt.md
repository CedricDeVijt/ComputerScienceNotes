## 1.1 Fundamentals of Turing Machines
### Core Components
A **Turing Machine (TM)** consists of:  
- Finite control unit with states (`Q`)  
- Infinite tape with read/write head  
- Alphabet symbols (`Σ` for input, `Γ` for tape)  
- Transition function `δ` governing state/symbol changes  
- Accept/reject halting states  

**Key Mechanism**: The tape extends infinitely rightward, starting with input `w ∈ Σ*` followed by blanks (`⊔`). The head begins at position 1.

### Formal Definition
A deterministic TM is a 7-tuple:  
$$(Q, Σ, Γ, δ, q_0, q_{accept}, q_{reject})$$  
Where:  
- `δ: Q × Γ → Q × Γ × {←, □, →}` dictates state transitions  
- Special symbols: `⊢` marks tape position 0; `⊔` represents blank  

#### Example: Even Zero Counter
TM states alternate between `q₀` (even zeros) and `q₁` (odd zeros). Transitions overwrite symbols with `⊔` and move right. Accepts if `⊔` is read in `q₀`.

## 1.2 Computation and Acceptance
### Configurations
A **configuration** represents machine state as:  
$$⊢uqv$$  
Where:  
- `u`: Left tape content  
- `q`: Current state  
- `v`: Right tape content with head at first symbol  

### Acceptance Criteria
A TM **accepts** input `w` if any sequence of configurations leads to `q_{accept}`. The language recognized is:  
$$L(M) = \{w ∈ Σ^* | M \text{ accepts } w\}$$  

#### Example: Palindrome Checker
1. Compare first/last symbols via multitape copying  
2. Time complexity: `O(n²)` for single-tape vs. `O(n)` for 2-tape TM  

**Key Proof Concept**: 1-tape TMs require Ω(n²) steps for palindromes due to crossing sequences (back-and-forth head movements).

## 1.3 Time Complexity Analysis
### Measuring Complexity
- **Time_M(w)**: Steps taken by TM `M` on input `w`  
- **Worst-case complexity**:  
  $$t_M(n) = \max\{time_M(w) | |w| = n\}$$  

### Asymptotic Notation
- **Big-O**: Upper bound growth rate  
- **Big-Ω**: Lower bound growth rate  

#### Example: Palindrome TM Analysis
Single-tape palindrome checker has `O(n²)` complexity due to nested loops comparing symbols.

## 1.4 Multitape Turing Machines
### Definition and Operation
A **k-tape TM** uses:  
- `k` independent tapes with separate heads  
- Extended transition function:  
  $$δ: Q × Γ^k → Q × Γ^k × {←, □, →}^k$$  

### Simulation by Single-Tape TM
**Theorem**: Any k-tape TM running in `O(t(n))` time can be simulated by a 1-tape TM in `O(t(n)²)` time.  

#### Simulation Strategy:
1. Encode k tapes with virtual heads using marker symbols  
2. Track head positions via modified alphabet `Γ' = Γ ∪ {#} ∪ {̃a | a ∈ Γ}`  
3. Simulate each k-tape step via two passes (read heads → update tapes)

**Critical Trade-off**: Multitape TMs offer speed gains (e.g., linear-time palindrome check) but require quadratic overhead when simulated.

## 1.5 Non-Deterministic Turing Machines (NTM)
### Definition
An NTM uses a **transition relation** instead of function:  
$$δ ⊆ Q × Γ × Q × Γ × {←, □, →}$$  
**Acceptance**: At least one computation path reaches `q_{accept}`.

### Time Complexity
- **NTM time**: Maximum steps across all paths  
- **Deterministic Simulation**: Requires `2^{O(t(n))}` time via breadth-first search of computation tree  

#### Example: Satisfiability (SAT)
NTMs "guess" variable assignments, but deterministic simulation faces exponential blowup.

---

## Key Points to Remember
- **Church-Turing Thesis**: All computable functions = TM-computable (CHURCH mnemonic) ★★★★★  
- **Tape Trade-offs**: Multitape → speed; Single-tape → space efficiency ↗ See Section 4.2  
- **PAL-O(n²)**: 1-tape palindromes require quadratic time due to crossing sequences ★★★★☆  
- **Non-Det Blowup**: NTM→DTM conversion has exponential overhead ★★★☆☆  
- **Config Notation**: ⊢uqv encodes state + tape position ★★★★☆  
- **Big-O Hierarchy**: `O(1) < O(n) < O(n²) < O(2^n)` ★★★★★  

**Mnemonic**: "TMs PAL Around Quadratic Time" → highlights palindrome complexity constraint.