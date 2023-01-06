---
layout: post
title:  "Singular Value Decomposition"
date:   2023-01-05
categories: blog math matrix matrices linear-algebra singular-values
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$

The singular value decomposition is usually defined for a matrix. Here, we will show directly that any linear map between inner product spaces has a singular value decomposition. The singular value decomposition of a matrix follows by letting the inner product spaces be $\R^n$ or $\C^n$ with the standard inner product. Only real inner product spaces will be considered here, but the complex case is almost exactly the same.

Let $M$ be an $m$-dimensional real inner product space, $N$ be an $n$-dimensional real inner product space, and $L: M \rightarrow N$ be a linear map.

<p>
We start with a geometric description of a singular value decomposition of $L$. A singular value decomposition of $L$ consists of an orthonormal basis $(v_1, \dots, v_m)$ of $M$ and an orthonormal basis $(u_1, \dots, u_n)$ of $N$, andpositive real scalars $\lambda_1, \dots, \lambda_r$, where $r$ is the rank of $L$, such that the following hold:
<ul>
<li>$(v_{r+1}, \dots, r_m)$ is a basis of $\ker(L)$</li>
<li>$(u_{r+1}, \dots, u_n)$ is a basis of $(\operatorname{image}(L))^\perp$</li>
<li>$L(v_j) = \lambda_ju_j$ for each $1 \le j \le r$</li>
</ul>
The distinct values of $\lambda_1, \dots, \lambda_r$ are called the **singular values** of the map $L$.
</p>

<p>
Equivalently, a <b>singular value decomposition</b> of $L$ is
$$
L = U\Sigma V^*,
$$
where $V; \R^m \rightarrow M$ and $U: \R^n\rightarrow N$ are isometries and $\Sigma$ is a diagonal $n$-by-$m$ matrix, which means that for each $1 \le k \le m$ and $1 \le a \le n$,
\begin{align*}
  \Sigma_j^j &\lambda_j 0\text{ if }1 \le j \le r\\
  \Sigma_j^a &= 0\text{ otherwise}.
\end{align*}
</p>

<p>
The equivalence follows by observing that if $1 \le j \le r$, then
\begin{align*}
  U\Sigma V^*(v_j)
  &=   U\Sigma e_j\\
  &= \lambda_j Ue_j\\
  &= \lambda_j u_j
\end{align*}
and if $r+1 \le j \le m$, then
\begin{align*}
  U\Sigma V^*(v_j)
  &= U\Sigma e_j\\
  &= 0.
\end{align*}
</p>

A singular value decomposition of any linear map $L: M \rightarrow N$ can be constructed as follows:

The linear map $L^*L$ is nonnegative-definite and self-adjoint and therefore has  nonnegative real eigenvalues $\lambda_1^2, \dots, \lambda_m^2$. We can assume that $\lambda_1, \dots, \lambda_r > 0$ and $\lambda_{r+1}, \dots, \lambda_m = 0$. Let $s_1, \dots, s_k$ be the distinct values of $\lambda_1, \dots, \lambda_r$.

<p>
The eigenspaces of $L^*L$ are mutually orthogonal. Denote the dimensions of the eigenspaces for $s_1^2, \dots, s_k^2$ by $d_1, \dots, d_k$, respectively. Observe that
$$
  r = d_1 + \cdots + d_k
$$
is the rank of $L$. 
We can assume that
\begin{align*}
\lambda_{d_1+\cdots+d_{j-1}+1}=\cdots=\lambda_{d_1+\cdots+d_{j-1}+d_j}&= s_j\text{ for each }1 \le j \le r\\
\lambda_{r+1} = \cdots \lambda_m &= 0.
\end{align*}
</p>

<p>
Let $(v_1, \dots, v_m)$ be an orthonormal basis of $M$ of eigenvectors of $L^*L$, where each $v_j$ is an eigenvector for the eigenvalue $\lambda_j$.  Let $V: \R^m \rightarrow M$ be the linear map such that
$$
V(e_j) = v_j,\ 1 \le j \le m,
$$
where $(e_1, \dots, e_m)$ is the standard basis of $\R^m$.
</p>

<p>
For each $1 \le j \le r$, let
\[
  \bar{u}_j = L(v_j) \in N.
\]
For each $1 \le i, j \le r$,
\begin{align*}
  \langle \bar{u}_i,\bar{u}_j\rangle &= \langle L(v_i), L(v_j)\rangle\\
                                     &= \langle v_i, L^*L(v_j)\rangle\\
                                     &= \lambda_j^2 \langle v_i,v_j\rangle\\
                                     &= \lambda_j^2\delta_{ij}.
\end{align*}
Since $\lambda_1, \dots, \lambda_r > 0$, it follows that
$$
u_1 = \frac{\bar{u}_1}{\lambda_1}, \dots, u_r = \frac{\bar{u}}{\lambda_r}
$$
is an orthonormal basis of $\operatorname{image}(L) \subset N$. This can be extended to an orthonormal basis $(u_1, \dots, u_n)$ of $N$. By their construction, the bases $(v_1, \dots, v_m)$ and $(u_1, \dots, u_n)$ satisfy the geometric definition of a singular value decomposition of $L$.

<p>
If we now define $V: \R^m \rightarrow M$ and $U: \R^n \rightarrow N$ such that
\begin{align*}
V(e_j) &= v_j,\ 1 \le j \le m\\
U(e_a) &= u_a,\ 1 \le a \le n,
$$
then they satisfy the second definition of a singular value decomposition.
</p>

A natural question is to what extent are $U$ and $V^*$ unique. If we fix an ordering of the singular values $s_1, \dots, s_k$ and the corresponding ordering of $\lambda_1, \dots, \lambda_r$, as specified above, then it is easy to see that $V$ is unique up to rotations in each eigenspace of $L^tL$ and, given $V$, $U$ is unique up to rotations of $(\operatorname{image}(L))^\perp$.


