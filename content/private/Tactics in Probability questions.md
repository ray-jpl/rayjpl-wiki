---
title: "Tactics in Probability questions"
enableToc: true
tags:
- Probability
---
## "At least" questions
When you are asked to calculate that some random variable is "at least" some value you can take the complement and this can be easier in some cases.
$$P(X\geq x)=1-P(X<x)$$
>[!note] Remark
>For a **continuous** distribution, $P(X\leq x)=P(x<x)$ is called the Cumulative Distribution function and is given by
>$$\int_{-\infty}^{x}f(t)dt=F(x)$$


>[!question] Example - Dice
>What is the probability we roll 2 dice and roll at least a 4?

**Solution**
$$\begin{eqnarray}
P(X\geq 4)&=&1-P(X<4)\\
&=& 1-P(X=2)-P(X=3)\\
&=& 1-[1/36 + 2/36]\\
&=& 11/12
\end{eqnarray}$$

## "Fair Value" questions
When encountered with questions such as “What is the fair value?” or “What would you be willing to pay to play this game?”, we use an **expected value**. The idea behind this is that by applying the expected value (or the mean as some call it), we can see the average amount of money that we will gain by playing the game. For example, if we find that a game $X$ has $E(X) = 4$, it means we would gain 4 on average by playing this game, and so, the break-even point would be to pay 4 to play this game. In that case, we would not win nor gain anything, on average. Also keep in mind, that you should be willing to pay anything less than the expected value to gain a profit. So if we gain $4 on average, and if we also paid $3 to play the game, we win $1. If you specify that to the interview, they will see you know how to gain profit.

## Conditional Probability questions
For these question just remember [[private/Conditional Probability#Bayes Theorem|Bayes Theorem]]. When you see that you are given certain information, setup this formula and begin to crunch the three components necessary.

## Telling the difference between combinatorics scenarios
![[files/combinatronics.png]]
For repetitions it may be better to think of Relevant and Irrelevant as Yes and No respectively. So for the top row $n^k$ when repetitions are required and $^{n}P_k$ when repetitions cannot be used.  
See more at details at [[private/Combinatorics|Combinatorics]]

## References
- Paris Kastanias - Quantsoc Workshop