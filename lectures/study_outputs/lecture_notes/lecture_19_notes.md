# Lecture 19 Notes

## Recap: Norms and the \(p\)-Norm Family

The lecture continues the normed-spaces topic. Recap from last time: if you are constrained to a rectangular grid (no diagonal moves), the distance to a point is the **absolute sum** of its components — the **one-norm**, also called the **taxicab** or **Manhattan** norm. It is one alternative to the Euclidean norm and, as the homework will show, a very powerful norm for **sparsity** applications.

### Norm Axioms (Review)

A **norm** maps the set of vectors to the reals and must satisfy:

1. **Non-negativity:** \(\|x\| \ge 0\) (it measures "bigness").
2. **Definiteness:** \(\|x\| = 0 \iff x = 0\) (only the origin has zero norm).
3. **Homogeneity:** \(\|\alpha x\| = |\alpha|\,\|x\|\) (scaling scales the norm by the **absolute value** of the scalar).
4. **Triangle inequality:** \(\|x + y\| \le \|x\| + \|y\|\) (the third side of a triangle is bounded by the sum of the other two).

### The Standing (Euclidean) Norm on \(\mathbb{C}^n\)

For complex vectors, the **Euclidean norm** is
\[
\|x\|_2 = \Big(\sum_k |x_k|^2\Big)^{1/2} = \sqrt{x^* x}.
\]
(The conjugate transpose handles complex entries.) The **one-norm** is the sum of absolute values, \(\|x\|_1 = \sum_k |x_k|\); minimizing it tends to produce **sparse** vectors (most entries zero, a few nonzero). Both are members of the **\(p\)-norm (\(L^p\)) family**:
\[
\|x\|_p = \Big(\sum_k |x_k|^p\Big)^{1/p}, \qquad p \ge 1.
\]
- \(p = 1\): taxicab / Manhattan norm.
- \(p = 2\): Euclidean norm. (You could name the \(p=3\) norm yourself — there is no standard name.)
- \(p \to \infty\): taking the limit picks out the **maximum absolute element**:
\[
\|x\|_\infty = \max_k |x_k|.
\]

**Worked values for \(x = (3, -4)\):** \(\|x\|_1 = 3 + 4 = 7\), \(\|x\|_2 = 5\), \(\|x\|_\infty = 4\) (the peak magnitude). **As \(p\) increases, the norm decreases** — not a coincidence but a general property.

### Why \(\ell_\infty\) Matters: Worst-Case / Minimax

If \(x\) is an **error vector**, the \(\infty\)-norm is the **maximum error**. Designing for robustness — minimizing the **worst** error — means minimizing \(\|e\|_\infty\), a **minimax** optimization.

---

## Application: FIR Filter Design

A clean application illustrating the three norms is **FIR filter design** in the frequency domain.

### Setup

On the (positive) frequency axis, suppose we want a **low-pass filter**: desired response \(= 1\) in the passband and \(= 0\) in the stopband. Sample the frequency axis at \(f\) points (e.g., 2000 samples) to get the **desired vector**
\[
h_d = (\,\underbrace{1,1,\ldots,1}_{\text{passband}},\ \underbrace{0,0,\ldots,0}_{\text{stopband}}\,)^\top \in \mathbb{C}^f.
\]
A **realizable** FIR filter has a finite impulse response with \(r\) coefficients \(c\); its frequency response is the Fourier transform of \(c\), written as a matrix product \(h = Fc\) (\(F\) the \(f\times r\) Fourier matrix). The realized response will **not** be perfectly flat — it ripples — so there is an **error vector**
\[
e = h_d - Fc.
\]

### Choice of Norm = Design Criterion

\[
\min_{c}\ \|h_d - Fc\|_p,
\]
and different \(p\) give different filters:

- **\(\ell_2\) → least squares.** \(\min_c \|h_d - Fc\|_2\) has a **closed-form algebraic solution** via the pseudoinverse, \(\hat c = (F^*F)^{-1}F^* h_d\). Easy.
- **\(\ell_\infty\) → equiripple / minimax.** \(\min_c \|h_d - Fc\|_\infty\) minimizes the worst-case deviation. **No formula** — needs an iterative algorithm. MATLAB's **`firpm`** (Finite Impulse Response **Parks–McClellan**, "pm") implements this minimax criterion. (A student asked which MATLAB filter-design command applies; the instructor distinguished special-purpose commands from `firpm`, the general minimax designer.)
- **\(\ell_1\) → robust.** \(\min_c \|h_d - Fc\|_1\) minimizes total absolute error; no formula, solvable as an LP / via CVX.

**The instructor's point:** there is **no universal "best" norm** — it depends on the application and which kind of error matters. "Each norm is easy to solve" only for \(\ell_2\) (closed form); the others need iteration.

### Convexity and Why It Helps

A **convex function** is one where the chord joining any two points on the graph lies **above** the function, and which has **no spurious local minima**. All \(p\)-norms (\(p \ge 1\)) are convex. Minimizing a convex function over a convex search space is **tractable**, even when iterative: tools like **CVX** solve it directly (you state the problem, get the answer), though you don't get a closed-form formula for \(\ell_1\)/\(\ell_\infty\). The instructor flags CVX as a tool students will use in the next homework.

### Linear-Programming Formulation of \(\ell_\infty\) (and \(\ell_1\))

\(\ell_\infty\) and \(\ell_1\) minimization can be cast as **linear programs (LP)** — a special class of convex optimization (an entire industrial-engineering course). The general LP form is
\[
\min_x\ c^\top x \quad \text{s.t.}\quad Ax \le b \ (\text{or } \ge),
\]
minimizing the **inner product** \(c^\top x\) over a **polyhedral region**.

**\(\ell_\infty\) trick.** Introduce a scalar upper bound \(t\) on the peak magnitude. Since \(|e_k| \le t \iff -t \le e_k \le t\):
\[
\min_{c,t}\ t \quad\text{s.t.}\quad Fc - h_d \le t\mathbf{1}, \ \ -(Fc - h_d) \le t\mathbf{1}.
\]
Stacking \(F\) and \(-F\) (with \(\mp\mathbf 1\) columns for \(t\)) puts it into the standard LP inequality form, and the objective is the inner product picking out \(t\). At the optimum, \(t\) equals the maximum absolute element of the error. So **\(\ell_\infty\) minimization = LP**; a similar trick handles **\(\ell_1\)**. You don't *need* the LP form (CVX's general convex solver works), but historically people were excited to discover \(\ell_1\)/\(\ell_\infty\) reduce to LP.

For a general \(p\)-norm objective such as \(p=3\), the LP trick no longer applies, but the problem is still convex as long as \(p \ge 1\). In that case the general convex-optimization route (for example CVX) is the natural tool.

---

## Weighted \(\ell_2\)-Norms

Beyond the \(p\)-norm family, another way to measure size is a **weighted** norm.

### Diagonal Weighting

For a diagonal **positive** matrix \(D = \text{diag}(d_1,\ldots,d_n)\), \(d_k > 0\):
\[
\|x\|_D = \sqrt{x^* D x} = \Big(\sum_k d_k |x_k|^2\Big)^{1/2}.
\]
Each coordinate's squared magnitude carries a **weight** \(d_k\). This is useful when not all components are equally significant. **In filter design**, for instance, you weight the **stopband** much more than the passband (e.g., \(10{,}000\) vs. \(1\)): on the dB scale a given error in the suppression band makes a "lousy filter," so you prioritize stopband suppression over passband flatness.

**Why the weights must be strictly positive.** If some \(d_k = 0\), then the nonzero vector \(e_k\) has \(\|e_k\|_D = 0\), violating definiteness. (Positive **semi**definite is not enough.)

### General Positive-Definite Weighting (Student Q&A)

Replace \(D\) by any positive definite matrix \(W\):
\[
\|x\|_W = \sqrt{x^* W x}.
\]
The instructor asks the class what \(W\) does **geometrically** when it is not diagonal. Through guided Q&A:
- A student guesses a **correlation** connection — the instructor agrees \(W\) is often a **correlation matrix** (in fact the **inverse** correlation appears naturally in applications).
- Another student suggests **projecting \(x\) onto eigenvector directions** — "Exactly."

**Derivation.** Since \(W\) is Hermitian PD, it is unitarily diagonalizable: \(W = U\Lambda U^*\) with positive eigenvalues. Then
\[
x^* W x = x^* U \Lambda U^* x = (U^* x)^* \Lambda (U^* x) = \sum_k \lambda_k |z_k|^2, \qquad z = U^* x.
\]
Here \(z_k = u_k^* x\) is the **projection of \(x\) onto eigenvector \(u_k\)** (its coordinate in the eigenbasis). So:

> Instead of weighting the **coordinate axes** (the diagonal case), a general \(W\) weights the **eigenvector directions** of \(W\): you change basis to the eigenvectors \(u_1, u_2, \ldots\), and the eigenvalues \(\lambda_1, \lambda_2, \ldots\) become the weights along those (possibly rotated) directions.

Geometrically: drop the projections \(z_1 = u_1^* x\), \(z_2 = u_2^* x\) onto the eigenvectors; each squared projection is scaled by its eigenvalue.

---

## Weighted \(\ell_2\)-Norm in Statistics: the Multivariate Gaussian

The PD-weighted 2-norm appears naturally in statistical estimation (the subject of a 530-type course; here just the connection).

### Scalar and Independent Gaussians

A single Gaussian has density \(\propto \exp\!\big(-\frac{(x-\mu)^2}{2\sigma^2}\big)\) — a bell curve centered at \(\mu\), with \(\sigma\) controlling width. For **jointly Gaussian** random variables, the instructor notes a special fact: if they are uncorrelated, then they are independent. That implication is **not true for arbitrary random variables**.

For two independent zero-mean Gaussians with variances \(\sigma_1^2\) and \(\sigma_2^2\), the joint density is the product of marginals:
\[
p(x_1,x_2) \propto \frac{1}{2\pi\sigma_1\sigma_2}
\exp\!\Big(-\frac{1}{2}\Big(\frac{x_1^2}{\sigma_1^2}+\frac{x_2^2}{\sigma_2^2}\Big)\Big).
\]
If the variances are equal, \(\sigma_1=\sigma_2=\sigma\), this simplifies to
\[
p(x_1,x_2) \propto \exp\!\Big(-\frac{x_1^2 + x_2^2}{2\sigma^2}\Big) = \exp\!\Big(-\frac{\|x\|_2^2}{2\sigma^2}\Big).
\]
So for **uncorrelated, equal-variance** Gaussians the ordinary **2-norm squared** appears in the exponent.

### Correlated Gaussians → Weighted 2-Norm

When the components are **correlated**, you need the covariance matrix \(\Sigma\), and the joint density becomes
\[
p(x) = \frac{1}{(2\pi)^{n/2}\sqrt{\det \Sigma}}\ \exp\!\Big(-\tfrac{1}{2}\, x^\top \Sigma^{-1} x\Big).
\]
The exponent is a **weighted 2-norm squared** with weight \(W = \Sigma^{-1}\), the **precision (inverse covariance) matrix**. So the PD-weighted norm sits "at the top of the Gaussian," with the inverse covariance as the weight.

### Maximum Likelihood = Weighted Least Squares

Maximizing the Gaussian likelihood means **minimizing** the (negated) exponent \(\frac{1}{2}x^\top \Sigma^{-1} x\) — a **weighted least squares** problem. The weighting along eigen-directions interpretation applies: directions of large variance (large eigenvalues of \(\Sigma\)) get small precision weight, so they are penalized less.

---

## \(L^p\) Norms for Function Spaces

Norms are not restricted to \(n\)-dimensional vectors. For appropriately integrable functions on an interval \([a,b]\), define the **\(L^p\) norm**:
\[
\|f\|_{L^p} = \Big(\int_a^b |f(t)|^p\, dt\Big)^{1/p}.
\]
Think of \(f(t)\) as a "vector" with **uncountably many** entries (one per \(t\)); the integral replaces the sum. This lets us measure **how big a function is** and the **distance between two functions** \(\|f - g\|_{L^p}\) — treating each function as a **point** in an infinite-dimensional space.

### Polynomial Approximation

Approximate an arbitrary target function \(g(t)\) by a polynomial \(f(t) = a + bt + ct^2\). The polynomial can only take certain shapes, so it deviates from \(g\) at various points (big error here, zero there). To measure performance with a **single number**, define the error function \(e(t) = g(t) - f(t)\) and minimize a norm of it:
\[
\min_{a,b,c}\ \|g - f\|_{L^p}.
\]
- \(p = 2\): minimize total squared error (closed-form via inner products with the polynomial basis).
- \(p = \infty\): minimize the worst-case pointwise deviation (Chebyshev / equiripple approximation).

The big idea: **norms let us carry two- and three-dimensional geometric intuition (distance, closeness, projection) into high- and infinite-dimensional problems.** The instructor cautions, however, that geometric intuition from 2-D/3-D can sometimes **fail** in high dimensions — "there are surprises in high dimensions."

---

## Norm Balls (Geometric Understanding)

Before matrix norms, the instructor develops **norm balls**, which give geometric insight — especially into the \(\ell_1\)-sparsity connection. The **unit \(\ell_p\)-ball** is the region of all vectors with \(\|x\|_p \le 1\) (the boundary is where \(\|x\|_p = 1\); "unit" is dropped for brevity).

### The \(\ell_1\) Ball in 2-D (Quadrant-by-Quadrant)

We need \(|x_1| + |x_2| \le 1\). The sign of each term changes by quadrant:
- **First quadrant** (\(x_1, x_2 > 0\)): \(x_1 + x_2 \le 1\). The boundary \(x_1 + x_2 = 1\) is a line; \(x_1 + x_2 = 0.9, 0.8, \ldots\) are parallel lines; the region is the triangle below \(x_1 + x_2 = 1\).
- **Second quadrant** (\(x_1 < 0, x_2 > 0\)): \(-x_1 + x_2 \le 1\), another line, another triangle.
- Continuing through the third and fourth quadrants gives four triangular pieces that assemble into a **diamond** (a rotated square) with corners at \((\pm1, 0)\) and \((0, \pm1)\).

So the **\(\ell_1\) ball is a diamond** — "this is a new geometry; your ball is no longer the round thing."

### The \(\ell_2\) and \(\ell_\infty\) Balls in 2-D

- **\(\ell_2\):** \(x_1^2 + x_2^2 \le 1\) is the familiar **circular** disk.
- **\(\ell_\infty\):** \(\max(|x_1|, |x_2|) \le 1\) means **both** \(|x_1| \le 1\) and \(|x_2| \le 1\) — a **square** (axis-aligned, **not** tilted) with corners at \((\pm1, \pm1)\). On the right edge \(x_1 = 1\) (with \(|x_2| \le 1\)), the peak value is \(1\); inside, both coordinates are \(< 1\).

### Nesting Comparison

Overlaying the three: the **\(\ell_1\) diamond is inside the \(\ell_2\) circle, which is inside the \(\ell_\infty\) square.** This visualizes \(\|x\|_\infty \le \|x\|_2 \le \|x\|_1\):
- A point with \(\|x\|_1 > 1\) but \(\|x\|_2 \le 1\) sits **outside** the diamond but **inside** the circle (and square).
- A point with \(\|x\|_1, \|x\|_2 > 1\) but \(\|x\|_\infty \le 1\) sits outside both the diamond and circle but inside the square.

### The 3-D Balls and "Orthant" Terminology

In \(\mathbb{R}^3\):
- **\(\ell_2\) ball:** \(x_1^2 + x_2^2 + x_3^2 \le 1\) — a **sphere** (solid spherical region) around the origin.
- **\(\ell_\infty\) ball:** \(\max(|x_1|,|x_2|,|x_3|) \le 1\) — a **cube**.
- **\(\ell_1\) ball:** \(|x_1| + |x_2| + |x_3| \le 1\) — an **octahedron**.

For the \(\ell_1\) ball, in the all-positive region the boundary \(x_1 + x_2 + x_3 = 1\) is a **hyperplane** — note \(x_1 + x_2 + x_3 = \langle x, \mathbf{1}\rangle = 1\), a plane orthogonal to \(\mathbf 1\), shifted off the origin (since the right side is \(1\)). Each of the \(2^n\) sign regions contributes a triangular face, giving the octahedron.

**Terminology Q&A.** Students try to name the \(n\)-dimensional generalization of "quadrant." In 2-D the axes divide the plane into **4** regions (quadrants); in 3-D into **8** regions; in \(n\)-D into \(2^n\) regions. The general name (after some back-and-forth) is **orthant** — each orthant being where all components have fixed signs.

---

## Application: Overdetermined Systems and Norms

One of the most useful parts of the course: using norms to solve linear systems.

### Overdetermined (Tall) Systems

An **overdetermined** system has **more equations than unknowns** — \(A\) is a **tall** matrix. The potential problem: the column space (range) of \(A\) does **not** cover the whole target space, so if \(b\) is **not** in the range of \(A\) there is **no solution** (the system is **inconsistent**). A "lazy researcher" stops there — but we don't.

### Closest Point in the Range

Instead, find the point \(\hat b = A x^\star\) in the range of \(A\) that is **as close as possible to \(b\)**, minimizing the **norm** of the error \(b - Ax\). But "close" requires a choice of norm:
\[
\min_x\ \|b - Ax\|.
\]

### The \(\ell_2\) Case Has a Formula

If we use the **2-norm** (and \(A\) is full rank), the solution is the **orthogonal projection** of \(b\) onto the range of \(A\) with respect to the Euclidean inner product. Recalling the projection formula for a non-orthonormal basis,
\[
\hat b = A (A^* A)^{-1} A^* b,
\]
and the multiplier of \(A\) is the solution
\[
\boxed{x^\star = (A^* A)^{-1} A^* b.}
\]
This closed-form formula is **why people gravitate to the 2-norm**: no iterative algorithm needed. (For \(\ell_1\)/\(\ell_\infty\) there is no such formula — use CVX or LP.)

For \(\ell_1\) and \(\ell_\infty\), the same LP reductions discussed earlier can be used; for a general \(p\)-norm residual, CVX can still solve the convex problem when \(p \ge 1\), but it will not usually be a linear program.

### Why the 2-Norm Has a Formula but \(\ell_1\)/\(\ell_\infty\) Don't

The 2-norm is **associated with an inner product**: \(\langle x, y\rangle = y^\top x\) (real case), and \(\|x\|_2 = \sqrt{\langle x, x\rangle}\). That inner-product structure is what yields the orthogonal-projection solution. The \(\ell_1\) and \(\ell_\infty\) norms have **no associated inner product** — you cannot write them as \(\sqrt{\langle x, x\rangle}\) — so the projection machinery does not apply, and you must optimize numerically. (Inner-product norms will be developed in the inner-product lectures.)

### Statistical Justification: Gaussian Noise → Least Squares

The 2-norm criterion is also **statistically optimal** under a Gaussian-noise model. Suppose the measurement is
\[
b = Ax + n,
\]
with \(n\) Gaussian noise. If \(n\) is **white** (covariance \(= \sigma^2 I\)), the **maximum-likelihood** estimate minimizes \(\|b - Ax\|_2^2\) — exactly **least squares** (the \(\sigma^2\) scales out). This is why minimizing the sum of squared errors is "justified": \(b\) was really in the range, and only Gaussian noise pushed it out.

### Correlated Noise → Weighted Least Squares

If the noise is **correlated** with covariance \(\Sigma\), the ML estimate uses the **weighted** norm with \(W = \Sigma^{-1}\):
\[
\min_x\ \|b - Ax\|_{\Sigma^{-1}}^2 = \min_x\ (b - Ax)^\top \Sigma^{-1} (b - Ax).
\]
For uncorrelated noise \(\Sigma = \sigma^2 I\) this collapses back to ordinary least squares because the scalar \(\sigma^2\) only rescales the objective. With known noise statistics you insert \(\Sigma^{-1}\) as the weight; this again weights the eigen-directions of \(\Sigma\) by the inverse eigenvalues. (For non-full-rank \(A\), additional tricks are needed — deferred to later lectures.)

---

## Instructor Remarks and Study Guidance

- **No universally best norm** — the norm encodes which error you care about: \(\ell_1\) (total absolute, robust, sparsity-promoting), \(\ell_2\) (total squared, smooth, closed-form), \(\ell_\infty\) (worst-case, equiripple, minimax).
- **As \(p\) grows the norm shrinks**: \(\|x\|_\infty \le \|x\|_2 \le \|x\|_1\). Norm balls: \(\ell_1\) **diamond** ⊂ \(\ell_2\) **circle** ⊂ \(\ell_\infty\) **square** (sphere/cube/octahedron in 3-D). The \(n\)-D sign regions are **orthants** (\(2^n\) of them).
- **Convexity** (\(p \ge 1\)) makes all these minimizations tractable; \(\ell_1\) and \(\ell_\infty\) further reduce to **linear programs**; use **CVX** for general convex \(p\), including cases such as \(p=3\) that are not LPs. CVX is explicitly tied to the next homework.
- **Weighted \(\ell_2\)** with PD weight \(W\) weights the **eigenvector directions** of \(W\) by its eigenvalues. It is the natural norm for **multivariate Gaussian** estimation, with weight \(=\) precision matrix \(\Sigma^{-1}\).
- **The 2-norm is special** because it comes from an **inner product**, giving the closed-form least-squares / orthogonal-projection solution \(x^\star = (A^*A)^{-1}A^*b\). \(\ell_1\) and \(\ell_\infty\) have no associated inner product.
- **Least squares is ML estimation** under white Gaussian noise; correlated noise gives **weighted** least squares with \(\Sigma^{-1}\).

## Source and Coverage Note

Source: `corrected/lecture19_corrected.md`.

Coverage: Recap of norm axioms and the \(p\)-norm family (\(\ell_1\)/\(\ell_2\)/\(\ell_\infty\), worked \((3,-4)\) values, monotonicity in \(p\)); \(\ell_\infty\) as worst-case/minimax; FIR filter design (low-pass desired vector, \(h = Fc\), error vector, three criteria — \(\ell_2\) least-squares closed form, \(\ell_\infty\) `firpm`/Parks–McClellan equiripple, \(\ell_1\) robust — with the filter-command Q&A); convex-function definition; LP formulation of \(\ell_\infty\) (scalar bound \(t\), polyhedral region, inner-product objective) and the \(\ell_1\) analog; weighted \(\ell_2\)-norm (diagonal weighting with filter-design stopband example, strict-positivity requirement, general PD \(W\) with the correlation/eigenvector student Q&A and eigen-decomposition derivation); multivariate Gaussian (scalar/independent → 2-norm, correlated → weighted 2-norm with precision matrix, MLE = weighted least squares); \(L^p\) function-space norms and polynomial approximation; detailed norm-ball geometry (quadrant-by-quadrant \(\ell_1\) diamond, \(\ell_2\) circle, \(\ell_\infty\) square, nesting comparison, 3-D sphere/cube/octahedron, hyperplane faces, orthant terminology Q&A); overdetermined systems and norms (tall/inconsistent, closest point, \(\ell_2\) projection formula \(x^\star=(A^*A)^{-1}A^*b\), 2-norm↔inner-product connection and why \(\ell_1\)/\(\ell_\infty\) lack one, Gaussian-noise/MLE justification, correlated-noise weighted least squares).
