# 7 Testing Discrete and Continuous Distributions

This chapter explores statistical methods for testing whether observed data follows a specified distribution, focusing on the chi-square test for discrete distributions and both chi-square and Kolmogorov-Smirnov tests for continuous distributions. These methods are crucial for validating hypotheses about data distributions in various applications, such as quality control and social sciences. The content connects the mathematical foundations of these tests with practical examples to enhance understanding and retention.

## 7.1 Chi-Square Test for Discrete Distributions

The **chi-square test** evaluates whether observed data follows a specified discrete distribution defined over a set of $k$ values $\{z_1, \ldots, z_k\}$ with theoretical probabilities $\{p_1, \ldots, p_k\}$. The null hypothesis assumes the data conforms to this distribution, and observed frequencies are compared to expected frequencies to assess fit. This test is widely used when expected frequencies are sufficiently large, linking to the normal approximation for binomial distributions.

### Formulating the Null Hypothesis

The null hypothesis is defined as:

$$
H_0: X_1, \ldots, X_n \sim \text{the specified discrete distribution}.
$$

After collecting $n$ observations, we compute the observed frequencies $N_j$, where $N_j$ is the number of times value $z_j$ appears, and $\sum_{j=1}^k N_j = n$. Under $H_0$, each $N_j$ follows a binomial distribution $B(n, p_j)$, approximated by a Poisson distribution with parameter $\lambda = n p_j$ when $n p_j$ is large, and further approximated by a normal distribution:

$$
\frac{N_j - n p_j}{\sqrt{n p_j}} \approx N(0,1).
$$

This approximation connects to the central limit theorem, ensuring the test’s validity for large samples.

### Chi-Square Test Statistic

The chi-square test statistic aggregates the standardized differences across all categories:

$$
\sum_{j=1}^k \left( \frac{N_j - n p_j}{\sqrt{n p_j}} \right)^2 \approx \chi^2_{k-1},
$$

where the degrees of freedom are $k-1$ due to the constraint $\sum N_j = n$. Alternatively, it can be expressed as:

$$
\sum_{j=1}^k \frac{(N_j - n p_j)^2}{n p_j}.
$$

The test statistic is always non-negative, with smaller values indicating a better fit to the theoretical distribution. The acceptance region for $H_0$ at significance level $\alpha$ is $[0, \chi^2_{k-1, 1-\alpha}]$. For reliable approximation, theoretical frequencies $n p_j$ should be at least 5, which may require grouping categories to ensure sufficient expected counts.

### Example: Uniform Distribution of Book Loans

Consider a librarian testing whether book loans across six days (Monday to Saturday) follow a uniform distribution. With $n=185$ loans and observed frequencies $N_j = \{26, 32, 23, 29, 34, 41\}$, the theoretical probability is $p_j = \frac{1}{6}$, yielding expected frequencies $n p_j = \frac{185}{6} \approx 30.833$. The test statistic is calculated as:

$$
\sum_{j=1}^6 \frac{(N_j - 30.833)^2}{30.833} = 6.578.
$$

For $k=6$, degrees of freedom are $5$. At $\alpha=5\%$, the acceptance region is $[0, 11.070]$, and at $\alpha=1\%$, it is $[0, 15.086]$. Since $6.578$ lies within both regions, $H_0$ is not rejected, suggesting the data is consistent with a uniform distribution. This example illustrates how the chi-square test validates uniformity in real-world data.

### Adjusting for Estimated Parameters

When parameters of the distribution are estimated from the data, the degrees of freedom are reduced by the number of estimated parameters ($v$), resulting in $\chi^2_{k-v-1}$. For example, testing a Poisson distribution with $n=80$ observations and values $z_j = \{0, 1, 2, 3, 4, 5, 6, \geq 7\}$, the parameter $\lambda$ is estimated as $\bar{x} = 2.1$. Grouping into five classes (e.g., $\{0\}, \{1\}, \{2\}, \{3\}, \{4,5,6,\ldots\}$), the test statistic is:

$$
\sum_{j=1}^5 \frac{(n_j - n p_j)^2}{n p_j} \approx 2.11,
$$

with $k-v-1 = 5-1-1 = 3$ degrees of freedom. The acceptance regions $[0, 7.815]$ ($\alpha=5\%$) and $[0, 11.345]$ ($\alpha=1\%$) include $2.11$, so $H_0$ is not rejected. This adjustment ensures the test accounts for parameter estimation, linking to the concept of model fitting.

## 7.2 Chi-Square Test for Continuous Distributions

For continuous distributions, the chi-square test groups data into $k$ classes to compare observed and expected frequencies, adjusting for estimated parameters. This approach is effective when the sample size ensures adequate expected frequencies per class, extending the discrete chi-square framework to continuous data.

### Estimating Parameters and Class Probabilities

Parameters like mean $\mu$ and variance $\sigma^2$ are estimated using class centers $c_j$ and observed frequencies $n_j$. For a normal distribution $N(\mu, \sigma^2)$, probabilities $p_j$ for each class are computed using the cumulative distribution function. For example, with $n=300$ observations across 10 classes, estimates are $\bar{x} = 68.22$ and $s^2 = 79.36$. The probability for class $[49.5, 54.5)$ is:

$$
P[49.5 \leq X < 54.5] = \Phi\left(\frac{54.5 - 68.22}{8.91}\right) - \Phi\left(\frac{49.5 - 68.22}{8.91}\right) \approx 0.044.
$$

The lowest and highest classes are extended to $-\infty$ and $+\infty$ to ensure the sum of probabilities equals 1, connecting to the properties of continuous distributions.

### Test Statistic and Decision

The test statistic is:

$$
\sum_{j=1}^k \frac{(n_j - n p_j)^2}{n p_j},
$$

with $k-v-1$ degrees of freedom, where $v$ is the number of estimated parameters. In the normal distribution example, combining the last two classes yields $k=9$, and with two estimated parameters ($\mu$, $\sigma^2$), degrees of freedom are $6$. The test statistic is $21.64$, exceeding the critical value $12.592$ at $\alpha=5\%$, leading to rejection of $H_0$. This result highlights the importance of sufficient sample sizes and proper class grouping in continuous distribution testing.

## 7.3 Kolmogorov-Smirnov Test for Continuous Distributions

The **Kolmogorov-Smirnov (KS) test** is an exact method for testing whether a sample follows a specific continuous distribution by comparing the empirical distribution function $\hat{F}_n(x)$ to the theoretical distribution function $F_P(x)$. Unlike the chi-square test, it imposes no minimum sample size requirements, making it versatile for smaller datasets.

### Empirical and Theoretical Distribution Functions

The empirical distribution function is defined as:

$$
\hat{F}_n(x) = \frac{1}{n} \sum_{i=1}^n I(X_i \leq x),
$$

where $I$ is the indicator function counting observations less than or equal to $x$. The KS test statistic is the maximum absolute difference:

$$
D = \sup_x |\hat{F}_n(x) - F_P(x)|.
$$

Critical values are obtained from statistical tables, and the test’s exact nature makes it robust for continuous distributions, linking to the concept of distribution-free testing.

---

## Key Points to Remember

- **Chi-Square Test → Discrete Distributions**: Tests fit to a specified discrete distribution using $\sum \frac{(N_j - n p_j)^2}{n p_j} \approx \chi^2_{k-1}$. Requires $n p_j \geq 5$ for reliable approximation. _(High Priority)_ ★★★★★
- **Parameter Estimation → Degrees of Freedom**: Estimating $v$ parameters reduces degrees of freedom to $k-v-1$ in chi-square tests, accounting for model fitting. _(Critical Distinction)_ ★★★★
- **Chi-Square Test → Continuous Distributions**: Groups continuous data into classes, computes probabilities using estimated parameters, and applies the chi-square statistic. _(Common Application)_ ★★★★
- **Kolmogorov-Smirnov Test → Exact Method**: Compares empirical and theoretical distribution functions for continuous distributions, with no sample size constraints, offering a robust alternative to chi-square. _(Key Advantage)_ ★★★★
- **Acceptance Region → Decision Rule**: For chi-square tests, $H_0$ is accepted if the test statistic falls within $[0, \chi^2_{df, 1-\alpha}]$, guiding hypothesis testing decisions. _(Essential Rule)_ ★★★★
- **Practical Consideration → Class Grouping**: Grouping categories or classes ensures $n p_j \geq 5$ in chi-square tests, critical for valid approximations in both discrete and continuous cases. _(Common Pitfall)_ ★★★★
