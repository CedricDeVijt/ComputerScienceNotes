## 1.1 Discrete Univariate Distributions

### Discrete Uniform Distribution
- **Definition**: A random variable $X$ is uniformly distributed on $\Omega = \{1, 2, \ldots, n\}$ if all outcomes are equally likely.
- **PMF**:  
  $$
  P(X = j) = \frac{1}{n}, \quad j = 1, 2, \ldots, n
 $$
- **Expectation**:  
  $$
  E[X] = \frac{n + 1}{2}
 $$
- **Variance**:  
  $$
  \text{Var}[X] = \frac{(n+1)(n-1)}{12} = \frac{n^2 - 1}{12}
 $$

### Bernoulli Distribution
- **Definition**: Models a binary experiment (success = 1, failure = 0) with success probability $p$.
- **PMF**:  
  $$
  P(X = 1) = p, \quad P(X = 0) = 1 - p
 $$
- **Notation**: $X \sim \mathcal{B}(1, p)$
- **Expectation**: $E[X] = p$
- **Variance**: $\text{Var}[X] = p(1 - p)$

### Binomial Distribution
- **Definition**: Counts the number of successes $Y$ in $n$ independent Bernoulli trials.
- **PMF**:  
  $$
  P(Y = k) = \binom{n}{k} p^k (1 - p)^{n - k}, \quad k = 0, 1, \ldots, n
 $$
- **Notation**: $Y \sim \mathcal{B}(n, p)$
- **Expectation**: $E[Y] = np$
- **Variance**: $\text{Var}[Y] = np(1 - p)$
- **Additivity**: If $Y_1 \sim \mathcal{B}(n_1, p)$ and $Y_2 \sim \mathcal{B}(n_2, p)$ are independent, then $Y_1 + Y_2 \sim \mathcal{B}(n_1 + n_2, p)$.

### Negative Binomial Distribution
- **Definition**: Counts the number of failures $j$ before the $r$-th success.
- **PMF**:  
  $$
  P(X = j) = \binom{j + r - 1}{j} (1 - \theta)^r \theta^j, \quad j = 0, 1, 2, \ldots
 $$
- **Notation**: $X \sim \text{NB}(r, \theta)$ (or $\text{NB}(r, p)$ depending on convention).
- **Key Use**: Models overdispersed count data.

### Poisson Distribution
- **Definition**: Models the number of events in a fixed interval with rate $\alpha$.
- **PMF**:  
  $$
  P(X = j) = \frac{\alpha^j}{j!} e^{-\alpha}, \quad j = 0, 1, 2, \ldots
 $$
- **Notation**: $X \sim \mathcal{P}(\alpha)$
- **Expectation**: $E[X] = \alpha$
- **Variance**: $\text{Var}[X] = \alpha$
- **Additivity**: If $X_1 \sim \mathcal{P}(\alpha_1)$ and $X_2 \sim \mathcal{P}(\alpha_2)$ are independent, then $X_1 + X_2 \sim \mathcal{P}(\alpha_1 + \alpha_2)$.

## 1.2 Continuous Univariate Distributions

### Continuous Uniform Distribution
- **Definition**: Equal probability density over $[a, b]$.
- **PDF**:  
  $$
  f_{a,b}(x) = \begin{cases}
    \frac{1}{b - a} & \text{if } a \leq x \leq b \\
    0 & \text{otherwise}
  \end{cases}
 $$
- **Expectation**: $E[X] = \frac{a + b}{2}$
- **Variance**:  
  $$
  \text{Var}[X] = \frac{(b - a)^2}{12}
 $$

### Normal (Gaussian) Distribution
- **Standard Normal**: $Z \sim \mathcal{N}(0, 1)$ with PDF:  
  $$
  \phi(x) = \frac{1}{\sqrt{2\pi}} e^{-x^2/2}
 $$
- **General Normal**: $X = \sigma Z + \mu \sim \mathcal{N}(\mu, \sigma^2)$ with PDF:  
  $$
  f_{\mu,\sigma}(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}
 $$
- **Expectation**: $E[X] = \mu$
- **Variance**: $\text{Var}[X] = \sigma^2$
- **Additivity**: If $X_1 \sim \mathcal{N}(\mu_1, \sigma_1^2)$ and $X_2 \sim \mathcal{N}(\mu_2, \sigma_2^2)$ are independent, then $X_1 + X_2 \sim \mathcal{N}(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$.

### Chi-Squared ($\chi^2$) Distribution
- **Definition**: Sum of squares of $n$ independent standard normal variables.
- **Notation**: $X \sim \chi_n^2$
- **PDF**:  
  $$
  f_{\chi_n^2}(x) = \frac{1}{2^{n/2} \Gamma(n/2)} x^{n/2 - 1} e^{-x/2}, \quad x > 0
 $$
- **Expectation**: $E[X] = n$
- **Variance**: $\text{Var}[X] = 2n$
- **Additivity**: If $X_1 \sim \chi_{n_1}^2$ and $X_2 \sim \chi_{n_2}^2$ are independent, then $X_1 + X_2 \sim \chi_{n_1 + n_2}^2$.

### Student’s t-Distribution
- **Definition**: Arises from $T = \frac{Z}{\sqrt{X/n}}$ where $Z \sim \mathcal{N}(0,1)$ and $X \sim \chi_n^2$.
- **Notation**: $T \sim t_n$
- **PDF**:  
  $$
  f_{t_n}(t) = \frac{\Gamma\left(\frac{n+1}{2}\right)}{\sqrt{n\pi} \Gamma\left(\frac{n}{2}\right)} \left(1 + \frac{t^2}{n}\right)^{-\frac{n+1}{2}}
 $$
- **Expectation**: $E[T] = 0$ (for $n > 1$)
- **Variance**: $\text{Var}[T] = \frac{n}{n - 2}$ (for $n > 2$)

### F-Distribution
- **Definition**: Ratio of two scaled chi-squared variables: $X = \frac{W/m}{V/n}$ where $W \sim \chi_m^2$ and $V \sim \chi_n^2$.
- **Notation**: $X \sim F_{m,n}$
- **Key Property**:  
  $$
  F_{m,n}(x) = 1 - F_{n,m}\left(\frac{1}{x}\right)
 $$
- **Expectation**: $E[X] = \frac{n}{n - 2}$ (for $n > 2$)

## Key Points to Remember
- **Discrete Uniform**:  
  - $E[X] = \frac{n+1}{2}$, $\text{Var}[X] = \frac{n^2 - 1}{12}$.
- **Bernoulli**:  
  - Binary outcomes; $E[X] = p$, $\text{Var}[X] = p(1-p)$.
- **Binomial**:  
  - Sum of $n$ Bernoulli trials; $E[Y] = np$, $\text{Var}[Y] = npq$.
  - Additive for independent trials with same $p$.
- **Negative Binomial**:  
  - Models failures before $r$-th success; PMF uses combinations with repetition.
- **Poisson**:  
  - $E[X] = \text{Var}[X] = \alpha$; additive for independent counts.
- **Continuous Uniform**:  
  - $E[X] = \frac{a+b}{2}$, $\text{Var}[X] = \frac{(b-a)^2}{12}$.
- **Normal Distribution**:  
  - Linear transformations preserve normality; 68-95-99.7 rule for standard normal.
- **Chi-Squared**:  
  - Sum of squared normals; $E[X] = n$, $\text{Var}[X] = 2n$.
- **Student’s t**:  
  - Heavier tails than normal; approaches normal as $n \to \infty$.
- **F-Distribution**:  
  - Used in ANOVA; reciprocal relationship between $F_{m,n}$ and $F_{n,m}$.