## 3.1 Introduction to Interpolation

**Interpolation** involves constructing a function $\Phi(t)$ that passes through given data points $(t_i, y_i)$. For polynomial interpolation, $\Phi$ is a polynomial $P(t)$ of degree $n$. The **Lagrange Interpolation Formula** provides a unique polynomial $P(t)$ that fits the data exactly.

## 3.2 Lagrange Basis Polynomials

- The Lagrange basis polynomials $L_i(t)$ are defined such that $L_i(t_i) = 1$ and $L_i(t_j) = 0$ for $j \neq i$.
- The interpolating polynomial is constructed as:
  $$
  P(t) = \sum_{i=0}^n y_i L_i(t).
  $$
- **Example**: For linear interpolation ($n=1$), the formula simplifies to:
  $$
  P(t) = \frac{t - t_1}{t_0 - t_1} y_0 + \frac{t - t_0}{t_1 - t_0} y_1.
  $$

### Practical Application

- **Case Study**: Estimating temperature at $t = 18$ minutes using quadratic interpolation ($n=2$) with points $(15, 48)$, $(20, 36)$, $(25, 29)$. The result is $P(18) = 40.2$.

## 3.3 Neville’s Method

**Neville’s Method** efficiently computes interpolated values for varying degrees of polynomials using a recursive approach.

### Recursive Formula

- The method builds higher-degree polynomials from lower-degree ones:
  $$
  P_{j,\ldots,j+k}(t) = \frac{(t - t_j)P_{j+1,\ldots,j+k}(t) - (t - t_{j+k})P_{j,\ldots,j+k-1}(t)}{t_{j+k} - t_j}.
  $$
- **Advantage**: Adding new data points only requires computing a new row in the Neville table.

### Example

- For $t = 18$, the Neville table yields intermediate results like $P_{012}(18) = 42.12$ and $P_{0123}(18) = 40.872$.

## 3.4 Newton’s Interpolation Formula

**Newton’s Formula** expresses the interpolating polynomial using divided differences, making it easier to update with new data.

### Divided Differences

- The $j$-th divided difference $d_{0,\ldots,j}$ is computed recursively:
  $$
  d_{i,\ldots,i+j} = \frac{d_{i+1,\ldots,i+j} - d_{i,\ldots,i+j-1}}{t_{i+j} - t_i}.
  $$
- The polynomial is written as:
  $$
  P(t) = d_0 + d_{01}(t - t_0) + \cdots + d_{0,\ldots,n}(t - t_0)\cdots(t - t_{n-1}).
  $$

### Example

- For points $t = 10, 15, 20, 25$, the polynomial is:
  $$
  P(t) = 61 - \frac{13}{5}(t - 10) + \frac{1}{50}(t - 10)(t - 15) + \frac{2}{375}(t - 10)(t - 15)(t - 20).
  $$

## 3.5 Error Analysis in Polynomial Interpolation

**Interpolation Error** quantifies the difference between the true function $f(t)$ and the interpolating polynomial $P(t)$.

### Error Formula

- If $f$ is $(n+1)$-times differentiable, the error at $t$ is:
  $$
  r(t) = \frac{f^{(n+1)}(\tau)}{(n+1)!} \prod_{i=0}^n (t - t_i).
  $$
- **Example**: For $f(t) = \ln t$ interpolated at $t = 2, 3, 4, 5$, the error at $t = 3.5$ is bounded by:
  $$
  |r(3.5)| \leq \frac{9}{1024}.
  $$

---

## Key Points to Remember

- **Lagrange vs. Newton**: Lagrange is explicit, Newton is recursive and updatable. ★★★★☆
- **Neville’s Efficiency**: Builds interpolations incrementally, reducing redundant calculations. ★★★★☆
- **Error Dependency**: Higher derivatives and wider intervals increase error. ★★★☆☆
- **Divided Differences**: Key to Newton’s method; computed recursively. ★★★★★
- **Practical Trade-off**: Higher-degree polynomials improve accuracy but risk overfitting. ★★★☆☆
