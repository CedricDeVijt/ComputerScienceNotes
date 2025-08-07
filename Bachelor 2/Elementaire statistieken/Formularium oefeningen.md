## 1.1 Central Limit Theorem and Estimators

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

## 1.2 Confidence Intervals

### Mean (Known Variance)
- $\bar{X} \pm Z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$
- Critical Values:
  - 95%: $Z_{\alpha/2} = 1.96$
  - 99%: $Z_{\alpha/2} = 2.576$
  - 90%: $Z_{\alpha/2} = 1.645$

### Mean (Unknown Variance)
- $\bar{X} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}$
- Sample Variance: $s^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X})^2$

### Standard Deviation
- $\left( \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}} \right)$

### Proportion
- $\hat{p} \pm Z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$
- $\hat{p} = \frac{X}{n}$

## 1.3 Hypothesis Testing

### Mean (Known Variance)
- Hypotheses: $H_0: \mu = \mu_0$, $H_1: \mu \neq \mu_0$ (or one-sided)
- Test Statistic: $Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}}$, $Z \sim N(0,1)$
- Rejection Region:
  - Two-sided: $|Z| > Z_{\alpha/2}$
  - One-sided: $Z > Z_{\alpha}$ or $Z < -Z_{\alpha}$
- P-value:
  - Two-sided: $p = 2 \cdot [1 - \Phi(|Z|)]$
  - One-sided: $p = 1 - \Phi(Z)$ or $p = \Phi(Z)$

### Mean (Unknown Variance)
- Test Statistic: $T = \frac{\bar{X} - \mu_0}{s / \sqrt{n}}$, $T \sim t_{n-1}$

### Variance
- Hypotheses: $H_0: \sigma^2 = \sigma_0^2$, $H_1: \sigma^2 \neq \sigma_0^2$ (or one-sided)
- Test Statistic: $\chi^2 = \frac{(n-1)s^2}{\sigma_0^2}$, $\chi^2 \sim \chi^2_{n-1}$
- Rejection Region:
  - Two-sided: $\chi^2 < \chi^2_{1-\alpha/2, n-1}$ or $\chi^2 > \chi^2_{\alpha/2, n-1}$
  - One-sided: $\chi^2 > \chi^2_{\alpha, n-1}$ or $\chi^2 < \chi^2_{1-\alpha, n-1}$

### Type II Error
- $\beta = \Phi\left(Z_{\alpha/2} - \frac{|\mu_1 - \mu_0|}{\sigma / \sqrt{n}}\right) - \Phi\left(-Z_{\alpha/2} - \frac{|\mu_1 - \mu_0|}{\sigma / \sqrt{n}}\right)$

## 1.4 Comparison Tests

### Two-Sample Z-Test (Known Variance, Equal Variances)
- Hypotheses: $H_0: \mu_1 = \mu_2$, $H_1: \mu_1 \neq \mu_2$
- Test Statistic: $Z = \frac{\bar{X}_1 - \bar{X}_2}{\sqrt{\sigma^2 \left(\frac{1}{n_1} + \frac{1}{n_2}\right)}}$
- P-value: $p = 2 \cdot [1 - \Phi(|Z|)]$

## 1.5 Distributions

### Uniform Distribution (Discrete)
- PMF: $P(X = k) = \frac{1}{n}$, $k = 0, 1, \ldots, 9$
- Expected Value: $E(X) = \frac{n-1}{2}$
- Variance: $\text{Var}(X) = \frac{n^2 - 1}{12}$

## 1.6 General Formulas
- Sample Mean: $\bar{X} = \frac{1}{n} \sum_{i=1}^n X_i$
- Sample Proportion: $\hat{p} = \frac{X}{n}$