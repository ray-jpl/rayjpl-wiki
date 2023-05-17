---
title: "Conditional Probability"
enableToc: true
tags:
- Probability
- Conditional Probability
---
## Conditional Probability
>[!note] Definition
>Conditional Probability is defined as the following
>$$\begin{eqnarray}
>P(A|B) &=& \frac{P(A\cap B)}{P(B)}\\
>&=& \frac{P(B|A)P(A)}{P(B)}\\
>\end{eqnarray}$$
>We call $A|B$, "A given B". Given that the event B will occur, what is the probvability that $A$ will occur.
>The reason we divide by the probability of $B$ is because if $B$ has occured then it is the new sample space

Visit [[private/Set Operations|Set Operations]] if you need a refresher.

>[!question] Example - Prime numbers dice
>Suppose we roll dice and wish to find the expected value of their sum. Furthermore, suppose both of the numbers we roll are prime numbers. Denote this experiment as the random variable $X$. 
>(a) Find $P(X ≥ 8)$. 
>(b) Find $E(X)$.

**Solution**
(A) The prime numbers possible on a dice are {2,3,5}. Hence, to roll an 8 or above, we need the rolls to be a pair of either {3,5}, {5,3} or {5,5}. Denote $B$ as rolling the prime numbers and denote $Y$ as the sum of two normal dice. Hence $X=Y|B$. 
($X$ is the sum of the two dice role($Y$) given that both are prime numbers($B$)).

$$P(Y|B >= 8) = \frac{P(B|Y>=8) P(Y>=8)}{P(B)}$$
Now $P(B|Y ≥ 8)$ is the probability that we rolled two prime numbers given the sum of the dice was 8, 9, 10, 11 or 12. 
The ways we could have rolled 8 is (2, 6),(3, 5),(4, 4),(5, 3),(6, 2). 
The ways we could have rolled 9 is (3, 6),(4, 5),(5, 4),(6, 3). 
The ways we could have rolled 10 is (4, 6),(5, 5),(6, 4). 
The ways we could have rolled 11 is (5, 6),(6, 5). 
The ways we could have rolled 12 is (6, 6). 
In total there are 15 outcomes possible, and only 3 of them have both of the numbers as primes. Hence, $P(B|Y ≥ 8) = \frac {1}{5}$

$P(Y ≥ 8)$ is the probability we roll 2 normal dice and the sum is 8 or higher. To make this easier, we will refer to the previous information. Hence, there are 36 outcomes in total, and 15 have a sum of 8 or more. Hence, $P(Y ≥ 8) = \frac {15}{36}$.

$P(B)$ is the probability that we roll two prime numbers. As there are three prime numbers {2,3,5}, there are 9 ways we can roll both prices. Therefore $P(B) = \frac{9}{36} = \frac{1}{4}$

$$\begin{eqnarray}
P(Y|B >= 8) &=& \frac{\frac{1}{5}\cdot \frac{15}{36}}{\frac{1}{4}}\\
&=& \frac{1}{3}
\end{eqnarray}$$
(B) $E(X)$ is the expected value of two die rolls where both are prime numbers. As the only possible results for each roll is {2,3,5}, 
$$\begin{eqnarray}
E(X) &=& 2[\frac{1}{3}\times 2 + \frac{1}{3}\times3+\frac{1}{3}\times 5]\\
&=& \frac{2}{3}[2+3+5]\\
&=& \frac{20}{3}\\
\end{eqnarray}$$