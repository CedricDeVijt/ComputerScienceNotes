## 6.1 Introduction to Variance Comparison

The **F-test** is used to compare the variances of two independent samples from normal distributions, determining if their population variances $\sigma_1^2$ and $\sigma_2^2$ are equal. This test is critical before comparing means, as equal variances are often assumed in subsequent tests. The test statistic is based on the ratio of sample variances, following an F-distribution under the null hypothesis.

## 6.2 Test Setup and Assumptions

Consider two independent samples:

- $X_1, \ldots, X_{n_1} \sim \mathcal{N}(\mu_1, \sigma_1^2)$, with $\mu_1$ and $\sigma_1$ unknown.
- $Y_1, \ldots, Y_{n_2} \sim \mathcal{N}(\mu_2, \sigma_2^2)$, with $\mu_2$ and $\sigma_2$ unknown.

Sample variances are calculated as:

$$
S_1^2 = \frac{1}{n_1-1} \sum_{i=1}^{n_1} (X_i - \bar{X}_{n_1})^2, \quad S_2^2 = \frac{1}{n_2-1} \sum_{j=1}^{n_2} (Y_j - \bar{Y}_{n_2})^2.
$$

The test statistic is:

$$
F = \frac{S_1^2 / \sigma_1^2}{S_2^2 / \sigma_2^2} \sim F_{n_1-1, n_2-1}.
$$

### Null and Alternative Hypotheses

For a two-sided test:

$$
H_0: \sigma_1^2 = \sigma_2^2 \quad \text{vs.} \quad H_1: \sigma_1^2 \neq \sigma_2^2.
$$

Under $H_0$, the test statistic simplifies to:

$$
F = \frac{S_1^2}{S_2^2} \sim F_{n_1-1, n_2-1}.
$$

## 6.3 Confidence Interval for Variance Ratio

A $100(1-\alpha)\%$ confidence interval for $\frac{\sigma_1^2}{\sigma_2^2}$ is:

$$
\left[ \frac{S_1^2}{S_2^2} \frac{1}{F_{n_1-1, n_2-1, 1-\frac{\alpha}{2}}}, \frac{S_1^2}{S_2^2} F_{n_2-1, n_1-1, 1-\frac{\alpha}{2}} \right].
$$

This interval uses the property $F_{n,m,\alpha} = \frac{1}{F_{m,n,1-\alpha}}$ to reduce table lookup.

## 6.4 Two-Sided F-Test Procedure

- Compute the test statistic: $f = \frac{s_1^2}{s_2^2}$.
- The acceptance region is $\left[ F_{n_1-1, n_2-1, \frac{\alpha}{2}}, F_{n_1-1, n_2-1, 1-\frac{\alpha}{2}} \right]$.
- Reject $H_0$ if $f$ lies outside this region.
- The p-value is:
  $$
  p = 2 \min \left\{ F_{n_1-1, n_2-1}(f), 1 - F_{n_1-1, n_2-1}(f) \right\}.
  $$

### One-Sided F-Test

For $H_0: \sigma_1 \leq \sigma_2$ vs. $H_1: \sigma_1 > \sigma_2$:

- Acceptance region: $\left[ 0, F_{n_1-1, n_2-1, 1-\alpha} \right]$.
- P-value: $p = 1 - F_{n_1-1, n_2-1}(f)$.

For $H_0: \sigma_1 \geq \sigma_2$ vs. $H_1: \sigma_1 < \sigma_2$:

- Acceptance region: $\left[ F_{n_1-1, n_2-1, \alpha}, \infty \right)$.
- P-value: $p = F_{n_1-1, n_2-1}(f)$.

### Example: Voltmeter Variability

Two voltmeters are tested for equal variability with $s_1 = 4 \, \mu V$ ($n_1 = 16$), $s_2 = 3 \, \mu V$ ($n_2 = 21$), and $\alpha = 5\%$. The test statistic is:

$$
f = \frac{s_1^2}{s_2^2} = \frac{4^2}{3^2} = 1.777.
$$

Critical values are $F_{15,20,0.975} = 2.57$, $F_{15,20,0.025} = 0.362$. Since $f \in [0.362, 2.57]$, do not reject $H_0$. The p-value is $p = 2 \cdot 0.1142 = 0.2284 > 0.05$, confirming non-significance.

# 6 Comparing Means: Two-Sample T-Tests

## 6.5 Overview of Mean Comparison

Comparing means of two normal populations tests whether $\mu_1 = \mu_2$. The approach differs for **unpaired** (independent) and **paired** data. Unpaired tests assume equal variances (verified via F-test), while paired tests account for dependencies by analyzing differences.

## 6.6 Unpaired Data: Two-Sample T-Test

Assume $\sigma_1 = \sigma_2 = \sigma$ (unknown) and samples:

$$
X_1, \ldots, X_{n_1} \sim \mathcal{N}(\mu_1, \sigma^2), \quad Y_1, \ldots, Y_{n_2} \sim \mathcal{N}(\mu_2, \sigma^2).
$$

The pooled variance is:

$$
\bar{S}^2 = \frac{(n_1-1)S_1^2 + (n_2-1)S_2^2}{n_1 + n_2 - 2}.
$$

The test statistic is:

$$
T = \frac{\bar{X} - \bar{Y}}{\bar{S} \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}} \sim t_{n_1 + n_2 - 2} \quad \text{under } H_0: \mu_1 = \mu_2.
$$

### Confidence Interval for Mean Difference

A $100(1-\alpha)\%$ confidence interval for $\mu_1 - \mu_2$ is:

$$
\left[ \bar{x} - \bar{y} \pm t_{n_1 + n_2 - 2, 1-\frac{\alpha}{2}} \bar{s} \sqrt{\frac{1}{n_1} + \frac{1}{n_2}} \right].
$$

### Two-Sided T-Test

For $H_0: \mu_1 = \mu_2$ vs. $H_1: \mu_1 \neq \mu_2$:

- Acceptance region: $\left[ -t_{n_1 + n_2 - 2, 1-\frac{\alpha}{2}}, t_{n_1 + n_2 - 2, 1-\frac{\alpha}{2}} \right]$.
- P-value: $p = 2 \mathrm{P}_{H_0}(T \geq |t|)$.

### One-Sided T-Test

For $H_0: \mu_1 \leq \mu_2$ vs. $H_1: \mu_1 > \mu_2$:

- Acceptance region: $\left[ -\infty, t_{n_1 + n_2 - 2, 1-\alpha} \right]$.
- P-value: $p = \mathrm{P}_{H_0}(T \geq t)$.

For $H_0: \mu_1 \geq \mu_2$ vs. $H_1: \mu_1 < \mu_2$:

- Acceptance region: $\left[ -t_{n_1 + n_2 - 2, 1-\alpha}, \infty \right)$.
- P-value: $p = \mathrm{P}_{H_0}(T \leq t)$.

### Example: Fertilizer Effect on Grain Yield

A farmer tests if fertilizer increases grain yield with $n_1 = 8$, $\bar{x}_1 = 5.8$ tons, $s_1 = 0.36$ tons, $n_2 = 7$, $\bar{x}_2 = 4.9$ tons, $s_2 = 0.40$ tons, $\alpha = 1\%$. First, an F-test confirms $\sigma_1 = \sigma_2$. The pooled variance is:

$$
\bar{s}^2 = \frac{7 \cdot 0.36^2 + 6 \cdot 0.40^2}{13} = 0.1436, \quad \bar{s} = 0.379.
$$

The test statistic is:

$$
t = \frac{5.8 - 4.9}{0.379 \sqrt{\frac{1}{8} + \frac{1}{7}}} = 4.59.
$$

Since $t > t_{13,0.99} = 2.6503$, reject $H_0$. The p-value is $p = 0.0003 < 0.01$, indicating a significant increase.

## 6.7 Paired Data: Paired T-Test

For paired samples, define $D_i = X_i - Y_i$, where $D_i \sim \mathcal{N}(\mu, \sigma^2)$, $\mu = \mu_1 - \mu_2$. The test reduces to:

$$
H_0: \mu = 0 \quad \text{vs.} \quad H_1: \mu \neq 0.
$$

The test statistic is:

$$
T = \frac{\bar{D}}{S_D / \sqrt{n}} \sim t_{n-1},
$$

where $\bar{D} = \frac{1}{n} \sum D_i$, $S_D^2 = \frac{1}{n-1} \sum (D_i - \bar{D})^2$.

### Example: Gasoline Efficiency

Test if gasoline $Y$ outperforms $X$ using paired data from 10 cars. Differences yield $\bar{d} = -2.8$ km, $s_D = 3.853$ km. For $H_0: \mu \geq 0$ vs. $H_1: \mu < 0$:

$$
t = \frac{-2.8}{3.853 / \sqrt{10}} = -2.298.
$$

At $\alpha = 5\%$, the acceptance region is $[-1.833, \infty)$, so reject $H_0$. At $\alpha = 1\%$, it is $[-2.821, \infty)$, so do not reject. The p-value is $p = 0.0236$, significant at $5\%$ but not $1\%$.

# 6 Comparing Proportions: Z-Test

## 6.8 Introduction to Proportion Comparison

Comparing proportions tests if two population proportions $p_1$ and $p_2$ are equal using sample proportions $\widehat{P}_1$ and $\widehat{P}_2$ from independent Bernoulli experiments.

## 6.9 Test Statistic and Distribution

For large $n_1, n_2$, the test statistic is:

$$
Z = \frac{\widehat{P}_1 - \widehat{P}_2}{\sqrt{\frac{\widehat{p}_1 (1 - \widehat{p}_1)}{n_1} + \frac{\widehat{p}_2 (1 - \widehat{p}_2)}{n_2}}} \approx \mathcal{N}(0,1) \quad \text{under } H_0: p_1 = p_2.
$$

Alternatively, use a pooled proportion:

$$
\widehat{p}_0 = \frac{n_1 \widehat{p}_1 + n_2 \widehat{p}_2}{n_1 + n_2},
$$

with:

$$
Z = \frac{\widehat{P}_1 - \widehat{P}_2}{\sqrt{\widehat{p}_0 (1 - \widehat{p}_0) \left( \frac{1}{n_1} + \frac{1}{n_2} \right)}}.
$$

## 6.10 Confidence Interval for Proportion Difference

A $100(1-\alpha)\%$ confidence interval for $p_1 - p_2$ is:

$$
\left[ (\widehat{p}_1 - \widehat{p}_2) \pm \Phi^{-1}\left(1 - \frac{\alpha}{2}\right) \sqrt{\frac{\widehat{p}_1 (1 - \widehat{p}_1)}{n_1} + \frac{\widehat{p}_2 (1 - \widehat{p}_2)}{n_2}} \right].
$$

## 6.11 Test Procedure

For $H_0: p_1 = p_2$ vs. $H_1: p_1 \neq p_2$:

- Acceptance region: $\left[ -\Phi^{-1}\left(1 - \frac{\alpha}{2}\right), \Phi^{-1}\left(1 - \frac{\alpha}{2}\right) \right]$.
- P-value: $p = 2 \mathrm{P}_{H_0}\left( Z \geq \frac{|\widehat{p}_1 - \widehat{p}_2|}{\sqrt{\frac{\widehat{p}_1 (1 - \widehat{p}_1)}{n_1} + \frac{\widehat{p}_2 (1 - \widehat{p}_2)}{n_2}}} \right)$.

## Key Points to Remember

- **F-Test → Variance Equality**: Tests $\sigma_1^2 = \sigma_2^2$ using $F = \frac{S_1^2}{S_2^2} \sim F_{n_1-1, n_2-1}$. Critical for validating assumptions in mean comparison. ★★★★☆
- **Two-Sample T-Test → Unpaired Means**: Assumes $\sigma_1 = \sigma_2$, uses pooled variance $\bar{S}^2$. Test statistic $T \sim t_{n_1 + n_2 - 2}$. ★★★★☆
- **Paired T-Test → Dependent Means**: Reduces to a single-sample t-test on differences $D_i = X_i - Y_i$. Requires $n_1 = n_2$. ★★★☆☆
- **Z-Test → Proportions**: Uses normal approximation for large samples to compare $p_1 = p_2$. Pooled proportion enhances efficiency under $H_0$. ★★★☆☆
- **Common Pitfall → Variance Assumption**: Always verify $\sigma_1 = \sigma_2$ with an F-test before a two-sample t-test to avoid invalid results. ★★★★★
- **Critical Distinction → Paired vs. Unpaired**: Paired tests control for confounding factors, increasing power but requiring matched data. ★★★★☆
