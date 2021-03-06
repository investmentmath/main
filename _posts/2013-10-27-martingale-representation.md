---
layout: post 
title: Martingale Representation 
author: Guillaume Rabault
date: 2013-10-27
categories: [Math]
tags: [Martingales] 
fullview: false 
--- 


*The martingale representation
problem in its simplest form is the following. Given a filtration
generated by a martingale $M$ and given another martingale $N$
adapted to the filtration, can we express $N$ as a stochastic integral
with $M$ as the integrator? The martingale $N$ is generally closed,
i.e. it can be expressed as the conditional expectation of a terminal
variable $N_{T}$. In this case, the integrand $H_{t}$ of the
stochastic integral representation is heuristically the sensitivity of
$N_{T}$ to the shock $dM_{t}$.The Brownian filtration is the most
important example where a Martingale Representation Theorem holds.*

* * * * *

The theory of martingale representation is concerned with the following
problem.

Consider a filtered probability space $(\Omega,{\cal F},P)$ with
index space $\mathbb{T}=[0,T]$ where $T$ is finite. Such a space
supports a set of martingales ${\cal M}$ against which we can compute
stochastic integrals for predictable integrands.

We are given an ${\cal F}_{T}$-measurable random variable
$X_{T}$. It induces a martingale $(E_{t}[X_{T}])_{t \in
\mathbb{T}}$. This process represents, within the model, the
anticipation of $X_{T}$ at any point $t$. The changes in
$E_{t}[X_{T}]$ as a function of $t$ reflect the real time
acquisition of information on $X_{T}$. New information comes as
surprises as modeled in martingale differences (see [this
post](/math/2013/04/24/martingales.html "MARTINGALES")). Heuristically,
martingale representation asks the following question: can we represent
the surprises in $(E_{t}[X_{T}])_{t \in \mathbb{T}}$ for any
$X_{T}$ as a linear function of the (contemporaneous) surprises
embedded in our set ${\cal M}$ of martingales. More precisely, can we
represent the martingale $(E_{t}[X_{T}])_{t \in \mathbb{T}}$ as a
sum of stochastic integrals against some martingales in ${\cal M}$.

A striking incarnation of this issue is found when the filtered
probability space is generated by a Brownian motion[^1].

**Theorem (Martingale Representation for the Brownian Filtration)**:*Let
${\cal F}$ be the smallest right continuous and complete filtration
generated by a univariate Brownian motion $(B_{t})_{t \in
\mathbb{T}}$. Let $X_{T}$ be an ${\cal F}_{T}$-measurable
random variable with finite second moment
$E_{0}[X_{T}^{2}]<\infty$. Then there is a predictable process
$(H_{t})_{t \in \mathbb{T}}$ with
$\int_{0}^{T}H_{s}^{2}ds<\infty$ such
that:$$X_{T}=E[X_{T}]+\int_{0}^{T}H_{s}dB_{s}.$$*

${\scriptstyle \blacksquare}$

In the same context as above, we have a simple yet important corollary:

**Corollary:** *For any square integrable[^2]right continuous
martingale $(M_{t})_{t \in \mathbb{T}}$ with $M_{0}=0$, there
exists a predictable process $(H_{t})_{t \in \mathbb{T}}$ with
$\int_{0}^{T}H_{s}^{2}ds<\infty$ such
that:$$M_{t}=\int_{0}^{t}H_{s}dB_{s}.$$*

${\scriptstyle \blacksquare}$

In other words, all square integrable right continuous martingales with
initial value zero are Brownian stochastic integrals. Actually, in our
context, all square integrable martingales have a version which is still
a martingale and is right continuous with left limits. They can
therefore be represented as Brownian integrals. Since Brownian integrals
have continuous trajectories, all square integrable martingales in this
setup have a continuous version. Finally, one can extend the above
result to show that all local martingales can be represented as a
Brownian stochastic integral.

It is quite easy to generate setups where the filtration is the minimal
filtration generated by a given martingale $(M_{t})_{t \in
\mathbb{T}}$, and yet, the filtration supports other martingales which
cannot be written as sotchastic integrals of $(M_{t})_{t \in
\mathbb{T}}$. In [this
post](/math/2013/04/24/martingales.html "MARTINGALES"), an example is
given where $\mathbb{T}$ is discrete and $(M_{t})_{t \in
\mathbb{T}}$ has standardized gaussian increments. If, on the other
hand, $(M_{t})_{t \in \mathbb{T}}$ has binomial increments, the
martingale representation holds with the set ${\cal M}$ consisting of
$(M_{t})_{t \in \mathbb{T}}$. A solution to recover a martingale
representation result when it does not hold for ${\cal M}=\{
(M_{t})_{t \in \mathbb{T}} \}$ is to add other martingales in
${\cal M}$, based on higher order moments of $(M_{t})_{t \in
\mathbb{T}}$ for instance. Indeed, the problems generally come from
the difficulty of generating non linear functions of $(M_{t})_{t \in
\mathbb{T}}$ through the stochastic integral which, in the end, is
just a linear reweighting of the increments of $(M_{t})_{t \in
\mathbb{T}}$.

Given the above remarks, the Brownian martingale representation theorem
looks like a nice accident. I now sketch the proof. An ${\cal
F}_{T}$-measurable random variable is, roughly speaking, a function of
the increments of the Brownian motion. A simple example would be a
function
$f(B_{t_{1}}-B_{t_{0}},\cdots,B_{t_{n}}-B_{t_{n-1}})$ where
the time intervals $[t_{i},t_{i-1}]$ do not overlap. Such functions
can however be recovered through Fourier transform from products of
complex exponentials[^3]:
$$\exp(iu_{1}(B_{t_{1}}-B_{t_{0}}))\cdots
\exp(iu_{n}(B_{t_{n}}-B_{t_{n-1}})).$$ It is conceivable that if
a martingale representation were to hold for such a function, the
representation could be extended by limiting arguments to all ${\cal
F}_{T}$-measurable random variables. However, Ito calculus implies
that:
$$\exp(iu_{k}(B_{t}-B_{t_{k-1}})+\frac{1}{2}u_{k}^{2}(t-t_{k-1}))=1+$$
$$\int_{t_{k-1}}^{t_{k}}iu_{k}\exp(iu_{k}(B_{s}-B_{t_{k-1}})+\frac{1}{2}u_{k}^{2}(s-t_{k-1}))dB_{s},$$
i.e.
$$d\left(\exp(iu_{k}(B_{t}-B_{t_{k-1}})+\frac{1}{2}u_{k}^{2}(t-t_{k-1}))\right)=\exp(iu_{k}(B_{t}-B_{t_{k-1}})+\frac{1}{2}u_{k}^{2}(t-t_{k-1}))dB_{t}.$$
This complex exponential is a geometric martingale with initial value
$1$ at $t=t_{k-1}$.

From this, we get (taking $t=t_{k}$ and rearranging terms):
$$Z_{k-1}=\exp(iu_{k}(B_{t_{k}}-B_{t_{k-1}}))=\exp(-\frac{1}{2}u_{k}^{2}(t_{k}-t_{k-1}))+$$
$$\int_{t_{k-1}}^{t_{k}}iu_{k}\exp(iu_{k}(B_{s}-B_{t_{k-1}})+\frac{1}{2}u_{k}^{2}(s-t_{k}))dB_{s}$$
$$=F_{k-1}+\int_{t_{k-1}}^{t_{k}}H_{k-1}(s)dB_{s},$$ where
$Z_{k-1}$ is the random variable of interest, $F_{k-1}$ is a
function of non random parameters only and $H_{k-1}$ is the integrand
within the stochastic integral. We thus have the right representation
for a single exponential of a Brownian increment.

When multiplying two such terms attached to non overlapping intervals,
say $[t_{k-1},t_{k}]$ and $[t_{k},t_{k+1}]$, the product rule
entails no covariation terms because the stochastic integrals refer to
non overlapping time intervals:
$$[\int_{t_{k-1}}^{t_{k}}H_{k-1}(s)dB_{s},\int_{t_{k}}^{t_{k+1}}H_{k}(s)dB_{s}]=0.$$
We thus have the following representation for the product:
$$Z_{k-1}Z_{k}=F_{k-1}F_{k}+\int_{t_{k-1}}^{t_{k}}F_{k}H_{k-1}(s)dB_{s}+\int_{t_{k}}^{t_{k+1}}Z_{k-1}H_{k}(s)dB_{s},$$
which still has the right structure. It is now clear that any product
involving a finite number of such exponentials involving non overlapping
intervals has a martingale representation. The rest of the proof is a
matter of spelling out the limiting arguments that allow to
extend[^4] the representation to any function
$f(B_{t_{1}}-B_{t_{0}},\cdots,B_{t_{n}}-B_{t_{n-1}})$ and
then to any ${\cal F}_{T}$-measurable random variable (through a
density argument).

In the Brownian context thus, Brownian integrals allow to generate all
the local martingales supported by the filtration[^5]. Amongst
them are all the martingales generated by moments $B^{\alpha}_{t}$,
for instance $X_{t}=B^{2}_{t}-t=2\int_{0}^{t}B_{s}dB_{s}$.

A striking illustration of this involves Hermite polynomial functions.
If
$H_{n}(x,y)=\left(\frac{y}{2}\right)^{\frac{n}{2}}h_{n}(\frac{x}{\sqrt{2y}})$
($n \geq 0$) where $h_{n}(\cdot)$ are Hermite
polynomials[^6], then $H_{n}(B_{t},t)$ are martingales and
we have the following integral representation:
$$H_{n}(B_{t},t)=\int_{0}^{t}nH_{n-1}(B_{u},u)dB_{u
}=n!\int_{0}^{t}\int_{0}^{t_{n-1}}\cdots\int_{0}^{t_{1}}dB_{s}dB_{t_{1}}
\cdots dB_{t_{n-1}}.$$ This result can be found for instance in
Chung[1990], chapter 6.

Reference: Chung K.L and R.J. Williams, 1990 : *An introduction to
Stochastic Integration*, Birkhauser.

Bass R.F., 2011, *Stochastic Processes*, Cambridge University Press


[^1]:  The following results can be found in Bass[2011], p. 80.

 [^2]: $E_{0}[M_{T}^{2}]<\infty$. 

 [^3]: In our context, the Fourier transform amounts to mixing functions
    indexed by $(u_{1},\ldots,u_{n})$ using a weighting scheme
    ${\hat f}(u_{1},\ldots,u_{n})$. 

 [^4]: Through the Fourier transform, which amounts to integrating the
    integral representations attached to different parameters
    $(u_{1},\ldots,u_{n})$, using a weighting scheme ${\hat
    f}(u_{1},\ldots,u_{n})$. 

 [^5]: It is important that the filtration be the minimal filtration
    generated by the Brownian motion, i.e. the smallest right continuous
    and complete filtration generated by the Brownian motion.
    

 [^6]: $H_{0}(x,y)=1,H_{1}(x,y)=x,H_{2}(x,y)=x^{2}-y,\ldots$
