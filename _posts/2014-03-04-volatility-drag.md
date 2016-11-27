--- 
layout: post 
title: The Volatility-Drag 
author: Guillaume Rabault
categories: [Finance] 
tags: [Volatility] 
fullview: false 
--- 

*I review the impact on the future
price level of random noise in the return process. This effect operates
through the non-linearity of compounding. I look at how an increased
level of volatility changes the price trajectories. Normally distributed
(say) return variability lowers the median of the price distribution and
skews it towards the upside. Over time, the skew increases as
compounding operates. The majority of price trajectories are depressed
by volatility. The mean price level is however unaffected as the lower
trajectories are made up by a few 'explosive' ones. This will be
important to bear in mind when discussing portfolio choice and the
effect of portfolio rebalancing.*

* * * * *

Volatility and compounding Consider a set of yearly returns (say)
$(r_{t})_{t=1,\ldots,T}$. The compounded return over the period
$[0,T]$ is: $$(1+r_{1})\cdots(1+r_{T}).$$ If we want to
assess the impact of the variability of returns, we might wish to
compare this to $(1+\bar{r})^{T},$ where:
$$\bar{r}=\frac{1}{T}\sum_{t=1}^{T} r_{t}.$$ Introducing the
deviations to the mean $\varepsilon_{t}=r_{t}-\bar{r}$
($t=1,\ldots,T$), we now need to compare:
$$(1+\bar{r}+\varepsilon_{1})\cdots(1+\bar{r}+\varepsilon_{T})$$
and $(1+\bar{r})^{T}$. This is equivalent to comparing
$1/T$ times the logs of these quantities, but then the inequality:
$$\frac{1}{T}\sum_{t=1}^{T}
\log(1+\bar{r}+\varepsilon_{t})\leq
\log(\frac{1}{T}\sum_{t=1}^{T}r_{t})=\log(1+\bar{r}),$$ is a
simple consequence of the concavity of the log[^f]. Given that the log
is strictly concave, we know that the inequality is strict unless the
return series is constant. A simple second order approximation of the
log function yields: $$\frac{1}{T}\sum_{t=1}^{T}
\log(1+\bar{r}+\varepsilon_{t}) \approx
\log(1+\bar{r})-\frac{1}{2}\frac{1}{(1+\bar{r})^{2}}Var(\varepsilon),$$
where $Var(\varepsilon)$ is the empirical variance of return
shocks:
$$Var(\varepsilon)=\frac{1}{T}\sum_{t=1}^{T}\varepsilon_{t}^{2}.$$
The former relationship can be read as linking the geometric mean return
and the arithmetic mean:
$$\left(\prod_{t=1}^{T}(1+r_{t})\right)^{1/T} \approx
\exp\left(\log(1+\bar{r})-\frac{1}{2}\frac{1}{(1+\bar{r})^{2}}Var(\varepsilon)\right).$$
We thus see that variability in the returns
$(r_{t})_{t=1,\ldots,T}$ lowers the compounded return. Of
course, this result hinges on the anchoring of the *standard mean
return*. In other words, the volatlity-drag is obtained when holding
the average standard return constant and increasing the dispersion of
realized standard returns around it. Variability in log-returns for a
given mean log-return would have no effect on compounding[^q]. The
volatility-drag should not be over-interpreted. 
I now look at the consequences of volatility in more
structured models of price dynamics, starting with the discrete time log
normal model presented in [this
post](/finance/2014/02/03/discrete-time-lognormal-dynamics.html "LOG-NORMAL-DYNAMICS").This
will allow to identify the impact of volatility on the
**distribution** of compounded returns and thereby better understand
the volatility-drag. To simplify the description, I assume the expected
returns $(r_{t})_{t=1,\cdots,T}$ and volatilities
$(\sigma_{t})_{t=1,\cdots,T}$ are deterministic. In this
setup, the compounded return over $T$ periods is:
$$\prod_{t=1}^{T}\exp(r_{t}+\sigma_{t}\varepsilon_{t}-\frac{1}{2}\sigma_{t}^{2})=\exp(\sum_{t=1}^{T}
r_{t}+\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t}-\sum_{t=1}^{T}\frac{1}{2}\sigma_{t}^{2}).$$
The median realization of
$\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t}$ is zero and under
this scenario, the compounded return is just:
$$\exp(\sum_{t=1}^{T}
r_{t}-\sum_{t=1}^{T}\frac{1}{2}\sigma_{t}^{2}).$$ The mean of
the compounded return however is:
$$E_{0}\left[\exp(\sum_{t=1}^{T}
r_{t}+\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t}-\sum_{t=1}^{T}\frac{1}{2}\sigma_{t}^{2})\right]=\exp(\sum_{t=1}^{T}
r_{t}).$$ It is therefore apparent that volatility lowers the median
compounded return but not the mean compounded return. Compared to the
median, the mean is pushed upwards by the right tail of the distribution
of shocks. This reflects the convexity of the exponential function!
Volatility drives a constant wedge between the mean and the median. This
has strong consequences over the long run. Assume $t$ measures
time in years, the annualized compounded return can be written:
$$\exp\left(\frac{1}{T}\left(\sum_{t=1}^{T}
r_{t}-\sum_{t=1}^{T}\frac{1}{2}\sigma_{t}^{2}\right)+\frac{1}{T}\left(\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t}\right)\right).
$$ It is easy to design conditions such that as $T$ goes to
infinity: $$\frac{1}{T}\left(\sum_{t=1}^{T}
r_{t}-\sum_{t=1}^{T}\frac{1}{2}\sigma_{t}^{2}\right)
\rightarrow c,$$ where $c$ is a constant, and (law of large
numbers) almost surely:
$$\frac{1}{T}\left(\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t}\right)\rightarrow
0.$$ This means that in the long run, annualized returns get very
close to the median return and the right tail of the annualized return
distribution (i.e. the upside) becomes negligible. Volatility indeed
drags down the annualized return with probability one in the long run.
This suggests that a long term investor might choose a portfolio so as
to maximize $c$. Although the annualized return converges to
$c$, the set of non annualized compounded returns still contain
trajectories which are much above $cT$ as the volatility of the
'compounded' return shock:
$$\sum_{t=1}^{T}\sigma_{t}\varepsilon_{t},$$ grows like:
$$\left(\sum_{t=1}^{T}\sigma_{t}^{2}\right)^{1/2} \propto
\sqrt{T}.$$ From a finite horizon investment perspective finally,
whether volatility is good or bad depends on how you weigh the different
scenarios into your investment objective. It thus depends on the chosen
utility function. When the utility function is logarithmic, the investor
indeed maximizes $c$. This whole topic will require a specific
development. Continuous time Unsurprisingly, the same reasoning can
be carried out in continuous time using the standard geometric
diffusions to model the price process:
$$\frac{dP_{t}}{P_{t}}=r_{t}dt+\sigma_{t}dW_{t}.$$ The only
difference to the discrete case above is that sums are replaced by
integrals. Conditions have to be designed such that for instance (law of
large numbers)[^p]:
$$\frac{1}{T}\left(\int_{0}^{T}\sigma_{t}dW_{t}\right)\rightarrow
0,$$ almost surely as $T$ goes to infinity. When this is
satisfied, the long run annualized return is characterized by:
$$\exp\left(\frac{1}{T}\left(\int_{0}^{T}
r_{t}dt-\int_{0}^{T}\frac{1}{2}\sigma_{t}^{2}dt\right)\right).$$
When comparing asset returns in the long run, one can then concentrate
on the log of the above quantity, i.e.:
$$\frac{1}{T}\left(\int_{0}^{T}
(r_{t}-\frac{1}{2}\sigma_{t}^{2})dt\right).$$ Some authors (for
example Fernholz[2002]) call
$(r_{t}-\frac{1}{2}\sigma_{t}^{2})$ the growth rate of the
security although this might be a bit misleading.   **Notes and
references:** There is a literature that argues that investors should
optimize the growth rate
$(r_{p,t}-\frac{1}{2}\sigma_{p,t}^{2})$ of a portfolio
$p$. This is usually called the Kelly approach to investing. In
the economic tradition, one starts with a utility function, and
maximizes the utility of (say) terminal wealth. One can recover the
Kelly investment rule by using a logarithmic utility function. More
generally, optimal portfolios generated through a utility function
contain a fraction of the Kelly optimal portfolio. For a recent review
of the interaction between volatility and growth, see for instance
Dempster[2007].  

* * * * *

Dempster, M.A.H, Evstigneev, I.V., and Shenk-Hoppé, K.R. [2007],
'Volatility-Induced Financial Growth', *Quantitative Finance*, Vol 7
No. 2, April 2007, 151-260. 

Fernholz, E.R. [2002], *Stochastic
Portfolio Theory*, Springer.


[^f]: For a concave function $f(\cdot)$ ($\mathbb{R}
\rightarrow \mathbb{R}$), if
$\sum_{i=1}^{n}\lambda_{i}x_{i}$ is a convex combination of
$(x_{i})_{i=1,\cdots,n}$, we have:
$$\sum_{i=1}^{n}\lambda_{i}f(x_{i}) \leq
f(\sum_{i=1}^{n}\lambda_{i}x_{i}).$$ This property can be used
to characterize concavity. 

[^q]: One could therefore say that the
volatility-drag is purely an artefact of the choice of units. Returns ar
not measured in decibels, so to speak (decibels is a logarithmic scale
for sound). 

[^p]: In Fernholz[2002], section 1.3, Fernholz shows that
the law of large numbers holds if $\lim_{t \rightarrow \infty}
t^{-2}\left(\int_{0}^{t}\sigma_{u}^{2}du\right)\log(\log(t))=0.$
The proof of this fact hinges on the time changing technique and the law
of interated logarithm for the Brownian motion.
