## 5.1 Introduction to Hypothesis Testing

Hypothesis testing is a statistical method used to make decisions about population parameters based on sample data. It involves formulating two opposing hypotheses, the null hypothesis ($H_0$) and the alternative hypothesis ($H_1$), and using sample evidence to decide whether to reject $H_0$. This process is critical in fields like science and industry to evaluate claims, such as whether a new product outperforms an existing one or if environmental standards are met. The method accounts for sampling variability, ensuring decisions are statistically robust.

### Formulating Hypotheses

Hypotheses are statements about population parameters that frame a decision problem. The **null hypothesis** ($H_0$) represents the default or conservative assumption, while the **alternative hypothesis** ($H_1$) represents the claim to be tested. These hypotheses are mutually exclusive, and the goal is to determine whether sample data provides sufficient evidence to reject $H_0$ in favor of $H_1$.

- **Key Idea**: $H_0$ is typically the status quo (e.g., $\mu = \mu_0$), while $H_1$ reflects the research question (e.g., $\mu \neq \mu_0$).
- **Example**: To test if a battery lasts longer than a competitor’s, set $H_0: \mu \leq \mu_0$ and $H_1: \mu > \mu_0$, where $\mu_0$ is the competitor’s mean duration.

#### Types of Hypotheses

1. **One-sided test**: $H_1$ specifies a direction (e.g., $\mu > \mu_0$ or $\mu < \mu_0$).
2. **Two-sided test**: $H_1$ indicates a difference without direction (e.g., $\mu \neq \mu_0$).

**Practical Note**: The choice of $H_0$ and $H_1$ depends on the research question and the consequences of errors, with $H_0$ often reflecting the more critical assumption to avoid falsely rejecting.

### Steps in Hypothesis Testing

The hypothesis testing process follows four structured steps to ensure a systematic approach to decision-making. These steps guide the researcher from hypothesis formulation to interpreting results while controlling for errors.

1. **Define Hypotheses**: Clearly state $H_0$ and $H_1$ based on the parameter of interest.
2. **Select Test Statistic**: Choose a statistic ($T$) calculable from the sample, with a known distribution under $H_0$.
3. **Set Decision Criterion**: Use a **significance level** ($\alpha$) to define the **acceptance region** and **rejection region**. Reject $H_0$ if the test statistic falls in the rejection region.
4. **Evaluate Errors**: Consider the risks of **Type-I error** (rejecting $H_0$ when true, probability $\alpha$) and **Type-II error** (failing to reject $H_0$ when false, probability $\beta$).

- **Connection**: The significance level $\alpha$ links to confidence intervals, as both reflect the probability of error in statistical inference.

#### Error Types and Their Implications

1. **Type-I Error**: Incorrectly rejecting $H_0$ when it is true (probability = $\alpha$).
2. **Type-II Error**: Failing to reject $H_0$ when $H_1$ is true (probability = $\beta$).

- **Power of the Test**: Defined as $1 - \beta$, it measures the test’s ability to detect a true alternative hypothesis.
- **Example**: In testing whether a medicine is effective ($H_1$), a Type-I error might lead to investing in an ineffective drug, while a Type-II error might miss a beneficial treatment.

| Decision            | $H_0$ True              | $H_0$ False             |
| ------------------- | ----------------------- | ----------------------- |
| Reject $H_0$        | Type-I Error ($\alpha$) | Correct ($1 - \beta$)   |
| Do Not Reject $H_0$ | Correct ($1 - \alpha$)  | Type-II Error ($\beta$) |

## 5.2 Testing the Mean of a Normal Distribution with Known Variance

This section focuses on testing the mean ($\mu$) of a normally distributed population with known variance ($\sigma^2$). The **z-test** is used due to the known variance, leveraging the standard normal distribution for decision-making.

### Two-Sided z-Test

The two-sided z-test evaluates whether the population mean differs from a specific value ($\mu_0$). Hypotheses are:

$$
\begin{cases}
H_0: \mu = \mu_0 \\
H_1: \mu \neq \mu_0
\end{cases}
$$

The test statistic is:

$$
Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}} \sim \mathcal{N}(0,1) \text{ under } H_0
$$

where $\bar{X}$ is the sample mean and $n$ is the sample size. The **acceptance region** is $[-z_{1-\alpha/2}, z_{1-\alpha/2}]$, and $H_0$ is rejected if $|Z|$ falls outside this interval.

- **Decision Rule**: Reject $H_0$ if $|Z| > z_{1-\alpha/2}$; otherwise, do not reject.
- **Connection**: The test is equivalent to checking if $\mu_0$ lies within the $(1-\alpha)$ confidence interval for $\mu$.

#### p-Value for Two-Sided z-Test

The **p-value** measures the probability of observing a test statistic as extreme as the one calculated, under $H_0$. For a two-sided test:

$$
p = 2 \cdot \mathrm{P}(Z \geq |z|) \text{ where } z = \frac{\bar{x} - \mu_0}{\sigma / \sqrt{n}}
$$

Reject $H_0$ if $p < \alpha$.

- **Example**: If $z = 2.5$ and $\alpha = 0.05$, then $p = 2 \cdot \mathrm{P}(Z \geq 2.5) \approx 0.0124$, leading to rejection of $H_0$.

### One-Sided z-Test

For a one-sided test, the alternative hypothesis specifies a direction. For example:

$$
\begin{cases}
H_0: \mu \leq \mu_0 \\
H_1: \mu > \mu_0
\end{cases}
$$

The test statistic remains $Z = \frac{\bar{X} - \mu_0}{\sigma / \sqrt{n}}$. The acceptance region is $(-\infty, z_{1-\alpha}]$, and $H_0$ is rejected if $Z > z_{1-\alpha}$.

- **p-Value**: For $H_1: \mu > \mu_0$, $p = \mathrm{P}(Z \geq z)$; for $H_1: \mu < \mu_0$, $p = \mathrm{P}(Z \leq z)$.
- **Practical Note**: One-sided tests are used when the research question focuses on a specific direction of difference (e.g., testing if a new battery lasts longer).

## 5.3 Testing the Mean of a Normal Distribution with Unknown Variance

When the variance ($\sigma^2$) is unknown, the **t-test** replaces the z-test, using the sample standard deviation ($s$) and the t-distribution with $n-1$ degrees of freedom.

### Two-Sided t-Test

Hypotheses are:

$$
\begin{cases}
H_0: \mu = \mu_0 \\
H_1: \mu \neq \mu_0
\end{cases}
$$

The test statistic is:

$$
T = \frac{\bar{X} - \mu_0}{S / \sqrt{n}} \sim t_{n-1} \text{ under } H_0
$$

The acceptance region is $[-t_{n-1,1-\alpha/2}, t_{n-1,1-\alpha/2}]$, and $H_0$ is rejected if $|T|$ falls outside this interval.

- **p-Value**: $p = 2 \cdot \mathrm{P}_{H_0}(T \geq |t|)$.
- **Example**: For a steel plate thickness test with $\bar{x} = 0.53 \, \text{mm}$, $\mu_0 = 0.5 \, \text{mm}$, $s = 0.03 \, \text{mm}$, $n = 10$, and $\alpha = 0.05$, calculate:
  $$
  t = \frac{0.53 - 0.5}{0.03 / \sqrt{10}} = 3.162
  $$
  Since $t_{9,0.975} = 2.262$, and $3.162 > 2.262$, reject $H_0$. The p-value is $p = 2 \cdot \mathrm{P}(T \geq 3.162) = 0.0115$, confirming rejection at $\alpha = 0.05$ but not at $\alpha = 0.01$.

### One-Sided t-Test

For hypotheses like:

$$
\begin{cases}
H_0: \mu \geq \mu_0 \\
H_1: \mu < \mu_0
\end{cases}
$$

The test statistic is the same, but the acceptance region is $[-t_{n-1,1-\alpha}, +\infty)$. Reject $H_0$ if $T < -t_{n-1,1-\alpha}$.

- **p-Value**: For $H_1: \mu < \mu_0$, $p = \mathrm{P}_{H_0}(T \leq t)$.
- **Example**: Testing rope breaking strength with $\bar{x} = 7750 \, \text{kg}$, $\mu_0 = 8000 \, \text{kg}$, $s = 145 \, \text{kg}$, $n = 6$, and $\alpha = 0.05$:
  $$
  t = \frac{7750 - 8000}{145 / \sqrt{6}} = -4.223
  $$
  Since $-4.223 < -t_{5,0.95} = -2.015$, reject $H_0$. The p-value is $p = \mathrm{P}(T \leq -4.223) = 0.0042$, indicating strong evidence against the manufacturer’s claim.

## 5.4 Testing the Variance of a Normal Distribution

When testing the variance ($\sigma^2$) of a normal distribution, the **chi-square test** is used, leveraging the chi-square distribution.

### Two-Sided Chi-Square Test

Hypotheses are:

$$
\begin{cases}
H_0: \sigma^2 = \sigma_0^2 \\
H_1: \sigma^2 \neq \sigma_0^2
\end{cases}
$$

The test statistic is:

$$
X^2 = \frac{(n-1)S^2}{\sigma_0^2} \sim \chi_{n-1}^2 \text{ under } H_0
$$

The acceptance region is $[\chi_{n-1,\alpha/2}^2, \chi_{n-1,1-\alpha/2}^2]$, and $H_0$ is rejected if $X^2$ falls outside this interval.

- **p-Value**: $p = 2 \cdot \min\{\mathrm{P}_{H_0}(X^2 \geq \chi^2), \mathrm{P}_{H_0}(X^2 \leq \chi^2)\}$.

### One-Sided Chi-Square Test

For testing if the variance is larger:

$$
\begin{cases}
H_0: \sigma^2 \leq \sigma_0^2 \\
H_1: \sigma^2 > \sigma_0^2
\end{cases}
$$

The acceptance region is $[0, \chi_{n-1,1-\alpha}^2]$, and $H_0$ is rejected if $\chi^2 > \chi_{n-1,1-\alpha}^2$.

- **p-Value**: $p = \mathrm{P}_{H_0}(X^2 \geq \chi^2)$.
- **Example**: For canned vegetable weights with $s = 3.2 \, \text{g}$, $\sigma_0 = 2.5 \, \text{g}$, $n = 20$, and $\alpha = 0.05$:
  $$
  \chi^2 = \frac{19 \cdot (3.2)^2}{(2.5)^2} = 31.13
  $$
  Since $\chi_{19,0.95}^2 = 30.144$, and $31.13 > 30.144$, reject $H_0$ at $\alpha = 0.05$. The p-value is $p = \mathrm{P}(X^2 \geq 31.13) = 0.0391$, confirming the result.

## 5.5 Testing Proportions

Testing proportions involves evaluating the population proportion ($p$) using either an approximate z-test for large samples or an exact binomial test for small samples.

### Approximate z-Test for Large Samples

For large samples ($n \geq 30$, $np \geq 5$, $n(1-p) \geq 5$), the test statistic is:

$$
Z = \frac{\widehat{P} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}} \approx \mathcal{N}(0,1) \text{ under } H_0: p = p_0
$$

The acceptance region for a two-sided test is $[-z_{1-\alpha/2}, z_{1-\alpha/2}]$.

- **p-Value**: For a two-sided test, $p = 2 \cdot \mathrm{P}_{H_0}(Z \geq |z|)$.
- **Example**: Testing if $p > 0.5$ with $\widehat{p} = 0.833$, $n = 60$, and $\alpha = 0.05$:
  $$
  z = \frac{0.833 - 0.5}{\sqrt{\frac{0.5 \cdot 0.5}{60}}} = 5.16
  $$
  Since $5.16 > z_{0.95} = 1.64$, reject $H_0$. The p-value is $\mathrm{P}(Z \geq 5.16) \approx 0$, confirming rejection.

### Exact Test for Small Samples

For small samples, use the binomial distribution with test statistic $n\widehat{P} \sim \mathcal{B}(n, p_0)$. Calculate the p-value directly from the binomial probabilities.

- **Example**: Testing $p = 0.65$ with $n = 14$, 7 successes, and $\alpha = 0.05$:
  $$
  p = \mathrm{P}(|n\widehat{P} - 9.1| \geq |7 - 9.1|) = 0.0839 + 0.1836 = 0.2675
  $$
  Since $p > 0.05$, do not reject $H_0$.

## 5.6 Assessing Normality

Many tests assume normality, which must be verified, especially for small samples. The **normal QQ-plot** and **correlation coefficient** ($r_Q$) are used to test normality.

### Testing Normality with QQ-Plots

A normal QQ-plot compares sample quantiles to theoretical normal quantiles. If points form a straight line, normality is supported. The correlation coefficient $r_Q$ quantifies this linearity, with values close to 1 indicating normality.

- **Test Hypotheses**:
  $$
  \begin{cases}
  H_0: \text{Data are normally distributed} \\
  H_1: \text{Data are not normally distributed}
  \end{cases}
  $$
- **Decision Rule**: Reject $H_0$ if $r_Q$ is below the critical value for the given $n$ and $\alpha$ (e.g., for $n=10$, $\alpha=0.05$, critical value = 0.918).
- **Example**: For $n=20$, if $r_Q = 0.940 < 0.950$, reject normality at $\alpha=0.05$.

#### Handling Non-Normal Data

If data are not normal, consider transformations (e.g., logarithmic) to achieve normality, or use non-parametric tests like the Wilcoxon or Mann-Whitney test.

---

## Key Points to Remember

- **Hypothesis Formulation → Choose Conservative $H_0$**: Always set $H_0$ as the default assumption to minimize Type-I errors. ★★★★☆
- **Test Statistic → Match Distribution**: Use z-test for known variance, t-test for unknown variance, and chi-square for variance tests. ★★★★★
- **p-Value → Interpret Evidence Strength**: A smaller p-value indicates stronger evidence against $H_0$. ★★★★★
- **Error Control → Balance $\alpha$ and $\beta$**: Choose $\alpha$ (e.g., 0.05) to limit Type-I errors, but larger samples reduce $\beta$. ★★★★☆
- **Normality Check → Use QQ-Plots**: Verify normality with QQ-plots and $r_Q$ before applying parametric tests. ★★★★☆
- **Proportions → Sample Size Matters**: Use z-tests for large samples and exact binomial tests for small samples. ★★★★☆
