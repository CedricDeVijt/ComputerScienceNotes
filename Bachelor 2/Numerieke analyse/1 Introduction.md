## 1.1 Foundations of Numerical Analysis

This chapter introduces the core principles of numerical analysis, focusing on calculating approximate solutions to mathematical problems, particularly through computational methods. It emphasizes the importance of understanding errors and their propagation in computations, as well as the representation of numbers in digital systems. The content provides a foundation for designing, applying, and analyzing numerical methods across various scientific and engineering fields.

### Overview of Numerical Analysis

Numerical analysis involves computing approximate solutions, denoted as $\tilde{y}$, to mathematical problems where exact solutions $y$ are often derived from equations. It is critical in fields like engineering, finance, and physics, where precise calculations drive innovation. The discipline is divided into three key areas: designing numerical methods, applying them to practical problems, and investigating their reliability through error analysis.

- **Key Idea**: Numerical methods approximate solutions when exact solutions are impractical or impossible to compute.
- **Applications**: Include electromagnetism, financial mathematics, aerospace, molecular biology, quantum physics, and weather forecasting.
- **Error Analysis**: Focuses on quantifying the reliability of $\tilde{y}$ by examining absolute and relative errors.

### Example: Volume Ratio of Spheres

Consider two perpendicular planes $V$ and $W$, and a sphere $B$ with radius 1. The goal is to find the volume ratio $y$ of the largest small sphere (radius $r$) that can pass between $V$, $W$, and $B$, relative to $B$'s volume. The solution is derived as follows:

- Volume of the small sphere: $\frac{4}{3}\pi r^3$.
- Volume of $B$: $\frac{4}{3}\pi$.
- Thus, $y = r^3$, where $r = \frac{\sqrt{2} - 1}{\sqrt{2} + 1}$.
- Equivalent expressions:
  - $y = \left( \frac{\sqrt{2} - 1}{\sqrt{2} + 1} \right)^3$,
  - $y = 99 - 70\sqrt{2}$,
  - $y = \frac{1}{99 + 70\sqrt{2}}$.
- Approximating $\sqrt{2} \approx 1.4$:
  - First expression yields $\frac{1}{216}$,
  - Second yields 1,
  - Third yields $\frac{1}{197}$.
- True value: $\frac{1}{16} < y < \frac{1}{107}$.

This example illustrates how different mathematical formulations of the same problem can yield varying numerical results due to approximation errors, highlighting the need for careful method selection.

### Components of Numerical Analysis

Numerical analysis encompasses three main activities, each critical to achieving reliable computational results:

- **Design of Numerical Methods**: Developing algorithms by mathematicians and practitioners to solve specific problems efficiently.
- **Application of Numerical Methods**: Implementing these algorithms in diverse fields to address real-world challenges.
- **Investigation of Numerical Methods**: Analyzing the reliability of computed results by studying errors, including:
  - **Absolute Error**: $|\tilde{y} - y|$,
  - **Relative Error**: $\frac{|\tilde{y} - y|}{|y|}$.
- **Error Sources**:
  - Measurement errors (e.g., in physical experiments),
  - Rounding errors (due to finite computer precision),
  - Truncation errors (e.g., approximating infinite series like $e = 1 + \frac{1}{1!} + \frac{1}{2!} + \dots$).

Numerical analysis is a dynamic field, with thousands of new publications annually and expanding software tools like MATLAB.

## 1.2 Number Representation in Computers

This section explores how numbers are stored and processed in digital computers, focusing on floating-point representation and its implications for numerical accuracy. Understanding these limitations is essential for predicting and managing computational errors.

### Floating-Point Representation

Computers represent numbers with finite precision, limiting the set of exactly representable numbers. In floating-point representation, a number $x \neq 0$ is expressed as:

$$x = \pm 0.\alpha_1 \alpha_2 \dots \alpha_t \times 10^b,$$

where:

- $\alpha_i \in \{0, 1, \dots, 9\}$, $\alpha_1 \neq 0$,
- $t$ is the fixed number of digits (precision),
- $a = \pm 0.\alpha_1 \alpha_2 \dots \alpha_t$ is the mantissa,
- $b \in \mathbb{Z}$ is the exponent.

For simplicity, the text uses base $B = 10$ (decimal), though computers typically use $B = 2$ (binary). Zero is represented as $0.\underbrace{00\dots0}_t \times 10^0$.

- **Example**: For $x = -0.73862 \times 10^2$:
  - With $t = 3$, $\tilde{x} = -0.739 \times 10^2$,
  - With $t = 4$, $\tilde{x} = -0.7386 \times 10^2$.

### Rounding and Machine Precision

When a number $x$ cannot be exactly represented, it is approximated by $\tilde{x} = \text{fl}(x)$, the closest representable number. The process involves:

- Expressing $x = \pm 0.\beta_1 \beta_2 \dots \times 10^d$, with $\beta_1 \neq 0$,
- Adding $\pm 0.\underbrace{00\dots0}_t 5 \times 10^d$,
- Truncating to $t$ digits.

The relative error in this approximation is bounded by:

$$\frac{|\text{fl}(x) - x|}{|x|} \leq \text{eps} := 5 \times 10^{-t},$$

where $\text{eps}$ is the machine precision. Thus, $\text{fl}(x) = (1 + \varepsilon)x$, with $|\varepsilon| \leq \text{eps}$.

- **Connection**: This precision limit directly impacts the reliability of numerical methods, as seen in the volume ratio example where approximations of $\sqrt{2}$ led to significant differences.

## 1.3 Error Propagation in Numerical Algorithms

This section examines how errors in input data or computations affect the final result, introducing the concept of condition numbers to quantify sensitivity. It uses practical examples to illustrate error propagation in single and multi-variable scenarios.

### Error Propagation with One Variable

Consider a function $y = f(a)$, where $\tilde{y} = f(\tilde{a})$ is computed using an approximate input $\tilde{a}$. The error in the output is:

$$\Delta y = \tilde{y} - y \approx f'(a) \Delta a,$$

where $\Delta a = \tilde{a} - a$. The relative error is:

$$\frac{\Delta y}{y} \approx \gamma \frac{\Delta a}{a}, \quad \gamma = \frac{a}{y} f'(a),$$

where $\gamma$ is the condition number, indicating the sensitivity of $y$ to changes in $a$. A large $|\gamma|$ indicates a poorly conditioned problem.

- **Example (Volume Ratio Revisited)**:
  - For $y = 99 - 70a$, with $a = \sqrt{2}$, $\tilde{a} = 1.4$:
    - $f(x) = 99 - 70x$, $f'(x) = -70$,
    - $\Delta y \approx -70 \Delta a$, with $|\Delta y| \leq 70 \times 0.05 = 3.5$,
    - $\gamma \approx -19600$, indicating poor conditioning.
  - For $y = \frac{1}{99 + 70a}$:
    - $f(x) = \frac{1}{99 + 70x}$, $f'(x) = -\frac{70}{(99 + 70x)^2}$,
    - $f'(a) \approx -0.002$, so $|\Delta y| \approx 0.002 \times 0.05 = 10^{-4}$,
    - $\gamma \approx -0.50$, indicating good conditioning.
  - **Insight**: The second formulation is more numerically stable due to a smaller condition number, explaining why $\tilde{y} = 0.005076$ is closer to the true $y$.

### Error Propagation with Multiple Variables

For operations involving multiple variables, errors propagate differently depending on the operation.

#### Multiplication

For $y = ab$, $\tilde{y} = \tilde{a} \tilde{b}$, the error is:

$$\Delta y \approx b \Delta a + a \Delta b.$$

Relative error:

$$\frac{\Delta y}{y} \approx \frac{\Delta a}{a} + \frac{\Delta b}{b},$$

with condition numbers $\gamma_a = \gamma_b = 1$, indicating good conditioning.

#### Subtraction

For $y = a - b$, $\tilde{y} = \tilde{a} - \tilde{b}$:

$$\Delta y = \Delta a - \Delta b,$$

$$\frac{\Delta y}{y} \approx \gamma_a \frac{\Delta a}{a} + \gamma_b \frac{\Delta b}{b}, \quad \gamma_a = \frac{1}{1 - b/a}, \quad \gamma_b = \frac{1}{1 - a/b}.$$

When $a \approx b$, $\gamma_a$ and $\gamma_b$ become large, indicating poor conditioning.

- **Example**: For $a = 0.621307$, $b = 0.614532$, $\tilde{a} = 0.621$, $\tilde{b} = 0.615$:
  - Product: $y = ab \approx 0.381813$, $\tilde{y} \approx 0.381915$, relative error $\approx 0.03\%$.
  - Difference: $y = a - b \approx 0.006775$, $\tilde{y} = 0.006$, relative error $\approx 11\%$.
  - **Insight**: Subtraction is poorly conditioned when inputs are close, amplifying errors.

### Computer Arithmetic Operations

In computers, arithmetic operations ($\oplus, \ominus, \otimes, \oslash$) involve rounding:

$$x \oplus y = \text{fl}(x + y), \quad x \ominus y = \text{fl}(x - y), \quad x \otimes y = \text{fl}(xy), \quad x \oslash y = \text{fl}(x/y).$$

- **Example**: For $t = 3$, $x = 0.100 \times 10^1$, $y = 0.400 \times 10^{-2}$:
  - $x + y = 0.1004 \times 10^1$, so $x \oplus y = 0.100 \times 10^1$.
  - $(x \oplus y) \oplus y = 0.100 \times 10^1$, but $y \oplus y = 0.800 \times 10^{-2}$ also results in $x \oplus (y \oplus y) = 0.101 \times 10^1$.
  - **Insight**: The order of operations affects accuracy; starting with smaller numbers often yields better results.

## 1.4 Algorithm Stability

Algorithm stability assesses how errors in inputs and computations affect the final result. A stable algorithm minimizes the impact of small errors, ensuring reliable outputs.

### Defining Stability

An algorithm $A$ computes $y$ from inputs $a, b, c, \dots$, while its computer version $\tilde{A} \equiv \text{fl}(A)$ uses approximate inputs $\tilde{a}, \tilde{b}, \tilde{c}, \dots$ and operations. Stability is defined as:

- **Stable Algorithm**: Small relative errors in inputs and operations result in a small relative error $\frac{|\tilde{y} - y|}{|y|}$.

### Example: Computing $(a + b)^2 - a^2$

Consider computing $y = (a + b)^2 - a^2 = (2a + b)b$ with $\tilde{a} = 0.897$, $\tilde{b} = 0.0014$, and $t = 3$.

#### Algorithm $A_1$: $y = (a + b)^2 - a^2$

Computer version: $\tilde{y} = (\tilde{a} \oplus \tilde{b}) \otimes (\tilde{a} \oplus \tilde{b}) \ominus (\tilde{a} \otimes \tilde{a})$.

- **Analysis**:
  - Let $c = (a + b)^2$, $\tilde{c} = (a + b) \otimes (a + b)$, $y = c - a^2$, $\tilde{y} = \tilde{c} - a^2$.
  - Relative error: $\frac{\Delta y}{y} \approx \gamma \frac{\Delta c}{c}$, where $\gamma = \frac{c}{c - a^2} \approx 321$.
  - With $|\Delta c|/|c| \leq 5 \times 10^{-3}$, $|\Delta y|/|y| \lesssim 321 \times 5 \times 10^{-3} \approx 1.6\ (160\%)$.
  - **Result**: $\tilde{y} = 0.001$, highly inaccurate due to large $\gamma$.
  - **Conclusion**: $A_1$ is unstable due to error amplification in the subtraction.

#### Algorithm $A_2$: $y = (2a + b)b$

Computer version: $\tilde{y} = [(\tilde{b} \oplus \tilde{a}) \oplus \tilde{a}] \otimes \tilde{b}$.

- **Analysis**:
  - **Input Errors**:
    - For $a$: $\gamma_a = \frac{2a}{2a + b} \approx 1$.
    - For $b$: $\gamma_b = \frac{2a + 2b}{2a + b} \approx 1$.
  - **Operation Errors**:
    - First addition ($c = a + b$): $\gamma_1 = \frac{a + b}{2a + b} \approx 0.5$.
    - Second addition: $\gamma_2 = 1$.
    - Multiplication: $\gamma_3 = 1$.
  - Total relative error: $\frac{\Delta y}{y} \approx \gamma_a \varepsilon_a + \gamma_b \varepsilon_b + \gamma_1 \varepsilon_1 + \gamma_2 \varepsilon_2 + \gamma_3 \varepsilon_3$.
  - With each $\varepsilon_i \leq 5 \times 10^{-3}$, $|\Delta y|/|y| \lesssim \frac{9}{2} \times 5 \times 10^{-3} \approx 0.0225\ (2.25\%)$.
  - **Result**: $\tilde{y} = 0.00252$, closer to the true value.
  - **Conclusion**: $A_2$ is stable, with a stability number $\sigma_2 \approx \frac{9}{2}$.

#### Stability Number

The stability number $\sigma = \sigma_G + \sigma_A$:

- $\sigma_G$: Sum of absolute condition numbers for inputs ($\gamma_a, \gamma_b, \dots$).
- $\sigma_A$: Sum of absolute condition numbers for operations.
- For $A_1$, $\sigma_1 \geq 323$ (unstable).
- For $A_2$, $\sigma_2 \approx 4.5$ (stable).

- **Insight**: $A_2$ avoids large error amplification by restructuring the computation, demonstrating the importance of algorithm design.

---

## Key Points to Remember

- **Numerical Analysis → Core Objective**: Solve mathematical problems approximately, focusing on reliability through error analysis. ★★★★☆
- **Error Types → Sources**: Measurement, rounding, and truncation errors impact computational accuracy. ★★★★☆
- **Floating-Point → Precision Limit**: Numbers are approximated as $\text{fl}(x) = (1 + \varepsilon)x$, with $|\varepsilon| \leq 5 \times 10^{-t}$. ★★★★☆
- **Condition Number → Sensitivity**: Large $|\gamma|$ indicates poor conditioning, amplifying input errors (e.g., subtraction when $a \approx b$). ★★★★★
- **Algorithm Stability → Error Control**: Stable algorithms (low $\sigma$) minimize error propagation, as seen in $A_2$ vs. $A_1$. ★★★★★
- **Common Pitfall → Operation Order**: The sequence of arithmetic operations affects accuracy; start with smaller numbers for better results. ★★★★☆
- **Critical Distinction → Formulation Choice**: Different mathematical expressions (e.g., $y = 99 - 70\sqrt{2}$ vs. $y = \frac{1}{99 + 70\sqrt{2}}$) yield different numerical stability. ★★★★★
