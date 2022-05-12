---
layout: post
title:  "Exponential function and Euler's formula without power series"
date:   2022-05-11
categories: blog math exponential-function euler-formula
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}$

<p><i>This was inspired by Michael Hutchings' observation that Euler's formula can be proved by solving an ordinary differential equation.</i></p>

<p>
Euler's formula states that given any real number $\theta$,
$$e^{i\theta} = \cos\theta + i\sin\theta.$$
This is usually proved by showing that the power series
$$\sum_{k=0} \frac{(i\theta)^k}{k!} = 1 + i\theta + \frac{(i\theta)^2}{2!} +\cdots$$
converges and, by splitting the series into its real and imaginary parts, satisfies
\begin{align*}
e^{i\theta} &= \sum_{k=0} \frac{(i\theta)^k}{k!}\\
            &= \sum_{k=0} (-1)^k \frac{\theta^{2k}}{(2k)!}
            + i\sum_{k=0} (-1)^k \frac{\theta^{2k+1}}{(2k+1)!}\\
            &= \cos\theta + i\sin\theta.
\end{align*}  
Here, we assume that the functions $\sin$ and $\cos$ are either defined by their power series or have been shown to be equal to the respective power series.
</p>

Here, I propose a different approach using differential equations. However, since the differential equations are constant coefficient linear ODEs, no prior knowledge of ODEs is needed. In particular, it is easy to prove the existence andu niqueness of solutions to the ODEs that arise, using only the fundamental theorem of calculus and basic real analysis. This leads to what I consider to be a more geometrically natural approach.

<p>
We start by postulating what we mean by an exponential function of a real number. A function
$$ E: \R \rightarrow \R $$
is said to be growing or decaying exponentially if its derivative is proportional to itself. In other words, it is differentiable and satisfies the equation
\begin{equation} E' = kE. \label{ode}\end{equation}
Applying the fundamental theorem of calculus, this is equivalent to the equation
$$ E(x) = e_0 + k\int_{\tau=0}^{\tau=t} E(\tau)\,d\tau. $$
It is straightforward, using a contraction mapping argument, that, given $E_0 \in \R$ , there is a unique differentiable function $E_k: \R \rightarrow \R$ satisfying \eqref{ode} and $E_k(0) = e_0$.
</p>

<p>
We want, however, to restrict to functions that satisfy $E(0)=1$. For each $k \in \R$, let $e_k$ denote the unique function that satisfies
$$ e_k' = ke_k\text{ and }e_k(0) = 1.$$
It is straightforward to show that for any $k, s, t \in \R$,
\begin{align*}
e_k(s+t) &= e_k(s)e_k(t).
\end{align*}
This in turn implies that, if
$$ e = e_1(1),$$
then for any rational number $\frac{n}{d}$,
$$ e_1\left(\frac{n}{d}\right) = e^{\frac{n}{d}}. $$
These are exactly the crucial properties we would expect from an exponential function and justifies writing, for any $t \in \R$,
$$e_1(t) = e^t.$$
</p>

<p>
We now turn to the exponential function of a pure imaginary number. At first sight, this is problematic, because
$$ e_1(i\theta) $$
cannot be defined by solving \eqref{ode}, because $t$ would have to be complex. The crucial observation is that, in the real case, it follows by the existence and uniqueness of solutions to \eqref{ode} and the chain rule that
$$ e^(kt) = e_1(kt) = e_k(t). $$
This now allows us to define the exponential of an imaginary number $i\theta$ to be $e_i(\theta)$, where $e_i$ is the unique solution to the ODE
\begin{equation} e_i' = ie_i\text{ and }e_i(0) = 1. \label{ode2} \end{equation}
If we write $e_i(t) = x(t) + iy(t)$, this is equivalent to the system
\begin{align*}
(x',y') &= (-y,x)\text{ and }(x(0),y(0)) = (1,0).
\end{align*}
The existence and uniqueness of a solution to this follows by the same contraction mapping argument used before. 
It is straightforward to show that
\begin{align*}
(x',y')\cdot (x,y) &= 0\\
x^2 + y^2 &= 1\\
(x')^2+(y')^2 &= 1.
\end{align*}
Therefore, the solution is a unit speed parameterization of the circle, where the velocity is always orthogonal to the position vector.
</p>

<p align="center">
  <img src="/blog/assets/images/circle.jpg" style="height:12%;"/>
</p>

<p>
A straightforward argument shows that there exists $T > 0$ such that
$$ (x(T),y(T)) = (x(0),y(0)) $$
and $(x,y)$ is periodic with period $T$. We can now define the constant $\pi$ by
$$ T = 2\pi. $$
</p>

<p>
The same argument as before shows that
$$ e_i(\theta_1 + \theta_2) = e_i(\theta_1)e_i(\theta_2) $$
This justifies writing, for any $\theta \in \R$,
$$
e_i(\theta) = e^{i\theta}.
$$
</p>

<p>
We can now define the functions
\begin{align*}
\cos\theta &= x(\theta)\\
\sin\theta &= y(\theta).
\end{align*}
A direct consequence is Euler's formula
$$ e^{i\theta} = \cos\theta + i\sin\theta. $$
It is now straightforward to use the symmetries of \eqref{ode2} to derive all of the basic properties of the sine and cosine functions:
\begin{align*}
(\sin\theta)^2 + (\cos\theta)^2 &= 1\\
\sin(n\pi) &= 0\\
\sin\left(\frac{\pi}{2}+2\pi n\right) &= 1\\
\sin\left(\frac{3\pi}{2}+2\pi n\right) &= -1\\
\cos(2n\pi) &= 1\\
\cos((2n+1)\pi) &= -1\\
\cos\left(\frac{\pi}{2}+n\pi\right) &= 0,
\end{align*}
where $n$ is any integer.
All of the trigonometric identities also follow easily by raising $e^{i\theta}$ to integer and rational powers.
</p>

<p>
Finally, it is now obvious how to define the exponential of a complex number $z$, namely
$$ e^{z} = e_z(1), $$
where $e_z$ is the unique solution to the ODE
$$
e_z' = ze_z\text{ and }e_z(0) = 1.
$$
Again, it is straightforward to show that
$$
e^{x+iy} = e^xe^{iy}.
$$
</p>

<p>
We have now succeeded in obtaining the following, using only basic calculus, including the fundamental theorem of calculus, and basic real analysis:
<ul>
<li>Definitions of the constants $e$ and $\pi$</li>
<li>Definitions and fundamental properties of the functions $e^z$, $\sin\theta$, $\cos\theta$, including Euler's formula</li>
</ul>
</p>

