# Lecture 08 Exam Report

Scope: only `corrected\lecture8_corrected.md`, `study_outputs\lecture_notes\lecture_08_notes.md`, and `study_outputs\audits\lecture_08_audit.md` were used. This report extracts exam-relevant signals only: explicit exam markers, repeated emphasis, warnings, proof chains, theorem-like statements, notation traps, and conceptual questions.

## High Probability Topics

### 1. Basis-change coordinates and the basis matrix

Probability: High.

Why: explicitly marked as an exam note, and it is the entry point for the entire diagonalization storyline. The instructor specifically said to remember the matrix multiplication interpretation when basis vectors are placed as columns.

Likely exam task:

- Given basis vectors \(t_1,\dots,t_n\), form \(T=[t_1\ \cdots\ t_n]\).
- Convert between standard and new coordinates:
  \[
  x=T\tilde{x}, \qquad \tilde{x}=T^{-1}x.
  \]
- Explain why \(T\) is invertible: its columns are a basis, so they are linearly independent.

Notation trap:

- \(x\) and \(\tilde{x}\) are coordinates for the same vector in different bases, not two different vectors.
- The new basis does not have to be orthogonal; it only needs to span and be linearly independent.
- This part is only representation change; no linear transformation has been applied yet.

### 2. Matrix representation of a linear map under basis change

Probability: High.

Why: repeated several times and directly feeds the diagonalization question. The instructor emphasized that the mapping itself does not change, only its matrix representation changes.

Likely exam task:

- Starting from \(y=Ax\), substitute
  \[
  x=T\tilde{x}, \qquad y=T\tilde{y}.
  \]
- Derive
  \[
  T\tilde{y}=AT\tilde{x},
  \qquad
  \tilde{y}=T^{-1}AT\tilde{x}.
  \]
- Identify the new representation:
  \[
  \tilde{A}=T^{-1}AT.
  \]

Conceptual question:

- What changes under basis change? The coordinates and representing matrix.
- What stays fixed? The actual linear transformation and the points/vectors being mapped.

Notation trap:

- The same basis \(T\) is being used for input and output here. That restriction is why this discussion applies naturally to square matrices.

### 3. Diagonalization by basis change

Probability: High.

Why: explicitly marked as a likely exam topic and described as the main storyline. The instructor said the diagonalization idea will return repeatedly.

Likely exam task:

- State the diagonalization question:
  \[
  \text{Can we find invertible }T\text{ such that }T^{-1}AT\text{ is diagonal?}
  \]
- Explain why this is a restricted diagonalization problem: the same basis is used for both input and output.
- Connect this question to eigenvectors.

Conceptual question:

- Why do we want diagonal form? Diagonal matrices are simple, so linear systems, differential systems, and repeated linear actions become easier.

Notation trap:

- This is not the same as allowing different bases for the domain and codomain. Different input/output bases lead toward SVD.

### 4. Eigenvectors: geometric definition and algebraic condition

Probability: High.

Why: explicitly tied to the likely exam topic list. The lecture spends substantial time turning the geometric idea into the determinant equation.

Likely exam task:

- Define an eigenvector/eigenvalue pair:
  \[
  Ax=\lambda x, \qquad x\ne 0.
  \]
- Explain the geometry: \(Ax\) points in the same or opposite direction as \(x\), so the matrix acts like scalar multiplication along that direction.
- Derive
  \[
  Ax-\lambda x=0,
  \qquad
  (A-\lambda I)x=0.
  \]
- State that \(x\) must be a nonzero vector in the null space of \(A-\lambda I\).

Notation trap:

- The zero vector is excluded. It satisfies the equation trivially for every \(\lambda\), so it is not an eigenvector.
- \(\lambda x\) must be rewritten as \(\lambda I x\) before factoring out \(x\).

### 5. Characteristic polynomial and eigenvalue roots

Probability: High.

Why: explicitly marked as a likely exam topic and exam note. The instructor also connected it to homework and the fundamental theorem of algebra.

Likely exam task:

- Use rank deficiency to get the determinant condition:
  \[
  \det(A-\lambda I)=0
  \]
  or
  \[
  \det(\lambda I-A)=0.
  \]
- Define the characteristic polynomial:
  \[
  p_A(\lambda)=\det(\lambda I-A).
  \]
- Know it is an \(n\)-degree monic polynomial for an \(n\times n\) matrix.
- Find eigenvalues as roots of the characteristic polynomial.

Notation trap:

- \(\det(A-\lambda I)\) and \(\det(\lambda I-A)\) have the same roots, even though they may differ by an overall sign depending on \(n\).
- A real matrix can have complex eigenvalues.
- Roots are counted with multiplicity.

### 6. Eigenspace, null space, and scalar multiples

Probability: High.

Why: repeated in the eigenvalue derivation and needed for diagonalizability. It is also a common conceptual exam target.

Likely exam task:

- After finding \(\lambda_i\), find eigenvectors from
  \[
  \operatorname{null}(A-\lambda_i I)
  \]
  or equivalently
  \[
  \operatorname{null}(\lambda_i I-A).
  \]
- Define the eigenspace as this null space.
- State that eigenvectors are the nonzero vectors in the eigenspace.

Conceptual question:

- If \(x\) is an eigenvector, why are \(5x\), \(10x\), or any nonzero scalar multiple also eigenvectors for the same eigenvalue?

Notation trap:

- The eigenspace includes the zero vector because it is a subspace, but the set of eigenvectors excludes the zero vector.

### 7. Connecting eigenvectors to diagonalization: \(AT=T\Lambda\)

Probability: High.

Why: explicitly marked as an exam note and proof-heavy. The instructor reused \(t_i\) notation on purpose to connect eigenvectors to basis vectors.

Likely exam task:

- Let \(t_1,\dots,t_n\) be eigenvectors of \(A\) with
  \[
  At_i=\lambda_i t_i.
  \]
- Form
  \[
  T=[t_1\ \cdots\ t_n].
  \]
- Use column-partitioned multiplication:
  \[
  AT=[At_1\ \cdots\ At_n]
  =[\lambda_1t_1\ \cdots\ \lambda_nt_n].
  \]
- Rewrite as
  \[
  AT=T\Lambda.
  \]
- If \(T\) is invertible, conclude
  \[
  T^{-1}AT=\Lambda.
  \]

Conceptual question:

- Diagonalization is equivalent to finding \(n\) linearly independent eigenvectors.

Notation trap:

- The eigenvalues \(\lambda_i\) do not need to be distinct in the displayed \(AT=T\Lambda\) setup.
- Right multiplication by a diagonal matrix scales columns; left multiplication by \(A\) applies \(A\) to each column.

### 8. Diagonalizable vs non-diagonalizable matrices

Probability: High.

Why: the instructor made this the answer to the diagonalization question and gave a concrete non-diagonalizable example.

Likely exam task:

- State:
  \[
  A\text{ is diagonalizable}
  \Longleftrightarrow
  A\text{ has }n\text{ linearly independent eigenvectors.}
  \]
- Classify a matrix as diagonalizable or not based on eigenspace dimensions.
- Explain why not every square matrix is diagonalizable.

Concrete example to know:

For
\[
A=
\begin{bmatrix}
0 & 1\\
0 & 0
\end{bmatrix},
\]
\[
\det(\lambda I-A)=\lambda^2.
\]
The only eigenvalue is \(0\), with algebraic multiplicity \(2\), but
\[
\operatorname{null}(A)=\operatorname{span}
\left\{
\begin{bmatrix}
1\\
0
\end{bmatrix}
\right\}
\]
has dimension \(1\). So there is not a full basis of eigenvectors, and the matrix is not diagonalizable.

Notation trap:

- Repeated eigenvalue does not automatically mean non-diagonalizable.
- Identity matrix has repeated eigenvalue \(1\) but is diagonalizable.

### 9. Algebraic vs geometric multiplicity

Probability: High.

Why: introduced to explain the core failure of diagonalization in the example. This is theorem-like and likely to become a test condition.

Likely exam task:

- Define algebraic multiplicity: number of times \(\lambda_i\) appears as a root of the characteristic polynomial.
- Define geometric multiplicity:
  \[
  g_i=\dim\operatorname{null}(\lambda_i I-A).
  \]
- Know that algebraic multiplicities add to \(n\).
- For diagonalization, the total number of independent eigenvector directions must reach \(n\):
  \[
  \sum_i g_i=n.
  \]

Conceptual question:

- Why does algebraic multiplicity \(2\) but geometric multiplicity \(1\) cause failure of diagonalization in a \(2\times2\) matrix?

Important implication:

- \(n\) distinct eigenvalues imply diagonalizable.
- The converse is false.

## Medium Probability Topics

### 10. Determinant as volume scaling and rank deficiency

Probability: Medium.

Why: proof-heavy support for the eigenvalue condition. It was not marked as a standalone likely exam topic, but the instructor spent time motivating determinant zero.

Likely exam task:

- Explain why rank deficiency corresponds to determinant zero for square matrices.
- Interpret determinant as area/volume scaling.
- Connect:
  \[
  A-\lambda I\text{ rank deficient}
  \Longleftrightarrow
  \det(A-\lambda I)=0.
  \]

Proof idea:

- A full-rank linear map sends a square/cube to a parallelogram/parallelepiped with nonzero area/volume.
- A rank-deficient map collapses the space into a lower-dimensional subspace, so the ambient volume becomes zero.

Notation trap:

- Determinant zero is a square-matrix condition. Do not apply determinant language directly to non-square matrices.

### 11. Matrix factorization philosophy: diagonal, triangular, orthogonal

Probability: Medium.

Why: it opens the lecture and frames why the course cares about diagonalization, QR, LU, and permutation matrices. Less likely as a computation question, more likely as a conceptual prompt.

Likely exam task:

- Explain why diagonal, triangular, and orthogonal systems are easy.
- Connect solving a hard system to factoring the matrix into simple matrices.
- Recognize examples:
  - \(QR\): orthogonal times upper triangular.
  - Gaussian elimination/LU: lower triangular operations converting to upper triangular form.
  - Row exchanges: permutation matrix \(P\), which is orthogonal.

Conceptual question:

- Why is matrix factorization equivalent to solving a sequence of easier systems?

### 12. Similarity, triangularization, Schur/Jordan direction, and SVD

Probability: Medium.

Why: explicitly marked as a likely exam topic in the transcript summary, but much of it is preview rather than fully developed. Expect conceptual comparison, not detailed Schur/Jordan computations.

Likely exam task:

- Identify \(T^{-1}AT\) as a similarity transformation.
- State that not every square matrix is similar to a diagonal matrix.
- State the weaker positive result given in lecture:
  \[
  \text{Every square matrix can be triangularized by basis change.}
  \]
- Distinguish:
  - diagonalization: same basis for input and output;
  - SVD direction: different bases for input and output.

Conceptual question:

- Why does allowing different input/output bases make diagonal-type representation more flexible?

Notation trap:

- Same-basis diagonalization is only natural for square matrices.
- For rectangular matrices, "diagonal" means only main-diagonal entries may be nonzero; dimensions of input and output differ.
- Jordan form was mentioned only as close-to-diagonal with possible superdiagonal entries; the instructor said not to go deeply into it.

### 13. Complex norm and conjugate transpose

Probability: Medium.

Why: explicitly marked as an exam note, and the instructor warned about mistakes with complex transpose. It is likely as a definition or notation trap.

Likely exam task:

- For real vectors:
  \[
  \|x\|_2=\sqrt{x^T x}.
  \]
- For complex vectors:
  \[
  \|x\|_2=\sqrt{x^H x}
  =
  \sqrt{\sum_i |x_i|^2}.
  \]
- Explain why conjugation is needed: \(\overline{a}a=|a|^2\) is nonnegative real, while \(a^2\) may be complex.

Notation trap:

- \(x^H\), \(x^*\), or Hermitian transpose means transpose plus conjugation.
- Plain transpose is \(x^T\), not \(x^H\).

### 14. MATLAB transpose warning

Probability: Medium.

Why: explicit instructor warning. Even if not a formal theorem, this is exactly the kind of implementation/notation trap that can appear in short questions.

Likely exam task:

- Know MATLAB conventions:
  - `x'` is conjugate transpose.
  - `x.'` is plain transpose.
  - `conj(x)` conjugates without transposing.

Notation trap:

- For real vectors, `x'` and `x.'` give the same numerical result.
- For complex vectors, confusing them changes the result and can break inner-product/norm computations.

### 15. Complex inner product convention and scaling rules

Probability: Medium.

Why: definition-heavy and trap-heavy. The instructor emphasized that complex inner products are not symmetric and scaling depends on which argument is scaled.

Likely exam task:

- Use the lecture convention:
  \[
  \langle x,y\rangle=y^H x
  =
  \sum_i x_i\overline{y_i}.
  \]
- Recover the norm:
  \[
  \|x\|_2=\sqrt{\langle x,x\rangle}.
  \]
- State conjugate symmetry:
  \[
  \langle x,y\rangle=\overline{\langle y,x\rangle}.
  \]
- State scaling rules:
  \[
  \langle \alpha x,y\rangle=\alpha\langle x,y\rangle,
  \qquad
  \langle x,\beta y\rangle=\overline{\beta}\langle x,y\rangle.
  \]

Notation trap:

- The lecture uses linearity in the first argument and conjugate-linearity in the second. Some books use the opposite convention.
- If \(\langle x,y\rangle=3+5i\), then \(\langle y,x\rangle=3-5i\), not \(3+5i\).

### 16. Orthogonal and orthonormal sets over complex vector spaces

Probability: Medium.

Why: explicitly marked as an exam note and it transitions into the next major topic, orthogonal projection. Likely as a definition check.

Likely exam task:

- Define an orthogonal set \(S\subseteq C^m\):
  \[
  \langle u,v\rangle=0
  \quad\text{for every distinct }u,v\in S.
  \]
- Define an orthonormal set: orthogonal plus every vector has unit norm.
- Recognize the standard basis as orthonormal.
- Recognize scaled coordinate vectors as orthogonal but not necessarily orthonormal.

Notation trap:

- Orthogonality is a property of every distinct pair in the set, not just one pair.
- Orthonormal requires both pairwise orthogonality and unit norms.

## Low Probability Topics

### 17. Historical polynomial-solving remarks

Probability: Low.

Why: included to motivate why characteristic roots are not always available by simple formulas. It supports the eigenvalue discussion but is unlikely to be tested directly.

Likely exam task:

- At most, know the conceptual point: high-degree characteristic polynomials may not have general closed-form formulas, but over complex numbers the roots still exist by the fundamental theorem of algebra.

Notation trap:

- "No formula in radicals for all degree-five polynomials" does not mean eigenvalues do not exist.

### 18. Orthogonal projection preview

Probability: Low.

Why: mentioned only as the next lecture's key operation. Lecture 08 does not develop projection formulas.

Likely exam task:

- Only know that the complex inner product and orthogonal/orthonormal set definitions prepare for projection.

Do not over-study from Lecture 08:

- Projection of a vector onto a vector.
- Projection onto a subspace.
- Projection formula derivations.

Those were previewed, not taught in this lecture.

## Fast Priority List

1. Master \(x=T\tilde{x}\), \(\tilde{x}=T^{-1}x\), and \(\tilde{A}=T^{-1}AT\).
2. Be able to derive \(Ax=\lambda x\Rightarrow(A-\lambda I)x=0\Rightarrow\det(A-\lambda I)=0\).
3. Be able to explain eigenspace as a null space and exclude the zero vector from eigenvectors.
4. Be able to prove \(AT=T\Lambda\Rightarrow T^{-1}AT=\Lambda\) when eigenvectors form a basis.
5. Know the diagonalizability condition: \(n\) linearly independent eigenvectors.
6. Know algebraic vs geometric multiplicity and the nilpotent Jordan-block example.
7. Know the complex-vector traps: conjugate transpose, MATLAB `'` vs `.'`, and conjugate symmetry of the inner product.
