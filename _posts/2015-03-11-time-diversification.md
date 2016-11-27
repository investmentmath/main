--- 
layout: post 
title: Allocating risk across periods
author: Guillaume Rabault
categories: [Finance] 
tags: [Diversification] 
fullview: false 
--- 

*In the cross section, portfolio returns are a weighted sum of securities' returns. This opens up the door to diversification gains when returns are imperfectly correlated. Optimal diversification is reached when the independent underlying factors are weighted proportionately to their prospective Sharpe ratios. It is perhaps less well known that the same principle holds across periods. When returns are independent from one period to another (the benchmark case), efficiency requires that the risk budget be allocated proportionately to the prospective Sharpe ratio of the period. This leads to constant volatility strategies, when the portfolio's Sharpe ratio is constant over time. Constant volatility strategies can be contrasted with policies which hold the weight of the risky asset constant. The latter are efficient when the incentive to invest is proportional to volatility. Choosing between the two types of policies requires an empirical investigation of the link between volatility and the prospective Sharpe ratio.*

* * * * *

## Discrete time

In this paragraph, I consider an investor who has access to a risky asset and to cash. The risky asset provides a Sharpe ratio which I take to be constant $\lambda>0$ in a first step. I assume that its return distribution is lognormal, with volatility $\sigma_{t}$. I assume volatility changes with time but is deterministic. I also assume that the cash rate $r^{f}$ is constant (this is just a simplification). The dynamics of the risky asset is spelled out in discrete time:
$$\frac{P_{t+1}}{P_{t}}=\exp(r^{f}+\sigma_{t+1}\lambda+\sigma_{t+1}\epsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2}),$$
where the shocks $(\epsilon_{t})$ are i.i.d., normally distributed ${\cal N}(0,1)$.

If the proportion allocated to the risky asset is $\pi_{t}$, the portfolio return between date $t$ and date $t+1$ is:
$$\frac{W_{t+1}}{W_{t}}=\exp(r^{f}+\pi_{t}\sigma_{t+1}\lambda+\pi_{t}\sigma_{t+1}\epsilon_{t+1}-\frac{1}{2}\pi_{t}^{2}\sigma_{t+1}^{2}).$$
The cumulated change in wealth from date $0$ to date $T$ is:
$$\frac{W_{T}}{W_{0}}=\exp\left(r^{f}T+\sum_{k=0}^{T-1}\pi_{k}\sigma_{k+1}\lambda+\sum_{k=0}^{T-1}\pi_{k}\sigma_{k+1}\epsilon_{k+1}-\frac{1}{2}\sum_{k=0}^{T-1}\pi_{k}^{2}\sigma_{k+1}^{2}\right).$$

The expected cumulated change in wealth is:
$$E_{0}\left[\frac{W_{T}}{W_{0}}\right]=\exp\left(r^{f}T+\sum_{k=0}^{T-1}\pi_{k}\sigma_{k+1}\lambda\right),$$
since:
$$E_{t}\left[\exp\left(\sigma_{t+1}\epsilon_{t+1}-\frac{1}{2}\sigma_{t+1}^{2}\right)\right]=1,$$
and $r^{f}$, $\sigma_{t}$ and $\lambda$ are deterministic.
The variance of the cumulated return is that of the lognormal variable:
$$\exp\left(\sum_{k=0}^{T-1}\pi_{k}\sigma_{k+1}\epsilon_{k+1}-\frac{1}{2}\sum_{k=0}^{T-1}\pi_{k}^{2}\sigma_{k+1}^{2}\right).$$

In the context of a holding interval $[0,T]$, a portfolio will be efficient for a given expected return if it minimizes variance while controlling the return $\mu_{p}$, i.e. (the factor $1/2$ is included to simplify the lagrangian):
$$\underset{(\pi_{k})_{k=0,\ldots,T-1}}{\text{min}} \; \frac{1}{2}\sum_{k=0}^{T-1}\pi_{k}^{2}\sigma_{k+1}^{2}$$
$$\text{s.t.}: \;\; r^{f}+\sum_{k=0}^{T-1}\pi_{k}\sigma_{k+1}\lambda=\mu_{p}.$$
The expected return $\mu_{p}$ is assumed to exceed the cumulated cash return. The first order condition of this constrained optimization program is:
$$\pi_{k}\sigma_{k+1}=\gamma\lambda,$$
where $\gamma$ is a positive constant ($\lambda>0)$ i.e. the risk budget should be equal in all periods.

Given that the incentive to take risk is constant, risk is minimized when the risk budget is evenly spread across periods. This result is the counterpart in the time dimension of the cross sectional rule that says that if the covariance matrix is diagonal and Sharpe ratios equal across securities, risk budgets should be equalized. The constrained optimization problem has exactly the same form as above in this case.

It is easy to introduce a time varying deterministic Sharpe ratio, in which case the condition becomes:
$$\pi_{k}\sigma_{k+1}=\gamma\lambda_{k},$$
where $\lambda_{k}$ is the incentive to take exposure to the shock $\epsilon_{k+1}$.
It is useful to think of this equation as saying that the investment policy is such that the sensitivities to the shocks are proportional (with a common constant of proportionality) to the Sharpe ratio of each shock. 

We have thus seen that efficiency in the time dimension can be analyzed as efficiency in the cross sectional dimension, provided the covariance matrix is properly mapped from one problem to another. We now want to mix the time and cross sectional dimensions in a single problem. To be able to do so, we have to move to continuous time.

## Continuous time

The weighted average of two lognormal processes is not a lognormal process (unless one of them is constant, as above). As a consequence, we cannot introduce several risky assets and preserve log-normality. In continuous time, this problem disappears. We can thus consider a set of $N$ risky assets following diffusion processes:
$$\frac{dP_{i,t}}{P_{i,t}}=r^{f}dt+\sigma_{i,t}\lambda_{t}+\sigma_{i,t}dB_{t}.$$
We have an $N$ dimensional Brownian motion $(B_{t})$ with covariance matrix equal to the identity and $\sigma_{i,t}$ is an $(1,N)$ matrix os sensitivities. The $(N,N)$ matrix $\sigma_{t}$ obtained by stacking the rows $(1,N)$ is assumed to be invertible. It is such that $\Sigma_{t}=\sigma_{t}^{\prime}\sigma_{t}$ is the covariance matrix of the risky assets. All quantities above are assumed to be deterministic.

If $\pi_{t}$ is the $(N,1)$ vector of risky asset weights, the wealth process is such that:
$$\frac{W_{T}}{W_{0}}=\exp\left(r^{f}T+\int_{0}^{T}\pi_{u}'\sigma_{u}\lambda_{u} du+\int_{0}^{T}\pi_{u}'\sigma_{u}dB_{u}-\frac{1}{2}\int_{0}^{T}\pi_{u}'\Sigma_{u}\pi_{u}du\right).$$

As in the discrete time case, the expected cumulated return is:
$$E_{0}\left[\frac{W_{T}}{W_{0}}\right]=\exp\left(r^{f}T+\int_{0}^{T}\pi_{u}'\sigma_{u}\lambda_{u} du\right).$$
The variance of the cumulated return is that of the lognormal variable:
$$\exp\left(\int_{0}^{T}\pi_{u}'\sigma_{u}dB_{u}-\frac{1}{2}\int_{0}^{T}\pi_{u}'\Sigma_{u}\pi_{u}du\right).$$
Efficient portfolios can be found through solving:
$$\underset{(\pi_{u})_{u \in [0,T]}}{\text{min}} \; \frac{1}{2}\int_{0}^{T}\pi_{u}'\Sigma_{u}\pi_{u}du$$
$$\text{s.t.}: \;\; \int_{0}^{T}\pi_{u}'\sigma_{u}\lambda_{u} du=\mu_{p}.$$

No constraints apply to the collection of risky asset portfolios. The first order condition of the problem is:
$$\Sigma_{u}\pi_{u}=\gamma\sigma_{u}\lambda_{u},$$
or multiplying by $\sigma_{u}^{-1}$ on both sides:
$$\sigma_{u}'\pi_{u}=\gamma\lambda_{u}.$$
This condition entails $N$ equations, one for each component of the Brownian motion. Each equation stipulates that at a given point in time, the sensitivity to the infinitesimal shock over the next infinitesimal period is proportionate to its specific Sharpe ratio. However, these conditions also hold across periods with the same constant of proportionality.

There is thus one single proportionality condition in the cross sectional and in the time dimension, once the shocks affecting the portfolio are arranged so as to form an orthogonal set. In our case, the different Brownian motions are orthogonal to one another and of course, increments of the Brownian motions pertaining to different time intervals are orthogonal as well. Variance is naturally additive in the time dimension. It is additive in the cross sectional dimension as well if one works with orthogonal factors as opposed to the original correlated assets. 

Finally, let's just note that:
$$\Sigma_{u}\pi_{u}=\gamma\sigma_{u}\lambda_{u},$$
implies:
$$\sqrt{\pi_{u}'\Sigma_{u}\pi_{u}}=\gamma\frac{\pi_{u}'\sigma_{u}\lambda_{u}}{\sqrt{\pi_{u}'\Sigma_{u}\pi_{u}}},$$
or:
$$\sigma_{p,u}=\gamma\lambda_{p,u}.$$
This gives the relationship between portfolio risk and its prospective Sharpe ratio.


## Constant volatility strategies and constant proportion strategies

Constant volatility strategies (CVS) obtain from the above analysis when the portfolio's prospective Sharpe ratio is constant over time. Constant volatility strategies rebalance so as to keep their risk budget constant. This is a response to constant incentives to invest. The relevance of constant volatility strategies hinges on the assumption of a constant incentive to invest. It is clear that if volatility and expected returns do not move in locksteps so as to keep the prospective Sharpe ratio constant, they lose their relevance.   

Constant volatility strategies are an alternative to strategies which hold the risky asset weight constant. The risk budget consumed by the constant asset weight strategy (CAWS) is $\omega \sigma_{t}$ where $\omega$ is the chosen proportion. CAWS is efficient if the prospective Sharpe ratio is proportional to volatility. 

In the end, choosing between CVS and CAWS requires an empirical investigation of the correlation between the prospective Sharpe ratio and volatility.
