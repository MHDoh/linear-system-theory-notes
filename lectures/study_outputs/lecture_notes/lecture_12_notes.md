# Lecture 12 Notes

## 1. Course Storyline: Simple Matrices, Factorizations, and Basis Changes

The lecture begins by placing the current topic inside the overall storyline of the course:

- Start with linear systems that are easy to solve.
- Use these easy cases as motivation for factorizations and matrix structure.
- Then study what happens for a general matrix by trying to convert it into one of the easier forms.

The simple matrix classes mentioned are:

- **Diagonal systems**: easy because each equation separates.
- **Triangular systems**: easy because they can be solved by forward or backward substitution.
- **Orthogonal or unitary systems**: easy because the inverse is obtained by transpose or conjugate transpose.

For a general matrix \(A\), the main idea is to represent it as a product of simple matrices. This gives different matrix factorizations.

Another major idea is basis change:

- A matrix \(A\) defines a linear transformation.
- One can try to choose bases in the input and output spaces so that the representation of this transformation becomes diagonal.
- This leads to diagonalization.

A key limitation was recalled:

- Not every matrix is diagonalizable.
- Some matrices can be diagonalized, but others cannot.
- This motivates more flexible replacements, especially triangularization.

The diagonalization question is closely tied to eigenvalues and eigenvectors.

## 2. Orthogonality, Projection, and Complex Inner Products

The lecture recalls earlier material on geometry:

- Orthogonality.
- Orthogonal projection of a vector onto another vector.
- Orthogonal projection of a vector onto a subspace.
- Orthogonal projection matrices and their properties.

[Likely exam topic] Projection and orthogonality are part of the course's central set of structured matrix examples.

The instructor also recalls that the Euclidean inner product was extended to complex vectors:

- For complex vectors, the conjugate transpose appears in the inner product.
- This complex inner product is the setting for unitary matrices and Hermitian matrices.

The instructor remarks that later the course will generalize the inner product further:

- Alternative inner products will be introduced.
- These can be viewed as alternative geometries.

The structured matrices seen so far include:

- Diagonal matrices.
- Triangular matrices.
- Orthogonal matrices.
- Orthogonal projection matrices.
- Hermitian matrices.

The instructor emphasizes that understanding what each structure implies is at the core of the analysis.

## 3. Review of Unitary Matrices

A unitary matrix is the complex analogue of a real orthogonal matrix.

Definition:

\[
U^*U = UU^* = I,
\]

so

\[
U^{-1} = U^*.
\]

This means the inverse is obtained effortlessly by taking the conjugate transpose.

Solving a system involving a unitary matrix is therefore simple:

\[
Ux = v
\]

implies

\[
x = U^*v.
\]

Important properties of unitary matrices:

- They preserve Euclidean norm:

\[
\|Ux\| = \|x\|.
\]

- They preserve inner products:

\[
\langle Ux, Uy\rangle = \langle x, y\rangle.
\]

- Their eigenvalues lie on the unit circle:

\[
|\lambda| = 1.
\]

- Their determinant also lies on the unit circle, because it is the product of eigenvalues.

[Exam note] If a unitary matrix has two distinct eigenvalues, then the corresponding eigenspaces are orthogonal to each other. The instructor says this property will be generalized in this lecture.

This same distinct-eigenvalue orthogonality property also holds for Hermitian matrices.

## 4. Right and Left Eigenvectors

The standard, or right, eigenvalue equation is:

\[
Ax = \lambda x.
\]

A left eigenvector is written as a row vector multiplying the matrix from the left:

\[
y^T A = \lambda y^T.
\]

The instructor connects this to the idea of left null spaces:

- A left null space condition involves multiplying from the left by a row vector.
- The left null space of \(A\) is the null space of \(A^T\).

Taking transposes relates left eigenvectors of \(A\) to right eigenvectors of \(A^T\).

Instructor warning:

- The right-eigenvector equation and left-eigenvector equation are the same eigenvalue idea written on different sides of the matrix.
- A left eigenvector is not a new geometric object detached from the usual eigenvector concept; after transposition it becomes an eigenvector condition for \(A^T\).
- The instructor briefly framed this as a trick question to make students distinguish column-vector multiplication from row-vector multiplication.

## 5. Orthogonal and Unitary Matrices in Applications

Real orthogonal matrices can model rigid motion.

Example:

- A triangle moving in two-dimensional space can be modeled by multiplication by a real orthogonal matrix, together with a translation.

The lecture also recalls unitary transformations:

- A unitary transformation is essentially an orthogonal basis change in complex space.
- It preserves the geometry determined by the Euclidean inner product.

## 6. Fourier Transform as a Unitary Transformation

[Exam note] The Fourier transform is described as an orthogonal/unitary transformation.

The Fourier basis appears naturally because it diagonalizes circulant matrices.

Important relationship:

- Circulant matrix diagonalization by the Fourier basis means that convolution in the time domain becomes multiplication in the frequency domain.
- This is the major significance of the Fourier transform in the linear algebra viewpoint.

The instructor mentions that the homework studies why the Fourier basis emerges.

## 7. Lossless Systems, Energy, and All-Pass Systems

Another application of unitary matrices is the modeling of lossless systems.

The instructor notes that "lossless" can mean different things depending on what notion of loss is used. In this lecture, losslessness is defined in terms of energy.

For a vector or signal \(x\), energy is defined as:

\[
\sum_i |x_i|^2.
\]

The words vector and signal are used interchangeably in this discussion.

A system is lossless if:

\[
\text{input energy} = \text{output energy}.
\]

For a linear system, preserving this energy can be modeled by a unitary matrix.

If the system is also time invariant, this leads to all-pass systems:

- The frequency response has magnitude equal to one.
- At every frequency, the system neither amplifies nor attenuates the input.

[Exam note] The convolution matrix for a linear time-invariant causal system has several structures at once:

- It is **lower triangular** because the system is causal.
- It is **Toeplitz** because it represents convolution.
- It is **unitary** if the system is lossless.

The rows of this convolution matrix contain the impulse response of the system.

The Fourier transform of the impulse response is the frequency response.

For a lossless time-invariant system, the frequency response has magnitude one at every frequency.

## 8. Schur Factorization as a Consolation for Non-Diagonalizability

The lecture recalls the main result from the previous lecture: Schur factorization.

Since not every matrix can be diagonalized, Schur factorization provides a weaker but always-available result.

The theorem says:

For any square matrix \(A\), there exists a unitary matrix \(U\) such that

\[
A = UTU^*,
\]

where \(T\) is upper triangular.

The columns of \(U\) form an orthonormal basis.

Interpretation:

- We may not be able to find a basis in which \(A\) is diagonal.
- But we can always find an orthonormal basis in which \(A\) is upper triangular.

[Exam note] The proof starts with one eigenvalue and one eigenvector of \(A\), then extends that eigenvector to an orthonormal basis.

This result is important because it will be used to prove properties of normal matrices.

## 9. Hermitian Matrices

A Hermitian matrix satisfies:

\[
A^* = A.
\]

The instructor contrasts this with unitary matrices:

- For a unitary matrix, \(A^* = A^{-1}\).
- For a Hermitian matrix, \(A^* = A\).

So the conjugate transpose does not directly give the inverse for a Hermitian matrix. Hermitian matrices are therefore not "simple" in the same solve-a-linear-system sense as unitary matrices.

However, Hermitian matrices are very important because they define real-valued quadratic functions.

For a complex vector \(x\):

\[
x^*x
\]

is always real and nonnegative.

For a Hermitian matrix \(A\), the scalar

\[
x^*Ax
\]

is real-valued even when \(x\) is complex.

This expression defines a real-valued quadratic function of a complex vector.

[Exam note] Understanding Hermitian matrix properties is important because these properties partition the space of Hermitian matrices into useful subclasses.

Using the real-valued quadratic form property, one can show that every eigenvalue of a Hermitian matrix is real.

Comparison with unitary matrices:

- Unitary matrices have eigenvalues on the unit circle.
- Hermitian matrices have eigenvalues on the real line.

## 10. Matrices That Are Both Hermitian and Unitary

The identity matrix is both Hermitian and unitary:

\[
I^* = I,
\]

and

\[
I^{-1} = I.
\]

Its eigenvalues are all \(1\), which lie both on the real axis and on the unit circle.

The instructor notes that the identity is not the only example.

A matrix can be both Hermitian and unitary when:

- Its eigenvalues are constrained to \(1\) and \(-1\).
- It satisfies the relevant orthogonality structure between eigenspaces.

This will connect to the later normal-matrix viewpoint.

## 11. Real Symmetric and Skew-Hermitian Matrices

The real-valued version of a Hermitian matrix is a symmetric matrix.

If the matrix entries are real, conjugation does not change anything, so:

\[
A^* = A
\]

becomes

\[
A^T = A.
\]

A skew-symmetric real matrix satisfies:

\[
A^T = -A.
\]

The complex analogue is a skew-Hermitian matrix:

\[
A^* = -A.
\]

The instructor names this form as **skew-Hermitian**, not "Hermitian skew."

Entrywise interpretation:

- An off-diagonal entry is the negative conjugate of the transposed entry.
- In the real skew-symmetric case, the \((1,5)\) entry is the negative of the \((5,1)\) entry.
- On the diagonal, the skew-Hermitian condition reduces to a scalar satisfying \(\overline{a}_{ii}=-a_{ii}\), so diagonal entries are purely imaginary or zero.
- In the real skew-symmetric case, the diagonal entries must be zero.

The instructor asks students to check the eigenvalue property for skew-Hermitian matrices.

For Hermitian matrices:

\[
A^* = A
\]

implies eigenvalues are real.

For skew-Hermitian matrices:

\[
A^* = -A
\]

implies eigenvalues are purely imaginary.

Thus skew-Hermitian eigenvalues have the form:

\[
i\lambda_r,
\]

where \(\lambda_r\) is real.

The instructor gives a useful one-dimensional analogy:

- A \(1 \times 1\) Hermitian matrix is just a real number.
- A \(1 \times 1\) skew-Hermitian matrix is just a purely imaginary number.

So Hermitian and skew-Hermitian matrices can be viewed as matrix generalizations of real and imaginary numbers.

## 12. Normal Matrices: The Common Family

Hermitian matrices, unitary matrices, and skew-Hermitian matrices all belong to a larger family called normal matrices.

Normal matrices are square matrices.

The instructor describes a conceptual Venn diagram:

- Normal matrices contain unitary matrices.
- Normal matrices contain Hermitian matrices.
- Normal matrices contain skew-Hermitian matrices.
- Hermitian and unitary matrices can intersect.
- The diagram is only conceptual, not a literal low-dimensional geometric picture.
- There is also a large collection of square matrices outside the normal class.

The defining equation for a normal matrix is:

\[
AA^* = A^*A.
\]

This says that \(A\) commutes with its conjugate transpose.

The instructor remarks that matrix multiplication is not generally commutative, so this is a special property.

Warning:

- The equation \(AA^* = A^*A\) does not immediately make the eigenspace orthogonality property obvious.
- A main goal of the lecture is to explain why this commutation condition is equivalent to unitary diagonalization and to orthogonal eigenspaces for distinct eigenvalues.

Why unitary matrices are normal:

\[
U^*U = UU^* = I.
\]

Why Hermitian matrices are normal:

If \(A^* = A\), then

\[
AA^* = A^2
\]

and

\[
A^*A = A^2.
\]

Why skew-Hermitian matrices are normal:

If \(A^* = -A\), then both products reduce consistently, so the order does not matter.

The instructor jokes that matrices outside the normal set could be called "abnormal," but the mathematical name is normal.

Important interpretation:

- The word normal is connected to eigenspaces being normal, or orthogonal, to each other.
- For normal matrices, eigenspaces corresponding to distinct eigenvalues are orthogonal.

Eigenvalue locations distinguish the major subclasses:

- Hermitian matrices: eigenvalues on the real line.
- Unitary matrices: eigenvalues on the unit circle.
- Skew-Hermitian matrices: eigenvalues on the imaginary axis.

The list of structured matrices seen so far includes:

- Diagonal matrices.
- Triangular matrices.
- Hankel matrices from homework.
- Toeplitz matrices from homework.
- Orthogonal matrices.
- Orthogonal projection matrices.
- Hermitian matrices.
- Skew-Hermitian matrices.

[Exam note] Hankel and Toeplitz matrices were explicitly tied to homework.

## 13. Equivalent Definitions of Normal Matrices

The instructor gives several equivalent definitions. Each can be used as a definition because they imply each other.

The instructor notes that the choice of starting definition is partly pedagogical:

- He starts from \(AA^*=A^*A\) because it connects directly to the earlier stories \(A^*=A\) for Hermitian matrices and \(U^*=U^{-1}\) for unitary matrices.
- He could instead have started from the energy equality or from unitary diagonalizability and then treated the other statements as properties.
- Showing how the definitions imply each other is described as an algebraically rich and useful exercise.

### Definition A: Commutation with the Conjugate Transpose

\[
AA^* = A^*A.
\]

This is the starting definition in the lecture.

### Definition B: Unitary Diagonalizability

A matrix is normal if and only if it is unitarily diagonalizable:

\[
A = UDU^*,
\]

where:

- \(U\) is unitary.
- \(D\) is diagonal.
- The diagonal entries of \(D\) are the eigenvalues of \(A\).

[Exam note] Not every matrix is diagonalizable, but every normal matrix is diagonalizable. More specifically, every normal matrix is diagonalizable by a unitary matrix.

### Definition C: Matrix Energy Equals Eigenvalue Energy

A matrix is normal if and only if:

\[
\sum_{i,j} |a_{ij}|^2 = \sum_i |\lambda_i|^2.
\]

The left side is the sum of squared magnitudes of all matrix entries.

The square root of the left side is the Frobenius norm:

\[
\|A\|_F = \left(\sum_{i,j} |a_{ij}|^2\right)^{1/2}.
\]

Without the square root, the instructor calls it the energy of the matrix through its elements.

The right side is the energy of the eigenvalues.

[Likely exam topic] The equality between matrix-entry energy and eigenvalue energy is one of the equivalent ways to recognize normal matrices.

### Definition D: Orthonormal Eigenbasis

A matrix is normal if and only if its eigenvectors can form an orthonormal basis for \(\mathbb{C}^n\).

The instructor clarifies what is nontrivial here:

- Within a single eigenspace, one can always choose an orthonormal basis.
- The key issue is whether eigenspaces for distinct eigenvalues are orthogonal to each other.
- For normal matrices, distinct eigenspaces are orthogonal, so the eigenvectors from all eigenspaces can be assembled into one orthonormal basis.

This connects back to the earlier property for Hermitian and unitary matrices.

## 14. Proof Idea: Orthonormal Eigenbasis Implies Unitary Diagonalization

The instructor shows that Definition D implies Definition B.

Assume \(A\) has eigenvectors

\[
u_1, u_2, \ldots, u_n
\]

that form an orthonormal basis.

Put these vectors into the columns of a matrix:

\[
U = [u_1 \ u_2 \ \cdots \ u_n].
\]

Because the columns are orthonormal, \(U\) is unitary.

Now multiply \(A\) by \(U\):

\[
AU = [Au_1 \ Au_2 \ \cdots \ Au_n].
\]

Since each \(u_i\) is an eigenvector,

\[
Au_i = \lambda_i u_i.
\]

So:

\[
AU = [\lambda_1u_1 \ \lambda_2u_2 \ \cdots \ \lambda_nu_n].
\]

This can be written as:

\[
AU = U\Lambda,
\]

where

\[
\Lambda =
\begin{bmatrix}
\lambda_1 & 0 & \cdots & 0 \\
0 & \lambda_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & \lambda_n
\end{bmatrix}.
\]

The instructor emphasizes the side of multiplication:

- Multiplying by a diagonal matrix from the right scales columns.
- Multiplying by a diagonal matrix from the left scales rows.

Here we need to scale the columns of \(U\), so the diagonal matrix appears on the right:

\[
AU = U\Lambda.
\]

Multiplying on the right by \(U^*\) gives:

\[
A = U\Lambda U^*.
\]

Equivalently,

\[
U^*AU = \Lambda.
\]

Thus \(A\) is unitarily diagonalizable.

## 15. Trace as a Useful Algebraic Tool

The instructor introduces trace as a tool for proving the energy equivalence.

Definition:

\[
\operatorname{tr}(A)
\]

is the sum of the diagonal entries of \(A\).

[Exam note] Trace is a simple but very useful operator.

Trace is defined for square matrices. In this lecture it is applied to products such as \(A^*A\) and \(AA^*\), which are square.

Properties of trace:

- It ignores off-diagonal entries.
- It is linear:

\[
\operatorname{tr}(\alpha A) = \alpha \operatorname{tr}(A),
\]

and

\[
\operatorname{tr}(A+B) = \operatorname{tr}(A) + \operatorname{tr}(B).
\]

- It satisfies the cyclic two-factor property:

\[
\operatorname{tr}(AB) = \operatorname{tr}(BA),
\]

when the products are defined.

The instructor says trace is useful because it can replace messy index-based summations with matrix expressions.

## 16. Trace and the Energy of a Matrix

The instructor derives:

\[
\operatorname{tr}(A^*A) = \sum_{i,j} |a_{ij}|^2.
\]

Let \(A\) be partitioned into columns:

\[
A = [a_1 \ a_2 \ \cdots \ a_n].
\]

Then:

\[
A^*A
\]

has diagonal entries:

\[
a_1^*a_1,\ a_2^*a_2,\ \ldots,\ a_n^*a_n.
\]

Taking the trace gives:

\[
\operatorname{tr}(A^*A)
= \sum_j a_j^*a_j
= \sum_j \|a_j\|^2.
\]

Each column norm expands into the sum of squared magnitudes of entries in that column:

\[
\sum_j \|a_j\|^2
= \sum_{i,j} |a_{ij}|^2.
\]

The same energy can also be obtained using \(\operatorname{tr}(AA^*)\).

This establishes that the entrywise energy of a matrix can be written compactly using trace.

Important status of this step:

- At this point the instructor has not yet proved the normal-matrix energy equivalence.
- He has proved the reusable identity that converts the entrywise sum into a trace expression.
- That identity is then plugged into the unitary diagonalization argument.

## 17. Proof Idea: Unitary Diagonalization Implies Energy Equality

Assume \(A\) is unitarily diagonalizable:

\[
A = U\Lambda U^*.
\]

Then:

\[
A^* = U\Lambda^*U^*.
\]

Using the trace expression for matrix energy:

\[
\sum_{i,j}|a_{ij}|^2
= \operatorname{tr}(A^*A).
\]

Substitute the diagonalization:

\[
\operatorname{tr}(A^*A)
= \operatorname{tr}(U\Lambda^*U^*U\Lambda U^*).
\]

Because \(U^*U=I\),

\[
\operatorname{tr}(A^*A)
= \operatorname{tr}(U\Lambda^*\Lambda U^*).
\]

Using the trace property \(\operatorname{tr}(AB)=\operatorname{tr}(BA)\), move \(U^*\) cyclically to combine with \(U\):

\[
\operatorname{tr}(U\Lambda^*\Lambda U^*)
= \operatorname{tr}(\Lambda^*\Lambda U^*U)
= \operatorname{tr}(\Lambda^*\Lambda).
\]

Since \(\Lambda\) is diagonal, \(\Lambda^*\Lambda\) is diagonal with entries:

\[
|\lambda_1|^2,\ |\lambda_2|^2,\ \ldots,\ |\lambda_n|^2.
\]

Therefore:

\[
\operatorname{tr}(\Lambda^*\Lambda)
= \sum_i |\lambda_i|^2.
\]

So:

\[
\sum_{i,j} |a_{ij}|^2 = \sum_i |\lambda_i|^2.
\]

Instructor clarification:

- The result uses magnitude squares, not ordinary squares.
- This is because each eigenvalue is multiplied by its complex conjugate.

## 18. Proof Idea: Normality Implies Unitary Diagonalization

The instructor next discusses why:

\[
AA^* = A^*A
\]

implies unitary diagonalizability.

The instructor remarks that trying to prove this directly from the eigenvector definition would be possible but nontrivial. The previous lecture's Schur factorization makes the proof much cleaner.

The key tool is Schur factorization.

For any square matrix \(A\), write:

\[
A = UTU^*,
\]

where \(U\) is unitary and \(T\) is upper triangular.

The goal is to show that if \(A\) is normal, then \(T\) is not merely triangular but actually diagonal.

Since \(T\) is upper triangular, it has the eigenvalues of \(A\) on its diagonal. Its possible nonzero entries above the diagonal are the only obstruction to diagonal form.

Substitute the Schur form into the normality equation:

\[
AA^* = A^*A.
\]

Using:

\[
A = UTU^*,
\]

and

\[
A^* = UT^*U^*,
\]

the normality equation becomes:

\[
UTT^*U^* = UT^*TU^*.
\]

Multiplying by \(U^*\) on the left and \(U\) on the right gives:

\[
TT^* = T^*T.
\]

Now use the fact that \(T\) is upper triangular.

Compare the \((1,1)\) entry of both sides.

For \(TT^*\), the \((1,1)\) entry is:

\[
|t_{11}|^2 + |t_{12}|^2 + \cdots + |t_{1n}|^2.
\]

For \(T^*T\), the \((1,1)\) entry is:

\[
|t_{11}|^2,
\]

because the first column of an upper triangular matrix has no entries below \(t_{11}\).

Equality forces:

\[
|t_{12}|^2 + \cdots + |t_{1n}|^2 = 0.
\]

Since each term is nonnegative, all of them must be zero:

\[
t_{12}=t_{13}=\cdots=t_{1n}=0.
\]

Then one repeats the same argument for the \((2,2)\) entry, then the \((3,3)\) entry, and so on.

At each step, the remaining off-diagonal entries in that row must be zero.

Therefore \(T\) is diagonal.

Thus:

\[
A = UTU^*
\]

is actually a unitary diagonalization.

Conclusion:

- Schur factorization says every square matrix is unitarily triangularizable.
- Normality forces the triangular factor to be diagonal.
- Therefore every normal matrix is unitarily diagonalizable.

## 19. Normal Matrices Classified by Eigenvalue Geometry

The instructor summarizes the big picture:

Normal matrices are exactly the unitarily diagonalizable matrices.

Within this family, subclasses are distinguished by where their eigenvalues lie.

Examples:

- If the eigenvalues lie on the unit circle, the matrix is unitary.
- If the eigenvalues lie on the real line, the matrix is Hermitian.
- If the eigenvalues lie on the imaginary axis, the matrix is skew-Hermitian.

This explains why these classes share properties:

- They all sit inside the normal matrix family.
- They are all unitarily diagonalizable.
- Their eigenspaces for distinct eigenvalues are orthogonal.

What changes from one subclass to another is the eigenvalue constraint.

## 20. Focusing on Hermitian Matrices by Eigenvalue Signs

The lecture then turns to a finer classification inside the Hermitian matrices.

Hermitian matrices have real eigenvalues. Since the eigenvalues are real, their signs become meaningful.

The instructor says the course will partition Hermitian matrices according to whether their eigenvalues are:

- Positive.
- Negative.
- Zero.
- Mixed positive and negative.

This partition is not arbitrary notation: it is motivated by the quadratic form \(x^*Ax\) and by the geometry of multivariable quadratic functions.

This classification is important because of the quadratic function:

\[
x^*Ax.
\]

[Exam note] The sign of the eigenvalues is critical for understanding the shape of this quadratic function.

## 21. Quadratic Forms and Surface Shapes

For a two-variable quadratic function, think of:

\[
x =
\begin{bmatrix}
x_1 \\
x_2
\end{bmatrix},
\]

and the function:

\[
x^*Ax.
\]

If \(A\) is Hermitian with positive eigenvalues, the quadratic surface looks like an upward-opening paraboloid.

Optimization interpretation:

- This is a convex function.
- It has a unique minimum.
- It is easier to optimize.
- The instructor calls this one of the "dream" cases for optimization.

If \(A\) has negative eigenvalues, the surface looks like a downward-opening paraboloid.

Optimization interpretation:

- This is a concave function.
- It is the negative analogue of the convex case.

If \(A\) has mixed eigenvalues, with some positive and some negative, the surface has a saddle structure.

Geometric interpretation:

- In one direction, it curves upward.
- In an orthogonal direction, it curves downward.
- The instructor compares it to a horse saddle.

Optimization and machine learning remark:

- Saddle structures are difficult in nonconvex optimization.
- The instructor mentions terminology such as rideable and non-rideable saddles.
- Mixed-sign eigenvalues lead to functions that are neither convex nor concave.

## 22. Probability Connection: Covariance and Correlation Matrices

The instructor asks where Hermitian matrices arise in probability.

The answer is:

- Correlation matrices.
- Covariance matrices.

These matrices are Hermitian.

The instructor adds that they always have nonnegative eigenvalues.

This property will be derived later.

This previews the connection between:

- Hermitian matrices.
- Positive semidefinite matrices.
- Covariance and correlation.

## 23. Zero Matrix and Intersections of Classes

The zero matrix is both Hermitian and skew-Hermitian:

\[
0^* = 0
\]

and

\[
0^* = -0.
\]

Its eigenvalues are all zero.

Zero lies both on the real axis and on the imaginary axis.

The instructor uses this to explain that the class diagrams should touch at the origin.

The zero matrix also belongs to both the nonnegative and nonpositive eigenvalue classes, because all its eigenvalues are zero.

## 24. Positive, Negative, Semidefinite, Definite, and Indefinite Matrices

The lecture introduces names for subclasses of Hermitian matrices based on eigenvalue signs.

The instructor remarks that the names may sound more intimidating than the definitions: they are simply labels for Hermitian matrices whose real eigenvalues satisfy sign constraints.

### Positive Definite

A Hermitian matrix \(A\) is positive definite if all eigenvalues are strictly positive:

\[
\lambda_i > 0 \quad \text{for all } i.
\]

Example:

- The identity matrix is positive definite because all eigenvalues are \(1\).

### Positive Semidefinite

A Hermitian matrix \(A\) is positive semidefinite if all eigenvalues are nonnegative:

\[
\lambda_i \ge 0 \quad \text{for all } i.
\]

Zero eigenvalues are allowed.

### Negative Definite

A Hermitian matrix \(A\) is negative definite if all eigenvalues are strictly negative:

\[
\lambda_i < 0 \quad \text{for all } i.
\]

### Negative Semidefinite

A Hermitian matrix \(A\) is negative semidefinite if all eigenvalues are nonpositive:

\[
\lambda_i \le 0 \quad \text{for all } i.
\]

Zero eigenvalues are allowed.

### Indefinite

A Hermitian matrix is indefinite if it has a mixture of positive and negative eigenvalues.

This corresponds to saddle-shaped quadratic forms.

[Likely exam topic] The instructor explicitly highlights positive definite, negative definite, positive semidefinite, negative semidefinite, and indefinite matrices.

## 25. Meaning of "Semidefinite" and Connection to Rank

A student asks about the word "definite."

The instructor connects definiteness to rank and invertibility:

- If all eigenvalues are strictly nonzero, the matrix is invertible.
- If zero eigenvalues are present, the matrix is not invertible.

For positive or negative definite matrices:

- All eigenvalues are strictly positive or strictly negative.
- No eigenvalue is zero.
- The matrix is invertible.

For semidefinite matrices:

- Some eigenvalues may be zero.
- The matrix may be non-invertible.

The instructor says he is not certain of the exact historical origin of the word "definite," but his interpretation is that when all eigenvalues are strictly nonzero, the related problem can be solved without ambiguity.

## 26. Alternative Definition of Positive Definite Matrices

The first definition of positive definiteness is spectral:

\[
A \text{ is positive definite}
\iff
\lambda_i > 0 \text{ for all } i.
\]

The instructor then gives an equivalent quadratic-form definition.

A Hermitian matrix \(A\) is positive definite if and only if:

\[
x^*Ax > 0
\]

for every nonzero vector \(x\).

At the origin:

\[
x = 0
\]

gives:

\[
x^*Ax = 0.
\]

[Exam note] The expression \(x^*Ax\) is a real-valued quadratic function of \(x\). For positive definite matrices, it is always positive except at the origin.

Why the spectral definition can lead to the quadratic-form definition:

- Since \(A\) is Hermitian, it is normal and therefore unitarily diagonalizable.
- Thus one can write \(A=U\Lambda U^*\), where \(\Lambda\) is real diagonal.
- If \(A\) is positive definite, the diagonal entries of \(\Lambda\) are positive.
- The postponed proof will use this structure to show \(x^*Ax>0\) for every \(x\neq 0\).

The instructor notes that the equivalence between the eigenvalue definition and the quadratic-form definition can be shown both ways:

- Positive eigenvalues imply \(x^*Ax > 0\) for all nonzero \(x\).
- The positivity of \(x^*Ax\) for all nonzero \(x\) implies all eigenvalues are positive.

He postpones the full proof to the next lecture because it would take time and he does not want to confuse the class at the end of the session.

## 27. Relationships to Preserve

The lecture repeatedly links concepts through the following relationships:

- Easy-to-solve matrix structures motivate factorizations.
- Failure of universal diagonalization motivates Schur factorization.
- Schur factorization gives universal unitary triangularization.
- Normality forces the Schur triangular factor to become diagonal.
- Therefore normal matrices are exactly unitarily diagonalizable matrices.
- Unitary, Hermitian, and skew-Hermitian matrices are all normal.
- These subclasses are distinguished by eigenvalue location:
  - Unit circle for unitary matrices.
  - Real line for Hermitian matrices.
  - Imaginary axis for skew-Hermitian matrices.
- Orthogonality of eigenspaces for distinct eigenvalues is shared by normal matrices.
- Hermitian matrices define real-valued quadratic forms.
- The signs of Hermitian eigenvalues determine the geometry of the quadratic form.
- Positive eigenvalues correspond to convex upward paraboloid behavior.
- Negative eigenvalues correspond to concave downward paraboloid behavior.
- Mixed signs correspond to saddle behavior.
- Covariance and correlation matrices are Hermitian and will later be shown to be positive semidefinite.

## 28. Instructor Remarks, Warnings, and Exam Cues

The instructor explicitly flags or emphasizes:

- Projection and orthogonality are important structured-matrix material.
- The orthogonality of eigenspaces for distinct eigenvalues, previously seen for unitary and Hermitian matrices, is generalized by normal matrices.
- Fourier transform and Fourier bases are important because they diagonalize circulant matrices.
- Convolution matrices combine multiple structures: lower triangular, Toeplitz, and unitary in the lossless causal LTI case.
- Schur factorization is important and was proved by starting with an eigenvector and extending it to an orthonormal basis.
- Hermitian matrices are important because they define real-valued quadratic functions.
- Normal matrices are important because they are unitarily diagonalizable.
- The Frobenius norm and the energy equality between entries and eigenvalues are important equivalent descriptions of normality.
- Trace is simple but powerful, especially for replacing index-heavy expressions.
- The commutation condition \(AA^*=A^*A\) should not be treated as self-evidently geometric; the lecture's proof chain explains why it yields unitary diagonalization and orthogonal eigenspaces.
- The normal-matrix equivalences are not just facts to memorize; the instructor treats the implications between them as useful algebra practice.
- The sign of eigenvalues is critical for understanding the quadratic form \(x^*Ax\).
- Positive definite, semidefinite, negative definite, negative semidefinite, and indefinite matrices are likely important classifications.
- The proof that positive eigenvalues are equivalent to \(x^*Ax>0\) for all nonzero \(x\) is explicitly postponed to the next lecture.

The instructor also gives informal remarks:

- The name "normal" can sound distracting, but it is connected to eigenspaces being normal to each other.
- The Venn diagram picture of matrix classes is conceptual, not an exact geometric picture.
- The labels positive semidefinite, negative semidefinite, definite, and indefinite are just the named sign-based subsets of Hermitian matrices.
- The term "definite" may be understood through the absence of zero eigenvalues and the resulting invertibility, though the instructor does not claim this as the historical origin.
- Saddle structures are a major difficulty in nonconvex optimization and machine learning.

## Source and Coverage Note

These notes were created from the corrected Lecture 12 transcript only:

`C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture12_corrected.md`

Coverage follows the transcript chronologically, including the opening review, instructor examples and remarks, exam cues, proof ideas, normal matrix equivalences, trace/Frobenius arguments, and the closing transition into positive definiteness. The transcript ends with the instructor postponing the proof of the positive-definite quadratic-form equivalence to the next lecture.
