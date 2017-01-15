--- 
layout: post 
title: Complete Markets, Discrete Time
author: Guillaume Rabault
categories: [Ensae] 
tags: [Completeness] 
fullview: false 
--- 

*In this post, I present the so-called martingale method in a complete market setup where the time scale is discrete and the probability space is discrete as well. In the absence of arbitrage, there is a strictly positive stochastic discount factor (SDF) and a risk neutral measure can be defined. The market is said to be complete if any consumption stream which is adapted to the underlying filtration can be traded using the available financial instruments. If this is the case, the SDF and the risk neutral measure are both unique. A portfolio optimization problem without labour income is defined. Despite the dynamic context, the maximization problem is essentially static. The gradient of the utility function has to be proportional to the SDF, and the optimal plan is found by varying the coefficient of proportionality to satisfy the intertemporal budget constraint. The optimal consumption plan is thus in principal easily derived. The corresponding portfolio policy has to be identified in a second step however.* 

* * * * *

## Single period SDF and risk neutral probabilities

* What follows should be read after [this post](/ensae/2014/11/16/complete.html).

* Here, I drop the tildas on random variables to avoid overloading the notation.

* The general ideas presented in the static case can be applied to the dynamic case. The easiest extension assumes a discrete time scale and a discrete probability space represented by a tree of events.

* Let the set of time indices be $\{0,1,\ldots,T\}$. If there is no arbitrage, one can define strictly positive discount factors $z_{t+1}$ such that all pay-offs $x_{\theta_{t},t+1}$ of an investment policy $\theta_{t}$ are priced according to:
$$p_{\theta_{t},t}=E_{t}[z_{t+1}x_{\theta_{t},t+1}].$$

* In the absence of arbitrage, the discount factor is strictly positive and we can define risk neutral probabilities with derivative:
$$\psi_{t+1}=R^{f}_{t+1}z_{t+1},$$
($E_{t}[\psi_{t+1}]=1$) so that for any $x$ that is ${\cal F}_{t}$ measurable:
$$E_{t}[\psi_{t+1}x]=\tilde{E}_{t}[x].$$

* Under this new measure:
$$p_{\theta_{t},t}=\tilde{E}_{t}\left[\frac{x_{\theta_{t},t+1}}{R^{f}_{t+1}}\right]=\frac{\tilde{E}_{t}\left[x_{\theta_{t},t+1}\right]}{R^{f}_{t+1}}.$$

## Multiperiod SDF

* One can telescope the period by period discount factors by defining: 
$$m_{t}=z_{1}z_{2}\cdots z_{t}\; (t \geq 1),$$
$$m_{0}=1.$$

* Considering a self-financed trading rule $\theta[t,t+1]=\{\theta_{t},\theta_{t+1}\}$ defined over the time interval $[t,t+1]$, and assuming that it leads to a pay-off in $t+2$ only, one can write using the rules regarding conditional expectations:
$$p_{\theta_{t+1},t+1}=E_{t+1}[z_{t+2}x_{\theta_{t+1},t+2}],$$
$$p_{\theta_{t+1},t}=E_{t}[z_{t+1}p_{\theta_{t+1},t+1}]=E_{t}[E_{t+1}[z_{t+1}z_{t+2}x_{\theta_{t+1},t+2}]],$$
$$p_{\theta_{t+1},t}=E_{t}[z_{t+1}z_{t+2}x_{\theta_{t+1},t+2}],$$
$$m_{t}p_{\theta_{t+1},t}=E_{t}[m_{t+2}x_{\theta_{t+1},t+2}].$$

* When the self-financed trading policy $\theta[t,T]=\{\theta_{t},\ldots,\theta_{T}\}$ leads to pay-offs that accrue at different times, $\{x_{t+1},\ldots,x_{T}\}$, we just have to sum their discounted values:
$$m_{t}p_{\theta_{t},t}=E_{t}[\sum_{k=t+1}^{T}m_{k}x_{k}].$$


## Multiperiod risk neutral probabilities

* If we collapse all Radon-Nikodym derivatives into:
$$\Psi_{t}=\psi_{1} \cdots \psi_{t}\; (t \geq 1),$$
$$\Psi_{0}=1.$$

obviously:
$$E_{0}[\Psi_{t}]=1,$$
and:
$$E_{t}[\Psi_{T}]=\Psi_{t}.$$


* We can define for an ${\cal F}_{T}$ random variable $X$:
$$\tilde{E}_{0}[X]=E_{0}[\Psi_{T}X],$$
and for conditional expectations:
$$\tilde{E}_{0}[X|{\cal F}_{t}]=E_{t}[X]=\frac{E_{0}[\Psi_{T}X|{\cal F}_{t}]}{E_{0}[\Psi_{T}|{\cal F}_{t}]}=\frac{E_{t}[\Psi_{T}X]}{E_{t}[\Psi_{T}]}
=\frac{E_{t}[\Psi_{T}X]}{\Psi_{t}}.$$

* Note that we recover the one step ahead risk neutral derivatives. As above, we have:
$$p_{\theta_{t},t}=E_{t}[\psi_{t+1}\frac{x_{\theta_{t},t+1}}{R^{f}_{t+1}}]=\tilde{E}_{t}[\frac{x_{\theta_{t},t+1}}{R^{f}_{t+1}}],$$
and more generally for $\theta[t,t+1]=\{\theta_{t},\theta_{t+1}\}$ delivering a pay-off in $t+2$ as above:
$$p_{\theta_{t+1},t}=E_{t}[\frac{m_{t+2}}{m_{t}}x_{\theta_{t+1},t+2}]=\tilde{E}_{t}[\frac{x_{\theta_{t+1},t+2}}{R^{f}_{t+1}R^{f}_{t+2}}].$$

* Similarly, when the self-financed trading policy $\theta[t,T]=\{\theta_{t},\ldots,\theta_{T}\}$ leads to pay-offs that accrue at different times, $\{x_{t+1},\ldots,x_{T}\}$, we just have to sum the risk neutral expectations of discounted values with discount rates being risk free discount rates:
$$p_{\theta_{t},t}=\tilde{E}_{t}\left[\sum_{k=t+1}^{T}\frac{x_{k}}{\Pi_{q=t+1}^{k}R^{f}_{q}}\right].$$

* To simplify the notation, we can write:
$$B_{t,k}=\Pi_{q=t+1}^{k}R^{f}_{q}.$$
This is the amount generated at date $k$ by investing $1$ dollar at date $t$. Using this we can rewrite the intertemporal budget constraint above as:
$$p_{\theta_{t},t}=\tilde{E}_{t}\left[\sum_{k=t+1}^{T}B_{t,k}^{-1}x_{k}\right].$$

* One can paraphrase this as saying that the price is the risk neutral expectation of cash flows expressed using the cash account as the numeraire.

* Suppose we consider an asset that does not distribute dividends. We initiate an investment in the cash account at date $0$ and this delivers a cash amount $B_{0,t}$ at date $t$. Expressing the price of the asset in terms of the cash account, we thus define the discounted price:
$$\tilde{P}_{t}=\frac{P_{t}}{B_{0,t}}.$$
We have, using risk neutral probabilities:
$$P_{0}=\tilde{P}_{0}=\tilde{E}_{0}[\tilde{P}_{t}].$$  
Similarly:
$$P_{t}=\tilde{E}_{t}[B_{t,T}^{-1}{P}_{T}],$$
and thus (multiplying the equation by $B_{0,t}^{-1}$):
$$\tilde{P}_{t}=\tilde{E}_{t}[\tilde{P}_{T}].$$
We thus see that discounted prices follow a martingale process.  

* As a consequence, wealth also follows a martingale process.

## Intertemporal budget constraints

* The budget constraints records the way wealth evolves over time along a trajectory of returns (assuming no income and no consumption):
$$W_{t+1}=W_{t}\pi_{t}'R_{T+1}.$$

* Multiplying both sides by $m_{t+1}$, taking expectations and using the relationship between the SDF and returns, we get:
$$E_{t}[m_{t+1}W_{t+1}]=m_{t}W_{t}.$$

* Similarly, in the presence of consumption and income, the budget constraint trajectory by trajectory:
$$W_{t+1}+C_{t}\pi_{t}'R_{T+1}=W_{t}\pi_{t}'R_{T+1}+Y_{t+1},$$
leads to:
$$E_{t}[m_{t+1}W_{t+1}]+m_{t}C_{t}=m_{t}W_{t}+E_{t}[m_{t+1}Y_{t+1}].$$

* Over a sequence $\{t,t+1,\cdots,T\}$ of periods : 
$$\sum_{k=t}^{T-1}E_{t}[m_{k}C_{k}]+E_{t}[m_{T}W_{T}]=m_{t}W_{t}+\sum_{k=t+1}^{T}E_{t}[m_{k}Y_{k}].$$

* Similarly, one can write the above relationships using risk-neutral probabilities instead of the SDF: 
$$\sum_{k=t}^{T-1}\tilde{E}_{t}[B_{t,k}^{-1}C_{k}]+\tilde{E}_{t}[B_{t,T}^{-1}W_{T}]=m_{t}W_{t}+\sum_{k=t+1}^{T}\tilde{E}_{t}[B_{t,k}^{-1}Y_{k}].$$

## Complete markets


* We restrict the problem to a set of times $[0,T]$. We have a fitration ${\cal F}_{T}$ and as usual random processes considered are supposed to be adapted to that filtration.  

* In the static case, completeness meant that the traded assets allowed to synthesize all Arrow-Debreu securities. One can then transfer wealth exclusively to any state of nature. There needs to be as many traded assets as there are states of nature, and the matrix of pay-offs needs to have full rank.

* In this context, any pay-off function $\tilde{x}(\cdot)$ from the set of states of nature to $\mathbb{R}_{+}$ can be obtained as the pay-off of a portfolio.

* In our dynamic context, we say that the market is complete if any pay-off $C_{t}$ (a function from the states of nature of time $t$ to $\mathbb{R}_{+}$) for any $t \in [1,T]$ can be obtained as the pay-off of a given trading policy. In particular, we need to be able to synthesize all Arrow Debreu securities of all dates $t \in [1,T]$.

* In a market without arbitrage, there is at least one strictly positive SDF and therefore one risk neutral probability measure. If markets are complete, there is necessarily only one SDF and only one risk neutral measure. 

* Indeed, consider the price of the Arrow Debreu security $e_{t,k}$ that pays $1$ in state $\omega_{t,k}$ of date $t$ is:
$$P_{0,e_{t,k}}=E_{0}[m_{t}(\omega_{t,k})]=p_{0}(\omega_{t,k})m_{t}(\omega_{t,k}),$$
where $p_{0}(\omega_{t,k})$ is the probability as seen from date $0$ of state $\omega_{t,k}$.
Thus, the value of the SDF is fixed by probabilities as of time $0$ and time $0$ prices.

## The martingale method

* In a general context, checking that a certain consumption stream over $[0,T]$ can be finance by trading involves a complex investigation of the structure that markets impose through the intertemporal budget constraint to the ability to transfer wealth across time and states of nature.

* In a complete market, there is no limit to the ability to transfer wealth. All consumption streams are tradables. In the end thus, whether a certain consumption stream can be financed is just a matter of having enough wealth at time $0$. This is true regardless of whether we receive income or not.

* In what follows, I assume as a simplification that there is no income. 

* In the complete market case, the feasibility of a consumption stream is encapsulated in the budget constraint:
$$\sum_{t=0}^{T}E_{0}[m_{t}C_{t}]+E_{0}[m_{T}W_{T}]=m_{0}W_{0}.$$

* Whereas this equation necessarily holds in incomplete markets, a consumption stream that satisfies this equation is not 
necessarily actually feasible. One would indeed need to verify that a trading strategy using available assets can finance the consumption stream.. In a complete market, the existence of such a trading strategy is ensured.

* The structure of a complete markets portfolio optimization problem is as follows: we maximize a utility function under a constraint which is defined by a linear functional on the consumption function. This is entirely analogous to the static multigood consumption problem of traditional microeconomic theory and we can therefore say that the optimization problem is static.

* We assumption that the optimization problem is:
$$\underset{(C_{0},\ldots,C_{T})}{\text{max}}
\; E_{0}[\sum_{t=0}^{T} \delta^{t}u_{t}(C_{t})],$$
subject to:
$$W_{0}=\sum_{t=0}^{T}E_{0}[m_{t}C_{t}],$$
assuming $u_{t}(\cdot)$ has range $\mathbb{R}_{+}^{*}$ and is strictly increasing and concave, with $u_{t}^{\prime}$ ranging from $+\infty$ to $0$ as consumption varies in $\mathbb{R}_{+}^{*}$.


* The command is the set of consumption values for all times and states of nature. This is a finite set of numbers since we assume discrete time, a finite horizon and a discrete probability state. The system is solved as usual using the Lagrangian, the first order condition being:
$$\delta^{t}u_{t}'(C_{t}(\omega_{t,k}))=\lambda m_{t}(\omega_{t,k}).$$

* As in the static case, we can thus take:
$$C_{t}(\omega_{t,k})=u_{t}^{\prime -1}(\lambda \delta^{-t} m_{t}(\omega_{t,k})),$$
and one picks the value of $\lambda$ which implies that the budget constraint is satisfied.

## Conclusion

* Completeness (and absence of arbitrage) thus implies that the optimization problem is static. It can be solved under the right technical assumption as in the two period case, and as in the standard microeconomic multi-good consumption problem.

* The key point is that the gradient of the utility function has to be, at the optimum, proportional to the unique SDF.

* To apply this in practice, one needs to set up a complete market model such as the binomial model for stock prices.

* Note that the solution directly gives the consumption function. How the consumption plan is practically financed requires a separate investigation. What we know is that it can be financed for sure.

* One could describe the optimization process using the risk neutral measure instead of the SDF. Because under this measure, the properly discounted wealth process (i.e. discounted using the cash account) is a martingale, this method is usually called the martingale method.





