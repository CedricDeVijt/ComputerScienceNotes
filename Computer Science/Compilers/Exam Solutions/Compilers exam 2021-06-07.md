### 1. (20 points) Translate the following C snippet into LLVM intermediate representation and into MIPS.

```c
int ackermann(int x, int y) {
	if (x < 0 || y < 0)
		return -1;
	if (x == 0)
		return y + 1;
	if (y == 0)
		return ackermann(x-1, 1);
	return achermann(x-1, ackermann(x, y-1));
}
```
<span style="color:red">SKIP</span>
### 2. (5 points) Suppose we are given a deterministic finite automaton for language L on Σ. For all words w ∈ Σ*, we can use the automaton to determine whether w ∈ L in time:

In a DFA, the process of checking if a word w of length |w| is accepted involves the following steps:

1. Start from the initial state of the DFA.
2. For each symbol in w, transition to the next state according to the transition function of the DFA.
3. After processing all symbols in w, check if the final state is an accepting state or not.

The time complexity of this process is directly proportional to the length of the word w, as we need to process each symbol once. So, the time complexity is O(|w|).

### 3. (5 points) Suppose we are given a context free grammar for a language L on Σ. For al words ∈ Σ*,  we can use the grammar to determine whether w ∈ Σ* in time:

For most general CFGs, the time complexity of determining whether a word w belongs to the language defined by the grammar is O(n^3), where n is the length of the word w. This time complexity is polynomial in the length of the word.

The reason for this time complexity is that the most widely used parsing algorithms for general CFGs, such as the Cocke-Younger-Kasami (CYK) algorithm, have a time complexity of O(n^3) in the worst case.

However, there are certain classes of CFGs, such as unambiguous grammars or certain types of restricted grammars, where more efficient parsing algorithms can be used, leading to a better time complexity (e.g., O(n^2) or even O(n)).

### 4. Split the following words into tokens (that is, lexeme-word pairs)
(a) baaaab → C
(b) bbba → B
(c) abbbab → BA

![[Screenshot 2024-06-04 at 21.20.55.png]]
### 5. Let T = {id, +} be a set of terminals. Is the following grammar LL(1)? Does it define an LL(2) language?
| (1) |  S  | E      |
| --: | :-: | :----- |
| (2) |  E  | id + C |
| (3) |  C  | id     |
All rules can be distinguished with one look ahead, this means that the grammar is LL(1) 
Since the grammar is LL(1), it is also LL(k) for any $k \ge 1$. Therefore, the grammar defines an LL(2) language.

### 6. (14 points) During the course we have focused on conservative approximations of both type checking and reachability analysis. Argue that the exact versions of both tasks are in fact undecidable.

The halting problem asks whether a given program will halt or run indefinitely for a given input. To prove the undecidability of exact type checking, we can reduce the halting problem to it. Suppose we have a method to perform exact type checking on any program. We can then construct a program that contains a type error if and only if it does not halt. By checking for type errors in this program, we can effectively solve the halting problem, which is known to be undecidable.

To prove the undecidability of exact reachability analysis, we can construct a program that reaches a specific program point if and only if it does not halt. By checking whether the specific program point is reachable, we can effectively solve the halting problem, which is undecidable.

Both exact type checking and exact reachability analysis require solving problems that are inherently linked to the Halting Problem and other undecidable problems. Therefore, the undecidability of the Halting Problem directly implies the undecidability of exact type checking and exact reachability analysis. Conservative approximations are used in practice to provide safe and computable guarantees about programs, avoiding the undecidability inherent in the exact versions of these tasks.

