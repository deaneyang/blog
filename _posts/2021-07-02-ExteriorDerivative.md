---
layout: post
title:  "A simple definition of the exterior derivative"
date:   2021-07-02
categories: blog math differential-geometry
---

(This post is based on my answer to a [question posted on math.stackexchange.com](https://math.stackexchange.com/questions/4188943/exterior-derivative-of-one-form-vs-torsion-of-connection).)

<p>
The exterior derivative of a $1$-form is usually defined as follows:
Let $df$ denote the differential of a scalar function $f$. The exterior derivative is defined to be a linear operator from $1$-forms to $2$-forms that satisfies the following properties: Given any scalar function $f$ and $1$-form $\theta$,
\begin{align*}
d(df) &= 0\\
d(f\theta) &= df\wedge\theta + fd\theta.
\end{align*}
It is not difficult to show that, if such an operator exists, it is unique.
We can use local coordinates to show that operator $d$ does exist locally by defining the exterior derivative of $\theta = a_i\,dx^i$ to be
$$
d\theta = da_i\wedge\,dx^i.
$$
It is straightforward to verify that this satisfies the properties above. Uniqueness of $d$ implies that it is in fact a global operator on the manifold.
</p>

<p>
The standard coordinate-free definition is, given vector fields $V$ and $W$,
\begin{equation}\label{standard}
\langle d\theta, V\otimes W\rangle
=
\langle V, d\langle W,\theta\rangle\rangle
-
\langle W, d\langle V,\theta\rangle\rangle
-
\langle\theta,[V,W]\rangle.
\end{equation}
It is necessary, however, to verify that $d\theta$ is in fact a tensor.
</p>

<p>
Here is another way that is new to me. Let $\nabla$ be a torsion-free connection. In other words, it defines a directional derivative of vector fields that satisfies the following properties: Given vector fields $U$, $V$, and $W$ and a scalar function $f$,
\begin{align}
\nabla_{U+V}W &= \nabla_UW + \nabla_VW \label{additive}\\
\nabla_{fV}W &= f\nabla_VW\\
\nabla_U(V+W) &= \nabla_UV + \nabla_UW\\
\nabla_V(fW) &= \langle V,df\rangle W + f\nabla_VW \label{derivation}\\
\nabla_VW - \nabla_WV &= [V,W] \label{torsion-free}
\end{align}
Equations \eqref{additive}-\eqref{derivation} define a connection, and equation \eqref{torsion-free} is the torsion-free property.
</p>

<p>
The connection can be extended uniquely to an operator on $1$-forms by assuming the product rule
\begin{equation}\label{product}
\langle W, d\langle \theta, V\rangle\rangle
= \langle \nabla_W\theta,V\rangle + \langle \theta, \nabla_WV\rangle.
\end{equation}
Since the left side does not depend on the connection, neither does the right. Therefore, if $\tilde\nabla$ is another torsion-free connection, then
$$
\langle \tilde\nabla_W\theta,V\rangle + \langle \theta, \tilde\nabla_WV\rangle
=
\langle \nabla_W\theta,V\rangle + \langle \theta, \nabla_WV\rangle
$$
By this and the torsion-free property \eqref{torsion-free},
\begin{equation}
\begin{split}
\langle V, \tilde\nabla_W\theta\rangle - \langle W,\tilde\nabla_V\theta\rangle
&=
\langle V, \nabla_W\theta\rangle - \langle W,\nabla_V\theta\rangle
+ \langle\theta, \tilde\nabla_VW - \tilde\nabla_WV - \nabla_VW + \nabla_WV\rangle\\
&=
\langle V, \nabla_W\theta\rangle - \langle W,\nabla_V\theta\rangle
+ [V,W] - [V,W]\\
&=
\langle V, \nabla_W\theta\rangle - \langle W,\nabla_V\theta\rangle.
\end{split}\label{independent}
\end{equation}
</p>

<p>
We now define the exterior derivative of $\theta$ to be the $2$-form $d\theta$ such that, if $V, W \in T_pM$, then
$$
\langle d\theta(p), V\otimes W\rangle = \langle V, \nabla_W\theta(p)\rangle - \langle W,\nabla_V\theta(p)\rangle.
$$
It follows directly from this definition that $d\theta(p)$ is an antisymmetric bilinear function on $T_pM$ and therefore a well-defined exterior $2$-tensor.
By \eqref{independent}, this definition is independent of the connection used.
</p>

<p>
The standard coordinate-free definition \eqref{standard} can be obtained from this definition and \eqref{product}:
\begin{align*}
\langle d\theta, V\otimes W\rangle
&= \langle \nabla_V\theta,W\rangle - \langle V,\nabla_W\theta\rangle\\
&= \langle V,d\langle\theta,W\rangle\rangle - \langle \theta, \nabla_VW\rangle
- \langle W,d\langle\theta,V\rangle\rangle + \langle \theta,\nabla_WV\rangle\\
&= \langle V,d\langle\theta,W\rangle\rangle
- \langle W,d\langle\theta,V\rangle\rangle - \langle \theta,[V,W]\rangle\\
\end{align*}
</p>

