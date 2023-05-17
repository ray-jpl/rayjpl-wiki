---
title: "Binomial Distribution"
enableToc: true
tags:
- Binomial Distribution
- Probability Distributions
---
>[!note] Definition
>A binomial distribution is a discrete probability distribution that is used for n trials in which there are only binary outcomes. We use the formula:
>$$f(x; n, p) = {n\choose x} p^x (1 − p)^{n-x}$$
>where p is the probability and $x \in \{1,2,3,...,n\}$

>[!question] Example - Biased Coin
>Suppose we flip a biased coin 10 times. This coin has a 0.3 probability of landing on tails. 
>(a) What is the probability we flip exactly 2 heads? 
>(b) What is the probability that the only 2 heads we flip are the first 2 heads? 
>(c) What is the probability that the only 2 heads we flip are the last 2 heads?

**Solution**
a) The probability to flip exactly 2 heads for this biased coin is 
$$\begin{eqnarray}
f(x;10,0.7) &=& {{10} \choose {2}}\times 0.7^2\times(0.3)^8\\
&=& 0.0014\\
\end{eqnarray}$$
Multiply by $n \choose k$ to account for all combinations of 2 heads to get total probability.

b) The probability of getting two heads on the first two flips is the same as the probability of getting 2 heads on any specific flips. $$0.7^2\times 0.3^8=0.00003$$
c) Answer is the same as b).

