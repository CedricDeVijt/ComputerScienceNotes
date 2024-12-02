## 5.1 Elementary Probability
### Definitions:
- **Sample Space (S)**: The set of all possible outcomes of a probabilistic experiment.
- **Event (A)**: A subset of the sample space, consisting of selected outcomes.
- **Atomic Event**: A single possible outcome.
- **Compound Event**: Consists of two or more outcomes.
- **Disjoint Events (A, B)**: Events with no common outcomes (e.g., $A \cap B = \emptyset$).

### Key Properties of Probabilities
- **Probability Function (P)**:
  - $P(\emptyset) = 0, P(S) = 1$
  - Additivity: $P(A \cup B) = P(A) + P(B)$ for disjoint $A, B$.

### Examples:
1. **Single Die Roll**:
   - Sample Space $S = \{1, 2, 3, 4, 5, 6\}$
   - Event $A$: {even rolls} → $A = \{2, 4, 6\}$.
   - Probability: $P(A) = \frac{|A|}{|S|} = \frac{3}{6} = 0.5$.

2. **Two Dice Rolls**:
   - Different descriptions of sample space:
     - $S_1$: Sum of rolls → $\{2, 3, \ldots, 12\}$
     - $S_2$: Ordered pairs → $\{(1, 1), (1, 2), \ldots, (6, 6)\}$
     - $S_3$: Unordered pairs.

### **Complementary Rule**:
- $P(A') = 1 - P(A)$, where $A'$ is the complement of $A$.

## 5.2 Conditional Probability
### Definitions:
- **Independence**: Events $A$ and $B$ are independent if $P(A \cap B) = P(A) \cdot P(B)$.
- **Conditional Probability**: $P(A|B) = \frac{P(A \cap B)}{P(B)}$, assuming $P(B) \neq 0$.

### Example:
1. **Coin Toss**:
   - Two tosses, $A$: first toss is heads, $B$: second toss is tails.
   - $P(A) = 0.5, P(B) = 0.5, P(A \cap B) = 0.25$.
   - Independence confirmed since $P(A \cap B) = P(A) \cdot P(B)$.

2. **Dice Roll**:
   - Event $A$: Blue die shows 2.
   - Event $B$: Total of 8 across two dice.
   - $P(A|B) \neq P(A)$: Dependent.

## 5.3 Probability Paradoxes
### **Simpson’s Paradox**:
- Aggregated data can lead to conclusions that contradict subgroup analyses.

### **Birthday Paradox**:
- In a group of 30 people, the probability that at least two share a birthday exceeds 70%.

### **Monty Hall Problem**:
- Switching doors after Monty Hall reveals a goat increases the probability of winning from $\frac{1}{3}$ to $\frac{2}{3}$.

## 5.4 Random Variables and Probability Distributions
### **Discrete Random Variables**:
- Defined as functions $X: S \to \mathbb{R}$ assigning numerical values to outcomes.

### **Common Distributions**:
1. **Uniform Distribution**:
   - Equal probabilities across $n$ outcomes.
   - $P(X = x) = \frac{1}{n}$.

2. **Bernoulli Distribution**:
   - One trial, success ($p$) or failure ($1-p$).
   - $P(X = 1) = p, P(X = 0) = 1-p$.

3. **Binomial Distribution**:
   - $n$ Bernoulli trials, counts successes.
   - $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$.

4. **Poisson Distribution**:
   - Counts events over fixed intervals with mean $\lambda$.
   - $P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}$.

## 5.5 Expectation and Variance
### **Expectation (E[X])**:
- $E[X] = \sum x \cdot P(X = x)$
- **Example**: For a die, $E[X] = \frac{1}{6} \sum\limits_{i=1}^{6} i = 3.5$.

### **Variance (Var[X])**:
- $Var[X] = E[X^2] - (E[X])^2$.
- Measures spread of $X$.

---

## Key Points to Remember
- **Sample Space**: Foundation for defining probabilities.
- **Probability Rules**: Completeness ($P(S) = 1$), additivity, complements.
- **Conditional Probability**: Adjusts likelihoods given new information.
- **Distributions**: Uniform, Bernoulli, Binomial, Poisson.
- **Simpson’s Paradox**: Aggregated versus subgroup analysis.
- **Monty Hall Problem**: Switching improves outcomes.
- **Expectation and Variance**: Key metrics for random variables.