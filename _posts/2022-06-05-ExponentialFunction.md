---
layout: post
title:  "Exponential functions and Euler's formula"
date:   2022-06-05
categories: blog math exponential-function euler-formula
---
$\newcommand\R{\mathbb{R}}\newcommand\C{\mathbb{C}}\newcommand\Z{\mathbb{Z}}$


<p>
Most of this post is identical to an older post. Both posts were driven by a desire to explain and prove Eulder's formula,
\begin{equation}\label{euler}
e^{i\theta} = \cos\theta + i\sin \theta,
\end{equation}
in a more conceptual way than the proof using power series. In the original post, I tried to avoid power series completely. This post has the same conceptual explanation of Euler's formula but uses power series as the key technical tool in the rigorous proofs.
</p>

<p><b>Acknowledgements.</b> <i>This was provoked by a <a href="https://www.quantamagazine.org/how-infinite-series-reveal-the-unity-of-mathematics-20220124/">Quanta Magazine article by Steven Strogatz on how to prove Euler's formula using power series.</a> The discussion below was inspired by Michael Hutchings' observation that Euler's formula can be proved by solving an ordinary differential equation.</i> I'd also like to thank Dan Lee, Keith Conrad, and my other Facebook friends for their comments and corrections.</p>

### Introduction

<p>
At first, even the meaning of the left side of Euler's formula \eqref{euler} is unclear. The standard approach is to use power series to define $e^{i\theta}$ and prove Euler's formula. The argument is outlined below. It is simple and elegant. I have, however, always found it unsatisfying, since the power series alone provides little intuition into what's going on.
</p>

<p>
Here, I provide an alternative approach that I find that is easier to understand intuitively. Moreover, it accomplishes much more. Using only calculus, it provides definitions of the constants $\pi$ and $e$, as well as definitions and basic properties of the exponential, sine, and cosine functions, including Euler's formula.
</p>

<p>
The exposition here does not require the use of power series. Power series are needed only for rigorous proofs of what is stated.
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

### Exponential function of a real number

We start by postulating what we mean by an exponential function.

#### Linear function

<p>
First, recall that a function $f: \R \rightarrow \R$ is <b>linear</b> if, for any $\Delta \ne 0$, the change in $f$
$$
f(x+\Delta) - f(x)
$$
is independent of $x$ and proportional to $\Delta$. In other words, there exists a constant $c \in \R$ such that for any $x, \Delta \in \R$,
$$
f(x+\Delta) - f(x) = c\Delta.
$$
If $f$ is assumed to be differentiable, then, by taking the limit $\Delta \rightarrow 0$, then
$$
f'(x) = \lim_{\Delta\rightarrow 0} \frac{f(x+\Delta)-f(x)}{\Delta} = c.
$$
</p>

#### Exponential function

<p>
An exponential function has a similar definition except that, for a given $\Delta > 0$, the percentage change of $f$ (instead of the change in $f$) is proportional to $\Delta$. It is necessary, however, to assume that $f$ is never zero.
We therefore say that a function $E: \R \rightarrow (0,\infty)$ is <b>exponential</b> if, for any $\Delta \ne 0$, there exists $c(\Delta)\in \R$ such that
$$
\frac{E(x+\Delta)}{E(x)} = c(\Delta),
$$
for any $x \in \R$. Observe that $c(0) = 1$.
From this, it follows that, if $E$ is differentiable, then
\begin{align*}
\frac{E'(x)}{E(x)} &= \lim_{\Delta\rightarrow 0}\frac{E(x+\Delta)-E(x)}{E(x)\Delta}\\
      &= E(x)\lim_{\Delta\rightarrow 0}\frac{c(\Delta) - c(0)}{\Delta}.
\end{align*}
This implies that $c(\Delta)$, as a function of $\Delta$, is differentiable at $\Delta = 0$, and
$$
E'(x) = \kappa E(x),
$$
where $\kappa = c'(0)$.
</p>

Conversely, the following is proved in the Appendix:

<div class="theorem">
Given any $\kappa, e_0 \in \R$, there exists a unique smooth function $E: \R \rightarrow \R$ satisfying
\begin{equation}\label{ode}
E' = \kappa E\text{ and }E(0) = e_0.
\end{equation}
</div>

<p>
One important property of this equation is called <b>translation invariance</b>. This says that if $E: \R \rightarrow \R$ is an exponential function, then given any $s \in \R$, the function $E_s: \R \rightarrow (0,\infty)$ given by
\[
E_s(t) = E(s+t)
\]
is also an exponential function, where
$$
E_s' = \kappa E_s\text{ and }E_s(0) = E(s).
$$
This property follows by the chain rule and is exploited, both explicitly and implicitly, extensively below.
</p>

<p>
Given any exponential function $E$ such that $E' = \kappa E$, observe that, for any $x \in \R$,
$$
E(x) = E(0)e_\kappa(x),
$$
where $e_\kappa$ is the exponential function such that $e_\kappa(0) = 1$ and $e_\kappa' = \kappa e_\kappa$.
It therefore makes sense to focus on the functions $e_\kappa$. Moreover, it is easy to show, using the chain rule, that, for any $t \in \R$,
\begin{align*}\label{multiplicative-shift}
e_\kappa(t) = e_1(\kappa t).
\end{align*}
It therefore makes sense to focus on the exponential function $e_1$.
</p>

<p>
Using the properties we have found so far of the exponential function $e_\kappa$, it follows that, for any $s, t \in \R$,
\begin{align*}
e_\kappa(s+t) &= e_1(s)e_\kappa(t).
\end{align*}
This in turn implies that, if we define the (rather important) constant
$$ e = e_1(1),$$
then for any rational number $\frac{n}{d}$,
$$ e_1\left(\frac{n}{d}\right) = e^{\frac{n}{d}}. $$
These are the exact properties we would expect from an exponential function and justify writing, for any $t \in \R$,
$$e_1(t) = e^t.$$
Using this notation with \eqref{multiplicative-shift}, we can also write
$$
e_\kappa(t) = e_1(\kappa t) = e^{\kappa t}.
$$
</p>

<p>
In summary, we have shown the following, using the notation defined above:
</p>
<p>
<i>There exists a number $e > 0$ such that any exponential function $E: \R \rightarrow \R$ can be written as
$$
E(t) = E_0e^{\kappa t},
$$
where $E_0 = E(0)$ and $\kappa = E'(0)/E(0)$.
</i>
</p>

### Exponential of an imaginary number

#### Definition

<p>
Now suppose you want to extend the definition of $e^t$ to $t \in \C$. Let us focus first on the case $t = i$. One possible approach is defining this is setting
$$
e^i = e_1(i).
$$
But this is problematic, because it would mean trying to solve \eqref{ode} with $t$ being complex instead of real. A better approach is to use \eqref{ode} as a template and define
$$
e^i = e_i(1),
$$
where $e_i$ satisfies the equation
\begin{equation} e_i' = ie_i\text{ and }e_i(0) = 1. \label{ode2} \end{equation}
By Theorem A in the appendix that there is a unique solution $e_i: \R \rightarrow \C$ to \eqref{ode2}. Moreover, for any $t_1, t_2 \in \R$,
$$ e_i(t_1 + t_2) = e_i(t_1)e_i(t_2), $$
which justifies writing, for any $t \in \R$,
$$ e_i(t) = e^{it}. $$
</p>

#### Geometric properties of the exponential of an imaginary number

<p>
We now want to understand the function $e^{it}$ better. An unexpected twist is that geometry and trigonometry naturally appear in the description of this function.
</p>

<p>
If we write $e_i(t) = x(t) + iy(t)$, then \eqref{ode2} is equivalent to the system
\begin{align}\label{ode3}
(x',y') &= (-y,x)\text{ and }(x(0),y(0)) = (1,0).
\end{align}
A solution to this satisfies
$$
(x',y')\cdot (x,y) = x'x + y'y = -yx + xy = 0.
$$
Therefore, $(x(t),y(t))$, $t \in \R$, is a parameterized curve whose velocity vector
$$
v = (x', y')
$$
is always orthogonal to the position vector $(x,y)$.
It follows easily from \eqref{ode3} that
\begin{align*}
x^2 + y^2 &= 1\\
(x')^2+(y')^2 &= 1.
\end{align*}
The first equation says the curve always lies on the unit circle centered at the origin. The second says that the speed, which is the norm of the velocity vector, is always equal to $1$.
Putting this all together, we see that the solution is a unit speed parameterization of the circle.
</p>

<p align="center">
  <img src="/blog/assets/images/circle.jpg" style="height:12%;"/>
</p>

<p>
Since the parameterization has unit speed, it is intuitively clear that the solution to \eqref{ode3} goes around the entire circle. In particular, there exists $T > 0$ such that
$$
e_i(T) = e_i(0).
$$
The translation invariance of \eqref{ode2} implies that $z$ is in fact periodic, which means that, for any $t \in \R$,
$$
e_i(t + T) = e_i(t).
$$
</p>

#### Definition of $\pi$

<p>
We can now define the constant $\pi$ by setting
$$
T = 2\pi.
$$
Since, for each $t \in [0,2\pi]$, $e_i(t) = (x(t),y(t))$ is point reached by traveling at unit speed along the circle staring from $(1,0)$, it follows that $t$ is the length of the arc from $(1,0)$ to $(x(t),y(t))$. In other words, $t$ is the angle in radians. In particular, the length of the full circle, i.e., its circumference, is $2\pi$.
</p>

#### Definitions and properties of trig functions

<p>
We can now define the basic trig functions to be, for any $\theta \in \R$,
\begin{align*}
\cos\theta &= x(\theta)\\
\sin\theta &= y(\theta).
\end{align*}
Direct consequences of everything above include
$$ (\sin\theta)^2 + (\cos\theta)^2 = 1, $$
Euler's formula
$$ e^{i\theta} = \cos\theta + i\sin\theta, $$
and the standard differentiation formulas,
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
\begin{equation}\label{ode4}
e_z' = ze_z\text{ and }e_z(0) = 1.
\end{equation}
Again, it is straightforward to show that
$$
e^{z_1+z_2} = e^{z_1}e^{z_2}
$$
and, in particular,
$$
e^{x+iy} = e^xe^{iy} = e^x(\cos y + i\sin y)..
$$
</p>

### Summary
<p>
We have succeeded in using only calculus to obtain the following in a natural and intuitive way:
<ul>
<li>Definitions of the constants $e$ and $\pi$</li>
<li>Definitions and fundamental properties of the functions $e^z$, $\sin\theta$, $\cos\theta$</li>
<li>Euler's formula</li>
</ul>
</p>

### Appendix

#### Derivative of an exponential function is proportional to the function

<div class="lemma">
Let $f: \R \rightarrow \R$ be a differentiable function such that for any $\delta \in \R$, there exists $r_\delta > 0$ such that
\begin{align*}
  \frac{f(x+\delta)}{f(x)} = r_\delta\text{, for any }x \in \R.
\end{align*}
Then there exists $\kappa \in \R$ such that
$$
f' = \kappa f.
$$
</div>

<div class="proof">
  First, observe that, given any $\delta$,
  \begin{align*}
    r_\delta &= \frac{f(x+\delta)}{f(x)}\\
        &= \frac{f(x+1)}{f(x+\frac{\delta}{2})}\frac{f(x+\frac{\delta}{2})}{f(x)}\\
             &= r_{\frac{\delta}{2}}^2.
  \end{align*}
  Iterating this and denoting $r = r_1$, we find that for any $N \in \Z^+$,
  \begin{align*}
    r &= (r_{2^{-N}})^{2^N}.
  \end{align*}
  It follows that
  \begin{align*}
    \frac{f(x+2^{-N}) - f(x)}{2^{-N}}
    &= f(x)2^N\left(\frac{f(x+2^{-N})}{f(x)}-1\right)\\
    &= f(x)2^N(r^{2^{-N}}-1)\\
    &= f(x)\kappa_N,
  \end{align*}
  where
  \begin{align*}
    \kappa_N &= 2^N(r^{2^{-N}}-1).
  \end{align*}
  Since
  \begin{align*}
    \kappa_N &= 2^N(r^{2^{-N}}-1)\\
             &= 2^{N}(r^{2^{-(N+1)}}-1)(r^{2^{-(N+1)}}+1)\\
             &= \kappa_{N+1}\left(\frac{r^{2^{-(N+1)}}+1}{2}\right),
  \end{align*}
  it follows that $\kappa_N$ defines a bounded monotone sequence and converges to a limit $\kappa \in \R$. Since $f$ is differentiable,
  \begin{align*}
    f'(x) &= \lim_{N\rightarrow\infty}\frac{f(x+2^{-N})-f(x)}{2^{-N}}\\
          &= f(x)\lim_{N\rightarrow\infty} \kappa_N\\
          &= \kappa f(x).
  \end{align*}
  </div>
<br>

#### Existence and uniqueness of solutions to \eqref{ode}, \eqref{ode2}, \eqref{ode4}

<div class="theorem">
Given $e_0, z \in \C$, there exists a unique differentiable function $e: \R \rightarrow \C$ satisfying
\begin{equation}\label{ivp}
  e' = ze\text{ and }e(0) = e_0.
\end{equation}
</div>

<div class="proof">
<p> Consider the power series
$$
e(t) = \sum_{k=0} c_kt^k.
$$
If $e$ satisfies equation \eqref{ivp} implies that $c_0 = e_0$ and
$$
\sum_{k=0}^\infty (k+1)c_{k+1}t^k = \sum_{k=0}^\infty zkc_kt^k,
$$
which in turns implies that for any $k \ge 0$,
$$
c_{k+1} = \frac{z}{k+1}c_k.
$$
By induction, we see that
$$
c_k = \frac{z^k}{k!},
$$
Therefore, the power series for $e$ is
$$
e_0\sum_{k=0}^\infty \frac{(zt)^k}{k!}.
$$
It is easily checked that by the ratio test for series, the series converges for all $t \in \R$. This also implies that the power series for $e'$ also converges for all $t \in \R$ and the function $e$ satisfies \eqref{ivp}.
</p>

<p>
Now suppose $e_1$ and $e_2$ are both solutions to \eqref{ivp}. Then the function $f = e_2-e_1$ satisfies
\begin{equation}\label{ivpz}
  f' = zf\text{ and }f(0) = 0.
\end{equation}
We want to show that this implies $f=0$ on $\R$.
</p>

<p>
Let $T > 0$ and denote
$$
\|f\| = \max \{|f(t)|\ :\ t \in [t_0-T,t_0+T]\}.
$$
By the fundamental theorem of calculus,
\begin{align*}
f(t) &= f(t)-f(t_0)\\
     &=  \int_{s=t_0}^{s=t}f'(s)\,ds\\
     &=  z\int_{s=t_0}^{s=t}f(s)\,ds.
\end{align*}
and therefore
\begin{align*}
\|f\| &= |z|\max_{t\in[t_0-T,t_0+T]}\left|\int_{s=t_0}^{s=t}f(s)\,ds\right|\\
&\le |z|T\|f\|
\end{align*}
It follows that if
$$
|z| < \frac{1}{T},
$$
then $\|f\|=0$. By applying this repeatedly with
$$
t_0 = k\frac{T}{2},\ k \in \Z,
$$
it follows that $f(t) = 0$ for all $t \in \R$.
</p>
</div>

#### A solution to \eqref{ode2} goes around the whole circle

<p>
We sketch a proof. The key point is that suppose we have solutions $(x_1,y_1): (a_1, b_1) \rightarrow \R^2$ and $(x_2,y_2): (a_2,b_2) \rightarrow \R^2$
to
$$ (x',y') = (-y,x) $$
such that for some $t_1 \in(a_1,b_1)$ and $t_2 \in (a_2,b_2)$,
$$
(x_1,y_1)(t_1) = (x_2,y_2)(t_2).
$$
By the uniqueness of a solution to \eqref{ode2}, it follows that
$$
(x_1,y_1)(t) = (x_2,y_2)(t_2-t_1+t)
$$
for all $t \in (a_1,b_1)\cap (a_2-t_2+t_1,b_2-t_2+t_1)$. Therefore, the two solutions join together to form a single solution on the interval
$$
(\min(a_1,a_2-t_2+t_1),\max(b_1,b_2-t_2+t_1)).
$$
</p>

<p>
The idea now is to show that if the solution does not cover the whole circle, it can always be extended further. This implies that the solution does cover the whole circle.
</p>

