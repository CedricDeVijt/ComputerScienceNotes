## Combinatorics

### Number of Subsets
$$
2^n
$$

### Permutations
$$
n! = n \times (n-1) \times (n-2) \times \dots \times 1
$$
$$
\frac{n!}{k_1! \cdot k_2! \cdot \dots \cdot k_m!}
$$

### Combinations
$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

### Multinomial Coefficients
$$
\binom{n}{n_1, n_2, \dots, n_k} = \frac{n!}{n_1! n_2! \dots n_k!}
$$

## Probability

### Basic Probability
$$
P(A) = \frac{|A|}{|\Omega|}
$$

### Complement Rule
$$
P(\overline{A}) = 1 - P(A)
$$

### Addition Rule
$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

### Conditional Probability
$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

### Independence
$$
P(A \cap B) = P(A) \cdot P(B)
$$

### Bayes' Theorem
$$
P(A \mid B) = \frac{P(A) \cdot P(B \mid A)}{P(B)}
$$

## Random Variables and Distributions

### Expectation
$$
E[X] = \sum_{x} x \cdot P(X = x)
$$

### Variance
$$
\text{Var}(X) = E[X^2] - (E[X])^2
$$

### Binomial Distribution
$$
P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
$$
$$
E[X] = np, \quad \text{Var}(X) = np(1-p)
$$

### Poisson Distribution
$$
P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}
$$
$$
E[X] = \lambda, \quad \text{Var}(X) = \lambda
$$

### Uniform Distribution
$$
P(X = x) = \frac{1}{b-a+1}, \quad x \in \{a, a+1, \dots, b\}
$$
$$
E[X] = \frac{a+b}{2}, \quad \text{Var}(X) = \frac{(b-a+1)^2-1}{12}
$$

## Other Useful Formulas

### Inclusion-Exclusion Principle
$$
|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |B \cap C| - |A \cap C| + |A \cap B \cap C|
$$

### Stirling's Approximation
$$
n! \sim \sqrt{2\pi n} \left(\frac{n}{e}\right)^n
$$
