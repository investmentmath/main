--- 
layout: post 
title: Solutions to Exercises 
author: Guillaume Rabault
categories: [Ensae] 
tags: [Solutions] 
fullview: false 
--- 

*This post collects the solutions to [the exercises](/ensae/2015/10/15/exercises.html) of the ENSAE course.*

* * * * *

## Mean-Variance


### Exercise 1

* If you find the following difficult, solve the problem in the context of a single risky asset.

1.

* ${\cal I}=\{1,2,\ldots,N\}$ (no riskless asset).

* $\pmb{\pi}=(\pi_{i})_{i \in \cal{I}}'$
$$\underset{\pmb{\pi}}{\text{max}} \; E[-\exp(-\alpha \tilde{w})]$$
$$\text{s.t.}:$$
$$\tilde{w}=w_{0}\sum_{i \in \cal{I}}\pi_{i}\tilde{R}_{i}$$ 
$$\sum_{i \in \cal{I}}\pi_{i}=1,$$
with $\alpha>0$.


* We have: $E[-\exp(-\alpha\tilde{w})]  =\; -\exp(-\alpha E[\tilde{w}]+(\alpha^{2}/2)V[\tilde{w}]).$
We can thus maximize $E[\tilde{w}]-(\alpha/2)V[\tilde{w}]$.

* This function is decreasing in wealth when wealth is large. The investor therefore does not benefit of being wealthier beyond a certain point.

* The criterion can be written:
$$w_{0}\pmb{\pi}'\pmb{\mu}-(\alpha/2)w_{0}^{2}\pmb{\pi}'\Sigma\pmb{\pi},$$
where $\pmb{\mu}$ is the expected return vector and $\Sigma$ is the covariance matrix.

* Assuming as usual that $\Sigma$ is positive definite and the criterion is strictly concave.

* In the absence of a budget constraint, we can choose $w_{0}=1$ and leave the vector of weights unconstrained. The first order condition characterizes the solution. It is:
$$\pmb{\mu}=\alpha \Sigma \pmb{\pi},$$
$$\pmb{\pi}=\frac{1}{\alpha}\Sigma^{-1}\pmb{\mu}.$$

* The total wealth needed to reach the optimum is:
$$\pmb{e}'\pmb{\pi}=\frac{1}{\alpha}\pmb{e}'\Sigma^{-1}\pmb{\mu}.$$
Any additional wealth is useless.

2.

* We now start from an initial wealth level $w_{0}>0$ and impose that the vector of weights sum to $1$.
$$\underset{\pmb{\pi}}{\text{max}} \; \pmb{\pi}'\pmb{\mu}-(\alpha/2)w_{0}\pmb{\pi}'\Sigma\pmb{\pi}$$
$$\text{s.t.}:$$
$$\pmb{e}'\pmb{\pi}=1.$$ 

* The lagrangian can be written:
$$\pmb{\pi}'\pmb{\mu}-(\alpha/2)w_{0}\pmb{\pi}'\Sigma\pmb{\pi}-\lambda(\pmb{\pi}'\pmb{e}-1),$$
and the first order condition:
$$\pmb{\mu}-\alpha w_{0}\Sigma\pmb{\pi}-\lambda\pmb{e}=0,$$

* The langrangian multiplier is given by (multiply the first order condition on the right by $\pmb{\pi}'$):
$$\lambda=\pmb{\pi}'\pmb{\mu}-\alpha w_{0}\pmb{\pi}'\Sigma\pmb{\pi}.$$

* The solution splits as follows:
$$w_{0}\pmb{\pi}=\frac{1}{\alpha}\Sigma^{-1}\pmb{\mu}-\frac{\lambda}{\alpha}\Sigma^{-1}\pmb{e}.$$
The first term corresponds to the optimal unconstrained solution of question $1$. The second term ensures that what the whole wealth 
is invested.

* We have:
$$w_{0}=\frac{1}{\alpha}\pmb{e}'\Sigma^{-1}\pmb{\mu}-\frac{\lambda}{\alpha}\pmb{e}'\Sigma^{-1}\pmb{e}.$$

* For $\lambda>0$, $w_{0}$ is below the optimal wealth level of question $1$. For $\lambda<0$, $w_{0}$ is above the optimal wealth level of question $1$. Since the budget constraint prevents from throwing money away, too much is invested when $\lambda<0$.  

* We know that the utility outcome is measured by:
$$w_{0}\pmb{\pi}'\pmb{\mu}-(\alpha/2)w_{0}^{2}\pmb{\pi}'\Sigma\pmb{\pi}.$$
An infinitesimal increase in wealth has an inmpact on utility measured through (using the envelope theorem - one can neglect the infinitesimal change in the optimal portfolio as we change wealth infinitesimally - differentiate with respect to $w_{0}$):
$$\pmb{\pi}'\pmb{\mu}-\alpha w_{0}\pmb{\pi}'\Sigma\pmb{\pi},$$
which is just $\lambda$. Therefore when $\lambda<0$ indeed, the marginal utility of wealth is negative. This is due to the fact that the utility function decreases beyond a certain level of wealth.

3. 

* In the presence of cash, we know that we can parameterize the optimization problem using the risky asset weights. The optimization is unconstrained and the cash position is deduced from the budget constraint. The risky asset weight solves the problem of question $1$ with $\mu-r^{f}$ in place of $\mu$. The residual amount of wealth (positive if wealth is high, negative if wealth is low) is invested in the riskless asset. The level of investment in the risky assets is always optimal (i.e. as in question $1$ up to the substitution of $\mu-r^{f}$ for $\mu$).


### Exercise 2

* See the notebook, which directly applies the formulas in the section on static optimization.

3. 

* The tangent portfolio is:
$$\pmb{\pi_{*}}=\frac{1}{\pmb{e}'\Sigma^{-1}(\pmb{\mu}-r^{f}\pmb{e})}\Sigma^{-1}(\pmb{\mu}-r^{f}\pmb{e}),$$
while the solution for the given utility function is:
$$\pmb{\pi_{\rho}}=\frac{1}{\rho}\Sigma^{-1}(\pmb{\mu}-r^{f}\pmb{e}).$$
Thus the value of $\rho$ that delivers the tangent portfolio is just:
$$\rho_{*}=\pmb{e}'\Sigma^{-1}(\pmb{\mu}-r^{f}\pmb{e}).$$

5. 

* The risky asset portfolios along the efficient frontier are all proportional to the tangent portfolio. The proportions across risky assets are thus constant along the efficient frontier. As we move towards more volatile portfolios, efficient portfolios borrow cash to finance positions in risky assets. If borrowing is ruled out, the risky asset positions need to change. The efficient frontier cannot be linear beyond the point where cash borrowing kicks in. Positions in the most volatile risky asset (equities in our case) needs to be financed through lower positions on the least volatile risky asset (in our case bonds). The proportion of bonds to equities falls as we increase volatility.

* The no borrowing constraint does not impact safe portfolios.

6. 

* The efficient proportion of bonds to equities is at least four to one. This holds if bonds are quite attractive relatively to equities. You can play with the program to find specific parameters that match this situation.  


### Exercise 4
1.

* The first order condition is:
$$\pmb{\pi_{\rho}}=\frac{1}{\rho}\Sigma^{-1}(\pmb{\mu}-r^{f}\pmb{e}),$$
which can also be written:
$$\Sigma\pmb{\pi_{\rho}}=\frac{1}{\rho}(\pmb{\mu}-r^{f}\pmb{e}).$$
We therefore have:
$$\pmb{\pi_{\rho}}'\Sigma\pmb{\pi_{\rho}}=\frac{1}{\rho}\pmb{\pi_{\rho}}'(\pmb{\mu}-r^{f}\pmb{e}).$$
$$\sigma_{\rho}=\frac{1}{\rho}\frac{\pmb{\pi_{\rho}}'(\pmb{\mu}-r^{f}\pmb{e})}{\sigma_{\rho}}=\frac{1}{\rho}\lambda_{\rho}.$$
with $\sigma_{\rho}$ being the volatility of the optimal portfolio and $\lambda_{\rho}$ its sharpe ratio.

* We remind that $\lambda_{\rho}$ is independent of $\rho$. It is given by the Sharpe ratio of the tangent portfolio.

2. 

* We have:
$$\mu_{\rho}=\lambda\sigma_{\rho}=\rho\sigma_{\rho}^{2}.$$
In the $(\sigma,\mu)$ space, the locus of optimal portfolios attached to a given $\rho$, as we vary the Sharpe ratio $\lambda$, is a parabola.  


### Exercise 5

1.

* Because the support of $\tilde{R}_{1}$ has $0$ as its lower bound, wealth invested in the risky asset in period $0$ can can lead to nothing in period $1$. The minimum amount of wealth needed to obtain $\underline{w}_{1}$ in period is:
$$\underline{w}_{0}=\frac{\underline{w}_{1}}{R^{f}}.$$

2.

* According to question $1$, at least $\underline{w}_{0}$ should be invested in the riskless asset. Thus nothing more than $w_{0}-\underline{w}_{0}$ can be invested in the risky asset. This quantity (the surplus) can be split into the fraction invested in the risky asset and the remaining fraction invested in the riskless asset. Thus the transfer of wealth obeys:
$$w_{1}=\underline{w}_{0}R^{f}+(w_{0}-\underline{w}_{0})(1-\pi_{0})R^{f}+(w_{0}-\underline{w}_{0})\pi_{0}\tilde{R}_{1},$$  
or given that $\underline{w}_{0}R^{f}=\underline{w}_{1}$:
$$w_{1}-\underline{w}_{1}=(w_{0}-\underline{w}_{0})(R^{f}+\pi_{0}(\tilde{R}_{1}-R^{f})).$$  

* To see that $\pi_{0}$ should be positive or zero, note that because the return $\tilde{R}_{1}$ can be arbitrarily large, going short the risky asset can wipe out any level of wealth.

3.


* We have:

    * the budget constraint expressed as a function of the surplus is geometric. Multiplying the initial surplus $w_{0}-\underline{w}_{0}$ by $\lambda$ leaving the proportion $\pi_{0}$ unchanged leads to $\lambda$ times $w_{1}-\underline{w}_{1}$ as the final surplus: 
$$\lambda (w_{1}-\underline{w}_{1})=\lambda (w_{0}-\underline{w}_{0})(R^{f}+\pi_{0}(\tilde{R}_{1}-R^{f})).$$  

    * the set of feasible investment policies does not depend on the initial surplus.

    * for a given investment policy $\pi_{0}$, if $U(w_{0}-\underline{w}_{0},\pi_{0})$ is the utility level reached starting from a surplus $w_{0}-\underline{w}_{0}$, the utility level reached starting from $\lambda(w_{0}-\underline{w}_{0})$ is $U(\lambda(w_{0}-\underline{w}_{0}),\pi_{0})=\lambda^{1-\rho}U(w_{0}-\underline{w}_{0},\pi_{0})$.

* These facts imply that the value function $V(w_{0}-\underline{w}_{0})$ is homogenous of degree $1-\rho$ in the surplus. Indeed, if $V(\lambda (w_{0}-\underline{w}_{0}))>\lambda^{1-\rho}V(w_{0}-\underline{w}_{0})$, then using the optimal choice for the initial condition $\lambda (w_{0}-\underline{w}_{0})$, one can achieve the value:
$$\frac{1}{\lambda^{1-\rho}} V(\lambda (w_{0}-\underline{w}_{0}))>V(w_{0}-\underline{w}_{0}),$$
for the utility level reached from the initial conditon $w_{0}-\underline{w}_{0}$. This is a contradiction. Similarly:
$$V(\lambda (w_{0}-\underline{w}_{0}))<\lambda^{1-\rho}V(w_{0}-\underline{w}_{0}),$$
would lead to a contradiction.

* The optimal program for the initial condition $w_{0}-\underline{w}_{0}=1$ is:
$$V(1)=\underset{\pi_{0}}{\text{max}} \; E[\frac{1}{1-\rho}(R^{f}+\pi_{0}(\tilde{R}_{1}-R^{f}))^{1-\rho}]$$
$$\text{s.t.}:$$
$$0 \leq \pi_{0} \leq 1,$$
and the solution does not depend on the initial condition.

4. 

* We know from the previous questions that in the two period case, the value function in date $0$ reads:
$$V_{T-1}(1)(w_{0}-\underline{w}_{0})^{1-\rho}.$$ 
Note that $V_{T-1}(1)$ has the same sign as $1-\rho$.

* We can extend the reasoning by recurrence using the dynamic programming principle, and we therefore obtain that the value function at any date $t$ reads:
$$V_{t}(1)(w_{0}-\underline{w}_{0})^{1-\rho}.$$ 
The optimal command is given by:
$$\underset{\pi_{t}}{\text{max}} \; E[V_{t+1}(1)(R^{f}+\pi_{0}(\tilde{R}_{1}-R^{f}))^{1-\rho}]$$
$$\text{s.t.}:$$
$$0 \leq \pi_{t} \leq 1.$$
This gives the same result for every date $t$ (we have i.i.d. risky asset returns and a constant cash rate).

### Exercise 7

1. 

* For $t \in (t_{i},t_{i+1}]$ and $t' \in (t_{k},t_{k+1}]$ (I assume $k>i+1$, the case where $k=i+1$ follows similar lines):
$$M_{t'}=\int_{0}^{t'}h(u)dB_{u}=\sum_{j=1}^{i-1}F_{j}(B_{t_{j}}-B_{t_{j+1}})+F_{t_{i}}(B_{t}-B_{t_{i}})+$$
$$F_{t_{i}}(B_{t_{i+1}}-B_{t})+\sum_{j=i+1}^{k-1}F_{j}(B_{t_{j}}-B_{t_{j+1}})+F_{t_{k}}(B_{t'}-B_{t_{k}}).$$

* Using the properties of the Brownian motion, we have:
$$E_{t}[M_{t'}]=E_{t}[\sum_{j=1}^{i-1}F_{j}(B_{t_{j}}-B_{t_{j+1}})+F_{t_{i}}(B_{t}-B_{t_{i}})]=M_{t}.$$
This says that the stochastic integral of a simple process is a martingale.

2. 

* For the left hand side, one just needs to develop $M_{t}^2$ and use the fact that:
$$E_{0}[F_{t_{k}}(B_{t_{k+1}}-B_{t_{k}})F_{t_{j}}(B_{t_{j+1}}-B_{t_{j}})]=0,$$
when intervals $[t_{k},t_{k+1}]$ and $[t_{j},t_{j+1}]$ don't overlap while:
$$E_{0}[F_{t_{k}}^{2}(B_{t_{k+1}}-B_{t_{k}})^{2}]=E_{0}[F_{t_{k}}^{2}(t_{k+1}-t_{k})].$$

* For the right-hand side:
$$h(t)=\sum_{i=1}^{n}F_{i}^{2}{\bf 1}_{(t_{i},t_{i+1}]},$$
so that:
$$\int_{0}^{t}h(u)^{2}du=\sum_{j=1}^{i-1}F_{j}^{2}(t_{j+1}-t_{j})+F_{t_{i}}^{2}(t-t_{i}).$$ 

* Identification is then immediate.

3. 

* We have ($t' \geq t$):
$$\int_{0}^{t'}h(u)dB_{u}=\int_{0}^{t}h(u)dB_{u}+\int_{t}^{t'}h(u)dB_{u},$$
and:
$$E_{t}[|\int_{0}^{t'}h(u)dB_{u}|^{2}]=|\int_{0}^{t}h(u)dB_{u}|^{2}+E_{t}[|\int_{t}^{t'}h(u)dB_{u}|^{2}],$$
as the expectation of the cross-product vanishes.

* Similarly:
$$\int_{0}^{t'}h(u)^{2}du=\int_{0}^{t}h(u)^{2}du+\int_{t}^{t'}h(u)^{2}du,$$
and:
$$E_{t}[\int_{0}^{t'}h(u)^{2}du]=\int_{0}^{t}h(u)^{2}du+E_{t}[\int_{t}^{t'}h(u)^{2}du].$$

* Then we can proceed as in $2$ to get:
$$E_{t}[|\int_{t}^{t'}h(u)dB_{u}|^{2}]-E_{t}[\int_{t}^{t'}h(u)^{2}du]=0,$$
so that:
$$E_{t}[|\int_{0}^{t'}h(u)dB_{u}|^{2}]-E_{t}[\int_{0}^{t'}h(u)^{2}du]=|\int_{0}^{t}h(u)dB_{u}|^{2}-\int_{0}^{t}h(u)^{2}du,$$
which is what we needed to establish.

4.

* Because $E_{0}[M_{t}]=0$, the variance of $M_{t}$ (as seen from date $0$) is $E_{0}[M_{t}^{2}]$ which is equal to $E_{0}[[M]_{t}]$, i.e. the expectation
of the quadratic variation. When quadratic variation is deterministic, it is equal to the variance (as seen from date $0$) of $M_{t}$. 


### Exercise 8

1. 

* We just need to apply Ito to $\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}$. The exponential is a finite variation process and the Ito boils down to the standard differential formula in this case:
$$d\left(\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}\right)=d\left(\exp\left(-\int_{0}^{t}r_{u}du\right)\right)P_{t}^{T}+\exp\left(-\int_{0}^{t}r_{u}du\right)d(P_{t}^{T}),$$
$$=-\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}r_{t}dt+\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}r_{t}dt+
\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}\sigma_{t}^{T}dB_{t}.$$
$$=\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}\sigma_{t}^{T}dB_{t}.$$

* Thus $\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}$ is a martingale.

2. 

* We therefore have:
$$\exp\left(-\int_{0}^{t}r_{u}du\right)P_{t}^{T}=E_{t}\left[\exp\left(-\int_{0}^{T}r_{u}du\right)P_{T}^{T}\right]$$
$$=E_{t}\left[\exp\left(-\int_{0}^{T}r_{u}du\right)\right].$$
Therefore:
$$P_{t}^{T}=E_{t}\left[\exp\left(-\int_{t}^{T}r_{u}du\right)\right].$$

3. 

* Differentiate $\exp(\rho t)r_{t}$:
$$d\left(\exp(\rho t)(r_{t}-\bar{r})\right)=\rho\exp(\rho t)(r_{t}-\bar{r})dt-\rho\exp(\rho t)(r_{t}-\bar{r})dt+\exp(\rho t)\sigma_{r}dB_{t}.$$
$$=\exp(\rho t)\sigma_{r}dB_{t}.$$
Therefore:
$$\exp(\rho t)(r_{t}-\bar{r})-(r_{0}-\bar{r})=\int_{0}^{t}\exp(\rho u)\sigma_{r}dB_{u},$$
$$r_{t}-\bar{r}=\exp(-\rho t)(r_{0}-\bar{r})+\int_{0}^{t}\exp(-\rho (t-u))\sigma_{r}dB_{u}.$$

4.

* One needs to integrate the above equation written between $t$ and $u>t$ instead on $0$ and $t$. Integrating the term $\exp(-\rho t)(r_{0}-\bar{r})$ leads to: $(r_{t}-\bar{r})b(T-t)$ where:
$$b(T-t)=\int_{t}^{T}\exp(-\rho(u-t))du=-\frac{1}{\rho}[\exp(-\rho(u-t))]_{u=t}^{u=T}=\frac{1-\exp(-\rho(T-t))}{\rho}.$$

* One then applies Fubini to the following double integral:
$$\int_{t}^{T}\left(\int_{t}^{u}\exp(-\rho (u-v))\sigma_{r}dB_{v}\right)du=\int_{t}^{T}\left(\int_{v}^{T}\exp(-\rho (u-v))du\right)\sigma_{r}dB_{v},$$
and observes that:
$$\int_{v}^{T}\exp(-\rho (u-v))du=b(T-v).$$
This gives the result.



5. 

* Write:
$$b(h-u)=\frac{1}{\rho^{2}}-\frac{1}{\rho^{2}}\exp(-\rho (h-u))-\frac{1}{\rho}\exp(-\rho (h-u))\frac{1}{\rho}(1-\exp(-\rho (h-u))),$$
and observe that:
$$-\frac{1}{\rho}\exp(-\rho (h-u))\frac{1}{\rho}(1-\exp(-\rho (h-u)))=\frac{1}{\rho}b_{u}'(h-u)b(h-u),$$
where $b_{u}'(h-u)$ is the $u$ derivative of $b(h-u)$.
The formula then follows by straitghtforward integration.

6.

* The variable $\int_{t}^{T}r_{u}du$ is Gaussian with mean $\bar{r}(T-t)+(r_{t}-\bar{r})b(T-t)$ and variance:
$$\int_{t}^{T}b(T-u)^{2}\sigma_{r}^{2}du.$$
Thus:
$$P_{t}^{T}=\exp\left(-\bar{r}(T-t)-(r_{t}-\bar{r})b(T-t)+\frac{\sigma_{r}^{2}}{2}\left(\int_{t}^{T}b(T-u)^{2}du\right)\right).$$

7. 

* Applying Ito to the above formula shows that the volatility of the price process is $\sigma_{r}b(T-t)$.

### Exercise 9

1. 

* Inserting $dB_{t}=dB^{Q}_{t}-\lambda dt$ into:
$$\frac{dP_{t}^{T}}{P_{t}^{T}}=(r_{t}+\sigma_{t}^{T}\lambda)dt+\sigma_{t}^{T}dB_{t},$$
we get:
$$\frac{dP_{t}^{T}}{P_{t}^{T}}=r_{t}dt+\sigma_{t}^{T}dB^{Q}_{t}.$$

2. 

* The SDE followed by the cash rate is:
$$dr_{t}=-\rho(r_{t}-\bar{r}+\frac{\lambda}{\rho})dt+\sigma_{r}dB^{Q}_{t},$$
i.e.:
$$dr_{t}=-\rho(r_{t}-\tilde{r})dt+\sigma_{r}dB^{Q}_{t},$$
with:
$$\tilde{r}=\bar{r}-\frac{\lambda}{\rho}.$$
Therefore, the mean cash rate has changed.

3.

* We now have:
$$P_{t}^{T}=E^{Q}_{t}\left[\exp\left(-\int_{t}^{T}r_{u}du\right)\right].$$

* The process $(B^{Q}_{t})$ is a Brownian motion. We can thus compute the price as in the previous exercise. This gives:
$$P_{t}^{T}=\exp\left(-\tilde{r}(T-t)-(r_{t}-\tilde{r})b(T-t)+\frac{\sigma_{r}^{2}}{2}\left(\int_{t}^{T}b(T-u)^{2}du\right)\right).$$

4. 

* Only the mean short rate has changed. Price volatility is unchanged.
























 

