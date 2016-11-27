--- 
layout: post 
title: Defining Returns 
author: Guillaume Rabault
categories: [Finance] 
tags: [Returns] 
fullview: false 
--- 

*This post reviews the definition of
returns. It looks at discrete time returns and log returns as well as at
the operation of compounding. In the log return context, return
compounding becomes additive, which proves very convenient. Log returns
however depend in a non additive way in the components of returns
(dividends and price appreciation)[^0]. Continuous compounding
arises as the discretization grid get finer. Continuous time often lends
itself to closed analytical formulas.*

* * * * *

Single period returns
=====================

Discrete time does not demand much mathematical sophistication, at least
at first sight. Dates at which data are observed are forced to belong to
a grid $t=0, \delta, 2\delta, 3\delta, \ldots$ where $1/\delta$
can be conveniently set a to natural number. If, as is customary, $1$
corresponds to a year, we get a quarterly grid when $1/\delta$ is set
to $4$. The price $(P_{t})$ of an asset will be defined on those
dates only, as will income payments $(D_{t})$. In this context, the
rate of return of the asset over the time interval $[t,t+\delta],$ is
defined as:
$$R_{t+\delta}=\frac{P_{t+\delta}-P_{t}+D_{t+\delta}}{P_{t}}=\frac{\Delta
P_{t+\delta}+D_{t+\delta}}{P_{t}}=\frac{P_{t+\delta}+D_{t+\delta}}{P_{t}}-1,$$
or through:\
 $$1+R_{t+\delta}=\frac{P_{t+\delta}+D_{t+\delta}}{P_{t}}.$$

The interpretation of the time interval is key. If $\delta =1/4$ is
interpreted as a quarter, the above return is a quarterly return. It is
practical to define an arithmetically annualized return
$\tilde{R}_{t+\delta}$ (multiplying $R_{t+\delta}$ by
$1/\delta$; this is not as neat as we would like however since
arithmetic compounding is not valid in this context - see below the
compounding section) and similarly an arithmetically annualized income
payment $\tilde{D}_{t+\delta}$ leading to the following equation:
$$\frac{\Delta
P_{t+\delta}+\tilde{D}_{t+\delta}\delta}{P_{t}}=\tilde{R}_{t+\delta}\delta$$\
 This clearly looks like a geometric differential equation:\
 $$\frac{dP_{t}+\tilde{D}_{t}dt}{P_{t}}=\tilde{R}_{t}dt.$$

Compounding
===========

Returns computed across several time intervals require some care. Assume
an investor buys the financial instrument at date $t$ and manages to
receive over each elementary time interval the return
$R_{t+k\delta}$ for $k=1,\ldots, N$ (this involves reinvesting
income into the contract; the quantity invested in the contract thus
changes at each date). One can then compute the cumulated return as the
product: $$1+R_{t\rightarrow t+N\delta}=(1+R_{t+\delta})\cdots
(1+R_{t+N\delta}).$$\
 For $N=1/\delta$, we get an annual return. 
 
 Annualization is a
geometric operation. One can use the logarithmic function to describe
compounding as an arithmetic operation instead. Setting:
$$r_{t}=\log(1+R_{t}),$$\
 we then have: $$1+R_{t\rightarrow
t+N\delta}=\exp\left(r_{t\rightarrow
t+N\delta}\right)=\exp\left(r_{t+\delta}+\cdots+r_{t+N\delta}\right).$$\
 All compounding operations applied to log-returns are arithmetic,
including annualization.

Within the log return set-up, the difference equation reads:\
 $$\log(1+\frac{\Delta
P_{t+\delta}+D_{t+\delta}}{P_{t}})=\tilde{r}_{t+\delta}\delta$$
where $\tilde{r}_{t+\delta}$ is, adequately this time, the
arithmetically annualized log return
($r_{t+\delta}=\tilde{r}_{t+\delta}\delta$). The drawback of
this scheme is that:$$\log(\frac{\Delta
P_{t+\delta}+D_{t+\delta}}{P_{t}}),$$ is not additive in the two
components of the return, the price return and the dividend yield.

Continuous time
===============

We have thus seen that in discrete time, we face a few hurdles.
Compounding is geometric and this suggests to concentrate on
log-returns. But for log returns, the return decomposition into price
return and dividend yield is non-linear. Continuous time is analytically
simpler. It can be recovered by letting the discretization get finer and
finer. The return equation then becomes[^1]:
$$\frac{dP_{t}+\tilde{D}_{t}dt}{P_{t}}=\tilde{r}_{t}dt,$$
where as before, the tilde notation is used to denote annualized
variables. In particular, $\tilde{r}_{t}$ is an annualized log
return as in the absence of dividends for instance, the integral
equation reads:
$$P_{t}=P_{0}\exp\left(\int_{0}^{t}\tilde{r}_{u}du\right).$$
In continuous time indeed, instantaneous returns and log-returns
coincide[^2] since $$\frac{dP_{t}}{P_{t}}=d(\log(P_{t})).$$

Summary
=======

We have looked at the definition of returns and log-returns both in
discrete time and in continuous time. Both discrete time and continuous
time entail their own challenges. Discrete time is usually more
elementary from a mathematical standpoint (integrals are reduced to
sums, differential equations to difference equations...), although quite
often, closed form formulas are hard to come by. Continuous time
involves more elaborate mathematical operations but provides more
compact expressions. In what follows, I will try to make the best of
both set-ups when introducing portfolio returns and uncertainty.


[^0]: A later post will show a loglinear approximation of the discrete
time log returns in the presence of dividends and capital gains. 
[^1]: Assuming standard calculus applies, as opposed to Ito calculus. Another
[post](/finance/2013/03/14/integrating-returns.html "Integrating Returns")
will explain what's at stake behind these two modeling choices. 
[^2]: In standard calculus, as opposed to Ito calculus - see footnote $2$.
