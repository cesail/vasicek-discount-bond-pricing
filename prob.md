# Probability Set-up

$(C,B,P)$ forms a sigma algebra.
- $C$ sample space
- $B$ a collection of subsets of $C$, called events; we have $C\in B$.
- If $\{A_n\}$ is a collection of events, each of which a subset of $C$, then $\cup A_n$ is also in $B$, i.e., also an event.
- If $A\in B$ (i.e. $A$ is an event), then $A^c=C\setminus A$ is also in $B$ (i.e., also an event).
- $P$ is a probability measure. 
  1. $P(C)=1$ 
  2. Given $\{A_n\}$ mutually disjoint events, $P(\cup A_n)=\sum P(A_n)$

## Random Variable 

> pdf of X is denoted by $f_X$: $f_X(x)=Prob(X=x)$

> cdf of X is denoted by $F_X$: $$F_X(a)=Prob(X\leq a)=\int^a_{-\infty} f_X(x)dx$$
> $$F_X(a)=Prob(X\leq a)=\sum_{x\leq a} f_X(x) (\text{discrete case}$$


> $$Ver(X+Y) = E[(x+y-E[x+y])^2]$$ 
> $$=Ver(x)+Ver(y)-2(E[xy]+E[x]E[y])$$

> $Cov(x,y)=E[xy]+E[x]E[y]$

> If x=y (have the same distribution?), then $Cov(x,y)=Var(x).$
>
> If x,y are independent, then $E[xy]=E[x]E[y]$, so $cov(x,y)=0,\,var(x+y)=var(x)+var(y).$


For any real number $a$ we have $$var(ax)=E[a^2x^2]-E[ax]^2=a^2E[x]$$ and $var(x+a)=var(x)$

### Example 1. Bernoulli
Given $x\sim Bernoulli(p)$ we have $x^n\sim Bernoulli(p)$ and the moment generating  function $$E[e^{tx}]=1-p+pe^t.$$

If $x,y$ are independent then $e^{tx},e^{ty}$ are also independent, so $$E[e^{tx+ty}]=E[e^{tx}]E[e^{ty}],$$ i.e. $m_{x+y}(t)=m_x(t)m_y(t).$

### Example 2. Binomial
$x\sim Binomial(n,p),$ then $m_x(t)=(1-p+pe^t)^n$.

### Example 3. Sum of independent variables with identical distribution
Take $x_1,...,x_n,...$ to be a sequence of independent variables with identical distribution, i.e. $x_i\sim x$. Let $\mu=E[x]$ and $\sigma=\sigma_x$. Let $y_n=\frac{x_1+...+x_n-n\mu}{\sigma\sqrt{n}}$. Then we have $$E[y_n]=0,$$ $$var(y_n)=1.$$
The moment generating function is $$m_{y_n}(t)=\left(m_{x-\mu}(\frac{t}{\sigma\sqrt{n}})\right)^n.$$ Let's take $n\to \infty$. To understand $\lim_{n\to \infty} m_{y_n}$ we take the $\log$ to get $\lim_{n\to\infty} n \ln(m_{x-\mu}(\frac{t}{\sigma\sqrt{n}})).$  But $$m_{x-\mu}(\frac{t}{\sigma\sqrt{n}})=1+\frac{t^2}{2n}+O(n^{-3/2}).$$ Let $z$ be the nonconstant part in this sum, then from the expansion of $\ln(1+z)$ we get $$\ln(m_{x-\mu}(\frac{t}{\sigma\sqrt{n}}))$$ approaches $t^2/2$ as $n\to \infty.$ Therefore, $$\lim_{n\to\infty}m_{y_n}(t)=\exp(t^2/2).$$

### Central limit theorem 

$$\lim_{n\to \infty} y_n \sim \mathcal{N}(0,1)$$ if $var(x_i)=var(x_j)<\infty.$

### Log normal distribution

Fix $\mu,\,\sigma$ in $\mathbb{R}$. A variable $x$ is log-normal if $x\sim \exp(\mu+\sigma\mathcal{N}(0,1)).$ Then $$e^{-\mu} E[x]=E[\exp{\sigma\mathcal{N}(0,1)}]=e^{\sigma^2/2}.$$ Taking $\mu=-\sigma^2/2$ we get $E[x]=1.$