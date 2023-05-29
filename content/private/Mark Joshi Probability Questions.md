---
title: "Mark Joshi Probability Questions"
enableToc: true
tags:
- Probability 
---
## General
>[!question] Question 3.1
>Consider the following game. The player tosses a die once only. The payoff is $1 for each dot on the upturned face. Assuming a fair die, at what level should you set the ticket price of this game.

**Solution**
Find the expected value of 1 dice roll. 
$$E(X)=\frac{1}{6}(1+2+3+4+5+6)=3.5$$
Therefore the expected payout is $3.50 on average. To breakeven on average I need to set the price at $3.50 but if I want to make a profit then I need to charge more than that. 

>[!question] Question 3.2
>Suppose we play a game. I roll a die up to three times. Each time I roll, you can either take the number showing as dollar, or roll again. What is your expected winnings. 

**Solution**
For this case we know the expected value from one dice roll is 3.5 as we calculated in Question 3.1. 
Therefore we should only roll again if the first roll is less than 3.5, meaning roll again if we roll a 1,2 or 3 and keep our roll if we get 4,5 or 6. 

$$E(\text{2 rolls}) = \frac{1}{2}(3.5) + \frac{1}{6}(4+5+6) = 4.25$$
Similarly we can apply this logic to the scenario with 3 rolls, if we roll lower than 4.25 then we should re roll.

$$E(\text{3 rolls}) = \frac{4}{6}(4.25)+\frac{1}{6}(5+6)=4.6667 \text{ or } \frac{14}{3}$$

>[!question] Question 3.3
>There are 4 sealed boxes. There is \$100 in one box and the rest are empty. A player can pay $X$ to open a box and take the contents as many times as they like. Assuming this is a fair game, what is the value of $X$?

**Solution**
We continue playing until we pick the correct box. This means we can either pick the first, second, third or fourth box to win the prize. As we have to pay a fee for each box and the probabilities of the other boxes change once we open a new box we can write the expected cost as,
$$\begin{eqnarray}
E(cost)&=&\frac{1}{4}\times X + (\frac{3}{4} \times \frac{1}{3})\times 2X+ (\frac{3}{4}\times \frac{2}{3}\times \frac{1}{2})\times 3X + (\frac{3}{4}\times \frac{2}{3}\times \frac{1}{2})\times 4X\\
&=& \frac{1}{4} \times 10X\\
&=&2.5X
\end{eqnarray}$$

As the winning box has \$100, we can calculate the cost to play
$$\begin{eqnarray}
2.5X&=&100\\
X&=&40
\end{eqnarray}$$
>[!question] Question 3.4
>I pick a number $n$ from 1 to 100. If you guess correctly, I pay you $n$ and zero otherwise. How much would you pay to play this game?

**Solution**
