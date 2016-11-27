--- 
layout: post 
title: Introducing Diffusions 
author: Guillaume Rabault
categories: [Math] 
tags: [Processes] 
fullview: false 
--- 

*The purpose of this note is to
introduce diffusions which are made up of a drift and a martingale
component. I start from the elementary discrete time setup where the
drift of the process is most easily understood. I then explain how the
specialized decomposition of a diffusion into a drift and a Brownian
integral can arise as the limit of the decompositions obtained on the
discretized process.*

* * * * *

Doob's decomposition
====================

We introduced the martingale concept in the [post on
martingales](/math/2013/04/24/martingales.html "MARTINGALES"). In
particular, we explained (see the [post on
martingales](/math/2013/04/24/martingales.html "MARTINGALES") for
notation) that in discrete time ($\mathbb{T}=\mathbb{N}$), a
martingale $(M_{t})_{t \in \mathbb{T}}$ has martingale differences
$\Delta M_{t}=M_{t}-M_{t-1}$ which are conditionally centered:
$$E_{t}[\Delta M_{t+1}]=0.$$ We now wish to relax this constraint
and consider more general processes.

Starting from an adapted process $(X_{t})_{t \in \mathbb{T}}$, we
can consider its differences $\Delta X_{t}=X_{t}-X_{t-1}$ and
define their one step ahead conditional expectation: $$\Delta
A_{t+1}=E_{t}[\Delta X_{t+1}].$$ The random variables $\Delta
A_{t+1}$ are by construction ${\cal F}_{t}$ measurable. In the
language introduced to describe [stochastic
integrals](/math/2013/05/02/stochastic-integrals-as-martingale-transforms.html "STOCHASTIC INTEGRALS AS MARTINGALE TRANSFORMS"),
this process is predictable. Removing $\Delta A_{t+1}$ from
$\Delta X_{t+1}$ is a centering operation. Indeed, setting $\Delta
M_{t+1}=\Delta X_{t+1}-\Delta A_{t+1}$, we get: $$E_{t}[\Delta
M_{t+1}]=0.$$ The variables $\Delta M_{t+1}$ are martingale
differences. Cumulating differences, we can recover the level $X_{t}$
through:$$X_{t}=X_{0}+\sum_{k=1}^{t}\Delta
A_{k}+\sum_{k=1}^{t}\Delta M_{k}.$$ Setting $M_{0}=0$ and
$A_{0}=0$, we can now define two 'level' processes $(A_{t})_{t
\in \mathbb{T}}$ and $(M_{t})_{t \in \mathbb{T}}$ through:
$$A_{t}=A_{0}+\sum_{k=1}^{t}\Delta A_{k},\, t \geq 1,$$
$$M_{t}=M_{0}+\sum_{k=1}^{t}\Delta M_{k},\, t \geq 1.$$ The
first process $(A_{t})_{t \in \mathbb{T}}$ is predictable in the
sense that each $A_{t}$ is ${\cal F}_{t-1}$ measurable (its value
at date $t$ is known at date $t-1$), and the second process
$(M_{t})_{t \in \mathbb{T}}$ is a martingale. Both processes are
of course adapted to the filtration. We can finally write:
$$X_{t}=X_{0}+A_{t}+M_{t}.$$ This decomposition is called Doob's
decomposition.

It should be stressed that $\Delta A_{t}$ are one step ahead
predictions. Two step ahead predictions for instance involve predicting
$\Delta A_{t}$ one step ahead: $$E_{t}[\Delta A_{t+1}+\Delta
A_{t+2}]=\Delta A_{t+1}+E_{t}[\Delta A_{t+2}].$$

By constraining the sign of $(\Delta A_{t})_{t \in \mathbb{T},\,
t \geq 1}$, we obtain sub and supermartingales. A supermartingale is a
process which is expected to decrease or remain stable. It is obtained
by forcing $(\Delta A_{t})_{t \in \mathbb{T},\, t \geq 1}$ to
be negative. A submartingale is a process which is expected to increase
or remain stable, that is $(\Delta A_{t})_{t \in \mathbb{T},\, t
\geq 1}$ is forced to be positive (a martingale is thus both a super
and a submartingale). Accordingly, the process $(A_{t})_{t \in
\mathbb{T}}$ is monotonic in both cases.

Quasimartingales
================

We now look at the case of a continuous time process $(X_{t})_{t \in
[0,T]}$ where $T<\infty$. To carry out the above decomposition, we
can introduce a discretization scheme and apply the previous
calculations to the process obtained thereby. For each discretization
grid $\pi_{n}$ of $[0,1]$ indexed by $n$
($t_{0}=0,\ldots,t_{n}=T$), we can thus split the discretized
version $(X_{t_{i}})_{t_{i} \in \pi_{n}}$ of the original
process into a discrete time martingale and the cumulated expected
changes along the discretization intervals:
$$X^{n}_{t_{i}}=X_{0}+A^{n}_{t_{i}}+M^{n}_{t_{i}}.$$ As
the grid is refined ($n$ tending to infinity), one can hope to
recover: $$X_{t}=X_{0}+A_{t}+M_{t},$$ where $(M_{t})_{t \in
\mathbb{R}_{+}}$ is a continuous time martingale and $(A_{t})_{t
\in [0,T]}$ is the limit of the discretized processes
$(A_{t_{i}})_{t_{i} \in \pi_{n}}$, i.e. the cumulated
infinitesimal expected changes of $(X_{t})_{t \in [0,T]}$.

The first results generalizing the discrete time decomposition to the
continuous time setup and ensuring that the above discretization scheme
converges concerned submartingales and supermartingales, for which the
process $(A_{t})_{t \in [0,T]}$ is monotonic (these assumptions
lead to the Doob-Meyer decomposition, the continuous time version of
Doob's decomposition). A natural generalization was sought among
processes for which $(A_{t})_{t \in [0,T]}$ would be of bounded
variation, since this class of functions is the simplest extension of
monotonic functions (any bounded variation function is the difference of
two bounded monotonic functions). This led to the concept of
quasimartingales, where the main ingredient consists in bounding the
following sums
:$$E[V(\pi)]=E\left[\sum_{i=1}^{n}E_{t_{i-1}}[\left|X_{t_{i}}-X_{t_{i-1}}\right||{\cal
F}_{t_{i-1}}]\right] \leq K < \infty,$$ uniformly with respect
to partitions $\pi=(t_{0}=0,\ldots,t_{n}=T)$ of $[0,T]$ of any
size $n$. The decomposition of a quasimartingale involves a process
$(A_{t})_{t \in [0,T]}$ which has finite expected variation and *a
fortiori* almost everyhere bounded variation.

Stochastic integration can be easily extended from martingales to
quasimartingales since bounded variation functions can be used as
integrators within a well understood integration theory (cf.
Lebesgue-Stieltjes integration). What this means for mathematical
finance is that most continuous time calculus can be carried out
assuming prices follow quasimartingales[^1].

In the case of processes with continuous paths, *necessary and
sufficient conditions* have been identified (see Fisk,
Quasi-Martingales, *Transactions of the American Mathematical Society*,
1965) for $(X_{t})_{t \in [0,T]}$ to be a quasimartingale, in which
case the discretization process described above delivers a martingale
with continuous paths $(M_{t})_{t \in [0,T]}$ and a bounded
variation process $(A_{t})_{t \in [0,T]}$ with continuous paths as
well. This decomposition is unique.

Ito diffusions
==============

We now wish to specialize the above setup so as to get tractable and
flexible specifications for a process $(X_{t})_{t \in [0,T]}$. We
will assume the filtration is generated by a one dimensional Brownian
motion $(B_{t})_{t \in [0,T]}$. We assume the process
$(A_{t})_{t \in [0,T]}$ is of the
form:$$\int_{0}^{t}r(X_{u})du.$$ We thereby select a specific
class of bounded variation processes, those that can be written as the
integral of a function. In addition, we constrain that function to be a
function of the state variable $X_{u}$. Similarly the martingale
process $(M_{t})_{t \in [0,T]}$ is assumed to be a Brownian
stochastic integral:$$\int_{0}^{t}\sigma(X_{u})dB_{u},$$ where
again $\sigma(\cdot)$ is a function of the state variable $X_{u}$
only. The functions $r(\cdot)$ and $\sigma(\cdot)$ are real
measurable functions. We thus
get:$$X_{t}=X_{0}+\int_{0}^{t}r(X_{u})du+\int_{0}^{t}\sigma(X_{u})dB_{u}.$$
The function $r(\cdot)$ is called the drift of the diffusion and the
function $\sigma(\cdot)$ is the volatility of the diffusion. The
interpretation of these two terms is now obvious. The drift measures the
infinitesimal expected change of the process, while volatility measures
the infinitesimal surprises.

The technical conditions usually applied to the drift and volatility
coefficients are (almost everywhere):
$$\int_{0}^{T}\left|r(X_{u})\right|du<\infty,$$
$$\int_{0}^{T}\sigma(X_{u})^{2}du<\infty.$$ The first
condition ensures that $(A_{t})_{t \in [0,T]}$ is almost everywhere
of bounded variation[^2], while the second is needed to define
the Brownian integral.

We finally note that it is customary to summarize the integral equations
through the differential notation:
$$dX_{t}=r(X_{t})dt+\sigma(X_{t})dB_{t},$$ with an initial
condition $X_{0}$. This should however merely be seen as a shorthand
for the integral equation.


[^1]:  Actually, a continuous time process for which stochastic integration
    can be defined is called a semimartingale and quasimartingales are a
    strict subset of semimartingales, but the gap is very small from a
    modeling perspective.

[^2]:  To be precise, one would have to impose stronger condition in the
    quasimartingale context. In spirit, the variation has to be
    integrable:
    $$E[\int_{0}^{T}\left|r(X_{u})\right|du]<\infty.$$ The
    condition spelled out in the text corresponds to the requirement
    that the process $(X_{t})_{t \in [0,T]}$ be a semimartingale,
    rather than a quasimartingale.
