# Lecture 02 Notes

## Course Motivation: Geometry Behind Algebra

The lecture begins with the main goal of the course: become comfortable looking at algebraic expressions and asking for the geometric picture behind them. An expression might define a quadratic equation, another expression might define a hyperplane, and the real object of interest might be the intersection of those objects. The course will repeatedly translate algebraic formulas, constraints, objective functions, and data into geometric language.

Historically, algebra and geometry were treated mostly separately. Geometry involved figures and proofs based on those figures. Algebra involved numbers and symbolic expressions. The instructor gives Descartes as the main historical figure who linked the two through coordinates, while adding the caveat that the whole credit should not necessarily go to him alone. By assigning numbers to geometric locations, a point in the plane can be represented by an ordered pair, and a geometric object can be represented by an equation.

This link is analytical geometry: equations can be visualized as circles, lines, planes, or other geometric sets, and geometric objects can be described with algebraic equations. Linear algebra and vector space methods continue this idea. They let us take algebraic problems or data sets and bring a geometric view to them.

The course will use high-dimensional spaces to visualize or reason about objects such as objective functions and constraints in optimization problems. Beyond two or three dimensions we cannot draw the figures directly, but we can still use the same terminology and reasoning. The instructor warns that high-dimensional spaces sometimes have surprises that do not match ordinary two- or three-dimensional intuition.

Planned topics include:

- Vectors and matrices.
- Vector space definitions.
- Linear independence.
- Span.
- Basis.
- Norms.
- Inner products.
- Applications and significance of these definitions.

## Vectors as Positions, Arrows, and Ordered Boxes of Numbers

The usual first exposure to vectors is often in physics, especially position vectors. In Cartesian coordinates, a position in the plane can be represented by two numbers organized as a column vector. The same object can be viewed either as a point or as an arrow from the origin to that point. The arrow view gives both location and direction.

Informally, from the mathematical point of view, a vector is a collection of numbers placed into a box for some purpose. For a two-dimensional vector, the entries are ordered. The first entry refers to the horizontal coordinate and the second entry refers to the vertical coordinate.

Exam note: the order of the entries is important. Swapping entries changes which coordinate is horizontal and which is vertical.

The instructor tells a Descartes anecdote from a children's book. Descartes was sick in bed and noticed a fly landing on the ceiling. He wondered whether it was landing in the same geometric location, so he drew horizontal and vertical lines, numbered them, and recorded the fly's positions as pairs of numbers. The point of the story is that position information was converted into numerical pairs. The instructor jokingly notes that this line of thinking eventually supports modern machine learning.

Velocity vectors are another geometric example. A velocity can be decomposed into horizontal and vertical components depending on the frame of reference, and these components can again be placed in a vector. The velocity vector tells us in which direction and how fast something is moving.

## Non-Geometric Data as Vectors: Student Grades

The lecture then moves from physical vectors to data that is not naturally geometric. A student can be represented, for the purpose of a class, by two numbers: midterm grade and final grade.

For example,

```text
x = [midterm grade, final grade]^T
```

This is a two-dimensional vector. The first element is the midterm grade, and the second element is the final grade. The instructor uses a special vector notation, often an arrow or bold symbol, to distinguish vectors from scalars.

Although grades are not physical positions, we can make an analogy with position vectors:

- Treat the midterm grade as the horizontal coordinate.
- Treat the final grade as the vertical coordinate.
- Represent the student as a point in a plane.

This is a simple observation, but conceptually important: non-geometric information has been converted into a geometric form. The instructor remarks that this helps humans because visual processing is powerful. If multiple students are plotted as points, we can use geometric language:

- Two students may have close performance.
- One student may be an outlier.
- The class distribution can be visually inspected.

This same idea extends to machine intelligence: numerical data is represented as vectors, and geometric relationships between those vectors become meaningful.

## Overall Grades, Hyperplanes, and Half-Spaces in Two Dimensions

Suppose the class has two grading components: midterm and final. Each student is a two-dimensional vector. If the overall grade is computed as a weighted combination, for example

```text
overall = 0.4 * midterm + 0.6 * final
```

and the passing condition is

```text
overall > 40,
```

then the equality case

```text
0.4 * midterm + 0.6 * final = 40
```

defines a line in the midterm-final plane. That line is the set of all potential grade pairs that produce exactly the passing threshold. The instructor calls this line a hyperplane.

In two dimensions, a hyperplane is a line. The line divides the plane into two regions:

- One half-space consists of grade pairs with overall grade greater than 40. The instructor calls this the half-space of "happy students" because these students pass.
- The other half-space consists of grade pairs with overall grade less than 40. The instructor calls this the half-space of "sad students" because these students fail.

The instructor uses notation such as \(H^+\) for the passing half-space. These sets contain all potential student grade vectors satisfying the property, not necessarily only students who are actually in the class.

Instructor clarification: a hyperplane does not need to pass through the origin. In the grade example, the passing threshold line is generally away from the origin. The coordinate axes are arbitrary reference choices in an infinite plane. Since both sides of the line extend infinitely, one should not think of one side as inherently "larger"; they are just two half-spaces determined by the line.

## Extension to Three and Four Grading Components

With three grading components, such as midterm, final, and homework, each student becomes a point in three-dimensional space:

```text
x = [midterm, final, homework]^T
```

The instructor gives an overall grade rule of the form

```text
0.3 * midterm + 0.4 * final + 0.3 * homework
```

The weights sum to one, and the instructor notes that this will later be called a convex combination. The equality condition

```text
0.3 * midterm + 0.4 * final + 0.3 * homework = 40
```

defines a plane in three-dimensional space. That plane divides the space into two half-spaces: passing grade triples and failing grade triples.

With four grading components, such as midterm, final, homework, and project, each student becomes a four-dimensional vector:

```text
x = [midterm, final, homework, project]^T
```

The instructor gives a rule like

```text
0.3 * midterm + 0.4 * final + 0.2 * homework + 0.1 * project = 40
```

The set of grade vectors satisfying this equality is the set of barely passing combinations:

```text
H = { (m, f, h, p) : 0.3m + 0.4f + 0.2h + 0.1p = 40 }
```

The passing half-space is

```text
H^+ = { (m, f, h, p) : 0.3m + 0.4f + 0.2h + 0.1p > 40 }
```

The instructor emphasizes that we cannot draw this four-dimensional object, but we can still use the same terminology. In two dimensions the hyperplane is a line. In three dimensions it is a plane. In four and higher dimensions, it is called a hyperplane. The key idea is to extend familiar geometric terminology to higher-dimensional vector spaces.

## Machine Learning Interpretation: Credit Approval and Neurons

The instructor connects the half-space idea to machine learning and artificial intelligence using a bank credit approval example. A customer applies for credit and declares information such as salary and real-estate value. These numbers form a feature vector:

```text
x = [salary, real_estate_value]^T
```

The bank wants to decide whether to approve or reject the credit application. Past data may show approved customers in one region of the feature plane and rejected customers in another. The instructor remarks that financial institutions may be required by government or the financial system to declare a decision rule: what criterion is used for giving or denying credit, and whether the rule discriminates against anyone. This is one reason machine-learning credit rules raise explainability issues. A simple explainable decision rule can be represented by a hyperplane:

```text
w_1 * salary + w_2 * real_estate_value = threshold
```

One half-space corresponds to approved applications, and the other corresponds to rejected applications. Once we know that such a hyperplane can separate the data, the remaining problem is to determine the weights and threshold. The instructor says this is essentially the machine learning problem.

A simple artificial neuron implements this kind of half-space test. It computes something like

```text
w_1 * salary + w_2 * real_estate_value - threshold
```

Then a nonlinear rule maps the result to an output:

- If the value is positive, output 1.
- If the value is negative, output 0.

So the neuron checks whether the input vector lies in a particular half-space. The instructor's geometric interpretation is that a neuron with this kind of threshold nonlinearity is a half-space identifier.

The instructor also briefly describes a biological neuron. A real neuron has dendrites that receive inputs, a cell body, and an axon that produces outputs. When a neuron fires, an action potential propagates along the axon, chemicals are released, and those chemicals bind to dendrites of another neuron. This opens gates, allowing charges such as sodium ions to enter, increasing the membrane potential. If the potential exceeds a threshold, the next neuron fires. The instructor notes that artificial models simplify this substantially, and real neurons have complications such as different types of dendrites and dendrite positions. On average, a biological neuron has about 10,000 connections.

## When One Hyperplane Is Not Enough

The instructor then considers a data pattern where approved and rejected points cannot be separated by a single half-space. In such a case, one neuron is not enough. However, the same half-space concept can be extended by using intersections of half-spaces.

For example, a desired region may be described as the intersection of:

- A left-right half-space determined by one hyperplane.
- An up-down half-space determined by another hyperplane.

Each half-space can be checked by a separate neuron:

```text
neuron 1: w_11 * salary + w_12 * real_estate - threshold_1
neuron 2: w_21 * salary + w_22 * real_estate - threshold_2
```

Then another neuron can check whether both outputs are 1. The instructor mentions McCulloch-Pitts logic elements in this context but says the lecture is not meant to go through neural network theory. The point is geometric: combinations of neurons can test membership in intersections of half-spaces.

Question/clarification: a student asks why the weights changed. The instructor explains that each neuron corresponds to a different hyperplane, so the weights are different. One neuron checks one half-space, another checks another half-space, and a later neuron can combine their outputs.

The instructor also notes that real neural networks may have thousands of inputs per neuron. We cannot draw those spaces, but the same geometric intuition about hyperplanes and half-spaces extends to high-dimensional cases.

## Matrices as Collections of Vectors

The lecture then shifts from vectors to matrices. A matrix can be viewed as a rectangular organization of numbers, like an Excel sheet. But it can also be viewed as a collection of column vectors or a collection of row vectors.

In the student grade example:

- Each column might represent one student vector.
- Each row might represent one measurement or grading component.

This simple distinction, viewing a matrix by columns or by rows, is fundamental in linear algebra. The instructor says it lies at the heart of vector space concepts and the analysis of systems of linear equations, which will be studied later.

## Scalar Multiplication of a Vector

The first formal vector operation introduced is scaling a vector by a scalar. A scalar is typically a real number or complex number from a field. The operation takes:

- One scalar \(\alpha\).
- One vector \(x\).

If

```text
x = [x_1, x_2, ..., x_n]^T,
```

then

```text
\alpha x = [\alpha x_1, \alpha x_2, ..., \alpha x_n]^T.
```

The output is a vector of the same dimension as the input vector. Geometrically:

- If \(\alpha > 1\), the vector is magnified in the same direction.
- If \(0 < \alpha < 1\), the vector is shrunk in the same direction.
- If \(\alpha < 0\), the vector points in the opposite direction.

The instructor stresses that this geometric interpretation is easy in two or three dimensions and then extended abstractly to higher-dimensional spaces.

## Vector Addition

The second operation is vector addition. Addition is defined for two vectors of the same dimension. If

```text
x = [x_1, x_2, ..., x_n]^T
y = [y_1, y_2, ..., y_n]^T,
```

then

```text
x + y = [x_1 + y_1, x_2 + y_2, ..., x_n + y_n]^T.
```

Geometrically, one can translate the tail of the second vector to the tip of the first vector. The sum is the vector from the original starting point to the final tip. The two vectors and their sum form a triangle.

The instructor gives a displacement example. If someone first moves a certain amount north and east, and then moves another amount west and north, the final location is obtained by summing the displacement vectors. In geometric terms, the second motion vector can be moved so that it starts at the end of the first motion vector, and the resulting final location is the vector sum.

Exam note: the final location after sequential vector displacements is given by vector addition.

## Linear Combination

The lecture combines scalar multiplication and vector addition into the central operation of a linear combination.

For two vectors \(x_1, x_2 \in \mathbb{R}^n\) and scalars \(\alpha_1, \alpha_2 \in \mathbb{R}\),

```text
y = \alpha_1 x_1 + \alpha_2 x_2
```

is a linear combination. The scalars are degrees of freedom. Each vector is scaled first, and the scaled vectors are then added.

The definition extends to any number of vectors:

```text
y = \sum_{i=1}^m \alpha_i x_i.
```

Here \(n\) is the dimension of each vector, while \(m\) is the number of vectors in the combination. The instructor explicitly clarifies that \(m\) does not have to equal \(n\). You may take any number of vectors in a linear combination, even more than the dimension. Later, the number of vectors relative to dimension will matter for linear independence, but not for the basic definition of linear combination.

There are no restrictions on the scalars in a linear combination. They can be arbitrary real numbers in the current discussion, with complex extensions to come later in the course.

## Span

The span of a set of vectors is the set of all possible linear combinations of those vectors.

If we are given vectors \(x_1, x_2, \ldots, x_m\), then

```text
span{x_1, ..., x_m}
= { \sum_{i=1}^m \alpha_i x_i : \alpha_i are scalars }.
```

For two vectors in the plane:

- If \(x_1\) and \(x_2\) are not collinear, their span is the whole plane \(\mathbb{R}^2\).
- If \(x_1\) and \(x_2\) point in the same or opposite direction, their span is a line through the origin.

The instructor calls this line a hyperplane in the two-dimensional setting. It goes through the origin because linear combinations allow all scalars, including zero, and the zero vector is always included.

In three dimensions, if two non-collinear vectors are considered as position vectors from the origin, their linear combinations form a plane through the origin. The instructor warns that a picture can be misleading if one forgets the role of the origin. Linear combinations of \(x_1\) and \(x_2\) form the plane through the origin and those vectors, not merely the line through the endpoints \(x_1\) and \(x_2\).

Relationship: span is built directly from linear combinations. The geometric object produced by a span depends on the directions and dependencies among the vectors.

## Affine Combination

An affine combination is a restricted linear combination. The formula still looks like a weighted sum:

```text
y = \sum_{i=1}^m \alpha_i x_i,
```

but the weights must satisfy

```text
\sum_{i=1}^m \alpha_i = 1.
```

There is no nonnegativity requirement for affine combinations. The coefficients may be negative, as long as they sum to one.

The instructor gives the overall grade of a student as an example. If the grade weights sum to one, then the overall grade is an affine combination of the grading components. This makes the grading method meaningful as a weighted average.

### Two-Point Affine Combinations

For two points \(x_1\) and \(x_2\), an affine combination has the form

```text
\alpha_1 x_1 + \alpha_2 x_2,
```

with

```text
\alpha_1 + \alpha_2 = 1.
```

Since \(\alpha_2 = 1 - \alpha_1\), we can write

```text
\alpha_1 x_1 + (1 - \alpha_1)x_2.
```

This can be rearranged as

```text
x_2 + \alpha_1(x_1 - x_2).
```

Proof idea from the instructor: \(x_1 - x_2\) is the direction vector from \(x_2\) to \(x_1\). Starting at \(x_2\) and moving by an arbitrary scalar multiple of \(x_1 - x_2\) traces the whole line through the two points. Therefore all affine combinations of two points lie on the line through them, and every point on that line can be represented this way.

Special cases:

- If \(\alpha_1 = 0\), the point is \(x_2\).
- If \(\alpha_1 = 1\), the point is \(x_1\).
- If \(0 < \alpha_1 < 1\), the point lies between \(x_1\) and \(x_2\).
- If \(\alpha_1 > 1\), the point lies beyond \(x_1\) on the same line.
- If \(\alpha_1 < 0\), the point lies beyond \(x_2\) on the other side.

This remains true in three dimensions: all affine combinations of two points form the line through the two points.

Relationship to linear combinations: linear combinations of two non-collinear position vectors in three dimensions can form a plane through the origin. Affine combinations of two points form only the line through those two points. The restriction that the weights sum to one changes the geometry.

## Affine Hull

The affine hull of a set is the set of all possible affine combinations of points in that set.

For three points \(x_1, x_2, x_3\), affine combinations have the form

```text
\alpha_1 x_1 + \alpha_2 x_2 + \alpha_3 x_3
```

with

```text
\alpha_1 + \alpha_2 + \alpha_3 = 1.
```

If the three points are not collinear, their affine hull is the plane containing the three points. If the points are collinear, their affine hull is the line containing them. The instructor says these dimension issues will be discussed later and asks students to verify the plane case at home.

Relationship: affine hull is to affine combinations what span is to linear combinations.

## Convex Combination

A convex combination is an even more restricted affine combination. It has the same weighted-sum form:

```text
y = \sum_{i=1}^m \alpha_i x_i,
```

but now the weights must satisfy both:

```text
\sum_{i=1}^m \alpha_i = 1
```

and

```text
\alpha_i \ge 0 for all i.
```

Thus:

- Linear combination: no restriction on coefficients.
- Affine combination: coefficients sum to one.
- Convex combination: coefficients sum to one and are nonnegative.

The instructor again uses grades as an example. A normal overall grade calculation is a convex combination if the weights sum to one and are nonnegative. It is also an affine combination and a linear combination, but convex combination is the most specific description.

For two points, all convex combinations form the line segment joining them. The instructor says this line segment is sometimes called a chord. Unlike affine combinations, convex combinations cannot go beyond the endpoints because nonnegative weights summing to one keep the point between the endpoints.

## Convex Hull

Given a set \(S\), the convex hull of \(S\), often written \(\operatorname{conv}(S)\), is the set of all possible convex combinations of elements of \(S\).

In symbolic form:

```text
conv(S) =
{ \sum_{i=1}^m \alpha_i x_i :
  x_i in S,
  \alpha_i >= 0,
  \sum_{i=1}^m \alpha_i = 1,
  m is any positive integer }.
```

For two points, the convex hull is the line segment between them.

For three non-collinear points, the convex hull is the triangle whose vertices are those three points. This contrasts with the affine hull of the same three points, which is the entire plane through them.

The instructor also describes the triangle as an intersection of half-spaces within the plane of the three points. Each line through a pair of vertices defines a half-space inside that plane. The triangular convex hull is the intersection of the appropriate three half-spaces, restricted to the affine hull of the three points.

## Convex Set

A set is convex if, whenever we pick any two points in the set, the entire line segment joining those points also stays inside the set.

Using convex-combination notation: a set \(S\) is convex if for any \(x_1, x_2 \in S\) and any \(\alpha \in [0,1]\),

```text
\alpha x_1 + (1 - \alpha)x_2 in S.
```

The instructor describes a round or bowl-like set as convex because every chord between two points of the set remains inside the set. A heart-shaped set is not convex because one can choose two points inside it such that part of the line segment between them goes outside the set.

Exam note: convexity is an important definition.

## Convex Optimization and Convex Functions

The instructor relates convex sets to optimization. In optimization theory, convex optimization is the simpler case, while non-convex optimization is hard and remains an active difficult area.

The intuitive reason is that searching inside a convex set is simpler. If line segments between feasible points stay feasible, the geometry is better behaved. The instructor also notes that convex optimization is not only about the search domain; the function being optimized is potentially even more important.

For a scalar function of a scalar variable, a convex function looks like a bowl or parabola. A parabola is a special case. Such a function does not have multiple separate bumps or local minima in the way a non-convex function might. This supports the existence of a simple global optimum structure.

The instructor introduces the epigraph of a function: the set of points lying above the graph of the function. A function is convex when its epigraph is convex, with the domain also convex. An optimization problem involving such a function and domain is called a convex optimization problem.

Relationship:

- Convex combination leads to convex hull.
- Convex hull and line-segment containment lead to convex sets.
- Convex sets and convex epigraphs are central to convex optimization.

## Applications of Convex Combinations

The instructor returns to the student-grade setting with three grading components: midterm, final, and homework.

There are two natural ways to organize the data:

- Student vectors: each vector contains one student's midterm, final, and homework grades.
- Component vectors: one vector contains all students' midterm grades, one contains all students' final grades, and one contains all students' homework grades.

The instructor notes that, in the small example, there are three student vectors and three grading-component vectors, so six related vectors appear. He also warns that the equality between the number of students and the number of grading components in this example is accidental; he should have chosen different counts to avoid suggesting they must coincide.

If the overall grade vector for the whole class is computed from the midterm vector, final vector, and homework vector using nonnegative weights that sum to one, then the overall grade vector is a convex combination of the component vectors. For example:

```text
overall_vector =
0.3 * midterm_vector +
0.4 * final_vector +
0.3 * homework_vector
```

This produces each student's overall grade as the corresponding entry of the resulting vector.

The instructor then connects this to probability. For a discrete random vector, expectation is computed by multiplying each possible realization by its probability and summing:

```text
E[X] = \sum_i p_i x_i.
```

The probabilities satisfy:

```text
p_i >= 0
\sum_i p_i = 1.
```

Therefore, expectation is a convex combination of the possible realizations of the random vector.

Another example is the average student vector. If all students are averaged with equal nonnegative weights that sum to one, the result is a vector containing the midterm average, final average, and homework average. This average vector is a convex combination of the student vectors.

## End-of-Lecture Summary and Next Lecture

The instructor summarizes the progression of ideas:

1. Scale a vector by a scalar.
2. Add vectors.
3. Combine scaling and addition to get linear combinations.
4. Restrict the weights to sum to one to get affine combinations.
5. Add nonnegativity of weights to get convex combinations.

These ideas support span, affine hull, convex hull, convex sets, hyperplanes, half-spaces, and geometric reasoning in high-dimensional vector spaces.

The next lecture will introduce another operation, but the transcript is garbled at this point. The instructor then says the next lecture will introduce norms, define distance for vectors, extend distance concepts from two- and three-dimensional spaces to high-dimensional and arbitrary vector spaces, and later extend these ideas to matrices. After this introductory phase, the course will move toward the formal vector space definition.

## Exam-Relevant Topics Marked in the Source

The corrected transcript explicitly marks these as likely exam topics:

- Hyperplanes and half-spaces.
- Affine and convex combinations.
- Convex sets and convex hulls.

The transcript also marks as exam-relevant the ordered nature of vector entries, the student-grade vector example, grade-threshold hyperplanes and half-spaces in two, three, and four dimensions, the final location interpretation of vector addition, the importance of linear combination, the two-point convex-combination line segment, convexity as an important definition, convex functions/epigraphs in optimization, the three-point convex hull triangle versus affine hull plane, and the grade/probability/average examples of convex combinations.

## Source and Coverage Note

Source used: `corrected/lecture2_corrected.md` only.

Coverage: These notes preserve the lecture's chronological structure, examples, exam-marked comments, instructor warnings, definitions, relationships between concepts, proof ideas, and end-of-lecture preview.
