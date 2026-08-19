# EE 545 — Theoretical Final Exam Prediction (Calibrated)

**Calibration anchor (actual exam, 3 theoretical questions):**
1. Orthogonal projections + projection-matrix properties (\(P^2=P\), \(P^*=P\), range/null-space meaning, why they work).
2. A defined Hermitian PSD — conceptual/algebraic consequences of \(A^*\), \(A^\top\), conjugation, the Hermitian and PSD properties, notation traps.
3. Schur theorem — statement, meaning, proof idea, why every square complex matrix is unitarily triangularizable.

**Inferred selection rule (the key sentence):**
> *The professor asks definitions plus consequences of special matrix structures, especially where notation and proof properties matter.*

**Operational decoding of his style:**
- He picks the **central, repeatedly-motivated structured matrices** (projection, unitary, Hermitian, normal, PD/PSD, Schur/SVD), never peripheral computation.
- Every question is **definition + immediate consequence/property + "why"**, almost no arithmetic.
- He **rotates among the structured-matrix family**: the three tested archetypes were (A) *structured matrix + properties + why*, (B) *Hermitian/PSD notation + algebraic consequence*, (C) *named theorem: statement + proof idea + meaning*. A future final will reuse these archetypes with **different members of the family**.
- He **weaponizes notation**: \(A^\top\) vs \(A^*\), real vs complex, Hermitian vs symmetric, PSD vs PD, "diagonalizable" vs "unitarily diagonalizable", "triangularizable" vs "diagonalizable".
- He likes the **cross-lecture chain**: inner product → Cauchy–Schwarz → orthogonality → projection → unitary → Hermitian/normal → Schur/spectral → SVD.

---

## RANKED PREDICTED QUESTIONS (most → least likely)

### Q1. Normal matrices & the spectral theorem  — **~80%**
**Likely wording.** "Define a normal matrix. Prove that a square complex matrix is **unitarily diagonalizable if and only if it is normal**. Explain how unitary, Hermitian, and skew-Hermitian matrices arise as special cases according to where their eigenvalues lie."

**Why he asks it.** It is the *direct successor* to the Schur question he already set (Schur → normal → spectral is his explicit storyline). It is a named theorem with a short, elegant proof built on Schur, plus a "special cases by eigenvalue location" part that tests notation (real axis vs unit circle vs imaginary axis). Maximum concept, minimum calculation.

**Lecture patterns.** L11–L12 (normal = \(A^*A=AA^*\), unitary diagonalization, eigenspace orthogonality); L14/L16 reviews repeatedly draw the "normal family tree."

**Answer outline.**
- Def: \(A\) normal iff \(A^*A=AA^*\).
- Start from **Schur** \(A=UTU^*\), \(T\) upper triangular. Normality is preserved by unitary similarity, so \(T\) is normal.
- Show a **normal triangular matrix is diagonal**: compare the \((1,1)\) entries of \(T^*T\) and \(TT^*\) ⇒ off-diagonal entries of the first row vanish; induct ⇒ \(T=\Lambda\). Hence \(A=U\Lambda U^*\).
- Converse: if \(A=U\Lambda U^*\) then \(A^*A=U|\Lambda|^2U^*=AA^*\).
- Special cases: eigenvalues **real ⇒ Hermitian**, on the **unit circle ⇒ unitary**, on the **imaginary axis ⇒ skew-Hermitian**; distinct-eigenvalue eigenspaces orthogonal.

**Marks.** 18–20.

**Common mistakes.** Asserting *all* matrices are unitarily diagonalizable; conflating "diagonalizable" with "unitarily diagonalizable"; skipping the triangular-normal⇒diagonal step (the heart of the proof); forgetting eigenvalues are complex in general; saying normal ⇒ Hermitian.

---

### Q2. \(A^*A\) is Hermitian PSD; PD vs PSD  — **~75%**
**Likely wording.** "Let \(A\) be an arbitrary \(m\times n\) **complex** matrix. Prove that \(A^*A\) is Hermitian and positive semidefinite for *every* \(A\). State precisely the condition under which \(A^*A\) is positive **definite**. Give both the eigenvalue and the quadratic-form definitions of PD and PSD and explain the difference."

**Why he asks it.** This is *exactly* his Exam-Question-2 archetype (Hermitian PSD, \(A^*\) vs \(A^\top\), notation traps) but pivoted to the PD/PSD distinction — his favorite danger topic. It rewards the quadratic-form definition and punishes elementwise misreadings of "\(A\ge0\)".

**Lecture patterns.** L12–L15: \(x^*(A^*A)x=\|Ax\|^2\ge0\); PD iff full column rank; "\(A>0\) is not an entrywise statement."

**Answer outline.**
- Hermitian: \((A^*A)^*=A^*A\).
- PSD: \(x^*(A^*A)x=(Ax)^*(Ax)=\|Ax\|_2^2\ge0\) for all \(x\).
- PD iff \(Ax=0\Rightarrow x=0\), i.e. **\(A\) has full column rank** (trivial null space); then \(x\ne0\Rightarrow\|Ax\|^2>0\).
- Definitions: PD ⇔ all eigenvalues \(>0\) ⇔ \(x^*Ax>0\ \forall x\ne0\); PSD ⇔ eigenvalues \(\ge0\) ⇔ \(x^*Ax\ge0\). PSD allows **zero eigenvalues / flat directions**.
- Notation trap: "\(A>0\)" / "\(A\succ0\)" means definiteness, **not** \(a_{ij}>0\).

**Marks.** 15–18.

**Common mistakes.** Using \(A^\top\) for complex \(A\); proving only Hermitian and forgetting PSD (or vice versa); claiming \(A^*A\) is always PD (true only for full column rank); reading \(A\ge0\) entrywise; confusing "no negative eigenvalues" with "all positive."

---

### Q3. Unitary matrices: norm/inner-product preservation & eigenvalues  — **~65%**
**Likely wording.** "Define a unitary matrix. Prove that multiplication by a unitary matrix **preserves the Euclidean inner product and norm**. What are the possible eigenvalues of a unitary matrix, and why? Contrast a unitary matrix with a Hermitian matrix."

**Why he asks it.** Archetype A on a different family member; central to the orthogonality→unitary→Schur chain; tests \(U^*U=I\) vs \(UU^*=I\), the unit-circle eigenvalue fact, and the unitary-vs-Hermitian danger pair.

**Lecture patterns.** L10 (preservation properties), L11–L12 (eigenvalues on unit circle, special case of normal).

**Answer outline.**
- Def: \(U^*U=UU^*=I\) (square); columns orthonormal.
- \(\langle Ux,Uy\rangle=(Uy)^*(Ux)=y^*U^*Ux=y^*x=\langle x,y\rangle\); set \(y=x\) ⇒ \(\|Ux\|_2=\|x\|_2\).
- Eigenvalue: \(Ux=\lambda x\), \(\|x\|=\|Ux\|=|\lambda|\,\|x\|\Rightarrow|\lambda|=1\).
- Contrast: unitary = eigenvalues on unit circle, \(U^{-1}=U^*\); Hermitian = real eigenvalues, \(A=A^*\); both are **normal**.

**Marks.** 12–15.

**Common mistakes.** Only requiring \(U^*U=I\) without noting the square case gives \(UU^*=I\) too; proving norm but not inner-product preservation; claiming eigenvalues are real; confusing unitary with orthogonal-projection or Hermitian.

---

### Q4. SVD: statement, existence, four subspaces  — **~55%**
**Likely wording.** "State the singular value decomposition of an arbitrary \(m\times n\) matrix \(A\). Explain *why it always exists* (proof idea) and how it differs from the eigenvalue decomposition. Show how the SVD provides orthonormal bases for all four fundamental subspaces."

**Why he asks it.** "The best thing that happened to us," heavily motivated; a named decomposition with a conceptual existence argument and a clean subspace payoff — pure concept, no arithmetic. Natural archetype-C question if he rotates past Schur.

**Lecture patterns.** L21–L22 (geometric sphere→ellipsoid, algebraic \(A=U\Sigma V^*\), existence via induced 2-norm + block diagonalization, four subspaces from columns of \(U,V\)).

**Answer outline.**
- \(A=U\Sigma V^*\), \(U,V\) unitary, \(\Sigma\) rectangular diagonal, \(\sigma_1\ge\cdots\ge\sigma_r>0\) real nonneg.
- Existence idea: \(\sigma_1=\|A\|_{2,2}\) gives \(Av_1=\sigma_1u_1\); extend to orthonormal bases; unitary invariance of the 2-norm forces a block-diagonal form (\(w=0\) argument); recurse. Always exists (unlike eigen-decomposition).
- Differs from EVD: two bases vs one; any matrix vs square; real nonneg vs complex.
- Four subspaces: \(\{u_1..u_r\}\)=column space, \(\{u_{r+1}..u_m\}\)=left null space, \(\{v_1..v_r\}\)=row space, \(\{v_{r+1}..v_n\}\)=null space.

**Marks.** 15–20.

**Common mistakes.** Writing \(V\) instead of \(V^*\); claiming \(\Sigma\) square; saying singular values can be complex/negative; confusing left/right singular vectors with the subspaces; conflating SVD with eigen-decomposition.

---

### Q5. Projection theorem / orthogonality principle (abstract)  — **~50%**
**Likely wording.** "State the projection theorem in an inner product space. Prove that the error of the best approximation in a subspace is **orthogonal** to that subspace, and derive the resulting normal equations / Gram-matrix system. Why does an orthonormal basis simplify the solution?"

**Why he asks it.** He already tested projection *matrices*; the *abstract projection theorem* is the conceptual twin and the climax of L23 (he explicitly flagged the exam boundary "through the projection theorem inclusive").

**Lecture patterns.** L9 (orthogonal projection \(P=QQ^*\), \(P=A(A^*A)^{-1}A^*\)); L23 (projection theorem, Gram matrix, orthonormal simplification).

**Answer outline.**
- Minimize \(\|x-\hat x\|\), \(\hat x\in\text{span}\{p_i\}\). Optimal ⇔ \(\langle x-\hat x,p_i\rangle=0\ \forall i\) (orthogonality principle); Pythagoras shows any in-subspace error component increases the norm.
- Write \(\hat x=\sum\alpha_jp_j\) ⇒ Gram system \(G\alpha=b\), \(G_{ij}=\langle p_j,p_i\rangle\), \(b_i=\langle x,p_i\rangle\).
- Orthonormal basis ⇒ \(G=I\) ⇒ \(\alpha_i=\langle x,p_i\rangle\), \(\hat x=\sum\langle x,p_i\rangle p_i\). Least squares = special case.

**Marks.** 15–18.

**Common mistakes.** Stating the result without the orthogonality proof; forgetting the Gram matrix must be invertible (independent \(p_i\)); for the orthogonal projection matrix forgetting \(P^*=P\) (see danger topics).

---

### Q6. Cauchy–Schwarz inequality  — **~45%**
**Likely wording.** "State and prove the Cauchy–Schwarz inequality in \(\mathbb{C}^n\). Explain how it allows the definition of the angle between two vectors, and when equality holds."

**Why he asks it.** Foundational, repeatedly motivated as the gateway to angles/orthogonality; short proof; low calculation.

**Lecture patterns.** L03; reused in L16/L20 norm-inequality discussions.

**Answer outline.** \(|\langle x,y\rangle|\le\|x\|\|y\|\). Proof: \(0\le\|x-\tfrac{\langle x,y\rangle}{\|y\|^2}y\|^2\) expand; equality iff \(x,y\) linearly dependent. Angle: \(\cos\theta=\tfrac{\langle x,y\rangle}{\|x\|\|y\|}\in[-1,1]\).

**Marks.** 10–12.

**Common mistakes.** Forgetting the conjugate in the complex inner product; wrong equality condition; circular use of the angle definition.

---

### Q7. Sylvester's law of inertia & \(A=SS^*\)  — **~40%**
**Likely wording.** "Define the **inertia** of a Hermitian matrix and the relation of **\(*\)-congruence**. State Sylvester's law of inertia. Use it to prove that every positive definite matrix can be written \(A=SS^*\) for some invertible \(S\)."

**Why he asks it.** A definition-plus-consequence chain he repeatedly stressed ("review star-congruence, Sylvester, square roots — used again and again"). Notation-sensitive (\(S B S^*\) vs similarity \(S^{-1}BS\)).

**Lecture patterns.** L14–L15.

**Answer outline.** Inertia \((n_+,n_-,n_0)\). \(A=SBS^*\), \(S\) invertible (not necessarily unitary). Sylvester: \(*\)-congruent ⇔ same inertia. PD has inertia \((n,0,0)\)=inertia of \(I\) ⇒ \(*\)-congruent to \(I\) ⇒ \(A=SIS^*=SS^*\).

**Marks.** 12–15.

**Common mistakes.** Confusing \(*\)-congruence with similarity (eigenvalues vs only signs preserved); thinking \(S\) must be unitary; claiming square root is unique.

---

### Q8. Cholesky factorization & the Schur-complement argument  — **~40%**
**Likely wording.** "State the Cholesky factorization theorem for a positive definite matrix. Outline the proof, and explain *why the Schur complement \(M-vv^*/\alpha\) is positive definite*."

**Why he asks it.** A named factorization whose proof hinges on the *concept* (\(*\)-congruence preserves inertia), not algebra — exactly his taste.

**Lecture patterns.** L14–L15.

**Answer outline.** \(A\succ0\Rightarrow A=LL^*\), \(L\) lower triangular with positive diagonal. Partition, block-eliminate to \(SAS^*=\text{diag}(\alpha,\,M-vv^*/\alpha)\); since \(SAS^*\) is \(*\)-congruent to \(A\succ0\), it is PD, so each diagonal block (incl. the Schur complement) is PD; recurse.

**Marks.** 12–15.

**Common mistakes.** Trying to prove the Schur complement PD directly from the formula (the trap the professor warns against); forgetting the positive-diagonal requirement; confusing with LU.

---

### Q9. Hermitian ⇒ real eigenvalues & orthogonal eigenvectors  — **~35%**
**Likely wording.** "Prove that the eigenvalues of a Hermitian matrix are real and that eigenvectors corresponding to distinct eigenvalues are orthogonal."

**Why he asks it.** Tiny, clean, definition-driven; could appear as a sub-part of the Hermitian/PSD slot.

**Answer outline.** \(Ax=\lambda x\Rightarrow x^*Ax=\lambda\|x\|^2\); \((x^*Ax)^*=x^*A^*x=x^*Ax\) real ⇒ \(\lambda\) real. For \(\lambda\ne\mu\): \(\lambda\langle x,y\rangle=\langle Ax,y\rangle=\langle x,Ay\rangle=\mu\langle x,y\rangle\Rightarrow\langle x,y\rangle=0\).

**Marks.** 8–12.

**Common mistakes.** Dropping conjugates; assuming real symmetric only; not using Hermitian-ness in the cross term.

---

### Q10. Four fundamental subspaces & orthogonality relations  — **~30%**
**Likely wording.** "Define the four fundamental subspaces of \(A\). State and justify the orthogonality relations \(\mathcal N(A)\perp\mathcal R(A^*)\) and \(\mathcal N(A^*)\perp\mathcal R(A)\). How does the SVD exhibit orthonormal bases for all four?"

**Why he asks it.** The analysis backbone of the whole \(Ax=b\) storyline; conceptual.

**Marks.** 12–15.

**Common mistakes.** Mixing up which space pairs with which; forgetting dimensions sum to \(n\) (or \(m\)); confusing row space with column space.

---

## DANGER TOPICS (simple-looking, high test-probability)

| Trap | What students confuse | What to say |
|---|---|---|
| \(A^*\) vs \(A^\top\) | use transpose for complex matrices | \(A^*=\bar A^\top\); they coincide only for real matrices |
| Hermitian vs symmetric | "symmetric" is the **real** case | Hermitian \(A=A^*\); symmetric \(A=A^\top\) (real) |
| PSD vs PD | "no negatives" vs "all positive" | PSD: \(\lambda\ge0\), \(x^*Ax\ge0\) (flat dirs allowed); PD: \(\lambda>0\), strict |
| projection vs **orthogonal** projection | both satisfy \(P^2=P\) | oblique projection: \(P^2=P\) only; orthogonal: \(P^2=P\) **and** \(P^*=P\) |
| diagonalizable vs **unitarily** diagonalizable | general \(T\) vs unitary \(U\) | unitarily diagonalizable ⇔ **normal**; diagonalizable is weaker |
| Schur vs diagonalization | triangular always vs diagonal sometimes | Schur \(A=UTU^*\) exists for **every** square \(A\); diagonalization may fail |
| unitary vs Hermitian | both "nice" normal matrices | unitary: \(|\lambda|=1\), \(U^*U=I\); Hermitian: \(\lambda\in\mathbb R\), \(A=A^*\) |
| normal vs Hermitian | Hermitian ⊊ normal | normal: \(A^*A=AA^*\) (eigenvalues anywhere); Hermitian: real eigenvalues |
| similarity vs \(*\)-congruence | \(S^{-1}BS\) vs \(SBS^*\) | similarity preserves eigenvalues; \(*\)-congruence preserves only **inertia** |
| "\(A>0\)" entrywise vs definite | reads \(a_{ij}>0\) | means positive definite, not elementwise |

---

## EXAM-STRUCTURE ADJUSTMENT — Final emphasizes L13–23

**Fact:** the **midterm** covered L1–12; the **final covers everything but emphasizes the later material (L13–23)**. The calibration exam's three questions (projections L9, Hermitian-PSD L11–14, Schur L11) confirm he *still* pulls the canonical structured matrices whose **roots are early but whose payoff is in L13–23** (normal→spectral, PSD→inertia→Cholesky, Schur→SVD). So the reweighting is: **keep the cross-boundary structured-matrix theorems at the top, raise the pure-L13–23 topics, and lower the pre-L13-only topics** (Cauchy–Schwarz L3, plain unitary L10) since the midterm already owned them.

**Reweighted ranking (final, emphasis L13–23):**

| Rank | Question | Lectures | Prob |
|---|---|---|---|
| 1 | Normal matrices + spectral theorem (unitarily diag. ⇔ normal) | L12–13 | **80%** |
| 2 | \(A^*A\) Hermitian PSD; PD vs PSD; full-column-rank | L13–15 | **75%** |
| 3 | SVD: statement, existence, four subspaces | L21–22 | **70%** ↑ |
| 4 | Inner product spaces + **projection theorem** (he named it the exam boundary) | L23 | **68%** ↑ |
| 5 | **Schatten / nuclear norm** as convex relaxation of rank | L23 | **55%** ↑(new) |
| 6 | Sylvester's law of inertia + \(A=SS^*\) | L14–15 | **55%** ↑ |
| 7 | **Matrix norms:** Frobenius vs operator (\(\sigma_1\)) + unitary invariance | L20 | **52%** ↑(new) |
| 8 | Cholesky + Schur-complement-is-PD argument | L14–15 | **50%** ↑ |
| 9 | **Schur complement / block PD criterion / Woodbury** | L18 | **42%** (new) |
| 10 | **Eckart–Young** best low-rank approximation | L22 | **40%** (new) |
| — | Unitary preserves inner product/norm | L10 | 45% ↓ |
| — | Hermitian ⇒ real eigenvalues / orthogonal eigenvectors | L11–13 | 38% |
| — | Cauchy–Schwarz | L3 | 25% ↓ |

**New L13–23 questions to add to your prep (high emphasis):**

- **Q5' Schatten/nuclear norm (L23, ~55%).** *"Define the Schatten \(p\)-norms of a matrix. Show that \(p=2\) gives the Frobenius norm and \(p=\infty\) the operator norm. Explain why minimizing the **nuclear norm** (\(p=1\)) is a convex relaxation of rank minimization."* Answer: \(\|A\|_{(p)}=\|\sigma\|_p\); \(p=1\) is \(\ell_1\) of singular values ⇒ sparsifies \(\sigma\) ⇒ minimizes #nonzero \(\sigma\) = rank; convex, SDP-solvable; matrix completion / Netflix. Mistakes: confusing Frobenius with operator norm; thinking rank itself is convex.
- **Q7' Matrix norms (L20, ~52%).** *"Distinguish the Frobenius norm from the induced 2-norm. Prove both are unitarily invariant and express each in terms of singular values."* Answer: \(\|A\|_F=\sqrt{\sum\sigma_k^2}=\sqrt{\operatorname{tr}A^*A}\); \(\|A\|_2=\sigma_1\); invariance via trace cyclicity / ratio of invariant norms. **Danger:** \(\|A\|_2\ne\|A\|_F\).
- **Q9' Schur complement (L18, ~42%).** *"For Hermitian \(A=\begin{bmatrix}A_{11}&A_{12}\\A_{21}&A_{22}\end{bmatrix}\), state the PD criterion via the Schur complement. Why is \(A_{11}\succ0\) and \(A_{22}\succ0\) not sufficient?"* Answer: \(A\succ0\iff A_{11}\succ0\) **and** \(S_{11}=A_{22}-A_{21}A_{11}^{-1}A_{12}\succ0\); subtracting a PSD term can break definiteness.
- **Q10' Eckart–Young (L22, ~40%).** *"State the best rank-\(p\) approximation theorem. Why is the rank-\(p\) constraint non-convex, yet the SVD gives the global optimum?"* Answer: truncate SVD to \(p\) terms; error \(\sqrt{\sum_{k>p}\sigma_k^2}\) (Frobenius), \(\sigma_{p+1}\) (2-norm); rank set non-convex (sum of two rank-1 can be rank-2) but SVD truncation is the global optimum.

---

## A. TOP 10 MOST LIKELY EXAM QUESTIONS (final, emphasis L13–23 — see reweighted table above)
1. Normal matrices + spectral theorem (unitarily diagonalizable ⇔ normal) — **80%**
2. \(A^*A\) Hermitian PSD; PD vs PSD; full-column-rank condition — **75%**
3. SVD: statement, why it always exists, four subspaces — **70%**
4. Inner product spaces + projection theorem + Gram normal equations — **68%**
5. Schatten / nuclear norm as convex relaxation of rank — **55%**
6. Sylvester's law of inertia + \(A=SS^*\) for PD — **55%**
7. Matrix norms: Frobenius vs operator + unitary invariance — **52%**
8. Cholesky factorization + Schur-complement-PD argument — **50%**
9. Schur complement / block PD criterion / Woodbury — **42%**
10. Eckart–Young best low-rank approximation — **40%**

## B. TOP 10 DEFINITIONS TO MEMORIZE EXACTLY
1. **Unitary:** \(U^*U=UU^*=I\) (orthonormal columns).
2. **Hermitian:** \(A=A^*\) (real eigenvalues); symmetric = real case \(A=A^\top\).
3. **Normal:** \(A^*A=AA^*\) (⇔ unitarily diagonalizable).
4. **Positive definite / semidefinite:** \(x^*Ax>0\) / \(\ge0\) for all \(x\ (\ne0)\); equivalently eigenvalues \(>0\) / \(\ge0\) (Hermitian assumed).
5. **Orthogonal projection matrix:** \(P^2=P\) **and** \(P^*=P\); \(P=QQ^*\) (orthonormal \(Q\)) or \(A(A^*A)^{-1}A^*\).
6. **Schur factorization:** \(A=UTU^*\), \(U\) unitary, \(T\) upper triangular (every square complex \(A\)).
7. **SVD:** \(A=U\Sigma V^*\), \(U,V\) unitary, \(\Sigma\) rectangular diagonal with \(\sigma_k\ge0\).
8. **Inertia / \(*\)-congruence:** \((n_+,n_-,n_0)\); \(A=SBS^*\), \(S\) invertible.
9. **Inner product (axioms):** conjugate symmetry, linearity in 1st arg, \(\langle x,x\rangle\ge0\) with \(=0\) iff \(x=0\); induced norm \(\sqrt{\langle x,x\rangle}\).
10. **Four fundamental subspaces:** \(\mathcal R(A),\mathcal N(A^*),\mathcal R(A^*),\mathcal N(A)\) with \(\mathcal N(A)\perp\mathcal R(A^*)\), \(\mathcal N(A^*)\perp\mathcal R(A)\).

## C. TOP 10 THEOREM / PROOF IDEAS
1. **Spectral theorem (normal):** Schur \(\Rightarrow\) triangular-normal-is-diagonal (compare \(T^*T,TT^*\) diagonals).
2. **\(A^*A\succeq0\):** \(x^*A^*Ax=\|Ax\|^2\); PD iff full column rank.
3. **Unitary preserves inner product:** \(\langle Ux,Uy\rangle=y^*U^*Ux=\langle x,y\rangle\); \(|\lambda|=1\).
4. **Hermitian real eigenvalues:** \(x^*Ax\) real; distinct eigenvectors orthogonal.
5. **Schur existence:** induct by deflating one (unit) eigenvector into an orthonormal basis.
6. **SVD existence:** \(\sigma_1=\|A\|_{2,2}\); orthonormal extension + 2-norm unitary invariance forces \(w=0\); recurse.
7. **Projection / orthogonality principle:** error \(\perp\) subspace minimizes distance (Pythagoras) ⇒ Gram normal equations.
8. **Sylvester inertia ⇒ \(A=SS^*\):** PD has inertia \((n,0,0)\)= that of \(I\).
9. **Cholesky:** block elimination + \(*\)-congruence preserves inertia ⇒ Schur complement PD ⇒ recurse.
10. **Cauchy–Schwarz:** minimize \(\|x-cy\|^2\) over \(c\); equality iff dependent.

## D. MOCK FINAL EXAM (3 major theoretical questions, calibrated style)

**Question 1 — Structured matrices & the spectral theorem (35 marks).**
(a) Define a **normal** matrix and state precisely what "unitarily diagonalizable" means. (5)
(b) Prove that a square complex matrix is unitarily diagonalizable **if and only if** it is normal. You may invoke the Schur factorization. (15)
(c) For a normal matrix, state where the eigenvalues lie when the matrix is (i) unitary, (ii) Hermitian, (iii) skew-Hermitian, and justify each. (9)
(d) True/false with one-line reasons: "Every diagonalizable matrix is normal"; "\(A=A^\top\) implies \(A\) is Hermitian." (6)

**Question 2 — Hermitian, PSD, and notation (35 marks).**
Let \(A\) be an arbitrary \(m\times n\) **complex** matrix.
(a) Show \(A^*A\) is Hermitian. State why you must write \(A^*\), not \(A^\top\). (6)
(b) Prove \(A^*A\) is positive **semi**definite for every \(A\). (8)
(c) State and justify the exact condition under which \(A^*A\) is positive **definite**. (8)
(d) Give the eigenvalue and quadratic-form definitions of PD and PSD and explain the difference; explain why "\(A\succeq0\)" is **not** an entrywise statement. (8)
(e) If \(A\succ0\) (Hermitian), explain why it can be written \(A=SS^*\) and name one such \(S\). (5)

**Question 3 — A named theorem: statement, meaning, proof idea (30 marks).**
(a) State the **Schur factorization** theorem and explain precisely why it differs from diagonalization. (8)
(b) Give the **proof idea** (deflation via an orthonormal basis) for why every square complex matrix is unitarily triangularizable. (12)
(c) Explain the geometric/conceptual **meaning**: what does "triangular in a unitary basis" tell you, and why is a unitary basis preferable to a general one? (6)
(d) Notation check: contrast Schur triangularization with the SVD \(A=U\Sigma V^*\) — one basis vs two, square vs rectangular, triangular vs diagonal. (4)

*(Marking philosophy mirrors the real exam: credit for correct definitions, correct \(*\)/\(\top\) usage, the key proof step, and the conceptual "why" — minimal credit for computation.)*
