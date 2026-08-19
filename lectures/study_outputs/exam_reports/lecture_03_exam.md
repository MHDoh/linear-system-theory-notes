# Lecture 03 Exam Report

Scope: Lecture 03 only.

Sources read:

- `corrected\lecture3_corrected.md`
- `study_outputs\lecture_notes\lecture_03_notes.md`
- `study_outputs\audits\lecture_03_audit.md`

This report extracts only exam-relevant signals: explicit exam markers, repeated emphasis, warnings, proof-heavy material, theorem-heavy material, notation traps, and conceptual questions.

## Probability Map

| Topic | Probability | Why it is exam-relevant | What to prepare |
|---|---:|---|---|
| Euclidean norm definition in R^n | High | Explicitly marked as likely exam topic. The instructor repeatedly builds from 2D to 3D to arbitrary dimensions and stresses that the high-dimensional formula is a definition, not a drawable derivation. | Know \(\|x\|=\sqrt{\sum_i x_i^2}\). Explain size of a vector, distance to origin, and why the formula extends beyond dimensions we can draw. |
| Norm as distance between vectors | Medium | Repeated conceptual emphasis: once a norm is defined, distance becomes \(\|x-y\|\). It is not explicitly theorem-heavy, but it supports later optimization and geometry. | Be able to compute \(d(x,y)=\|x-y\|\) and explain that different norms can produce different distances and different optimization behavior. |
| Fundamental norm properties | High | Explicitly marked as likely exam topic through the generalization of norm properties. These are core definition-style facts likely to be tested directly. | Memorize nonnegativity, definiteness, homogeneity \(\|\alpha x\|=|\alpha|\|x\|\), and triangle inequality. Know equality in the triangle inequality when vectors are collinear and point in the same direction. |
| Absolute value in norm scaling | High | This is a notation trap. The instructor contrasts length scaling with orientation change under negative scalars. | Do not write \(\|\alpha x\|=\alpha\|x\|\) unless \(\alpha\ge0\). The scalar leaves the norm as \(|\alpha|\). |
| Euclidean inner product definition | High | Inner product is the main new tool for angle, orthogonality, hyperplanes, matrix multiplication, and linear systems. It is heavily reused throughout the lecture. | Know \(\langle x,y\rangle=\sum_i x_i y_i\) for real vectors. Be able to compute it and state that it maps two vectors to a scalar. |
| Inner product output can be negative | Medium | Instructor warning. Students often confuse inner product with norm because both involve component products. | Remember \(\langle x,y\rangle\) may be positive, zero, or negative. Only \(\langle x,x\rangle\) is always nonnegative in the positive definite setting. |
| Norm induced by inner product | High | Explicit exam note and repeated "remember" signal. The instructor emphasizes that the Euclidean norm is derived from the Euclidean inner product. | Know \(\langle x,x\rangle=\|x\|^2\) and \(\|x\|=\sqrt{\langle x,x\rangle}\). Be able to explain "induced norm." |
| Angle formula from inner product | High | Proof-heavy section. The instructor derives the formula using geometry, the law of cosines, and expansion of \(\langle x-y,x-y\rangle\). | Know \(\cos\theta=\frac{\langle x,y\rangle}{\|x\|\|y\|}\). Be able to reproduce the main derivation steps and connect the formula to the law of cosines. |
| Nonzero-vector condition in angle formula | High | Audit flags this as a missing item that was patched into the notes. It is a common denominator trap. | The angle formula requires \(x\ne0\) and \(y\ne0\). Orthogonality via \(\langle x,y\rangle=0\) is algebraic, but the cosine formula needs nonzero norms. |
| Orthogonality via inner product zero | High | Explicitly marked as exam-relevant and central to high-dimensional geometry. | Know \(x\perp y\) iff \(\langle x,y\rangle=0\). Be ready to test examples such as \([3,4]^T\) and \([-4,3]^T\). |
| Sign of inner product and angle type | Medium | Conceptual extension from 2D/3D to high dimensions. Used later for half-spaces. | Know positive inner product means acute angle, negative means obtuse angle, and zero means orthogonal, for nonzero vectors under the Euclidean angle interpretation. |
| Cauchy-Schwarz inequality | High | Theorem-heavy and proof-heavy. It justifies the high-dimensional cosine definition and is explicitly said to be broadly useful, including in estimation theory. | Know \(|\langle x,y\rangle|\le\|x\|\|y\|\). Understand that it guarantees the cosine quotient lies in \([-1,1]\). |
| Cauchy-Schwarz proof idea | High | The proof is detailed in the lecture and audit. This is likely to appear as a derivation or conceptual proof question. | Start from \(\|u-v\|^2\ge0\), expand to get \(2\langle u,v\rangle\le\|u\|^2+\|v\|^2\), normalize \(u=x/\|x\|\), \(v=y/\|y\|\), then repeat with a negative vector for the lower bound. |
| Inner product properties | High | Definition-style and repeatedly used in proofs. A student asks whether all properties are required, making this an emphasized point. | Know scaling in each argument, additivity in each argument, bilinearity for real vectors, symmetry \(\langle x,y\rangle=\langle y,x\rangle\), positivity, and definiteness. |
| No absolute value in inner product scaling | High | Notation trap directly contrasted with norm scaling. | For real inner products, \(\langle \alpha x,y\rangle=\alpha\langle x,y\rangle\), not \(|\alpha|\langle x,y\rangle\). |
| Positive definiteness vs indefinite spaces | Medium | Explicitly marked as likely exam topic, but mostly as a clarification rather than a main computational tool. | Know that \(\langle x,x\rangle=0\) iff \(x=0\) is needed for a true positive definite induced norm. If removed, one enters semidefinite or indefinite settings, which the course does not pursue deeply. |
| Hyperplane through the origin | High | Explicitly marked as likely exam topic. It uses orthogonality and inner products, tying together earlier material. | Know \(H_a=\{x:\langle x,a\rangle=0\}\). Interpret \(a\) as the normal vector. In 2D this is a line through the origin; in 3D it is a plane through the origin. |
| Positive and negative half-spaces | High | Important geometric extension and directly tied to signs of inner products. | Know \(H_a^+=\{x:\langle x,a\rangle>0\}\) and \(H_a^-=\{x:\langle x,a\rangle<0\}\). Interpret them as the two sides of the hyperplane. |
| Shifted hyperplane with threshold \(b\) | High | Explicit exam note. The instructor calls the origin-only definition incomplete and generalizes it with a threshold. | Know \(H_{a,b}=\{x:\langle x,a\rangle=b\}\). \(a\) is normal, \(b\) is the threshold, and \(b\ne0\) shifts the hyperplane away from the origin. |
| Shift derivation for \(H_{a,b}\) | Medium | Derivation-style but shorter than the Cauchy-Schwarz and angle derivations. | Start from \(\langle x-x_0,a\rangle=0\), expand to \(\langle x,a\rangle=\langle x_0,a\rangle\), and set \(b=\langle x_0,a\rangle\). |
| Shifted half-spaces and sign test | High | Audit specifically patched this omission. It is a natural exam trap after defining \(H_{a,b}\). | Know \(H_{a,b}^+=\{x:\langle x,a\rangle>b\}\), \(H_{a,b}^-=\{x:\langle x,a\rangle<b\}\), and classify points using the sign of \(\langle x,a\rangle-b\). |
| Projection interpretation of hyperplanes | Medium | Instructor says projection will be covered later but gives a detailed answer to a student question. This makes it conceptually important but probably not the central Lecture 03 test item. | Know \(x_a=\frac{\langle x,a\rangle}{\|a\|^2}a\). The fixed quantity on \(H_{a,b}\) is the projection component along \(a\), not a fixed angle. |
| Threshold \(b\) is not projection length | High | Strong notation trap from the student-question segment. | \(\langle x,a\rangle\) is not the projection length unless \(a\) is unit length. Projection length along \(a\) is \(\langle x,a\rangle/\|a\|\), so \(b\) must be divided by \(\|a\|\) to become a signed projection length. |
| Neuron as a half-space test | Medium | Explicit exam note, but presented as an application that may be revisited. | Understand that a threshold neuron computes \(\langle x,w\rangle-b\) and checks which half-space \(x\) lies in. The decision boundary is a hyperplane normal to \(w\). |
| Matrix multiplication as a box of inner products | Medium | The instructor explicitly reframes matrix multiplication through inner products. This is likely for conceptual or computational checks. | Know \(c_{ij}\) is the inner product of row \(i\) of \(A\) and column \(j\) of \(B\). Inner dimensions must match: \((m\times n)(n\times p)=m\times p\). |
| Matrix form of linear systems \(Ax=b\) | High | Leads directly into the course's main linear-system questions. The instructor says this is the starting point for linear algebra and matrix analysis. | Be able to convert scalar equations into \(Ax=b\), identify \(A\), \(x\), and \(b\), and explain that rows of \(A\) produce inner products with the unknown vector. |
| Existence and uniqueness of \(Ax=b\) | High | The lecture closes by presenting this as the fundamental future analysis. It includes explicit conceptual questions. | Be ready to answer: Does a solution exist? If it exists, is it unique? Can there be exactly five solutions? What properties of \(A\) and \(b\) matter? |
| Linear equations as hyperplanes | High | This ties hyperplanes to solution sets and gives the geometric meaning of \(Ax=b\). | One equation \(a_i^T x=b_i\) defines a hyperplane. The solution set of \(Ax=b\) is the intersection of those hyperplanes. |
| Three solution-set cases | High | Repeated end-of-lecture emphasis. The instructor states vector-space methods will generalize the picture to arbitrary systems. | Know the trichotomy: unique solution, no solution, infinitely many solutions. In 2D: intersecting lines, parallel distinct lines, or the same line. |
| Linear, affine, and convex combinations recap | Medium | Explicitly marked as likely exam topic in the transcript, but it is a recap from the previous lecture rather than the main Lecture 03 development. | Know linear combination as weighted sum, affine combination as weights summing to 1, convex combination as affine plus nonnegative weights. Geometry: line segment, triangle, convex hull. |
| Convex hull geometric interpretation | Medium | Attached to the explicit likely-exam recap. It may appear as a conceptual short answer. | For multiple points, all convex combinations form the convex hull, the higher-dimensional analogue of polygons/polyhedra. |
| Historical/use-case remarks on norm choice | Low | Instructor mentions signal processing and machine learning research, but this is motivational rather than a formal result. | Useful for conceptual context only: Euclidean norm is analytically convenient; other norms may promote different solution behavior. |
| 3D norm derivation via projection to \(x_1x_2\)-plane | Low | Marked as an exam note, but likely subordinate to the general R^n norm formula and Pythagorean reasoning. | Know the two-step Pythagorean argument if asked to justify \(\sqrt{x_1^2+x_2^2+x_3^2}\). |
| Complex-vector caveat | Low | Mentioned briefly as a future modification. Lecture 03 formulas are real-vector formulas. | Do not overgeneralize real bilinearity/symmetry to complex inner products unless the course later defines the complex convention. |

## Likely Conceptual Questions

1. Why does defining a norm let us talk about distance in high-dimensional spaces?
2. Why is the Euclidean norm formula in \(R^n\) a definition rather than a drawable derivation?
3. What is the difference between \(\|\alpha x\|\) and \(\langle \alpha x,y\rangle\) in terms of scalar handling?
4. How does the inner product induce the Euclidean norm?
5. How do we obtain the angle formula from the inner product?
6. Why is Cauchy-Schwarz needed before defining angle in high-dimensional spaces?
7. Why does \(\langle x,y\rangle=0\) define orthogonality beyond 2D and 3D?
8. How does changing the inner product change the geometry and possibly orthogonality?
9. Why is \(H_a=\{x:\langle x,a\rangle=0\}\) only an incomplete hyperplane definition?
10. What is the role of \(b\) in \(H_{a,b}=\{x:\langle x,a\rangle=b\}\)?
11. Why is \(b\) not automatically a projection length?
12. How is a threshold neuron a half-space classifier?
13. Why is matrix multiplication naturally described as a collection of inner products?
14. How does each row of \(Ax=b\) define a hyperplane?
15. Why can a linear system have no solution, one solution, or infinitely many solutions, but not exactly five solutions?

## Highest-Risk Traps

- Writing \(\|\alpha x\|=\alpha\|x\|\) instead of \(\|\alpha x\|=|\alpha|\|x\|\).
- Treating \(\langle x,y\rangle\) as always nonnegative.
- Forgetting that \(\cos\theta=\frac{\langle x,y\rangle}{\|x\|\|y\|}\) requires both vectors to be nonzero.
- Confusing inner product zero with zero vector. \(\langle x,y\rangle=0\) means orthogonality, not necessarily \(x=0\) or \(y=0\).
- Confusing \(\langle x,a\rangle=b\) with a fixed-angle condition. It fixes the projection component along \(a\), not the angle.
- Treating \(b\) as a projection length without dividing by \(\|a\|\).
- Forgetting that the vector \(a\) or \(w\) is normal to the hyperplane.
- Missing the dimension rule in matrix multiplication: row length of the first matrix must match column length of the second matrix.
- Thinking two equations in two unknowns always have a unique solution. Parallel distinct lines give no solution; identical lines give infinitely many.

## Proof And Derivation Targets

| Derivation | Probability | Minimum expected structure |
|---|---:|---|
| Norm formula in 3D from Pythagoras | Low | Project to \(x_1x_2\)-plane, compute \(\sqrt{x_1^2+x_2^2}\), then combine with \(x_3\). |
| Angle formula | High | Compare law of cosines for \(\|x-y\|^2\) with the inner-product expansion of \(\langle x-y,x-y\rangle\). |
| Cauchy-Schwarz | High | Use \(\|u-v\|^2\ge0\), derive additive bound, normalize \(x\) and \(y\), then use sign flip for absolute value. |
| Shifted hyperplane equation | Medium | Expand \(\langle x-x_0,a\rangle=0\) to get \(\langle x,a\rangle=b\). |
| Matrix form of equations | Medium | Show each scalar equation is an inner product of one row of \(A\) with \(x\), then stack equations into \(Ax=b\). |

## Instructor Emphasis Signals

- Explicit likely exam tags appear around Euclidean norm/inner product, orthogonality and angles, hyperplanes, and positive definiteness/generalized inner products.
- Multiple "remember" remarks occur around the norm-inner-product relationship, generalized hyperplanes, and the neuron half-space interpretation.
- The instructor repeatedly contrasts drawable 2D/3D geometry with high-dimensional definitions.
- The lecture spends substantial proof time on the angle formula and Cauchy-Schwarz.
- Student-question segments highlight traps: all inner-product properties are needed for the positive definite setting, and \(\langle x,a\rangle\) is not projection length unless scaled correctly.
