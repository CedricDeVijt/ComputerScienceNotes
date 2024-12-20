## 4.1 Basic Techniques
1. **Sum Rule**  
   - If there are $n(A)$ ways to perform $A$ and $n(B)$ ways to perform $B$, then there are **$n(A) + n(B)$** ways to perform **$A$ OR $B$**.

2. **Product Rule**  
   - If there are $n(A)$ ways to perform $A$ and $n(B)$ ways to perform $B$ independently, then there are **$n(A) \times n(B)$** ways to perform **$A$ AND $B$**.

3. **Division Rule**  
   - Given a $k:1$ correspondence between objects of types $A$ and $B$ with $n(A)$ objects of type $A$, there are **$n(A) / k = n(B)$** objects of type $B$.

## 4.2 Inclusion-Exclusion Principle
1. **Two Sets**  
   - For sets $A$ and $B$:  
     $|A \cup B| = |A| + |B| - |A \cap B|$

2. **Three Sets**  
   - For sets $A$, $B$, and $C$:  
     $|A \cup B \cup C| = |A| + |B| + |C| - |A \cap B| - |A \cap C| - |B \cap C| + |A \cap B \cap C|$

3. **General Formula**  
   - For $n$ sets $A_1, A_2, \ldots, A_n$:  
     $\left| \bigcup_{i=1}^n A_i \right| = \sum_{i=1}^n |A_i| - \sum_{i<j} |A_i \cap A_j| + \sum_{i<j<k} |A_i \cap A_j \cap A_k| - \dots + (-1)^{n+1} |A_1 \cap A_2 \cap \dots \cap A_n|$

## 4.3 Decision Trees
- **Example 4.8**: Decision trees can illustrate all possible outcomes of a series of choices. For instance, a staircase problem where each step can be climbed in several different ways can be visualized as a decision tree, helping to count total unique paths.

## 4.4 Permutations and Combinations
1. **Variation**  
   - Choosing $k$ elements from $n$ with order important and no repetition:  
     $V^k_n = \frac{n!}{(n-k)!}$
   - **Permutation**: A variation where $k = n$, hence $P_n = n!$.
2. **Repeated Variation**  
   - Choosing $k$ elements from $n$ with order important and repetition allowed:  
     $V^k_n = n^k$
3. **Combination**  
   - Choosing $k$ elements from $n$ without considering order and without repetition:  
     $C^k_n = \binom{n}{k} = \frac{n!}{k!(n-k)!}$
4. **Repeated Combination**  
   - Choosing $k$ elements from $n$ without considering order and with repetition:  
     $D^k_n = C^k_n = \binom{n+k-1}{k} = \frac{(n+k-1)!}{k!(n-1)!}$
5. **Repeated Permutation**  
   - Choosing $k_1, k_2, \ldots, k_r$ elements from $n$ types, considering order within each type irrelevant:  
     $P^{k_1, \ldots, k_r}_n = \frac{n!}{k_1! k_2! \dots k_r!}$

|                              | **Order Important**      | **Order Not Important**    |
|------------------------------|--------------------------|----------------------------|
| **Repetition Allowed**       | $V^k_n = n^k$           | $D^k_n = \binom{n+k-1}{k}$ |
| **Repetition Not Allowed**   | $V^k_n = \frac{n!}{(n-k)!}$ | $C^k_n = \binom{n}{k} = \frac{n!}{k!(n-k)!}$ |


## 4.6 Special Forms of Binomial Coefficients
- The **Binomial Coefficient** $\binom{n}{k} = \frac{n!}{k!(n-k)!}$ can be generalized for non-integer values using factorial and other combinatorial techniques.

## 4.7 Combinatorial Identities
1. **Symmetry Property**  
   - For any $n$ and $k$:  
     $\binom{n}{k} = \binom{n}{n-k}$

2. **Pascal's Identity**  
   - $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$

3. **Subset Sum**  
   - The sum of binomial coefficients for all subsets:  
     $\sum_{k=0}^n \binom{n}{k} = 2^n$

## 4.8 Newton's Binomial Theorem
1. **Newton’s Binomial Theorem (Theorem 4.24)**  
   - For $(x + y)^n$:  
     $(x + y)^n = \sum\limits_{k=0}^n \binom{n}{k} x^k y^{n-k}$

2. **Multinomial Theorem (Theorem 4.26)**  
   - For more than two terms $(x_1 + x_2 + \dots + x_r)^n$:  
     $(x_1 + x_2 + \dots + x_r)^n = \sum_{n_1 + n_2 + \dots + n_r = n} \binom{n}{n_1, n_2, \dots, n_r} x_1^{n_1} x_2^{n_2} \dots x_r^{n_r}$

---

# Key Points to Remember

- **Sum Rule** and **Product Rule** are foundational counting techniques.
- **Inclusion-Exclusion Principle** helps avoid double-counting in unions of sets.
- **Decision Trees** are useful for visualizing possible combinations.
- **Permutations and Combinations** cover ordered and unordered selections with and without repetition.
- **Binomial Coefficients** represent ways to choose subsets and have numerous properties.
- **Newton’s Binomial Theorem** expands powers of sums into individual terms.