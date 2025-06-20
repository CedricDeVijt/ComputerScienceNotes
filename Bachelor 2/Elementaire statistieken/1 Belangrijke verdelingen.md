## 1.1 Discrete Probability Distributions

This section introduces key discrete univariate probability distributions, focusing on their definitions, properties, and applications. Each distribution is explored with its sample space, probability mass function, and key statistical measures like expectation and variance, providing a foundation for understanding random variables in discrete settings.

### Discrete Uniform Distribution

The **discrete uniform distribution** models scenarios where each outcome in a finite sample space is equally likely, such as rolling a fair die. It is defined on a sample space $\Omega = \{1, \dots, n\}$ with equal probabilities for each outcome. This distribution is foundational for understanding symmetry in probability and serves as a basis for more complex distributions.

#### Definition and Properties

For a random variable $X$ following a discrete uniform distribution on $\Omega = \{1, \dots, n\}$:

- **Probability**: $P(X = j) = \frac{1}{n}$ for $j = 1, \dots, n$.
- **Expectation**: $E[X] = \sum_\limits{j=1}^n j \cdot \frac{1}{n} = \frac{n+1}{2}$, derived using the sum $\sum\limits_{j=1}^n j = \frac{n(n+1)}{2}$.
- **Variance**: $\text{Var}[X] = \sum\limits_{j=1}^n j^2 \cdot \frac{1}{n} - \left(\frac{n+1}{2}\right)^2 = \frac{(n+1)(n-1)}{12}$, using $\sum\limits_{j=1}^n j^2 = \frac{n(n+1)(2n+1)}{6}$.
- **Example**: Rolling a fair die ($n = 6$) yields $E[X] = 3.5$ and $\text{Var}[X] = \frac{35}{12} \approx 2.9167$.

This distribution’s symmetry makes it ideal for modeling scenarios like random sampling or lottery draws.

### Bernoulli Distribution

The **Bernoulli distribution** models experiments with two outcomes, labeled as "success" (1) and "failure" (0), such as flipping a coin. It is the building block for the binomial distribution and is critical for analyzing binary events.

#### Definition and Properties

For a random variable $X \sim \mathcal{B}(1, p)$ with sample space $\Omega = \{0, 1\}$:

- **Probability**: $P(X = 1) = p$, $P(X = 0) = q = 1 - p$, where $0 < p < 1$.
- **Expectation**: $E[X] = p$.
- **Variance**: $\text{Var}[X] = p q$.
- **Example**: In a coin toss with $p = 0.5$, $E[X] = 0.5$, $\text{Var}[X] = 0.25$.

This distribution connects to real-world binary scenarios like pass/fail tests or yes/no responses.

### Binomial Distribution

The **binomial distribution** describes the number of successes in $n$ independent Bernoulli trials, each with success probability $p$. It is widely used in scenarios like quality control or survey analysis, generalizing the Bernoulli distribution.

#### Definition and Properties

For a random variable $Y = X_1 + \dots + X_n$, where $X_i \sim \mathcal{B}(1, p)$ are independent and identically distributed (i.i.d.), $Y \sim \mathcal{B}(n, p)$:

- **Sample space**: $\Omega = \{0, 1, \dots, n\}$.
- **Probability**: $P(Y = k) = \binom{n}{k} p^k q^{n-k} = \frac{n!}{k!(n-k)!} p^k q^{n-k}$.
- **Expectation**: $E[Y] = n p$.
- **Variance**: $\text{Var}[Y] = n p q$.
- **Property**: If $Y_1 \sim \mathcal{B}(n_1, p)$ and $Y_2 \sim \mathcal{B}(n_2, p)$ are independent, then $Y_1 + Y_2 \sim \mathcal{B}(n_1 + n_2, p)$.

The probability sums to 1 via the binomial theorem: $\sum\limits_{k=0}^n \binom{n}{k} p^k q^{n-k} = (p + q)^n = 1$. The mode is 0 for $p \approx 0$ and $n$ for $p \approx 1$.

### Negative Binomial Distribution

The **negative binomial distribution** models the number of failures before the $r$-th success in a sequence of i.i.d. Bernoulli trials. It is used in reliability testing or waiting-time problems, extending the Bernoulli framework.

#### Definition and Properties

For a random variable $X$ representing the number of failures before the $r$-th success, $X \sim \text{NB}(r, \theta)$, where $\theta = 1 - p$:

- **Sample space**: $\Omega = \{0, 1, 2, \dots\}$.
- **Probability**: $P(X = j) = \binom{j + r - 1}{j} p^r q^j$.
- **Example**: If $r = 3$, $p = 0.4$, the probability of 2 failures before the third success is $P(X = 2) = \binom{4}{2} (0.4)^3 (0.6)^2$.
- **Note**: Some notations use $p$ instead of $\theta$, so verify the parameter definition.

The distribution’s name derives from its relation to the negative binomial expansion, linking it to combinatorial identities.

### Poisson Distribution

The **Poisson distribution** models the number of events in a fixed interval, given a constant average rate $\alpha$. It is used in fields like telecommunications or epidemiology for counting rare events and approximates the binomial for large $n$ and small $p$.

#### Definition and Properties

For a random variable $X \sim \mathcal{P}(\alpha)$:

- **Sample space**: $\Omega = \{0, 1, 2, \dots\}$.
- **Probability**: $P(X = j) = \frac{e^{-\alpha}\alpha^j}{j!}$.
- **Expectation**: $E[X] = \alpha$.
- **Variance**: $\text{Var}[X] = \alpha$.
- **Property**: If $X_1 \sim \mathcal{P}(\alpha_1)$ and $X_2 \sim \mathcal{P}(\alpha_2)$ are independent, then $X_1 + X_2 \sim \mathcal{P}(\alpha_1 + \alpha_2)$.
- **Example**: If $\alpha = 2$ calls per hour in a call center, $P(X = 3) = \frac{2^3}{3!} e^{-2} \approx 0.1804$.

The probability sums to 1: $\sum_{j=0}^\infty \frac{\alpha^j}{j!} e^{-\alpha} = e^{-\alpha} e^\alpha = 1$.

## 1.2 Continuous Probability Distributions

This section covers continuous univariate distributions, emphasizing their density functions, distribution functions, and statistical properties. These distributions model phenomena over continuous intervals, such as time or distance measurements.

### Continuous Uniform Distribution

The **continuous uniform distribution** models random selection over a continuous interval $[a, b]$, where all subintervals of equal length are equally likely. It is used in simulations and random sampling, serving as the continuous analog of the discrete uniform distribution.

#### Definition and Properties

For a random variable $X \sim \mathcal{U}[a, b]$, with $-\infty < a < b < \infty$:

- **Density function**: $f_{a,b}(x) = \frac{1}{b - a} \mathbb{1}_{[a, b]}(x)$.
- **Distribution function**: $F_{a,b}(x) = \begin{cases} 0 & x < a \\ \frac{x - a}{b - a} & a \leq x \leq b \\ 1 & x > b \end{cases}$.
- **Expectation**: $E[X] = \frac{a + b}{2}$.
- **Variance**: $\text{Var}[X] = \frac{(b - a)^2}{12}$.
- **Example**: For $X \sim \mathcal{U}[0, 10]$, $E[X] = 5$, $\text{Var}[X] = \frac{100}{12} \approx 8.3333$.

The density’s rectangular shape, integrating to 1 over $[a, b]$, earns it the name "rechthoeksverdeling" (rectangular distribution).

### Normal Distribution

The **normal distribution**, or Gaussian distribution, is characterized by its bell-shaped density and is central to statistics due to the Central Limit Theorem. It models phenomena like measurement errors and is standardized for table-based calculations.

#### Standard Normal Distribution

For a random variable $Z \sim \mathcal{N}(0, 1)$:

- **Density**: $\phi(x) = \frac{1}{\sqrt{2\pi}} e^{-\frac{x^2}{2}}$.
- **Distribution function**: $\Phi(x) = \int_{-\infty}^x \phi(t) \, dt$, with values from tables due to no closed-form expression.
- **Expectation**: $E[Z] = 0$.
- **Variance**: $\text{Var}[Z] = 1$.
- **Key probabilities**: $P(|Z| \leq 1) \approx 0.6827$, $P(|Z| \leq 2) \approx 0.9545$, $P(|Z| \leq 3) \approx 0.9973$.
- **Quantiles**: $\Phi^{-1}(0.95) = 1.645$, $\Phi^{-1}(0.975) = 1.96$.
- **Symmetry**: $\Phi(-x) = 1 - \Phi(x)$.

#### General Normal Distribution

For $X \sim \mathcal{N}(\mu, \sigma^2)$, defined as $X = \sigma Z + \mu$ where $Z \sim \mathcal{N}(0, 1)$:

- **Density**: $f_{\mu, \sigma}(x) = \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}$.
- **Distribution function**: $F_X(x) = \Phi\left(\frac{x - \mu}{\sigma}\right)$.
- **Expectation**: $E[X] = \mu$.
- **Variance**: $\text{Var}[X] = \sigma^2$.
- **Property**: If $X_1 \sim \mathcal{N}(\mu_1, \sigma_1^2)$ and $X_2 \sim \mathcal{N}(\mu_2, \sigma_2^2)$ are independent, then $X_1 + X_2 \sim \mathcal{N}(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$.
- **Example**: For $X \sim \mathcal{N}(5, 4)$, $P(1 \leq X \leq 7) = \Phi(1) - \Phi(-2) \approx 0.8413 - (1 - 0.9772) = 0.8185$.

Standardization, $\frac{X - \mu}{\sigma} \sim \mathcal{N}(0, 1)$, enables use of standard normal tables.

### Chi-Square Distribution

The **chi-square distribution** arises as the sum of squared independent standard normal variables and is used in hypothesis testing and confidence intervals. It is defined for positive values and depends on degrees of freedom.

#### Definition and Properties

For $X = Z_1^2 + \dots + Z_n^2$, where $Z_i \sim \mathcal{N}(0, 1)$ are i.i.d., $X \sim \chi_n^2$:

- **Density**: $f_{\chi_n^2}(x) = \begin{cases} \frac{1}{2^{\frac{n}{2}} \Gamma\left(\frac{n}{2}\right)} e^{-\frac{x}{2}} x^{\frac{n}{2} - 1} & x > 0 \\ 0 & x \leq 0 \end{cases}$, where $\Gamma(t) = \int_0^\infty x^{t-1} e^{-x} \, dx$.
- **Expectation**: $E[X] = n$.
- **Variance**: $\text{Var}[X] = 2n$.
- **Property**: If $X_1 \sim \chi_{n_1}^2$ and $X_2 \sim \chi_{n_2}^2$ are independent, then $X_1 + X_2 \sim \chi_{n_1 + n_2}^2$.
- **Approximation**: For $n \geq 30$, $\sqrt{2X} \approx \mathcal{N}(\sqrt{2n - 1}, 1)$.
- **Example**: For $n = 2$, the density is strictly decreasing, with $\lim_{x \downarrow 0} f_{\chi_2^2}(x) = \frac{1}{2}$.

The gamma function $\Gamma(t)$ satisfies $\Gamma(t+1) = t \Gamma(t)$, $\Gamma(n+1) = n!$, and $\Gamma\left(\frac{1}{2}\right) = \sqrt{\pi}$.

### Student’s t-Distribution

The **Student’s t-distribution** models the ratio of a standard normal variable to the square root of a scaled chi-square variable. It is used in small-sample hypothesis testing, with heavier tails than the normal distribution.

#### Definition and Properties

For $Z \sim \mathcal{N}(0, 1)$ and $X \sim \chi_n^2$ independent, $T = \frac{Z}{\sqrt{X / n}} \sim t_n$:

- **Density**: $f_{t_n}(t) = \frac{\Gamma\left(\frac{n+1}{2}\right)}{\sqrt{n \pi} \Gamma\left(\frac{n}{2}\right)} \left(1 + \frac{t^2}{n}\right)^{-\frac{n+1}{2}}$, for $-\infty < t < \infty$.
- **Expectation**: $E[T] = 0$ (for $n > 1$).
- **Variance**: $\text{Var}[T] = \frac{n}{n - 2}$ (for $n > 2$).
- **Property**: As $n$ increases, the t-distribution approaches $\mathcal{N}(0, 1)$.

The distribution, introduced by W. Gosset (Student) in 1908, is symmetric around 0.

### F-Distribution

The **F-distribution** models the ratio of two scaled chi-square variables and is used in analysis of variance (ANOVA). It depends on numerator and denominator degrees of freedom.

#### Definition and Properties

For $W \sim \chi_m^2$ and $V \sim \chi_n^2$ independent, $X = \frac{W / m}{V / n} \sim F_{m, n}$:

- **Density**: $f_{m, n}(x) = \begin{cases} \frac{m^{\frac{m}{2}} n^{\frac{n}{2}} \Gamma\left(\frac{m+n}{2}\right)}{\Gamma\left(\frac{m}{2}\right) \Gamma\left(\frac{n}{2}\right)} \frac{x^{\frac{m}{2} - 1}}{(n + m x)^{\frac{m+n}{2}}} & x > 0 \\ 0 & x \leq 0 \end{cases}$.
- **Expectation**: $E[X] = \frac{n}{n - 2}$ (for $n > 2$).
- **Variance**: $\text{Var}[X] = \frac{2 n^2 (m + n - 2)}{m (n - 4) (n - 2)^2}$ (for $n > 4$).
- **Property**: $F_{m, n}(x) = 1 - F_{n, m}\left(\frac{1}{x}\right)$, so quantiles satisfy $F_{m, n, \alpha} = \frac{1}{F_{n, m, 1 - \alpha}}$.
- **Example**: For $m = n$, $F_{m, m, \frac{1}{2}} = 1$.

Introduced by Fisher in 1924, this distribution is critical for comparing variances.

---

## Key Points to Remember

- **Discrete Uniform → Equal Probabilities**: Each outcome in $\Omega = \{1, \dots, n\}$ has probability $\frac{1}{n}$, with $E[X] = \frac{n+1}{2}$, $\text{Var}[X] = \frac{(n+1)(n-1)}{12}$. ★★★★☆
- **Bernoulli → Binary Outcomes**: Models success/failure with $P(X = 1) = p$, $E[X] = p$, $\text{Var}[X] = p(1 - p)$. Foundation for binomial. ★★★★☆
- **Binomial → Repeated Trials**: Sums $n$ i.i.d. Bernoulli trials, $P(Y = k) = \binom{n}{k} p^k q^{n-k}$, $E[Y] = n p$, $\text{Var}[Y] = n p q$. ★★★★★
- **Negative Binomial → Waiting for Success**: Counts failures before $r$-th success, $P(X = j) = \binom{j + r - 1}{j} p^r q^j$. Verify notation for $p$ vs. $\theta$. ★★★★☆
- **Poisson → Rare Events**: Models event counts with rate $\alpha$, $P(X = j) = \frac{\alpha^j}{j!} e^{-\alpha}$, $E[X] = \text{Var}[X] = \alpha$. ★★★★★
- **Continuous Uniform → Rectangular Density**: Defined on $[a, b]$, $f(x) = \frac{1}{b - a}$, $E[X] = \frac{a + b}{2}$, $\text{Var}[X] = \frac{(b - a)^2}{12}$. ★★★★☆
- **Normal → Bell-Shaped Curve**: Standard normal $Z \sim \mathcal{N}(0, 1)$, general $X \sim \mathcal{N}(\mu, \sigma^2)$, with standardization $\frac{X - \mu}{\sigma} \sim \mathcal{N}(0, 1)$. ★★★★★
- **Chi-Square, t, F → Statistical Testing**: Chi-square sums squared normals, t for small samples, F for variance ratios. Use tables for quantiles. ★★★★☆
