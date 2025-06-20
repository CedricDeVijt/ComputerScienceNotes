## 4.1 Confidence Intervals: Constructing Reliable Parameter Estimates

Confidence intervals (CIs) provide a range of values within which an unknown population parameter is likely to lie, based on sample data. Unlike point estimates, which yield a single value, CIs account for sampling variability by quantifying the uncertainty associated with an estimate. This chapter explores the construction and interpretation of CIs for parameters like means, variances, and proportions, emphasizing their probabilistic nature and practical applications.

### Defining Confidence Intervals

A **confidence interval** is a statistical tool that estimates a population parameter $\theta$ with a specified level of confidence. It is defined as an interval $[L(X_1, \ldots, X_n), R(X_1, \ldots, X_n)]$, where $L$ and $R$ are functions of the sample data $X_1, \ldots, X_n$, such that:

$$
P\left(\theta \in [L(X_1, \ldots, X_n), R(X_1, \ldots, X_n)]\right) = 1 - \alpha
$$

- **Confidence level** ($1 - \alpha$): The probability that the interval contains $\theta$, typically 0.9, 0.95, or 0.99.
- **Significance level** ($\alpha$): The probability that the interval does not contain $\theta$, e.g., 0.05 for a 95% CI.
- CIs are not unique; they can be two-sided or one-sided (left or right), depending on the application.

#### Types of Confidence Intervals

- **Two-sided CI**: Satisfies $P(\theta < L) = P(\theta > R) = \alpha/2$, balancing the error on both sides.
- **Left-sided CI**: Takes the form $[-\infty, R(X_1, \ldots, X_n)]$, focusing on an upper bound.
- **Right-sided CI**: Takes the form $[L(X_1, \ldots, X_n), \infty]$, focusing on a lower bound.

### General Strategy for Constructing Confidence Intervals

Constructing a CI involves transforming a sample statistic into an interval estimate with a desired confidence level. The process leverages the distribution of a function of the estimator and the parameter. The steps are:

1. **Identify a suitable estimator** $T$ for the parameter $\theta$.
2. **Determine the distribution** of a function $h(T, \theta)$, which is independent of $\theta$.
3. **Find quantiles** $a$ and $b$ such that $P(a \leq h(T, \theta) \leq b) = 1 - \alpha$.
4. **Rearrange the inequality** to isolate $\theta$ in the middle, with $T$ in the bounds.

This strategy ensures the CI captures the parameter with the specified probability, accounting for sample variability.

### Confidence Interval for the Mean (Known Variance)

When estimating the mean $\mu$ of a normal distribution $\mathcal{N}(\mu, \sigma^2)$ with **known variance** $\sigma^2$, the sample mean $\bar{X}_n$ is a natural estimator. The CI leverages the normal distribution of the standardized variable.

#### Theoretical Foundation

Given a sample $X_1, \ldots, X_n \sim \mathcal{N}(\mu, \sigma^2)$, the sample mean follows:

$$
\bar{X}_n \sim \mathcal{N}\left(\mu, \frac{\sigma^2}{n}\right)
$$

The standardized variable is:

$$
Z = \frac{\bar{X}_n - \mu}{\sigma / \sqrt{n}} \sim \mathcal{N}(0, 1)
$$

For a 95% CI ($\alpha = 0.05$), the critical value is $z_{1 - \alpha/2} = 1.96$, since:

$$
P(-1.96 \leq Z \leq 1.96) = 0.95
$$

Rearranging gives the CI:

$$
\left[\bar{x}_n - 1.96 \frac{\sigma}{\sqrt{n}}, \bar{x}_n + 1.96 \frac{\sigma}{\sqrt{n}}\right]
$$

#### Example: Mountain Height Estimation

Suppose 16 measurements of a mountain’s height yield $\bar{x} = 3118.5 \, \text{m}$, with a known standard deviation $\sigma = 2 \, \text{m}$. The 95% CI is:

$$
\left[3118.5 - 1.96 \frac{2}{\sqrt{16}}, 3118.5 + 1.96 \frac{2}{\sqrt{16}}\right] = [3117.52 \, \text{m}, 3119.48 \, \text{m}]
$$

This interval suggests that, in 95% of repeated samples, the true mean height lies within this range.

### Confidence Interval for Variance

Estimating the **variance** $\sigma^2$ of a normal distribution $\mathcal{N}(\mu, \sigma^2)$ with unknown $\mu$ and $\sigma$ relies on the sample variance $S^2$. The CI uses the chi-square distribution.

#### Theoretical Foundation

The sample variance is defined as:

$$
S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)^2
$$

It is an unbiased estimator of $\sigma^2$, i.e., $\mathbb{E}[S^2] = \sigma^2$. The distribution of the scaled sample variance is:

$$
\frac{(n-1) S^2}{\sigma^2} \sim \chi_{n-1}^2
$$

For a $(1 - \alpha)$ CI, find quantiles $\chi_{n-1, \alpha/2}^2$ and $\chi_{n-1, 1 - \alpha/2}^2$ such that:

$$
P\left(\chi_{n-1, \alpha/2}^2 \leq \frac{(n-1) S^2}{\sigma^2} \leq \chi_{n-1, 1 - \alpha/2}^2\right) = 1 - \alpha
$$

Rearranging yields the CI for $\sigma^2$:

$$
\left[\frac{(n-1) s^2}{\chi_{n-1, 1 - \alpha/2}^2}, \frac{(n-1) s^2}{\chi_{n-1, \alpha/2}^2}\right]
$$

For the standard deviation $\sigma$, take the square root:

$$
\left[\sqrt{\frac{(n-1) s^2}{\chi_{n-1, 1 - \alpha/2}^2}}, \sqrt{\frac{(n-1) s^2}{\chi_{n-1, \alpha/2}^2}}\right]
$$

#### Example: Soldier Height Variability

For 16 soldiers, the sample variance of height is $s^2 = 5.76 \, \text{cm}^2$. For a 95% CI ($\alpha = 0.05$) with 15 degrees of freedom:

$$
\chi_{15, 0.025}^2 = 6.262, \quad \chi_{15, 0.975}^2 = 27.488
$$

The CI for $\sigma$ is:

$$
\left[\sqrt{\frac{15 \times 5.76}{27.488}}, \sqrt{\frac{15 \times 5.76}{6.262}}\right] = [1.77 \, \text{cm}, 3.72 \, \text{cm}]
$$

This interval is asymmetric around $s$, reflecting the chi-square distribution’s skewness.

### Confidence Interval for the Mean (Unknown Variance)

When both $\mu$ and $\sigma^2$ are unknown, the CI for the mean uses the **t-distribution**, accounting for the uncertainty in estimating $\sigma$ with $S$.

#### Theoretical Foundation

The standardized variable is:

$$
T = \frac{\bar{X}_n - \mu}{S / \sqrt{n}} \sim t_{n-1}
$$

For a $(1 - \alpha)$ CI, use the critical value $t_{n-1, 1 - \alpha/2}$:

$$
P\left(-t_{n-1, 1 - \alpha/2} \leq T \leq t_{n-1, 1 - \alpha/2}\right) = 1 - \alpha
$$

The CI for $\mu$ is:

$$
\left[\bar{x} - t_{n-1, 1 - \alpha/2} \frac{s}{\sqrt{n}}, \bar{x} + t_{n-1, 1 - \alpha/2} \frac{s}{\sqrt{n}}\right]
$$

#### Example: Easter Egg Weights

For 12 Easter eggs, the sample mean weight is $\bar{x} = 177.66 \, \text{g}$, with sample standard deviation $s = 4.774 \, \text{g}$. For a 95% CI ($\alpha = 0.05$) with 11 degrees of freedom, $t_{11, 0.975} = 2.201$. The CI for $\mu$ is:

$$
\left[177.66 - 2.201 \frac{4.774}{\sqrt{12}}, 177.66 + 2.201 \frac{4.774}{\sqrt{12}}\right] = [174.6 \, \text{g}, 180.7 \, \text{g}]
$$

The CI for $\sigma$ is:

$$
\left[\sqrt{\frac{11 \times 22.787}{21.92}}, \sqrt{\frac{11 \times 22.787}{3.816}}\right] = [3.38 \, \text{g}, 8.09 \, \text{g}]
$$

### Confidence Interval for a Proportion

Estimating a population **proportion** $p$ (e.g., success rate) uses the sample proportion $\widehat{P}$. For large samples, the normal approximation applies.

#### Theoretical Foundation

Given a sample $X_1, \ldots, X_n \sim \text{Bernoulli}(p)$, the sample proportion is:

$$
\widehat{P} = \frac{\sum_{i=1}^n X_i}{n}
$$

It is unbiased, with $\mathbb{E}[\widehat{P}] = p$. For $n \geq 30$, $np \geq 5$, and $n(1-p) \geq 5$, the distribution is approximately:

$$
\widehat{P} \approx \mathcal{N}\left(p, \frac{p(1-p)}{n}\right)
$$

Using the estimated standard error $\sqrt{\frac{\widehat{P}(1-\widehat{P})}{n}}$, the standardized variable is:

$$
Z = \frac{\widehat{P} - p}{\sqrt{\frac{\widehat{P}(1-\widehat{P})}{n}}} \approx \mathcal{N}(0, 1)
$$

The CI for $p$ is:

$$
\left[\hat{p} - z_{1 - \alpha/2} \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}, \hat{p} + z_{1 - \alpha/2} \sqrt{\frac{\hat{p}(1 - \hat{p})}{n}}\right]
$$

#### Example: Election Poll

In a poll of 200 voters, 110 support candidate A ($\hat{p} = 0.55$). For a 95% CI ($\alpha = 0.05$), $z_{1 - \alpha/2} = 1.96$. The standard error is:

$$
\sqrt{\frac{0.55 \times 0.45}{200}} = 0.0352
$$

The CI is:

$$
[0.55 - 1.96 \times 0.0352, 0.55 + 1.96 \times 0.0352] = [48.1\%, 61.9\%]
$$

For a 99% CI ($\alpha = 0.01$), $z_{1 - \alpha/2} = 2.576$, yielding:

$$
[45.9\%, 64.1\%]
$$

---

## Key Points to Remember

- **CI Definition → Probability Interpretation**: A $(1 - \alpha)$ CI means that in repeated sampling, 95% of intervals (for $\alpha = 0.05$) contain the true parameter. ★★★★☆
- **Mean (Known Variance) → Normal Distribution**: Use $z_{1 - \alpha/2}$ and $\sigma/\sqrt{n}$ for precise intervals when $\sigma$ is known. ★★★★☆
- **Variance → Chi-Square Distribution**: The CI for $\sigma^2$ is asymmetric due to the chi-square distribution’s shape. ★★★☆☆
- **Mean (Unknown Variance) → t-Distribution**: Accounts for $\sigma$ estimation uncertainty, converging to the normal case as $n \to \infty$. ★★★★☆
- **Proportion → Normal Approximation**: Requires large $n$ and sufficient successes/failures for validity. ★★★☆☆
- **Common Pitfall → Misinterpreting CIs**: A 95% CI does not mean a 95% chance that $\theta$ lies in the interval for a specific sample. ★★★★★
- **Sample Size Effect → Interval Width**: Larger $n$ narrows the CI, while higher confidence widens it. ★★★★☆
