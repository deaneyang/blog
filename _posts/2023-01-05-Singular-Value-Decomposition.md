---
layout: post
title:  "Singular Value Decomposition"
date:   2023-01-05
categories: blog math matrix matrices linear-algebra singular-values
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$

The singular value decomposition is usually defined for a matrix. Here, we will show directly that any linear map between inner product spaces has a singular value decomposition. The singular value decomposition of a matrix follows by letting the inner product spaces be $\R^n$ or $\C^n$.

Let $M$ be an $m$-dimensional Hermitian vector space, $N$ be an $n$-dimensional Hermitian vector space, and $L: M \rightarrow N$ be a linear map.

The matrix $L^*L$ is nonnegative-definite and self-adjoint and therefore has  nonnegative real eigenvalues $\lambda_1^2, \dots, \lambda_m^2$. If $s_1^2, \dots, s_k^2$ are the distinct positive eigenvalues, then their positive square roots $s_1, \dots, s_k$ are called the **singular values** of the map $L$.

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
A <b>singular value decomposition</b> of $L$ is
$$
L = U\Sigma V^*,
$$
where $V; \R^m \rightarrow M$ and $U: \R^n\rightarrow N$ are isometries and $\Sigma$ is a diagonal $n$-by-$m$ matrix, which means that for each $1 \le k \le m$ and $1 \le a \le n$,
\begin{align*}
  \Sigma_j^j &\lambda_j 0\text{ if }1 \le j \le r\\
  \Sigma_j^a &= 0\text{ otherwise}.
\end{align*}
</p>

A singular value decomposition of $L: M \rightarrow N$ can be constructed as follows:

<p>
Let $(v_1, \dots, v_m)$ be a unitary basis of $M$ of eigenvectors of $L^*L$, where each $v_j$ is an eigenvector for the eigenvalue $\lambda_j$.  Let $V: \R^m \rightarrow M$ be the linear map such that
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
is an orthonormal basis of $\operatorname{image}(L) \subset N$. This can be extended to a unitary basis $(u_1, \dots, u_n)$ of $N$. Let $U: \R^n \rightarrow N$ be the linear map such that
$$
U(e_a) = u_a,\ 1 \le a \le n.
$$
</p>

<p>
Now observe that if $1 \le j \le r$, then
\begin{align*}
  U\Sigma V^*(v_j)
  &=   U\Sigma e_j\\
  &= \lambda_j Ue_j\\
  &= \lambda_j u_j\\
  &= L(v_j).
\end{align*}
On the other hand, if $r+1 \le j \le m$, then
\begin{align*}
  U\Sigma V^*(v_j)
  &= U\Sigma e_j\\
  &= 0\\
  &= L(v_j).
\end{align*}
It follows that
$$
L = U\Sigma V^*.
$$
</p>

<p>
The singular value decomposition gives a geometric description of the linear map $L$. There exists a unitary basis $(v_1, \dots, v_m)$ of $M$ and a unitary basis $(u_1, \dots, u_n)$ such that the following hold:
<ul>
<li>$(v_{r+1}, \dots, r_m)$ is a basis of $\ker(L)$</li>
<li>$(u_{r+1}, \dots, u_n)$ is a basis of $(\operatorname{image}(L))^\perp$</li>
<li>$L$ rotates the unitary set $(v_1, \dots, v_r)$ to the unitary set $(u_1, \dots, u_r)$ and rescales each $u_j$ by a factor of $\lambda_k$</li>
</ul>
</p>

A natural question is to what extent are $U$ and $V^*$ unique.


