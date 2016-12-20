--- 
layout: post 
title: Constrained Optimization
author: Guillaume Rabault
categories: [Ensae] 
tags: [Math] 
fullview: false 
--- 

*This post collects constrained optimzation results for reference.*

* * * * *



## Kuhn-Tucker

The presentation below is an adaptation of *Functional Analysis, Calculus of Variations and Optimal Control*, by Francis Clarke, Springer Verlag 2013 (Chapter $9$).

We start with the following data:

* $S$ is a convex set of $\mathbb{R}^{N}$
* $f : S \to \mathbb{R}$
* $f$ is concave
* $g_{i} : S \to \mathbb{R},\, i=1,2,\ldots,m$
* each $g_{i}$ is convex
* $h_{i} : S \to \mathbb{R},\, i=1,2,\ldots,n$
* each $h_{i}$ is affine

Program $P$:
$$\underset{x}{\text{max}} \; f(x)$$
$$\text{s.t.}:$$
$$x \in S,$$ 
$$h(x)=0,$$ 
$$g(x)\leq 0.$$ 

**Theorem (Kuhn-Tucker)**: *Let $x_{*}$ be a solution of $P$. Then there exists $(\eta_{*},\gamma_{*},\lambda_{*}) \in \mathbb{R}\times\mathbb{R}^{m}\times\mathbb{R}^{n}$ satisfying*:

$$(\eta_{*},\gamma_{*},\lambda_{*})\neq 0 \, \text{({\em non triviality})},$$
*as well as (positivity and complementary slackness)*:
$$\eta_{*}=0\,\text{{\em or}}\,1,\, \gamma_{*}\geq 0, \,\langle\gamma_{*},g(x_{*})\rangle=0,$$
*and (maximization condition)*, $\forall x \in S$:
$$\eta_{*} f(x)-\langle\gamma_{*},g(x)\rangle-\langle\lambda_{*},h(x)\rangle\leq \eta_{*} f(x_{*})-\langle\gamma_{*},g(x_{*})\rangle-\langle\lambda_{*},h(x_{*})\rangle=\eta_{*} f(x_{*}).$$

${\scriptstyle \blacksquare}$

The proof of this proposition entails the analysis of the convex cone:
$$C=\{(f(x)-\delta,g(x)+\Delta,h(x)): \delta \geq 0,\Delta \geq 0, x\in S\},$$
around $z_{*}=(f(x_{*}),0,0)$, which must lie on its boundary. One then uses the fact that there must exist a vector at $z_{*}$ that points towards the exterior of $C$ and such that the scalar product of this vector with any vector $z-z_{*}$ (where $z$ is in $C$) is negative.

### First order condition

In the above theorem, the usual stationarity condition (first order condition) is replaced by a maximization condition. It is clear that if $x_{*}$ is in the interior of $S$ and that $f$ and $g$ are differentiable at $x_{*}$, the maximization condition implies:
$$\eta_{*} \nabla f(x)-\langle\gamma_{*},\nabla g(x)\rangle-\langle\lambda_{*},\nabla h(x)\rangle=0.$$

### Sufficiency

When $\eta_{*}=1$ (the normal case), the maximization condition reads:
$$f(x)-\langle\gamma_{*},g(x)\rangle-\langle\lambda_{*},h(x)\rangle\leq f(x_{*}), \forall x \in S.$$
Since $\gamma_{*}\geq 0$, we have $\langle\gamma_{*},g(x)\rangle\leq 0$ whenever $x$ satisfies the inequality constraint $g(x)\leq 0$. In addition, under the set of constraints, $h(x)=0$. We can thus conclude that:
$$f(x) \leq f(x_{*}), \forall x \in S,\, g(x)\leq 0,\, h(x)=0,$$
and we can conclude that $x_{*}$ is optimum, i.e. the conditions in the theorem are also sufficient.

### Slater condition

**Theorem (Slater conditions)**: *Assume that there exists a strictly admissible point $x_{0}$ for $P$, i.e.*:
$$x_{0}\in \text{int}S,\, g(x_{0})<0,\, h(x_{0})=0,$$
*and the affine functions of the equality constraints are independent. Then the multiplier of the Kuhn-Tucker Theorem satisfies $\eta_{*}=1$.*

${\scriptstyle \blacksquare}$


### Saddle point property

Assume $x_{*}$ and $(1,\gamma_{*},\lambda_{*})$ are the multiplier of problem $P$. The maximization condition in the Kuhn-Tucker theorem reads:
$$f(x)-\langle\gamma_{*},g(x)\rangle-\langle\lambda_{*},h(x)\rangle\leq f(x_{*})-\langle\gamma_{*},g(x_{*})\rangle-\langle\lambda_{*},h(x_{*})\rangle=f(x_{*}), \forall x \in S.$$
Now, since $\gamma_{*}\geq 0$ and $g(x_{*})\leq 0$, we have $\langle\gamma,g(x_{*})\rangle\geq 0$ for all $\gamma\geq 0$ with equality for $\gamma_{*}$ (complementary slackness). We also have $\langle\lambda,h(x_{*})\rangle=0$. As a result we have:
$$f(x)-\langle\gamma_{*},g(x)\rangle-\langle\lambda_{*},h(x)\rangle\leq f(x_{*})\leq f(x_{*})-\langle\gamma,g(x_{*})\rangle-\langle\lambda,h(x_{*})\rangle,$$
$$\forall x \in S,\, \gamma \geq 0,\, \lambda.$$
This is the famous saddle point property for the Lagrangian of the constrained optimization problem.

### Envelope theorem

One can consider the following maximization problem, noted $P(\alpha,\beta)$:
$$\underset{x}{\text{max}} \; f(x)$$
$$\text{s.t.}:$$
$$x \in S,$$ 
$$h(x)=\beta,$$ 
$$g(x)\leq \alpha.$$ 

**Theorem**: *Assuming there is a solution $x_{*}$ to problem $P$ where the Slater condition is satisfied. Define $V(\alpha,\beta)$ as the value function of $P(\alpha,\beta)$. Then, $V(\cdot,\cdot)$ is concave with values in $[-\infty,+\infty)$. The vector $(1,\gamma,\lambda)$ is a multiplier associated to $x_{*}$ if and only if $(\gamma,\lambda)$ is such that*:
$$V(\alpha,\beta)\leq V(0,0)+\langle\gamma,\alpha\rangle+\langle\lambda,\beta\rangle.$$

${\scriptstyle \blacksquare}$

The vector $(\gamma,\lambda)$ is called the superdifferential of the concave value function at $(0,0)$. If $V(\cdot,\cdot)$ is differentiable, $\gamma$ is the partial derivative with respect to $\alpha$ and $\lambda$ is the partial derivative with respect to $\beta$.




### Remark

The most confusing aspect in the multiplier rule is perhaps the choice of the sign of the multiplier in the case of inequality constraints. In other words, how should we choose to formulate the Lagrangian? The logic is as follows. When the inequality constraint is of the form $g(x)\leq 0$ and the problem is a maximization one, the multiplier rule should be that at the optimum, increasing $f$ should require increasing $g$. Gradients therefore have to be colinear (up to the adjustment for the equality constraints) with a positive constant of proportionality. In the expression below:
$$\nabla f(x)=\langle\gamma_{*},\nabla g(x)\rangle+\langle\lambda_{*},\nabla h(x)\rangle,$$
$\gamma$ should be positive. This pins down the form of the Lagrangian. Should the constraint be $g(x)\geq 0$, the sign of $\gamma$ would have to be reversed.

