
### 1. (18 points) Translate the following C snippet into LLVM intermediate representation and into MIPS.
<span style="color: red">skip</span>

### 2. (12 points) Split the following words into tokens (that is, lexeme-word pairs)
(a) (4 points) aa
- B
(b) (4 points) aab
- C
(c) (4 points) abbbab
- BA

### 3. (26 points) Let T = {id, +} be a set of terminals. Is the following grammar LL(2)? Does it define an LL(3) language?

| (1) | S     | →    | Exp     |
|-----|-------|------|---------|
| (2) | Exp   | →    | Exp + Exp |
| (3) |       | →    | id      |
| (4) |       | →    | id++    |
The grammar is not LL(2), if we look at the rules for Exp, the first will always be id, but to know if we use rule 2 in combination with rule 4 we need 3 lookup tokens so we can differentiate between all the rules, so the grammar does define an LL(3) language

### 4. (10 points) Let T = {cst, ∗} be a set of terminals and S be the initial non-terminal symbol. In the following attribute grammar the assignments on the right of the grammar rules should be understood as semantic rules a.k.a. attribute functions.
- (a) (5 points) Classify the attributes, per non-terminal variable, into synthesized and inherited. 
	- S:
		- Synthesized: v(S)
		- Inherited:
	- T:
		- Synthesized:
		- Inherited:
	- F:
		- Synthesized:
		- Inherited:

- (b) (5 points) What is the meaning (i.e. the semantics) of a word derived from S?