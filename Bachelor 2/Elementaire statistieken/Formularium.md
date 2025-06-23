## 1 Descriptive Statistics and Estimators

### Sample Mean

- Sample mean:
  $$
  \bar{X} = \frac{1}{n} \sum_{i=1}^n X_i
  $$

### Sample Variance

- Sample variance (unbiased estimator):
  $$
  S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X})^2
  $$

### Expectation and Variance of Linear Combinations

- For $\hat{\theta} = \sum_{i=1}^n a_i X_i$, with i.i.d. $X_i \sim (\mu, \sigma^2)$:
  - Expectation:
    $$
    E[\hat{\theta}] = \sum_{i=1}^n a_i \mu
    $$
  - Variance:
    $$
    \text{Var}(\hat{\theta}) = \sum_{i=1}^n a_i^2 \sigma^2
    $$

### Bias and Mean Squared Error (MSE)

- Bias of an estimator $\hat{\theta}$:
  $$
  \text{Bias}(\hat{\theta}) = E[\hat{\theta}] - \theta
  $$
- Mean Squared Error:
  $$
  \text{MSE}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Bias}(\hat{\theta})]^2
  $$

### Variance of Sample Mean

- Variance of sample mean for i.i.d. $X_i$:
  $$
  \text{Var}(\bar{X}) = \frac{\sigma^2}{n}
  $$

## 2 Central Limit Theorem

### Sum of Random Variables

- For $S_n = \sum_{i=1}^n X_i$, with $E[X_i] = \mu$, $\text{Var}(X_i) = \sigma^2$:
  - Expectation:
    $$
    E[S_n] = n \mu
    $$
  - Variance:
    $$
    \text{Var}(S_n) = n \sigma^2
    $$

### Central Limit Theorem

- For large $n$:
  $$
  \frac{S_n - n \mu}{\sigma \sqrt{n}} \approx N(0,1)
  $$
- For sample mean:
  $$
  \frac{\bar{X} - \mu}{\sigma / \sqrt{n}} \approx N(0,1)
  $$

## 3 Confidence Intervals

### Mean (Known Variance)

- Confidence interval for $\mu$:
  $$
  \bar{X} \pm z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}
  $$
  where $z_{\alpha/2}$ is the critical value from $N(0,1)$.

### Mean (Unknown Variance)

- Confidence interval for $\mu$:
  $$
  \bar{X} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}
  $$
  where $t_{\alpha/2, n-1}$ is the critical value from the t-distribution with $n-1$ degrees of freedom.

### Variance

- Confidence interval for $\sigma^2$:
  $$
  \left( \frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}} \right)
  $$
- For $\sigma$:
  $$
  \left( \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}} \right)
  $$

### Proportion

- Sample proportion:
  $$
  \hat{p} = \frac{X}{n}
  $$
- Confidence interval for $p$:
  $$
  \hat{p} \pm z_{\alpha/2} \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}
  $$

### Sample Size

- For mean (margin of error $E$):
  $$
  n = \left( \frac{z_{\alpha/2} \cdot \sigma}{E} \right)^2
  $$
- For proportion (maximum SE, $p = 0.5$):
  $$
  n = \frac{0.25}{(\text{SE})^2}
  $$

## 4 Hypothesis Testing

### Z-Test for Mean (Known Variance)

- Test statistic:
  $$
  Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}} \sim N(0,1) \text{ under } H_0
  $$
- P-value:
  - Two-sided ($H_1: \mu \neq \mu_0$):
    $$
    p = 2 \cdot P(Z > |z|)
    $$
  - One-sided ($H_1: \mu > \mu_0$):
    $$
    p = P(Z > z)
    $$

### T-Test for Mean (Unknown Variance)

- Test statistic:
  $$
  T = \frac{\bar{X} - \mu_0}{s / \sqrt{n}} \sim t_{n-1} \text{ under } H_0
  $$
- P-value:
  - Two-sided:
    $$
    p = 2 \cdot P(T > |t|)
    $$
  - One-sided:
    $$
    p = P(T > t)
    $$

### Test for Proportion

- Test statistic:
  $$
  Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}} \sim N(0,1) \text{ under } H_0
  $$
- P-value: As for Z-test above.

### Chi-Squared Test for Variance

- Test statistic:
  $$
  \chi^2 = \frac{(n-1)s^2}{\sigma_0^2} \sim \chi^2_{n-1} \text{ under } H_0: \sigma^2 = \sigma_0^2
  $$
- P-value (two-sided):
  $$
  p = 2 \cdot \min(P(\chi^2 > \chi^2_{\text{obs}}), P(\chi^2 < \chi^2_{\text{obs}}))
  $$

### Power and Sample Size

- Power:
  $$
  1 - \beta = P(\text{reject } H_0 \mid \mu = \mu_1)
  $$
- Sample size for mean:
  $$
  n = \left( \frac{(z_{\alpha} + z_{\beta}) \sigma}{\mu_1 - \mu_0} \right)^2
  $$

## 5 Comparison Tests

### Two-Sample Z-Test (Known Variances)

- Test statistic:
  $$
  Z = \frac{\bar{X} - \bar{Y} - (\mu_1 - \mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}} \sim N(0,1) \text{ under } H_0: \mu_1 = \mu_2
  $$

### Two-Sample T-Test (Equal Variances)

- Pooled variance:
  $$
  s_p^2 = \frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1 + n_2 - 2}
  $$
- Test statistic:
  $$
  T = \frac{\bar{X} - \bar{Y}}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim t_{n_1 + n_2 - 2} \text{ under } H_0
  $$

### Paired T-Test

- Differences: $D_i = X_i - Y_i$
- Test statistic:
  $$
  T = \frac{\bar{D}}{s_D / \sqrt{n}} \sim t_{n-1} \text{ under } H_0: \mu_D = 0
  $$
  where $\bar{D} = \frac{1}{n} \sum D_i$, $s_D^2 = \frac{1}{n-1} \sum (D_i - \bar{D})^2$.

## 6 Distribution Tests

### Chi-Squared Goodness-of-Fit Test

- Test statistic:
  $$
  \chi^2 = \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i} \sim \chi^2_{k-1}
  $$
  where $O_i$ are observed frequencies, $E_i$ are expected frequencies.

### Chi-Squared Test for Specific Distributions

- For distributions (e.g., binomial, Poisson), adjust expected frequencies $E_i = n \cdot P(X = i)$ and degrees of freedom (subtract number of estimated parameters).

### Exact Binomial Test

- P-value for $X \sim \text{Bin}(n, p_0)$:
  $$
  p = \sum_{k \geq x_{\text{obs}}} \binom{n}{k} p_0^k (1-p_0)^{n-k}
  $$

## 7 Specific Distributions

### Binomial

- Variance:
  $$
  \text{Var}(X) = np(1-p)
  $$
- Unbiased estimator for variance:
  $$
  \hat{\sigma}^2 = \frac{X(n-X)}{n-1}
  $$

### Poisson

- Probability:
  $$
  P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad \hat{\lambda} = \bar{x}
  $$
