# Professor-Style Theoretical Questions with Answers

Scope: likely proof/concept questions for a Linear System Theory final. These are not numerical exercises. Each answer is written in the style expected for a theoretical exam: definition, key property, proof argument, and common trap where relevant.

## Projection and Least Squares

### 1. Prove that the orthogonal projection \(P_Vx\) is the closest vector in \(V\) to \(x\).

Let

\[
x=P_Vx+r,
\]

where \(P_Vx\in V\) and \(r=x-P_Vx\in V^\perp\). For any \(v\in V\),

\[
x-v=(x-P_Vx)+(P_Vx-v).
\]

The first term is in \(V^\perp\), while the second is in \(V\), so they are orthogonal. Hence, by Pythagoras,

\[
\|x-v\|^2=\|x-P_Vx\|^2+\|P_Vx-v\|^2\ge \|x-P_Vx\|^2.
\]

Thus \(P_Vx\) is the closest vector in \(V\) to \(x\). Equality holds only when \(v=P_Vx\).

### 2. Let \(P^2=P\). Explain why \(P\) is a projection. If also \(P^*=P\), prove it is an orthogonal projection.

The identity \(P^2=P\) means applying \(P\) twice is the same as applying it once. Therefore, points in \(\mathcal R(P)\) are fixed by \(P\):

\[
y\in\mathcal R(P)\Rightarrow y=Px \Rightarrow Py=P^2x=Px=y.
\]

So \(P\) projects onto \(\mathcal R(P)\). If also \(P^*=P\), then the projection direction is orthogonal to the range. Indeed, if \(z\in\mathcal N(P)\) and \(y\in\mathcal R(P)\), write \(y=Px\). Then

\[
y^*z=(Px)^*z=x^*P^*z=x^*Pz=0.
\]

Thus \(\mathcal N(P)\perp\mathcal R(P)\), so \(P\) is an orthogonal projection.

### 3. If \(Q^*Q=I\), prove \(P=QQ^*\) is an orthogonal projection.

Compute

\[
P^2=(QQ^*)(QQ^*)=Q(Q^*Q)Q^*=QIQ^*=QQ^*=P.
\]

Also

\[
P^*=(QQ^*)^*=QQ^*=P.
\]

Therefore \(P\) is an orthogonal projection. Its range is \(\mathcal R(Q)\), because if \(y=Qc\), then

\[
Py=QQ^*Qc=Qc=y.
\]

Common trap: if \(Q\) is tall, \(Q^*Q=I\), but generally \(QQ^*\ne I\). Instead, \(QQ^*\) is the projection onto \(\mathcal R(Q)\).

### 4. For full column-rank \(A\), prove \(P=A(A^*A)^{-1}A^*\) is the orthogonal projection onto \(\mathcal R(A)\).

Since \(A\) has full column rank, \(A^*A\) is invertible. Define

\[
P=A(A^*A)^{-1}A^*.
\]

Then

\[
P^2=A(A^*A)^{-1}A^*A(A^*A)^{-1}A^*
=A(A^*A)^{-1}(A^*A)(A^*A)^{-1}A^*=P.
\]

Also \(A^*A\) is Hermitian positive definite, so \((A^*A)^{-1}\) is Hermitian. Hence

\[
P^*=\left[A(A^*A)^{-1}A^*\right]^*
=A(A^*A)^{-1}A^*=P.
\]

Thus \(P\) is an orthogonal projection. Since \(Px\in\mathcal R(A)\) for every \(x\), and \(P\) fixes every vector \(y=Ac\in\mathcal R(A)\),

\[
Py=A(A^*A)^{-1}A^*Ac=Ac=y,
\]

it projects onto \(\mathcal R(A)\).

### 5. Derive the normal equations \(A^*A\hat x=A^*b\) from residual orthogonality.

The least-squares approximation \(A\hat x\) is the orthogonal projection of \(b\) onto \(\mathcal R(A)\). Therefore the residual

\[
r=b-A\hat x
\]

is orthogonal to \(\mathcal R(A)\). Since columns of \(A\) span \(\mathcal R(A)\),

\[
A^*r=0.
\]

Thus

\[
A^*(b-A\hat x)=0,
\]

so

\[
A^*A\hat x=A^*b.
\]

In the real case this becomes \(A^TA\hat x=A^Tb\). In the complex case, use \(A^*\), not \(A^T\).

## Range, Nullspace, and Orthogonality

### 6. Prove \(\mathcal R(A)^\perp=\mathcal N(A^*)\).

Let \(z\in\mathcal R(A)^\perp\). Then for every \(x\),

\[
z^*Ax=0.
\]

Equivalently,

\[
(A^*z)^*x=0
\]

for every \(x\), so \(A^*z=0\). Hence \(z\in\mathcal N(A^*)\).

Conversely, if \(z\in\mathcal N(A^*)\), then \(A^*z=0\). For any \(y\in\mathcal R(A)\), \(y=Ax\), so

\[
z^*y=z^*Ax=(A^*z)^*x=0.
\]

Thus \(z\perp\mathcal R(A)\). Therefore

\[
\mathcal R(A)^\perp=\mathcal N(A^*).
\]

### 7. Explain why \(A^*A\) is always Hermitian positive semidefinite.

Hermitian:

\[
(A^*A)^*=A^*A.
\]

Positive semidefinite:

\[
x^*A^*Ax=(Ax)^*(Ax)=\|Ax\|^2\ge0.
\]

Therefore \(A^*A\succeq0\).

### 8. Prove \(A^*A\succ0\) iff \(A\) has full column rank.

If \(A\) has full column rank, then \(Ax\ne0\) for all \(x\ne0\). Therefore

\[
x^*A^*Ax=\|Ax\|^2>0
\]

for all \(x\ne0\), so \(A^*A\succ0\).

Conversely, if \(A^*A\succ0\), then for \(x\ne0\),

\[
\|Ax\|^2=x^*A^*Ax>0.
\]

Thus \(Ax\ne0\) for all \(x\ne0\), so \(\mathcal N(A)=\{0\}\), and \(A\) has full column rank.

### 9. Explain geometrically why least squares is a projection problem.

The vector \(Ax\) always lies in \(\mathcal R(A)\). Solving

\[
\min_x\|Ax-b\|
\]

means finding the vector in \(\mathcal R(A)\) closest to \(b\). The closest vector is the orthogonal projection of \(b\) onto \(\mathcal R(A)\). Therefore \(A\hat x=P_{\mathcal R(A)}b\), and the residual is orthogonal to the column space:

\[
b-A\hat x\in\mathcal R(A)^\perp.
\]

### 10. If \(x\in\mathcal R(A)\) and \(z\in\mathcal N(A^*)\), prove \(x\perp z\).

Since \(x\in\mathcal R(A)\), there exists \(u\) such that \(x=Au\). Since \(z\in\mathcal N(A^*)\), \(A^*z=0\). Then

\[
z^*x=z^*Au=(A^*z)^*u=0.
\]

Therefore \(x\perp z\).

## Unitary and Orthogonal Matrices

### 11. Prove that a unitary matrix preserves inner products.

If \(U^*U=I\), then

\[
\langle Ux,Uy\rangle=(Uy)^*(Ux)=y^*U^*Ux=y^*x=\langle x,y\rangle.
\]

Thus unitary matrices preserve inner products.

### 12. Prove that a unitary matrix preserves norms.

Using the previous result with \(y=x\),

\[
\|Ux\|^2=(Ux)^*(Ux)=x^*U^*Ux=x^*x=\|x\|^2.
\]

Since norms are nonnegative,

\[
\|Ux\|=\|x\|.
\]

### 13. If \(U\) is unitary, prove \(U^{-1}=U^*\).

By definition,

\[
U^*U=I,\qquad UU^*=I.
\]

Thus \(U^*\) is both a left inverse and right inverse of \(U\). Therefore

\[
U^{-1}=U^*.
\]

### 14. Explain why multiplying by a unitary matrix does not change least-squares error.

For unitary \(U\),

\[
\|U(Ax-b)\|=\|Ax-b\|.
\]

Thus minimizing \(\|Ax-b\|\) is equivalent to minimizing \(\|UAx-Ub\|\). This is why QR factorization is useful: unitary transformations simplify \(A\) without changing the least-squares objective.

### 15. Distinguish orthogonal and unitary matrices. When is \(Q^TQ=I\) enough?

Orthogonal is the real case:

\[
Q^TQ=I.
\]

Unitary is the complex case:

\[
U^*U=I.
\]

If all entries are real, then \(Q^*=Q^T\), so \(Q^TQ=I\) is enough. In complex spaces, \(Q^TQ=I\) is not the right condition; use \(Q^*Q=I\).

## Hermitian and Positive Semidefinite Matrices

### 16. Prove that eigenvalues of a Hermitian matrix are real.

Assume \(A=A^*\) and \(Av=\lambda v\), \(v\ne0\). Then

\[
v^*Av=\lambda v^*v.
\]

But

\[
(v^*Av)^*=v^*A^*v=v^*Av,
\]

so \(v^*Av\) is real. Since \(v^*v>0\) is real,

\[
\lambda=\frac{v^*Av}{v^*v}\in\mathbb R.
\]

### 17. Prove that eigenvectors of a Hermitian matrix corresponding to distinct eigenvalues are orthogonal.

Assume \(A=A^*\), \(Ax=\lambda x\), \(Ay=\mu y\), and \(\lambda\ne\mu\). Hermitian eigenvalues are real. Compute

\[
y^*Ax=\lambda y^*x.
\]

From \(Ay=\mu y\),

\[
(Ay)^*=y^*A^*=\mu y^*.
\]

Since \(A^*=A\), \(y^*A=\mu y^*\). Hence

\[
y^*Ax=\mu y^*x.
\]

Therefore

\[
(\lambda-\mu)y^*x=0.
\]

Since \(\lambda\ne\mu\),

\[
y^*x=0.
\]

Thus the eigenvectors are orthogonal.

### 18. State the spectral theorem for Hermitian matrices.

If \(A=A^*\), then there exists a unitary matrix \(U\) and a real diagonal matrix \(\Lambda\) such that

\[
A=U\Lambda U^*.
\]

Equivalently, a Hermitian matrix has an orthonormal eigenbasis and real eigenvalues.

For a real symmetric matrix \(A=A^T\),

\[
A=Q\Lambda Q^T,
\]

where \(Q\) is orthogonal and \(\Lambda\) is real diagonal.

### 19. Prove that for Hermitian \(A\), \(A\succeq0\) iff all eigenvalues are nonnegative.

By the spectral theorem,

\[
A=U\Lambda U^*.
\]

Let \(y=U^*x\). Then

\[
x^*Ax=y^*\Lambda y=\sum_i\lambda_i |y_i|^2.
\]

If all \(\lambda_i\ge0\), then \(x^*Ax\ge0\), so \(A\succeq0\).

Conversely, if \(A\succeq0\), choose \(x=u_i\), an eigenvector. Then

\[
u_i^*Au_i=\lambda_i u_i^*u_i=\lambda_i\ge0.
\]

Thus every eigenvalue is nonnegative.

### 20. Prove that \(A=SS^*\) implies \(A\succeq0\).

For any \(x\),

\[
x^*Ax=x^*SS^*x=(S^*x)^*(S^*x)=\|S^*x\|^2\ge0.
\]

Also \(SS^*\) is Hermitian:

\[
(SS^*)^*=SS^*.
\]

Therefore \(A\succeq0\).

### 21. Prove the converse: if \(A\succeq0\), then \(A=SS^*\) for some \(S\).

Since \(A\succeq0\), \(A\) is Hermitian and has spectral decomposition

\[
A=U\Lambda U^*,
\]

where \(\Lambda\ge0\). Define

\[
\Lambda^{1/2}=\operatorname{diag}(\sqrt{\lambda_i})
\]

and

\[
S=U\Lambda^{1/2}.
\]

Then

\[
SS^*=U\Lambda^{1/2}(\Lambda^{1/2})U^*=U\Lambda U^*=A.
\]

Thus every PSD matrix has a square-root factorization.

### 22. Explain the difference between positive definite and positive semidefinite using eigenvalues and geometry.

For Hermitian \(A\),

\[
A\succ0
\]

means all eigenvalues are strictly positive. Then

\[
x^*Ax>0
\]

for every nonzero \(x\), and the quadratic form has no flat directions.

\[
A\succeq0
\]

means all eigenvalues are nonnegative. Zero eigenvalues are allowed, so some nonzero directions may satisfy

\[
x^*Ax=0.
\]

Geometrically, PSD can have flat directions; PD cannot.

## Normal Matrices, Schur, and Diagonalization

### 23. State Schur theorem.

Every square complex matrix \(A\in\mathbb C^{n\times n}\) admits

\[
A=UTU^*,
\]

where \(U\) is unitary and \(T\) is upper triangular. The diagonal entries of \(T\) are the eigenvalues of \(A\).

### 24. Use Schur theorem to prove that every normal matrix is unitarily diagonalizable.

By Schur theorem,

\[
A=UTU^*
\]

with \(T\) upper triangular. If \(A\) is normal, then \(T=U^*AU\) is also normal. A triangular normal matrix must be diagonal. Therefore \(T=\Lambda\), and

\[
A=U\Lambda U^*.
\]

Thus every normal matrix is unitarily diagonalizable.

### 25. Explain why Schur factorization is not the same as diagonalization.

Schur gives

\[
A=UTU^*
\]

with \(T\) upper triangular. It exists for every square complex matrix. Diagonalization requires

\[
A=T_0\Lambda T_0^{-1}
\]

with \(\Lambda\) diagonal, and this requires enough linearly independent eigenvectors. Schur is always triangular; diagonalization is a stronger condition.

### 26. Give a matrix property that guarantees unitary diagonalization.

Normality guarantees unitary diagonalization:

\[
A^*A=AA^*
\quad\Longleftrightarrow\quad
A=U\Lambda U^*.
\]

Special cases include Hermitian, skew-Hermitian, and unitary matrices.

### 27. Prove that Hermitian matrices are normal.

If \(A=A^*\), then

\[
A^*A=AA
\]

and

\[
AA^*=AA.
\]

Therefore

\[
A^*A=AA^*.
\]

So \(A\) is normal.

### 28. Prove that unitary matrices are normal.

If \(U\) is unitary, then

\[
U^*U=I
\]

and

\[
UU^*=I.
\]

Thus

\[
U^*U=UU^*.
\]

Therefore \(U\) is normal.

### 29. Explain why diagonalizable does not imply unitarily diagonalizable.

Diagonalizable means

\[
A=T\Lambda T^{-1}
\]

for some invertible \(T\). Unitarily diagonalizable means

\[
A=U\Lambda U^*
\]

with \(U\) unitary. The second requires an orthonormal eigenbasis and is equivalent to normality. A matrix may have enough eigenvectors to be diagonalizable, but those eigenvectors may not be orthogonal, so the matrix need not be unitarily diagonalizable.

### 30. Explain what the off-diagonal entries in Schur form mean conceptually.

In Schur form,

\[
U^*AU=T.
\]

The diagonal entries are eigenvalues. If \(T\) is diagonal, the orthonormal Schur basis consists of eigenvectors. Off-diagonal entries represent coupling between Schur basis directions. For normal matrices this coupling disappears, which is why normal matrices are unitarily diagonalizable.

## QR and Gram-Schmidt

### 31. Derive \(A=QR\) from Gram-Schmidt.

Let the columns of \(A\) be \(a_1,\ldots,a_n\). Gram-Schmidt constructs orthonormal vectors \(q_1,\ldots,q_n\). Each \(a_k\) can be written as a combination of the first \(k\) orthonormal vectors:

\[
a_k=\sum_{i=1}^k q_i r_{ik}.
\]

Collecting these equations gives

\[
A=QR,
\]

where \(Q=[q_1\ \cdots\ q_n]\) and \(R=(r_{ik})\) is upper triangular.

### 32. Explain the difference between classical Gram-Schmidt and modified Gram-Schmidt.

Classical Gram-Schmidt subtracts projections of the original vector \(a_k\) onto all previously computed \(q_i\)'s in one formula. Modified Gram-Schmidt updates the remaining vectors after each projection step. Mathematically they aim for the same QR factorization, but modified Gram-Schmidt is usually more stable numerically because it removes components sequentially from the current residual vectors.

### 33. In reduced QR, why does \(Q^*Q=I\) but generally \(QQ^*\ne I\)?

In reduced QR for \(A\in\mathbb C^{m\times n}\) with \(m\ge n\), \(Q\in\mathbb C^{m\times n}\) has orthonormal columns. Therefore

\[
Q^*Q=I_n.
\]

But \(QQ^*\in\mathbb C^{m\times m}\) projects onto the \(n\)-dimensional column space of \(Q\). If \(n<m\), this projection is not the identity on all of \(\mathbb C^m\). Thus generally

\[
QQ^*\ne I_m.
\]

### 34. Show how QR gives the least-squares solution.

Let \(A=Q_1R_1\) be reduced QR with full column rank. Then

\[
\min_x\|Ax-b\|_2=\min_x\|Q_1R_1x-b\|_2.
\]

Complete \(Q_1\) to a unitary \(Q=[Q_1\ Q_2]\). Since unitary transformations preserve norms,

\[
\|Q^*(Q_1R_1x-b)\|_2^2
=
\left\|
\begin{bmatrix}
R_1x-Q_1^*b\\
-Q_2^*b
\end{bmatrix}
\right\|_2^2.
\]

The second block does not depend on \(x\), so the minimum occurs when

\[
R_1x=Q_1^*b.
\]

### 35. Explain why QR is numerically preferable to solving normal equations.

Normal equations use

\[
A^*Ax=A^*b.
\]

Forming \(A^*A\) squares the condition number:

\[
\kappa(A^*A)=\kappa(A)^2
\]

in the 2-norm. QR uses unitary transformations, which preserve norms and do not amplify conditioning in the same way. Therefore QR is usually more numerically stable for least squares.

## SVD and Norms

### 36. Prove existence of SVD using the spectral theorem applied to \(A^*A\).

Since \(A^*A\) is Hermitian PSD, spectral theorem gives

\[
A^*A=V\Lambda V^*,
\]

where \(\Lambda\ge0\). Define

\[
\sigma_i=\sqrt{\lambda_i}.
\]

For \(\sigma_i>0\), define

\[
u_i=\frac{Av_i}{\sigma_i}.
\]

Then

\[
Av_i=\sigma_i u_i.
\]

The \(u_i\)'s are orthonormal:

\[
u_i^*u_j=\frac{v_i^*A^*Av_j}{\sigma_i\sigma_j}.
\]

Using \(A^*Av_j=\sigma_j^2v_j\) and \(v_i^*v_j=\delta_{ij}\), this gives \(u_i^*u_j=\delta_{ij}\). Complete the \(u_i\)'s and \(v_i\)'s to orthonormal bases. Then

\[
A=U\Sigma V^*.
\]

### 37. Explain why singular values are nonnegative.

Singular values are defined as

\[
\sigma_i=\sqrt{\lambda_i(A^*A)}.
\]

Since \(A^*A\succeq0\), all eigenvalues of \(A^*A\) are nonnegative. Therefore their square roots are real and nonnegative.

### 38. Prove \(\|A\|_2=\sigma_{\max}(A)\).

Let

\[
A=U\Sigma V^*.
\]

Then, using unitary norm preservation and \(y=V^*x\),

\[
\frac{\|Ax\|_2}{\|x\|_2}
=\frac{\|\Sigma y\|_2}{\|y\|_2}.
\]

Now

\[
\|\Sigma y\|_2^2=\sum_i\sigma_i^2|y_i|^2
\le \sigma_1^2\sum_i|y_i|^2
=\sigma_1^2\|y\|_2^2.
\]

Thus \(\|A\|_2\le\sigma_1\). Equality is achieved by choosing \(y=e_1\), equivalently \(x=v_1\). Hence

\[
\|A\|_2=\sigma_1=\sigma_{\max}(A).
\]

### 39. Explain the geometric meaning of SVD as rotation, stretching, rotation.

In

\[
A=U\Sigma V^*,
\]

\(V^*\) changes the input orthonormal coordinates, \(\Sigma\) stretches along coordinate axes by singular values, and \(U\) rotates or reflects into the output space. Thus a unit ball maps to an ellipsoid whose semi-axis lengths are singular values and whose directions are left singular vectors.

### 40. State the best rank-\(k\) approximation theorem using truncated SVD.

If

\[
A=\sum_{i=1}^r\sigma_i u_iv_i^*
\]

with \(\sigma_1\ge\cdots\ge\sigma_r>0\), then

\[
A_k=\sum_{i=1}^k\sigma_i u_iv_i^*
\]

is a best rank-\(k\) approximation to \(A\) in both spectral norm and Frobenius norm. Moreover,

\[
\|A-A_k\|_2=\sigma_{k+1},
\]

and

\[
\|A-A_k\|_F=\sqrt{\sum_{i>k}\sigma_i^2}.
\]

### 41. Explain why singular values, not eigenvalues, determine the induced 2-norm.

The induced 2-norm measures maximum length amplification:

\[
\|A\|_2=\max_{x\ne0}\frac{\|Ax\|_2}{\|x\|_2}.
\]

Length amplification depends on \(A^*A\):

\[
\|Ax\|_2^2=x^*A^*Ax.
\]

Therefore the maximum amplification is controlled by the largest eigenvalue of \(A^*A\), whose square root is the largest singular value. Eigenvalues of \(A\) describe invariant directions of \(A\), not necessarily maximum length gain.

### 42. Relate SVD to the four fundamental subspaces.

For rank \(r\), in the SVD \(A=U\Sigma V^*\):

\[
\mathcal R(A)=\operatorname{span}(u_1,\ldots,u_r),
\]

\[
\mathcal N(A^*)=\operatorname{span}(u_{r+1},\ldots,u_m),
\]

\[
\mathcal R(A^*)=\operatorname{span}(v_1,\ldots,v_r),
\]

\[
\mathcal N(A)=\operatorname{span}(v_{r+1},\ldots,v_n).
\]

Thus SVD gives orthonormal bases for the four fundamental subspaces.

## Cholesky and Schur Complement

### 43. State Cholesky factorization and its hypothesis.

If \(A=A^*\succ0\), then

\[
A=LL^*,
\]

where \(L\) is lower triangular with positive diagonal entries. In the real symmetric case,

\[
A=LL^T.
\]

### 44. Prove Cholesky factorization using a Schur complement argument.

Partition

\[
A=
\begin{bmatrix}
\alpha & b^*\\
b & C
\end{bmatrix}.
\]

Since \(A\succ0\), \(\alpha>0\). Let

\[
L=
\begin{bmatrix}
\sqrt{\alpha} & 0\\
\frac{b}{\sqrt{\alpha}} & L_2
\end{bmatrix}.
\]

Then \(LL^*=A\) requires

\[
L_2L_2^*=C-\frac{1}{\alpha}bb^*.
\]

The matrix on the right is the Schur complement of \(\alpha\) in \(A\). Since \(A\succ0\), this Schur complement is also positive definite. By induction, it has a Cholesky factor \(L_2\). Hence \(A=LL^*\).

### 45. State the Schur complement positive definiteness criterion.

For

\[
M=
\begin{bmatrix}
A & B\\
B^* & C
\end{bmatrix},
\qquad A\succ0,
\]

we have

\[
M\succ0
\quad\Longleftrightarrow\quad
A\succ0
\text{ and }
C-B^*A^{-1}B\succ0.
\]

### 46. Prove the Schur complement PD criterion using block factorization.

Factor

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

The first and third factors are conjugate transposes of each other. Since congruence by an invertible matrix preserves positive definiteness, \(M\succ0\) iff the block diagonal middle matrix is positive definite. That holds iff

\[
A\succ0
\quad\text{and}\quad
C-B^*A^{-1}B\succ0.
\]

### 47. Explain why subtracting a PSD rank-one term from a PD matrix is not always safe, but is safe in the Cholesky proof.

In general, if \(C\succ0\) and \(vv^*\succeq0\), it does not follow that

\[
C-vv^*\succ0.
\]

The subtraction may remove too much curvature in some direction. In the Cholesky proof, however,

\[
C-\frac{1}{\alpha}bb^*
\]

is not an arbitrary subtraction. It is the Schur complement of a positive definite block matrix. The Schur complement theorem guarantees it remains positive definite.

### 48. Derive the block LDU factorization and identify the Schur complement.

For

\[
A=
\begin{bmatrix}
A_{11} & A_{12}\\
A_{21} & A_{22}
\end{bmatrix},
\]

with \(A_{11}\) invertible,

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
S=A_{22}-A_{21}A_{11}^{-1}A_{12}.
\]

This \(S\) is the Schur complement of \(A_{11}\).

## Covariance and Random Vectors

### 49. Prove that a covariance matrix is positive semidefinite.

Let

\[
C_x=\mathbb E[(x-\mu)(x-\mu)^*].
\]

For any vector \(a\),

\[
a^*C_xa
=\mathbb E[a^*(x-\mu)(x-\mu)^*a]
=\mathbb E\left[|(x-\mu)^*a|^2\right]\ge0.
\]

Therefore \(C_x\succeq0\).

### 50. Explain why uncorrelated does not imply independent in general.

Uncorrelated means covariance is zero:

\[
\operatorname{Cov}(X,Y)=0.
\]

This only removes linear dependence. Independence is stronger: the joint distribution must factor as the product of marginals. Variables can have nonlinear dependence while having zero covariance.

### 51. Explain why uncorrelated Gaussian random variables are independent.

For jointly Gaussian random variables, the full dependence structure is determined by the mean vector and covariance matrix. If the covariance matrix is diagonal, the joint Gaussian density factors into a product of one-dimensional Gaussian densities. Therefore, in the jointly Gaussian case, uncorrelated components are independent.

### 52. Show how \(C=SS^*\) colors white noise.

Let \(z\) be white with covariance \(I\). Define

\[
x=Sz.
\]

Then

\[
C_x=\mathbb E[xx^*]
=\mathbb E[Szz^*S^*]
=S\mathbb E[zz^*]S^*
=SIS^*
=SS^*.
\]

Thus \(S\) maps white noise into colored noise with covariance \(SS^*\).

### 53. Explain whitening using \(C^{-1/2}CC^{-1/2}=I\).

If \(C\succ0\), write

\[
C=U\Lambda U^*.
\]

Then

\[
C^{-1/2}=U\Lambda^{-1/2}U^*.
\]

Therefore

\[
C^{-1/2}CC^{-1/2}
=U\Lambda^{-1/2}U^*U\Lambda U^*U\Lambda^{-1/2}U^*
=UIU^*
=I.
\]

Applying \(C^{-1/2}\) to a random vector with covariance \(C\) produces a whitened vector with identity covariance. If \(C\) is singular, whitening is only possible on the nonzero-eigenvalue subspace.

## Highest-Yield Short List

If time is limited, prioritize these:

1. Orthogonal projection is closest.
2. \(P=QQ^*\) is an orthogonal projection.
3. \(P=A(A^*A)^{-1}A^*\).
4. Normal equations from residual orthogonality.
5. \(\mathcal R(A)^\perp=\mathcal N(A^*)\).
6. \(A^*A\succeq0\), and when \(A^*A\succ0\).
7. Unitary matrices preserve inner products and norms.
8. Hermitian eigenvalues are real.
9. Hermitian eigenspaces for distinct eigenvalues are orthogonal.
10. PSD eigenvalue criterion.
11. Schur theorem.
12. Normal implies unitarily diagonalizable.
13. SVD existence from \(A^*A\).
14. \(\|A\|_2=\sigma_{\max}(A)\).
15. Schur complement PD criterion.
