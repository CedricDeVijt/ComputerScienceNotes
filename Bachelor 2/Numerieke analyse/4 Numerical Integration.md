## 4.1 **Trapezoidal Rule**

The Trapezoidal Rule is a numerical method to approximate the definite integral of a function $f(x)$ over an interval $[a, b]$. It works by approximating the area under the curve as a series of trapezoids.

- **How it works**: Divide the interval $[a, b]$ into $n$ subintervals of width $h = \frac{b-a}{n}$. At each subinterval $[x_i, x_{i+1}]$, approximate the area under $f(x)$ as a trapezoid with height $h$ and bases $f(x_i)$ and $f(x_{i+1})$. The area of each trapezoid is $\frac{h}{2} [f(x_i) + f(x_{i+1})]$.
- **Formula**:
  $$
  \int_a^b f(x) \, dx \approx \frac{h}{2} \left[ f(x_0) + 2 \sum_{i=1}^{n-1} f(x_i) + f(x_n) \right]
  $$
  where $x_i = a + i h$.
- **Error**: The error is proportional to $h^2$, specifically $O(h^2)$, assuming $f(x)$ is twice differentiable. The error term is:
  $$
  -\frac{(b-a) h^2}{12} f''(\xi), \quad \xi \in [a, b]
  $$
- **Use**: Simple and effective for smooth functions but less accurate than higher-order methods.

## 4.2 **Regel of Simpson (Simpson’s Rule)**

Simpson’s Rule (often called "Regel of Simpson" in some contexts) is a more accurate numerical integration method that approximates the integrand with quadratic polynomials instead of straight lines.

- **How it works**: Divide $[a, b]$ into $n$ (even) subintervals of width $h = \frac{b-a}{n}$. For each pair of subintervals $[x_{i-2}, x_i]$, fit a quadratic polynomial through three points $(x_{i-2}, f(x_{i-2})), (x_{i-1}, f(x_{i-1})), (x_i, f(x_i))$ and compute the area under this parabola.
- **Formula**:
  $$
  \int_a^b f(x) \, dx \approx \frac{h}{3} \left[ f(x_0) + 4 \sum_{\text{odd } i} f(x_i) + 2 \sum_{\text{even } i} f(x_i) + f(x_n) \right]
  $$
- **Error**: The error is proportional to $h^4$, specifically $O(h^4)$, assuming $f(x)$ is four times differentiable. The error term is:
  $$
  -\frac{(b-a) h^4}{180} f^{(4)}(\xi), \quad \xi \in [a, b]
  $$
- **Use**: More accurate than the Trapezoidal Rule, especially for smooth functions, but requires an even number of subintervals.

## 4.3 **Extended Trapezoidal Rule**

The Extended Trapezoidal Rule refers to applying the Trapezoidal Rule over multiple subintervals to improve accuracy by reducing the step size $h$.

- **How it works**: Instead of approximating the integral over $[a, b]$ with one trapezoid, divide the interval into $n$ smaller subintervals and sum the areas of the trapezoids. This is essentially the Trapezoidal Rule formula above, but "extended" emphasizes its application over many subintervals.
- **Formula**: Same as the Trapezoidal Rule:
  $$
  \frac{h}{2} \left[ f(x_0) + 2 \sum_{i=1}^{n-1} f(x_i) + f(x_n) \right]
  $$
- **Error**: Decreases as $n$ increases (since $h = \frac{b-a}{n}$), with error $O(h^2)$. Increasing $n$ reduces $h$, improving accuracy.
- **Use**: Common in numerical integration for its simplicity, especially when combined with techniques like Richardson extrapolation to enhance accuracy.

## 4.4 **Extended Regel of Simpson (Extended Simpson’s Rule)**

The Extended Simpson’s Rule applies Simpson’s Rule over multiple pairs of subintervals to approximate the integral with higher accuracy.

- **How it works**: Divide $[a, b]$ into $n$ (even) subintervals and apply Simpson’s Rule across each pair of subintervals. This is the standard Simpson’s Rule formula but applied systematically over many subintervals.
- **Formula**: Same as Simpson’s Rule:
  $$
  \frac{h}{3} \left[ f(x_0) + 4 \sum_{\text{odd } i} f(x_i) + 2 \sum_{\text{even } i} f(x_i) + f(x_n) \right]
  $$
- **Error**: Decreases as $O(h^4)$, making it more accurate than the Extended Trapezoidal Rule for the same $n$. Increasing $n$ further reduces the error.
- **Use**: Preferred for functions with smooth behavior due to its higher accuracy compared to the Trapezoidal Rule.

## 4.5 **Extrapolation to $h = 0$** (Richardson Extrapolation)

Extrapolation to $h = 0$ is a technique, often called Richardson extrapolation, used to improve the accuracy of numerical integration methods like the Trapezoidal or Simpson’s Rule by eliminating lower-order error terms.

- **How it works**: Compute the integral using a method (e.g., Trapezoidal Rule) with step sizes $h_1$ and $h_2$ (e.g., $h_2 = h_1/2$). The error in these methods depends on powers of $h$. By combining results, you can cancel out the leading error term to obtain a more accurate estimate.
- **For Trapezoidal Rule**:
  - Let $T(h)$ be the Trapezoidal Rule approximation with step size $h$. The error is $T(h) = I + c h^2 + O(h^4)$, where $I$ is the true integral.
  - Compute $T(h)$ and $T(h/2)$. The extrapolated estimate is:
    $$
    T_{\text{extrap}} = \frac{4 T(h/2) - T(h)}{4 - 1} = T(h/2) + \frac{T(h/2) - T(h)}{3}
    $$
  - This eliminates the $h^2$ error term, yielding an $O(h^4)$ accurate result, similar to Simpson’s Rule.
- **For Simpson’s Rule**:
  - Simpson’s Rule is already $O(h^4)$. Extrapolation combines results from two step sizes to eliminate the $h^4$ term, yielding an $O(h^6)$ accurate result.
  - Formula:
    $$
    S_{\text{extrap}} = \frac{16 S(h/2) - S(h)}{16 - 1} = S(h/2) + \frac{S(h/2) - S(h)}{15}
    $$
- **Use**: Significantly improves accuracy without requiring more function evaluations. Commonly used in Romberg integration, which repeatedly applies extrapolation to achieve higher-order accuracy.

## 4.6 Summary

- **Trapezoidal Rule**: Approximates integrals using trapezoids, $O(h^2)$ error.
- **Simpson’s Rule**: Uses quadratic polynomials, $O(h^4)$ error, more accurate.
- **Extended versions**: Apply these rules over many subintervals to reduce $h$ and improve accuracy.
- **Extrapolation to $h = 0$**: Combines results from different step sizes to eliminate error terms, achieving higher accuracy (e.g., $O(h^4)$ for Trapezoidal, $O(h^6)$ for Simpson’s).

If you’d like a specific example, chart, or deeper mathematical derivation for any of these methods, let me know!
