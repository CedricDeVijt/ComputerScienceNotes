## 3.1 Fundamentals of Space Complexity
### Measuring Space Complexity
**Space complexity** quantifies the maximum tape cells scanned by a Turing Machine (TM) on inputs of size $n$. For non-deterministic TMs (NTMs), it considers all computation branches.  
- **Deterministic TM**: $s_M(n) = \max\{\text{space}_M(w) \mid |w|=n\}$
- **Non-deterministic TM**: Worst-case across all branches  
**Key Classes**:  
- $\text{DSPACE}(s(n))$: Languages decidable by deterministic TMs in $O(s(n))$ space  
- $\text{NSPACE}(s(n))$: Analogous for NTMs  

#### Example: 3SAT in DSPACE(n)
A TM checks all $2^m$ truth assignments for a 3CNF formula $\varphi$ by reusing space. Each assignment is tested sequentially, requiring only $O(m)$ space for variables.

## 3.2 Core Theorems in Space Complexity
### Savitch's Theorem: PSPACE = NPSPACE
**Theorem**: For $s(n) \geq n$, $\text{NSPACE}(s(n)) \subseteq \text{DSPACE}(s(n)^2)$. Thus, $\text{PSPACE} = \text{NPSPACE}$.  
**Proof Strategy**:  
1. Model computations as a **configuration graph** with $2^{O(s(n))}$ nodes.  
2. Use recursive `REACH` procedure to check $c_{\text{start}} \rightsquigarrow c_{\text{accept}}$ in $O(s(n)^2)$ space.  
**Implications**: Non-determinism doesn't grant extra power in polynomial space.  

### Immerman-Szelepcsényi Theorem: NLOGSPACE = co-NLOGSPACE
**Theorem**: Non-deterministic logarithmic space is closed under complement.  
**Application**: $\text{PATH} \in \text{NLOGSPACE} \implies \overline{\text{PATH}} \in \text{NLOGSPACE}$.  
**Algorithm**: Count reachable nodes incrementally to verify $t$ is unreachable from $s$ without storing all nodes.  

## 3.3 PSPACE-Completeness and Applications
### TQBF: A Canonical PSPACE-Complete Problem
**True Quantified Boolean Formulas (TQBF)**: Deciding if a fully quantified Boolean formula is true.  
- **Reduction Strategy**: Simulate a PSPACE TM’s configurations as QBF variables.  
- **Game Interpretation**: Alternating existential/universal quantifiers model adversarial choices.  

#### Example: Generalized Geography
**Problem**: Determine if Player 1 has a winning strategy in a graph traversal game.  
**PSPACE-Hardness**: Reduced from TQBF by modeling quantifiers as player moves and clauses as board configurations.  

### PSPACE vs. NP
**Critical Difference**:  
- **NP**: Single existential quantifier ($\exists$-verifier).  
- **PSPACE**: Alternating quantifiers ($\exists \forall \exists...$), capturing longer-term strategy.  

## 3.4 Logarithmic Space Complexity
### LOGSPACE and NLOGSPACE
**Definitions**:  
- $\text{LOGSPACE} = \text{DSPACE}(\log n)$: Read-only input + logarithmic work tape.  
- $\text{NLOGSPACE} = \text{NSPACE}(\log n)$.  
**Example**: $\{0^k1^k\} \in \text{LOGSPACE}$ via counter comparison.  

### NLOGSPACE-Complete Problems
**PATH**: Decide if a path exists from $s$ to $t$ in a directed graph.  
- **NLOGSPACE Algorithm**: Non-deterministically guess next nodes while tracking steps.  
**2SAT**: Determine satisfiability of 2-variable clauses.  
- **Reduction**: Encode PATH as 2SAT implications ($\overline{u} \lor v$ for edges $u \to v$).

## 3.5 Complexity Class Relationships
### Hierarchies and Inclusions
**Key Inclusions**:  
1. $\text{PTIME} \subseteq \text{NP} \subseteq \text{PSPACE} \subseteq \text{EXPTIME}$  
2. $\text{NLOGSPACE} \subseteq \text{PTIME}$ (via Savitch)  
**Open Questions**: $\text{PTIME} \stackrel{?}{=} \text{PSPACE}$, $\text{NP} \stackrel{?}{=} \text{co-NP}$.  

### Space vs. Time
**Space-Time Tradeoff**: A TM using $O(s(n))$ space runs in $2^{O(s(n))}$ time (limited by configuration count).  
**Consequence**: $\text{PSPACE} \subseteq \text{EXPTIME}$.  

---

## Key Points to Remember
- **Savitch’s Theorem**: $\text{PSPACE} = \text{NPSPACE}$ via quadratic space simulation. (★★★★☆)  
- **TQBF Completeness**: Central to PSPACE; models adversarial games. Use **recursive quantifier elimination**. (★★★☆☆)  
- **NLOGSPACE = co-NLOGSPACE**: Immerman-Szelepcsényi enables complement closure. Critical for $\overline{\text{PATH}}$. (★★★★★)  
- **2SAT in NLOGSPACE**: Encode graph reachability as implications. (★★★☆☆)  
- **Mnemonic**: "**S**avitch **S**quares **S**pace" (for $\text{NSPACE}(s) \subseteq \text{DSPACE}(s^2)$).  
- **Hierarchy**: $\text{LOGSPACE} \subseteq \text{NLOGSPACE} \subseteq \text{PTIME} \subseteq \text{PSPACE}$. Use **L** < **NL** < **P** < **PSPACE** for quick recall.  