## 1.1 Introduction to Numerical Analysis

### Overview of Numerical Analysis

Numerical Analysis focuses on computing approximate solutions, denoted as $\tilde{y}$, to mathematical equations where the exact solution $y$ is often challenging to obtain directly. It encompasses designing, applying, and evaluating numerical methods across various fields like engineering, finance, and physics. This interdisciplinary field addresses errors such as measurement, rounding, and truncation to ensure reliable computations.

#### Core Components of Numerical Analysis

- **Design of Numerical Methods**: Involves creating algorithms by mathematicians and practitioners to solve mathematical problems efficiently.
- **Application of Numerical Methods**: Used in diverse domains like aerospace, molecular biology, and weather forecasting, often implemented through software like MATLAB.
- **Evaluation of Numerical Methods**: Focuses on assessing the reliability of computed values by analyzing **absolute error** ($\tilde{y} - y$) and **relative error** ($\frac{\tilde{y} - y}{y}$).
- **Error Sources**: Include **measurement errors** (e.g., in experiments), **rounding errors** (due to finite computer precision), and **truncation errors** (e.g., approximating infinite series like $e = 1 + \frac{1}{1!} + \frac{1}{2!} + \cdots$).

### Example: Volume Ratio of Spheres

Consider two perpendicular planes $V$ and $W$ and a sphere $B$ with radius 1. The goal is to find the ratio $y$ of the volume of the largest sphere that can roll between $V$, $W$, and $B$ to the volume of $B$. If the smaller sphere’s radius is $r$, then:

$$
y = \frac{\frac{4}{3} \pi r^3}{\frac{4}{3} \pi} = r^3
$$

Analysis yields $r = \frac{\sqrt{2} - 1}{\sqrt{2} + 1}$, so:

$$
y = \left( \frac{\sqrt{2} - 1}{\sqrt{2} + 1} \right)^3
$$

Using identities $(\sqrt{2} - 1)^6 = 99 - 70\sqrt{2}$ and $(\sqrt{2} + 1)^6 = 99 + 70\sqrt{2}$, alternative forms are:

$$
y = 99 - 70\sqrt{2} \quad \text{or} \quad y = \frac{1}{99 + 70\sqrt{2}}
$$

Approximating $\sqrt{2} \approx 1.4$ in these expressions yields varying results, highlighting the impact of computational methods on accuracy. The true value satisfies $\frac{1}{16} < y < \frac{1}{107}$.

## 1.2 Number Representation in Computers

### Floating-Point Representation

Computers represent numbers with finite precision, limiting them to a set of **representable numbers**. In **floating-point representation**, a number $x \neq 0$ is expressed as:

$$
x = \pm 0.\alpha_1 \alpha_2 \cdots \alpha_t \times B^b
$$

where $B$ is the base (typically 2 for computers, but 10 for simplicity here), $\alpha_i$ are digits, $\alpha_1 \neq 0$, $t$ is the number of digits, and $b \in \mathbb{Z}$ is the exponent. Zero is represented as $0.\underbrace{00 \cdots 0}_t \times 10^0$.

#### Rounding and Machine Precision

For a number $x = \pm 0.\beta_1 \beta_2 \cdots \times 10^d$, the computer approximates it as $\tilde{x} = \mathrm{fl}(x)$ by rounding to $t$ digits. The **relative error** in this approximation is:

$$
\frac{|\mathrm{fl}(x) - x|}{|x|} \leq \text{eps} := 5 \times 10^{-t}
$$

where $\text{eps}$ is the **machine precision**. Thus, $\mathrm{fl}(x) = (1 + \varepsilon)x$ with $|\varepsilon| \leq \text{eps}$.

#### Example: Rounding a Number

For $x = -0.73862 \times 10^2$:

- With $t = 3$, $\tilde{x} = -0.739 \times 10^2$.
- With $t = 4$, $\tilde{x} = -0.7386 \times 10^2$.
  This demonstrates how precision affects the accuracy of represented numbers.

## 1.3 Error Propagation in Algorithms

### Error Analysis for Single-Variable Dependency

When computing $y = f(a)$ but using an approximate input $\tilde{a} = \mathrm{fl}(a)$, the error $\Delta y = \tilde{y} - y$ depends on $\Delta a = \tilde{a} - a$. Using the derivative:

$$
\Delta y \approx f'(a) \Delta a
$$

The **relative error** is:

$$
\frac{\Delta y}{y} \approx \gamma \frac{\Delta a}{a}, \quad \gamma = \frac{a}{y} f'(a)
$$

where $\gamma$ is the **condition number**, indicating whether the problem is **well-conditioned** (small $|\gamma|$) or **ill-conditioned** (large $|\gamma|$).

#### Example: Error in Sphere Volume Ratio

For $y = 99 - 70\sqrt{2}$, with $\tilde{a} = 1.4 \approx \sqrt{2}$, compute $\tilde{y} = 99 - 70 \tilde{a} = 1$. Here, $f(x) = 99 - 70x$, so $f'(x) = -70$, and:

$$
\Delta y = -70 \Delta a, \quad |\Delta y| \leq 70 \times 0.05 = 3.5
$$

For $y = \frac{1}{99 + 70\sqrt{2}}$, compute $\tilde{y} = \frac{1}{99 + 70 \tilde{a}} \approx 0.005076$. Here, $f(x) = \frac{1}{99 + 70x}$, so:

$$
f'(x) = -\frac{70}{(99 + 70x)^2}, \quad f'(\sqrt{2}) \approx -0.002
$$

Thus, $|\Delta y| \approx 0.002 \times 0.05 = 10^{-4}$, indicating a smaller error. The condition numbers are:

- First expression: $\gamma \approx -19600$ (ill-conditioned).
- Second expression: $\gamma \approx -0.50$ (well-conditioned).

### Error Analysis for Multi-Variable Dependency

#### Multiplication: $y = ab$

For $\tilde{y} = \tilde{a} \tilde{b}$, the error is:

$$
\Delta y \approx b \Delta a + a \Delta b
$$

Relative error:

$$
\frac{\Delta y}{y} \approx \frac{\Delta a}{a} + \frac{\Delta b}{b}, \quad \gamma_a = \gamma_b = 1
$$

Multiplication is always **well-conditioned** ($\gamma_a = \gamma_b = 1$).

#### Subtraction: $y = a - b$

For $\tilde{y} = \tilde{a} - \tilde{b}$, the error is:

$$
\Delta y = \Delta a - \Delta b
$$

Relative error:

$$
\frac{\Delta y}{y} \approx \gamma_a \frac{\Delta a}{a} + \gamma_b \frac{\Delta b}{b}, \quad \gamma_a = \frac{1}{1 - b/a}, \quad \gamma_b = \frac{1}{1 - a/b}
$$

Subtraction is **ill-conditioned** when $a \approx b$, as $\gamma_a$ and $\gamma_b$ become large.

#### Example: Multiplication vs. Subtraction

For $a = 0.621307$, $b = 0.614532$, with $\tilde{a} = 0.621$, $\tilde{b} = 0.615$ ($t = 3$):

- **Product**: $y = ab \approx 0.381813$, $\tilde{y} = \tilde{a} \tilde{b} = 0.381915$, relative error $\approx 0.03\%$.
- **Difference**: $y = a - b \approx 0.006775$, $\tilde{y} = \tilde{a} - \tilde{b} = 0.006$, relative error $\approx 11\%$, due to $a \approx b$.

## 1.4 Computer Arithmetic Operations

### Floating-Point Arithmetic

Computer operations ($\oplus, \ominus, \otimes, \oslash$) approximate exact operations:

$$
x \oplus y = \mathrm{fl}(x + y), \quad x \ominus y = \mathrm{fl}(x - y), \quad x \otimes y = \mathrm{fl}(xy), \quad x \oslash y = \mathrm{fl}(x / y)
$$

Results may not be representable, requiring rounding.

#### Example: Non-Associative Addition

For $t = 3$, $x = 0.100 \times 10^1$, $y = 0.400 \times 10^{-2}$:

- $x \oplus y = \mathrm{fl}(0.1004 \times 10^1) = 0.100 \times 10^1 = x$.
- $(x \oplus y) \oplus y = x = 0.100 \times 10^1$.
- $y \oplus y = \mathrm{fl}(0.800 \times 10^{-2}) = 0.800 \times 10^{-2}$, so $x \oplus (y \oplus y) = 0.101 \times 10^1$.
  This shows $(x \oplus y) \oplus y \neq x \oplus (y \oplus y)$, emphasizing the importance of operation order.

## 1.5 Algorithm Stability

### Defining Stability

An algorithm $A$ computes $y$ from inputs $a, b, c, \ldots$, while its computer version $\tilde{A} = \mathrm{fl}(A)$ uses approximate operations and inputs $\tilde{a}, \tilde{b}, \tilde{c}, \ldots$. An algorithm is **stable** if small relative errors in inputs and operations result in a small relative error in $\tilde{y}$:

$$
\frac{|\tilde{y} - y|}{|y|}
$$

#### Example: Computing $y = (a + b)^2 - a^2$

For $\tilde{a} = 0.897$, $\tilde{b} = 0.0014$, $t = 3$:

- **Algorithm $A_1$**: $\tilde{y} = (\tilde{a} \oplus \tilde{b}) \otimes (\tilde{a} \oplus \tilde{b}) \ominus (\tilde{a} \otimes \tilde{a}) = 0.001$.
- **Algorithm $A_2$**: $\tilde{y} = [(\tilde{b} \oplus \tilde{a}) \oplus \tilde{a}] \otimes \tilde{b} = 0.00252$.
  Since $(a + b)^2 - a^2 = (2a + b)b$, both algorithms are mathematically equivalent, but $A_2$ is more accurate due to stability.

#### Stability Analysis of $A_1$

Let $c = (a + b)^2$, $\tilde{c} = (a + b) \otimes (a + b)$, $y = c - a^2$, $\tilde{y} = \tilde{c} - a^2$. Define $f(x) = x - a^2$. The condition number is:

$$
\gamma = \frac{c}{y} f'(c) = \frac{c}{c - a^2} \approx 321
$$

With $|\Delta c|/|c| \leq 5 \times 10^{-3}$, the relative error is:

$$
\frac{|\Delta y|}{|y|} \lesssim 321 \times 5 \times 10^{-3} \approx 1.6
$$

Thus, $A_1$ is **unstable** due to a large condition number.

#### Stability Analysis of $A_2$

For $y = (2a + b)b$, consider errors in inputs and operations:

- **Input $a$**: $\gamma_a = \frac{2a}{2a + b} \approx 1$.
- **Input $b$**: $\gamma_b = \frac{2a + 2b}{2a + b} \approx 1$.
- **First addition**: $\gamma_1 = \frac{a + b}{2a + b} \approx 0.5$.
- **Second addition**: $\gamma_2 = 1$.
- **Multiplication**: $\gamma_3 = 1$.
  Total relative error:
  $$
  \frac{|\Delta y|}{|y|} \lesssim \left( |\gamma_a| + |\gamma_b| + |\gamma_1| + |\gamma_2| + |\gamma_3| \right) \varepsilon \approx \frac{9}{2} \varepsilon
  $$
  The **stability number** $\sigma_2 \approx \frac{9}{2}$, compared to $\sigma_1 \geq 323$ for $A_1$, confirms $A_2$ is more stable.

### Stability Number

The stability number $\sigma = \sigma_G + \sigma_A$ measures:

- **$\sigma_G$**: Sensitivity to input errors (sum of absolute condition numbers).
- **$\sigma_A$**: Sensitivity to operational errors in $\tilde{A}$.

---

## Key Points to Remember

- **Numerical Analysis → Core Focus**: Solving mathematical equations approximately, addressing errors from measurement, rounding, and truncation. ★★★★☆
- **Floating-Point → Precision Limits**: Numbers are represented with finite digits, leading to rounding errors bounded by machine precision $\text{eps} = 5 \times 10^{-t}$. ★★★★☆
- **Error Propagation → Condition Number**: Large $|\gamma|$ indicates an ill-conditioned problem, amplifying input errors, as seen in subtraction when $a \approx b$. ★★★★★
- **Arithmetic Operations → Non-Associative**: Computer operations like $\oplus$ are not associative, affecting accuracy based on operation order. ★★★☆☆
- **Algorithm Stability → Stability Number**: Stable algorithms (low $\sigma$) minimize error amplification from inputs and operations, e.g., $A_2$ over $A_1$. ★★★★★
- **Common Pitfall → Ill-Conditioned Problems**: Expressions like $y = 99 - 70\sqrt{2}$ can yield large errors due to high condition numbers. ★★★★☆
- **Critical Distinction → Multiplication vs. Subtraction**: Multiplication is inherently well-conditioned ($\gamma = 1$), while subtraction is ill-conditioned when inputs are close. ★★★★☆
