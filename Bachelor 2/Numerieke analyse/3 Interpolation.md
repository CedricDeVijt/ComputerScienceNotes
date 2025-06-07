## 3.1 Introduction to Interpolation

**Interpolation** is a method used to estimate unknown values within a range of known data points by constructing a function that passes through or approximates those points. It’s commonly used to approximate values of a function at points where direct measurements or data are unavailable, based on discrete data points.

Interpolation involves finding a function (called an interpolant) that fits a set of data points $(x_i, y_i)$ exactly or approximately, allowing estimation of values at intermediate points $x$ within the range of $x_i$.

## 3.2 Lagrange Interpolation Formula

Lagrange interpolation constructs a polynomial of degree at most $n$ that passes through $n+1$ points by expressing the polynomial as a linear combination of basis polynomials.

**Formula**: For points $(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)$, the Lagrange polynomial is:

$$
P(x) = \sum_{i=0}^n y_i \ell_i(x)
$$

where $\ell_i(x)$ is the Lagrange basis polynomial:

$$
\ell_i(x) = \prod_{\substack{j=0 \\ j \neq i}}^n \frac{x - x_j}{x_i - x_j}
$$

Each $\ell_i(x)$ is 1 at $x = x_i$ and 0 at all other $x_j$, ensuring $P(x_i) = y_i$.

**Key Features**:

- **Direct computation**: No need to solve a system of equations; the formula is explicit.
- **Drawbacks**: Computationally expensive for large $n$ (requires $\mathcal{O}(n^2)$ operations for evaluation), and adding a new point requires recalculating the entire polynomial.
- **Use case**: Best for theoretical work or small datasets due to its simplicity in formulation.

**Example**: For points $(0, 1), (1, 2), (2, 0)$, the Lagrange polynomial is:

$$
\ell_0(x) = \frac{(x-1)(x-2)}{(0-1)(0-2)}, \quad \ell_1(x) = \frac{(x-0)(x-2)}{(1-0)(1-2)}, \quad \ell_2(x) = \frac{(x-0)(x-1)}{(2-0)(2-1)}
$$

$$
P(x) = 1 \cdot \ell_0(x) + 2 \cdot \ell_1(x) + 0 \cdot \ell_2(x)
$$

## 3.3 Neville’s Method

Neville’s method is an iterative algorithm to compute the value of the interpolating polynomial at a specific point $x$ without explicitly constructing the polynomial. It builds a table of intermediate values to find $P(x)$.

**Algorithm**: Given points $(x_0, y_0), \dots, (x_n, y_n)$ and evaluation point $x$, construct a table where each entry $P_{i,j}(x)$ is the polynomial of degree $j$ that passes through points $(x_i, y_i), \dots, (x_{i+j}, y_{i+j})$. The recursive formula is:

$$
P_{i,j}(x) = \frac{(x - x_{i+j})P_{i,j-1}(x) + (x_i - x)P_{i+1,j-1}(x)}{x_i - x_{i+j}}
$$

- Start with $P_{i,0}(x) = y_i$.
- Compute higher-order terms until $P_{0,n}(x)$, which is the value of the interpolating polynomial at $x$.

**Key Features**:

- **Efficiency**: Computes $P(x)$ at a single point in $\mathcal{O}(n^2)$ operations without forming the full polynomial.
- **Flexibility**: Easily incorporates additional points by extending the table.
- **Drawbacks**: Not ideal for computing the polynomial’s coefficients or evaluating at multiple points.

**Use case**: Useful for evaluating the interpolating polynomial at specific points, especially in dynamic datasets.

## 3.4 Newton’s Interpolation Formula

Newton’s interpolation (forward or backward) expresses the polynomial using divided differences, making it efficient for adding new points and evaluating the polynomial.

**Formula**: The Newton polynomial is:

$$
P(x) = f[x_0] + f[x_0, x_1](x - x_0) + f[x_0, x_1, x_2](x - x_0)(x - x_1) + \dots + f[x_0, \dots, x_n] \prod_{i=0}^{n-1} (x - x_i)
$$

where $f[x_i, \dots, x_{i+k}]$ are divided differences, defined recursively:

- First divided difference: $f[x_i, x_{i+1}] = \frac{f(x_{i+1}) - f(x_i)}{x_{i+1} - x_i}$
- Higher-order: $f[x_i, \dots, x_{i+k}] = \frac{f[x_{i+1}, \dots, x_{i+k}] - f[x_i, \dots, x_{i+k-1}]}{x_{i+k} - x_i}$

**Key Features**:

- **Incremental**: Adding a new point only requires computing additional divided differences, not recomputing the entire polynomial.
- **Efficiency**: Evaluation is $\mathcal{O}(n)$ per point after computing divided differences ($\mathcal{O}(n^2)$).
- **Forms**: Forward differences are used when points are equally spaced or $x$ is near the start; backward differences when $x$ is near the end.

**Use case**: Preferred for numerical computations, especially when points are added incrementally or when the polynomial’s coefficients are needed.

## 3.5 Error Analysis in Polynomial Interpolation

The error in polynomial interpolation arises because the interpolating polynomial $P(x)$ approximates the true function $f(x)$. The error depends on the function’s smoothness and the placement of interpolation points.

**Error Formula**: For a function $f(x)$ interpolated by a polynomial $P(x)$ of degree at most $n$ at points $x_0, x_1, \dots, x_n$, the error is:

$$
f(x) - P(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!} \prod_{i=0}^n (x - x_i)
$$

where $\xi \in [a, b]$ (the interval containing $x$ and the $x_i$) is some point, and $f^{(n+1)}$ is the $(n+1)$-th derivative of $f$.

**Key Points**:

- **Error magnitude**: The error depends on:
  - The term $\frac{f^{(n+1)}(\xi)}{(n+1)!}$, which is small if $f$ is smooth (low higher derivatives) or $n$ is large.
  - The term $\prod_{i=0}^n (x - x_i)$, which is minimized by choosing points (e.g., Chebyshev nodes) that reduce this product’s maximum value.
- **Runge’s phenomenon**: For equally spaced points and high-degree polynomials, interpolation can oscillate wildly near the edges of the interval, increasing error. This is mitigated by using Chebyshev nodes.
- **Convergence**: If $f$ is sufficiently smooth and points are well-chosen, the error decreases as $n$ increases, but high-degree polynomials can be numerically unstable.

**Practical Considerations**:

- **Point placement**: Chebyshev nodes (roots of Chebyshev polynomials) minimize the maximum error compared to equally spaced points.
- **Error estimation**: If $f^{(n+1)}$ is unknown, bounds on the derivative or numerical methods (e.g., adding more points and comparing results) can estimate the error.
- **Trade-offs**: Higher-degree polynomials reduce error for smooth functions but increase computational cost and risk numerical instability.

### Summary Table

| Method             | Formula Type        | Computational Cost                                        | Adding Points               | Best Use Case                    |
| ------------------ | ------------------- | --------------------------------------------------------- | --------------------------- | -------------------------------- |
| **Lagrange**       | Explicit polynomial | $\mathcal{O}(n^2)$ per evaluation                         | Requires full recalculation | Small datasets, theoretical work |
| **Neville**        | Iterative table     | $\mathcal{O}(n^2)$ for one point                          | Easy to add points          | Single-point evaluation          |
| **Newton**         | Divided differences | $\mathcal{O}(n^2)$ setup, $\mathcal{O}(n)$ per evaluation | Incremental addition        | Numerical work, incremental data |
| **Error Analysis** | Error term          | Depends on derivative estimation                          | N/A                         | Assessing accuracy               |

---

## Key Points to Remember

- **Lagrange vs. Newton**: Lagrange is explicit, Newton is recursive and updatable. ★★★★☆
- **Neville’s Efficiency**: Builds interpolations incrementally, reducing redundant calculations. ★★★★☆
- **Error Dependency**: Higher derivatives and wider intervals increase error. ★★★☆☆
- **Divided Differences**: Key to Newton’s method; computed recursively. ★★★★★
- **Practical Trade-off**: Higher-degree polynomials improve accuracy but risk overfitting. ★★★☆☆
