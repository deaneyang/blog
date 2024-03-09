---
layout: post
title:  "Chain Rule for Maps"
date:   2024-03-09
categories: blog math multivariable-calculus maps chain-rule differential
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$


<p>
Let $M$ be an open subset of $\R^m$ and $N$ be an open subset of $\R^n$. Everything below is done without using coordinates, so you can simply assume that $M$ is an $m$-manifold and $N$ is an $n$-manifold.

Let $F: M \rightarrow N$ be a $C^1$ map.
</p>

### Differential of a Map ###

<p>
Recall that the <b>directional derivative</b> of $F$ at $x \in M$ in the direction $v \in \R^m$ is defined to be
$$ D_vF(x) = \left.\frac{d}{dt}\right|_{t=0}F(c(t)), $$
where $c: I \rightarrow M$ is a $C^1$ curve such that
$$ c(0) = x\text{ and }c'(0) = v. $$
In other words, if $v \in \R^n$ is the velocity vector of a curve $c$ passing through $x \in M$, then $D_vF(x)$ is the velocity vector of the curve $F\circ c$ at $F(x)$.
</p>

<p>It is easy to check that the map
$$ v \mapsto D_vF(x) $$
is linear. The <b>differential</b> of $F$ at $x$ is defined to be this linear map and is denoted
$$ \partial F(x): \R^m \rightarrow \R^n. $$
This is also called the <b>Jacobian</b> and often written as a matrix of partial derivatives. We avoid doing this here.
</p>

#### Aside
<p>
If $M$ and $N$ are manifolds, then the linear map is
$$ \partial F(x): T_xM \rightarrow T_{F(x)}N $$
and often denoted $F_*$.
</p>

### Chain Rule

<p>
Let $O$ be an open subset of $\R^p$ and
$$
G: N \rightarrow O
$$
be a $C^1$ map. Given $x \in M$, we want to find the formula for the differential of
$$ G\circ F: M \rightarrow O. $$
</p>

<p>
Let $c: I \rightarrow M$ be a curve such that $c(0) = x$ and $c'(0) = v$. This in turn defines a curve
$$ F\circ c: I \rightarrow N, $$
which satisfies $(F\circ c)(0) = F(x)$ and, repeating what we said above,
\begin{align*}
(F\circ c)'(0) &= \left.\frac{d}{dt}\right|_{t=0}F(c(t))\\
&= D_vF(x) = \partial F(x)v.
\end{align*}

Therefore,
\begin{align*}
D_v(G\circ F)(x) &= \left.\frac{d}{dt}\right|_{t=0}G(F(c(t))\\
&= \left.\frac{d}{dt}\right|_{t=0}G((F\circ c)(t))\\
&= D_{(F\circ c)'(0)}G(F(x))\\
&= D_{\partial F(x)v}(F(x))\\
&= (\partial G)(F(x))(\partial F(x)v).
\end{align*}
This proves the chain rule
$$ \partial(G\circ F)(x) = (\partial G)(F(x))\circ (\partial F(x)). $$