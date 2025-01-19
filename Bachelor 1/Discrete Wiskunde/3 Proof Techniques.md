## 3.1: Introduction to Mathematical Proofs
### 3.1.1 Definition of a Mathematical Proof
- A mathematical proof is a sequence of logically connected arguments designed to convince a reader of the truth of a statement.
- Arguments must be detailed enough to persuade the intended audience.

### 3.1.2 Overview of Common Proof Methods
- **Trivial Proof**: Uses known facts to prove a statement without additional work.
- **Direct Proof**: Derives the statement directly through logical steps.
- **Proof by Contraposition**: Proves the contrapositive ($¬Q \rightarrow ¬P$).
- **Proof by Contradiction**: Assumes the negation of the statement and shows that it leads to a contradiction.
- **Proof by Cases**: Breaks the statement into multiple cases and proves each individually.
- **Proof by Induction**: Demonstrates that a statement holds for a base case and that if it holds for one case, it holds for the next.

## 3.2: Types of Proofs
### 3.2.1 Trivial Proof
- A trivial proof requires no work because the statement is inherently true or follows directly from given information.

Example:
- If $x$ is a real number such that $x^2 - 1 = 0$, then $x = 1$.

### 3.2.2 Direct Proof
- Direct proofs involve showing that each step logically follows from the previous one, starting with known facts and definitions.

Example:
- If $n$ is a composite number, then it has at least one prime factor.

### 3.2.3 Proof by Contraposition
- Instead of proving $P \rightarrow Q$, prove $¬Q \rightarrow ¬P$.

Example:
- If $p$ is a number greater than 1 with no divisors between 1 and $p$, then $p$ is prime.

### 3.2.4 Proof by Contradiction
- Assume the negation of the statement and demonstrate that it leads to a contradiction.

Example:
- Prove that $\sqrt{2}$ is irrational by assuming it is rational and reaching a contradiction.

### 3.2.5 Proof by Cases
- Split the statement into distinct cases and prove each case.

Example:
- Prove that for every integer $n$, $n^3 - n$ is divisible by 2 by splitting into cases where $n$ is even and where $n$ is odd.



## 3.3: Proof by Induction
### 3.3.1 Basic Induction
- Prove a base case is true (e.g., $S(1)$).
- Assume $S(k)$ is true and prove that $S(k+1)$ follows.

Example:
- Prove that the sum of the first $n$ positive integers is $\frac{n(n + 1)}{2}$.

### 3.3.2 Complete Induction
- Similar to basic induction, but the statement might not hold for all $n \geq 1$. In these cases, modify the base case to start from the appropriate $n_0$.

## 3.4: Advanced Techniques
### 3.4.1 Structural Induction
- Applied to recursively defined structures, such as trees or expressions.

### 3.4.2 Method of Undetermined Coefficients
- Used to find a formula for a sequence when it is known that the sequence can be represented by a polynomial.

Example:
- Given the sequence $-1, -1, 1, 5, 11, 19, 29, \ldots$, derive the polynomial $P(x) = x^2 - 3x + 1$.

### 3.4.3 Guessing Closed Formulas
- Converting recursive relations into closed formulas by transforming the recursive equation into an algebraic equation.

Example:
- The Fibonacci sequence can be expressed as:
  $$F_n = \frac{1}{\sqrt{5}}\left(\left(\frac{1+\sqrt{5}}{2}\right)^n - \left(\frac{1-\sqrt{5}}{2}\right)^n\right)$$

---

## Key Points to Remember

- **Trivial Proof**: Uses already established facts; no need for extra work.
- **Direct Proof**: Logical sequence from known facts.
- **Contraposition**: Prove the negation of the conclusion implies the negation of the premise.
- **Contradiction**: Assume the opposite of what you're trying to prove and show a contradiction.
- **Proof by Cases**: Break the proof into different cases.
- **Mathematical Induction**: Prove a base case, then prove that the next case follows from the previous one.
- **Structural Induction**: Prove statements about recursively defined structures.
- **Undetermined Coefficients**: Solve for unknowns in polynomial representations of sequences.
- **Heuristics for Starting Proofs**: Use different perspectives, simplify the problem, visualize, or work backward to find solutions.