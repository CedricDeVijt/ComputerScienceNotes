### Required and Target Competences
- **Tools Required**:
	- Formal language theory (languages and machines, machines and computability).
- **Skills acquired**: 
	- Theory of look-ahead pushdown automata, practice in implementing LPDA-based predictive parsers.
- **Utility**: 
	- Enables compiler construction without manual parser crafting.
## 4.1 Top-down Parsers

### Parsing from the Top
- Intuition: CFGs can be transformed into equivalent PDAs.
- Deterministic top-down parsing algorithm derived from this concept.
### Top-down Parsers: Background
- Historical context: Evolution from bottom-up parsers to top-down parsers.
- Examples: gcc, clang, ANTLR.
### From a CFG to a PDA
- **Algorithm**
	- The idea is to keep in the stack the current sentential form: left = top.
		- **Produce**: For all rules A → α, the PDA has a transition that pops A and pushes α into the stack (without reading from the input).
		- **Match**: For all terminals a ∈ T, there is a transition that pops a and reads a from the input. 
	- The PDA accepts by empty stack.
### Predictive Parsers
- **Look-ahead** corresponds to having access to more than one letter of the input at a time without consuming it.
- Predictive parsers utilize lookahead for deterministic parsing.
## 4.2 Look-ahead Pushdown Automata

### Definition (k-look-ahead PDA)
- A k-LPDA A is a tuple $(Q, \Sigma, \Gamma, \delta, q_0, Z_0, F)$ where everything is as for PDAs except for $\delta : \times (\Sigma \cup \{ \epsilon \}) \times \Gamma \times \Sigma^{≤k} \rightarrow 2^{(Q\times\gamma^*)}$ where $\Sigma^{≤k} = \displaystyle\bigcup_{i=0}^k \Sigma^i$
## 4.3 First and Follow

### Definition (First)
- **First Set**: a set of non-terminal symbol in a grammar that represents the set of terminal symbols that can appear as the first symbol(s) of any string derived from that non-terminal.
- $First^k(\alpha) := \{ w \in T^* : \alpha \Rightarrow^*  wx \wedge (|w|=k or |w| < k \wedge x = \epsilon) \}$
### Definition (Follow)
- **Follow Set**: a set of non-terminal symbol in a grammar that represents the set of terminal symbols that can appear immediately to the right of that non-terminal in any derivation.
- $Follow^k(\alpha) := \{ w \in T^* : \exists \beta, \gamma : S \Rightarrow^* \beta \alpha \gamma \wedge w \in First^k (\gamma)\}$
## 4.4 LL(k) Grammars
### Definition (LL(k) grammar)
- Characteristics of LL(k) grammars.
- Determining LL(k) nature of a grammar.
### Solutions to LL(k) Conflicts
- Strategies for resolving conflicts: Left factoring, Substitution, Left recursion removal.
## 4.5 LL(k) Languages
### Definition (LL(k) language)
- Characteristics of LL(k) languages.
- Equivalence and determinism considerations.
### A Hierarchy of LL(\*) Languages
- Theorem highlighting a strict hierarchy of LL(\*) languages.
## 4.6 LL(1) Parser
### The Action Table for LL(1) Parsers
- Using First and Follow sets for constructing action tables.
- Importance of a well-structured parsing table.
### LL(1) Parsing Example
- Step-by-step parsing example using LL(1) grammar.
### Incorrect Parse
- Error reporting and recovery in parsing process.
### What about LL(k) Action Tables?
- Discussion on complexity and practicality.
- Mention of ANTLR and recursive-descent parsers.
## 4.7 Recursive-Descent Parsers
### Simple Rules
- Introduction to recursive-descent parsing.
- Example of parsing rules with Python-like syntax.