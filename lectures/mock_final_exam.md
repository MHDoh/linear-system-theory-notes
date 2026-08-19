# Linear System Theory — Mock Final Exam
## Based on Lectures 2–23 | EE 545

**Time:** 120 minutes  
**Total:** 100 marks  
**Instructions:** Answers must include precise definitions, conceptual interpretations, and proof ideas where requested. Minimal computation required. Write clearly.

---

## Question 1: Foundations (20 marks)

### 1(a): 8 marks

Define the following terms precisely, giving the exact mathematical condition:

1. **Convex set** (2 marks)
2. **Affine combination** and how it differs from a convex combination (3 marks)
3. **Hyperplane** in \(\mathbb{R}^n\), including what the normal vector represents (3 marks)

---

### 1(b): 6 marks

Define the **Euclidean inner product** on \(\mathbb{C}^n\) and the associated **Euclidean norm**. Then:

(i) State the Cauchy-Schwarz inequality.  
(ii) Explain why Cauchy-Schwarz is needed to define the **angle** between two vectors in \(\mathbb{C}^n\).  
(iii) What does it mean for two vectors to be **orthogonal**?

---

### 1(c): 6 marks

A student defines a function \(f(x) = \sum_{k=1}^n x_k^2 - 2\) on \(\mathbb{R}^n\). Is \(f\) a norm? Justify your answer by checking each norm axiom carefully, pointing out which axiom fails (if any).

---

## Question 2: Fundamental Subspaces and \(Ax=b\) (25 marks)

### 2(a): 8 marks

Let \(A\) be an \(m\times n\) matrix.

(i) Define all four fundamental subspaces of \(A\): the column space, row space, null space, and left null space. State the ambient space (input or output) for each. (4 marks)  
(ii) State the orthogonality relationships between these subspaces and give the direct sum decompositions of the input space and output space. (4 marks)

---

### 2(b): 5 marks

**Prove** that \(Ax = b\) has a solution if and only if \(b \in \mathcal{R}(A)\).

---

### 2(c): 5 marks

Suppose \(x_0\) is one solution of \(Ax = b\).

(i) **Prove** that every solution has the form \(x_0 + z\) for some \(z \in \mathcal{N}(A)\).  
(ii) State the condition on \(A\) that makes the solution **unique**.

---

### 2(d): 7 marks

(i) Define **rank** of \(A\). State (without proof) that row rank equals column rank. (2 marks)  
(ii) A matrix \(A\) is \(3\times 5\). Answer the following: Can \(Ax=b\) have a unique solution for every \(b\in\mathbb{R}^3\)? Can \(Ax=b\) have a solution for every \(b\in\mathbb{R}^3\)? Explain using rank and shape. (5 marks)

---

## Question 3: Basis Change, Eigenvalues, and Factorizations (20 marks)

### 3(a): 5 marks

Explain why changing the basis from the standard basis to a basis given by columns of an invertible matrix \(T\) changes the representation of a linear map \(A\) to \(T^{-1}AT\).

---

### 3(b): 6 marks

(i) Define **eigenvalue**, **eigenvector**, and **eigenspace**. What is the **characteristic polynomial**, and how are eigenvalues related to it? (3 marks)  
(ii) State when a matrix \(A\) is **diagonalizable**. Express the diagonalization as \(A = T\Lambda T^{-1}\) and explain what the columns of \(T\) must be. (3 marks)

---

### 3(c): 5 marks

**State the Schur factorization theorem.** Give the proof idea (you may describe the inductive structure without writing full detail).

---

### 3(d): 4 marks

Explain the distinction between **diagonalizable** and **unitarily diagonalizable** matrices. What class of matrices is exactly the unitarily diagonalizable matrices?

---

## Question 4: Structured Matrices (25 marks)

### 4(a): 8 marks

(i) Define a **unitary matrix**. Prove that a unitary matrix preserves the Euclidean norm: \(\|Ux\|_2 = \|x\|_2\). (4 marks)  
(ii) Prove that all eigenvalues of a unitary matrix lie on the unit circle \(|\lambda|=1\). (4 marks)

---

### 4(b): 8 marks

(i) Define a **Hermitian matrix**. Prove that \(x^*Ax \in \mathbb{R}\) for every Hermitian \(A\) and every \(x\in\mathbb{C}^n\). (4 marks)  
(ii) Using (i), prove that all eigenvalues of a Hermitian matrix are **real**. (4 marks)

---

### 4(c): 5 marks

Define **positive definite**, **positive semidefinite**, and **indefinite** Hermitian matrices. Give the quadratic form interpretation for each. Explain how the eigenvalue sign pattern determines the shape of the quadratic function \(f(x) = x^*Ax\).

---

### 4(d): 4 marks

State the **spectral theorem for normal matrices** and give the proof idea. How does it relate Hermitian and unitary matrices as special cases?

---

## Question 5: SVD and Norms (10 marks)

### 5(a): 5 marks

(i) State the Singular Value Decomposition (SVD): \(A = U\Sigma V^*\). Describe each factor and its dimensions for an \(m\times n\) matrix. (2 marks)  
(ii) Express the **rank**, the **induced 2-2 norm**, and the **Frobenius norm** of \(A\) in terms of its singular values. (3 marks)

---

### 5(b): 5 marks

(i) What is the **best rank-\(p\) approximation** of a matrix \(A\) (state the Eckart-Young result)? (2 marks)  
(ii) Define the **nuclear norm** \(\|A\|_*\) and explain its role as a convex relaxation of rank minimization. (3 marks)

---

## MARKING GUIDELINES

### Q1(a) — 8 marks

**Convex set (2 marks):** Set \(S\) is convex if for any \(x,y\in S\) and \(t\in[0,1]\): \(tx+(1-t)y\in S\). (Award 1 mark for condition, 1 for "for all pairs".)

**Affine vs. convex combination (3 marks):** Affine: \(\sum\alpha_ix_i\) with \(\sum\alpha_i=1\), no nonnegativity. Convex adds \(\alpha_i\ge0\). Award 1 mark each for correct affine definition, nonnegativity distinction, and example or illustration.

**Hyperplane (3 marks):** \(\{x:a^Tx=b\}\), \(a\ne0\). Normal vector \(a\) is orthogonal to the hyperplane; it determines its orientation. Two half-spaces on either side. Award 1 mark each for formula, normal vector role, dimensionality statement (2D: line, 3D: plane).

### Q1(b) — 6 marks

**Inner product** \(\langle x,y\rangle = y^*x\) (1). **Norm** \(\|x\|=\sqrt{x^*x}\) (1). **Cauchy-Schwarz** \(|\langle x,y\rangle|\le\|x\|\|y\|\) (1). Needed so \(\cos\theta=\langle x,y\rangle/(\|x\|\|y\|)\) lies in \([-1,1]\) (1). Orthogonal iff \(\langle x,y\rangle=0\) (2).

### Q1(c) — 6 marks

\(f(x) = 0\) for \(x = 0\) gives \(f(0) = -2 \ne 0\). Norm axiom: \(f(x)=0\iff x=0\) fails since \(f(0)\ne0\). Also: scaling \(f(\alpha x) = \alpha^2\sum x_k^2 - 2 \ne |\alpha|^2(\sum x_k^2-2)\) in general. Full marks for identifying the definiteness failure and checking scaling.

### Q2(a) — 8 marks

Award 0.5 marks per subspace definition + 0.5 for correct ambient space × 4 = 4 marks.  
Orthogonality \(\mathcal{N}(A)\perp\mathcal{R}(A^*)\) and \(\mathcal{N}(A^*)\perp\mathcal{R}(A)\): 2 marks.  
Direct sums: 2 marks.

### Q2(b) — 5 marks

Forward: if \(Ax_0=b\) then \(b=\sum x_{0,i}a_i\in\mathcal{R}(A)\). Backward: if \(b=\sum\alpha_ia_i\) then \(x=\alpha\) gives \(Ax=b\). 2.5 marks each direction.

### Q2(c) — 5 marks

Proof: if \(Ax_1=b\) and \(Ax_0=b\), then \(A(x_1-x_0)=0\) so \(z=x_1-x_0\in\mathcal{N}(A)\); conversely \(A(x_0+z)=b\) for any \(z\in\mathcal{N}(A)\). 4 marks.  
Uniqueness: \(\mathcal{N}(A)=\{0\}\). 1 mark.

### Q3(c) — 5 marks

**Statement:** Every square complex \(A\) can be written \(A=UTU^*\) where \(U\) unitary and \(T\) upper triangular. 2 marks.  
**Proof idea:** (1) Find an eigenvector of \(A\), normalize it to \(u_1\). (2) Extend to orthonormal basis. (3) In this basis \(A\) has block upper triangular form. (4) Apply recursion to the lower-right \((n-1)\times(n-1)\) block. 3 marks.

### Q4(b) — 8 marks

Proof \(x^*Ax\in\mathbb{R}\): Take complex conjugate of scalar: \((x^*Ax)^* = x^*A^*x = x^*Ax\) since \(A=A^*\). So it equals its conjugate, hence real. 4 marks.  
Eigenvalue proof: For \(Ax=\lambda x\), \(x^*Ax=\lambda x^*x\). LHS real, \(x^*x>0\), so \(\lambda\) real. 4 marks.

---

## APPENDIX: FORMULA REFERENCE

Allow students to use this formula reference.

| Symbol | Meaning |
|---|---|
| \(A^*\) | Conjugate transpose of \(A\) |
| \(\mathcal{R}(A)\) | Column space/range space of \(A\) |
| \(\mathcal{N}(A)\) | Null space of \(A\) |
| \(A\succ0\) | \(A\) is positive definite |
| \(A\succeq0\) | \(A\) is positive semidefinite |
| \(U\Sigma V^*\) | Singular Value Decomposition |
| \(\sigma_k\) | \(k\)-th singular value (ordered \(\sigma_1\ge\sigma_2\ge\ldots\)) |
| \(\|A\|_F\) | Frobenius norm of \(A\) |
| \(\|A\|_2\) | Induced 2-2 norm (= \(\sigma_1\)) |
| \(\|A\|_*\) | Nuclear norm (= \(\sum_k\sigma_k\)) |
