--- 
layout: post 
title: Stochastic Integration and Localization
author: Guillaume Rabault
categories: [Math] 
tags: [Integration] 
fullview: false 
--- 

*As
explained in [this
post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "quadratic variation and stochastic integration"),
stochastic integration has initially been developed under the condition $E\left[\int_{0}^{T}H^{2}_{s}d[M]_{s}\right]<\infty$.
This condition has then been replaced by the more general condition $P\left(\int_{0}^{T}H^{2}_{s}d[M]_{s}<\infty \right)=1$.
This turns out to be the most general integrability condition under
which stochastic integration can be defined. This post introduces the
idea behind this generalization. The process whereby stochastic
integration is thus generalized is called localization. In words, the
above condition means that the set of trajectories for which integrated
variance remains bounded should have probability one.*

* * * * *

Localizing stochastic integrals
===============================

[This
post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "quadratic variation and stochastic integration")
on the stochastic integral emphasized the role of the quadratic
variation in its definition. The quadratic variation of the integrator
(a continuous martingale in effect) allowed to define a norm on the
integrand space (some subspace of predictable processes, effectively
incorporating a boundedness condition) so that a given suitable
integrand could be approximated by simple predictable processes, the
approximation process being controlled by the norm. For each simple
predictable process, we have an explicit definition of the stochastic
integral. The construction then consisted in making sure that as we get
closer to the integrand using our simple processes the value of the
integral stabilizes around a well defined random variable, which is our
stochastic integral.

This construction is done for a given time interval $[0,T]$ and
delivers a random variable $\int_{0}^{T}H_{s}dM_{s}$. The
construction loses sight of the process obtained when time is allowed to
vary. We would like to consider the trajectories
$(\int_{0}^{t}H_{s}dM_{s})_{t \in [0,T]}$ however. Fortunately,
the process dimension can be recovered, and in our case (the integrator
is a continuous martingale), $(\int_{0}^{t}H_{s}dM_{s})_{t \in
[0,T]}$ can be given continuous trajectories. Intuitively, the integral
weighs the increments of the continuous martingale. The weighting scheme
cannot break the continuity of the original martingale. This is easily
verified for simple integrands. One needs to check that the continuity
of the trajectories is preserved in the convergence process. It does.
The proof of this result uses the fact that uniform limits of continuous
functions are continuous.

The stochastic integral is initially defined under the boundedness
condition:$$E\left[\int_{0}^{T}H^{2}_{s}d[M]_{s}\right]<\infty,\tag{*}$$
using $L^{2}$ Hilbert space techniques. The stochastic integral can
still be defined if:
$$E\left[\int_{0}^{T}H^{2}_{s}d[M]_{s}\right]=\infty,$$
provided: $$P\left(\int_{0}^{T}H^{2}_{s}d[M]_{s}<\infty
\right)=1.$$ One can then indeed identify an increasing sequence of
sets of time and events which union is whole space $[0,T] \times
\Omega$, and such that when restricted to each one of the sets in the
sequence, the previous expectation (integral) is finite. This is done
using stopping times $(T_{k})_{k \in N}$, with each set of time and
events being defined as $\{(t,\omega) | t \leq T_{k}(\omega)\}$.
On each of these sets, the restricted integral is finite:
$$E\left[\int_{0}^{T_{k}}H^{2}_{s}d[M]_{s}\right]<\infty.$$
Finally, the sequence of stopping times converges almost surely to
$T$. In other words, the sequence of stopping times covers the time
axis.

The set of stopping times is called a localizing sequence. It is used to
define localized (stopped) versions of $(H_{s})_{s \in [0,T]}$ and
$(M_{s})_{s \in [0,T]}$ through:

-   $H^{k}_{s}=H_{s}$ on $\{(t,\omega) | t \leq
    T_{k}(\omega)\}$, $H^{k}_{s}=0$ on $\{(t,\omega) | t
    \>T_{k}(\omega)\}$, 
-   $M^{k}_{s}=M_{s}$ on $\{(t,\omega) | t \leq
    T_{k}(\omega)\}$, $M^{k}_{s}=M_{T_{k}}$ on
    $\{(t,\omega) | t \> T_{k}(\omega)\}$.

The stochastic integral can then be defined for each stopped process
(the right boundedness conditions having been ensured by construction)
leading to a stochastic integral process which we can formally write
down as $(\int_{0}^{t}H^{k}_{s}dM^{k}_{s})_{t \in [0,T]}$. It
can be shown for any two indices $p$ and $q \geq p$:
$$\int_{0}^{t}H^{q}_{s}dM^{q}_{s}=\int_{0}^{t}H^{p}_{s}dM^{p}_{s}$$
on $\{(t,\omega) | t \leq T_{p}(\omega)\}$. One can thus glue
all stopped integrals together to lead to an unambiguous stochastic
integral[^2]:$$\int_{0}^{t}H_{s}dM_{s},\,t \leq T.$$

Stochastic integrals and local martingales
==========================================

Relaxing the boundedness condition, we lose the property that the
stochastic integral is a continuous martingale. It is instead a local
continuous martingale. The concept of a local martingale is related to
the previous construction. As above, the construct is designed to tame
unboundedness. Essentially, a local martingale is a process coming with
an increasing sequence of stopping times which fully covers the time
axis and such that each stopped version of the process is a true
martingale. Because in our construction above, the stopped processes
verified the boundedness condition, each 'stopped stochastic integral'
is a martingale. It is thus expected that our extended stochastic
integral delivers a local martingale and it indeed does[^1].
Finally, the integral can be fully generalized by allowing integrators
to be local continuous martingales instead of true continuous
martingales. First, local martingales have a proper continuous quadratic
variation. Second, to adapt the above construction to this case, one
needs to find a localizing sequence which both localizes the martingale
and ensures the boundedness condition (*). This is possible and is
actually easy in our case given the continuous trajectories of the local
martingale.

In our context where integrators are continuous local martingales, the
true constraint on extending stochastic integration is the divergence of
$\int_{0}^{T}H^{2}_{s}d[M]_{s}$ on a non negligible set of
trajectories. Heuristically, when this quantity explodes, the stochastic
integral oscillates wildly between $+\infty$ and $-\infty$ and its
value cannot be defined. This corresponds to the asymptotic behavior of
the Brownian motion at infinity ($\limsup_{t \rightarrow
\infty}B_{t}=+\infty$, $\liminf_{t \rightarrow
\infty}B_{t}=-\infty$). These wild oscillations have to remain the
unreachable horizon of our stochastic integrals.

The moral of the story
======================

The objective of this post was to introduce localization. A lot of
details have been swept under the rug but hopefully, the logic is clear.
Localization is the price we have to pay to be able to develop
stochastic integration without imposing ad-hoc boundedness conditions.
One can integrate local continuous martingales using predictable
processes. The outcome is a local continuous martingale. The key
condition which has to be enforced is that
$\int_{0}^{T}H^{2}_{s}d[M]_{s}$ be almost surely finite.

This post opens the door to the nirvana of (continuous) semimartingales.
Semimartingales are precisely the processes for which stochastic
integration makes sense. They decompose additively into finite variation
processes and local martingales. We are one step away from
semimartingales and we will remain there in this post. Using
semimartingales, we will be able to explicit the rules of Ito
integration.

[^1]:  A boundedness condition is needed to prove that a local martingale
    is a true martingale. Roughly speaking, the boundedness condition
    allows to apply the dominated convergence theorem of Lebesgue
    integration (or the related Vitali convergence theorem). As a
    reminder, the dominated convergence theorem identifies a sufficient
    condition for integration and limits to commute.

[^2]:  One can check that the construction is independent of the particular
    localizing sequence that has been chosen.

