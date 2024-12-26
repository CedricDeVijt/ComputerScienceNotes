### Chapter 5: Probability
$P(A) = \frac{|A|}{|S|}$

$P(A|B) = \frac{P(A \cap B)}{P(B)}, \quad \text{if } P(B) > 0$

$P(A \cap B) = P(A) \cdot P(B)$

$P(A_i | B) = \frac{P(A_i) \cdot P(B | A_i)}{\sum_{j=1}^{n} P(A_j) \cdot P(B | A_j)}$ (**Bayesian Formula**)

$P(X = x) = \frac{1}{n}, \quad x \in \{x_1, x_2, \dots, x_n\}$ (**Uniform Distribution**)



$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$ (**Binomial Distribution**)
$E[X] = np$
$\text{Var}(X) = np(1-p)$

$P(X = k) = \binom{k-1}{n-1} p^n (1-p)^{k-n}, \quad k \geq n$ (**Negative Binomial Distribution**)

  P(X = k) = \frac{e^{-\lambda} \lambda^k}{k!}, \quad k \geq 0
 $$
- **Expected Value and Variance:**
  $$
  E[X] = \lambda, \quad \text{Var}(X) = \lambda
 $$

## 5.5 Variance and Standard Deviation
- **Variance:**
  $$
  \text{Var}(X) = E[X^2] - (E[X])^2
 $$
- **Standard Deviation:**
  $$
  \sigma(X) = \sqrt{\text{Var}(X)}
 $$
