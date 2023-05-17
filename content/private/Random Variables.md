---
title: "Random Variables"
enableToc: true
tags:
- Random Variables
---

## Random Variable
>[!note] Definition
 A random variable is a quantity that we wish to measure. It varies depending on the outcome of an event.
* We usually denote them with capital letters, such as X and Y
- Some examples include measuring things like how many customers walk into a grocery store within an hour, or how much profit I expect to make through trading

It is important to not confuse
- $X$, the name of the random variable
- $X(ω)$, the numerical value taken by the random variable at some sample point $ω$
- $x$, a generic numerical value


>[!question] Example
>Let $X$ denote the sum of the roll of two fair dice. Find $P(X = 8)$.

**Solution**
We are being asked to find the probability that we roll two dice and the sum is 8. The possible ways it can occur is by rolling any of the following pairs: (2, 6),(3, 5),(4, 4),(5, 3),(6, 2). Hence, $P(X = 8) = \frac{5}{36}$ .

## Expectation of a random variable
>[!note] Definiton
>The expectation of a random variable $X$ is denoted as $E(X)$. It is defined by a weighted average of the possible values that $X$ can take on, more specifically,
$$E(X)=\sum_{i}^{n}p_ix_i$$
where $p_i$ is the probability of the outcome $i$ occuring, and $x_i$ is the value that $X$ takes on when outcome $i$ occurs.
>

>[!question] Example
>You plan to sell a stock tomorrow that is currently worth $100.
>There is a 50% chance it moves to $170 when you sell.
>There is a 30% chance it moves to $60 when you sell.
>There is a 20% chance it moves to $90 when you sell.
>Find the expected value of the profit you make when you sell tomorrow.

**Solution**
We define X as the profit we make whhen we sell. We know $x_1 = 70, x_2 = -40$ and $x_3 = -10$. We also know $p_1 = 0.5, p_2 = 0.3$ and $p_3 = 0.2$. Therefore
$$\begin{eqnarray}  
E(X) &=& \sum_{i}^{3}p_ix_i\\  
&=& (0.5\times70) + (0.3\times-40)+(0.2\times-10)\\
&=& 21  
\end{eqnarray}$$

#### Expectation is linear
Expectation is a linear function. This means that $$E(aX+bY) = aE(X)+bE(Y)$$where $a,b$ are constants and $X,Y$ are random variables.

>[!question] Example - 10 Cards Problem
>Suppose there is a game where there are 10 cards, each labelled 1 to 10. A dealer then shuffles these cards and randomly flips 5 of them face up onto a table. You win the sum of the numbers on those 5 cards. How much money are you willing to pay to play this game?

**Solution**
Let $X$ be a random variable denoting the value of a dealt card. 5 cards are dealt, so we want to find the expectation of 5$X$.
$$\begin{eqnarray}  
E(5X) &=& 5\sum_{i}^{10}p_ix_i\\  
&=& \frac{5}{10}\sum_{i}^{10}x_i\\
&=& \frac{5}{10}\times 55\\
&=& 27.5
\end{eqnarray}$$
Therefore you will need to pay $27.50 to break-even on average. Therefore I will be willing to pay anything less than $27.50 in order to profit. 

## Variance
>[!note] Definition
>The variance of a random variable $X$ is defined as 
>$$Var(X) = E[(X-E(X))^2]$$
>Intuitively it represents how spread out the values are from the average

>[!note] Alternate version of variance formula
>$$\begin{eqnarray}  
Var(X) &=& E[(X-E(X))^2]\\  
&=& E[X^2-2XE(X)+E(X)^2]\\
&=& E(X^2)-2E(X)^2+E(X)^2\\
&=& E(X^2)-E(X)^2
\end{eqnarray}$$

#### Variance Properties
>[!note] Property 1
>$$Var(aX)=a^2Var(X)$$
>Proof:
>$$\begin{eqnarray}  
Var(aX) &=& E[(aX)^2]-E(aX)^2\\  
&=& E(a^2X^2)-a^2E(X)^2\\
&=& a^2[E(X^2)-E(X)^2]\\
&=& a^2Var(X)
\end{eqnarray}$$

>[!note] Property 2
>$$Var(X+Y) = Var(X) + 2[E(XY)-E(X)E(Y)]+Var(Y)$$
>Proof:
>$$\begin{eqnarray}  
Var(X+Y) &=& E[(X+Y)^2]-E(X+Y)^2\\  
&=& E[X^2+2XY+Y^2]-(E(X)+E(Y))^2\\
&=& E(X^2)+2E(XY)+E(Y^2)-(E(X)^2+2E(X)E(Y)+E(Y)^2)\\
&=& E(X^2)+2E(XY)+E(Y^2)-E(X)^2-2E(X)E(Y)-E(Y)^2\\
&=& E(X^2)-E(X^2)+2E(XY)-2E(X)E(Y)+E(Y^2)-E(Y)^2\\
&=& Var(X) + 2[E(XY)-E(X)E(Y)]+Var(Y)
\end{eqnarray}$$


