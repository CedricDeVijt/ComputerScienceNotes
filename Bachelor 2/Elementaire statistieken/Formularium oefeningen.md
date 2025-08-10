## 1 General Formulas

- Sample Mean: $\bar{X} = \frac{1}{n} \sum_{i=1}^n X_i$
- Sample Proportion: $\hat{p} = \frac{X}{n}$

## 2 Central Limit Theorem and Estimators

### Variance of Sample Mean

- $\text{Var}(\bar{X}) = \frac{\sigma^2}{n}$
- $\text{SE}(\bar{X}) = \frac{\sigma}{\sqrt{n}}$

### Probability for Sample Mean

- $Z = \frac{\bar{X} - \mu}{\sigma / \sqrt{n}}$
- $P(\bar{X} > x) = 1 - \Phi\left(\frac{x - \mu}{\sigma / \sqrt{n}}\right)$

### Estimator Bias and MSE

- Unbiased: $E(\hat{\theta}) = \theta$
- Bias: $\text{Bias}(\hat{\theta}) = E(\hat{\theta}) - \theta$
- MSE: $\text{MSE}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Bias}(\hat{\theta})]^2$

### Binomial Estimator

- Sample Proportion: $\hat{p} = \frac{X}{n}$, where $X \sim B(n, p)$
- Expected Value: $E(\hat{p}) = p$
- Variance: $\text{Var}(\hat{p}) = \frac{p(1-p)}{n}$
- Alternative Estimator Bias (e.g., $\tilde{p}$): $\text{Bias}(\tilde{p}) = E(\tilde{p}) - p$

## 3 Confidence Intervals

### Mean (Known Variance)

- $\bar{X} \pm Z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$

### Mean (Unknown Variance)

- $\bar{X} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}$
- Sample Variance: $s^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X})^2$

### Variance

- $\left( \frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}} \right)$

### Standard Deviation

- $\left( \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}} \right)$

### Proportion

- $\hat{p} \pm Z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$
- $\hat{p} = \frac{X}{n}$

## 4 Hypothesis Testing

### Mean (Known Variance)

- Hypotheses: $H_0: \mu = \mu_0$, $H_1: \mu \neq \mu_0$ (or one-sided)
- Test Statistic: $Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}}$, $Z \sim N(0,1)$
- Acceptance Region:
  - Two-sided: $|Z| \leq Z_{\alpha/2}$
  - One-sided: $Z \leq Z_{\alpha}$ or $Z \geq -Z_{\alpha}$
- P-value:
  - Two-sided: $p = 2 \cdot [1 - \Phi(|Z|)]$
  - One-sided: $p = 1 - \Phi(Z)$ or $p = \Phi(Z)$

### Mean (Unknown Variance)

- Test Statistic: $T = \frac{\bar{X} - \mu_0}{s / \sqrt{n}}$, $T \sim t_{n-1}$
- Acceptance Region:
  - Two-sided: $|T| \leq t_{\alpha/2, n-1}$
  - One-sided: $T \leq t_{\alpha, n-1}$ or $T \geq -t_{\alpha, n-1}$
- P-value:
  - Two-sided: $p = 2 \cdot [1 - \Phi(|T|)]$
  - One-sided: $p = 1 - \Phi(T)$ or $p = \Phi(T)$

### Proportion

- Test Statistic: $Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}$, $Z \sim N(0,1)$
- Acceptance Region:
  - Two-sided: $|Z| \leq Z_{\alpha/2}$
  - One-sided: $Z \leq Z_{\alpha}$ or $Z \geq -Z_{\alpha}$
- P-value:
  - Two-sided: $p = 2 \cdot [1 - \Phi(|Z|)]$
  - One-sided: $p = 1 - \Phi(Z)$ or $p = \Phi(Z)$

### Variance

- Hypotheses: $H_0: \sigma^2 = \sigma_0^2$, $H_1: \sigma^2 \neq \sigma_0^2$ (or one-sided)
- Test Statistic: $\chi^2 = \frac{(n-1)s^2}{\sigma_0^2}$, $\chi^2 \sim \chi^2_{n-1}$
- Acceptance Region:
  - Two-sided: $\chi^2_{1-\alpha/2, n-1} \leq \chi^2 \leq \chi^2_{\alpha/2, n-1}$
  - One-sided: $\chi^2 \leq \chi^2_{\alpha, n-1}$ or $\chi^2 \geq \chi^2_{1-\alpha, n-1}$
- P-value:
  - Two-sided: $p = 2 \cdot \min\{P(\chi^2_{n-1} \geq \chi^2_{obs}), P(\chi^2_{n-1} \leq \chi^2_{obs})\}$
  - One-sided: $p = P(\chi^2_{n-1} \geq \chi^2_{obs})$ or $p = P(\chi^2_{n-1} \leq \chi^2_{obs})$

### Type II Error

- $\beta = \Phi\left(Z_{\alpha/2} - \frac{|\mu_1 - \mu_0|}{\sigma / \sqrt{n}}\right) - \Phi\left(-Z_{\alpha/2} - \frac{|\mu_1 - \mu_0|}{\sigma / \sqrt{n}}\right)$ (for two-sided tests)

### Chi-Square Goodness of Fit

- Hypotheses: 
	- $H_0$: Observed frequencies match expected, 
	- $H_1$: They do not
- Test Statistic: $\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i}$, where $O_i$ is observed frequency, $E_i$ is expected frequency
- Distribution: $\chi^2 \sim \chi^2_{k-1}$, where $k$ is the number of categories
- Acceptance Region: $\chi^2 \leq \chi^2_{\alpha, k-1}$
- P-value: $p = P(\chi^2_{k-1} \geq \chi^2_{observed})$

## 5 Comparison Tests

### Two-Sample Z-Test (Known Variances — σ₁ and σ₂ given)

- Hypotheses:
  $H_0: \mu_1 - \mu_2 = \Delta_0$ (often $\Delta_0 = 0$)
  $H_1:$ one- or two-sided depending on problem.
- Test Statistic:$Z = \frac{(\bar{X}_1 - \bar{X}_2) - \Delta_0}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}}$
- Acceptance Region:
  - Two-sided: $|Z| > z_{\alpha/2}$
  - Upper-tail: $Z > z_{\alpha}$
  - Lower-tail: $Z < -z_{\alpha}$
- p-value:
  - Two-sided: $p = 2\,[1 - \Phi(|Z|)]$
  - Upper-tail: $p = 1 - \Phi(Z)$
  - Lower-tail: $p = \Phi(Z)$

### Two-Sample t-Test (Unknown Variances, Equal Variances Assumed — pooled)

- F-test for Equal Variances (prerequisite):
  - Hypotheses: $H_0: \sigma_1^2 = \sigma_2^2$, $H_1: \sigma_1^2 \neq \sigma_2^2$
  - Test Statistic: $F = \frac{s_1^2}{s_2^2}$ (larger variance in numerator), $F \sim F_{n_1-1, n_2-1}$
  - Acceptance Region: $F \leq F_{\alpha/2, n_1-1, n_2-1}$
- Hypotheses:
  $H_0: \mu_1 - \mu_2 = \Delta_0$ (often $\Delta_0 = 0$)
  $H_1:$ one- or two-sided depending on problem.
- Pooled variance: $s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}$
- Test Statistic: $T = \frac{(\bar{X}_1 - \bar{X}_2) - \Delta_0}{s_p\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}$ with $T \sim t_{n_1 + n_2 - 2}$
- Acceptance Region:
  - Two-sided: $|T| > t_{\alpha/2,\,n_1+n_2-2}$
  - Upper-tail: $T > t_{\alpha,\,n_1+n_2-2}$
  - Lower-tail: $T < -t_{\alpha,\,n_1+n_2-2}$
- p-value: same structure as Z-test but with $t$-CDF $F_t(\cdot)$.

## 6 Distributions

### Uniform Distribution (Discrete)

- PMF: $P(X = k) = \frac{1}{n}$, $k = a, a+1, \ldots, a+n-1$
- Expected Value: $E(X) = a + \frac{n-1}{2}$
- Variance: $\text{Var}(X) = \frac{n^2 - 1}{12}$

### Binomial Distribution

- PMF: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$
- Expected Value: $E(X) = np$
- Variance: $\text{Var}(X) = np(1-p)$
