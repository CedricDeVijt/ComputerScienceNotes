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

- $\left( \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}, \frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}} \right)$

### Standard Deviation

- $\left( \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}} \right)$

### Proportion

- $\hat{p} \pm Z_{\alpha/2} \cdot \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}$
- $\hat{p} = \frac{X}{n}$

## 4 Hypothesis Testing

### Mean (Known Variance)

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

- Test Statistic: $\chi^2 = \sum \frac{(O_i - E_i)^2}{E_i}$, where $O_i$ is observed frequency, $E_i$ is expected frequency
- Distribution: $\chi^2 \sim \chi^2_{k-1}$, where $k$ is the number of categories
- Acceptance Region: $\chi^2 \leq \chi^2_{\alpha, k-1}$
- P-value: $p = P(\chi^2_{k-1} \geq \chi^2_{observed})$

## 5 Comparison Tests

### Test for Equality of Two Variances (F-Test)

- Test Statistic: $F = \frac{S_1^2}{S_2^2}$, $F \sim F_{n_1-1, n_2-1}$ under $H_0$ (swap samples if needed so $S_1^2 > S_2^2$ and $f > 1$)
- Acceptance Region:
  - Two-sided: $F_{n_1-1,n_2-1,\alpha/2} \leq F \leq F_{n_1-1,n_2-1,1-\alpha/2}$ (or equivalently using $F_{m,n,\alpha} = 1/F_{n,m,1-\alpha}$: $[1/F_{n_2-1,n_1-1,1-\alpha/2}, F_{n_1-1,n_2-1,1-\alpha/2}]$)
  - Upper-tailed ($H_1: \sigma_1 > \sigma_2$): $F \leq F_{n_1-1,n_2-1,1-\alpha}$
  - Lower-tailed ($H_1: \sigma_1 < \sigma_2$): $F \geq F_{n_1-1,n_2-1,\alpha}$
- P-value:
  - Two-sided: $p = 2 \min\{F_{n_1-1,n_2-1}(f), 1 - F_{n_1-1,n_2-1}(f)\}$
  - Upper-tailed: $p = 1 - F_{n_1-1,n_2-1}(f)$
  - Lower-tailed: $p = F_{n_1-1,n_2-1}(f)$
- Confidence Interval for $\sigma_1^2 / \sigma_2^2$ $(100(1-\alpha)\%$): $\left[ \frac{S_1^2}{S_2^2} \cdot \frac{1}{F_{n_1-1,n_2-1,1-\alpha/2}}, \frac{S_1^2}{S_2^2} \cdot F_{n_2-1,n_1-1,1-\alpha/2} \right]$

### Two-Sample Z-Test for Means (Known Variances — $\sigma_1$ and $\sigma_2$ given)

- Test Statistic: $Z = \frac{(\bar{X}_1 - \bar{X}_2) - \Delta_0}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}}$
- Acceptance Region:
  - Two-sided: $|Z| \leq z_{1-\alpha/2}$
  - Upper-tailed: $Z \leq z_{1-\alpha}$
  - Lower-tailed: $Z \geq -z_{1-\alpha}$
- P-value:
  - Two-sided: $p = 2\,[1 - \Phi(|Z|)]$
  - Upper-tailed: $p = 1 - \Phi(Z)$
  - Lower-tailed: $p = \Phi(Z)$
- Confidence Interval for $\mu_1 - \mu_2$ (100(1-$\alpha$)%): $(\bar{X}_1 - \bar{X}_2) \pm z_{1-\alpha/2} \sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}$

### Two-Sample t-Test for Means (Independent Samples, Unknown but Equal Variances Assumed — pooled)

- Prerequisite: Use F-test to confirm $\sigma_1^2 = \sigma_2^2$
- Pooled variance: $s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}$
- Hypotheses: $H_0: \mu_1 - \mu_2 = \Delta_0$ (often $\Delta_0 = 0$), $H_1:$ one- or two-sided depending on problem.
- Test Statistic: $T = \frac{(\bar{X}_1 - \bar{X}_2) - \Delta_0}{s_p\sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}$ with $T \sim t_{n_1 + n_2 - 2}$
- Acceptance Region:
  - Two-sided: $|T| \leq t_{1-\alpha/2,\,n_1+n_2-2}$
  - Upper-tailed: $T \leq t_{1-\alpha,\,n_1+n_2-2}$
  - Lower-tailed: $T \geq -t_{1-\alpha,\,n_1+n_2-2}$
- P-value: same structure as Z-test but with $t$-CDF $F_t(\cdot)$.
- Confidence Interval for $\mu_1 - \mu_2$ (100(1-$\alpha$)%): $(\bar{X}_1 - \bar{X}_2) \pm t_{1-\alpha/2,\,n_1+n_2-2} \, s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}$

### Two-Sample t-Test for Means (Independent Samples, Unknown and Unequal Variances — Welch's t-test)

- Test Statistic: $T = \frac{(\bar{X}_1 - \bar{X}_2) - \Delta_0}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}$ with $T \sim t_{df}$, $df = \dfrac{\left(\tfrac{s_1^2}{n_1} + \tfrac{s_2^2}{n_2}\right)^2}{\tfrac{\left(\tfrac{s_1^2}{n_1}\right)^2}{n_1-1} + \tfrac{\left(\tfrac{s_2^2}{n_2}\right)^2}{n_2-1}}$ (round down to nearest integer if needed)
- Acceptance Region:
  - Two-sided: $|T| \leq t_{1-\alpha/2, df}$
  - Upper-tailed: $T \leq t_{1-\alpha, df}$
  - Lower-tailed: $T \geq -t_{1-\alpha, df}$
- P-value: same structure as Z-test but with $t$-CDF $F_t(\cdot)$.
- Confidence Interval for $\mu_1 - \mu_2$ (100(1-$\alpha$)%): $(\bar{X}_1 - \bar{X}_2) \pm t_{1-\alpha/2, df} \sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}$

### Paired t-Test for Means (Dependent Samples)

- Compute differences: $D_i = X_i - Y_i$ for $i=1,\dots,n$ (must have $n_1 = n_2 = n$)
- Sample mean difference: $\bar{D} = \frac{1}{n} \sum D_i$
- Sample variance of differences: $S_D^2 = \frac{1}{n-1} \sum (D_i - \bar{D})^2$
- Hypotheses: $H_0: \mu_D = 0$ (i.e., $\mu_1 = \mu_2$), $H_1:$ one- or two-sided depending on problem.
- Test Statistic: $T = \frac{\bar{D}}{S_D / \sqrt{n}}$, $T \sim t_{n-1}$
- Acceptance Region:
  - Two-sided: $|T| \leq t_{1-\alpha/2, n-1}$
  - Upper-tailed: $T \leq t_{1-\alpha, n-1}$
  - Lower-tailed: $T \geq -t_{1-\alpha, n-1}$
- P-value: same structure as single-sample t-test.
- Confidence Interval for $\mu_D = \mu_1 - \mu_2$ (100(1-$\alpha$)%): $\bar{D} \pm t_{1-\alpha/2, n-1} \cdot \frac{S_D}{\sqrt{n}}$

### Test for Equality of Two Proportions (Large Samples)

- Test Statistic (unpooled): $Z = \frac{\hat{p}_1 - \hat{p}_2}{\sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}}$, $Z \approx N(0,1)$
- Alternative (pooled under $H_0$): $\hat{p}_0 = \frac{n_1 \hat{p}_1 + n_2 \hat{p}_2}{n_1 + n_2}$, $Z = \frac{\hat{p}_1 - \hat{p}_2}{\sqrt{\hat{p}_0(1-\hat{p}_0) \left( \frac{1}{n_1} + \frac{1}{n_2} \right)}}$
- Acceptance Region:
  - Two-sided: $|Z| \leq z_{1-\alpha/2}$
  - Upper-tailed: $Z \leq z_{1-\alpha}$
  - Lower-tailed: $Z \geq -z_{1-\alpha}$
- P-value:
  - Two-sided: $p = 2\,[1 - \Phi(|Z|)]$
  - Upper-tailed: $p = 1 - \Phi(Z)$
  - Lower-tailed: $p = \Phi(Z)$
- Confidence Interval for $p_1 - p_2$ (100(1-$\alpha$)% approximate): $(\hat{p}_1 - \hat{p}_2) \pm z_{1-\alpha/2} \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$

## 6 Distributions

### Uniform Distribution (Discrete)

- PMF: $P(X = k) = \frac{1}{n}$, $k = a, a+1, \dots, a+n-1$
- Expected Value: $E(X) = a + \frac{n-1}{2}$
- Variance: $\text{Var}(X) = \frac{n^2 - 1}{12}$

### Binomial Distribution

- PMF: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$
- Expected Value: $E(X) = np$
- Variance: $\text{Var}(X) = np(1-p)$
