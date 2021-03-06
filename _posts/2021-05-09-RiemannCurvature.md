---
layout: post
title:  "A simple way to discover the Riemann curvature tensor"
date:   2021-01-28
categories: blog math differential-geometry riemannian-geometry
---
$\newcommand{\R}{\mathbb{R}}$
A natural question is determining when two Riemannian metrics are locally isometric. In other words, given two Riemannian metrics
\begin{equation}\label{metrics}
  g = g_{ij}(x)\,dx^i\,dx^j\text{ and }h = h_{ij}(y)\,dy^i\,dy^j,
\end{equation}
we want to know whether there exists a smooth diffeomorphism $y(x)$ such that
\begin{equation}\label{equation:isometric}
 g_{ij}(x)\,dx^i\,dx^j =  h_{ij}(y(x))\,\frac{\partial y^i}{\partial x^p}\frac{\partial y^j}{\partial x^q}\,dx^i\,dx^j.
\end{equation}
This is in general a hard question to answer. We can, however, ask a simpler question. When are two metrics equal up to, say, second order at a given point? We know immediately that there is no obstruction in the first order expansion of a metric, since we can always change coordinates so that both metrics are equal to $\delta_{ij}$ at a point and their first partial derivatives vanish at the point, too. We show below that there is indeed an obstruction in the second order expansion of the metric, and this leads to the definition of the Riemann curvature tensor.

We begin by recalling how to normalize the metric up to first order. This can also be done using exponential coordinates (also known as geodesic normal coordinates), but the direct proof is quite simple.

<div class="lemma">
  Given a Riemannian metric $h_{ij}\,dy^i\,dy^j$ on an open neighborhood $O$ of $0 \in \R^n$, there exists a diffeomorphism $x \mapsto y(x)$ such that the metric $g_{ij}\,dx^i\,dx^j$ given by \eqref{equation:isometric} satisfies the following properties: For every $1 \le i, j, k \le n$,
  \begin{align}
    y(0) &= 0\\
    g_{ij}(0) &= \delta_{ij} \label{zeroth-order-metric}\\
    \partial_kg_{ij}(0) &= 0. \label{first-order-metric}
  \end{align}
The diffeomorphism is unique up to second order.
</div>

<div class="proof">
  We do this through a sequence of coordinate changes. First, to satisfy \eqref{zeroth-order-metric}, it suffices to do a linear change of coordinates
  $$
    y^i =  A^i_jx^j,
  $$
  where
  $$
    A^p_ih_{pq}(0)A^q_j = \delta_{ij}.
  $$
  It suffces to set $A$ to the inverse of the square root of the symmetric positive definite matrix.

  We can now assume that $h_{ij}(0) = \delta_{ij}(0)$. We now use a diffeomorphism of the form
\begin{equation}\label{first-order-map}
    y^i(x) = x^i  + A^i_{pq}x^px^q,
\end{equation}
  where we can assume that $A^i_{pq} = A^i_{qp}$.
  Let
  $$
    \partial_i = \frac{\partial}{\partial x^i}.
  $$
  Differentiating \eqref{equation:isometric} and evaluating at $x = 0$, we get
  \begin{align*}
    g_{ij}(0) &= \delta_{ij}\\
    \partial_kg_{ij}(0) &= \partial_kh_{ij}(0) + A^i_{jk} + A^j_{ik}.
  \end{align*}
  We want to solve for the $A^i_{jk}$ so that the right side equals $0$. If we write that three times, we get
  \begin{align*}
    0 &= \partial_ih_{jk}(0) + A^j_{ki} + A^k_{ij}\\
    0 &= \partial_jh_{ki}(0) + A^k_{ij} + A^i_{jk}\\
    0 &= \partial_kh_{ij}(0) + A^i_{jk} + A^j_{ki}\\
  \end{align*}
  If we add the last two equations and subtract the first, we get
  $$
    A^i_{jk} = \frac{1}{2}(\partial_ih_{jk} - \partial_jh_{ki} - \partial_kh_{ij}).
  $$
  Using this in \eqref{first-order-map} implies that $\partial_kg_{ij}(0) = 0$.
</div>

We therefore assume that we have two metrics \eqref{metrics} such that both satisfy \eqref{zeroth-order-metric} and \eqref{first-order-metric}.
Now consider a local diffeomorphism of the form
\begin{equation}\label{third-order-map}
y^i = x^i + B^i_{jkl}x^jx^kx^l +\text{ higher order terms}.
\end{equation}
If we now differentiate \eqref{equation:isometric} twice and evaluate at $0$, we get

$$
\partial_{kl}^2g_{ij}
  = \partial_{kl}^2h_{ij}
    + \partial_{jkl}^3y^i + \partial_{ikl}^3y^j.
$$

Permuting the indices, we get
\begin{equation}
  \partial_{jl}^2g_{ik} = \partial_{jl}^2h_{ik} + \partial_{jkl}^3y^i \label{g1}
\end{equation}
\begin{equation}
  \partial_{ik}^2g_{jl} = \partial_{ik}^2h_{jl} + \partial_{ikl}^3y^j \label{g2}
\end{equation}
\begin{equation}
  \partial_{jk}^2g_{il} = \partial_{jk}^2h_{il} + \partial_{jkl}^3y^i \label{g3}
\end{equation}
\begin{equation}
  \partial_{il}^2g_{jk} = \partial_{il}^2h_{jk} + \partial_{ikl}^3y^j \label{g4}
\end{equation}
Therefore,
$$
  \eqref{g1} + \eqref{g2} - \eqref{g3} - \eqref{g4}
$$
implies that

$$
  \partial^2_{jl}g_{ik} + \partial^2_{ik}g_{jl}
  - \partial^2_{jk}g_{il} - \partial^2_{il}g_{jk}
  =
  \partial^2_{jl}h_{ik} + \partial^2_{ik}h_{jl}
  - \partial^2_{jk}h_{il} - \partial^2_{il}h_{jk}
$$

It follows that, if we define

$$
  R^g_{ijkl} = -\frac{1}{2}(\partial^2_{jl}g_{ik}(0) + \partial^2_{ik}g_{jl}(0)
  - \partial^2_{jk}g_{il}(0) - \partial^2_{il}g_{jk}(0)),
$$

then if two metrics $g$ and $h$ are isometric up to second order near $0$, then, there exist local coordinates for each metric such that \eqref{zeroth-order-metric}, \eqref{first-order-metric}, and

$$
  R^g_{ijkl} = R^h_{ijkl}.
$$

The fact that this is invariant under local diffeomorphisms given by \eqref{third-order-map} implies that it transforms as a $4$-th order tensor under arbitrary local diffeomorphisms. In other words, it is a coordinate-independent invariant of the metric. It is, in fact, the Riemann curvature tensor at $0$.