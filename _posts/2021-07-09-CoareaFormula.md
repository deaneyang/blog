---
layout: post
title:  "What's the intuition behind the coarea formula?"
date:   2021-07-09
categories: blog math differential-geometry integration
---
$\newcommand{\R}{\mathbb{R}}$

(This is based on an <a href="https://math.stackexchange.com/a/4031416/10584">answer to this question on math.stackexchange.com question</a>)

The coarea formula is a way to write an integral on a Riemannian mnanifold in terms of integrals over level sets of a function. It is widely used for proving functional inequalities, such as Sobolev inequalities, via symmetrization arguments.

For simplicity, we restrict to an integral over an open domain $O \subset\R^n$. The coarea formula states the following:

<div class="lemma">
If $f: A \rightarrow \R^k$ is Lipschitz, where $k < n$, and $\phi: A \rightarrow \R$ is $L^1$, then
\begin{align*}
\int_A \phi(x)|\partial f(x)|\,dx &= \int_{\R^k} \left(\int_{f^{-1}(y)} \phi(x)\,dH_{n-k}(x)\right)\,dy,
\end{align*}
where $H_{n-k}$ is $(n-k)$-dimensional Hausdorff measure on each $f^{-1}(y)$, $\partial f$ is the Jacobian of $f$, and
$$ |\partial f| = \sqrt{\det (\partial f \partial f^T)} $$
</div>

This is most easily understood when $n = 1$ and $f$ is a bounded smooth function  whose gradient is everywhere nonzero.

<p>
The level sets of $f$ are non-intersecting hypersurfaces. Suppos first that you want to compute the volume of the $A$ in terms of the surface areas of the hypersurfaces. Let $a = \inf f$ and $b = \sup f$. You can divide the interval $[a,b]$ into equal sized subintervals $I_1 = [y_0,y_1], \dots, I_N = [y_{N-1},y_N]$ of size $\delta = (b-a)/N$. The volume of $A$ is the sum of the volumes of $f^{-1}(I_k)$. On the other hand, each $f^{-1}(I_k)$ is a shell with varying thickness. At each point, the thickness is roughly $\Delta t/|\nabla f|$. So the volume of the shell is roughly
$$
V(f^{-1}(I_k)) \simeq \Delta t\int_{f^{-1}(y_k)}\frac{dH_{n-1}}{|\nabla f|},
$$
where $dH_{n-1}$ is the $(n-1)$-dimensional Hausdorff measure on $f^{-1}(y_k)$.
Adding up the volumes of the shells and taking the limit $N \rightarrow \infty$, we see that the volume of $A$ is
$$
V(A) = \int_{-\infty}^{\infty} \left(\int_{f^{-1}(y)} \frac{dH_{n-1}}{|\nabla f|}\right)\,dy,
$$
where $dH_{n-1}$ is the $(n-1)$-dimensional Hausdorff measure of $f^{-1}(y)$.
</p>

<p>
If, on the other hand, you integrate $\phi|\nabla f|$ on $A$ using the same approach, you get
$$
\int_{f^{-1}(I_k)} \phi|\nabla f|\,dx \simeq \Delta y\int_{f^{-1}(y_k)}\phi|\nabla f|\,\frac{dH_{n-1}}{|\nabla f|},
$$
and therefore in the limit $N \rightarrow \infty$,
$$
\int_A \phi|\nabla f|\,dx = \int_{-\infty}^{\infty} \left(\int_{f^{-1}(y)} \phi\,dH_{n-1}\right)\,dy
$$
</p>

<p>
The $k>1$ case is similar, except you chop $\mathbb{R}^k$ into small rectangular pieces $B_\alpha$ and use the fact that the cross section of the inverse image of each piece is roughly a parallelogram whose volume is $|\partial f|^{-1}$ times the volume of $B_\alpha$. The argument analogous to the one above yields
$$
\int_A \phi|\partial f|\,dx = \int_{\mathbb{R}^k} \left(\int_{f^{-1}(y)}\phi\,dH_{n-k}\right)\,dy.
$$
</p>

