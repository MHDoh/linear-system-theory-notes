# Lecture 20 Notes

## Recap and Goal: From Vector Norms to Matrix Norms

The previous lectures developed vector \(p\)-norms in \(\mathbb{C}^n\) (\(\ell_1\) taxicab/sparsity, \(\ell_2\) Euclidean, \(\ell_\infty\) Chebyshev/minimax). This lecture asks: **how do we measure how big a matrix is?** There are two fundamentally different answers.

---

## Two Approaches to Matrix Norms

### Approach 1: Flatten the Matrix into a Vector

Take the \(m\times n\) matrix, stack its columns into a single \(mn\)-dimensional vector (the **vec** notation), and apply a vector norm. This approach **does not care where the entries come from** — it just stuffs them into a vector.

Using the **2-norm** of the flattened vector gives the **Frobenius norm**: the "total energy" of the matrix.
\[
\|A\|_F = \Big(\sum_{i,j}|a_{ij}|^2\Big)^{1/2} = \sqrt{\operatorname{tr}(A^*A)} = \sqrt{\operatorname{tr}(AA^*)}.
\]
(Recall \(\operatorname{tr}(A^*A) = \sum_{i,k}|a_{ik}|^2\): the sum of squared magnitudes.)

### Approach 2: Induced (Operator) Norms

Other norms **care about the locations** of the entries because a matrix defines a **linear mapping** \(A:\mathbb{C}^n \to \mathbb{C}^m\). Picture an **input space** \(\mathbb{C}^n\) and a (possibly different-dimensional) **output space** \(\mathbb{C}^m\). We may measure size **differently** in each space — say a \(p\)-norm in the input and a \(q\)-norm in the output. For a nonzero input \(x\), look at the **gain**
\[
\frac{\|Ax\|_q}{\|x\|_p},
\]
the factor by which the map changes the norm. Gain \(> 1\) is amplification, \(< 1\) is attenuation — but it depends on \(x\) (one direction might give \(1.1\), another \(0.5\)). The **induced norm** is the **maximum gain** over all directions:
\[
\boxed{\|A\|_{q,p} = \max_{x\ne0}\frac{\|Ax\|_q}{\|x\|_p} = \max_{\|x\|_p=1}\|Ax\|_q.}
\]
**Scale invariance.** Because \(\|A(\alpha x)\|_q/\|\alpha x\|_p = \|Ax\|_q/\|x\|_p\), the ratio depends only on the **direction** of \(x\). So we restrict the search to the **boundary of the unit \(p\)-norm ball** in the input space and ask: which boundary point produces the maximum output \(q\)-norm?

---

## Geometric Calculation Strategy

To compute an induced norm geometrically:
1. Draw the unit \(\|\cdot\|_p\)-ball boundary in the input space.
2. Map all boundary points through \(A\) to find the **image**.
3. Find the maximum \(\|\cdot\|_q\)-norm over that image.

**Key lemma (linear maps send line segments to line segments).** Let \(a, b\) be two points with images \(Aa = a'\), \(Ab = b'\). Any point on the segment joining them is a **convex combination** \(\lambda a + (1-\lambda)b\) with \(\lambda \in [0,1]\), and
\[
A\big(\lambda a + (1-\lambda)b\big) = \lambda Aa + (1-\lambda)Ab = \lambda a' + (1-\lambda)b'.
\]
So the segment from \(a\) to \(b\) maps to the segment from \(a'\) to \(b'\). **Consequence:** for a **polytope** ball (boundaries are line segments, as for \(\ell_1\) and \(\ell_\infty\)), it suffices to map the **vertices** and connect them.

---

## Induced 1-1 Norm (Worked Example)

Throughout, use the running example
\[
A = \begin{bmatrix} 1 & 2 \\ 0 & 2 \end{bmatrix}.
\]
For \(\|A\|_{1,1}\) we use the \(\ell_1\)-norm at both input and output (written just \(\|A\|_1\), understood as 1-1). The unit \(\ell_1\)-ball is a **diamond** with vertices
\[
A=(1,0),\quad B=(0,1),\quad C=(-1,0),\quad D=(0,-1).
\]
Map the vertices (multiplying by a standard basis vector **picks a column**):
\[
A\!\to\!\begin{bmatrix}1\\0\end{bmatrix}, \quad B\!\to\!\begin{bmatrix}2\\2\end{bmatrix}, \quad C\!\to\!\begin{bmatrix}-1\\0\end{bmatrix}, \quad D\!\to\!\begin{bmatrix}-2\\-2\end{bmatrix}.
\]
(\(B=(0,1)\) picks column 2 \(=(2,2)\); \(A=(1,0)\) picks column 1 \(=(1,0)\).) The diamond maps to a parallelogram; the image is this **polytope** (a bounded region whose boundaries are hyperplanes; an unbounded one is a **polyhedron**, a bounded one a **polytope**). Now take \(\ell_1\)-norms of the image vertices:
\[
\|(1,0)\|_1=1,\quad \|(2,2)\|_1=4,\quad \|(-1,0)\|_1=1,\quad \|(-2,-2)\|_1=4.
\]
Maximum is at \(B'\) and \(-D'\): \(\boxed{\|A\|_{1,1} = 4}\).

Geometric reading: if the maximum point is visually unclear, imagine expanding centered \(\ell_1\)-balls in the output space until the largest one still intersects the image. The last-contact points here are the images of \(B\) and \(D\), both with \(\ell_1\)-norm \(4\).

**Shortcut.** This was "a heck of a thing" even for a \(2\times2\). It can be shown (via the Hölder inequality below) that
\[
\|A\|_{1,1} = \max_j \|a_j\|_1 \quad(\text{maximum column } \ell_1\text{-norm}).
\]
Here columns have \(\ell_1\)-norms \(1\) and \(4\); max is \(4\). ✓ Essential for large matrices (you cannot draw a 1000-dimensional \(\ell_1\)-ball).

**Frobenius for comparison:** \(\|A\|_F = \sqrt{1+4+0+4} = \sqrt 9 = 3\).

---

## Induced ∞-∞ Norm (Worked Example)

For \(\|A\|_{\infty,\infty}\) (written \(\|A\|_\infty\)), the unit \(\ell_\infty\)-ball is a **square** with vertices \((\pm1,\pm1)\). Map them:
\[
\begin{bmatrix}1\\1\end{bmatrix}\!\to\!\begin{bmatrix}3\\2\end{bmatrix},\quad
\begin{bmatrix}-1\\1\end{bmatrix}\!\to\!\begin{bmatrix}1\\2\end{bmatrix},\quad
\begin{bmatrix}-1\\-1\end{bmatrix}\!\to\!\begin{bmatrix}-3\\-2\end{bmatrix},\quad
\begin{bmatrix}1\\-1\end{bmatrix}\!\to\!\begin{bmatrix}-1\\-2\end{bmatrix}.
\]
(\((1,1)\) sums the columns \(=(3,2)\); \((-1,1)\) subtracts column 1 from column 2 \(=(1,2)\).) The square maps to a parallelogram ("a parallel-parking shape"). Take \(\ell_\infty\)-norms of the image vertices:
\[
\|(3,2)\|_\infty=3,\quad \|(1,2)\|_\infty=2,\quad \|(-3,-2)\|_\infty=3,\quad \|(-1,-2)\|_\infty=2.
\]
Maximum is \(\boxed{\|A\|_{\infty,\infty} = 3}\).

**Shortcut (dual to the 1-1 case).** Where 1-1 used max **column** \(\ell_1\)-norm, ∞-∞ uses the maximum **row** \(\ell_1\)-norm:
\[
\|A\|_{\infty,\infty} = \max_i \|r_i\|_1.
\]
Rows have \(\ell_1\)-norms \(\|(1,2)\|_1 = 3\) and \(\|(0,2)\|_1 = 2\); max is \(3\). ✓

The bottom line: the **same matrix** gives **different norm values** for different input/output norm choices, each useful in different applications.

---

## The Star of the Show: Induced 2-2 Norm

Using \(\ell_2\) at both input and output (written \(\|A\|_{2,2}\) or \(\|A\|_2\)) gives the **maximum Euclidean gain** — "one of the most frequently used norms," and the gateway to the **SVD**.

### The Image of the Unit Sphere Is an Ellipse(oid)

The unit \(\ell_2\)-ball boundary in 2-D is a **circle**. Unlike the polytope cases (whose images are polytopes), the image of a sphere under a linear map is an **ellipsoid**. For invertible \(A\), set \(y = Ax\), so \(x = A^{-1}y\), and the condition \(\|x\|_2 = 1\) becomes \(\|A^{-1}y\|_2 = 1\), i.e.
\[
y^*\,(A^{-1})^*A^{-1}\,y = y^*\,(AA^*)^{-1}\,y = 1.
\]
This is the equation of an **ellipse** \(y^* M^{-1} y = 1\) with \(M = AA^*\). The **principal semi-axes** point along the eigenvectors of \(M\), with lengths \(\sqrt{\lambda_i(AA^*)}\). The maximum \(\ell_2\)-norm on the ellipse is the **longest semi-axis**:
\[
\|A\|_{2,2} = \sqrt{\lambda_{\max}(A^*A)} = \sigma_1(A),
\]
the **largest singular value** (the nonzero eigenvalues of \(AA^*\) and \(A^*A\) coincide; either works — to be justified later).

### Worked Numbers for the Running Example

For \(A = \begin{bmatrix}1&2\\0&2\end{bmatrix}\):
\[
A^*A = \begin{bmatrix}1&2\\2&8\end{bmatrix}, \qquad \text{char. eqn: } \lambda^2 - 9\lambda + 4 = 0,
\]
\[
\lambda = \frac{9 \pm \sqrt{81-16}}{2} = \frac{9 \pm \sqrt{65}}{2} \approx 8.53 \ \text{and}\ 0.47.
\]
The eigenvectors give the **directions** of the principal semi-axes (e.g., the longest, \(v_1\)), and the semi-axis **lengths** are the square roots of the eigenvalues: \(\sqrt{8.53}\approx2.92\) (long axis) and \(\sqrt{0.47}\approx0.69\) (short axis). Drawing a sequence of \(\ell_2\)-balls of increasing radius over the ellipse, the largest one that still touches the ellipse touches it at the **ends of the longest semi-axis** — confirming that the maximum 2-norm is the longest semi-axis. Hence
\[
\|A\|_{2,2} = \sqrt{8.53} \approx 2.92.
\]
(The instructor's running discussion is partly garbled around the numbers, but the eigenvalues \(8.53\) and \(0.47\) are exactly those of \(A^*A = [1,2;2,8]\).)

The output-side ellipse derivation in the lecture used
\[
AA^*=\begin{bmatrix}5&4\\4&4\end{bmatrix},
\]
because the ellipse equation was written as \(y^*(AA^*)^{-1}y=1\). This matrix has the same characteristic equation \(\lambda^2-9\lambda+4=0\), so the same eigenvalues \(8.53\) and \(0.47\). If \(AA^*=V\Lambda V^*\) and \(z=V^*y\), then
\[
y^*(AA^*)^{-1}y=1
\quad\Longleftrightarrow\quad
\frac{|z_1|^2}{\lambda_1}+\frac{|z_2|^2}{\lambda_2}=1.
\]
So the inverse matrix contributes \(1/\lambda_i\) in the ellipse equation, but the actual semi-axis lengths are \(\sqrt{\lambda_i}\), not \(\lambda_i\). The instructor explicitly corrected this point: the long-axis length is \(\sqrt{8.53}\), not \(8.53\). The drawn \(v_1,v_2\) arrows on the slide were directions of principal axes, not eigenvectors already scaled by the eigenvalues, and the picture was not to scale.

### Notation Warning

\(\|A\|_2\) means the **induced 2-2 norm** \(= \sigma_1\), **not** the Frobenius norm. If you mean the root-sum-of-squares-of-entries, you must write \(\|A\|_F\). The 2-2 induced norm is also called the **operator norm** or **spectral norm**. In some references "\(\|A\|\)" with no subscript defaults to the operator norm; in others it defaults to Frobenius — so always check.

### The Non-Invertible (Degenerate) Case — Student Question

A student asks what happens if \(A\) is **not invertible**. Then the image of the sphere is a **degenerate ellipsoid**: in 2-D with a rank-1 matrix, a line segment; in 3-D with a rank-2 matrix, an ellipse lying in the (rank-2) plane through the origin (the range space). You can reach that subspace via the **QR factorization** of \(A\) (whose \(Q\) columns give an orthonormal basis for the range) and write the ellipse in restricted coordinates. **Crucially**, the formula \(\sqrt{\lambda_{\max}(A^*A)}\) still gives the maximum 2-norm **even when \(A\) is singular** — invertibility was only needed to *draw* the full ellipse, not to compute the largest semi-axis. So **invertibility is not required** for \(\|A\|_{2,2} = \sigma_1\).

---

## Shortcut Formulas Summary

| Induced norm | Shortcut | Geometric meaning |
|---|---|---|
| \(\|A\|_{1,1}\) | \(\max_j \|a_j\|_1\) (max column \(\ell_1\)) | \(\ell_1\)-ball vertex \(\to\) column |
| \(\|A\|_{\infty,\infty}\) | \(\max_i \|r_i\|_1\) (max row \(\ell_1\)) | \(\ell_\infty\)-ball vertex \(\to\) row |
| \(\|A\|_{2,2}\) | \(\sigma_1 = \sqrt{\lambda_{\max}(A^*A)}\) | longest semi-axis of image ellipsoid |
| \(\|A\|_F\) | \(\sqrt{\sum_{ij}|a_{ij}|^2}\) | flatten + \(\ell_2\) |

For the running example: \(\|A\|_F = 3\), \(\|A\|_{1,1} = 4\), \(\|A\|_{\infty,\infty} = 3\), \(\|A\|_{2,2} = \sqrt{8.53}\approx2.92\). Different numbers, different meanings — none universally "largest."

---

## A Few Student Questions on Defining Norms

**Affine maps.** A student asks whether you can define a norm for an affine map \(x \mapsto Ax + b\). The instructor: you typically **lift** the affine map into a linear one by concatenation,
\[
Ax + b = \begin{bmatrix} A & b \end{bmatrix}\begin{bmatrix} x \\ 1 \end{bmatrix},
\]
working in the lifted space (this is how affine expressions are folded into a single matrix, used e.g. in **total least squares**). But the gain of the concatenated matrix \([A\ b]\) is **not** a true norm of the affine map, because the lifted input's last entry is **fixed at 1** — you don't have the freedom over that coordinate. Computing the 2-norm of \([A\ b]\) gives an **upper bound** on the affine map's peak gain (it assumes control over that fixed coordinate), but whether the bound is achieved is unclear. The peak gain of an affine system *can* be defined, but it is a system gain, not a matrix norm.

**Averaging two norms.** Another student asks whether averaging norms (or "average of \(2\) and \(4\)") yields a norm. The instructor hasn't seen it and is unsure it would satisfy the **homogeneity** (scaling) and **triangle inequality** axioms — but notes that we *do* build norms from singular values (next), so some non-obvious combinations are legitimate norms.

**Preview — nuclear norm and the Netflix challenge.** One especially important matrix norm to come is the **sum of the principal semi-axis lengths** (the sum of singular values / square roots of the \(A^*A\) eigenvalues) — the **nuclear norm**. It is the key to **low-rank approximation** and powered the **Netflix challenge** (recommendation systems: recommend movies so users keep their subscription). It "burnt the brains" of many researchers in the 1990s–2000s. (The instructor jokes about reusing the same Netflix-challenge story year after year — like a friend told to "change your jokes or change your friends"; luckily the students change each term, so the jokes can repeat.) Details come with the Schatten norms in a later lecture.

---

## Unitary-Invariant Norms

Earlier, **unitary matrices** were introduced as the matrices that **preserve the 2-norm**. Now flip the viewpoint: which **norms** are preserved under unitary maps? The 2-norm is — multiplying a vector by a unitary matrix doesn't change its 2-norm. This is now read as a **property of the 2-norm**: it is **unitarily invariant**. By contrast, the **\(\ell_1\)** and **\(\ell_\infty\)** norms are **not** unitarily invariant (a unitary rotation changes them).

### Frobenius Norm Is Unitarily Invariant

For unitary \(U, Q\):
\[
\|UAQ\|_F^2 = \operatorname{tr}\big((UAQ)^*(UAQ)\big) = \operatorname{tr}(Q^*A^*U^*UAQ) = \operatorname{tr}(Q^*A^*AQ).
\]
Using \(U^*U = I\), then cycling the trace (\(\operatorname{tr}(Q^*A^*AQ) = \operatorname{tr}(A^*A\,QQ^*) = \operatorname{tr}(A^*A)\)) and \(QQ^* = I\):
\[
\|UAQ\|_F = \sqrt{\operatorname{tr}(A^*A)} = \|A\|_F.
\]
So multiplying \(A\) by unitary matrices on the left and right leaves the Frobenius norm unchanged.

### 2-2 (Operator) Norm Is Unitarily Invariant

The 2-2 norm is a **ratio of two 2-norms**, each unitarily invariant. Multiplying \(A\) on the right by a unitary changes the input without changing its 2-norm; multiplying on the left by a unitary changes the output without changing its 2-norm. So \(\|UAQ\|_{2,2} = \|A\|_{2,2}\).

In formula form, for unitary \(U,Q\):
\[
\|UAQ\|_{2,2}
=\max_{x\ne0}\frac{\|UAQx\|_2}{\|x\|_2}
=\max_{x\ne0}\frac{\|AQx\|_2}{\|x\|_2}.
\]
Let \(z=Qx\). Since \(Q\) is unitary, \(\|z\|_2=\|x\|_2\) and \(z\) ranges over the same input space as \(x\). Hence
\[
\|UAQ\|_{2,2}
=\max_{z\ne0}\frac{\|Az\|_2}{\|z\|_2}
=\|A\|_{2,2}.
\]

**Why this matters:** both the Frobenius and 2-2 norms depend **only on the singular values** of \(A\) (which are themselves unitarily invariant). Indeed \(\|A\|_{2,2} = \sigma_1\) and \(\|A\|_F = \sqrt{\sigma_1^2+\cdots+\sigma_r^2}\) (proved after SVD).

---

## Norm Inequalities (Toward Shortcut Justifications)

### Cauchy–Schwarz (Recap)

For \(n\)-dimensional vectors, the magnitude of the **Euclidean inner product** is bounded by the product of the 2-norms:
\[
|\langle x, y\rangle| \le \|x\|_2\,\|y\|_2.
\]
This is what lets us define the cosine of the angle (the ratio of inner product to the product of norms). The proof is short.

### The Hadamard Product

Define the **Hadamard product** as **elementwise** multiplication: for same-dimension vectors (or matrices) \(x\) and \(y\), \((x \odot y)_i = x_i y_i\). In MATLAB this is `.*` (the dot before the star); ordinary `*` is matrix multiplication. In Python (NumPy), elementwise is the default `*`, while **matrix** multiplication needs `@` (or `np.dot`) — "I like Python, but I hate that part."

### A Hölder-Type Inequality

A stronger bound than Cauchy–Schwarz uses the **\(\ell_1\)-norm of the Hadamard product**:
\[
\|x \odot y\|_1 = \sum_i |x_i y_i| \ \ge\ |\langle x, y\rangle|,
\]
because summing **absolute values** of the term-by-term products is at least the magnitude of their (signed) sum. And this is itself bounded by a product of a \(p\)-norm and a \(q\)-norm:
\[
\boxed{\ \|x \odot y\|_1 \le \|x\|_p\,\|y\|_q, \qquad \frac1p + \frac1q = 1.\ }
\]
The exponents are **conjugate** (\(1/p + 1/q = 1\)), not arbitrary. Common special cases:
- \(p = \infty,\ q = 1\) (the most common).
- \(p = 1,\ q = \infty\) (the symmetric version, used in the equalization application below).
- \(p = 2,\ q = 2\) (recovers Cauchy–Schwarz, since \(\|x\odot y\|_1 \ge |\langle x,y\rangle|\)).

So this Hölder inequality is **stronger** than bounding \(|\langle x, y\rangle|\) directly.

**Clarification (student Q&A).** The inner product here is the **Euclidean** inner product — there is **no inner product that induces the \(\ell_1\) or \(\ell_\infty\) norm** (only the 2-norm comes from an inner product). Cauchy–Schwarz in its general form holds in any **inner product space** with the **induced** norm; here we are in a normed space bounding the Euclidean inner product by **non-induced** norms (\(\ell_p, \ell_q\)). The full inner-product-space treatment comes later.

**Use:** this Hölder inequality is exactly what **justifies the shortcut formulas** for the induced 1-1 and ∞-∞ matrix norms (each matrix-norm entry involves a row × vector inner product, bounded by the relevant \(p\)/\(q\) norms).

For the 1-1 norm, let \(a_j\) be column \(j\). For \(\|x\|_1=1\),
\[
\|Ax\|_1
=\sum_i\left|\sum_j a_{ij}x_j\right|
\le \sum_i\sum_j |a_{ij}|\,|x_j|
=\sum_j |x_j|\,\|a_j\|_1
\le \max_j\|a_j\|_1.
\]
Equality is achieved by choosing \(x=e_j\) for a column with maximum \(\ell_1\)-norm, so \(\|A\|_{1,1}=\max_j\|a_j\|_1\).

For the ∞-∞ norm, let \(r_i\) be row \(i\). For \(\|x\|_\infty=1\),
\[
\|Ax\|_\infty
=\max_i |\langle r_i,x\rangle|
\le \max_i \|r_i\|_1\|x\|_\infty
=\max_i\|r_i\|_1.
\]
For a row attaining the maximum, choose \(x_j\) with signs matching the conjugates/signs of that row's entries; then the bound is attained. Thus \(\|A\|_{\infty,\infty}=\max_i\|r_i\|_1\).

---

## Application: Communication-Channel Equalization

The Hölder/\(\ell_1\)–\(\ell_\infty\) inequality has a real engineering use in **channel equalization** (one of the instructor's research areas).

**Setup.** In digital communications, bits are sent as a sequence of \(\pm 1\) symbols (logic 1 → \(+1\), logic 0 → \(-1\)). Passing through a physical channel (reflections off "mountains," multiple delayed copies), the signal is **scrambled** — this is **inter-symbol interference**, modeled as **convolution** with the channel impulse response \(h\). An ideal channel would be a **delta** (all zeros except one tap): no scrambling.

**Equalizer.** At the receiver we add a filter and convolve, producing an **overall channel** \(g = h * (\text{equalizer})\), under our control. We want \(g\) to be as close to a **delta** as possible — i.e., **sparse**, with small \(\ell_1\)-norm.

**The inequality at work.** The equalizer output is an **inner product** of the overall channel \(g\) with the (bounded) input symbol sequence. By Hölder with \(p=1, q=\infty\): the inner product is bounded by \(\|g\|_1 \,\|\text{symbols}\|_\infty\), and since the symbols are \(\pm1\) (\(\ell_\infty\)-norm \(=1\)), **minimizing the peak (worst-case) output magnitude is equivalent to minimizing the \(\ell_1\)-norm of the overall channel** — which **sparsifies** \(g\), inverting the channel without training. This connects matrix norms, the Hölder inequality, and sparsity into a practical equalization method.

---

## Toward SVD

The image of the unit sphere under \(A\) is an **ellipsoid** whose principal semi-axes have lengths equal to the **singular values** \(\sigma_1 \ge \sigma_2 \ge \cdots\), point along the **left singular vectors** \(u_k\), and correspond to input directions the **right singular vectors** \(v_k\), with \(Av_k = \sigma_k u_k\). This sphere → ellipsoid picture is the geometric heart of the **Singular Value Decomposition** — "the best thing that happened to us" — which writes a matrix as **unitary × diagonal × unitary** (two unitary matrices, one real nonneg diagonal), gives a clean picture of the four fundamental subspaces, and underlies countless algorithms and proofs. Developed in L21.

---

## Instructor Remarks and Study Guidance

- **Frobenius ≠ operator norm.** \(\|A\|_F = \sqrt{\sum\sigma_k^2}\) (flatten + \(\ell_2\)); \(\|A\|_2 = \sigma_1\) (induced 2-2). Both use \(\ell_2\) but differently; this is a classic point of confusion. Write \(\|A\|_F\) explicitly.
- **Induced norm = maximum gain** over the unit input ball; restrict to the ball boundary, and for polytope balls, to the **vertices**.
- **Shortcuts:** 1-1 = max **column** \(\ell_1\); ∞-∞ = max **row** \(\ell_1\); 2-2 = \(\sigma_1 = \sqrt{\lambda_{\max}(A^*A)}\), valid even for singular \(A\).
- **Frobenius and 2-2 norms are unitarily invariant** (hence functions of singular values only); \(\ell_1\) and \(\ell_\infty\) are not.
- **Hölder inequality** \(\|x\odot y\|_1 \le \|x\|_p\|y\|_q\) with \(1/p+1/q=1\) is stronger than bounding \(|\langle x,y\rangle|\); it justifies the matrix-norm shortcut formulas and underlies the channel-equalization sparsity application. Only the 2-norm comes from an inner product.
- **Nuclear norm** (sum of singular values) is coming — the engine of low-rank approximation and the Netflix challenge.

## Source and Coverage Note

Source: `corrected/lecture20_corrected.md`.

Coverage: Two approaches to matrix norms (flatten/Frobenius vs. induced); Frobenius definition, trace formulas; induced-norm definition as maximum gain with scale-invariance and unit-ball-boundary reduction; geometric calculation strategy and the line-segment/convex-combination lemma with polytope/polyhedron terminology; worked 1-1 norm for \(A=[1,2;0,2]\) (diamond vertices → parallelogram, max \(\ell_1=4\), output \(\ell_1\)-ball last-contact cue, max-column shortcut) and worked ∞-∞ norm (square → parallelogram, max \(\ell_\infty=3\), max-row shortcut); induced 2-2 norm (sphere → ellipse derivation \(y^*(AA^*)^{-1}y=1\), output-side \(AA^*=[5,4;4,4]\), inverse-eigenvalue coordinate equation, longest semi-axis \(=\sqrt{\lambda_{\max}}=\sigma_1\), worked eigenvalues \(8.53/0.47\) of both \(AA^*\) and \(A^*A=[1,2;2,8]\), drawing/not-to-scale correction, operator/spectral-norm notation warning, non-invertible degenerate case and QR/reduced-form remark, invertibility not required); shortcut-formula summary table; student Q&As (affine-map lifting/total-least-squares upper bound, averaging norms, nuclear-norm/Netflix preview with the recurring-joke anecdote); unitary-invariant norms (2-norm viewpoint flip, Frobenius invariance via trace proof, 2-2 invariance via explicit maximum-ratio proof, \(\ell_1/\ell_\infty\) not invariant); norm inequalities (Cauchy–Schwarz recap, Hadamard product with `.*`/`@` notation, Hölder inequality \(\|x\odot y\|_1\le\|x\|_p\|y\|_q\) with conjugate exponents and special cases, clarification that only the 2-norm is inner-product-induced, proof sketches for the 1-1 and ∞-∞ shortcuts); communication-channel equalization application (ISI as convolution, overall channel sparsification, peak-minimization ⇔ \(\ell_1\)-minimization via Hölder); SVD preview.
