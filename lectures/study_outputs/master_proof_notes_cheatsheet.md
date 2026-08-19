# Exam-Oriented Master Proof Notes and Cheat Sheet

Scope: Lectures 2-23, using the completed lecture notes in `study_outputs/lecture_notes` and the corrected transcripts in `corrected`. The midterm covered Lectures 2-12, so the final prediction is inclusive but weighted toward Lectures 13-23.

This is not a general summary. It is organized by proof-testable structures and notation traps.

## PART 1 - Professor's Exam Logic

- The professor tends to ask definitions plus their immediate consequences: if a matrix is unitary, Hermitian, normal, PSD, a projection, etc., what follows immediately and why.
- The highest-yield topics are structures that compress many facts into one condition: \(P^2=P\), \(P^*=P\), \(A^*=A\), \(A^*A=AA^*\), \(U^*U=I\), \(x^*Ax\ge 0\).
- Proof questions are usually short structural arguments, not long computations: preserve norms, show eigenvalues are real, show eigenspaces are orthogonal, derive projection identities, prove a factorization idea.
- Notation matters heavily: \(A^T\) is real transpose; \(A^*\) is conjugate transpose; complex inner products require conjugation; symmetric is the real version of Hermitian.
- The professor likes "why this theorem matters" questions: Schur as always triangularizable, spectral theorem as normal matrices are unitarily diagonalizable, SVD as diagonalization using different input/output bases.
- Later lectures are more likely on the final: positive definite/semidefinite matrices, Cholesky/square roots, QR, Schur complements, matrix inversion lemma, norms, SVD, inner product spaces, projection theorem, least squares.
- Earlier lectures remain likely as supporting proof language: range/null space, rank, orthogonality, basis, inner product, projection matrices.
- Exam answers should be concise but complete: exact definition, one key identity, one proof line, and the conceptual interpretation.

## PART 2 - Master Proof Notes

### 1. Inner Products, Norms, and Orthogonality

**Definition.** An inner product on \(V\) is a map \(\langle x,y\rangle\) satisfying conjugate symmetry, linearity in one argument, conjugate-linearity in the other, and positive definiteness:
\[
\langle x,x\rangle\ge 0,\qquad \langle x,x\rangle=0 \iff x=0.
\]
It induces the norm \(\|x\|=\sqrt{\langle x,x\rangle}\). In \(\mathbb C^n\), the course commonly writes the complex Euclidean inner product using conjugate transpose, e.g. \(y^*x\) or equivalently \(x^*y\) depending on argument convention.

**Properties.**
- Orthogonality: \(x\perp y\iff \langle x,y\rangle=0\).
- Orthonormal set: pairwise orthogonal and each vector has norm 1.
- Cauchy-Schwarz: \(|\langle x,y\rangle|\le \|x\|\|y\|\).
- Inner products define geometry; norms alone define size but not angles.
- Weighted inner product: \(\langle x,y\rangle_W=y^*Wx\) with \(W\succ 0\).

**Proofs to know.**
- Cauchy-Schwarz from \(\|x-\alpha y\|^2\ge 0\).
- Norm induced by inner product satisfies positivity, homogeneity, triangle inequality.
- Orthogonality depends on the chosen inner product, so changing \(W\) changes geometry.

**Exam wording.** "Define an inner product space. How does it induce a norm? What does orthogonal mean in an abstract inner product space?"

**Answer outline.** State axioms, define \(\|x\|\), define \(x\perp y\), mention complex conjugation and Cauchy-Schwarz.

**Common mistakes.**
- Forgetting conjugation in complex spaces.
- Treating \(x^Ty\) as valid complex inner product.
- Saying orthogonality is absolute rather than inner-product dependent.

**Likelihood: High.**

### 2. Orthogonal Complements, Range, Null Space, and Rank

**Definition.**
\[
R(A)=\{Ax:x\in\mathbb F^n\},\qquad N(A)=\{x:Ax=0\}.
\]
The row space is \(R(A^*)\) in the complex setting. The left null space is \(N(A^*)\). Rank is the common dimension of row and column spaces.

**Properties.**
- \(Ax=b\) has a solution iff \(b\in R(A)\).
- If \(x_0\) solves \(Ax=b\), all solutions are \(x_0+N(A)\).
- Uniqueness iff \(N(A)=\{0\}\).
- \(N(A)=R(A^*)^\perp\).
- \(R(A)=N(A^*)^\perp\).
- Row rank equals column rank.

**Proofs to know.**
- Solvability: \(Ax\) is a linear combination of columns of \(A\).
- Uniqueness: if \(Ax_1=Ax_2=b\), then \(A(x_1-x_2)=0\).
- Null space orthogonal to row space: each component of \(Ax\) is an inner product with a row.
- Rank equality proof idea: independent row directions produce independent images; repeat for \(A^*\).

**Exam wording.** "For \(Ax=b\), explain existence and uniqueness using the four fundamental subspaces."

**Answer outline.** Existence from \(b\in R(A)\). Uniqueness from \(N(A)=0\). General solution \(x_0+N(A)\). State orthogonal complement relations.

**Common mistakes.**
- Saying full row rank gives uniqueness. It gives existence for all \(b\); uniqueness needs full column rank.
- Confusing the space where the row space lives with the output space.
- Using \(A^T\) when complex \(A^*\) is required.

**Likelihood: High.**

### 3. Projections and Orthogonal Projection Matrices

**Definition.** A projection matrix satisfies
\[
P^2=P.
\]
It is an orthogonal projection iff additionally
\[
P^*=P.
\]
The orthogonal projection of \(x\) onto subspace \(S\) is \(p\in S\) such that \(x-p\perp S\).

**Properties.**
- If \(Q\) has orthonormal columns spanning \(S\), then
\[
P=QQ^*
\]
projects orthogonally onto \(S\).
- \(P^2=QQ^*QQ^*=Q(Q^*Q)Q^*=QQ^*=P\).
- \(P^*=(QQ^*)^*=QQ^*=P\).
- \(R(P)=S\), \(N(P)=S^\perp\).
- Eigenvalues of a projection are 0 or 1.

**Proofs to know.**
- Show \(P^2=P\) for \(QQ^*\).
- Show \(P^*=P\) for orthogonal projection.
- Show \(x-Px\perp S\): for any \(Qz\in S\), \((Qz)^*(x-QQ^*x)=z^*(Q^*x-Q^*QQ^*x)=0\).

**Exam wording.** "What is the difference between a projection and an orthogonal projection? Derive the projection matrix onto a subspace with orthonormal basis."

**Answer outline.** Define idempotent; define self-adjoint idempotent for orthogonal projection; give \(P=QQ^*\); prove \(P^2=P\), \(P^*=P\), error orthogonal.

**Common mistakes.**
- Assuming \(P^2=P\) implies \(P^*=P\). It does not.
- Using \(QQ^{-1}\) instead of \(QQ^*\).
- Forgetting \(Q\) must have orthonormal columns.

**Likelihood: High.**

### 4. Projection Theorem and Least Squares

**Definition.** In an inner product space, the best approximation to \(x\) in a subspace \(S\) is the orthogonal projection \(p\in S\) satisfying \(x-p\perp S\).

**Properties.**
- Least squares solves an inconsistent \(Hx\approx y\) by projecting \(y\) onto \(R(H)\).
- Normal equations arise from orthogonality:
\[
H^*(y-H\hat x)=0,\qquad H^*H\hat x=H^*y.
\]
- If basis vectors are orthonormal, coefficients are inner products.
- If not orthonormal, the Gram matrix appears.

**Proofs to know.**
- Pythagorean proof: for \(z\in S\), \(x-z=(x-p)+(p-z)\), with orthogonal components, so \(\|x-z\|^2=\|x-p\|^2+\|p-z\|^2\).
- Derive normal equations from residual orthogonality.

**Exam wording.** "State the projection theorem and explain how least squares is a projection problem."

**Answer outline.** State \(x-p\perp S\), use \(S=R(H)\), residual \(y-H\hat x\perp R(H)\), derive \(H^*(y-H\hat x)=0\).

**Common mistakes.**
- Minimizing componentwise errors without orthogonality condition.
- Writing \(H^T\) in complex case instead of \(H^*\).
- Forgetting least squares projects \(y\), not \(x\), onto \(R(H)\).

**Likelihood: High.**

### 5. Unitary and Orthogonal Matrices

**Definition.**
\[
U^*U=UU^*=I.
\]
The real version is orthogonal:
\[
Q^TQ=QQ^T=I.
\]

**Properties.**
- \(U^{-1}=U^*\).
- Columns and rows form orthonormal bases.
- Norm preservation:
\[
\|Ux\|^2=x^*U^*Ux=x^*x.
\]
- Inner product preservation:
\[
\langle Ux,Uy\rangle=\langle x,y\rangle.
\]
- Eigenvalues satisfy \(|\lambda|=1\).
- Determinant satisfies \(|\det U|=1\).
- Models rotations/reflections and energy-preserving/lossless systems.

**Proofs to know.**
- Norm preservation from \(U^*U=I\).
- Eigenvalue magnitude: if \(Ux=\lambda x\), then \(\|x\|=\|Ux\|=|\lambda|\|x\|\), so \(|\lambda|=1\).
- Inner product preservation from \((Ux)^*(Uy)=x^*U^*Uy\).

**Exam wording.** "Define unitary. Prove it preserves Euclidean norm and characterize its eigenvalues."

**Answer outline.** State \(U^*U=I\), compute \(\|Ux\|^2\), then apply to eigenvector.

**Common mistakes.**
- Saying unitary means \(U^*=U\). That is Hermitian, not unitary.
- Forgetting real orthogonal is the real special case.
- Saying eigenvalues are real; they are on the unit circle.

**Likelihood: High.**

### 6. Hermitian and Symmetric Matrices

**Definition.**
\[
A^*=A.
\]
In the real case, this reduces to symmetric:
\[
A^T=A.
\]

**Properties.**
- \(x^*Ax\) is real for all \(x\).
- Eigenvalues are real.
- Eigenvectors corresponding to distinct eigenvalues are orthogonal.
- Hermitian matrices define real-valued quadratic forms.
- Hermitian matrices are normal.

**Proofs to know.**
- \(x^*Ax\) real:
\[
(x^*Ax)^*=x^*A^*x=x^*Ax.
\]
- Eigenvalues real: if \(Ax=\lambda x\), then
\[
\lambda=\frac{x^*Ax}{x^*x}\in\mathbb R.
\]
- Orthogonal eigenspaces: if \(Ax=\lambda x\), \(Ay=\mu y\), then
\[
\lambda x^*y=(Ax)^*y=x^*Ay=\mu x^*y.
\]
If \(\lambda\ne\mu\), \(x^*y=0\).

**Exam wording.** "Show that a Hermitian matrix has real eigenvalues and orthogonal eigenspaces."

**Answer outline.** Use Rayleigh quotient for real eigenvalues; compare \(x^*Ay\) two ways for orthogonality.

**Common mistakes.**
- Using \(x^TAx\) for complex vectors.
- Saying Hermitian means entries are real. Hermitian matrices may be complex with conjugate symmetry.
- Confusing symmetric with Hermitian in complex spaces.

**Likelihood: High.**

### 7. Positive Definite, Positive Semidefinite, Negative Definite, Indefinite

**Definition.** For Hermitian \(A\):
- \(A\succ0\): all eigenvalues \(>0\), equivalently \(x^*Ax>0\) for all \(x\ne0\).
- \(A\succeq0\): all eigenvalues \(\ge0\), equivalently \(x^*Ax\ge0\) for all \(x\).
- \(A\prec0\): all eigenvalues \(<0\).
- \(A\preceq0\): all eigenvalues \(\le0\).
- Indefinite: at least one positive and at least one negative eigenvalue.

**Properties.**
- PD implies invertible; PSD may be singular.
- PD matrices define strictly convex quadratic forms.
- PSD matrices define nonnegative quadratic forms but may be flat in null directions.
- Principal submatrices of PD matrices are PD.
- Positive weighted sums of PD matrices are PD.
- For \(A\succeq0\), there exists a square root \(S\) with \(A=SS^*\).

**Proofs to know.**
- Eigenvalue form implies quadratic form: write \(A=U\Lambda U^*\), let \(y=U^*x\), then
\[
x^*Ax=y^*\Lambda y=\sum_i\lambda_i |y_i|^2.
\]
- Quadratic form implies eigenvalue signs: plug eigenvectors into \(x^*Ax\).
- PD implies invertible: no zero eigenvalues.

**Exam wording.** "Define PSD and PD. Explain the difference and prove the equivalence with \(x^*Ax\)."

**Answer outline.** State Hermitian assumption, eigenvalue sign definition, quadratic form equivalence using unitary diagonalization/eigenvectors.

**Common mistakes.**
- Forgetting PSD allows zero eigenvalues.
- Applying PD/PSD terminology to non-Hermitian matrices without qualification.
- Saying \(x^*Ax>0\) for all \(x\), forgetting \(x=0\).

**Likelihood: High.**

### 8. Quadratic Forms and Geometry

**Definition.** A Hermitian matrix \(A\) defines the real-valued quadratic form
\[
q(x)=x^*Ax.
\]

**Properties.**
- Eigenvectors give principal directions.
- Eigenvalues give curvature/sign along those directions.
- PD: bowl-up; ND: bowl-down; indefinite: saddle.
- Level sets of PD/ND quadratic forms are ellipses/ellipsoids.
- Larger eigenvalue means stronger curvature and shorter principal semi-axis for fixed level.

**Proofs to know.**
- Diagonalize \(A=U\Lambda U^*\), set \(y=U^*x\), then \(q(x)=\sum_i\lambda_i |y_i|^2\).
- Interpret signs of eigenvalues through slices along eigenvectors.

**Exam wording.** "How does the eigenvalue structure of a Hermitian matrix determine the shape of \(x^*Ax\)?"

**Answer outline.** Use orthonormal eigenbasis coordinates; signs determine convex/concave/saddle; magnitudes determine curvature.

**Common mistakes.**
- Treating cross terms as arbitrary after diagonalization; in eigenbasis they disappear.
- Confusing ellipsoid axes with standard coordinate axes when \(A\) is not diagonal.

**Likelihood: High.**

### 9. Normal Matrices and the Spectral Theorem

**Definition.**
\[
A^*A=AA^*.
\]

**Properties.**
- Hermitian, unitary, and skew-Hermitian matrices are normal.
- Normal matrices are exactly the unitarily diagonalizable matrices:
\[
A=U\Lambda U^*.
\]
- Eigenspaces for distinct eigenvalues are orthogonal.
- For normal matrices, Frobenius energy equals eigenvalue energy:
\[
\operatorname{tr}(A^*A)=\sum_i|\lambda_i|^2.
\]

**Proofs to know.**
- Normal plus Schur implies diagonal: Schur gives \(A=UTU^*\), with \(T\) upper triangular. Normality transfers to \(T\). A normal upper triangular matrix must be diagonal.
- Spectral theorem for Hermitian is a special case: since Hermitian is normal and eigenvalues are real, \(A=U\Lambda U^*\) with real \(\Lambda\).

**Exam wording.** "Why are normal matrices precisely the matrices diagonalizable by a unitary matrix?"

**Answer outline.** One direction: if \(A=U\Lambda U^*\), then \(A^*A=U\Lambda^*\Lambda U^*=U\Lambda\Lambda^*U^*=AA^*\). Converse: Schur triangularization plus normal triangular matrix is diagonal.

**Common mistakes.**
- Saying all diagonalizable matrices are normal. False; normal requires orthonormal eigenbasis.
- Confusing Hermitian with normal; Hermitian is a subset.
- Forgetting eigenvalues of normal matrices can be arbitrary complex values.

**Likelihood: High.**

### 10. Diagonalization vs Unitary Diagonalization

**Definition.**
- Diagonalizable:
\[
A=T\Lambda T^{-1}
\]
for some invertible \(T\).
- Unitarily diagonalizable:
\[
A=U\Lambda U^*
\]
for unitary \(U\).

**Properties.**
- Diagonalizable iff there is a basis of eigenvectors.
- Unitarily diagonalizable iff there is an orthonormal basis of eigenvectors.
- Normal iff unitarily diagonalizable.
- Unitary diagonalization preserves geometry and gives stable projections.

**Proofs to know.**
- If \(AT=T\Lambda\), then \(T^{-1}AT=\Lambda\).
- If \(A=U\Lambda U^*\), then columns of \(U\) are orthonormal eigenvectors.

**Exam wording.** "Explain why unitary diagonalization is stronger than diagonalization."

**Answer outline.** General \(T\) only gives a basis; \(U\) gives orthonormal basis and \(U^{-1}=U^*\). Normal matrices are exactly the unitary case.

**Common mistakes.**
- Replacing \(T^{-1}\) with \(T^*\) for arbitrary diagonalizable matrices.
- Saying every matrix is diagonalizable.
- Saying Schur factorization is diagonalization.

**Likelihood: High.**

### 11. Schur Triangularization

**Definition/Theorem.** Every square complex matrix \(A\) has a Schur factorization:
\[
A=UTU^*
\]
where \(U\) is unitary and \(T\) is upper triangular. The diagonal entries of \(T\) are eigenvalues of \(A\).

**Properties.**
- Always exists over \(\mathbb C\).
- Weaker than diagonalization, stronger than arbitrary similarity because the basis is orthonormal.
- Used to prove spectral theorem for normal matrices.

**Proofs to know.**
- Pick an eigenvector \(u_1\) with \(\|u_1\|=1\).
- Extend \(u_1\) to an orthonormal basis using Gram-Schmidt.
- In that basis, the first column below the diagonal is zero, giving block upper triangular form.
- Apply induction to the remaining block.

**Exam wording.** "State Schur's theorem and explain why it is a consolation prize for non-diagonalizable matrices."

**Answer outline.** State theorem, say not every matrix is diagonalizable but every complex square matrix can be unitarily triangularized, then give eigenvector-plus-induction proof idea.

**Common mistakes.**
- Calling \(T\) diagonal. It is only triangular in general.
- Forgetting complex field is needed for guaranteed eigenvalue.
- Confusing Schur with SVD.

**Likelihood: High.**

### 12. QR Factorization and Gram-Schmidt

**Definition.** QR factorization writes
\[
A=QR,
\]
where \(Q\) has orthonormal columns and \(R\) is upper triangular. Full QR extends \(Q\) to a unitary matrix.

**Properties.**
- Gram-Schmidt orthogonalizes columns.
- Modified Gram-Schmidt eliminates components along each new \(q_k\) immediately.
- Upper triangular \(R\) appears because each new vector is built from current and previous columns.
- QR is a unitary/orthogonal-triangular factorization, useful for solving systems and least squares.

**Proofs to know.**
- Show \(A=QR\) from expressing each \(a_j\) as a combination of \(q_1,\ldots,q_j\).
- Explain why \(R\) is upper triangular.
- Explain reduced vs full QR.

**Exam wording.** "Why does Gram-Schmidt produce an upper triangular factor?"

**Answer outline.** Each \(a_j\) lies in span of first \(j\) orthonormal vectors, so coefficients below row \(j\) are zero.

**Common mistakes.**
- Saying \(Q\) is square/unitary in reduced QR. It has orthonormal columns; full QR makes it square unitary.
- Confusing orthogonalization with normalization only.

**Likelihood: Medium-High.**

### 13. Cholesky, Matrix Square Roots, and Star Congruence

**Definitions.**
- A square root of \(A\) is \(S\) such that
\[
A=SS^*.
\]
- Positive definite square root:
\[
A=U\Lambda U^*,\qquad A^{1/2}=U\Lambda^{1/2}U^*.
\]
- Cholesky factorization:
\[
A=LL^*
\]
where \(L\) is lower triangular with positive diagonal, for \(A\succ0\).
- Star congruence:
\[
A=SBS^*
\]
with invertible \(S\).

**Properties.**
- Star-congruent Hermitian matrices have the same inertia.
- \(A\succ0\) iff it is star-congruent to \(I\).
- Positive definite matrices have infinitely many square roots, including positive definite and Cholesky square roots.
- Cholesky proof uses block Gaussian elimination and induction.

**Proofs to know.**
- Positive definite square root from spectral theorem.
- Cholesky induction: partition \(A\), eliminate first column/row by congruence, show Schur complement remains PD, recurse.
- Star congruence preserves inertia: Sylvester law of inertia.

**Exam wording.** "Explain why a positive definite matrix has a square root and state Cholesky factorization."

**Answer outline.** Use spectral theorem for \(A^{1/2}\); state \(LL^*\) lower triangular form and mention PD Schur complement induction.

**Common mistakes.**
- Thinking square root is unique. Positive definite square root is unique, but square roots in general are not.
- Writing \(LL^T\) for complex matrices; use \(LL^*\).
- Ignoring positive diagonal condition in Cholesky.

**Likelihood: Medium-High.**

### 14. Schur Complement, Block LDU/UDL, and Matrix Inversion Lemma

**Definition.** For block matrix
\[
A=\begin{bmatrix}A_{11}&A_{12}\\ A_{21}&A_{22}\end{bmatrix},
\]
with \(A_{11}\) invertible, the Schur complement of \(A_{11}\) is
\[
S_{22}=A_{22}-A_{21}A_{11}^{-1}A_{12}.
\]
With \(A_{22}\) invertible, the Schur complement of \(A_{22}\) is
\[
S_{11}=A_{11}-A_{12}A_{22}^{-1}A_{21}.
\]

**Properties.**
- Block LDU factorization results from block Gaussian elimination.
- Determinant:
\[
\det A=\det(A_{11})\det(S_{22})=\det(A_{22})\det(S_{11}).
\]
- Inverse formulas follow by inverting block triangular and block diagonal factors.
- Matrix inversion lemma/Woodbury comes from equating block inverse expressions.
- Important in recursive least squares and updating inverse autocorrelation matrices.

**Proofs to know.**
- Derive \(S_{22}\) by eliminating \(A_{21}\) using block lower triangular multiplication.
- Explain determinant product from block triangular/diagonal factors.
- State Woodbury idea, not necessarily memorize full algebra unless professor emphasized it.

**Exam wording.** "What is the Schur complement and how does it arise from block Gaussian elimination?"

**Answer outline.** Show block partition, eliminate lower-left block, identify \(A_{22}-A_{21}A_{11}^{-1}A_{12}\), mention determinant/inverse consequences.

**Common mistakes.**
- Reversing multiplication order. Matrix multiplication is not commutative.
- Confusing Schur complement with Schur factorization.
- Forgetting invertibility condition on the pivot block.

**Likelihood: Medium-High.**

### 15. Matrix Norms, Induced Norms, and Norm Geometry

**Definitions.**
- Vector \(\ell_p\)-norm:
\[
\|x\|_p=\left(\sum_i |x_i|^p\right)^{1/p},\qquad \|x\|_\infty=\max_i |x_i|.
\]
- Matrix Frobenius norm:
\[
\|A\|_F=\sqrt{\operatorname{tr}(A^*A)}.
\]
- Induced norm:
\[
\|A\|_{q,p}=\max_{x\ne0}\frac{\|Ax\|_q}{\|x\|_p}.
\]
Usually \(\|A\|_{2,2}\) is the operator norm.

**Properties.**
- \(\|A\|_{1,1}\): maximum column one-norm.
- \(\|A\|_{\infty,\infty}\): maximum row one-norm.
- \(\|A\|_{2,2}=\sigma_1\), largest singular value.
- Frobenius norm treats matrix as a vector.
- Induced norm treats matrix as a linear mapping and measures maximum gain.
- \(p\)-norm balls reveal sparsity behavior: \(\ell_1\) has corners and encourages sparse solutions.

**Proofs to know.**
- Induced norm can be restricted to \(\|x\|_p=1\) by homogeneity.
- Show unitary invariance for Frobenius/operator norm using \(U^*U=I\).
- Use Cauchy-Schwarz/duality ideas to bound inner products.

**Exam wording.** "Compare Frobenius norm and induced norm. What does the induced 2-norm measure?"

**Answer outline.** Frobenius flattens entries; induced norm is max output/input norm gain; induced 2-norm equals largest singular value.

**Common mistakes.**
- Treating all matrix norms as entrywise norms.
- Confusing \(\|A\|_F\) with \(\|A\|_{2,2}\).
- Forgetting induced norm depends on chosen input/output vector norms.

**Likelihood: Medium-High.**

### 16. Singular Value Decomposition

**Definition/Theorem.** Every \(m\times n\) complex matrix has an SVD
\[
A=U\Sigma V^*
\]
where \(U,V\) are unitary and \(\Sigma\) is rectangular diagonal with nonnegative singular values
\[
\sigma_1\ge\sigma_2\ge\cdots\ge\sigma_r>0.
\]
Reduced SVD:
\[
A=\sum_{k=1}^r \sigma_k u_kv_k^*.
\]

**Properties.**
- Singular values are square roots of eigenvalues of \(A^*A\) and \(AA^*\).
- \(v_k\): right singular vectors; \(u_k\): left singular vectors.
- \(Av_k=\sigma_k u_k\).
- \(R(A)\) is spanned by left singular vectors with nonzero singular values.
- \(N(A)\) is spanned by right singular vectors with zero singular values.
- \(\|A\|_{2,2}=\sigma_1\), \(\|A\|_F=\sqrt{\sum\sigma_i^2}\).
- SVD always exists, even for rectangular matrices.

**Proofs to know.**
- Geometric construction: unit ball maps to ellipsoid; principal semi-axis lengths are singular values.
- Start with direction \(v_1\) achieving maximum gain; define \(\sigma_1=\|Av_1\|\), \(u_1=Av_1/\sigma_1\); extend bases and recurse.
- Relate \(A^*A=V\Sigma^2V^*\).

**Exam wording.** "Explain the meaning of SVD as diagonalization with different input and output bases."

**Answer outline.** Unlike eigenvalue decomposition, SVD uses \(V\) basis in input and \(U\) basis in output; maps \(v_k\) to \(\sigma_k u_k\); works for rectangular/all matrices.

**Common mistakes.**
- Saying singular values are eigenvalues. They are nonnegative square roots of eigenvalues of \(A^*A\).
- Confusing left and right singular vectors.
- Saying SVD needs square or diagonalizable matrix.

**Likelihood: High for final.**

### 17. SVD Applications and Schatten Norms

**Definitions.**
- Nuclear norm:
\[
\|A\|_*=\sum_i\sigma_i.
\]
- Schatten \(p\)-norm:
\[
\|A\|_{(p)}=\|\sigma(A)\|_p.
\]
- Schatten 2-norm is Frobenius; Schatten infinity-norm is operator norm.

**Properties.**
- Nuclear norm is convex and promotes low rank.
- Rank equals number of nonzero singular values.
- Low-rank approximation keeps largest singular values.
- Matrix completion uses low-rank structure; Netflix challenge is the motivating example.
- Closest unitary matrix problem connects SVD/polar decomposition.

**Proofs to know.**
- Explain why nuclear norm is an \(\ell_1\)-norm on singular values and therefore sparsifies singular values.
- Frobenius norm from singular values:
\[
\|A\|_F^2=\operatorname{tr}(A^*A)=\sum_i\sigma_i^2.
\]

**Exam wording.** "Why is the nuclear norm used as a convex substitute for rank?"

**Answer outline.** Rank counts nonzero singular values; nuclear norm sums singular values, analogous to \(\ell_1\) relaxation of sparsity.

**Common mistakes.**
- Calling nuclear norm the same as Frobenius norm.
- Forgetting convexity is the reason it replaces rank minimization.

**Likelihood: Medium.**

### 18. Abstract Inner Product Spaces and Gram Matrices

**Definition.** A vector space equipped with an inner product becomes an inner product space. In finite dimensions it behaves like Euclidean geometry once the inner product is chosen.

**Examples.**
- \(\mathbb C^n\): \(y^*x\).
- Functions: \(\int f(t)\overline{g(t)}\,dt\).
- Matrices: \(\langle A,B\rangle=\operatorname{tr}(B^*A)\).
- Random variables: \(\langle X,Y\rangle=E[X\overline{Y}]\), correlation as inner product.

**Properties.**
- Orthogonality, projections, Gram-Schmidt generalize.
- Gram matrix contains pairwise inner products.
- If basis is orthonormal, Gram matrix is identity.
- SVD rank-one matrices \(u_kv_k^*\) are orthonormal under Frobenius inner product.

**Proofs to know.**
- Frobenius inner product equals vectorized complex inner product.
- Orthogonality of SVD rank-one pieces:
\[
\langle u_iv_i^*,u_jv_j^*\rangle=\delta_{ij}.
\]
- Projection coefficients require solving Gram matrix unless basis is orthonormal.

**Exam wording.** "Give examples of inner product spaces beyond \(\mathbb C^n\), and explain why orthonormal bases are useful."

**Answer outline.** List examples, define induced norm, explain projections and Gram matrix simplification.

**Common mistakes.**
- Treating function/matrix/random-variable inner products as unrelated; they are same abstract structure.
- Forgetting conjugation in function/matrix/random-variable examples.

**Likelihood: High for later final.**

## PART 3 - Cheat Sheet

### 1. Definitions to Memorize Exactly

| Object | Definition |
|---|---|
| Inner product | Conjugate-symmetric, linear/sesquilinear, positive definite map \(\langle x,y\rangle\). |
| Orthogonal | \(x\perp y\iff \langle x,y\rangle=0\). |
| Orthonormal | Orthogonal and unit norm. |
| Range | \(R(A)=\{Ax:x\in\mathbb F^n\}\). |
| Null space | \(N(A)=\{x:Ax=0\}\). |
| Projection | \(P^2=P\). |
| Orthogonal projection | \(P^2=P\) and \(P^*=P\). |
| Unitary | \(U^*U=UU^*=I\). |
| Orthogonal matrix | Real unitary: \(Q^TQ=QQ^T=I\). |
| Hermitian | \(A^*=A\). |
| Symmetric | Real Hermitian: \(A^T=A\). |
| Normal | \(A^*A=AA^*\). |
| PSD | Hermitian \(A\), \(x^*Ax\ge0\) for all \(x\), equivalently \(\lambda_i\ge0\). |
| PD | Hermitian \(A\), \(x^*Ax>0\) for \(x\ne0\), equivalently \(\lambda_i>0\). |
| Schur factorization | \(A=UTU^*\), \(T\) upper triangular. |
| SVD | \(A=U\Sigma V^*\), \(\Sigma\ge0\) diagonal rectangular. |
| Cholesky | \(A=LL^*\), \(L\) lower triangular positive diagonal, for \(A\succ0\). |
| Schur complement | \(A_{22}-A_{21}A_{11}^{-1}A_{12}\). |
| Induced norm | \(\|A\|_{q,p}=\max_{x\ne0}\|Ax\|_q/\|x\|_p\). |
| Nuclear norm | \(\|A\|_*=\sum_i\sigma_i\). |

### 2. Theorems to State Exactly

- Cauchy-Schwarz: \(|\langle x,y\rangle|\le\|x\|\|y\|\).
- Projection theorem: the closest point in a subspace is characterized by orthogonal residual.
- Solvability: \(Ax=b\) solvable iff \(b\in R(A)\).
- General solution: all solutions are \(x_0+N(A)\).
- Diagonalization: \(A\) diagonalizable iff it has a basis of eigenvectors.
- Schur theorem: every complex square matrix is unitarily triangularizable.
- Spectral theorem: \(A\) normal iff \(A=U\Lambda U^*\).
- Hermitian spectral theorem: Hermitian \(A=U\Lambda U^*\) with real \(\Lambda\).
- SVD theorem: every rectangular matrix admits \(A=U\Sigma V^*\).
- Sylvester law of inertia: star-congruent Hermitian matrices have the same inertia.
- Cholesky theorem: \(A\succ0\) iff \(A=LL^*\) with \(L\) lower triangular positive diagonal.

### 3. Proof Templates

**To prove a matrix is Hermitian.**
1. Compute \(A^*\).
2. Use \((BC)^*=C^*B^*\), \((A+B)^*=A^*+B^*\).
3. Show \(A^*=A\).

**To prove \(P\) is a projection.**
1. Compute \(P^2\).
2. Reduce using identities such as \(Q^*Q=I\).
3. Conclude \(P^2=P\).

**To prove an orthogonal projection.**
1. Prove \(P^2=P\).
2. Prove \(P^*=P\).
3. Or prove residual \(x-Px\perp R(P)\).

**To prove PSD from eigenvalues.**
1. Use \(A=U\Lambda U^*\).
2. Let \(y=U^*x\).
3. \(x^*Ax=\sum_i\lambda_i|y_i|^2\ge0\).

**To prove Hermitian eigenvalues are real.**
1. \(Ax=\lambda x\), \(x\ne0\).
2. \(\lambda=\frac{x^*Ax}{x^*x}\).
3. Numerator real because \(A=A^*\), denominator positive.

**To prove distinct Hermitian eigenvectors are orthogonal.**
1. \(Ax=\lambda x\), \(Ay=\mu y\).
2. \(x^*Ay=\mu x^*y\).
3. Also \((Ax)^*y=\lambda x^*y\).
4. \((\lambda-\mu)x^*y=0\), so \(x^*y=0\).

**To prove unitary preserves norms.**
1. \(\|Ux\|^2=(Ux)^*(Ux)\).
2. \(=x^*U^*Ux=x^*x\).

**To explain Schur triangularization.**
1. Pick one eigenvector.
2. Extend to orthonormal basis.
3. Matrix becomes block upper triangular.
4. Induct on lower block.

**To distinguish Schur from diagonalization.**
1. Schur always gives upper triangular \(T\).
2. Diagonalization requires enough eigenvectors.
3. Normality forces Schur \(T\) to be diagonal.

**To prove normal implies unitarily diagonalizable.**
1. Schur: \(A=UTU^*\).
2. Normality transfers to \(T\).
3. Upper triangular normal \(T\) must be diagonal.
4. Therefore \(A=U\Lambda U^*\).

**To derive least squares normal equations.**
1. Minimize \(\|y-Hx\|\).
2. Optimal residual \(r=y-H\hat x\) is orthogonal to \(R(H)\).
3. \(H^*r=0\).
4. \(H^*H\hat x=H^*y\).

### 4. Matrix-Structure Consequences

| If \(A\) is... | Then... |
|---|---|
| Unitary | \(A^{-1}=A^*\), preserves norm/inner product, eigenvalues on unit circle. |
| Hermitian | eigenvalues real, \(x^*Ax\in\mathbb R\), orthogonal eigenspaces. |
| Skew-Hermitian | eigenvalues purely imaginary or zero. |
| Normal | unitarily diagonalizable, orthonormal eigenbasis. |
| PD | Hermitian, eigenvalues positive, invertible, \(x^*Ax>0\) for \(x\ne0\). |
| PSD | Hermitian, eigenvalues nonnegative, may be singular. |
| Projection | \(P^2=P\), eigenvalues 0 or 1. |
| Orthogonal projection | \(P^2=P\), \(P^*=P\), range perpendicular to null space. |
| Lower triangular | eigenvalues on diagonal; easy forward substitution. |
| Toeplitz | constant diagonals; convolution structure. |
| Circulant | diagonalized by Fourier basis. |

### 5. Notation Traps

- \(A^T\): transpose only. Use mainly real case.
- \(A^*\): conjugate transpose. Required for complex inner products, unitary, Hermitian, PSD.
- \(U^{-1}=U^*\) only for unitary \(U\), not arbitrary invertible \(U\).
- \(T^{-1}AT\) is general basis change; \(U^*AU\) is unitary basis change.
- \(x^*Ax\), not \(x^TAx\), for complex quadratic forms.
- PSD means \(\ge0\); PD means \(>0\) for every nonzero vector.
- Projection means \(P^2=P\); orthogonal projection means also \(P^*=P\).

### 6. "If \(A\) is ___, then ___" Table

| Premise | Required conclusion |
|---|---|
| \(A^*=A\) | \(x^*Ax\) real; eigenvalues real. |
| \(A^*=-A\) | eigenvalues purely imaginary. |
| \(A^*A=AA^*\) | \(A\) is unitarily diagonalizable. |
| \(U^*U=I\) | columns orthonormal; \(U\) preserves norms. |
| \(A\succeq0\) | \(x^*Ax\ge0\); eigenvalues nonnegative. |
| \(A\succ0\) | \(A^{-1}\) exists; Cholesky exists. |
| \(P^2=P\) | eigenvalues 0 or 1. |
| \(P^2=P, P^*=P\) | \(P\) is an orthogonal projection. |
| \(A=U\Sigma V^*\) | singular vectors give orthonormal bases for fundamental spaces. |
| \(A=UTU^*\) | Schur form; diagonal of \(T\) contains eigenvalues. |

### 7. "Do Not Confuse" Table

| This | With this | Difference |
|---|---|---|
| Hermitian | Unitary | \(A^*=A\) vs \(A^*=A^{-1}\). |
| Symmetric | Hermitian | Symmetric is real; Hermitian uses conjugate transpose. |
| PSD | PD | PSD allows zero eigenvalues; PD does not. |
| Projection | Orthogonal projection | Idempotent vs idempotent and Hermitian. |
| Diagonalizable | Unitarily diagonalizable | arbitrary basis vs orthonormal basis. |
| Schur factorization | Eigenvalue diagonalization | triangular always vs diagonal only sometimes. |
| Schur complement | Schur theorem | block elimination term vs triangularization theorem. |
| SVD | Eigenvalue decomposition | all rectangular matrices, two bases vs square/eigenbasis. |
| Frobenius norm | Operator norm | entry energy vs maximum gain. |
| Range space | Row space | output subspace vs input subspace. |
| Null space | Left null space | \(N(A)\) vs \(N(A^*)\). |

### 8. Likely Exam Questions and Answer Skeletons

1. **Define Hermitian and prove eigenvalues are real.**  
Skeleton: \(A^*=A\). If \(Ax=\lambda x\), then \(x^*Ax=\lambda x^*x\). Since \(x^*Ax\in\mathbb R\) and \(x^*x>0\), \(\lambda\in\mathbb R\).

2. **Prove eigenspaces of Hermitian matrices for distinct eigenvalues are orthogonal.**  
Skeleton: compare \(x^*Ay=\mu x^*y\) and \((Ax)^*y=\lambda x^*y\).

3. **State Schur theorem and explain proof idea.**  
Skeleton: \(A=UTU^*\); pick eigenvector, extend to orthonormal basis, induction.

4. **Show normal iff unitarily diagonalizable.**  
Skeleton: one direction direct from \(U\Lambda U^*\); converse Schur plus triangular normal is diagonal.

5. **Define PSD/PD and prove quadratic form equivalence.**  
Skeleton: spectral theorem, \(y=U^*x\), sum \(\lambda_i|y_i|^2\).

6. **Projection matrix onto subspace with orthonormal basis.**  
Skeleton: \(P=QQ^*\), prove \(P^2=P\), \(P^*=P\), residual orthogonal.

7. **Compare diagonalization, Schur, and SVD.**  
Skeleton: diagonalization needs eigenbasis; Schur always triangularizes square complex; SVD always exists for rectangular and uses input/output bases.

8. **Explain least squares using projection theorem.**  
Skeleton: project \(y\) onto \(R(H)\), residual orthogonal, \(H^*(y-H\hat x)=0\).

9. **Derive or interpret Schur complement.**  
Skeleton: block elimination; \(S=A_{22}-A_{21}A_{11}^{-1}A_{12}\); determinant/inverse consequences.

10. **Explain SVD fundamental-space interpretation.**  
Skeleton: right singular vectors span input row/null directions; left singular vectors span range/left null directions; \(Av_i=\sigma_i u_i\).

### 9. Three-Question Mock Final Exam

**Question 1.** Let \(A\in\mathbb C^{n\times n}\).  
(a) Define Hermitian, unitary, and normal matrices.  
(b) Prove that Hermitian matrices have real eigenvalues.  
(c) State Schur's theorem and use it to explain why normal matrices are unitarily diagonalizable.  
(d) Give one example of a normal matrix that is not Hermitian.

**Expected style.** Definitions must use \(A^*\). Proof must be symbolic and short. For (c), mention upper triangular normal implies diagonal. For (d), a non-real diagonal unitary matrix works.

**Question 2.** Let \(S\subseteq\mathbb C^n\) be a subspace with orthonormal basis columns collected in \(Q\).  
(a) Derive the orthogonal projection matrix onto \(S\).  
(b) Prove it is a projection and an orthogonal projection.  
(c) State the projection theorem and derive the least-squares normal equations for \(Hx\approx y\).

**Expected style.** Must show \(P=QQ^*\), \(P^2=P\), \(P^*=P\), residual orthogonality, \(H^*(y-H\hat x)=0\).

**Question 3.**  
(a) Define positive definite and positive semidefinite Hermitian matrices using both eigenvalues and quadratic forms.  
(b) Prove the equivalence between the eigenvalue and quadratic-form definitions.  
(c) State the SVD and explain how it differs from eigenvalue diagonalization.  
(d) Explain why the nuclear norm is a convex surrogate for rank.

**Expected style.** Use \(A=U\Lambda U^*\), \(y=U^*x\), distinguish zero eigenvalues, state \(A=U\Sigma V^*\), and connect rank to nonzero singular values.

### 10. Emergency Last-Night Study List

1. Memorize exact definitions: unitary, Hermitian, normal, PSD, PD, projection, orthogonal projection, SVD, Schur.
2. Practice five proof templates: unitary norm preservation, Hermitian real eigenvalues, Hermitian orthogonal eigenspaces, \(P=QQ^*\), PSD quadratic form.
3. Be able to state Schur theorem and spectral theorem without hesitation.
4. Be able to explain diagonalization vs Schur vs SVD in two sentences.
5. Review range/null space existence and uniqueness for \(Ax=b\).
6. Review projection theorem and least-squares normal equations.
7. Know \(A^T\) vs \(A^*\) traps cold.
8. Know PSD vs PD and projection vs orthogonal projection cold.
9. For SVD, memorize \(Av_i=\sigma_i u_i\), \(A^*u_i=\sigma_i v_i\), \(\|A\|_{2,2}=\sigma_1\), \(\|A\|_F^2=\sum\sigma_i^2\).
10. If time is short, prioritize Hermitian/PSD/normal/Schur/SVD/projection theorem over numerical examples.

## PART 5 - Danger Topics

### \(A^*\) vs \(A^T\)

- Use \(A^T\) only for real transpose.
- Use \(A^*\) for complex conjugate transpose.
- Complex inner products, unitary matrices, Hermitian matrices, PSD definitions, least squares normal equations, and SVD all require \(A^*\).
- Wrong exam answer: \(U^TU=I\) for complex unitary. Correct: \(U^*U=I\).

### Hermitian vs Symmetric

- Symmetric: \(A^T=A\), real setting.
- Hermitian: \(A^*=A\), complex setting.
- Hermitian entries satisfy \(a_{ij}=\overline{a_{ji}}\); diagonal entries are real.
- Do not say Hermitian matrices must have all real entries.

### PSD vs PD

- PSD: \(x^*Ax\ge0\) for all \(x\); zero eigenvalues allowed; may be singular.
- PD: \(x^*Ax>0\) for all \(x\ne0\); all eigenvalues positive; invertible.
- Always include "Hermitian" in the definition unless the question states it.

### Projection vs Orthogonal Projection

- Projection: \(P^2=P\).
- Orthogonal projection: \(P^2=P\) and \(P^*=P\).
- Oblique projections are idempotent but not self-adjoint.
- For an orthonormal basis \(Q\), \(P=QQ^*\), not \(Q^*Q\).

### Diagonalizable vs Unitarily Diagonalizable

- Diagonalizable: \(A=T\Lambda T^{-1}\), arbitrary invertible \(T\).
- Unitarily diagonalizable: \(A=U\Lambda U^*\), orthonormal eigenbasis.
- Normal matrices are exactly unitarily diagonalizable.
- A matrix can be diagonalizable but not normal.

### Schur Triangularization vs Diagonalization

- Schur: always \(A=UTU^*\), \(T\) upper triangular.
- Diagonalization: only if enough eigenvectors exist.
- Normality is the condition that turns Schur triangular \(T\) into diagonal \(\Lambda\).

### Unitary vs Hermitian

- Unitary: \(A^*=A^{-1}\), preserves norm, eigenvalues on unit circle.
- Hermitian: \(A^*=A\), real eigenvalues, real quadratic form.
- A matrix can be both, e.g. eigenvalues only \(\pm1\) with orthonormal eigenbasis.

### Normal vs Hermitian

- Hermitian implies normal.
- Normal does not imply Hermitian.
- Normal eigenvalues may be complex; Hermitian eigenvalues are real.
- Normal is the right condition for unitary diagonalization.

### Real Inner Product vs Complex Inner Product

- Real: \(x^Ty\), symmetric.
- Complex: use conjugation; conjugate symmetry replaces symmetry.
- Scaling one argument by \(\alpha\) may pull out \(\bar\alpha\) depending on convention.
- If the answer ignores conjugation, it is incomplete.

### Range/Nullspace Interpretation

- \(R(A)\): what outputs are reachable.
- \(N(A)\): input directions invisible to \(A\).
- \(N(A)=R(A^*)^\perp\).
- Existence: \(b\in R(A)\).
- Uniqueness: \(N(A)=0\).
- Least squares: project \(b\) or \(y\) onto \(R(A)\) or \(R(H)\).

