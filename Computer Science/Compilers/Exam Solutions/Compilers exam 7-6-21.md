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


### 2. (5 points) Suppose we are given a deterministic finite automaton for language L on Σ. For all words w ∈ Σ*, we can use the automaton to determine whether w ∈ L in time:

- ~~O(2^{|w|})~~
- ~~O(|w|^2)~~
- O(|w|)
- ~~O(log|w|)~~

Explanation:
In a DFA, the process of checking if a word w of length |w| is accepted involves the following steps:

1. Start from the initial state of the DFA.
2. For each symbol in w, transition to the next state according to the transition function of the DFA.
3. After processing all symbols in w, check if the final state is an accepting state or not.

The time complexity of this process is directly proportional to the length of the word w, as we need to process each symbol once. So, the time complexity is O(|w|).

### 3. (5 points) Suppose we are given a context free grammar for a language L on Σ. For al words ∈ Σ*,  we can use the grammar to determine whether w ∈ Σ* in time:

- polynomial in w
- ~~exponential in w~~
- ~~nope, that is an undecidable problem~~

Explanation:
For most general CFGs, the time complexity of determining whether a word w belongs to the language defined by the grammar is O(n^3), where n is the length of the word w. This time complexity is polynomial in the length of the word.

The reason for this time complexity is that the most widely used parsing algorithms for general CFGs, such as the Cocke-Younger-Kasami (CYK) algorithm or the Earley algorithm, have a time complexity of O(n^3) in the worst case.

However, there are certain classes of CFGs, such as unambiguous grammars or certain types of restricted grammars, where more efficient parsing algorithms can be used, leading to a better time complexity (e.g., O(n^2) or even O(n)).

