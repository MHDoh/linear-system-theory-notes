# Lecture 09 Notes

## 1. Review: Factorizations and Simpler Matrix Forms

The lecture opens by returning to the idea that solving many linear algebra
problems is essentially helped by factorizing a matrix \(A\) into simpler
matrices.

Important examples mentioned:

- QR factorization, to be covered later: write \(A = QR\), where \(Q\) is
  orthogonal/unitary and \(R\) is upper triangular.
- LU factorization: write a matrix using lower triangular and upper triangular
  factors. Gaussian elimination is essentially a process of triangularizing a
  matrix into lower and upper triangular structure.
- Permutation matrices appear when row exchanges are needed in elimination.
  The instructor groups them with the "simple" factors and notes that a
  permutation matrix is an orthogonal matrix.
- Diagonal matrices are especially simple, so it is natural to ask when a given
  matrix can be converted into diagonal form.

The main relationship emphasized is:

> If \(A\) can be replaced by a product of simpler matrices, then one difficult
> problem involving \(A\) can often be replaced by a sequence of simpler
> problems.

## 2. Basis Change, Similarity, and Diagonalization

For a square matrix \(A\), the matrix can be interpreted as the representation
of a linear transformation in the standard basis. If the basis is changed to a
new basis collected in an invertible matrix \(T\), the same transformation is
represented by a new matrix

\[
\widetilde A = T^{-1}AT.
\]

This operation is called a similarity transformation.

The central question from the previous lecture was:

> Given a matrix \(A\) that is not diagonal in the standard basis, can we find a
> clever basis \(T\) such that \(T^{-1}AT\) becomes diagonal?

This leads to the classification of square matrices into:

- diagonalizable matrices: there exists an invertible \(T\) such that
  \(T^{-1}AT\) is diagonal;
- non-diagonalizable matrices: no such invertible \(T\) exists.

The instructor stressed that not all matrices are diagonalizable.

## 3. Similar Matrices Preserve Eigenvalues

The instructor asked what \(A\) and its similarity-transformed version
\(\widetilde A = T^{-1}AT\) have in common.

One answer was rank, but the more important answer was:

> Similar matrices have the same eigenvalues.

### Proof Using the Characteristic Polynomial

Start from the characteristic polynomial of \(\widetilde A\):

\[
p_{\widetilde A}(\lambda)
  = \det(\lambda I - \widetilde A).
\]

Substitute \(\widetilde A = T^{-1}AT\):

\[
\det(\lambda I - T^{-1}AT).
\]

Use \(I = T^{-1}T\) to rewrite \(\lambda I\) compatibly:

\[
\lambda I - T^{-1}AT
  = T^{-1}(\lambda I - A)T.
\]

Then

\[
\det(T^{-1}(\lambda I - A)T)
  = \det(T^{-1})\det(\lambda I - A)\det(T).
\]

Since

\[
\det(T^{-1}) = \frac{1}{\det(T)},
\]

the determinant factors cancel:

\[
\det(T^{-1})\det(T) = 1.
\]

Therefore

\[
p_{\widetilde A}(\lambda)
  = \det(\lambda I - A)
  = p_A(\lambda).
\]

So \(A\) and \(\widetilde A\) have the same characteristic polynomial and hence
the same eigenvalues.

## 4. Diagonalization, Triangularization, and SVD Preview

Although not every square matrix can be diagonalized by a similarity
transformation, the instructor stated that every matrix can be triangularized in
an appropriate basis:

\[
T^{-1}AT
\]

can always be made triangular for a suitable invertible \(T\).

The lecture also previews an important contrast:

- Similarity transformations use the same basis for input and output spaces.
- If we allow different bases for the input and output spaces, then a much more
  flexible representation is possible.

In similarity, the same basis-change matrix appears on both sides:
\(T^{-1}AT\). If the input and output bases are allowed to differ, the
representation has different left and right basis changes, for example
\(S^{-1}AT\). That extra freedom is what makes a diagonal representation
available in the SVD setting even when a similarity diagonalization is not
available.

[Likely exam topic] If we are flexible about choosing different bases for input
and output spaces, then a linear transformation can be represented by a diagonal
matrix. This is the idea behind singular value decomposition (SVD), which will
be covered later.

This connects eigenvalues/eigenvectors, characteristic polynomials,
diagonalization, triangularization, and SVD into one larger theme:

> Matrix factorization and basis choice are ways to turn a difficult
> transformation into a simpler one.

## 5. Complex Inner Products and Conjugate Transpose

Before entering orthogonal/unitary matrices, the lecture reviews how Euclidean
inner products extend from real vector spaces to complex vector spaces.

For real vectors, the Euclidean norm is based on expressions like

\[
x^T x.
\]

For complex vectors, using \(x^T x\) is not appropriate because squaring complex
entries can produce complex values. Instead, use the conjugate transpose:

\[
x^*x.
\]

Here \(x^*\) denotes the conjugate transpose, also called the Hermitian
transpose. For a column vector, \(x^*\) is a row vector whose entries are the
complex conjugates of the entries of \(x\).

Instructor notation remark: the star notation is useful because, for scalars,
it reduces to ordinary complex conjugation, while for vectors and matrices it
also includes the transpose operation. Thus a column vector becomes a row vector
with conjugated entries.

The reason for conjugation is that

\[
\overline{x_k}x_k = |x_k|^2,
\]

which is real and nonnegative. This gives the proper squared norm.

### Inner Product Convention

The lecture uses the convention that the second vector is conjugate transposed:

\[
\langle x,y\rangle = y^*x.
\]

With this convention:

- exchanging the two inputs conjugates the result:

  \[
  \langle x,y\rangle = \overline{\langle y,x\rangle};
  \]

- scaling the first input by a complex scalar scales the inner product by the
  same scalar;
- scaling the second input by a complex scalar scales the inner product by the
  conjugate of that scalar.

The real symmetric property of the inner product therefore becomes Hermitian
symmetry in the complex case.

## 6. Orthogonal and Orthonormal Sets

A set \(S\) is orthogonal if any pair of distinct vectors in the set has inner
product zero.

A set \(S\) is orthonormal if:

- it is orthogonal;
- every vector in the set has unit norm.

So:

> An orthogonal set with unit-norm elements is an orthonormal set.

This is the foundation for the projection and unitary-matrix material that
follows.

## 7. Orthogonal Projection of a Vector Onto Another Vector

[Likely exam topic] The instructor calls orthogonal projection a very basic but
very important operation related to orthogonality and inner products.

Instructor remark: the same projection idea later extends to estimation and
random variables after the inner product is generalized. The geometry here is
simple, but the concept is foundational.

The first projection problem is:

> Given a vector \(x\), project it onto another vector \(y\).

The projection vector is denoted \(\widehat x\). It lies on the line determined
by \(y\), meaning

\[
\widehat x = \alpha y
\]

for some scalar \(\alpha\).

Because this is an orthogonal projection, the projection error

\[
x-\widehat x
\]

must be orthogonal to \(y\):

\[
\langle x-\widehat x,y\rangle = 0.
\]

Substitute \(\widehat x=\alpha y\):

\[
\langle x-\alpha y,y\rangle = 0.
\]

Distribute the inner product:

\[
\langle x,y\rangle - \alpha \langle y,y\rangle = 0.
\]

Equivalently,

\[
\langle x,y\rangle = \langle \widehat x,y\rangle.
\]

So the original vector and its projection have the same inner product with the
vector being projected onto.

Therefore

\[
\alpha = \frac{\langle x,y\rangle}{\langle y,y\rangle}.
\]

So the projection of \(x\) onto the line spanned by \(y\) is

\[
\widehat x
  = \frac{\langle x,y\rangle}{\langle y,y\rangle}y.
\]

[Exam note] This coefficient is the projection coefficient: take the inner
product of the vector being projected with the vector being projected onto, then
divide by the inner product of the vector with itself.

### Geometric Interpretation in Real Euclidean Space

Since

\[
\langle y,y\rangle = \|y\|^2,
\]

the projection formula can be written as

\[
\widehat x
  = \frac{\langle x,y\rangle}{\|y\|^2}y
  = \frac{\langle x,y\rangle}{\|y\|}\frac{y}{\|y\|}.
\]

The vector

\[
\frac{y}{\|y\|}
\]

is the unit vector in the direction of \(y\).

For real two- or three-dimensional vectors,

\[
\langle x,y\rangle = \|x\|\|y\|\cos\theta.
\]

Then

\[
\frac{\langle x,y\rangle}{\|y\|}
  = \|x\|\cos\theta.
\]

So the projection has:

- length \(\|x\|\cos\theta\) along the direction of \(y\);
- direction \(y/\|y\|\).

The instructor connects this to the right-triangle picture where \(\|x\|\) is
the hypotenuse and the projected length is \(\|x\|\cos\theta\).

### Orthogonal vs. Oblique Projection

The instructor notes that "projection" here means orthogonal projection by
default.

There is also a different operation called oblique projection, where the
projection direction is tilted rather than perpendicular to the target space.
Oblique projection is mentioned but not covered in this part of the lecture.

## 8. Orthogonal Bases and Coordinates

Now consider an \(n\)-dimensional subspace \(V\) inside an \(m\)-dimensional
ambient space, such as \(\mathbb C^m\).

Let

\[
\{q_1,q_2,\ldots,q_n\}
\]

be an orthogonal basis for \(V\).

Since this is a basis, any vector \(x\in V\) can be written as

\[
x = \alpha_1q_1+\alpha_2q_2+\cdots+\alpha_nq_n.
\]

The key claim is:

> If the basis is orthogonal, the coordinates \(\alpha_k\) are obtained by
> projecting \(x\) onto each basis vector separately.

### Proof of the Coordinate Formula

Take the inner product of \(x\) with a basis vector \(q_k\):

\[
\langle x,q_k\rangle
  =
  \left\langle
    \sum_{i=1}^n \alpha_i q_i,
    q_k
  \right\rangle.
\]

Using linearity in the first argument:

\[
\langle x,q_k\rangle
  =
  \sum_{i=1}^n \alpha_i \langle q_i,q_k\rangle.
\]

Because the basis vectors are orthogonal,

\[
\langle q_i,q_k\rangle = 0
\quad\text{when } i\ne k.
\]

Only the \(i=k\) term survives:

\[
\langle x,q_k\rangle
  =
  \alpha_k\langle q_k,q_k\rangle.
\]

Therefore

\[
\alpha_k
  =
  \frac{\langle x,q_k\rangle}{\langle q_k,q_k\rangle}.
\]

[Exam note] This is the same projection coefficient as in the vector-on-vector
projection formula.

### Why Orthogonal Bases Are Convenient

With an orthogonal basis, each coordinate is found independently:

\[
\alpha_k
  =
  \frac{\langle x,q_k\rangle}{\langle q_k,q_k\rangle}.
\]

You do not need to solve a coupled system of equations.

For an arbitrary non-orthogonal basis, simply taking inner products with basis
vectors does not directly give the coordinates. The basis vectors are coupled,
so one must solve a system of linear equations.

[Exam note] With an orthogonal basis, to find the coordinate in the direction of
\(q_k\), just project \(x\) onto \(q_k\). With a general basis, this shortcut
does not work.

### Orthonormal Basis Simplification

If the basis is orthonormal, then

\[
\langle q_k,q_k\rangle = 1.
\]

So the coordinate formula becomes

\[
\alpha_k = \langle x,q_k\rangle.
\]

Thus

\[
x
  =
  \sum_{k=1}^n \langle x,q_k\rangle q_k.
\]

Each term

\[
\langle x,q_k\rangle q_k
\]

is the projection of \(x\) onto the one-dimensional direction \(q_k\).

The whole vector is reconstructed by summing these individual projections.

### Two-Dimensional Picture

The instructor describes a two-dimensional picture with basis vectors \(q_1\)
and \(q_2\):

- project \(x\) onto \(q_1\) to get the component along \(q_1\);
- project \(x\) onto \(q_2\) to get the component along \(q_2\);
- these give \(\alpha_1\) and \(\alpha_2\).

[Exam note] This picture is important because it shows coordinates as
projection coefficients.

## 9. Student Question: Rotation, Reflection, and Orthonormal Bases

A student asks whether an orthonormal basis is just a rotation of the standard
basis.

The instructor answers:

- orthonormal is a special case of orthogonal, where the vectors also have unit
  length;
- in the real domain, one can move from one orthogonal/orthonormal basis to
  another using geometric operations such as rotations and reflections;
- a reflection is with respect to some reflection axis;
- combinations of rotations and reflections can convert the standard basis into
  an arbitrary orthogonal basis in the real setting.

The instructor says the forms of these operations will be studied later.

## 10. Outer Products and Rank-One Projection Matrices

For an orthonormal basis vector \(q_\ell\), the projection of \(x\) onto
\(q_\ell\) can be written as

\[
\langle x,q_\ell\rangle q_\ell.
\]

Using the lecture's convention,

\[
\langle x,q_\ell\rangle = q_\ell^*x.
\]

So

\[
\langle x,q_\ell\rangle q_\ell
  =
  q_\ell(q_\ell^*x)
  =
  (q_\ell q_\ell^*)x.
\]

The matrix

\[
q_\ell q_\ell^*
\]

is a projection matrix onto the one-dimensional space spanned by \(q_\ell\).

[Likely exam topic] The instructor emphasizes that this object is a matrix, not
a scalar.

### Inner Product vs. Outer Product

Compare the two orders:

\[
q_\ell^*q_\ell
\]

is a row vector times a column vector, so it is a scalar inner product.

But

\[
q_\ell q_\ell^*
\]

is a column vector times a row vector, so it is a matrix. This is called an
outer product.

If \(q_\ell\in\mathbb C^m\), then

\[
q_\ell q_\ell^*
\]

is an \(m\times m\) matrix.

### Rank of an Outer Product

The instructor asks for the rank of an outer product matrix.

For a general outer product

\[
xy^*,
\]

where \(x\) and \(y\) do not even need to have the same dimension, the columns
of \(xy^*\) are scaled copies of \(x\). Therefore the column space is contained
in

\[
\operatorname{span}\{x\}.
\]

If \(x\ne 0\) and \(y\ne 0\), the rank is one.

So an outer product of a column vector and a row vector is a rank-one matrix.

[Exam note] This is an important concept: outer products create rank-one
matrices because all columns point in the same direction.

### One-Dimensional Projection Matrix

For a unit vector \(q_\ell\),

\[
q_\ell q_\ell^*
\]

takes any input vector \(x\) and projects it onto

\[
\operatorname{span}\{q_\ell\}.
\]

The range of this projection matrix is exactly that one-dimensional subspace.

## 11. Summing Rank-One Projections Over an Orthonormal Basis

If

\[
\{q_1,\ldots,q_n\}
\]

is an orthonormal basis for a subspace \(V\subseteq\mathbb C^m\), then each
rank-one matrix

\[
q_\ell q_\ell^*
\]

projects onto the one-dimensional direction \(q_\ell\).

The sum

\[
\sum_{\ell=1}^n q_\ell q_\ell^*
\]

combines all these one-dimensional projections.

Define the basis matrix

\[
Q_V = [q_1\ q_2\ \cdots\ q_n].
\]

This matrix is \(m\times n\), usually tall if \(n<m\). Its columns are the
orthonormal basis vectors for \(V\).

Then

\[
\sum_{\ell=1}^n q_\ell q_\ell^*
  =
  Q_V Q_V^*.
\]

Dimension/rank warning from the board discussion:

- \(Q_V\) is \(m\times n\);
- \(Q_V^*\) is \(n\times m\);
- \(Q_VQ_V^*\) is \(m\times m\), but when \(n<m\) its rank is \(n\), not \(m\).

Therefore \(Q_VQ_V^*\) cannot be the full identity matrix on
\(\mathbb C^m\) unless \(V\) is the whole ambient space. The identity that does
hold for orthonormal columns is

\[
Q_V^*Q_V=I_n.
\]

For \(x\in V\),

\[
Q_VQ_V^*x=x.
\]

So \(Q_VQ_V^*\) acts like the identity on vectors already inside \(V\).

But \(Q_VQ_V^*\) is not generally the identity matrix on the whole ambient
space. If \(x\notin V\), then \(Q_VQ_V^*x\) is not equal to \(x\); it is the
projection of \(x\) onto \(V\).

This resolves the instructor's point:

> The matrix \(Q_VQ_V^*\) behaves like identity on the subspace \(V\), but it is
> a projection operator on the full ambient space.

## 12. Orthogonal Projection of a Vector Onto a Subspace

[Likely exam topic] The lecture then moves from projecting onto one vector to
projecting onto a vector space.

Let \(V\) be an \(n\)-dimensional subspace of an \(m\)-dimensional ambient space.
Let \(x\) be an arbitrary vector in the ambient space. The vector \(x\) may or
may not lie in \(V\).

The orthogonal projection of \(x\) onto \(V\) is the point \(\widehat x\in V\)
such that

\[
x-\widehat x
\]

is orthogonal to every vector in \(V\).

Equivalently:

- \(\widehat x\) must be a member of \(V\);
- the error vector \(x-\widehat x\) must be orthogonal to \(V\).

The instructor notes that this projection point also has a minimization
property:

> It is the closest point in \(V\) to \(x\), with distance measured using the
> norm induced by the inner product.

With the complex Euclidean inner product used here, that norm is

\[
\|z\|=\sqrt{z^*z}.
\]

The optimization viewpoint will be discussed later, so here the focus remains
on the orthogonality condition.

## 13. Deriving the Projection Onto a Subspace

The original definition of projection onto \(V\) depends only on the subspace,
not on a particular basis. However, a basis is a tool for computing the
projection.

Assume an orthonormal basis

\[
\{q_1,\ldots,q_n\}
\]

for \(V\).

Since \(\widehat x\in V\), write

\[
\widehat x
  =
  \alpha_1q_1+\cdots+\alpha_nq_n.
\]

The unknowns are the coefficients \(\alpha_1,\ldots,\alpha_n\).

The orthogonality condition says

\[
\langle x-\widehat x,q_k\rangle=0
\]

for every basis vector \(q_k\). This gives \(n\) equations for \(n\) unknowns.

Using the same projection-coefficient reasoning:

\[
\alpha_k
  =
  \frac{\langle x,q_k\rangle}{\langle q_k,q_k\rangle}.
\]

For an orthonormal basis,

\[
\langle q_k,q_k\rangle = 1,
\]

so

\[
\alpha_k = \langle x,q_k\rangle.
\]

Therefore

\[
\widehat x
  =
  \sum_{k=1}^n \langle x,q_k\rangle q_k.
\]

This is the sum of the projections of \(x\) onto the individual orthonormal
basis directions.

## 14. Orthogonal Projection Matrix Onto a Subspace

Using the matrix

\[
Q = [q_1\ q_2\ \cdots\ q_n],
\]

the projection formula becomes

\[
\widehat x = QQ^*x.
\]

So the orthogonal projection matrix onto \(V\) is

\[
P_V = QQ^*.
\]

[Likely exam topic] Projection matrices are a central object in this lecture.
The matrix \(P_V\) depends on the subspace \(V\), maps ambient vectors back into
\(\operatorname{range}(Q)=V\), and behaves differently on vectors inside and
outside \(V\).

[Exam note] To compute \(P_V\) for a given subspace:

1. Find any orthonormal basis for \(V\).
2. Put the basis vectors into the columns of \(Q\).
3. Compute \(Q^*\).
4. Multiply:

   \[
   P_V = QQ^*.
   \]

This matrix maps an \(m\)-dimensional vector to another \(m\)-dimensional vector,
but the output lies in \(V=\operatorname{range}(Q)\).

If \(x\in V\), then

\[
P_Vx=x.
\]

If \(x\notin V\), then \(P_Vx\) is the point in \(V\) obtained by orthogonally
projecting \(x\) onto \(V\).

## 15. Projection Matrix Does Not Depend on the Chosen Orthonormal Basis

A student asks whether the projection matrix is the same for all orthonormal
bases of the same subspace.

The instructor answers yes:

> The projection matrix depends on the subspace, not on the particular
> orthonormal basis chosen for that subspace.

Proof idea given in class:

Suppose another orthonormal basis matrix for the same subspace can be written as

\[
\widetilde Q = QT,
\]

where \(T\) is unitary. Then

\[
\widetilde Q\widetilde Q^*
  =
  (QT)(QT)^*
  =
  QTT^*Q^*.
\]

Since \(T\) is unitary,

\[
TT^*=I.
\]

Therefore

\[
\widetilde Q\widetilde Q^*
  =
  QQ^*.
\]

So all orthonormal bases of the same subspace produce the same orthogonal
projection matrix.

The instructor notes that the fact that one orthonormal basis is obtained from
another by multiplying by a unitary matrix will be shown more fully later.

## 16. Properties of Orthogonal Projection Matrices

Let

\[
P_V=QQ^*
\]

where the columns of \(Q\) are orthonormal.

### Property 1: Hermitian

The conjugate transpose of \(P_V\) is

\[
P_V^*
  =
  (QQ^*)^*
  =
  QQ^*
  =
  P_V.
\]

The proof uses the rule \((AB)^*=B^*A^*\) and the fact that
\((Q^*)^*=Q\).

So an orthogonal projection matrix is Hermitian:

\[
P_V^*=P_V.
\]

[Exam note] Hermitian matrices are an important family. Later topics include
positive semidefinite matrices, which sit under the broader Hermitian-matrix
family.

### Property 2: Idempotent

The square of \(P_V\) is

\[
P_V^2
  =
  (QQ^*)(QQ^*)
  =
  Q(Q^*Q)Q^*.
\]

Since the columns of \(Q\) are orthonormal,

\[
Q^*Q=I.
\]

Therefore

\[
P_V^2
  =
  QIQ^*
  =
  QQ^*
  =
  P_V.
\]

So

\[
P_V^2=P_V.
\]

A matrix satisfying this property is called idempotent.

Geometric reason:

- \(P_Vx\) is already in \(V\).
- Projecting it onto \(V\) again does not change it.
- Therefore \(P_V(P_Vx)=P_Vx\) for every \(x\).

## 17. Projection Matrices vs. Orthogonal Projection Matrices

The instructor distinguishes two related ideas:

- A matrix satisfying

  \[
  P^2=P
  \]

  is a projection matrix.

- If, in addition,

  \[
  P^*=P,
  \]

  then it is an orthogonal projection matrix.

If a projection matrix is idempotent but not Hermitian, it corresponds to an
oblique projection. In that case, the projection direction is tilted rather than
orthogonal.

The instructor says oblique projections are not covered at this point.

## 18. Projection Using a Non-Orthonormal Basis

The lecture briefly gives the more general projection formula when the basis is
not orthonormal.

Suppose \(A\) has linearly independent columns

\[
a_1,\ldots,a_n
\]

that form a basis for the target subspace. These columns are not necessarily
orthogonal.

Because these columns are a basis, \(A^*A\) is invertible in this full-column
rank case, so the correction factor below is well-defined.

Then the orthogonal projection matrix onto \(\operatorname{range}(A)\) is

\[
P_A
  =
  A(A^*A)^{-1}A^*.
\]

The middle factor

\[
(A^*A)^{-1}
\]

is the correction term that accounts for the fact that the basis vectors are not
orthonormal.

If the columns are orthonormal, then

\[
A^*A=I,
\]

and the formula reduces to

\[
P_A=AA^*,
\]

which matches the earlier \(QQ^*\) formula.

[Exam note] The simple formula \(QQ^*\) is special to the orthonormal-basis
case. With a general basis, the correction term \((A^*A)^{-1}\) is needed.

The instructor says this general formula will be revisited when discussing
least squares.

## 19. Least Squares Connection

The lecture connects projection matrices to the system

\[
Ax=b.
\]

The columns of \(A\) span the column space, or range space, of \(A\):

\[
\operatorname{range}(A).
\]

Solving \(Ax=b\) asks whether \(b\) can be written as a linear combination of
the columns of \(A\).

If

\[
b\notin \operatorname{range}(A),
\]

then there is no exact solution.

This is where the earlier existence-and-uniqueness discussion would stop:
outside the column space, the equation \(Ax=b\) is inconsistent.

But in applications and research, we often do not stop there. Instead, we look
for a nearby solution:

> Find the point in \(\operatorname{range}(A)\) that is as close as possible to
> \(b\).

That closest point is the orthogonal projection of \(b\) onto
\(\operatorname{range}(A)\).

This is the geometric meaning of the least squares solution.

### Different Least-Squares Viewpoints Mentioned

The instructor describes several interpretations:

- Standard least squares "blames" \(b\): \(b\) should have been in the range
  space of \(A\), but measurement noise or error pushed it outside. We project
  \(b\) back onto \(\operatorname{range}(A)\).
- A data/tilted-space version "blames" \(A\): \(b\) is treated as correct, but
  \(A\) is noisy, so the range space of \(A\) is tilted until it contains or
  better matches \(b\).
- Total least squares "blames" both: both \(b\) and the space may be moved to
  meet each other.

[Exam note] The instructor gives the "mountain and mouse" analogy:

- least squares moves/projects the vector \(b\) to the space;
- the tilted-space version moves the space toward \(b\);
- total least squares moves both.

These versions will be discussed later.

## 20. Summary of Orthogonality Topics Covered

The instructor explicitly summarizes the orthogonality material covered in this
lecture:

- orthogonality;
- orthogonal sets;
- orthonormal sets;
- orthogonal projection of a vector onto another vector;
- orthogonal projection of a vector onto a vector space;
- projection matrices.

These are described as important and foundational topics.

## 21. Unitary Matrices

After projection matrices, the next special matrix family introduced is the
unitary matrices.

Unitary matrices are the complex version of real orthogonal matrices.

A matrix \(U\in\mathbb C^{n\times n}\) is unitary if

\[
U^*U=I
\]

and equivalently

\[
UU^*=I.
\]

This means

\[
U^{-1}=U^*.
\]

So the inverse of a unitary matrix is simply its conjugate transpose.

The real version is called an orthogonal matrix.

### Why Unitary Matrices Are Useful

Systems involving unitary matrices are easier to solve. If

\[
Ux=b,
\]

then

\[
x=U^{-1}b=U^*b.
\]

No general matrix inversion is needed. One only takes the conjugate transpose of
\(U\), which means transpose the matrix and conjugate its entries, then multiply
by \(b\).

In the instructor's words, forming the inverse is just swapping rows and columns
and changing the signs of the imaginary parts, because \(U^{-1}=U^*\).

## 22. Columns and Rows of a Unitary Matrix Are Orthonormal Bases

The condition

\[
U^*U=I
\]

means the columns of \(U\) form an orthonormal set.

Reason:

- write \(U\) by columns;
- \(U^*U\) forms all pairwise inner products of the columns;
- the identity matrix says each column has norm one and distinct columns are
  orthogonal.

Because \(U\) is square, these columns form an orthonormal basis for
\(\mathbb C^n\).

The condition

\[
UU^*=I
\]

means the rows of \(U\) also form an orthonormal basis.

So for a unitary matrix:

- columns are an orthonormal basis;
- rows are an orthonormal basis;
- the inverse is the conjugate transpose.

[Likely exam topic] Orthonormal bases and unitary matrices are directly linked:
unitary matrices are exactly the square matrices whose columns and rows are
orthonormal bases.

## 23. Forward Look

The instructor says unitary matrices have many interesting and useful
properties, and the course will continue with them after the break.

Upcoming special matrix families:

- unitary matrices;
- Hermitian matrices;
- important subsets of Hermitian matrices, including positive semidefinite
  matrices.

## Source and Coverage Note

Source used: `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture9_corrected.md`.

Coverage: These notes cover only Lecture 09. They preserve the chronological
flow of the transcript, including the review of matrix factorizations and
similarity, the proof that similar matrices preserve eigenvalues, the complex
inner-product recap, orthogonal and orthonormal sets, vector and subspace
projection formulas, projection matrices and their properties, least-squares
connections, unitary matrices, instructor remarks, student questions, warnings,
and all exam-relevant markers present in the transcript. No other lecture
transcripts were used.
