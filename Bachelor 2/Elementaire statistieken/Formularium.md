## 1 Fundamental Probability Concepts

### Basic Probability Rules

- **Complement rule**: $P(A^c) = 1 - P(A)$
- **Addition rule (mutually exclusive)**: $P(A \cup B) = P(A) + P(B)$
- **Addition rule (general)**: $P(A \cup B) = P(A) + P(B) - P(A \cap B)$
- **Multiplication rule (independent)**: $P(A \cap B) = P(A) \cdot P(B)$
- **Conditional probability**: $P(A|B) = \frac{P(A \cap B)}{P(B)}$

### Expected Value and Variance

- **Expected value (discrete)**: $E[X] = \sum\limits_{i} x_i P(X = x_i)$
- **Expected value (continuous)**: $E[X] = \int\limits_{-\infty}^{\infty} x f(x) dx$
- **Variance definition**: $\text{Var}(X) = E[(X - \mu)^2] = E[X^2] - (E[X])^2$
- **Standard deviation**: $\sigma = \sqrt{\text{Var}(X)}$

### Linear Transformations

- **For $Y = aX + b$**:
  - $E[Y] = aE[X] + b$
  - $\text{Var}(Y) = a^2 \text{Var}(X)$
- **For independent $X$ and $Y$**:
  - $E[X + Y] = E[X] + E[Y]$
  - $\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y)$

## 2 Probability Distributions

### Normal Distribution $N(\mu, \sigma^2)$

- **Mean**: $\mu$
- **Variance**: $\sigma^2$
- **Standard deviation**: $\sigma$
- **PDF**: $f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$

### Standard Normal Distribution $N(0,1)$

- **Mean**: $\mu = 0$, **Variance**: $\sigma^2 = 1$
- **PDF**: $\phi(z) = \frac{1}{\sqrt{2\pi}} e^{-\frac{z^2}{2}}$
- **Z-score (standardization)**: $Z = \frac{X - \mu}{\sigma}$
- **Converting back**: $X = \mu + Z \cdot \sigma$

### Binomial Distribution $X \sim \text{Bin}(n,p)$

- **PMF**: $P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$
- **Mean**: $E[X] = np$
- **Variance**: $\text{Var}(X) = np(1-p)$

### Poisson Distribution $X \sim \text{Poisson}(\lambda)$

- **PMF**: $P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}$
- **Mean**: $E[X] = \lambda$
- **Variance**: $\text{Var}(X) = \lambda$

### Percentiles and Quantiles

- **$p$-th percentile**: Value $x_p$ such that $P(X \leq x_p) = p/100$
- **$q$-th quantile**: Value $x_q$ such that $P(X \leq x_q) = q$
- **For standard normal**: $P(Z \leq z_\alpha) = 1 - \alpha$

## 3 Sampling Distributions and Central Limit Theorem

### Sample Statistics

- **Sample mean**: $\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$
- **Sample variance (unbiased)**: $S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X})^2$
- **Sample standard deviation**: $s = \sqrt{S^2}$

### Properties of Sample Statistics

- **Variance of sample mean**: $\text{Var}(\bar{X}_n) = \frac{\sigma^2}{n}$
- **Sum of i.i.d. variables** $S_n = \sum_{i=1}^n X_i$:
  - $E[S_n] = n\mu$
  - $\text{Var}(S_n) = n\sigma^2$
- **Variance of linear combination** $\hat{\mu} = \sum_{i=1}^n a_i X_i$:
  - $\text{Var}(\hat{\mu}) = \sum_{i=1}^n a_i^2 \sigma^2$

### Central Limit Theorem

- **Distribution of sample mean**: $\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right)$
- **Standardized sample mean**: $Z = \frac{\bar{X} - \mu}{\sigma / \sqrt{n}} \sim N(0,1)$
- **Standardized sum**: $\frac{S_n - n\mu}{\sigma \sqrt{n}} \approx N(0,1)$

## 4 Estimation Theory

### Estimator Properties

- **Bias**: $\text{Bias}(\hat{\theta}) = E[\hat{\theta}] - \theta$
- **Mean Squared Error**: $\text{MSE}(\hat{\theta}) = \text{Var}(\hat{\theta}) + [\text{Bias}(\hat{\theta})]^2$
- **Unbiased condition**: $E[\hat{\theta}] = \theta$

### Common Estimators

- **Binomial proportion**: $\hat{p} = \frac{X}{n}$, where $E[\hat{p}] = p$
- **Unbiased binomial variance**: $\hat{\sigma}^2 = \frac{X(n-X)}{n-1}$
- **Sum of squares expectation**: $E\left[\sum_{i=1}^n (X_i - \bar{X})^2\right] = (n-1)\sigma^2$
- **Chi-squared variance**: $\text{Var}\left(\sum_{i=1}^n (X_i - \bar{X})^2\right) = 2(n-1)\sigma^4$

## 5 Confidence Intervals

### For Population Mean

**Known variance**: $\bar{X} \pm z_{\alpha/2} \cdot \frac{\sigma}{\sqrt{n}}$

**Unknown variance**: $\bar{X} \pm t_{\alpha/2, n-1} \cdot \frac{s}{\sqrt{n}}$

### For Population Variance and Standard Deviation

**Variance**: $\left( \frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}, \frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}} \right)$

**Standard deviation**: $\left( \sqrt{\frac{(n-1)s^2}{\chi^2_{\alpha/2, n-1}}}, \sqrt{\frac{(n-1)s^2}{\chi^2_{1-\alpha/2, n-1}}} \right)$

### For Proportions

**Single proportion**: $\hat{p} \pm z_{\alpha/2} \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$

**Difference of proportions**: $(\hat{p}_1 - \hat{p}_2) \pm z_{\alpha/2} \sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}$

### One-Sided Intervals

**Upper bound**: $\bar{X} + z_\alpha \cdot \frac{\sigma}{\sqrt{n}}$ or $\bar{X} + t_{\alpha, n-1} \cdot \frac{s}{\sqrt{n}}$

## 6 Sample Size Determination

### For Mean Estimation

**Margin of error $E$**: $n = \left( \frac{z_{\alpha/2} \cdot \sigma}{E} \right)^2$

### For Proportion Estimation

**Given standard error**: $n = \frac{\hat{p}(1-\hat{p})}{(\text{SE})^2}$

**Maximum standard error** (at $p = 0.5$): $\text{SE}_{\text{max}} = \frac{0.5}{\sqrt{n}}$

### For Hypothesis Testing

**Power analysis**: $n = \left( \frac{(z_{\alpha} + z_{\beta}) \sigma}{\mu_1 - \mu_0} \right)^2$

## 7 Hypothesis Testing

### One-Sample Tests

#### Z-Test for Mean (Known Variance)

- **Test statistic**: $Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}} \sim N(0,1)$ under $H_0$
- **Acceptance region (two-sided)**: $[-z_{\alpha/2}, z_{\alpha/2}]$

#### T-Test for Mean (Unknown Variance)

- **Test statistic**: $T = \frac{\bar{X} - \mu_0}{s / \sqrt{n}} \sim t_{n-1}$ under $H_0$
- **Acceptance region (two-sided)**: $[-t_{\alpha/2, n-1}, t_{\alpha/2, n-1}]$

#### Chi-Squared Test for Variance

- **Test statistic**: $\chi^2 = \frac{(n-1)s^2}{\sigma_0^2} \sim \chi^2_{n-1}$ under $H_0: \sigma^2 = \sigma_0^2$

#### Proportion Test

- **Test statistic**: $Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}} \sim N(0,1)$ under $H_0$

### Two-Sample Tests

#### Two-Sample Z-Test (Known Variances)

$$Z = \frac{\bar{X} - \bar{Y} - (\mu_1 - \mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}} \sim N(0,1) \text{ under } H_0$$

#### Two-Sample T-Test (Equal Variances)

- **Pooled variance**: $s_p^2 = \frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1 + n_2 - 2}$
- **Test statistic**: $T = \frac{\bar{X} - \bar{Y}}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim t_{n_1 + n_2 - 2}$ under $H_0$

#### Paired T-Test

- **Differences**: $D_i = X_i - Y_i$
- **Sample mean**: $\bar{D} = \frac{1}{n} \sum_{i=1}^n D_i$
- **Sample variance**: $s_D^2 = \frac{1}{n-1} \sum_{i=1}^n (D_i - \bar{D})^2$
- **Test statistic**: $T = \frac{\bar{D}}{s_D / \sqrt{n}} \sim t_{n-1}$ under $H_0: \mu_D = 0$

### P-Values and Error Analysis

- **Two-sided**: $p = 2 \cdot P(|Z| > |z_{obs}|)$ or $p = 2 \cdot P(|T| > |t_{obs}|)$
- **One-sided (right)**: $p = P(Z > z_{obs})$ or $p = P(T > t_{obs})$
- **One-sided (left)**: $p = P(Z < z_{obs})$ or $p = P(T < t_{obs})$

### Error Types and Power

- **Type I error**: $\alpha = P(\text{reject } H_0 \mid H_0 \text{ true})$
- **Type II error**: $\beta = P(\text{accept } H_0 \mid H_1 \text{ true})$
- **Power**: $1 - \beta = P(\text{reject } H_0 \mid H_1 \text{ true})$

## 8 Goodness of Fit and Independence Tests

### Chi-Squared Goodness of Fit

- **Test statistic**: $\chi^2 = \sum_{i=1}^k \frac{(O_i - E_i)^2}{E_i}$
- **Degrees of freedom**:
  - No parameters estimated: $df = k - 1$
  - $m$ parameters estimated: $df = k - 1 - m$

### Chi-Square Test of Independence

- **Test statistic**: $\chi^2 = \sum_{i,j} \frac{(O_{ij} - E_{ij})^2}{E_{ij}}$
- **Expected frequencies**: $E_{ij} = \frac{(\text{row total})_i \times (\text{column total})_j}{n}$
- **Degrees of freedom**: $df = (r-1)(c-1)$

### Distribution-Specific Tests

#### Uniform Distribution

- **Expected frequencies**: $E_i = \frac{n}{k}$ for $k$ categories

#### Binomial Distribution

- **Expected frequencies**: $E_i = n \cdot \binom{n}{i} p^i (1-p)^{n-i}$

#### Poisson Distribution

- **Parameter estimate**: $\hat{\lambda} = \bar{x}$
- **Expected frequencies**: $E_i = n \cdot \frac{\lambda^i e^{-\lambda}}{i!}$

### Exact Tests

#### Exact Binomial Test

- **P-value (one-sided)**: $p = \sum_{k \geq x_{obs}} \binom{n}{k} p_0^k (1-p_0)^{n-k}$

## 9 Correlation and Regression

### Correlation

- **Pearson correlation coefficient**:
  $$r = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^n (x_i - \bar{x})^2 \sum_{i=1}^n (y_i - \bar{y})^2}}$$

### Simple Linear Regression

- **Model**: $y = a + bx + \epsilon$
- **Slope**: $b = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2}$
- **Intercept**: $a = \bar{y} - b\bar{x}$
- **Coefficient of determination**: $R^2 = r^2$

## 10 Special Formulas and Applications

### Distribution-Specific Properties

- **Standard error for proportion**: $\text{SE} = \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}$
- **Maximum SE for proportion** (at $p = 0.5$): $\text{SE}_{\text{max}} = \frac{0.5}{\sqrt{n}}$

### Critical Value Applications

- **Finding threshold $L$** for $P(\bar{X} > L) = \alpha$:
  $$L = \mu + z_{1-\alpha} \cdot \frac{\sigma}{\sqrt{n}}$$

### Optimization in Statistics

- **Unbiased linear combination**: For $W = aX + bY$ to be unbiased for $\mu$:
  $$E[W] = \mu \implies a + b = 1$$
- **Variance minimization**: Take derivative with respect to parameter, set to zero, solve

## 11 Distribution Tables Reference

### Critical Values

- **Standard Normal**: $z_{\alpha/2}$ (two-sided), $z_{\alpha}$ (one-sided)
- **t-Distribution**: $t_{\alpha/2, df}$ (two-sided), $t_{\alpha, df}$ (one-sided)
- **Chi-Squared**: $\chi^2_{\alpha/2, df}$ and $\chi^2_{1-\alpha/2, df}$ (intervals), $\chi^2_{\alpha, df}$ (tests)

### Common Significance Levels

- **90% confidence**: $\alpha = 0.10$, $z_{0.05} = 1.645$
- **95% confidence**: $\alpha = 0.05$, $z_{0.025} = 1.96$
- **99% confidence**: $\alpha = 0.01$, $z_{0.005} = 2.576$
