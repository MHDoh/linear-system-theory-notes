# Last-Day Revision Review: Linear System Theory

Scope: short final-review document for the proof-heavy part of the course. It is not a full replacement for the audited lecture notes. It prioritizes definitions, theorem statements, notation traps, and complete proof formulations that are likely to be asked.

## 1. Professor's Likely Exam Pattern

The most likely questions are not long numerical computations. Expect short theoretical questions of the following forms:

- State the definition and prove the immediate consequence.
- Show why a special matrix structure implies a spectral or geometric property.
- Distinguish two similar-looking notions, especially over real versus complex fields.
- Prove a projection, unitary, Hermitian, normal, PSD, or SVD property.
- State a theorem precisely and give the proof idea.
- Explain what a factorization reveals and what hypotheses it needs.

The final is inclusive, but later lectures are more likely to dominate: Schur, normal matrices, spectral theorem, PSD/PD, Cholesky, QR, Schur complements, matrix norms, SVD, low-rank approximation, polar decomposition, and nuclear norm.

## 2. Definitions to Memorize Exactly

### Inner Product and Norm

For complex vectors, the standard inner product is

\[
\langle x,y\rangle = y^*x
\]

or equivalently \(x^*y\), depending on the course convention. Be consistent with the convention used in the proof. The induced norm is

\[
\|x\|=\sqrt{x^*x}.
\]

Vectors are orthogonal if

\[
x^*y=0.
\]

### Unitary and Orthogonal Matrices

A complex square matrix \(U\) is unitary if

\[
U^*U=UU^*=I.
\]

A real square matrix \(Q\) is orthogonal if

\[
Q^TQ=QQ^T=I.
\]

### Projection and Orthogonal Projection

A matrix \(P\) is a projection if

\[
P^2=P.
\]

It is an orthogonal projection if additionally

\[
P^*=P.
\]

If \(Q\) has orthonormal columns spanning a subspace \(V\), then the orthogonal projection onto \(V\) is

\[
P=QQ^*.
\]

If \(A\) has full column rank and \(\mathcal R(A)=V\), then

\[
P=A(A^*A)^{-1}A^*.
\]

### Hermitian, Symmetric, Skew-Hermitian

A complex matrix is Hermitian if

\[
A^*=A.
\]

A real matrix is symmetric if

\[
A^T=A.
\]

A complex matrix is skew-Hermitian if

\[
A^*=-A.
\]

### Positive Definite and Positive Semidefinite

A Hermitian matrix \(A\) is positive definite if

\[
x^*Ax>0 \quad \text{for all } x\ne 0.
\]

It is positive semidefinite if

\[
x^*Ax\ge 0 \quad \text{for all } x.
\]

Write \(A\succ0\) for positive definite and \(A\succeq0\) for positive semidefinite.

### Normal Matrix

A square complex matrix \(A\) is normal if

\[
A^*A=AA^*.
\]

Hermitian, skew-Hermitian, and unitary matrices are normal, but normal matrices need not be Hermitian.

### Matrix Norms

The induced norm from vector norms is

\[
\|A\|_{p,p}=\max_{x\ne0}\frac{\|Ax\|_p}{\|x\|_p}.
\]

Important cases:

\[
\|A\|_{2,2}=\sigma_{\max}(A),
\]

\[
\|A\|_F=\sqrt{\sum_{i,j}|a_{ij}|^2}
=\sqrt{\sum_i\sigma_i^2},
\]

\[
\|A\|_*=\sum_i\sigma_i.
\]

## 3. Theorems to State Exactly

### Schur Theorem

Every square complex matrix \(A\in\mathbb C^{n\times n}\) admits a factorization

\[
A=UTU^*,
\]

where \(U\) is unitary and \(T\) is upper triangular. The diagonal entries of \(T\) are the eigenvalues of \(A\).

### Spectral Theorem for Hermitian Matrices

If \(A=A^*\), then

\[
A=U\Lambda U^*,
\]

where \(U\) is unitary and \(\Lambda\) is real diagonal.

For real symmetric \(A\),

\[
A=Q\Lambda Q^T,
\]

with \(Q\) orthogonal and \(\Lambda\) real diagonal.

### Normal Matrix Theorem

A square complex matrix \(A\) is normal if and only if it is unitarily diagonalizable:

\[
A^*A=AA^*
\quad\Longleftrightarrow\quad
A=U\Lambda U^*.
\]

### SVD Theorem

Every \(A\in\mathbb C^{m\times n}\) has a singular value decomposition

\[
A=U\Sigma V^*,
\]

where \(U\) and \(V\) are unitary and \(\Sigma\) is rectangular diagonal with nonnegative singular values.

### Cholesky Theorem

If \(A=A^*\succ0\), then

\[
A=LL^*,
\]

where \(L\) is lower triangular with positive diagonal entries. In the real symmetric case, \(A=LL^T\).

### Schur Complement PD Test

For a Hermitian block matrix

\[
M=\begin{bmatrix}
A & B\\
B^* & C
\end{bmatrix},
\]

with \(A\succ0\),

\[
M\succ0
\quad\Longleftrightarrow\quad
A\succ0
\text{ and }
C-B^*A^{-1}B\succ0.
\]

## 4. Complete Proofs Most Likely to Be Asked

### Proof 1: Unitary Matrices Preserve Inner Products and Norms

Claim: If \(U^*U=I\), then

\[
\langle Ux,Uy\rangle=\langle x,y\rangle
\]

and

\[
\|Ux\|=\|x\|.
\]

Proof:

\[
\langle Ux,Uy\rangle=(Uy)^*(Ux)=y^*U^*Ux=y^*x=\langle x,y\rangle.
\]

Taking \(y=x\),

\[
\|Ux\|^2=(Ux)^*(Ux)=x^*U^*Ux=x^*x=\|x\|^2.
\]

Since norms are nonnegative,

\[
\|Ux\|=\|x\|.
\]

Likely exam wording: "Show that unitary matrices preserve lengths and angles."

Common mistake: using \(U^T\) instead of \(U^*\) in the complex case.

### Proof 2: \(P=QQ^*\) Is an Orthogonal Projection

Assume \(Q\in\mathbb C^{m\times k}\) has orthonormal columns, so

\[
Q^*Q=I_k.
\]

Let

\[
P=QQ^*.
\]

Then

\[
P^2=(QQ^*)(QQ^*)=Q(Q^*Q)Q^*=QIQ^*=QQ^*=P.
\]

Also,

\[
P^*=(QQ^*)^*=(Q^*)^*Q^*=QQ^*=P.
\]

Therefore \(P\) is an orthogonal projection.

Likely exam wording: "Prove that \(QQ^*\) is the orthogonal projection onto the column space of \(Q\)."

To finish the range statement:

- If \(y=Qc\in\mathcal R(Q)\), then \(Py=QQ^*Qc=Qc=y\).
- If \(z\perp\mathcal R(Q)\), then \(Q^*z=0\), so \(Pz=0\).

Common mistake: claiming \(QQ^*=I\) when \(Q\) is tall. Only \(Q^*Q=I\) is guaranteed.

### Proof 3: Projection Formula \(P=A(A^*A)^{-1}A^*\)

Assume \(A\in\mathbb C^{m\times n}\) has full column rank. Then \(A^*A\) is invertible.

Define

\[
P=A(A^*A)^{-1}A^*.
\]

Idempotence:

\[
P^2=A(A^*A)^{-1}A^*A(A^*A)^{-1}A^*
=A(A^*A)^{-1}(A^*A)(A^*A)^{-1}A^*
=P.
\]

Hermitian property:

\[
P^*=
\left[A(A^*A)^{-1}A^*\right]^*
=A\left[(A^*A)^{-1}\right]^*A^*.
\]

Since \(A^*A\) is Hermitian positive definite, its inverse is Hermitian, so

\[
\left[(A^*A)^{-1}\right]^*=(A^*A)^{-1}.
\]

Thus

\[
P^*=P.
\]

Therefore \(P\) is an orthogonal projection onto \(\mathcal R(A)\).

Likely exam wording: "Derive or verify the projection matrix onto \(\mathcal R(A)\) for full column rank \(A\)."

Common mistake: forgetting the full-column-rank condition needed for \((A^*A)^{-1}\).

### Proof 4: Normal Equations for Least Squares

Problem:

\[
\min_x \|Ax-b\|_2^2.
\]

Let

\[
f(x)=(Ax-b)^*(Ax-b).
\]

In the real case, expand:

\[
f(x)=x^TA^TAx-2x^TA^Tb+b^Tb.
\]

Setting the gradient to zero gives

\[
A^TAx=A^Tb.
\]

In the complex case, the normal equations are

\[
A^*Ax=A^*b.
\]

Geometric proof:

At the minimizer \(\hat x\), the residual

\[
r=b-A\hat x
\]

is orthogonal to the column space of \(A\). Therefore

\[
A^*r=0,
\]

so

\[
A^*(b-A\hat x)=0,
\]

which gives

\[
A^*A\hat x=A^*b.
\]

Likely exam wording: "Explain the geometric meaning of the normal equations."

Common mistake: treating \(A^TA\) as correct in complex least squares.

### Proof 5: Hermitian Eigenvalues Are Real

Assume

\[
A=A^*
\]

and

\[
Av=\lambda v,\qquad v\ne0.
\]

Then

\[
v^*Av=\lambda v^*v.
\]

Since \(A=A^*\),

\[
(v^*Av)^*=v^*A^*v=v^*Av.
\]

So \(v^*Av\) is real. Also \(v^*v>0\) is real. Hence

\[
\lambda=\frac{v^*Av}{v^*v}\in\mathbb R.
\]

Likely exam wording: "Prove eigenvalues of Hermitian matrices are real."

Common mistake: writing \(v^TAv\) in the complex case.

### Proof 6: Hermitian Eigenvectors for Distinct Eigenvalues Are Orthogonal

Assume \(A=A^*\),

\[
Ax=\lambda x,\qquad Ay=\mu y,
\]

with \(\lambda\ne\mu\). Since Hermitian eigenvalues are real, \(\overline{\mu}=\mu\).

Compute:

\[
y^*Ax=y^*(\lambda x)=\lambda y^*x.
\]

Also, from \(Ay=\mu y\),

\[
(Ay)^*=y^*A^*=\overline{\mu}y^*=\mu y^*.
\]

Since \(A^*=A\),

\[
y^*A=\mu y^*.
\]

Therefore

\[
y^*Ax=\mu y^*x.
\]

Combining,

\[
\lambda y^*x=\mu y^*x.
\]

Thus

\[
(\lambda-\mu)y^*x=0.
\]

Because \(\lambda\ne\mu\),

\[
y^*x=0.
\]

So \(x\) and \(y\) are orthogonal.

Likely exam wording: "Prove eigenspaces of a Hermitian matrix corresponding to distinct eigenvalues are orthogonal."

Common mistake: skipping the conjugate-transpose step from \(Ay=\mu y\) to \(y^*A=\mu y^*\).

### Proof 7: PSD Eigenvalue Criterion

Assume \(A=A^*\). By the spectral theorem,

\[
A=U\Lambda U^*
\]

with \(U\) unitary and \(\Lambda=\operatorname{diag}(\lambda_i)\) real.

For any \(x\), let

\[
y=U^*x.
\]

Then

\[
x^*Ax=x^*U\Lambda U^*x=y^*\Lambda y
=\sum_i\lambda_i |y_i|^2.
\]

If all \(\lambda_i\ge0\), then \(x^*Ax\ge0\), so \(A\succeq0\).

Conversely, if \(A\succeq0\), choose \(x=u_i\), the \(i\)-th eigenvector. Then

\[
u_i^*Au_i=\lambda_i u_i^*u_i=\lambda_i\ge0.
\]

Therefore all eigenvalues are nonnegative.

For positive definite, replace \(\ge0\) by \(>0\) for all nonzero \(x\). Then all eigenvalues must be strictly positive.

Likely exam wording: "Show that a Hermitian matrix is PSD iff all eigenvalues are nonnegative."

Common mistake: applying eigenvalue sign criteria to non-Hermitian matrices without qualification.

### Proof 8: Gram Matrices Are PSD

Let

\[
G=A^*A.
\]

Then \(G\) is Hermitian:

\[
G^*=(A^*A)^*=A^*A=G.
\]

For any \(x\),

\[
x^*Gx=x^*A^*Ax=(Ax)^*(Ax)=\|Ax\|^2\ge0.
\]

Therefore

\[
A^*A\succeq0.
\]

If \(A\) has full column rank, then \(Ax\ne0\) for all \(x\ne0\), so

\[
x^*A^*Ax=\|Ax\|^2>0,
\]

and \(A^*A\succ0\).

Likely exam wording: "Prove \(A^*A\) is positive semidefinite and state when it is positive definite."

Common mistake: saying \(A^*A\) is always invertible. It is invertible only when \(A\) has full column rank.

### Proof 9: Schur Theorem

Claim: For every square complex matrix \(A\), there exists a unitary \(U\) and upper triangular \(T\) such that

\[
A=UTU^*.
\]

Proof idea:

Every complex square matrix has at least one eigenvalue \(\lambda_1\) and eigenvector \(u_1\). Normalize \(u_1\), then complete it to an orthonormal basis:

\[
U_1=[u_1\ u_2\ \cdots\ u_n].
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

The lower-left block is zero because

\[
Au_1=\lambda_1u_1.
\]

Now apply the same argument recursively to \(A_2\). By induction, the lower-right block can be unitarily triangularized. Combining the unitary transformations gives

\[
U^*AU=T,
\]

where \(T\) is upper triangular. Thus

\[
A=UTU^*.
\]

Likely exam wording: "State Schur theorem and explain its proof."

Common mistake: saying Schur gives diagonal form. It gives triangular form.

### Proof 10: Normal Implies Unitary Diagonalizable

Assume \(A\) is normal:

\[
A^*A=AA^*.
\]

By Schur theorem,

\[
A=UTU^*
\]

with \(T\) upper triangular. Normality is preserved by unitary similarity, so \(T\) is normal.

Now use the fact: an upper triangular normal matrix is diagonal.

Reason: for an upper triangular normal \(T\), compare row and column norm relations from \(T^*T=TT^*\). The first column has only \(t_{11}\), while the first row has \(t_{11},t_{12},\ldots,t_{1n}\). Equality of the relevant diagonal entries forces

\[
t_{12}=\cdots=t_{1n}=0.
\]

Repeat inductively for the remaining block. Hence all off-diagonal entries are zero.

Thus \(T=\Lambda\), and

\[
A=U\Lambda U^*.
\]

Likely exam wording: "Use Schur theorem to prove that normal matrices are unitarily diagonalizable."

Common mistake: trying to prove this by assuming eigenvectors are already orthogonal.

### Proof 11: SVD Existence

Start with

\[
A^*A.
\]

It is Hermitian PSD, so by the spectral theorem,

\[
A^*A=V\Lambda V^*,
\]

where \(V\) is unitary and

\[
\Lambda=\operatorname{diag}(\lambda_1,\ldots,\lambda_n),\qquad \lambda_i\ge0.
\]

Define singular values

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

Check orthonormality:

\[
u_i^*u_j
=\frac{v_i^*A^*Av_j}{\sigma_i\sigma_j}
=\frac{v_i^*\lambda_jv_j}{\sigma_i\sigma_j}.
\]

If \(i\ne j\), then \(v_i^*v_j=0\), so \(u_i^*u_j=0\). If \(i=j\), then

\[
u_i^*u_i=\frac{\lambda_i}{\sigma_i^2}=1.
\]

Complete the \(u_i\)'s to an orthonormal basis of the output space. With \(U\) and \(V\) built from these bases,

\[
A=U\Sigma V^*.
\]

Likely exam wording: "Prove or explain why SVD exists."

Common mistake: saying singular values are eigenvalues of \(A\). They are square roots of eigenvalues of \(A^*A\).

### Proof 12: Best Rank-\(k\) Approximation by Truncated SVD

Statement: If

\[
A=\sum_{i=1}^r\sigma_i u_iv_i^*
\]

with \(\sigma_1\ge\cdots\ge\sigma_r>0\), then

\[
A_k=\sum_{i=1}^k\sigma_i u_iv_i^*
\]

is a best rank-\(k\) approximation to \(A\) in the spectral norm and Frobenius norm.

Expected proof idea, not full long proof:

Unitary invariance reduces the problem to approximating \(\Sigma\):

\[
\|A-B\|=\|U^*(A-B)V\|=\|\Sigma-U^*BV\|.
\]

Since \(U^*BV\) has rank at most \(k\), it cannot match all singular directions beyond the first \(k\). The best choice keeps the largest \(k\) singular values and discards the rest.

Consequences:

\[
\|A-A_k\|_2=\sigma_{k+1},
\]

\[
\|A-A_k\|_F=\sqrt{\sum_{i>k}\sigma_i^2}.
\]

Likely exam wording: "State the low-rank approximation theorem and explain why truncating the SVD is optimal."

Common mistake: truncating eigenvalues of \(A\) instead of singular values.

### Proof 13: Cholesky via Schur Complement

Assume \(A=A^*\succ0\). Partition

\[
A=
\begin{bmatrix}
\alpha & b^*\\
b & C
\end{bmatrix}.
\]

Since \(A\succ0\),

\[
\alpha>0.
\]

Set

\[
L=
\begin{bmatrix}
\sqrt{\alpha} & 0\\
\frac{b}{\sqrt{\alpha}} & L_2
\end{bmatrix}.
\]

Then matching \(LL^*\) requires

\[
L_2L_2^*=C-\frac{1}{\alpha}bb^*.
\]

The matrix

\[
C-\frac{1}{\alpha}bb^*
\]

is the Schur complement of \(\alpha\) in \(A\), and it is positive definite because \(A\succ0\) and \(\alpha>0\). Therefore, by induction, it has a Cholesky factor \(L_2\). This gives

\[
A=LL^*.
\]

Likely exam wording: "Explain the proof of Cholesky factorization using Schur complements."

Common mistake: saying subtracting a PSD rank-one term from a PD matrix is always PD. It is true here because it is the Schur complement of a PD block matrix.

### Proof 14: Schur Complement Positive Definiteness Test

Let

\[
M=
\begin{bmatrix}
A & B\\
B^* & C
\end{bmatrix},
\qquad A\succ0.
\]

Factor:

\[
M=
\begin{bmatrix}
I & 0\\
B^*A^{-1} & I
\end{bmatrix}
\begin{bmatrix}
A & 0\\
0 & C-B^*A^{-1}B
\end{bmatrix}
\begin{bmatrix}
I & A^{-1}B\\
0 & I
\end{bmatrix}.
\]

The left and right factors are conjugate transposes of each other:

\[
\begin{bmatrix}
I & A^{-1}B\\
0 & I
\end{bmatrix}^*
=
\begin{bmatrix}
I & 0\\
B^*A^{-1} & I
\end{bmatrix}.
\]

Congruence by an invertible matrix preserves positive definiteness. Therefore,

\[
M\succ0
\]

if and only if

\[
\begin{bmatrix}
A & 0\\
0 & C-B^*A^{-1}B
\end{bmatrix}\succ0.
\]

This holds if and only if

\[
A\succ0
\quad\text{and}\quad
C-B^*A^{-1}B\succ0.
\]

Likely exam wording: "Prove the Schur complement criterion for positive definiteness."

Common mistake: using ordinary similarity instead of congruence for definiteness.

### Proof 15: Matrix 2-Norm Equals Largest Singular Value

Let

\[
A=U\Sigma V^*.
\]

Then

\[
\|Ax\|_2=\|U\Sigma V^*x\|_2.
\]

Unitary matrices preserve norms, so if \(y=V^*x\), then \(\|y\|_2=\|x\|_2\), and

\[
\frac{\|Ax\|_2}{\|x\|_2}
=
\frac{\|\Sigma y\|_2}{\|y\|_2}.
\]

Now

\[
\|\Sigma y\|_2^2
=\sum_i\sigma_i^2|y_i|^2
\le \sigma_1^2\sum_i|y_i|^2
=\sigma_1^2\|y\|_2^2.
\]

Therefore

\[
\|A\|_{2,2}\le\sigma_1.
\]

Equality is attained by taking \(y=e_1\), equivalently \(x=v_1\). Then

\[
\|Av_1\|_2=\sigma_1.
\]

Thus

\[
\|A\|_{2,2}=\sigma_1.
\]

Likely exam wording: "Prove that the induced 2-norm is the largest singular value."

Common mistake: using largest eigenvalue of \(A\) instead of largest singular value.

## 5. Factorizations Last-Day Table

| Factorization | Form | Hypothesis | What it reveals |
|---|---|---|---|
| LU | \(A=LU\) or \(PA=LU\) | pivot assumptions | triangular solves |
| QR | \(A=QR\) | general; clean reduced form if full column rank | orthonormal basis for range |
| Schur | \(A=UTU^*\) | square complex | triangular form, eigenvalues on diagonal |
| Spectral | \(A=U\Lambda U^*\) | Hermitian | real eigenvalues, orthonormal eigenbasis |
| Normal diagonalization | \(A=U\Lambda U^*\) | \(A^*A=AA^*\) | unitary eigenbasis |
| Cholesky | \(A=LL^*\) | Hermitian PD | triangular square root |
| PSD square root | \(A=SS^*\) | Hermitian PSD | energy/covariance factor |
| Block LDU | block triangular product | invertible block | Schur complement |
| Woodbury | \((A+BCD)^{-1}\) formula | compatible inverses | low-rank inverse update |
| DFT diagonalization | \(C=F^*\Lambda F\) | circulant | convolution becomes multiplication |
| SVD | \(A=U\Sigma V^*\) | any matrix | rank, geometry, norms |
| Polar | \(A=QH\) | square nonsingular or partial-isometry generalization | unitary-like times PSD |

## 6. Danger Topics

### \(A^T\) vs \(A^*\)

Use \(A^T\) for real transpose. Use \(A^*\) for complex conjugate transpose. In complex inner products, projections, Hermitian matrices, unitary matrices, SVD, and PSD definitions, use \(A^*\).

### Hermitian vs Symmetric

Hermitian:

\[
A^*=A.
\]

Symmetric:

\[
A^T=A.
\]

Symmetric is correct only over real fields.

### PSD vs PD

PSD:

\[
x^*Ax\ge0.
\]

PD:

\[
x^*Ax>0\quad x\ne0.
\]

PSD allows zero eigenvalues and may be singular. PD has strictly positive eigenvalues and is invertible.

### Projection vs Orthogonal Projection

Projection:

\[
P^2=P.
\]

Orthogonal projection:

\[
P^2=P,\qquad P^*=P.
\]

### Diagonalizable vs Unitarily Diagonalizable

Diagonalizable:

\[
A=T\Lambda T^{-1}.
\]

Unitarily diagonalizable:

\[
A=U\Lambda U^*.
\]

Unitary diagonalization is stronger and is equivalent to normality over \(\mathbb C\).

### Schur vs Diagonalization

Schur always gives triangular form for square complex matrices:

\[
A=UTU^*.
\]

It does not always give diagonal form.

### Normal vs Hermitian

Hermitian implies normal, but normal does not imply Hermitian.

Normal:

\[
A^*A=AA^*.
\]

Hermitian:

\[
A^*=A.
\]

### Singular Values vs Eigenvalues

Singular values are nonnegative and come from \(A^*A\):

\[
A^*Av_i=\sigma_i^2v_i.
\]

Eigenvalues of \(A\) solve

\[
Av=\lambda v.
\]

Do not confuse them.

## 7. Likely Exam Questions and Minimal Answer Skeletons

### Question 1

State and prove that an orthogonal projection matrix is Hermitian and idempotent.

Minimal answer:

Use \(P=QQ^*\), \(Q^*Q=I\). Show \(P^2=P\) and \(P^*=P\).

### Question 2

Prove eigenvalues of Hermitian matrices are real and eigenvectors for distinct eigenvalues are orthogonal.

Minimal answer:

Use \(v^*Av=\lambda v^*v\) for real eigenvalues. For orthogonality, compare \(y^*Ax=\lambda y^*x\) and \(y^*Ax=\mu y^*x\).

### Question 3

State Schur theorem and use it to prove normal matrices are unitarily diagonalizable.

Minimal answer:

Schur gives \(A=UTU^*\). Normality transfers to \(T\). Upper triangular normal implies diagonal. Hence \(A=U\Lambda U^*\).

### Question 4

State the spectral theorem and derive the PSD eigenvalue criterion.

Minimal answer:

Write \(A=U\Lambda U^*\), let \(y=U^*x\), compute \(x^*Ax=\sum_i\lambda_i|y_i|^2\).

### Question 5

Prove \(A^*A\) is PSD and explain when it is PD.

Minimal answer:

\[
x^*A^*Ax=\|Ax\|^2\ge0.
\]

It is PD iff \(Ax\ne0\) for all \(x\ne0\), i.e. \(A\) has full column rank.

### Question 6

Prove or explain the existence of SVD.

Minimal answer:

Diagonalize \(A^*A=V\Lambda V^*\), set \(\sigma_i=\sqrt{\lambda_i}\), define \(u_i=Av_i/\sigma_i\), prove orthonormality, complete bases.

### Question 7

State and prove the Schur complement positive definiteness criterion.

Minimal answer:

Use block LDU/congruence factorization and show \(M\succ0\) iff \(A\succ0\) and the Schur complement is PD.

### Question 8

Prove \(\|A\|_2=\sigma_{\max}(A)\).

Minimal answer:

Use SVD and unitary invariance. Reduce to \(\Sigma\), bound by \(\sigma_1\), and attain equality at the first right singular vector.

## 8. Emergency Last-Night List

Memorize these exact statements:

1. \(U^*U=I\) implies inner products and norms are preserved.
2. \(P^2=P\) means projection; \(P^*=P\) makes it orthogonal.
3. \(P=QQ^*\) and \(P=A(A^*A)^{-1}A^*\).
4. \(A=A^*\) implies real eigenvalues and orthogonal eigenspaces.
5. \(A\succeq0\) iff \(x^*Ax\ge0\) iff Hermitian eigenvalues are nonnegative.
6. \(A^*A\succeq0\), and \(A^*A\succ0\) iff \(A\) has full column rank.
7. Schur: \(A=UTU^*\), every square complex matrix.
8. Normal: \(A^*A=AA^*\) iff \(A=U\Lambda U^*\).
9. SVD: \(A=U\Sigma V^*\), every matrix.
10. Cholesky: \(A=LL^*\), Hermitian positive definite.
11. Schur complement: \(M\succ0\) iff leading block and Schur complement are PD.
12. \(\|A\|_2=\sigma_{\max}(A)\).

If time is limited, prioritize proofs 1, 2, 5, 6, 7, 9, 10, 11, and 15 from this review.
