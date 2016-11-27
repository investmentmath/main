--- 
layout: post 
title: From Gaussian to Ornstein Uhlenbeck Processes
author: Guillaume Rabault
categories: [Math] 
tags: [Processes] 
fullview: false 
--- 

*This post
introduces Gaussian processes, i.e. processes with Gaussian finite
dimensional multivariate distributions. Amongst Gaussian processes, the
Ornstein Uhlenbeck process is the only Markovian covariance stationary
example. It plays a key role in applications thanks to its
tractability.*

* * * * *

Gaussian processes
==================

Gaussian processes provide a very handy toolbox for modeling. A Gaussian
process is a process $(X_{t})_{t \in \mathbb{T}}$ such that for
any finite set of indices $(t_{1},t_{2},\ldots,t_{n})$,
$(X_{t_{1}},X_{t_{2}}\ldots,X_{t_{n}})$ follows a multivariate
Gaussian distribution. It should be reminded that the distribution of a
random process, i.e. the distribution of the function $\omega \mapsto
(X_{t}(\omega))_{t \in \mathbb{T}}$ , is determined by its finite
dimensional distributions., i.e. the set of distributions corresponding
to the set of functions $\omega \mapsto
(X_{t_{1}}(\omega),X_{t_{2}}(\omega)\ldots,X_{t_{n}}(\omega))$
indexed by $n-$uples $(t_{1},t_{2},\ldots,t_{n})$.

A multivariate Gaussian distribution is characterized by its mean
${\boldsymbol \mu}$ (a vector) and its covariance matrix
${\boldsymbol \Sigma}$. All its other moments are a function of the
first two moments.[^1]

One can prove furthermore that the set of finite dimensional Gaussian
distributions of a Gaussian process is characterized by the mean
function $t \mapsto E(X_{t})$ and the covariance function $(u,v)
\mapsto Cov(X_{u},X_{v})$. Indeed, one can recover the finite
dimensional means and covariances from these two functions.

Brownian stochastic integrals using deterministic integrands deliver
continuous time Gaussian processes. Assume the function $h(\cdot)$ on
$[0,\infty[$ is square integrable when restricted to $[0,t]$
($\int_{0}^{t}|h(u)|^{2}du<+\infty$). We can then define a
continuous Gaussian process through varying the end point $t$ of the
stochastic integral:$$\int_{0}^{t}h(u)dW_{u}.$$ This process is
obviously centered ($E[\int_{0}^{t}h(u)dW_{u}]=0$). It is also
Gaussian. When $h$ is a step function, it is a simple weighted sum
(with deterministic weights) of non overlapping (and thus independent)
Brownian increments. A square integrable function can be approximated in
the $L^{2}$ sense by step functions $h_{n}$ and it can be shown
that the limiting operation preserves the Gaussian nature of the
process[^2].

One can similarly define $\int_{-\infty}^{t}h(u)dW_{u}$ provided
$\int_{-\infty}^{t}|h(u)|^{2}du < +\infty$.

Ornstein-Uhlenbeck
==================

A process is stationary if the distribution of
$(X_{t+t_{1}},X_{t+t_{2}}\ldots,X_{t+t_{n}})$ is independent of
$t$ for all choices of $n$, $t$ and
$(t_{1},t_{2},\ldots,t_{n})$. Stationarity is invariance with
respect to time translations. The covariance function $(u,v) \mapsto
Cov(X_{u},X_{v})$ then only depends on $v-u$. A process is
Markovian if as of time $s$, all information regarding the future
trajectory of $X$ is contained in the value $X_{s}$. One does not
need to know more than the current value of $X$ to predict its future.

Markovianity and stationarity imply[^3] that
$cov(X_{s},X_{t})=a\exp(-b|t-s|)$ for positive constants $a$ and
$b$. This is the covariance function of the Ornstein Uhlenbeck which
can thus be described as the only stationary markovian Gaussian process
out there.

We can express the Ornstein Uhlenbeck process as Brownian integral. To
do so, we need recover this covariance function through a suitable
choice of $h$ in $\int_{-\infty}^{t}h(t,u)dW_{u}$ using:
$$cov(\int_{-\infty}^{s}h(s,u)dW_{u},\int_{-\infty}^{t}h(t,u)dW_{u})=\int_{-\infty}^{\min(s,t)}h(s,u)h(t,u)du.$$
Choosing $h(t,u)=\beta^{\frac{1}{2}}\exp(-\alpha (t-u))$ with
both $\beta$ and $\alpha$ strictly positive, we get:
$$\int_{-\infty}^{\min(s,t)}h(s,u)h(t,u)du=\frac{\beta}{2\alpha}\exp(-\alpha|t-s|).$$

We have thus defined a Gaussian stationary and markovian process
through:$$X_{t}=\int_{-\infty}^{t}\beta^{\frac{1}{2}}\exp(-\alpha
(t-u))dW_{u}.$$ This is a moving average representation of the random
variable $X_{t}$, which has mean $0$ and variance
$\beta/(2\alpha)$. From the moving average representation, it is
easy to establish that for $t \geq s$:
$$X_{t}=\exp(-\alpha(t-s))X_{s}+\int_{s}^{t}\beta^{\frac{1}{2}}\exp(-\alpha
(t-u))dW_{u}.$$ We can condition the process on $X_{0}=x$ in which
case we have: $$X_{t}=\exp(-\alpha t)x+\int_{0}^{t}
\beta^{\frac{1}{2}}\exp(-\alpha (t-u))dW_{u}.$$ We can thus
build a (non stationary) Ornstein Uhlenbeck process on
$\mathbb{R}_{+}$.

A useful martingale derived from $(X_{t})_{t \in \mathbb{r}_{+}}$
is $(\exp(\alpha t)X_{t})_{t \in \mathbb{r}_{+}}$. Indeed:
$$\exp(\alpha
t)X_{t}=X_{0}+\int_{0}^{t}\beta^{\frac{1}{2}}\exp(\alpha
u)dW_{u}.$$ In differential form, this gives: $$d(\exp(\alpha
t)X_{t})=\beta^{\frac{1}{2}}\exp(\alpha t)dW_{t},$$ or (ito):
$$\exp(\alpha t)dX_{t}+\alpha \exp(\alpha
t)X_{t}dt=\beta^{\frac{1}{2}}\exp(\alpha t)dW_{t},$$ i.e.:
$$dX_{t}=-\alpha X_{t}dt+\beta^{\frac{1}{2}}dW_{t},$$ which
is known as Langevin's equation.

One can change the mean of the Ornstein Uhlenbeck process. An Ornstein
Uhlenbeck process with mean $\mu$ is obtained from $X$ by setting
$Y_{t}=X_{t}+\mu$.

An Ornstein Uhlenbeck in one dimension is thus determined through three
parameters with the following interpretations:

-   $\sigma=\beta^{\frac{1}{2}}$ is the volatility of the process;
    it describes the elasticity of $X_{t}$ to the contemporaneous
    shock of the Brownian motion,
-   $\alpha$ is the speed of mean reversion of $(X_{t})_{t \in
    \mathbb{t}}$; $\alpha$ determines how persistent an impact a
    given shock $\beta^{\frac{1}{2}}dW_{u}$ has on the future
    trajectory of $(X_{t})_{t \in \mathbb{t}}$,
-   $\mu$ is the mean of $(X_{t})_{t \in \mathbb{t}}$.

Finally, the stationary distribution of an Ornstein Uhlenbeck process is
$N(\mu,(\beta/2\alpha )^{\frac{1}{2}})$

To complete this introduction, let's quote a relationship between the
Ornstein Uhlenbeck process and time changed Brownian processes (see this
[post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "quadratic variation and stochastic integration")).
To simplify the formulas, let's assume $\mu=0$. The case where
$\mu$ is different from $0$ is then immediate. We saw that
$(\exp(\alpha t)X_{t})_{t \in \mathbb{r}_{+}}$ is a continuous
martingale that can thus be expressed as a time changed Brownian motion.
To identify this time change, one starts from the idea that the time
changed Brownian motion should have the same quadratic variation as the
continuous martingale. We thus start by computing the latter:
$$[\beta^{\frac{1}{2}}\int_{0}^{\cdot}\exp(\alpha
u)dW_{u}]_{t}=\int_{0}^{t}\beta \exp(2\alpha
u)du=\frac{\beta}{2\alpha} \int_{0}^{t}d(\exp(2\alpha u))=$$
$$\frac{\beta}{2\alpha} \int_{0}^{\exp(2 \alpha t)}dv.$$ We
can thus find (see Kallenberg[2002], theorem 18.4) a new Brownian motion
$(B_{t})_{t \in \mathbb{r}_{+}}$ initialized at $0$ such that:
$$\beta^{\frac{1}{2}}\int_{0}^{t}\exp(\alpha
u)dW_{u}=(\frac{\beta}{2\alpha})^{1/2}\int_{0}^{\exp(2\alpha
t)}dB_{v}=(\frac{\beta}{2\alpha})^{1/2}B(\exp(2\alpha t)).$$ It
thus turns out that: $$\exp(\alpha t)X_{t}=(\beta/2\alpha
)^{\frac{1}{2}}B(\exp(2\alpha t)),$$ or:
$$X_{t}=(\beta/2\alpha )^{\frac{1}{2}}\exp(-\alpha
t)B(\exp(2\alpha t)).$$

Note: This note owes a lot to Kallenberg[2002], chapter 13.

References: Kallenberg, O., 2002, *Foundations of Modern Probability*,
Springer.


[^1]:  As a reminder, its density function is: $$f({\boldsymbol
    x})=(2\pi)^{-n/2}\det(\boldsymbol{\Sigma})^{-1/2}\exp(-\frac{1}{2}(\boldsymbol{x-\mu})^{t}\boldsymbol{\Sigma}^{-1}(\boldsymbol{(x-\mu})),$$
    and its characteristic function is:
    $$E(\exp(i\boldsymbol{u^{t}X}))=\exp(i\boldsymbol{u^{t}\mu}-\frac{1}{2}\boldsymbol{u^{t}\Sigma
    u}).$$ 

[^2]:  This proof requires a few steps. It hinges crucially on the fact
    that for fixed $t$, $\int_{0}^{t}h_{n}(u)dW_{u}$ converges
    to a Gaussian variable as $n$ tends to infinity. It also uses the
    fact that the process $(\int_{0}^{t}h(u)dW_{u})_{t \in
    \mathbb{T}}$ has independent increments - remember that for two
    non overlapping intervals
    $Cov(\int_{I}h(u)dW_{u},\int_{J}h(u)dW_{u})=0$ which implies
    that both integrals are independent since they have Gaussian
    distributions. 

[^3]:  See Kallenberg[2002], proposition $13.7$ p. 254. 
