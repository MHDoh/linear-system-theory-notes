# Lecture 02 Exam Report

Owned scope: Lecture 02 only. Sources used: `corrected/lecture2_corrected.md`, `study_outputs/lecture_notes/lecture_02_notes.md`, and `study_outputs/audits/lecture_02_audit.md`.

## High Probability

### Hyperplanes and Half-Spaces

Probability: High

Why: The corrected transcript explicitly marks this as a likely exam topic. The instructor returns to it through two-, three-, and four-dimensional grade examples, then reuses it in the credit-approval/neuron interpretation.

Exam-relevant points:

- Equality such as `0.4m + 0.6f = 40` defines the threshold hyperplane.
- Inequality such as `0.4m + 0.6f > 40` defines a half-space.
- In 2D, a hyperplane is a line; in 3D, it is a plane; in 4D and higher, the same terminology still applies even though it cannot be drawn.
- A hyperplane does not have to pass through the origin.
- The sets describe all potential vectors satisfying the condition, not only observed data points.

Likely conceptual questions:

- Given a weighted grade rule and a threshold, identify the hyperplane and the passing/failing half-spaces.
- Explain why the same rule remains meaningful in four dimensions even when it cannot be visualized.
- Explain why a threshold line in the grade example is still a hyperplane even if it is away from the origin.

### Affine and Convex Combinations

Probability: High

Why: Explicitly marked as a likely exam topic and repeatedly contrasted with linear combinations. The instructor emphasizes coefficient restrictions and uses grades, expectation, and averages as applications.

Exam-relevant points:

- Linear combination: `sum alpha_i x_i`, no coefficient restriction.
- Affine combination: same weighted sum, with `sum alpha_i = 1`.
- Convex combination: affine combination plus `alpha_i >= 0`.
- Normal grade averages with nonnegative weights summing to one are convex combinations.
- Expectation of a discrete random vector is a convex combination of realizations.
- Average student vector is a convex combination of student vectors.

Notation traps:

- Do not confuse number of vectors `m` with vector dimension `n`; the instructor explicitly clarified they do not have to match.
- Convex implies affine, and affine implies linear, but the reverse implications are false without the extra restrictions.
- Nonnegative weights are required only for convex combinations, not affine combinations.

Likely conceptual questions:

- Classify a weighted sum as linear, affine, convex, or none based on the coefficients.
- Explain why an expected value is a convex combination.
- Explain why a valid grade average is convex, not merely affine.

### Convex Sets and Convex Hulls

Probability: High

Why: Explicitly marked as a likely exam topic. The instructor calls convexity a very important definition and connects it to optimization, convex functions, and epigraphs.

Exam-relevant points:

- A set is convex if the line segment between any two points in the set stays inside the set.
- The convex hull `conv(S)` is the set of all convex combinations of points from `S`.
- For two points, the convex hull is the line segment between them.
- For three non-collinear points, the convex hull is the triangle with those points as vertices.
- Convex optimization is easier than non-convex optimization because the feasible geometry is better behaved.
- For a convex function, the epigraph is convex and the domain is also convex.

Important distinction:

- The affine hull of three non-collinear points is the entire plane through them.
- The convex hull of the same three points is only the triangle.

Likely conceptual questions:

- Decide whether a set is convex using the line-segment test.
- Compare affine hull and convex hull for two or three points.
- Explain the epigraph criterion for convex functions.

## Medium Probability

### Span and Linear Combination Geometry

Probability: Medium

Why: Linear combination is exam-marked as important, and span is introduced directly from it. It is not separately listed in the transcript's likely-exam-topic summary, but the instructor spent time on geometric cases and a student clarification.

Exam-relevant points:

- Span is the set of all possible linear combinations.
- Two non-collinear vectors in `R^2` span the whole plane.
- Two collinear vectors in `R^2` span a line through the origin.
- In `R^3`, two non-collinear position vectors span a plane through the origin.

Notation and concept traps:

- Linear combinations include the zero vector and pass through the origin.
- Do not confuse the span of two vectors with the line segment joining their endpoints.
- A misleading drawing can make a span look like an affine line; the origin matters.

Likely conceptual questions:

- Determine whether two vectors span a line or the whole plane.
- Explain why span objects pass through the origin.
- Contrast span with affine hull.

### Proof That Two-Point Affine Combinations Form a Line

Probability: Medium

Why: This is one of the most proof-heavy parts of the lecture. The instructor walks through the algebra and responds to a student asking how we know affine combinations only yield that line.

Exam-relevant derivation:

For `alpha_1 + alpha_2 = 1`,

```text
alpha_1 x_1 + alpha_2 x_2
= alpha_1 x_1 + (1 - alpha_1)x_2
= x_2 + alpha_1(x_1 - x_2).
```

This starts at `x_2` and moves along direction `x_1 - x_2`, so it traces the line through `x_1` and `x_2`.

Likely conceptual questions:

- Prove that affine combinations of two points lie on the line through the points.
- Interpret `alpha < 0`, `0 <= alpha <= 1`, and `alpha > 1` geometrically.

### Matrix as Columns or Rows of Vectors

Probability: Medium

Why: Not marked as a likely exam topic, but the instructor says the row/column view lies at the heart of vector space concepts and systems of linear equations.

Exam-relevant points:

- A matrix can be viewed as a rectangular table of numbers.
- It can also be viewed as a collection of column vectors or row vectors.
- In the grade example, columns can represent students and rows can represent grading components.

Notation trap:

- The same matrix supports both row-based and column-based interpretations; exam questions may ask which interpretation matches a given modeling choice.

Likely conceptual questions:

- Given a class-grade matrix, identify whether students are columns or rows.
- Explain why viewing a matrix as vectors matters for later linear-equation analysis.

### Vector Addition and Scalar Multiplication

Probability: Medium

Why: Vector addition is marked with an exam note for final displacement, and scalar multiplication is foundational for linear combinations. These operations are less likely to be standalone major questions, but likely appear inside larger questions.

Exam-relevant points:

- Scalar multiplication scales every component by the same scalar.
- Positive scalars keep direction; negative scalars reverse direction.
- Vector addition requires vectors of the same dimension and adds matching coordinates.
- Sequential displacements are combined by vector addition.

Likely conceptual questions:

- Compute a vector sum or scalar multiple.
- Explain the geometric meaning of adding two displacement vectors.
- State why vectors must have the same dimension to be added.

## Low Probability

### Course Motivation: Geometry Behind Algebra

Probability: Low

Why: The opening is marked as likely exam-relevant, but mainly as framing. It is more likely to appear as a short conceptual prompt than as a calculation or proof question.

Exam-relevant points:

- Linear system theory uses linear algebra and vector-space methods to translate algebraic expressions, constraints, objective functions, and data into geometric objects.
- High-dimensional spaces cannot be drawn directly, but geometric terminology remains useful.
- Instructor warning: high-dimensional spaces can behave differently from 2D or 3D intuition.

Likely conceptual questions:

- Explain why geometric language is useful for algebraic constraints.
- Explain why high-dimensional geometry must be handled carefully.

### Ordered Vector Entries and Data-as-Geometry

Probability: Low

Why: The order of entries is explicitly exam-marked, but it is a small notation trap rather than a full topic. It may appear as part of grade-vector or feature-vector modeling.

Exam-relevant points:

- Vector entry order matters: `[midterm, final]^T` is not the same representation as `[final, midterm]^T`.
- Non-geometric data, such as grades or bank features, can be treated geometrically after being placed into vectors.

Likely conceptual questions:

- Identify what each coordinate of a feature or grade vector represents.
- Explain why swapping vector entries changes the meaning of the vector.

### Credit Approval, Neurons, and Intersections of Half-Spaces

Probability: Low

Why: The example reinforces hyperplanes and half-spaces, but the instructor explicitly says the lecture is not going into neural network theory. Exam value is mainly conceptual.

Exam-relevant points:

- A single threshold neuron checks whether `w^T x - threshold` is positive or negative.
- Geometrically, that is a half-space membership test.
- When one hyperplane cannot separate data, intersections of multiple half-spaces can describe more complex regions.
- Different neurons have different weights because they represent different hyperplanes.

Likely conceptual questions:

- Explain why a threshold neuron corresponds to a half-space test.
- Explain why two half-space checks need different weight vectors.
- Describe how an intersection of half-spaces can represent a region that one half-space cannot.

## Instructor Warnings and Traps

- Hyperplanes do not need to pass through the origin. Probability: High.
- In dimensions above three, keep the terminology even when visualization fails. Probability: High.
- `m`, the number of vectors in a linear combination, does not have to equal `n`, the vector dimension. Probability: High.
- Linear combination, affine combination, and convex combination differ only by coefficient restrictions, so coefficient conditions are the main trap. Probability: High.
- Span uses arbitrary linear combinations and therefore includes the origin; affine hull does not have to pass through the origin. Probability: Medium.
- Three students and three grading components in the class example were accidental; those counts need not match. Probability: Medium.
- The transcript has a garbled phrase before the next-lecture norm preview; do not infer an unprovided operation from it. Probability: Low.

## Proof-Heavy Targets

- Show two-point affine combinations form the entire line through the two points. Probability: Medium.
- Show two-point convex combinations form only the line segment between the points. Probability: High.
- Compare the affine hull and convex hull of three non-collinear points. Probability: High.
- Explain the triangle convex hull as an intersection of half-spaces within the affine plane. Probability: Medium.

## Theorem-Heavy Targets

No named theorem-heavy section appears in Lecture 02. The exam-relevant material is definition-heavy and proof/interpretation-heavy rather than theorem-heavy. Probability: Low for named-theorem recall from this lecture.
