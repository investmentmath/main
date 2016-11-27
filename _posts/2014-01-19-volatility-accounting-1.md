--- 
layout: post 
title: Volatility Accounting (1) 
author: Guillaume Rabault
categories: [Finance]
tags: [Volatility] 
fullview: false 
--- 

*In this post, I shed some light
on the volatility of the price process of a zero coupon equity contract.
The aim is to understand how the volatility of prospective expected
returns impacts the volatility of the price process. I derive under a
specific condition[^1] a simple accounting relationship linking
price volatility on one hand and cash flow as well as discount factor
volatility on the other hand. There is some empirical presumption that
markets exhibit excess volatility, i.e. that market prices are more
volatile than warranted by cash flow volatility. Under the afore
mentionned condition, this requires that discount rate shocks be
negatively correlated with cash flow shocks[^2].*

* * * * *

Accounting for volatility 
=========================

It was shown at the end of [this
post](/finance/2013/12/16/zero-coupon-contracts.html "ZERO COUPON CONTRACTS")
that the volatility of the price process $(P_{t})_{t \in [0,T]}$
was equal to that of the martingale $(Y_{t})_{t \in [0,T]}$ with
$Y_{t}=E_{t}[\exp(-\int_{0}^{T}r_{u}du)X_{T}]$. We want to
understand how this relates to the volatility of the fundamental
solution, i.e. the volatility of $(X_{t})_{t \in [0,T]}$ with
$X_{t}=E_{t}[X_{T}]$. To be clear, volatility is meant here as
the integrand of the stochastic integral in the *geometric*
representation of each process. For instance, the volatility of the
martingale $(X_{t})_{t \in [0,T]}$ is the process
$(\eta_{t})_{t \in [0,T]}$ such
that:$$\frac{dX_{t}}{X_{t}}=\eta_{t}dB_{t}.$$

We want to relate the volatility $Z$ of $P$, i.e. the volatility
of the martingale $Y$, with the volatility of the martingale $X$
and that of the martingale
$R=(E_{t}[\exp(-\int_{0}^{T}r_{u}du)])_{t \in [0,T]}$. By
definition, these martingales follow drift-less diffusions with the
relevant terminal conditions:

-   $X$: $dX_{t}=X_{t}\eta_{t}dB_{t}$, with terminal value
    $X_{T}$,
-   $R$: $dR_{t}=R_{t}\nu_{t}dB_{t}$, with terminal value
    $\exp(-\int_{0}^{T}r_{u}du)$,
-   $Y$: $dY_{t}=Y_{t}Z_{t}dB_{t}$, with terminal value
    $\exp(-\int_{0}^{T}r_{u}du)X_{T} \qquad (1)$ ,

Now the process $XR$ follows (Ito):
$$d(X_{t}R_{t})=X_{t}R_{t}\eta_{t}dB_{t}+X_{t}R_{t}\nu_{t}dB_{t}+X_{t}R_{t}\eta_{t}\nu_{t}dt$$
and has the same terminal condition as $(1)$. It does not define a
martingale given that the drift term is not equal to zero. It is
therefore not a solution to $(1)$. We can however easily modify this
process to solve $(1)$ when the following assumption holds:

**Assumption H:** *Both volatility processes $(\eta_{t})_{t \in
[0,T]}$ and $(\nu_{t})_{t \in [0,T]}$ are deterministic*

Indeed, consider the process
$W_{t}=X_{t}R_{t}\exp(-\int_{t}^{T}\eta_{u}\nu_{u}du)$
under this assumption. This is a well defined adapted process because
although all terms in the exponential relate to the future, they are
deterministic and therefore do not involve future shocks. The Ito rule
implies:$$dW_{t}=W_{t}(\eta_{t}+\nu_{t})dt,$$ and obviously we
have $W_{T}=X_{T}R_{T}=\exp(-\int_{0}^{T}r_{u}du)X_{T}$. We
have thus identified the martingale representation of $Y_{T}$ and
therefore the volatility process of P:$$Z_{t}=\eta_{t}+\nu_{t}.$$

**Proposition:** *Price volatility $Z_{t}$ is under **Assumption
H** the sum of fundamental volatility $\eta_{t}$ and discount
factor volatility $\nu_{t}$.*

The meaning of ‘discount factor volatility’ can be clarified further.
Discount factor volatility is the volatility $(\nu_{t})_{t \in
[0,T]}$ of $R$. It is tied to the integral
representation:$$\exp(-\int_{0}^{T}r_{u}du)=E_{0}[\exp(-\int_{0}^{T}r_{u}du)]+\int_{0}^{T}E_{u}[\exp(-\int_{0}^{T}r_{w}dw)]\nu_{u}du.$$
In addition, we have:
$$E_{t}[\exp(-\int_{0}^{T}r_{u}du)]=E_{0}[\exp(-\int_{0}^{T}r_{u}du)]+\int_{0}^{t}E_{u}[\exp(-\int_{0}^{T}r_{w}dw)]\nu_{u}du.$$
Injecting this identity in the above equation and dividing the result by
$\exp(-\int_{0}^{t}r_{w}dw)$, we get:
$$\exp(-\int_{t}^{T}r_{u}du)=E_{t}[\exp(-\int_{t}^{T}r_{u}du)]+\int_{t}^{T}E_{u}[\exp(-\int_{t}^{T}r_{w}dw)]\nu_{u}du$$
which is the martingale representation of
$\exp(-\int_{t}^{T}r_{u}du)$. It entails the volatility process
$(\nu_{u})_{u \in [t,T]}$. The quantity $\nu_{t}$ can thus
the be interpreted as the elasticity (the log derivative) of
$\exp(-\int_{t}^{T}r_{u}du)$ to the shock $dB_{t}$.

We saw in [this
post](/finance/2013/12/16/zero-coupon-contracts.html "ZERO COUPON CONTRACTS")
that the market price has the following representation:
$$P_{t}=E_{t}[\exp(-\int_{t}^{T}r_{u}du)X_{T}].$$ Intuitively,
this suggests that the elasticity of $P_{t}$ to $dB_{t}$
either arises from that of $X_{T}$ or from that of
$\exp(-\int_{t}^{T}r_{u}du)$. This thus turns out to be true
under **Assumption H**.

Excess volatility
=================

I assume now that fundamental volatility $\eta_{t}$ is positive.
This is just a normalization[^3] which ensures that positive
Brownian shocks raise the expectation of the terminal payoff. Given the
above proposition, we now have two polar cases:

-   If $\nu_{t}$ is positive, price volatility is greater than
    fundamental volatility $Z_{t}=\eta_{t}+\nu_{t} \geq
    \eta_{t}$. This requires that a positive cash flow shock raises
    the prospective discount factor
    $\exp(-\int_{t}^{T}r_{u}du)$, i.e. lowers the cumulated
    prospective return.

-   If $\nu_{t}$ is negative, price volatility is lower than
    fundamental volatility $Z_{t}=\eta_{t}+\nu_{t} \leq
    \eta_{t}$. This requires that a positive cash flow shock lowers
    the prospective discount factor
    $\exp(-\int_{t}^{T}r_{u}du)$, i.e. raises the cumulated
    prospective return.

The former situation is called excess volatility. A story rationalizing
excess volatility is as follows. When negative cash flow news hits the
market, the price of the fundamental solution falls to reflect the lower
cash flows. Yet this also spooks investors who require a greater
expected return on the contract to hold it. The prospective return
therefore rises and this amplifies the price move downwards. The reverse
effect occurs on the upside.


[^1]:  Deterministic volatilies (**see Assumption H**). A later post will
    extend the volatility identity to a more general
    context.

[^2]:  Although natural, this condition is not strictly equivalent to
    excess volatility. This will be detailed in a later
    post.

[^3]:  If $\eta_{t}$ was negative, we would just redefine the
    underlying Brownian to be $W=-B$. This change of sign preserves
    the Brownian property.
