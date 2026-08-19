# Lecture 06 Exam Report

Owned output: `study_outputs/exam_reports/lecture_06_exam.md`

Sources read:

- `corrected/lecture6_corrected.md`
- `study_outputs/lecture_notes/lecture_06_notes.md`
- `study_outputs/audits/lecture_06_audit.md`

Scope note: only Lecture 06 was processed. This report extracts exam-relevant signals only, not a general lecture summary.

## High Probability Topics

### Existence versus uniqueness for `Ax=b`

Probability: High

Why: The corrected transcript marks the opening discussion as `[LIKELY EXAM TOPIC]`, and the whole lecture keeps returning to the two separate questions: does a solution exist, and if it exists, is it unique?

Exam-relevant core:

- Existence asks whether there is at least one `x` satisfying `Ax=b`.
- Uniqueness asks whether that solution is the only one.
- The old `2 x 2` line picture generalizes:
  - one intersection point: unique solution,
  - parallel distinct lines: no solution,
  - coincident lines: infinitely many solutions.

Likely conceptual questions:

- Given a geometric description, identify whether the system has no solution, one solution, or infinitely many.
- Explain why existence and uniqueness are logically separate.
- State what uniqueness means only after existence is known.

### Column/range space criterion for existence

Probability: High

Why: The transcript marks the range/column-space existence discussion as `[LIKELY EXAM TOPIC]`. The instructor repeats that the column view of `Ax` decides whether `b` can be generated.

Exam-relevant core:

```text
Ax=b has a solution  <=>  b is in R(A)=Col(A).
```

- `Ax` is a linear combination of the columns of `A`.
- The range space is the set of all possible outputs:

```text
R(A) = { Ax : x in R^n } = Col(A).
```

- If `b` lies outside `R(A)`, no solution exists.
- If `b` lies inside `R(A)`, at least one solution exists.

Notation trap:

- The corrected transcript contains speech artifacts such as "rank space", "rate space", or "green space"; the intended concept is range space.

Likely conceptual questions:

- Decide if `Ax=b` is solvable by checking whether `b` is in the column space.
- Give the three equivalent descriptions of `R(A)`: possible outputs, span of columns, and all right-hand sides for which `Ax=b` is solvable.
- Explain why the column space lives in the output space `R^m`.

### Existence for every right-hand side and the shape condition

Probability: High

Why: The instructor repeatedly distinguishes solvability for a fixed `b` from solvability for every `b`. The transcript also flags a "remember" exam note about square/fat matrices.

Exam-relevant core:

```text
Ax=b has a solution for every b in R^m  <=>  R(A)=R^m.
```

- The column space must cover the whole target/output space.
- Necessary shape condition:

```text
n >= m
```

- So `A` must be square or fat/wide.
- This shape condition is necessary, not sufficient.
- Tall matrices cannot guarantee existence for arbitrary `b`, because their columns cannot span all of a higher-dimensional output space.

Likely conceptual questions:

- Explain why "square or fat" is necessary for existence for all `b`.
- Give an example of why square or fat is not sufficient.
- Compare "there exists a solution for this `b`" with "there is a solution for every `b`".

### Right inverse from full range space

Probability: High

Why: The corrected transcript explicitly flags "Remember how we got this conclusion?" as `[EXAM NOTE]`. That is a strong signal that the derivation, not only the final statement, is testable.

Exam-relevant core:

Assume:

```text
R(A)=R^m.
```

Then each standard basis vector `e_i` is in the range, so there is at least one `d_i` such that:

```text
A d_i = e_i.
```

Build:

```text
D = [d_1 d_2 ... d_m].
```

Then:

```text
AD = [A d_1 A d_2 ... A d_m] = [e_1 e_2 ... e_m] = I_m.
```

So `D` is a right inverse of `A`.

Important remark:

- If `A` is fat and has full range, there can be infinitely many right inverses.
- The right-inverse result is not magic; it follows directly from being able to solve `Ax=b` for every basis vector `b=e_i`.

Likely conceptual questions:

- Prove that full range implies a right inverse.
- Explain the dimensions of `D`.
- Explain why the standard basis vectors are used in the construction.

### Row space, null space, and uniqueness

Probability: High

Why: The corrected transcript marks row space/null space/uniqueness as `[LIKELY EXAM TOPIC]`. The instructor develops a full proof of why null space controls uniqueness.

Exam-relevant core:

The null space is:

```text
N(A) = { x in R^n : Ax=0 }.
```

It is a subspace:

- if `x in N(A)`, then `alpha x in N(A)`;
- if `x,y in N(A)`, then `x+y in N(A)`.

Using the row view of multiplication:

```text
x in N(A)  <=>  x is orthogonal to every row of A.
```

Therefore:

```text
N(A) = Row(A)^\perp.
```

Uniqueness condition:

```text
N(A) = {0}.
```

Reason:

- If `Ax=b` and `z in N(A)`, then `A(x+z)=b`.
- If `z != 0`, then `x+z` gives a second solution.
- Therefore uniqueness requires no nonzero null-space vector.

Instructor emphasis:

- The null space cannot be empty because `0` always maps to `0`.
- The smallest possible null space is the trivial null space `{0}`.
- The `b=0` case already reveals non-uniqueness if multiple vectors map to the origin.

Likely conceptual questions:

- Prove that a nonzero null-space vector destroys uniqueness.
- Explain why `N(A)={0}` is necessary and sufficient for uniqueness whenever a solution exists.
- Given a matrix, compute or reason about `N(A)` and decide whether solutions are unique.

### Row space covering the input space

Probability: High

Why: This is the stated dual of the existence condition and is repeated in the lecture's comparison section.

Exam-relevant core:

```text
Uniqueness for solvable systems
<=> N(A)={0}
<=> Row(A)=R^n.
```

- Row space is a subspace of the input space.
- If the row space spans the whole input space, then no nonzero vector can be orthogonal to all rows.
- Necessary shape condition:

```text
m >= n
```

- So `A` must be square or tall.
- This shape condition is necessary, not sufficient.

Likely conceptual questions:

- Explain why uniqueness needs enough rows, while existence for all `b` needs enough columns.
- State the duality:

```text
Existence for every b: Col(A)=R^m.
Uniqueness: Row(A)=R^n.
```

### Shape comparison: fat, tall, and square matrices

Probability: High

Why: The transcript explicitly flags this as `[EXAM NOTE]` with "remember square or fat matrices." The instructor also contrasts it directly with the uniqueness shape condition.

Exam-relevant core:

```text
Existence for every b requires: m <= n  -> square or fat.
Uniqueness requires:              m >= n  -> square or tall.
Both require:                     m = n  -> square.
```

Important warning:

- These are necessary shape conditions, not sufficient conditions.
- Only a subset of square matrices satisfy both full existence and uniqueness.
- When both hold for a square matrix, the left and right inverses coincide and are called `A^{-1}`.

Likely conceptual questions:

- Fill in a table comparing tall, square, and fat matrices.
- Explain why a tall matrix can have uniqueness for solvable `b` but cannot guarantee existence for every `b`.
- Explain why a fat matrix can have existence for every `b` but cannot have uniqueness.

### Fundamental theorem: row rank equals column rank

Probability: High

Why: The transcript explicitly says "we are coming to an important result" and marks the result as `[EXAM NOTE]`. The notes also flag rank as a likely exam topic.

Exam-relevant core:

Let:

```text
r_C = dim(Col(A))
r_R = dim(Row(A))
```

Then:

```text
r_C = r_R.
```

This common dimension is:

```text
rank(A).
```

Instructor emphasis:

- The row space and column space live in different ambient spaces.
- They are defined using different vectors.
- Their dimensions are still equal.

Likely conceptual questions:

- Define row rank, column rank, and rank.
- Explain why it is meaningful that row and column rank are equal even though the spaces live in different dimensions.
- Use rank to connect existence, uniqueness, and matrix shape.

### Proof idea for row rank <= column rank

Probability: High

Why: The lecture spends substantial time on this proof, and the instructor frames the rank equality as fundamental before continuing the system-of-equations analysis.

Exam-relevant proof skeleton:

1. Let `v_1,...,v_rR` be a basis for the row space.
2. Consider their images:

```text
A v_1, ..., A v_rR.
```

3. These images lie in `Col(A)`.
4. Show they are linearly independent.
5. Suppose:

```text
alpha_1 A v_1 + ... + alpha_r A v_r = 0.
```

6. Factor out `A`:

```text
A(alpha_1 v_1 + ... + alpha_r v_r)=0.
```

7. The vector inside parentheses lies in the row space, but it is also in the null space.
8. Row space and null space intersect only at `0`.
9. Therefore the vector is `0`.
10. Since the `v_i` are linearly independent, all `alpha_i=0`.
11. Thus the images are linearly independent inside `Col(A)`, so:

```text
r_R <= r_C.
```

Reverse direction:

- Use the analogous argument with a column-space basis and `A^T`.
- This gives `r_C <= r_R`.
- Therefore `r_C=r_R`.

Likely conceptual questions:

- Reproduce the proof outline.
- Identify where the row-space/null-space disjointness is used.
- Explain why `A v_i` belongs to the column space.

## Medium Probability Topics

### Two perceptions of matrix-vector multiplication

Probability: Medium

Why: The instructor calls this a "key observation" and says it is central to the vector-space analysis. It is foundational for the high-probability topics, though less likely to be tested alone.

Exam-relevant core:

Column view:

```text
Ax = x_1 c_1 + ... + x_n c_n.
```

- Used for existence.

Row view:

```text
Ax = [r_1^T x, r_2^T x, ..., r_m^T x]^T.
```

- Used for null space and uniqueness.

Instructor visual-notation warning:

- A row vector may be represented visually using a column vector and then transposed.
- Do not confuse the displayed vector shape with whether it is acting as a row or column.

Likely conceptual questions:

- Express `Ax` using columns.
- Express the entries of `Ax` as inner products with rows.
- Explain why the column view is tied to existence and the row view is tied to uniqueness.

### Transpose mapping and row space as range of `A^T`

Probability: Medium

Why: The instructor warns that the notation is confusing and explicitly says the `A^T` mapping will be used in the vector-space method.

Exam-relevant core:

```text
Row(A) = Col(A^T) = R(A^T).
```

Notation trap:

- In `R(A^T)`, the `R` means range, not row.
- Row space of `A` is the range space of `A^T`.

Warning:

- `A^T` is not generally `A^{-1}`.
- `A^T(Ax)` is not generally equal to `x`.
- Transpose reverses dimensions but does not undo the original map except in special cases.

Likely conceptual questions:

- Explain why row space equals column space of `A^T`.
- Identify the domain and codomain of `A^T`.
- Avoid claiming that transpose is inverse.

### Linear independence implications of full range

Probability: Medium

Why: The transcript flags this as an exam note and says some proof directions are left to students. It supports the higher-probability full-range condition.

Exam-relevant core:

If:

```text
R(A)=R^m,
```

then:

- the columns of `A` contain `m` linearly independent columns;
- the rows of `A` are linearly independent.

Important distinction:

- Full range does not mean all columns are linearly independent.
- If `n>m`, the full set of columns must be dependent.
- The correct statement is that some subset of `m` columns forms a basis of `R^m`.

Proof hint:

- If columns span `R^m`, remove dependent extra columns until a basis remains.

Likely conceptual questions:

- Explain why a fat full-range matrix has dependent columns but independent rows.
- Prove or justify that full range implies row independence.
- Distinguish "all columns independent" from "some `m` columns independent."

### Contrapositive proof: row independence and full column space

Probability: Medium

Why: The audit specifically notes this proof detail as important, and the notes patched it. The instructor develops the argument but does not present it as the final theorem.

Exam-relevant proof idea:

Rows are linearly independent exactly when:

```text
alpha^T A = 0  =>  alpha=0.
```

This product can be read two ways:

- a linear combination of rows;
- a row vector of inner products between `alpha` and the columns.

If `alpha^T A=0`, then `alpha` is orthogonal to every column.

If also `alpha in R(A)`, then:

```text
alpha = beta_1 c_1 + ... + beta_n c_n.
```

Taking inner product with `alpha` gives:

```text
alpha^T alpha = beta_1 alpha^T c_1 + ... + beta_n alpha^T c_n = 0.
```

Thus `alpha=0`, contradiction if `alpha` was nonzero.

Likely conceptual questions:

- Explain why a nonzero vector orthogonal to all columns cannot lie in the span of the columns.
- Use a contradiction argument to connect row independence and full column space.

### Direct sum, disjointness, and the union warning

Probability: Medium

Why: The instructor gives an explicit warning not to write the union expression. This is a notation trap likely to appear in conceptual or true/false questions.

Exam-relevant core:

Wrong:

```text
R^n = Row(A) union N(A)
```

Correct:

```text
R^n = Row(A) direct-sum N(A).
```

Meaning:

- Every vector in `R^n` can be written as a sum of one row-space vector and one null-space vector.
- The two spaces are disjoint in the lecture's sense:

```text
Row(A) intersection N(A) = {0}.
```

- In this case they are also orthogonal complements.

Likely conceptual questions:

- Explain why union is wrong.
- Define disjoint subspaces as used in the lecture.
- State the direct-sum decomposition of the input space.

### Four fundamental subspaces and left null space

Probability: Medium

Why: The instructor says the three-subspace picture is incomplete and adds the output-space companion. This is conceptually important, but less directly flagged than existence/uniqueness/rank.

Exam-relevant core:

Input-space subspaces:

```text
Row(A) = R(A^T) subset R^n
N(A) subset R^n
```

Output-space subspaces:

```text
Col(A)=R(A) subset R^m
N(A^T) subset R^m
```

Orthogonal decompositions:

```text
R^n = Row(A) direct-sum N(A)
R^m = R(A) direct-sum N(A^T)
```

Left null space:

```text
N(A^T) = { z in R^m : A^T z = 0 }.
```

Taking transpose:

```text
A^T z = 0  =>  z^T A = 0^T.
```

So `N(A^T)` is called the left null space of `A`.

Naming trap:

- `N(A)` is usually just "null space", not "right null space".
- Kernel and null space refer to the same idea.
- "Left null space" specifically means `N(A^T)`.

Likely conceptual questions:

- List the four fundamental subspaces and their ambient spaces.
- Explain why `N(A^T)` is orthogonal to the column space.
- Explain the name "left null space".

### Concrete examples used in lecture

Probability: Medium

Why: The instructor uses simple examples to make the conditions concrete. They are good exam-style conceptual checks, even if the specific matrices may not be reused.

Example 1: `3 x 3` matrix with columns `(1,0,0)^T`, `(0,1,0)^T`, `(0,0,0)^T`.

- Column space is the `xy`-plane.
- Row space is also the `xy`-plane for this special matrix.
- Existence for every `b` is not guaranteed.
- If `b` lies in the `xy`-plane, solutions exist.
- Solutions are not unique because the null space is the `z`-axis.

Warning:

- Row space and column space being equal here is special, not true in general.

Example 2: `3 x 2` tall matrix mapping `R^2` to `R^3`.

- Column space is the `xy`-plane in `R^3`.
- Row space covers the whole input space `R^2`.
- Null space is `{0}`.
- Existence is not guaranteed for arbitrary `b`.
- If `b` is in the range, the solution is unique.

Likely conceptual questions:

- For a given matrix, identify column space, row space, null space, and decide existence/uniqueness.
- Explain how a tall matrix can have uniqueness without existence for all `b`.
- Explain why equality of row and column spaces is not generally meaningful when their ambient spaces differ.

## Low Probability Topics

### Finite-dimensional clarification

Probability: Low

Why: It appears as a response to a student question. It sets scope but is unlikely to be a standalone exam target.

Exam-relevant core:

- The lecture works with finite-dimensional spaces `R^n` and `R^m`.
- Extensions to general operators are outside the course level at this point.

Likely conceptual question:

- If asked about the scope of the theory in this lecture, answer in finite-dimensional matrix terms.

### Brute-force mapping picture

Probability: Low

Why: The audit identified it as a missing detail patched into the notes, but it mainly supports intuition for the column-space criterion.

Exam-relevant core:

- Vary `x` in the input space.
- Watch where `Ax` lands in the output space.
- The attainable outputs form the range space.
- The question "can `Ax` reach `b`?" becomes "is `b` in the range?"

Likely conceptual question:

- Explain the geometric meaning of solving `Ax=b` as trying to hit `b` through the map `A`.

### Dimension intuition for orthogonal complements

Probability: Low

Why: The instructor explicitly says the complete proof was not given. The intuition may support conceptual questions but is less likely as a formal proof demand.

Exam-relevant core:

- If `R(A)` has dimension `r`, then its orthogonal complement `N(A^T)` has dimension `m-r`.
- Basis vectors from the subspace plus basis vectors from the orthogonal complement span the ambient output space.

Likely conceptual question:

- Explain why the dimensions of `R(A)` and `N(A^T)` add to `m`.

## Highest-Yield Exam Checklist

- Know `Ax=b` solvability:

```text
b in Col(A)=R(A)
```

- Know existence for every `b`:

```text
Col(A)=R^m, requires square or fat, implies right inverse.
```

- Know uniqueness:

```text
N(A)={0} <=> Row(A)=R^n, requires square or tall, implies left inverse.
```

- Know the shape comparison:

```text
existence for all b: m <= n
uniqueness:          m >= n
both:                m = n
```

- Know the warning:

```text
R^n is not Row(A) union N(A).
R^n = Row(A) direct-sum N(A).
```

- Know rank:

```text
rank(A)=dim(Col(A))=dim(Row(A)).
```

- Be able to outline the proof that row-rank equals column-rank.

## Likely Exam Question Forms

1. State and justify the existence criterion for `Ax=b`.
2. State and justify the uniqueness criterion using the null space.
3. Given matrix dimensions, say whether existence for every `b` or uniqueness is possible.
4. Prove that full range implies a right inverse.
5. Explain why a nonzero null-space vector creates infinitely many or multiple solutions.
6. Explain why `A^T` is not generally the inverse of `A`.
7. Identify the four fundamental subspaces and their ambient spaces.
8. Correct false statements involving row space, column space, null space, union, direct sum, or rank.
9. Reproduce the proof idea for `dim(Row(A)) <= dim(Col(A))`.
10. Use a small matrix example to decide existence, uniqueness, and rank.
