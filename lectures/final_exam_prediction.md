# Linear System Theory Final Exam Prediction

Scope: corrected Lectures 2-12. This is not a lecture summary. It is a prediction of what a theory-heavy final exam from this professor is likely to test.

Main prediction: the exam will be built around the geometric meaning of linear algebra: vector spaces, subspaces, inner products, orthogonality, projections, rank/existence/uniqueness, eigen-structure, and structured matrices such as unitary, Hermitian, normal, and positive definite matrices.

## Part 1: Lecture Importance Ranking

| Rank | Topic | Probability | Why likely | Lecture evidence |
|---:|---|---:|---|---|
| 1 | Inner products, norms, orthogonality, and projections | 98% | This is the backbone connecting geometry, vector spaces, unitary matrices, projection matrices, least squares, and spectral properties. The professor repeatedly emphasizes "very important" and returns to the same geometry. | L3: Euclidean norm, inner product, Cauchy-Schwarz, angles, orthogonality. L8: complex inner product. L9: orthonormal bases, projections, projection matrices. L10: unitary maps preserve norms and inner products. L11-L12: orthogonal eigenspaces. |
| 2 | Fundamental subspaces, rank, and existence/uniqueness of \(Ax=b\) | 97% | The professor calls \(Ax=b\) the "mother of all problems" and uses it as the excuse to introduce vector spaces. This is exactly the kind of conceptual framework he tests. | L3: unique/no/infinite solutions via hyperplane intersections. L5: column space and existence. L6: row space, null space, left null space, rank as common row/column dimension. L7: full rank and existence/uniqueness. |
| 3 | Unitary/orthogonal matrices and their interpretations | 96% | Treated as one of the three "simple" matrix families for solving systems. The professor explicitly says they are important and proves preservation/eigenvalue properties. | L9: unitary as complex version of orthogonal matrices. L10: \(U^{-1}=U^*\), columns/rows orthonormal, norm/inner product/energy preservation, eigenvalues on unit circle, determinant magnitude one. L11-L12 revisit unitary matrices before normal/Hermitian matrices. |
| 4 | Hermitian matrices, real quadratic forms, and real eigenvalues | 95% | The professor explicitly says Hermitian matrices are "very important", ties them to optimization and stochastic processes, and uses them to introduce positive definite matrices. | L11: \(A^*=A\), \(x^*Ax\) real, Hermitian matrices are important. L12: Hermitian properties, eigenvalues real, orthogonal eigenspaces, quadratic functions. |
| 5 | Normal matrices and unitary diagonalization | 94% | This topic synthesizes unitary and Hermitian matrices. It appears as a generalization of a property already proved twice: orthogonal eigenspaces for distinct eigenvalues. | L12: normal matrices, equivalent conditions, normal iff unitarily diagonalizable, matrix energy equals eigenvalue energy. L11 previews normal matrices as the larger family containing unitary and Hermitian matrices. |
| 6 | Positive definite, positive semidefinite, negative definite, indefinite | 92% | Introduced as a classification of Hermitian matrices by eigenvalue sign and directly linked to the shape of quadratic functions. Strong conceptual exam fit. | L12: explicit [LIKELY EXAM TOPIC] on positive definite and indefinite matrices. L11-L12: quadratic forms and optimization motivation. |
| 7 | Diagonalization, basis change, eigenvalues/eigenvectors, characteristic polynomial | 91% | The professor frames diagonalization as a central historical and algorithmic goal: choose a clever basis to simplify a linear transformation. | L8: [LIKELY EXAM TOPIC] diagonalization by basis change; eigenvalues/eigenvectors; characteristic polynomial. L9-L12: revisited through projections, unitary matrices, Schur, normal matrices. |
| 8 | Vector spaces, subspaces, span, basis, linear independence | 90% | Foundational for nearly every later topic. The professor uses these concepts to generalize geometry beyond 2D/3D and to analyze \(Ax=b\). | L4: [LIKELY EXAM TOPIC] vector spaces/subspaces and span/basis/linear independence. L5-L7: all solution analysis depends on them. |
| 9 | Schur factorization and triangularization | 88% | Schur is repeatedly framed as the theorem that every square matrix can be triangularized by a unitary basis. Conceptual proof idea likely. | L10: future topic from triangularization. L11: [LIKELY EXAM TOPIC] Schur factorization theorem; proof begins with eigenvector and extends to an orthonormal basis. L12: used to prove normal matrices are unitarily diagonalizable. |
| 10 | Orthogonal projection matrices and least-squares interpretation | 86% | Projection is introduced as a "very important concept" with applications to estimation and least squares. It is not calculation-heavy if asked conceptually. | L9: projection over vector/subspace; \(P=QQ^*\); range interpretation; arbitrary basis formula mentioned; least squares projection of \(b\) onto range space. |
| 11 | Linear, affine, convex combinations; convex sets/hulls | 82% | Early lectures repeatedly use this to connect algebraic weights to geometry, grading examples, expectation, and optimization. | L2: [LIKELY EXAM TOPIC] affine and convex combinations, convex sets/hulls. L3: revisited while defining norm/geometry. |
| 12 | Hyperplanes and half-spaces | 80% | This is the first major example of "algebra becomes geometry" and reappears in linear systems as intersection of solution sets. | L2: [LIKELY EXAM TOPIC] hyperplanes/half-spaces. L3-L4: hyperplanes from inner products and systems of equations. |
| 13 | Complex vector spaces, Hermitian transpose, complex inner product | 78% | Necessary for unitary/Hermitian/normal matrices. Common source of student mistakes, so likely as a definition/comparison question. | L8: complex inner product and conjugate symmetry. L9-L12: all structured matrices use \(A^*\). |
| 14 | Matrix factorization philosophy: diagonal, triangular, orthogonal/simple systems | 75% | The professor uses solving \(Ax=b\) to motivate factorizations. Likely conceptual, not computational. | L7: diagonal, triangular, orthogonal as simple systems; factorizations convert arbitrary problems into sequences of simple ones. L10-L11: QR/LU/Schur references. |
| 15 | Row rank equals column rank | 74% | It is a proof-based result connecting row space and column space, exactly matching the professor's style. | L6-L7: proof idea using basis of row space and images under \(A\); rank defined as common dimension. |
| 16 | Full row/column rank, left/right inverse, tall/fat matrix logic | 72% | The professor explains right inverse from full row rank and relates matrix shape to existence/uniqueness. | L5: full row rank and right inverse [LIKELY EXAM TOPIC]. L7: full rank implications for tall/fat matrices. |
| 17 | Trace and Frobenius/eigenvalue energy identity for normal matrices | 68% | Less central, but explicitly developed in L12 as a useful algebraic technique and equivalent normal condition. | L12: trace as simple linear operator; matrix element energy equals eigenvalue energy for normal/unitarily diagonalizable matrices. |
| 18 | LTI convolution matrices, Toeplitz/circulant, Fourier basis | 62% | Likely as an application/conceptual bridge rather than a core proof. It appears around homework and connects unitary/Fourier/circulant. | L10-L12: Fourier transform, convolution matrices, Toeplitz/circulant, lossless systems as unitary/orthogonal. |
| 19 | Cauchy-Schwarz inequality and angle/cosine interpretation | 60% | It appeared with proof flavor and supports the definition of angles. Moderate likelihood as a proof idea. | L3-L4: Cauchy-Schwarz, angle definition, cosine distance, proof mentioned/homework. |
| 20 | SVD | 45% | Mentioned as a future/general factorization, but not fully developed in Lectures 2-12. More likely as "what is the idea?" than a theorem to prove. | L7-L9 and L11: SVD mentioned as using different bases for input/output, but not yet central. |

## Part 2: Predicted Exam Questions

### Very High Probability Questions, 90%+

1. Exact wording: "Define the Euclidean inner product and Euclidean norm. Explain how the inner product gives a notion of angle and orthogonality in high-dimensional spaces."
   Why: This is the main bridge from algebraic vectors to geometry, repeated in L3, L8, L9, and L10.
   Expected answer: \(\langle x,y\rangle=x^Ty\) in real case, \(\langle x,y\rangle=x^*y\) or the course convention equivalent in complex case; \(\|x\|=\sqrt{\langle x,x\rangle}\); angle via \(\cos\theta=\langle x,y\rangle/(\|x\|\|y\|)\) in real case; orthogonal means inner product zero; Cauchy-Schwarz makes cosine well-defined.

2. Exact wording: "For \(Ax=b\), explain the roles of the column space, row space, null space, and left null space. State the conditions for existence and uniqueness."
   Why: This is the central L5-L7 storyline.
   Expected answer: \(b\in R(A)\) iff at least one solution exists; uniqueness iff \(N(A)=\{0\}\) iff row space is the whole input space; all solutions are \(x_0+N(A)\); left null space is \(N(A^T)\) or \(N(A^*)\); rank is common dimension of row and column spaces.

3. Exact wording: "Define a unitary matrix. Prove that a unitary matrix preserves Euclidean norm and inner product. What can be said about its eigenvalues?"
   Why: L10 proves this and the professor calls unitary matrices important.
   Expected answer: \(U^*U=UU^*=I\), so \(U^{-1}=U^*\); columns and rows form orthonormal bases; \(\|Ux\|^2=x^*U^*Ux=x^*x\); \(\langle Ux,Uy\rangle=\langle x,y\rangle\); if \(Ux=\lambda x\), then \(|\lambda|=1\).

4. Exact wording: "Define a Hermitian matrix. Show that \(x^*Ax\) is real for a Hermitian matrix and conclude that the eigenvalues of a Hermitian matrix are real."
   Why: L11-L12 strongly emphasize real-valued quadratic forms and Hermitian spectral properties.
   Expected answer: \(A^*=A\); \((x^*Ax)^*=x^*A^*x=x^*Ax\), so it is real; for \(Ax=\lambda x\), \(x^*Ax=\lambda x^*x\); denominator \(x^*x>0\), so \(\lambda=(x^*Ax)/(x^*x)\in\mathbb R\).

5. Exact wording: "What is a normal matrix? State equivalent characterizations and explain why normal matrices are important."
   Why: L12 generalizes unitary and Hermitian matrices into normal matrices.
   Expected answer: \(A^*A=AA^*\); equivalent to unitarily diagonalizable \(A=U\Lambda U^*\); eigenvectors/eigenspaces can form an orthonormal basis; sum of squared magnitudes of entries equals sum of squared magnitudes of eigenvalues; Hermitian, unitary, and skew-Hermitian are examples.

6. Exact wording: "Define positive definite, positive semidefinite, negative definite, negative semidefinite, and indefinite Hermitian matrices. Explain their relation to quadratic forms."
   Why: Explicit [LIKELY EXAM TOPIC] in L12 and strongly linked to optimization.
   Expected answer: classification by signs of eigenvalues; positive definite iff all eigenvalues \(>0\) iff \(x^*Ax>0\) for all nonzero \(x\); PSD iff eigenvalues \(\ge 0\) iff \(x^*Ax\ge0\); indefinite has both positive and negative eigenvalues and quadratic form bends up in some directions and down in others.

7. Exact wording: "Explain diagonalization as a basis-change problem. What is the connection between diagonalization and eigenvectors?"
   Why: L8 frames eigenvalues through the attempt to make \(T^{-1}AT\) diagonal.
   Expected answer: changing basis from standard basis to columns of \(T\) represents the same linear map by \(T^{-1}AT\); if columns of \(T\) are eigenvectors, \(AT=T\Lambda\), hence \(T^{-1}AT=\Lambda\); diagonalizable iff enough linearly independent eigenvectors form a basis.

### High Probability Questions, 70-90%

8. Exact wording: "State Schur's factorization theorem and give the proof idea."
   Why: Explicit [LIKELY EXAM TOPIC] and used to prove normal matrix diagonalization.
   Expected answer: Every square complex matrix \(A\) can be written \(A=UTU^*\), where \(U\) is unitary and \(T\) is upper triangular. Proof idea: choose one eigenvector, extend it to an orthonormal basis, get a block upper triangular form, then repeat recursively/inductively.

9. Exact wording: "What is an orthogonal projection onto a subspace? Derive the projection matrix when the subspace has orthonormal basis \(Q\)."
   Why: Projection receives heavy emphasis in L9 and is connected to least squares.
   Expected answer: projection \(p\in V\) such that \(x-p\perp V\); if columns of \(Q\) are orthonormal, \(p=QQ^*x\); \(P=QQ^*\); \(P=P^*\), \(P^2=P\), range\(P=V\), \(Px=x\) for \(x\in V\).

10. Exact wording: "Define vector space and subspace. Why is the subspace concept central to solving \(Ax=b\)?"
    Why: L4 calls subspace a major tool for existence/uniqueness.
    Expected answer: vector space has vectors, scalars, vector addition, scalar multiplication satisfying axioms; subspace is subset closed under addition and scalar multiplication and contains zero; column, row, null, and left null spaces are subspaces determining solvability.

11. Exact wording: "Define span, basis, and linear independence. Explain the difference between a basis and a dictionary/redundant spanning set."
    Why: L4 repeatedly motivates basis as nonredundant representation.
    Expected answer: span is all linear combinations; linearly independent means only trivial linear combination gives zero; basis is linearly independent spanning set; redundant set spans but contains unnecessary vectors.

12. Exact wording: "Prove or explain why row rank equals column rank."
    Why: L6-L7 gave an explicit proof idea.
    Expected answer: choose basis for row space; map its basis vectors by \(A\) into column space and show independence using \(N(A)\perp row(A)\); get row rank <= column rank; reverse with \(A^T\) gives equality.

13. Exact wording: "Explain full row rank, full column rank, left inverse, and right inverse. Which cases imply existence or uniqueness?"
    Why: L5-L7 tie shape/rank to inverse type.
    Expected answer: full row rank \(rank(A)=m\) gives row/range covers target and \(AD=I_m\) right inverse, existence for every \(b\), usually not unique if fat; full column rank \(rank(A)=n\) gives \(N(A)=0\), uniqueness if solution exists, left inverse exists.

14. Exact wording: "Compare a general diagonalization with unitary diagonalization. Why is unitary diagonalization stronger?"
    Why: L8-L12 distinguishes diagonalizable, unitarily diagonalizable, and normal.
    Expected answer: diagonalizable uses any invertible \(T\); unitarily diagonalizable uses \(U^*=U^{-1}\), orthonormal eigenbasis, preserves geometry, numerically/geometrically special; normal matrices exactly unitarily diagonalizable.

15. Exact wording: "Explain why a causal LTI convolution matrix is lower triangular Toeplitz. What extra property corresponds to a lossless system?"
    Why: L11-L12 connect system theory to matrix structure.
    Expected answer: causality means output at time \(n\) depends only on current/past inputs, giving lower triangular; time invariance means diagonals repeat, giving Toeplitz; circular convolution gives circulant; lossless/energy-preserving gives unitary or real orthogonal matrix.

### Medium Probability Questions, 50-70%

16. Exact wording: "State and prove the Cauchy-Schwarz inequality, or explain why it is needed to define the angle between vectors."
    Why: L3-L4 mention proof and angle/cosine interpretation.
    Expected answer: \(|\langle x,y\rangle|\le\|x\|\|y\|\); proof from nonnegativity of \(\|x-\alpha y\|^2\) or normalized vector trick; guarantees cosine ratio lies in \([-1,1]\).

17. Exact wording: "Define a hyperplane and half-space. Explain how one linear equation defines a hyperplane."
    Why: Strong in L2-L3 but early/foundational.
    Expected answer: hyperplane \(\{x:a^Tx=b\}\); \(a\) is normal vector; \(a^Tx>b\) and \(a^Tx<b\) define half-spaces; in 2D line, in 3D plane, in higher dimensions still same concept.

18. Exact wording: "Define linear, affine, and convex combinations. What are affine hull and convex hull?"
    Why: Explicit L2 likely exam topic.
    Expected answer: linear combination arbitrary weights; affine weights sum to one; convex weights sum to one and are nonnegative; affine hull is all affine combinations; convex hull is all convex combinations.

19. Exact wording: "Use trace to relate matrix energy to eigenvalue energy for a normal matrix."
    Why: L12 develops trace as an algebraic technique.
    Expected answer: Frobenius energy \(\sum_{ij}|a_{ij}|^2=tr(A^*A)\); if \(A=U\Lambda U^*\), trace cyclicity gives \(tr(A^*A)=tr(\Lambda^*\Lambda)=\sum_i|\lambda_i|^2\).

20. Exact wording: "What is the significance of the Fourier basis for circular convolution?"
    Why: Mentioned with homework; likely application question.
    Expected answer: DFT basis is orthogonal/orthonormal after normalization; it diagonalizes circulant matrices; circular convolution in time becomes multiplication in frequency.

## Part 3: Definition Questions

| Definition | Exact statement | Often forgotten | Difficulty |
|---|---|---|---|
| Vector and dimension | A vector in \(\mathbb R^n\) or \(\mathbb C^n\) is an ordered \(n\)-tuple/column of scalars. | Order matters; components have meaning tied to coordinates/features. | Easy |
| Linear combination | \(\sum_{i=1}^m \alpha_i x_i\), where \(\alpha_i\) are scalars and \(x_i\) are vectors in the same vector space. | Vectors must belong to same space; weights are arbitrary. | Easy |
| Affine combination | A linear combination with \(\sum_i\alpha_i=1\). | Negative weights are allowed. | Medium |
| Convex combination | A linear combination with \(\sum_i\alpha_i=1\) and \(\alpha_i\ge0\). | Both conditions are required. | Easy |
| Convex set | A set \(S\) is convex if for any \(x,y\in S\) and \(0\le t\le1\), \(tx+(1-t)y\in S\). | It is enough to check line segments between pairs. | Easy |
| Convex hull | The set of all convex combinations of points from \(S\). | It is the smallest convex set containing \(S\). | Medium |
| Affine hull | The set of all affine combinations of points from \(S\). | It can be an infinite line/plane, not just the polygon between points. | Medium |
| Hyperplane | \(H=\{x:a^Tx=b\}\) or \(H=\{x:a^*x=b\}\), with nonzero normal vector \(a\). | It need not pass through the origin unless \(b=0\). | Medium |
| Half-space | One side of a hyperplane, e.g. \(\{x:a^Tx\ge b\}\) or \(\{x:a^Tx\le b\}\). | Strict vs non-strict inequality changes boundary inclusion. | Easy |
| Norm | A function \(\|\cdot\|\) satisfying positivity, definiteness, homogeneity, and triangle inequality. | \(\|x\|=0\) only for \(x=0\). | Medium |
| Euclidean norm | \(\|x\|_2=\sqrt{x^Tx}\) in real case, \(\sqrt{x^*x}\) in complex case. | Complex case needs conjugates. | Easy |
| Inner product, real | \(\langle x,y\rangle=x^Ty\), or a general map satisfying linearity, symmetry, and positive definiteness. | It is not just multiplication; it induces geometry. | Medium |
| Inner product, complex | \(\langle x,y\rangle=x^*y\) under the common convention, with conjugate symmetry. | Scaling one argument conjugates depending on convention. | Medium |
| Orthogonal vectors | \(x\perp y\) iff \(\langle x,y\rangle=0\). | Orthogonality depends on the chosen inner product. | Easy |
| Orthogonal set | A set where every distinct pair has zero inner product. | Individual vectors do not have to be unit norm. | Easy |
| Orthonormal set | Orthogonal set whose members all have norm one. | Orthogonal plus normalized, not just orthogonal. | Easy |
| Vector space | A set of vectors with a scalar field, vector addition, and scalar multiplication satisfying the vector space axioms. | It has four ingredients: vector set, scalar set, addition, scalar multiplication. | Medium |
| Subspace | A subset \(S\subseteq V\) that is closed under vector addition and scalar multiplication. | Must contain zero automatically; empty set is not a subspace. | Easy |
| Span | \(span(S)\) is the set of all finite linear combinations of elements of \(S\). | Span is a subspace. | Easy |
| Linear independence | \(\sum_i\alpha_i x_i=0\) implies all \(\alpha_i=0\). | Applies to a set, not one vector alone except by convention. | Medium |
| Basis | A linearly independent set that spans the space. | Both conditions are required. | Easy |
| Column/range space | \(R(A)=\{Ax:x\in\mathbb F^n\}=span\{columns\ of\ A\}\). | It lives in the output/target space. | Medium |
| Row space | Span of the rows of \(A\), equivalently column space of \(A^T\) or \(A^*\). | It lives in the input space. | Medium |
| Null space | \(N(A)=\{x:Ax=0\}\). | It is orthogonal to the row space. | Medium |
| Left null space | \(N(A^T)\) in real case or \(N(A^*)\) in complex case; vectors \(z\) such that \(z^TA=0\) or \(z^*A=0\). | It lives in the output space. | Medium |
| Rank | Common dimension of column space and row space. | Row rank equals column rank; rank <= min(m,n). | Medium |
| Full rank | \(rank(A)=\min(m,n)\). | Meaning differs for tall, fat, and square matrices. | Medium |
| Right inverse | \(D\) such that \(AD=I_m\). | Exists when \(A\) has full row rank; not necessarily \(DA=I\). | Medium |
| Left inverse | \(C\) such that \(CA=I_n\). | Exists when \(A\) has full column rank; not necessarily \(AC=I\). | Medium |
| Eigenvalue/eigenvector | \(Ax=\lambda x\) for nonzero \(x\). \(\lambda\) is eigenvalue, \(x\) is eigenvector. | Eigenvector cannot be zero. | Easy |
| Eigenspace | \(N(A-\lambda I)\). | It includes zero as a subspace, but eigenvectors themselves are nonzero. | Medium |
| Characteristic polynomial | \(p_A(\lambda)=det(\lambda I-A)\) or \(det(A-\lambda I)\), depending on convention. | Roots are eigenvalues; sign convention does not change roots. | Medium |
| Diagonalizable matrix | \(A=T\Lambda T^{-1}\) for invertible \(T\), equivalently \(A\) has a basis of eigenvectors. | Not every matrix is diagonalizable. | Medium |
| Similarity transformation | \(T^{-1}AT\), the representation of the same linear map in a new basis. | Similar matrices have same eigenvalues. | Medium |
| Unitary matrix | \(U^*U=UU^*=I\). Real version: orthogonal matrix \(Q^TQ=QQ^T=I\). | Inverse is conjugate transpose; columns and rows are orthonormal. | Easy |
| Hermitian matrix | \(A^*=A\). Real version: symmetric matrix. | Hermitian does not mean inverse equals conjugate transpose. | Easy |
| Skew-Hermitian matrix | \(A^*=-A\). | Eigenvalues are imaginary or zero, not real in general. | Medium |
| Normal matrix | \(A^*A=AA^*\). | Normal includes unitary and Hermitian but is larger than both. | Medium |
| Orthogonal projection | The closest vector \(p\in V\) to \(x\) such that \(x-p\perp V\). | Orthogonal projection is not the same as any projection/oblique projection. | Medium |
| Projection matrix | Matrix \(P\) with \(P^2=P\); orthogonal projection additionally has \(P^*=P\). | Idempotent alone does not imply orthogonal projection unless Hermitian. | Medium |
| Quadratic form | \(x^*Ax\), especially real-valued when \(A\) is Hermitian. | In complex case use \(x^*\), not \(x^T\). | Medium |
| Positive definite | Hermitian \(A\) with all eigenvalues \(>0\), equivalently \(x^*Ax>0\) for all \(x\ne0\). | Must be Hermitian in this course's classification. | Medium |
| Positive semidefinite | Hermitian \(A\) with eigenvalues \(\ge0\), equivalently \(x^*Ax\ge0\) for all \(x\). | Zero eigenvalues are allowed. | Easy |
| Indefinite | Hermitian \(A\) with both positive and negative eigenvalues. | It means quadratic form can be positive or negative depending on direction. | Medium |
| Toeplitz matrix | Matrix with constant entries along diagonals. | For causal LTI convolution it is lower triangular Toeplitz. | Medium |
| Circulant matrix | Matrix whose rows/columns are cyclic shifts. | Circular convolution gives circulant, not ordinary Toeplitz. | Medium |

## Part 4: Theorem Questions

1. Cauchy-Schwarz inequality
   Statement: \(|\langle x,y\rangle|\le\|x\|\|y\|\).
   Intuition: inner product cannot exceed the product of lengths; cosine magnitude cannot exceed one.
   Proof idea: use nonnegativity of \(\|x-\alpha y\|^2\) with optimal \(\alpha\), or normalize \(x,y\) and use \(\|u-v\|^2\ge0\).
   Likely requirement: proof idea or short proof.

2. Solvability theorem for \(Ax=b\)
   Statement: \(Ax=b\) has a solution iff \(b\in R(A)\), the column/range space of \(A\).
   Intuition: \(Ax\) is a linear combination of columns of \(A\); only vectors in that span can be produced.
   Proof idea: expand \(Ax=\sum_i x_i a_i\).
   Likely requirement: full understanding and short proof.

3. Uniqueness theorem for \(Ax=b\)
   Statement: if \(x_0\) is one solution, all solutions are \(x_0+N(A)\). The solution is unique iff \(N(A)=\{0\}\).
   Intuition: null-space directions are invisible to \(A\).
   Proof idea: if \(Ax_1=b\) and \(Ax_2=b\), then \(A(x_1-x_2)=0\).
   Likely requirement: full proof likely.

4. Null space and row space orthogonality
   Statement: \(N(A)=R(A^*)^\perp\) in complex case; real case \(N(A)=row(A)^\perp\).
   Intuition: \(Ax=0\) says every row has zero inner product with \(x\).
   Proof idea: write components of \(Ax\) as row inner products.
   Likely requirement: understanding plus proof.

5. Row rank equals column rank
   Statement: dimension of row space equals dimension of column space; this common value is rank.
   Intuition: the number of independent input directions that survive equals the number of independent output directions produced.
   Proof idea: choose a row-space basis, map it with \(A\), show independent images in column space; reverse with \(A^*\).
   Likely requirement: proof idea likely, full proof possible.

6. Full rank and inverse-type theorem
   Statement: full row rank implies a right inverse exists; full column rank implies a left inverse exists. Square full rank implies a two-sided inverse.
   Intuition: full row rank covers the target space; full column rank kills no input direction.
   Proof idea: solve \(Ad_i=e_i\) for standard basis vectors to build a right inverse; analogous for left inverse.
   Likely requirement: conceptual explanation.

7. Basis-change representation theorem
   Statement: if \(T\) is a basis matrix, the representation of a linear map \(A\) in that basis is \(T^{-1}AT\).
   Intuition: convert new coordinates to old, apply \(A\), convert back.
   Proof idea: \(x=T[x]_T\), so output coordinates satisfy \([Ax]_T=T^{-1}AT[x]_T\).
   Likely requirement: full understanding.

8. Diagonalization theorem
   Statement: \(A\) is diagonalizable iff it has a basis of eigenvectors; then \(A=T\Lambda T^{-1}\).
   Intuition: in eigenvector coordinates, \(A\) only scales coordinate axes.
   Proof idea: \(AT=T\Lambda\) when columns of \(T\) are eigenvectors.
   Likely requirement: statement and explanation.

9. Schur factorization theorem
   Statement: every square complex matrix \(A\) can be written \(A=UTU^*\), where \(U\) is unitary and \(T\) is upper triangular.
   Intuition: even when diagonalization fails, an orthonormal basis can at least make the transformation triangular.
   Proof idea: choose one eigenvector, extend to orthonormal basis, obtain block triangular form, induct on the remaining block.
   Likely requirement: statement plus proof idea.

10. Unitary preservation theorem
    Statement: if \(U\) is unitary, then \(\|Ux\|=\|x\|\) and \(\langle Ux,Uy\rangle=\langle x,y\rangle\).
    Intuition: unitary transformations are rotations/reflections/complex phase changes; they preserve geometry and energy.
    Proof idea: \(x^*U^*Ux=x^*x\).
    Likely requirement: full proof likely.

11. Eigenvalues of a unitary matrix
    Statement: all eigenvalues of a unitary matrix lie on the unit circle.
    Intuition: eigenvectors are only scaled by eigenvalues; if norm is preserved, scaling magnitude must be one.
    Proof idea: \(\|Ux\|=\|\lambda x\|=|\lambda|\|x\|=\|x\|\).
    Likely requirement: full proof likely.

12. Orthogonality of unitary eigenspaces
    Statement: eigenvectors of a unitary matrix corresponding to distinct eigenvalues are orthogonal.
    Intuition: unitary maps preserve inner products, but distinct unit-magnitude eigenvalues force the inner product to vanish.
    Proof idea: compare \(\langle Ux,Uy\rangle\) with \(\langle x,y\rangle\).
    Likely requirement: proof idea.

13. Hermitian quadratic form theorem
    Statement: if \(A=A^*\), then \(x^*Ax\in\mathbb R\) for all \(x\).
    Intuition: Hermitian matrices define real-valued quadratic surfaces even over complex vectors.
    Proof idea: take conjugate: \((x^*Ax)^*=x^*A^*x=x^*Ax\).
    Likely requirement: full proof likely.

14. Eigenvalues of Hermitian matrices
    Statement: all eigenvalues of a Hermitian matrix are real.
    Intuition: along an eigenvector, the quadratic form equals \(\lambda\|x\|^2\), and the left side is real.
    Proof idea: \(x^*Ax=\lambda x^*x\), with \(x^*x>0\).
    Likely requirement: full proof likely.

15. Orthogonality of Hermitian eigenspaces
    Statement: eigenvectors corresponding to distinct eigenvalues of a Hermitian matrix are orthogonal.
    Intuition: Hermitian matrices have independent orthogonal action directions.
    Proof idea: compare \(y^*Ax=\lambda y^*x\) and \((Ay)^*x=\mu y^*x\), then \((\lambda-\mu)y^*x=0\).
    Likely requirement: proof likely.

16. Spectral theorem for normal matrices
    Statement: \(A\) is normal iff \(A\) is unitarily diagonalizable: \(A=U\Lambda U^*\).
    Intuition: normal matrices are exactly those whose action can be decomposed along an orthonormal eigenbasis.
    Proof idea: use Schur \(A=UTU^*\); normality transfers to \(T\); upper triangular normal matrices must be diagonal.
    Likely requirement: statement plus proof idea, maybe not full proof.

17. Positive definiteness equivalence
    Statement: Hermitian \(A\) is positive definite iff all eigenvalues are positive iff \(x^*Ax>0\) for every \(x\ne0\).
    Intuition: unitary diagonalization turns the quadratic form into \(\sum_i \lambda_i |z_i|^2\).
    Proof idea: write \(A=U\Lambda U^*\), set \(z=U^*x\).
    Likely requirement: statement and proof idea likely.

18. Orthogonal projection matrix theorem
    Statement: if \(Q\) has orthonormal columns spanning \(V\), then \(P=QQ^*\) is the orthogonal projection onto \(V\), with \(P^2=P\), \(P^*=P\), \(R(P)=V\).
    Intuition: take coordinates by inner products and rebuild the vector in the subspace.
    Proof idea: \(Q^*Q=I\); \(Px\in V\); \(x-Px\perp V\).
    Likely requirement: derivation and properties likely.

## Part 5: Concept Comparison Questions

1. Hermitian vs Unitary
   Model answer: Hermitian means \(A^*=A\); unitary means \(A^*A=I\) and \(A^{-1}=A^*\). Hermitian matrices define real quadratic forms and have real eigenvalues. Unitary matrices preserve norm/inner product and have eigenvalues on the unit circle. Identity is both. A Hermitian matrix is not generally unitary, and a unitary matrix is not generally Hermitian.

2. Normal vs Hermitian
   Model answer: Normal means \(A^*A=AA^*\). Hermitian means \(A^*=A\). Every Hermitian matrix is normal, but not every normal matrix is Hermitian. Normal matrices are unitarily diagonalizable; Hermitian matrices are the normal matrices whose eigenvalues are real.

3. Diagonalizable vs Unitarily Diagonalizable
   Model answer: Diagonalizable means \(A=T\Lambda T^{-1}\) for some invertible \(T\). Unitarily diagonalizable means \(A=U\Lambda U^*\) for unitary \(U\). The second is stronger: it requires an orthonormal eigenbasis. Normal matrices are exactly unitarily diagonalizable.

4. Positive Definite vs Positive Semidefinite
   Model answer: For Hermitian \(A\), positive definite means all eigenvalues \(>0\), equivalently \(x^*Ax>0\) for all nonzero \(x\). Positive semidefinite means all eigenvalues \(\ge0\), equivalently \(x^*Ax\ge0\) for all \(x\). PSD allows zero eigenvalues, so it may be singular.

5. Orthogonal vs Unitary
   Model answer: Orthogonal is the real case: \(Q^TQ=I\). Unitary is the complex case: \(U^*U=I\). Both preserve norms and inner products; unitary uses conjugate transpose.

6. Left Eigenvectors vs Right Eigenvectors
   Model answer: A right eigenvector satisfies \(Av=\lambda v\). A left eigenvector satisfies \(w^*A=\lambda w^*\), equivalently \(A^*w=\bar\lambda w\). Right eigenvectors are input directions mapped to scaled versions of themselves; left eigenvectors are eigenvectors of the adjoint and act as dual measurement directions.

7. Column Space vs Row Space
   Model answer: Column space is in the output space and determines which \(b\)'s can be produced by \(Ax\). Row space is in the input space and is orthogonal to the null space; it determines uniqueness through whether input directions are invisible to \(A\).

8. Null Space vs Left Null Space
   Model answer: Null space \(N(A)\) contains input vectors mapped to zero. Left null space \(N(A^*)\) contains output-side vectors orthogonal to the column space; equivalently \(z^*A=0\). Null space affects uniqueness; left null space gives compatibility conditions for existence.

9. Span vs Basis
   Model answer: Span is all linear combinations of a set. A basis is a spanning set with no redundancy. A dictionary may span but not be linearly independent.

10. Affine vs Convex Combination
    Model answer: Affine combinations require weights sum to one. Convex combinations additionally require nonnegative weights. Convex combinations stay inside the line segment/polytope; affine combinations can extend beyond it.

11. Hyperplane vs Subspace
    Model answer: A hyperplane \(a^Tx=b\) is generally an affine set. It is a subspace only when \(b=0\), because only then it contains the origin and is closed under scaling.

12. Projection Matrix vs Orthogonal Projection Matrix
    Model answer: Any projection matrix satisfies \(P^2=P\). An orthogonal projection also satisfies \(P^*=P\), and its error \(x-Px\) is orthogonal to the range.

13. Triangularization vs Diagonalization
    Model answer: Diagonalization represents a matrix using independent eigen-directions and is not always possible. Triangularization via Schur is always possible over complex spaces and uses a unitary basis, but may leave upper triangular coupling terms.

14. Toeplitz vs Circulant
    Model answer: Toeplitz matrices have constant diagonals and model ordinary time-invariant convolution. Circulant matrices are cyclic shifts and model circular convolution; Fourier basis diagonalizes circulant matrices.

## Part 6: Professor Pattern Analysis

What the professor clearly cares about:

- Geometry behind algebraic expressions: vectors as points, hyperplanes, half-spaces, projections, distances, angles.
- Subspaces as the organizing language for systems of equations.
- Conceptual meaning of matrix multiplication: linear combinations of columns and inner products with rows.
- Structured matrices that make problems simple: diagonal, triangular, orthogonal/unitary, Hermitian, normal.
- Basis choice: choosing the right basis simplifies a transformation.
- Eigenvalues/eigenvectors as geometric directions of a transformation.
- Quadratic forms as the bridge to optimization and stochastic processes.

What the professor repeatedly revisits:

- \(Ax=b\): existence, uniqueness, solution sets.
- Orthogonality: from vectors to bases, projections, unitary matrices, eigenspaces.
- Inner product and norm preservation.
- Column/row/null spaces and their orthogonal relationships.
- Diagonalization failure and triangularization as consolation.
- Hermitian/unitary/normal relationships.
- Eigenvalue location: unit circle for unitary, real line for Hermitian, sign for definiteness.

Foundational topics:

- Linear combination, span, basis, linear independence.
- Vector space/subspace definitions.
- Inner product, norm, orthogonality.
- Matrix multiplication as columns and rows.
- Rank and fundamental subspaces.

Likely distractions or lower priority:

- Detailed historical stories such as Descartes/fly motivation.
- Heavy numerical computations.
- Detailed MATLAB broadcasting tricks, except the notation warning: in written exam, do not rely on MATLAB broadcasting; write replicated vectors explicitly such as \(t1^T\).
- Full SVD derivation, because it was mostly previewed.
- Oblique projection, because it was mentioned but not developed.
- Detailed Fourier calculations, unless tied to conceptual diagonalization of circulant convolution.

Professor exam style prediction:

- Expect short proofs and "explain why" questions.
- Expect definitions with one or two properties attached.
- Expect comparisons between matrix families.
- Expect geometric interpretations of algebraic statements.
- Expect "state theorem, explain intuition, give proof idea" format.
- Expect low computational burden but high penalty for wrong definitions or missing conditions.

## Part 7: Top 20 Most Likely Exam Questions

1. Define unitary matrix and prove norm/inner-product preservation.
   Probability: 96%.
   Outline: \(U^*U=I\); columns/rows ONB; \(\|Ux\|^2=x^*U^*Ux\); inner product preserved; energy interpretation.
   Estimated marks: 10.

2. Explain existence and uniqueness of \(Ax=b\) using column space and null space.
   Probability: 96%.
   Outline: existence iff \(b\in R(A)\); uniqueness iff \(N(A)=0\); all solutions \(x_0+N(A)\); row space link.
   Estimated marks: 12.

3. Define Hermitian matrix and prove its eigenvalues are real.
   Probability: 95%.
   Outline: \(A=A^*\); \(x^*Ax\) real; eigenvector equation; Rayleigh quotient real.
   Estimated marks: 10.

4. Define positive definite/semidefinite/indefinite Hermitian matrices and relate to \(x^*Ax\).
   Probability: 93%.
   Outline: eigenvalue sign classification; quadratic form sign; zero eigenvalue distinction.
   Estimated marks: 10.

5. State and explain the spectral theorem for normal matrices.
   Probability: 92%.
   Outline: normal iff \(A=U\Lambda U^*\); orthonormal eigenbasis; examples Hermitian/unitary.
   Estimated marks: 10.

6. Explain diagonalization as basis change and connect it to eigenvectors.
   Probability: 91%.
   Outline: \(T^{-1}AT\); columns of \(T\) eigenvectors; diagonal entries eigenvalues; not always possible.
   Estimated marks: 10.

7. Define orthogonal projection onto a subspace and derive \(P=QQ^*\).
   Probability: 90%.
   Outline: \(p\in V\), error orthogonal; \(Q^*Q=I\); \(p=Q(Q^*x)\); \(P^2=P\), \(P^*=P\).
   Estimated marks: 12.

8. State Schur factorization and give its proof idea.
   Probability: 88%.
   Outline: \(A=UTU^*\); choose eigenvector; extend to ONB; inductive triangularization.
   Estimated marks: 10.

9. Compare Hermitian, unitary, and normal matrices.
   Probability: 87%.
   Outline: definitions; inclusion relationships; eigenvalue locations; diagonalization properties.
   Estimated marks: 8.

10. Define vector space, subspace, span, basis, and linear independence.
    Probability: 86%.
    Outline: exact definitions; closure; redundancy; dimension.
    Estimated marks: 10.

11. Prove row rank equals column rank or explain the proof.
    Probability: 84%.
    Outline: row basis mapped by \(A\); independence; reverse inequality using transpose/adjoint.
    Estimated marks: 12.

12. Explain full row rank/full column rank and left/right inverses.
    Probability: 82%.
    Outline: rank \(m\) gives right inverse and existence for all \(b\); rank \(n\) gives left inverse and uniqueness.
    Estimated marks: 10.

13. Define complex inner product and contrast it with real inner product.
    Probability: 80%.
    Outline: conjugate transpose; conjugate symmetry; scaling convention; norm \(x^*x\).
    Estimated marks: 7.

14. Define hyperplane and half-space and interpret a linear equation geometrically.
    Probability: 78%.
    Outline: \(a^Tx=b\); normal vector; boundary and two sides; 2D/3D/high-dimensional interpretations.
    Estimated marks: 7.

15. Define linear, affine, and convex combinations; explain convex hull.
    Probability: 76%.
    Outline: arbitrary weights; sum-to-one; nonnegative plus sum-to-one; hull examples.
    Estimated marks: 8.

16. Prove eigenvalues of a unitary matrix lie on the unit circle.
    Probability: 75%.
    Outline: \(Ux=\lambda x\); norm preservation; nonzero eigenvector; \(|\lambda|=1\).
    Estimated marks: 6.

17. Prove eigenvectors of a Hermitian matrix with distinct eigenvalues are orthogonal.
    Probability: 73%.
    Outline: compare \(y^*Ax\) two ways; real eigenvalues; \((\lambda-\mu)y^*x=0\).
    Estimated marks: 8.

18. Explain Toeplitz/circulant convolution matrices and Fourier diagonalization.
    Probability: 65%.
    Outline: time invariance -> Toeplitz; causality -> lower triangular; circular convolution -> circulant; Fourier diagonalizes circulant.
    Estimated marks: 8.

19. State Cauchy-Schwarz and explain angle/cosine definition.
    Probability: 62%.
    Outline: inequality; why cosine lies in valid range; orthogonality at zero inner product.
    Estimated marks: 7.

20. Use trace to show matrix energy equals eigenvalue energy for normal matrices.
    Probability: 58%.
    Outline: Frobenius energy \(tr(A^*A)\); unitary diagonalization; trace cyclic property.
    Estimated marks: 8.

## Part 8: If I Were Writing The Exam

### Linear System Theory Final Exam, Theoretical Version

Time: 120 minutes. Total: 100 marks. No heavy computation is required. Answers must include definitions, conceptual interpretation, and proof ideas where requested.

#### Question 1: Foundations of Geometry in Vector Spaces, 20 marks

a. Define vector space, subspace, span, basis, and linear independence. Explain why a basis is a nonredundant spanning set. 8 marks

Marking:
- Vector space ingredients and operations: 2
- Subspace closure under addition/scalar multiplication: 2
- Span as all linear combinations: 1
- Linear independence condition: 1
- Basis = span + independence: 1
- Redundancy explanation: 1

b. Define norm and inner product. Explain how inner product gives angle and orthogonality. 6 marks

Marking:
- Norm properties: 2
- Inner product definition/properties: 2
- Angle formula and Cauchy-Schwarz role: 1
- Orthogonality as zero inner product: 1

c. Define linear, affine, and convex combinations. What is the convex hull of a set? 6 marks

Marking:
- Linear combination: 1
- Affine sum-to-one: 1
- Convex sum-to-one plus nonnegative: 2
- Convex hull as all convex combinations/smallest convex set: 2

#### Question 2: Fundamental Subspaces and \(Ax=b\), 20 marks

a. Define column space, row space, null space, and left null space of a matrix \(A\). State which spaces live in the input space and which live in the output space. 8 marks

Marking:
- Column/range space: 2
- Row space: 2
- Null space: 2
- Left null space and ambient-space distinction: 2

b. Prove that \(Ax=b\) has a solution iff \(b\in R(A)\). 4 marks

Marking:
- Matrix-vector product as column combination: 2
- Both directions of iff: 2

c. Prove that if \(x_0\) is one solution, then all solutions are \(x_0+N(A)\). What is the uniqueness condition? 5 marks

Marking:
- Difference of two solutions lies in null space: 2
- Adding null vector preserves solution: 1
- Solution set form: 1
- Unique iff \(N(A)=\{0\}\): 1

d. State the rank theorem that row rank equals column rank. Explain why rank matters for full row rank and full column rank. 3 marks

Marking:
- Rank as common dimension: 1
- Full row rank/existence meaning: 1
- Full column rank/uniqueness meaning: 1

#### Question 3: Orthogonal Projection, 15 marks

a. Define the orthogonal projection of a vector \(x\) onto a subspace \(V\). 4 marks

Marking:
- Projected vector lies in \(V\): 1
- Error \(x-p\) orthogonal to \(V\): 2
- Closest-point interpretation: 1

b. Suppose columns of \(Q\) are an orthonormal basis for \(V\). Derive \(P=QQ^*\). 6 marks

Marking:
- Coordinates by \(Q^*x\): 2
- Reconstruct projected vector \(Q(Q^*x)\): 2
- Projection matrix \(P=QQ^*\): 2

c. Prove two properties of an orthogonal projection matrix. 5 marks

Marking:
- \(P^2=P\): 2
- \(P^*=P\): 2
- Range/fixed-vector interpretation: 1

#### Question 4: Basis Change, Eigenvalues, and Schur, 20 marks

a. Explain why changing basis changes the matrix representation of a linear map to \(T^{-1}AT\). 5 marks

Marking:
- Coordinate conversion into old basis: 2
- Apply \(A\): 1
- Convert back: 1
- Same transformation, different representation: 1

b. Define eigenvalue, eigenvector, eigenspace, and characteristic polynomial. 5 marks

Marking:
- \(Ax=\lambda x\), \(x\ne0\): 2
- Eigenspace \(N(A-\lambda I)\): 1
- Characteristic polynomial determinant: 1
- Roots are eigenvalues: 1

c. State and explain the diagonalization criterion. 5 marks

Marking:
- \(A=T\Lambda T^{-1}\): 1
- Columns of \(T\) are eigenvectors: 2
- Need a basis of eigenvectors: 1
- Not every matrix is diagonalizable: 1

d. State Schur factorization and give the proof idea. 5 marks

Marking:
- \(A=UTU^*\), \(U\) unitary, \(T\) triangular: 2
- Start with eigenvector: 1
- Extend to orthonormal basis: 1
- Inductive/block triangular argument: 1

#### Question 5: Structured Matrices, 25 marks

a. Define unitary matrix. Prove it preserves norm and inner product. State where its eigenvalues lie. 8 marks

Marking:
- Definition \(U^*U=I\): 2
- Norm proof: 2
- Inner product proof: 2
- Eigenvalues on unit circle: 2

b. Define Hermitian matrix. Prove \(x^*Ax\) is real and eigenvalues are real. 7 marks

Marking:
- Definition \(A^*=A\): 1
- Quadratic form conjugate proof: 3
- Eigenvalue proof: 3

c. Define normal matrix and state the spectral theorem for normal matrices. Compare normal, Hermitian, and unitary matrices. 5 marks

Marking:
- Normal definition: 1
- Unitary diagonalization theorem: 2
- Hermitian subset/eigenvalues real: 1
- Unitary subset/eigenvalues unit circle: 1

d. Define positive definite, positive semidefinite, and indefinite Hermitian matrices. Explain the quadratic-form interpretation. 5 marks

Marking:
- PD eigenvalue/quadratic definitions: 2
- PSD allows zero eigenvalues: 1
- Indefinite both signs: 1
- Shape/direction interpretation: 1

#### Optional Bonus: System Interpretation, 5 marks

Explain why a causal LTI convolution matrix is lower triangular Toeplitz. What changes for circular convolution, and what does losslessness imply?

Marking:
- Causality -> lower triangular: 1
- Time invariance -> Toeplitz: 1
- Circular convolution -> circulant: 1
- Fourier diagonalizes circulant: 1
- Lossless -> unitary/orthogonal: 1

## Part 9: Final Prediction Sheet

If studying time is limited, study these first.

### Top 10 Definitions

1. Inner product and induced norm.
2. Orthogonality, orthogonal set, orthonormal set.
3. Vector space and subspace.
4. Span, basis, linear independence.
5. Column space, row space, null space, left null space.
6. Rank and full rank.
7. Eigenvalue, eigenvector, eigenspace, characteristic polynomial.
8. Unitary/orthogonal matrix.
9. Hermitian and normal matrix.
10. Positive definite, positive semidefinite, indefinite.

### Top 10 Theorems

1. \(Ax=b\) solvable iff \(b\in R(A)\).
2. All solutions of \(Ax=b\) are \(x_0+N(A)\).
3. \(N(A)\) is orthogonal to row space.
4. Row rank equals column rank.
5. Diagonalizable iff there is a basis of eigenvectors.
6. Schur factorization \(A=UTU^*\).
7. Unitary matrices preserve norm and inner product.
8. Eigenvalues of unitary matrices lie on the unit circle.
9. Hermitian matrices have real quadratic forms and real eigenvalues.
10. Normal matrices are exactly unitarily diagonalizable matrices.

### Top 10 Conceptual Questions

1. Why is \(Ax=b\) a question about column space?
2. Why does null space determine uniqueness?
3. Why does changing basis simplify a linear transformation?
4. Why are diagonal, triangular, and orthogonal/unitary systems "simple"?
5. Why is orthogonality central to projections and coordinates?
6. Why is unitary transformation energy-preserving?
7. Why do Hermitian matrices define real quadratic functions?
8. Why does positive definiteness determine the shape of a quadratic function?
9. Why are normal matrices the natural common family containing Hermitian and unitary matrices?
10. Why does Fourier basis simplify circular convolution?

### Top 10 Proof Ideas

1. \(b\in R(A)\) iff \(Ax=b\) is solvable: expand \(Ax\) as column combination.
2. Solution set \(x_0+N(A)\): subtract two solutions.
3. Null space orthogonal to row space: components of \(Ax\) are row inner products.
4. Row rank equals column rank: map a row-space basis and reverse by transpose/adjoint.
5. Basis change \(T^{-1}AT\): convert coordinates, apply map, convert back.
6. Diagonalization: collect eigenvectors into \(T\) so \(AT=T\Lambda\).
7. Schur theorem: eigenvector, extend to orthonormal basis, induct.
8. Unitary preservation: insert \(U^*U=I\).
9. Hermitian eigenvalues real: \(x^*Ax=\lambda x^*x\).
10. Positive definite equivalence: use \(A=U\Lambda U^*\) and write \(x^*Ax=\sum_i\lambda_i |z_i|^2\).

Strongest final prediction:

If the final has five long theory questions, expect them to be close to:

1. Fundamental subspaces and \(Ax=b\).
2. Inner product/orthogonality/projection.
3. Basis change, eigenvalues, diagonalization, Schur.
4. Unitary and Hermitian matrix properties.
5. Normal/positive definite/quadratic form classification.

