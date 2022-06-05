---
layout: post
title:  "Exponential function and Euler's formula with power series"
date:   2022-06-05
categories: blog math exponential-function euler-formula
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$

<p><b>Acknowledgements.</b> <i>This was provoked by a <a href="https://www.quantamagazine.org/how-infinite-series-reveal-the-unity-of-mathematics-20220124/">Quanta Magazine article by Steven Strogatz on how to prove Euler's formula using power series.</a> The discussion below was inspired by Michael Hutchings' observation that Euler's formula can be proved by solving an ordinary differential equation.</i> I'd also like to thank Dan Lee, Keith Conrad, and my other Facebook friends for their comments and corrections.</p>

### Introduction

<p>
Euler's formula states that given any real number $\theta$,
$$e^{i\theta} = \cos\theta + i\sin\theta.$$
At first, even the meaning of the left side is unclear. The standard approach is to use power series to define $e^{i\theta}$ and prove Euler's formula. The argument is outlined below. It is simple and elegant. I have, however, always found it unsatisfying, since it provides little intuition into what's going on.
</p>

<p>
Here, I provide an alternative approach that I find that is easier to understand intuitively.. Moreover, it accomplishes much more. From nothing more than elementary calculus (and some elementary real analysis if you want rigorous proofs), it provides definitions of the constants $\pi$ and $e$, as well as definitions and basic properties of the exponential, sine, and cosine functions, including Euler's formula.
</p>

<p>
In a previous post, I tried to present everything without using power series at all. Since I wrote that, I have realized that power series does play a useful role here, but a purely technical one.
</p>

### Power series proof of Euler's formula

<p>
Here is a brief outline of how to prove Euler's formula using power series. The starting point are the power series
\begin{align}
  e^{x} &= \sum_{k=0}^\infty \frac{x^k}{k!} = 1 + x + \frac{x^2}{2!} +\cdots \label{taylor}\\
  \sin x &= \sum_{k=0}^\infty (-1)^k\frac{x^{2k+1}}{(2k+1)!}
  = x - \frac{x^3}{3!} + \frac{x^5}{5!} + \cdots \notag\\
  \cos x &= \sum_{k=0}^\infty (-1)^k\frac{x^{2k}}{(2k)!}
  = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} + \cdots. \notag
\end{align}
It follows by the ratio test that these series converge for every $x \in \R$.
The key observation is that these power series also converge if $x$ is complex, extending the domains of these functions from $\R$ to $\C$. 
 Euler's formula now follows by setting $x = i\theta$ in \eqref{taylor} and splitting the series into its real and imaginary parts,
\begin{align*}
e^{i\theta} &= \sum_{k=0} \frac{(i\theta)^k}{k!}\\
            &= \sum_{k=0} (-1)^k \frac{\theta^{2k}}{(2k)!}
            + i\sum_{k=0} (-1)^k \frac{\theta^{2k+1}}{(2k+1)!}\\
            &= \cos\theta + i\sin\theta.
\end{align*}  
This is simple and elegant, but the proof provides little intuition to what is going on. Euler's formula appears magically.
</p>

<p>
Below is an alternative approach that I think elucidates how the exponential function of both real and imaginary numbers arise and why exponential of an imaginary number has a geometric interpretation. The explanation below requires only basic calculus. A rigorous discussion requires the basics of when a power series converges.
</p>

### Exponential of a real number

We start by postulating what we mean by an exponential function of a real number.

<p>
First, recall that a function $f: \R \rightarrow \R$ is <b>linear</b> if, for a fixed value of $\Delta \ne 0$, the difference
$$
f(x+\Delta) - f(x)
$$
is the same, no matter what $x$ is. If $f$ is assumed to be differentiable, this is equivalent to saying $f'$ is constant.
</p>

To define an exponential function, we look at the percentage change in the output, instead of the difference. This, however, works only if the function is never zero.

<p>
We therefore say that a function $E: \R \rightarrow (0,\infty)$ is <b>exponential</b> if, for a fixed value of $\Delta \ne 0$,
$$
\frac{E(x+\Delta)}{E(x)}
$$
is the same, no matter what $x$ is. If $E$ is assumed to be differentiable, this is equivalent to saying that $E'$ is proportional to $E$. In other words, there exists a real constant $k$ such that $E$ satisfies the equation
\begin{equation} E' = kE. \label{ode}\end{equation}
An important property of this equation is called <b>translation invariance</b>. This says that if $E: \R \rightarrow \R$ is a solution to \eqref{ode} and $s \in \R$, the function $E_s$ given by
\[
E_s(t) = E(s+t)
\]
is also a solution to \eqref{ode}. This property follows by the chain rule and is exploited, both explicitly and implicitly, extensively below.
</p>

<p>
Theorem A in the appendix implies the following:
</p>

<p><b>Theorem</b>. Given any $k, e_0 \in \R$, there exists a unique smooth function $e$ satisfying
\begin{equation}
E' = kE\text{ and }E(0) = e_0.
\end{equation}
</p>

<p>
We want, however, to restrict to functions that satisfy $E(0)=1$. For each $k \in \R$, let $e_k: \R \rightarrow \R$ denote the unique function that satisfies
$$ e_k' = ke_k\text{ and }e_k(0) = 1.$$
It is straightforward, using the theorem above, to show that for any $s, t \in \R$,
\begin{align*}
e_k(s+t) &= e_k(s)e_k(t).
\end{align*}
This in turn implies that, if we define
$$ e = e_1(1),$$
then for any rational number $\frac{n}{d}$,
$$ e_1\left(\frac{n}{d}\right) = e^{\frac{n}{d}}. $$
These are the exact properties we would expect from an exponential function and justify writing, for any $t \in \R$,
$$e_1(t) = e^t.$$
</p>

### Exponential of an imaginary number

<p>
We now turn to the exponential function of a pure imaginary number. At first sight, this is problematic, because
$$ e_1(i\theta) $$
cannot be defined by solving \eqref{ode}, because $t$ would have to be complex. The crucial observation is that, in the real case, the theorem above and the chain rule imply that
$$ e^{kt} = e_1(kt) = e_k(t). $$
So the trick is to solve for a function $e_i$ satisfying
\begin{equation} e_i' = ie_i\text{ and }e_i(0) = 1. \label{ode2} \end{equation}
By Theorem A in the appendix, there is a unique solution.
This also has the property that
$$ e_i(\theta_1 + \theta_2) = e_i(\theta_1)e_i(\theta_2), $$
which justifies writing, for any $\theta \in \R$,
$$ e_i(\theta) = e^{i\theta}. $$
</p>

<p>
We now want to understand this function better. If we write $e_i(t) = x(t) + iy(t)$, then \eqref{ode2} is equivalent to the system
\begin{align*}
(x',y') &= (-y,x)\text{ and }(x(0),y(0)) = (1,0).
\end{align*}
A solution to this satisfies
$$
(x',y')\cdot (x,y) = x'x + y'y = -yx + xy = 0
$$
and therefore is a parameterized curve whose velocity vector
$$
v = (x', y')
$$
is always orthoronal to the position vector $(x,y)$.
It also follows easily that
\begin{align*}
x^2 + y^2 &= 1\\
(x')^2+(y')^2 &= 1.
\end{align*}
Putting this all together, we see that the solution is a unit speed parameterization of the circle.
</p>

<p align="center">
  <img src="/blog/assets/images/circle.jpg" style="height:12%;"/>
</p>

<p>
It is shown in the appendix that there exists $T > 0$ such that
$$
z(T) = z(0).
$$
The translation invariance of \eqref{ode2} implies that $z$ is in fact periodic and, for any $\theta \in \R$,
$$
z(\theta + T) = z(\theta).
$$
We can now define the constant $\pi$ by
$$
T = 2\pi.
$$
and the functions
\begin{align*}
\cos\theta &= x(\theta)\\
\sin\theta &= y(\theta).
\end{align*}
Direct consequences include
$$ (\sin\theta)^2 + (\cos\theta)^2 = 1, $$
Euler's formula
$$ e^{i\theta} = \cos\theta + i\sin\theta, $$
and
\begin{align*}
\frac{d}{d\theta}(\sin\theta) &= \cos\theta\\
\frac{d}{d\theta}(\cos\theta) &= -\sin\theta.
\end{align*}
It is also straightforward to use the symmetries of \eqref{ode2} to derive all of the basic properties of the sine and cosine functions, such as:
\begin{align*}
\sin(n\pi) &= 0\\
\sin\left(\frac{\pi}{2}+2\pi n\right) &= 1\\
\sin\left(\frac{3\pi}{2}+2\pi n\right) &= -1\\
\cos(2n\pi) &= 1\\
\cos((2n+1)\pi) &= -1\\
\cos\left(\frac{\pi}{2}+n\pi\right) &= 0,
\end{align*}
where $n$ is any integer.
Many trigonometric identities also follow easily by raising $e^{i\theta}$ to integer and rational powers.
</p>

### Exponential of a complex number

<p>
Finally, it is now obvious how to define the exponential of a complex number $z$, namely
$$ e^{z} = e_z(1), $$
where $e_z$ is the unique solution to the ODE
\begin{equation}\label{ode3}
e_z' = ze_z\text{ and }e_z(0) = 1.
\end{equation}
Again, it is straightforward to show that
$$
e^{z_1+z_2} = e^{z_1}e^{z_2}
$$
and, in particular,
$$
e^{x+iy} = e^xe^{iy}.
$$
</p>

### Summary
<p>
We have succeeded in using only basic calculus and basic real analysis to obtain the following in a natural and intuitive way:
<ul>
<li>Definitions of the constants $e$ and $\pi$</li>
<li>Definitions and fundamental properties of the functions $e^z$, $\sin\theta$, $\cos\theta$</li>
<li>In particular, Euler's formula</li>
</ul>
</p>

### Appendix

We recall some basic facts about series, i.e., infinite sums of real and complex numbers.

#### Geometric series

<p>
First, recall that if $a, r \in\R$, then the geometric series
$$
a + ar + ar^2 + \cdots = \sum_{k=0}^\infty ar^k
$$
converges if $|r| < 1$. Its value can be calculated explicitly,
\begin{align*}
a + ar + ar^2 + \cdots &= \lim_{n\rightarrow\infty} a + ar + \cdots + ar^n\\
&=a\lim_{n\rightarrow\infty} 1 + r + \cdots + r^n\\
&= a\lim_{n\rightarrow\infty} \frac{1 - r^{n+1}}{1-r}\\
&=  \frac{a}{1-r}.
\end{align*}
</p>

### Ratio test for a series

<p>
Observe that the ratio of any two consecutive terms in the geometric series above is always equal to $r$. Consider a series
$$
a_0 + a_1 + \cdots = \sum_{k=0}^\infty a_k,
$$
where we assume all of the terms $a_k$ are positive. For each positive integer $k$, let
$$ r_k = \left|\frac{a_k}{a_{k-1}}\right|. $$
It can be shown that if
$$
\limsup_k r_k < 1,
$$
then the series converges.
</p>

### Ratio test for a power series

<p>
A power series is like a polynomial but with infinitely many terms. Given coefficients $c_0, c_1, \dots \in \R$, consider the power series
$$
c_0 + c_1t + c_2t^2 + \cdots = \sum_{k=0}^\infty c_kt^k.
$$
Assume all of the coefficients $c_k$ are nonzero. This sum converges trivially if $t = 0$. By the ratio test for series, the power series converges for $t \ne 0$ if
$$
\limsup_k \left|\frac{c_k}{c_{k-1}}t\right| < 1.
$$
Therefore, if $R > 0$ satisfies
$$
\left|\frac{c_k}{c_{k-1}}\right| < \frac{1}{R},
$$
then the power series converges for all $t$ such that
$$
|t| < R.
$$
$R$ is called the radius of convergence for the power series.
</p>

<p>
If the ratio test for the power series holds for all $R > 0$, then the power series defines a smooth function $f: \R \rightarrow \R$, where the coefficients are given by
$$
 c_k = \frac{f^{(k)}(0)}{k!}.
$$
Moreover, the derivative of $f$ is also a smooth function on $\R$ given by the power series obtained by differentiating each term of the power series of $f$,
$$
f'(t) = \sum_{k=1}^\infty kc_kt^{k-1} = \sum_{k=0}^\infty (k+1)c_{k+1}t^k.
$$
</p>

#### Series of complex numbers and power series with complex coefficients

All of the results above still hold when the terms of a series and the coefficients of a power series are complex numbers.

#### Existence and uniqueness of solution to \eqref{ode3}

<p><b>Theorem A.</b>
Given $e_0, z \in \C$, there exists a unique differentiable function $e: \R \rightarrow \C$ satisfying
\begin{equation}\label{ivp}
  e' = ze\text{ and }e(0) = e_0.
\end{equation}
</p>

<p><b>Proof.</b>
We solve for $e$ as a power series and show that the power series has infinite radius of convergence. Suppose
$$
e(t) = \sum_{k=0} c_kt^k.
$$
Equation \eqref{ivp} implies that $c_0 = e_0$ and
$$
</p>

