### 1. (20 points) Translate the following C snippet into LLVM intermediate representation and into MIPS.
Skip for now

### 2. (6 points) According to the “longest match” principle, what are the first prefixes of
a) a
b) cbcaa
c) bbba
d) bcabcaa
d) bbb

### 3. (20 points) Let T = {id, +} be a set of terminals. Is the following grammar LL(0)? Does it define an LL(2) language?

```
(1) S → E
(2) E → E+E 
(3)   → id
```

The given grammar is not LL(0). This is because the non-terminal $E$ has two productions, both of which can start with the terminal symbol $\text{id}$. Therefore, it is impossible to distinguish between the two rules based solely on the first terminal, making the grammar not LL(0).

However, the grammar does define an LL(2) language. With two symbols of lookahead, a parser can distinguish between the productions $E \rightarrow E + E$ and $E \rightarrow \text{id}$. Specifically, the presence of $\text{id}$ followed by $+$ or other indicators allows correct selection of the production, satisfying the LL(2) condition.

### 4. (12 points) Let $T = \{0, 1, . . . , 9,a,b,. . . ,f\}$ be a set of terminals and R be the initial non-terminal symbol. In the following attribute grammar the assignments on the right of the grammar rules should be understood as semantic rules a.k.a. attribute functions.

![[Screenshot 2024-06-04 at 15.35.44.png]]

(a) (6 points) Classify the attributes, per non-terminal variable, into synthesized and inherited.





(b) (6 points) What is the meaning (i.e. the semantics) of a word derived from R?
