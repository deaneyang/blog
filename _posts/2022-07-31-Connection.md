---
layout: post
title:  "Covariant differentiation on a bundle"
date:   2022-06-05
categories: blog math vector-bundle principal-bundle connection covariant-differentiation covariant-derivative
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$


<p>
Details to come, but here is the brief version.
</p>

<p>
Let $M$ be a smooth manifold and $B$ be a bundle over $M$. This means that there is a projection map $\pi: B \rightarrow M$ that is a submersion and there exists a manifold $F$, called the fiber, such that for each $m \in M$, $\pi^{-1}(m)$ is diffeomorphic to $F$. The implicit function theorem shows that this is equivalent to the standard definition of a bundle. For each $m \in M$, we denote the fiber over $m$ by
$$
F_m = \pi^{-1}(m).
$$
</p>

<p>
Recall that a section of $B$ is a map
$$
s: M \rightarrow B
$$
such that $\pi(s(m)) = m$ for any $m \in M$.
It should be considered to be the generalization of the graph of a function. In particular, given a map $f: M \rightarrow F$, the graph of $f$, given by
$$
s(m) = (m, f(m)),\ m \in M,
$$
is a section of the trivial bundle $B = M\times F$.
</p>

<p>
A <em>connection</em> is a way to differentiate a section of a bundle. It is also called covariant differentiation and usually denoted $\nabla$.
</p>

<p>
There in fact is already a natural way to differentiate a section. Its differential, Jacobian, or pushforward defines for each $m \in M$, a linear map
$$
s_*: T_mM \rightarrow T_{s(m)}B.
$$
When $B = M\times F$, then the guiding example of a covariant derivative is the differential
$$
f_*: T_mM \rightarrow T_{f(m)}F.
$$
It is important to note that $f_*$ is linear and is the composition of two linear maps,
$$
f_* = \Pi_f\circ s_*,
$$
where $\Pi_m: T_f(M\times F) \rightarrow T_fF$ is the vertical projection map.
</p>

<p>
Given a section of $s: M \rightarrow B$, we want the covariant derivative of $s$ to be, for each $m \in M$, a linear map
\begin{align*}
T_mM &\rightarrow T_{s(m)}F_m\\
v &\mapsto \nabla_v s(m)
\end{align*}
that depends only on first derivatives of $s$.
</p>

<p>
An obvious way to do this is to choose, for each $m \in M$ and $f \in F_m$, a linear projection map$$
\Pi_f: T_fB \rightarrow T_fF_m,
$$
and, given a section $s$ and $v \in T_mM$,
$$
\nabla_vs(m) = \Pi_{s(m)}s_*v.
$$
</p>

<p>
If the bundle is either a vector or principal bundle, then we want the covariant derivative to satisfy an additional condition, namely that it be a derivation.
</p>

<p>
This is all that is needed to define what a connection on a bundle is.
</p>