---
layout: post
title: Rational Canonical Form
tags:
  - Linear Algebra
published: true
---

We want to understand the structure of finitely generated modules $M$ over a principal ideal domain $R$. Simplest among such modules are free modules of finite "rank", $M \cong R^n$ for some finite $n$. Note that the $R$-module structure on $R^n$ is clear unlike that of $M$, and it is this feature that aids in understanding the structure of $M$ via $R^n$. It is intuitively clear that $R^n$ has a "basis" of $n$ elments analogous to the case of vector spaces. Vector spaces are torsion-free, i.e. no nonzero element of the vector space is annihilated by an element of the base ring. On the contrary, the uniquely nonzero element of the $\mathbb{Z}$-module $\mathbb{Z}/ 2 \mathbb{Z}$ is annihilated by $2$ of the base ring $\mathbb{Z}$. This additional feature of modules that are not vector spaces leads one to consider the notion of linearly independence and spanning separately; recall that in the case of vector spaces, a maximal linearly independent set is also a spanning set, and a spanning set contains a maximal linearly independent set, while in the case of modules a spanning set need not contains a linearly independent set. Indeed the subset $\{ 1 + 2 \mathbb{Z} \}$ spans $\mathbb{Z}/2 \mathbb{Z}$ over $\mathbb{Z}$ but it is not linearly independent for $2 \cdot (1 + 2 \mathbb{Z}) = 0$. Similarly a maximal linearly independent set need not span the module: the element $2$ of the $\mathbb{Z}$-module $\mathbb{Z}$ is linearly independent over $\mathbb{Z}$ but it does not span the module. For another example, consider the ring $R := \mathbb{Z}\[x\]$ considered as a module over itself, and consider the module $(2,x)$. Clearly the element $2, x$ span the module $(2,x)$ over $R$ but they are not linearly indendent for there is a nontrivial dependence relation $x \cdot 2 + (-2) \cdot x = 0$ between them. Thus a spanning set may contain a linearly independent set but may not contain a maximal linearly independent set.

**Rank of an $R$-module**: Let $M$ be a free $R$-module, so that $M \cong R^n$ for some integer $n$. Any $n+1$ elements of $M$ is not linearly independent over $R$, i.e. if $y_1, \ldots, y_{n+1}$ are elements of $M$ then there exists $n+1$ elements $r_1, \ldots, r_{n+1}$ not all zero such that $r_1 y_1 + \ldots + r_{n+1} y_{n+1} = 0$. 

**Proof**: (**Embedding Trick**) Let $F$ be the field of fractions of $R$. Consider $R^n$ as a subset of $F^n$ which is a $n$-dimensional vector space over $F$. The $n+1$ elements $y_i$ considered as elements of $F^n$ are not linearly dependent over $F$ so that a relation of the above form exists with $r_i$ in $F$ and not all zero. Taking common denominator of the coefficients gives a corresponding nontrivial relation over $R$. For example, if we have $\frac{2}{3} x + \frac{4}{5} y = 0$ over $F$ then we have $10 x + 12 y = 0$ over $R$.

(**Determinant Trick**) First recall the Cramer's rule for solving a system of equations, say in the form $Ax = b$ where $A$ is an $n \times n$ matrix over $F$, and $b$ is a column vector over $F$ and $x = \[ x_1, \ldots, x_n \]^T$ the solution column vector. The determinant is an alternating $n$-linear map $\textrm{ det } : V \ldots V \to F$ where $V = F^n$, and the determinant of a matrix $A$ is, by definition, the value of the determinant with $A$ considered as an element of $V^n$ where each column of $A$ is considered as an element of $V$. The equation $Ax = b$ can be written in the vector form as $x_1 A_1 + \ldots + x_n A_n = b$ where $A_i$ is the $i$th column of $A$; in other words, is the vector $b$ in the column space of $A$? Consider the determinant of $A$ viewed as the value of the function $\textrm{ det }$ at the "point" $(A_1, \ldots, A_n)$ and let $B_i =  (A_1, \ldots,A_{i-1}, b, A_{i+1} \cdots, A_n)$ be the matrix obtained by replacing the $i$th column of $A$ by $b$. Since the determinant function is multilinear and alternating,

$$
\begin{align*}
det(B_i) &= det \left( A_1, \ldots, A_{i-1}, \sum x_k A_k, A_{i+1}, \ldots, A_n \right)
\\
&= x_i \cdot det \left(A_1, \ldots , A_{i-1}, A_i, A_{i+1}, \ldots, A_n \right) \\
&= x_i \cdot det(A).
\end{align*}
$$

So, if the columns are not linearly dependent \underline{over $R$}, hence over $F$, then $Ax = 0$ has a nontrivial solution $\[x_1, \ldots, x_n \]^T$, with $x_i$ nonzero for some $i$. Replacing the $i$th column of $A$ by $0$ and expanding its determinant in two ways as above we see that $x_i \cdot det(A)$ is $0$ for all $i$. Since $R$ is a domain and $x_i$ is nonzero for some $i$ it follows that the determinant of $A$ is $0$. Conversely, suppose that the columns of $A$ are linearly dependent over $R$. Then they are linearly independent over $F$ too, otherwise any linear dependence relation over $F$ yields one over $R$ by multiplying the relation over $F$ by the common denominator of its coefficients. Therefore the columns of $A$ form a basis of $F^n$ over $F$. In particular, the standard basis vectors can be expressed as a linear combination of the columns over $F$. Now expanding the determinant $\textrm{ det }(e_1, \cdots, e_n)$ in terms of the columns of $A$, we see that $1 = x \textrm{ det } (A)$ for some $x$ in $F$, so that the determinant of $A$ is nonvanishing.

In summary, if $R$ is an integral domain and $A$ is a $n\times n$ matrix over $R$ then the determinant of $A$ is vanishing if and only if its columns are linearly dependent over $R$. Now we proceed to prove that in the free $R$-module $R^n$ any $n+1$ elements are linearly dependent over $R$. Choose a basis $e_1, \ldots, e_n$ of $M$ and let $y_1, \ldots, y_{n+1}$ be the given $n+1$ elements. Then each $y_i$ is a linear combination of $e_i$ over $R$ (since $e_i$ is a \underline{basis}) and the corresponding coefficient matrix obtained by writing the coefficients of $y_i$ in the expansion as the $i$th column is an $n \times (n+1)$ matrix. By padding this matrix with an extra row consisting of all zeros, we obtain an $(n+1) \times (n+1)$ matrix with determinant $0$. By the above discussion, it follows that the columns of the matrix are linearly dependent, and clearly any such dependence relation gives a dependence relation among $y_i$s. Indeed, if $\sum \alpha_i \[ a_{1i}, a_{2i}, \cdots a_{ni}, 0 ]^T = 0$ then $\sum_{j =1}^n \alpha_i a_{j i} = 0$ for all $1 \leq i \leq n$, so that 

$$
\sum_{i =1}^n \alpha_i y_i = \sum_{i=1}^n \alpha_i \sum_{j = 1}^n a_{j i} e_j = \sum_{j = 1}^n  \left( \sum_{i=1}^n \alpha_i a_{ji} \right) e_j = 0.
$$

**Rank**: Let $M$ be a finitely generated module over an integral domain $R$. The rank of $M$ is the maximal number of elements that are linearly independent over $R$. By the above discussion, it is clear that the rank is a well-defined notion. 

An element $m \in M$ is called a torsion element if there is a nonzero element of $R$ that annihilates it. A module is said to be a torsion module if every element in it is a torsion element. 

Suppose the rank of $M$ is $n$ (and $M$ not necessarily free), let $x_1, \ldots, x_n$ be a maximal set of linearly independent elements. Then $N := Rx_1 + \ldots + R x_n$ is a free submodule of rank $n$, and for any $x \in M - N$ the set $\{ x, x_1, \ldots, x_n \}$ is not linearly dependent, so that $r \cdot x + \sum_{i =1}^n r_i x_i = 0$ with, clearly, $r$ nonzero (if $r$ is $0$ then some $r_i$ is nonzero so that $\{x_1, \ldots x_n \}$ is not linearly independent). Therefore the quotient module $M/N$ is a torsion module.  Conversely, if $M$ contains a free module $N$ of rank $n$ such that $M/N$ is a torsion module then $M$ has rank $n$. Indeed, let $y_1, \ldots, y_{n+1}$ be $n+1$ elements in $M$, and $x_1, \ldots, x_n$ be a basis of $N$. Since $M/N$ is a torsion module $r_i y_i = \sum_{j = 1}^n a_{ji} x_i$ for all $1 \leq i \leq (n+1)$. Proceeding as in the **(Determinant trick)** above, we see that the $(n+1)$ elements $r_i y_i$ are linearly dependent, hence $y_i$ are linearly dependent. Thus $M$ has rank at most $n$, but since $x_1, \ldots, x_n$ are linearly independent it follows that $M$ has rank exactly $n$.

We use the above assertions to show the following: let $R$ be a domain and $M$ an module with $N$ a submodule. Suppose $M$ has rank $n$, $N$ has rank $r$ and $M/N$ has rank $s$. Then $n = r + s$. Let $x_1, \ldots, x_r$ be a maximal linearly independent elements of $N$, and let $x_{r+1}, \ldots, x_{r+s}$ be a maximal, necessarily, linearly independent elements of $M$ that maps to a maximal linearly independent elements of $M/N$. Then the set $\{x_1, \ldots, x_{r+s} \}$ is linearly independent set of $M$ for if $\sum_{i = 1}^{r +s}  \alpha_i x_i = 0$ then $\sum_{i=r+1}^{r+s} \alpha_i x_i = 0$ in $M/N$ so that $\alpha_i = 0$ for all $r +1 \leq i \leq r +s$ because $x_i+N$, $r+1 \leq i \leq r + s$ is a linearly independent subset of $M/N$. Thus we have $\sum_{i =1}^{r +s } \alpha_i x_i = \sum_{i =1}^{r} \alpha_i x_i = 0$ implies $\alpha_i = 0$ for $1 \leq i \leq r$ too because $\{ x_1, \ldots, x_r \}$ is a linearly independent subset of $N$. Therefore the rank of $M$ is at least $r +s $. Similarly, maximality is proved.

This result is used in induction. If $M = M_1 \oplus M_2$ and if we know the ranks of $M$ and $M_1$ then we infer the rank of $M_2$.



**Theorem:** Let $R$ be a PID,  $M$ be a free module of rank $n$ over $R$ and $N$ be a submodule of $M$. Then $N$ is a free $R$-module of rank at most $n$. Furthermore there exists a basis $y_1, \ldots, y_n$ of $M$ and elements $a_1, \ldots, a_m$ of $R$ satisfying the divisibility conditions $a_1 \mid \ldots \mid a_m$ such that $a_1 y_1, \cdots a_m y_m$ is a basis of $N$. The elements $a_i$ of $R$ are called the **invariant factors** of $M$.

**Proof:**

1. Fix a basis $x_1, \ldots, x_n$ of $M$. Assuming that $N$ is nontrivial, consider the set of $R$-linear functionals $M \to R$, and the family of ideals $\{ \phi(N) : \phi \in Hom(M,R) \}$ in $R$. Since $R$ is Noetherian (every ideal of $R$ is finitely generated, n fact by a single element) it follows that the set contains a maximal element, say $(a_1)$ with $\nu(y) = a_1$ for some linear functional $\nu: M \to R$. Since $N$ is nonzero, at least one of the ideals $\pi_i(N)$ is nonzero, where $\pi_i$ is the canonical projections with respect to the above choice of basis of $M$. In particular, $a_1$ is nonzero, hence $y$ is nonzero. 

2. Now show that $a_1$ divides the generator of $\phi(N)$ for all linear functionals $\phi: N \to R$. In particular, it divides $\pi_i(N)$ so that $\pi_i(N) = a_1 b_i$ for some $b_i$ in $R$. Define the "partitions-of-unity" 
$$
y_1 = b_1 x_1 + \ldots  + b_n x_n, a_1 y_1 = y , \nu(y_1) = 1
$$

3. Now show that $M = Ry_1 \oplus ker \nu$ and $N = a_1 y_1 \oplus (ker \nu) \cap N$. 

4. We shall prove that $\ker \nu$ has rank $n-1$ below; for a while accept this and proceed and apply the induction hypothesis to conclude that $ker(\nu)$ has a basis $y_2, \ldots, y_n$ and there exists elements $a_2, \ldots, a_m$  satisyfing $a_2 \mid \ldots \mid a_m$ such that $a_2 y_2, \ldots, a_m y_m$ is a basis of $ker(\nu) \cap N$. 

5. By considering the $R$-linear functional $\psi$ that sends $y_1$ and $y_2$ to $1$ and the remaining $y_i$ to $0$, show that $a_1 \mid a_2$.


Let $M$ be a finitely generated module over a PID $R$ of rank $n$. Let $x_1, \ldots, x_n$ be a choice of maximal linearly independent elements of $M$, and consider the natural surjection $\pi: R^n \to M$ obtained by mapping $e_i \to x_i$. Then $ker \phi$ is free of rank at most $m$ and there exists a choice of basis $y_1, \ldots, y_n$ of $R^n$ (not necessarily equal to the standard basis $e_1, \ldots, e_n$) and elements $a_1, \ldots, a_m$ satisfying the divisibility conditions $a_1 \mid \ldots \mid a_m$ such that $a_1 y_1, \ldots, a_m y_m$ is a basis of $ker \pi$. Therefore
$$
M \cong Ry_1 \oplus \ldots \oplus R y_n / R a_1 y_1 \oplus \ldots \oplus a_m y_m \cong R/a_1 \oplus \ldots \oplus R/a_m \oplus R^{n-m}.
$$

The submodule of $M$ corresponding to the torsion part $R/a_1 \oplus R/a_m$ is the torsion submodule of $M$ and to that of $R^{n-m}$ is the free part with **free rank** $r = n-m$. Thus $M$ can be decomposed into torsion submodule and a free submodule, but note that there is no canonical way to do it. Note that such a decomposition is not possible if $R$ is not a PID. For example, if $R = \mathbb{Z}\[ X \]$ then the module $M = (2,X)$ has rank $1$ and both $\{ 2 \}$ and $\{ X \}$ are linearly independent subsets over $R$, but $M$ has free rank $1$ with no torsion and $M$ is not free.


By the Chinese Remainder Theorem, each summand of the form $R/a$ in the above decomposition is a direct sum of finitely many summands of the form $R/p^k$ for some $k \geq 1$. Collecting all the summands belonging to various summand $R/a_i$ in the above decomposition, we obtain what is called decomposition of $M$ in **elementary divisor form**. Thus every finitely generated module over a PID $R$ is of the form 
$$
M \cong R^r \oplus R/(p_1^{\alpha_1} \oplus \ldots \oplus R/(p_r^{\alpha_r})
$$
where $r \geq 0$ and $p_1, \ldots, p_r$ are primes of $R$ and not necessarily distinct.

We now see that the elementary divisor of $M$ is essentially unique. Since the torsion parts and the free parts of a module $M$ are invariant under isomorphism we may assume that $M$ is a torsion module. Now note that if $M = R/(a)$ and if $p$ is not a divisor of $a$ then $M/pM$ is $0$ otherwise $R/(p)$ a field. Thus, if $M$ is a decomposition of $p$-primary components which are direct sum of $R/p^{\alpha_i}$ then by reducing $M$ modulo $pM$ we are left with a direct sum of the form $R/p^{\alpha_i} \oplus R/p^{\alpha_k}$ for some positive integers $\alpha_1, \ldots, \alpha_k$. Clearly it suffices to prove the uniqueness assuming that $M$ is a $p$-primary component. Now consider the submodule $pM$ and do the induction on the power of $p$ in the annihilator of $M$ to obtain the uniqueness. 

We finally note that the elementary divisors of $M$ are the prime power factors of the invariant factors of $M$. Conversely, the largest invariant factor of $M$ is the product of the largest of the distinct prime powers among the elementary divisors of $M$, the next largest invariant factor is the product of the largest of the distinct prime powers among the remainaing elementary divisors of $M$, and so on. Thus orresponding to invariant factor decomposition of $M$ there is a unique decomposition of $M$ in elementary divisor form and conversely.













