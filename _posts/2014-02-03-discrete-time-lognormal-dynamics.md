--- 
layout: post 
title: Discrete Time Lognormal Dynamics 
author: Guillaume Rabault
categories: [Finance] 
tags: [Processes] 
fullview: false
--- 

*This post introduces
discrete time price dynamics in a log-normal setup. This framework
allows an easy translation of some of the continuous time results
discussed on this site.*

* * * * *

Reminder on log normality The random variable $X$ has a log-normal
distribution if $x=\log(X)$ has a normal distribution. If the
distribution of $x$ is $\cal{N}(\mu,\sigma)$, then we will note
the distribution of $X$ $\cal{L}(\mu,\sigma)$. Its mean is:
$$\exp(\mu+\frac{1}{2}\sigma^{2}).$$ This is consistent with
the convexity of the exponential function and the Jensen effect[^q].
Whereas $x$ has a distribution which is centered around its mean
$\mu$, the distribution of $X$ is positively skewed. Its median is
$\exp(\mu)$ which is lower than its mean
$\exp(\mu+\frac{1}{2}\sigma^{2})$ by the factor
$\exp(-\frac{1}{2}\sigma^{2})$. Log normal price dynamics
Suppose now that we have a value process $(P_{t})_{t \in
\mathbb{N}}$ such that as seen from date $t$,
$P_{t+1}/P_{t}$ is log-normal
$\cal{L}(\mu_{t+1},\sigma_{t+1})$. More explicitly, we assume
that the variables $\mu_{t+1}$ and $\sigma_{t+1}$ are
$\cal{F}_{t}$ measurable. Then:
$$E_{t}[\frac{P_{t+1}}{P_{t}}]=\exp(\mu_{t+1}+\frac{1}{2}\sigma_{t+1}^{2}).$$
I will note $r_{t+1}=\mu_{t+1}+\frac{1}{2}\sigma_{t+1}^{2}$
the log of the sequential expected return as of date $t$. With this
notation, we can now write:
$$\frac{P_{t+1}}{P_{t}}=\exp(r_{t+1}+\sigma_{t+1}\varepsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2}),$$
where by construction, $\varepsilon_{t+1}$ is
$\cal{N}(0,1)$. We can also write:
$$\frac{P_{t+1}}{P_{t}}=\exp(r_{t+1})\exp(\sigma_{t+1}\varepsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2}),$$
where:
$$E_{t}[\exp(\sigma_{t+1}\varepsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2})]=1,$$
so that
$\exp(\sigma_{t+1}\varepsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2})$
can be interpreted as a multiplicative surprise. It is indeed the
martingale ratio of a multiplicative martingale (see the notion of
martingale difference in [this
post](/math/2013/04/24/martingales.html "MARTINGALES").). This
multiplicative surprise has mean $1$ but median
$\exp(-\frac{1}{2}\sigma_{t+1}^{2})<1$. We have thus
decomposed the return into its expected component and a surprise. This
is really a discrete time version of the usual geometric Brownian
diffusion: $$\frac{dP_{t}}{P_{t}}=r_{t}dt+\sigma_{t}dB_{t}.$$
Intuition is sometimes easier to develop working on the discrete time
model. As a final remark, we need to emphasize that although the shocks
in the above discrete time model are conditionally log-normal, it does
not imply that prices have log-normal marginal distributions. This is
the case if $(\mu_{t})_{t \in \mathbb{N}}$ and
$(\sigma_{t})_{t \in \mathbb{N}}$ are deterministic
processes, but it fails to be the case in general.


[^q]: If $f(\cdot)$ is a conxex function ($\mathbb{R} \rightarrow
\mathbb{R}$) and $z$ is a random variable, $E[f(z)]\geq f(E[z])$.
