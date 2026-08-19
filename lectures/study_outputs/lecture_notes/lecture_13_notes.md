# Lecture 13 Notes

## Opening Context: Hermitian Matrices and Quadratic Functions

The lecture begins by continuing the discussion of special subsets of the normal matrix family. The instructor remarks that some subsets, such as some materials or regions in the unit circle picture from the previous lecture, may not have special names. The main named family of interest here is the Hermitian family.

Hermitian matrices are important because they define real-valued quadratic forms. The lecture focuses on multivariate quadratic functions and explains how the eigenvalue structure of a Hermitian matrix determines the shape of those functions.

Within the Hermitian matrices, the instructor divides matrices according to the signs of their eigenvalues:

- all eigenvalues positive: positive definite;
- all eigenvalues nonnegative: positive semidefinite;
- all eigenvalues negative: negative definite;
- all eigenvalues nonpositive: negative semidefinite;
- a mixture of positive and negative eigenvalues: indefinite.

The remaining case, where a Hermitian matrix has both positive and negative eigenvalues, is called indefinite. These sign classes are not just algebraic labels; they determine the geometry and optimization behavior of the associated quadratic function.

## Hermitian Matrices and the Quadratic Form \(x^*Ax\)

Let \(A\) be Hermitian. Then

\[
A=A^*
\]

and the quadratic form

\[
x^*Ax
\]

is always real-valued, even when \(x\) is a complex vector.

Hermitian matrices are also normal matrices. Since normal matrices are unitarily diagonalizable, a Hermitian matrix can be written as

\[
A = U \Lambda U^*
\]

where:

- \(U\) is unitary;
- the columns of \(U\) are unit-norm eigenvectors of \(A\);
- \(\Lambda\) is diagonal;
- the diagonal entries \(\lambda_i\) are the eigenvalues of \(A\);
- for Hermitian matrices, all \(\lambda_i\) are real.

The instructor connects this to earlier results:

- Hermitian matrices are a special case of normal matrices.
- Normal matrices are unitarily diagonalizable.
- Distinct eigenvalues of Hermitian matrices have orthogonal eigenspaces.
- Because of this, one can choose an orthonormal eigenbasis and build \(U\) from those eigenvectors.

## Coordinate Interpretation of \(U^*x\)

The lecture emphasizes the geometric meaning of

\[
U^*x.
\]

If

\[
U = [u_1 \ u_2 \ \cdots \ u_n],
\]

then

\[
U^*x =
\begin{bmatrix}
u_1^*x\\
u_2^*x\\
\vdots\\
u_n^*x
\end{bmatrix}.
\]

Each entry \(u_i^*x\) is an inner product of \(x\) with a unit eigenvector \(u_i\). Therefore \(U^*x\) gives the coordinates of \(x\) with respect to the orthonormal eigenbasis of \(A\).

The instructor denotes

\[
y = U^*x.
\]

Then

\[
x^*Ax
= x^*U\Lambda U^*x
= y^*\Lambda y.
\]

Since \(U\) is unitary, it preserves norm:

\[
\|U^*x\| = \|x\|.
\]

Thus, if \(x \neq 0\), then \(y=U^*x \neq 0\). Equivalently, \(U^*\) has trivial null space because it is full rank.

## Positive Definite Matrices

A Hermitian matrix \(A\) is positive definite if all its eigenvalues are strictly positive:

\[
\lambda_i > 0 \quad \text{for all } i.
\]

The identity matrix is an example of a positive definite matrix.

The lecture states the equivalent quadratic-form definition:

\[
A \succ 0
\quad \Longleftrightarrow \quad
x^*Ax > 0 \text{ for every } x \neq 0.
\]

The condition \(x \neq 0\) is essential. At the origin,

\[
0^*A0 = 0,
\]

so strict positivity cannot hold for every vector including \(0\).

### Proof Idea: Eigenvalues Positive Implies Quadratic Form Positive

Assume \(A\) is Hermitian and all eigenvalues are positive. Use the unitary diagonalization

\[
A = U\Lambda U^*.
\]

Let

\[
y = U^*x.
\]

Then

\[
x^*Ax = y^*\Lambda y.
\]

Because \(\Lambda\) is diagonal,

\[
y^*\Lambda y
= \sum_{i=1}^n \lambda_i |y_i|^2.
\]

Here:

- every \(\lambda_i > 0\);
- every \(|y_i|^2 \geq 0\);
- if \(x \neq 0\), then \(y \neq 0\), so at least one \(|y_i|^2 > 0\).

Therefore the sum is strictly positive:

\[
x^*Ax > 0
\quad \text{for every } x \neq 0.
\]

The instructor notes that this proves one implication: positive eigenvalues imply positivity of the quadratic form. The reverse implication can be checked by evaluating the quadratic form along eigenvector directions.

### Eigenvector Direction Check

Let \(u_i\) be the eigenvector corresponding to \(\lambda_i\). In matrix form,

\[
u_i = Ue_i,
\]

where \(e_i\) is the standard basis vector with a \(1\) in the \(i\)-th position and zeros elsewhere.

Multiplying \(U\) by \(e_i\) picks out the \(i\)-th column of \(U\), which is \(u_i\).

If \(x=u_i=Ue_i\), then

\[
y = U^*x = U^*Ue_i = e_i.
\]

So

\[
x^*Ax
= e_i^*\Lambda e_i
= \lambda_i.
\]

Thus, along an eigenvector direction, the value of the quadratic form is exactly the corresponding eigenvalue. This explains why the eigenvalue signs directly determine the sign behavior of \(x^*Ax\).

The instructor remarks that there was some notation confusion during this derivation, but the key idea is: choosing \(x\) in an eigenvector direction isolates the corresponding eigenvalue.

## Positive Semidefinite Matrices

A Hermitian matrix \(A\) is positive semidefinite if all eigenvalues are nonnegative:

\[
\lambda_i \geq 0 \quad \text{for all } i.
\]

Equivalently,

\[
x^*Ax \geq 0
\quad \text{for every } x.
\]

The instructor warns that this is not the same as positive definite. The slide or expression with eigenvalue condition \(\lambda_i \geq 0\) corresponds to positive semidefinite, not positive definite.

The difference is that positive semidefinite matrices may have zero eigenvalues. If \(A\) has a zero eigenvalue, then there can be nonzero vectors in the null space of \(A\). For such nonzero vectors,

\[
x^*Ax = 0.
\]

Therefore, in the positive semidefinite definition, one does not require \(x \neq 0\) and strict positivity. The statement is simply nonnegativity for all \(x\).

Relationships:

- Positive definite matrices are a subset of positive semidefinite matrices.
- Positive definite matrices are exactly the full-rank, invertible positive semidefinite matrices.
- A zero eigenvalue means rank deficiency.
- A zero eigenvalue corresponds to a nontrivial null space.
- Positive semidefinite matrices can be non-invertible.

## Negative Definite and Negative Semidefinite Matrices

The negative counterparts are defined by reversing the signs.

A Hermitian matrix is negative definite if all eigenvalues are strictly negative:

\[
\lambda_i < 0 \quad \text{for all } i.
\]

A Hermitian matrix is negative semidefinite if all eigenvalues are nonpositive:

\[
\lambda_i \leq 0 \quad \text{for all } i.
\]

Here, nonpositive means each eigenvalue is either negative or zero.

Relationships:

- Negative definite matrices are a subset of negative semidefinite matrices.
- Negative definite matrices are invertible negative semidefinite matrices.
- Negative semidefinite matrices may have zero eigenvalues and therefore may be non-invertible.

## Indefinite Hermitian Matrices

If a Hermitian matrix has a mixture of positive and negative eigenvalues, it is indefinite.

An example is a Hermitian matrix with eigenvalues \(1\) and \(-1\), such as

\[
\begin{bmatrix}
1 & 0\\
0 & -1
\end{bmatrix}.
\]

This matrix is neither positive semidefinite nor negative semidefinite, because it has both signs among its eigenvalues.

The instructor asks why these subclasses matter. The answer is that eigenvalue signs determine the geometry of multivariable quadratic functions.

## Single-Variable Quadratic Functions as Motivation

The lecture then reviews a single-variable quadratic function:

\[
f(x)=ax^2+bx+c.
\]

The coefficient \(a\), which multiplies \(x^2\), is the critical parameter for the general shape of the function:

- \(a>0\): parabola opens upward;
- \(a<0\): parabola opens downward;
- \(a=0\): the function becomes a line \(bx+c\).

The coefficients \(b\) and \(c\) affect shifts:

- \(b\) changes the horizontal location of the optimum;
- \(c\) shifts the function vertically;
- together they affect where the minimum or maximum occurs and what value it takes.

But the main parabola-up or parabola-down shape is determined by \(a\).

### Convex and Concave Functions

For \(a>0\), the quadratic function is convex. It has a global minimum.

For \(a<0\), the quadratic function is concave. It has a global maximum.

The instructor gives the geometric chord definitions:

- A function is convex if, when any two points on the function are connected by a line segment, that line segment lies above the function.
- A function is concave if the line segment between any two points lies below the function.

For \(a=0\), the function is affine:

\[
f(x)=bx+c.
\]

A line is both convex and concave, because the chord between any two points on the line lies exactly on the function.

Convex and concave quadratics are important in optimization because they have simple global behavior. A convex quadratic has a single global minimum. A concave quadratic has a single global maximum.

## Quadratic Approximation and Taylor Series

The instructor relates quadratic functions to optimization of general nonlinear functions. A general nonlinear function can have many peaks, valleys, and local structures. To optimize it, one often builds a local quadratic approximation around a point.

Taylor series expansion is one way to obtain such a local approximation. Suppose the original function is \(g(x)\) and we approximate it around \(x_0\). The Taylor expansion uses derivative information at \(x_0\):

- the function value at \(x_0\);
- the first derivative at \(x_0\), which gives the local slope;
- the second derivative at \(x_0\), which gives curvature;
- higher derivatives if included.

The instructor assumes, for the Taylor series discussion, that \(g\) is infinitely differentiable.

For a single-variable function, the local expansion around \(x_0\) has the form

\[
g(x)
= g(x_0)
+ g'(x_0)(x-x_0)
+ \frac{1}{2}g''(x_0)(x-x_0)^2
+ \cdots.
\]

Keeping terms through the second derivative gives a quadratic approximation. The approximation is built entirely from local derivative information at \(x_0\), so its reliability is tied to how close \(x\) stays to \(x_0\).

The first derivative gives the slope of the tangent line. At a local minimum or local maximum, the tangent slope is zero.

The second derivative gives curvature:

- positive second derivative: locally parabola-up behavior, convex approximation;
- negative second derivative: locally parabola-down behavior, concave approximation.

Taylor approximations are local and are most accurate for small deviations around \(x_0\). The instructor notes that one can also fit a quadratic approximation over a chosen region if one wants a better approximation on that region rather than only an infinitesimal neighborhood.

### Warning About Zero Slope and Saddle-Like Points

A zero first derivative does not automatically mean a local minimum or maximum. The instructor gives the idea of a point with zero slope but curvature behavior changing around it. Such a point is saddle-like rather than a true local optimum.

In the instructor's sketch, the slope at the point is zero, but one side has negative curvature while the other side has positive curvature. The warning is that the first derivative test alone is not enough: zero slope can occur at points that are neither minima nor maxima.

The lecture mentions that, in multivariable settings, saddle points become important. In optimization, there are terms such as attraction to saddles, and one often wants to avoid converging to saddle points when searching for maxima or minima.

## Two-Variable Real Quadratic Functions

The lecture then moves to real-valued quadratic functions of two real variables:

\[
f(x_1,x_2)
= ax_1^2 + bx_1x_2 + cx_2^2 + ex_1 + fx_2 + d.
\]

The terms are:

- \(ax_1^2\): square term in \(x_1\);
- \(cx_2^2\): square term in \(x_2\);
- \(bx_1x_2\): cross term or product term;
- \(ex_1+fx_2\): linear terms;
- \(d\): constant term.

The constant term \(d\) shifts the graph up or down. It does not change the shape.

The linear terms \(ex_1\) and \(fx_2\) shift the function in the domain. They affect where the optimum is located, but they do not determine the basic quadratic shape.

To focus on the shape, the instructor first removes the linear terms and studies the quadratic part. The instructor also first studies the case where the cross term coefficient \(b\) is zero.

## Two-Variable Quadratic With No Cross Term

Assume \(b=0\) and ignore the linear terms. Then

\[
f(x_1,x_2)=ax_1^2+cx_2^2+d.
\]

This can be written in matrix notation as

\[
f(x)=x^TAx+d,
\]

where

\[
x=
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix},
\qquad
A=
\begin{bmatrix}
a & 0\\
0 & c
\end{bmatrix}.
\]

This matrix is real symmetric, hence Hermitian. Its eigenvalues are simply \(a\) and \(c\).

### Case 1: \(a>0\), \(c>0\)

If both \(a\) and \(c\) are positive, then \(A\) is positive definite.

The corresponding quadratic surface is parabola-up in every direction. Any slice through the surface in any direction looks like an upward-opening parabola. The function is convex and has bowl-like geometry.

The instructor notes that if one walks in any direction on the surface, one sees parabola-up behavior in that direction.

### Case 2: \(a<0\), \(c<0\)

If both \(a\) and \(c\) are negative, then \(A\) is negative definite.

The quadratic surface is concave, shaped like an upside-down bowl or dome. It has a single optimal point, now a maximum rather than a minimum.

### Case 3: One Eigenvalue Positive and One Negative

If one of \(a,c\) is positive and the other is negative, then \(A\) is indefinite.

In one coordinate direction, the function behaves like a parabola up. In the other coordinate direction, it behaves like a parabola down. This creates a saddle surface.

Such a function is neither convex nor concave.

The instructor emphasizes that this saddle structure is a new richness that appears in multivariable quadratic functions and does not occur in the same way for single-variable quadratics.

### Instructor Remark on Generated Plots

The instructor remarks that some surface plots shown in lecture were generated by asking an early GPT model, around GPT-3 or GPT-3.5 and around late 2022, to write Python code for a convex two-variable quadratic plot. This remark was not mathematically central, but it explained how the plotted surfaces were produced.

## Two-Variable Quadratic With a Cross Term

Now consider \(b \neq 0\):

\[
f(x_1,x_2)=ax_1^2+bx_1x_2+cx_2^2.
\]

The cross term \(bx_1x_2\) adds coupling between the two coordinate directions.

The instructor asks what \(b\) does. A student suggests that it should rotate the oval or contour. The instructor agrees: the cross term corresponds to a rotation of the principal axes in the domain.

However, \(b\) also affects the eigenvalues. When \(b=0\), the eigenvalues are simply \(a\) and \(c\). When \(b \neq 0\), the eigenvalues depend on all three coefficients \(a,b,c\), not just \(a\) and \(c\).

The instructor also warns that a plot can hide this distinction if the curvatures are too close to each other. A larger eigenvalue means the surface rises faster in that principal direction; a smaller eigenvalue means a flatter parabola-up direction. The cross term changes the principal directions and can change those curvature values.

Main effects of the cross term:

- it rotates the principal axes;
- the principal axes are no longer aligned with the coordinate axes;
- the curvatures are determined by the eigenvalues of the associated symmetric matrix;
- those eigenvalues depend on \(a,b,c\).

## Matrix Representation of the Cross Term

The quadratic form can be represented by a symmetric matrix:

\[
A=
\begin{bmatrix}
a & b/2\\
b/2 & c
\end{bmatrix}.
\]

Then

\[
x^TAx
= ax_1^2 + \frac{b}{2}x_1x_2 + \frac{b}{2}x_2x_1 + cx_2^2
= ax_1^2 + bx_1x_2 + cx_2^2.
\]

The two off-diagonal terms each contribute half of the cross term.

The instructor points out that this symmetric choice is not the only possible matrix representation. For the same quadratic expression, the off-diagonal entries only need to sum to \(b\). For example, one could choose one off-diagonal entry to be \(b\) and the other to be \(0\). There are infinitely many matrices that give the same quadratic form.

Equivalently, the allowable off-diagonal choices form a line of possibilities: if the \((1,2)\) entry is \(r\) and the \((2,1)\) entry is \(s\), then any pair with \(r+s=b\) produces the same \(bx_1x_2\) term. The symmetric choice \(r=s=b/2\) is selected for analysis, not because the quadratic expression forces it uniquely.

But choosing the symmetric matrix is helpful because:

- it is Hermitian in the real case;
- its eigenvalues are real;
- it is diagonalizable by an orthogonal matrix;
- the eigenvectors give meaningful principal directions;
- the analysis becomes easier.

## Symmetric and Skew-Symmetric Decomposition

The instructor gives an important decomposition for any real square matrix \(A\):

\[
A = \frac{A+A^T}{2} + \frac{A-A^T}{2}.
\]

The first part,

\[
\frac{A+A^T}{2},
\]

is symmetric.

The second part,

\[
\frac{A-A^T}{2},
\]

is skew-symmetric, because its transpose equals its negative.

This decomposition is algebraically simple because adding the two parts cancels the \(A^T\) terms and leaves \(A\).

### Why the Skew-Symmetric Part Does Not Matter for \(x^TAx\)

Let

\[
K = \frac{A-A^T}{2}.
\]

Then \(K^T=-K\), so \(K\) is skew-symmetric.

For the quadratic form,

\[
x^TKx
\]

is a scalar. A scalar equals its own transpose:

\[
x^TKx = (x^TKx)^T.
\]

But

\[
(x^TKx)^T = x^TK^Tx = x^T(-K)x = -x^TKx.
\]

Therefore

\[
x^TKx = -x^TKx,
\]

so

\[
x^TKx = 0.
\]

Thus the skew-symmetric component contributes nothing to the quadratic form. Only the symmetric component matters:

\[
x^TAx = x^T\left(\frac{A+A^T}{2}\right)x.
\]

This justifies always choosing the symmetric matrix representation for real quadratic forms.

## Orthogonal Diagonalization of the Symmetric Matrix

For a real symmetric matrix \(A\), there exists a real orthogonal matrix \(Q\) such that

\[
A = Q\Lambda Q^T.
\]

Here:

- \(Q\) is real orthogonal;
- \(Q^TQ=I\) and \(QQ^T=I\);
- the columns of \(Q\) are orthonormal eigenvectors of \(A\);
- \(\Lambda\) is the diagonal matrix of eigenvalues.

This is the real version of unitary diagonalization. In the real symmetric case, the unitary matrix becomes a real orthogonal matrix.

## Change of Coordinates to the Eigenbasis

Substitute

\[
A=Q\Lambda Q^T
\]

into the quadratic form:

\[
x^TAx
=x^TQ\Lambda Q^Tx.
\]

Define

\[
z=Q^Tx.
\]

Then

\[
x^TAx = z^T\Lambda z.
\]

As with \(U^*x\) earlier, \(Q^Tx\) gives coordinates of \(x\) in the orthonormal eigenbasis.

If

\[
Q=[q_1 \ q_2 \ \cdots \ q_n],
\]

then

\[
Q^Tx=
\begin{bmatrix}
q_1^Tx\\
q_2^Tx\\
\vdots\\
q_n^Tx
\end{bmatrix}.
\]

Each entry \(q_i^Tx\) is the inner product of \(x\) with a unit eigenvector \(q_i\), so it is the projection coefficient of \(x\) along \(q_i\). These entries are the coordinates of \(x\) with respect to the normalized eigenbasis.

In the new coordinates,

\[
z^T\Lambda z
= \lambda_1 z_1^2+\lambda_2 z_2^2+\cdots+\lambda_n z_n^2.
\]

There are no cross terms. The change of basis to eigenvector coordinates eliminates cross terms.

Geometric meaning:

- the original \(x_1,x_2\) axes are the natural coordinate axes in which the quadratic was first written;
- the \(q_1,q_2\) axes are eigenvector directions;
- in the eigenvector coordinates, the curvature in direction \(q_i\) is \(\lambda_i\);
- if \(\lambda_i>0\), the surface curves upward in direction \(q_i\);
- if \(\lambda_i<0\), the surface curves downward in direction \(q_i\).

The instructor notes that in a drawing, the eigenvectors may not visually look orthogonal or unit length because of the perspective of the picture, but mathematically they are assumed to be unit vectors at \(90^\circ\).

## Example: Matrix With Rotated Principal Directions

The lecture uses the matrix

\[
A=
\begin{bmatrix}
5 & 4\\
4 & 5
\end{bmatrix}.
\]

The off-diagonal entries are \(4\), so in the convention

\[
A=
\begin{bmatrix}
a & b/2\\
b/2 & c
\end{bmatrix},
\]

this corresponds to a mixed-term coefficient \(b=8\) in \(x^TAx\). The instructor describes the off-diagonal entries as the cross-term entries.

### Eigenvector \([1,1]^T\)

Compute:

\[
A
\begin{bmatrix}
1\\
1
\end{bmatrix}
=
\begin{bmatrix}
5+4\\
4+5
\end{bmatrix}
=
\begin{bmatrix}
9\\
9
\end{bmatrix}
=
9
\begin{bmatrix}
1\\
1
\end{bmatrix}.
\]

Therefore

\[
\begin{bmatrix}
1\\
1
\end{bmatrix}
\]

is an eigenvector with eigenvalue \(9\).

### Eigenvector \([1,-1]^T\)

Compute:

\[
A
\begin{bmatrix}
1\\
-1
\end{bmatrix}
=
\begin{bmatrix}
5-4\\
4-5
\end{bmatrix}
=
\begin{bmatrix}
1\\
-1
\end{bmatrix}.
\]

Therefore

\[
\begin{bmatrix}
1\\
-1
\end{bmatrix}
\]

is an eigenvector with eigenvalue \(1\).

The normalized versions of these vectors form the orthonormal eigenbasis.

### Curvature Interpretation

In the \([1,1]^T\) direction, the curvature is \(9\).

In the \([1,-1]^T\) direction, the curvature is \(1\).

So the function rises much faster in the \([1,1]^T\) direction than in the \([1,-1]^T\) direction. The principal curvature directions are rotated relative to the original coordinate axes.

## Level Sets and Contours of Quadratic Functions

The lecture then introduces level sets.

For a function \(f\), the level set at value \(\alpha\) is

\[
\{x : f(x)=\alpha\}.
\]

It is the set of domain points that produce the same function value. The instructor also calls these:

- contours;
- preimages of a function value;
- regions in the domain where the function achieves a constant output.

Geometrically, for a two-variable function whose graph is a surface in three dimensions, choosing a level value \(\alpha\) is like slicing the surface with a plane parallel to the domain. The intersection corresponds to the points whose function value is \(\alpha\). Looking down at the domain gives the contour or level set.

For positive definite or negative definite quadratic functions, level sets are ellipses in two dimensions and ellipsoids or hyperellipses in higher dimensions, when the chosen level value is compatible with the sign of the function. For a positive definite quadratic form, negative levels are empty and the zero level is only the origin. For a negative definite quadratic form, the analogous nonempty ellipses occur for negative levels, with the zero level again at the origin when no shifts are included.

## Level Set Example: Equal Eigenvalues

Consider

\[
A=
\begin{bmatrix}
9 & 0\\
0 & 9
\end{bmatrix}.
\]

Then

\[
f(x_1,x_2)=9x_1^2+9x_2^2.
\]

The level set equation is

\[
9x_1^2+9x_2^2=\alpha.
\]

If \(\alpha<0\), the level set is empty, because \(f(x_1,x_2)\geq 0\) for every point.

If \(\alpha=0\), the only point in the level set is the origin:

\[
(x_1,x_2)=(0,0).
\]

If \(\alpha>0\), divide by \(9\):

\[
x_1^2+x_2^2=\frac{\alpha}{9}.
\]

This is a circle centered at the origin with radius

\[
\frac{\sqrt{\alpha}}{3}.
\]

The intersections with the coordinate axes occur at

\[
x_1=\pm \frac{\sqrt{\alpha}}{3}
\]

when \(x_2=0\), and similarly for \(x_2\) when \(x_1=0\).

Because the eigenvalues are equal, the curvature is the same in both coordinate directions and the level sets are circles.

## Level Set Example: Different Eigenvalues

Now consider a diagonal positive definite matrix with eigenvalues \(9\) and \(1\):

\[
f(x_1,x_2)=9x_1^2+x_2^2.
\]

The level set equation is

\[
9x_1^2+x_2^2=\alpha.
\]

For \(x_2=0\),

\[
9x_1^2=\alpha,
\]

so

\[
x_1=\pm \frac{\sqrt{\alpha}}{3}.
\]

For \(x_1=0\),

\[
x_2^2=\alpha,
\]

so

\[
x_2=\pm \sqrt{\alpha}.
\]

The level set is not a circle. It is an ellipse. The axis in the \(x_2\) direction is longer because the coefficient/eigenvalue in that direction is smaller. Smaller curvature allows the level set to extend farther before reaching the same function value.

## Principal Semi-Axes of an Ellipse

The instructor defines principal semi-axes using distance from the center of the ellipse.

The first principal semi-axis is the direction from the center in which the ellipse reaches the largest distance, or largest radius.

The second principal semi-axis is the next orthogonal direction in which the ellipse reaches the largest distance after the first direction is fixed.

The orthogonality requirement matters. Without requiring the next direction to be orthogonal, many nearby directions could also have large distances from the center.

For a diagonal positive definite matrix, the ellipse's principal semi-axes align with the coordinate axes.

For a non-diagonal matrix, the ellipse is rotated. Its principal semi-axes no longer align with the original coordinate axes. Instead, they align with the eigenvectors of the symmetric matrix defining the quadratic form.

The instructor says this will be derived and examined more fully in the next lecture.

## Relationships Between the Main Concepts

Hermitian matrices connect algebra to geometry through quadratic forms:

\[
A=A^*
\quad \Rightarrow \quad
x^*Ax \in \mathbb{R}.
\]

Unitary diagonalization connects eigenvalues to the quadratic form:

\[
A=U\Lambda U^*,
\qquad
y=U^*x,
\qquad
x^*Ax=y^*\Lambda y.
\]

The coordinate vector \(y=U^*x\) is the representation of \(x\) in the orthonormal eigenbasis.

Eigenvalue signs determine quadratic-form signs:

- all \(\lambda_i>0\): \(x^*Ax>0\) for \(x\neq 0\);
- all \(\lambda_i\geq 0\): \(x^*Ax\geq 0\) for all \(x\);
- all \(\lambda_i<0\): \(x^*Ax<0\) for \(x\neq 0\);
- all \(\lambda_i\leq 0\): \(x^*Ax\leq 0\) for all \(x\);
- mixed signs: the quadratic form can be positive in some directions and negative in others.

Eigenvalue signs determine shape:

- positive definite: convex bowl;
- negative definite: concave dome;
- indefinite: saddle;
- semidefinite: flat directions may occur because of zero eigenvalues.

Eigenvectors determine directions:

- in the original coordinates, cross terms may appear;
- in the eigenvector coordinates, cross terms disappear;
- the eigenvectors give the principal directions;
- the eigenvalues give curvature along those directions.

Level sets reflect the same structure:

- equal positive eigenvalues produce circular level sets;
- unequal positive eigenvalues produce ellipses;
- non-diagonal symmetric matrices produce rotated ellipses;
- eigenvectors align with principal semi-axes;
- eigenvalues determine how stretched the ellipse is in each principal direction.

## Instructor Warnings and Study Remarks

The instructor specifically warns about the distinction between positive definite and positive semidefinite:

- positive definite requires \(\lambda_i>0\) and \(x^*Ax>0\) for \(x\neq 0\);
- positive semidefinite allows \(\lambda_i=0\) and only requires \(x^*Ax\geq 0\).

The instructor also emphasizes that zero eigenvalues mean rank deficiency and non-invertibility.

Another important warning is that a quadratic form can be represented by many matrices if the matrix is not required to be symmetric. For analysis, use the symmetric or Hermitian representative because the skew-symmetric part contributes zero to \(x^TAx\).

The instructor asks students to review positive definite matrices, semidefinite matrices, and quadratic functions before the next lecture so the class can continue with the derivation and geometry of ellipses and ellipsoids.

## Source and Coverage Note

These notes were created only from `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture13_corrected.md`. They cover the full lecture 13 transcript in chronological order, including definitions, proof ideas, examples, instructor remarks, warnings, and concept relationships. No other lecture transcript was processed, and no audit or exam files were created.
