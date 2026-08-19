# Lecture 04 Exam Report

Source scope: only `corrected/lecture4_corrected.md`, `study_outputs/lecture_notes/lecture_04_notes.md`, and `study_outputs/audits/lecture_04_audit.md` were used.

This is not a general lecture summary. It keeps only exam-relevant hints, repeated emphasis, instructor warnings, proof-heavy material, theorem-heavy material, notation traps, and conceptual question shapes.

## Probability Guide

- High: explicitly marked as an exam note or likely topic, repeatedly emphasized, or central to later analysis.
- Medium: likely to appear as a supporting conceptual check or example.
- Low: mentioned as future motivation or background, but not developed enough in Lecture 04 to be a main exam target.

## Exam-Probability Topics

| Topic | Probability | Why | Likely exam task |
|---|---:|---|---|
| Cauchy-Schwarz inequality and cosine-angle definition | High | Explicit exam note. The instructor said a proof was already given and an alternative proof appears in homework. It justifies why \(\langle x,y\rangle/(\|x\|\|y\|)\) lies in \([-1,1]\). | Prove or explain why the normalized inner product can be called \(\cos\theta\). Connect Cauchy-Schwarz to angle/cosine similarity. |
| Orthogonality as zero inner product | High | Repeated across the lecture and used to generalize geometry beyond \(\mathbb{R}^2\) and \(\mathbb{R}^3\). | State \(x\perp y\) iff \(\langle x,y\rangle=0\). Apply this to ordinary vectors, matrices, random variables, or columns of a matrix. |
| Hyperplanes and half-spaces from inner products | High | The instructor reminded students of this before moving to \(Ax=b\). It is the geometric bridge from one equation to a solution set. | Interpret one linear equation as a hyperplane. Explain why a two-dimensional hyperplane is a line. |
| Matrix multiplication as a "bag of inner products" | Medium | Repeated as an organizing idea, and later used to interpret \(X^T X=I\). | Explain each entry of \(AB\) as row-column inner product. Use this to interpret \(X^T X\). |
| \(Ax=b\): existence and uniqueness questions | High | Explicit exam note and the main motivation for vector spaces/subspaces. The instructor repeatedly framed the course around solution existence and uniqueness. | Given \(A,b\), ask whether a solution exists, whether it is unique, whether no solution is possible, and whether infinitely many solutions occur. |
| Two equations, two unknowns: line-intersection cases | High | Explicit exam note. The instructor said this picture will be extended to arbitrary numbers of equations and unknowns. | Classify intersecting lines as unique solution, overlapping lines as infinitely many solutions, and parallel distinct lines as no solution. |
| "Finite number of solutions" trap for linear systems | Medium | The audit notes explicitly restored this omitted instructor question. It is a conceptual prompt, even though the full proof is not completed in this lecture. | Be ready for the question: can a real linear system have finitely many solutions other than one? The expected later answer is no: solution sets are empty, a point, or affine subspaces with infinitely many points. |
| General \(m\times n\) systems and role of \(A\) vs \((A,b)\) | High | Explicit exam note. The instructor asked whether conditions can be characterized from \(A\) alone or require the pair \((A,b)\). | Know that \(m\) rows mean equations and \(n\) columns mean unknowns. Distinguish "for this \(b\)" from "for every \(b\)" and "if a solution exists, is it unique?" |
| Vector spaces as the major analysis tool | High | Explicit likely exam topic and repeatedly described as the tool for \(Ax=b\) existence/uniqueness. | Define a vector space and explain why it lets geometric ideas extend to arbitrary objects. |
| Vector space ingredients | High | The lecture spent substantial time on the formal construction. | List the four ingredients: vector set, scalar set/field, vector addition, scalar multiplication. |
| Vector space axioms and compatibility conditions | High | Proof/theorem-style section. The instructor emphasized closure and compatibility with scalar-field operations. | Verify closure under addition/scalar multiplication, additive identity, inverses, commutativity, associativity, \(a(bx)=(ab)x\), \(1x=x\), and \(0x=0\). |
| Closure under linear combinations | High | The instructor explicitly concluded that vector spaces are closed under arbitrary linear combinations. This underlies span and subspaces. | Show that if \(x_i\in V\), then \(\sum_i a_i x_i\in V\). Use it as the fast test for vector spaces/subspaces. |
| Nonstandard vector spaces | Medium | The lecture repeatedly generalizes vectors to matrices, polynomials, sequences, functions, random variables, and random processes. | Recognize that "vectors" need not be column arrays if operations satisfy the vector-space axioms. |
| Complex vector spaces | Medium | Important notation issue for electrical engineering. | Identify the scalar field as \(\mathbb{C}\), not \(\mathbb{R}\), when vectors have complex entries and scalars are complex. |
| Matrix spaces as vector spaces | Medium | Important because later examples all live inside spaces of matrices. | Treat each \(m\times n\) matrix as one vector under matrix addition and scalar multiplication. |
| Polynomial spaces | Medium | Flagged as potentially confusing because polynomials are nonlinear in the argument. | Explain why polynomials of degree at most \(n\) form a vector space with \(n+1\) coefficients. Trap: operations act on the polynomial object or coefficients, not on linearity in the variable. |
| Inner products/norms/orthogonality for polynomials | Medium | Marked as likely exam topic in the transcript because it extends geometric language to polynomial spaces. | Explain how a polynomial can be orthogonal to another polynomial once an inner product is defined. |
| Discrete-time sequence spaces | Medium | Used as a signal-processing example and later for causal subspaces. | Treat \(x[n]\) as an infinite-dimensional vector-like object with pointwise addition and scaling. |
| Function spaces | Medium | Included as a standard abstract-vector-space example. | Recognize square-integrable functions on an interval as vectors under pointwise operations. |
| Zero-mean random variables as a vector space | High | The instructor called the random-variable inner-product viewpoint an important leap and tied it to estimation theory/signal processing. The audit specifically restored \(E[XY]\). | Show that sums and scalar multiples of zero-mean random variables are zero-mean. Use \(\langle X,Y\rangle=E[XY]\) for zero-mean real random variables. |
| Correlation as inner product; uncorrelated vs independent | High | Explicit exam note and instructor question. | State that \(E[XY]=0\) means orthogonal/uncorrelated in this vector-space view. Trap: uncorrelated does not necessarily mean independent. |
| Subspace concept | High | Explicit exam note: "major tool" and "really critical" for existence/uniqueness of \(Ax=b\). | Define subspace and test whether a subset is closed under linear combinations. |
| Subset vs subspace | High | Instructor warning through examples. | Do not conclude a set is a subspace just because it is a subset or contains the origin. Verify closure under addition and scalar multiplication. |
| First quadrant in \(\mathbb{R}^2\) | Medium | Used as a basic non-subspace example. | Explain failure under negative scalar multiplication. |
| Union of first and third quadrants | Medium | Misleading example because it contains the origin and handles some scaling. | Explain failure under addition when adding one vector from each quadrant. |
| Line not passing through origin | High | Instructor warning: it looks linear geometrically but is not a linear subspace. | Use absence of zero vector and failure of closure to reject it as a subspace. |
| Lines and planes through the origin | High | Core geometric subspace examples. | Identify lines through the origin in \(\mathbb{R}^2\), and lines/planes through the origin in \(\mathbb{R}^3\), as subspaces. |
| Symmetric matrices as a subspace | High | Explicitly important because symmetric matrices support high-dimensional quadratic functions and optimization. Proof-style closure check was done in lecture. | Prove \(S_1=\{X:X^T=X\}\) is a subspace using \(0^T=0\), \((\alpha X)^T=\alpha X\), and \((X+Y)^T=X^T+Y^T\). |
| Trace operation | High | Explicit exam note: trace was introduced as very important, though simple. | Define \(\operatorname{tr}(X)=\sum_i x_{ii}\). Trap: trace ignores off-diagonal entries and is defined for square matrices. |
| Zero-trace matrices as a subspace | High | Explicit exam note and proof-heavy section. | Prove \(S_2=\{X:\operatorname{tr}(X)=0\}\) is a subspace using trace linearity. |
| Trace linearity | High | Repeated as the reason zero-trace matrices form a subspace. | Use \(\operatorname{tr}(X+Y)=\operatorname{tr}(X)+\operatorname{tr}(Y)\) and \(\operatorname{tr}(\alpha X)=\alpha\operatorname{tr}(X)\). |
| Degrees of freedom for matrix subspaces | Medium | Introduced as the bridge to dimension. | Know arbitrary \(m\times m\) matrices have \(m^2\) parameters, symmetric matrices have \((m^2+m)/2\), and zero-trace matrices have \(m^2-1\). |
| Zero-trace matrices as a hyperplane orthogonal to identity | Medium | Explicit exam note, but the matrix inner product was only previewed, not fully developed. | With \(\langle A,B\rangle=\operatorname{tr}(B^TA)\), recognize \(\operatorname{tr}(X)=\langle X,I\rangle\), so zero-trace matrices are orthogonal to \(I\). |
| Hyperplanes through origin vs shifted hyperplanes | High | Instructor asked this as a trap question. The audit specifically clarified shifted trace hyperplanes. | Distinguish \(\operatorname{tr}(X)=0\), a subspace, from \(\operatorname{tr}(X)=1\), not a subspace. Explain that \(Z+S_2\) has constant trace \(\operatorname{tr}(Z)\) and is translated away from the origin. |
| Real orthogonal matrices \(X^TX=I\) | High | Explicit exam note and important non-subspace example. | Interpret \(X^TX=I\) as columns of \(X\) being mutually orthogonal and unit norm. |
| Orthogonal matrices are not a subspace | High | Explicitly emphasized. | Reject \(S_4=\{X:X^TX=I\}\) as a subspace because the zero matrix is not included: \(0^T0=0\neq I\). |
| Closest point to circle / closest orthogonal matrix idea | Low | The instructor marked the set as important but framed distance-to-orthogonal-set problems as future material requiring distance definitions. | Conceptual only: know this motivates matrix distance/projection problems, not a fully developed Lecture 04 proof target. |
| Causal discrete-time sequences as a subspace | Medium | A concrete subspace example linked to signals and systems background. | Show \(x[n]=0\) for \(n<0\) is preserved by addition and scalar multiplication. |
| Dimension motivation | Medium | The lecture uses degrees of freedom to motivate formal dimension, but formal dimension is deferred. | Explain dimension as "how large" a space/subspace is or how many free parameters are needed. |
| Span | High | Explicit likely exam topic. It is introduced formally at the end and tied to linear combinations. | Define span as all possible linear combinations of a set, or equivalently the smallest subspace containing the set. |
| Span examples and redundant vectors | High | Instructor emphasized that adding a vector already in the span does not add a dimension or new information. | Given vectors, decide whether adding another vector changes the span. |
| Basis | High | Explicit likely exam topic and described as the reverse of span. | Given a space/subspace, find a minimal spanning set. State that no basis vector can be written as a linear combination of the others. |
| Linear independence | High | Explicitly named as required for basis, though developed more in the next lecture. | Be ready for the connection: a basis is a spanning set with no redundant vectors. |
| Dictionary vs basis | Medium | Mentioned as a machine-learning-relevant distinction. | Identify a redundant spanning set as a dictionary rather than a basis. |

## High-Risk Traps

| Trap | Probability | Correct handling |
|---|---:|---|
| "Looks linear" does not mean subspace. | High | A line/hyperplane must pass through the origin and be closed under linear combinations. |
| A subset containing zero is not automatically a subspace. | High | The union of first and third quadrants contains zero but fails closure under addition. |
| \(\operatorname{tr}(X)=0\) vs \(\operatorname{tr}(X)=1\). | High | Zero trace is a subspace; trace one is a shifted hyperplane, not a subspace. |
| Orthogonal matrices are not a subspace despite the word "orthogonal." | High | \(X^TX=I\) imposes unit-norm columns; zero matrix is excluded. |
| Correlation zero is not independence. | High | In the random-variable vector-space view, \(E[XY]=0\) means uncorrelated/orthogonal, not necessarily independent. |
| Polynomial vector spaces are not about the polynomial being a linear function of its argument. | Medium | The vector is the polynomial object, equivalently its coefficient vector. |
| Scalar zero and zero vector are different objects. | Medium | In \(0x=0\), the left zero is the scalar-field zero and the right zero is the additive identity vector. |
| \(A\)'s dimensions encode roles. | High | \(m\) rows are equations; \(n\) columns are unknowns. Do not reverse them. |
| Trace ignores off-diagonal entries. | High | \(\operatorname{tr}(X)\) is only the sum of diagonal elements. |
| Matrix inner product preview is not yet fully formalized. | Medium | The lecture previews \(\langle A,B\rangle=\operatorname{tr}(B^TA)\); use it carefully as a preview, especially for \(\operatorname{tr}(X)=\langle X,I\rangle\). |

## Proof And Derivation Targets

| Target | Probability | Expected proof skeleton |
|---|---:|---|
| Cauchy-Schwarz implies valid cosine range | High | Use \(|\langle x,y\rangle|\leq \|x\|\|y\|\), then divide by nonzero norms to get the normalized inner product in \([-1,1]\). |
| Vector space closure under linear combinations | High | Combine closure under scalar multiplication and closure under addition. |
| Symmetric matrices form a subspace | High | Check zero, scalar multiplication, and addition using transpose identities. |
| Zero-trace matrices form a subspace | High | Check zero, scalar multiplication, and addition using trace linearity. |
| Trace-one matrices are not a subspace | High | Zero matrix is absent; sum of two trace-one matrices has trace two. |
| Orthogonal matrices are not a subspace | High | Zero matrix fails \(X^TX=I\). |
| Orthogonal matrix column interpretation | High | Treat entries of \(X^TX\) as inner products between columns of \(X\). Diagonal entries equal one, off-diagonal entries equal zero. |
| Causal sequences form a subspace | Medium | Negative-index samples remain zero under addition and scalar multiplication. |
| Span is a subspace | Medium | All linear combinations of elements of a set are closed under further linear combinations. |

## Conceptual Questions To Prepare

| Question shape | Probability | Key answer |
|---|---:|---|
| When does \(Ax=b\) have no solution, one solution, or infinitely many solutions? | High | Use geometric hyperplane intersections first; later use vector-space/subspace tools. |
| Can existence/uniqueness be decided from \(A\) alone? | High | Sometimes the question is "for every \(b\)" or "if a solution exists"; otherwise the pair \((A,b)\) matters. |
| Why introduce vector spaces at all? | High | They generalize geometric reasoning from ordinary vectors to matrices, functions, random variables, sequences, and solution sets. |
| How do you prove a candidate subset is a subspace? | High | Show it is nonempty/contains zero and closed under arbitrary linear combinations, or separately under addition and scalar multiplication. |
| Why are symmetric matrices important later? | High | They support high-dimensional quadratic functions, which are key in optimization. |
| What is the difference between a basis and a dictionary? | Medium | A basis is minimal/nonredundant; a dictionary may span the same space with redundant vectors. |
| What does adding a redundant vector do to a span? | High | Nothing; if the vector is already a linear combination of the others, the span is unchanged. |

