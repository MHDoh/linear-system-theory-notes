# Lecture 08 Notes

## 1. Big Picture: Linear Systems Through Matrix Factorization

The lecture begins by continuing the philosophy for solving systems of linear equations.

The instructor emphasized that some systems are easy to solve because their coefficient matrices have simple structure:

- **Diagonal form**: the simplest case; equations decouple completely.
- **Triangular form**: easy to solve by forward or back substitution.
- **Orthogonal form**: easy because orthogonal transformations preserve lengths and have simple inverses.

For a general system of linear equations, the strategy is to convert the original system into a sequence of easier systems involving these simple matrix types. This conversion is equivalent to factoring the original matrix into a product of simple matrices.

This viewpoint explains many famous linear algebra factorizations:

- If \(A = QR\), where \(Q\) is orthogonal and \(R\) is upper triangular, then solving \(Ax=b\) becomes solving a sequence involving an orthogonal matrix and an upper triangular matrix. The instructor noted that the solver used in the course/platform is based on QR factorization.
- Gaussian elimination is also a matrix factorization. The row operations in Gaussian elimination can be viewed as multiplication from the left by lower triangular matrices.
- Gaussian elimination uses lower triangular matrices to convert a matrix into upper triangular form, producing an \(LU\)-type factorization.
- Sometimes row exchanges are needed, so a permutation matrix \(P\) is included. A permutation matrix is orthogonal, so the factorization still uses simple matrices.

The unifying idea is:

\[
\text{hard matrix} = \text{product of simple matrices}.
\]

Then solving one hard system is replaced by solving several easier systems.

## 2. Diagonalization as a Guiding Theme

[Likely exam topic]

The instructor then introduced the main storyline of the lecture: the desire to convert matrices into diagonal form.

Diagonal matrices are the simplest matrices, so the diagonalization principle has been central in the development of algorithms. The lecture will explore what can and cannot be done when trying to turn a matrix into diagonal form.

The main related ideas are:

- basis change,
- representation of linear transformations under a new basis,
- eigenvalues and eigenvectors,
- diagonalizable and non-diagonalizable matrices,
- triangularization as a weaker but always possible goal for square matrices,
- singular value decomposition as a more flexible diagonalization framework.

The instructor described the situation as having:

- some good news,
- some bad news,
- and some consolation results,

eventually leading toward SVD.

## 3. Basis Change for Vectors

The first step is to understand basis change in a vector space.

By default, vectors in \(\mathbb R^2\) or \(\mathbb R^n\) are represented with respect to the **standard basis**. In \(\mathbb R^2\), this means

\[
x = x_1 e_1 + x_2 e_2.
\]

The coordinates \(x_1,x_2\) are standard coordinates, and \(e_1,e_2\) are the standard coordinate vectors. These standard basis vectors are unit-norm vectors aligned with the coordinate axes, giving the default coordinate system.

However, we can choose a different basis. The new basis vectors do not have to be orthogonal. The only requirements are:

- they span the vector space,
- they are linearly independent.

For example, in \(\mathbb R^2\), choose basis vectors \(t_1,t_2\). Then the same vector \(x\) can be represented as

\[
x = \tilde{x}_1 t_1 + \tilde{x}_2 t_2.
\]

The coordinates \(\tilde{x}_1,\tilde{x}_2\) are the coordinates of the same vector \(x\) with respect to the new basis.

[Exam note]

The instructor emphasized the matrix multiplication interpretation: if basis vectors are placed as columns of a matrix, then multiplying that matrix by a coordinate vector forms the corresponding linear combination of the columns.

Define the basis matrix

\[
T = [t_1 \; t_2].
\]

Then

\[
x = T\tilde{x}.
\]

Here:

- \(x\) is the vector in standard coordinates,
- \(T\) is the basis matrix,
- \(\tilde{x}\) is the coordinate vector in the new basis.

Because \(T\) has linearly independent columns and is square, it is full rank and invertible. Therefore,

\[
\tilde{x} = T^{-1}x.
\]

So:

- To go from new coordinates to standard coordinates, multiply by \(T\).
- To go from standard coordinates to new coordinates, multiply by \(T^{-1}\).

This is only a **representation change**. No linear transformation has been applied yet.

The same construction extends directly to \(\mathbb R^n\). For an \(n\)-dimensional basis \(t_1,\dots,t_n\), define

\[
T = [t_1 \; t_2 \; \cdots \; t_n].
\]

Then

\[
x = T\tilde{x},
\qquad
\tilde{x}=T^{-1}x.
\]

## 4. Basis Change for Linear Transformations

The discussion then moves from representing vectors to representing linear transformations.

The lecture focuses first on square matrices, because the immediate goal is diagonalization of square matrices. A square matrix represents a mapping from \(\mathbb R^n\) to \(\mathbb R^n\). Since input and output live in spaces of the same dimension, it makes sense to ask whether the same basis can be used for both.

For a linear mapping

\[
y = Ax,
\]

suppose \(x\) and \(y\) are represented in standard coordinates. Now choose a new basis \(T\) and represent both input and output in that same basis:

\[
x = T\tilde{x},
\qquad
y = T\tilde{y}.
\]

The actual mapping does not change. The same point still maps to the same point. What changes is the matrix representation of that mapping.

Substitute the new-coordinate expressions into \(y=Ax\):

\[
T\tilde{y} = A T \tilde{x}.
\]

Multiply by \(T^{-1}\) on the left:

\[
\tilde{y} = T^{-1} A T \tilde{x}.
\]

Therefore the new matrix representation is

\[
\tilde{A} = T^{-1}AT.
\]

This matrix represents the same linear transformation, but with respect to the new basis.

The relationship

\[
\tilde{A}=T^{-1}AT
\]

is the central basis-change formula for square matrices when the same basis is used for input and output.

## 5. The Diagonalization Question

Once the basis-change formula is available, the natural question is:

\[
\text{Can we choose a smart basis } T \text{ such that } T^{-1}AT
\text{ is diagonal?}
\]

If such a basis exists, then the linear transformation is represented by a diagonal matrix in that basis.

The instructor called this the diagonalization trick, but also stressed that this is a **restricted** version of diagonalization because the same basis is being used for both input and output.

This restriction matters:

- If the same basis must be used for input and output, not every square matrix can be diagonalized.
- If different bases are allowed for input and output, then the situation becomes more flexible, and every matrix can be represented in a diagonal-type form. This leads to singular value decomposition.

For now, the main question is:

\[
\text{Given a square matrix } A,\text{ can we find an invertible } T
\text{ such that } T^{-1}AT \text{ is diagonal?}
\]

This question leads directly to eigenvalues and eigenvectors.

[Exam note]

The instructor said to "put this in your pocket" because the same question will return repeatedly: diagonalization by basis change is ultimately tied to eigenvectors.

## 6. Eigenvectors: Geometric Motivation

For a square matrix \(A\), the mapping \(x \mapsto Ax\) sends a vector in \(\mathbb R^n\) back into the same space.

Usually, \(Ax\) points in a different direction from \(x\), and it may also have a different length.

The eigenvector question is:

\[
\text{Are there special directions } x \text{ such that } Ax
\text{ points in the same or opposite direction as } x?
\]

Opposite direction is allowed because that is still the same line, just scaled by a negative number.

If \(Ax\) lies in the same direction as \(x\), then \(A\) acts like scalar multiplication on that vector:

\[
Ax = \lambda x.
\]

Here:

- \(x\neq 0\) is an eigenvector,
- \(\lambda\) is the corresponding eigenvalue.

The zero vector is excluded because it satisfies \(A0=\lambda 0\) trivially for every \(\lambda\), which carries no directional information.

## 7. Algebraic Derivation of the Eigenvalue Condition

Start with

\[
Ax = \lambda x.
\]

Move the right-hand side to the left:

\[
Ax - \lambda x = 0.
\]

The two terms are not in the same matrix-multiplication form yet: \(Ax\) is a matrix-vector product, while \(\lambda x\) is scalar multiplication.

Use the identity matrix to rewrite scalar multiplication:

\[
\lambda x = \lambda I x.
\]

Then

\[
Ax - \lambda Ix = 0,
\]

so

\[
(A-\lambda I)x = 0.
\]

The question becomes:

\[
\text{Can we find } \lambda \text{ such that } A-\lambda I
\text{ has a nonzero null-space vector?}
\]

Equivalently:

- \(x\) must be a nonzero vector in the null space of \(A-\lambda I\),
- therefore \(A-\lambda I\) must have a nontrivial null space,
- therefore \(A-\lambda I\) must be rank deficient.

The instructor explained this as subtracting the same scalar \(\lambda\) from all diagonal entries of \(A\) and asking whether the resulting matrix becomes rank deficient.

If \(A\) is already rank deficient, then \(\lambda=0\) is an eigenvalue, because \(A-0I=A\) already has a nontrivial null space. The null-space vectors of \(A\) are eigenvectors corresponding to eigenvalue \(0\).

For square matrices, rank deficiency is equivalent to determinant zero. Therefore the eigenvalue condition is

\[
\det(A-\lambda I)=0.
\]

The lecture also used

\[
\det(\lambda I-A)=0.
\]

For the purpose of finding roots, either form can be used; the sign convention changes only by a possible factor depending on dimension.

## 8. Determinant as Volume Scaling

To motivate why determinant zero corresponds to rank deficiency, the instructor reviewed determinant as volume scaling.

For a \(2\times 2\) diagonal mapping, one basis direction might be scaled by \(2\) and the other by \(4\). A unit square is mapped to a rectangle with area

\[
2\cdot 4 = 8.
\]

For a diagonal matrix, this area scale is the product of the diagonal entries, which is the determinant.

The instructor also gave the geometric reason that the image of the square is determined by the images of its edge vectors. Points on an edge can be written as convex combinations of the edge endpoints, and a linear map sends those convex combinations to the same convex combinations of the mapped endpoints. This is why the transformed square becomes the rectangle or parallelogram spanned by the images of the basis directions.

More generally:

- A square region maps to a parallelogram.
- A circular region maps to an ellipse; in the same diagonal example, its area is also scaled by the determinant factor \(8\).
- In higher dimensions, a unit volume maps to a parallelepiped.
- The determinant gives the signed volume-scaling factor.

If the determinant is \(1\), the mapped parallelogram or parallelepiped has the same area or volume as the original unit region, even though its shape may have changed.

If a mapping is rank deficient, it collapses the input space into a lower-dimensional subspace. For example, a two-dimensional region may be mapped into a one-dimensional line. In the ambient two-dimensional output space, the area is then zero.

Thus:

\[
A \text{ rank deficient}
\quad \Longleftrightarrow \quad
\det(A)=0
\]

for square matrices.

This explains why the condition for eigenvalues is a determinant equation.

## 9. Characteristic Polynomial

[Likely exam topic]

[Exam note]

The instructor said that in homework one can show that

\[
\det(\lambda I-A)
\]

is an \(n\)-degree polynomial in \(\lambda\) for an \(n\times n\) matrix \(A\).

This polynomial is called the **characteristic polynomial** of \(A\):

\[
p_A(\lambda)=\det(\lambda I-A).
\]

It is a **monic polynomial**, meaning the coefficient of the highest-degree term \(\lambda^n\) is \(1\).

The eigenvalue problem can therefore be rephrased:

\[
\text{Find the roots of the characteristic polynomial.}
\]

Those roots are the eigenvalues of \(A\).

The instructor connected this to the historical problem of solving polynomial equations:

- Degree 1 equations are simple.
- Degree 2 equations have the quadratic formula.
- Degree 3 and degree 4 also have formulas.
- For degree 5 and higher, there is no general formula in radicals for all polynomial roots.

However, this does not mean roots do not exist.

By the **fundamental theorem of algebra**, every degree \(n\) polynomial has \(n\) complex roots counted with multiplicity. Some roots may repeat. Even if \(A\) is a real matrix, its eigenvalues can be complex.

Therefore, over the complex numbers, every square matrix has eigenvalues.

Once an eigenvalue \(\lambda_i\) is found, the corresponding eigenvectors are the nonzero vectors in

\[
\operatorname{null}(\lambda_i I-A)
\]

or equivalently in

\[
\operatorname{null}(A-\lambda_i I).
\]

This null space is called the **eigenspace** associated with \(\lambda_i\).

If \(x\) is an eigenvector, then any nonzero scalar multiple of \(x\) is also an eigenvector for the same eigenvalue. For example, \(5x\) and \(10x\) are also eigenvectors. Thus each eigenspace contains infinitely many eigenvectors unless it is trivial, and the eigenvectors are the nonzero vectors in that eigenspace.

## 10. Connecting Eigenvectors Back to Diagonalization

Now suppose \(A\) is an \(n\times n\) matrix and we choose \(n\) eigenvectors

\[
t_1,t_2,\dots,t_n.
\]

For each \(i\),

\[
At_i=\lambda_i t_i.
\]

At this point the \(\lambda_i\)'s do not have to be distinct. Repeated eigenvalues are allowed; the only assumption is that the selected columns \(t_i\) are eigenvectors of \(A\).

[Exam note]

The instructor deliberately reused the notation \(t_i\) because earlier \(t_i\) denoted basis vectors. The goal is to connect eigenvectors to the basis matrix \(T\).

Put the eigenvectors into a matrix as columns:

\[
T=[t_1\;t_2\;\cdots\;t_n].
\]

Then left-multiply by \(A\):

\[
AT = A[t_1\;t_2\;\cdots\;t_n].
\]

Using column-partitioned matrix multiplication:

\[
AT = [At_1\;At_2\;\cdots\;At_n].
\]

Since each \(t_i\) is an eigenvector:

\[
AT = [\lambda_1 t_1\;\lambda_2 t_2\;\cdots\;\lambda_n t_n].
\]

This can be written as

\[
AT = T\Lambda,
\]

where

\[
\Lambda=
\begin{bmatrix}
\lambda_1 & 0 & \cdots & 0\\
0 & \lambda_2 & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & \lambda_n
\end{bmatrix}.
\]

The instructor highlighted the column-scaling interpretation:

- Left-multiplying \(T\) by \(A\) applies \(A\) to each column.
- Right-multiplying \(T\) by a diagonal matrix scales each column by the corresponding diagonal entry.

If \(T\) is invertible, then multiply \(AT=T\Lambda\) on the left by \(T^{-1}\):

\[
T^{-1}AT = \Lambda.
\]

So the original diagonalization question is equivalent to:

\[
\text{Can we find } n \text{ linearly independent eigenvectors of } A?
\]

Because \(T\) is invertible exactly when its columns form a linearly independent set.

## 11. Diagonalizable and Non-Diagonalizable Matrices

[Exam note]

The instructor restated the key requirement:

To diagonalize \(A\) by a basis change, we need an invertible matrix \(T\) whose columns are eigenvectors of \(A\). Equivalently, we need \(n\) linearly independent eigenvectors.

This leads to a classification of square matrices:

- **Diagonalizable matrices**: matrices for which we can find \(n\) linearly independent eigenvectors.
- **Non-diagonalizable matrices**: matrices for which we cannot find \(n\) linearly independent eigenvectors.

The answer to the diagonalization question is not always positive. Some matrices are diagonalizable; some are not.

### Non-Diagonalizable Example

The instructor gave an "innocent looking" \(2\times 2\) example. From the characteristic calculation in the transcript, the matrix is the standard nilpotent Jordan block:

\[
A=
\begin{bmatrix}
0 & 1\\
0 & 0
\end{bmatrix}.
\]

Then

\[
\lambda I-A
=
\begin{bmatrix}
\lambda & -1\\
0 & \lambda
\end{bmatrix}.
\]

The characteristic polynomial is

\[
\det(\lambda I-A)=\lambda^2.
\]

So the only eigenvalue is

\[
\lambda=0,
\]

and it appears twice as a root.

The eigenvectors are found from the null space of \(A\). The instructor described null-space vectors as vectors orthogonal to every row of the matrix. For this example, the zero row is orthogonal to every vector, while the row \([0\;1]\) forces the second component of the vector to be zero.

A vector

\[
\begin{bmatrix}
r\\
0
\end{bmatrix}
\]

is in the null space for any scalar \(r\) from the field being used, real or complex. The eigenspace is therefore spanned by

\[
\begin{bmatrix}
1\\
0
\end{bmatrix}.
\]

This eigenspace is one-dimensional. Therefore there is only one linearly independent eigenvector direction, not two. Since a \(2\times 2\) matrix would need two linearly independent eigenvectors to be diagonalizable, this matrix is not diagonalizable.

## 12. Algebraic and Geometric Multiplicity

The example motivates two types of multiplicity.

The **algebraic multiplicity** of an eigenvalue is the number of times it appears as a root of the characteristic polynomial.

The **geometric multiplicity** of an eigenvalue is the dimension of its eigenspace:

\[
g_i = \dim \operatorname{null}(\lambda_i I-A).
\]

In the example

\[
A=
\begin{bmatrix}
0 & 1\\
0 & 0
\end{bmatrix},
\]

the eigenvalue \(0\) has:

- algebraic multiplicity \(2\),
- geometric multiplicity \(1\).

This mismatch is the core reason the matrix is not diagonalizable.

For a general \(n\times n\) matrix with \(k\) distinct eigenvalues, let:

- \(a_i\) be the algebraic multiplicity of eigenvalue \(\lambda_i\),
- \(g_i\) be the geometric multiplicity of eigenvalue \(\lambda_i\).

The algebraic multiplicities always add to \(n\):

\[
\sum_{i=1}^k a_i = n.
\]

The geometric multiplicities do not necessarily add to \(n\). For diagonalization, we want enough eigenspace dimensions to build a full basis:

\[
\sum_{i=1}^k g_i = n.
\]

When this happens, \(A\) is diagonalizable.

The instructor did not go into a full if-and-only-if theorem in detail, but the practical condition stated in the lecture is:

\[
A \text{ is diagonalizable if we can find } n
\text{ linearly independent eigenvectors.}
\]

### Distinct Eigenvalues

If an \(n\times n\) matrix has \(n\) distinct eigenvalues, then it is diagonalizable. Each distinct eigenvalue contributes an independent eigenspace direction, giving enough independent eigenvectors.

However, the converse is not true:

\[
n \text{ distinct eigenvalues} \Longrightarrow \text{diagonalizable},
\]

but

\[
\text{diagonalizable} \not\Longrightarrow n \text{ distinct eigenvalues}.
\]

The identity matrix is the instructor's example of the converse failing. The identity matrix has one repeated eigenvalue, but it is already diagonal and is certainly diagonalizable.

## 13. Similarity, Triangularization, Schur/Jordan Direction, and SVD

The basis-change expression

\[
T^{-1}AT
\]

is called a **similarity transformation**. The question "Can \(A\) be diagonalized by a basis change?" is the question of whether \(A\) is similar to a diagonal matrix.

The answer is no in general: not every square matrix is diagonalizable.

The reason diagonal matrices are desirable is that they make many problems easier, including:

- systems of linear equations,
- systems of linear differential equations,
- other computations involving repeated action of a linear map.

The instructor then proposed a less ambitious target. If diagonalization cannot always be guaranteed, can we at least represent a square matrix as triangular after a basis change?

The question is:

\[
\text{Can we find } T \text{ such that } T^{-1}AT
\text{ is triangular?}
\]

The answer stated in lecture:

\[
\text{Every square matrix can be triangularized by a basis change.}
\]

The transcript renders the name unclearly, but this is the direction of the Schur/triangular form discussion. The instructor said this will be discussed later.

The instructor also mentioned Jordan form:

- Jordan form is not always diagonal.
- It is close to diagonal, with possible superdiagonal entries.
- The course will not go deeply into Jordan form.

Then the instructor returned to the restriction that caused the diagonalization problem: using the same basis for input and output.

Using the same basis can be appropriate in some applications, but it is a constraint rather than a necessity in every application.

If we allow different bases:

- one basis for the input space,
- another basis for the output space,

then the diagonal-representation question becomes more flexible.

The instructor stated that with this freedom, the answer is positive: one can represent the linear transformation in diagonal form by choosing smart input and output bases. The special form of this positive result is the **singular value decomposition**.

This also connects to non-square matrices. For a rectangular matrix, input and output dimensions differ, so using the same basis for both spaces does not make sense. In rectangular "diagonal" matrices, only entries on the main diagonal are allowed to be nonzero; all other entries are zero.

## 14. Transition to Orthogonality and Complex Inner Products

Before continuing with diagonalization, triangularization, and SVD, the instructor said the course needs a deeper treatment of orthogonality.

To discuss orthogonality properly in complex vector spaces, the inner product definition must be extended from real vectors to complex vectors.

## 15. Real Euclidean Norm Review

[Exam note]

For a real vector \(x\in \mathbb R^n\), the Euclidean norm is

\[
\|x\|_2 = \sqrt{x^T x}
=
\sqrt{\sum_{i=1}^n x_i^2}.
\]

This is the standard extension of the length concept to \(n\)-dimensional real vectors.

## 16. Complex Magnitude and Conjugate Transpose

For complex vectors, ordinary transpose is not enough. The instructor introduced the **conjugate transpose**, also called the **Hermitian transpose**.

Notation used:

\[
x^H
\]

or sometimes

\[
x^*
\]

depending on convention.

The conjugate transpose does two things:

1. It transposes the vector or matrix.
2. It conjugates every complex entry.

For a complex scalar \(a\), its magnitude is its distance from the origin in the complex plane. If

\[
a = u+iv,
\]

then

\[
|a| = \sqrt{u^2+v^2}.
\]

This can be written using conjugation:

\[
|a| = \sqrt{\overline{a}a}.
\]

The reason conjugation is needed is that multiplying a complex number by itself does not generally produce its squared magnitude. For example,

\[
(1+i)^2 = 2i,
\]

which is complex, while

\[
\overline{(1+i)}(1+i)=(1-i)(1+i)=2.
\]

So multiplying by the conjugate produces a nonnegative real magnitude-squared value.

For a complex vector \(x\), define the Euclidean norm by

\[
\|x\|_2 = \sqrt{x^H x}.
\]

Expanding this:

\[
x^H x
=
\overline{x_1}x_1+\overline{x_2}x_2+\cdots+\overline{x_n}x_n
=
|x_1|^2+|x_2|^2+\cdots+|x_n|^2.
\]

Thus

\[
\|x\|_2 =
\sqrt{\sum_{i=1}^n |x_i|^2}.
\]

This gives a nonnegative real number.

## 17. MATLAB Warning: Transpose vs Conjugate Transpose

[Exam note]

The instructor gave a practical MATLAB warning.

In MATLAB:

- `x'` is the conjugate transpose.
- For real vectors, `x'` behaves like an ordinary transpose because conjugation has no effect.
- For complex vectors, `x'` also conjugates entries.
- To take the plain transpose without conjugating, use `x.'`.
- To conjugate without transposing, use `conj(x)`.

In mathematical notation, the plain transpose is written \(x^T\), while the conjugate/Hermitian transpose is written \(x^H\) or \(x^*\), depending on convention.

The instructor warned that many people mistakenly use `'` thinking it is only transpose. This can cause debugging problems in complex-valued computations.

## 18. Complex Inner Product Convention

The lecture then defined the complex inner product.

The instructor's convention is linear in the first argument and conjugate-linear in the second argument:

\[
\langle x,y\rangle = y^H x
=
\sum_{i=1}^n x_i \overline{y_i}.
\]

With this convention, the norm is still obtained from the inner product of a vector with itself:

\[
\|x\|_2 = \sqrt{\langle x,x\rangle}
=
\sqrt{x^H x}.
\]

For real vectors, the inner product is symmetric:

\[
\langle x,y\rangle = \langle y,x\rangle.
\]

For complex vectors, this is no longer true in general. Instead:

\[
\langle x,y\rangle
=
\overline{\langle y,x\rangle}.
\]

So the two reversed inner products are complex conjugates of each other.

Example form from the lecture:

If

\[
\langle x,y\rangle = 3+5i,
\]

then

\[
\langle y,x\rangle = 3-5i.
\]

## 19. Scaling Rules for the Complex Inner Product

Because of conjugation, scaling behaves differently depending on which argument is scaled.

With the lecture's convention:

\[
\langle \alpha x,y\rangle
=
\alpha \langle x,y\rangle.
\]

Scaling the first vector scales the inner product by the same scalar.

But if the second vector is scaled:

\[
\langle x,\beta y\rangle
=
\overline{\beta}\langle x,y\rangle.
\]

The scalar is conjugated because the second argument is the conjugated one in this convention.

For real scalars, this distinction disappears because

\[
\overline{\beta}=\beta.
\]

For complex scalars, the distinction matters.

## 20. Orthogonal and Orthonormal Sets

[Exam note]

The instructor extended the definition of orthogonality to complex vectors.

Let

\[
S\subseteq \mathbb C^m.
\]

The set \(S\) is an **orthogonal set** if and only if every distinct pair of vectors in \(S\) is orthogonal:

\[
\langle u,v\rangle = 0
\quad
\text{for all distinct } u,v\in S.
\]

Orthogonality is a property of the set: any pair chosen from the set must have zero inner product.

The standard basis in three dimensions is an example:

\[
e_1=
\begin{bmatrix}
1\\0\\0
\end{bmatrix},
\quad
e_2=
\begin{bmatrix}
0\\1\\0
\end{bmatrix},
\quad
e_3=
\begin{bmatrix}
0\\0\\1
\end{bmatrix}.
\]

Any pair has inner product zero, so the standard basis is orthogonal.

A set is an **orthonormal set** if:

1. it is orthogonal,
2. every vector in the set has unit norm.

The standard basis is orthonormal, because each standard basis vector has norm \(1\).

The instructor also contrasted this with an orthogonal set whose vectors are not unit norm. Such a set is orthogonal but not orthonormal. For example, scaled coordinate vectors such as \(\{2e_1,3e_2,e_3\}\) still have zero pairwise inner products, but not every vector has norm \(1\).

## 21. Preview of Next Lecture

The next lecture will focus on **orthogonal projection**, which the instructor described as a key operation.

The projection discussion will include:

- projecting a vector onto a vector,
- projecting a vector onto a subspace,
- extending the geometric idea of projection into the linear algebra framework.

## Source and Coverage Note

These notes were created only from `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture8_corrected.md`. They cover the lecture chronologically, including the transcript's exam-marked topics, definitions, proof ideas, examples, warnings, instructor remarks, and stated links to later topics. No other lecture transcript was processed.
