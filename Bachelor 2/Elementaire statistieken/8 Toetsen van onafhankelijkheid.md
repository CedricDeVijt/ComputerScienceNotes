## 8.1 Testing Independence of Variables

This chapter explores methods for testing the independence of two variables, either discrete or continuous, using statistical techniques such as the chi-square test for discrete variables and correlation analysis for continuous variables. The content emphasizes constructing contingency tables, calculating theoretical frequencies, and applying statistical tests to determine whether variables are independent. These methods are critical for analyzing relationships in categorical and numerical data, ensuring robust statistical inference.

### Testing Independence of Discrete Variables

The independence of discrete variables is tested using a chi-square test based on a contingency table, which organizes observed frequencies of paired categorical variables. The null hypothesis ($H_0$) assumes that the variables are independent, meaning the joint probability equals the product of marginal probabilities. The test compares observed frequencies to expected (theoretical) frequencies under independence, using the chi-square statistic to assess significance.

#### Constructing the Contingency Table

A contingency table organizes data into rows and columns representing the categories of two discrete variables, $X$ and $Y$, with $r$ and $k$ categories, respectively. Observed frequencies $N_{lj}$ represent the count of occurrences where $X_i = l$ and $Y_i = j$. Marginal frequencies ($N_{l.}$ and $N_{.j}$) are the row and column totals, summing to the total sample size $n$.

- **Example**: For $X$ (man/woman, $r=2$) and $Y$ (hair color: blond/brunette/black, $k=3$), the table has $2 \times 3$ cells with observed frequencies like $N_{11}$ (men with blond hair).
- **Marginal probabilities**: Estimated as $\hat{p}_{l.} = \frac{N_{l.}}{n}$ for $X = l$ and $\hat{p}_{.j} = \frac{N_{.j}}{n}$ for $Y = j$.

#### Calculating Theoretical Frequencies

Under the null hypothesis of independence, the joint probability is $p_{lj} = p_{l.} \cdot p_{.j}$. The theoretical frequency for each cell is computed as:

$$
n \hat{p}_{lj} = n \cdot \hat{p}_{l.} \cdot \hat{p}_{.j} = \frac{N_{l.} N_{.j}}{n}
$$

These form a theoretical contingency table with the same marginal totals as the observed table, allowing comparison between observed and expected frequencies.

#### Chi-Square Test Statistic

The chi-square test statistic measures the discrepancy between observed ($N_{lj}$) and theoretical ($\frac{N_{l.} N_{.j}}{n}$) frequencies:

$$
\sum_{l=1}^r \sum_{j=1}^k \frac{\left( N_{lj} - \frac{N_{l.} N_{.j}}{n} \right)^2}{\frac{N_{l.} N_{.j}}{n}} \approx \chi^2_{(r-1)(k-1)} \quad | H_0
$$

The degrees of freedom are $(r-1)(k-1)$, accounting for the number of estimated parameters ($r-1$ for $X$, $k-1$ for $Y$). The test assumes theoretical frequencies $\frac{N_{l.} N_{.j}}{n} \geq 5$; otherwise, categories must be regrouped to meet this condition.

#### Example: Alcohol Consumption and Exam Results

A study of 870 students examined the relationship between alcohol consumption ($X$: regular/sometimes/never) and exam results ($Y$: pass/fail). The contingency table showed observed frequencies, and theoretical frequencies were calculated (e.g., for regular drinkers who failed: $\frac{105 \cdot 440}{870} = 53.1$). The chi-square statistic was 22.33, with 2 degrees of freedom. At $\alpha = 5\%$, the critical value is 5.991, and at $\alpha = 1\%$, it is 9.210. Since 22.33 exceeds both, $H_0$ is rejected, indicating dependence. Notably, occasional drinkers had a higher pass rate (53%) compared to regular (33%) or never (32%) drinkers.

#### Properties and Considerations

- **Invariance**: The chi-square test is invariant to permutations of $X$ and $Y$ or changes in category coding.
- **2x2 Tables**: Rejection of independence implies a positive or negative relationship, e.g., if $N_{11} > \frac{N_{1.} N_{.1}}{n}$, then $N_{22} > \frac{N_{2.} N_{.2}}{n}$.
- **Extensions**: For three variables ($X, Y, Z$), a three-dimensional contingency table with $(r-1)(k-1)(h-1)$ degrees of freedom can test joint independence.

### Testing Independence of Continuous Variables

For continuous variables, independence is tested by examining the correlation coefficient, which measures linear dependence. If the correlation is zero, the variables are independent under normality assumptions, though zero correlation does not always imply independence. This approach uses sample statistics like means, variances, and covariances to estimate population parameters.

#### Estimating Key Characteristics

From a sample $\{(X_1, Y_1), \ldots, (X_n, Y_n)\}$, unbiased estimators are calculated:

- **Mean**: $\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$, $\bar{Y}_n = \frac{1}{n} \sum_{i=1}^n Y_i$
- **Variance**: $S_X^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)^2$, $S_Y^2 = \frac{1}{n-1} \sum_{i=1}^n (Y_i - \bar{Y}_n)^2$
- **Covariance**: $S_{XY} = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)(Y_i - \bar{Y}_n)$

The covariance measures the joint variability of $X$ and $Y$, with properties like $\text{Cov}[X, Y] = \text{Cov}[Y, X]$ and $\text{Cov}[aX+b, cY+d] = ac \cdot \text{Cov}[X, Y]$.

#### Correlation Coefficient

The Pearson correlation coefficient normalizes covariance to be unitless and invariant to linear transformations:

$$
R_{XY} = \frac{S_{XY}}{\sqrt{S_X^2 S_Y^2}} = \frac{\sum_{i=1}^n (X_i - \bar{X}_n)(Y_i - \bar{Y}_n)}{\sqrt{\sum_{i=1}^n (X_i - \bar{X}_n)^2} \sqrt{\sum_{i=1}^n (Y_i - \bar{Y}_n)^2}}
$$

- **Range**: $-1 \leq R_{XY} \leq 1$, where $R_{XY} = \pm 1$ indicates a perfect linear relationship, and $R_{XY} = 0$ suggests no linear relationship.
- **Properties**: $\text{Corr}[X, X] = 1$, $\text{Corr}[X, Y] = \text{Corr}[Y, X]$, and $\text{Corr}[aX+b, cY+d] = \text{Corr}[X, Y]$ for $a, c > 0$.
- **Limitation**: If $X$ and $Y$ are independent, $\text{Corr}[X, Y] = 0$, but the converse is not true (e.g., $Y = X^2$ has $\text{Cov}[X, Y] = 0$ but is dependent).

#### Visualizing Correlation

The correlation coefficient reflects the shape of the scatterplot of $(X_i, Y_i)$:

- $R_{XY} = 1$: Points lie on a straight line with a positive slope.
- $R_{XY} = -1$: Points lie on a straight line with a negative slope.
- $R_{XY} \approx 0.5$: A positive trend, where higher $X_i$ corresponds to higher $Y_i$.
- $R_{XY} \approx 0$: No clear linear pattern; for normal variables, the scatterplot is spherical or ellipsoidal if independent.

#### Hypothesis Testing for Correlation

Assuming $X_i \sim N(\mu_1, \sigma_1^2)$ and $Y_i \sim N(\mu_2, \sigma_2^2)$, the null hypothesis is $H_0: \text{Corr}[X, Y] = 0$. The test statistic is:

$$
\frac{R_{XY}}{\sqrt{\frac{1 - R_{XY}^2}{n-2}}} \sim t_{n-2} \quad | H_0
$$

- **Two-sided test**: $H_1: \text{Corr}[X, Y] \neq 0$, with acceptance region $[-t_{n-2, 1-\alpha/2}, t_{n-2, 1-\alpha/2}]$.
- **One-sided test**: $H_1: \text{Corr}[X, Y] > 0$, with acceptance region $[-\infty, t_{n-2, 1-\alpha}]$.

#### Example: Maternal Weight Gain and Newborn Weight

A sample of 30 mothers showed a correlation of $R_{XY} = 0.47$ between maternal weight gain and newborn weight. The test statistic for a one-sided test ($H_1: \text{Corr}[X, Y] > 0$) at $\alpha = 5\%$ is:

$$
\frac{0.47}{\sqrt{\frac{1 - 0.47^2}{28}}} = 2.818
$$

The critical value is $t_{28, 0.95} = 1.701$. Since $2.818 > 1.701$, $H_0$ is rejected, confirming a significant positive linear relationship.

---

## Key Points to Remember

- **Discrete Variables → Chi-Square Test**: Use contingency tables to compute observed and theoretical frequencies, with the chi-square statistic $\sum \frac{(N_{lj} - \frac{N_{l.} N_{.j}}{n})^2}{\frac{N_{l.} N_{.j}}{n}}$ following a $\chi^2_{(r-1)(k-1)}$ distribution under $H_0$. ★★★★☆
- **Theoretical Frequencies → Minimum Threshold**: Ensure $\frac{N_{l.} N_{.j}}{n} \geq 5$ for valid chi-square approximation; regroup categories if needed. ★★★☆☆
- **Continuous Variables → Correlation Coefficient**: The Pearson correlation $R_{XY}$ measures linear dependence, ranging from $-1$ to $1$, and is invariant to linear transformations. ★★★★☆
- **Correlation Test → Normality Assumption**: The test $\frac{R_{XY}}{\sqrt{\frac{1 - R_{XY}^2}{n-2}}} \sim t_{n-2}$ assumes $X$ and $Y$ are normally distributed. ★★★☆☆
- **Common Pitfall → Correlation vs. Independence**: Zero correlation implies independence only for normally distributed variables; non-linear dependencies may exist otherwise. ★★★★☆
- **Degrees of Freedom → Contingency Tables**: For discrete variables, degrees of freedom are $(r-1)(k-1)$, reflecting constraints from marginal probabilities. ★★★☆☆
