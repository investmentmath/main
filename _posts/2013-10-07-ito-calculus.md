--- 
layout: post 
title: Ito Calculus 
author: Guillaume Rabault
categories: [Math] 
tags: [Ito]
fullview: false 
--- 

*This post introduces the Ito rule of stochastic
calculus. This rule provides the semimartingale decomposition of a
nonlinear (this being the non trivial case) function of given
semimartingales. Its simplest incarnation is the product rule of
stochastic calculus which gives the semimartingale decomposition of the
product of two given semimartingales.*

* * * * *

Ito calculus for simple polynomial expressions
==============================================

All semimartingales considered below are assumed continuous.

In [this
post](/math/2013/05/29/quadratic-variation-and-stochastic-integration.html "QUADRATIC VARIATION AND STOCHASTIC INTEGRATION")
(I will use the same notation), we established the following algebraic
identity :
$$X_{t}^{2}-X_{0}^{2}=\sum_{i=1}^{k}2X_{t_{i-1}}(X_{t_{i}}-X_{t_{i-1}})+\sum_{i=1}^{k}(X_{t_{i}}-X_{t_{i-1}})^{2},$$
along a grid $\pi_{[0,t]}$ satisfying $t_{0}=0 ,t_{k}=t$.
Applying the polarization identity[^1] we can derive :
$$X_{t}Y_{t}-X_{0}Y_{0}=\sum_{i=1}^{k}Y_{t_{i-1}}(X_{t_{i}}-X_{t_{i-1}})+\sum_{i=1}^{k}X_{t_{i-1}}(Y_{t_{i}}-Y_{t_{i-1}})+$$
$$\sum_{i=1}^{k}(X_{t_{i}}-X_{t_{i-1}})(Y_{t_{i}}-Y_{t_{i-1}}).$$
We will concentrate on this last relationship since it contains the
other one as a special case.

The terms on the right hand side have the following behavior as a
function of the nature of $(X_{t})_{t \in [0,T]}$ when the grid
gets refined:

-   If $(X_{t})_{t \in [0,T]}$ and $(Y_{t})_{t \in [0,T]}$ are
    continuous local martingales, the last term converges to the cross
    variation $([X,Y]_{t})_{t \in [0,T]}$ and the other terms
    converge to stochastic integrals. We have :
    $$X_{t}Y_{t}-X_{0}Y_{0}=\int_{0}^{t}X_{u}dY_{u}+\int_{0}^{t}Y_{u}dX_{u}+[X,Y]_{t}.
    \tag{1}$$
-   If $(X_{t})_{t \in [0,T]}$ and $(Y_{t})_{t \in [0,T]}$ are
    continuous bounded variation processes, the last term converges
    to[^2] $0$ and the first two terms converge towards the
    obvious Lebesgue Stieltjes integrals. Thus :
    $$X_{t}Y_{t}-X_{0}Y_{0}=\int_{0}^{t}X_{u}dY_{u}+\int_{0}^{t}Y_{u}dX_{u}.
    \tag{2}$$

We can also study what happens when one of the process is a local
continuous martingale, say $(X_{t})_{t \in [0,T]}$ while the other
one, say $(Y_{t})_{t \in [0,T]}$, is continuous bounded variation
process. In this case, on can make use the following identity :
$$X_{t}Y_{t}-X_{0}Y_{0}=\sum_{i=1}^{k}X_{t_{i}}(Y_{t_{i}}-Y_{t_{i-1}})+\sum_{i=1}^{k}Y_{t_{i-1}}(X_{t_{i}}-X_{t_{i-1}}).$$
The dominated convergence theorem of Lebesgue Stieltjes integration
shows that the first term converges to the Lebesgue Stieltjes
integral[^3] $(\int_{0}^{t}X_{u}dY_{u})_{t \in [0,T]}$
while the second term, as usual, converges to the stochastic integral
$(\int_{0}^{t}Y_{u}dX_{u})_{t \in [0,T]}$. We thus get :
$$X_{t}Y_{t}-X_{0}Y_{0}=\int_{0}^{t}X_{u}dY_{u}+\int_{0}^{t}Y_{u}dX_{u}.
\tag{3}$$

It is convenient to summarize these results in differential notation.
The logic of the notation, illustrated on the product $X_{t}Y_{t}$
of two local martingales, is as follows. We write
$X_{t}Y_{t}-X_{0}Y_{0}=\int_{0}^{t}d (X_{u}Y_{u})$.
Similarly,
$[X,Y]_{t}=[X,Y]_{t}-[X,Y]_{0}=\int_{0}^{t}d[X,Y]_{u}$. We can
then write equation $(1)$ as : $$d (X_{u}Y_{u})=X_{u}d
Y_{u}+Y_{u}d X_{u}+d[X,Y]_{u}.$$ We can wrap up the cases we saw
as follows :

-   $(X_{t})_{t \in [0,T]}$ and $(Y_{t})_{t \in [0,T]}$ are
    local martingales : $$d (X_{u}Y_{u})=X_{u}d Y_{u}+Y_{u}d
    X_{u}+d[X,Y]_{u} \qquad (\text{equation}\,1).$$
-   $(X_{t})_{t \in [0,T]}$ and $(Y_{t})_{t \in [0,T]}$ are of
    bounded variation : $$d (X_{u}Y_{u})=X_{u}d Y_{u}+Y_{u}d
    X_{u} \qquad (\text{equation}\,2).$$
-   $(X_{t})_{t \in [0,T]}$ is of bounded variation and
    $(Y_{t})_{t \in [0,T]}$ is a local martingale : $$d
    (X_{u}Y_{u})=X_{u}d Y_{u}+Y_{u}d X_{u} \qquad
    (\text{equation}\,3).$$.

In the special case where $X$ is equal to $Y$, we have :

-   $(X_{t})_{t \in [0,T]}$ is a local martingale :
    $dX^{2}_{u}=2X_{u}dX_{u}+d[X]_{u}$.
-   $(X_{t})_{t \in [0,T]}$ is of bounded variation :
    $dX^{2}_{u}=2X_{u}dX_{u}$.

From product rules to Ito calculus
==================================

We now consider two continuous semimartingales $(X_{t})_{t \in
[0,T]}$ and $(Y_{t})_{t \in [0,T]}$ with their decompositions :
$$X_{t}=M_{t}+A_{t},$$ $$Y_{t}=N_{t}+B_{t},$$ into their
local continuous martingale component ($(M_{t})_{t \in [0,T]}$ and
$(N_{t})_{t \in [0,T]}$) and their continuous bounded variation
process ($(A_{t})_{t \in [0,T]}$ and $(B_{t})_{t \in [0,T]}$).
We can write : $$d (X_{u}Y_{u})=X_{u}d Y_{u}+Y_{u}d
X_{u}+d[X,Y]_{u}$$ $$=X_{u}d B_{u}+Y_{u}d A_{u}+X_{u}d
N_{u}+Y_{u}d M_{u}+d[X,Y]_{u},$$ with $[X,Y]_{u}=[M,N]_{u}$.
We note that if $X$ or $Y$ is actually a bounded variation process,
then $[X,Y]_{u}=0$.

This decomposition of $d(X_{u}Y_{u})$ is actually the semimartingale
decomposition of $(X_{t}Y_{t})_{\in [0,T]}$ into its local
martingale component :$$\int_{0}^{t}X_{u}d
N_{u}+\int_{0}^{t}Y_{u}d M_{u},$$ and its finite variation
component : $$\int_{0}^{t}X_{u}d B_{u}+\int_{0}^{t}Y_{u}d
A_{u}+[X,Y]_{t}.$$ We can thus compute $d(X_{u}Y_{u}Z_{u})$ for
a third semimartingale $(Z_{t})_{t \in [0,T]}$ by considering the
product of the three semimartingale $X_{u}Y_{u}Z_{u}$ as a product
of two semimartingales $(X_{u}Y_{u})Z_{u}$. This remark leads to
consider the differential of polynomial functions of a set of underlying
semimartingales.

One can show by recurrence along the above lines that for any polynomial
expression $F(X_{1,u},X_{2,u},\ldots,X_{n,u})$ in $n$
semimartingales, we have : $$dF(X_{1,u},\ldots,X_{n,u})=
\sum_{i}F^{\prime}_{i}(X_{1,u},\ldots,X_{n,u})dX_{i,u}+$$
$$\frac{1}{2}\sum_{i,j}F^{\prime\prime}_{i,j}(X_{1,u},\ldots,X_{n,u})d[X_{i},X_{j}]_{u}.$$
The reader can check that this works for all simple polynomials
considered in the first section, and that if it works for two polynomial
expressions, it works for their product.

What then remains to be seen is whether this can be applied to general
twice continuously differentiable functions. This is indeed the case.
The key step in the proof of this result consists in restricting the
semimartingales to compact subspaces through localization, and then
approximate the function with polynomials. In a compact domain, a twice
continuously differentiable function together with its first and second
derivatives can be arbitrarily closely approximated (in the sense of
uniform convergence) by a polynomial.

To conclude, let's state Ito's formula precisely :

**Theorem (Ito's Formula):** *Consider $n$ continuous semimartingales
$(X_{1,t},\ldots,X_{n,t})$ with $t$ in $[0,T]$ and a twice
continuously differentiable function of $n$ variables $F:
\mathbb{R}^{n}\rightarrow \mathbb{R}$. Then we have with
probability one for all $u$ in
$[0,T]$:$$dF(X_{1,u},\ldots,X_{n,u})=
\sum_{i}F'_{i}(X_{1,u},\ldots,X_{n,u})dX_{i,u}+$$
$$\frac{1}{2}\sum_{i,j}F^{\prime\prime}_{i,j}(X_{1,u},\ldots,X_{n,u})d[X_{i},X_{j}]_{u},$$
or in integral form, for all $t$ in $[0,T]$:
$$F(X_{1,t},\ldots,X_{n,t})-F(X_{1,0},\ldots,X_{n,0})=
\sum_{i}\int_{0}^{t}F'_{i}(X_{1,u},\ldots,X_{n,u})dX_{i,u}+$$
$$\frac{1}{2}\sum_{i,j}\int_{0}^{t}F^{\prime\prime}_{i,j}(X_{1,u},\ldots,X_{n,u})d[X_{i},X_{j}]_{u}.$$*

${\scriptstyle \blacksquare}$

 

This theorem singles out the semimartingale decomposition of the process
$(F(X_{1,t},\ldots,X_{n,t}))_{t \in [0,T]}$. If we decompose each
semimartingale $(X_{i,t})_{t \in [0,T]}$ into its bounded variation
component $(A_{i,t})_{t \in [0,T]}$ and its local martingale
component $(M_{i,t})_{t \in [0,T]}$, then the bounded variation
component of $(F(X_{1,t},\ldots,X_{n,t}))_{t \in [0,T]}$ is :
$$
\sum_{i}\int_{0}^{t}F'_{i}(X_{1,u},\ldots,X_{n,u})dA_{i,u}+\frac{1}{2}\sum_{i,j}\int_{0}^{t}F^{\prime\prime}_{i,j}(X_{1,u},\ldots,X_{n,u})d[X_{i},X_{j}]_{u},$$
while the local martingale component is: $$
\sum_{i}\int_{0}^{t}F'_{i}(X_{1,u},\ldots,X_{n,u})dM_{i,u}.$$

Note : This post takes its inspiration from section IV.32 of
Rogers[2000].

Reference: Rogers L.C.G. and D. Williams[2000] : *Diffusions,Markov
Processes and Martingales, Vol 2, Ito Calculus*, Cambridge University
Press.


[^1]:  $ab=\frac{1}{4}[(a+b)^{2}-(a-b)^{2}]$. 

[^2]:  The cross variation of two bounded variation functions is zero. This
    can easily be deduced from the fact that the quadratic variation of
    each process is null and using the Cauchy Schwartz inequality.
 

[^3]:  In Lebesgue Stieltjes integration, the sums
    $\sum_{i=1}^{k}X_{t_{i}}(Y_{t_{i}}-Y_{t_{i-1}})$ and
    $\sum_{i=1}^{k}X_{t_{i-1}}(Y_{t_{i}}-Y_{t_{i-1}})$
    converge to the same result, the integral
    $\int_{0}^{t}X_{u}dY_{u}$. Within stochastic integration,
    i.e. when $(Y_{t})_{t \in [0,T]}$ is a local martingale, the
    two sums differ. The second expression converges to the Ito integral
    $\int_{0}^{t}X_{u}dY_{u}$ while the first converges to
    $\int_{0}^{t}X_{u}dY_{u}+[X,Y]_{t}$. The Stratonovitch
    integral is defined as the limit of the average of the two weighted
    sums, namely
    $\int_{0}^{t}X_{u}dY_{u}+\frac{1}{2}[X,Y]_{t}$.
 
