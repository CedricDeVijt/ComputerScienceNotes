## Grammar - Parser
To determine if a grammar is LL(k), LR(k), SLR(k), or LALR(k) without constructing a parser, you can follow these guidelines:
LL(k):
1. Start by finding the first k terminals of each production.
2. If any two productions start with the same k terminals, it's not LL(k).
3. If no two productions start with the same k terminals, it's LL(k).
LR(k):
1. Start by finding the follow sets for each non-terminal.
2. Construct the LR(k) items (production rules with a dot and look-ahead of k terminals).
3. If the LR(k) items have no conflicts (shift-reduce or reduce-reduce), it's LR(k).
4. If there are conflicts, it's not LR(k).
SLR(k):
1. SLR(k) is a subset of LR(k) where k = 1.
2. Follow the same steps as LR(k), but with k = 1.
3. If there are no conflicts for k = 1, it's SLR(k).
LALR(k):
1. LALR(k) is a more relaxed version of SLR(k).
2. Construct the LR(0) items (production rules with a dot, no look-ahead).
3. If the LR(0) items have no conflicts or the conflicts can be resolved by merging certain states, it's LALR(k).
4. If there are unresolvable conflicts, it's not LALR(k).
