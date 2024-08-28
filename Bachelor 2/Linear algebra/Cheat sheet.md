## Ch1 Numbers and Vectors
Triangular inequality:
$\|a+b\| ≤ \|a\|+\|b\|$
Cauchy-Schwartz inequality:
$\langle x,y \rangle ≤ \|a\| \|b\|$
Inner product
$\langle x,y \rangle = a_1b_1 + a_2b_2 +. . . + a_nb_n = \|a\|\|b\|\cos \theta$

## Ch2 Matrices
\\
## Ch3 Linear Systems of Equations
\\
## Ch4 Matrix Four Spaces
**Column space**: For a given matrix $A \in \mathbb{R}^{m\times n}$, the set of all linear combinations of columns of A forms the column space which is denoted by C(A).
**Nullspace**: For a given matrix $A \in \mathbb{R}^{m\times n}$, the set of all solutions of the homogeneous linear system Ax = 0 is called nullspace of A, which is denoted by N (A)

**Rank** of a matrix $A \in \mathbb{R}^{m\times n}$ : maximum number of linearly independent column vectors (or row vectors) in the matrix.

**Row space**: The subspace spanned by the rows of $A$. The row space of $A$ is column space of $A^T$

**Left nullspace**: the set of all solutions of the homogeneous linear system $A^T x = 0$

## Ch5 Inverse Matrices
For $A \in \mathbb{R}^{n\times n}:  AA^{-1}=I^n$

Solving linear system of equations using inverse matrices
$x = A^{-1}b$

## Ch6 Determinant
**Cramer’s Rule**:
Let $Ax= b$ for $B \in \mathbb{R}^{n}$ and $A \in \mathbb{R}^{m\times n}$ with $det(A) ≠ 0$. Then, this system is solved by determinants, i.e.
$x_i=\frac{det(B_i)}{det(A)}$ for $i = 1,2,...,n$
where the matrix Bi has the ith column of A replaced by b, i.e.,

## Ch7 Eigenvalue and Eigenvector
Rayleigh quotient:
$R_A (x) = \frac {\langle x,Ax \rangle}{\|x\| ^2}$

Computing eigenvalues:
$det(A - \lambda I_n) = 0$
Computing eigenvectors:
$(A - \lambda I_n) \mathbf{x} = 0 \text{ for the non-zero vector } x$

Relation eigenvalues and determinant
$det(A) = \lambda _1  \lambda _2 ...  \lambda _n$
Relation eigenvalues and trace
$tr(A) = \lambda _1 + \lambda _2 + ... + \lambda _n$
## Ch8 Diagonalizable and Similar Matrices
Matrix diagonalization:
Let $A$ be an $n \times n$ square matrix ($A \in \mathbb{R}^{m\times n}$), let $\lambda _1,  \lambda _2, ...,  \lambda _n$ be its n eigenvalues, and let $x_1, x_2, . . . , x_n$ be n linearly independent eigenvectors of A.
$A = X \Lambda X^{—1}$

A must be diagonalizable if A has n distinct eigenvalues.

Calculating kth power of a diagonalizable matrix:
$A^k = X \Lambda ^k X^{—1}$

A and C are similar matrices if $A = BCB^{-1}$

Similar matrices have same eigenvalues
## Ch9 Orthogonality
Orthogonal vectors or subspaces
$\langle x,y \rangle = 0$

Orthogonality of four subspaces
The column space $C(A)$ and the left null space $N (A^T)$ are orthogonal
The row space $C(A^T )$ and the null space $N (A)$ are orthogonal

Orthogonal complement
Let $V$ be a subspace of $\mathbb{R}^n$. Then, the orthogonal complement of $V$ is a set of all vectors that are perpendicular to to $V$, which is denoted by $V^{\bot}$

Orthogonal **projection** of b onto the line through a
$p= \frac{\langle a,b \rangle}{\langle a,a \rangle}a$

Orthogonal projection onto a subspace
$p= A(A^TA)^{-1}A^T b$

Orthonormal vectors
Let $q_1, q_2, . . . , q_n \in \mathbb{R}^m$ and $Q = [ q_1, q_2, . . . , q_n ]$ Then, these vectors are said to be orthonormal if $Q^T Q= I$

Orthonormal matrices leave length unchanged

Gram-Schmidt process:
1) Set $b_1 = a_1$;
2) Set $b_i = a_i - \sum_{j=1}^{i-1} \frac{\langle b_j,a_i \rangle}{\langle b_j,b_j \rangle}b_j$ for $i = 3,4,...,n$
3) Normalize $q_i = \frac{b_i}{\|b_i\|}$

## Ch10 Symmetric and positive definite matrices

## Ch11 Singular Value Decomposition