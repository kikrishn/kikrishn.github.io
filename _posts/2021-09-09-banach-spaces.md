---
layout: post
title: Banach Spaces and Preserving Finite Dimensional Theorems
tags:
  - analysis-qual-prep
---

Banach Spaces are ubiquitous in analysis, and they let us rein in analytic
objects using algebra (in particular, vector spaces) and completeness.
Infinite dimensional vector spaces can be pathological, but by restricting
attention to _continuous_ operations for our topology, we can recover 
analogues for a lot of the finite dimensional theory! 

---

Recall a Banach Space is a vector space equipped with a norm so that
the resulting metric space is [complete][4]. We have already seen some
examples of this, but let's explicitly list some to get a sense of _just_
how common Banach Spaces are!

- $L^p$ spaces, with the $L^p$ norm

    $$\lVert f \rVert_p \triangleq \left ( \int |f|^p \right )^{1/p}$$

- Bounded continuous functions with the $\sup$ norm 

    $$\lVert f \rVert_\infty \triangleq \sup_{x \in X} |fx|$$

  (A particular case is _all_ continuous functions on a compact space[^3])

- Complex valued measures with the [total variation][6] norm[^2]

    $$\lVert \mu \rVert \triangleq |\mu|(X)$$

- $k$-times differentiable functions on $[0,1]$ with the norm

    $$\lVert f \rVert \triangleq \sum_{j=0}^k \left \lVert \frac{d^j}{dx^j} f \right \rVert_\infty$$

- Lipschitz functions on $[0,1]$ with the norm

    $$\lVert f \rVert \triangleq C_f + \lVert f \rVert_\infty$$

  (where $C_f$ is the lipshitz constant for $f$)

- [Sobolev Spaces][8], which I'm told are extremely important.

Of course, we can also build new Banach Spaces from old, and these work in
much the same way as in classical (by which I mean finite dimensional)
linear algebra. 

- If $X$ and $Y$ are banach spaces, then so is $X \times Y$ with the norm

  $$\lVert (x, y) \rVert \triangleq \max \{ \lVert x \rVert, \lVert y \rVert \}$$

  moreover this is the categorical product in $\mathsf{Ban}_1$[^5].

- More generally, if $(X_\alpha)$ is a family of banach spaces, then by 
    $\prod X_\alpha$, we mean 
    $$\{ (x_\alpha) \mid \exists C . \forall \alpha . \lVert x_\alpha \rVert \leq C \}$$.

    We define $\lVert (x_\alpha) \rVert$ to be the least such $C$ 
    (which necessarily equals $\sup \{ \lVert x_\alpha \rVert \}$).
    This is the categorical product in $\mathsf{Ban}_1$, and since one can
    show $\mathsf{Ban}_1$ also has equalizers, we see it is complete.

- If $X$ and $Y$ are banach spaces, then so is $X \oplus Y$ with the norm

    $$\lVert (x,y) \rVert \triangleq \lVert x \rVert + \lVert y \rVert$$

    moreover this is the categorical coproduct in $$\mathsf{Ban}_1$$. 
    Notice, as in the finite dimensional case, that 
    $X \times Y \cong X \oplus Y$, and the difference only becomes relevant
    for _infinite_ products/coproducts[^4].

- More generally, if $(X_\alpha)$ is a family of banach spaces, then by
    $\bigoplus X_\alpha$ we mean 
    $$\{ (x_\alpha) \mid \sum \lVert x_\alpha \rVert \lt \infty \}$$[^6].
    
    Unsurprisingly, we define the norm to be

    $$\lVert (x_\alpha) \rVert \triangleq \sum \lVert x_\alpha \rVert.$$

    Again, this is the categorical coproduct in $\mathsf{Ban}_1$, and since 
    one can show $\mathsf{Ban}_1$ has coequalizers, we see it is cocomplete.

- If $A$ is a closed subspace of $X$, then $A$ is itself a banach space
    with the induced norm[^7]. 

- If $A$ is a closed subspace of $X$, then $X / A$ is a banach space with
    the norm

    $$\lVert x + A \rVert \triangleq \inf_{a \in A} \lVert x + a \rVert$$

    the topology generated by this norm agrees with the quotient topology,
    so we find this does indeed satisfy the universal property of quotients[^16].

<div class=boxed markdown=1>
⚠ Short exact sequences of banach spaces do _not_ split in general! 
That is, if $A$ is a closed subspace of $X$, it is _not_ the case that
$X \cong A \oplus (X / A)$! 

See, for instance, [this survey][9] by Mohammad Sal Moslehian[^8].
</div>

- If $X$ and $Y$ are banach spaces, then $\mathcal{L}(X,Y)$, the space
    of continuous linear maps $X \to Y$ is a banach space with the norm[^9]

    $$\lVert T \rVert \triangleq \sup_{\lVert x \rVert = 1} \lVert Tx \rVert$$

<div class=boxed markdown=1>
  As a quick exercise, prove

  $$\lVert Tx \rVert \leq \lVert T \rVert \lVert x \rVert$$

  This is one of the most important inequalities in the subject.
</div>

- As a special case of the previous example, $\mathcal{L}(X,\mathbb{C})$
    is always a banach space. We denote it by $X^*$, the 
    <span class=defn>dual</span> of $X$[^10]. 

---

Now that we have a wide array of examples of banach spaces, we should start
asking how much of our intuition from finite dimensional linear algebra carries
over. After all, a lot of these constructions looked really familiar, but
then we got blindsided by the lack of complements.

Thankfully, there are lots of foundational theorems in banach space theory
which tell us that certain things work exactly as we'd like!

For instance, in the finite dimensional case, if we've defined a functional
on some subspace, then we can always extend it to the whole space. But the 
proof crucially relies on a choice of basis, so in the infinite dimensional case,
we need to be a bit careful to guarantee that the extension is still continuous.

Thankfully, everything works out:

<div class=boxed markdown=1>
<span class=defn>The Hahn-Banach Theorem</span>[^11]

If $f$ is a continuous linear functional defined on a subspace of $X$,
then $f$ extends to a continuous linear functional $F$ defined on all of $X$.

Moreover, $\lVert F \rVert = \lVert f \rVert$.
</div>

Another piece of intuition from the finite dimensional case is that a
bijective linear map is automatically an isomorphism 
(that is, the inverse map is automatically linear). Is it the case that
a _continuous_ bijective linear map is automatically an isomorphism?
That is, must its inverse _also_ be continuous? Again, the answer is "yes"!

<div class=boxed markdown=1>
<span class=defn>The Open Mapping Theorem</span>

Let $X$ and $Y$ be banach spaces. If $T \in \mathcal{L}(X,Y)$ is surjective,
then it is [open][14]. 

In particular, if $T$ is bijective, then $T^{-1}$ is continuous.
</div>

There's another nice corollary of the open mapping theorem too. Topologically
we expect a quotient map to be open, and we know from the homomorphism theorems
that we can factor any surjection $T : X \to Y$ as 

$$X \to X / \text{Ker}(T) \cong Y$$

the open mapping theorem says that this quotient map is open, as we would expect.
In fact, the projection $\pi : X \to X / A$ (for $A$ closed, of course) always
has norm $1$.

Continuing with our examples, in the finite dimensional case, we think of 
subspaces as being "much smaller" than the ambient space. For instance, the
$xy$-plane is measure $0$ inside $\mathbb{R}^3$ (with lebesgue measure) because
it has no thickness. One can ask if sub-banach spaces (that is, closed subspaces)
must be "small" in some sense. Again, the answer is "yes"[^12], but we 
have to use a different notion of "small"[^14]:

<div class=boxed markdown=1>
<span class=defn>The (Strong) Open Mapping Theorem</span>

If $X$ and $Y$ are banach spaces[^13] and $T \in \mathcal{L}(X,Y)$, then if
the image $T[X]$ is nonmeagre in $Y$, we automatically have surjectivity
and open-ness.

As a simple corollary, every proper closed subspace is meagre.
</div>

---

Of course, we can't talk about banach spaces without talking about a theorem
which honestly feels like magic.

<div class=boxed markdown=1>
<span class=defn>The Uniform Boundedness Principle</span>

  Say $\{ T_\alpha \}$ is a family of continuous linear maps between
  banach spaces[^15] $X$ and $Y$. If, this family is bounded _pointwise_
  in the sense that every $x$ satisfies

  $$\sup \lVert T_\alpha x \rVert \lt \infty$$

  (where the precise bound is allowed to depend on $x$)

  then we actually get a _uniform_ bound for free!

  $$\sup \lVert T_\alpha \rVert \lt \infty$$
</div>

The ability to boost pointwise results to uniform results is often important
(this is one of many reasons to care about compactness), and there are 
innumerable appplications of this theorem. Here's one that seems to show up 
on a lot of practice quals:

<div class=boxed markdown=1>
  Show that a weakly convergent sequence $(x_n)$ is bounded.

  Recall $(x_n)$ is weakly convergent if $(T x_n)$ is convergent in $\mathbb{C}$
  for every continuous functional $T$.
</div>

And here's one that says a certain pathology you might remember from an 
undergraduate analysis class doesn't happen in the banach space setting:

<div class=boxed markdown=1>
  Show that if $X$, $Y$, and $Z$ are banach spaces, then every _separately_
  continuous bilinear map $X \times Y \to Z$ is automatically _jointly_ 
  continuous[^18].

  Here $X \times Y$ is meant as merely the product of topological spaces, 
  rather than as the product of banach spaces defined earlier.
</div>

As with the open mapping princple, it's actually enough to know that you're 
pointwise bounded on some set that isn't small:

<div class=boxed markdown=1>
<span class=defn>The (Strong) Uniform Boundedness Principle</span>

If $X$ and $Y$ are normed vector spaces[^17] and $(T_\alpha)$ is a 
sequence of continuous linear maps from $X$ to $Y$, then 
as long as the family is _pointwise_ bounded on a nonmeagre set, it's 
actually uniformly bounded! 

More formally, if $E \subseteq X$ is nonmeagre, and we have a bound

$$\sup \lVert T_\alpha x \rVert \lt \infty$$ 

for each $x \in E$ 

then we actually get a uniform bound for free!

$$\sup \lVert T_\alpha \rVert \lt \infty$$
</div>

This is fairly indicative of working with meagre and nonmeagre sets. 
We frequently get a kind of dichotomy where things are either bad 
almost everywhere or good almost everywhere (by which I mean on a comeagre set).

So if you can show that something good/bad happens on a set that isn't small
(meagre) then you often get for free that good/bad things happen almost everywhere!

For instance, let's look at the contrapositive of the above theorem. It says
that if $\sup \lVert T_\alpha \rVert = \infty$, then actually for 
_comeagrely many_ choices of $x$, we must have 
$\sup \lVert T_\alpha x \rVert = \infty$!


---

Next time[^1], we'll talk about [Hilbert Spaces][3], where we'll require
even more algebraic structure, and in exchange we'll gain better structure 
theorems telling us about our spaces. These structure theorems will lead us
into the beautiful world of Fourier Analysis, which we'll discuss afterwards.

In the meantime, you should definitely read Terry Tao's post about banach
spaces [here][18]. 

See you soon! ^_^

---

[^1]:
    I didn't forget about the [closed graph theorem][19], I just couldn't
    find a way to make it fit into the narrative of this blog post
    (comparing finite dimensional and infinite dimensional banach spaces).

    I have some interesting stuff to say, though, since it's analogous to a theorem 
    in [universal algebra][1].
    Terry Tao talks some about this in one of his [blog posts][2] 
    (and gives a _very_ interesting application in [another][21]), but the
    idea behind the closed graph theorem is true in very high generality:

    <div class=boxed markdown=1>
      Show that $f : A \to B$ is a homomorphism of algebras if and only if
      its graph is a subalgebra of $A \times B$.
    </div>

    Moreover, if $Y$ is compact and hausdorff, then $f : X \to Y$ is continuous
    if and only if its graph is closed in $X \times Y$. This should make some
    vague sense, since compact hausdorff spaces behave a lot like algebras
    (in fact, they _are_ a category of algebras for the ultrafilter monad. 
    See [here][20], for instance), so $f$ is a "homomorphism" (is continuous)
    exactly when its graph is a subalgebra (sub-compact-hausdorff space) 
    of $X \times Y$.  Of course, to be sub-compact-hausdorff, it suffices to 
    check closedness.

    Now the closed graph theorem says that this is true of banach spaces as well.
    $f : X \to Y$ is a continuous linear map if and only if its graph is a
    sub-banach space of $X \times Y$. Linearity comes from the "space" 
    part of "sub-banach space" and continuity comes from the "banach" part. 
    Of course, as in the compact hausdorff case, it suffices to check closedness.

    _Unlike_ the case of compact hausdorff spaces, though, I don't know of 
    any categorical justification for this theorem! If anyone happens to have
    one, I would love to hear about it!


[^2]:
    Intuitively this makes sense, but formally it is far from obvious
    (at least to me!). That said, you can find a smattering of proofs
    [here][5]. I like the proof by Radon-Nikodym, if you want to do it directly. 

    The most conceptual way to see this is by
    citing the [Riesz Representation Theorem][11], which says that this
    space of measures is actually isometric to $C_0^*$, and thus is banach.
    Of course, that only works when $X$ is locally compact hausdorff. The 
    theorem as proven in that mse link works more generally.

[^3]:
    In fact, this accounts for _all_ banach spaces!

    The [Banach-Mazur Representation Theorem][7] says that every banach space
    is isometric to a closed subspace of $C(K)$ for some compact space $K$
    (in fact, the unit ball in the dual with the weak-* topology works).

    In case your banach space is separable, we can do better -- it is a closed
    subspace of $C([0,1])$!

[^4]:
    In fact, in the finite case we can take $\lVert (x,y) \rVert$ to be any of

    - $\max \{ \lVert x \rVert_X, \lVert y \rVert_Y \}$
    - $\sqrt{ \lVert x \rVert_X^2 + \lVert y \rVert_Y^2 }$
    - $\lVert x \rVert_X + \lVert y \rVert_Y$

    and we'll get the same banach space up to isomorphism (but NOT isometry!).

    If you've not seen this before, you should prove it! 
    It's a fairly quick exercise to show these are all equivalent norms,
    and that they are complete.

[^5]:
    The category $\mathsf{Ban}$ of banach spaces with _all_ continuous linear 
    maps turns out to be somewhat badly behaved. 
    But if we restrict to _contracting_ maps, we get a much nicer category,
    $\mathsf{Ban}_1$.

    Notice we can rescale any linear transformation $T$ by a constant to make 
    it a contraction, so this is not really a limitation.

[^6]:
    Notice the coproduct you might expect

    $$\{ (x_\alpha) \mid x_\alpha \neq 0 \text{ for finitely many $\alpha$ } \}$$

    is not complete, and thus not banach (do you see why?). The actual definition
    of the coproduct is exactly the completion of this space in the coproduct
    norm, though.

[^7]:
    Notice we need $A$ to be closed so that it is itself complete, and is thus
    a sub-banach space.

[^8]:
    In fact, there's more to say! A (nontrivial) theorem says that
    if a banach space satisfies "every closed subspace has a complement" then
    it must actually be a hilbert space! 

    So every non-hilbert banach space must contain a noncomplemented closed subspace!

    See [here][10] (as well as the linked article), for more.

[^9]:
    Recall a linear function is continuous if and only if it is bounded in
    the sense that the norm we're defining is finite.

[^10]:
    In fact, $X^*$ is complete even when $X$ _isn't_. 
    One slick corollary of this is the construction of the completion of 
    a normed space.

    Since $X$ (isometrically!) embeds into its double dual 
    $X \hookrightarrow X^{**}$, we can define the completion of $X$ to be the 
    closure of $X$ under this embedding.

[^11]:
    The proof of this fact makes use of the fact that any vector space is 
    the filtered colimit of its finite dimensional subspaces. We show how to
    extend by one basis element at a time in a way that preserves the norm,
    then we apply Zorn's Lemma to the partial order of these extensions.

    It turns out this appeal to Zorn's Lemma is somewhat unavoidable. There
    are models of $\mathsf{ZFC}$ where Hahn-Banach fails in full generality,
    so we need _some_ amount of choice to prove it. However it's strictly
    weaker than full AC (see [here][12] for more discussion).

    Thankfully, in many concrete situations, we _don't_ need choice! If $X$
    is [separable][13], then we can extend one dimension at a time, making 
    sure we eventually choose each element of our countable dense subset. 
    At the end of this (countable length!) process, we can extend to the whole
    space by continuity.

[^12]:
    Interestingly, we can ask about more general subspaces 
    (which are necessarily not closed). It turns out the answer here is
    a firm "no". 

    Every infinite dimensional banach space has a proper nonmeagre subspace
    (which is necessarily not closed). It turns out such a subspace must be
    dense and cannot have [BP][15].

    These subspaces arise as kernels of discontinuous functionals, so the
    next question is "does every discontinuous functional work?", and the 
    answer here is "it's subtle".

    Using [Martin's Axiom][16] one can show that every separable
    banach space has a discontinuous functional whose kernel is still meagre.
    See [here][17] for more info.


[^13]:
    Actually we only need $X$ to be banach -- 
    a priori $Y$ can be any normed vector space. 

    Interestingly, though. As soon as we know that $T[X] = Y$, we also know
    that $Y \cong X / \text{Ker}(T)$ is banach.

[^14]:
    The post about the baire category theorem is coming up!

[^15]:
    Again, we only _really_ need $X$ to be banach.

[^16]:
    Again, we need $A$ to be closed so that we're working with sub-banach spaces.
    Notice this is not a serious issue -- as a quick exercise, you might show
    that the kernel of a continuous linear map is always a closed subspace.

[^17]:
    In particular neither needs to be complete.

[^18]:
    It might be helpful to recall that a bilinear operator is jointly
    continuous if and only if it is "jointly bounded" in the sense that
    $$\sup \{ \lVert f(x,y) \rVert \ \mid \ \lVert x \rVert = 1, \lVert y \rVert = 1 \} \lt \infty$$.

    As a bigger hint, you might try applying the uniform boundedness principle
    to the family of maps $f(x,-) : Y \to Z$.

    Also, as a fun ~ bonus game ~ for particularly enthusiastic readers, 
    it turns out we don't need all of $X$, $Y$, and $Z$ to be banach spaces! 
    How weak can you make the assumptions and still prove this theorem?


[1]: https://en.wikipedia.org/wiki/Universal_algebra
[2]: https://terrytao.wordpress.com/2012/11/20/the-closed-graph-theorem-in-various-categories/
[3]: https://en.wikipedia.org/wiki/Hilbert_space
[4]: https://en.wikipedia.org/wiki/Complete_metric_space
[5]: https://math.stackexchange.com/questions/178921/space-of-complex-measures-is-banach-proof
[6]: https://en.wikipedia.org/wiki/Total_variation#Total_variation_norm_of_complex_measures
[7]: https://en.wikipedia.org/wiki/Banach%E2%80%93Mazur_theorem
[8]: https://en.wikipedia.org/wiki/Sobolev_space
[9]: https://arxiv.org/pdf/math/0501048v1.pdf
[10]: https://math.stackexchange.com/questions/2176497/banach-space-with-non-complemented-subspace
[11]: https://en.wikipedia.org/wiki/Riesz%E2%80%93Markov%E2%80%93Kakutani_representation_theorem
[12]: https://mathoverflow.net/questions/5351/whats-an-example-of-a-space-that-needs-the-hahn-banach-theorem
[13]: https://en.wikipedia.org/wiki/Separable_space
[14]: https://en.wikipedia.org/wiki/Open_and_closed_maps
[15]: https://en.wikipedia.org/wiki/Property_of_Baire
[16]: https://en.wikipedia.org/wiki/Martin%27s_axiom
[17]: https://mathoverflow.net/questions/3188/are-proper-linear-subspaces-of-banach-spaces-always-meager
[18]: https://terrytao.wordpress.com/2009/02/01/245b-notes-9-the-baire-category-theorem-and-its-banach-space-consequences/
[19]: https://en.wikipedia.org/wiki/Closed_graph_theorem_(functional_analysis)
[20]: https://ncatlab.org/nlab/show/compactum
[21]: https://terrytao.wordpress.com/2016/04/22/a-quick-application-of-the-closed-graph-theorem/