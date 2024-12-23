### Chapter 5: Probability
## 5.1 Elementary Probability
### Key Definitions
1. **Sample Space $S$:**
   The set of all possible outcomes of an experiment.

2. **Event $A$:**
   A subset of the sample space.

3. **Atomic Event:**
   A single possible outcome.

4. **Composite Event:**
   An event comprising two or more outcomes.

5. **Disjoint Events $A$ and $B$:**
   Events with no shared outcomes ($A \cap B = \emptyset$).

### Basic Probability Formula
- For equiprobable sample spaces:
  $$
  P(A) = \frac{|A|}{|S|}
 $$

## 5.2 Conditional Probabilit
### Definitions and Formulas
1. **Conditional Probability:**
   $$
   P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad \text{if } P(B) > 0
  $$

2. **Independence of Events $A$ and $B$:**
   $$
   P(A \cap B) = P(A) \cdot P(B)
  $$
   $A$ and $B$ are independent if knowledge of one does not affect the probability of the other.

## 5.3 Bayes' Theore
- **Bayesian Formula:**
  $$
  P(A_i | B) = \frac{P(A_i) \cdot P(B | A_i)}{\sum_{j=1}^{n} P(A_j) \cdot P(B | A_j)}
 $$

## 5.4 Common Probability Distribution
### 1. Uniform Distribution
- Each outcome is equally likely:
  $$
  P(X = x) = \frac{1}{n}, \quad x \in \{x_1, x_2, \dots, x_n\}
 $$

### 2. Binomial Distribution
- **Probability Mass Function (PMF):**
  $$
  P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}
 $$
- **Expected Value:**
  $$
  E[X] = np
 $$
- **Variance:**
  $$
  \text{Var}(X) = np(1-p)
 $$

### 3. Negative Binomial Distribution
- Number of trials required to achieve $n$ successes:
  $$
  P(X = k) = \binom{k-1}{n-1} p^n (1-p)^{k-n}, \quad k \geq n
 $$

### 4. Poisson Distribution
- Describes the count of events in a fixed interval with rate $\lambda$:
  $$
  P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k \geq 0
 $$
- **Expected Value and Variance:**
  $$
  E[X] = \lambda, \quad \text{Var}(X) = \lambda
 $$

## 5.5 Variance and Standard Deviatio
- **Variance:**
  $$
  \text{Var}(X) = E[X^2] - (E[X])^2
 $$
- **Standard Deviation:**
  $$
  \sigma(X) = \sqrt{\text{Var}(X)}
 $$

## 5.6 Notable Problem
### 1. Monty Hall Problem
- After Monty reveals a door with a goat, switching doors increases the chance of winning to $\frac{2}{3}$.

### 2. Birthday Paradox
- Probability of at least two people sharing a birthday in a group of $n$:
  $$
  P(\text{At least one match}) = 1 - \frac{365 \cdot 364 \cdots (365-n+1)}{365^n}
 $$
