## 7.1 Finite Generating Functions

### Overview
Generating functions provide a new perspective on counting problems. Using polynomial expansions, such as the Binomial Theorem:

$$(1+x)^n = \binom{n}{0} + \binom{n}{1}x + \cdots + \binom{n}{r}x^r + \cdots + \binom{n}{n}x^n,$$

coefficients of terms like $x^r$ reveal the number of ways to choose $r$ objects from $n$ objects.

### Examples
- **Example 7.1**: Choosing 2 fruits from a basket of 5 distinct fruits. Coefficient of $x^2$ in $(1+x)^5$:

  $$\binom{5}{2} = 10$$

- **Example 7.2**: A basket with 2 apples, 1 pear, 1 plum, and 1 banana. The generating function becomes:

  $$(1+x+x^2)(1+x)(1+x)(1+x) = 1+4x+7x^2+7x^3+4x^4+x^5.$$
  $$(0 \, \text{apples} + 1 \, \text{apple} + 2 \, \text{apples})(0 \, \text{pears} + 1 \, \text{pear})(0 \, \text{plums} + 1 \, \text{plum})(0 \, \text{bananas} + 1 \, \text{banana})$$

### Definition
If a finite sequence $(a_0, a_1, \ldots, a_n)$ is given such that $a_n = a_{n+1} = a_{n+2} = \ldots = 0$, the generating function is:

$$a_0 + a_1x + a_2x^2 + \ldots + a_nx^n.$$

## 7.2 Formal Power Series

### Infinite Sequences
Formal power series extend generating functions to infinite sequences, like $(a_0, a_1, \ldots)$:

$$a_0 + a_1x + a_2x^2 + \ldots$$

### Operations
1. **Addition**:
   $$(a_0 + a_1x + \ldots) + (b_0 + b_1x + \ldots) = (a_0+b_0) + (a_1+b_1)x + \ldots$$

2. **Multiplication**:
   $$(a_0 + a_1x + \ldots)(b_0 + b_1x + \ldots) = \sum_{k=0}^\infty \left(\sum_{i+j=k}a_ib_j\right)x^k.$$

## 7.3 Inverse Generating Functions

### Definition
A generating function $S = s_0 + s_1x + s_2x^2 + \ldots$ with $s_0 \neq 0$ has an inverse $T$, satisfying:

$$S \cdot T = 1.$$

### Example 7.14
Find the inverse of $S = 1+2x+3x^2+\ldots$:

1. Write $T = t_0 + t_1x + t_2x^2 + \ldots$.
2. Solve:
   $$s_0t_0 = 1, \quad s_0t_1+s_1t_0 = 0, \quad \text{etc.}$$
3. Result:
   $$S^{-1} = \frac{1}{1-2x+x^2}.$$

## 7.4 Solving Recurrence Relations

### Example 7.19: Towers of Hanoi
The recurrence for the minimum moves $h_n$ is:

$$h_n = \begin{cases} 0, & n=0, \\ 2h_{n-1} + 1, & n \geq 1. \end{cases}$$

Using generating functions, $H = \sum_{n=0}^\infty h_nx^n$:

$$H(1-2x) = x/(1-x).$$

Solution:

$$h_n = 2^n - 1.$$

## 7.5 Practice Problems

1. **Books**: Find the generating function for selecting $r$ books from 7 distinct books and 5 identical ones.
2. **Currency**: Find the generating function for spending $r$ euros using coins of 7$$, 9$$, and other denominations.
3. **Goldbach Conjecture**: Count ways to write $r = p+q$, where $p,q$ are primes.

---

## Key Points to Remember

- **Definition of Generating Functions**: Encode sequences as polynomial coefficients.
- **Finite Generating Functions**: Capture finite sequences.
- **Formal Power Series**: Extend to infinite cases, allowing algebraic operations.
- **Inverse Functions**: $S^{-1}$ exists if $s_0 \neq 0$.
- **Applications**: Solving recursions, combinatorics, number theory.
