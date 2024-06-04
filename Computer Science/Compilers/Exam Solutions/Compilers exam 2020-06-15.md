### 4. (20 points) Consider the following grammar G and the language L it defines.

| (1) | S   | abc |
| ---: | :---: | :--- |
| (2) |     | ac  |
| (3) |     | ba  |
| (4) |     | bc  |
Which of the following are true? (Several may be true!)
- [x] G is LL(1)
- [ ] G is strongly LL(2)
- [x] G is LL(2)
- [ ] L is LL(3)

Strong Determinism: The grammar must be strongly deterministic with respect to two symbols of lookahead. This means that the decision of which production to apply must be uniquely determined by the current non-terminal and the next two input symbols.

