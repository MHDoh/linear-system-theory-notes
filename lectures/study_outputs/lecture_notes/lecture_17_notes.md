# Lecture 17 Notes

## Opening: Where We Are in the Factorization Story

The instructor reminds the class that the current theme is **matrix factorization**, the major tool for solving systems of linear equations by writing a matrix as a product of simple matrices. So far the course has covered:

- **PLU** (permutation × lower triangular × upper triangular),
- **Eigenvalue decomposition**,
- **Schur factorization**,
- **Cholesky factorization**, and
- the general **square-root factorization** for positive definite matrices.

Now the focus is **QR factorization**: writing a matrix as a product of a matrix with **orthonormal columns** (\(Q\)) and an **upper triangular** matrix (\(R\)):
\[
A = QR.
\]
The instructor again jokes about the naming — he doesn't know whether "QR" comes from someone's initials — and notes that since \(Q\) is unitary and \(R\) is upper triangular, "UT factorization" would be a more descriptive name.

### Reduced vs. Full QR

- **Reduced (economical) QR:** \(\hat Q\) has the **same size** as \(A\) (an \(m\times n\) matrix with orthonormal columns) and \(\hat R\) is an \(n\times n\) **square** upper triangular matrix.
- **Full QR:** add extra columns to \(\hat Q\) to make it a genuine **unitary** \(m\times m\) matrix \(Q\). Then \(R\) becomes \(m\times n\) — a **rectangular** upper triangular matrix whose entries below the main diagonal are zero (the bottom rows are all zero). The added columns of \(Q\) are "silenced" by the zero rows of \(R\).

**Why QR matters:** it is numerically stable for solving least squares because it operates on \(A\) directly without forming \(A^*A\) (which would square the condition number). MATLAB's backslash uses QR/SVD-based methods.

---

## Review: Gram-Schmidt Process

The instructor recaps the Gram-Schmidt construction from the previous lecture.

### Problem Statement

View the columns \(a_1,\ldots,a_n\) of \(A\) as spanning some vector space. Gram-Schmidt finds an **orthonormal basis** \(q_1,\ldots,q_n\) for that space — but with a **causal constraint**:
\[
\text{span}\{q_1,\ldots,q_k\} = \text{span}\{a_1,\ldots,a_k\}, \qquad k = 1,\ldots,n.
\]
This "causality" (each \(q_k\) is built only from \(a_1,\ldots,a_k\)) is exactly what produces the **upper triangular** \(R\): "all the theory is reflected in the triangular structure."

### Step-by-Step

**Step 1.** \(q_1 = a_1/\|a_1\|\) — just normalize the first column; the span constraint is trivial.

**Step 2.** Find the component of \(a_2\) orthogonal to \(q_1\) by orthogonal projection:
\[
\tilde a_2 = a_2 - (q_1^* a_2)\,q_1, \qquad q_2 = \frac{\tilde a_2}{\|\tilde a_2\|}.
\]
The subtracted term is the projection of \(a_2\) onto \(q_1\); the leftover error vector is orthogonal to \(q_1\) (because it is an orthogonal projection), and we normalize it.

**Step 3.** Find the component of \(a_3\) orthogonal to **both** previous directions:
\[
\tilde a_3 = a_3 - (q_1^*a_3)q_1 - (q_2^*a_3)q_2, \qquad q_3 = \frac{\tilde a_3}{\|\tilde a_3\|}.
\]
Because \(a_1,a_2\) span the same space as \(q_1,q_2\), removing the \(q_1,q_2\) components is the same as removing the \(a_1,a_2\) components.

**General step \(k\):**
\[
\tilde a_k = a_k - \sum_{i=1}^{k-1}(q_i^* a_k)\,q_i, \qquad q_k = \frac{\tilde a_k}{\|\tilde a_k\|}.
\]

**Cross-product analogy.** The instructor recalls the 3-D picture: given two vectors, the cross product gives a vector orthogonal to the plane they span. Gram-Schmidt does the analogous thing in **high dimensions** — find the component of a new vector orthogonal to the span of the previous ones. The cross product is the special low-dimensional case.

### Why \(R\) Is Upper Triangular

Inverting the construction, each \(a_k\) is a combination of only the first \(k\) orthonormal vectors:
\[
a_k = \sum_{i=1}^{k}(q_i^*a_k)\,q_i.
\]
Defining \(R_{ik} = q_i^* a_k\) for \(i\le k\) and \(R_{ik}=0\) for \(i>k\) gives \(A = QR\) with \(R\) upper triangular. The diagonal entries \(R_{kk} = \|\tilde a_k\|\) (the norms before normalization) are positive when the columns are linearly independent.

### Linear Dependence Case

If at step \(k\) the vector \(a_k\) lies in the span of \(a_1,\ldots,a_{k-1}\), it carries **no new dimension / no new information** (the instructor adds: "not in the Shannon sense," but a genuine linear relationship). After subtracting projections, \(\tilde a_k = 0\). The number of \(q\)-vectors produced is then \(k' = \text{rank}(A) < n\). To complete a **full** unitary QR, add \(m - k'\) extra orthonormal columns to \(Q\) (orthogonal to all the constructed \(q\)'s) and append corresponding **zero rows** to \(R\) to silence them. The instructor recalls having worked an explicit example of this in the previous lecture and does not repeat it.

---

## Modified Gram-Schmidt (Triangular Orthogonalization)

The next step is the **Modified Gram-Schmidt (MGS)** procedure — "a variation on Gram-Schmidt." The mathematical result is identical in exact arithmetic, but the **order of operations** differs, which matters numerically.

### The Key Difference

**Classical Gram-Schmidt:** to find \(q_k\), project the *original* \(a_k\) onto each previous \(q_i\) and subtract all at once.

**Modified Gram-Schmidt:** as soon as \(q_1\) is generated, **immediately subtract its component from ALL remaining vectors**, so that every other vector becomes orthogonal to \(q_1\) right away:
\[
q_1 = \frac{a_1}{\|a_1\|}, \qquad a_j^{(1)} = a_j - (q_1^* a_j)\,q_1 \quad \text{for all } j = 2,\ldots,n.
\]
After this first pass, all vectors are orthogonal to \(q_1\) (but not yet to each other). Then take \(q_2 = a_2^{(1)}/\|a_2^{(1)}\|\) (already orthogonal to \(q_1\)), and subtract the \(q_2\)-component from all remaining **updated** vectors:
\[
a_j^{(2)} = a_j^{(1)} - (q_2^* a_j^{(1)})\,q_2 \quad \text{for all } j = 3,\ldots,n,
\]
and continue. In words: **once you generate an orthonormal basis element, you kill the component of all remaining vectors in that direction immediately**, then move on. You progressively build the orthonormal basis.

### Matrix Interpretation

Each MGS pass is a **right-multiplication of \(A\) by an upper triangular matrix**. For example, the first pass multiplies \(A\) by an upper triangular \(R_1\) whose first column is \([1/\|a_1\|,\,0,\ldots]^\top\) (normalizing column 1) and whose later columns encode "subtract the \(q_1\)-projection." For three columns, the instructor's board calculation is:
\[
[a_1\ a_2\ a_3]
\begin{bmatrix}
1/\|a_1\| & -\dfrac{a_1^*a_2}{a_1^*a_1} & -\dfrac{a_1^*a_3}{a_1^*a_1} \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}
=
[q_1\ a_2^{(1)}\ a_3^{(1)}],
\]
where \(a_j^{(1)}\) means "the \(q_1\)-component has been removed." The second and third columns keep their original vector with coefficient \(1\), then subtract a multiple of \(a_1\); entries below the diagonal are zero because earlier columns are the only ones used.

The second pass leaves \(q_1\) untouched, normalizes \(a_2^{(1)}\), and removes only the \(q_2\)-direction from the remaining updated columns:
\[
[q_1\ a_2^{(1)}\ a_3^{(1)}]
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1/\|a_2^{(1)}\| & -\dfrac{(a_2^{(1)})^*a_3^{(1)}}{(a_2^{(1)})^*a_2^{(1)}} \\
0 & 0 & 1
\end{bmatrix}
=
[q_1\ q_2\ a_3^{(2)}].
\]
The instructor stresses that there is "no business with \(q_1\)" in this later projection: the \(q_1\)-component was already eliminated. After this pass, \(a_3^{(2)}\) is orthogonal to the span of the first two directions but is not yet unit norm; the next pass normalizes it and removes its direction from any remaining columns.

Because each step only touches components of vectors at or before the current index, the multiplying matrix is upper triangular. Successive passes give
\[
A R_1 R_2 \cdots = \hat Q \quad\Longrightarrow\quad A = \hat Q\, (\cdots R_2^{-1} R_1^{-1}) = \hat Q \hat R,
\]
and since inverses and products of upper triangular matrices are upper triangular, \(\hat R\) is upper triangular.

**The instructor's name for this:** **triangular orthogonalization** — *use triangular matrices to convert a given matrix into orthogonal form.* The matrix \(A\) is multiplied from the right by triangular matrices until its columns are orthonormal.

### Why MGS Is Numerically Better

In floating point, classical Gram-Schmidt reuses the original \(a_k\) and accumulates rounding errors. MGS always subtracts from an **already partially orthogonalized** vector \(a_j^{(i)}\) (with \(q_1,\ldots,q_i\) components already removed), so each subtraction acts on a "cleaner" vector and rounding errors do not compound as badly.

---

## Householder Reflections (Orthogonal Triangularization)

The instructor introduces the **dual** of triangular orthogonalization:

- **MGS / triangular orthogonalization:** multiply \(A\) from the **right** by upper triangular matrices to obtain an orthogonal matrix.
- **Householder / orthogonal triangularization:** multiply \(A\) from the **left** by **unitary** matrices to obtain an upper triangular matrix.

He draws the analogy to LU: in Gaussian elimination (LU) we multiply \(A\) from the left by **lower triangular** matrices to make it upper triangular. Here we instead multiply from the left by **unitary** matrices to make it upper triangular. So LU and QR are "similar" in that both have an upper triangular right factor; QR's other factor is unitary instead of lower triangular.

### Goal of Each Step

Triangularize column by column, zeroing entries **below the diagonal**. Step 1: find a unitary \(Q_1'\) that maps the first column \(a_1\) to a multiple of \(e_1\):
\[
Q_1' a_1 = r_{11}\, e_1 = \begin{bmatrix} r_{11} \\ 0 \\ \vdots \\ 0 \end{bmatrix}.
\]
Since \(Q_1'\) is unitary, it **preserves the Euclidean norm**, so
\[
|r_{11}| = \|a_1\|_2.
\]
We know the **target vector** exactly: \(\|a_1\|\, e_1\) (or \(-\|a_1\|\,e_1\) — either sign is allowed, "it's up to me, nothing harmful").

### Rotation vs. Reflection

Geometrically (2-D toy picture) we want to move \(a_1\) onto the first coordinate axis while preserving its length. Two kinds of length-preserving maps do this:
- a **rotation** (Givens rotation), which involves cosines and sines, or
- a **reflection** across a hyperplane (the **Householder** form).

The instructor chooses the **reflection** because it is **simpler** (the rotation/Givens approach with cosines and sines is "left to homework or exam"). He defines a hyperplane and reflects \(a_1\) onto the target \(r_{11}e_1\); this is the **Householder form**.

### Constructing the Reflection

Define the **direction vector** (the difference between \(a_1\) and its target):
\[
z = a_1 - r_{11}\,e_1, \qquad r_{11} = \|a_1\|_2,
\]
which is the **normal of the reflection hyperplane**. The geometric reasoning the instructor walks through:

1. Project \(a_1\) onto \(z\): the projection coefficient is \(\dfrac{z^* a_1}{z^* z}\).
2. Subtracting **once** lands you on the hyperplane (the foot of the projection).
3. To reach the **reflection** (the mirror image), you must move **twice** as far in the \(-z\) direction.

A student questioned the "twice" step; the instructor clarified there is an implicit factor of \(z\): the scalar \(\frac{z^*a_1}{z^*z}\) is just the **reflection coefficient**, which then multiplies the vector \(z\). ("I'm more excited about the reflection coefficient than the reflection itself.") Carrying this out:
\[
Q_1' a_1 = a_1 - 2\,\frac{z\, z^* a_1}{z^* z} = \Big(I - 2\,\frac{z z^*}{z^* z}\Big) a_1.
\]
So the **Householder reflection matrix** is
\[
\boxed{\,H = I - 2\,\frac{z z^*}{z^* z}\,}, \qquad z = a_1 - \|a_1\|\,e_1.
\]

**Properties:**
- **Hermitian:** \(H^* = H\).
- **Unitary:** \(H^* H = I\) — reflecting twice returns the identity.
- Maps \(a_1\) onto \(\|a_1\|\, e_1\) (by construction).

### Applying Householder Iteratively (Shrinking Columns)

After step 1, \(Q_1' A\) has first column \(r_{11}e_1\): entries below the diagonal in column 1 are zero, and the rest is
\[
Q_1' A = \begin{bmatrix} r_{11} & * & \cdots \\ 0 & & \\ \vdots & & \tilde A \\ 0 & & \end{bmatrix}.
\]
Now focus on the second column **within the \((m-1)\)-dimensional subspace** (ignoring the already-finished first row/column). Build an \((m-1)\times(m-1)\) Householder reflection \(Q_2''\) that sends that shorter vector to its own \(\|\cdot\|\,e_1\), and embed it as a **block-diagonal** unitary
\[
Q_2' = \begin{bmatrix} 1 & 0 \\ 0 & Q_2'' \end{bmatrix},
\]
(identity in the top-left, Householder in the bottom-right). This is unitary and zeros the entries below the diagonal in column 2 without disturbing column 1. Continue for columns \(3, 4, \ldots\), each time working in a one-dimension-smaller space:
\[
Q_k' \cdots Q_2' Q_1' A = R.
\]
Since each \(Q_i'\) is unitary, its inverse is its conjugate transpose (very simple), so
\[
A = (Q_1')^* (Q_2')^* \cdots (Q_k')^* R = QR,
\]
with \(Q = (Q_1')^*\cdots(Q_k')^*\) unitary. (The instructor notes the sign choice for \(r_{11}\) corresponds to two possible reflection hyperplanes; in practice the sign is chosen to keep \(z\) large and avoid numerical cancellation.)

---

## Gram Matrix (Student Question)

A student asks about the **Gram matrix**. Given a set of vectors \(p_1,\ldots,p_n\), the Gram matrix collects **all pairwise inner products**:
\[
G_{ij} = \langle p_i, p_j\rangle = p_i^* p_j.
\]
Putting the vectors as columns of \(P = [p_1\ \cdots\ p_n]\),
\[
G = P^* P.
\]
**Properties:**
- **Hermitian:** \(G^* = P^*P = G\).
- **Positive semidefinite:** \(x^* G x = \|Px\|^2 \ge 0\).
- **Positive definite** iff the vectors are linearly independent (iff \(P\) has full column rank).

**Connection to least squares / projection.** The instructor reminds students that the projection onto the range of a general (non-orthonormal) \(A\) used the inverse \((A^*A)^{-1}\) — and \(A^*A\) is exactly the **Gram matrix** of the columns of \(A\). This will reappear in the least squares normal equations.

---

## Recap of the Two Dual Procedures

- **Triangular orthogonalization** (Gram-Schmidt / MGS): right-multiply \(A\) by triangular matrices to orthogonalize it.
- **Orthogonal triangularization** (Householder): left-multiply \(A\) by unitary matrices to triangularize it.

Both yield the same \(A = QR\). All of this still revolves around the very first lecture's question: *what are the simple matrices?* (diagonal, triangular, orthogonal) — and the goal of writing \(A\) in terms of them. "But the story is not over."

| Property | Classical GS | Modified GS | Householder |
|---|---|---|---|
| Mechanism | right × triangular | right × triangular (reordered) | left × unitary |
| Produces directly | orthonormal columns \(Q\) | orthonormal columns \(Q\) | upper triangular \(R\) |
| Conceptual name | — | triangular orthogonalization | orthogonal triangularization |
| Numerical stability | least stable | better | most stable |

---

## Preview: Polar Decomposition

The instructor previews an upcoming factorization (to be developed with the SVD): the **polar decomposition**, motivated by the **polar form of a complex number**.

A nonzero complex number \(c\) can be written
\[
c = r\, e^{j\theta},
\]
where \(r = |c| > 0\) is the magnitude (distance to the origin) and \(e^{j\theta}\) is a unit-magnitude complex number on the unit circle (with \(\cos\theta, \sin\theta\) the real and imaginary parts). The matrix generalization: any **non-singular** \(n\times n\) matrix \(A\) can be written
\[
A = P\,T,
\]
where \(P\) is a **positive definite** matrix (the analog of the positive magnitude \(r\)) and \(T\) is a **unitary** matrix (the analog of \(e^{j\theta}\) on the unit circle). This is the **polar decomposition**.

The instructor notes \(P\,T\) is not quite a "simple-matrix" factorization, but since a positive definite matrix is itself normal (= unitary × diagonal × unitary), the polar decomposition connects to the SVD. It has applications such as **finding the closest unitary matrix** to a given matrix. (A brief exchange about left/right inverses: since \(A\) here is square and invertible, its inverse is unique — the left-inverse notion was for tall full-rank matrices, not relevant for this invertible square case.)

---

## Beginning of Block LDU Factorization (Carried into L18)

With time remaining, the instructor begins the next topic, warning it is **"a bit algebraically involved but very useful"** — it underlies major algorithms in **adaptive filtering, optimization, and control**. The topic is **block LDU factorization**: lower–diagonal–upper triangular factorization, but in terms of **block** submatrices.

### Block Partition

Partition a non-singular square matrix \(A\) of size \((m+n)\times(m+n)\) into blocks:
\[
A = \begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix},
\]
where \(A_{11}\) is \(m\times m\), \(A_{12}\) is \(m\times n\), \(A_{21}\) is \(n\times m\), and \(A_{22}\) is \(n\times n\). The full \(A\), \(A_{11}\), and \(A_{22}\) are assumed non-singular. The goal: perform **Gaussian elimination at the block level**.

### Block Elimination

To convert \(A\) into **block upper triangular** form, eliminate the \(A_{21}\) block by left-multiplying by a **block lower triangular** matrix:
\[
\begin{bmatrix} I & 0 \\ -A_{21}A_{11}^{-1} & I \end{bmatrix}
\begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix}
=
\begin{bmatrix} A_{11} & A_{12} \\ 0 & A_{22} - A_{21}A_{11}^{-1}A_{12} \end{bmatrix}.
\]
The first block row is preserved (multiplied by identity). The \((2,1)\) block becomes \(-A_{21}A_{11}^{-1}A_{11} + A_{21} = 0\), and the \((2,2)\) block becomes
\[
A_{22} - A_{21}A_{11}^{-1}A_{12},
\]
the **Schur complement** (of \(A_{11}\)). The instructor gives a memory aid for reconstructing the formula: start at index **2-2**, then go **2-1**, then invert **1-1**, then **1-2** — i.e., \(A_{22} - A_{21}A_{11}^{-1}A_{12}\).

The next step (eliminating \(A_{12}\) by right-multiplying with a block upper triangular matrix to reach block **diagonal** form) is deferred to the next lecture. "Please look at this so that we can pick up from here."

---

## Instructor Remarks and Study Guidance

- The **causal/span constraint** \(\text{span}\{q_1,\ldots,q_k\}=\text{span}\{a_1,\ldots,a_k\}\) is exactly what forces \(R\) to be upper triangular — the central structural fact of QR.
- **MGS vs. classical GS:** identical in exact arithmetic; MGS subtracts each new \(q\)-component from *all* remaining vectors immediately, which is more stable. The matrix view is **triangular orthogonalization** (right-multiply by triangular matrices).
- **Householder is the dual** (orthogonal triangularization, left-multiply by unitaries). The reflector \(H = I - 2zz^*/z^*z\) with \(z = a_1 - \|a_1\|e_1\) is Hermitian and unitary, and reflects \(a_1\) onto \(\|a_1\|e_1\). It is the most numerically stable QR method. The **Givens rotation** (cosine/sine) is the alternative, left to homework.
- The reflection requires moving **twice** the projection distance along \(z\) — that factor of 2 is the source of the \(2\) in \(H\).
- The **Gram matrix** \(G = P^*P\) is Hermitian PSD (PD iff columns independent) and is exactly the \(A^*A\) that appears in least squares / projection.
- **Polar decomposition** \(A = PT\) (PD × unitary) is the matrix analog of \(c = re^{j\theta}\); developed alongside the SVD.
- **Block LDU** begins here and continues in L18; the \((2,2)\) block after block elimination is the **Schur complement** \(A_{22} - A_{21}A_{11}^{-1}A_{12}\).

## Source and Coverage Note

Source: `corrected/lecture17_corrected.md`.

Coverage: QR overview (reduced and full, naming aside, why QR matters); Gram-Schmidt review (causal/span constraint, step-by-step, cross-product analogy, upper triangular R, diagonal entries, linear-dependence case and completion to full unitary QR); Modified Gram-Schmidt (immediate elimination of each new direction from all remaining vectors, explicit first- and second-pass right-multiplication matrices, matrix interpretation as triangular orthogonalization via upper triangular matrices, numerical-stability reasoning); Householder reflections (dual orthogonal triangularization, left-multiplication by unitaries, LU analogy, norm preservation and target vector, rotation vs. reflection choice, full geometric derivation of the reflection coefficient and the factor of 2, the reflector \(H=I-2zz^*/z^*z\), Hermitian and unitary properties, iterative shrinking-column application via block-diagonal embedding, sign choice); Gram matrix (definition, \(P^*P\), Hermitian/PSD/PD, connection to least squares); recap of the two dual procedures and comparison table; polar decomposition preview (complex-number analogy, \(A=PT\), closest-unitary application, left/right-inverse aside); beginning of block LDU factorization (block partition with block sizes, block lower triangular elimination, Schur complement and its memory aid, deferral of the right-elimination step to L18).
