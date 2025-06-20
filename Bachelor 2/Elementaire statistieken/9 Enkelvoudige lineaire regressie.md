## 9.1 Understanding Simple Linear Regression

Simple linear regression is a statistical method used to model the relationship between a **dependent variable** (response) and an **independent variable** (predictor) by fitting a linear equation to observed data. This chapter introduces the core concepts of the linear model, parameter estimation, and hypothesis testing, enabling students to predict outcomes and assess model fit. It connects the mathematical formulation to practical applications, such as forecasting business losses or housing taxes, ensuring a clear understanding of how data drives decision-making.

### The Linear Regression Model

The **simple linear regression model** assumes a linear relationship between a predictor variable $x_i$ and a response variable $Y_i$, expressed as $Y_i = \alpha + \beta x_i + \varepsilon_i$. Here, $\alpha$ is the **intercept**, $\beta$ is the **slope**, and $\varepsilon_i$ represents random **errors**, which are independent and normally distributed with mean 0 and constant variance $\sigma_{\varepsilon}^2$ (homoscedasticity). The model assumes $x_i$ values are fixed or experimentally chosen, with no measurement error, and $Y_i$ depends on $x_i$. This framework allows us to predict the expected value of $Y_i$, given by $E(Y_i | x_i) = \alpha + \beta x_i$, and understand variability through $\text{Var}(Y_i | x_i) = \sigma_{\varepsilon}^2$.

#### Key Assumptions of the Model

- **Linearity**: The relationship between $x_i$ and $Y_i$ is linear, with $\alpha + \beta x_i$ as the expected value.
- **Homoscedasticity**: The variance of errors $\varepsilon_i$ is constant ($\sigma_{\varepsilon}^2$) across all $x_i$.
- **Normality**: Errors $\varepsilon_i \sim N(0, \sigma_{\varepsilon}^2)$, ensuring statistical tests are valid.
- **Independence**: Observations $Y_i$ are independent of each other.

#### Practical Interpretation

The **intercept** $\alpha$ represents the expected value of $Y$ when $x = 0$, i.e., $E(Y | 0) = \alpha$. The **slope** $\beta$ indicates the change in the expected value of $Y$ for a one-unit increase in $x$, as $E(Y | x+1) - E(Y | x) = \beta$. For example, in a dataset of company losses over months, a negative slope suggests decreasing losses over time, aiding in forecasting.

### Estimating Model Parameters

To fit the regression model to data, we estimate the parameters $\alpha$, $\beta$, and $\sigma_{\varepsilon}$ using the **least squares method**, which minimizes the sum of squared residuals. Residuals, defined as $e_i = y_i - (\widehat{\alpha} + \widehat{\beta} x_i)$, measure the difference between observed and predicted values. This method ensures the regression line best fits the data by solving the **normal equations** derived from minimizing $\sum_{i=1}^n (y_i - (a + b x_i))^2$. The resulting estimators provide insights into the relationship between variables, such as predicting losses based on time.

#### Least Squares Estimation

The least squares estimators $\widehat{\alpha}$ and $\widehat{\beta}$ are found by solving:

$$
\begin{cases}
\sum_{i=1}^n x_i y_i = a \sum_{i=1}^n x_i + b \sum_{i=1}^n x_i^2 \\
\sum_{i=1}^n y_i = n a + b \sum_{i=1}^n x_i
\end{cases}
$$

This yields:

$$
\widehat{\beta} = \frac{\sum_{i=1}^n (x_i - \bar{x}_n)(y_i - \bar{y}_n)}{\sum_{i=1}^n (x_i - \bar{x}_n)^2} = \frac{s_{XY}}{s_X^2}, \quad \widehat{\alpha} = \bar{y}_n - \widehat{\beta} \bar{x}_n
$$

where $s_{XY}$ is the empirical covariance and $s_X^2$ is the empirical variance of $x$. The error variance is estimated as $s_{\varepsilon}^2 = \frac{\sum_{i=1}^n e_i^2}{n-2}$, accounting for the two estimated parameters.

#### Example: Company Losses

Consider a dataset of company losses over five months:

$$
\begin{array}{c|ccccc}
\text{Month} (x_i) & 1 & 2 & 3 & 4 & 5 \\
\text{Loss} (y_i) & 11 & 6 & 4 & 0 & -1 \\
\end{array}
$$

Using least squares, we compute:

- $\bar{x}_n = 3$, $\bar{y}_n = 4$, $\sum (x_i - \bar{x}_n)(y_i - \bar{y}_n) = -30$, $\sum (x_i - \bar{x}_n)^2 = 10$.
- Slope: $\widehat{\beta} = \frac{-30}{10} = -3$.
- Intercept: $\widehat{\alpha} = 4 - (-3) \cdot 3 = 13$.
- Regression line: $\widehat{y} = 13 - 3x$.
- Error variance: $s_{\varepsilon}^2 = \frac{\sum e_i^2}{n-2} = \frac{4}{3}$.
  For month 6 ($x = 6$), the predicted loss is $\widehat{y} = 13 - 3 \cdot 6 = -5$, but caution is needed due to extrapolation beyond the observed $x$-range [1, 5].

### Assessing Model Fit and Significance

To evaluate the regression model, we use **confidence intervals** and **hypothesis tests** to assess the significance of parameters and the validity of assumptions. The error variance $\sigma_{\varepsilon}^2$ follows a chi-squared distribution, allowing us to construct confidence intervals, while $\widehat{\alpha}$ and $\widehat{\beta}$ follow t-distributions for testing significance. These tools help determine whether the slope or intercept significantly differs from zero, indicating a meaningful relationship.

#### Confidence Intervals for Error Variance

The statistic $\frac{(n-2) s_{\varepsilon}^2}{\sigma_{\varepsilon}^2} \sim \chi_{n-2}^2$ enables a confidence interval for $\sigma_{\varepsilon}^2$:

$$
\left[ \frac{(n-2) s_{\varepsilon}^2}{\chi_{n-2, 1-\frac{\alpha}{2}}^2}, \frac{(n-2) s_{\varepsilon}^2}{\chi_{n-2, \frac{\alpha}{2}}^2} \right]
$$

For the company loss example with $n = 5$, $s_{\varepsilon}^2 = \frac{4}{3}$, and 95% confidence ($\alpha = 0.05$):

$$
\left[ \frac{3 \cdot \frac{4}{3}}{\chi_{3, 0.975}^2}, \frac{3 \cdot \frac{4}{3}}{\chi_{3, 0.025}^2} \right] = \left[ \frac{4}{9.348}, \frac{4}{0.216} \right] = [0.428, 18.52]
$$

This wide interval reflects the small sample size.

#### Hypothesis Testing for Parameters

To test $H_0: \beta = 0$ (no linear relationship), use:

$$
t = \frac{\widehat{\beta}}{s_{\varepsilon}} \sqrt{\sum_{i=1}^n (x_i - \bar{x}_n)^2}
$$

For the example, $\widehat{\beta} = -3$, $s_{\varepsilon} = \sqrt{\frac{4}{3}}$, $\sum (x_i - \bar{x}_n)^2 = 10$:

$$
t = \frac{-3 \sqrt{10}}{\sqrt{\frac{4}{3}}} = -8.22
$$

The acceptance region for $\alpha = 0.05$ with 3 degrees of freedom is $[-3.18, 3.18]$. Since $-8.22$ is outside, we reject $H_0$, indicating a significant slope. Similarly, for $H_0: \alpha = 0$:

$$
t = \frac{\widehat{\alpha}}{s_{\varepsilon} \sqrt{\bar{x}_n^2 + \frac{1}{n} \sum (x_i - \bar{x}_n)^2}} = \frac{13 \sqrt{10}}{\sqrt{\frac{4}{3}} \sqrt{9 + 2}} = 10.73
$$

This is also outside $[-3.18, 3.18]$, so the intercept is significant.

#### Correlation and Significance

The **correlation coefficient** $r_{XY} = \frac{s_{XY}}{\sqrt{s_X^2 s_Y^2}}$ measures the strength of the linear relationship. In the example:

$$
r_{XY} = \frac{-30}{\sqrt{10 \cdot 94}} = -0.98
$$

Testing $H_0: \rho = 0$ uses:

$$
t = \frac{r_{XY}}{\sqrt{\frac{1 - r_{XY}^2}{n-2}}} = -8.22
$$

This matches the slope test, confirming a significant negative correlation.

### Real-World Application: Housing Taxes

In a dataset of 107 houses in Albuquerque, the annual tax ($y$) is regressed against the house price ($x$, in hundreds of dollars). The R output provides:

- Intercept: $\widehat{\alpha} = 36.3444$, not significant ($p = 0.4025ros = \widehat{\beta} = 0.7028$, highly significant ($p = 0.0000$).
- Residual standard error: 149.5, degrees of freedom: 105.
- $R^2 = 0.7668$, indicating a strong linear fit.
  However, residual plots reveal **heteroscedasticity** (increasing variance with larger predicted values) and non-normal residuals, violating model assumptions. A logarithmic transformation ($\log(\text{tax}) \sim \log(\text{price})$) improves homoscedasticity, with:
- Intercept: $-0.6504$, not significant ($p = 0.1236$).
- Slope: $1.0470$, significant ($p = 0.0000$).
- $R^2 = 0.741$, still a good fit.
  The transformed model shows more consistent residual variance, though some normality issues persist, suggesting further analysis may be needed.

#### Addressing Model Violations

- **Heteroscedasticity**: When residual variance increases with predicted values, transformations like logarithmic or weighted regression can stabilize variance.
- **Non-normality**: If residuals deviate from normality (seen in QQ-plots), alternative models or robust methods may be considered.
- **Outliers**: Expensive houses with lower taxes pull the regression line, suggesting a need for robust regression techniques.

---

## Key Points to Remember

- **Core Model → Linear Relationship**: The model $Y_i = \alpha + \beta x_i + \varepsilon_i$ assumes a linear relationship with normally distributed, homoscedastic errors. ★★★★☆
- **Least Squares → Parameter Estimation**: Minimize $\sum e_i^2$ to estimate $\widehat{\alpha}$ and $\widehat{\beta}$, with $s_{\varepsilon}^2$ estimating error variance. ★★★★★
- **Residual Analysis → Model Fit**: Small residuals indicate a good fit; use $\sum e_i^2$, Laplace, or other measures to assess. ★★★★☆
- **Significance Testing → Parameter Validity**: Use t-tests for $\alpha$ and $\beta$, and chi-squared tests for $\sigma_{\varepsilon}^2$, with $n-2$ degrees of freedom. ★★★★☆
- **Correlation → Relationship Strength**: $r_{XY}$ quantifies the linear relationship, with significance tests mirroring slope tests. ★★★★☆
- **Assumption Violations → Data Transformation**: Heteroscedasticity or non-normality may require transformations (e.g., logarithmic) to meet model assumptions. ★★★★☆
- **Extrapolation Caution → Prediction Limits**: Predictions outside the observed $x$-range (e.g., month 6 in the example) risk inaccuracy due to potential non-linear relationships. ★★★☆☆
- **Practical Application → Real Data**: Real-world examples like housing taxes highlight the need to check assumptions and consider transformations. ★★★★☆
