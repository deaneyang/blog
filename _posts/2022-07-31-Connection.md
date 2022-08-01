---
layout: post
title:  "Covariant differentiation on a bundle"
date:   2022-07-31
categories: blog math vector-bundle principal-bundle connection covariant-differentiation covariant-derivative
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$


<p>
Details to come, but here is the brief version.
</p>

<p>
Let $M$ be a smooth manifold and $B$ be a bundle over $M$. This implies that there is a projection map $\pi: B \rightarrow M$ that is a submersion. For each $m \in M$,
$$
F_m = \pi^{-1}(m)
$$
is called the fiber over $m$.
</p>

<p>
Recall that a section of $B$ is a map
$$
s: M \rightarrow B
$$
such that for each $m \in M$,  $s(m) \in F_m$.
It should be considered to be the generalization of the graph of a function. In particular, given a manifold $F$ and a map $f: M \rightarrow F$, the graph of $f$, given by
$$
s(m) = (m, f(m)),\ m \in M,
$$
is a section of the trivial bundle $B = M\times F$.
</p>

<p>
A <em>connection</em> is a way to differentiate a section of a bundle. It is also called covariant differentiation and usually denoted $\nabla$.
</p>

<p>
The guiding example of a connection is for the trivial bundle $B = M\times F$, where we can define the covariant derivative of a section $s$ to be the differential
\begin{align*}
T_mM &\rightarrow T_{f(m)}F\\
v &\mapsto D_vf(m).
\end{align*}
We would like to extend this to an arbitrary bundle and define the covariant derivative of a section of $s: M \rightarrow B$ to be, for each $m \in M$, a linear map
\begin{align*}
T_mM &\rightarrow T_{s(m)}F_m\\
v &\mapsto \nabla_v s(m)
\end{align*}
that depends only on first derivatives of $s$.
</p>

<p>
We could do this by using a local trivialization of of $B$ to represent a section $s$ as the graph of a map $f$. The covariant derivative of $s$ could then be defined to be the differential of $f$, as we did for the trivial bundle. However, this definition depends on the local trivialization used, and we want something that is independent of local trivializations.
</p>

<p>
There is already a natural way to differentiate a section, namely its differential (also known as its Jacobian or pushforward), which defines for each $m \in M$, a linear map
\begin{align*}
T_mM &\rightarrow T_{s(m)}B\\
v &\mapsto D_vs(m).
\end{align*}
This is not quite what we want.
</p>

<p>
Moreover, for the trivial bundle $B = M\times F$, the differential of $f$ is the composition of a projection map and the differential of $s$,
$$
D_vf(m) = \Pi_{(m,f(m))}\circ Ds,
$$
where
\begin{align*}
\Pi_{(m,f)}: T_{(m,f)}(M\times F) &\rightarrow T_fF\\
(v,\dot{f}) &\mapsto \dot{f}
\end{align*}
projects the tangent space of $M\times F$ onto the tangent space of $F$. This leads to the following definition of a covariant derivative.
</p>

<p>
We can choose, for each $m \in M$ and $f \in F_m$, a linear projection map$$
\Pi_f: T_fB \rightarrow T_fF_m,
$$
and define the covariant derivative of a section $s$ in the direction $v \in T_mM$ by
$$
\nabla_vs(m) = \Pi_{s(m)}(D_vs(m)).
$$
Note that the connection depends on the projection maps chosen and therefore is not uniquely determined by the bundle itself.
</p>

<p>
If the bundle is either a vector or principal bundle, then we want the covariant derivative to satisfy an additional condition, namely that it be a derivation.
</p>

<p>
This is all that is needed to define what a connection on a bundle is.
</p>