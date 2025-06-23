## 0 Basic Probability Formulas

### Z-Score and Standardization

- **Z-score (standardization)**:
  $$Z = \frac{X - \mu}{\sigma}$$

- **Converting back from Z-score**:
  $$X = \mu + Z \cdot \sigma$$

### Distribution Parameters

#### Normal Distribution $N(\mu, \sigma^2)$

- **Mean**: $\mu$
- **Variance**: $\sigma^2$
- **Standard deviation**: $\sigma$
- **Probability density function**:
  $$f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$

#### Standard Normal Distribution $N(0,1)$

- **Mean**: $\mu = 0$
- **Variance**: $\sigma^2 = 1$
- **Standard deviation**: $\sigma = 1$
- **Probability density function**:
  $$\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}}$$

### Basic Probability Rules

- **Complement rule**:
  $$P(A^c) = 1 - P(A)$$

- **Addition rule (mutually exclusive)**:
  $$P(A \cup B) = P(A) + P(B)$$

- **Addition rule (general)**:
  $$P(A \cup B) = P(A) + P(B) - P(A \cap B)$$

- **Multiplication rule (independent)**:
  $$P(A \cap B) = P(A) \cdot P(B)$$

- **Conditional probability**:
  $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$

### Expected Value and Variance

- **Expected value (discrete)**:
  $$E[X] = \sum_{i} x_i P(X = x_i)$$

- **Expected value (continuous)**:
  $$E[X] = \int_{-\infty}^{\infty} x f(x) dx$$

- **Variance definition**:
  $$\text{Var}(X) = E[(X - \mu)^2] = E[X^2] - (E[X])^2$$

- **Standard deviation**:
  $$\sigma = \sqrt{\text{Var}(X)}$$

### Linear Transformations

- **For $Y = aX + b$**:
  $$E[Y] = aE[X] + b$$
  $$\text{Var}(Y) = a^2 \text{Var}(X)$$

- **For independent $X$ and $Y$**:
  $$E[X + Y] = E[X] + E[Y]$$
  $$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$$

### Common Discrete Distributions

#### Binomial Distribution $X \sim \text{Bin}(n,p)$

- **Parameters**: $n$ (trials), $p$ (success probability)
- **PMF**: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$
- **Mean**: $E[X] = np$
- **Variance**: $\text{Var}(X) = np(1-p)$

#### Poisson Distribution $X \sim \text{Poisson}(\lambda)$

- **Parameter**: $\lambda$ (rate)
- **PMF**: $P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$
- **Mean**: $E[X] = \lambda$
- **Variance**: $\text{Var}(X) = \lambda$

### Percentiles and Quantiles

- **$p$-th percentile**: Value $x_p$ such that $P(X \leq x_p) = p/100$
- **$q$-th quantile**: Value $x_q$ such that $P(X \leq x_q) = q$
- **For standard normal**: $P(Z \leq z_\alpha) = 1 - \alpha$

## 1 Basic Statistics and Central Limit Theorem

### Sample Statistics

- **Sample mean**:
  $$\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$$

- **Sample variance** (unbiased):
  $$S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X})^2$$

- **Sample standard deviation**:
  $$s = \sqrt{S^2}$$

### Variance Properties

- **Variance of sample mean**:
  $$\text{Var}(\bar{X}_n) = \frac{\sigma^2}{n}$$

- **Sum of i.i.d. random variables** $S_n = \sum_{i=1}^n X_i$:
  $$E[S_n] = n\mu, \quad \text{Var}(S_n) = n\sigma^2$$

- **Variance of linear combination** $\hat{\mu} = \sum_{i=1}^n a_i X_i$:
  $$\text{Var}(\hat{\mu}) = \sum_{i=1}^n a_i^2 \sigma^2$$

### Central Limit Theorem

- **Standardized sum**:
  $$\frac{S_n - n\mu}{\sigma \sqrt{n}} \approx N(0,1)$$

- **Distribution of sample mean**:
  $$\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$$

- **Standardized sample mean**:
  $$Z = \frac{\bar{X} - \mu}{\sigma / \sqrt{n}} \sim N(0,1)$$

## 2 Estimators and Mean Squared Error

### Estimator Properties

- **Bias**:
  $$\text{Bias}(\hat{\theta}) = E[\hat{\theta}] - \theta$$

- **Mean Squared Error (MSE)**:
  $$\text{MSE}(\hat{\theta}) = E[(\hat{\theta} - \theta)^2] = \text{Var}(\hat{\theta}) + [\text{Bias}(\hat{\theta})]^2$$

- **Unbiased estimator condition**:
  $$E[\hat{\theta}] = \theta$$

### Specific Estimators

- **Binomial proportion estimator**:
  $$\hat{p} = \frac{X}{n}, \quad E[\hat{p}] = p$$

- **Unbiased estimator for binomial variance**:
  $$\hat{\sigma}^2 = \frac{X(n-X)}{n-1}$$

- **Expectation of sum of squares**:
  $$E\left[\sum_{i=1}^n (X_i - \bar{X})^2\right] = (n-1)\sigma^2$$

- **Variance of chi-squared**:
  $$\text{Var}\left(\sum_{i=1}^n (X_i - \bar{X})^2\right) = 2(n-1)\sigma^4$$

## 3 Confidence Intervals

### Mean (Known Variance)

$$\bar{X} \pm z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$$

### Mean (Unknown Variance)

$$\bar{X} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}$$

### Variance

$$\left( \frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}} \right)$$

### Standard Deviation

$$\left( \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}} \right)$$

### Proportion

$$\hat{p} \pm z_{\alpha/2} \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$$

### One-sided Confidence Intervals

- **Upper bound**:
  $$\bar{X} + z_\alpha \cdot \frac{\sigma}{\sqrt{n}} \quad \text{or} \quad \bar{X} + t_{\alpha, n-1} \cdot \frac{s}{\sqrt{n}}$$

## 4 Sample Size Calculations

### For Mean (Margin of Error E)

$$n = \left( \frac{z_{\alpha/2} \cdot \sigma}{E} \right)^2$$

### For Proportion (Standard Error)

$$n = \frac{\hat{p}(1-\hat{p})}{(\text{SE})^2}$$

### Maximum Standard Error (at p = 0.5)

$$\text{SE}_{\text{max}} = \frac{0.5}{\sqrt{n}}$$

### For Hypothesis Testing Power

$$n = \left( \frac{(z_{\alpha} + z_{\beta}) \sigma}{\mu_1 - \mu_0} \right)^2$$

## 5 Hypothesis Testing

### One-Sample Tests

#### Z-Test for Mean (Known Variance)

- **Test statistic**:
  $$Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}} \sim N(0,1) \text{ under } H_0$$

- **Acceptance region (two-sided)**:
  $$[-z_{\alpha/2}, z_{\alpha/2}]$$

#### T-Test for Mean (Unknown Variance)

- **Test statistic**:
  $$T = \frac{\bar{X} - \mu_0}{s / \sqrt{n}} \sim t_{n-1} \text{ under } H_0$$

- **Acceptance region (two-sided)**:
  $$[-t_{\alpha/2, n-1}, t_{\alpha/2, n-1}]$$

#### Chi-Squared Test for Variance

- **Test statistic**:
  $$\chi^2 = \frac{(n-1)s^2}{\sigma_0^2} \sim \chi^2_{n-1} \text{ under } H_0: \sigma^2 = \sigma_0^2$$

#### Proportion Test

- **Test statistic**:
  $$Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}} \sim N(0,1) \text{ under } H_0$$

### Two-Sample Tests

#### Two-Sample Z-Test (Known Variances)

$$Z = \frac{\bar{X} - \bar{Y} - (\mu_1 - \mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}} \sim N(0,1) \text{ under } H_0$$

#### Two-Sample T-Test (Equal Variances)

- **Pooled variance**:
  $$s_p^2 = \frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1 + n_2 - 2}$$

- **Test statistic**:
  $$T = \frac{\bar{X} - \bar{Y}}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim t_{n_1 + n_2 - 2} \text{ under } H_0$$

#### Paired T-Test

- **Differences**: $D_i = X_i - Y_i$
- **Sample mean of differences**:
  $$\bar{D} = \frac{1}{n} \sum_{i=1}^n D_i$$
- **Sample variance of differences**:
  $$s_D^2 = \frac{1}{n-1} \sum_{i=1}^n (D_i - \bar{D})^2$$
- **Test statistic**:
  $$T = \frac{\bar{D}}{s_D / \sqrt{n}} \sim t_{n-1} \text{ under } H_0: \mu_D = 0$$

### P-Values

- **Two-sided**: $p = 2 \cdot P(|Z| > |z_{obs}|)$ or $p = 2 \cdot P(|T| > |t_{obs}|)$
- **One-sided (right)**: $p = P(Z > z_{obs})$ or $p = P(T > t_{obs})$
- **One-sided (left)**: $p = P(Z < z_{obs})$ or $p = P(T < t_{obs})$

### Error Types and Power

- **Type I error probability**: $\alpha = P(\text{reject } H_0 \mid H_0 \text{ true})$
- **Type II error probability**: $\beta = P(\text{accept } H_0 \mid H_1 \text{ true})$
- **Power**: $1 - \beta = P(\text{reject } H_0 \mid H_1 \text{ true})$

## 6 Distribution Tests (Goodness of Fit)

### Chi-Squared Goodness of Fit Test

- **Test statistic**:
  $$\chi^2 = \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i}$$
  where $O_i$ = observed frequencies, $E_i$ = expected frequencies

- **Degrees of freedom**:
  - No parameters estimated: $df = k - 1$
  - $m$ parameters estimated: $df = k - 1 - m$

### Specific Distributions

#### Uniform Distribution

- **Expected frequencies**: $E_i = \frac{n}{k}$ for $k$ categories

#### Binomial Distribution

- **Probability**: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$
- **Expected frequencies**: $E_i = n \cdot P(X = i)$

#### Poisson Distribution

- **Probability**: $P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$
- **Parameter estimate**: $\hat{\lambda} = \bar{x}$
- **Expected frequencies**: $E_i = n \cdot P(X = i)$

### Exact Tests

#### Exact Binomial Test

- **P-value (one-sided)**:
  $$p = \sum_{k \geq x_{obs}} \binom{n}{k} p_0^k (1-p_0)^{n-k}$$

## 7 Special Formulas and Relationships

### Distribution-Specific Properties

- **Binomial variance**: $\text{Var}(X) = np(1-p)$ for $X \sim \text{Bin}(n,p)$
- **Standard error for proportion**: $\text{SE} = \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$

### Critical Value Relationships

- **Finding threshold L**: For $P(\bar{X} > L) = \alpha$:
  $$L = \mu + z_{1-\alpha} \cdot \frac{\sigma}{\sqrt{n}}$$

### Optimization Problems

- **Minimizing variance**: Take derivative with respect to parameter, set to zero, solve
- **Unbiased condition**: For linear combination $W = aX + bY$:
  $$E[W] = \mu \implies a + b = 1$$

## 8 Distribution Tables Reference

### Standard Normal Distribution

- $z_{\alpha/2}$ = critical value for two-sided test at significance level $\alpha$
- $z_{\alpha}$ = critical value for one-sided test at significance level $\alpha$

### t-Distribution

- $t_{\alpha/2, df}$ = critical value for two-sided test with $df$ degrees of freedom
- $t_{\alpha, df}$ = critical value for one-sided test with $df$ degrees of freedom

### Chi-Squared Distribution

- $\chi^2_{\alpha/2, df}$ and $\chi^2_{1-\alpha/2, df}$ = critical values for confidence intervals
- $\chi^2_{\alpha, df}$ = critical value for goodness of fit tests
