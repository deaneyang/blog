---
layout: post
title:  "The definition of a manifold"
date:   2022-03-22
categories: blog math differential-geometry manifolds
---
$\newcommand{\R}{\mathbb{R}}$
I've always disliked the standard ways to state the definition of a manifold in differential geometry. First, the definition always starts with a topological space $M$. I don't understand why you need to start with that assumption. The topology of $M$ is in fact a *consequence* of the definition. Second, the definition always uses two technical terms, paracompact and Hausdorff. I prefer to describe the properties concretely in terms of coordinate maps.

Here's my way to define a manifold:

Start with a set $M$, just a set. Define a coordinate map to be a bijection $\phi: O \rightarrow \mathbb{R}^n$, where $O$ is a subset of $M$ and $\phi(O) \subset \mathbb{R}^n$ is open. Define an atlas to be a countable collection of coordinate maps, where the domains of the maps cover $M$. No assumptions about topology or smoothness yet. 

A topological atlas is one where for any two coordinate maps $\phi_1: O_1 \rightarrow \mathbb{R}^n$ and $\phi_2: O_2\rightarrow \mathbb{R}^n$ such that $O_1\cap O_2 \ne \emptyset$, the change of coordinate map

$$\phi_2\circ\phi_1^{-1}: \phi_1(O_1\cap O_2) \rightarrow \phi_2(O_1\cap O_2) $$

is a homeomorphism. A topological manifold is a set $M$ with a topological atlas. You can now define a function $f: M \rightarrow \R$ to be continuous if for any coordinate map $\phi: O \rightarrow \R^n$, the function $f\circ\phi^{-1}: \phi(O) \rightarrow \R$ is continuous. It is also now straightforward to define what a continuous map from one topological manifold to another is. The assumption on the change of coordinate maps is the necessary and sufficient condition that these definitions are logically consistent.

Observe that there is now a unique topology on $M$ such that all coordinate maps are continuous. It is the topology where given any coordinate map $\phi: O \rightarrow \R^n$ and open subset $U \subset \phi(O)$, $\phi^{-1}(U)$ is open. Again, the assumption on the change of coordinate maps implies that this definition is logically consistent.

Usually (but not always), there is one more assumption made, which I like to state as follows:

<i>You can separate points using coordinate charts.</i>

More precisely, given two different points $p_1, p_2 \in M$, there exist coordinate maps $\phi_1: O_1\rightarrow \R^n$, $\phi_2: O_2\rightarrow \R^n$ and open subsets $O_1' \subset O_1$, $O'2\subset O_2$ such that
- $p_1 \in O'_1$ and $p_2 \in O'_2$
- $O'_1\cap O'_2 = \emptyset$

That the atlas has countably many coordinate maps is equivalent to $M$ being paracompact. That points can be separated by coordinate charts is equivalent to $M$ being Hausdorff.

The definition of a smooth manifold is exactly the same, except that the change of coordinate maps are also assumed to be smooth, i.e., diffeomorphisms.