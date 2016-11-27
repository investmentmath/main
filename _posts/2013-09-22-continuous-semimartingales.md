--- 
layout: post 
title: Continuous Semimartingales 
author: Guillaume Rabault
categories: [Math]
tags: [Processes] 
fullview: false 
--- 

*The previous posts introduced
stochastic integration of an integrand $H$ against an integrator $M$
which was chosen to be a continuous martingale. Continuous
semimartingales are now defined as continuous processes that can be
decomposed into a continuous martingale and a continuous finite
variation process. Because 'standard' integration theory allows to
integrate against finite variation processes, one can easily extend
stochastic integration from continuous martingale integrators to
continuous semimartingale integrators.*

* * * * *

As seen in [this
post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "QUADRATIC VARIATION AND STOCHASTIC INTEGRATION"),
stochastic integration allows to integrate a predictable process
$(H_{s})_{s \in [0,T]}$ against a continuous local martingale
$(M_{s})_{s \in [0,T]}$.This theory requires $(H_{s})_{s \in
[0,T]}$ to satisfy :
$$\int_{0}^{T}H^{2}_{s}d[M]_{s}<\infty,$$ almost surely.

Less exotic is the Lebesgue-Stieltjes theory of integration which says
that if the continuous process $(A_{s})_{s \in [0,T]}$ has almost
surely finite first order variation $V_{A}(t,\omega)$ (see [this
post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "QUADRATIC VARIATION AND STOCHASTIC INTEGRATION")),
it induces a positive measure $\mu_{\omega}$ as well as a signed
measure $\nu_{\omega}$ on [0,T] (with its Borel sigma
field)[^1]. The trajectories of $(H_{s})_{s \in [0,T]}$
being measurable with respect to the Borel sigma field on $[0,T]$,
they are $\mu_{\omega}$ integrable if and only if (introducing a
customary notation)
:$$\int_{0}^{T}|H_{s}(\omega)|d\mu_{\omega}=\int_{0}^{T}|H_{s}(\omega)|\,|dA
|_{s}(\omega)<\infty.$$ When this condition is met, one writes :
$$\int_{0}^{t}H_{s}(\omega)d\nu_{\omega}=\int_{0}^{t}H_{s}(\omega)dA_{s}(\omega).$$
In addition, the integral as a function of time is continuous and of
bounded variation.

We can thus integrate adequate predictable integrands against processes
$(X_{s})_{s \in [0,T]}$ which decompose as a sum of a continuous
finite variation process and a continuous local martingale. Such
processes are called continuous semimartingales. Suppose :
$$X_{s}=X_{0}+M_{s}+A_{s},$$ where $X_{0}$ is an ${\cal
F}_{0}$-measurable variable, $(M_{s})_{s \in [0,T]}$ is a
continuous local martingale with $M_{0}=0$ and $(A_{s})_{s \in
[0,T]}$ is continuous and has almost surely finite variation on
$[0,T]$, then we can define :
$$\int_{0}^{t}H_{s}dX_{s}=\int_{0}^{t}H_{s}dM_{s}+\int_{0}^{t}H_{s}dA_{s},$$
for predictable processes provided :
$$\int_{0}^{T}H^{2}_{s}d[M]_{s}+\int_{0}^{T}|H_{s}|\,|dA
|_{s}<\infty. \tag{*}$$ The integral
$\int_{0}^{t}H_{s}dX_{s}$, as a function of $t$ is a continuous
process. The first integral in the decomposition
$\int_{0}^{t}H_{s}dM_{s}$ is a continuous local martingale. The
second is a continuous finite variation process.

From a modelling perspective, we do not really need more than this. We
can for instance allow prices to follow continuous semimartingales, and
define portfolio value through a stochastic integral as explained in
[this
post](/finance/2013/04/06/portfolio-returns.html "PORTFOLIO RETURNS").
We now know that the condition we need to impose on portfolio weights
for all this to work is condition (*).

From a mathematical point of view, one can still raise other interesting
questions. Given a local continuous semimartingale $(X_{s})_{s \in
[0,T]}$, can we find several distinct additive decompositions of $X$
into a continuous local martingale and a continuous finite variation
process? If that was the case, we might end up with different results
for $(\int_{0}^{t}H_{s}dX_{s})_{t \in [0,T]}$ for different
decompositions. Such a a decomposition is unique however so that we need
not worry about indeterminacy.

Another question we can raise is whether we could extend integration to
a larger class of integrators. One can in effect allow for jumps both in
the martingale and in the bounded variation components and define
stochastic integration against general (not necessarily continuous)
semimartingales[^2]. But one could still raise the question of
whether we could not extend the space of integrators even further. This
question has been investigated as follows : minimal properties
stochastic integration should have are specified; one then looks for a
characterization of the integrator processes $(X_{s})_{s \in
[0,T]}$ such that the stochastic integral of suitable predictable
processes $(H_{s})_{s \in [0,T]}$ (integrands) has the specified
properties. The Bichteler Dellacherie theorem (cf. Protter[2005] p. 146)
spells out the required properties of the integration
operation[^3] and the integrand space[^4]. Under these
conditions, it shows that integrators have to be semimartingales in the
sense of being decomposable. Semimartingales are thus the most general
processes for which stochastic integration makes sense (within the
assumptions of the Bichteler Dellacherie theorem). They can equivalently
be defined through the above decomposition or through the property of
being a proper integrator in the sense of the Bichteler Dellacherie
theorem. The latter approach is the one used in Protter[2005].

Reference : P.E. Protter[2005], *Stochastic Integration and Differential
Equations*, Springer, 2005.


[^1]:  The measure $\mu_{\omega}$ 'counts' all the changes of
    $|A|(\cdot,\omega) $ whereas $\nu_{\omega}$ 'counts' the
    changes of $A(\cdot,\omega)$.

[^2]:  A semimartingale has to be a cadlag adapted process however.


[^3]:  The integral should coincide with the usual definition for simple
    integrands, should be linear in the integrand and should satisfy
    some sort of dominated convergence theorem.

[^4]:  Integrands are assumed bounded predictable. 
