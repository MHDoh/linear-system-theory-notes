# Lecture 15 Notes

## Opening Review: Story Line Summary

The lecture begins with the instructor placing the current work inside the course narrative.

The course has been building toward solving \(Ax=b\) efficiently by writing \(A\) as a product of simple matrices. The full hierarchy covered so far:

- All square matrices can be triangularized using a unitary basis: **Schur factorization** \(A = UTU^*\), where \(U\) is unitary and \(T\) is upper triangular.
- When \(T\) is diagonal, we have **unitary diagonalization** \(A = U\Lambda U^*\). Matrices that can be diagonalized this way are the **normal matrices** (\(A^*A = AA^*\)).
- Within normal matrices, **Hermitian** matrices (\(A^* = A\)) have real eigenvalues, and **unitary** matrices (\(U^*U = I\)) have eigenvalues on the unit circle.
- Within Hermitian matrices, the sign of eigenvalues determines the class: positive definite, positive semidefinite, negative definite, negative semidefinite, or indefinite.

The instructor then reviews properties of positive definite matrices established in the previous lecture:

1. Positive linear combinations with positive scalar weights: \(\sum c_i A_i\) is positive definite if each \(A_i\) is PD and each \(c_i > 0\).
2. Diagonal entries of a PD matrix are positive (proved by setting \(x = e_i\)).
3. **Principal submatrix property:** If \(A\) is PD and we select a submatrix using the same row and column indices \(I\) (e.g., rows/columns 1, 3, 5), that submatrix is also PD. Proof: choose a vector \(x\) that is zero outside index set \(I\); then \(x^*Ax > 0\) restricts to the submatrix.
4. **Star-congruence:** \(A = SBS^*\) for invertible \(S\) preserves inertia (the sign pattern of eigenvalues). This is Sylvester's law: star-congruent Hermitian matrices have the same inertia.
5. The identity matrix has inertia \((n,0,0)\). Any PD matrix also has inertia \((n,0,0)\). Therefore any PD matrix is star-congruent to the identity, meaning it can be written \(A = SS^*\) for some invertible \(S\). The instructor calls \(S\) a **matrix square root** of \(A\).
6. There are infinitely many matrix square roots: if \(S\) works, so does \(ST\) for any unitary \(T\), because \((ST)(ST)^* = S(TT^*)S^* = SS^* = A\).
7. The **positive definite square root** is \(A^{1/2} = U\Lambda^{1/2}U^*\) where \(A = U\Lambda U^*\).
8. The **lower triangular square root** exists by Cholesky factorization (the focus of this lecture).

The instructor pauses to clarify notation in this review. The principal submatrix statement is about selecting the same indexed rows and columns from one matrix. The positive linear combination statement is different: \(A_1,A_2,A_3,\ldots\) are separate positive definite matrices, and the coefficients \(c_i\) are arbitrary positive scalars. The index \(i\) in the sum is not the same as the row/column index set \(I\).

---

## Cholesky Proof Completion

The Cholesky proof started in L14 and was left at a critical point. The instructor resumes.

### Recap of Where We Were

Partition positive definite \(A\) as:

\[
A = \begin{bmatrix} \alpha & v^* \\ v & M \end{bmatrix},
\]

where:
- \(\alpha > 0\) (proved in L14 by setting \(x = e_1\) in \(x^*Ax > 0\)).
- \(M\) is \((n-1)\times(n-1)\) PD (proved by setting the first entry of \(x\) to zero).

Block Gaussian elimination by left-multiplying by the lower triangular matrix:

\[
S = \begin{bmatrix} 1 & 0 \\ -v/\alpha & I \end{bmatrix}
\]

and right-multiplying by \(S^*\) (conjugate transpose):

\[
S A S^* = \begin{bmatrix} \alpha & 0 \\ 0 & M - \frac{vv^*}{\alpha} \end{bmatrix}.
\]

The lower-right block \(M - vv^*/\alpha\) is the **Schur complement** of \(\alpha\).

### Why the Schur Complement Is Positive Definite

The critical question: is \(M - vv^*/\alpha\) positive definite?

At first glance this is not obvious. We know \(M\) is PD and \(vv^*/\alpha\) is positive semidefinite (it is a scaled outer product). Subtracting a PSD matrix from a PD matrix does not automatically give a PD matrix — the subtracted piece could be large enough to destroy positive definiteness.

The instructor also notes the outer-product intuition: for nonzero \(v\), \(vv^*\) is rank one and its nonzero eigenvalue is \(\|v\|^2\). That still does not make the subtraction safe.

The argument that resolves this is **star-congruence**:

1. \(S\) is invertible (it is lower triangular with ones on the diagonal, so \(\det(S)=1\ne0\)).
2. \(SAS^*\) is star-congruent to \(A\).
3. \(A\) is PD, so \(\text{inertia}(A) = (n,0,0)\).
4. Star-congruence preserves inertia.
5. Therefore \(SAS^*\) also has inertia \((n,0,0)\), i.e., it is PD.
6. The block diagonal matrix is PD iff each diagonal block is PD.
7. The upper-left block is \(\alpha > 0\) (positive definite, trivially).
8. Therefore the lower-right block \(M - vv^*/\alpha\) must also be PD.

**Instructor emphasis:** This is the right way to see it. Trying to prove positivity of the Schur complement directly from the expression \(M - vv^*/\alpha\) is harder. The star-congruence argument is clean and powerful.

### Inductive/Recursive Step

Once we know the Schur complement \(M - vv^*/\alpha\) is PD and \((n-1)\times(n-1)\), we can apply the same partition-and-eliminate procedure to it. Two equivalent ways to continue:

**Recursive approach:** Apply block diagonalization to the Schur complement block, and then again to its Schur complement, and so on. After \(n\) steps, the original PD matrix has been converted to a diagonal matrix with all positive diagonal entries, through star-congruent transformations.

**Inductive approach:** Assume Cholesky factorization holds for \((n-1)\times(n-1)\) PD matrices (base case \(n=1\) is trivial: the Cholesky factor of \(\alpha>0\) is \(\sqrt{\alpha}\)). Then apply it to the Schur complement: \(M - vv^*/\alpha = L_{n-1}L_{n-1}^*\). Reconstruct:

\[
SAS^* = \begin{bmatrix} \alpha & 0 \\ 0 & L_{n-1}L_{n-1}^* \end{bmatrix} = \underbrace{\begin{bmatrix}\sqrt{\alpha}&0\\0&L_{n-1}\end{bmatrix}}_{L_{\text{new}}}\underbrace{\begin{bmatrix}\sqrt{\alpha}&0\\0&L_{n-1}^*\end{bmatrix}}_{L_{\text{new}}^*}.
\]

Since \(A = S^{-1}(L_{\text{new}}L_{\text{new}}^*)(S^*)^{-1}\), and multiplying through the triangular factors of \(S^{-1}\) and \(L_{\text{new}}\) gives a lower triangular product, we recover \(A = LL^*\) for a lower triangular \(L\). The positive diagonal entries of \(L\) come from the square roots of positive pivots at each recursive step.

### What Cholesky Is Not

The instructor notes the connection to Gaussian elimination: when Gaussian elimination is applied to a PD matrix, the LDU factorization has positive diagonal entries in \(D\), and the Cholesky factorization is essentially combining \(L\) and \(D^{1/2}\) into the Cholesky factor.

---

## Application of Cholesky: Solving Positive Definite Systems

Suppose \(Px = y\) where \(P\) is positive definite.

**Strategy using Cholesky:**

1. Factor \(P = LL^*\) (Cholesky factorization, computed once).
2. The system becomes \(LL^*x = y\).
3. Set \(z = L^*x\). Then \(Lz = y\): a lower triangular system, solved by **forward substitution**.
4. Once \(z\) is known, solve \(L^*x = z\): an upper triangular system, solved by **back substitution**.

Two simple triangular system solves instead of one expensive inversion.

### Application to Causal Estimators

The instructor mentions another important use of the lower triangular Cholesky factor that connects to systems theory.

A lower triangular matrix corresponds to a **causal linear system**: the output at time \(n\) depends only on inputs at times \(\le n\). This is the linear systems interpretation of lower triangularity.

In estimation theory, when the observation covariance matrix must be factored, using the Cholesky factor (lower triangular) gives a **causal Wiener filter** — a causal linear estimator. The non-causal Wiener filter uses the full matrix; the causal version requires the Cholesky factorization. This is mentioned as a topic from a separate estimation theory course; the lecture does not go into details.

---

## The Least Squares Problem

The instructor now asks: in practice, when does a positive definite system arise?

### Setup

Consider \(Ax = b\) where:
- \(A\) is \(m\times n\) with \(m > n\) (tall matrix, more equations than unknowns).
- \(A\) has full column rank (\(\text{rank}(A) = n\)).

**What is the problem?**

- Null space of \(A\) is trivial (full column rank), so uniqueness is guaranteed if a solution exists.
- However, the column space of \(A\) is an \(n\)-dimensional subspace of \(\mathbb{R}^m\). Since \(n < m\), not every \(b \in \mathbb{R}^m\) lies in \(\mathcal{R}(A)\).
- In practice, \(b\) may be a noisy measurement that doesn't exactly lie in the column space of \(A\).

**The instructor's attitude:** Instead of giving up when \(b \notin \mathcal{R}(A)\), "blame it on \(b\)." Assume the noise in \(b\) has pushed it out of the column space. Find the nearest vector \(\hat{b}\) inside the column space, and use that.

This is the **least squares problem**:

\[
\min_x \|Ax - b\|_2^2.
\]

We minimize the squared Euclidean distance between \(Ax\) and \(b\) over all choices of \(x\).

### Geometric Interpretation

The best \(\hat{b} = A\hat{x}\) inside the column space is the **orthogonal projection** of \(b\) onto \(\mathcal{R}(A)\).

The error vector \(b - \hat{b} = b - A\hat{x}\) must be **orthogonal to the column space** of \(A\). This is the **projection theorem** (or orthogonality principle).

Formally: \(b - A\hat{x} \perp \mathcal{R}(A)\), meaning for every column \(a_j\) of \(A\):

\[
a_j^* (b - A\hat{x}) = 0.
\]

Collecting all columns:

\[
A^*(b - A\hat{x}) = 0.
\]

Rearranging:

\[
A^*A\hat{x} = A^*b.
\]

These are the **normal equations**.

The transcript writes this derivation using \(A^T\) while discussing real least squares, because the rows of \(A^T\) are the columns of \(A\). In complex notation the same orthogonality condition is written with \(A^*\).

### Normal Equations

\[
\boxed{A^*A\hat{x} = A^*b.}
\]

The solution is:

\[
\hat{x} = (A^*A)^{-1}A^*b \quad \text{(when }A^*A\text{ is invertible)}.
\]

The matrix \((A^*A)^{-1}A^*\) is called the **Moore-Penrose left pseudoinverse** of \(A\).

---

## \(A^*A\) Is Positive Definite for Full Column Rank \(A\)

The instructor proves a key result, generalizing from the specific least squares setup to a broader statement.

### Theorem: \(Z^*Z\) Is Always PSD

For any matrix \(Z\):

**Step 1:** \(Z^*Z\) is Hermitian: \((Z^*Z)^* = Z^*(Z^*)^* = Z^*Z\). ✓

**Step 2:** Positive semidefiniteness: for any vector \(x\):

\[
x^*(Z^*Z)x = (Zx)^*(Zx) = \|Zx\|_2^2 \ge 0.
\]

Therefore \(Z^*Z \succeq 0\) for any \(Z\). No conditions needed. The same style of argument also shows \(ZZ^*\succeq0\); the lecture says the PSD/Hermitian conclusion does not depend on whether \(Z\) is tall, fat, square, full rank, or rank deficient.

### When Is \(Z^*Z\) Positive Definite?

If \(Z\) has full column rank, then \(Zx = 0 \iff x = 0\) (trivial null space). Therefore:

\[
x \ne 0 \implies Zx \ne 0 \implies \|Zx\|^2 > 0 \implies x^*(Z^*Z)x > 0.
\]

So \(Z^*Z \succ 0\) when \(Z\) has full column rank. If \(Z\) is merely tall but not full column rank, then \(Z^*Z\) is still PSD but not PD, because some nonzero \(x\) lies in the null space and gives \(x^*Z^*Zx=0\). For \(ZZ^*\), the analogous PD condition is full row rank.

**Application:** For our tall full-rank \(A\), \(A^*A \succ 0\). Therefore the normal equations have a **unique solution**.

The instructor asks students to think about the general case: even if \(Z\) is not tall (it could be square or fat), as long as it has full column rank, \(Z^*Z \succ 0\). The condition is purely about the column rank, not the shape.

---

## Solving Least Squares via Cholesky: Theoretically Correct, Numerically Inadvisable

Since \(A^*A\succ0\), apply Cholesky to solve the normal equations:

1. Factor \(A^*A = LL^*\).
2. Solve \(Lz = A^*b\) by forward substitution.
3. Solve \(L^*\hat{x} = z\) by back substitution.

**The instructor's warning:** "This is good in theory, but bad in practice. Don't do that."

The reason involves **numerical conditioning**. If \(A\) has condition number \(\kappa(A) = \sigma_{\max}/\sigma_{\min}\), then \(A^*A\) has condition number \(\kappa(A)^2\). Forming \(A^*A\) squares the condition number, making the system much harder to solve in finite-precision arithmetic. The rounding errors accumulate.

**What to do instead:** MATLAB's backslash operator (and Python's `numpy.linalg.lstsq`) uses QR decomposition or SVD-based approaches that operate directly on \(A\) without forming \(A^*A\). These methods maintain the original condition number.

The instructor explicitly says: "If \(b\) is not in the range space of \(A\), MATLAB doesn't do this. It uses other methods." QR-based and SVD-based least squares solutions will be discussed in later lectures.

The theoretical purpose of the Cholesky approach is to establish the connection between least squares and positive definite systems. Practically, prefer QR or SVD.

---

## Application: Generating Correlated Random Vectors

The instructor introduces an application of matrix square roots (not restricted to the Cholesky or positive definite square root specifically) that is practically important in signal processing.

**The problem:** A graduate student's advisor says: "Write code to generate random vectors whose elements have a specific correlation structure." The advisor gives a desired covariance matrix \(C_y\). MATLAB's `randn` generates uncorrelated (white) random vectors. How do you produce correlated ones?

More specifically, the lecture frames the computational task as generating \(L\) samples of a random vector with prescribed mean \(m_x\) and prescribed covariance \(C_x\). A call like `randn(n,L)` gives \(L\) columns, each an \(n\)-dimensional Gaussian sample. The entries are independent Gaussian variables; for Gaussian variables, independence and uncorrelatedness coincide. The instructor emphasizes that the goal here is the covariance structure, not a detailed discussion of Gaussian versus non-Gaussian distributions.

---

## Background: Random Vectors

The lecture reviews the basics for completeness.

### Mean Vector

For a random vector \(x = (x_1,\ldots,x_n)^T\):

\[
\mu_x = \mathbb{E}[x] = \begin{bmatrix}\mathbb{E}[x_1]\\\vdots\\\mathbb{E}[x_n]\end{bmatrix}.
\]

The mean vector contains the individual means of each component.

For continuous random vectors, the instructor expands the definition using the joint PDF:

\[
\mathbb{E}[x] = \int x f_X(x_1,\ldots,x_n)\,dx_1\cdots dx_n.
\]

Looking at the first component, this integral becomes:

\[
\int x_1 f_X(x_1,\ldots,x_n)\,dx_1\cdots dx_n
  = \int x_1 f_{X_1}(x_1)\,dx_1
  = \mathbb{E}[x_1],
\]

because integrating the joint PDF over the other variables produces the marginal PDF of \(x_1\). The same argument applies component by component, so \(\mathbb{E}[x]\) is the vector of scalar expectations.

### Correlation and Covariance Between Two Scalar Random Variables

The **correlation** between \(x_i\) and \(x_j\) is \(\mathbb{E}[x_i \bar{x}_j]\) (real case: \(\mathbb{E}[x_ix_j]\)). The instructor calls this a potentially confusing point: two variables being uncorrelated does **not** mean this raw correlation is zero in general. It means the raw correlation equals the product of the means:

\[
\mathbb{E}[x_i\bar{x}_j] = \mathbb{E}[x_i]\,\overline{\mathbb{E}[x_j]}.
\]

Only in the zero-mean case does "uncorrelated" reduce to raw correlation equal to zero.

The **covariance** subtracts the product of means:

\[
\text{Cov}(x_i,x_j) = \mathbb{E}[(x_i-\mu_i)\overline{(x_j-\mu_j)}].
\]

This is the correlation of the **centralized** variables \(x_i-\mu_i\) and \(x_j-\mu_j\). Centralizing means subtracting the mean, shifting the PDF so the new variable has mean zero. Expanding the product gives:

\[
\text{Cov}(x_i,x_j)=\mathbb{E}[x_i\bar{x}_j]-\mu_i\bar{\mu}_j.
\]

**Distinction:** Two random variables are **uncorrelated** if \(\text{Cov}(x_i,x_j) = 0\), equivalently if their raw correlation equals the product of their means.

### Geometric/Intuitive Meaning of Covariance

The instructor explains covariance by asking students to imagine a scatter plot of \(n\) independent sample points \((x_1^{(k)}, x_2^{(k)})\) drawn from the joint PDF. The point of the picture is intuition, not a probability-one theorem.

When the cloud has a positive trend, most points above the \(x_1\) mean also sit above the \(x_2\) mean, but not all of them must. The instructor phrases this as a bet that is usually right but can sometimes lose.

**Case 1: Positive covariance.** The cloud of points has a positive slope — when \(x_1\) is above its mean, \(x_2\) tends to be above its mean. Then \((x_1 - \mu_1)\) and \((x_2 - \mu_2)\) tend to have the same sign, so their product is positive, and the expectation of the product is positive.

**Case 2: Negative covariance.** The cloud slopes downward — when \(x_1\) is above its mean, \(x_2\) tends to be below its mean. Opposite signs → negative product → negative expectation.

**Case 3: Zero covariance.** The cloud is circular — knowing \(x_1\) gives no linear information about \(x_2\). However, the instructor notes: zero covariance does NOT mean \(x_1\) contains no information about \(x_2\). A circular cloud can have a nonlinear relationship; zero covariance only means there is no **linear** relationship.

The zero-covariance picture need not literally be circular. The transcript's point is broader: a symmetric or nonlinear cloud can have no clear positive or negative linear trend. Knowing \(x_1\) may still restrict \(x_2\) to a smaller nonlinear region, but a linear estimator cannot exploit that structure. A nonlinear estimator would be needed, and estimation theory is not pursued here.

**Practical meaning:** If someone tells you \(x_1 > \mu_1\) and the covariance is positive, you would bet that \(x_2 > \mu_2\). If covariance is zero, knowing \(x_1\) gives you no useful linear prediction of \(x_2\).

**MMSE Linear Estimator:** If you want to estimate \(x_2\) as a linear function of \(x_1\) (i.e., \(\hat{x}_2 = a(x_1 - \mu_1) + \mu_2\) minimizing the mean squared error), the optimal coefficient is:

\[
a = \frac{\text{Cov}(x_1,x_2)}{\text{Var}(x_1)}.
\]

Equivalently, for an affine estimator \(\hat{x}_2=ax_1+b\), the offset is \(b=\mu_2-a\mu_1\). The instructor labels this estimator discussion as extra intuition "in case you are curious."

If the covariance is zero, \(a = 0\), and your best linear estimator of \(x_2\) is just its mean \(\mu_2\) — \(x_1\) provides no linear benefit. The instructor notes: "this looks like an inner product divided by an inner product — in fact, covariances can be viewed as inner products," a connection to be developed later.

**Variance:** \(\text{Var}(x_i) = \text{Cov}(x_i,x_i) = \mathbb{E}[|x_i-\mu_i|^2]\). Expanding gives \(\text{Var}(x_i)=\mathbb{E}[|x_i|^2]-|\mu_i|^2\). This is the diagonal entry of the covariance matrix.

### Autocorrelation Matrix

\[
R_x = \mathbb{E}[xx^*].
\]

Autocorrelation is for one random vector, not two different random vectors. It is a library of all pairwise correlations between components of that vector. Entry \((R_x)_{ij} = \mathbb{E}[x_i\bar{x}_j]\).

**Key point:** Even though each sample \(xx^*\) is a rank-one matrix, the expectation \(\mathbb{E}[xx^*]\) is generally full rank (it is a weighted sum of many rank-one matrices and can have arbitrary rank).

For a discrete random vector taking values \(x^{(k)}\) with probabilities \(p_k\):

\[
R_x=\sum_k p_k x^{(k)}(x^{(k)})^*.
\]

Each \(x^{(k)}(x^{(k)})^*\) is rank one, but the sum need not be rank one.

### Covariance Matrix

\[
C_x = \mathbb{E}[(x-\mu_x)(x-\mu_x)^*] = R_x - \mu_x\mu_x^*.
\]

Entry \((C_x)_{ij} = \text{Cov}(x_i,x_j)\). The diagonal entries are variances.

The terminology "white" and "colored" comes from random processes, which the instructor says are outside this course. A random process can be viewed as a random vector with infinitely many components. Pairwise correlations across time form a correlation function; the Fourier transform of that function is a spectrum. If the samples are uncorrelated, the spectrum is constant across frequencies, analogous to white light. If some pairs are correlated, engineers call the vector or process colored.

**White vs. colored random vectors:**
- **White random vector:** elements are pairwise uncorrelated → \(C_x\) is diagonal. Analogy: white light has a flat power spectrum; white random vectors have a flat (diagonal) covariance.
- **Colored random vector:** elements have nonzero covariances → \(C_x\) has nonzero off-diagonal entries.

---

## Autocorrelation and Covariance Matrices Are Hermitian and Positive Semidefinite

The instructor explicitly connects the random-vector definitions back to Hermitian and positive definite matrices. Both \(R_x\) and \(C_x\) are Hermitian and PSD; \(C_x\) is the autocorrelation matrix of the mean-centered vector \(x-\mu_x\).

For the autocorrelation matrix:

\[
a^*R_xa = \mathbb{E}[a^*xx^*a] = \mathbb{E}[|a^*x|^2] \ge 0.
\]

Here \(a\) is deterministic, so it can be moved inside the expectation, and \(a^*x\) is a scalar random variable.

**Hermitian:** \(C_x^* = \mathbb{E}[(x-\mu)(x-\mu)^*]^* = C_x\). ✓

**Positive semidefinite:** For any vector \(a\):

\[
a^*C_x a = \mathbb{E}[a^*(x-\mu)(x-\mu)^*a] = \mathbb{E}[|a^*(x-\mu)|^2] \ge 0.
\]

The expected value of a nonnegative quantity is nonneg. Therefore \(C_x \succeq 0\).

**Positive definite?** If \(C_x\) has full rank (all eigenvalues positive), then it is PD. If the random vector lies in a lower-dimensional subspace with probability 1, then \(C_x\) is only PSD.

In most practical scenarios with a full-rank random vector, \(C_x \succ 0\). The instructor states this as: a full-rank PSD matrix cannot have zero eigenvalues, so its eigenvalues must all be positive.

---

## Coloring: Generating a Correlated Random Vector

**Goal:** Given desired covariance \(C_y \succ 0\) and a white random vector \(z\) with \(\mathbb{E}[zz^*] = I\) (e.g., columns from MATLAB's `randn(n,L)`), construct a zero-mean \(y\) with covariance \(C_y\). Then add the desired mean if the requested random vector is nonzero mean.

**Algorithm:**

1. Find any matrix square root \(S\) satisfying \(SS^* = C_y\).
   - Options: Cholesky factor \(L\) (lower triangular), or positive definite square root \(C_y^{1/2} = U\Lambda^{1/2}U^*\).
   - For the coloring application, it does not matter which square root is used.

2. Set \(y = Sz\).
3. If the final desired mean is \(m_x\), set \(x=y+m_x\). For \(L\) samples stored as columns, write \(X=S Z + m_x\mathbf{1}_L^T\).

Mean shifting does not change covariance, so the zero-mean construction is enough for the covariance part.

**Verification:**

\[
\mathbb{E}[yy^*] = \mathbb{E}[Szz^*S^*] = S\mathbb{E}[zz^*]S^* = SIS^* = SS^* = C_y. \checkmark
\]

**Why it works intuitively:** When we multiply \(z\) by \(S\), we take weighted sums of the uncorrelated components of \(z\). The elements of \(y = Sz\) each depend on the same pool of uncorrelated sources, creating linear relationships between them. The square root structure ensures that the pairwise covariances are exactly as specified by \(C_y\).

**The key insight for why we use the square root:** When computing \(\mathbb{E}[yy^*] = \mathbb{E}[Szz^*S^*] = S\cdot I\cdot S^* = SS^* = C_y\), the \(S\) appears once on each side, so we need the factor that multiplied by its conjugate gives \(C_y\) — i.e., the square root. The instructor explicitly explains this to a student asking why we use the square root.

**Note on unitary coloring matrix:** If instead of a general square root we used a unitary matrix \(U\), then \(y = Uz\) would still have identity covariance:
\(\mathbb{E}[yy^*] = U\mathbb{E}[zz^*]U^* = UIU^* = I\).
So using a unitary matrix does not create correlation; you still get a white vector. The non-unitary part of the square root is what introduces the correlation.

---

## Whitening: Reversing the Process

**Goal:** Given a colored random vector \(y\) with covariance \(C_y\), produce a white vector \(q\) with identity covariance.

**Algorithm:** Set \(q = S^{-1}y\), where \(S\) is any invertible square root satisfying \(SS^*=C_y\). If \(S\) is denoted \(C_y^{1/2}\), this is often written \(q=C_y^{-1/2}y\): multiply by the inverse square root.

**Verification:**

\[
\mathbb{E}[qq^*] = S^{-1}\mathbb{E}[yy^*](S^{-1})^* = S^{-1}C_yS^{-*} = S^{-1}SS^*S^{-*} = I. \checkmark
\]

The transcript has a student correction during this derivation: the vector being whitened should be the colored vector \(y\) with covariance \(C_y\), and the matrix should be the inverse square root of \(C_y\). The instructor agrees that the notation became confusing and says it will be clarified in the next lecture.

**Applications of whitening:** Blind source separation and signal pre-processing in communications. The idea is to remove the correlation structure so that subsequent algorithms can assume uncorrelated inputs.

---

## Instructor Remarks and Study Guidance

- The Cholesky proof's key step is **star-congruence preserves inertia** → the Schur complement is PD. Do not try to prove Schur complement positivity from the formula alone.
- **Normal equations** \(A^*A\hat{x}=A^*b\) arise from the projection theorem: the least squares error must be orthogonal to the column space of \(A\). This is the geometric meaning.
- **\(Z^*Z\) is always PSD** and PD when \(Z\) has full column rank. These are frequently examined facts.
- Numerically, **do not solve least squares via normal equations + Cholesky**; the condition number gets squared. Use QR or SVD.
- The **coloring and whitening operations** use the matrix square root. The choice of which square root (PD vs. Cholesky vs. other) does not matter for the coloring application; it matters for applications like causal estimation where lower triangularity is required.
- **Covariance as inner product:** The expression \(\text{Cov}(x_i,x_j)/\text{Var}(x_i)\) looks like an inner product divided by a squared norm — the same structure as the projection coefficient. This connection will be made explicit when inner products are formalized.

- For random variables, **uncorrelated means covariance zero**, not necessarily raw correlation zero. Raw correlation equals the product of means; in the zero-mean case these statements coincide.
- The whitening derivation has a notation caveat in the transcript. Remember the clean version: if \(C_y=SS^*\), then \(q=S^{-1}y\) has covariance \(I\).

## Source and Coverage Note

Source: `corrected/lecture15_corrected.md`.

Coverage: Full lecture covered chronologically. Topics: opening summary of all factorizations and matrix classes, review of PD properties (positive linear combinations, diagonal entries, principal submatrices, star-congruence, Sylvester's law, SS* form), Cholesky proof completion (Schur complement PD by star-congruence, inductive step), causal estimator application of lower triangular square root, solving PD systems via Cholesky, least squares problem (geometric setup, orthogonality condition, normal equations, pseudoinverse), Z*Z always PSD and PD for full column rank (proof), numerical warning about normal equations, covariance intuition (scatter plot, positive/negative/zero covariance, MMSE linear estimator, covariance as inner product, variance), autocorrelation and covariance matrices (Hermitian and PSD proofs), white vs. colored random vectors, coloring algorithm (any square root of C_y), why unitary coloring does not create correlation, whitening algorithm, applications.

Audit addendum: Notes now also preserve the instructor's notation clarification for principal submatrices versus sums of separate PD matrices, the joint-PDF/marginal-PDF derivation of \(\mathbb{E}[x]\), raw correlation versus covariance, centralization, trend exceptions in covariance scatter plots, the nonlinear-information caveat for zero covariance, the discrete weighted-sum expression for \(R_x\), the Random Processes origin of white/colored terminology, PSD proofs for both \(R_x\) and \(C_x\), multiple-sample coloring with mean shift, and the whitening notation correction.
