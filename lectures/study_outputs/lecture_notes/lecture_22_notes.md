# Lecture 22 Notes

## Recap: Full and Reduced SVD

The instructor recaps the SVD established in L21.

- **Singular values:** the diagonal entries of \(\Sigma\), real and non-negative; only \(r\) of them are nonzero.
- **Left singular vectors:** \(u_1,\ldots,u_m\) (columns of \(U\)); **right singular vectors:** \(v_1,\ldots,v_n\) (columns of \(V\)).
- **Full SVD:** \(A = U\Sigma V^*\) with \(U\) (\(m\times m\)) and \(V\) (\(n\times n\)) **unitary** and \(\Sigma\) (\(m\times n\)) rectangular diagonal.
- **Reduced SVD:** eliminate the zero diagonal entries of \(\Sigma\) (which silence the corresponding columns of \(U\) and \(V\)); what remains are the **non-degenerate principal semi-axis directions** \(u_1,\ldots,u_r\) and their pre-images \(v_1,\ldots,v_r\), giving \(A = \hat U\hat\Sigma\hat V^*\) with an \(r\times r\) positive diagonal.
- **Outer-product form:** \(A = \sum_{k=1}^r \sigma_k u_k v_k^*\), a sum of rank-1 terms that (with respect to the matrix inner product) are **orthogonal**. The instructor describes this as writing \(A\) in a matrix basis **adapted to \(A\)**: the full family can be completed from singular-vector outer products, while \(A\) itself uses only the diagonal/rank-1 SVD terms weighted by \(\sigma_k\).

The geometric origin: the image of a hypersphere under \(A\) is an **ellipsoid**; the \(\sigma_k\) are the principal semi-axis lengths, the \(u_k\) the axis directions, the \(v_k\) their pre-images.

---

## SVD as the Ultimate Matrix-Analysis Tool

The instructor stresses the SVD is a **perfect matrix / linear-mapping analysis tool** — "like the miracle products they sell on TV," advertising feature after feature. Given the SVD of \(A\), you can read off:

1. **Rank:** the number of nonzero singular values \(= r\) (the number of non-degenerate ellipsoid dimensions = dimension of range = dimension of row space).
2. **Column space \(\mathcal R(A)\):** orthonormal basis \(u_1,\ldots,u_r\) (first \(r\) columns of \(U\)).
3. **Left null space \(\mathcal N(A^*)\):** \(u_{r+1},\ldots,u_m\) (orthogonal to the column space).
4. **Row space \(\mathcal R(A^*)\):** \(v_1,\ldots,v_r\) (first \(r\) columns of \(V\)).
5. **Null space \(\mathcal N(A)\):** \(v_{r+1},\ldots,v_n\).
6. **Induced 2-norm:** \(\|A\|_{2,2} = \sigma_1\) (recall the proof started by setting \(\sigma_1 = \|A\|_{2,2}\)).
7. **Frobenius norm:** \(\|A\|_F = \sqrt{\sum_k \sigma_k^2}\) (derived below).

Projecting a vector onto the range of \(A\) is then **easy**: take inner products with the orthonormal \(u_1,\ldots,u_r\) and recombine.

---

## Why Singular Values Are Real and Non-Negative

**Geometric reason.** In the construction, \(\sigma_1 = \|A\|_{2,2}\) is a **norm** (a length of a principal semi-axis), hence real and \(\ge 0\). Each subsequent \(\sigma_k\) is the 2-norm of a smaller block in the recursive proof — also a norm. So all \(\sigma_k\) are non-negative reals; off-diagonal entries of \(\Sigma\) are zero. Hence \(\Sigma\) is a **real non-negative diagonal** matrix, and the count of nonzero diagonal entries is the rank.

**Algebraic reason (via \(A^*A\)).** From \(A = U\Sigma V^*\),
\[
A^*A = V\Sigma^* U^* U\Sigma V^* = V(\Sigma^*\Sigma)V^*,
\]
the eigendecomposition of \(A^*A\) with eigenvalues \(\sigma_k^2\) (diagonal of \(\Sigma^*\Sigma\)) and eigenvectors \(V\). Since \(A^*A\succeq 0\) (proved earlier: \(x^*A^*Ax = \|Ax\|^2\ge0\)), the eigenvalues \(\sigma_k^2 \ge 0\), so \(\sigma_k = \sqrt{\lambda_k(A^*A)}\) is a real non-negative number.

---

## Frobenius Norm from Singular Values

\[
\|A\|_F = \sqrt{\operatorname{tr}(A^*A)}.
\]
Substitute the SVD. With \(A = U\Sigma V^*\) and \(A^* = V\Sigma^\top U^*\) (order reverses; \(\Sigma\) is real):
\[
\operatorname{tr}(A^*A) = \operatorname{tr}(V\Sigma^\top U^* U\Sigma V^*) = \operatorname{tr}(V\Sigma^\top\Sigma V^*).
\]
The \(U^*U = I\) cancels; then by the cyclic property \(\operatorname{tr}(V X V^*) = \operatorname{tr}(V^*V X) = \operatorname{tr}(X)\):
\[
\operatorname{tr}(A^*A) = \operatorname{tr}(\Sigma^\top\Sigma).
\]
Now \(\Sigma^\top\Sigma\) is diagonal with entries \(\sigma_1^2,\ldots,\sigma_r^2,0,\ldots\), whose trace is \(\sum_k\sigma_k^2\). Therefore
\[
\boxed{\|A\|_F = \sqrt{\sigma_1^2 + \cdots + \sigma_r^2}}\,.
\]
**Alternative (unitary invariance).** Frobenius is unitarily invariant, so \(\|A\|_F = \|U\Sigma V^*\|_F = \|\Sigma\|_F = \sqrt{\sum_k\sigma_k^2}\) directly. The instructor phrases this as the **energy of the singular-value vector**. Both \(\|A\|_{2,2} = \sigma_1\) and \(\|A\|_F\) depend **only on the singular values**, because both are unitarily invariant.

---

## Computing the SVD via \(A^*A\) or \(AA^*\)

This is **not** the numerically preferred algorithm, but it shows the **connection between SVD and eigendecomposition**.

- **Via \(A^*A\):** \(A^*A = V(\Sigma^\top\Sigma)V^*\). It is Hermitian and **positive semidefinite** (always), so it has a unitary eigendecomposition. Its eigenvectors are the **right singular vectors** \(V\); its eigenvalues are \(\sigma_k^2\), giving the singular values. Then recover the left singular vectors from \(Av_k = \sigma_k u_k\), i.e. \(u_k = Av_k/\sigma_k\) — **no second eigendecomposition needed**.
- **Via \(AA^*\):** \(AA^* = U(\Sigma\Sigma^\top)U^*\); its eigenvectors are the **left singular vectors** \(U\).

(Shape note: if \(A\) is fat, \(A^*\) is tall; if \(A\) is full-rank fat then \(AA^*\) is positive **definite**, but \(A^*A\) or \(AA^*\) is always at least positive **semidefinite** and Hermitian — hence normal, hence unitarily diagonalizable.)

**Numerical warning.** In practice forming \(A^*A\) is **inadvisable** (it squares the condition number). Built-in routines (MATLAB `svd`, NumPy `numpy.linalg.svd`) work directly on \(A\) (bidiagonalization), avoiding \(A^*A\). The instructor doesn't know the exact state-of-the-art algorithm but confirms it avoids the explicit product.

---

## Low-Rank Approximation (Eckart–Young)

A major application area.

**Problem.** Given \(A\), find a rank-\(p\) matrix \(B\) as close to \(A\) as possible in Frobenius norm:
\[
\min_{\operatorname{rank}(B)\le p}\ \|A - B\|_F.
\]
The transcript states the constraint as "rank \(p\)"; the standard formulation is rank **at most** \(p\). The truncated SVD has rank at most \(p\), and it has rank exactly \(p\) when the first \(p\) retained singular values are nonzero.

**Why it's hard.** The objective (a norm) is **convex** — "a pleasure to optimize." But the **constraint set** (rank-\(p\) matrices) is **not convex**: the convex combination of two rank-\(p\) matrices can have rank up to \(2p\). (Example: two orthogonal rank-1 matrices averaged \(0.5/0.5\) give a rank-2 matrix.) So the feasible region is non-convex, making the problem hard in general.

**Solution (Eckart–Young).** Despite non-convexity, the SVD gives the **exact global optimum**. Because the singular values are **ordered** \(\sigma_1 \ge \sigma_2 \ge \cdots\) (monotonically non-increasing, by construction), simply **truncate** the outer-product sum at \(p\):
\[
A_p = \sum_{k=1}^p \sigma_k u_k v_k^*,
\]
discarding the \(r - p\) smallest singular values. The error is
\[
\|A - A_p\|_F = \sqrt{\sum_{k=p+1}^r \sigma_k^2}.
\]
The instructor does **not** prove this theorem in lecture; he states the result and moves to implications/applications.

**The same truncation is optimal in the induced 2-norm**, with error \(\|A - A_p\|_{2,2} = \sigma_{p+1}\). The instructor notes he mentions this only after emphasizing the ordering, which is "critical" for this application. For other norms, e.g. the **1-1 norm**, he says he does not know a closed-form solution; changing the norm can force non-convex heuristics. Thus the **choice of norm determines both the meaning of "close" and the tractability** of the problem.

### Application: Image Compression

A grayscale image is a matrix; the running example is the **guitar-player** photo. The source aside identifies the musician with Deep Purple, but the transcribed name is garbled. The image began as color/RGB and was converted to a monochrome intensity matrix of size \(1236 \times 2060 \approx 2.5\) million pixel values.

Compute the SVD and keep only the first \(k\) rank-1 terms: \(A_k = \sum_{i=1}^k \sigma_i u_i v_i^*\). **Storage:** instead of \(mn\) numbers, store \(k\) singular values, \(km\) numbers for the \(u\)'s, and \(kn\) for the \(v\)'s — total \(k(m+n+1)\). For \(m\approx1000, n\approx2000\):
- **Rank-1** (\(k=1\)): you "barely have some idea" what the image is — a poor representation.
- **Rank-10:** \(\approx 10\cdot1000 + 10\cdot2000 + 10 \approx 30{,}000\) numbers vs. 2 million.
- **Rank-20:** \(\approx 60{,}000\) vs. 2 million.

The point of the storage count is that we store the **factors** \(u_i\), \(v_i\), and \(\sigma_i\), not the already-multiplied reconstructed image. The instructor repeatedly frames the comparison as roughly **2 million full pixel values** versus **30,000** (rank 10) or **60,000** (rank 20) stored factor entries.

The error (in Frobenius/MSE sense, since Frobenius measures squared error) is small for modest \(k\) because the **singular values decay rapidly** for natural images (the first is large; most are near zero — best seen on a log scale). This is **not** how real image compression is done, but it illustrates the principle: represent the data in a basis where energy concentrates in a few coefficients. (Netflix matrix completion — discussed later — is another low-rank application.)

---

## Closest Unitary Matrix to a Given Matrix

A second SVD application. **Problem:** given a square matrix \(A\) (not unitary), find the unitary \(Q\) (\(QQ^* = I\)) closest to it in **Frobenius** norm:
\[
\min_{QQ^*=I}\ \|A - Q\|_F^2.
\]
Again the objective is convex but the **set of unitary matrices is non-convex** (the convex combination of two unitaries need not be unitary), so it looks hard. But the SVD gives a **closed-form** solution.

The Frobenius norm is chosen deliberately: the instructor says the problem is hard for other norms, while Frobenius gives a clean analytic formula. He also mentions that unitary approximation appears in some recent neural-network algorithms.

**Scalar analogy (\(1\times1\)).** For a complex number \(a = r e^{j\theta}\), the closest unit-magnitude number is \(e^{j\theta}\) — obtained by the **polar decomposition** and replacing \(r\) with \(1\).

**Derivation.** Write \(A = U\Sigma V^*\) and use Frobenius unitary invariance:
\[
\|A - Q\|_F = \|U\Sigma V^* - Q\|_F = \|\Sigma - U^* Q V\|_F = \|\Sigma - Q'\|_F,
\]
where \(Q' = U^* Q V\) is unitary (product of unitaries). Minimizing the distance from a **non-negative diagonal** \(\Sigma\) to a unitary \(Q'\) is solved by \(Q' = I\). Hence
\[
\boxed{Q = U V^*}\,,
\]
i.e. **find the SVD, set all singular values to 1, and multiply \(U V^*\)** — clearly unitary, and the closest unitary to \(A\) in Frobenius norm.

### Application: Rigid Motion / Image Registration (Computer Vision)

**Setup.** In one scene a (rigid) object sits at some location; in a second scene it has **moved without changing shape**. We want the motion = **rotation** (a unitary/orthogonal \(\Theta\)) **plus translation** \(t\). Register matching points \(x_1, x_2, \ldots\) in the first scene and \(y_1, y_2, \ldots\) in the second; ideally each \(y_i = \Theta x_i + t\). Stacking points as columns of \(X\) and \(Y\) (and adding \(t\) to each column via \(t\,\mathbf 1^\top\)):
\[
Y \approx \Theta X + t\,\mathbf 1^\top.
\]
**Why it's not exact:** registration noise, and projecting a 3-D world to 2-D. So minimize the **least-squares** error:
\[
\min_{\Theta, t}\ \big\|\,Y - \Theta X - t\,\mathbf 1^\top\,\big\|_F^2,
\]
which (as a least-squares problem, revisited under inner-product spaces) has a nice solution — **but** it ignores the **constraint** that \(\Theta\) be unitary (\(\Theta\Theta^* = I\)). Two strategies:
1. **Project after solving:** solve the unconstrained least squares to get a general \(\Theta^\star\), then find the **closest unitary matrix** to \(\Theta^\star\) via \(UV^*\). (Simple but not optimal.)
2. **Gradient on the unitary manifold:** take a gradient step that leaves the unitary set, then **project back** onto the unitary set (via \(UV^*\) from the SVD), repeating — moving "a little bit and coming back" along the manifold.

Related ideas appear in **independent component analysis (ICA)** (minimize mutual information over a unitary matrix, after a PCA whitening step). These are mentioned as buzzwords; details deferred.

The projected-gradient picture is not presented as the only or best constrained method. The instructor says there are many algorithms; in practice one may use something other than the raw gradient, and he skips those details.

---

## Polar Decomposition for Matrices

The complex polar form \(c = r e^{j\theta}\) (\(r > 0\), \(e^{j\theta}\) on the unit circle) generalizes to matrices. The instructor calls this a **non-trivial decomposition**: a **non-singular square** \(A\) can be written
\[
A = P\,T, \qquad P \succ 0\ (\text{positive definite}),\quad T\ \text{unitary}.
\]
("\(P\)" plays the role of \(r > 0\); \(T\) the role of \(e^{j\theta}\).) **Why it's easy from the SVD:** for non-singular \(A\), \(\Sigma\) is positive (full rank). Insert \(U^*U = I\):
\[
A = U\Sigma V^* = (U\Sigma U^*)(U V^*).
\]
Here \(U\Sigma U^*\) is **positive definite** (unitary diagonalization with positive diagonal), and \(U V^*\) is **unitary**. So \(P = U\Sigma U^*\), \(T = UV^*\). **Notably, the unitary factor \(T = UV^*\) is exactly the closest unitary matrix to \(A\)** in Frobenius norm (from the previous section).

**\(1\times1\) check and the correspondence.** In the scalar case \(P\) is a positive real number (\(=r\)) and \(T\) is a number on the unit circle (\(=e^{j\theta}\)) — recovering the complex polar form. A **student asks** about a real/imaginary-part decomposition; the instructor clarifies the right correspondence is via **eigenvalues**, not real/imaginary parts: a general complex matrix lives in an \(n^2\)-dimensional space, so you cannot split it into "two dimensions." The clean analogy is:
- **Hermitian** matrices ↔ **real** numbers (eigenvalues on the real line),
- **positive definite** matrices ↔ **positive real** numbers,
- **unitary** matrices ↔ numbers on the **unit circle** (eigenvalues on the unit circle).
So a unitary matrix generalizes a point on the unit circle, and the polar decomposition generalizes \(c = re^{j\theta}\).

---

## Schatten \(p\)-Norms

New norms defined from the **singular values**. Collect the singular values into a vector \(\sigma = (\sigma_1,\ldots,\sigma_r)\). The **Schatten \(p\)-norm** of \(A\) is the **vector \(p\)-norm of \(\sigma\)**:
\[
\|A\|_{(p)} = \Big(\sum_k \sigma_k^p\Big)^{1/p}.
\]
(The subscript \((p)\) is written on the **left/inside** to distinguish it from the induced norm.) Special cases:
- \(p = 2\): \(\|A\|_{(2)} = \sqrt{\sum_k\sigma_k^2} = \|A\|_F\) — the **Frobenius** norm.
- \(p = \infty\): \(\|A\|_{(\infty)} = \sigma_1 = \|A\|_{2,2}\) — the **operator** norm.
- \(p = 1\): \(\|A\|_{(1)} = \sum_k\sigma_k\) — the **nuclear norm** (below).

So Frobenius and operator norms are both Schatten norms; the new one is \(p = 1\).

---

## Nuclear Norm and Low-Rank via Convex Relaxation

The **Schatten-1 norm** — the **sum of singular values** — is "the star of the show," researched intensively for two decades. It has its own name and notation:
\[
\|A\|_* = \sum_k \sigma_k \quad(\text{nuclear norm, a.k.a. trace norm}),
\]
sometimes written as the trace of \((A^*A)^{1/2}\).

**Why it matters — convex relaxation of rank.** Recall \(\ell_1\) minimization promotes **sparsity** (many zero entries). Applying the same idea to the **singular value vector** \(\sigma\): minimizing the nuclear norm \(\|A\|_*\) drives most \(\sigma_k\) to **zero** — and the number of nonzero singular values is the **rank**. So **minimizing the nuclear norm minimizes the rank** (with appropriate constraints on \(A\); otherwise the trivial minimizer is the zero matrix). The nuclear norm is the **convex substitute for rank**, just as \(\ell_1\) is the convex substitute for sparsity. This gives **low-rank solutions** through a tractable convex problem.

**Warning / exam-style caution.** The instructor explicitly flags the same caution as in \(\ell_1\)/CVX-style sparsity problems: minimizing the nuclear norm alone gives the zero matrix. It becomes meaningful only with constraints, e.g. matching observed entries in a completion problem.

---

## Application: Matrix Completion and the Netflix Challenge

**Who wants low rank?** Matrix completion — central to **recommendation systems** and the **Netflix challenge**.

**Setup.** Rows = customers (tens/hundreds of millions), columns = movies (perhaps hundreds of thousands). Entry \((i,j)\) is customer \(i\)'s rating of movie \(j\), but each customer has rated only a few movies, so the matrix is **mostly incomplete**. Goal: **fill in** the missing entries to predict whether a customer would like an unseen movie.

**Low-rank model.** Represent the rating matrix as a product of two thin matrices:
\[
\text{Ratings} \approx P\,Q^\top,
\]
where each customer is an \(r\)-dimensional **preference vector** (a row of \(P\)) and each movie is an \(r\)-dimensional **feature vector** (a row of \(Q\)). The **inner product** of a user-preference vector and a movie-feature vector gives the predicted **score**. The features may correspond to interpretable factors (is it a horror movie? a comedy? a certain actor present?); a user who weights "comedy" highly scores a comedy highly.

**Two approaches:**
1. **Fixed-rank factorization:** choose rank \(r\) (e.g. 100), and minimize the **Frobenius error over the known entries**:
\[
\min_{P,Q}\ \big\|\,\text{Ratings} - P Q^\top\,\big\|_F^2 \quad(\text{over observed entries}),
\]
recovering the customer matrix \(P\) and movie matrix \(Q\). This **low-rank decomposition is the approach that won the Netflix challenge.**
2. **Nuclear-norm minimization:** minimize \(\|X\|_*\) subject to matching the observed entries — a convex relaxation that produces a low-rank completion without fixing \(r\) in advance.

**History:** the instructor describes the Netflix challenge as an early-2000s event (the transcript says "2003 / beginning of 2000") where Netflix released ratings data but held out some values; teams who best predicted the hidden values won a **\$1,000,000 prize**, and the winning solutions used such low-rank approximation.

The next topic is **inner product spaces**; the instructor says he will continue this discussion on Thursday. He also ends with an administrative request for students to complete a class/course item (the transcript wording is garbled).

---

## Instructor Remarks and Study Guidance

- The SVD is the **ultimate analysis tool**: rank, orthonormal bases for all four fundamental subspaces, \(\|A\|_2 = \sigma_1\), and \(\|A\|_F = \sqrt{\sum\sigma_k^2}\) — all read off directly.
- Singular values are **real, non-negative** because they are norms (geometric) and because \(\sigma_k^2 = \lambda_k(A^*A) \ge 0\) with \(A^*A \succeq 0\) (algebraic).
- **\(\|A\|_F = \sqrt{\sum\sigma_k^2}\)** via the trace cyclic property or unitary invariance.
- **Eckart–Young:** truncating the ordered SVD gives the best rank-\(p\) approximation (global optimum despite the non-convex rank constraint), in both Frobenius and 2-norms; image compression is the showcase.
- **Closest unitary matrix** to \(A\) (Frobenius) is \(Q = UV^*\) (set all \(\sigma_k = 1\)); used in rigid-motion/registration and ICA.
- **Polar decomposition** \(A = (U\Sigma U^*)(UV^*) = P\,T\) generalizes \(c = re^{j\theta}\); the correspondence is via eigenvalues (Hermitian↔real, PD↔positive real, unitary↔unit circle).
- **Schatten \(p\)-norms** are \(p\)-norms of the singular-value vector: \(p=2\) → Frobenius, \(p=\infty\) → operator, \(p=1\) → **nuclear norm** (\(\sum\sigma_k\)), the **convex relaxation of rank** (low-rank analog of \(\ell_1\) sparsity).
- **Matrix completion / Netflix:** model ratings as low-rank \(PQ^\top\); the winning approach minimized Frobenius error over observed entries; nuclear-norm minimization is the convex alternative.
- **Recurring warnings:** changing the norm can destroy the closed-form SVD solution; non-convex constraints appear in both rank-\(p\) and unitary-matrix problems; nuclear-norm minimization needs additional constraints or the zero matrix wins.
- **Closing:** continuation on Thursday, then inner product spaces; administrative class/course request at the end.

## Source and Coverage Note

Source: `corrected/lecture22_corrected.md`.

Coverage: Recap of full/reduced SVD and outer-product form; SVD as analysis tool (rank, four fundamental subspaces, projection to range, \(\sigma_1\), Frobenius); why singular values are real/non-negative (geometric and algebraic via \(A^*A\succeq0\)); Frobenius norm \(=\sqrt{\sum\sigma_k^2}\) (trace-cyclic and unitary-invariance derivations, singular-value energy); computing the SVD via \(A^*A\)/\(AA^*\) eigendecomposition (both directions, \(u_k = Av_k/\sigma_k\), PSD/Hermitian/normal structure, numerical warning); low-rank approximation / Eckart-Young (rank \(p\) versus rank at most \(p\), convex objective, non-convex rank set with the rank-1+rank-1 example, ordered-\(\sigma\) truncation solution stated without proof, Frobenius and 2-norm errors, no closed form for other norms); image compression (guitar-player/Deep Purple aside with garbled name, RGB-to-monochrome conversion, \(1236\times2060\), storage \(k(m+n+1)\), factor storage rather than full product, rank-1/10/20 comparison, singular-value decay, not real image compression); closest unitary matrix (\(Q=UV^*\) via Frobenius invariance, deliberate Frobenius choice, scalar polar analogy, neural-network mention); rigid-motion/image-registration application (rotation+translation, least squares, ignored unitary constraint, project-onto-unitary vs. projected-gradient/manifold method, many algorithms/raw-gradient caveat, ICA/PCA mention); matrix polar decomposition (\(A=(U\Sigma U^*)(UV^*)\), nonsingular square assumption, non-triviality, unitary factor = closest unitary, scalar check, eigenvalue correspondence Hermitian/PD/unitary, student Q&A on real/imaginary parts); Schatten \(p\)-norms (\(p\)-norm of singular-value vector; notation distinction; \(p=2\) Frobenius, \(p=\infty\) operator, \(p=1\) nuclear); nuclear/trace norm as convex relaxation of rank (sparsifying singular values, zero-solution constraint warning); matrix completion and the Netflix challenge (incomplete ratings matrix, low-rank \(PQ^\top\) user/movie factorization, fixed-rank Frobenius vs. nuclear-norm approaches, \$1M prize and source-stated early-2000s history); closing continuation on Thursday, inner product spaces, and garbled administrative request.
