## Ch1: Numbers and Vectors
- **Triangular inequality**:
  $\|a+b\| \leq \|a\| + \|b\|$
- **Cauchy-Schwarz inequality**:
  $\langle x, y \rangle \leq \|x\| \|y\|$
- **Inner product**:
  $\langle x, y \rangle = a_1b_1 + a_2b_2 + \cdots + a_nb_n = \|x\|\|y\|\cos \theta$

## Ch2 Matrices
_(Empty)_

## Ch3 Linear Systems of Equations
_(Empty)_

## Ch4 Matrix Four Spaces
- **Column space**: Set of all linear combinations of columns of $A$. Denoted as $C(A)$.
- **Nullspace**: Set of all solutions of $Ax = 0$. Denoted as $N(A)$.
- **Rank**: Maximum number of linearly independent column (or row) vectors.
- **Row space**: Subspace spanned by rows of $A$. Equivalent to the column space of $A^T$.
- **Left nullspace**: Set of all solutions of $A^T x = 0$.

## Ch5 Inverse Matrices
- For $A \in \mathbb{R}^{n \times n}$:
  $AA^{-1} = I_n$
- **Solving linear systems**:
  $x = A^{-1}b$

## Ch6 Determinant
- **Cramer’s Rule**:
  If $Ax = b$ and $\det(A) \neq 0$, then:
  $x_i = \frac{\det(B_i)}{\det(A)}$, where $B_i$ is $A$ with the $i$-th column replaced by $b$.

## Ch7 Eigenvalue and Eigenvector
- **Rayleigh quotient**:
  $R_A(x) = \frac{\langle x, Ax \rangle}{\|x\|^2}$
- **Eigenvalue computation**:
  $\det(A - \lambda I_n) = 0$
- **Eigenvector computation**:
  $(A - \lambda I_n) x = 0$
- **Relation to determinant**:
  $\det(A) = \lambda_1 \lambda_2 \cdots \lambda_n$
- **Relation to trace**:
  $\text{tr}(A) = \lambda_1 + \lambda_2 + \cdots + \lambda_n$

## Ch8 Diagonalizable and Similar Matrices
- **Diagonalization**:
  If $A$ has $n$ linearly independent eigenvectors,
  $A = X \Lambda X^{-1}$
- **Power of diagonalizable matrix**:
  $A^k = X \Lambda^k X^{-1}$
- **Similar matrices**:
  $A = BCB^{-1}$
  Similar matrices have the same eigenvalues.

## Ch9 Orthogonality
- **Orthogonal vectors/subspaces**:
  $\langle x, y \rangle = 0$
- **Orthogonality of subspaces**:
  $C(A)$ and $N(A^T)$ are orthogonal.
  $C(A^T)$ and $N(A)$ are orthogonal.
- **Orthogonal complement**:
  $V^\perp = \{x \in \mathbb{R}^n : \langle x, v \rangle = 0, \forall v \in V\}$
- **Orthogonal projection (line)**:
  $p = \frac{\langle a, b \rangle}{\langle a, a \rangle}a$
- **Orthogonal projection (subspace)**:
  $p = A(A^TA)^{-1}A^T b$
- **Orthonormal vectors**:
  $Q = [q_1, q_2, \dots, q_n]$, $Q^T Q = I$
- **Gram-Schmidt process**:
  1. Set $b_1 = a_1$;
  2. Set $b_i = a_i - \sum_{j=1}^{i-1} \frac{\langle b_j,a_i \rangle}{\langle b_j,b_j \rangle}b_j$ for $i = 3,4,...,n$
  3. Normalize $q_i = \frac{b_i}{\|b_i\|}$

## Ch10: Symmetric and Positive Definite Matrices
### Symmetric Matrices
- **Definition**: $A \in \mathbb{R}^{n \times n}$ is symmetric if $A = A^T$, denoted as $A \in \mathbb{S}^{n \times n}$.
- **Property 1**:
  If $A \in \mathbb{S}^{n \times n}$, then all eigenvalues $\lambda_i \in \mathbb{R}$ for $i = 1, 2, \ldots, n$.
- **Property 2**:
  If $A \in \mathbb{S}^{n \times n}$, eigenvectors corresponding to different eigenvalues are orthogonal.
- **Property 3**:
  $A \in \mathbb{S}^{n \times n} \Rightarrow A = Q\Lambda Q^T$, where $Q = [q_1 \ q_2 \ \cdots \ q_n]$ and $\Lambda = \text{diag}(\lambda_1, \lambda_2, \ldots, \lambda_n)$. The vectors $q_i \in \mathbb{R}^n$ are orthonormal:
  $$
  \langle q_i, q_j \rangle =
  \begin{cases}
  1 & \text{if } i = j, \\
  0 & \text{if } i \neq j.
  \end{cases}
  $$
- **Property 4**:
  For $A \in \mathbb{S}^{n \times n}$, $A = Q \Lambda Q^T$ with $Q^{-1} = Q^T$.

### Positive Definite Matrices
- **Definition**:
  $A \in \mathbb{S}^{n \times n}$ is positive definite if all its eigenvalues are positive.
- **Property**:
  If $A$ is an $m \times n$ matrix ($A \in \mathbb{R}^{m \times n}$) with linearly independent columns, then $A^T A$ is symmetric and positive definite:
  $$
  \langle x, (A^T A)x \rangle = \|Ax\|^2 > 0, \quad \forall x \neq 0.
  $$
- **Sum of Positive Definite Matrices**:
  The sum of positive definite matrices is also positive definite.
- **Diagonal Dominance**:
  If matrix $A$ is strictly diagonally dominant, then $A$ is positive definite.

### Positive Semidefinite Matrices
- **Definition**:
  A symmetric matrix is positive semidefinite if its smallest eigenvalue is 0.
- **Property**:
  If $A$ is an $m \times n$ matrix ($A \in \mathbb{R}^{m \times n}$) with linearly dependent columns, then $A^T A$ is symmetric and positive semidefinite:
  $$
  \langle x, (A^T A)x \rangle = \|Ax\|^2 \geq 0, \quad \forall x \neq 0.
  $$
- **Diagonal Dominance**:
  If matrix $A$ is diagonally dominant, then $A$ is positive semidefinite.

## Ch11 Singular Value Decomposition



 
Play some domino
🁁🁂🁋
