This chapter introduces the concept of **parameter estimation** in statistics, focusing on how sample data can approximate unknown population parameters like the mean ($\mu$) and variance ($\sigma^2$). It explores the **sample mean** as an estimator for the population mean, the role of the **Central Limit Theorem**, and properties of **point estimators** like bias and mean squared error (MSE). The content emphasizes practical applications and theoretical foundations, connecting sample-based estimates to population characteristics for robust statistical inference.

## 3.1 Sample Mean as an Estimator

The **sample mean** ($\bar{X}_n$) serves as a primary estimator for the **population mean** ($\mathrm{E}[X] = \mu$). It is calculated as the average of $n$ independent observations from a population, denoted as $\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$, where $X_i$ are random variables. The observed sample mean ($\bar{x}_n$) from specific data ($x_1, \ldots, x_n$) provides a point estimate, but its value varies across samples due to randomness. Understanding its variability is crucial for assessing how well it approximates $\mu$.

### Distribution of the Sample Mean

The **distribution** of the sample mean ($\bar{X}_n$) provides insight into its reliability as an estimator. For a sample of size $n$ from a normally distributed population ($X_i \sim \mathcal{N}(\mu, \sigma^2)$), the sample mean is also normally distributed: $\bar{X}_n \sim \mathcal{N}(\mu, \frac{\sigma^2}{n})$. Its **expected value** is $\mathrm{E}[\bar{X}_n] = \mu$, and its **variance** is $\operatorname{Var}[\bar{X}_n] = \frac{\sigma^2}{n}$, showing that larger samples reduce variability, making $\bar{X}_n$ a more precise estimator.

- **Example**: For a population $X \sim \mathcal{N}(10, 9)$, a sample of size $n=60$ yields sample means clustering around 10, with most values between 9 and 11, as seen in histograms of 50 sample means. This illustrates the **normal distribution** and reduced spread of $\bar{X}_n$ compared to individual observations.

![[Bachelor 2/Elementaire statistieken/images/Pasted image 20250620193426.png]]

### Central Limit Theorem

The **Central Limit Theorem (CLT)** extends the utility of the sample mean to non-normal populations. For large $n$, the distribution of $\bar{X}_n$ approximates a normal distribution: $\bar{X}_n \approx \mathcal{N}(\mu, \frac{\sigma^2}{n})$, regardless of the underlying distribution of $X_i$, provided $\mathrm{E}[X_i] = \mu$ and $\operatorname{Var}[X_i] = \sigma^2 < \infty$. This makes the sample mean a versatile estimator, with precision improving as $n$ increases.

- **Key Insight**: The CLT implies that the standardized form $\frac{\sqrt{n}(\bar{X}_n - \mu)}{\sigma} \xrightarrow{D} \mathcal{N}(0,1)$, enabling probabilistic statements about how close $\bar{X}_n$ is to $\mu$. For sums, $S_n = X_1 + \cdots + X_n \approx \mathcal{N}(n\mu, n\sigma^2)$.

## 3.2 Point Estimators and Their Properties

**Point estimators** are statistics used to estimate unknown population parameters ($\theta$) based on sample data. A **statistic** $T(X_1, \ldots, X_n)$ depends only on the sample and not on $\theta$. The section introduces criteria like **bias** and **mean squared error (MSE)** to evaluate estimator quality, ensuring accurate and reliable estimates across repeated samples.

### Definition of Estimators

An **estimator** $T(X_1, \ldots, X_n)$ is a statistic designed to approximate a parameter $\theta$, while an **estimate** is the specific value $T(x_1, \ldots, x_n)$ for a given sample. For example, the sample mean $\bar{X}_n$ estimates $\mu$, and for a sample like (170, 178, 185, 168, 182), the estimate is $\bar{x}_n = 176.6$. Other estimators, like the **sample median**, may also estimate $\mu$, especially in symmetric distributions like the normal.

- **Example**: For a normal population, both the sample mean and median estimate $\mu$, but the sample mean is preferred due to its well-defined properties under normality assumptions.

### Properties of Estimators

Estimators are evaluated based on **bias**, **variance**, and **mean squared error (MSE)**. An estimator $T$ is **unbiased** if $\mathrm{E}[T] = \theta$, meaning it does not systematically over- or underestimate $\theta$. The **MSE** measures overall accuracy: $\operatorname{MSE}(T) = \mathrm{E}[(T - \theta)^2] = (b(T))^2 + \operatorname{Var}[T]$, where $b(T) = \mathrm{E}[T] - \theta$ is the bias. Unbiased estimators with low variance are preferred.

- **Key Relationship**: For an unbiased estimator, $\operatorname{MSE}(T) = \operatorname{Var}[T]$, emphasizing the importance of minimizing variance for precision.

### Estimating Parameters of a Normal Population

For a normal population $X_i \sim \mathcal{N}(\mu, \sigma^2)$, the **sample mean** ($\bar{X}_n$) and **sample variance** ($S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)^2$) are key estimators. $\bar{X}_n$ is unbiased ($\mathrm{E}[\bar{X}_n] = \mu$) with $\operatorname{MSE} = \frac{\sigma^2}{n}$, and $S^2$ is unbiased for $\sigma^2$ ($\mathrm{E}[S^2] = \sigma^2$). The **Helmert Theorem** confirms that $\frac{(n-1)S^2}{\sigma^2} \sim \chi_{n-1}^2$ and that $\bar{X}_n$ and $S^2$ are independent.

- **Why $n-1$**? The denominator $n-1$ in $S^2$ corrects for the loss of one degree of freedom when estimating $\mu$ with $\bar{X}_n$, ensuring unbiasedness.

### Estimating Proportions

For a **Bernoulli population** with success probability $p$, the sample proportion $\widehat{P} = \bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$ estimates $p$. It is unbiased ($\mathrm{E}[\widehat{P}] = p$) with variance $\operatorname{Var}[\widehat{P}] = \frac{p(1-p)}{n}$. The CLT ensures that for large $n$, $\widehat{P} \approx \mathcal{N}(p, \frac{p(1-p)}{n})$, allowing precise estimation of proportions.

- **Example**: In a sample of 100 Bernoulli trials, if 60 successes are observed, $\widehat{p} = 0.6$ estimates $p$, with variability decreasing as $n$ grows.

## Key Points to Remember

- **Sample Mean → Estimating $\mu$**: The sample mean $\bar{X}_n$ is an unbiased estimator for the population mean, with variance $\frac{\sigma^2}{n}$, making it more precise for larger samples. ★★★★☆
- **Central Limit Theorem → Normal Approximation**: For large $n$, $\bar{X}_n \approx \mathcal{N}(\mu, \frac{\sigma^2}{n})$, enabling robust inference regardless of the population’s distribution. ★★★★★
- **Unbiased Estimators → Zero Bias**: An estimator is unbiased if $\mathrm{E}[T] = \theta$, ensuring no systematic error. ★★★★☆
- **MSE → Accuracy Measure**: MSE combines bias and variance ($\operatorname{MSE}(T) = (b(T))^2 + \operatorname{Var}[T]$) to evaluate estimator quality. ★★★★☆
- **Sample Variance → Estimating $\sigma^2$**: Use $S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar{X}_n)^2$ for unbiased estimation of variance, with distribution $\frac{(n-1)S^2}{\sigma^2} \sim \chi_{n-1}^2$. ★★★★☆
- **Proportions → Bernoulli Estimation**: The sample proportion $\widehat{P}$ is unbiased for $p$, with variance $\frac{p(1-p)}{n}$, stabilizing around $p$ as $n$ increases. ★★★★☆
- **Common Pitfall → Assuming Exact Normality**: The CLT is an approximation for large $n$; skewed distributions may require larger samples for normality. ★★★☆☆
