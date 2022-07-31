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
Let $M$ be a smooth manifold and $B$ be a bundle over $M$. This means that there is a projection map $\pi: B \rightarrow M$ that is a submersion and there exists a manifold $F$, called the fiber, such that for each $m \in M$, $\pi^{-1}(m)$ is diffeomorphic to $F$. The implicit function theorem shows that this is equivalent to the standard definition of a bundle.
</p>

<p>
Recall that a section of $B$ is a map $s: M \rightarrow B$ such that $\pi(s(m)) = m$, for any $m \in M$. It should be considered to be a generalization of the graph of a function. In particular, given a map $f: M \rightarrow F$, the graph of $f$, given by
$$
s(m) = (m, f(m)),\ m \in M,
$$
is a section of the trivial bundle $B = M\times F$.
</p>

<p>
A <em>connection</em> is a way to differentiate a section of a bundle. It is also called covariant differentiation and usually denoted $\nabla$.
</p>

<p>
There in fact is already a natural way to differentiate a section. Its differential, Jacobian, or pushforward defines a map
$$
s_*: T_*M \rightarrow T_*B.
$$
The covariant derivative of $s$ is a generalization of the differential
$$
f_*: T_*M \rightarrow T_*F
$$
for the trivial bundle.
</p>

In other words, we want, for each $m \in M$, a map
$$
\nabla s(m): T_mM \rightarrow T_{s(m)}F_m,
$$
where $F_m = \pi^{-1}(m)$, that depends only on first derivatives of $s$. The most obvious way to do this is to choose, for each $m \in M$ and $f \in F_m$, a linear projection map
$$
\Pi_f: T_fB \rightarrow T_fF_m,
$$
and, given a section $s$ and $v \in T_mM$,
$$
\nabla_vs(m) = \Pi_{s(m)}s_*v.
$$

<p>
If the bundle is either a vector or principal bundle, then we want the covariant derivative to satisfy an additional condition, namely that it be a derivation.
</p>

<p>
This is all that is needed to define what a connection on a bundle is.
</p>