# Linear System Theory — Master Notes
## EE 545 | Lectures 2–23 | Complete Study Reference

---

## CHAPTER 1: GEOMETRIC VIEW OF ALGEBRA (L02)

### Course Philosophy

The central theme: find the geometric picture behind every algebraic expression. An equation may define a hyperplane; a constraint may define a half-space; a dataset may be a point cloud. Linear algebra translates between algebraic and geometric languages.

### Vectors

A vector in \(\mathbb{R}^n\) is an ordered \(n\)-tuple. The order of entries matters. Views:

- **Position:** a point in \(n\)-dimensional space.
- **Arrow:** direction and magnitude from the origin.
- **Data container:** e.g., a student represented by (midterm, final, homework).

Non-geometric data (grades, sensor readings, pixel values) becomes geometric by treating it as a point in \(\mathbb{R}^n\).

### Linear, Affine, and Convex Combinations

| Type | Formula | Constraint |
|---|---|---|
| Linear | \(\sum_{i=1}^m \alpha_i x_i\) | None |
| Affine | \(\sum_{i=1}^m \alpha_i x_i\) | \(\sum\alpha_i=1\) |
| Convex | \(\sum_{i=1}^m \alpha_i x_i\) | \(\sum\alpha_i=1\), \(\alpha_i\ge0\) |

**Span:** Set of all linear combinations of \(\{x_1,\ldots,x_m\}\). Always a subspace.

**Affine hull:** All affine combinations of a set. Two points → the line through them. Three non-collinear points → the plane through them.

**Convex hull:** All convex combinations. Two points → line segment. Three non-collinear points → triangle.

**Convex set:** A set \(S\) is convex if for any \(x,y\in S\) and \(t\in[0,1]\): \(tx+(1-t)y\in S\). Equivalently: all line segments between points in \(S\) stay in \(S\).

**Expectation as convex combination:** \(\mathbb{E}[X] = \sum_i p_i x_i\) where \(p_i\ge0\), \(\sum p_i=1\).

### Hyperplanes and Half-Spaces

A **hyperplane** in \(\mathbb{R}^n\): \(H = \{x : a^Tx = b\}\), \(a\ne0\).

- In 2D: a line. In 3D: a plane. In higher dimensions: a hyperplane.
- Does NOT need to pass through the origin (unless \(b=0\)).
- The vector \(a\) is the **normal vector** (orthogonal to \(H\)).

**Half-spaces:** \(H^+ = \{x:a^Tx\ge b\}\) and \(H^- = \{x:a^Tx\le b\}\).

**Neural network connection:** A simple neuron computes \(w^Tx - \theta\) and fires iff the result is positive → it is a half-space classifier. A neuron identifies which side of a hyperplane the input lies on.

---

## CHAPTER 2: NORMS AND INNER PRODUCTS (L03, L19)

### Norm Axioms

\(\|\cdot\|: V\to\mathbb{R}_{\ge0}\) satisfying:
1. \(\|x\|\ge0\); \(\|x\|=0\iff x=0\) (positive definite)
2. \(\|\alpha x\|=|\alpha|\|x\|\) (homogeneity)
3. \(\|x+y\|\le\|x\|+\|y\|\) (triangle inequality)

### Vector \(p\)-Norms

\(\|x\|_p = (\sum_k|x_k|^p)^{1/p}\), \(\|x\|_\infty=\max_k|x_k\|\).

Key cases:
- \(\ell_1\): taxicab norm; promotes **sparsity** in optimization.
- \(\ell_2\): Euclidean norm; \(\|x\|_2 = \sqrt{x^*x}\).
- \(\ell_\infty\): Chebyshev norm; captures worst-case/maximum error.

As \(p\) increases, \(\|x\|_p\) decreases for fixed \(x\).

**Norm balls:** \(\ell_1\) ball = diamond, \(\ell_2\) ball = circle, \(\ell_\infty\) ball = square (in 2D).

### Sparsity and \(\ell_1\) Minimization

Minimizing \(\|x\|_1\) subject to constraints tends to produce sparse solutions. The \(\ell_1\) ball's corners lie on coordinate axes; constrained optimization often "hits" a corner, zeroing out most components.

Applications: compressed sensing, feature selection, LASSO regression, filter design.

### Euclidean Inner Product and Cauchy-Schwarz

**Real:** \(\langle x,y\rangle = x^Ty = \sum_k x_ky_k\).  
**Complex:** \(\langle x,y\rangle = y^*x = \sum_k\bar{y}_kx_k\) (conjugate the second argument).

**Cauchy-Schwarz:** \(|\langle x,y\rangle|\le\|x\|_2\|y\|_2\).

This is essential for defining the **angle** between vectors:

\[\cos\theta = \frac{\langle x,y\rangle}{\|x\|_2\|y\|_2}.\]

The inequality guarantees \(\cos\theta\in[-1,1]\).

**Orthogonality:** \(x\perp y\iff\langle x,y\rangle=0\).

**Orthonormal set:** pairwise orthogonal and each has unit norm.

---

## CHAPTER 3: VECTOR SPACES AND SUBSPACES (L04)

### Vector Space (Formal Definition)

Four ingredients: (1) set of vectors \(V\), (2) scalar field \(\mathbb{F}\), (3) vector addition, (4) scalar multiplication. Must satisfy 10 axioms (closure, associativity, commutativity, identity elements, inverses, distributivity).

**Examples:** \(\mathbb{R}^n\), \(\mathbb{C}^n\), polynomials of degree \(\le n\), continuous functions on \([a,b]\), matrices with zero trace.

### Subspace

A nonempty subset \(S\subseteq V\) closed under addition and scalar multiplication. Automatically contains the zero vector.

**Test:** \(S\) is a subspace iff for all \(x,y\in S\) and scalars \(\alpha,\beta\): \(\alpha x+\beta y\in S\).

### Span, Basis, Linear Independence, Dimension

**Span:** \(\text{span}\{x_1,\ldots,x_m\}\) = set of all linear combinations. Always a subspace.

**Linear independence:** \(\sum\alpha_ix_i=0\implies\alpha_i=0\) for all \(i\).

**Basis:** linearly independent set that spans the space. Two characterizations: (a) minimal spanning set, (b) maximal independent set.

**Dimension:** number of vectors in any basis (well-defined).

---

## CHAPTER 4: \(Ax=b\) — EXISTENCE AND UNIQUENESS (L05, L06, L07)

### Two Views of Matrix-Vector Multiplication

**Column view:** \(Ax = x_1a_1 + x_2a_2 + \cdots + x_na_n\). Relevant to **existence**.

**Row view:** \((Ax)_i = r_i^Tx\) (inner product of row \(i\) with \(x\)). Relevant to **uniqueness**.

### Four Fundamental Subspaces

For \(A\) of size \(m\times n\), rank \(r\):

| Subspace | Definition | Lives in | Dim |
|---|---|---|---|
| \(\mathcal{R}(A)\) | span of columns = \(\{Ax\}\) | Output \(\mathbb{C}^m\) | \(r\) |
| \(\mathcal{R}(A^*)\) | span of rows | Input \(\mathbb{C}^n\) | \(r\) |
| \(\mathcal{N}(A)\) | \(\{x:Ax=0\}\) | Input \(\mathbb{C}^n\) | \(n-r\) |
| \(\mathcal{N}(A^*)\) | \(\{z:A^*z=0\}\) | Output \(\mathbb{C}^m\) | \(m-r\) |

**Orthogonality:** \(\mathcal{N}(A)\perp\mathcal{R}(A^*)\) (proof: each row of \(A\) has zero inner product with null vectors); \(\mathcal{N}(A^*)\perp\mathcal{R}(A)\).

**Direct sums:** \(\mathbb{C}^n=\mathcal{R}(A^*)\oplus\mathcal{N}(A)\); \(\mathbb{C}^m=\mathcal{R}(A)\oplus\mathcal{N}(A^*)\).

### Existence and Uniqueness

**Existence:** \(Ax=b\) has a solution \(\iff b\in\mathcal{R}(A)\).  
**Existence for every \(b\):** \(\mathcal{R}(A)=\mathbb{C}^m\) (full row rank, requires \(n\ge m\)) \(\iff\) right inverse exists.  
**Uniqueness:** \(\mathcal{N}(A)=\{0\}\) (full column rank, requires \(m\ge n\)) \(\iff\) left inverse exists.  
**All solutions:** \(\hat{x}+\mathcal{N}(A)\) for any particular solution \(\hat{x}\).

**Rank:** \(\text{rank}(A)=\dim\mathcal{R}(A)=\dim\mathcal{R}(A^*)\). Row rank = column rank.

**Proof that row rank ≤ column rank:** Choose a basis \(v_1,\ldots,v_{r_R}\) for the row space. Map to \(Av_1,\ldots,Av_{r_R}\) in the column space. These are linearly independent (if \(\sum\alpha_iAv_i=0\), then \(A(\sum\alpha_iv_i)=0\), so \(w=\sum\alpha_iv_i\in\mathcal{N}(A)\cap\mathcal{R}(A^*)=\{0\}\), giving \(\alpha_i=0\)). So column rank \(\ge\) row rank; reverse by transpose.

---

## CHAPTER 5: FACTORIZATIONS AND BASIS CHANGE (L07, L08, L09)

### Simple Systems

Solving \(Ax=b\) is easy when \(A\) is:
- **Diagonal:** decouple equations, \(x_i=b_i/a_{ii}\).
- **Triangular:** forward/back substitution.
- **Unitary/Orthogonal:** \(x=A^{-1}b=A^*b\).

**Strategy:** Convert arbitrary \(A\) into a product of simple matrices.

### Basis Change

In a basis given by columns of invertible \(T\): the representation of the linear map \(A\) changes to \(T^{-1}AT\).

**Derivation:** \(x=T\tilde{x}\) (old-to-new), so \(A x=AT\tilde{x}\). The output in new coordinates is \(T^{-1}ATx\).

**Similar matrices** (\(B=T^{-1}AT\)) have the same **eigenvalues**.

### Eigenvalues and Diagonalization

**Eigenvalue equation:** \(Ax=\lambda x\), \(x\ne0\).  
**Eigenspace:** \(\mathcal{N}(A-\lambda I)\).  
**Characteristic polynomial:** \(p(\lambda)=\det(\lambda I-A)\). Eigenvalues = roots.

**Diagonalizable:** \(A=T\Lambda T^{-1}\) iff \(A\) has \(n\) linearly independent eigenvectors (columns of \(T\)).

Not all matrices are diagonalizable. But all square complex matrices can be **triangularized** (Schur).

### Gram-Schmidt and Orthogonal Projections

**Projection of \(x\) onto \(y\):** \(\hat{x}=\frac{\langle x,y\rangle}{\|y\|^2}y=\frac{y^*x}{y^*y}y\). Error \(x-\hat{x}\perp y\).

**Projection onto subspace with ONB \(Q\):** \(p=QQ^*x\). Projection matrix \(P=QQ^*\).

Properties: \(P^2=P\) (idempotent), \(P^*=P\) (self-adjoint), \(\mathcal{R}(P)=\text{col space of }Q\).

For non-orthogonal columns \(A\): \(P=A(A^*A)^{-1}A^*\).

---

## CHAPTER 6: UNITARY AND HERMITIAN MATRICES (L10, L11)

### Unitary Matrices

\(U^*U=UU^*=I\). Real case: orthogonal \(Q\), \(Q^TQ=I\).

**Equivalent conditions:** columns form ONB; rows form ONB; \(U^{-1}=U^*\).

**Norm preservation:** \(\|Ux\|_2=\|x\|_2\). Proof: \(\|Ux\|^2=x^*U^*Ux=x^*x\).  
**Inner product preservation:** \(\langle Ux,Uy\rangle=\langle x,y\rangle\).  
**Energy preservation:** \(\|UA\|_F=\|A\|_F\).

**Eigenvalues on unit circle:** If \(Ux=\lambda x\), then \(|\lambda|=1\).  
Proof: \(\|Ux\|_2=\|\lambda x\|_2=|\lambda|\|x\|_2=\|x\|_2\), so \(|\lambda|=1\).

**Eigenspaces for distinct eigenvalues are orthogonal.**

### Hermitian Matrices

\(A^*=A\). Real case: symmetric \(A^T=A\).

**Quadratic form:** \(x^*Ax\in\mathbb{R}\) for all \(x\).  
Proof: \((x^*Ax)^*=x^*A^*x=x^*Ax\), so it equals its conjugate → real.

**Eigenvalues real:** From \(x^*Ax=\lambda x^*x\), since LHS is real and \(x^*x>0\), we get \(\lambda\in\mathbb{R}\).

**Eigenspaces for distinct eigenvalues orthogonal:** Compare \(\lambda\langle y,x\rangle=\langle Ax,y\rangle=\langle x,Ay\rangle=\mu\langle y,x\rangle^*\). Since \(\lambda,\mu\) real and distinct: \(\langle y,x\rangle=0\).

### Schur Factorization Theorem

**Every** square complex matrix has \(A=UTU^*\) with \(U\) unitary, \(T\) upper triangular.

**Proof idea:**
1. Find an eigenvector \(u_1\) (exists by fundamental theorem of algebra).
2. Extend \(\{u_1\}\) to an orthonormal basis of \(\mathbb{C}^n\).
3. In this basis, \(A\) has block upper triangular form (first column has only one nonzero entry).
4. Apply the same argument recursively to the \((n-1)\times(n-1)\) lower-right block.

---

## CHAPTER 7: NORMAL MATRICES AND SPECTRAL THEORY (L11, L12, L13)

### Normal Matrices

\(A^*A=AA^*\).

**Spectral theorem:** \(A\) is normal \(\iff A\) is unitarily diagonalizable: \(A=U\Lambda U^*\).

**Proof:** Schur gives \(A=UTU^*\). If \(A\) is normal, then \(T\) is normal. An upper triangular normal matrix must be diagonal. Conversely, if \(A=U\Lambda U^*\), then \(A^*A=U|\Lambda|^2U^*=AA^*\).

**Energy identity:** For normal \(A\): \(\|A\|_F^2=\sum_i|\lambda_i|^2\). (Frobenius energy = eigenvalue energy.)

**Subclasses of normal matrices:**

| Condition | Matrix Class | Eigenvalues |
|---|---|---|
| \(A^*=A\) | Hermitian | Real |
| \(U^*U=I\) | Unitary | On unit circle |
| \(A^*=-A\) | Skew-Hermitian | Imaginary |

### Positive Definite Matrices

For Hermitian \(A\):

\[A\succ0 \iff \text{all }\lambda_i>0 \iff x^*Ax>0\;\forall x\ne0 \iff A=SS^*\text{ for invertible }S.\]

**Sign classes:**

| Class | Eigenvalues | Quadratic form shape |
|---|---|---|
| PD | All \(>0\) | Convex paraboloid |
| PSD | All \(\ge0\) | Flat in zero-eigenvalue directions |
| ND | All \(<0\) | Concave paraboloid |
| Indefinite | Mixed | Saddle |

**Diagonal dominance (sufficient, not necessary):** \(a_{ii}>\sum_{j\ne i}|a_{ij}|\) implies PD.

**Positive linear combinations:** If \(A_i\succ0\) and \(c_i>0\), then \(\sum c_iA_i\succ0\).

**Submatrix property:** If \(A\succ0\), then every principal submatrix (same row/column indices) is PD.

---

## CHAPTER 8: INERTIA, STAR-CONGRUENCE, CHOLESKY (L13, L14, L15)

### Inertia and Sylvester's Law

**Inertia:** \((n_+,n_-,n_0)\) = (# positive, # negative, # zero eigenvalues), counted with multiplicity.

**Star-congruence:** \(A\stackrel{\star}{\sim}B\) means \(A=SBS^*\) for invertible \(S\).

**Sylvester's law:** \(A\stackrel{\star}{\sim}B \iff \text{inertia}(A)=\text{inertia}(B)\).

**Similarity vs. star-congruence:**
- Similarity preserves **eigenvalues**.
- Star-congruence preserves only **inertia** (sign pattern).

**Corollary:** \(A\succ0 \iff A\stackrel{\star}{\sim}I\) (same inertia \((n,0,0)\)) \(\iff A=SS^*\).

### Matrix Square Roots

For any invertible \(S\) with \(SS^*=A\), \(S\) is a square root of \(A\). There are infinitely many (insert any unitary factor \(T\): \((ST)(ST)^*=STT^*S^*=SS^*=A\)).

**Positive definite square root:** \(A^{1/2}=U\Lambda^{1/2}U^*\) where \(A=U\Lambda U^*\). Unique PD symmetric square root.

### Cholesky Factorization

\(A\succ0 \implies \exists\) unique lower triangular \(L\) with positive diagonal: \(A=LL^*\).

**Proof sketch:** Partition \(A=\begin{bmatrix}\alpha&v^*\\v&M\end{bmatrix}\). Star-congruence by block Gaussian elimination gives block diagonal \(\begin{bmatrix}\alpha&0\\0&M-vv^*/\alpha\end{bmatrix}\), which is PD by inertia preservation. The Schur complement \(M-vv^*/\alpha\) is PD (not by direct computation — by star-congruence). Induct on dimension.

**Application:** Solve \(Px=y\) (PD \(P\)) via \(Lz=y\), then \(L^*x=z\).

### Least Squares Problem

For tall full-rank \(A\) (\(m>n\), rank \(n\)) and general \(b\):

\[\min_x\|Ax-b\|_2 \quad\Rightarrow\quad A^*A\hat{x}=A^*b \quad\Rightarrow\quad \hat{x}=(A^*A)^{-1}A^*b.\]

**Normal equations** from orthogonality: \(b-A\hat{x}\perp\mathcal{R}(A)\).

\(A^*A\succ0\) when \(A\) has full column rank: proof from \(\|Ax\|^2=x^*(A^*A)x\ge0\) with equality only for \(x=0\).

**Numerically:** Use QR or SVD; avoid forming \(A^*A\).

### Random Vectors: Covariance and Square Roots

**Covariance matrix:** \(C_x=\mathbb{E}[(x-\mu_x)(x-\mu_x)^*]\). Always Hermitian and PSD; PD if full rank.

**Coloring:** \(y=C_y^{1/2}z\) where \(z\) has identity covariance → \(y\) has covariance \(C_y\).

**Whitening:** \(q=C_y^{-1/2}y\) → \(q\) has identity covariance.

---

## CHAPTER 9: QR FACTORIZATION (L16, L17)

### QR Factorization

Any \(m\times n\) matrix \(A\) (with \(m\ge n\)) can be written:

\[A = QR,\]

where \(Q\) has orthonormal columns and \(R\) is upper triangular.

- **Reduced QR:** \(Q\) is \(m\times n\), \(R\) is \(n\times n\).
- **Full QR:** \(Q\) is \(m\times m\) unitary, \(R\) is \(m\times n\).

### Gram-Schmidt Process

Build orthonormal \(q_1,\ldots,q_n\) from columns \(a_1,\ldots,a_n\) of \(A\):

\[q_k = \frac{a_k - \sum_{i<k}(q_i^*a_k)q_i}{\|a_k - \sum_{i<k}(q_i^*a_k)q_i\|}\]

**Causal constraint:** \(\text{span}\{q_1,\ldots,q_k\}=\text{span}\{a_1,\ldots,a_k\}\) for all \(k\) → upper triangular \(R\).

**Linear dependence:** \(\tilde{a}_k=0\) → no new direction; rank of \(A\) < \(n\).

**Modified Gram-Schmidt:** Orthogonalize against each \(q_k\) immediately after computing it; numerically more stable.

### Circulant Matrices and Fourier Diagonalization (L16)

Circulant matrix: each row is a circular shift of the previous.

**DFT eigenvectors:** Complex exponentials \(f_k=(1,e^{j2\pi k/n},\ldots,e^{j2\pi k(n-1)/n})^T\) are eigenvectors:

\[Hf_k=\hat{h}_k f_k,\]

where \(\hat{h}_k\) is the DFT of the impulse response at frequency \(k\).

**DFT matrix:** \(F=[f_0\ f_1\ \cdots\ f_{n-1}]\). \(F^*F=nI\) (not unitary, but scaled unitary).

**Diagonalization:** \(H=F\Lambda F^{-1}=\tilde{F}\Lambda\tilde{F}^*\) where \(\tilde{F}=F/\sqrt{n}\) is unitary.

**Consequence:** All circulant matrices are normal matrices; convolution in time = multiplication in frequency.

**FFT:** Computes \(\tilde{F}^*x\) in \(O(n\log n)\) instead of \(O(n^2)\).

---

## CHAPTER 10: BLOCK MATRIX TECHNIQUES (L18)

### Block LDU Factorization

For \(A=\begin{bmatrix}A_{11}&A_{12}\\A_{21}&A_{22}\end{bmatrix}\) with \(A_{11}\) invertible:

\[A = \begin{bmatrix}I&0\\A_{21}A_{11}^{-1}&I\end{bmatrix}\begin{bmatrix}A_{11}&0\\0&S_{11}\end{bmatrix}\begin{bmatrix}I&A_{11}^{-1}A_{12}\\0&I\end{bmatrix},\]

where \(S_{11}=A_{22}-A_{21}A_{11}^{-1}A_{12}\) is the **Schur complement** of \(A_{11}\).

**Determinant:** \(\det(A)=\det(A_{11})\det(S_{11})\).

**PD criterion (Hermitian case):** \(A\succ0 \iff A_{11}\succ0\) and \(S_{11}\succ0\).

**Inertia additivity (Hermitian):** \(\text{inertia}(A)=\text{inertia}(A_{11})+\text{inertia}(S_{11})\).

### Matrix Inversion Lemma (Woodbury Identity)

\[(A+BCD)^{-1}=A^{-1}-A^{-1}B(C^{-1}+DA^{-1}B)^{-1}DA^{-1}.\]

**Application:** Rank-one update of matrix inverse; used in Recursive Least Squares (RLS).

---

## CHAPTER 11: MATRIX NORMS (L19, L20)

### Frobenius Norm

\[\|A\|_F=\sqrt{\text{tr}(A^*A)}=\sqrt{\sum_k\sigma_k^2}.\]

### Induced Norms

\[\|A\|_{q,p}=\sup_{\|x\|_p=1}\|Ax\|_q.\]

**Shortcuts:**
- \(\|A\|_{1,1}=\max_j\|a_j\|_1\) (max column 1-norm).
- \(\|A\|_{\infty,\infty}=\max_i\|r_i\|_1\) (max row 1-norm).
- \(\|A\|_{2,2}=\sigma_1(A)\) (largest singular value = operator norm).

**Geometric interpretation:** Unit \(\ell_2\) sphere maps to ellipsoid; longest semi-axis = \(\sigma_1\).

### Schatten \(p\)-Norms

\[\|A\|_{S_p}=\|\sigma\|_p=\left(\sum_k\sigma_k^p\right)^{1/p}.\]

- \(p=1\): nuclear norm \(\|A\|_*=\sum_k\sigma_k\).
- \(p=2\): Frobenius norm.
- \(p=\infty\): operator norm \(\sigma_1\).

**Nuclear norm:** Convex relaxation of rank minimization. Used in matrix completion (e.g., Netflix problem).

### Weighted 2-Norm

\(\|x\|_W=\sqrt{x^*Wx}\) for PD \(W\). Eigenvectors of \(W\) define weighted directions; eigenvalues are weights. Appears naturally in multivariate Gaussian: the precision matrix \(\Sigma^{-1}\) is the weighting.

---

## CHAPTER 12: SINGULAR VALUE DECOMPOSITION (L21, L22)

### Definition

For any \(m\times n\) matrix \(A\) of rank \(r\):

\[A=U\Sigma V^*, \quad \sigma_1\ge\sigma_2\ge\cdots\ge\sigma_r>0.\]

- \(U\): \(m\times m\) unitary (columns = left singular vectors \(u_k\)).
- \(V\): \(n\times n\) unitary (columns = right singular vectors \(v_k\)).
- \(\Sigma\): \(m\times n\) real nonneg diagonal.

**Outer product:** \(A=\sum_{k=1}^r\sigma_ku_kv_k^*\) (rank-1 sum, terms mutually orthogonal).

### Geometric Foundation

Unit sphere in \(\mathbb{C}^n\) maps to an ellipsoid in \(\mathbb{C}^m\). Principal semi-axis lengths = singular values. Semi-axis directions = left singular vectors. Pre-images = right singular vectors.

### Singular Values: Properties

- Always real and nonneg (they are norms of images of unit vectors).
- \(\sigma_k^2\) = eigenvalues of \(A^*A\) (= eigenvalues of \(AA^*\)).
- Right singular vectors = eigenvectors of \(A^*A\).
- Left singular vectors = eigenvectors of \(AA^*\).

### Full and Reduced SVD

- **Full SVD:** \(U\) is \(m\times m\), \(V\) is \(n\times n\).
- **Reduced (compact) SVD:** \(\hat{U}\) is \(m\times r\), \(\hat{\Sigma}\) is \(r\times r\), \(\hat{V}\) is \(n\times r\).

### SVD and Four Fundamental Subspaces

| Subspace | Basis |
|---|---|
| \(\mathcal{R}(A)\) | Columns 1 to \(r\) of \(U\) |
| \(\mathcal{N}(A^*)\) | Columns \(r+1\) to \(m\) of \(U\) |
| \(\mathcal{R}(A^*)\) | Columns 1 to \(r\) of \(V\) |
| \(\mathcal{N}(A)\) | Columns \(r+1\) to \(n\) of \(V\) |

### Norms from SVD

\[\|A\|_2=\sigma_1, \qquad \|A\|_F=\sqrt{\sum_{k=1}^r\sigma_k^2}, \qquad \text{rank}(A)=r.\]

### Best Rank-\(p\) Approximation (Eckart-Young)

\[A_p=\sum_{k=1}^p\sigma_ku_kv_k^*, \qquad \|A-A_p\|_F=\sqrt{\sum_{k=p+1}^r\sigma_k^2}.\]

\(A_p\) is the closest rank-\(p\) matrix in both Frobenius and 2-2 norms.

---

## CHAPTER 13: ABSTRACT INNER PRODUCT SPACES (L23)

### Inner Product Space Axioms

Function \(\langle\cdot,\cdot\rangle:V\times V\to\mathbb{C}\):
1. Conjugate symmetry: \(\langle x,y\rangle=\overline{\langle y,x\rangle}\).
2. Linear in first argument.
3. Positive definite: \(\langle x,x\rangle\ge0\); \(=0\iff x=0\).

**Induced norm:** \(\|x\|=\sqrt{\langle x,x\rangle}\). All geometric concepts (orthogonality, projection, Cauchy-Schwarz) generalize.

**Hilbert space:** complete inner product space.

### Examples

- **\(\mathbb{C}^n\):** \(\langle x,y\rangle=y^*x\). Induces Euclidean norm.
- **\(L^2([a,b])\):** \(\langle f,g\rangle=\int_a^b f(t)\overline{g(t)}dt\). Induces \(L^2\) norm.
- **Matrices:** \(\langle A,B\rangle=\text{tr}(A^*B)\). Induces Frobenius norm. SVD outer products are an orthonormal basis.

### Why Inner Products Enable Closed Forms

Optimization problems involving the induced norm have closed-form solutions via the orthogonality principle: the optimal error is orthogonal to the constraint set. This generalizes least squares, projection, Fourier series coefficients.

### Nuclear Norm and Matrix Completion (L23)

**Matrix completion (Netflix):** Fill in unknown entries of a matrix using the low-rank hypothesis.

**Nuclear norm minimization:** \(\min_B\|B\|_*\) s.t. \(B_{ij}=A_{ij}\) for known entries. Convex; recovers the true low-rank matrix when enough entries are observed (under incoherence conditions).

---

## KEY THEOREMS SUMMARY

| Theorem | Statement |
|---|---|
| Solvability | \(Ax=b\) has solution iff \(b\in\mathcal{R}(A)\) |
| Solution set | All solutions: \(\hat{x}+\mathcal{N}(A)\) |
| Null ⊥ Row | \(\mathcal{N}(A)\perp\mathcal{R}(A^*)\) |
| Rank | Row rank = column rank |
| Cauchy-Schwarz | \(|\langle x,y\rangle|\le\|x\|\|y\|\) |
| Schur | Every square complex \(A=UTU^*\) (\(U\) unitary, \(T\) triangular) |
| Spectral | \(A\) normal \(\iff\) \(A=U\Lambda U^*\) |
| Sylvester | \(A\stackrel\star\sim B\iff\text{inertia}(A)=\text{inertia}(B)\) |
| Cholesky | \(A\succ0\iff A=LL^*\) (lower triangular, positive diagonal) |
| SVD | Any \(A=U\Sigma V^*\) (singular values real, nonneg) |
| Eckart-Young | \(A_p=\sum_{k=1}^p\sigma_ku_kv_k^*\) = best rank-\(p\) approx |
| Woodbury | \((A+BCD)^{-1}=A^{-1}-A^{-1}B(\cdots)^{-1}DA^{-1}\) |
