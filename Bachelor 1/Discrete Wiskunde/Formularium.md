## Chapter 5: Probability

### 1. **Basic Probability**
- Probability of an event $A$:
  $$
  P(A) = \frac{|A|}{|S|}
 $$
  where $|A|$ is the number of favorable outcomes and $|S|$ is the total number of outcomes in the sample space.

- Conditional probability:
  $$
  P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad \text{if } P(B) > 0
 $$

- Intersection of two events:
  $$
  P(A \cap B) = P(A|B) \cdot P(B) = P(B|A) \cdot P(A)
 $$

- Union of two events:
  $$
  P(A \cup B) = P(A) + P(B) - P(A \cap B)
 $$

### 2. **Bayes' Theorem**
- Bayesian formula for events $A_i$ given $B$:
  $$
  P(A_i | B) = \frac{P(A_i) \cdot P(B | A_i)}{\sum_{j=1}^{n} P(A_j) \cdot P(B | A_j)}
 $$

### 3. **Random Variables and Distributions**

#### Uniform Distribution
- Discrete uniform distribution:
  $$
  P(X = x) = \frac{1}{n}, \quad x \in \{x_1, x_2, \dots, x_n\}
 $$

#### Binomial Distribution
- Probability mass function (PMF):
  $$
  P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}, \quad k = 0, 1, \dots, n
 $$
- Expected value:
  $$
  E[X] = np
 $$
- Variance:
  $$
  \text{Var}(X) = np(1-p)
 $$

#### Negative Binomial Distribution
- PMF for $k \geq n$:
  $$
  P(X = k) = \binom{k-1}{n-1} p^n (1-p)^{k-n}
 $$

#### Poisson Distribution
- PMF for $k \geq 0$:
  $$
  P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}
 $$
- Expected value and variance:
  $$
  E[X] = \lambda, \quad \text{Var}(X) = \lambda
 $$

### 4. **General Properties**
- Variance of a random variable:
  $$
  \text{Var}(X) = E[X^2] - (E[X])^2
 $$
- Standard deviation:
$$\mu = np$$
$$ 

