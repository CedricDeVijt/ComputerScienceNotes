# 1 Bayesian Networks
## Factorization
a) Each variable has 2 possible states (binary). For 5 binary variables, there are $2^5 = 32$ entries in the joint probability table. Since the probabilities must sum to 1, we need **31** independent values to fully specify $P(O, G, S, F, I)$.

b) Using the Bayesian network structure the factorization of $P(O, G, S, F, I)$ is derived by applying the chain rule and using the conditional independencies encoded in the network:
$P(O, G, S, F, I) = P(G) \cdot P(S) \cdot P(O \mid G, S) \cdot P(F \mid S) \cdot P(I \mid O, F)$.

c) Each conditional probability table must be calculated based on the number of parent configurations for a node:
1. $P(G)$: $2 - 1 = 1$ value (1 binary variable).
2. $P(S)$: $2 - 1 = 1$ value.
3. $P(O \mid G, S)$: $2^2 \cdot (2 - 1) = 4$ values (2 parents, binary each).
4. $P(F \mid S)$: $2 \cdot (2 - 1) = 2$ values (1 parent).
5. $P(I \mid O, F)$: $2^2 \cdot (2 - 1) = 4$ values (2 parents).

Thus, the minimum number of probabilistic values required is **12**.

## Probability

a) $P(+b \mid +a)=0.5$
b) $P(+a, +b)= P(+a) \cdot P(+b \mid +a)= 0.25⋅0.5=0.125$
c) $P(+a \mid +b)= \frac{P(+a, +b)}{P(+b)}$
d) $P(−e, +a)=$





To solve these problems, let's use the structure of the Bayesian Network (BN) and the Conditional Probability Tables (CPTs) provided in the image.

---

### a) \( P(+b \mid +a) \)

From the \( P(B \mid A) \) table:

\[
P(+b \mid +a) = 0.5
\]

---

### b) \( P(+a, +b) \)

Using the chain rule for Bayesian Networks:

\[
P(+a, +b) = P(+a) \cdot P(+b \mid +a)
\]

From the \( P(A) \) table:

\[
P(+a) = 0.25
\]

From part (a):

\[
P(+b \mid +a) = 0.5
\]

Thus:

\[
P(+a, +b) = 0.25 \cdot 0.5 = 0.125
\]

---

### c) \( P(+a \mid +b) \)

Using Bayes' Rule:

\[
P(+a \mid +b) = \frac{P(+a, +b)}{P(+b)}
\]

We already know \( P(+a, +b) = 0.125 \). Now, we calculate \( P(+b) \) using the total probability rule:

\[
P(+b) = P(+b \mid +a) \cdot P(+a) + P(+b \mid -a) \cdot P(-a)
\]

From the tables:

\[
P(+b \mid +a) = 0.5, \quad P(+a) = 0.25, \quad P(+b \mid -a) = 0.25, \quad P(-a) = 0.75
\]

\[
P(+b) = (0.5 \cdot 0.25) + (0.25 \cdot 0.75) = 0.125 + 0.1875 = 0.3125
\]

Now:

\[
P(+a \mid +b) = \frac{0.125}{0.3125} = 0.4
\]

---

### d) \( P(-e, +a) \)

Using the chain rule:

\[
P(-e, +a) = P(+a) \cdot P(-e \mid +a)
\]

First, \( P(-e \mid +a) \) can be computed using marginalization:

\[
P(-e \mid +a) = P(-e \mid +b) \cdot P(+b \mid +a) + P(-e \mid -b) \cdot P(-b \mid +a)
\]

From the \( P(E \mid B) \) table:

\[
P(-e \mid +b) = 0.75, \quad P(-e \mid -b) = 0.9
\]

From the \( P(B \mid A) \) table:

\[
P(+b \mid +a) = 0.5, \quad P(-b \mid +a) = 0.5
\]

Thus:

\[
P(-e \mid +a) = (0.75 \cdot 0.5) + (0.9 \cdot 0.5) = 0.375 + 0.45 = 0.825
\]

Now, using \( P(+a) = 0.25 \):

\[
P(-e, +a) = P(+a) \cdot P(-e \mid +a) = 0.25 \cdot 0.825 = 0.20625
\]

---

### Final Answers:

a) \( P(+b \mid +a) = 0.5 \)  
b) \( P(+a, +b) = 0.125 \)  
c) \( P(+a \mid +b) = 0.4 \)  
d) \( P(-e, +a) = 0.20625 \)