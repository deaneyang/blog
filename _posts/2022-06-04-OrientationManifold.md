---
layout: post
title:  "Orientation of a manifold"
date:   2022-06-04
categories: blog math differential-geometry manifolds
---
<p>
$\newcommand\R{\mathbb{R}}$
$\newcommand\extV{\Lambda^nV^*}$
$\newcommand\extVo{\Lambda^nV^*\backslash\{0\}}$
$\newcommand\extT{\Lambda^nT^*M}$
</p>

A lot of differential geometry starts with linear or tensor algebra. I like to say that a manifold is a parameterized family of vector spaces.

### Orientation of a vector space

The first observation is that a $1$-dimensional vector space with the origin removed has two connected components. There is no natural way of labeling one as positive and the other as negative. The second observation is that if $V$ is an $n$-dimensional vector space, then the vector space $\extV$ of exterior $n$-tensors is $1$-dimensional.

An orientation on $V$ is defined by choosing one of the connected components of $\extV$. Let's call that component $\extV_+$. Given any nonzero $\Theta \in \extV$, we say that $\Theta$ has positive orientation if $\Theta \in \extV_+$ and negative orientation otherwise.

Conversely, any nonzero $\Theta \in \extV$ uniquely determines an orientation on $V$ by letting $\extV_+$ be the component containing $\Theta$.

Also, note that $\Theta_1, \Theta_2 \in \extVo$ have the same orientation if and only if $\Theta_2 = c \Theta_1$ for some $c > 0$.

### Orientation of a manifold

Now let $M$ be a smooth manifold. We say that $M$ is orientable if there exists a continuous nowhere zero exterior $n$-form $\Theta$ on $M$. If such an form exists, then it uniquely determines an orientation on each $T_pM$, $p \in M$.

Any nowhere zero $n$-form on a connected oriented manifold is either positively or negatively oriented. If the manifold is not connected, then the form has a sign on each connected component but the signs do not have to be the same.

### Volume form

A volume form on $M$ is defined to be a continuous nowhere zero $n$-form. If $M$ is connected and oriented, then a volume form is either positively or negatively oriented.

### Integral of a volume form

The definition of the integral of a volume form on an $n$-dimensional manifold has an ambiguity in its sign. If the manifold is oriented, then the ambiguity is resolved as follows:

If a volume form is positively oriented, then the sign of its integral is chosen to be positive. If it has negative orientation, then the sign is chosen to be negative.

More generally, if $\Theta$ is a volume form and $f$ is a continuous nonnegative function on $M$, then the sign of
$$
\int_M f\Theta
$$
is chosen to be nonnegative.

### Integral of an $n$-form

<p>
Let $\Theta$ be a positively oriented volume form on an oriented manifold $M$. If $\Omega$ is a continuous $n$-form, there is a continuous function $f$ on $M$ such that $\Omega = f\Theta$. If we let $f_+$ and $f_-$ denote the positive and negative parts of $f$, then we define the integral of $\Omega$ to be
$$
\int_M \Omega = \int_M f_+\Theta - \int_M f_-\Theta.
$$
</p>

It is now clear that if $M$ is oriented but not connected, then for any $c \in \R$ there exists a volume form $\Theta$ such that
$$
\int_M \Theta = c.
$$