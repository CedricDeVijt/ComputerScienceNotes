## Which one of the following is an advantage of automata-based scanners over hand-built scanners?

A. They can always be automatically constructed.
B. They can go beyond regular languages.
C. They implicitly factor out common prefixes.
D. They require less coding effort.

## If you are implementing an LL(k) parser based on a given grammar, which version of recursion should you favor when manipulating/rewriting the grammar?

A. Left recursion
B. Right recursion

## Which of the following is not true about the LLVM intermediate representation language?

A. The number of registers is unlimited
B. The code has to be in SSA: single static assignment
C. Basic blocks can end without a terminator
D. Jumps can only target the start of a basic block

## During the course we have focused on conservative approximations of both type checking and reachability analysis. Argue that the exact versions of both tasks are in fact undecidable.

## Suppose we are given a context free grammar for a language L on Σ. For all words $w \in \sigma^∗$, we can use the grammar to determine whether w ∈ L in time:

A. polynomial in |w|
B. exponential in |w|
C. nope, that is an undecidable problem

## Suppose we are given a grammar (not necessarily context free!) for a language L on Σ. For all words $w \in \sigma^∗$, we can use the grammar to determine whether w ∈Lin time:

A. polynomial in |w|
B. exponential in |w|
C. nope, that is an undecidable problem

## Suppose we are given a deterministic finite automaton with state set Q for a language

Lon Σ. For all words $w \in \sigma^∗$, we can use the automaton to determine whether w ∈Lin time:
A. $O(|Q|^{|w|})$
B. $O(|w|^2)$
C. $O(|w|)$
D. $O(\log |w|)$

## Suppose we are given a deterministic finite automaton for a language Lon Σ. For all words $w \in \sigma^∗$, we can use the automaton to determine whether w ∈Lin time:

A. O($2^{|w|}$)
B. O($|w|^2$)
C. O($|w|$)
D. O($\log |w|$)

## How can we make sure the sequence “true” is always deemed a constant and not a string?

## Give an arithmetic-expression tree such that the minimal number of registers required to evaluate it is exactly 7.

## Give an arithmetic-expression tree such that the minimal number of registers required to evaluate it is exactly 8.

## Give an arithmetic-expression tree such that the minimal number of registers required to evaluate it is exactly the Strahler number of the tree.

## Argue that the converse of the following statement studied during the course is not true.

Theorem 1 (Sentential-form prefixes on the stack). Let (q,w,γZ0) be a configuration reached along
an accepting run of the classical bottom-up parser with q not of the form (A,...). Then:
$$S \rightarrow^∗ \gamma^R\cdot w$$
along a rightmost derivation.
In other words: Give an example of a context-free grammar G and a rightmost derivation of it that
reaches a sentential form γRwsuch that (q,w,γZ0) is not a configuration reached along an accepting
run of the classical bottom-up parser constructed for G — i.e. the one that only has Shift/Reduce
transitions.
