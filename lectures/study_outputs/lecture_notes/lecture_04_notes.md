# Lecture 04 Notes

## Recap: Angles, Cosine Distance, and Orthogonality

The lecture begins by continuing the discussion of angles between vectors. Even in high-dimensional spaces, the angle between two vectors can be defined through the inner product:

\[
\cos \theta = \frac{\langle x,y\rangle}{\|x\|\|y\|}
\]

The instructor emphasized that this quantity is used in machine learning to judge how close or similar vectors are. This use is connected to what is often called cosine distance or cosine similarity, depending on whether one uses the cosine value directly or converts it into a distance-like measure.

The expression above is guaranteed to lie between \(-1\) and \(1\). The reason is the Cauchy-Schwarz inequality, also referred to in the transcript as the Schwarz inequality:

\[
|\langle x,y\rangle| \le \|x\|\|y\|
\]

Because of this inequality, the normalized inner product can legitimately be interpreted as a cosine value.

Exam-related remark: the instructor said a proof of this inequality was already given, and an alternative proof would appear in the homework. The purpose of the proof is to justify why the normalized inner product is always in the valid range for a cosine.

This recap also connects to orthogonality. In ordinary two- or three-dimensional geometry, perpendicular vectors have angle \(90^\circ\). The generalized definition used in vector spaces is simpler:

\[
x \perp y \quad \text{if and only if} \quad \langle x,y\rangle = 0
\]

So two vectors are called orthogonal when their inner product is zero. This definition extends the familiar geometric notion of perpendicularity into high-dimensional spaces.

The instructor also reminded the class that hyperplanes and half-spaces can be defined using inner products. These were part of the previous lecture's conclusion and will remain important for understanding systems of linear equations geometrically.

## Matrix Multiplication as a Collection of Inner Products

The lecture then returns to matrix multiplication.

The instructor described the product of two matrices as a "bag of inner products." Each entry of a matrix product is computed by taking the inner product of:

- one row of the first matrix
- one column of the second matrix

Thus matrix multiplication can be understood as computing all possible row-column inner products.

This viewpoint is important because it connects matrix multiplication directly to geometry. Matrix products are not just formal algebraic rules; they organize many inner products into one object.

## Systems of Linear Equations and the Form \(Ax=b\)

Matrix multiplication is used to write systems of linear equations compactly. A collection of equations can be represented as:

\[
Ax=b
\]

Here:

- \(A\) is the coefficient matrix.
- \(x\) is the vector of unknown variables.
- \(b\) is the right-hand side vector.

The instructor described this as isolating the unknown variables into a vector or matrix and putting the known coefficients into another matrix. This compact form is convenient for both analysis and computation.

The system \(Ax=b\) will be used as an excuse or motivation to introduce several important concepts in linear algebra. These concepts are useful not only for solving systems of equations, but also for many other purposes in engineering, optimization, signal processing, and machine learning.

The main questions are:

- When does a solution exist?
- When is the solution unique?
- Can there be no solution?
- Can there be a finite number of solutions?
- Can there be infinitely many solutions?
- Can the answer be characterized from \(A\) alone, or does it depend on the pair \((A,b)\)?

The instructor emphasized that solving systems of linear equations appears either explicitly or implicitly in many applications.

## Geometric Picture for Two Equations in Two Unknowns

For a two-dimensional example, each equation defines a hyperplane. In two dimensions, a hyperplane is a line.

For example, an equation can be viewed as an inner product between a coefficient vector and the unknown vector \((x_1,x_2)\), equal to a constant. The solution set of one equation is the set of all \(x\)-vectors satisfying that equality. Geometrically, this is a line.

For two equations in two unknowns, the solution set of the full system is the intersection of two lines, because both equations must be satisfied at the same time.

The instructor described three possible cases:

1. The two lines intersect at exactly one point.
   - There is a unique solution.

2. The two equations look different but define the same line.
   - The lines overlap.
   - There are infinitely many solutions.

3. The two lines are parallel and distinct.
   - They cannot be satisfied at the same time.
   - This means there is no solution.
   - Note: the transcript's wording at this point appears to say "infinitely many solutions" after saying the lines cannot be satisfied simultaneously. The surrounding context indicates the intended conclusion is no solution.

Likely exam topic: the instructor said that these same types of conclusions for the two-variable, two-equation case will be extended to arbitrary numbers of equations and unknowns. The main tool for that extension will be vector spaces.

## Why Vector Spaces Are Introduced

Vector spaces will be the major tool for analyzing existence and uniqueness of solutions to systems such as:

\[
Ax=b
\]

They are also useful beyond this specific problem. The instructor repeatedly emphasized that the system of linear equations is a motivation for introducing concepts that have much wider use.

Vector spaces allow geometric ideas from two- and three-dimensional vectors to be generalized to many other kinds of objects.

The examples mentioned include:

- ordinary position vectors in \(\mathbb{R}^2\), \(\mathbb{R}^3\), and higher dimensions
- student grade vectors
- matrices
- polynomials
- functions
- random variables
- random processes
- discrete-time sequences

The instructor gave a grade-vector example:

- If a student has two grade components, such as midterm and homework, this can be viewed as a point in a two-dimensional space.
- If a student has three components, this can be viewed as a point in three-dimensional space.
- If a project component is added, the vector becomes four-dimensional.

In four dimensions, we cannot draw the object directly, but we can still talk about its projections or shadows in lower-dimensional spaces. We can also still discuss hyperplanes, half-spaces, inner products, norms, distances, and angles.

The major conceptual point is that geometry is not limited to objects we can draw. Once a vector space structure exists, geometric language can be transported to much more abstract objects.

## General Systems \(Ax=b\): Role of \(m\), \(n\), \(A\), and \(b\)

The instructor stated the general setup as follows:

- \(A\) has \(m\) rows.
- Each row corresponds to one equation.
- \(A\) has \(n\) columns.
- The number \(n\) is the number of unknown variables.

The basic questions are:

- Given \(A\) and \(b\), is there a solution?
- If there is a solution, is it unique?
- Are there many solutions?
- If only \(A\) is given, can we say whether every \(b\) has a solution?
- For a fixed \(A\), can some choices of \(b\) have solutions while others do not?
- For a fixed \(A\), if a solution exists, is it always unique?

The instructor said the course will characterize existence and uniqueness in terms of:

- the pair \((A,b)\)
- and, when possible, properties of \(A\) alone

The relevant properties will involve the dimensions of \(A\), and relationships among its rows and columns.

Special forms of \(A\), including symmetric matrices, will also be studied. Symmetric matrices are important because they help develop high-dimensional versions of quadratic functions, which are key functions in optimization.

Instructor clarification: when a student asked about a random matrix, the instructor clarified that the immediate analysis is not mainly about probabilistic methods. The course first treats the general matrix \(A\), characterizing existence and uniqueness through dimensions and row/column relationships, then studies special matrix forms and how those forms affect solutions.

Exam-related remark: the instructor said a significant amount of time will be spent on symmetric matrices because of their role in quadratic functions and optimization.

## Definition: Vector Space

A vector space consists of four ingredients:

1. A set of vectors.
2. A set of scalars, usually a field such as \(\mathbb{R}\) or \(\mathbb{C}\).
3. A vector addition operation.
4. A scalar multiplication operation.

The set of vectors is the main object of interest. The instructor called it the "star of the show."

Vector addition takes two vectors and returns another vector:

\[
+: V \times V \to V
\]

Scalar multiplication takes one scalar and one vector and returns another vector:

\[
\cdot: F \times V \to V
\]

These operations must satisfy certain properties. Some of the properties are closure conditions: performing the operations should not take us outside the original vector set. Other properties are compatibility conditions with the scalar field's own addition and multiplication.

## Vector Space Axioms Discussed in Lecture

Let \(x,y,z\) be vectors from the vector set \(V\), and let \(a,b\) be scalars from the scalar field.

The lecture discussed the following requirements.

### Closure Under Vector Addition

For any \(x,y \in V\),

\[
x+y \in V
\]

Adding two vectors should produce another vector in the same vector set.

### Additive Identity

There must be a zero vector \(0 \in V\) such that:

\[
x+0 = x
\]

and, conceptually, also:

\[
0+x = x
\]

The zero vector is the additive identity.

### Commutativity of Vector Addition

Vector addition should not depend on the order:

\[
x+y = y+x
\]

The instructor described this as symmetry of the addition operation.

### Additive Inverses

For every vector \(x\), there must be a vector \(-x\) such that:

\[
x+(-x)=0
\]

The vector \(-x\) is the negative of \(x\).

### Associativity of Vector Addition

When adding three vectors, it should not matter which pair is added first:

\[
(x+y)+z = x+(y+z)
\]

The instructor noted that vector addition is a binary operation: it takes two inputs and produces one output. Associativity makes repeated addition well-defined.

Instructor remark: these addition properties are essentially the group-like part of the vector space definition for the vector set together with vector addition.

### Closure Under Scalar Multiplication

For any scalar \(a\) and vector \(x\),

\[
ax \in V
\]

Scalar multiplication should produce a vector in the same vector set.

### Compatibility Between Scalar Multiplication and Field Multiplication

The lecture emphasized the property:

\[
a(bx) = (ab)x
\]

The left-hand side applies scalar multiplication twice. The right-hand side first multiplies \(a\) and \(b\) inside the scalar field, then performs scalar multiplication once. These must agree.

This is a compatibility requirement between multiplication in the scalar field and scalar multiplication in the vector space.

### Multiplicative Identity of the Scalar Field

The scalar field has a multiplicative identity, \(1\). It must satisfy:

\[
1x = x
\]

for every vector \(x\).

### Zero Scalar Produces the Zero Vector

If the scalar zero is used in scalar multiplication, the result should be the additive identity of the vector space:

\[
0x = 0
\]

The zero on the left is the scalar zero. The zero on the right is the zero vector.

## Linear Combinations and Closure

The instructor stressed that these properties imply closure under linear combinations.

If scaled versions of vectors stay inside \(V\), and sums of vectors stay inside \(V\), then any expression of the form:

\[
a_1x_1 + a_2x_2 + \cdots + a_kx_k
\]

also stays inside \(V\), as long as the \(x_i\) are in \(V\) and the \(a_i\) are scalars.

This is one of the most important consequences of the vector space structure:

> A vector space is closed under linear combinations.

This idea later becomes central to span, subspaces, basis, and the analysis of \(Ax=b\).

## Example: \(\mathbb{R}^3\)

The first example is ordinary three-dimensional real space:

\[
\mathbb{R}^3
\]

A vector has three components:

\[
x = (x_1,x_2,x_3)
\]

Vector addition is defined elementwise:

\[
x+y = (x_1+y_1,\ x_2+y_2,\ x_3+y_3)
\]

Scalar multiplication is also elementwise:

\[
ax = (ax_1,\ ax_2,\ ax_3)
\]

The zero vector is:

\[
0 = (0,0,0)
\]

All vector space properties are satisfied in the usual way.

## Example: \(\mathbb{R}^n\)

The same construction extends from \(\mathbb{R}^3\) to \(\mathbb{R}^n\).

Vectors have \(n\) real components. Addition and scalar multiplication are defined component by component. The zero vector has all entries equal to zero.

This is the natural finite-dimensional generalization of two- and three-dimensional Euclidean space.

## Example: Complex Vector Spaces

Complex vectors are common in electrical engineering.

A vector in \(\mathbb{C}^n\) has complex entries:

\[
x = (x_1,\ldots,x_n)
\]

where each \(x_i\) is a complex number.

The scalar field is \(\mathbb{C}\), the complex numbers. The instructor explicitly noted that the notation for complex numbers is different from \(\mathbb{R}\), the real numbers.

Vector addition is still elementwise:

\[
x+y = (x_1+y_1,\ldots,x_n+y_n)
\]

Scalar multiplication uses complex multiplication:

\[
ax = (ax_1,\ldots,ax_n)
\]

This is a direct extension of real vector spaces, but over the complex scalar field.

## Example: Matrix Spaces

Another vector space is the set of \(m \times n\) matrices.

In this setting, each matrix is treated as one vector in an abstract sense. The instructor emphasized that this may feel different because the object does not look like a column vector, but the abstract vector-space definition allows it.

An \(m \times n\) matrix can be regarded as one point in a high-dimensional space.

The operations are:

- usual matrix addition
- multiplication of a matrix by a scalar

If two \(m \times n\) matrices are added, the result is still an \(m \times n\) matrix. If an \(m \times n\) matrix is scaled by a scalar, the result is still an \(m \times n\) matrix.

Thus closure is satisfied, and the remaining vector space properties follow from ordinary arithmetic on matrix entries.

This example is important because it allows us to discuss:

- distances between matrices
- angles between matrices
- orthogonality of matrices
- subspaces of matrix spaces

These ideas appear later in the lecture through symmetric, trace-zero, and orthogonal matrices.

## Example: Polynomial Spaces

The instructor next discussed polynomial spaces, which can be confusing at first because polynomials may be nonlinear functions of their argument.

The vector space is the set of polynomials of degree at most \(n\). A typical polynomial is:

\[
p(x)=a_0+a_1x+\cdots+a_nx^n
\]

The coefficients \(a_0,\ldots,a_n\) define the polynomial. Therefore, a polynomial of degree at most \(n\) has \(n+1\) coefficients.

Polynomial addition is defined by adding coefficients of matching powers. If:

\[
p(x)=a_0+a_1x+\cdots+a_nx^n
\]

and:

\[
q(x)=b_0+b_1x+\cdots+b_nx^n
\]

then:

\[
(p+q)(x)=(a_0+b_0)+(a_1+b_1)x+\cdots+(a_n+b_n)x^n
\]

Scalar multiplication scales each coefficient:

\[
(cp)(x)=ca_0+ca_1x+\cdots+ca_nx^n
\]

The instructor pointed out that there is a one-to-one connection between such polynomials and vectors of coefficients in \(\mathbb{R}^{n+1}\). Under this connection, polynomial addition corresponds to vector addition of coefficient vectors.

Likely exam topic: once polynomial spaces are treated as vector spaces, we can define inner products, norms, and orthogonality for polynomials. We can speak of one polynomial being orthogonal to another polynomial.

The key warning is that the polynomial may be nonlinear in the variable \(x\), but the vector space operations act on the polynomial as an object, or equivalently on its coefficient vector.

## Example: Discrete-Time Sequences

The lecture also introduced the set of discrete-time sequences as a vector space.

A discrete-time sequence is a collection of values indexed by integers, as in signals and systems notation. The instructor referenced Oppenheim's notation for such sequences.

A real-valued sequence may be written conceptually as:

\[
\{x[n]\}_{n\in\mathbb{Z}}
\]

Complex-valued sequences can also be used.

The instructor said one may imagine such a sequence as an infinite-dimensional vector containing infinitely many samples. However, the axiomatic vector space definition is useful because we do not need to explicitly force every object into a finite column-vector representation.

With suitable addition and scalar multiplication:

- adding two sequences means adding corresponding samples
- scaling a sequence means scaling every sample

Then each sequence can be viewed as a point in a high-dimensional or infinite-dimensional space.

This allows geometric language to be used for sequences. For example, we can later define when two discrete-time sequences are orthogonal.

## Example: Function Spaces

Function spaces were also mentioned.

For example, one can consider functions defined on an interval \([a,b]\) that are square-integrable on that interval.

Function addition is pointwise:

\[
(f+g)(t)=f(t)+g(t)
\]

Scalar multiplication is also pointwise:

\[
(cf)(t)=c f(t)
\]

The instructor's point was that vector space language is broad enough to include functions, not only finite-dimensional coordinate vectors.

## Example: Zero-Mean Random Variables

Another important example is the set of zero-mean random variables.

If \(X\) and \(Y\) are zero-mean random variables, then:

\[
E[X]=0,\qquad E[Y]=0
\]

Their sum is also zero-mean:

\[
E[X+Y]=E[X]+E[Y]=0
\]

Scaling also preserves zero mean:

\[
E[aX]=aE[X]=0
\]

Therefore, zero-mean random variables form a vector space under the usual addition and scalar multiplication of random variables.

The instructor said random variables, random vectors, and random processes can be viewed through vector space ideas.

## Inner Products for Random Variables: Correlation and Orthogonality

The instructor then highlighted an important leap: once random variables are viewed as vectors, one can define inner products on them.

For two random variables \(X\) and \(Y\), correlation can be interpreted as an inner product. In this setting, the condition that the inner product is zero corresponds to the random variables being uncorrelated.

For zero-mean real random variables, the correlation inner product can be thought of as:

\[
\langle X,Y\rangle = E[XY]
\]

So the orthogonality condition becomes:

\[
E[XY]=0
\]

The instructor explicitly distinguished this from independence:

- Zero correlation means uncorrelated.
- It does not necessarily mean independent.

Under this interpretation, uncorrelated random variables can be described geometrically as orthogonal.

Exam-related remark: this point was marked as important. The instructor said this viewpoint is very useful in estimation theory and signal processing.

Applications mentioned:

- Kalman filters
- Wiener filters
- estimation theory
- signal processing

These are built on the basic terminology of orthogonality in spaces of random variables.

## Subspaces: Definition and Motivation

The next major concept is subspace.

Exam-related remark: the instructor said subspaces will be a major tool for addressing existence and uniqueness problems for systems of linear equations. Subspaces are also used in algorithmic constructions and analysis.

Let \(V\) be a vector space. A subset \(S \subseteq V\) is called a subspace of \(V\) if \(S\) itself forms a vector space using the same vector addition and scalar multiplication as \(V\).

The key requirements are:

- \(S\) is a subset of \(V\).
- \(S\) contains the zero vector.
- \(S\) is closed under vector addition.
- \(S\) is closed under scalar multiplication.

The instructor phrased the formal definition as: \(S\) is a subset of \(V\), and \(S\) itself can be used to construct a vector space with the same operations.

## Subspace Examples and Non-Examples in \(\mathbb{R}^2\)

The instructor used several subsets of \(\mathbb{R}^2\) to clarify what is and is not a subspace.

### A Subset That Does Not Contain Zero

The first pictured subset was some region in the plane. It was a subset of \(\mathbb{R}^2\), but it was not a subspace.

Reasons:

- It did not contain the zero vector.
- It was not closed under vector addition.
- Adding two vectors in the subset could produce a vector outside the subset.

The instructor emphasized that being a subset is not enough. A subspace must satisfy the vector space requirements.

### First and Third Quadrants Together

Another example was the union of the first and third quadrants.

This example is misleading because it contains the origin. It also seems partly compatible with scalar multiplication:

- Positive scaling keeps a vector in the same quadrant.
- Negative scaling can move a vector from the first quadrant to the third, or from the third to the first.

Also:

- the sum of two vectors in the first quadrant remains in the first quadrant
- the sum of two vectors in the third quadrant remains in the third quadrant

However, if one vector is taken from the first quadrant and another from the third quadrant, their sum can land outside the union of the first and third quadrants.

Therefore this set is not closed under vector addition, so it is not a subspace.

### A Line Not Passing Through the Origin

A line in \(\mathbb{R}^2\) that does not pass through the origin is not a subspace.

Reasons:

- It does not contain the zero vector.
- Adding two vectors on the line can produce a vector outside the line.

The instructor warned that this object looks like a linear object geometrically, but it is not a linear subspace unless it passes through the origin.

### Lines Through the Origin

Lines through the origin are subspaces of \(\mathbb{R}^2\).

Reasons:

- They contain the zero vector.
- The sum of any two vectors on the same line through the origin stays on that line.
- Any scalar multiple of a vector on the line stays on that line.

The instructor described the vectors as collinear.

### Trivial Subspaces of \(\mathbb{R}^2\)

Two trivial subspaces were also mentioned:

- the entire ambient space \(\mathbb{R}^2\)
- the set containing only the origin, \(\{0\}\)

Both satisfy the subspace requirements.

## Subspaces of \(\mathbb{R}^3\)

For \(\mathbb{R}^3\), the instructor asked what the subspaces are.

The examples given were:

- planes through the origin
- lines through the origin
- the origin alone
- the entire space \(\mathbb{R}^3\)

A student suggested something like \(\mathbb{R}^2\), and the instructor clarified that inside \(\mathbb{R}^3\), the relevant geometric object is a plane through the origin.

The instructor said planes through the origin satisfy the main condition: all possible linear combinations of vectors in the plane remain inside the plane.

## Matrix Subspaces: Symmetric Matrices

The lecture then moved to more interesting examples inside matrix spaces.

The ambient vector space is the set of square real matrices, for example \(m \times m\) real matrices. The instructor noted that, strictly speaking, one should specify the vector set, scalar set, and operations, but in common mathematical speech the operations are often implied.

Define:

\[
S_1=\{X: X^T=X\}
\]

This is the set of real symmetric matrices.

The transpose operation swaps rows and columns. A matrix is symmetric when it is equal to its transpose.

The instructor checked whether this set is a subspace.

### Zero Matrix

The zero matrix is symmetric:

\[
0^T=0
\]

So the origin of the ambient matrix space is included.

### Closure Under Scalar Multiplication

If \(X\) is symmetric, then scaling every entry of \(X\) by a scalar preserves symmetry:

\[
(\alpha X)^T = \alpha X^T = \alpha X
\]

Thus scalar multiplication does not break symmetry.

### Closure Under Addition

If \(X\) and \(Y\) are symmetric, then:

\[
(X+Y)^T = X^T+Y^T = X+Y
\]

Therefore the sum is symmetric.

Conclusion:

\[
S_1
\]

is a subspace of the square matrix space.

The instructor said one may imagine this subspace as a plane or slice in a high-dimensional geometric region, although such geometric imagination can sometimes mislead.

## Matrix Operation: Trace

The instructor then introduced the trace of a square matrix and called it a very important, though simple, operation.

For a square matrix \(X\), the trace is the sum of its diagonal elements:

\[
\operatorname{tr}(X)=\sum_{i=1}^m x_{ii}
\]

For example, if:

\[
X=
\begin{bmatrix}
x_{11} & x_{12} & \cdots \\
x_{21} & x_{22} & \cdots \\
\vdots & \vdots & \ddots
\end{bmatrix}
\]

then:

\[
\operatorname{tr}(X)=x_{11}+x_{22}+\cdots+x_{mm}
\]

The trace ignores off-diagonal elements.

Exam-related remark: trace was explicitly flagged as important.

## Matrix Subspaces: Zero-Trace Matrices

Define:

\[
S_2=\{X:\operatorname{tr}(X)=0\}
\]

This is the set of square matrices whose diagonal elements sum to zero.

The instructor checked whether this is a subspace.

### Zero Matrix

The zero matrix has trace zero:

\[
\operatorname{tr}(0)=0
\]

So the origin is included.

### Closure Under Scalar Multiplication

If \(\operatorname{tr}(X)=0\), then:

\[
\operatorname{tr}(\alpha X)=\alpha \operatorname{tr}(X)=\alpha\cdot 0=0
\]

So scaling preserves the zero-trace condition.

### Closure Under Addition

If \(\operatorname{tr}(X)=0\) and \(\operatorname{tr}(Y)=0\), then:

\[
\operatorname{tr}(X+Y)=\operatorname{tr}(X)+\operatorname{tr}(Y)=0+0=0
\]

So addition preserves the zero-trace condition.

The instructor emphasized that trace is a linear operator:

\[
\operatorname{tr}(X+Y)=\operatorname{tr}(X)+\operatorname{tr}(Y)
\]

and:

\[
\operatorname{tr}(\alpha X)=\alpha\operatorname{tr}(X)
\]

Conclusion:

\[
S_2
\]

is a subspace of the square matrix space.

The instructor again described it geometrically as a plane through the origin in a high-dimensional space.

## Degrees of Freedom and Dimension Preview

The lecture used matrix examples to preview the idea of dimension.

An arbitrary \(m \times m\) matrix has:

\[
m^2
\]

free parameters.

For symmetric \(m \times m\) matrices:

- all \(m\) diagonal entries can be chosen freely
- the off-diagonal entries are mirrored across the diagonal
- there are \(m^2-m\) off-diagonal entries total
- half of those, \((m^2-m)/2\), can be chosen freely

So the number of free parameters is:

\[
\frac{m^2-m}{2}+m
=\frac{m^2+m}{2}
\]

For zero-trace \(m \times m\) matrices:

- the full matrix would have \(m^2\) parameters
- the trace condition imposes one linear constraint on the diagonal entries
- \(m-1\) diagonal entries can be chosen freely, and the final diagonal entry must make the trace equal zero

Therefore the number of degrees of freedom is:

\[
m^2-1
\]

The instructor said this means the zero-trace subspace is one dimension less than the full square-matrix space. It is a hyperplane.

## Zero-Trace Matrices as Orthogonal to the Identity

The instructor previewed a matrix inner product that will be defined later:

\[
\langle A,B\rangle = \operatorname{tr}(B^T A)
\]

Using this inner product, the zero-trace condition can be viewed as an orthogonality condition involving the identity matrix:

\[
\operatorname{tr}(X)=\langle X,I\rangle = 0
\]

Thus zero-trace matrices can be thought of as all matrices orthogonal to the identity matrix, according to the matrix inner product.

The instructor was careful to note that this matrix inner product had not yet been formally defined in the lecture.

Exam-related remark: this was flagged as important because it connects trace, inner products, orthogonality, and hyperplanes.

## Hyperplanes Through the Origin Versus Shifted Hyperplanes

The instructor asked whether every set defined by a condition equal to zero is a subspace. In the context being discussed, the idea was that a linear condition or inner-product condition equal to zero, such as trace zero, gives a subspace because it passes through the origin and is closed under linear combinations.

If the condition is changed from zero to a nonzero number, the result is generally not a subspace.

For example:

\[
\{X:\operatorname{tr}(X)=1\}
\]

is not a subspace.

Reasons:

- The zero matrix is not included because its trace is zero, not one.
- If two matrices each have trace one, their sum has trace two.
- Scalar multiplication also does not preserve trace one.

However, this set can still be viewed geometrically as a hyperplane. It is just a hyperplane that does not pass through the origin.

The instructor also described a shifted version of the zero-trace subspace. If \(S_2\) is the trace-zero subspace and \(Z\) has nonzero trace, then:

\[
S_3 = Z + S_2
\]

is a shifted subset of the square matrix space. It is not a subspace, because it is moved away from the origin and its elements have a nonzero trace determined by the shift.

More explicitly, every element of \(S_3\) has trace \(\operatorname{tr}(Z)\), since adding an element of \(S_2\) contributes zero trace. Thus \(S_3\) is a translated hyperplane, not a subspace through the origin.

## Matrix Subspaces and Non-Subspaces: Real Orthogonal Matrices

The instructor next introduced real orthogonal matrices.

Define:

\[
S_4=\{X:X^T X=I\}
\]

Such matrices are called real orthogonal matrices.

The ambient space is again the set of \(m \times m\) real matrices. The instructor mentioned that complex extensions will be considered later.

The condition:

\[
X^T X=I
\]

has a geometric interpretation using matrix multiplication as inner products.

Recall that matrix multiplication forms entries by taking inner products of rows and columns. In \(X^T X\), the rows of \(X^T\) are the columns of \(X\). Therefore, the entries of \(X^T X\) are inner products between columns of \(X\).

The identity matrix condition means:

- the inner product of a column with itself is \(1\)
- the inner product of two different columns is \(0\)

Therefore, the columns of \(X\) are mutually orthogonal and each has norm \(1\). For square real orthogonal matrices, this also implies corresponding orthogonality properties for rows.

Exam-related remark: the instructor explicitly connected this condition back to matrix multiplication as inner products.

### Orthogonal Matrices Are Not a Subspace

The set of real orthogonal matrices is not a subspace.

The quickest reason is that the zero matrix is not included:

\[
0^T0=0\ne I
\]

Equivalently, the zero matrix's columns do not have norm one.

So the origin of the ambient matrix space is not in the set, and the set cannot be a subspace.

The instructor emphasized that orthogonal matrices are still important even though they are not a subspace.

## Orthogonal Matrices, Circles, Manifolds, and Closest Points

The instructor used the orthogonal-matrix condition to motivate future distance and projection problems.

If the object were a single vector \(x=(x_1,x_2)\) satisfying:

\[
x^T x = 1
\]

then the set would be the unit circle.

Given a point outside or inside the circle, the closest point on the circle in Euclidean distance is found by drawing the line through the point and the origin. The closest point is where this line intersects the circle.

The instructor then generalized this idea:

- The set of orthogonal matrices is not a linear subspace.
- It behaves more like a curved set, such as a sphere or manifold.
- The transcript uses wording like "hyper spherical thing" and "manifold."

Even though it is not a subspace, we can still ask optimization questions about it:

- Given a matrix \(Y\) not in the set, what is the closest matrix in the set?
- What does "closest" mean?
- Which distance measure are we using?

The instructor said that there are infinitely many ways to define distance between matrices. Some distance measures are algebraically attractive because they lead to closed-form solutions.

The practical problem is:

> Given an arbitrary matrix, find a matrix with orthogonal columns that is as close as possible to it.

The instructor stressed that the goal is not to find just any orthogonal-column matrix, but one close to the original matrix.

Applications mentioned include:

- orthogonalization-like procedures (the transcript wording appears as "auto organization")
- independent component analysis
- machine learning gradient-search-related algorithms

This topic will be revisited after defining appropriate notions of matrix distance and closeness.

## Subspace Example: Causal Discrete-Time Sequences

The lecture returned to sequence spaces for another subspace example.

Consider two-sided discrete-time sequences. These have values indexed over both positive and negative integers.

A causal sequence is one whose values are zero at all negative indices:

\[
x[n]=0 \quad \text{for } n<0
\]

The instructor said such sequences correspond to causal impulse responses of causal systems.

The set of causal sequences is a subset of the set of all two-sided sequences. It is a subspace.

Reason:

- If two causal sequences are added, their negative-index entries remain zero, because \(0+0=0\).
- If a causal sequence is multiplied by a scalar, its negative-index entries remain zero, because \(\alpha\cdot 0=0\).

Therefore causal sequences are closed under addition and scalar multiplication.

Instructor remark: students missing signals and systems background should review causal systems, causal impulse responses, impulse response, and frequency response, because these ideas will be needed later.

## Dimension, Span, Basis, and Linear Independence: Motivation

After discussing degrees of freedom in matrix subspaces, the instructor introduced the next formal topic: dimension.

Dimension is meant to answer questions such as:

- How large is a vector space?
- How large is a subspace?
- How many degrees of freedom are needed to describe its elements?

The instructor said the formal discussion of dimension will require:

- span
- basis
- linear independence

Span is introduced first. Basis is the reverse direction of span, and basis requires linear independence.

## Definition: Span

Given a set \(A\subseteq V\), the span of \(A\) is the set of all possible linear combinations of elements of \(A\).

The set \(A\) may be:

- finite
- large
- infinite

To form the span, one takes arbitrary numbers of elements from \(A\), multiplies them by arbitrary scalars, and sums them.

For example, if \(A=\{x,y\}\), then:

\[
\operatorname{span}(A)
=\{a x + b y : a,b \text{ are scalars}\}
\]

If \(x\) and \(y\) are suitable non-collinear vectors in three-dimensional space, all their linear combinations form the plane containing them.

The instructor described span as a kind of machine:

1. You give the machine a set of vectors.
2. It generates all possible linear combinations.
3. The output is a subspace containing the original set.

This description reinforces the idea that span produces a vector space or subspace from a given collection of vectors.

## Span Example: Vectors in a Plane

The instructor described a set of vectors lying in a plane such as the \(z=0\) plane.

The transcript's example appears as vectors like \(100\) and \(110\), which can be read as coordinate vectors such as:

\[
(1,0,0),\qquad (1,1,0)
\]

Their span is the plane containing all linear combinations of them, namely a plane with zero third coordinate, assuming the vectors are independent within that plane.

The instructor then considered adding another vector that already lies in the same span.

If the new vector can be generated as a linear combination of the previous vectors, adding it does not change the span. It does not bring a new dimension or new information.

The instructor connected this to random variables as well: if a new vector or random variable is already derivable from existing ones, it does not add a new independent form of information.

## Alternative Definition of Span

The instructor gave another definition:

> The span of a set \(A\) is the smallest subspace containing \(A\).

"Smallest" means that if a subspace contains \(A\), then the span is contained in that subspace. There is no smaller subspace that still contains all elements of \(A\).

This definition is equivalent to the "all possible linear combinations" definition.

## Basis as the Reverse Problem of Span

The instructor described basis as the reverse of the span problem.

For span:

- You are given a set of vectors.
- You generate the subspace they produce.

For basis:

- You are given a vector space or subspace.
- You try to find a set of vectors that spans it.

The goal is to find a minimal set of vectors that can represent or generate the whole space.

The instructor used the plane example:

- If a plane is given, one can communicate the plane by giving two suitable spanning vectors \(p_1\) and \(p_2\).
- One could also give \(p_1,p_2,p_3\), but if \(p_3\) is already generated by \(p_1\) and \(p_2\), then this includes redundant information.

A basis is a spanning set with no redundant vector. No element of a basis can be written as a linear combination of the others.

This connects directly to linear independence.

## Dictionaries Versus Bases

The instructor introduced the term dictionary for a spanning set that may include redundant vectors.

If \(p_1,p_2,p_3\) span the same space as \(p_1,p_2\), and \(p_3\) can be derived from the others, then:

- \(\{p_1,p_2\}\) may be a basis
- \(\{p_1,p_2,p_3\}\) is not a basis because it is not minimal
- the larger redundant set can be called a dictionary

The instructor noted that dictionaries are useful in machine learning. Sometimes it is useful to represent a space with more than the minimal number of elements.

However, the strict definition of a basis involves the minimum number of elements needed to represent the space, with no element derivable from the others.

This topic will continue in the next lecture.

## Instructor Study Advice

At the end, the instructor gave two study recommendations.

First, students who are missing signals and systems background should review:

- causal systems
- causal impulse responses
- impulse response
- frequency response

The instructor said these will be needed in the future.

Second, students who are missing linear algebra background should begin reading a linear algebra book in some detail. The instructor mentioned Strang's book and advised reading the basic explanatory text, not only the equations.

## Exam-Relevant Items Mentioned in the Transcript

The transcript explicitly marks or strongly signals the following as exam-relevant:

- Cauchy-Schwarz inequality guarantees the normalized inner product lies in \([-1,1]\), justifying the cosine-angle definition.
- Orthogonality is generalized by the condition \(\langle x,y\rangle=0\).
- Systems of linear equations can be analyzed geometrically through hyperplanes and their intersections.
- The two-equation, two-unknown cases generalize to arbitrary numbers of equations and unknowns.
- Vector spaces and subspaces are likely exam topics.
- Span, basis, and linear independence are likely exam topics.
- Symmetric matrices are important for high-dimensional quadratic functions and optimization.
- Random variables can be treated as vectors, with correlation acting like an inner product.
- Uncorrelated random variables correspond to orthogonality in that vector-space interpretation.
- Subspaces are a major tool for existence and uniqueness of solutions to \(Ax=b\).
- Trace is an important matrix operation.
- Zero-trace matrices form a subspace and can be viewed as matrices orthogonal to the identity under a matrix inner product.
- Orthogonal matrices satisfy \(X^TX=I\), meaning their columns are mutually orthogonal and unit norm.
- Orthogonal matrices are important but do not form a subspace.

## Source and Coverage Note

Source: `corrected/lecture4_corrected.md`.

Coverage: These notes use only the specified Lecture 4 corrected transcript. They preserve the lecture's chronological flow, examples, instructor remarks, exam flags, proof ideas, warnings, and relationships among concepts. No other lecture transcript was processed.
