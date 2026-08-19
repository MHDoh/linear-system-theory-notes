# Lecture: Matrix Factorizations in Linear System Theory

Scope: this lecture uses the audited course notes for Lectures 2-23, but it keeps only factorization material. It does not cover general linear algebra topics unless they are needed to state, prove, or use a factorization.

## 1. Why Factorizations Matter

A matrix factorization rewrites one complicated linear map as a product of simpler maps. In this course, the simple maps are usually:

- triangular matrices, which are easy to solve by substitution;
- diagonal matrices, which expose independent scalar actions;
- unitary or orthogonal matrices, which preserve inner products and norms;
- positive definite or positive semidefinite factors, which expose energy and covariance structure;
- block factors, which isolate subproblems and Schur complements.

The recurring principle is:

\[
\text{hard matrix} = \text{structure} \times \text{simple core} \times \text{structure}^{-1}.
\]

For proof questions, always state:

1. the hypotheses on \(A\);
2. the exact factorization;
3. what each factor satisfies;
4. whether the factorization exists for every matrix or only for special matrices;
5. what information the factorization reveals.

## 2. Change of Basis and Diagonalization

The first factorization idea is a change of coordinates.

If the same basis is used on input and output, the matrix becomes

\[
\widetilde A = T^{-1}AT.
\]

This is called a similarity transformation. It represents the same linear operator in a different basis.

If \(A\) has a basis of eigenvectors \(t_1,\ldots,t_n\), put

\[
T=[t_1\ \cdots\ t_n],\qquad \Lambda=\operatorname{diag}(\lambda_1,\ldots,\lambda_n).
\]

Then

\[
AT=T\Lambda,
\]

and therefore

\[
A=T\Lambda T^{-1}.
\]

This is diagonalization.

The eigenvalues may repeat. Repetition is not the problem. The issue is whether there are enough linearly independent eigenvectors to form the matrix \(T\).

The factorization \(A=T\Lambda T^{-1}\) says that \(A\) acts independently along the eigenvector directions. In eigen-coordinates, applying \(A\) is just multiplying each coordinate by one scalar eigenvalue.

Common traps:

- Diagonalizable does not mean every square matrix is diagonalizable.
- Repeated eigenvalues do not automatically prevent diagonalization.
- Distinct eigenvalues guarantee independent eigenvectors, but the converse is not required.
- \(T^{-1}AT\) is a same-space coordinate change; using different input/output bases is a different idea.
- Diagonalization by an arbitrary invertible \(T\) is weaker than unitary diagonalization.

## 3. Different Input and Output Bases

For a general matrix that maps one space to another, it can make more sense to change the input basis and output basis separately.

The general coordinate form is

\[
\widetilde A = S^{-1}AT,
\]

where \(T\) changes input coordinates and \(S\) changes output coordinates.

This idea prepares the singular value decomposition:

\[
A=U\Sigma V^*.
\]

Here \(V\) changes the input coordinates, \(U\) changes the output coordinates, and \(\Sigma\) is diagonal or rectangular diagonal.

The key distinction:

- Similarity \(T^{-1}AT\) uses one basis for input and output.
- SVD \(U^*AV=\Sigma\) uses two orthonormal bases, one for the domain and one for the range/codomain.

## 4. LU Factorization and Gaussian Elimination

Gaussian elimination factors a matrix into triangular pieces.

In the simplest square case, elimination gives

\[
A=LU,
\]

where \(L\) is lower triangular and \(U\) is upper triangular. Often \(L\) is unit lower triangular, meaning its diagonal entries are all \(1\).

If row exchanges are needed, the more stable statement is

\[
PA=LU,
\]

where \(P\) is a permutation matrix.

Triangular systems are easy:

\[
LUx=b
\]

is solved by first solving

\[
Ly=b
\]

by forward substitution, then

\[
Ux=y
\]

by backward substitution.

The professor emphasized that this is like applying an inverse without explicitly forming the inverse. You should not think of elimination as computing \(A^{-1}\); think of it as replacing one hard solve by two structured solves.

Permutation matrices are simple orthogonal/unitary factors:

\[
P^{-1}=P^T=P^*.
\]

They reorder coordinates and preserve norms.

Common traps:

- LU is not the same as QR. LU uses elimination and triangular row-operation structure; QR uses orthogonal or unitary transformations.
- A square-looking matrix is not automatically easy. Coupling is the difficulty.
- Triangular matrices are easy because of substitution order, not because entries are small.
- Pivoting may be needed; bare \(A=LU\) is not guaranteed for every matrix without assumptions.

## 5. LDU Factorization

LU can be refined by separating diagonal scaling:

\[
A=LDU,
\]

where \(L\) is unit lower triangular, \(D\) is diagonal, and \(U\) is unit upper triangular.

This separates three effects:

- \(L\): lower triangular mixing;
- \(D\): coordinate scaling through pivots;
- \(U\): upper triangular mixing.

The block version of LDU is especially important later because it leads to Schur complements.

## 6. QR Factorization

QR factorization writes a matrix as

\[
A=QR.
\]

For \(A\in\mathbb C^{m\times n}\) with full column rank, the reduced QR factorization is

\[
A=Q_1R_1,
\]

where

\[
Q_1\in\mathbb C^{m\times n},\qquad Q_1^*Q_1=I_n,
\]

and

\[
R_1\in\mathbb C^{n\times n}
\]

is upper triangular with nonzero diagonal entries.

The full QR factorization is

\[
A=QR,
\]

where \(Q\in\mathbb C^{m\times m}\) is unitary and \(R\in\mathbb C^{m\times n}\) is upper trapezoidal.

The point is that the columns of \(Q_1\) form an orthonormal basis for \(\mathcal R(A)\). The matrix \(R_1\) contains the coordinates of the original columns of \(A\) in that orthonormal basis.

### QR from Gram-Schmidt

Classical Gram-Schmidt constructs \(q_1,q_2,\ldots,q_n\) from \(a_1,a_2,\ldots,a_n\).

At step \(k\), subtract the projections onto the previously constructed orthonormal directions:

\[
\widetilde q_k
=a_k-\sum_{i=1}^{k-1}q_i(q_i^*a_k),
\]

then normalize:

\[
q_k=\frac{\widetilde q_k}{\|\widetilde q_k\|}.
\]

The upper triangular entries are

\[
r_{ik}=q_i^*a_k,\qquad i\le k.
\]

Then

\[
a_k=\sum_{i=1}^k q_ir_{ik},
\]

which gives \(A=QR\).

### Modified Gram-Schmidt

Modified Gram-Schmidt performs the same mathematical orthogonalization but updates the remaining vectors step by step. After removing the \(q_1\)-component, later passes have no business projecting again onto \(q_1\). They project only onto the newly generated direction.

This matters numerically, because modified Gram-Schmidt is usually more stable than classical Gram-Schmidt.

### QR from Householder Reflections

Householder transformations are unitary reflections that zero out selected entries below the diagonal. Repeated Householder transformations produce an upper triangular matrix:

\[
Q^*A=R,
\]

so

\[
A=QR.
\]

Householder QR is the preferred numerical factorization because it uses norm-preserving transformations.

### QR and Least Squares

For full column rank \(A\), least squares solves

\[
\min_x\|Ax-b\|_2.
\]

If \(A=Q_1R_1\), then

\[
\|Ax-b\|_2
=\|Q_1R_1x-b\|_2.
\]

Using a full \(Q=[Q_1\ Q_2]\), unitary invariance gives the least-squares problem in coordinates:

\[
\left\|
\begin{bmatrix}
R_1x-Q_1^*b\\
-Q_2^*b
\end{bmatrix}
\right\|_2.
\]

The minimizing \(x\) satisfies

\[
R_1x=Q_1^*b.
\]

QR is often preferable to solving normal equations because it avoids squaring the condition number through \(A^*A\).

Common traps:

- Reduced QR has \(Q_1^*Q_1=I\), but generally \(Q_1Q_1^*\ne I\).
- \(Q_1Q_1^*\) is an orthogonal projection onto \(\mathcal R(A)\).
- Full QR and reduced QR have different dimensions.
- QR exists beyond full column rank, but the clean reduced form with invertible \(R_1\) needs full column rank.

## 7. Projection Factorizations from QR

If \(Q\) has orthonormal columns spanning a subspace \(V\), then the orthogonal projection onto \(V\) is

\[
P=QQ^*.
\]

This is a factorization of a projection matrix into an orthonormal basis and its adjoint.

It immediately gives

\[
P^2=QQ^*QQ^*=Q(Q^*Q)Q^*=QQ^*=P,
\]

and

\[
P^*=(QQ^*)^*=QQ^*=P.
\]

If \(A\) has full column rank and its columns span \(V\), then

\[
P=A(A^*A)^{-1}A^*.
\]

Using QR, \(A=Q_1R_1\), this becomes

\[
A(A^*A)^{-1}A^*
=Q_1R_1(R_1^*R_1)^{-1}R_1^*Q_1^*
=Q_1Q_1^*.
\]

This connects projection formulas, Gram matrices, QR, and least squares.

Common traps:

- Projection means \(P^2=P\).
- Orthogonal projection means \(P^2=P\) and \(P^*=P\).
- \(QQ^*=I\) only if \(Q\) is square unitary. For a tall \(Q\), \(QQ^*\) is a projection, not the identity.

## 8. Schur Factorization

Schur's theorem says that every square complex matrix \(A\in\mathbb C^{n\times n}\) can be written as

\[
A=UTU^*,
\]

where \(U\) is unitary and \(T\) is upper triangular.

Equivalently,

\[
U^*AU=T.
\]

The diagonal entries of \(T\) are the eigenvalues of \(A\).

### Proof Idea

The proof is by induction.

First choose one eigenvalue \(\lambda_1\) and a corresponding unit eigenvector \(u_1\). Complete \(u_1\) to an orthonormal basis:

\[
U_1=[u_1\ U_2].
\]

Then

\[
U_1^*AU_1
=
\begin{bmatrix}
\lambda_1 & *\\
0 & A_2
\end{bmatrix}.
\]

The lower-left block is zero because \(Au_1=\lambda_1u_1\). Then apply the same argument to \(A_2\), and continue recursively.

Schur factorization is always available over \(\mathbb C\) for square matrices. It is not diagonalization. It only guarantees triangular form.

Common traps:

- Schur is square-matrix theory. Rectangular matrices use SVD, not Schur.
- Schur gives triangular \(T\), not necessarily diagonal \(T\).
- The diagonal of \(T\) contains eigenvalues, but the off-diagonal entries carry non-normal coupling.
- Schur is not a numerical trick only; it is a theorem that underlies spectral results.

## 9. Normal Matrices and Unitary Diagonalization

A square matrix \(A\) is normal if

\[
A^*A=AA^*.
\]

The central theorem is:

\[
A\text{ is normal}
\quad\Longleftrightarrow\quad
A=U\Lambda U^*
\]

for some unitary \(U\) and diagonal \(\Lambda\).

This is unitary diagonalization.

### Proof Idea from Schur

By Schur,

\[
A=UTU^*.
\]

Since unitary similarity preserves normality, \(T\) is normal. But \(T\) is both upper triangular and normal. An upper triangular normal matrix must be diagonal. Therefore

\[
T=\Lambda,
\]

so

\[
A=U\Lambda U^*.
\]

This proof is efficient because directly proving orthogonality of all eigenvectors for a general normal matrix is harder.

Common traps:

- Normal does not mean Hermitian.
- Hermitian, unitary, and skew-Hermitian matrices are all normal, but normal is a larger class.
- Diagonalizable does not imply unitarily diagonalizable.
- Unitary diagonalization is tied to orthonormal eigenvectors.

## 10. Spectral Theorem for Hermitian and Symmetric Matrices

A complex matrix \(A\) is Hermitian if

\[
A^*=A.
\]

A real matrix is symmetric if

\[
A^T=A.
\]

The spectral theorem for Hermitian matrices says:

\[
A=A^*
\quad\Longrightarrow\quad
A=U\Lambda U^*
\]

where \(U\) is unitary and \(\Lambda\) is real diagonal.

For real symmetric matrices,

\[
A=Q\Lambda Q^T
\]

with \(Q\) orthogonal and \(\Lambda\) real diagonal.

Important consequences:

- Hermitian eigenvalues are real.
- Eigenvectors corresponding to distinct eigenvalues are orthogonal.
- Hermitian matrices are normal.
- Positive definiteness and semidefiniteness can be read from eigenvalues.

For a Hermitian matrix,

\[
x^*Ax=x^*U\Lambda U^*x.
\]

Let \(y=U^*x\). Then

\[
x^*Ax=y^*\Lambda y
=\sum_i \lambda_i |y_i|^2.
\]

Therefore:

- \(A\succ 0\) iff all \(\lambda_i>0\);
- \(A\succeq 0\) iff all \(\lambda_i\ge 0\);
- \(A\prec 0\) iff all \(\lambda_i<0\);
- \(A\preceq 0\) iff all \(\lambda_i\le 0\);
- mixed signs imply indefinite.

Common traps:

- In complex spaces, use \(A^*\), not \(A^T\).
- Symmetric is the real version; Hermitian is the complex version.
- \(x^TAx\) is not the right complex quadratic form; use \(x^*Ax\).
- PSD allows zero eigenvalues; PD does not.

## 11. Skew-Hermitian Factorization by Unitary Diagonalization

A matrix is skew-Hermitian if

\[
A^*=-A.
\]

Skew-Hermitian matrices are normal, so they are unitarily diagonalizable:

\[
A=U\Lambda U^*.
\]

The diagonal entries of \(\Lambda\) are purely imaginary. This follows from

\[
A^*=-A.
\]

If \(Av=\lambda v\), then using the Hermitian-style eigenvalue argument gives

\[
\overline{\lambda}=-\lambda,
\]

so \(\operatorname{Re}(\lambda)=0\).

This is not usually the central factorization in the course, but it is a good notation trap.

## 12. Cholesky Factorization

For a Hermitian positive definite matrix \(A\), Cholesky factorization writes

\[
A=LL^*
\]

where \(L\) is lower triangular with positive diagonal entries.

Equivalently,

\[
A=R^*R
\]

with \(R=L^*\) upper triangular.

For real symmetric positive definite \(A\),

\[
A=LL^T.
\]

Cholesky is a structured square-root factorization. It is stronger than merely saying \(A=SS^*\), because it requires a triangular factor with positive diagonal.

### Proof Idea

Partition

\[
A=
\begin{bmatrix}
\alpha & b^*\\
b & C
\end{bmatrix},
\qquad \alpha>0.
\]

Try

\[
L=
\begin{bmatrix}
\ell_{11} & 0\\
\ell_{21} & L_{22}
\end{bmatrix}.
\]

Matching blocks gives

\[
\ell_{11}=\sqrt{\alpha},\qquad
\ell_{21}=\frac{b}{\sqrt{\alpha}}.
\]

The remaining block is the Schur complement

\[
C-\frac{1}{\alpha}bb^*.
\]

One proves this Schur complement is positive definite, then applies induction.

The important warning from lecture is that subtracting a rank-one PSD term from a positive definite block is not automatically safe. The reason it is safe here is the Schur-complement property of a positive definite block matrix.

Common traps:

- Cholesky requires Hermitian positive definite, not just any invertible matrix.
- PSD matrices may not have a Cholesky factor with positive diagonal.
- In complex spaces the factor is \(LL^*\), not \(LL^T\).
- Do not confuse the unique Cholesky factor with a nonunique general square root.

## 13. Positive Semidefinite Square-Root Factorizations

A Hermitian matrix \(A\) is positive semidefinite if

\[
x^*Ax\ge 0
\]

for all \(x\).

For Hermitian PSD \(A\), the spectral theorem gives

\[
A=U\Lambda U^*,
\qquad \Lambda\ge 0.
\]

Define

\[
A^{1/2}=U\Lambda^{1/2}U^*.
\]

Then

\[
A^{1/2}(A^{1/2})^*=A.
\]

Because \(A^{1/2}\) is Hermitian PSD, this also gives

\[
(A^{1/2})^2=A.
\]

More generally,

\[
A=SS^*
\]

implies \(A\succeq 0\), because

\[
x^*SS^*x=\|S^*x\|_2^2\ge 0.
\]

Conversely, if \(A\succeq 0\), the spectral square root gives such an \(S\).

Thus

\[
A\succeq 0
\quad\Longleftrightarrow\quad
A=SS^*
\]

for some \(S\).

If one square-root factor \(S\) is known, multiplying on the right by a unitary matrix preserves the product:

\[
(SQ)(SQ)^*=SQQ^*S^*=SS^*.
\]

Common traps:

- \(A^{1/2}\) can mean the unique Hermitian PSD square root, but a general square-root factor \(S\) is not unique.
- \((A^{1/2})^*\) is meaningful only after a particular square-root factor has been chosen.
- \(SS^*\) is automatically PSD; \(S^*S\) is also PSD, but generally a different size if \(S\) is rectangular.

## 14. Covariance, Coloring, and Whitening Factorizations

Covariance matrices are PSD:

\[
C_x=\mathbb E[(x-\mu)(x-\mu)^*]\succeq 0.
\]

Therefore they can be factored as

\[
C_x=SS^*.
\]

This gives a coloring construction. If \(z\) is white with covariance \(I\), define

\[
x=Sz+\mu.
\]

Then

\[
C_x=SIS^*=SS^*.
\]

Whitening reverses the process. If

\[
C_x=U\Lambda U^*
\]

with positive eigenvalues, then a whitening transform can use

\[
C_x^{-1/2}=U\Lambda^{-1/2}U^*.
\]

Then

\[
C_x^{-1/2}C_xC_x^{-1/2}=I.
\]

This is a direct application of spectral factorization and square roots.

Common traps:

- Uncorrelated does not always mean independent; for jointly Gaussian variables, it does.
- Raw correlation and covariance are not the same unless the mean is zero.
- Whitening requires care with zero eigenvalues; singular covariance cannot be inverted on the whole space.

## 15. Block LDU Factorization and Schur Complements

Partition a square matrix as

\[
A=
\begin{bmatrix}
A_{11} & A_{12}\\
A_{21} & A_{22}
\end{bmatrix},
\]

where \(A_{11}\) is square and invertible.

Then

\[
A=
\begin{bmatrix}
I & 0\\
A_{21}A_{11}^{-1} & I
\end{bmatrix}
\begin{bmatrix}
A_{11} & 0\\
0 & S
\end{bmatrix}
\begin{bmatrix}
I & A_{11}^{-1}A_{12}\\
0 & I
\end{bmatrix},
\]

where

\[
S=A_{22}-A_{21}A_{11}^{-1}A_{12}
\]

is the Schur complement of \(A_{11}\) in \(A\).

This is a block version of Gaussian elimination.

If \(A_{22}\) is invertible instead, the other Schur complement is

\[
A_{11}-A_{12}A_{22}^{-1}A_{21}.
\]

### Positive Definiteness Test

For Hermitian block matrices,

\[
A\succ 0
\]

is equivalent, under the appropriate invertibility condition, to

\[
A_{11}\succ 0
\quad\text{and}\quad
A_{22}-A_{21}A_{11}^{-1}A_{12}\succ 0.
\]

This is one of the main reasons Schur complements matter in control and optimization.

### Linear Matrix Inequalities

A quadratic matrix inequality can sometimes be converted into a block linear matrix inequality. A standard form is

\[
\begin{bmatrix}
C & H^*\\
H & B
\end{bmatrix}\succ 0
\quad\Longleftrightarrow\quad
C\succ 0
\text{ and }
B-HC^{-1}H^*\succ 0.
\]

The larger block matrix is linear in \(H\), while the Schur complement contains the quadratic expression.

Common traps:

- Schur complement formulas are order-sensitive.
- You must state which block is assumed invertible.
- For PD tests, the matrix must be Hermitian.
- Block LDU is a factorization; the Schur complement is the remaining block after eliminating one variable group.

## 16. Matrix Inversion Lemma and Woodbury Identity

The Woodbury identity is a consequence of block inversion and Schur complements.

One common form is

\[
(A+BCD)^{-1}
=A^{-1}-A^{-1}B(C^{-1}+DA^{-1}B)^{-1}DA^{-1}.
\]

The dimensions must be compatible, and \(A\) and \(C^{-1}+DA^{-1}B\) must be invertible.

The rank-one update case is especially important:

\[
(A+uv^*)^{-1}
=A^{-1}-\frac{A^{-1}uv^*A^{-1}}{1+v^*A^{-1}u}.
\]

In recursive least squares, a covariance or Gram-type matrix is updated by a rank-one term. Woodbury updates the inverse without recomputing the inverse from scratch.

Common traps:

- The denominator in a rank-one update is scalar.
- The scaling constants matter; in the RLS form, the denominator comes from \(C^{-1}+DA^{-1}B\).
- Woodbury is not a new spectral theorem; it is block matrix factorization/inversion.

## 17. Circulant and DFT Diagonalization

Circular convolution matrices are diagonalized by the discrete Fourier basis.

Let \(F\) be a unitary DFT matrix, with convention-dependent scaling. For a circulant matrix \(C\),

\[
C=F^*\Lambda F
\]

or equivalently

\[
FCF^*=\Lambda,
\]

depending on the convention used for \(F\).

The diagonal entries of \(\Lambda\) are the DFT coefficients of the first column or impulse response.

The shift matrix is the prototype. Its eigenvectors are Fourier vectors. Since circulant matrices are polynomials in the shift matrix, they share the Fourier eigenvectors.

This factorization turns circular convolution into pointwise multiplication:

\[
y=Cx
\quad\Longleftrightarrow\quad
\widehat y=\Lambda \widehat x.
\]

The FFT is not a different factorization. It is a fast algorithm for applying the DFT factorization.

Common traps:

- DFT sign and scaling conventions vary. Always track whether \(F\) is unitary.
- Parseval scaling depends on convention.
- Linear convolution and circular convolution are not the same unless the problem has been embedded correctly.
- Toeplitz LTI matrices and circulant matrices are related but not identical.

## 18. Singular Value Decomposition

The singular value decomposition is the most general and most important rectangular factorization:

\[
A=U\Sigma V^*.
\]

For \(A\in\mathbb C^{m\times n}\),

- \(U\in\mathbb C^{m\times m}\) is unitary;
- \(V\in\mathbb C^{n\times n}\) is unitary;
- \(\Sigma\in\mathbb R^{m\times n}\) is rectangular diagonal;
- singular values satisfy
  \[
  \sigma_1\ge\sigma_2\ge\cdots\ge 0.
  \]

The thin SVD is

\[
A=U_r\Sigma_rV_r^*,
\]

where \(r=\operatorname{rank}(A)\), \(U_r\) and \(V_r\) have orthonormal columns, and \(\Sigma_r\) contains the positive singular values.

### Proof Idea

Start from the Hermitian PSD matrix

\[
A^*A.
\]

By the spectral theorem,

\[
A^*A=V\Lambda V^*,
\]

where \(\Lambda\ge 0\).

Set

\[
\sigma_i=\sqrt{\lambda_i}.
\]

For each positive \(\sigma_i\), define

\[
u_i=\frac{Av_i}{\sigma_i}.
\]

Then

\[
Av_i=\sigma_i u_i.
\]

The vectors \(u_i\) are orthonormal because

\[
u_i^*u_j
=\frac{v_i^*A^*Av_j}{\sigma_i\sigma_j}
=\frac{\lambda_j v_i^*v_j}{\sigma_i\sigma_j}.
\]

Complete the \(u_i\)'s and \(v_i\)'s to orthonormal bases. This gives

\[
A=U\Sigma V^*.
\]

### Geometric Meaning

The SVD says:

1. rotate or reflect the input using \(V^*\);
2. stretch by singular values using \(\Sigma\);
3. rotate or reflect the output using \(U\).

The image of the unit ball under \(A\) is an ellipsoid. The semi-axis lengths are the singular values, and the output directions are the left singular vectors.

The \(2\)-norm is

\[
\|A\|_2=\sigma_1.
\]

The Frobenius norm is

\[
\|A\|_F=\sqrt{\sum_i\sigma_i^2}.
\]

The nuclear norm is

\[
\|A\|_*=\sum_i\sigma_i.
\]

### Subspace Meaning

For rank \(r\),

- \(\mathcal R(A)=\operatorname{span}(u_1,\ldots,u_r)\);
- \(\mathcal R(A^*)=\operatorname{span}(v_1,\ldots,v_r)\);
- \(\mathcal N(A)=\operatorname{span}(v_{r+1},\ldots,v_n)\);
- \(\mathcal N(A^*)=\operatorname{span}(u_{r+1},\ldots,u_m)\).

This ties SVD to the four fundamental subspaces.

### Low-Rank Approximation

The best rank-\(k\) approximation in Frobenius norm and in spectral norm is obtained by truncating the SVD:

\[
A_k=\sum_{i=1}^k\sigma_i u_iv_i^*.
\]

This is the Eckart-Young theorem.

Common traps:

- SVD exists for every matrix, including rectangular matrices.
- Eigen-decomposition is for square matrices; SVD is not an eigen-decomposition of \(A\).
- Singular values are nonnegative.
- \(U\) and \(V\) are generally different.
- Left singular vectors live in output space; right singular vectors live in input space.
- \(\sigma_i^2\) are eigenvalues of \(A^*A\), not necessarily of \(A\).

## 19. Polar Decomposition

Polar decomposition factors a matrix into a unitary-like part and a positive semidefinite part.

For a square nonsingular matrix,

\[
A=QH,
\]

where \(Q\) is unitary and

\[
H=(A^*A)^{1/2}\succeq 0.
\]

Using the SVD,

\[
A=U\Sigma V^*.
\]

Then

\[
H=(A^*A)^{1/2}
=V\Sigma V^*,
\]

and

\[
Q=UV^*.
\]

Thus

\[
A=(UV^*)(V\Sigma V^*).
\]

For rectangular or rank-deficient matrices, the unitary factor becomes a partial isometry rather than a full unitary matrix.

The polar factor \(UV^*\) also appears in the closest-unitary problem:

\[
\min_{Q^*Q=I}\|A-Q\|_F.
\]

If \(A=U\Sigma V^*\), the closest unitary/orthogonal factor is

\[
Q=UV^*.
\]

Common traps:

- Polar decomposition is not QR. QR has triangular \(R\); polar has PSD \(H\).
- Polar decomposition is not SVD. It is derived from SVD but combines the two unitary factors.
- \(H\) is PSD and Hermitian; it is not triangular in general.

## 20. Gram Matrix Factorizations

Given a matrix \(A\), the Gram matrix is

\[
G=A^*A.
\]

It is Hermitian PSD:

\[
x^*Gx=x^*A^*Ax=\|Ax\|_2^2\ge 0.
\]

If \(A=QR\), then

\[
A^*A=R^*Q^*QR=R^*R.
\]

Thus QR gives a Cholesky-like factorization of the Gram matrix:

\[
G=R^*R.
\]

If \(A\) has full column rank, then \(G\succ0\), and \(R\) is invertible.

The normal equations

\[
A^*Ax=A^*b
\]

therefore involve a Gram/Cholesky structure. But QR is usually preferred numerically.

Common traps:

- \(A^*A\) is always Hermitian PSD, even if \(A\) is rectangular.
- \(A^*A\) is positive definite only if \(A\) has full column rank.
- Forming \(A^*A\) can worsen conditioning.

## 21. Factorization Comparison Table

| Factorization | Form | Main hypotheses | Core structure | Main use |
|---|---|---|---|---|
| Diagonalization | \(A=T\Lambda T^{-1}\) | square, enough eigenvectors | diagonal | eigen-coordinates |
| Unitary diagonalization | \(A=U\Lambda U^*\) | normal | diagonal plus unitary basis | spectral structure |
| Spectral theorem | \(A=U\Lambda U^*\) | Hermitian | real diagonal | quadratic forms, definiteness |
| Schur | \(A=UTU^*\) | square complex | upper triangular | universal square-matrix triangularization |
| LU | \(A=LU\), \(PA=LU\) | pivot assumptions | triangular | solving systems |
| LDU | \(A=LDU\) | pivot assumptions | triangular plus diagonal | expose pivots/scaling |
| QR | \(A=QR\) | general; clean reduced form for full column rank | unitary plus triangular | least squares, orthonormal bases |
| Cholesky | \(A=LL^*\) | Hermitian PD | triangular square root | covariance, PD solves |
| PSD square root | \(A=SS^*\) | Hermitian PSD | square-root factor | covariance, energy |
| Block LDU | block triangular factors | invertible leading block | Schur complement | elimination, PD tests |
| Woodbury | inverse update | compatible inverses | low-rank update | recursive inverse updates |
| DFT diagonalization | \(C=F^*\Lambda F\) | circulant | Fourier diagonal | convolution |
| SVD | \(A=U\Sigma V^*\) | any matrix | two unitary bases plus singular values | geometry, rank, norms |
| Polar | \(A=QH\) | general with partial-isometry caveat | unitary-like plus PSD | closest unitary, geometry |

## 22. Most Important Distinctions

### Schur vs Diagonalization

Schur:

\[
A=UTU^*
\]

exists for every square complex matrix, but \(T\) may only be triangular.

Diagonalization:

\[
A=T\Lambda T^{-1}
\]

requires enough eigenvectors.

Unitary diagonalization:

\[
A=U\Lambda U^*
\]

requires normality.

### QR vs LU

LU uses elimination:

\[
A=LU.
\]

QR uses orthonormalization or unitary transformations:

\[
A=QR.
\]

LU is triangular solving. QR is orthogonal geometry and stable least squares.

### Cholesky vs General Square Root

Cholesky:

\[
A=LL^*
\]

with \(L\) triangular and positive diagonal, requiring \(A\succ0\).

General PSD factor:

\[
A=SS^*
\]

requiring only \(A\succeq0\), with nonunique \(S\).

### Eigenvalues vs Singular Values

Eigenvalues solve

\[
Av=\lambda v.
\]

Singular values come from

\[
A^*A v=\sigma^2 v.
\]

Eigenvalues can be complex. Singular values are always real and nonnegative.

### Orthogonal/Unitary Factors

For real matrices:

\[
Q^TQ=I.
\]

For complex matrices:

\[
U^*U=I.
\]

Do not replace \(A^*\) by \(A^T\) in complex factorization statements.

## 23. Minimal Proof Templates

### To Prove Schur Factorization

Pick an eigenvector, normalize it, complete it to an orthonormal basis, block triangularize, then apply induction to the lower-right block.

### To Prove Normal Implies Unitary Diagonalizable

Use Schur:

\[
A=UTU^*.
\]

Normality passes to \(T\). A triangular normal matrix is diagonal. Therefore \(A=U\Lambda U^*\).

### To Prove the Spectral Theorem for Hermitian Matrices

Hermitian matrices are normal, so they are unitarily diagonalizable. Then show the diagonal entries are real:

\[
Av=\lambda v,\quad v^*Av=\lambda v^*v.
\]

Since \(A=A^*\), \(v^*Av\) is real, so \(\lambda\in\mathbb R\).

### To Prove Cholesky

Partition \(A\), choose the first positive pivot, match the first row/column of \(LL^*\), show the Schur complement remains positive definite, and use induction.

### To Prove SVD

Diagonalize \(A^*A\), take square roots of eigenvalues, define \(u_i=Av_i/\sigma_i\) for positive singular values, prove the \(u_i\)'s are orthonormal, then complete both sides to orthonormal bases.

### To Prove \(P=QQ^*\) Is an Orthogonal Projection

Use \(Q^*Q=I\):

\[
P^2=QQ^*QQ^*=QQ^*=P,
\]

and

\[
P^*=(QQ^*)^*=QQ^*=P.
\]

### To Prove \(A=SS^*\) Is PSD

For all \(x\),

\[
x^*Ax=x^*SS^*x=\|S^*x\|^2\ge0.
\]

### To Derive Block LDU

Multiply the three block factors and verify that the off-diagonal blocks match and that the lower-right block becomes

\[
A_{22}-A_{21}A_{11}^{-1}A_{12}.
\]

## 24. Study Order for Factorizations

1. Learn LU/LDU first: elimination and triangular solves.
2. Learn QR next: orthonormal bases, projections, least squares.
3. Learn Schur: every square complex matrix is unitarily triangularizable.
4. Learn normal and spectral theorem: when Schur becomes diagonal.
5. Learn Cholesky and PSD square roots: energy and covariance structure.
6. Learn block LDU and Schur complements: elimination at the block level.
7. Learn Woodbury: inverse update from block factorization.
8. Learn DFT diagonalization: Fourier basis diagonalizes circulant convolution.
9. Learn SVD: every matrix becomes diagonal between two orthonormal bases.
10. Learn polar decomposition: combine SVD into unitary-like times PSD.

If you can state each factorization, list its hypotheses, prove its existence idea, and explain what structure it reveals, you have the factorization part of the course under control.
