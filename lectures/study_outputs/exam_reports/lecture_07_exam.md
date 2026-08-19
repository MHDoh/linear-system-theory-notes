# Lecture 07 Exam Report

Source boundary: this report uses only `corrected/lecture7_corrected.md`, `study_outputs/lecture_notes/lecture_07_notes.md`, and `study_outputs/audits/lecture_07_audit.md`. It extracts exam-relevant material only.

Probability scale: High = explicitly marked, repeated, proof-heavy, or central to the course logic. Medium = emphasized or conceptually useful but less developed. Low = mentioned as context, software, or preview.

## High Probability

### [High] Existence and uniqueness for `Ax=b`

Why: The transcript explicitly marks this as a likely exam topic and calls `Ax=b` the course's central problem. The instructor also marks the column-space and null-space conditions as important.

Know:

- Existence: `Ax=b` has a solution iff `b in Col(A)`.
- Existence for every right-hand side: `Col(A)=R^m`.
- Uniqueness, assuming a solution exists: `N(A)={0}`.
- If `x_p` solves `Ax=b` and `z in N(A)`, then `x_p+z` also solves it.
- If `N(A)` contains a nonzero vector, then any existing solution is part of an infinite family.

Likely exam form: decide no solution / unique solution / infinitely many solutions from information about `Col(A)`, `N(A)`, and `b`.

### [High] Four fundamental spaces and where they live

Why: The instructor repeatedly returns to the "fundamental picture" of a matrix as a map `A:R^n -> R^m`, and later rank/existence/uniqueness conclusions depend on it.

Know:

- `Col(A)` / range space is in the output space `R^m`.
- `Row(A)` is in the input space `R^n`.
- `N(A)` is in the input space and is orthogonal to `Row(A)`.
- The left null space is in the output space and is orthogonal to `Col(A)`.
- The transcript's noisy phrase "green space" means the column/range space.

Likely exam form: identify which space answers existence, which answers uniqueness, and which ambient space each subspace belongs to.

### [High] Row rank equals column rank

Why: This is marked with an exam note and a "remember" cue. The instructor recalls the proof idea, so it is proof-heavy.

Know:

- `R_c = dim(Col(A))`.
- `R_r = dim(Row(A))`.
- The theorem is `R_c = R_r`; this common value is `rank(A)`.
- Proof idea: show one inequality by taking a basis on one side and proving corresponding images are linearly independent; apply the same argument to `A^T` for the reverse inequality.
- Since `Col(A) subset R^m` and `Row(A) subset R^n`, `rank(A) <= min(m,n)`.

Likely exam form: state/prove the equality of row and column rank, or use it to justify rank bounds.

### [High] Full rank, rank deficient, and shape-dependent consequences

Why: The instructor spends a long exam-marked section classifying tall, fat, and square matrices. This is a major notation and concept trap.

Know:

| Matrix shape | Rank condition | Exam outcome for `Ax=b` |
| --- | --- | --- |
| Tall, `m>n`, full rank `r=n` | `Row(A)=R^n`, `N(A)={0}` | If `b in Col(A)`, the solution is unique. If `b notin Col(A)`, no solution. Existence for all `b` is impossible. |
| Tall, rank deficient `r<n` | `N(A)` nontrivial | If `b in Col(A)`, infinitely many solutions. If `b notin Col(A)`, no solution. |
| Fat, `m<n`, full rank `r=m` | `Col(A)=R^m` | Every `b` has a solution, but solutions are never unique; infinitely many solutions. |
| Fat, rank deficient `r<m` | `Col(A)` does not fill `R^m` | If `b in Col(A)`, infinitely many solutions. If `b notin Col(A)`, no solution. |
| Square, full rank `r=m=n` | row and column spaces fill their ambient spaces | Every `b` has a unique solution; `A` is invertible and `x=A^{-1}b`. |
| Square, rank deficient | both null spaces nontrivial | If `b in Col(A)`, infinitely many solutions. If `b notin Col(A)`, no solution. |

Terminology trap: the instructor uses "degenerate" in the transcript, but notes that "rank deficient" is the standard term.

### [High] Matrix factorization as the strategy for solving systems

Why: The transcript explicitly marks matrix factorizations for solving linear systems as a likely exam topic. The instructor says solving `Ax=b` is the excuse for introducing major factorizations.

Know:

- The central idea is to write a hard matrix as a product of simple matrices:

```math
A = A_1 A_2 \cdots A_k.
```

- Then `Ax=b` becomes a sequence of simple systems.
- The simple matrix types emphasized are diagonal, triangular, orthogonal, and permutation matrices.
- Warning from the audit: square or symmetric-looking does not automatically mean simple; coupling among variables is the real difficulty.

Likely exam form: explain why a factorization turns one hard problem into several easy ones.

### [High] Simple matrix types

Why: The instructor explicitly says "remember" the simple cases and uses them to motivate QR, LU, SVD, and diagonalization.

Know:

- Diagonal matrices: equations are uncoupled; solve `d_i x_i=b_i`. Full-rank square diagonal requires every `d_i != 0`.
- Upper triangular matrices: solve from bottom to top by back substitution.
- Lower triangular matrices: solve from top to bottom by forward substitution.
- Orthogonal matrices: for real `Q`, `Q^{-1}=Q^T`, so `Qx=b` gives `x=Q^T b`.
- For complex matrices, replace transpose with conjugate transpose.
- Permutation matrices are orthogonal and represent row/column swaps or reordered decoupled systems.

Notation trap: triangular substitution acts like applying an inverse, but the instructor stresses that one usually does not explicitly form the inverse.

### [High] QR factorization solve path

Why: QR is the main worked example of the factorization philosophy using orthogonal and triangular factors.

Know:

```math
A=QR
```

where `Q` is orthogonal and `R` is upper triangular. Then:

```math
QRx=b.
```

Let:

```math
y=Rx.
```

Solve:

```math
Qy=b => y=Q^T b,
```

then solve:

```math
Rx=y
```

by back substitution.

Likely exam form: given `A=QR`, show the two-step solution procedure and identify why each step is easy.

### [High] LU factorization and Gaussian elimination

Why: This section has an exam note, a homework-zero reference, and detailed derivation. It is both computational and conceptual.

Know:

- Gaussian elimination aims to kill entries below the diagonal and produce an upper triangular matrix `U`.
- Row replacement examples:

```math
R_2 <- R_2 - 2R_1,\quad R_3 <- R_3 - 3R_1.
```

- Row operations are left multiplication because left multiplication forms linear combinations of rows.
- Right multiplication would form linear combinations of columns.
- The corresponding elimination matrix for those two row operations is:

```math
\begin{bmatrix}
1 & 0 & 0 \\
-2 & 1 & 0 \\
-3 & 0 & 1
\end{bmatrix}.
```

- This matrix is unit lower triangular.
- Standard forward elimination uses earlier rows to modify later rows; this "causality" rule is why elimination matrices are lower triangular.

Likely exam form: construct an elimination matrix for row operations, explain why it is lower triangular, or identify left vs right multiplication.

### [High] Deriving `A=LU` from elimination matrices

Why: The instructor turns the row-operation process into a factorization, and the audit flags unit lower triangular structure as important.

Know:

If elimination matrices produce:

```math
E_k \cdots E_2 E_1 A = U,
```

then moving them to the other side gives:

```math
A = E_1^{-1} E_2^{-1} \cdots E_k^{-1} U = LU.
```

Why `L` is lower triangular:

- The inverse of a lower triangular matrix is lower triangular.
- The product of lower triangular matrices is lower triangular.
- The elimination matrices here are unit lower triangular, and their inverses are also unit lower triangular.
- For these elementary eliminations, the below-diagonal signs flip when taking inverses.

Permutation warning: not every matrix has a plain `LU` without row exchanges; pivoting may require a permutation matrix.

## Medium Probability

### [Medium] One-sided inverses for non-square full-rank matrices

Why: The transcript is noisy here, but the audit identifies this as an omitted/tricky point. It is a natural exam trap because the side and identity size matter.

Know:

- Full-rank tall `A` with shape `m x n`, `m>n`, can have left inverses:

```math
L A = I_n.
```

- Full-rank fat `A` with shape `m x n`, `m<n`, can have right inverses:

```math
A R = I_m.
```

- A full-rank square matrix has a unique two-sided inverse.
- Non-square full-rank matrices generally have infinitely many one-sided inverses.

Likely exam form: choose the valid side of the inverse and the correct identity dimension.

### [Medium] Estimation versus control: whether uniqueness is desirable

Why: The instructor explicitly warns that uniqueness is not always good and non-uniqueness is not always bad. The examples are conceptual applications of the rank discussion.

Know:

- Estimation example: multi-user signal recovery. Users transmit simultaneously in the same band, antennas receive mixtures, and the goal is to recover the true transmitted vector `x`.
- Without prior information, uniqueness requires at least as many independent observations/equations as unknown user signals.
- In the communication example: number of antenna observations should be at least the number of users.
- Prior information can change the count. Sparse or structured vectors may be recoverable with fewer equations under later assumptions.
- Control example: if a full-rank fat matrix maps inputs to outputs, every target output can be reached with infinitely many inputs. Non-uniqueness gives freedom, such as choosing a lower-energy input.

Likely exam form: conceptual short answer comparing why estimation wants uniqueness while control may benefit from non-uniqueness.

### [Medium] Lower triangular matrices as causal systems

Why: The instructor says "do homework" twice near this discussion and explicitly connects it to system theory.

Know:

For time-indexed signals:

```math
y=Lx
```

with lower triangular `L` means:

- `y_1` depends only on `x_1`.
- `y_2` may depend on `x_1,x_2`.
- `y_3` may depend on `x_1,x_2,x_3`.
- No output depends on future inputs.

Likely exam form: explain why lower triangular matrices represent causal finite-time systems.

### [Medium] SVD and symmetric decomposition as products of simple matrices

Why: The instructor marks the factorization family with an exam note and calls this the "story of all factorizations," but these decompositions are only introduced at a high level in Lecture 07.

Know:

- SVD form:

```math
A = U \Sigma V^T
```

where `U` and `V` are orthogonal and `Sigma` is diagonal or diagonal-like.

- Symmetric matrix form:

```math
A = Q \Lambda Q^T
```

where `Q` is orthogonal and `Lambda` is diagonal.

Likely exam form: identify the simple factors, not compute a full decomposition from this lecture alone.

## Low Probability

### [Low] MATLAB backslash operator

Why: This is a software remark rather than a theorem, but the instructor emphasizes that the notation is misleading.

Know:

- `x = A\b` in MATLAB solves a linear system; it is not ordinary division.
- It often uses factorization-based linear algebra methods.
- It can handle non-square systems and may return special solutions such as minimum-norm or least-squares-related answers depending on the case.

Likely exam form: at most a conceptual note that backslash is a solver, not scalar division.

### [Low] Diagonalization preview

Why: This is a next-lecture preview, not developed in Lecture 07.

Know:

- The instructor previews the question of converting matrices into diagonal form because diagonal systems are easiest.
- Treat this as context for later lectures, not a standalone Lecture 07 computation topic.

## Notation Traps and Instructor Warnings

- [High] `Col(A)` answers existence; `N(A)` answers uniqueness.
- [High] `b notin Col(A)` means no solution, so uniqueness is irrelevant.
- [High] Full rank means `rank(A)=min(m,n)`, not "both row and column spaces fill everything" unless `A` is square.
- [High] Tall full rank guarantees uniqueness only if a solution exists; it does not guarantee existence for every `b`.
- [High] Fat full rank guarantees existence for every `b`; it cannot guarantee uniqueness.
- [High] Row space lives in `R^n`; column space lives in `R^m`.
- [High] Row operations are left multiplication. Column operations are right multiplication.
- [High] Plain `A=LU` may fail without row swaps; permutation matrices handle swaps.
- [Medium] `rank deficient` is the preferred term; "degenerate" appears in the transcript but is less standard.
- [Medium] For real orthogonal matrices use `Q^T`; for complex matrices use conjugate transpose.
- [Medium] A one-sided inverse must have the correct side and identity dimension.

## Likely Proof or Conceptual Prompts

- Prove or explain why `b in Col(A)` is the existence condition for `Ax=b`.
- Prove or explain why a nontrivial null space gives infinitely many solutions whenever one solution exists.
- State and prove the proof idea for `dim(Row(A)) = dim(Col(A))`.
- Classify solution behavior for tall, fat, and square matrices under full-rank and rank-deficient cases.
- Explain why matrix factorizations convert one hard system into a sequence of simple systems.
- Solve symbolically using `A=QR`: first orthogonal solve, then triangular solve.
- Solve symbolically using `A=LU`: first lower triangular solve, then upper triangular solve.
- Build an elimination matrix for given row operations and identify why it is lower triangular.
- Derive `A=LU` from `E_k ... E_1 A=U`.
- Explain why lower triangular time-indexed matrices represent causal systems.
