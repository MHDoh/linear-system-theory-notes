# Lecture 03 Notes

## 1. Opening Recap: Vector Operations And Combinations

The lecture opens by connecting back to the previous lecture's geometric intuition for vectors and vector spaces.

Previously covered operations:

- Scaling a vector.
- Adding vectors.
- Forming a linear combination of vectors.

A linear combination is a weighted sum of multiple vectors. The instructor emphasizes that when the weights are restricted, special kinds of linear combinations arise.

Special combinations:

- Affine combination: a linear combination where the weights sum to 1.
- Convex combination: a more restricted affine combination where the weights sum to 1 and each weight is nonnegative.

Geometric interpretation of convex combinations:

- For two vectors or points, all convex combinations form the line segment connecting the two points.
- For three vectors or points, all convex combinations form the triangle whose vertices are those three vectors.
- For multiple vectors, all possible convex combinations define the higher-dimensional analogue of polygons in two dimensions. This is the idea behind the convex hull of a set of points.

Exam relevance:

- The transcript explicitly marks this discussion as a likely exam topic.
- The important relationship is that algebraic restrictions on linear combination weights produce geometric objects such as line segments, triangles, polygons, and their higher-dimensional analogues.

## 2. Euclidean Norm

The lecture then moves to an additional operation on vectors: the Euclidean norm.

The norm is introduced as a way to answer the question: how big is a vector? A vector can have many components, but the norm maps the vector to a single number measuring its size.

The instructor stresses that there are different possible definitions of "how big" a vector is. The Euclidean norm is only one choice, although it is the main reference norm at this stage of the course.

### 2.1 Euclidean Norm In Two Dimensions

For a two-dimensional vector

\[
x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix},
\]

the Euclidean norm is the distance from the point \(x\) to the origin. Geometrically, it is the length of the arrow from the origin to the point \((x_1,x_2)\).

Using the right triangle with side lengths \(x_1\) and \(x_2\), the norm is

\[
\|x\| = \sqrt{x_1^2 + x_2^2}.
\]

The instructor notes that later the notation \(\|x\|_2\) may be used to distinguish the Euclidean norm from other norms. For now, when no special subscript is written, \(\|x\|\) means the Euclidean norm.

Properties visible from the definition:

- The norm maps a vector to a scalar.
- The scalar is nonnegative.
- Example: if \(x = (3,4)\), then \(\|x\| = 5\), the familiar 3-4-5 triangle.

### 2.2 Euclidean Norm In Three Dimensions

For a three-dimensional vector

\[
x = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix},
\]

the Euclidean norm is again interpreted as distance from the point to the origin.

Exam note from the transcript:

- The instructor explicitly discusses projecting the vector onto the \(x_1x_2\)-plane.

Derivation idea:

1. Project the vector onto the \(x_1x_2\)-plane.
2. In that plane, the first right triangle has side lengths \(x_1\) and \(x_2\).
3. The hypotenuse in the \(x_1x_2\)-plane has length

\[
\sqrt{x_1^2 + x_2^2}.
\]

4. A second right triangle uses that hypotenuse as one side and \(x_3\) as the other side.
5. Applying the Pythagorean theorem again gives

\[
\|x\| = \sqrt{x_1^2 + x_2^2 + x_3^2}.
\]

The three-dimensional formula extends the two-dimensional formula by squaring the additional coordinate, adding it to the sum, and taking the square root.

### 2.3 Distance Between Two Vectors

Once the norm is defined, geometric language becomes available.

The size of one vector is \(\|x\|\).

The distance between two vectors \(x\) and \(y\) is defined as the norm of their difference:

\[
d(x,y) = \|x-y\|.
\]

The difference vector \(x-y\) is itself a vector in the same space, so its norm measures how far apart \(x\) and \(y\) are.

Important relationship:

- The norm gives a notion of vector size.
- The norm of a difference vector gives a notion of distance between vectors.

The instructor warns that different norm definitions give different distance values. Therefore, optimization problems that minimize distances can produce different solutions depending on the chosen norm.

Instructor remark:

- A significant amount of signal processing and machine learning research has studied choices of norms, how they affect solution behavior, and what kinds of solutions they promote.

### 2.4 Why Euclidean Norm Is The Main Starting Point

The instructor describes the Euclidean norm as the "typical" norm in much of 20th-century signal processing, especially in engineering contexts.

Reasons for its popularity:

- It is convenient.
- It is easy to handle analytically.
- It often allows closed-form solutions.
- It can avoid iterative computations in many settings.

The instructor also notes that other norms are useful for different purposes and became heavily used in later parts of the 20th century, especially in different applications of signal processing and machine learning.

Course trajectory:

- The Euclidean norm is the main reference for now.
- Later the course will generalize the norm concept and study alternatives.

### 2.5 Euclidean Norm In Higher Dimensions

The instructor identifies the extension beyond three dimensions as a major conceptual leap.

In four-dimensional real space, or in a 2000-dimensional real space, a vector cannot be drawn and measured with a ruler. However, the formula can still be extended as a definition.

For

\[
x = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \in \mathbb{R}^n,
\]

the Euclidean norm is

\[
\|x\| = \sqrt{x_1^2 + x_2^2 + \cdots + x_n^2}
      = \sqrt{\sum_{i=1}^n x_i^2}.
\]

Important instructor remark:

- In dimensions higher than three, this is a definition, not a geometric derivation from a drawing.
- We are assigning geometric properties such as size and distance to objects we cannot draw.

The resulting setting is called \(n\)-dimensional Euclidean space equipped with the Euclidean norm.

Even though high-dimensional vectors cannot be drawn, the instructor encourages thinking by analogy with two- and three-dimensional pictures.

### 2.6 Fundamental Properties Of The Euclidean Norm

The Euclidean norm satisfies several key properties.

Nonnegativity:

\[
\|x\| \ge 0.
\]

This follows because the norm squares the components, sums nonnegative quantities, and then takes a square root.

Definiteness:

\[
\|x\| = 0 \quad \text{if and only if} \quad x = 0.
\]

Any vector other than the origin has at least one nonzero component. Squaring that component gives a positive term in the sum, so the norm cannot be zero.

Homogeneity under scalar multiplication:

\[
\|\alpha x\| = |\alpha| \|x\|.
\]

The absolute value is important. Multiplying by a negative scalar reverses orientation, but length is scaled by the magnitude of the scalar.

Triangle inequality:

\[
\|x+y\| \le \|x\| + \|y\|.
\]

Geometric interpretation:

- If \(x\) and \(y\) are placed tip-to-tail, then \(x+y\) is the third side of the triangle.
- The length of one side of a triangle is no larger than the sum of the other two side lengths.

Equality case mentioned in lecture:

- Equality occurs when \(x\) and \(y\) are collinear and point in the same direction.

Exam relevance:

- The transcript explicitly marks the generalization of norm properties as a likely exam topic.
- The instructor emphasizes that the Euclidean norm is only one norm satisfying these properties. Later, other norms satisfying analogous norm properties will be introduced.

## 3. Inner Product, Angles, And Orthogonality

After size and distance, the next geometric concept introduced is angle between vectors.

In two dimensions, the angle between vectors can be drawn directly. The instructor asks how this concept can be extended to arbitrary-dimensional real spaces, such as spaces of thousand-dimensional vectors.

The key tool is the Euclidean inner product.

Exam note:

- The transcript explicitly marks the connection between angles and orthogonality as exam-relevant.

### 3.1 Orthogonality Motivation

Once angle is available, orthogonality becomes available.

Definition from geometry:

- Two vectors are orthogonal if the angle between them is \(90^\circ\).

Goal:

- Extend the notion of orthogonality to higher-dimensional vector spaces.

The instructor emphasizes that inner products are choices. The Euclidean inner product is the standard initial choice, but later other inner products will be introduced.

Important relationship:

- Different inner products can define different geometries.
- Two vectors may be orthogonal with respect to one inner product but not orthogonal with respect to another.
- Orthogonality is therefore relative to the chosen inner product.

### 3.2 Euclidean Inner Product In Two Dimensions

For

\[
x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix},
\qquad
y = \begin{bmatrix} y_1 \\ y_2 \end{bmatrix},
\]

the Euclidean inner product is

\[
\langle x,y\rangle = x_1y_1 + x_2y_2.
\]

The operation:

- Takes two vector inputs.
- Produces one scalar output in the real case.
- Is formed by multiplying matching-index components and summing the products.

Extension to \(n\)-dimensional real vectors:

For

\[
x =
\begin{bmatrix}
x_1\\
x_2\\
\vdots\\
x_n
\end{bmatrix},
\qquad
y =
\begin{bmatrix}
y_1\\
y_2\\
\vdots\\
y_n
\end{bmatrix},
\]

the Euclidean inner product is

\[
\langle x,y\rangle
= x_1y_1+x_2y_2+\cdots+x_ny_n
= \sum_{i=1}^n x_i y_i.
\]

This is the same extension pattern as the Euclidean norm: start from the two- and three-dimensional geometric picture, then use the component formula as the definition in dimensions that cannot be drawn.

For complex vectors, the instructor notes that the output can be complex and the definition requires modifications later.

Important warning:

- The inner product output is not necessarily nonnegative.
- In the real case, \(\langle x,y\rangle\) can be positive, zero, or negative.

### 3.3 Norm Induced By Inner Product

Exam note:

- The transcript explicitly marks the relationship between inner product and norm as exam-relevant.

If a vector is inner-producted with itself, then

\[
\langle x,x\rangle = x_1x_1 + x_2x_2 = x_1^2 + x_2^2.
\]

Since the Euclidean norm satisfies

\[
\|x\| = \sqrt{x_1^2 + x_2^2},
\]

we have

\[
\langle x,x\rangle = \|x\|^2.
\]

Therefore,

\[
\|x\| = \sqrt{\langle x,x\rangle}.
\]

Terminology:

- The Euclidean norm is induced by the Euclidean inner product.
- This means the norm can be derived from the inner product by taking the inner product of a vector with itself and then taking the square root.

Important relationship:

- Defining an inner product automatically gives a way to define a norm, provided the positivity and definiteness requirements hold.

### 3.4 Deriving The Angle Formula From Inner Product

The instructor derives the connection between the inner product and the angle between two vectors.

Let \(\theta\) be the angle between \(x\) and \(y\).

Geometric setup:

- Consider the triangle formed by \(x\), \(y\), and the difference vector \(x-y\).
- The side corresponding to the difference vector has length \(\|x-y\|\).
- Drop an orthogonal projection so that right triangles appear in the picture.

Using the right-triangle decomposition:

- One side has length \(\|x\|\sin\theta\).
- Another side has length \(\|y\|-\|x\|\cos\theta\).

Applying the Pythagorean theorem gives

\[
\|x-y\|^2
= \|x\|^2\sin^2\theta
  + \left(\|y\|-\|x\|\cos\theta\right)^2.
\]

Expanding:

\[
\|x-y\|^2
= \|x\|^2\sin^2\theta
 + \|y\|^2
 -2\|x\|\|y\|\cos\theta
 + \|x\|^2\cos^2\theta.
\]

Using

\[
\sin^2\theta+\cos^2\theta=1,
\]

this becomes

\[
\|x-y\|^2
= \|x\|^2 + \|y\|^2 - 2\|x\|\|y\|\cos\theta.
\]

This is the law of cosines in vector notation.

Now write the left side using the inner product:

\[
\|x-y\|^2 = \langle x-y, x-y\rangle.
\]

Using bilinearity of the real inner product:

\[
\langle x-y, x-y\rangle
= \langle x,x\rangle - \langle x,y\rangle
  - \langle y,x\rangle + \langle y,y\rangle.
\]

For the real Euclidean inner product, \(\langle x,y\rangle=\langle y,x\rangle\), so

\[
\|x-y\|^2
= \|x\|^2 - 2\langle x,y\rangle + \|y\|^2.
\]

Matching this with the law-of-cosines expression gives

\[
\langle x,y\rangle = \|x\|\|y\|\cos\theta.
\]

Therefore,

\[
\cos\theta
= \frac{\langle x,y\rangle}{\|x\|\|y\|}.
\]

Important relationship:

- The inner product does not directly give the angle.
- The inner product, together with the induced norms, gives the cosine of the angle.

### 3.5 Orthogonality From Inner Product

If the angle between two vectors is \(90^\circ\), then

\[
\cos 90^\circ = 0.
\]

Using the angle formula,

\[
\langle x,y\rangle = \|x\|\|y\|\cos\theta,
\]

orthogonality implies

\[
\langle x,y\rangle = 0.
\]

Definition extended from geometry:

\[
x \perp y
\quad \text{if and only if} \quad
\langle x,y\rangle = 0.
\]

Example from the lecture:

Let

\[
x = \begin{bmatrix}3\\4\end{bmatrix},
\qquad
y = \begin{bmatrix}-4\\3\end{bmatrix}.
\]

Then

\[
\langle x,y\rangle = 3(-4) + 4(3) = -12 + 12 = 0.
\]

Therefore the vectors are orthogonal, and the angle between them is \(90^\circ\).

### 3.6 Inner Product Signs And Angle Types

In two and three dimensions, and then by extension in \(n\)-dimensional space:

- If \(\langle x,y\rangle > 0\), then \(\cos\theta>0\), so the angle is acute.
- If \(\langle x,y\rangle < 0\), then \(\cos\theta<0\), so the angle is obtuse.
- If \(\langle x,y\rangle = 0\), then \(\cos\theta=0\), so the vectors are orthogonal.

In three dimensions, two non-collinear vectors span a plane, so the same two-dimensional picture applies inside that plane. The formula

\[
\cos\theta
= \frac{\langle x,y\rangle}{\|x\|\|y\|}
\]

again gives the cosine of the angle between the vectors.

In \(n\)-dimensional space, the same formula is adopted as the definition of the cosine of the angle between two nonzero vectors.

Warning:

- The angle formula requires \(x\) and \(y\) to be nonzero, because \(\|x\|\|y\|\) appears in the denominator.
- The orthogonality definition \(\langle x,y\rangle=0\) is the algebraic condition that extends cleanly to high-dimensional spaces; the angle interpretation comes from the cosine formula when both vectors are nonzero.

### 3.7 Need For The Cauchy-Schwarz Inequality

When defining

\[
\cos\theta
= \frac{\langle x,y\rangle}{\|x\|\|y\|}
\]

in high-dimensional space, the expression must always lie between \(-1\) and \(1\) to be a valid cosine value.

The required guarantee is the Cauchy-Schwarz inequality:

\[
|\langle x,y\rangle|
\le \|x\|\|y\|.
\]

This inequality ensures that

\[
-1
\le
\frac{\langle x,y\rangle}{\|x\|\|y\|}
\le
1
\]

whenever \(x\) and \(y\) are nonzero.

Instructor remark:

- Cauchy-Schwarz is used in many areas, including estimation theory.
- The instructor specifically mentions that the Cramer-Rao lower bound in estimation theory is obtained from the Cauchy-Schwarz inequality.
- The instructor also mentions a book containing multiple proofs of the Cauchy-Schwarz inequality.

### 3.8 Proof Idea For Cauchy-Schwarz

The proof begins with the fact that a squared norm is always nonnegative:

\[
\|u-v\|^2 \ge 0.
\]

Using the inner product induced norm:

\[
\|u-v\|^2 = \langle u-v,u-v\rangle.
\]

For real inner products, expand:

\[
\langle u-v,u-v\rangle
= \|u\|^2 - 2\langle u,v\rangle + \|v\|^2.
\]

Therefore,

\[
\|u\|^2 - 2\langle u,v\rangle + \|v\|^2 \ge 0.
\]

Rearranging:

\[
2\langle u,v\rangle
\le
\|u\|^2 + \|v\|^2.
\]

This is not yet Cauchy-Schwarz. It is an additive bound, because it bounds the inner product by a sum of squared norms.

Equivalently,

\[
\langle u,v\rangle
\le
\frac{\|u\|^2+\|v\|^2}{2}.
\]

The transcript includes a suggested alternative of completing the square. The instructor notes that algebraic manipulation may be possible, but then uses a simpler normalization trick.

The instructor's trick is to convert the additive bound into a multiplicative bound by normalizing the vectors.

Assume \(x\) and \(y\) are nonzero and choose

\[
u = \frac{x}{\|x\|},
\qquad
v = \frac{y}{\|y\|}.
\]

Then

\[
\|u\|=1,
\qquad
\|v\|=1.
\]

Substituting into the additive bound gives

\[
2\left\langle \frac{x}{\|x\|}, \frac{y}{\|y\|}\right\rangle
\le 1^2 + 1^2 = 2.
\]

So

\[
\left\langle \frac{x}{\|x\|}, \frac{y}{\|y\|}\right\rangle
\le 1.
\]

Because \(\|x\|\) and \(\|y\|\) are positive, multiply both sides by \(\|x\|\|y\|\):

\[
\langle x,y\rangle \le \|x\|\|y\|.
\]

To get the lower bound, replace one normalized vector by its negative, for example

\[
u = -\frac{x}{\|x\|},
\qquad
v = \frac{y}{\|y\|}.
\]

This gives

\[
-\langle x,y\rangle \le \|x\|\|y\|.
\]

Combining both inequalities yields

\[
|\langle x,y\rangle|
\le
\|x\|\|y\|.
\]

Thus Cauchy-Schwarz justifies using the quotient

\[
\frac{\langle x,y\rangle}{\|x\|\|y\|}
\]

as a cosine value in \(n\)-dimensional Euclidean space.

### 3.9 Properties Of The Inner Product

The instructor lists the main properties of the Euclidean inner product for real \(n\)-dimensional vectors.

Scaling in the first argument:

\[
\langle \alpha x,y\rangle = \alpha\langle x,y\rangle.
\]

Scaling in the second argument:

\[
\langle x,\beta y\rangle = \beta\langle x,y\rangle.
\]

Scaling both arguments:

\[
\langle \alpha x,\beta y\rangle
= \alpha\beta\langle x,y\rangle.
\]

There is no absolute value in these scaling rules. This differs from the norm homogeneity rule, where the scalar appears as \(|\alpha|\).

Additivity in the first argument:

\[
\langle x+z,y\rangle
= \langle x,y\rangle + \langle z,y\rangle.
\]

Additivity in the second argument:

\[
\langle x,y+z\rangle
= \langle x,y\rangle + \langle x,z\rangle.
\]

Linearity in each argument:

- If the second argument is fixed, the inner product is linear in the first argument.
- If the first argument is fixed, the inner product is linear in the second argument.

This is why, in the real case, the Euclidean inner product is bilinear.

Symmetry in the real Euclidean case:

\[
\langle x,y\rangle = \langle y,x\rangle.
\]

This symmetry is what makes the two cross terms in expansions such as

\[
\langle u-v,u-v\rangle
\]

combine into \(-2\langle u,v\rangle\). The instructor warns during the proof discussion that the complex case has deviations, so the real-vector formulas are the setting for this lecture.

Positivity:

\[
\langle x,x\rangle \ge 0.
\]

Definiteness:

\[
\langle x,x\rangle = 0
\quad \text{if and only if} \quad
x=0.
\]

These properties are required for the positive definite inner product setting used to induce a true norm.

### 3.10 Instructor Remarks On Inner Product Generalizations

A student asks whether all these properties are required for old and new inner products.

Instructor response, preserved in substance:

- These properties are required for the kind of inner product being used in the course.
- Some extensions exist, such as semidefinite families and indefinite spaces.
- The course will not go deeply into those extensions.
- Such extensions are nevertheless used in practice.

Important clarification:

- The condition \(\langle x,x\rangle = 0\) only when \(x=0\) is the definiteness property.
- It is needed for the induced norm to be positive definite.
- If this condition is removed, one obtains indefinite spaces rather than the positive definite normed spaces being used here.

Instructor example of where indefinite spaces appear:

- Relativity and related theories use indefinite spaces.

Exam relevance:

- The transcript explicitly marks this distinction as likely exam-relevant.

## 4. Hyperplanes And Half-Spaces From Inner Products

The lecture next uses inner products and orthogonality to define hyperplanes and half-spaces.

### 4.1 Hyperplane Through The Origin

The instructor begins with an incomplete hyperplane definition that applies to hyperplanes passing through the origin.

Let \(a\) be a vector. The vector \(a\) is the normal vector of the hyperplane.

The hyperplane defined by \(a\) is the collection of all vectors \(x\) orthogonal to \(a\):

\[
H_a = \{x : \langle x,a\rangle = 0\}.
\]

In two dimensions:

\[
H_a
=
\left\{
\begin{bmatrix}x_1\\x_2\end{bmatrix}
:
a_1x_1+a_2x_2=0
\right\}.
\]

Geometric interpretation in two dimensions:

- \(H_a\) is a line through the origin.
- The vector \(a\) is perpendicular to that line.
- All vectors lying on the line are orthogonal to \(a\).

Geometric interpretation in three dimensions:

- \(H_a\) is a plane through the origin.
- The vector \(a\) is normal to that plane.

The instructor emphasizes that this is not yet the complete hyperplane definition, because it only covers hyperplanes through the origin.

### 4.2 Positive And Negative Half-Spaces

Using the same normal vector \(a\), define a positive half-space:

\[
H_a^+ = \{x : \langle x,a\rangle > 0\}.
\]

These are vectors making an acute angle with \(a\).

Define a negative half-space:

\[
H_a^- = \{x : \langle x,a\rangle < 0\}.
\]

These are vectors making an obtuse angle with \(a\).

In two dimensions:

- The hyperplane \(H_a\) is a line.
- \(H_a^+\) is one side of the line.
- \(H_a^-\) is the other side of the line.

In three dimensions:

- The hyperplane \(H_a\) is a plane.
- The positive and negative half-spaces are the two sides of that plane.

Important relationship:

- The sign of the inner product with the normal vector identifies which side of the hyperplane a vector lies on.

### 4.3 General Hyperplanes With A Threshold

Exam note:

- The transcript explicitly marks the generalized hyperplane definition as exam-relevant.

The full hyperplane definition compares the inner product not necessarily to zero, but to a scalar threshold \(b\):

\[
H_{a,b} = \{x : \langle x,a\rangle = b\}.
\]

Here:

- \(a\) is the normal vector.
- \(b\) is a scalar threshold.
- If \(b=0\), the hyperplane passes through the origin.
- If \(b\ne 0\), the hyperplane is shifted away from the origin.

The instructor connects this to an earlier grade-threshold example:

- A passing/failing threshold can be represented by comparing an inner product to a nonzero value \(b\).
- The passing students and failing students lie on different sides of a threshold hyperplane.

The corresponding shifted half-spaces are

\[
H_{a,b}^+
=
\{x : \langle x,a\rangle > b\},
\]

and

\[
H_{a,b}^-
=
\{x : \langle x,a\rangle < b\}.
\]

The sign of \(\langle x,a\rangle-b\) determines which side of the shifted hyperplane \(x\) lies on. When \(b=0\), these reduce to the origin-centered half-space definitions \(H_a^+\) and \(H_a^-\).

### 4.4 Deriving The Shifted Hyperplane Form

Start from the origin hyperplane condition, but shift it by a vector \(x_0\):

\[
\langle x-x_0,a\rangle = 0.
\]

Using linearity:

\[
\langle x,a\rangle - \langle x_0,a\rangle = 0.
\]

Therefore

\[
\langle x,a\rangle = \langle x_0,a\rangle.
\]

Let

\[
b = \langle x_0,a\rangle.
\]

Then the shifted hyperplane is

\[
H_{a,b} = \{x : \langle x,a\rangle = b\}.
\]

Important interpretation:

- \(x_0\) is a shift vector.
- \(a\) remains the normal vector.
- \(b\) is the threshold quantity produced by the shift.

### 4.5 Projection Interpretation Of The General Hyperplane

The instructor says projection will be covered later, but gives a preview because of a student question.

For a vector \(x\) projected onto the direction of a vector \(a\), the projection vector is

\[
x_a
=
\frac{\langle x,a\rangle}{\langle a,a\rangle}a
=
\frac{\langle x,a\rangle}{\|a\|^2}a.
\]

Equivalently,

\[
x_a
=
\frac{\langle x,a\rangle}{\|a\|}
\frac{a}{\|a\|}.
\]

Here:

- \(\frac{a}{\|a\|}\) is the unit vector in the direction of \(a\).
- The signed projection length along \(a\) is \(\frac{\langle x,a\rangle}{\|a\|}\).
- The magnitude of the projection length is \(\frac{|\langle x,a\rangle|}{\|a\|}\).

Warning from the instructor:

- \(\langle x,a\rangle\) is not itself the projection length unless \(a\) is a unit vector.
- To obtain the projection length, divide by \(\|a\|\).
- The threshold \(b\) in \(\langle x,a\rangle=b\) is not automatically a projection length.

For all vectors \(x\) in \(H_{a,b}\):

\[
\langle x,a\rangle=b.
\]

Since \(a\) is fixed, all such vectors have the same projection component along \(a\). This is why \(H_{a,b}\) is a shifted line, plane, or higher-dimensional hyperplane.

Important clarification:

- In \(H_{a,b}\), the angle between \(x\) and \(a\) is not fixed.
- What is fixed is the orthogonal projection component of \(x\) along \(a\).
- A set of constant-angle vectors would not be the same object as this hyperplane.

### 4.6 Neuron As A Half-Space Test

Exam note:

- The transcript explicitly marks the neuron connection as exam-relevant.

The instructor connects hyperplanes and half-spaces to a neuron model with a threshold/nonlinearity.

For an input vector \(x\) and weight vector \(w\), the neuron computes an inner product:

\[
\langle x,w\rangle = w_1x_1+w_2x_2+\cdots+w_nx_n.
\]

Then it subtracts or compares to a threshold \(b\):

\[
\langle x,w\rangle - b > 0.
\]

Interpretation:

- The weights are synaptic weights.
- The weight vector \(w\) defines a direction in high-dimensional space.
- The threshold \(b\) shifts the separating hyperplane.
- The neuron checks whether the input vector lies in a particular half-space determined by \(w\) and \(b\).

Important relationship:

- A threshold neuron is geometrically a half-space classifier.
- The decision boundary is a hyperplane.
- The normal direction of the boundary is the weight vector.

The instructor says this example may be revisited later.

### 4.7 High-Dimensional Geometric Thinking

The instructor summarizes that inner products allow the course to extend geometric language into high-dimensional spaces:

- Cosine of angle.
- Acute angle.
- Obtuse angle.
- Orthogonality.
- Hyperplanes.
- Half-spaces.

Even when the space cannot be drawn, the signs and values of inner products allow us to reason as if the two- and three-dimensional geometric pictures still guide the intuition.

## 5. Matrix Multiplication As A Box Of Inner Products

The lecture then moves to matrix-vector and matrix-matrix operations.

Matrix multiplication is described as a "box of inner products."

For matrices

\[
A \in \mathbb{R}^{m\times n},
\qquad
B \in \mathbb{R}^{n\times p},
\]

the product

\[
C = AB
\]

has entries

\[
c_{ij}
=
\text{inner product of row } i \text{ of } A
\text{ with column } j \text{ of } B.
\]

Explicitly:

\[
c_{ij}
=
\sum_{k=1}^{n} a_{ik}b_{kj}.
\]

Dimension requirement:

- A row of \(A\) has length \(n\).
- A column of \(B\) has length \(n\).
- These dimensions must match so the inner product is defined.

This is the usual inner-dimension matching condition for matrix multiplication:

\[
(m\times n)(n\times p) = m\times p.
\]

Instructor example:

- The element \(c_{25}\) is the inner product of the second row of the first matrix with the fifth column of the second matrix.

Important relationship:

- Matrix multiplication is not an unrelated operation. It is built from many inner products arranged in matrix form.

## 6. Systems Of Linear Equations In Matrix Form

The instructor next explains why matrix multiplication is useful by writing systems of linear equations compactly.

Example system:

\[
2x_1 + 3x_2 = 10,
\]

\[
x_1 - x_2 = 10.
\]

The left-hand sides and right-hand sides can be boxed into column vectors:

\[
\begin{bmatrix}
2x_1+3x_2\\
x_1-x_2
\end{bmatrix}
=
\begin{bmatrix}
10\\
10
\end{bmatrix}.
\]

Each left-hand side is an inner product:

\[
2x_1+3x_2
=
\begin{bmatrix}2&3\end{bmatrix}
\begin{bmatrix}x_1\\x_2\end{bmatrix},
\]

\[
x_1-x_2
=
\begin{bmatrix}1&-1\end{bmatrix}
\begin{bmatrix}x_1\\x_2\end{bmatrix}.
\]

Therefore the system can be written as

\[
\begin{bmatrix}
2&3\\
1&-1
\end{bmatrix}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
=
\begin{bmatrix}
10\\
10
\end{bmatrix}.
\]

In compact notation:

\[
Ax=b.
\]

Interpretation:

- \(A\) is the known coefficient matrix.
- \(x\) is the vector of unknown variables.
- \(b\) is the known right-hand-side vector.

Instructor remark:

- Matrix notation separates known quantities from unknown variables.
- This compact notation becomes the starting point for studying linear algebra and matrix analysis.

## 7. Existence And Uniqueness Questions For \(Ax=b\)

Once systems are written as

\[
Ax=b,
\]

the course will ask fundamental questions.

Existence:

- Is there an \(x\) such that \(Ax=b\)?
- Can we find a vector \(x\) satisfying the given matrix \(A\) and right-hand side \(b\)?

Uniqueness:

- If a solution exists, is it unique?
- Are there alternative solutions?
- How large is the solution set?

Instructor question:

- Can a system of linear equations have exactly five solutions only?

The later vector-space analysis will show the typical classification:

- No solution.
- A unique solution.
- Infinitely many solutions.

The instructor says the course will study which types of matrices guarantee unique solutions and what properties of \(A\) and \(b\) characterize each case.

Important relationship:

- Some questions depend only on \(A\).
- Other questions depend on \(A\) together with \(b\).
- Vector space concepts will be used to answer these existence and uniqueness questions.

## 8. Geometric View: Equations As Hyperplanes

The lecture closes by connecting linear systems back to hyperplanes.

Each row of a linear system defines one scalar equation. For example,

\[
2x_1+3x_2=10
\]

defines a hyperplane. In two dimensions, that hyperplane is a line.

Likewise,

\[
x_1-x_2=10
\]

defines another line.

The solution set of the full system is the intersection of the solution sets of the individual equations.

General relationship:

- One equation \(a_i^Tx=b_i\) defines a hyperplane.
- A system \(Ax=b\) asks for the intersection of all those hyperplanes.

### 8.1 Two Equations And Two Unknowns

For two equations in two unknowns, the geometric picture consists of two lines.

General form:

\[
a_{11}x_1+a_{12}x_2=b_1,
\]

\[
a_{21}x_1+a_{22}x_2=b_2.
\]

Each equation defines a line in the \(x_1x_2\)-plane.

The possible cases:

1. Unique solution.

   The two lines intersect at exactly one point. That intersection point satisfies both equations.

   Instructor remark:

   - For estimation purposes, this is the ideal case when the goal is to "nail down" \(x_1\) and \(x_2\).

2. No solution.

   The two lines are parallel and distinct. Each individual equation has infinitely many solutions, but there is no point satisfying both equations simultaneously.

3. Infinitely many solutions.

   The two equations define the same line. The second equation is redundant or artificial, so the system effectively contains only one independent equation.

The instructor emphasizes that vector-space methods will show the same trichotomy for arbitrary numbers of equations and arbitrary numbers of unknowns:

- Unique solution.
- No solution.
- Infinitely many solutions.

The course will then characterize these cases using properties of \(A\) and \(b\).

## 9. Source And Coverage Note

Source transcript used:

- `C:\Users\mohdh\Downloads\New folder (2)\lectures\corrected\lecture3_corrected.md`

Coverage:

- These notes follow only Lecture 3 and preserve the chronological development of the transcript.
- Included topics: recap of linear, affine, and convex combinations; Euclidean norm; distance; norm properties; two-dimensional and \(n\)-dimensional Euclidean inner products; induced norm; angle formula; orthogonality; Cauchy-Schwarz inequality and proof idea; inner product properties; positive definiteness and indefinite-space remarks; origin-centered and shifted hyperplanes and half-spaces; projection preview; neuron half-space interpretation; matrix multiplication; matrix form of linear systems; and geometric solution-set cases.
- Explicit transcript exam markers were incorporated in the relevant sections.
- No other lecture transcript was processed for these notes.
