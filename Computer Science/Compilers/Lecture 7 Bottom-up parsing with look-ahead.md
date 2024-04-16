### Required and target competences
- **Tools needed**: Formal language theory (languages and machines, machines and computability); understanding from the previous lecture.
- **Skills to obtain**: Theory behind canonical finite automaton with look-ahead; practice implementing SLR and LALR parsers.
- **Utility**: Understanding the implementation of (older/other) parser generators.
## 7.1 SLR(k) parsers
- Why more parsers?
  - Some grammars do not yield deterministic LR(0) parsers, i.e., they are not LR(0). We add look-ahead to make parsers deterministic.
- What are they?
  - Simple Left scanning, Right parsing parsers with k-look-ahead.
### Action table for SLR parsers
- *Action table*: helps the parser to determine the next action based on the current state of the parsing process and the input symbol being processed
- Common actions:
	- Shift
	- Reduce
	- Accept
	- Error
- *Action table with lookahead*: helps the parser make decisions about which actions to take. These lookaheads help the parser determine which action to perform based not only on the current state and input symbol but also on the next symbol in the input stream

## 7.2 LALR(k) parsers
- What are they?
  - Look-Ahead Left scanning, Right parsing parsers with k-look-ahead.

- Difference between SLR(k) and LALR(k) parsers.
	- SLR(k) and LALR(k) parsers are both types of LR(k) parsers
	- LALR parsers are generally more powerful and efficient than SLR parsers due to their compact parsing tables and ability to handle a wider range of grammars
	- SLR parsers are simpler to implement and understand, making them suitable for educational purposes or simpler grammars

### LALR(1) propagation graph
- *LALR(1) propagation graph*: a valuable tool in the construction of LALR(1) parsing tables, helping to visualize the propagation of lookahead symbols and resolve conflicts to produce an efficient and accurate parsing table for the given grammar
## 7.3 LR(k) parsers
- A real table
- generalize the CFSM to a LR(k)-CFSM.
	This means we need to re-visit the notions of item, closure, and successor.
### Items with look-ahead
- *LR(k)-items*: item-look-ahead pairs ($A \leftarrow \alpha_1 \bullet \alpha_2, w$) where $w \in \Sigma^{ \le k}$

- *LR(k)-closure*: closure of an LR(k)-time ($A \leftarrow \alpha_1 \bullet B \alpha_2, w$) is where the set of all LR(k)-times ($B \rightarrow \bullet \beta , y$) where
	$B \rightarrow \beta$ is a rule of the grammar
	$y \in First^k (\alpha_2 w)$
### The LR(k)-CFSM
- *CFSM states*: subsets of LR(k)-items. The a-successor of a state I, for $a \in T \cup V$, is the closure of the set $\{ (A \rightarrow \alpha_1 a \bullet\alpha_2 , w) | (A \rightarrow \alpha_1 \bullet a\alpha_2 , w) \in I \}$

- *LR(k)-CFSM*: the DFA ($Q,V\cup T, \delta , q_0$) where
	$Q$ is the set of all subsets of LR(k)-items
	$q_0$ is the closure of $\{ (S \rightarrow \bullet\alpha , \epsilon) | S \rightarrow \text{is a rule} \}$
	$\delta (q,a)$ maps the closure of the a-successor of q
## 7.4 A hierarchy of CLFs
- Theorem: Relationship between LR(k) languages, LR(1) languages, and languages recognizable by deterministic PDAs.
- Note: Most widely-used programming languages have an LALR(1) grammar.

![[Screenshot 2024-04-16 at 15.15.15.png]]
