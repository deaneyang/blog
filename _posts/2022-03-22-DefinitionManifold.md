---
layout: post
title:  "How I define a manifold"
date:   2022-03-22
categories: blog math differential-geometry manifolds
---
$\newcommand{\R}{\mathbb{R}}$
I've always disliked the standard ways to state the definition of a manifold in differential geometry. Here's how I like to do it.

Start with a set $M$, just a set. Define a coordinate map to be a bijection $\phi: O \rightarrow \mathbb{R}^n$, where $O$ is a subset of $M$ and $\phi(O) \subset \mathbb{R}^n$ is open. Define an atlas to be a collection of coordinate maps, where the domains of the maps cover $M$. No assumptions about topology or smoothness yet.

A topological atlas is one where for any two coordinate maps $\phi_1: O_1 \rightarrow \mathbb{R}^n$ and $\phi_2: O_2\rightarrow \mathbb{R}^n$ such that $O_1\cap O_2 \ne \emptyset$, the change of coordinate map

$$\phi_2\circ\phi_1^{-1}: \phi_1(O_1\cap O_2) \rightarrow \phi_2(O_1\cap O_2) $$

is a homeomorphism. A topological manifold is the set $M$ with a topological atlas. You can now define a function $f: M \rightarrow \R$ to be continuous if for any coordinate map $\phi: O \rightarrow \R^n$, the function $f\circ\phi^{-1}: \phi(O) \rightarrow \R$ is continuous. The assumption on the change of coordinate maps is the necessary and sufficient condition that this definition of continuity is logically consistent.

Observe that there is now a unique topology on $M$ such that all coordinate maps are continuous. It is the topology where the domains of all coordinate maps comprise a base of open sets. Again, the assumption on the change of coordinate maps is exactly what's needed for this topology to exist.

Usually, there is one more assumption made, which I like to state as follows:

First, observe that if $\phi: O \rightarrow \R^n$ is a coordinate chart, then for any open $O' \subset O$, you can also include in the atlas the map $\phi$ restricted to $O'$.

The additional assumption is the following: <i>You can separate points using coordinate charts.</i> More precisely, given any two different points $p_1, p_2 \in M$, there exist coordinate charts $\phi_1: O_1 \rightarrow \R^n$ and $\phi_2: O_2 \rightarrow \R^n$ such that $p_1 \in O_1$, $p_2 \in O_2$, and $O_1\cap O_2 = \emptyset$.

This assumption is usually stated by saying that the topology on $M$ is Hausdorff, but I think my way is easier to understand.

The definition of a smooth manifold is exactly the same, except that the change of coordinate maps are also assumed to be smooth, i.e., diffeomorphisms.