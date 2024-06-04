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

- Synthesized Attributes: These are attributes whose values are computed from the attribute values of their children nodes in the parse tree.
- Inherited Attributes: These are attributes whose values are computed from the attribute values of their parent and/or sibling nodes in the parse tree.

(a) (6 points) Classify the attributes, per non-terminal variable, into synthesized and inherited.
- R:
	- Synthesized: v(R)
	- Inherited: None
- S:
	- Synthesized: v(S0)
	- Inherited: d(H), d(S1)
- H:
	- Synthesized: v(H)
	- Inherited: d(D), d(A)
- D:
	- Synthesized: v(D)
	- Inherited: d(D)
- A:
	- Synthesized: v(A)
	- Inherited: d(A)

(b) (6 points) What is the meaning (i.e. the semantics) of a word derived from R?
The given attribute grammar seems to compute the numerical value of a hexadecimal string.

The semantics of the string is thus to evaluate the hexadecimal number it represents, calculating its value in decimal by considering the position of each digit. 
The final synthesized attribute v(R) gives the decimal value of the entire hexadecimal string derived from R.

### 5. (12 points) During the course we have focused on conservative approximations of both type checking and reachability analysis. Argue that the exact versions of both tasks are in fact undecidable.

The halting problem asks whether a given program will halt or run indefinitely for a given input. To prove the undecidability of exact type checking, we can reduce the halting problem to it. Suppose we have a method to perform exact type checking on any program. We can then construct a program that contains a type error if and only if it does not halt. By checking for type errors in this program, we can effectively solve the halting problem, which is known to be undecidable.

To prove the undecidability of exact reachability analysis, we can construct a program that reaches a specific program point if and only if it does not halt. By checking whether the specific program point is reachable, we can effectively solve the halting problem, which is undecidable.

Both exact type checking and exact reachability analysis require solving problems that are inherently linked to the Halting Problem and other undecidable problems. Therefore, the undecidability of the Halting Problem directly implies the undecidability of exact type checking and exact reachability analysis. Conservative approximations are used in practice to provide safe and computable guarantees about programs, avoiding the undecidability inherent in the exact versions of these tasks.

