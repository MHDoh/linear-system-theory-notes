# Lecture 21 Notes

## Recap: Matrix Norms Leading to SVD

The instructor recaps the matrix-norm results from L20:

- One way to define matrix norms is to **vectorize** \(A\) and apply a familiar vector \(p\)-norm. This treats the matrix as a vector in \(\mathbb C^{mn}\), not as a linear map.
- **Frobenius norm** (flatten then 2-norm): \(\|A\|_F = \big(\sum_{i,j}|a_{ij}|^2\big)^{1/2}\) — sums the energies of all entries; does **not** care where the entries sit (no linear-map perspective).
- **Induced norms** treat \(A: \mathbb{C}^n \to \mathbb{C}^m\) as a mapping; \(\|A\|_{q,p} = \sup_{x\ne0}\|Ax\|_q/\|x\|_p = \sup_{\|x\|_p=1}\|Ax\|_q\).
  - \(\|A\|_{1,1}\) = max column \(\ell_1\)-norm.
  - \(\|A\|_{\infty,\infty}\) = max row \(\ell_1\)-norm.
  - \(\|A\|_{2,2} = \sqrt{\lambda_{\max}(A^*A)}\) = length of the **longest principal semi-axis** of the ellipsoid that is the image of the unit \(\ell_2\)-ball.

That last picture — **unit sphere maps to an ellipsoid** — is the geometric center of the **Singular Value Decomposition (SVD)**. This lecture presents the SVD from an **algebraic** view and a **geometric** view, then gives a **formal existence proof**.

---

## SVD: The Algebraic View

The SVD states that **any** matrix \(A\) (rectangular allowed) can be written
\[
A = U\Sigma V^*,
\]
where:
- \(U\) is \(m\times m\) **unitary** (left singular vectors),
- \(V\) is \(n\times n\) **unitary** (right singular vectors),
- \(\Sigma\) is \(m\times n\) **rectangular diagonal** (the \((i,i)\) entries may be nonzero, all others zero), with **real, non-negative** diagonal entries \(\sigma_1 \ge \sigma_2 \ge \cdots \ge 0\).

The relative sizes follow the shape of \(A\): if \(A\) is **fat**, \(V\) is the larger unitary; if \(A\) is **tall**, \(U\) is larger. This fits the course storyline of writing \(A\) as a product of **simple matrices** — here **two unitaries and one (real, nonneg) diagonal**.

**On the conjugate transpose \(V^*\).** It is a convention to write the third factor as \(V^*\) rather than \(V\): multiplying by \(V^*\) means taking inner products with the right singular vectors. (Geometrically \(V\) might read more naturally, but the \(U\Sigma V^*\) convention is standard.)

### Connection to (and Departure from) Similarity

Recall the **similarity** story for a **square** \(A:\mathbb{C}^n\to\mathbb{C}^n\): pick **one** basis \(T\) for **both** input and output; the map's new representation is \(T^{-1}AT\); we asked whether we can choose \(T\) to make this **diagonal**. Answer: **not for all** matrices (only diagonalizable ones). The restriction was using the **same basis** for input and output.

**The key step to SVD: drop that restriction.** Use a basis \(T_1\) for the input and a **different** basis \(T_2\) for the output; the representation becomes \(T_2^{-1}AT_1\). Question: can we always find \(T_1, T_2\) making this **diagonal**, even for **rectangular** \(A\) (where input and output dimensions differ, so the **same** basis is impossible)? **Answer: yes — always — using orthonormal bases.** That is exactly the SVD: choosing one orthonormal basis for the input (\(V\)) and one for the output (\(U\)) renders **any** linear map diagonal, with real nonneg diagonal entries. "I can represent any linear mapping by a diagonal matrix if I choose my coordinate axes wisely — one set for the input, one for the output."

---

## SVD: The Geometric View

### Image of a Sphere Is an Ellipsoid

Two facts about linear maps:
1. The image of a **line segment** is a line segment (shown earlier for the \(\ell_1\)-ball).
2. The image of an **ellipsoid** (in particular the unit sphere) under a linear map is an **ellipsoid** — shape preserved.

A **line segment is a degenerate ellipsoid** (one semi-axis has length zero). So degenerate cases fit the same picture:
- A **rank-1** \(2\times2\) map sends the circle to a line segment (an ellipse with second semi-axis \(=0\)).
- A map from 3-D to 2-D sends a sphere to an ellipse in the plane; if the matrix is not full rank, that ellipse can collapse to a line segment.
- A **tall** \(3\times2\) map (rank \(\le 2\)) sends a 2-D circle to an ellipse lying in a plane through the origin (the range space). If the rank is only \(1\), the image is again a line segment.

The instructor notes that this geometric discussion is based on the hand-drawn/pre-lecture figure: a sphere/circle maps to an ellipsoid/ellipse, with degenerate cases handled by allowing zero semi-axis lengths.

### Student Q&A: What Is an Ellipsoid?

A student asks for the definition. An ellipsoid is the **level set of a quadratic function**:
\[
\{x : (x - x_0)^* A (x - x_0) \le b\},
\]
with \(A\) **positive definite**. (A positive **semi**definite \(A\) gives a **degenerate** ellipsoid — some dimensions collapse.) Geometrically you "cut" the quadratic at a level and look at the region in the domain.

### Assigning Singular Values and Vectors

Accept (formal proof later) that the image of the unit sphere is an ellipsoid. Label its components:
- The **first (longest) principal semi-axis** has length \(\sigma_1\) along the unit vector \(u_1\): the axis is \(\sigma_1 u_1\). Its **pre-image** on the input sphere is the unit vector \(v_1\). So \(Av_1 = \sigma_1 u_1\).
- The **second** semi-axis is \(\sigma_2 u_2\), with pre-image \(v_2\): \(Av_2 = \sigma_2 u_2\).
- For a rank-\(r\) matrix there are \(r\) nonzero semi-axes \(\sigma_1 \ge \cdots \ge \sigma_r > 0\) with \(Av_k = \sigma_k u_k\), \(k = 1,\ldots,r\).

Student check: why does such a \(v_k\) exist? Because \(\sigma_k u_k\) is chosen as a point on the image of the unit sphere under \(A\); by definition of image, at least one unit input vector maps to that point.

The \(u_k\) (semi-axis directions in the **output** space) are **orthogonal by definition** of principal axes. The pre-images \(v_k\) (in the **input** space) are also **orthonormal** — not obvious, proved formally below.

### Matrix Form (Reduced)

Collecting the pre-images as columns of \(\hat V = [v_1\ \cdots\ v_r]\) (\(n\times r\)) and the axis directions as \(\hat U = [u_1\ \cdots\ u_r]\) (\(m\times r\)):
\[
A\hat V = \hat U \hat\Sigma, \qquad \hat\Sigma = \operatorname{diag}(\sigma_1,\ldots,\sigma_r)\ (r\times r,\ \text{positive diagonal}).
\]
This relation records the nonzero action of \(A\): the \(v_k\)'s generate the principal semi-axes. After the null-space directions are added and the zero actions are accounted for, the zero terms can be removed again to give the **reduced (compact) SVD**
\[
A = \hat U \hat\Sigma \hat V^*.
\]

### Extending to the Full SVD and the Four Fundamental Subspaces

\(\hat V\) and \(\hat U\) have only \(r\) orthonormal columns (orthonormal, but not unitary). Extend:
- Add \(n-r\) orthonormal columns to \(\hat V\) → unitary \(V\). The added columns are arbitrary subject to completing an orthonormal basis, and in this construction they span the null space: \(Av_k = 0\) for \(k>r\) (they are silenced by the zero columns/diagonal positions of \(\Sigma\)).
- Add \(m-r\) orthonormal columns to \(\hat U\) → unitary \(U\). These added columns are also arbitrary subject to completing \(U\) to unitary; they do not contribute to \(A\) because their coefficients in \(\Sigma\) are zero.

The \(r\times r\) positive-diagonal block thus extends to the \(m\times n\) rectangular diagonal \(\Sigma\) (first \(r\) diagonal entries nonzero, rest zero). The geometric construction first gives
\[
AV = U\Sigma.
\]
Multiplying on the right by \(V^*\) gives the **full SVD** \(A = U\Sigma V^*\). The columns immediately give **orthonormal bases for all four fundamental subspaces**:

| Subspace | Basis | SVD columns |
|---|---|---|
| Row space \(\mathcal R(A^*)\) | \(v_1,\ldots,v_r\) | first \(r\) cols of \(V\) (nonzero outputs) |
| Null space \(\mathcal N(A)\) | \(v_{r+1},\ldots,v_n\) | last \(n-r\) cols of \(V\) (\(Av_k = 0\)) |
| Column space \(\mathcal R(A)\) | \(u_1,\ldots,u_r\) | first \(r\) cols of \(U\) |
| Left null space \(\mathcal N(A^*)\) | \(u_{r+1},\ldots,u_m\) | last \(m-r\) cols of \(U\) |

So the SVD hands us the **rank** (number of nonzero \(\sigma_k\)) and orthonormal bases for all four subspaces at once — "an excellent analysis tool."

### Outer-Product (Rank-1 Sum) Form

Expanding \(U\Sigma V^*\):
\[
A = \sum_{k=1}^{r} \sigma_k\, u_k v_k^*.
\]
The multiplication is: \(\hat U\hat\Sigma = [\sigma_1u_1\ \cdots\ \sigma_ru_r]\), while \(\hat V^*\) has rows \(v_1^*,\ldots,v_r^*\); multiplying column-by-row gives the sum of outer products.

Each \(\sigma_k u_k v_k^*\) is **rank one** (column vector × row vector). Summing \(r\) of them gives a rank-\(r\) matrix. Ordered by \(\sigma_1 \ge \sigma_2 \ge \cdots\), the first term is the "most important." This is the form you see in many papers; it is an **orthonormal expansion** of \(A\) in a basis **adapted to \(A\) itself** (derived from \(A\)).

---

## The Matrix Inner Product and Orthogonality of Rank-1 Components

The rank-1 terms \(\sigma_k u_k v_k^*\) are **orthogonal** with respect to the **matrix inner product** — the extension of the Euclidean inner product to matrices:
\[
\langle A, B\rangle = \operatorname{tr}(B^* A).
\]
**Proof of orthogonality.** For \(i \ne j\),
\[
\big\langle u_i v_i^*,\, u_j v_j^*\big\rangle = \operatorname{tr}\big((u_j v_j^*)^* (u_i v_i^*)\big) = \operatorname{tr}\big(v_j u_j^* u_i v_i^*\big).
\]
Because the left singular vectors are orthonormal, \(u_j^* u_i = 0\) for \(i \ne j\), so the whole trace is \(0\). Hence the rank-1 SVD components form an **orthonormal basis** (up to the \(\sigma_k\) scaling) for the subspace they span, in the Frobenius/matrix inner product. (Inner-product spaces for matrices are developed formally in L23.)

---

## Connection to PCA

The SVD is essentially **Principal Component Analysis (PCA)** applied to a **data matrix**. Suppose you observe data vectors \(x_1, \ldots, x_n\) and form the **sample correlation matrix**
\[
R = \frac{1}{n}\sum_{i=1}^{n} x_i x_i^* = \frac{1}{n} X X^*, \qquad X = [x_1\ \cdots\ x_n]\ (\text{data/snapshot matrix}).
\]
**PCA** looks at the **eigenvalue decomposition** of \(R\) and asks which eigenvalues (directions) are most significant. But computing the **SVD of the data matrix \(X\) directly** yields the **same** eigenvectors: the left singular vectors of \(X\) are the eigenvectors of \(R = \frac{1}{n}XX^*\). So **PCA = SVD on the data matrix** (rather than eigendecomposition of the correlation matrix). This is the standard, numerically preferable route.

---

## How Singular Values/Vectors Are Computed (Preview)

The singular values and **left/right singular vectors** come from the **eigenvalue decomposition of \(A^*A\) or \(AA^*\)** (detailed in L22): \(\sigma_k = \sqrt{\lambda_k(A^*A)}\), with \(v_k\) the eigenvectors of \(A^*A\) and \(u_k\) of \(AA^*\). There are efficient algorithms; the main conceptual route is via \(A^*A\).

---

## Formal Proof of the SVD (by Induced 2-Norm and Block Diagonalization)

This is the centerpiece of the lecture: an existence proof modeled on the **Schur decomposition** proof (extend a vector to an orthonormal basis, get a block form, recurse). The recalled Schur result was that every square matrix is unitarily triangularizable; here the same extension idea is used to get block diagonal pieces for SVD.

### Setup

Let \(\sigma_1 = \|A\|_{2,2}\), the induced 2-norm — the **maximum Euclidean gain**, which is the longest principal semi-axis from the geometric picture. By definition of the induced norm, there exist **unit vectors** \(v_1\) (input) and \(u_1\) (output) with
\[
A v_1 = \sigma_1 u_1, \qquad \|v_1\|_2 = \|u_1\|_2 = 1.
\]

### Extend to Orthonormal Bases

As in the Schur proof: extend \(u_1\) to an orthonormal basis \(u_1, u_2', \ldots, u_m'\) of the output space (forming unitary \(U_1\)), and extend \(v_1\) to an orthonormal basis \(v_1, v_2', \ldots, v_n'\) of the input space (forming unitary \(V_1\)). (The primed vectors are **not** the final singular vectors; they merely complete the bases.)

### Form \(S_1 = U_1^* A V_1\)

Compute \(S_1 = U_1^* A V_1\). The first column: \(A v_1 = \sigma_1 u_1\), and
\[
u_1^*(\sigma_1 u_1) = \sigma_1\ (\text{since } u_1^* u_1 = 1), \qquad (u_k')^*(\sigma_1 u_1) = 0\ (\text{orthogonality}).
\]
So the first column of \(S_1\) is \((\sigma_1, 0, \ldots, 0)^\top\). The top row has entries \(w_k^* = u_1^* A v_k'\) (call this row vector \(w^*\)). Thus
\[
S_1 = \begin{bmatrix} \sigma_1 & w^* \\ 0 & B \end{bmatrix},
\]
a **block upper-triangular-looking** form. The claim to prove: **\(w = 0\)**, which makes \(S_1\) block **diagonal** and lets the proof recurse.

### The Key Trick: \(w = 0\) from Unitary Invariance of the 2-Norm

The instructor recalls the relevant unitary-invariance facts: the Euclidean vector 2-norm is unitarily invariant, the Frobenius norm is unitarily invariant for matrices, and the induced 2-2 norm is also unitarily invariant. Since \(S_1 = U_1^* A V_1\) is \(A\) sandwiched by unitaries, \(S_1\) has the **same** 2-norm as \(A\):
\[
\|S_1\|_{2,2} = \|A\|_{2,2} = \sigma_1.
\]
So for **every** unit vector \(x\), \(\|S_1 x\|_2 \le \sigma_1\). Choose the **clever** unit vector built from the first row of \(S_1\):
\[
x = \frac{1}{\sqrt{\sigma_1^2 + \|w\|_2^2}}\begin{bmatrix} \sigma_1 \\ w \end{bmatrix}
\]
(its norm is \(1\) because the denominator is exactly the norm of \([\sigma_1;\,w]\)). Then
\[
S_1 x = \frac{1}{\sqrt{\sigma_1^2 + \|w\|^2}}\begin{bmatrix} \sigma_1^2 + \|w\|^2 \\ Bw \end{bmatrix},
\]
so its squared norm is
\[
\|S_1 x\|_2^2 = \frac{(\sigma_1^2 + \|w\|^2)^2 + \|Bw\|^2}{\sigma_1^2 + \|w\|^2}
= (\sigma_1^2 + \|w\|^2) + \frac{\|Bw\|^2}{\sigma_1^2 + \|w\|^2}.
\]
This must be \(\le \sigma_1^2\). The second term is **non-negative**, so already
\[
\sigma_1^2 + \|w\|^2 \le \|S_1 x\|_2^2 \le \sigma_1^2 \quad\Longrightarrow\quad \|w\|^2 \le 0.
\]
A norm cannot be negative, so \(\|w\|^2 = 0\), i.e. **\(w = 0\)**. Therefore
\[
S_1 = \begin{bmatrix} \sigma_1 & 0 \\ 0 & B \end{bmatrix}
\]
is **block diagonal**.

### Recurse

Now apply the identical argument to the smaller \((m-1)\times(n-1)\) block \(B\): its induced 2-norm is \(\sigma_2\) (\(\le \sigma_1\)), giving a unit \(u_2, v_2\), another orthonormal extension, and another block diagonalization \(\begin{bmatrix}\sigma_2 & 0\\0 & C\end{bmatrix}\). Continuing peels off \(\sigma_1 \ge \sigma_2 \ge \cdots\) down the diagonal, accumulating unitary factors, and **proves the SVD** \(A = U\Sigma V^*\). (The ordering \(\sigma_1 \ge \sigma_2 \ge \cdots\) follows because each step takes the 2-norm of a submatrix of the previous.) This also confirms the geometric claim that the **pre-images \(v_k\) are orthonormal**.

---

## SVD vs. Eigenvalue Decomposition (Summary)

| Property | Eigenvalue Decomposition | SVD |
|---|---|---|
| Form | \(A = T\Lambda T^{-1}\) | \(A = U\Sigma V^*\) |
| Applies to | square only | **any** (rectangular) matrix |
| Bases | **one** basis (same for in/out) | **two** orthonormal bases |
| Side matrices | invertible \(T\) (unitary iff normal) | unitary \(U\), unitary \(V\) |
| Diagonal entries | complex eigenvalues | real **non-negative** singular values |
| Always exists? | **no** (not all diagonalizable) | **yes** (always) |

Eigendecomposition diagonalizes using the **same** basis (when possible); for **normal** matrices that basis is unitary. The SVD uses **different** orthonormal bases for input and output, works for **any** matrix, and **always exists** — which is why it is so powerful.

---

## Instructor Remarks and Study Guidance

- The conceptual leap to SVD is **dropping the same-basis restriction** of similarity: two orthonormal bases (one in, one out) diagonalize **any** matrix.
- Geometrically, \(A\) maps the unit sphere to an **ellipsoid**; \(\sigma_k\) = semi-axis lengths, \(u_k\) = axis directions (output), \(v_k\) = pre-images (input), with \(Av_k = \sigma_k u_k\). Degenerate (rank-deficient) cases give flattened ellipsoids.
- The **rank** is the number of nonzero singular values; the **four fundamental subspaces** read directly off the columns of \(U\) and \(V\).
- The rank-1 components \(\sigma_k u_k v_k^*\) are **orthogonal in the matrix inner product** \(\langle A,B\rangle = \operatorname{tr}(B^*A)\) (proof via \(u_i^* u_j = 0\)).
- **PCA = SVD of the data matrix** (equivalently eigendecomposition of the correlation matrix).
- The **existence proof**: \(\sigma_1 = \|A\|_{2,2}\) gives \(Av_1 = \sigma_1 u_1\); extend to orthonormal bases; unitary invariance of the 2-norm + a clever unit vector forces the off-diagonal row \(w = 0\), giving a block-diagonal \(S_1\); recurse. Modeled on the Schur proof.
- Singular values come from the eigenvalues of \(A^*A\) (or \(AA^*\)); detailed in L22. The instructor says there are efficient algorithms, but the lecture's main conceptual route is through these eigenvalue decompositions.
- Next lecture will cover uses of SVD and additional matrix norms formed by combining the singular values/principal semi-axis lengths.
- The starting point of SVD is the **2-2 norm** — the instructor notes he has not seen an analogous construction starting from the 1-1 or ∞-∞ norm (an open curiosity).

## Source and Coverage Note

Source: `corrected/lecture21_corrected.md`.

Coverage: Matrix-norm recap motivating SVD, including vectorization-based matrix norms and the Frobenius example; algebraic view (\(A = U\Sigma V^*\), shapes, real nonneg diagonal, \(V^*\) convention); connection to and departure from similarity (drop the same-basis restriction → two orthonormal bases diagonalize any matrix); geometric view (sphere → ellipsoid, line segment as degenerate ellipsoid, rank-deficient and tall/fat degenerate cases, hand-drawn figure remark, ellipsoid-as-quadratic-level-set student Q&A, preimage-existence check, assigning \(\sigma_k, u_k, v_k\) with \(Av_k=\sigma_k u_k\)); reduced and full SVD with \(AV=U\Sigma\), multiplication by \(V^*\), extension to unitary matrices, arbitrary completion columns, null-space zero action, and the four fundamental subspaces table; outer-product/rank-1 sum form with multiplication steps as an \(A\)-adaptive orthonormal expansion; matrix inner product \(\langle A,B\rangle=\operatorname{tr}(B^*A)\) and proof that the rank-1 components are orthogonal; PCA connection (SVD of data matrix = eigendecomposition of correlation matrix); preview of computing singular values via \(A^*A\)/\(AA^*\) and efficient algorithms; full formal existence proof (induced 2-norm \(\sigma_1\), orthonormal-basis extension à la Schur, Schur triangularization recall, \(S_1 = U_1^*AV_1\) block form, unitary-invariance facts + clever-unit-vector argument forcing \(w=0\), recursion); SVD-vs-eigendecomposition comparison table; next-lecture remarks on SVD uses and norms built from singular values; instructor curiosity about whether analogous constructions exist for 1-1 or ∞-∞ norms.
