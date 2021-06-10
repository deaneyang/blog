---
layout: post
title:  "Solving Underdetermined Systems of PDEs à Gromov"
date:   2021-06-10
categories: blog math PDE Gromov Cartan
---
$\newcommand{\R}{\mathbb{R}}$

<p>
Gromov, in $\S 2$ of his book <i>Partial Differential Relations</i>, proves that
there exist 
many linear inhomogeneous underdetermined systems of PDE's of the form
$$
Du = f
$$
that can be solved with an arbitrary righthand side $f$
by {\em differentiating $f$} rather than using an
integral operator, which is the usual practice. This is
completely counterintuitive for most people working in analysis.
</p>

I describe below an example of how this works. In
subsequent sections I describe how Gromov's approach can be explained
and extended using Pfaff's theorem for a nondegenerate differential
$1$-form. I would like to thank Robert Bryant for explaining all of
this to me.

### Examples

<p>
A trivial example of Gromov's approach is the underdetermined PDE
$$
\sum_{i=1}^n a_i\partial_iu + v = f,
$$
which can be solved explicitly by simply setting $u = 0$ and $v = f$.
Here, we work through a more interesting example that Gromov often mentions.
</p>

<p>
Suppose, given smooth nonzero functions $a$ and $b$ on $\R$, we want to solve
\begin{equation}\label{ode}
au' + bv' = f,
\end{equation}
for any smooth function $f$ on $\R$.
</p>

<p>
An obvious way to solve this is to let $v$ be any smooth function and integrate:
$$
u(t) = u_0 + \int_{s=0}^{s=t}\frac{f-bv'}{a}\,ds.
$$
If, for example, $a$ and $b$ are constant functions, then this is the only way to solve the equation.
</p>

<p>
We show, however, that if $a$ and $b$ satisfy appropriate nondegeneracy conditions (which rule out constant functions), there are
explicit pointwise formulas (in terms of $a$, $b$, and $f$)
for functions $u$ and $v$ on a neighborhood of $0 \in
\mathbb{R}$ that satisfy \eqref{ode}.
</p>

<p>
First, we rewrite \eqref{ode} as
$$
D\begin{bmatrix}u \\ v\end{bmatrix}
= \begin{bmatrix} f \end{bmatrix},
$$
where
$$
D = \begin{bmatrix} a&b \end{bmatrix}\frac{d}{dx},
$$
To solve this equation for any function $f$, it suffices to find, for some $\delta > 0$, a right
inverse $R: C^\infty((-\delta,\delta)) \rightarrow
C^\infty((-\delta,\delta), \R^2)$ such that
\begin{equation}\label{right}
DR = I.
\end{equation}
</p>

Gromov's brilliant insight is that many underdetermined
differential operators have a right inverse that is also a
differential operator, which can be found by a 
pointwise algebraic calculation.

<p>
For this particular example, we solve for a zero-th order differential operator
$$
R = \begin{bmatrix} p \\ q\end{bmatrix}.
$$
If we try to do this by solving use \eqref{right} directly, we get a system
of ODE's for the components of $R$, which has only made the problem
even more difficult.
</p>

<p>
The trick is to note that \eqref{right} holds if and only if the
formal adjoints of $R$ and $D$ satisfy
\begin{equation}\label{adjoint}
R^*D^* = I,
\end{equation}
where
$$
D^*f = \frac{d}{dx}\begin{bmatrix} a \\ b\end{bmatrix}f =
\begin{bmatrix} af' + a'f \\ bf' + b'f\end{bmatrix}
$$
and
$$
R^* = \begin{bmatrix} p & q \end{bmatrix}.
$$
We therefore want to solve for $p$ and $q$ such that for any $f$,
\begin{align*}
f &= R^*D^*f\\
&= p(af' + a'f) + q(bf' + b'f)\\
& = (pa+qb)f' + (pa'+qb')f.
\end{align*}
This in turn is equivalent to the equations
\begin{align*}
pa + qb &= 0\\
pa' + qb' &= 1,
\end{align*}
which, if 
\begin{equation}\label{wronskian}
0 \ne \det\begin{bmatrix} a & b\\ a' & b'\end{bmatrix} = ab' - a'b,
\end{equation}
is easily solved:
$$
p = \frac{-b}{ab'-a'b},\ q = \frac{a}{ab'-a'b}.
$$
</p>

Unwinding everything, this implies that, for any function $f$, the
functions
\begin{equation}\label{gromov-solution}
u = \frac{-b}{ab'-a'b}f \text{ and }
v =  \frac{a}{ab'-a'b}f
\end{equation}
satisfy \eqref{ode}. Note that verifying this directly requires a calculation
whose outcome is not obvious.

<p>
The nondegeneracy condition required here is that
$$
a'b - ab' \ne 0.
$$
This is the Wronskian of $a$ and $b$, and a natural question is why
this is relevant. Recall that if $a$ is nonzero on an interval, then
the Wronskian vanishes on an open interval if and only if $b = ca$ for some constant
$c$. Therefore, the ODE is of the form
$$
(u + cv)' = \frac{f}{a},
$$
which can be solved only via integration.
</p>

### Generalization to underdetermined systems of PDE's

<p>
In general, a differential operator $R^*$ of some order satisfying
\eqref{adjoint} exists if and only if the coefficients of $R^*$
satisfy a pointwise linear system of equations, whose coefficients are
the coefficients of $D^*$ and their derivatives. Therefore, if the
number of equations in this system is less than or equal to the number
of unknowns (the number of coefficients of $R$) and the system has
maximal rank, then a solution always exists.
</p>

Gromov shows that if the number of equations in the original system is
sufficently less than the number of unknown functions, then the system
\eqref{adjoint} for a generic differential operator has maximal rank
and therefore \eqref{adjoint} has a solution.

He uses this result in Chapter 3 of his book to reduce the codimension needed for the existence of local isometric embeddings of a generic Riemannian metic and global
isometric embeddings of generic Riemannian metrics on manifolds that
have certain specified topological types such as the torus.

### Solving an underdetermined ODE via Pfaff

Robert Bryant was kind enough to explain how the approach described above can be
formulated and extended using
exterior differential systems. The overall point is that solutions
to \eqref{ode} correspond to integral curves of a $1$-form, which is a
contact form if \eqref{wronskian} holds. 
Pfaff's theorem states that there exist co-ordinates for which the
contact form is in normal form. Here, these co-ordinates can be
written down explicitly. These formulas can in turn
be used to obtain <i>all</i> solutions to
\eqref{ode} using only formal differentiation and linear algebra.

In fact, everything presented here, both Gromov's approach and the one
described below, works for any
first order linear ODE with two unknown functions:
\begin{equation}\label{general}
a_1u' + a_0u + b_1v' + b_0v = f.
\end{equation}
I show below how to find all solutions to this ODE.

<p>
Given co-ordinates $x, u, v$ on $\R^3$, set
\begin{align}
\theta &= a_1\,du + b_1\,dv - (f - a_0u - b_0v)\,dx \label{theta} \\
&= d(au + bv) - (f + (a_1' - a_0)u + (b_1'- b_0)v)\,dx \notag \\
&= dy - p\,dx, \label{contact}
\end{align}
where
\begin{equation}\label{yp}
y = au+bv\text{ and }p = f + Au + Bv
\end{equation}
and
$$
A = a_1' - a_0\text{ and } B = b_1' - b_0.
$$
A straightforward calculation shows that
$$
dx \wedge dy \wedge dp = - \theta \wedge d\theta = (a_1B -
b_1A)\,dx\wedge du\wedge dv.
$$
Therefore, $x, y, p$ are co-ordinates on $\R^3$ if and only if
$\theta\wedge d\theta$ is nonzero everywhere, which in turn holds if
and only
\begin{equation}\label{nondegeneracy}
a_1B - b_1A \ne 0,
\end{equation}
</p>

<p>
The functions $u(x)$ and $v(x)$ give a solution to \eqref{ode}
if and only if the curve
$$
C = \{(x, u(x), v(x))\ :\ x \in \R\} \subset \R^3
$$
is an integral curve of $\theta$ on which $dx$ is nowhere vanishing.
On the other hand, $x, y, p$ are also co-ordinates on this space if
and only if
\begin{align*}
0 &\ne dx\wedge dy\wedge dp\\
&= dx\wedge(a_1'u\,dx + a_1\,du + b_1'v\,dx + b_1\,dv)\wedge((f' + A'u +
  B'v)\,dx
+ A\,du + B\,dv)\\
&= (a_1B - b_1A)dx\wedge du\wedge dv.
\end{align*}
</p>

<p>
If we assume the nondegeneracy condition
then $\theta$ vanishes on a curve $C$ if and only if there exists a
function $g(x)$ such that for any $x \in \R$,
$$
(x,y,p) = (x, g(x), g'(x)) \in C,
$$
Therefore, functions $u$ and $v$ solve \eqref{general} if and only if
$$
\begin{bmatrix}a_1 & b_1\\ A & B\end{bmatrix}
\begin{bmatrix}u \\ v\end{bmatrix}
= \begin{bmatrix} g\\ g'-f\end{bmatrix},
$$
which holds if and only if
$$
\begin{bmatrix}u \\ v\end{bmatrix}
=
\frac{1}{a_1B-b_1A}
\begin{bmatrix} B & -b_1 \\ -A & a_1 \end{bmatrix}
\begin{bmatrix} g \\ g'-f\end{bmatrix}.
$$
The ODE \eqref{ode} is the special case where $a_0 = b_0 0$, and
Gromov's solution \eqref{gromov-solution} is the one given by setting
$g = 0$.
</p>


