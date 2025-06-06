## 2.1 Solving Nonlinear Equations

### Introduction to Nonlinear Problems

Nonlinear equations model complex phenomena like population growth, where analytical solutions are often impossible. The chapter introduces numerical methods (bisection, Newton, secant, fixed-point iteration) to approximate roots of equations like:
$$N(t) = N_0 e^{\lambda t} + \nu \frac{e^{\lambda t} - 1}{\lambda}.$$
**Key challenge**: Error propagation in input parameters (e.g., initial population $N_0$) affects solution accuracy.

#### Population Growth Example

Given $N(0)=1,000,000$, $N(1)=1,264,000$, and $\nu=35,000$, find $\lambda$:
$$1,264,000 = 1,000,000 e^{\lambda} + 35,000 \frac{e^{\lambda} - 1}{\lambda}.$$
Numerical methods are essential here due to the transcendental nature of the equation.

### Bisection Method

A robust but slow method for finding roots in intervals $[a, b]$ where $F(a)F(b) < 0$.

#### Algorithm Steps

1. **Initialize**: Set $a_0 = a$, $b_0 = b$, $k = 0$.
2. **Iterate**:
   - Compute midpoint $x_k = \frac{a_k + b_k}{2}$.
   - Update interval:
     - If $F(a_k)F(x_k) \leq 0$, set $[a_{k+1}, b_{k+1}] = [a_k, x_k]$.
     - Else, set $[a_{k+1}, b_{k+1}] = [x_k, b_k]$.
3. **Terminate** when $|b_k - a_k| < \text{TOL}$.

**Convergence**: $\mathcal{O}(2^{-k})$, requiring ~10 iterations for 3 extra decimal digits.

#### Example

For $F(x) = x^3 + 4x^2 - 10$ on $[1, 2]$, bisection yields:
| Iteration | $x_k$ |
|-----------|---------|
| 0 | 1.5000 |
| 9 | 1.3643 |
**Error bound**: $|x_9 - x^*| \leq 2^{-10} \approx 0.001$.

### Newton's Method

Faster convergence using tangents:
$$x_k = x_{k-1} - \frac{F(x_{k-1})}{F'(x_{k-1})}.$$

#### Strengths & Weaknesses

- **Strengths**: Quadratic convergence ($\mathcal{O}(\theta^{2^k})$).
- **Weaknesses**: Requires good initial guess $x_0 \approx x^*$ and derivative $F'$.

#### Example

For $F(x) = x^3 + 4x^2 - 10$ with $x_0=2$:
| Iteration | $x_k$ |
|-----------|---------------|
| 1 | 1.500000000 |
| 5 | 1.365230013 |

### Secant Method

Derivative-free variant using difference quotients:
$$x_k = x_{k-1} - \frac{F(x_{k-1})(x_{k-1} - x_{k-2})}{F(x_{k-1}) - F(x_{k-2})}.$$
**Convergence**: Slower than Newton but faster than bisection.

#### Example

For $F(x) = x^3 + 4x^2 - 10$ with $x_0=1$, $x_1=2$:
| Iteration | $x_k$ |
|-----------|---------------|
| 2 | 1.263157895 |
| 6 | 1.365230001 |

### Fixed-Point Iteration

Solves $x = G(x)$ for equivalent root-finding problems.

#### Convergence Criteria

- **Contraction**: $|G'(x)| \leq \theta < 1$ ensures convergence.
- **Error bounds**:
  - A priori: $|x_k - x^*| \leq \theta^k (b - a)$.
  - A posteriori: $|x_k - x^*| \leq \frac{\theta}{1-\theta} |x_k - x_{k-1}|$.

#### Example

For $e^{-x} = x$, use $G(x) = \frac{1}{2}(x + e^{-x})$:

- $\theta = \max |G'(x)| \approx \frac{1}{3}$ → linear convergence.
- After 9 iterations: $x_9 \approx 0.5671$.

---

## Key Points to Remember

- **Bisection → Guaranteed Convergence** (★★★☆☆): Always finds a root but slowly. Use for initial approximations.
- **Newton → Speed vs Stability Tradeoff** (★★★★☆): Quadratic convergence but sensitive to $x_0$ and requires $F'$.
- **Secant → Balanced Approach** (★★★☆☆): No derivative needed; faster than bisection but less robust than Newton.
- **Fixed-Point → Flexibility** (★★★☆☆): Generalizes to multi-dimensional problems but requires contraction.
- **Error Propagation**: Input errors (e.g., $\Delta w = 0.5$) amplify via $f'(u)$, limiting solution precision.
