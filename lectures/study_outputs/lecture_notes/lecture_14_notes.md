# Lecture 14 Notes

## Normal Matrices and Eigenvalue-Based Subclasses

The lecture opened by connecting several matrix classes through normal matrices.

- Normal matrices are diagonalizable by unitary matrices.
- A key reason this diagonalization is useful is that eigenspaces of a normal matrix are orthogonal to each other.
- Because of that orthogonal eigenspace structure, one can organize subclasses of normal matrices according to where their eigenvalues lie.

For a general normal matrix, eigenvalues may be arbitrary complex numbers. Important subclasses arise by restricting the eigenvalues:

- Eigenvalues on the unit circle correspond to unitary matrices.
- Eigenvalues on the real axis correspond to Hermitian matrices.
- Eigenvalues on the imaginary axis correspond to the skew case discussed in lecture, mathematically the skew-Hermitian type.

The lecture then focused on the Hermitian case. Hermitian matrices have real eigenvalues, so it becomes meaningful to classify them by the signs of their eigenvalues.

## Hermitian Sign Classes

For Hermitian matrices, the important sign-based classes are:

- Positive definite matrices.
- Negative definite matrices.
- Positive semidefinite matrices.
- Negative semidefinite matrices.
- Indefinite matrices.

The difference among these is determined by the sign pattern of the real eigenvalues.

### Positive Definite

There are two equivalent ways emphasized for defining a positive definite matrix.

1. Eigenvalue definition:
   - \(A\) is Hermitian.
   - All eigenvalues of \(A\) are positive.

2. Quadratic-form definition:
   - The quadratic form defined by \(A\) is always positive away from the origin:
     \[
     x^* A x > 0 \quad \text{for every } x \ne 0.
     \]

The second definition is often easier to use in proofs.

### Positive Semidefinite

The semidefinite case relaxes strict positivity:

- Eigenvalues may be positive or zero.
- No eigenvalue is negative.
- The quadratic form satisfies
  \[
  x^* A x \ge 0.
  \]

Zero eigenvalues correspond to directions where the quadratic form can be flat.

### Negative Semidefinite and Negative Definite

For negative semidefinite matrices:

- Eigenvalues are less than or equal to zero.
- No eigenvalue is positive.
- The quadratic form is always nonpositive:
  \[
  x^* A x \le 0.
  \]

For negative definite matrices, the "semi" is removed:

- Eigenvalues are strictly negative.
- For every nonzero \(x\),
  \[
  x^* A x < 0.
  \]

The instructor described this as removing the equality/zero allowance from the semidefinite case.

### Indefinite

If a Hermitian matrix has a mixture of positive and negative eigenvalues, then the quadratic form is indefinite.

- In some directions the form behaves like a parabola opening up.
- In other directions it behaves like a parabola opening down.
- Geometrically this leads to saddle-type behavior.

## Motivation: Quadratic Functions

The motivation for organizing Hermitian matrices by eigenvalue signs is the behavior of quadratic functions.

### Single-Variable Quadratics

For a single-variable quadratic, the coefficient of the \(x^2\) term determines the basic shape:

- Positive coefficient: parabola opening upward.
- Negative coefficient: parabola opening downward.
- Zero coefficient: the quadratic part disappears, leaving a linear structure.

### Multivariate Quadratics

In the multivariate case, a quadratic function can be written in shifted form as
\[
f(x) = (x-x_0)^* A (x-x_0) + d.
\]

Here:

- \(x_0\) shifts the center/location of the quadratic function.
- \(d\) shifts the function vertically.
- The matrix \(A\) determines the shape.

The sign class of \(A\) controls the geometry:

- If \(A\) is positive definite Hermitian, the function is convex and parabola-up.
- If \(A\) is negative definite Hermitian, the function is concave and parabola-down.
- If \(A\) is indefinite, the function has saddle structure.

The instructor remarked that an AI-generated example of an indefinite quadratic function naturally produced a function with mixed eigenvalue signs, even without explicitly asking for eigenvalue conditions.

## Cross Terms, Rotation, and Principal Directions

The lecture contrasted diagonal and non-diagonal quadratic forms.

When the matrix is diagonal, the main directions of the quadratic function align with the original coordinate axes. For example:

- In a saddle picture, the parabola-down direction might align with the \(x\)-axis.
- The parabola-up direction might align with the \(y\)-axis.

This is the case where the cross term is zero.

When a cross term such as \(b x_1 x_2\) is present with \(b \ne 0\), it effectively rotates the quadratic function. The principal axes no longer align with the standard coordinate axes.

The remedy is a change of coordinates using eigenvectors:

- The eigenvectors of \(A\) determine the principal directions.
- In the new eigenvector coordinates, the quadratic form has no cross terms.
- This is the geometric meaning of diagonalizing \(A\).

## Main Example: \(A = \begin{bmatrix}5&4\\4&5\end{bmatrix}\)

The lecture returned to the matrix
\[
A =
\begin{bmatrix}
5 & 4 \\
4 & 5
\end{bmatrix}.
\]

This matrix has cross terms in the standard-coordinate quadratic form and is positive definite.

The eigenvalues are:
\[
\lambda_1 = 9, \qquad \lambda_2 = 1.
\]

Interpretation:

- In the \((1,1)\) direction, the eigenvalue is \(9\), so the quadratic is highly curved.
- In the \((1,-1)\) or perpendicular direction, the eigenvalue is \(1\), so the function is flatter.

## Level Curves of Quadratic Functions

The previous lecture had introduced level curves of quadratic functions. Lecture 14 continued that discussion.

For a quadratic form, an \(\alpha\)-level set is the set of domain points satisfying
\[
x^* A x = \alpha.
\]

In the positive definite or negative definite case, these level sets are ellipse-like.

- For a convex quadratic, the level curves are ellipses around the center.
- For a concave quadratic, one can similarly look at intersections with horizontal levels and obtain corresponding level sets.
- For indefinite quadratic forms, the level sets are generally hyperbolic rather than elliptic. The instructor said that the hyperbolic indefinite case would not be covered further there.

### Circular and Elliptic Cases

If
\[
A =
\begin{bmatrix}
9 & 0 \\
0 & 9
\end{bmatrix},
\]
then
\[
9x_1^2 + 9x_2^2 = \alpha
\]
is a circle.

If one eigenvalue changes, for example to \(1\), the level set becomes an ellipse.

For diagonal matrices, the principal semi-axes align with the coordinate axes.

For non-diagonal matrices, the ellipse rotates. The level sets rotate because the quadratic function has rotated.

The principal semi-axes are the directions of maximum deviation from the origin or center of the ellipse. They are determined by the eigenvectors of \(A\).

## Eigenvalue Decomposition of the \(5,4;4,5\) Example

The formal procedure starts with the characteristic equation:
\[
\det(\lambda I - A) = 0.
\]

For
\[
A =
\begin{bmatrix}
5 & 4 \\
4 & 5
\end{bmatrix},
\]
we have
\[
\lambda I - A =
\begin{bmatrix}
\lambda - 5 & -4 \\
-4 & \lambda - 5
\end{bmatrix}.
\]

The determinant is
\[
(\lambda - 5)^2 - 16.
\]

Thus
\[
|\lambda - 5| = 4,
\]
which gives
\[
\lambda = 9 \quad \text{or} \quad \lambda = 1.
\]

### Eigenspace for \(\lambda = 9\)

To find the eigenspace, plug \(\lambda = 9\) into \(\lambda I - A\). This produces a rank-deficient matrix. One row is the negative of the other, so the null space is nontrivial.

Vectors with equal entries are annihilated:
\[
\begin{bmatrix}
\beta \\
\beta
\end{bmatrix}.
\]

So the eigenspace for \(\lambda = 9\) is in the direction of
\[
\begin{bmatrix}
1 \\
1
\end{bmatrix}.
\]

A unit eigenvector is
\[
q_1 =
\frac{1}{\sqrt{2}}
\begin{bmatrix}
1 \\
1
\end{bmatrix}.
\]

Because the matrix is normal/Hermitian, eigenspaces corresponding to distinct eigenvalues are orthogonal. Therefore, a unit eigenvector for the other eigenspace can be chosen as
\[
q_2 =
\frac{1}{\sqrt{2}}
\begin{bmatrix}
-1 \\
1
\end{bmatrix}.
\]

The instructor noted that the negative of a unit eigenvector could also have been chosen.

Putting the eigenvectors into a matrix \(Q\), with \(q_1\) and \(q_2\) as columns, gives an orthonormal eigenvector matrix. The decomposition is
\[
A = Q \Lambda Q^T
\]
in the real case, or \(A = Q \Lambda Q^*\) in the complex notation.

The eigenvectors form an orthonormal basis:

- They are orthogonal.
- They each have unit norm.

## Change of Coordinates and Cross-Term Removal

The eigenvector matrix gives a change of basis.

- \(x\) contains coordinates with respect to the standard basis.
- \(z\) contains coordinates with respect to the eigenvector basis.

In standard coordinates, the quadratic form is
\[
x^T A x = 5x_1^2 + 5x_2^2 + 8x_1x_2.
\]

The \(8x_1x_2\) term is the cross term.

In eigenvector coordinates, the quadratic form becomes
\[
z^T \Lambda z = 9z_1^2 + z_2^2.
\]

There is no cross term. The coordinate axes have been rotated intelligently so that they align with the eigenvectors.

Geometrically:

- \(q_1\) points at a 45-degree angle and corresponds to \(\lambda = 9\).
- \(q_2\) is perpendicular and corresponds to \(\lambda = 1\).
- These eigenspaces define the principal semi-axes of the ellipse.

## Larger Eigenvalue Means Narrower Axis for \(x^T A x = \alpha\)

For the level set
\[
9z_1^2 + z_2^2 = \alpha,
\]
if \(z_2 = 0\), then
\[
9z_1^2 = \alpha
\]
and therefore
\[
|z_1| = \frac{\sqrt{\alpha}}{3}.
\]

If \(z_1 = 0\), then
\[
|z_2| = \sqrt{\alpha}.
\]

Thus, for the level set \(x^T A x = \alpha\), the ellipse is narrower in the direction associated with the larger eigenvalue.

The instructor warned that some people instead write ellipses using \(A^{-1}\), such as \(x^T A^{-1}x\). In that convention the eigenvalues are reciprocals, so the visual relation between large eigenvalues and axis lengths reverses.

For \(x^T A x = \alpha\):

- Large eigenvalue direction -> narrower semi-axis.
- Small eigenvalue direction -> wider semi-axis.

The key relationship remains: the eigenvectors of \(A\) define the principal semi-axes of the ellipse.

## Higher-Dimensional Level Sets

In three dimensions, if
\[
A = I,
\]
then
\[
x^T A x = 1
\]
gives a sphere.

If one diagonal entry is changed, for example from \(1\) to \(2\), the level set becomes an ellipsoid.

In higher dimensions:

- The boundary level set is called a hyperellipse in the lecture's terminology.
- If the solid interior is included, it is a hyperellipsoid.

The instructor emphasized that so far the lecture had been constructing multivariate quadratic functions based on Hermitian matrices, and then moved to why they are useful.

## Application: Quadratic Approximation

One important application area is quadratic approximation of general nonlinear functions.

### Single-Variable Taylor Approximation

Near a point \(x_0\), a general nonlinear function can be approximated using Taylor series.

The instructor stressed that the Taylor series itself is not an approximation if all infinitely many terms are kept. It becomes an approximation when only finitely many terms are retained.

Keeping terms through second order gives
\[
f(x)
\approx
f(x_0)
+ f'(x_0)(x-x_0)
+ \frac{1}{2} f''(x_0)(x-x_0)^2.
\]

Interpretation:

- Keeping only the value gives a constant local approximation.
- Keeping the value and first-derivative term gives an affine/tangent approximation.
- Adding the second-derivative term gives a quadratic approximation.

If the original function has positive curvature around \(x_0\), then the quadratic approximation is convex and parabola-up in that region.

### Multivariate Taylor Approximation

For a multivariate function, the second-order approximation around \(x_0\) has the form
\[
f(x)
\approx
f(x_0)
+ \nabla f(x_0)^T (x-x_0)
+ \frac{1}{2}(x-x_0)^T H(x_0)(x-x_0),
\]
where \(H(x_0)\) is the Hessian matrix.

The parts have the following meanings:

- \(f(x_0)\) is the function value at the expansion point.
- \(\nabla f(x_0)^T(x-x_0)\) is the affine part.
- \((x-x_0)^T H(x_0)(x-x_0)\) is the quadratic curvature part.

The gradient contains partial derivatives with respect to the coordinate directions. Taking the inner product of the gradient with a direction vector gives a directional derivative in that direction.

The Hessian matrix contains second-order derivative information:

- Diagonal entries are second derivatives with respect to individual variables, such as \(\partial^2 f/\partial x_1^2\).
- Off-diagonal entries are mixed second derivatives and correspond to cross terms.

The lecture assumed regularity so that the order of differentiation does not matter. Under that assumption, the Hessian is symmetric.

The eigenvalue sign pattern of the Hessian determines the local quadratic shape:

- Positive definite Hessian: locally parabola-up/convex.
- Negative definite Hessian: locally parabola-down/concave.
- Mixed positive and negative eigenvalues: local saddle structure.

A student asked whether this connects to gradient descent or Newton's method. The instructor answered that this kind of quadratic approximation is the basis of Newton-like algorithms for optimization, and that this may be discussed later.

## Positive Semidefinite Geometry: Flat Directions

The instructor then discussed what happens when the Hessian or matrix is positive semidefinite but not positive definite.

Example:
\[
A =
\begin{bmatrix}
1 & 0 \\
0 & 0
\end{bmatrix}.
\]

This matrix is positive semidefinite because its eigenvalues are \(1\) and \(0\).

The quadratic form is
\[
x^T A x = x_1^2.
\]

Consequences:

- In the \(x_1\) direction, the function is parabola-up.
- In the \(x_2\) direction, the curvature is zero.
- The value of \(x_2\) does not affect the quadratic form.
- Along zero-eigenvalue directions, the function is flat.

The instructor described the shape as like a parabolic sheet or rolled paper: it curves in one direction and is flat in the other.

The same idea persists for shifted or rotated semidefinite quadratics. A shift changes where the parabolic sheet is centered, and a non-diagonal positive semidefinite matrix can rotate the curved and flat directions away from the standard coordinate axes. The zero-eigenvalue directions remain the directions with no quadratic curvature.

## Properties of Positive Definite Matrices

Before continuing with applications, the lecture gave useful algebraic properties of positive definite and negative definite matrices.

### Positive Linear Combinations

Suppose
\[
A_1,\ldots,A_m
\]
are positive definite matrices, and
\[
c_1,\ldots,c_m > 0
\]
are positive scalars.

Then
\[
\sum_{i=1}^m c_i A_i
\]
is also positive definite.

Proof idea using quadratic forms:

Take any nonzero \(x\). Then
\[
x^* \left(\sum_{i=1}^m c_i A_i\right) x
=
\sum_{i=1}^m c_i x^* A_i x.
\]

Each \(x^* A_i x\) is strictly positive because \(A_i\) is positive definite and \(x \ne 0\). Each \(c_i\) is also positive. Therefore every term in the sum is positive, so the total sum is positive.

The instructor noted that proving this directly from eigenvalues of the sum would be harder, while the quadratic-form definition makes it easy.

### Notation Warning: \(A > 0\)

The notation \(A > 0\) or \(A \ge 0\), when used for matrices in this context, does not mean that all entries of \(A\) are positive or nonnegative.

It means positive definite or positive semidefinite in the eigenvalue/quadratic-form sense.

Some authors use curved notation such as \(A \succ 0\) or \(A \succeq 0\) to avoid confusion with elementwise inequalities. The instructor said they would continue using the regular inequality notation with the understanding that it refers to definiteness.

### Positive Integer Powers

If \(A\) is positive definite, then every positive integer power \(A^k\) is also positive definite.

Proof idea:

Use the unitary eigenvalue decomposition
\[
A = U \Lambda U^*,
\]
where all diagonal entries of \(\Lambda\) are positive eigenvalues.

Then
\[
A^2 = U \Lambda U^* U \Lambda U^*
= U \Lambda^2 U^*.
\]

Similarly,
\[
A^k = U \Lambda^k U^*.
\]

Since positive numbers remain positive under positive integer powers, all eigenvalues of \(A^k\) are positive.

For a negative definite matrix, parity matters:

- Even powers are positive definite.
- Odd powers are negative definite.

This happens because even powers of negative eigenvalues become positive, while odd powers remain negative.

## Diagonal Dominance as a Sufficient Condition

The lecture introduced a sufficient condition for positive semidefiniteness and positive definiteness.

For a Hermitian matrix with positive diagonal entries, if each diagonal entry dominates the sum of the absolute values of the other entries in that row,
\[
a_{ii} \ge \sum_{j \ne i} |a_{ij}|,
\]
then the matrix is positive semidefinite.

The positive-diagonal condition is not cosmetic. The right side is nonnegative, so this dominance condition implicitly requires the relevant diagonal entries to be nonnegative, and in the strict positive definite version they must be positive.

If the inequality is strict for each row,
\[
a_{ii} > \sum_{j \ne i} |a_{ij}|,
\]
then the matrix is positive definite.

Important warning:

- This is a sufficient condition, not a necessary condition.
- A matrix may fail this diagonal dominance condition and still be positive semidefinite or positive definite.

The instructor connected this to the earlier matrix
\[
\begin{bmatrix}
5 & 4 \\
4 & 5
\end{bmatrix},
\]
which satisfies strict diagonal dominance because \(5 > 4\) in each row.

For negative definiteness, one can apply the positive definite condition to \(-A\). Equivalently, the negative of a negative definite matrix is positive definite.

In row-dominance language, a negative definite sufficient condition is obtained by having negative diagonal entries whose absolute values dominate the off-diagonal row sums. This is just the same positive definite dominance test applied after multiplying the matrix by \(-1\).

## Similarity Versus Star-Congruence

The lecture then introduced an important relationship for Hermitian matrices: star-congruence.

### Similarity

Similarity had appeared earlier in the context of changing basis for linear transformations.

If two matrices are related by a similarity transformation, they represent the same linear transformation in different bases. Similar matrices have the same eigenvalues.

In symbolic form, the relationship is of the type
\[
A = T B T^{-1}
\]
for an invertible \(T\).

Key property:

- Similar matrices have exactly the same eigenvalues.

### Star-Congruence

For Hermitian matrices, define a different relationship:
\[
A = S B S^*
\]
where \(S\) is invertible.

The instructor emphasized:

- \(S\) is not assumed to be unitary.
- It only needs to be nonsingular/invertible.
- This relationship is called star-congruence.

Star-congruence does not preserve the actual eigenvalues. Instead, it preserves the sign pattern of eigenvalues.

For example:

- If all eigenvalues of \(A\) are positive, all eigenvalues of \(B\) are positive.
- If five eigenvalues of \(A\) are positive, then five eigenvalues of \(B\) are positive.
- The numerical eigenvalues may differ, but the counts of positive, negative, and zero eigenvalues agree.

## Inertia

The preserved sign pattern is called the inertia of a Hermitian matrix.

For a Hermitian matrix, inertia is the ordered triple
\[
(n_+, n_-, n_0),
\]
where:

- \(n_+\) is the number of positive eigenvalues.
- \(n_-\) is the number of negative eigenvalues.
- \(n_0\) is the number of zero eigenvalues.

Eigenvalues are counted with multiplicity.

### Examples

For
\[
\begin{bmatrix}
5 & 4 \\
4 & 5
\end{bmatrix},
\]
the eigenvalues are \(9\) and \(1\). Therefore its inertia is
\[
(2,0,0).
\]

For the \(3 \times 3\) identity matrix, all three eigenvalues are \(1\). Counting multiplicity, the inertia is
\[
(3,0,0).
\]

For a matrix with two positive eigenvalues, one negative eigenvalue, and no zero eigenvalues, the inertia is
\[
(2,1,0).
\]

The instructor was asked about why the term "inertia" is used. The instructor did not give a definitive historical answer, but noted that these ideas arise in contexts involving Hermitian matrices and energy functions, such as mechanical systems and Lagrangian-type formulations.

## Sylvester's Law of Inertia

The lecture stated the key connection between star-congruence and inertia.

For Hermitian matrices \(A\) and \(B\),
\[
A = S B S^*
\]
for some nonsingular \(S\) if and only if \(A\) and \(B\) have the same inertia.

This is Sylvester's law of inertia.

The instructor emphasized the contrast:

- Similarity preserves eigenvalues.
- Star-congruence preserves inertia, meaning only the sign counts of eigenvalues.

The proof was skipped in lecture and left for students to think about in both directions.

## Corollary: Positive Definite Matrices Are Star-Congruent to Identity

An important corollary follows directly from Sylvester's law of inertia.

A matrix is positive definite if and only if it is star-congruent to the identity matrix.

Reason:

- The \(n \times n\) identity matrix has inertia \((n,0,0)\).
- Any \(n \times n\) positive definite matrix also has inertia \((n,0,0)\).
- Therefore a positive definite matrix and the identity have the same inertia.
- By Sylvester's law, they are star-congruent.

Thus, if \(A\) is positive definite, there exists a nonsingular matrix \(S\) such that
\[
A = S I S^* = S S^*.
\]

This leads to the notion of a matrix square root.

## Matrix Square Roots in the Broad \(S S^*\) Sense

If
\[
A = S S^*,
\]
then \(S\) is called a square root of the positive definite matrix \(A\) in the lecture's broad sense.

The instructor motivated this concept with applications:

- Generating random vectors with arbitrary correlation.
- Whitening signals in communication systems.

### Non-Uniqueness of Square Roots

The square root is not unique.

Suppose \(S\) is one square root:
\[
S S^* = A.
\]

Let \(T\) be any unitary matrix, so
\[
T T^* = I.
\]

Define
\[
S_2 = S T.
\]

Then
\[
S_2 S_2^*
=
(S T)(S T)^*
=
S T T^* S^*
=
S I S^*
=
S S^*
=
A.
\]

Therefore \(S_2\) is also a square root of \(A\).

Since there are infinitely many unitary matrices, a positive definite matrix has infinitely many square roots in this sense.

The instructor also pointed out the converse parameterization idea: once one square root \(S\) is known, the whole family of square roots can be described by right-multiplying \(S\) by unitary matrices. If \(R R^* = A\) and \(S S^* = A\), then \(R = S U\) for a unitary \(U = S^{-1}R\).

### \(1 \times 1\) Example

In the \(1 \times 1\) case, positive definite matrices are positive real numbers.

For example, if \(A = 25\), then \(S = 5\) is a square root because
\[
5 \cdot 5^* = 25.
\]

But \(1 \times 1\) unitary matrices are complex numbers on the unit circle, \(e^{j\phi}\). Therefore
\[
5e^{j\phi}
\]
is also a square root in the \(S S^* = A\) sense, because
\[
(5e^{j\phi})(5e^{j\phi})^* = 25.
\]

### Notation Warning

The instructor writes something like
\[
S = A^{1/2}
\]
for a square root, but warned that this notation is ambiguous unless a particular square root is specified.

It may simply mean "choose one matrix \(S\) satisfying \(S S^* = A\)."

The conjugate-transpose of a chosen square root must also be read relative to that choice. The instructor mentioned a shorthand style that saves parentheses, such as writing a conjugate-square-root notation for \((A^{1/2})^*\), but the warning is the same: without choosing the particular square root, the notation is not identifying a unique matrix.

A student suggested interpreting the notation as a set of all square roots and then choosing an element from that set. The instructor said that is a possible viewpoint, but the lecture notation would stick with choosing one square root.

## Positive Definite Square Root via Eigenvalue Decomposition

The lecture then gave a concrete way to find one square root.

Let
\[
A = U \Lambda U^*
\]
be the eigenvalue decomposition of a positive definite Hermitian matrix.

Because \(A\) is positive definite, all eigenvalues in \(\Lambda\) are positive.

Define
\[
A^{1/2} = U \Lambda^{1/2} U^*,
\]
where \(\Lambda^{1/2}\) is the diagonal matrix whose entries are the positive square roots of the eigenvalues.

This gives the positive definite square root.

Properties:

- It is Hermitian.
- It is positive definite.
- Its conjugate transpose equals itself.
- Multiplying it by its conjugate transpose gives back \(A\):
  \[
  A^{1/2}(A^{1/2})^* = A.
  \]

This is one distinguished square root among the infinitely many possible square roots.

## Cholesky Factorization: Lower Triangular Square Root

The lecture stated another square-root theorem for positive definite matrices: Cholesky factorization.

If \(A\) is positive definite, then there exists a lower triangular matrix \(L\) with positive diagonal entries such that
\[
A = L L^*.
\]

This \(L\) is a lower triangular square root of \(A\).

The instructor connected this to Gaussian elimination:

- Whenever lower triangular matrices appear, think of Gaussian elimination.
- Earlier \(LDU\) factorization was essentially based on Gaussian elimination.
- For positive definite matrices, the upper triangular factor can be related to the conjugate transpose of the lower triangular factor.

## Cholesky Proof Sketch: Block Partition

The instructor began a proof sketch for Cholesky factorization.

Partition the positive definite matrix \(A\) by separating its first row and first column:
\[
A =
\begin{bmatrix}
\alpha & v^* \\
v & M
\end{bmatrix},
\]
where:

- \(\alpha\) is the first diagonal entry.
- \(v\) is a column vector.
- \(v^*\) appears because \(A\) is Hermitian.
- \(M\) is an \((n-1) \times (n-1)\) Hermitian block.

### Why \(\alpha > 0\)

Since \(A\) is positive definite,
\[
x^* A x > 0
\]
for every nonzero \(x\).

Choose \(x = e_1\), the first standard basis vector. Then
\[
e_1^* A e_1 = \alpha.
\]

Therefore
\[
\alpha > 0.
\]

The same idea shows that every diagonal entry of a positive definite matrix is positive.

### Why \(M\) Is Positive Definite

Take a vector of the form
\[
x =
\begin{bmatrix}
0 \\
\beta
\end{bmatrix},
\]
where \(\beta \ne 0\).

Then
\[
x^* A x = \beta^* M \beta.
\]

Since \(A\) is positive definite, this quantity is positive for every nonzero \(\beta\). Therefore
\[
M
\]
is positive definite.

At this point:

- \(\alpha > 0\).
- \(M\) is positive definite.
- \(v\) has not yet been characterized.

## Eliminating the First Column

The next step is to eliminate the entries below \(\alpha\) in the first column, similar to Gaussian elimination.

Use the lower triangular matrix
\[
S =
\begin{bmatrix}
1 & 0 \\
-v/\alpha & I
\end{bmatrix}.
\]

Left multiplication by \(S\) performs row operations:

- The first row is preserved.
- Scaled multiples of the first row are subtracted from the lower rows.
- The lower entries in the first column are canceled.

This gives an intermediate block upper triangular form.

Then multiply on the right by \(S^*\):
\[
S A S^*.
\]

Right multiplication by \(S^*\) performs the corresponding column operation and cancels the upper-right block. The result is a block diagonal matrix:
\[
S A S^*
=
\begin{bmatrix}
\alpha & 0 \\
0 & M - \frac{vv^*}{\alpha}
\end{bmatrix}.
\]

This is block diagonal, not fully diagonal.

The matrix \(S\) is invertible because it is triangular with ones on its diagonal. Thus \(A\) and the block diagonal matrix are star-congruent.

## The Schur Complement Block

The lower-right block
\[
M - \frac{vv^*}{\alpha}
\]
is the important remaining block.

The instructor analyzed
\[
\frac{vv^*}{\alpha}.
\]

Since \(\alpha > 0\), division by \(\alpha\) preserves positive semidefiniteness.

### Properties of \(vv^*\)

The matrix \(vv^*\) is Hermitian:
\[
(vv^*)^* = vv^*.
\]

It is an outer product, so it has rank one unless \(v=0\).

The vector \(v\) is an eigenvector:
\[
vv^*v = v(v^*v) = \|v\|^2 v.
\]

Thus the one possible nonzero eigenvalue is
\[
\|v\|^2.
\]

All remaining eigenvalues are zero. Therefore \(vv^*\) is positive semidefinite, and so is \(vv^*/\alpha\).

### Important Warning

Even though \(M\) is positive definite and \(vv^*/\alpha\) is positive semidefinite, it is not automatically obvious from the expression alone that
\[
M - \frac{vv^*}{\alpha}
\]
is positive definite.

In general, subtracting a positive semidefinite matrix from a positive definite matrix can destroy positive definiteness if the subtracted matrix is large enough.

The instructor said that the expression-by-itself route is not the easiest way to prove positivity.

Instead, use star-congruence:

- \(S A S^*\) is star-congruent to \(A\).
- \(A\) is positive definite.
- Star-congruence preserves inertia.
- Therefore \(S A S^*\) is also positive definite.
- Since the block diagonal matrix is positive definite and \(\alpha > 0\), the lower-right block
  \[
  M - \frac{vv^*}{\alpha}
  \]
  must be positive definite.

This is the key proof idea that allows the Cholesky proof to continue recursively.

## Instructor Remarks and Study Warnings

The instructor made several remarks that are important for studying this lecture:

- The hyperbolic level sets of indefinite quadratic forms were mentioned but not covered further.
- Taylor series itself has infinitely many terms; approximation comes from truncating it.
- The symmetry of the Hessian assumes mixed partial derivatives commute.
- Quadratic approximations are a foundation for Newton-like optimization methods.
- For positive definite notation, \(A > 0\) is not an elementwise statement.
- Diagonal dominance is sufficient but not necessary.
- Similarity and star-congruence are different: one preserves eigenvalues, the other preserves inertia.
- The proof of Sylvester's law of inertia was left to students to think about in both directions.
- The Cholesky proof was not finished in this lecture; the instructor said it would continue on Thursday.
- The instructor specifically asked students to review star-congruence, Sylvester's law of inertia, and square roots. These algebraic tricks will be used repeatedly.

## Source and Coverage Note

Source used: `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture14_corrected.md`.

Coverage: These notes follow the lecture chronologically and include the concepts, definitions, examples, proof ideas, instructor remarks, warnings, and relationships present in the lecture 14 transcript. No other lecture transcript was processed.
