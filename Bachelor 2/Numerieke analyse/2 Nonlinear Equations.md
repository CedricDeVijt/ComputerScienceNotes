## 2.1 Introduction to Nonlinear Problems

Nonlinear equations model complex phenomena like population growth, where analytical solutions are often impossible. The chapter introduces numerical methods (bisection, Newton, secant, fixed-point iteration) to approximate roots of equations like:
$$N(t) = N_0 e^{\lambda t} + \nu \frac{e^{\lambda t} - 1}{\lambda}.$$
**Key challenge**: Error propagation in input parameters (e.g., initial population $N_0$) affects solution accuracy.

### Population Growth Example

Given $N(0)=1,000,000$, $N(1)=1,264,000$, and $\nu=35,000$, find $\lambda$:
$$1,264,000 = 1,000,000 e^{\lambda} + 35,000 \frac{e^{\lambda} - 1}{\lambda}.$$
Numerical methods are essential here due to the transcendental nature of the equation.

## 2.2 Bisection Method

The **Bisection Method** is a numerical technique used to find the root of a continuous function $f(x)$ within a given interval $[a, b]$, where a root is a value $x$ such that $f(x) = 0$. It relies on the **Intermediate Value Theorem**, which states that if $f(a)$ and $f(b)$ have opposite signs (i.e., $f(a) \cdot f(b) < 0$), then there is at least one root in $[a, b]$.

### How the Bisection Method Works

The method systematically narrows down the interval containing the root by repeatedly dividing it in half. Here’s a step-by-step explanation:

1. **Choose an Interval**: Select an interval $[a, b]$ where $f(a)$ and $f(b)$ have opposite signs ($f(a) \cdot f(b) < 0$). This ensures at least one root exists in the interval.

2. **Calculate the Midpoint**: Compute the midpoint $c = \frac{a + b}{2}$.

3. **Evaluate the Function at the Midpoint**: Compute $f(c)$.

   - If $f(c) = 0$ (or is sufficiently close to 0 within a desired tolerance), then $c$ is the root, and the process stops.
   - If $f(a) \cdot f(c) < 0$, the root lies in $[a, c]$. Update the interval by setting $b = c$.
   - If $f(c) \cdot f(b) < 0$, the root lies in $[c, b]$. Update the interval by setting $a = c$.

4. **Repeat**: Return to step 2 with the new, smaller interval $[a, b]$ and continue iterating until the interval is sufficiently small (e.g., $|b - a| < \epsilon$, where $\epsilon$ is a specified tolerance) or $f(c)$ is close enough to 0.

5. **Output the Approximation**: The final midpoint $c$ is an approximation of the root.

### Key Features

- **Convergence**: The Bisection Method is guaranteed to converge to a root if the function is continuous and the initial interval contains a root. The interval halves with each iteration, so the error is reduced by half each step.
- **Error Bound**: After $n$ iterations, the error is at most $\frac{b - a}{2^{n+1}}$.
- **Advantages**:
  - Simple and robust.
  - Guaranteed convergence for continuous functions with a root in the interval.
- **Disadvantages**:
  - Slow convergence compared to other methods (e.g., Newton-Raphson), as it reduces the error linearly.
  - Requires the function to be continuous and the initial interval to contain a root.
  - Cannot directly handle multiple roots or discontinuities.

### Example

Suppose we want to find a root of $f(x) = x^2 - 4$ in the interval $[1, 3]$.

- **Step 1**: Check signs: $f(1) = 1^2 - 4 = -3$, $f(3) = 3^2 - 4 = 5$. Since $f(1) \cdot f(3) = -3 \cdot 5 < 0$, a root exists in $[1, 3]$.
- **Step 2**: Compute midpoint: $c = \frac{1 + 3}{2} = 2$.
- **Step 3**: Evaluate $f(2) = 2^2 - 4 = 0$. Since $f(2) = 0$, the root is exactly $x = 2$, and we stop.
- If $f(c) \neq 0$, we would check the subintervals $[1, 2]$ or $[2, 3]$ based on the sign of $f(c)$ and continue.

### Practical Considerations

- **Stopping Criteria**: Stop when the interval size $|b - a|$ is smaller than a tolerance $\epsilon$, or when $|f(c)|$ is sufficiently small.
- **Limitations**: The method may fail if the function is not continuous or if the initial interval does not bracket a root. It also struggles with functions that are flat near the root (slowing convergence).

This method is widely used in numerical analysis due to its simplicity and reliability, especially when a good initial guess for faster methods is unavailable.

## 2.3 Newton's Method

**Newton's Method** (also called the Newton-Raphson Method) is a numerical technique for finding the roots of a differentiable function $f(x)$, where a root is a value $x$ such that $f(x) = 0$. It uses the function's derivative to iteratively approximate the root, converging faster than methods like the Bisection Method under favorable conditions.

### How Newton's Method Works

The method starts with an initial guess and refines it using the tangent line to the function at each step. Here’s the process:

1. **Choose an Initial Guess**: Select an initial approximation $x_0$ close to the suspected root.

2. **Iterate Using the Formula**: Compute the next approximation using the formula:

   $$
   x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
   $$

   where $f(x_n)$ is the function value at $x_n$, and $f'(x_n)$ is the derivative of $f$ at $x_n$.

3. **Check for Convergence**: Repeat the iteration until the difference between successive approximations $|x_{n+1} - x_n|$ is smaller than a specified tolerance $\epsilon$, or $|f(x_{n+1})|$ is sufficiently close to 0.

4. **Output the Approximation**: The final $x_{n+1}$ is the approximate root.

### Geometric Interpretation

Newton's Method approximates the root by following the tangent line at $x_n$ to where it intersects the x-axis. The point of intersection becomes $x_{n+1}$. This process leverages the local linearity of the function near the root.

### Key Features

- **Convergence**:
  - Newton's Method typically exhibits **quadratic convergence** near the root, meaning the number of correct digits roughly doubles with each iteration, making it much faster than the Bisection Method.
  - Convergence is not guaranteed unless the initial guess is sufficiently close to the root, the function is differentiable, and $f'(x) \neq 0$ near the root.
- **Advantages**:
  - Fast convergence for well-behaved functions (smooth, with non-zero derivatives near the root).
  - Highly accurate with fewer iterations compared to linear methods like Bisection.
- **Disadvantages**:
  - Requires the derivative $f'(x)$, which may be difficult or expensive to compute.
  - May fail if:
    - The initial guess is far from the root.
    - $f'(x_n) = 0$ or is very small (causing division issues or instability).
    - The function has discontinuities, multiple roots, or oscillatory behavior.
  - Sensitive to the choice of initial guess, potentially leading to divergence or convergence to a different root.

### Example

Find a root of $f(x) = x^2 - 4$ with initial guess $x_0 = 3$.

- Compute the derivative: $f'(x) = 2x$.
- **Iteration 1**:
  - $f(3) = 3^2 - 4 = 5$, $f'(3) = 2 \cdot 3 = 6$.
  - $x_1 = 3 - \frac{5}{6} = 3 - 0.8333 \approx 2.1667$.
- **Iteration 2**:
  - $f(2.1667) = 2.1667^2 - 4 \approx 0.6944$, $f'(2.1667) = 2 \cdot 2.1667 \approx 4.3334$.
  - $x_2 = 2.1667 - \frac{0.6944}{4.3334} \approx 2.1667 - 0.1603 \approx 2.0064$.
- **Iteration 3**:
  - $f(2.0064) \approx 0.0256$, $f'(2.0064) \approx 4.0128$.
  - $x_3 = 2.0064 - \frac{0.0256}{4.0128} \approx 2.0000$.
- Since $f(2.0000) = 0$, the root is $x = 2$.

### Practical Considerations

- **Stopping Criteria**: Stop when $|x_{n+1} - x_n| < \epsilon$ or $|f(x_{n+1})| < \epsilon$, where $\epsilon$ is the tolerance.
- **Derivative Issues**: If the derivative is hard to compute analytically, numerical approximations can be used, but this may reduce accuracy.
- **Failure Cases**: The method can oscillate, diverge, or converge to a wrong root if the initial guess is poor or the function is ill-behaved (e.g., near a horizontal tangent or multiple roots).
- **Improvements**: Combining Newton’s Method with a slower but more robust method (like Bisection) can ensure convergence by first bracketing the root.

Newton's Method is widely used in numerical analysis for its speed and efficiency when conditions are favorable, but careful selection of the initial guess and understanding of the function's behavior are critical for success.

## 2.4 Secant Method

The **Secant Method** is a numerical technique for finding the roots of a function $f(x)$, where a root is a value $x$ such that $f(x) = 0$. It is a derivative-free alternative to Newton's Method, approximating the derivative using two points and iteratively refining the root estimate. It’s useful when the derivative $f'(x)$ is difficult to compute or unavailable.

### How the Secant Method Works

The method uses two initial guesses and approximates the root by drawing a secant line (a straight line through two points on the function) and finding where it crosses the x-axis. Here’s the step-by-step process:

1. **Choose Two Initial Guesses**: Select two initial points, $x_0$ and $x_1$, preferably close to the root.

2. **Compute the Next Approximation**: Use the secant line formula to find the next approximation $x_2$:

   $$
   x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}
   $$

   This formula comes from the slope of the secant line between points $(x_{n-1}, f(x_{n-1}))$ and $(x_n, f(x_n))$, which approximates the derivative.

3. **Iterate**: Update the points by setting $x_{n-1} = x_n$ and $x_n = x_{n+1}$, then repeat step 2 until the difference $|x_{n+1} - x_n|$ is smaller than a specified tolerance $\epsilon$, or $|f(x_{n+1})|$ is sufficiently close to 0.

4. **Output the Approximation**: The final $x_{n+1}$ is the approximate root.

### Geometric Interpretation

The Secant Method approximates the root by drawing a secant line through the points $(x_{n-1}, f(x_{n-1}))$ and $(x_n, f(x_n))$. The x-intercept of this line becomes the next guess $x_{n+1}$. This process repeats, with each iteration using the two most recent points to form a new secant line.

### Key Features

- **Convergence**:
  - The Secant Method typically converges faster than the Bisection Method but slower than Newton's Method. Its convergence is **superlinear**, with an order of approximately 1.618 (the golden ratio), meaning the number of correct digits grows faster than linearly but not quite quadratically.
  - Convergence is not guaranteed unless the initial guesses are close to the root and the function is well-behaved (continuous and differentiable near the root).
- **Advantages**:
  - Does not require computing the derivative, unlike Newton's Method.
  - Simpler to implement when the derivative is complex or unavailable.
- **Disadvantages**:
  - Requires two initial guesses, which may need to bracket the root for better convergence.
  - Can diverge or oscillate if the initial guesses are poor or if $f(x_n) - f(x_{n-1}) \approx 0$, making the denominator small.
  - Less robust than the Bisection Method, as it doesn’t guarantee convergence without proper conditions.
  - May struggle with functions that are flat or have multiple roots.

### Example

Find a root of $f(x) = x^2 - 4$ with initial guesses $x_0 = 1$ and $x_1 = 3$.

- **Iteration 1**:
  - $f(x_0) = f(1) = 1^2 - 4 = -3$, $f(x_1) = f(3) = 3^2 - 4 = 5$.
  - Compute $x_2$:
    $$
    x_2 = 3 - \frac{5 \cdot (3 - 1)}{5 - (-3)} = 3 - \frac{5 \cdot 2}{8} = 3 - 1.25 = 1.75
    $$
- **Iteration 2**:
  - $f(x_1) = f(3) = 5$, $f(x_2) = f(1.75) = 1.75^2 - 4 = 3.0625 - 4 = -0.9375$.
  - Compute $x_3$:
    $$
    x_3 = 1.75 - \frac{-0.9375 \cdot (1.75 - 3)}{-0.9375 - 5} = 1.75 - \frac{-0.9375 \cdot (-1.25)}{-5.9375} \approx 1.75 + 0.1974 \approx 1.9474
    $$
- **Iteration 3**:
  - $f(x_2) = f(1.75) = -0.9375$, $f(x_3) = f(1.9474) \approx 1.9474^2 - 4 \approx -0.2088$.
  - Compute $x_4$:
    $$
    x_4 \approx 1.9474 - \frac{-0.2088 \cdot (1.9474 - 1.75)}{-0.2088 - (-0.9375)} \approx 1.9998
    $$
- Since $x_4 \approx 2$ and $f(2) = 0$, the root is approximately $x = 2$.

### Practical Considerations

- **Stopping Criteria**: Stop when $|x_{n+1} - x_n| < \epsilon$ or $|f(x_{n+1})| < \epsilon$, where $\epsilon$ is the tolerance.
- **Initial Guesses**: Choosing points that bracket the root (i.e., $f(x_0) \cdot f(x_1) < 0$) can improve convergence, but it’s not strictly required.
- **Failure Cases**: The method may fail if:
  - The denominator $f(x_n) - f(x_{n-1})$ is close to 0.
  - The initial guesses are far from the root or in a region where the function is not well-behaved.
  - The function has discontinuities or multiple roots.
- **Comparison to Newton’s Method**: The Secant Method avoids derivative calculations but may require more iterations and is less stable in some cases.

The Secant Method is a practical choice for root-finding when derivatives are unavailable or costly, offering a balance between simplicity and convergence speed, though it requires careful selection of initial guesses to ensure reliability.

## 2.5 Fixed-Point Iteration

**Fixed-Point Iteration** is a numerical method used to find the roots of a function $f(x) = 0$ by reformulating it as a fixed-point problem. A fixed point of a function $g(x)$ is a value $x$ such that $x = g(x)$. The method iteratively applies a function $g(x)$ to an initial guess to converge to a fixed point, which corresponds to a root of the original equation.

### How Fixed-Point Iteration Works

The goal is to solve $f(x) = 0$ by rewriting it in the form $x = g(x)$, where $g(x)$ is a function derived from $f(x)$. The steps are:

1. **Rewrite the Equation**: Transform $f(x) = 0$ into $x = g(x)$. For example, if $f(x) = x^2 - x - 2$, you might rewrite it as $x = x^2 - 2$ or $x = \sqrt{x + 2}$, so $g(x) = x^2 - 2$ or $g(x) = \sqrt{x + 2}$. The choice of $g(x)$ affects convergence.

2. **Choose an Initial Guess**: Select an initial approximation $x_0$, ideally close to the fixed point.

3. **Iterate**: Compute the next approximation using:

   $$
   x_{n+1} = g(x_n)
   $$

   Repeat this process, generating a sequence $x_0, x_1, x_2, \dots$.

4. **Check for Convergence**: Continue iterating until the difference between successive approximations $|x_{n+1} - x_n|$ is smaller than a specified tolerance $\epsilon$, or $|f(x_{n+1})|$ is sufficiently small (indicating proximity to the root of $f(x)$).

5. **Output the Approximation**: The final $x_{n+1}$ is the approximate fixed point, which should satisfy $f(x) = 0$.

### Convergence

- **Condition for Convergence**: The method converges to a fixed point $x^*$ (where $x^* = g(x^*)$) if:
  - $g(x)$ is continuous in a neighborhood of $x^*$.
  - The initial guess $x_0$ is sufficiently close to $x^*$.
  - The derivative $|g'(x^*)| < 1$, ensuring the iteration contracts toward the fixed point (a "contractive mapping").
- **Convergence Rate**: If $g'(x^*) \neq 0$, convergence is **linear**, with the error decreasing proportionally each step. If $g'(x^*) = 0$, convergence can be superlinear or quadratic, depending on higher derivatives.
- **Divergence**: If $|g'(x^*)| > 1$, the iteration may diverge. If $g'(x^*) = 1$, convergence is not guaranteed and depends on higher-order behavior.

### Key Features

- **Advantages**:
  - Simple to implement, requiring only function evaluations (no derivatives, unlike Newton’s Method).
  - Flexible, as there are often multiple ways to define $g(x)$ for a given $f(x)$.
- **Disadvantages**:
  - Convergence is not guaranteed and depends heavily on the choice of $g(x)$ and the initial guess.
  - Typically slower than Newton’s Method (linear vs. quadratic convergence in most cases).
  - May fail if $|g'(x)| \geq 1$ near the fixed point or if the initial guess is too far away.
- **Comparison to Other Methods**:
  - Unlike the Bisection Method, it doesn’t require bracketing the root but is less robust.
  - Unlike Newton’s Method, it doesn’t need derivatives but is generally slower.
  - Similar to the Secant Method in being derivative-free but uses only one point per iteration.

### Example

Solve $f(x) = x^2 - x - 2 = 0$ using fixed-point iteration with $g(x) = x^2 - 2$. The root corresponds to $x = g(x)$, and let’s try initial guess $x_0 = 2$.

- **Iteration 1**: $x_1 = g(x_0) = 2^2 - 2 = 2$.
- **Iteration 2**: $x_2 = g(x_1) = 2^2 - 2 = 2$.
- This iteration stalls at $x = 2$, which is a root since $f(2) = 2^2 - 2 - 2 = 0$.

Now try a different $g(x) = \sqrt{x + 2}$ with $x_0 = 1$:

- **Iteration 1**: $x_1 = g(1) = \sqrt{1 + 2} = \sqrt{3} \approx 1.732$.
- **Iteration 2**: $x_2 = g(1.732) = \sqrt{1.732 + 2} = \sqrt{3.732} \approx 1.932$.
- **Iteration 3**: $x_3 = g(1.932) = \sqrt{3.932} \approx 1.983$.
- Continue until convergence to $x \approx 2$, a root of $f(x) = 0$.
- Check convergence: For $g(x) = \sqrt{x + 2}$, the derivative is $g'(x) = \frac{1}{2\sqrt{x + 2}}$. At $x = 2$, $g'(2) = \frac{1}{2\sqrt{4}} = 0.25 < 1$, so convergence is expected near $x = 2$.

### Practical Considerations

- **Choosing $g(x)$**: The function $g(x)$ must be chosen such that $|g'(x)| < 1$ near the fixed point. Poor choices can lead to slow convergence or divergence.
- **Stopping Criteria**: Stop when $|x_{n+1} - x_n| < \epsilon$ or $|f(x_{n+1})| < \epsilon$.
- **Failure Cases**: The method fails if:
  - $|g'(x^*)| \geq 1$, causing divergence.
  - The initial guess is too far from the fixed point.
  - $g(x)$ is not well-defined or discontinuous.
- **Modifications**: Techniques like relaxation (e.g., $x_{n+1} = \alpha g(x_n) + (1 - \alpha) x_n$) can improve convergence for some functions.

### Visualizing Convergence (Optional Chart)

If you’d like, I can generate a chart to show how the sequence $x_n$ converges to the fixed point for the example above (e.g., using $g(x) = \sqrt{x + 2}$). Would you like me to create such a chart?

Fixed-Point Iteration is a versatile method for root-finding, valued for its simplicity and lack of derivative requirements, but its success depends critically on the choice of $g(x)$ and the initial guess.

---

## Key Points to Remember

- **Bisection → Guaranteed Convergence** (★★★☆☆): Always finds a root but slowly. Use for initial approximations.
- **Newton → Speed vs Stability Tradeoff** (★★★★☆): Quadratic convergence but sensitive to $x_0$ and requires $F'$.
- **Secant → Balanced Approach** (★★★☆☆): No derivative needed; faster than bisection but less robust than Newton.
- **Fixed-Point → Flexibility** (★★★☆☆): Generalizes to multi-dimensional problems but requires contraction.
- **Error Propagation**: Input errors (e.g., $\Delta w = 0.5$) amplify via $f'(u)$, limiting solution precision.
