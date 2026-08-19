# Lecture 05 Exam Report

Source scope: `corrected/lecture5_corrected.md`, `study_outputs/lecture_notes/lecture_05_notes.md`, and `study_outputs/audits/lecture_05_audit.md` only.

This report extracts exam-relevant material only: explicit exam markers, repeated emphasis, instructor warnings, proof-heavy parts, theorem-style statements, notation traps, and conceptual question targets.

## High Probability

### Existence and Uniqueness for \(Ax=b\)

Probability: High

Why: The corrected transcript opens with `[LIKELY EXAM TOPIC]` for existence and uniqueness questions. The instructor repeatedly returns to this as the main reason for introducing vector spaces.

Exam focus:

- Existence asks whether there is at least one \(x\) such that \(Ax=b\).
- Uniqueness asks whether that solution, if it exists, is the only one.
- The lecture emphasizes that these questions will be answered using vector spaces.
- Existence is developed in this lecture through column/range space.
- Uniqueness is previewed through the row/inner-product view, but not fully completed here.

Likely conceptual questions:

- What do existence and uniqueness mean for \(Ax=b\)?
- Which matrix-vector product view supports existence analysis?
- Which view will later support uniqueness analysis?

### Two Views of Matrix-Vector Multiplication

Probability: High

Why: This section has multiple `[EXAM NOTE]` markers. The instructor calls it simple but important and says it is at the heart of the matrix algebra used for existence and uniqueness.

Exam focus:

- Column view:

\[
A=[c_1\ c_2\ \cdots\ c_n],\qquad
Ax=x_1c_1+x_2c_2+\cdots+x_nc_n.
\]

- Row view:

\[
A=
\begin{bmatrix}
r_1^T\\
r_2^T\\
\vdots\\
r_m^T
\end{bmatrix},
\qquad
Ax=
\begin{bmatrix}
r_1^T x\\
r_2^T x\\
\vdots\\
r_m^T x
\end{bmatrix}.
\]

- Right multiplication by \(x\): linear combination of columns, or inner products with rows.
- Left multiplication by \(y^T\): linear combination of rows, or inner products with columns.

Notation traps:

- \(r_i\) is treated as a column vector; the actual row is \(r_i^T\).
- For \(A\in\mathbb{R}^{m\times n}\), rows have length \(n\), columns have length \(m\).
- Row vectors live in the input space with \(x\); column vectors live in the output space with \(b\).

Likely conceptual questions:

- Derive \(Ax\) as a linear combination of columns.
- Derive \(Ax\) as a vector of row inner products.
- Explain why the column view is tied to existence.

### Column Space / Range Space and Existence

Probability: High

Why: The transcript's exam-relevant list explicitly names "Column space and existence of solutions." The instructor also boxes the conclusion conceptually: solvability is determined by whether \(b\) lies in the range.

Exam focus:

\[
\operatorname{Col}(A)=\operatorname{span}\{c_1,\ldots,c_n\}.
\]

Equivalent descriptions:

- \(\operatorname{Col}(A)\) is the span of the columns.
- \(\mathcal{R}(A)=\{Ax:x\in\mathbb{R}^n\}\).
- \(\mathcal{R}(A)\) is the set of all possible outputs.
- \(\mathcal{R}(A)\) is the set of all \(b\)'s for which \(Ax=b\) has at least one solution.

Main criterion:

\[
Ax=b\text{ has at least one solution}
\Longleftrightarrow
b\in\mathcal{R}(A).
\]

Notation traps:

- \(\mathcal{R}(A)\) means range space here, not row space.
- The column space is a subspace of the output space \(\mathbb{R}^m\), not the input space.
- Geometric sketches are only intuition; do not infer rank or dependence from the drawing.

Likely conceptual questions:

- Why does \(b\notin\operatorname{Col}(A)\) imply no solution?
- Why is the column space the image of the map \(x\mapsto Ax\)?
- Given columns of \(A\), decide whether a specific \(b\) is reachable.

### Full Range and Solutions for Every \(b\)

Probability: High

Why: The instructor asks which matrices satisfy \(\mathcal{R}(A)=\mathbb{R}^m\), connects it to full rank, and warns that the correct rank language is full row rank rather than casually saying independent columns.

Exam focus:

\[
\mathcal{R}(A)=\mathbb{R}^m
\]

means every \(b\in\mathbb{R}^m\) has at least one solution to \(Ax=b\).

Important limitations:

- This guarantees existence for every \(b\).
- It does not guarantee uniqueness.
- A necessary condition is

\[
n\ge m.
\]

- Tall matrices with \(m>n\) cannot span all of \(\mathbb{R}^m\), so they cannot guarantee solvability for arbitrary \(b\).
- The condition \(n\ge m\) is necessary but not sufficient.

Instructor warning:

- Although full range is stated using the column/range space, the lecture flags that the rank condition will be tied to independence of rows, namely full row rank.
- Do not answer this point by reflexively saying "independent columns" unless the dimensions and rank condition actually support it.

Likely conceptual questions:

- Why can ten vectors not span \(\mathbb{R}^{100}\)?
- Why does \(\mathcal{R}(A)=\mathbb{R}^m\) imply solvability for every \(b\)?
- Why is \(n\ge m\) only necessary, not sufficient?

### Right Inverse and Full Range

Probability: High

Why: The corrected transcript marks right inverse as `[LIKELY EXAM TOPIC]`, and the section is theorem/proof-heavy. The audit specifically notes that the transpose-dimension shape was important enough to patch into the notes.

Exam focus:

For \(A\in\mathbb{R}^{m\times n}\),

\[
\mathcal{R}(A)=\mathbb{R}^m
\Longleftrightarrow
\exists D\in\mathbb{R}^{n\times m}\text{ such that }AD=I_m.
\]

The matrix \(D\) is a right inverse of \(A\).

Proof-heavy direction: full range implies right inverse.

1. Assume \(\mathcal{R}(A)=\mathbb{R}^m\).
2. For each standard basis vector \(e_i\in\mathbb{R}^m\), solve \(Ad_i=e_i\).
3. Assemble \(D=[d_1\ d_2\ \cdots\ d_m]\).
4. Then

\[
AD=[Ad_1\ Ad_2\ \cdots\ Ad_m]=[e_1\ e_2\ \cdots\ e_m]=I_m.
\]

Proof-heavy converse: right inverse implies full range.

If \(AD=I_m\), then for any \(b\in\mathbb{R}^m\), choose \(x=Db\). Then

\[
Ax=A(Db)=(AD)b=I_m b=b.
\]

So every \(b\) is reachable.

Notation traps:

- Right inverse means \(AD=I_m\), not necessarily \(DA=I_n\).
- \(D\) has transpose dimensions: if \(A\) is \(m\times n\), then \(D\) is \(n\times m\).
- For a fat full-range matrix, right inverses can be non-unique.
- For a square matrix, a right inverse will later become the usual unique inverse.
- The usual unique inverse concept is a square-matrix concept.

Likely conceptual questions:

- Construct a right inverse from solutions to \(Ax=e_i\).
- Prove that \(AD=I_m\) implies every \(b\) has a solution.
- Explain why \(AD=I_m\) is not the same statement as \(DA=I_n\).

### Span, Linear Independence, and Basis

Probability: High

Why: These definitions are repeatedly used to build the column-space and right-inverse results. The lecture gives both intuitive and algebraic definitions, plus a proof idea linking nontrivial zero combinations to redundancy.

Exam focus:

- Span is the set of all linear combinations of a given set.
- Span is also the smallest vector space containing that set.
- A set is linearly independent if no element can be written as a linear combination of the others.
- Algebraically,

\[
\alpha_1v_1+\cdots+\alpha_kv_k=0
\Longleftrightarrow
\alpha_1=\cdots=\alpha_k=0.
\]

- A basis of \(V\) is a set \(B\) such that:

\[
\operatorname{span}(B)=V
\]

and \(B\) is linearly independent.

Proof-heavy trap:

- If a nonzero coefficient combination equals zero, move one nonzero term to the other side to express one vector as a linear combination of the others.
- Example:

\[
2p_1+p_2=0\quad\Rightarrow\quad p_2=-2p_1.
\]

This proves redundancy and failure of linear independence.

Likely conceptual questions:

- Explain why a basis is a spanning set with no redundancy.
- Test whether a set is linearly independent using the zero-combination definition.
- Explain why a redundant vector can be removed without changing the span.

## Medium Probability

### Vector Spaces, Subspaces, and Closure

Probability: Medium

Why: These are explicit `[EXAM NOTE]` review items and are necessary for understanding span and column space, but the lecture's main exam direction is \(Ax=b\).

Exam focus:

- A vector space consists of a vector set, scalar set, vector addition, and scalar multiplication.
- The key property emphasized here is closure under linear combinations.
- A subspace is a subset that is itself a vector space.
- Lines and planes through the origin are subspaces; shifted lines or planes are not.
- The zero vector must be included in any subspace.

Likely conceptual questions:

- Why does closure under linear combinations matter for span?
- Decide whether a given subset is a subspace.
- Explain why missing the zero vector immediately prevents a subset from being a subspace.

### Matrix Subspace Examples

Probability: Medium

Why: The transcript explicitly marks square-matrix subspaces as `[EXAM NOTE]`, and these are natural short proof/counterexample questions.

Exam focus:

- Symmetric matrices form a subspace.
- Zero-trace matrices form a subspace because trace is linear:

\[
\operatorname{tr}(\alpha X+\beta Y)
=\alpha\operatorname{tr}(X)+\beta\operatorname{tr}(Y).
\]

- Matrices satisfying \(\operatorname{tr}(A^T X)=0\) are interpreted as matrices orthogonal to \(A\) under the matrix inner product.
- Real orthogonal matrices satisfying \(XX^T=I\) or \(X^TX=I\) are not a subspace because the zero matrix is not included.

Likely conceptual questions:

- Prove symmetric matrices are closed under linear combinations.
- Prove trace-zero matrices are closed under linear combinations.
- Give a quick reason orthogonal matrices are not a subspace.

### Dictionary Versus Basis and Sparsity

Probability: Medium

Why: The instructor spends noticeable time on it and uses it to motivate redundancy and non-unique coordinates. It is less central than the \(Ax=b\) range-space results, but it is conceptually testable.

Exam focus:

- A basis spans with no redundancy.
- A dictionary may span but can include redundant vectors.
- Redundancy means coefficient representations are not unique.
- Non-uniqueness can be useful because one may choose sparse coefficients.
- In high-dimensional settings, a 100-dimensional space might be represented using a 150-vector dictionary to encourage sparse representations.

Likely conceptual questions:

- Why is \(\{p_1,p_2,p_3\}\) not a basis for a plane if one vector is a linear combination of the others?
- Why can dictionaries produce non-unique coefficients?
- Why can redundancy help sparsity?

### Coordinates, Standard Basis, and Basis Dependence

Probability: Medium

Why: Coordinates relative to a basis are needed for the basis-change and Fourier discussion, and standard basis vectors are used again in the right-inverse proof.

Exam focus:

- Standard basis vectors \(e_i\) have one entry equal to 1 and all others 0.
- Coordinates are coefficients relative to a chosen basis.
- The same vector can have different coordinate representations in different bases.
- Standard coordinates are coordinates relative to the standard basis.

Notation trap:

- In signal-processing language, standard basis vectors correspond to discrete impulses.
- The instructor corrected the language to Kronecker delta, not Dirac delta, for the finite discrete setting.

Likely conceptual questions:

- Explain why coordinates depend on the chosen basis.
- Identify standard basis vectors in \(\mathbb{C}^n\) or \(\mathbb{R}^n\).
- Explain why the standard basis appears in the right-inverse proof.

### Complex Exponential Basis, LTI Systems, and Fourier Transform

Probability: Medium

Why: The instructor explicitly says this will be studied in homework and marks the easy-output property as important. It is likely to appear as a conceptual or homework-linked exam question, but the lecture's main theorem work is on range space and right inverses.

Exam focus:

Complex exponential vectors in \(\mathbb{C}^n\) have entries

\[
(f_k)_i=e^{j2\pi(k-1)(i-1)/n}.
\]

Key points:

- For different \(k\), these vectors are independent and span \(\mathbb{C}^n\).
- Therefore, they form a basis.
- Their real and imaginary parts are sampled cosines and sines.
- \(k\) controls frequency.
- Complex exponentials are eigenvectors of linear time-invariant systems.
- For an LTI system, input \(f_k\) gives output \(H_k f_k\).
- Fourier transform is a basis change from standard/time coordinates to complex-exponential/frequency coordinates.

Notation traps:

- Linear algebra indexing starts at 1, but time indexing often starts at 0.
- The formula uses \(i-1\) so the first entry corresponds to sample index 0.
- Do not try to draw \(e^{j\theta}\) as a real scalar curve; draw real and imaginary parts.

Likely conceptual questions:

- Why are complex exponentials useful for LTI systems?
- Explain Fourier transform as a basis change.
- Identify the indexing reason for \((i-1)\) in \((f_k)_i\).

## Low Probability

### Detailed Sparse Dictionary Design

Probability: Low

Why: The instructor says the dictionary idea will be discussed later and only gives the 100-dimensional/150-vector example as flavor.

Exam focus:

- Know the principle: redundancy creates non-unique representations, and non-uniqueness can be constrained toward sparsity.
- Do not over-invest in detailed sparse optimization mechanics from this lecture alone.

Likely conceptual question:

- Briefly explain why an overcomplete dictionary can allow sparse representations.

### Fine Details of Left Multiplication

Probability: Low

Why: The instructor discusses \(y^TA\), gets tangled in notation, and then returns to the main summary. The high-value part is the final dual interpretation, not the intermediate confusion.

Exam focus:

- If \(A\in\mathbb{R}^{m\times n}\), then \(y\in\mathbb{R}^m\) for \(y^TA\).
- \(y^TA\) is a linear combination of rows.
- It can also be viewed as inner products of \(y\) with columns.

Likely conceptual question:

- State the dual interpretation of left multiplication compared with right multiplication.

## Highest-Risk Traps to Memorize

- \(\mathcal{R}(A)\) means range/column space here, not row space.
- \(m\) is output dimension and number of rows; \(n\) is input dimension and number of columns.
- Rows live with \(x\) in \(\mathbb{R}^n\); columns live with \(b\) in \(\mathbb{R}^m\).
- \(b\in\mathcal{R}(A)\) gives existence, not uniqueness.
- \(\mathcal{R}(A)=\mathbb{R}^m\) gives a solution for every \(b\), not necessarily a unique solution.
- \(n\ge m\) is necessary for full range, not sufficient.
- Full range is flagged as tied to full row rank, not merely "independent columns."
- A right inverse satisfies \(AD=I_m\), not necessarily \(DA=I_n\).
- Orthogonal matrices are not a subspace because the zero matrix is absent.
- In the complex exponential basis formula, \(i-1\) handles the mismatch between 1-based vector indexing and 0-based time indexing.

No other lecture was processed.
