## 1 Introduction to Numerical Analysis

### Floating-Point Representation

- **Definition**: A number $x \neq 0$ is represented as $x = \pm 0.\alpha_1 \alpha_2 \dots \alpha_t \times B^b$, where:
  - $B$: Base (e.g., $B = 10$ for decimal, $B = 2$ for binary).
  - $t$: Precision (number of digits in mantissa).
  - $\alpha_i$: Digits in base $B$, with $\alpha_1 \neq 0$.
  - $b$: Exponent, $b \in \mathbb{Z}$.
- **Zero Representation**: $0.\underbrace{00\dots0}_t \times B^0$.
- **Rounding**: For a number $x$, the floating-point approximation is $\text{fl}(x)$, the closest representable number.
- **Relative Error Bound**:
  $$
  \frac{|\text{fl}(x) - x|}{|x|} \leq \text{eps} = \frac{1}{2} B^{1-t} \quad \text{(for base } B\text{)}.
  $$
  Thus, $\text{fl}(x) = (1 + \varepsilon)x$, with $|\varepsilon| \leq \text{eps}$.
- **Example for Binary ($B = 2, t = 3$)**:
  - Convert number to binary, normalize, and truncate mantissa to 3 bits.
  - E.g., for $x = 4$, binary is $100.0$, normalized as $0.100 \times 2^3$.

### Error Analysis

- **Absolute Error**: $|\tilde{y} - y|$.
- **Relative Error**: $\frac{|\tilde{y} - y|}{|y|}$.
- **Error Propagation (Single Variable)**:
  - For $y = f(a)$, with approximation $\tilde{y} = f(\tilde{a})$:
    $$
    \Delta y = \tilde{y} - y \approx f'(a) \Delta a, \quad \frac{\Delta y}{y} \approx \gamma \frac{\Delta a}{a}, \quad \gamma = \frac{a f'(a)}{f(a)}.
    $$
    Here, $\gamma$ is the condition number.
- **Error Propagation (Multiple Variables)**:
  - **Multiplication**: For $y = ab$:
    $$
    \frac{\Delta y}{y} \approx \frac{\Delta a}{a} + \frac{\Delta b}{b}, \quad \gamma_a = \gamma_b = 1.
    $$
  - **Division**: For $y = \frac{a}{b}$:
    $$
    \frac{\Delta y}{y} \approx \frac{\Delta a}{a} - \frac{\Delta b}{b}, \quad \gamma_a = 1, \quad \gamma_b = -1.
    $$
  - **Addition**: For $y = a + b$:
    $$
    \frac{\Delta y}{y} = \gamma_a \frac{\Delta a}{a} + \gamma_b \frac{\Delta b}{b}, \quad \gamma_a = \frac{a}{a+b}, \quad \gamma_b = \frac{b}{a+b}.
    $$
  - **Subtraction**: For $y = a - b$:
    $$
    \gamma_a = \frac{a}{a-b}, \quad \gamma_b = -\frac{b}{a-b}.
    $$
    Poorly conditioned when $a \approx b$.

### Algorithm Stability

- **Stability Definition**: An algorithm is stable if small relative errors in inputs and operations result in a small relative error in the output.
- **Stability Number**: $\sigma = \sigma_G + \sigma_A$, where:
  - $\sigma_G$: Sum of absolute condition numbers for inputs.
  - $\sigma_A$: Sum of absolute condition numbers for operations.
- **Computer Arithmetic**:
  - Operations: $x \oplus y = \text{fl}(x + y)$, $x \ominus y = \text{fl}(x - y)$, $x \otimes y = \text{fl}(xy)$, $x \oslash y = \text{fl}(x/y)$.
  - Relative error per operation: $\leq \text{eps}$.

## 2 Nonlinear Equations

### Bisection Method

- **Purpose**: Find root of $f(x) = 0$ in interval $[a, b]$ where $f(a) \cdot f(b) < 0$.
- **Iteration**:
  - Midpoint: $c = \frac{a + b}{2}$.
  - If $f(a) \cdot f(c) < 0$, set $b = c$; else set $a = c$.
- **Error Bound**: After $n$ iterations:
  $$
  |\text{error}| \leq \frac{b - a}{2^{n+1}}.
  $$
- **Number of Iterations**: To achieve $|\text{error}| < \epsilon$:
  $$
  n \geq \left\lceil \log_2 \left( \frac{b - a}{\epsilon} \right) - 1 \right\rceil.
  $$

### Newton’s Method

- **Iteration Formula**:
  $$
  x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}.
  $$
- **Convergence**: Quadratic near the root if $f'(x^*) \neq 0$.
- **Condition Number**: For root $x = f(\lambda)$, condition number is:
  $$
  \gamma = \frac{\lambda f'(\lambda)}{f(\lambda)}.
  $$

### Secant Method

- **Iteration Formula**:
  $$
  x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}.
  $$
- **Convergence**: Superlinear (order ~1.618).

### Fixed-Point Iteration

- **Formulation**: Rewrite $f(x) = 0$ as $x = g(x)$.
- **Iteration**: $x_{n+1} = g(x_n)$.
- **Convergence Condition**: $|g'(x^*)| < 1$ near fixed point $x^*$.
- **Error Bound**: If $|g'(x^*)| = k < 1$:
  $$
  |x_n - x^*| \leq k^n |x_0 - x^*|.
  $$
- **Newton as Fixed-Point**: For Newton’s method, $g(x) = x - \frac{f(x)}{f'(x)}$, and $g'(x^*) = 0$ if $f'(x^*) \neq 0$.

## 3 Interpolation

### Lagrange Interpolation

- **Polynomial**:
  $$
  P(x) = \sum_{i=0}^n y_i \ell_i(x), \quad \ell_i(x) = \prod_{\substack{j=0 \\ j \neq i}}^n \frac{x - x_j}{x_i - x_j}.
  $$
- **Property**: $\sum_{i=0}^n \ell_i(x) = 1$.
- **Error Propagation**:
  $$
  |\tilde{P}(x) - P(x)| \leq \gamma(x) \max_{0 \leq i \leq n} |\tilde{y}_i - y_i|, \quad \gamma(x) = \sum_{i=0}^n |\ell_i(x)|.
  $$

### Neville’s Method

- **Recursive Formula**:
  $$
  P_{i,j}(x) = \frac{(x - x_{i+j})P_{i,j-1}(x) + (x_i - x)P_{i+1,j-1}(x)}{x_i - x_{i+j}}, \quad P_{i,0}(x) = y_i.
  $$
- **Output**: $P_{0,n}(x)$ is the interpolated value at $x$.

### Newton’s Interpolation

- **Polynomial**:
  $$
  P(x) = f[x_0] + f[x_0, x_1](x - x_0) + \dots + f[x_0, \dots, x_n] \prod_{i=0}^{n-1} (x - x_i).
  $$
- **Divided Differences**:
  - $f[x_i] = f(x_i)$.
  - $f[x_i, x_{i+1}] = \frac{f(x_{i+1}) - f(x_i)}{x_{i+1} - x_i}$.
  - Higher-order: $f[x_i, \dots, x_{i+k}] = \frac{f[x_{i+1}, \dots, x_{i+k}] - f[x_i, \dots, x_{i+k-1}]}{x_{i+k} - x_i}$.

### Error Analysis

- **Error Formula**:
  $$
  f(x) - P(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!} \prod_{i=0}^n (x - x_i), \quad \xi \in [a, b].
  $$

## 4 Numerical Integration

### Trapezium Rule

- **Formula**:
  $$
  \bar{I} = \frac{h}{2}(y_0 + y_1), \quad h = \beta - \alpha, \quad y_0 = f(\alpha), \quad y_1 = f(\beta).
  $$
- **Error**:
  $$
  \bar{I} - I = \frac{1}{12} f''(\tau) h^3, \quad \tau \in [\alpha, \beta].
  $$
- **Extended Trapezium Rule**:
  $$
  \bar{I} = h \left( \frac{1}{2} y_0 + \sum_{i=1}^{n-1} y_i + \frac{1}{2} y_n \right), \quad h = \frac{\beta - \alpha}{n}.
  $$
- **Error**:
  $$
  \bar{I} - I = \frac{\beta - \alpha}{12} f''(\sigma) h^2.
  $$
- **Error Propagation**:
  $$
  |\bar{I} - \tilde{I}| \leq (\beta - \alpha) \max_{0 \leq i \leq n} |\tilde{y}_i - y_i|.
  $$

### Simpson’s Rule

- **Formula**:
  $$
  \bar{I} = \frac{h}{3}(y_0 + 4y_1 + y_2), \quad h = \frac{\beta - \alpha}{2}.
  $$
- **Error**:
  $$
  \bar{I} - I = \frac{1}{90} f^{(4)}(\tau) h^5.
  $$
- **Extended Simpson’s Rule** (even $n$):
  $$
  \bar{I} = \frac{h}{3} \left( y_0 + 2 \sum_{j=1}^{m-1} y_{2j} + 4 \sum_{j=1}^m y_{2j-1} + y_n \right), \quad m = \frac{n}{2}.
  $$
- **Error**:
  $$
  \bar{I} - I = \frac{\beta - \alpha}{180} f^{(4)}(\sigma) h^4.
  $$
- **Error Propagation**:
  $$
  |\bar{I} - \tilde{I}| \leq \frac{\beta - \alpha}{3} \left( \max_{i \text{ even}} |\tilde{y}_i - y_i| + 4 \max_{i \text{ odd}} |\tilde{y}_i - y_i| \right).
  $$

### Romberg Method

- **Euler-MacLaurin Formula**:
  $$
  T(h) = I + \gamma_1 h^2 + \gamma_2 h^4 + \dots.
  $$
- **Extrapolation**:
  $$
  T_{i,j} = T_{i,j-1} + \frac{1}{4^j - 1} (T_{i,j-1} - T_{i-1,j-1}).
  $$
