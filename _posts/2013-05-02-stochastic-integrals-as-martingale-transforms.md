--- 
layout: post 
title: Stochastic Integrals as Martingale Transforms
author: Guillaume Rabault
categories: [Math] 
tags: [Integration] 
fullview: false 
--- 

*Building on
the [portfolio return
post](/finance/2013/04/06/portfolio-returns.html "PORTFOLIO RETURNS"),
this article describes the stochastic inregral
$\int_{0}^{\cdot}H_{u}dM_{u}$ of an integrand $H$ against
a martingale $M$ as a martingale transform. The integral re-weights
the increments of $M$ using a system of 'predetermined' weights in
such a way that the resulting process remains a martingale. The
preservation of the martingale property is a key requirement of the
standard stochastic integration theory. The sensitivity of the resulting
martingale $\int_{0}^{\cdot}H_{u}dM_{u}$ with respect to the
infinitesimal increments of $M$ is an instanciation of the concept of
Malliavin derivative. The post ends by considering the martingale
representation property which plays a key role in financial theory.*

* * * * *

Martingale Transforms
=====================

The [portfolio return
post](/finance/2013/04/06/portfolio-returns.html "PORTFOLIO RETURNS")
took the perspective that a portfolio is a weighting scheme applied to
the returns of the available instruments. The weights are chosen as a
function of the information set of the portfolio manager. This leads to
a staggered information structure: weights depend on past information
and cannot anticipate future surprises in returns.

Martingale transforms can be understood from this perspective. Assume
that we are given a filtered probability space $(\Omega, {\cal
F},({\cal F}_{t})_{t \in \mathbb{T}},P)$ together with a
martingale $(M_{t})_{t \in \mathbb{T}}$. Let's assume a discrete
time setting $\mathbb{T}=\mathbb{N}$. The martingale differences
$\Delta M_{t}=M_{t}-M_{t-1}$ are our surprises. Let's weigh them
using a ${\cal F}_{t-1}$ random variable $H_{t-1}$. We get the
reweighted martingale difference: $$H_{t-1}\Delta
M_{t}=H_{t-1}(M_{t}-M_{t-1}),$$ which is still a martingale
difference in the sense that: $$E_{t-1}[H_{t-1}\Delta
M_{t}]=H_{t-1}E_{t-1}[\Delta M_{t}]=0.$$ Cumulating these
differences leads to a new martingale $(\tilde{M}_{t})_{t \in
\mathbb{T}}$: $$\tilde{M}_{t}=\sum_{k=1}^{t}H_{k-1}\Delta
M_{k}$$ which is centered $E_{0}[\tilde{M}_{t}]=0$. This is the
discrete time stochastic integral.

In continuous time ($\mathbb{T}=\mathbb{R}_{+}$), the staggered
information structure is more subtle. The key to the construction of the
stochastic integral is that we want it to preserve the martingale
property. The construction starts with the definition of simple weights,
i.e. piecewise constant weighting schemes, where discontinuities take
place at stopping times ($T_{i})_{i \in \mathbb{N}},\, T_{0}=0$:
$$H_{t}=\sum_{i=0}^{N-1}H^{i}1_{(T_{i},T_{i+1}]}(t),$$ where
$H^{i}$ is ${\cal F}_{T_{i}}$ measurable. The key point is that
the weight chosen at date $T_{i}$ is in place right after $T_{i}$,
and up until $T_{i+1}$. In particular, at $T_{i}$, $H^{i-1}$
prevails. When applied to the martingale differences, the simple
weighting scheme delivers for each $\omega$:
$$\tilde{M}_{t}=\int_{0}^{t}H_{u}dM_{u}:=\sum_{i=0}^{J(t)-1}H^{i}(M_{T_{i+1}}-M_{T_{i}})+H^{J(t)}(M_{t}-M_{T_{J(t)}}),$$
where $J(t)(\omega)$ is set such that $T_{J(t)}(\omega) \leq t <
T_{J(t)+1}(\omega)$. The staggered information structure implies that
each increment is conditionally centered, and $(\tilde{M}_{t})$ is a
centered ($E_{0}[\tilde{M}_{t}]=0$) martingale as in the discrete
time case.

The theory of stochastic integrals consists in extending this
construction to more general weighting schemes while preserving the
staggered information structure. We will be evasive about the technical
conditions needed for stochastic integration to work. We will however
keep the information structure in mind. Integrands[^1] cannot
anticipate on information. Adapted continuous processes (i.e. each
$H_{t}$ is ${\cal F}_{t}$ measurable and trajectories are
continuous) are suitable integrands. When the underlying martingale is
allowed to jump (while being continuous on the right with limits on the
left - cadlag), the integrands can also be allowed to jump provided they
are caglad (continuous on the left with limits on the right - see the
post on portfolio returns). These requirements are needed to ensure that
the stochastic integral of a valid integrand against a martingale
remains a martingale.

Sensitivity of a martingale to the underlying shocks
====================================================

A martingale $(M_{t})_{t \in \mathbb{T}}$ is the additive
accumulation of the associated shocks, whether these are true
differences $(\Delta M_{t})$ as in the discrete time case or
infinitesimal idealizations $(dM_{t})$. I use the discrete time case
in what follows. Any particular shock $\Delta M_{u}$ has a fully
persistent impact on the subsequent level $(M_{t})_{t \geq u}$ of
the martingale. We could write this as:$$\frac{\partial
M_{t}}{\partial \Delta M_{u}}=1,\, t \geq u.$$ We can see the
stochastic integral as a method to create a new martingale with a
different sensitivity to the underlying shocks. The new sensitivity is
*a priori* given by $H_{u-1}$. This is right when the integrand is a
deterministic function, in which case we thus have:$$\frac{\partial
\tilde{M}_{t}}{\partial \Delta M_{u}}=H_{u-1},\, t \geq u.$$
When integrands are stochastic however, $H_{u-1}$ cannot measure the
overall impact of the shock on the future level of the new martingale.
Indeed, the shock might alter the integrand $H_{t}$ at a future date.
We would like to write:$$\frac{\partial \tilde{M}_{t}}{\partial
\Delta M_{u}}=H_{u-1}+\sum_{u+1}^{t}\frac{\partial
H_{v-1}}{\partial \Delta M_{u}}\Delta M_{v},\, t \geq u.$$ The
meaning of $\frac{\partial H_{v-1}}{\partial \Delta M_{u}}$ is
however quite unclear unless $H_{v-1}$ can itself be described as a
stochastic integral with deterministic integrand! The martingale
$(\tilde{M}_{t})_{t \in \mathbb{T}}$ would then be a double
stochastic integral.

What is sketched above is precisely the program of defining Malliavin
derivatives, initially developed for Brownian filtrations and integrals.
The program can be carried out because in the Brownian filtration, all
square integrable random variables can be approximated as a multiple
stochastic integral[^2]. As such, their derivatives with respect
to the underlying Brownian shocks can be computed. We will not need the
full force of this theory, but we will keep in mind the idea. We will
often use deterministic integrands for which Malliavin derivatives are
trivial. Stochastic Brownian integrals with deterministic integrands are
Gaussian variables. They are extremely handy because they allow to
express a wide range of phenomena while permitting analytical
computation.

Martingales and martingale representation
=========================================

Readers with a mathematical inclination could raise the following
problem. Stochastic integrals allow to produce new martingales from an
initial one. Can we produce all martingales in this way?

Let's then start from a filtered probability space as above, with the
filtration being the filtration generated by a given martingale
$(M_{t})_{t \in \mathbb{T}}$. We take $\mathbb{T}$ to be an
interval within $\mathbb{N}$ or $\mathbb{R}$. We therefore start
with a minimal setup: a single martingale described in the most
parsimonious filtered probability space which can support it. We can now
define new martingales using stochastic integration based on suitably
adapted integrands. We thereby get a wealth of new (centered)
martingales as stochastic integrals. On the other hand, any ${\cal
F}_{T}$ integrable variable $X_{T}$ with mean $E_{0}[X_{T}]=0$
defines a centered martingale ($E_{t}[X_{T}]$). The latter set of
centered martingales is *a priori* larger than the previous set of
centered martingales defined through stochastic integrals against the
initial martingale. Indeed a stochastic integral is a closed centered
martingale:$$\int_{0}^{t}H_{u}dM_{u}=E_{t}[\int_{0}^{T}H_{u}dM_{u}].$$
The question is then whether the inclusion is strict[^3]. It
turns out again that in the Brownian filtration, the two sets of
martingales coincide. Martingales can be represented as stochastic
integrals: the martingale representation theorem holds. A similar result
holds when the underlying martingale is the compensated Poisson process.
There are however plenty of cases where the inclusion is strict. I give
below two trivial examples that shed some light on what is going on.

I assume an extreme discrete time case, with only two dates $T=0,1$.
The sigma algebra ${\cal F}_{0}$ is trivial and ${\cal F}_{1}$
is the sigma algebra generated by a variable $\epsilon$. Stochastic
integrals are just proportional functions of $\epsilon$ since
${\cal F}_{0}$ random variables (integrands) are constant. Assume
$\epsilon$ is a standardized Gaussian variable. Consider
$X_{1}=\epsilon^{2}-1$. This defines a centered martingale which is
not linear in $\epsilon$. The martingale representation theorem does
not hold.

If instead, $\epsilon$ equals a binomial variable taking values
$+1$ with probability $1/2$ and $-1$ with probability $1/2$, the
martingale representation theorem holds. Indeed, any centered ${\cal
F}_{1}$ measurable variable is defined by two values $X_{1}(1)$ and
$X_{1}(-1)$ such
that:$$\frac{1}{2}X_{1}(-1)+\frac{1}{2}X_{1}(1)=0.$$
Thus:$$X_{1}(-1)=-X_{1}(1),$$
and:$$X_{1}=X_{1}(1)\epsilon,$$ which is a stochastic integral
since $X_{1}(1)$ is a constant.

This gives a good sense of why the compensated Poisson model has a
martingale representation theorem. In the Brownian case, it is clear
that continuous time plays an important role. One can perhaps close this
post by noting that in this case:
$$M_{1}^{2}-1=\int_{0}^{1}M_{t}dM_{t}.$$ Moments shifted so
as to be centered and more generally centered non linear functions of
$M_{1}$ can be obtained as stochastic integrals. Continuous time does
achieve a few miracles!


[^1]:  The weighting function is called the integrand while the underlying
    martingale is called the integrator.

[^2]: See for instance D. Nualart, *The Malliavin Calculus and Related
    Topics*, Springer.

[^3]:  This question has an important interpretation in finance, in a
    broader but related context. In a market model, if all terminal
    pay-offs can be derived as a porfolio value (i.e. a stochastic
    integral) where the portfolio trades underlying financial
    instruments, the market is said to be complete. Completeness
    therefore means, loosely speaking, that a representation theorem
    holds with respect to the tradable instruments.
