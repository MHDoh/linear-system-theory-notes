# Lecture 23 Notes

## Schatten \(p\)-Norms

The **Schatten \(p\)-norm** of a matrix applies the vector \(\ell_p\)-norm to the **singular-value vector** \(\sigma = (\sigma_1,\ldots,\sigma_r)\):
\[
\|A\|_{(p)} = \|\sigma\|_p = \Big(\sum_{k=1}^r \sigma_k^p\Big)^{1/p}.
\]
(The subscript notation is the instructor's own, used to distinguish it from induced norms.) Three special cases unify the most important matrix norms:

| \(p\) | Formula | Name |
|---|---|---|
| \(1\) | \(\sum_k \sigma_k\) | **Nuclear norm** \(\|A\|_*\) (trace norm) |
| \(2\) | \(\sqrt{\sum_k \sigma_k^2} = \|A\|_F\) | **Frobenius norm** |
| \(\infty\) | \(\max_k \sigma_k = \sigma_1 = \|A\|_{2,2}\) | **operator** / induced 2-2 norm |

All three depend **only on the singular values** — they differ only in how the singular values are aggregated. The Schatten-\(\infty\) norm is \(\sigma_1\), which (since singular values are ordered) is the largest singular value — the very norm the SVD construction started from (the induced 2-2 / operator norm = max Euclidean gain).

---

## Nuclear Norm: Convex Relaxation of Rank

The **Schatten-1 norm** — the **sum of singular values** — is "the most famous one" and the focus of two decades of machine-learning and signal-processing research. Its own name and notation:
\[
\|A\|_* = \sum_{k=1}^r \sigma_k \quad(\text{nuclear norm, a.k.a. trace norm}).
\]

**Why it matters.** It is the **\(\ell_1\)-norm of the singular-value vector**. From the homework experience, minimizing an \(\ell_1\)-norm has a **sparsifying** effect. So minimizing the nuclear norm drives **most singular values to zero** — and the number of nonzero singular values is the **rank**. Thus:
\[
\text{minimize } \|A\|_* \ \Longleftrightarrow\ \text{minimize the rank of } A.
\]
Rank minimization is a **hard** (non-convex) problem; the nuclear norm is its **convex relaxation** (a convex function of the matrix entries), solvable efficiently with convex tools (e.g. SDP, CVX). This is exactly analogous to using \(\ell_1\) as the convex substitute for sparsity (the \(\ell_0\) count) in vectors.

---

## Application: Matrix Completion and the Netflix Challenge

**Setup.** Netflix has a matrix with **customers** as rows and **movies** as columns; entry \((i,j)\) is customer \(i\)'s rating of movie \(j\) (early ratings were thumbs-up/down or small integer scales). With millions of customers and tens/hundreds of thousands of movies — and each customer having rated only hundreds — **most entries are unknown**. Netflix's **challenge** (around 2006, a seminal event for large-scale data science): they hid some known ratings and offered a **\$1,000,000 prize** to whoever best predicted them.

Additional transcript details: the instructor's drawing labels rows and columns informally, but the orientation is not mathematically important; the key object is a partially observed customer-movie rating matrix. The old rating scheme is described loosely as numeric/thumb-style values, and the exact scale is not used in the math. Netflix deliberately removed some ratings it already knew, treated them as unknown, and used prediction of those held-out values to score the challenge.

### Low-Rank Model

Approximate the giant rating matrix as a product of two **thin** (low-rank) matrices:
\[
A \approx C\,M, \qquad C \in \mathbb{R}^{m\times r}\ (\text{customer feature matrix}), \quad M \in \mathbb{R}^{r\times n}\ (\text{movie feature matrix}).
\]
Each customer is an \(r\)-dimensional **feature vector** (a row of \(C\)); each movie is an \(r\)-dimensional feature vector (a column of \(M\)). The predicted rating \(A_{ij}\) is the **inner product** of customer \(i\)'s vector with movie \(j\)'s vector — measuring their **alignment** (e.g. a comedy-loving user against a comedy movie scores high). The feature dimensions may correspond to interpretable factors (horror? comedy? a given actor?).

### Two Approaches

**1. Fixed-rank factorization.** Choose \(r\) up front and fit \(C, M\) by minimizing the Frobenius error **over the observed entries only** (let \(\Omega\) be the known index set):
\[
\min_{C,M} \sum_{(i,j)\in\Omega} \big(A_{ij} - (CM)_{ij}\big)^2.
\]
The number of unknowns is \(r(m+n)\); ideally the number of known entries exceeds this (otherwise add **regularization**; there may be infinitely many solutions). **This low-rank factorization is the approach that won the Netflix challenge.** (It is a bilinear, non-convex problem — typically solved by alternating least squares.)

**2. Nuclear-norm minimization (convex).** Don't assume a rank; instead minimize the nuclear norm subject to matching the observed entries:
\[
\min_{B} \|B\|_* \quad\text{s.t.}\quad B_{ij} = A_{ij}\ \forall (i,j)\in\Omega.
\]
The objective is convex and the constraints are **linear**, so CVX/SDP solvers handle it. **Advantages:** no need to fix \(r\) in advance — the rank emerges **adaptively** from the data (the nuclear norm "pushes \(r\) as small as possible" to fit the data). The more observed entries you have, the better constrained the completion is.

More precisely, more observed entries make the completion better constrained. With too few known entries relative to the number of factor parameters, many completions/factorizations can fit the data; regularization or a rank-minimizing objective is then needed to avoid infinitely many plausible solutions.

Either way, once the completed matrix is obtained, you predict each customer's reaction to each movie and recommend accordingly.

---

## Other SVD Applications (Briefly)

The instructor notes there are countless SVD-based algorithms, especially in EE. One named example: **subspace algorithms** for **direction finding** — an array of antennas receives an impinging electromagnetic wave, and you estimate the **angle of arrival**. Subspace methods (built on the SVD of the data) are the key tool. (Skipped for time.)

This concludes the SVD; the lecture turns to **inner product spaces**.

---

## Abstract Inner Product Spaces

Just as a **norm** was added on top of a vector space to measure "how big" a vector is (generalizing the Euclidean norm), an **inner product** can be added to a vector space — and from it a norm is **induced**. Terminology: a complete **normed** space is a **Banach space**; a complete **inner product** space is a **Hilbert space** (a vector space equipped with an inner product, plus a technical completeness condition not dwelt on here — in finite dimensions completeness is automatic).

**Definition.** An inner product \(\langle\cdot,\cdot\rangle: V\times V \to \mathbb{C}\) (or \(\mathbb{R}\)) satisfies the properties the Euclidean inner product has:
1. **Conjugate symmetry:** \(\langle x,y\rangle = \overline{\langle y,x\rangle}\).
2. **Linearity in the first argument:** \(\langle \alpha x, y\rangle = \alpha\langle x,y\rangle\) and \(\langle x+z, y\rangle = \langle x,y\rangle + \langle z,y\rangle\). (Fixing the second argument, it is a **linear** operator — hence "bilinear"/sesquilinear overall; scaling the **second** argument by \(\alpha\) pulls out \(\bar\alpha\).)
3. **Positive definiteness:** \(\langle x,x\rangle \ge 0\), with equality **iff** \(x = 0\).

**Induced norm.** Property 3 makes
\[
\|x\| = \sqrt{\langle x,x\rangle}
\]
a valid norm. So **defining an inner product simultaneously defines a connected norm**, and the **main utility** of inner product spaces is that the inner product is a **tool for solving the norm-minimization (projection / least-squares) problems** — usually yielding **closed-form** solutions.

---

## Four Important Inner Product Spaces

### 1. \(\mathbb{C}^n\) (Euclidean and Weighted)

\[
\langle x,y\rangle = y^* x = \sum_k \bar y_k x_k, \qquad \|x\| = \sqrt{x^*x} = \|x\|_2.
\]
The conjugate is taken on the **second** argument. **Weighted version:** insert a positive definite \(W\),
\[
\langle x,y\rangle_W = y^* W x, \qquad \|x\|_W = \sqrt{x^* W x}.
\]

### 2. \(L^2([a,b])\) (Square-Integrable Functions)

\[
\langle f,g\rangle = \int_a^b f(t)\,\overline{g(t)}\,dt, \qquad \|f\|_{L^2} = \sqrt{\int_a^b |f(t)|^2\,dt}.
\]
**Fourier transform as an inner product:** \(\hat f(\nu) = \int f(t)e^{-j2\pi\nu t}\,dt = \langle f, e^{j2\pi\nu(\cdot)}\rangle\) — the Fourier coefficient at frequency \(\nu\) is the **inner product** of \(f\) with the complex exponential at that frequency. **Orthogonality** of functions: \(\langle f,g\rangle = 0\). A **weighted** version uses a positive weight \(w(t) > 0\): \(\langle f,g\rangle_w = \int f\bar g\, w\, dt\) (weighting each time/frequency differently).

### 3. Matrices (Frobenius Inner Product)

For \(m\times n\) complex matrices,
\[
\langle A,B\rangle = \operatorname{tr}(B^* A) = \operatorname{vec}(B)^* \operatorname{vec}(A) = \sum_{i,j} \bar b_{ij} a_{ij},
\]
i.e. the ordinary complex inner product of the vectorized matrices, where \(\operatorname{vec}(\cdot)\) stacks the matrix columns into one long vector. Induced norm \(= \|A\|_F\). Two matrices are **orthogonal** if \(\operatorname{tr}(B^*A) = 0\). This is how the usual geometric language extends to rectangular complex matrices.

### 4. Random Variables (Correlation as Inner Product)

For zero-mean complex random variables,
\[
\langle X,Y\rangle = \mathbb{E}[X\bar Y] = \operatorname{Corr}(X,Y).
\]
Two random variables are **orthogonal iff uncorrelated**. The induced norm is
\[
\|X\| = \sqrt{\mathbb{E}[|X|^2]} = \text{standard deviation (for zero mean)},
\]
a measure of the random variable's **uncertainty/spread**. The instructor asks for **another** uncertainty measure: **entropy** \(H = -\sum_x p_x \log p_x\) (Shannon entropy). Standard deviation is the right measure for **linear** MMSE estimation; for a **Gaussian**, entropy is essentially \(\log(\text{variance})\), so the two are simply related. (Entropy belongs to information theory, beyond this course.)

This inner product is the **basis of linear stochastic mean-square estimation** — **Wiener** and **Kalman** filters — via the principle "correlation = inner product."

---

## SVD Rank-1 Components Are Orthonormal in the Frobenius Inner Product

The reduced SVD \(A = \sum_{k=1}^r \sigma_k u_k v_k^*\) expresses \(A\) in a basis of rank-1 matrices \(u_k v_k^*\), which are **orthonormal** in the matrix (Frobenius) inner product.

**Proof of orthogonality.** For the inner product of \(u_i v_i^*\) and \(u_j v_j^*\):
\[
\langle u_i v_i^*, u_j v_j^*\rangle = \operatorname{tr}\big((u_j v_j^*)^*(u_i v_i^*)\big) = \operatorname{tr}(v_j u_j^* u_i v_i^*).
\]
Since the left singular vectors are orthonormal, \(u_j^* u_i = \delta_{ij}\), so this is \(\delta_{ij}\operatorname{tr}(v_j v_i^*)\). The trace of the (column)(row) product \(v_j v_i^*\) equals \(v_i^* v_j\) (cycling), which is also \(\delta_{ij}\). Hence
\[
\langle u_i v_i^*, u_j v_j^*\rangle = \delta_{ij}\ (\text{Kronecker delta}).
\]
The instructor paused on the notation: \(\delta_{ij}\) is the **Kronecker delta** - it is \(1\) when \(i=j\) and \(0\) when \(i\ne j\). This follows because the left singular vectors \(u_i\) are columns of a unitary matrix (unit norm and mutually orthogonal), and the same is true for the right singular vectors \(v_i\). The trace step uses \(\operatorname{tr}(AB)=\operatorname{tr}(BA)\); after cycling, the trace of the resulting \(1\times1\) scalar is just that scalar.

**Norm check:** \(\|u_k v_k^*\|_F^2 = \operatorname{tr}(v_k u_k^* u_k v_k^*) = \operatorname{tr}(v_k v_k^*) = v_k^* v_k = 1\). ✓

**Interpretation.** The SVD writes \(A\) as a linear combination of an **orthonormal basis** of rank-1 matrices, with **coordinates** \(\sigma_k = \langle A, u_k v_k^*\rangle\) — the singular value is the projection of \(A\) onto its own \(k\)-th natural basis element. This is the matrix analogue of a Fourier series (orthonormal basis functions, Fourier coefficients). The catch: this orthonormal basis is **adapted to \(A\) itself**.

---

## Orthogonality and Gram–Schmidt in Any Inner Product Space

Once an inner product is fixed, **orthogonality** and **Gram–Schmidt** carry over to **any** vector space — producing an orthonormal basis for the given inner product.

### Legendre Polynomials from Gram–Schmidt on Monomials

Take functions over \([-1,1]\) with \(\langle f,g\rangle = \int_{-1}^1 f(t)g(t)\,dt\). The **monomials** \(g_1 = 1, g_2 = t, g_3 = t^2, \ldots\) span the polynomials but are **not** orthonormal. Gram–Schmidt:

For degree \(n\), \(\operatorname{span}\{g_1,\ldots,g_{n+1}\}\) is the space of polynomials of degree at most \(n\). Gram-Schmidt must preserve that span while replacing the monomials by pairwise orthonormal functions \(h_1,\ldots,h_{n+1}\).

- **\(h_1\):** \(\|1\|^2 = \int_{-1}^1 1\,dt = 2\), so \(h_1 = 1/\sqrt 2\).
- **\(h_2\):** project \(t\) onto \(h_1\): \(\langle t, h_1\rangle = \frac{1}{\sqrt2}\int_{-1}^1 t\,dt = 0\) (odd integrand). So \(t\) is already orthogonal to the constant; normalize: \(\|t\|^2 = \int_{-1}^1 t^2\,dt = \tfrac{2}{3}\), giving \(h_2 = \sqrt{3/2}\,t\).
- **\(h_3\):** project \(t^2\) onto \(h_1\) and \(h_2\). \(\langle t^2, h_2\rangle = 0\) (odd integrand: \(t^2\) and \(t\) are orthogonal), but \(\langle t^2, h_1\rangle \ne 0\) (it gives \(\tfrac{2}{3\sqrt2}\)). Subtract the \(h_1\) component:
\[
v_3 = t^2 - \tfrac{1}{3},
\]
then normalize. (The \(t^2\)-vs-\(1\) inner product \(\int_{-1}^1 t^2\,dt = \tfrac23 \ne 0\) is exactly why the monomials are not orthogonal.)

The resulting (un-normalized) polynomials \(1,\ t,\ t^2 - \tfrac13,\ \ldots\) are the **Legendre polynomials** — an **orthogonal basis** for polynomials on \([-1,1]\). (Different inner products give different families: e.g. a spherical-geometry weight in electromagnetics yields other classical orthogonal polynomials.)

**Why bother?** With an **orthonormal** basis, projecting an arbitrary function \(g\) onto the polynomial subspace (best polynomial approximation of degree \(\le n\)) is just a sum of independent inner products — **no matrix inverse needed** (see the projection theorem below).

If the basis functions are not orthogonal, the closest polynomial is not obtained by projecting onto the monomials one at a time; the coupled Gram-matrix system must be solved instead.

### Innovation Sequence / Kalman Filter Interpretation

In estimation language, the span of measurements is the set of linear functions/linear estimators built from those measurements. Preserving the same span means preserving the same total information while repackaging it into uncorrelated pieces.

In the random-variable inner product space, Gram–Schmidt on correlated observations \(x_1, x_2, \ldots\) produces **uncorrelated** random variables \(q_1, q_2, \ldots\) with the **same span** — the **innovation sequence**. Geometrically, \(q_2\) is the component of \(x_2\) **orthogonal to** \(x_1\): the **new information** in \(x_2\) that **cannot be predicted** from \(x_1\). This is the **prediction interpretation** of projection: projecting \(x_2\) onto \(x_1\) is the best linear **prediction** of \(x_2\) from \(x_1\); the orthogonal remainder is the **prediction error** (the innovation). The **Kalman filter** does exactly this recursively — building an orthonormal basis on the fly as data arrives (assuming a special structure on the observations), so that estimation reduces to projection onto uncorrelated components. (Details belong to an estimation-theory course.)

---

## The Projection Theorem (Climax)

This is the central theorem of inner product spaces — the reason inner products are introduced and the reason orthonormal bases are valuable.

### Statement

Let \(V\) be an inner product space with induced norm \(\|x\| = \sqrt{\langle x,x\rangle}\). Given vectors \(p_1,\ldots,p_n \in V\) (spanning a subspace \(M\)) and a target \(x \in V\) (possibly outside \(M\)), consider the **approximation problem**
\[
\min_{\hat x \in \operatorname{span}\{p_1,\ldots,p_n\}} \|x - \hat x\|.
\]
The norm in this problem is not arbitrary: it is the norm induced by the inner product chosen for the application. That connection is exactly why the inner product can solve the minimization problem.
**Projection theorem:** the minimizer \(\hat x\) is the **orthogonal projection** of \(x\) onto \(M\), characterized by the **orthogonality principle**: the error \(x - \hat x\) is **orthogonal to the entire subspace** \(M\), i.e.
\[
\langle x - \hat x,\ p_i\rangle = 0 \quad \text{for all } i = 1,\ldots,n.
\]
This holds in **any** inner product space — \(x\) and the \(p_i\) could be vectors, **matrices**, **functions** (monomials), or **random variables**.

### Why Orthogonality Is Optimal (Pythagoras)

If the error were **not** orthogonal to \(M\), it would have a nonzero component **inside** \(M\); by the Pythagorean theorem, removing that component would strictly decrease the error. So at the optimum the error must be orthogonal to \(M\).

### Normal Equations and the Gram Matrix

Write the optimal point as a combination of the basis vectors, \(\hat x = \sum_j \alpha_j p_j\) (\(n\) unknown coefficients \(\alpha_j\)). The orthogonality conditions \(\langle x - \hat x, p_i\rangle = 0\) give \(n\) equations:
\[
\langle x, p_i\rangle = \sum_j \alpha_j \langle p_j, p_i\rangle, \qquad i = 1,\ldots,n.
\]
In matrix form \(G\alpha = b\), where \(b_i = \langle x, p_i\rangle\) and
\[
G_{ij} = \langle p_j, p_i\rangle
\]
is the **Gram matrix** of all pairwise inner products of the \(p_i\). Solving this linear system gives the coefficients \(\alpha\).

**Orthonormal simplification.** If \(\{p_i\}\) is **orthonormal**, then \(G = I\), and
\[
\alpha_i = \langle x, p_i\rangle, \qquad \hat x = \sum_i \langle x, p_i\rangle\, p_i.
\]
This is **why** we work so hard (Gram–Schmidt) to get orthonormal bases: projection becomes a set of **independent inner products** — no system to solve. (If merely orthogonal but not normalized, \(G\) is diagonal — still easy.) This is exactly what the Kalman filter exploits: project onto the on-the-fly orthonormal innovation basis.

### Connection to Least Squares

The projection theorem **is** the least-squares solution: given \(Hx = y\) with \(y \notin \mathcal R(H)\) (no exact solution), find the point in the range of \(H\) closest to \(y\) — the orthogonal projection of \(y\) onto \(\mathcal R(H)\). Variations are obtained simply by **changing the inner product**:
- **Weighted least squares** — use a weighted inner product (\(W\)-weighted).
- **Regularized least squares** — another inner-product-space formulation.

All become the same projection problem in the appropriate inner product space. In the transcript these are named as post-theorem applications rather than fully developed lecture material.

---

## Exam Boundary and Further Reading

The instructor states the exam covers **everything through the projection theorem, inclusive**; material after it (detailed least-squares applications, weighted/regularized least squares as projection, estimation-theory applications, state-space notes) is **not** on the exam but is highly recommended. He specifically recommends the supplementary notes on **estimation of a random variable from multiple observations** (LMMSE), **polynomial approximation**, and **state-space representations** (a current hot topic in machine learning), building on the matrix background from this course.

---

## Summary: Inner Products Unify the Geometry

| Concept | In \(\mathbb{C}^n\) | In a general inner product space |
|---|---|---|
| Inner product | \(y^*x\) | \(\langle x,y\rangle\) (space-specific) |
| Norm | \(\|x\|_2 = \sqrt{x^*x}\) | \(\|x\| = \sqrt{\langle x,x\rangle}\) |
| Orthogonality | \(x^*y = 0\) | \(\langle x,y\rangle = 0\) |
| Projection (ONB) | \(\hat x = \sum_k (q_k^*x) q_k\) | \(\hat x = \sum_k \langle x,q_k\rangle q_k\) |
| Projection (general) | normal equations \(A^*A\) | Gram-matrix system \(G\alpha = b\) |
| Gram–Schmidt | orthonormalize vectors | orthonormalize any elements |

The price of the generalization: verify the inner-product axioms for each specific space.

---

## Instructor Remarks and Study Guidance

- **Schatten norms** unify the three main matrix norms: nuclear (\(p=1\)), Frobenius (\(p=2\)), operator (\(p=\infty\)); all are functions of the singular values.
- **Nuclear norm** = convex relaxation of **rank** (the low-rank analog of \(\ell_1\) sparsity). It powers **matrix completion** / the **Netflix challenge** (low-rank \(CM\) factorization won; nuclear-norm minimization is the convex, rank-adaptive alternative).
- **Inner products generalize all linear-algebra geometry** to functions, matrices, and random variables. **Correlation = inner product** (uncorrelated = orthogonal, std-dev = norm) makes Wiener/Kalman filtering a projection problem.
- The **SVD rank-1 components are orthonormal** in the Frobenius inner product; \(\sigma_k\) is the matrix's coordinate along its own natural basis.
- **Gram–Schmidt** in \(L^2([-1,1])\) on monomials yields the **Legendre polynomials**; on random variables it yields the **innovation sequence** (new, unpredictable information = orthogonal component).
- **Projection theorem (exam climax):** the closest point in a subspace makes the **error orthogonal to the subspace**; this gives the **Gram-matrix normal equations** \(G\alpha = b\), which collapse to independent inner products when the basis is **orthonormal**. Least squares (and its weighted/regularized variants) are special cases obtained by choosing the inner product.
- **Exam covers through the projection theorem, inclusive.** Read the supplementary LMMSE, polynomial-approximation, and state-space notes for going further.

## Source and Coverage Note

Source: `corrected/lecture23_corrected.md`.

Audit patch addendum: Added transcript-specific details on the informal Netflix matrix setup and held-out ratings; observed-entry/regularization caveats; matrix vectorization as column stacking; the Kronecker-delta and trace-cycling clarification in the SVD orthonormality proof; same-span requirements for Gram-Schmidt on degree-\(n\) polynomials; why non-orthogonal monomials require a coupled projection solve; measurement-span/linear-estimator interpretation for innovation sequences; the induced-norm requirement in the projection theorem; and the optional status of post-theorem least-squares variants.

Coverage: Schatten \(p\)-norms (definition; nuclear/Frobenius/operator special cases; \(p=\infty\) = \(\sigma_1\) = induced 2-2 origin of SVD); nuclear/trace norm as \(\ell_1\) of singular values and convex relaxation of rank; matrix completion / Netflix challenge (customer×movie matrix, low-rank \(CM\) feature factorization with inner-product scores, fixed-rank Frobenius approach with \(r(m+n)\) unknowns and regularization, nuclear-norm convex/rank-adaptive approach, \$1M prize/history); other SVD applications (direction finding / subspace algorithms); abstract inner product spaces (Banach vs Hilbert, axioms, induced norm, utility for projection/least-squares); four examples (\(\mathbb{C}^n\) Euclidean and weighted; \(L^2[a,b]\) with Fourier transform as inner product and weighted version; matrices/Frobenius inner product; random variables/correlation with std-dev as norm and the entropy aside); SVD rank-1 components orthonormal in Frobenius inner product (full trace proof and norm check, singular value as coordinate); Gram–Schmidt in inner product spaces — Legendre polynomials (\(h_1, h_2, v_3 = t^2-\tfrac13\) steps, why monomials aren't orthogonal, other polynomial families) and the innovation-sequence/Kalman prediction interpretation; the **projection theorem** (statement, orthogonality principle, Pythagoras intuition, Gram-matrix normal equations \(G\alpha=b\), orthonormal simplification, least-squares/weighted/regularized connection); exam boundary (through projection theorem inclusive) and recommended further reading; unification table.
