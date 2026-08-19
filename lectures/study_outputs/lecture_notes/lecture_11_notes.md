# Lecture 11 Notes

## 1. Context From Previous Lectures

The lecture begins by tying together several earlier themes in matrix analysis and systems of linear equations.

### Matrix Rank and Matrix Shape

- The rank of a matrix is the dimension of both its column space and row space.
- Earlier conclusions depended on matrix shape:
  - tall matrices,
  - square matrices,
  - fat matrices.
- These shape-based cases lead to different conclusions about linear systems and matrix mappings.

### Solving Linear Systems Through "Simple Problems"

The instructor frames the methods for solving systems of linear equations under one broad strategy:

- Some systems are easy to solve when the coefficient matrix is one of a few simple types:
  - diagonal,
  - triangular,
  - orthogonal/unitary.
- The general strategy is to convert a difficult arbitrary system into a sequence of such simple systems.
- Matrix factorization is the algebraic version of this idea:
  - instead of solving directly with an arbitrary matrix \(A\),
  - write \(A\) as a product of simpler matrices,
  - then solve through the corresponding simpler steps.

This is the organizing principle behind later decompositions such as Schur decomposition and singular value decomposition.

### Basis Change and Diagonalization

For a change of basis, the same linear transformation is represented by

\[
T^{-1}AT.
\]

This representation was previously analyzed through eigenvalues and eigenvectors.

Important conclusion:

- Not every matrix is diagonalizable.
- Some matrices admit a basis in which the transformation is diagonal.
- Some matrices do not.
- Lecture 11 introduces a weaker but universal result:
  - every square matrix can be triangularized by a basis change.

This leads into Schur's theorem.

### Orthogonality, Inner Products, and Projections

Before this lecture, the course extended the real Euclidean inner product to complex inner products.

Previously discussed ideas include:

- projecting one vector onto another vector,
- projecting a vector onto a subspace,
- orthogonal projection matrices,
- describing a projection by choosing a basis for the target subspace.

For projection onto a subspace:

- If an orthonormal basis is chosen, the projection matrix has a simpler form.
- If an arbitrary basis is chosen, the projection matrix becomes more involved.
- The instructor said this more general formula was not derived at that time, but will return later in least squares.
- The formula can be derived independently.

## 2. Review of Unitary Matrices

[LIKELY EXAM TOPIC]

A unitary matrix \(U\) is a complex matrix whose inverse equals its conjugate transpose:

\[
U^{-1} = U^*.
\]

Here \(U^*\) denotes the Hermitian transpose, i.e. transpose plus complex conjugation.

### Why Unitary Systems Are Simple

Unitary systems are one of the "simple" classes of linear systems because solving

\[
Ux = b
\]

is easy:

\[
x = U^{-1}b = U^*b.
\]

The inverse is obtained directly by conjugate transposition.

### Orthonormal Columns and Rows

For an \(n \times n\) unitary matrix:

- the columns form an orthonormal basis for \(\mathbb{C}^n\),
- the rows also form an orthonormal basis for \(\mathbb{C}^n\).

In the real case, a real unitary matrix is called a real orthogonal matrix. Its rows and columns form orthonormal bases for \(\mathbb{R}^n\).

### Properties Reviewed

Unitary matrices preserve:

- Euclidean norm,
- inner product.

Consequences:

- eigenvalues of a unitary matrix lie on the complex unit circle,
- the determinant of a unitary matrix also lies on the unit circle,
- eigenvectors corresponding to distinct eigenvalues are orthogonal.

Equivalently, eigenspaces associated with distinct eigenvalues are orthogonal.

The instructor emphasized that this last eigenspace property will later be used to define a larger class of matrices, namely normal matrices.

## 3. Applications of Unitary Matrices

### Rigid Motion and Rotation

The most basic application of unitary or orthogonal matrices is rigid motion, especially rotation.

Because unitary matrices preserve norm and inner product, they preserve geometric structure such as lengths and angles.

### Lossless Linear Systems

Another application is modeling lossless linear systems or lossless linear transformations.

"Lossless" means energy-preserving.

Energy is defined using the Euclidean norm, often as the squared norm:

\[
\|x\|^2.
\]

If a system is represented by a unitary matrix, then the input and output have the same Euclidean norm, hence the same energy.

## 4. LTI Systems, Toeplitz Matrices, and All-Pass Systems

The instructor then connects unitary matrices to linear time-invariant systems.

### Linear Time-Invariant Systems

An LTI system is a linear time-invariant system.

The output sequence can be represented as an infinite vector, and each output sample is a weighted combination of input samples.

For a causal discrete-time system:

\[
y_0 = h_0x_0 + h_1x_{-1} + h_2x_{-2} + \cdots.
\]

[EXAM NOTE]

Causality means the output at a given time depends only on:

- the input at that same time,
- previous inputs.

It does not depend on future inputs.

For example:

- \(y_0\) depends on \(x_0, x_{-1}, x_{-2}, \ldots\),
- \(y_1\) depends on \(x_1, x_0, x_{-1}, \ldots\).

The instructor's point was not only the single equation for \(y_0\), but the repeated row pattern:

\[
y_1 = h_0x_1 + h_1x_0 + h_2x_{-1}+\cdots,
\]

and similarly for every later time. The same weights are reused; only the input indices shift.

### Time Invariance

Time invariance means the formula relating output to current and past inputs does not change over time.

For example:

- \(y_0\) relates to \(x_0\) through coefficient \(h_0\),
- \(y_1\) relates to \(x_1\) through the same coefficient \(h_0\),
- the same coefficients \(h_0,h_1,h_2,\ldots\) appear at each time, shifted in position.

If the coefficients changed from row to row, the system could still be linear, because each output would still be a weighted combination of inputs, but it would not be time-invariant.

### Matrix Structure

For a causal LTI system, the input-output relation can be written as a matrix-vector product.

The matrix has two important structural properties:

- lower triangular due to causality,
- shifted rows due to time invariance.

A matrix whose diagonals are constant is called a Toeplitz matrix.

Therefore, a causal LTI system is represented by a lower triangular Toeplitz matrix.

A one-sided finite display of the same structure is

\[
\begin{bmatrix}
y_0\\
y_1\\
y_2\\
\vdots
\end{bmatrix}
=
\begin{bmatrix}
h_0 & 0 & 0 & \cdots\\
h_1 & h_0 & 0 & \cdots\\
h_2 & h_1 & h_0 & \cdots\\
\vdots & \vdots & \vdots & \ddots
\end{bmatrix}
\begin{bmatrix}
x_0\\
x_1\\
x_2\\
\vdots
\end{bmatrix}.
\]

The lower-triangular zeros encode causality, and the constant diagonals encode time invariance.

### Convolution

The general input-output formula for a causal LTI system is

\[
y_n = \sum_{k=0}^{\infty} h_k x_{n-k}.
\]

This is the convolution operation.

The coefficients \(h_k\) are the impulse response of the system.

The infinite matrix representation of this convolution operation is called a convolution matrix.

### Homework Connection: Finite and Circular Convolution

[EXAM NOTE]

In the current homework, the instructor said students will examine finite-dimensional sequences rather than infinite-dimensional discrete-time sequences. This gives a finite convolution matrix.

[EXAM NOTE]

The homework uses circular convolution. In that case:

- the convolution matrix is not Toeplitz,
- it is circulant.

In a circulant matrix, rows are rotated rather than simply shifted:

- an entry shifted past the right end comes back to the beginning.

The instructor noted this as a homework topic and avoided giving the full spoiler.

### Losslessness for LTI Systems

The lower triangular Toeplitz structure comes from causality and time invariance.

Losslessness adds another property:

- in the complex case, the convolution matrix should be unitary,
- in the real-coefficient or real-signal case, it should be real orthogonal.

For a unitary convolution matrix:

\[
H^*H = I.
\]

In terms of the impulse response, this corresponds to a convolution relation involving \(h\) and the conjugated time-reversed impulse response, giving a Kronecker delta:

\[
\sum_k h_k \overline{h_{k-m}} = \delta[m]
\]

or, equivalently, the impulse response convolved with its conjugate-reversed version gives the delta function. The instructor left this derivation for students to inspect.

### Fourier-Domain Interpretation

The Fourier transform turns convolution into multiplication. The instructor emphasized this as one reason Fourier analysis is so useful.

The frequency response is the Fourier transform of the impulse response \(h_k\):

If

\[
H(e^{j\omega})
\]

is the Fourier transform of the impulse response, then the lossless/unitary condition implies

\[
|H(e^{j\omega})|^2 = 1
\]

for all frequencies.

Thus

\[
|H(e^{j\omega})| = 1
\]

for all \(\omega\).

Interpretation:

- a lossless LTI system passes every frequency with magnitude one,
- it does not attenuate any frequency,
- it does not amplify any frequency.

Such a system is called an all-pass system.

Relationship:

- arbitrary unitary matrices represent lossless finite-dimensional linear transformations,
- when the linear transformation is also time-invariant and has a frequency response, the unitary property appears as the all-pass property.
- the impulse-response orthogonality condition transforms into \(H(e^{j\omega})\overline{H(e^{j\omega})}=1\), which is exactly the magnitude-one condition.

## 5. Schur Theorem and Unitary Triangularization

[LIKELY EXAM TOPIC]

The next main theorem is Schur's theorem.

The instructor describes it as a useful consolation after the failure of universal diagonalization.

### Motivation

Previously:

- the class tried to find a basis that makes a given square matrix diagonal,
- this is possible only for diagonalizable matrices,
- not every matrix is diagonalizable.

Schur's theorem says something weaker but always possible for square matrices:

- every square matrix can be represented by a triangular matrix in a suitable orthonormal basis.
- this lecture's theorem is explicitly for square matrices; rectangular/non-square decompositions are deferred to later material, especially the SVD discussion.

### Statement

For every square matrix \(A\), there exists a unitary matrix \(U\) such that

\[
U^*AU = T,
\]

where \(T\) is upper triangular.

Equivalently,

\[
A = UTU^*.
\]

This is the Schur decomposition.

Because \(U^{-1}=U^*\), the expression \(U^*AU\) is a similarity transformation:

\[
U^{-1}AU.
\]

Interpretation:

- Schur's theorem gives a basis change,
- the new basis can be chosen orthonormal,
- in that basis the linear transformation is triangular.

The instructor's plain-language summary:

- all square matrices are unitarily triangularizable.

A lower triangular version is also possible.

### Relation to SVD

The instructor compares the theorem to singular value decomposition.

Schur decomposition:

\[
A = UTU^*
\]

uses the same unitary basis on the input and output side because \(A\) is square and the domain/codomain dimensions match.

SVD, to be discussed later, has the spirit of

\[
A = U\Sigma V^*
\]

and can handle non-square matrices. It uses different bases for input and output spaces.

Thus:

- Schur: same unitary basis on both sides, triangular middle factor, square matrices.
- SVD: generally different unitary bases on each side, diagonal/singular-value middle factor, can handle rectangular matrices.

## 6. Proof Idea for Schur Theorem

The proof is constructive and iterative.

### Step 1: Choose a Unit-Norm Eigenvector

Start with an eigenvalue-eigenvector pair of \(A\):

\[
Au_1 = \lambda_1 u_1.
\]

Choose \(u_1\) with unit norm:

\[
\|u_1\| = 1.
\]

This is allowed because any nonzero eigenvector can be normalized.

### Step 2: Extend to an Orthonormal Basis

Extend \(u_1\) to an arbitrary orthonormal basis:

\[
u_1, u_2', u_3', \ldots, u_n'.
\]

The vectors \(u_2',\ldots,u_n'\):

- are not assumed to be eigenvectors,
- are chosen only to complete an orthonormal basis,
- are orthogonal to \(u_1\),
- have unit norm.

There are generally infinitely many ways to choose them.

Place these vectors into the columns of a matrix:

\[
U_1 =
\begin{bmatrix}
u_1 & u_2' & \cdots & u_n'
\end{bmatrix}.
\]

Because its columns are orthonormal, \(U_1\) is unitary:

\[
U_1^*U_1 = I.
\]

Instructor remark:

- \(U_1\) is not yet the final \(U\) from Schur's theorem.
- It is an intermediate unitary matrix.

### Step 3: Apply a Similarity Transformation

Consider

\[
U_1^*AU_1.
\]

This is a basis change. It is the first iteration of the triangularization process.

Partition the right multiplication by columns:

\[
AU_1 =
\begin{bmatrix}
Au_1 & Au_2' & \cdots & Au_n'
\end{bmatrix}.
\]

Since \(u_1\) is an eigenvector,

\[
Au_1 = \lambda_1 u_1.
\]

Therefore, the first column of \(AU_1\) is \(\lambda_1 u_1\).

For the other columns \(Au_2',\ldots,Au_n'\), no eigenvector simplification is available. Those basis vectors were chosen only to complete an orthonormal basis, so their images can be collected into unspecified entries.

Now multiply on the left by \(U_1^*\). The entries in the first column are inner products between basis vectors and \(\lambda_1u_1\):

- first entry:

\[
u_1^*(\lambda_1u_1)=\lambda_1 u_1^*u_1=\lambda_1,
\]

because \(\|u_1\|=1\);

- lower entries:

\[
(u_j')^*(\lambda_1u_1)=0
\]

because \(u_j'\) is orthogonal to \(u_1\).

So the transformed matrix has the block form

\[
U_1^*AU_1
=
\begin{bmatrix}
\lambda_1 & q^* \\
0 & A_2
\end{bmatrix}.
\]

Here:

- \(q^*\) represents entries not controlled in the first row,
- \(A_2\) is an \((n-1)\times(n-1)\) submatrix,
- the first column already has the upper-triangular pattern.

Instructor wording:

- this first step does not finish triangularization,
- it makes progress by fixing the first column,
- subsequent steps will fix the second column, then the third, and so on.

## 7. Eigenvalues of the Submatrix \(A_2\)

[EXAM NOTE]

The instructor reminded the class that \(U_1^*AU_1\) is similar to \(A\), so it has the same eigenvalues as \(A\).

Proof:

\[
\det(\lambda I - U_1^*AU_1)
\]

can be rewritten using \(I=U_1^*U_1\):

\[
\det(U_1^*(\lambda I-A)U_1).
\]

Then

\[
\det(U_1^*)\det(\lambda I-A)\det(U_1).
\]

For a unitary matrix, \(\det(U_1^*)\det(U_1)=1\), so this equals

\[
\det(\lambda I-A).
\]

Therefore \(A\) and \(U_1^*AU_1\) share the same characteristic polynomial and eigenvalues.

Now use the block form:

\[
U_1^*AU_1
=
\begin{bmatrix}
\lambda_1 & q^* \\
0 & A_2
\end{bmatrix}.
\]

Then

\[
\lambda I - U_1^*AU_1
=
\begin{bmatrix}
\lambda-\lambda_1 & * \\
0 & \lambda I-A_2
\end{bmatrix}.
\]

The determinant of this block upper triangular matrix is

\[
(\lambda-\lambda_1)\det(\lambda I-A_2).
\]

Thus the characteristic polynomial of \(A\) factors as

\[
\det(\lambda I-A)
=
(\lambda-\lambda_1)\det(\lambda I-A_2).
\]

Conclusion:

- the eigenvalues of \(A_2\) are the remaining eigenvalues of \(A\), counting multiplicity,
- the eigenspaces are not the same, because \(A_2\) acts on an \((n-1)\)-dimensional space.

## 8. Continuing the Schur Iteration

The first step gives

\[
U_1^*AU_1
=
\begin{bmatrix}
\lambda_1 & q^* \\
0 & A_2
\end{bmatrix}.
\]

Equivalently,

\[
A
=
U_1
\begin{bmatrix}
\lambda_1 & q^* \\
0 & A_2
\end{bmatrix}
U_1^*.
\]

Now apply the same procedure to \(A_2\).

Since \(A_2\) is \((n-1)\times(n-1)\), choose a unitary matrix \(U_2\) such that

\[
U_2^*A_2U_2
=
\begin{bmatrix}
\lambda_2 & * \\
0 & A_3
\end{bmatrix}.
\]

Insert this into the block matrix by using the block diagonal unitary matrix

\[
\begin{bmatrix}
1 & 0 \\
0 & U_2
\end{bmatrix}.
\]

Concretely, the second step applies

\[
\begin{bmatrix}
1 & 0\\
0 & U_2^*
\end{bmatrix}
\begin{bmatrix}
\lambda_1 & q^*\\
0 & A_2
\end{bmatrix}
\begin{bmatrix}
1 & 0\\
0 & U_2
\end{bmatrix}
=
\begin{bmatrix}
\lambda_1 & q^*U_2\\
0 & U_2^*A_2U_2
\end{bmatrix}.
\]

Since \(U_2^*A_2U_2\) has first column \((\lambda_2,0,\ldots,0)^T\), the second column of the overall matrix now also satisfies the upper-triangular pattern.

This block diagonal matrix is unitary because:

- \(1\) is a \(1\times1\) unitary block,
- \(U_2\) is unitary,
- multiplying the block diagonal matrix by its conjugate transpose gives the identity.

The product of unitary matrices is also unitary.

After the second iteration:

- the first two columns have the upper-triangular structure,
- the remaining lower-right block is \(A_3\), now \((n-2)\times(n-2)\),
- \(A_3\) has the remaining eigenvalues of \(A\).

Continue this process.

After enough iterations, the whole matrix becomes upper triangular:

\[
U^*AU = T.
\]

The instructor said one can think of this as working column by column. In practice, after \(n-1\) main reductions, the final remaining scalar entry is already determined, so the process terminates.

### Handling Eigenvalue Multiplicity

In response to a question, the instructor noted that algebraic or geometric multiplicity does not cause difficulty in this construction.

If \(\lambda_1\) has a multidimensional eigenspace:

- choose one unit eigenvector \(u_1\) from that eigenspace,
- complete it to an orthonormal basis,
- the same eigenvalue may still appear in \(A_2\).

The method does not require distinct eigenvalues or one-dimensional eigenspaces.

### Conceptual Meaning

Schur decomposition achieves the course's main factorization goal:

\[
A = U T U^*.
\]

This writes any square matrix as a product of simple matrices:

- a unitary matrix,
- a triangular matrix,
- another unitary matrix, specifically the conjugate transpose of the first.

This is a major example of reducing arbitrary matrices to simple matrix factors.

## 9. Transition to Hermitian and Normal Matrices

The next topic is broader than unitary matrices.

The instructor introduced a bigger family called normal matrices.

Important big-picture relationships:

- unitary matrices are normal,
- Hermitian matrices are normal,
- normal matrices have orthogonal eigenspaces corresponding to distinct eigenvalues.

The lecture has not yet fully developed normal matrices, but the instructor used them to place unitary and Hermitian matrices in context.

### Intersection of Unitary and Hermitian Matrices

The intersection of unitary and Hermitian matrices is nontrivial.

Example:

\[
I
\]

is both unitary and Hermitian.

Why:

- \(I^{-1}=I=I^*\), so \(I\) is unitary,
- \(I^*=I\), so \(I\) is Hermitian.

The instructor said the class will return to the larger picture and further partition Hermitian matrices later.

## 10. Hermitian Matrices

[LIKELY EXAM TOPIC]

A Hermitian matrix \(A\) satisfies

\[
A^* = A.
\]

That is, the conjugate transpose of the matrix equals the matrix itself.

### Contrast With Unitary Matrices

For a unitary matrix:

\[
A^* = A^{-1}.
\]

For a Hermitian matrix:

\[
A^* = A.
\]

Thus Hermitian matrices are not "simple" in the same linear-system-solving sense as unitary matrices, because taking the conjugate transpose does not directly give the inverse. However, Hermitian matrices have many important structural properties and many applications.

[EXAM NOTE]

Hermitian matrices are very important. The instructor specifically mentioned later applications in:

- optimization,
- stochastic processes,
- random vectors.

## 11. Entrywise Structure of Hermitian Matrices

For a Hermitian matrix \(A\), the entries satisfy

\[
a_{ij} = \overline{a_{ji}}.
\]

Equivalently:

- across the diagonal, entries are conjugates of each other,
- not necessarily equal to each other.

Example:

If

\[
a_{21}=1+i,
\]

then

\[
a_{12}=1-i.
\]

### Real Symmetric Matrices as a Special Case

If the matrix is real, conjugation does nothing.

Then the Hermitian condition becomes

\[
a_{ij}=a_{ji}.
\]

So a real Hermitian matrix is exactly a real symmetric matrix.

Example form:

\[
\begin{bmatrix}
1 & 5 \\
5 & 2
\end{bmatrix}
\]

is real symmetric, hence Hermitian.

### Diagonal Entries Are Real

For diagonal entries:

\[
a_{ii} = \overline{a_{ii}}.
\]

A number equal to its own complex conjugate must be real.

Therefore, every diagonal entry of a Hermitian matrix is real.

## 12. Quadratic Forms From Hermitian Matrices

[LIKELY EXAM TOPIC]

The instructor emphasized that a major reason Hermitian matrices are important is that they define real-valued quadratic functions of complex vectors.

For a complex vector \(x\in\mathbb{C}^n\), consider

\[
x^*Ax.
\]

Here \(x^*x\) is only the special norm-squared case obtained when \(A=I\). The quadratic form discussed in this section is \(x^*Ax\).

Dimensions:

- \(x^*\) is \(1\times n\),
- \(A\) is \(n\times n\),
- \(x\) is \(n\times1\).

Therefore

\[
x^*Ax
\]

is a \(1\times1\) scalar.

For a general complex matrix \(A\), this scalar may be complex.

If \(A\) is Hermitian, then \(x^*Ax\) is real for every \(x\).

### Two-Dimensional Example

Let

\[
x =
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
\]

and let

\[
A =
\begin{bmatrix}
a_{11} & a_{12}\\
\overline{a_{12}} & a_{22}
\end{bmatrix}
\]

be Hermitian.

Then

\[
x^* =
\begin{bmatrix}
\overline{x_1} & \overline{x_2}
\end{bmatrix}.
\]

Expanding,

\[
x^*Ax
=
|x_1|^2a_{11}
+ \overline{x_1}x_2a_{12}
+ \overline{x_2}x_1\overline{a_{12}}
+ |x_2|^2a_{22}.
\]

The two cross terms are conjugates of each other:

\[
\overline{x_1}x_2a_{12}
\quad\text{and}\quad
\overline{x_2}x_1\overline{a_{12}}.
\]

Adding a complex number and its conjugate gives twice its real part. Thus

\[
x^*Ax
=
|x_1|^2a_{11}
+ |x_2|^2a_{22}
+ 2\operatorname{Re}(\overline{x_1}x_2a_{12}).
\]

Each term is real:

- \(|x_1|^2\) and \(|x_2|^2\) are real,
- \(a_{11}\) and \(a_{22}\) are real because Hermitian diagonal entries are real,
- the cross terms combine into a real number.

The instructor used this example to show why the expression is called a quadratic form:

- it contains squared magnitudes of vector components,
- it contains products of vector components and conjugates.

## 13. General Proof That \(x^*Ax\) Is Real for Hermitian \(A\)

The elementwise expansion is not necessary. The property follows directly from conjugate transposition.

Let

\[
z=x^*Ax.
\]

This is a scalar. Its conjugate is

\[
\overline{z} = z^*.
\]

Now compute:

\[
(x^*Ax)^*
= x^*A^*x.
\]

If \(A\) is Hermitian, then

\[
A^* = A.
\]

Therefore

\[
(x^*Ax)^*
= x^*Ax.
\]

So the scalar equals its own conjugate. Hence it is real.

Conclusion:

- Hermitian matrices define real-valued quadratic forms on complex vector spaces.

## 14. Quadratic Functions and Optimization

The instructor connected Hermitian quadratic forms to optimization.

Optimization often represents nonlinear functions locally by quadratic approximations. This is the idea behind Newton-type methods and related approaches.

For real multivariable functions, if \(x\in\mathbb{R}^n\), then a quadratic form has the form

\[
x^TAx,
\]

where \(A\) is real symmetric, i.e. the real version of Hermitian.

In two variables, such expressions include terms like

\[
a_{11}x_1^2 + 2a_{12}x_1x_2 + a_{22}x_2^2.
\]

The instructor noted that this is the untranslated version. A more general quadratic function can include:

- translation in \(x\), such as \(x-x_0\),
- vertical translation by adding a scalar \(b\).

A typical general form is conceptually like

\[
(x-x_0)^TA(x-x_0)+b.
\]

The untranslated form has its reference point at the origin and no vertical offset. The translated form moves the center/reference point to \(x_0\) and shifts the function value by \(b\). Whether this gives a minimum, maximum, or mixed saddle-like shape depends on the matrix \(A\), which motivates classifying Hermitian matrices by eigenvalue signs.

[EXAM NOTE]

Quadratic functions are important because a general nonlinear surface can be approximated near a point \(x_0\) by a quadratic function.

The Hermitian or symmetric matrix determines the shape of the quadratic function.

In one dimension, a quadratic is simply:

- parabola up,
- or parabola down.

In multiple dimensions, the shape can be mixed:

- upward curvature in some directions,
- downward curvature in other directions.

This motivates classifying Hermitian matrices by eigenvalue signs, which the instructor said will be discussed later.

## 15. Eigenvalues of Hermitian Matrices Are Real

The next theorem:

For a Hermitian matrix \(A\), every eigenvalue is real.

Hermitian matrices may have complex entries, but their eigenvalues lie on the real line.

### Proof

Let \(x\neq0\) be an eigenvector of \(A\) with eigenvalue \(\lambda\):

\[
Ax=\lambda x.
\]

Multiply on the left by \(x^*\):

\[
x^*Ax = x^*(\lambda x).
\]

Since \(\lambda\) is a scalar,

\[
x^*Ax = \lambda x^*x.
\]

Now:

- \(x^*Ax\) is real because \(A\) is Hermitian,
- \(x^*x = \|x\|^2\) is real and strictly positive because \(x\neq0\).

Therefore

\[
\lambda = \frac{x^*Ax}{x^*x}
\]

is a real number.

### Comparison With Unitary Matrices

For unitary matrices:

- eigenvalues lie on the complex unit circle.

For Hermitian matrices:

- eigenvalues lie on the real line.

The instructor related this to normal matrices:

- unitary and Hermitian matrices are both normal,
- among normal matrices, unitary matrices are characterized by eigenvalues on the unit circle,
- among normal matrices, Hermitian matrices are characterized by eigenvalues on the real line.

This full normal-matrix picture was flagged as a later topic.

## 16. Orthogonality of Hermitian Eigenspaces

The final property shown is that eigenvectors of a Hermitian matrix corresponding to distinct eigenvalues are orthogonal.

This was already shown earlier for unitary matrices, and the instructor emphasized it is part of the larger normal-matrix pattern.

### Statement

Let

\[
Ax=\lambda x,
\]

and

\[
Ay=\mu y,
\]

where \(\lambda\neq\mu\).

If \(A\) is Hermitian, then

\[
y^*x=0.
\]

So \(x\) and \(y\) are orthogonal.

Equivalently:

- eigenspaces corresponding to distinct eigenvalues are orthogonal.

### Proof

Start with

\[
y^*Ax.
\]

Using \(Ax=\lambda x\),

\[
y^*Ax = y^*(\lambda x)=\lambda y^*x.
\]

Now evaluate the same expression another way.

Because \(A\) is Hermitian,

\[
A^*=A.
\]

Also, since

\[
Ay=\mu y,
\]

and Hermitian eigenvalues are real, \(\mu=\overline{\mu}\).

Taking conjugate transposes gives

\[
(Ay)^*=(\mu y)^*
\]

so

\[
y^*A^*=\overline{\mu}\,y^*.
\]

Using \(A^*=A\) and \(\overline{\mu}=\mu\),

\[
y^*A = \mu y^*.
\]

Therefore

\[
y^*Ax = \mu y^*x.
\]

The two expressions for \(y^*Ax\) must be equal:

\[
\lambda y^*x = \mu y^*x.
\]

Thus

\[
(\mu-\lambda)y^*x=0.
\]

Because \(\lambda\neq\mu\), it follows that

\[
y^*x=0.
\]

So the eigenvectors are orthogonal.

## 17. Instructor Remarks and Reading Suggestion

The instructor ended by recommending the book *Matrix Analysis* by Horn and Johnson, noting that the lecture is following it closely while trying to present the material with a more accessible perspective.

The lecture will continue on Tuesday.

## 18. Exam and Homework Cues Collected Chronologically

- [LIKELY EXAM TOPIC] Unitary matrices: definition, inverse as conjugate transpose, orthonormal rows/columns, preservation of norm and inner product, unit-circle eigenvalues, orthogonality of eigenspaces.
- [EXAM NOTE] Causality: output at a time depends only on current and previous inputs.
- [EXAM NOTE] Homework uses finite-dimensional sequences, giving finite convolution matrices.
- [EXAM NOTE] Homework uses circular convolution, giving circulant rather than Toeplitz matrices; rows rotate rather than only shift.
- [LIKELY EXAM TOPIC] Schur factorization theorem: every square matrix is unitarily triangularizable.
- [EXAM NOTE] \(U_1^*AU_1\) is a similarity transformation and has the same eigenvalues as \(A\).
- [LIKELY EXAM TOPIC] Hermitian matrices: definition \(A^*=A\), entrywise conjugate symmetry, real diagonal entries, relation to real symmetric matrices.
- [EXAM NOTE] Hermitian matrices are important for optimization, stochastic processes, and random vectors.
- [LIKELY EXAM TOPIC] Real-valued quadratic forms \(x^*Ax\) for Hermitian \(A\).
- [EXAM NOTE] Quadratic functions are important because nonlinear surfaces are locally approximated by quadratic functions; matrix eigenvalue signs determine multivariable shape.

## Source and Coverage Note

These notes were generated only from `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture11_corrected.md`. They preserve the lecture order and include the stated concepts, definitions, theorem statements, proof ideas, examples, instructor remarks, homework/exam cues, and relationships between unitary, Schur, Hermitian, quadratic-form, LTI, and normal-matrix ideas.
