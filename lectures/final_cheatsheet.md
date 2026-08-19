# Linear System Theory — Final Exam Cheatsheet
## Lectures 2–23 | EE 545

---

## PART 1: VECTOR FUNDAMENTALS

### Combinations
| Type | Formula | Constraint |
|---|---|---|
| Linear | \(\sum \alpha_i x_i\) | None |
| Affine | \(\sum \alpha_i x_i\) | \(\sum \alpha_i = 1\) |
| Convex | \(\sum \alpha_i x_i\) | \(\sum \alpha_i = 1\), \(\alpha_i \ge 0\) |

- **Convex set:** for any \(x,y \in S\) and \(t\in[0,1]\), \(tx+(1-t)y \in S\).
- **Convex hull:** all convex combinations of points in a set.
- **Affine hull:** all affine combinations. Two points → line through them.

### Hyperplanes and Half-Spaces
- **Hyperplane:** \(\{x : a^Tx = b\}\). In 2D: a line. Normal vector \(a\).
- **Half-space:** \(\{x : a^Tx \ge b\}\) or \(\{x : a^Tx \le b\}\).
- A neuron is a half-space classifier.

---

## PART 2: NORMS AND INNER PRODUCTS

### Norm Axioms
1. \(\|x\| \ge 0\); \(\|x\|=0 \iff x=0\)
2. \(\|\alpha x\| = |\alpha|\|x\|\)
3. \(\|x+y\| \le \|x\|+\|y\|\) (triangle inequality)

### Vector \(p\)-Norms (on \(\mathbb{C}^n\))
\[
\|x\|_p = \left(\sum_k |x_k|^p\right)^{1/p}, \quad \|x\|_\infty = \max_k |x_k|
\]

- \(\ell_1\): taxicab/Manhattan; promotes sparsity.
- \(\ell_2\): Euclidean; \(\|x\|_2 = \sqrt{x^*x}\).
- \(\ell_\infty\): Chebyshev; worst-case error.

### Inner Products
**Real:** \(\langle x,y\rangle = x^Ty\). **Complex:** \(\langle x,y\rangle = y^*x\) (linear in first, conjugate-linear in second).

Properties: conjugate symmetry \(\langle x,y\rangle = \overline{\langle y,x\rangle}\); positive definite \(\langle x,x\rangle > 0\) for \(x\ne0\).

**Cauchy-Schwarz:** \(|\langle x,y\rangle| \le \|x\|\|y\|\)

**Angle:** \(\cos\theta = \frac{\langle x,y\rangle}{\|x\|\|y\|}\). **Orthogonal:** \(x\perp y \iff \langle x,y\rangle = 0\).

### Weighted 2-Norm
\(\|x\|_W = \sqrt{x^*Wx}\) for PD \(W\). Eigenvectors of \(W\) define weighted directions; eigenvalues are the weights.

---

## PART 3: VECTOR SPACES AND SUBSPACES

### Definitions
- **Vector space:** set with scalar field, vector addition, scalar multiplication satisfying axioms.
- **Subspace:** subset closed under addition and scalar multiplication (contains zero).
- **Span:** all linear combinations of a set.
- **Linear independence:** \(\sum \alpha_i x_i = 0 \implies \alpha_i = 0\).
- **Basis:** linearly independent spanning set.
- **Dimension:** number of vectors in any basis.

### Four Fundamental Subspaces of \(A\) (\(m\times n\), rank \(r\))

| Subspace | Definition | Ambient Space | Dimension |
|---|---|---|---|
| Column space \(\mathcal{R}(A)\) | \(\{Ax : x\in\mathbb{C}^n\}\) = span of columns | \(\mathbb{C}^m\) | \(r\) |
| Row space \(\mathcal{R}(A^*)\) | span of rows = \(\mathcal{R}(A^T)\) | \(\mathbb{C}^n\) | \(r\) |
| Null space \(\mathcal{N}(A)\) | \(\{x: Ax=0\}\) | \(\mathbb{C}^n\) | \(n-r\) |
| Left null space \(\mathcal{N}(A^*)\) | \(\{z: A^*z=0\}\) | \(\mathbb{C}^m\) | \(m-r\) |

**Orthogonality:** \(\mathcal{N}(A) \perp \mathcal{R}(A^*)\) and \(\mathcal{N}(A^*) \perp \mathcal{R}(A)\).

**Direct sums:** \(\mathbb{C}^n = \mathcal{R}(A^*) \oplus \mathcal{N}(A)\); \(\mathbb{C}^m = \mathcal{R}(A) \oplus \mathcal{N}(A^*)\).

---

## PART 4: \(Ax = b\) — EXISTENCE AND UNIQUENESS

| Condition | Requirement | Shape Needed |
|---|---|---|
| Solution exists | \(b \in \mathcal{R}(A)\) | — |
| Exists for ALL \(b\) | \(\mathcal{R}(A) = \mathbb{C}^m\) | Square or fat (\(n \ge m\)) |
| Unique (when exists) | \(\mathcal{N}(A) = \{0\}\) | Square or tall (\(m \ge n\)) |
| Both for all \(b\) | Full rank, square | Square only |

- **All solutions:** \(\hat{x} + \mathcal{N}(A)\) (one particular solution + null space).
- **Right inverse:** \(AD=I_m\) exists iff \(\mathcal{R}(A) = \mathbb{C}^m\) (full row rank).
- **Left inverse:** \(CA=I_n\) exists iff \(\mathcal{N}(A)=\{0\}\) (full column rank).

**Rank:** \(\text{rank}(A) = \dim\mathcal{R}(A) = \dim\mathcal{R}(A^*)\). Row rank = column rank.

---

## PART 5: MATRIX FACTORIZATIONS

| Factorization | Form | Conditions | Purpose |
|---|---|---|---|
| \(PLU\) | \(P^TAP = LU\) | Any square | Gaussian elimination |
| Eigenvalue | \(A = T\Lambda T^{-1}\) | Diagonalizable | System analysis |
| Schur | \(A = UTU^*\) | Any square | Triangularization |
| \(QR\) | \(A = QR\) | Any matrix | Least squares |
| Cholesky | \(A = LL^*\) | \(A\succ 0\) | PD system solving |
| SVD | \(A = U\Sigma V^*\) | Any matrix | All-purpose analysis |

### Eigenvalues and Diagonalization
- **Eigenvalue equation:** \(Ax = \lambda x\), \(x\ne 0\).
- **Characteristic polynomial:** \(p(\lambda) = \det(\lambda I - A)\). Roots = eigenvalues.
- **Eigenspace:** \(\mathcal{N}(A-\lambda I)\).
- **Diagonalizable:** \(A = T\Lambda T^{-1}\) iff \(A\) has \(n\) linearly independent eigenvectors.
- **Similarity:** \(T^{-1}AT\) has the same eigenvalues as \(A\).

---

## PART 6: ORTHOGONAL PROJECTION

### Orthogonal Projection of \(x\) onto Subspace \(V\)
- \(p \in V\) and \(x - p \perp V\).
- Minimizes \(\|x - v\|\) over all \(v \in V\).

### Projection Matrix
If \(Q\) has orthonormal columns spanning \(V\):

\[
P = QQ^*, \quad P^2 = P, \quad P^* = P.
\]

If columns are not orthonormal: \(P = A(A^*A)^{-1}A^*\).

---

## PART 7: SPECIAL MATRIX CLASSES

### Hierarchy
```
All matrices
  └── Diagonalizable (T^{-1}AT = Λ)
        └── Normal (A*A = AA*) = Unitarily diagonalizable (A = UΛU*)
              ├── Hermitian (A* = A): eigenvalues real
              │     └── Positive definite/semidefinite/indefinite (by sign of eigenvalues)
              ├── Unitary (U*U = I): eigenvalues on unit circle
              └── Skew-Hermitian (A* = -A): eigenvalues on imaginary axis
```

### Key Properties

| Matrix | Condition | Eigenvalues | \(x^*Ax\) |
|---|---|---|---|
| Hermitian | \(A^*=A\) | Real | Real |
| Unitary | \(U^*U=I\) | \(|\lambda|=1\) | Preserves norm |
| Normal | \(A^*A=AA^*\) | Any | — |
| PD Hermitian | All \(\lambda>0\) | Positive | \(>0\) for \(x\ne0\) |
| PSD Hermitian | All \(\lambda\ge0\) | Nonneg | \(\ge0\) |

### Unitary Matrices
- \(U^*U = UU^* = I\); \(U^{-1} = U^*\).
- Columns and rows form orthonormal bases.
- \(\|Ux\|_2 = \|x\|_2\); \(\langle Ux, Uy\rangle = \langle x,y\rangle\).
- Eigenvalues on unit circle: \(|\lambda|=1\) (proof: \(\|Ux\| = \|\lambda x\| = |\lambda|\|x\|\)).
- Eigenspaces for distinct eigenvalues are orthogonal.

### Hermitian Matrices
- \(A^* = A\); real version: symmetric.
- \(x^*Ax \in \mathbb{R}\) for all \(x\): proof \((x^*Ax)^* = x^*A^*x = x^*Ax\).
- Eigenvalues real: from \(x^*Ax = \lambda x^*x\) with \(x^*x > 0\).
- Eigenspaces for distinct eigenvalues orthogonal.

### Normal Matrices
- \(A^*A = AA^*\) iff unitarily diagonalizable iff orthonormal eigenbasis exists.
- Trace identity: \(\|A\|_F^2 = \sum_i |\lambda_i|^2\) (for normal matrices).

### Schur Factorization
Every square complex \(A\) has \(A = UTU^*\) where \(U\) unitary and \(T\) upper triangular.

**Proof idea:** Choose eigenvector, extend to ONB, get block triangular, induct.

---

## PART 8: POSITIVE DEFINITE MATRICES

### Equivalences (for Hermitian \(A\))
\[
A \succ 0 \iff \text{all eigenvalues} > 0 \iff x^*Ax > 0 \; \forall x\ne0 \iff A = SS^* \text{ for invertible }S.
\]

### Sign Classes
| Class | Eigenvalues | Quadratic Form |
|---|---|---|
| PD | All \(>0\) | \(x^*Ax>0\) |
| PSD | All \(\ge0\) | \(x^*Ax\ge0\) |
| ND | All \(<0\) | \(x^*Ax<0\) |
| NSD | All \(\le0\) | \(x^*Ax\le0\) |
| Indefinite | Mixed | Both signs possible |

### Inertia and Sylvester's Law
- **Inertia:** \((n_+, n_-, n_0)\) = (# positive, # negative, # zero eigenvalues).
- **Star-congruence:** \(A = SBS^*\) for invertible \(S\) preserves inertia.
- **Sylvester's law:** \(A \stackrel{\star}{\sim} B \iff \text{inertia}(A) = \text{inertia}(B)\).
- **Corollary:** \(A\succ 0 \iff A \stackrel{\star}{\sim} I \iff A = SS^*\).

### Diagonal Dominance (Sufficient, NOT Necessary)
\(a_{ii} > \sum_{j\ne i}|a_{ij}|\) for all \(i\) implies \(A\succ0\).

### Cholesky Factorization
\(A\succ0 \implies \exists\) unique lower triangular \(L\) with positive diagonal: \(A = LL^*\).

**Proof sketch:** block-partition, Schur complement is PD by star-congruence, induct.

**Solving \(Px=y\) (PD \(P\)):** Factor \(P = LL^*\), then solve \(Lz=y\), then \(L^*x=z\).

### Gram Matrices
For any \(Z\): \(Z^*Z\) is always PSD. If \(Z\) has full column rank, \(Z^*Z\succ0\).

---

## PART 9: LEAST SQUARES

**Problem:** \(A\) is tall full-rank (\(m>n\), rank \(n\)). No exact solution for general \(b\in\mathbb{R}^m\).

\[
\min_x \|Ax - b\|_2^2
\]

**Normal equations:** \(A^*A\hat{x} = A^*b\). Since \(A^*A\succ0\):

\[
\hat{x} = (A^*A)^{-1}A^*b.
\]

**Pseudo-inverse:** \(A^\dagger = (A^*A)^{-1}A^*\) (left inverse of \(A\)).

**Orthogonality condition:** \(b - A\hat{x} \perp \mathcal{R}(A)\).

**Numerically:** Use QR or SVD. Avoid forming \(A^*A\) (squares condition number).

---

## PART 10: QR FACTORIZATION

\(A = QR\) where \(Q\) has orthonormal columns and \(R\) is upper triangular.

- **Gram-Schmidt:** Orthonormalize columns with causal constraint → upper triangular \(R\).
- **Modified Gram-Schmidt:** Numerically superior; subtract \(q_k\) component from all remaining vectors as soon as \(q_k\) is found.
- **Full QR:** \(Q\) is square unitary; \(R\) is rectangular.
- **Reduced QR:** \(Q\) has same number of columns as \(A\); \(R\) is square.

Causal constraint: \(\text{span}\{q_1,\ldots,q_k\} = \text{span}\{a_1,\ldots,a_k\}\).

---

## PART 11: BLOCK MATRIX TECHNIQUES

### Schur Complement
For \(A = \begin{bmatrix}A_{11}&A_{12}\\A_{21}&A_{22}\end{bmatrix}\) with \(A_{11}\) invertible:

\[
S_{11} = A_{22} - A_{21}A_{11}^{-1}A_{12} \quad \text{(Schur complement of }A_{11}\text{)}.
\]

\[
\det(A) = \det(A_{11})\det(S_{11}).
\]

**PD criterion:** \(A\succ0 \iff A_{11}\succ0 \text{ and } S_{11}\succ0\).

**Inertia additivity (Hermitian \(A\)):** \(\text{inertia}(A) = \text{inertia}(A_{11}) + \text{inertia}(S_{11})\).

### Matrix Inversion Lemma (Woodbury Identity)
\[
(A + BCD)^{-1} = A^{-1} - A^{-1}B(C^{-1}+DA^{-1}B)^{-1}DA^{-1}.
\]

Application: rank-one updates of inverse in RLS algorithm.

---

## PART 12: MATRIX NORMS

### Frobenius Norm
\[
\|A\|_F = \sqrt{\sum_{i,j}|a_{ij}|^2} = \sqrt{\text{tr}(A^*A)} = \sqrt{\sum_k \sigma_k^2}.
\]

### Induced Norms
\[
\|A\|_{q,p} = \sup_{\|x\|_p=1}\|Ax\|_q.
\]

| Norm | Formula | Computation |
|---|---|---|
| \(\|A\|_{1,1}\) | \(\ell_1\) in, \(\ell_1\) out | Max column \(\ell_1\)-norm |
| \(\|A\|_{\infty,\infty}\) | \(\ell_\infty\) in, \(\ell_\infty\) out | Max row \(\ell_1\)-norm |
| \(\|A\|_{2,2} = \|A\|_2 = \sigma_1\) | \(\ell_2\) in, \(\ell_2\) out | Largest singular value |

**Geometric view:** Unit \(\ell_2\) sphere → ellipsoid; longest semi-axis = \(\sigma_1\) = induced 2-norm.

### Schatten \(p\)-Norms
\[
\|A\|_{S_p} = \|\sigma\|_p = \left(\sum_k \sigma_k^p\right)^{1/p}.
\]
- \(p=1\): **nuclear norm** \(\|A\|_* = \sum_k \sigma_k\). Convex relaxation of rank.
- \(p=2\): Frobenius norm.
- \(p=\infty\): induced 2-2 norm = \(\sigma_1\).

---

## PART 13: SINGULAR VALUE DECOMPOSITION

### Definition
For any \(m\times n\) matrix \(A\) of rank \(r\):

\[
A = U\Sigma V^*, \quad \sigma_1 \ge \sigma_2 \ge \cdots \ge \sigma_r > 0.
\]

- \(U\): \(m\times m\) unitary (left singular vectors as columns).
- \(V\): \(n\times n\) unitary (right singular vectors as columns).
- \(\Sigma\): \(m\times n\) real nonneg diagonal.

**Outer product form:** \(A = \sum_{k=1}^r \sigma_k u_k v_k^*\).

### SVD Reveals Everything

| Property | From SVD |
|---|---|
| Rank | \(\#\) nonzero \(\sigma_k\) |
| Column space | First \(r\) cols of \(U\) |
| Left null space | Last \(m-r\) cols of \(U\) |
| Row space | First \(r\) cols of \(V\) |
| Null space | Last \(n-r\) cols of \(V\) |
| Induced 2-norm | \(\sigma_1\) |
| Frobenius norm | \(\sqrt{\sum\sigma_k^2}\) |

### Connection to Eigenvalues
- Singular values of \(A\) = \(\sqrt{\text{eigenvalues of }A^*A}\).
- Right singular vectors = eigenvectors of \(A^*A\).
- Left singular vectors = eigenvectors of \(AA^*\).

### Best Rank-\(p\) Approximation (Eckart-Young)
\[
A_p = \sum_{k=1}^p \sigma_k u_k v_k^*, \qquad \|A - A_p\|_F = \sqrt{\sum_{k=p+1}^r \sigma_k^2}.
\]
\(A_p\) is the closest rank-\(p\) matrix to \(A\) in both Frobenius and induced 2-norm.

---

## PART 14: ABSTRACT INNER PRODUCT SPACES

### Axioms for Inner Product \(\langle\cdot,\cdot\rangle\)
1. \(\langle x,y\rangle = \overline{\langle y,x\rangle}\) (conjugate symmetry)
2. Linear in first argument
3. \(\langle x,x\rangle \ge 0\); \(=0\) iff \(x=0\)

Induced norm: \(\|x\| = \sqrt{\langle x,x\rangle}\). **Hilbert space** = complete inner product space.

### Examples
- \(\mathbb{C}^n\): \(\langle x,y\rangle = y^*x\).
- \(L^2([a,b])\): \(\langle f,g\rangle = \int_a^b f(t)\overline{g(t)}\,dt\).
- Matrices: \(\langle A,B\rangle = \text{tr}(A^*B)\) → Frobenius norm.

---

## KEY PROOF IDEAS (EXAM-READY)

1. **Ax=b solvable iff \(b\in\mathcal{R}(A)\):** expand \(Ax\) as column combination.
2. **All solutions \(= \hat{x}+\mathcal{N}(A)\):** subtract two solutions → difference in null space.
3. **\(\mathcal{N}(A)\perp\mathcal{R}(A^*)\):** \(Ax=0\) means inner product with every row is 0.
4. **Row rank = column rank:** map row-basis through \(A\), show independence; reverse.
5. **Basis change \(\to T^{-1}AT\):** convert coordinates, apply, convert back.
6. **\(U^*U=I\) preserves norm:** \(\|Ux\|^2=x^*U^*Ux=x^*x\).
7. **Unitary eigenvalues on unit circle:** norm preservation → \(|\lambda|=1\).
8. **Hermitian eigenvalues real:** \(x^*Ax=\lambda x^*x\), left side real by \(A=A^*\).
9. **Hermitian eigenspaces orthogonal:** compare \(\lambda y^*x\) and \(\mu y^*x\) → 0.
10. **Normal = unitarily diagonalizable:** Schur → \(T\) normal → \(T\) diagonal.
11. **PD criterion via quadratic form:** \(A=U\Lambda U^*\), write \(x^*Ax=\sum\lambda_i|z_i|^2\).
12. **\(Z^*Z\succeq0\):** \(x^*(Z^*Z)x = \|Zx\|^2\ge0\).
13. **Cholesky Schur complement PD:** by star-congruence preserving inertia.
14. **Projection \(P=QQ^*\):** \(Q^*Q=I\); \(Px\in V\); \(x-Px\perp V\).
15. **Eckart-Young:** truncate SVD to first \(p\) terms = best rank-\(p\) approximation.

---

## COMMON MISTAKES TO AVOID

- \(A>0\) for matrices means PD (not elementwise positive).
- Orthogonal ≠ orthonormal: orthonormal also requires unit norms.
- PSD ≠ PD: zero eigenvalues allowed in PSD, not in PD.
- Diagonal dominance is **sufficient** for PD, not necessary.
- Similarity preserves eigenvalues; star-congruence preserves **inertia** (not eigenvalues).
- SVD uses **two** unitary matrices (not one like eigendecomposition).
- Frobenius norm ≠ induced 2-norm: \(\|A\|_F = \sqrt{\sum\sigma_k^2}\) vs \(\|A\|_2=\sigma_1\).
- Nuclear norm promotes low rank; it does NOT equal rank.
- Gram-Schmidt with linear dependence: the dependent vector produces \(\tilde{a}_k=0\); rank < n.
- Left null space ≠ null space: \(\mathcal{N}(A^*)\) is in the **output** space; \(\mathcal{N}(A)\) is in the **input** space.
