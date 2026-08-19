# Lecture 10 Notes: Unitary and Real Orthogonal Matrices

## Big Picture: Turning Linear Systems Into Simple Problems

The lecture begins by returning to a broad strategy from earlier lectures: convert an arbitrary system of linear equations into a sequence of simpler systems. The simple matrix types emphasized are:

- Diagonal matrices.
- Triangular matrices.
- Orthogonal/unitary matrices.

These are easy to solve with compared to a general matrix. The practical goal is to factorize a general matrix \(A\) as a product of matrices from these simple classes.

Several factorizations fit into this same framework:

- Schur factorization uses orthogonal/unitary and triangular structure.
- QR factorization converts a problem into one involving an orthogonal/unitary factor and a triangular factor.
- Gaussian elimination is a special case of the same idea, leading to LU decomposition. In this view, a matrix is represented using lower and upper triangular matrices, sometimes with a permutation/orthogonal matrix \(P\).

## Diagonalization, Basis Change, and Triangularization

For square matrices, a matrix can be understood as the representation of a linear mapping. If the basis changes, the matrix representing the same mapping also changes.

With the usual coordinate convention, if \(x=T\tilde x\), then the same linear mapping is represented in the new coordinates by:

\[
\tilde A = T^{-1}AT.
\]

The exact left/right placement depends on the coordinate convention, but the important point in the lecture was that using the same basis for input and output produces the same transformation and its inverse on the two sides of \(A\).

The earlier question was whether one can choose a basis so that the matrix becomes diagonal. This is the diagonalization problem, studied through eigenvalues and eigenvectors.

Important distinction:

- Not every square matrix is diagonalizable.
- Square matrices are partitioned into diagonalizable and non-diagonalizable matrices.
- If the same basis must be used for the input and output spaces, diagonalization is not always possible.
- If two different bases are allowed for input and output spaces, the situation changes. The transformed representation has the form \(T_{\text{out}}^{-1}AT_{\text{in}}\), or in the instructor's wording two different matrices such as \(T_1\) and \(T_2^{-1}\), rather than the same \(T\) and \(T^{-1}\). In that broader input/output basis-change setting, the instructor noted that any matrix can be diagonalized or reduced to a diagonal canonical form. This topic is postponed.

### Exam Note: Every Square Matrix Can Be Triangularized

Even though not every matrix is diagonalizable, every square matrix can be triangularized. That is, for any square matrix, one can find a transformation matrix \(T\) so that the transformed representation is triangular.

The important extra property is that the transformation matrix used for this triangularization can be chosen to be orthogonal/unitary. Thus a general square matrix can be written in terms of simple matrix types: orthogonal/unitary and triangular matrices.

This is connected to Schur form, which will be a future topic. The instructor emphasized:

- Not all matrices are diagonalizable.
- But all square matrices are triangularizable.
- The triangularizing basis can be chosen orthogonal/unitary.

## Review: Orthogonal Projection Onto a Vector

The previous lecture introduced orthogonal projection. The first case was projecting a vector onto another vector.

If a vector \(x\) is projected onto a vector \(y\), the projection is a scaled version of \(y\). The scaling coefficient is the ratio of two inner products:

\[
\operatorname{proj}_y(x)
= \frac{\langle x,y\rangle}{\langle y,y\rangle}y.
\]

The numerator measures the interaction between \(x\) and \(y\). The denominator normalizes by the size of the vector being projected onto.

## Review: Orthogonal Projection Onto a Subspace

The more general case is projection of a vector onto a subspace.

To do this, choose a basis for the subspace and solve for the coefficients of the projected point. If the basis is orthonormal and its columns are collected in a tall matrix \(\hat Q\), then the orthogonal projection matrix has the form:

\[
P = \hat Q \hat Q^*.
\]

Here:

- \(\hat Q\) is tall.
- \(\hat Q^*\) is fat.
- The columns of \(\hat Q\) form an orthonormal basis for the subspace.
- The resulting projection matrix is generally rank deficient because it projects onto a lower-dimensional subspace.

Projection matrices satisfy:

\[
P^2 = P.
\]

This idempotence property is true for projection matrices in general.

For orthogonal projection matrices, there is an additional property:

\[
P^* = P.
\]

This means the projection matrix is self-adjoint/Hermitian in the complex case. The instructor contrasted orthogonal projections with oblique projections:

- Orthogonal projections satisfy \(P^*=P\).
- Oblique projections generally do not.
- Oblique projections will not be covered in this course.

## Definition: Unitary Matrices

A unitary matrix is a square complex matrix \(U\) satisfying:

\[
U^*U = I
\quad\text{and}\quad
UU^* = I.
\]

Here \(U^*\) denotes the conjugate transpose, also called the Hermitian transpose.

Therefore:

\[
U^{-1} = U^*.
\]

This is the complex generalization of a real orthogonal matrix.

### Why Unitary Systems Are Easy To Solve

If a system of linear equations has a unitary coefficient matrix,

\[
Ux=b,
\]

then solving is easy:

\[
x = U^*b.
\]

No general matrix inversion or elimination is needed; one only takes the conjugate transpose.

The operation \(U^*b\) can also be interpreted as taking inner products between \(b\) and the columns of \(U\), because conjugating and transposing the columns turns them into rows.

## Rows and Columns of a Unitary Matrix

The defining equalities imply two orthonormality facts:

- \(U^*U=I\) says the columns of \(U\) form an orthonormal basis of \(\mathbb C^n\).
- \(UU^*=I\) says the rows of \(U\) also form an orthonormal basis of \(\mathbb C^n\).

This links unitary matrices directly to orthonormal bases.

## Unitary Matrices Preserve Euclidean Norm

Consider the linear mapping

\[
x \mapsto Ux
\]

where \(U\) is unitary and \(x\in \mathbb C^n\). The input and output spaces have the same dimension.

The Euclidean norm is induced by the inner product:

\[
\|x\|_2 = \sqrt{x^*x}.
\]

For the transformed vector:

\[
\|Ux\|_2^2 = (Ux)^*(Ux).
\]

Using the rule \((Ux)^* = x^*U^*\):

\[
(Ux)^*(Ux)
= x^*U^*Ux
= x^*Ix
= x^*x
= \|x\|_2^2.
\]

Therefore:

\[
\|Ux\|_2 = \|x\|_2.
\]

### Important Warning About Norms

Unitary matrices preserve the Euclidean norm, also called the 2-norm for vectors. They do not necessarily preserve every possible norm.

Some other norms may also be preserved in special cases, but the guaranteed property discussed here is preservation of the Euclidean norm.

## Energy Preservation

The squared Euclidean norm is:

\[
\|x\|_2^2 = \sum_{i=1}^n |x_i|^2.
\]

The instructor referred to this as the energy of the vector or signal \(x\).

Since unitary matrices preserve \(\|x\|_2\), they also preserve energy:

\[
\|Ux\|_2^2 = \|x\|_2^2.
\]

Thus a unitary matrix defines an energy-preserving linear system.

## Relationship to Electrical Engineering and All-Pass Systems

In electrical engineering and signal processing, the energy of a signal in the Fourier domain is often written as an integral of the squared magnitude of the Fourier transform.

The limits depend on the setting:

- For discrete-time Fourier transforms, the frequency interval is typically from \(-\pi\) to \(\pi\).
- For continuous-time Fourier transforms, the interval is from \(-\infty\) to \(\infty\).

Energy-preserving linear time-invariant systems are called all-pass systems.

The instructor emphasized an important distinction:

- A unitary matrix gives an energy-preserving linear system.
- But it is not necessarily time invariant.
- To correspond to a linear time-invariant system, the matrix must have the special convolution/shift structure associated with LTI systems.

### Toeplitz Structure and LTI Systems

In an earlier homework, an LTI system was represented by a convolution operator. When written as a matrix, this gives a special structured matrix.

For an LTI system, each row is a shifted version of the previous row. This is the Toeplitz-type structure the instructor referred to.

Therefore:

- A unitary matrix without this shift structure is only a linear system.
- A unitary Toeplitz/convolution matrix would represent a linear time-invariant energy-preserving system.

## Distances and Inner Products Are Preserved

Because unitary matrices preserve Euclidean norms, they preserve distances. For two points \(x\) and \(y\), the distance is:

\[
\|x-y\|_2.
\]

Under the unitary mapping:

\[
\|Ux-Uy\|_2 = \|U(x-y)\|_2 = \|x-y\|_2.
\]

The Euclidean inner product is also preserved:

\[
\langle Ux, Uy\rangle = \langle x,y\rangle.
\]

Proof idea:

\[
(Uy)^*(Ux)
= y^*U^*Ux
= y^*x.
\]

Thus unitary matrices preserve:

- Euclidean norm.
- Energy.
- Distance.
- Euclidean inner product.
- Angles, in the real orthogonal case. The instructor noted that angle in the complex case requires more care and will not be emphasized here.

Since the norm is induced by the inner product, preservation of inner products implies preservation of norms.

## Geometric Interpretation: Shape Preservation

Unitary matrices preserve shapes in the sense that distances and inner products among components are preserved.

In the real orthogonal case, this geometric picture becomes especially clear. Real orthogonal transformations are built from two fundamental geometric operations:

- Rotations.
- Reflections.

The instructor noted that a general unitary/orthogonal transformation can be understood as a combination of such operations, with the most transparent geometric interpretation in the real case.

## Eigenvalues of Unitary Matrices

### Theorem: Eigenvalues Lie on the Unit Circle

If \(U\) is unitary and \(x\neq 0\) is an eigenvector satisfying:

\[
Ux = \lambda x,
\]

then:

\[
|\lambda| = 1.
\]

Proof idea:

Since unitary matrices preserve norm,

\[
\|Ux\|_2 = \|x\|_2.
\]

Substitute \(Ux=\lambda x\):

\[
\|\lambda x\|_2 = \|x\|_2.
\]

Using the scalar property of norms:

\[
|\lambda|\|x\|_2 = \|x\|_2.
\]

Because \(x\) is an eigenvector, \(x\neq 0\), so \(\|x\|_2\neq 0\). Divide by \(\|x\|_2\):

\[
|\lambda|=1.
\]

So every eigenvalue of a unitary matrix is a complex number on the unit circle.

### Determinant of a Unitary Matrix

The determinant is not necessarily \(1\), but its absolute value is \(1\):

\[
|\det(U)| = 1.
\]

The instructor answered a student question here: the determinant can be any point on the complex unit circle, not only \(1\).

Proof idea:

Unitary matrices are diagonalizable, and the lecture states this will be discussed more generally later. If:

\[
U = T\Lambda T^{-1},
\]

then:

\[
\det(U) = \det(T)\det(\Lambda)\det(T^{-1}).
\]

Since \(\det(T^{-1}) = 1/\det(T)\), those factors cancel:

\[
\det(U)=\det(\Lambda)=\prod_i \lambda_i.
\]

Each eigenvalue \(\lambda_i\) lies on the unit circle, so:

\[
|\det(U)| = \prod_i |\lambda_i| = 1.
\]

## Orthogonality of Eigenspaces for Distinct Eigenvalues

### Likely Exam Topic

If \(U\) is unitary and \(\lambda\neq \mu\) are two distinct eigenvalues, then the eigenspaces corresponding to \(\lambda\) and \(\mu\) are orthogonal.

Let:

\[
Ux = \lambda x,
\quad
Uy = \mu y.
\]

Using preservation of inner products:

\[
\langle Ux, Uy\rangle = \langle x,y\rangle.
\]

But using the eigenvalue equations:

\[
\langle Ux, Uy\rangle
= \langle \lambda x, \mu y\rangle.
\]

With the lecture's inner product convention, the scalar multiplying the first argument comes out as \(\lambda\), while the scalar multiplying the second argument comes out conjugated as \(\mu^*\). Hence:

\[
\langle \lambda x, \mu y\rangle
= \lambda \mu^* \langle x,y\rangle.
\]

Therefore:

\[
\lambda \mu^* \langle x,y\rangle = \langle x,y\rangle.
\]

Move terms:

\[
(1-\mu^*\lambda)\langle x,y\rangle = 0.
\]

Because \(\mu\) is on the unit circle,

\[
\mu^* = \frac{1}{\mu}.
\]

So:

\[
1-\mu^*\lambda = 1-\frac{\lambda}{\mu}.
\]

If \(\lambda\neq \mu\), then:

\[
1-\frac{\lambda}{\mu}\neq 0.
\]

Thus:

\[
\langle x,y\rangle = 0.
\]

Therefore eigenvectors from distinct eigenspaces are orthogonal, and the eigenspaces themselves are orthogonal.

### Relationship to Normal Matrices

This orthogonality property is not true for arbitrary matrices. It is true for unitary matrices.

The instructor also stated that the same property extends to a broader class of matrices, including Hermitian matrices. Matrices whose eigenspaces corresponding to distinct eigenvalues are orthogonal are part of the class called normal matrices.

Relationship:

- Unitary matrices are a subset of normal matrices.
- Hermitian matrices also belong to the same broader family.
- Normal matrices will be discussed later.

At this point the lecture used the eigenspace-orthogonality property as the preview. The formal normal-matrix condition will be developed later.

## Orthonormal Basis Coordinates

The lecture then returned to orthonormal bases and coordinates.

Suppose:

\[
x = \sum_{k=1}^n \alpha_k u_k
\]

where \(\{u_1,\dots,u_n\}\) is a basis.

For an arbitrary non-orthonormal basis, finding the coefficients \(\alpha_k\) requires solving a system of linear equations. If the basis vectors are put into a matrix \(U\), then:

\[
x = U\alpha.
\]

For a general basis, one must solve for:

\[
\alpha = U^{-1}x.
\]

But if the basis is orthonormal, finding the coordinates is simple.

Take the inner product of both sides with \(u_k\):

\[
\langle x,u_k\rangle
= \sum_i \alpha_i \langle u_i,u_k\rangle.
\]

All terms vanish except the \(i=k\) term because the basis is orthonormal:

\[
\langle u_i,u_k\rangle = 0 \quad (i\neq k),
\]

and:

\[
\langle u_k,u_k\rangle=1.
\]

Therefore:

\[
\alpha_k = \langle x,u_k\rangle.
\]

### Projection Interpretation

Finding the coordinate \(\alpha_k\) is the same as projecting \(x\) onto the basis element \(u_k\). Since \(u_k\) has norm \(1\), the usual projection denominator is \(1\).

Matrix interpretation:

If the orthonormal basis vectors are columns of \(U\), then \(U\) is unitary and:

\[
\alpha = U^{-1}x = U^*x.
\]

The entries of \(U^*x\) are inner products of \(x\) with the basis vectors:

\[
\alpha_1 = \langle x,u_1\rangle,\quad
\alpha_2 = \langle x,u_2\rangle,\quad \dots
\]

So the algebraic fact \(U^{-1}=U^*\) matches the geometric fact that coordinates in an orthonormal basis are obtained by projection.

### Warning: Non-Orthogonal Bases Do Not Work This Way

The instructor emphasized this warning several times:

- If the basis is not orthogonal, one cannot simply project \(x\) onto each basis vector and sum the projections.
- Non-orthogonal basis vectors have overlapping components.
- Projecting separately onto non-orthogonal directions double-counts shared components.
- In that case, each coefficient generally depends on inner products with all basis elements, and a full system must be solved.

If the basis vectors are orthogonal, individual projections are valid:

- Project \(x\) onto one orthogonal basis direction.
- Project \(x\) onto the other orthogonal basis directions.
- Sum those orthogonal components to reconstruct \(x\).

## Real Orthogonal Matrices

A real orthogonal matrix is a real version of a unitary matrix.

For a real matrix \(Q\), conjugate transpose becomes ordinary transpose, so:

\[
Q^TQ = I,
\quad
QQ^T = I,
\quad
Q^{-1}=Q^T.
\]

The instructor noted that the name "real orthogonal matrix" is historically standard, even though one could argue that "real orthonormal matrix" might be more descriptive because the columns form an orthonormal basis.

Properties:

- Columns of \(Q\) form an orthonormal basis for \(\mathbb R^n\).
- Rows of \(Q\) form an orthonormal basis for \(\mathbb R^n\).
- Multiplication by \(Q\) corresponds geometrically to combinations of rotations and reflections.

## Two-Dimensional Rotation Matrix

The instructor revisited a homework-style example: rotating a vector in \(\mathbb R^2\) counterclockwise by an angle \(\theta\).

If \(x=(x_1,x_2)^T\), then the rotated vector \(y\) is given by:

\[
y_1 = x_1\cos\theta - x_2\sin\theta,
\]

\[
y_2 = x_1\sin\theta + x_2\cos\theta.
\]

The instructor said this can be derived using trigonometric identities, but skipped the full derivation because it had already appeared in an early homework.

\[
y = Qx,
\]

where:

\[
Q =
\begin{bmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{bmatrix}.
\]

This matrix is real orthogonal:

\[
QQ^T = I.
\]

So a two-dimensional rotation is an example of a real orthogonal transformation.

## Reflections Across a Hyperplane

The second fundamental real orthogonal operation discussed was reflection.

In two dimensions, reflection across a line can be interpreted as taking the mirror image of a vector with respect to that line. In higher dimensions, the reflecting object is a hyperplane through the origin.

Suppose a hyperplane is defined by a normal vector \(v\). The hyperplane is:

\[
H = \{x : v^Tx = 0\}.
\]

The instructor assumes \(v\) may be unit norm for simplicity, though the formula can be written without that assumption.

### Projection Step

To reflect \(x\) across the hyperplane, first project \(x\) onto the normal direction \(v\). In the real case:

\[
\operatorname{proj}_v(x)
= \frac{v^Tx}{v^Tv}v.
\]

Equivalently:

\[
\operatorname{proj}_v(x)
= \frac{vv^T}{v^Tv}x.
\]

The matrix:

\[
\frac{vv^T}{v^Tv}
\]

is the orthogonal projection matrix onto the one-dimensional subspace spanned by \(v\).

### Orthogonal Component in the Hyperplane

Subtracting the projection onto \(v\) removes the normal component:

\[
x - \frac{vv^T}{v^Tv}x
= \left(I-\frac{vv^T}{v^Tv}\right)x.
\]

This gives the component of \(x\) lying in the hyperplane.

In the lecture's geometry, this hyperplane component is still not the reflected point. It is only the projection of \(x\) onto the mirror hyperplane. The reflection keeps this hyperplane component and flips the normal component to the other side.

### Reflection Formula

For the reflection itself, one must go twice the normal projection distance in the opposite direction. Thus:

\[
x_{\text{reflected}}
= x - 2\frac{vv^T}{v^Tv}x.
\]

So the reflection matrix is:

\[
R = I - 2\frac{vv^T}{v^Tv}.
\]

If \(v\) is unit norm, \(v^Tv=1\), and:

\[
R = I - 2vv^T.
\]

The instructor remarked that this was essentially one of the homework problems and that he had "sort of solved it" in lecture.

## Application: Rigid Motion

Real orthogonal matrices appear naturally in rigid motion, especially in mechanical engineering and computer vision.

The instructor remarked that modern deep networks may hide many of these details in applications, but the underlying geometry is still useful background.

A rigid object changes position and orientation but does not change shape. For example, a triangle in two-dimensional space may move and rotate, but its side lengths and internal geometry remain unchanged.

Rigid motion can be written as:

\[
b = Qa + t.
\]

Here:

- \(a\) is a point before motion.
- \(b\) is the corresponding point after motion.
- \(Q\) is a rotation/orthogonal matrix.
- \(t\) is a translation vector.

This mapping is not linear because of the translation term. It is an affine mapping. If \(t=0\), the mapping would be linear.

Relationship:

- \(Q\) determines the rotation/orientation change.
- \(t\) determines the translation/location change.
- \(Q\) satisfies the real orthogonality constraint \(QQ^T=I\).

Conceptually, the motion can be viewed as rotating the object, for example relative to its center of mass, and then translating the rotated object to its new location.

## Image Registration and Motion Detection

The instructor described image registration:

- Register points on the original object or image.
- Observe the corresponding points after motion.
- Use these correspondences to estimate \(Q\) and \(t\).

Example:

\[
b_1 = Qa_1 + t,
\]

\[
b_2 = Qa_2 + t,
\]

and so on for \(m\) registered points.

The motion detection problem is to determine \(Q\) and \(t\) from the observed point correspondences.

Because of noise and imperfect registration, the equations may not have an exact solution. Then one solves a least squares version of the problem.

## Matrix Form of Registered Point Equations

Collect the original points as columns of a matrix:

\[
A = [a_1\ a_2\ \cdots\ a_m],
\]

and the moved points as:

\[
B = [b_1\ b_2\ \cdots\ b_m].
\]

Then:

\[
B = QA + t\mathbf{1}^T.
\]

Here \(A,B\in \mathbb R^{d\times m}\), \(Q\in \mathbb R^{d\times d}\), \(t\in\mathbb R^d\), and \(\mathbf{1}\in\mathbb R^m\). The vector \(\mathbf{1}\) is a column vector of ones, so \(\mathbf{1}^T\) is a row vector. Multiplying \(t\) by \(\mathbf{1}^T\) replicates the translation vector \(t\) across all columns.

### Exam Warning About Broadcasting

The instructor warned that MATLAB may allow writing something like:

\[
B = QA + t
\]

and automatically replicate \(t\) across columns through broadcasting.

This is acceptable in MATLAB programming behavior but not acceptable in the course's mathematical notation or on the exam. In EE 545 notation, the replicated translation must be written explicitly:

\[
B = QA + t\mathbf{1}^T.
\]

## Three-Dimensional Motion Parameters

If the registered points are three-dimensional:

- \(Q\) is \(3\times 3\), so it has 9 entries.
- \(t\) is \(3\times 1\), so it has 3 entries.
- Together there are 12 scalar unknowns.

The orthogonality constraint means those 9 entries of \(Q\) are not freely independent in the final rotation estimate, but the instructor counted the raw scalar quantities before emphasizing the constraint.

More observations generally improve the quality of the estimate, but the quality of the point registration is critical.

The instructor also mentioned projective geometry: in images, two-dimensional measurements often come from projections of a three-dimensional world. For the lecture discussion, this complication was set aside by assuming the relevant three-dimensional coordinates are known.

## Orthogonality Constraints in Estimation

The motion estimation problem is not just an unconstrained least squares problem, because \(Q\) should satisfy:

\[
QQ^T=I.
\]

If the point correspondences are perfect, solving without explicitly imposing the constraint may still produce an orthogonal \(Q\).

If the data are noisy, the constraint is useful:

- It encodes the knowledge that \(Q\) is a rotation/orthogonal matrix.
- It can reduce the effect of noise.

One practical approach:

1. Ignore the orthogonality constraint and solve for \(Q\) and \(t\).
2. The resulting \(Q\) may not be exactly orthogonal.
3. Project that \(Q\) to the closest real orthogonal matrix.

The instructor said better methods also exist. One can formulate the estimation as an optimization problem and impose the orthogonality constraint throughout the iterative updates.

## Closest Orthogonal Matrix Problem

The lecture introduced the problem:

Given a square matrix \(Z\) that is not orthogonal, what is the closest orthogonal matrix to \(Z\)?

This raises the question: what does "closest" mean for matrices?

For vectors, distance is already defined through norms. For matrices, the course will extend vector distance concepts to matrix norms.

## Frobenius Norm

The Frobenius norm is the matrix analogue of the Euclidean norm.

For a vector, the Euclidean norm is:

\[
\|x\|_2 = \sqrt{\sum_i |x_i|^2}.
\]

For a matrix, the Frobenius norm is:

\[
\|A\|_F = \sqrt{\sum_{i,j} |a_{ij}|^2}.
\]

That is:

- Take the absolute square of every matrix entry.
- Sum them.
- Take the square root.

The closest orthogonal matrix problem can then be posed as minimizing an error such as:

\[
\|Z-Q\|
\]

over orthogonal \(Q\), with the particular answer depending on the chosen matrix norm.

The instructor noted:

- The problem is hard in general.
- For some special norms, it becomes easy.
- Singular value decomposition will be used later to solve such problems.

## Orthogonality Constraints in Machine Learning

The instructor briefly mentioned that orthogonality constraints appear in modern machine learning as well.

Examples and remarks:

- Some methods impose orthogonality constraints on matrices during optimization.
- There are applications involving special directions in gradient search.
- The instructor mentioned "Moo iterations" or a similar term in the transcript; the exact reference was unclear, but the point was that orthogonal matrices appear in machine learning optimization contexts.

## Returning to Energy-Preserving Systems

The lecture returned to the signal/vector interpretation.

A vector can be viewed as a signal. If:

\[
y=Ux
\]

with \(U\) unitary, then:

\[
\sum_i |y_i|^2 = \sum_i |x_i|^2.
\]

So the input signal energy equals the output signal energy.

## Fourier Transform as a Linear Transformation

The discrete Fourier transform can be written as a matrix multiplication:

\[
X = Fx.
\]

Here:

- \(x\) is a finite-duration discrete-time signal.
- \(X\) is its discrete Fourier transform.
- \(F\) is the Fourier transform matrix.

The Fourier transform is therefore a linear transformation of special form.

With the standard DFT convention discussed in the lecture, for \(k=0,\dots,N-1\):

\[
X[k] = \sum_{n=0}^{N-1} x[n]e^{-j2\pi kn/N}.
\]

So each Fourier coefficient is one row of \(F\) applied to the signal vector \(x\).

## Parseval Relationship and Scaling

The instructor connected this to Parseval's identity.

If \(F\) were unitary, then energy in the time domain and energy in the Fourier domain would match directly:

\[
\|X\|_2^2 = \|x\|_2^2.
\]

However, the common definition used in standard signal processing books, such as Oppenheim and Schafer, does not make the DFT matrix unitary. It gives a scaled unitary transformation.

In that convention, the inverse Fourier transform includes a factor \(1/n\). This scaling appears because the Fourier matrix has orthogonal but not orthonormal rows and columns.

Equivalently, under this convention:

\[
\|X\|_2^2 = N\|x\|_2^2,
\]

so Parseval's relation is written as:

\[
\sum_{n=0}^{N-1}|x[n]|^2
= \frac{1}{N}\sum_{k=0}^{N-1}|X[k]|^2.
\]

The \(1/N\) factor is exactly the scaling effect the instructor pointed to.

## DFT Matrix Rows as Complex Exponentials

The DFT coefficient \(X[k]\) is computed as an inner product of the signal \(x\) with a complex exponential sequence.

The minus sign in the DFT exponential appears because the complex exponential basis vector is conjugated in the inner product.

For example, if \(w_k[n]=e^{j2\pi kn/N}\), then:

\[
\langle x,w_k\rangle = w_k^*x
= \sum_{n=0}^{N-1}x[n]e^{-j2\pi kn/N}.
\]

Thus:

- Each row of the DFT matrix is the conjugate transpose of a complex exponential signal.
- Multiplying \(F\) by \(x\) takes inner products of \(x\) with these complex exponentials.
- This is like projecting \(x\) onto complex exponentials, except the normalization is delayed to the inverse transform.

## DFT Matrix Is Orthogonal but Not Orthonormal Under the Standard Scaling

The DFT matrix has orthogonal rows and columns, but the rows and columns do not have norm \(1\). Instead, each row/column has norm:

\[
\sqrt n.
\]

Therefore:

\[
FF^* = nI.
\]

The matrix is not unitary because a unitary matrix would satisfy:

\[
FF^* = I.
\]

Consequently:

\[
F^{-1} = \frac{1}{n}F^*.
\]

This explains the \(1/n\) factor in the inverse DFT.

It also explains the \(1/n\) factor in the Parseval relation under that convention: the DFT matrix is a scaled unitary matrix rather than a unitary matrix.

## Preview of Next Topics

The lecture will continue with unitary matrices next.

Then it will move to Hermitian matrices, which belong to the same broader family as unitary matrices and are also very important. Later topics will include positive semidefinite matrices.

## Instructor Remark About Homework and AI

The instructor closed with a learning warning about homework.

The main concern is not framed as academic honesty, but as learning:

- Students learn the material by solving problems themselves.
- Understanding a provided solution is not the same as understanding the concepts.
- Real understanding comes from struggling through and solving the problem independently.
- Students should not use AI to solve homework problems for them.
- It is acceptable to ask AI conceptual questions, but using it to bypass the problem-solving process undermines the purpose of the homework.

The instructor specifically warned that it is tempting to upload a screenshot of a problem to an AI system and ask for the answer, but students should spend substantial time thinking through the problem themselves.

## Exam-Relevant Items Explicitly Flagged in the Transcript

The transcript explicitly marked the following as likely exam topics or exam notes:

- Unitary and orthogonal matrices.
- Eigenvalues of unitary matrices.
- Orthogonal eigenspaces for distinct eigenvalues.
- Every square matrix can be triangularized, and the triangularizing matrix can be chosen orthogonal/unitary.
- Orthogonal projection onto a subspace using an orthonormal basis matrix.
- Definition of unitary matrices and \(U^{-1}=U^*\).
- Unitary matrices preserve Euclidean norm and energy.
- LTI systems require convolution/shift/Toeplitz structure; a unitary matrix alone is not necessarily time invariant.
- Coordinates in an orthonormal basis are found by inner products/projections.
- Projection onto non-orthogonal basis vectors cannot be done independently.
- Two-dimensional rotation matrices are real orthogonal.
- Reflection across a hyperplane uses projection onto the normal direction.
- The reflection formula \(I-2vv^T/(v^Tv)\) was essentially a homework problem.
- In exam notation, do not rely on MATLAB broadcasting; write \(B=QA+t\mathbf{1}^T\).
- Under the standard DFT scaling used in Oppenheim/Schafer-style notation, \(F\) is scaled unitary rather than unitary, \(FF^*=nI\), \(F^{-1}=\frac{1}{n}F^*\), and Parseval has a \(1/n\) factor.
- Homework should be solved independently for learning; AI may be used for conceptual questions but not as a shortcut to solutions.

## Source and Coverage Note

Source: `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture10_corrected.md`.

Coverage: These notes follow only Lecture 10 and preserve the chronological development from matrix factorizations and projection review through unitary matrices, eigenvalue properties, orthonormal coordinates, real orthogonal rotations/reflections, rigid motion, closest orthogonal matrix motivation, Frobenius norm, Fourier/Parseval scaling, and the closing homework/AI learning remark. No other lecture transcript was processed.
