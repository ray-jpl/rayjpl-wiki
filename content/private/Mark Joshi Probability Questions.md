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
>We play a game. I pick a number $n$ from 1 to 100. If you guess correctly, I pay you $n$ and zero otherwise. How much would you pay to play this game?

**Solution**
This is more of a game theory question. Each player has to pick a strategy. In this case, an optimal strategy will be one in which the expected winnings is independent of the strategy the opponent picks. 

Clearly, it is better for the payer to choose a small number so that he has to pay less. However if he always goes for a small number then he is more likely to have to pay out since the receiver will then also go for a small number. If the payer assumes the worst case scenario where the guesser knows the pickers probability numbers for each choice then the guesser has the potential to exploit this to gain a higher than expected payoff. 

Therefore in the optimal strategy, the payer should be indifferent to what the guesser chooses, also known as the [Indifference Principle](https://en.wikipedia.org/wiki/Principle_of_indifference). If the payer is indifferent then the expected value for any number should be the same. E.g $1p_1 = 2p_2=3p_3=\text{...}=100p_{100}$. However the probabilities need to add to 1. 
$$\begin{eqnarray}
p_1 + p_2 +p_3 +\text{...}+p_{100}&=&1\\
p_1+\frac{1}{2}p_1 +\frac{1}{3}p_1+\text{...}+\frac{1}{100}p_{1}&=&1\\
p_1(1+\frac{1}{2} +\frac{1}{3}+\text{...}+\frac{1}{100})&=&1\\
p_1&=& \frac{1}{\sum_{j=1}^{100}\frac{1}{j}}\\
p_1&=&0.192776
\end{eqnarray}$$
Therefore the expected value of the game is 0.192776 and I would pay less than that to play the game. 



>[!question] Question 3.5
>Suppose you have a fair coin. You start with a dollar, and if you toss a H, you position doubles, if you toss a T, your position halves. What is the expected value of the money you have if you toss the coin indefinitely

**Solution**
Let $S_i$ be the random variable that denotes your dollars after the toss $i$.
$$E(S_1)=\frac{1}{2}\times 2 + \frac{1}{2}\times\frac{1}{2}=\frac{5}{4}$$
Now the subsequent toss is $S_2$ either doubles or halves our position so,
$$\begin{eqnarray}
E(S_2)&=&\frac{1}{2}\times 2E(S_1) + \frac{1}{2}\times\frac{E(S_1)}{2}\\
&=&\frac{5}{4}E(S_1)\\
&=&(\frac{5}{4})^2\\
\end{eqnarray}$$
By recurrence
$$E(S_n)=(\frac{5}{4})^n$$
Therefore the value tends towards infinity as you toss the coin indefinitely.

>[!question] Question 3.6
>Suppose we toss a fair coin, and let $N$ denote the number of tosses until we get a head (including the final toss). What is $E(N)$ and $Var(N)$.

**Solution**
If $N=k$, then we have $k-1$ tails followed by 1 head.
$$P(N=k)=0.5^{k-1} \times 0.5^1=0.5^k$$

Using the standard calculation for EV,
$$E(X)=\sum_{k=1}^{\infty}\frac{1}{2^k}k$$
To calculate the result of the series we can do this. 
$$\begin{eqnarray}
E(X)&=& 1\times\frac{1}{2}+2\times\frac{1}{2^2}+3\times\frac{1}{2^3}+\text{...}\\
\frac{1}{2}E(X)&=&1\times\frac{1}{2^2}+2\times\frac{1}{2^3}+3\times\frac{1}{2^4}+\text{...}
\end{eqnarray}$$
Subtracting the two equations together we are left with 
$$\begin{eqnarray}
\frac{1}{2}E(X)&=&\frac{1}{2}+\frac{1}{2^2}+\frac{1}{2^3}+\frac{1}{2^4}+\text{...}\\
E(X)&=&1+\frac{1}{2}+\frac{1}{2^2}+\frac{1}{2^3}+\frac{1}{2^4}+\text{...}
\end{eqnarray}$$
Subtracting these two equations removes the series,
$$\begin{eqnarray}
E(X)-\frac{1}{2}E(X)&=&1\\
\frac{1}{2}E(X)&=&1\\
E(X)&=&2\\
\end{eqnarray}$$
Now, variance can be calculated as
$$Var(X)=E(X^2)-[E(X)]^2$$

As we already calculated what $E(X)$ is we just need to find $E(X^2)$. To find $E(X^2)$ we can consider the possible outcomes for the first toss. [Law of Total Expectation](https://en.wikipedia.org/wiki/Law_of_total_expectation)
1. If we get a heads on the first toss, the number of tosses squares is just $1^2=1$
2. If we get a tails on the first toss, we effectively restart the process and the expected number of additional tosses is squared until we get a head is $E((X+1)^2)=E(X^2+2X+1)=E(X^2)+2E(X)+1$. 

$$\begin{eqnarray}
E(X^2)&=& 1^2\times\frac{1}{2}+(E(X^2)+2E(X)+1)\times\frac{1}{2}\\
2E(X^2)&=& 1+E(X^2)+2E(X)+1\\
E(X^2)&=& 2+2E(X)\\
&=& 2+2(2)\\
&=& 6\\
\end{eqnarray}$$
Therefore 
$$\begin{eqnarray}
Var(X)&=&6-[2]^2\\
&=&2
\end{eqnarray}
$$

>[!question] Question 3.7
>We play a game, with a fair coin. The game stops when either two heads or tails appear consecutively. What is the expected time until the game stops?

**Solution 1**
The solution I like using is to use a tree diagram.
![[files/Pasted image 20230601222736.png]]
Let the expected number of flips to be $x$. For case 1 we flip two heads straight away and win which has probability of $\frac{1}{4}$, similarly for case 4 the probability of two tails is the same. Both these scenarios take 2 turns in order to end the game. 

Case 2 and case 3 are also similar in the way that the game extends by an extra turn as heads or tails haven't appeared consecutively. We can say this scenario takes $x+1$ turns as it has the same 'game state' as if we just flipped a head/tail but we have used an extra flip to arrive. 

Therefore the expected number of turns is 
$$
\begin{eqnarray}
x&=&\frac{1}{4}\times2+\frac{1}{4}\times(x+1)+\frac{1}{4}\times(x+1)+\frac{1}{4}\times2\\
4x&=&2+x+1+x+1+2\\
4x&=&6+2x\\
2x&=&6\\
x&=&3
\end{eqnarray}
$$
>[!question] Question 3.8
>For a fair coin, what is the expected number of tosses to get 3 heads in a row?

Using the same working as question 3.7, 
1. It takes 3 tosses to get 3 heads in a row with probability of $0.5^3$
2. If tails is flipped then reset, $x+1$ tosses with probability of $0.5$ .
3. If HT flip then reset, $x+2$ tosses with probability of  $0.5^2$
4. If HHT flip then reset, $x+3$ tosses with probability of $0.5^3$
Adding this up we get, 
$$
\begin{eqnarray}
x&=&\frac{1}{8}\times3+\frac{1}{2}\times(x+1)+\frac{1}{4}\times(x+2)+\frac{1}{8}\times(x+3)\\
8x&=&3+4x+4+2x+4+x+3\\
8x&=&7x+14\\
x&=&14\\
\end{eqnarray}
$$

>[!question] Question 3.9
>You toss a biased coin. What is the expected length of time until a head is tossed? For two consecutive heads?

Let $p$ be the probability of getting heads for the biased coin. 
For one head.
$$\begin{eqnarray}
x&=&p\times1+(1-p)(x+1)\\
x&=&p+x+1-xp-p\\
xp&=&1\\
x&=&\frac{1}{p}
\end{eqnarray}
$$

For two consecutive heads, we consider the cases (HH), (T) and (HT) 
$$\begin{eqnarray}
x&=&p^2\times2+(1-p)(x+1)+p(1-p)(x+2)\\
x&=&2p^2+x+1-px-p+(p-p^2)(x+2)\\
x&=&2p^2+x+1-px-p+px+2p-p^2x-2p^2\\
x&=&x+1+p-p^2x\\
p^2x&=&1+p\\
x&=&\frac{1+p}{p^2}
\end{eqnarray}
$$
>[!question] Question 3.10
>I have a bag containing 9 ordinary coins and 1 double-headed one. I remove a coin and flip it three times. It comes up heads each time. What is the probability that it is the double header. 

As conditional probability is involved, we should look to apply [[private/Conditional Probability#Bayes Theorem|Bayes Theorem]].

$$\begin{eqnarray}
P(A|B) &=& \frac{P(A\cap B)}{P(B)}\\
&=& \frac{P(B|A)P(A)}{P(B)}\\
\end{eqnarray}$$

Substituting A as the event of  picking the double headed coin and B as the probability of getting 3 heads we can substitute as follows. 

$$\begin{eqnarray}
P(\text{Double-headed coin |3 heads}) &=& \frac{P(\text{3 heads | Double-headed coin})\times P(\text{Double-headed coin})}{P(\text{3 heads})}\\
&=&\frac{1\times\frac{1}{10}}{(1\times\frac{1}{10}+\frac{1}{2^3}\times\frac{9}{10})}\\
&=&\frac{8}{17}
\end{eqnarray}$$

>[!question] Question 3.11
>I take an ordinary-looking coin out of my pocket and flip it three times. Each time it is a head. What do you think the probability that the next flip is also a head? What if I had flipped the coin 100 times and each flip was a head.

For the first case of three heads. It is uncommon but I wouldn't consider it highly unlikely since it has a $\frac{1}{8}$ chance of occurring. There is still no reason for me to expect the coin to be unfair at this stage, so I would assume that the probability is 0.5.

For the second case, flipping 100 heads has the probability of $2^{-100}$ which is highly unlikely. We don't have any information on whether the coin is fair or not. If this was conducted in an interview setting then the interviewer may play tricks on us. If we were playing this as a game then the person flipping may be using a biased coin in order to make the odds in their favor. 

We can use Bayes theorem again and use $p$ to represent the probability that the coin is double sided
$$\begin{eqnarray}
P(\text{Double-headed coin |N heads}) &=& \frac{P(\text{N heads | Double-headed coin})\times P(\text{Double-headed coin})}{P(\text{N heads})}\\
&=&\frac{1\times p}{1\times p+\frac{1}{2^N}\times(1-p)}\\
&=&\frac{p}{p+\frac{1-p}{2^N}}
\end{eqnarray}$$

Unless the probability of having a double sided coin is extremely small the $\frac{1-p}{2^N}$ term will always approach zero as dividing by $2^{100}$ will approach zero unless the numerator is a similar magnitude. Therefore the probability is very close to 1 for any reasonable value for $p$.

>[!question] Question 3.12
>You throw a fair coin one million times. What is the expected number of strings of 6 heads followed by 6 tails.

We flip the coin 1,000,000 times but there are 1,000,000 -11 possible slots for this sequence to occur as a string of 6 heads and 6 tails can't begin on the 999,999th flip, the last possible place for the string to begin is the 999,989th flip. If you want to generalise this for $n$ flips then the amount of slots would be $n-k+1$, where $k$ is the length of the string.

Now for each slot to have the string, the chance for 6 heads and 6 tails in a row is $2^{-12}$. Therefore the expected number of strings of 6 heads followed by 6 tails is $$\frac{1000000-11}{2^{12}}\approx244.14$$
The reason we can do this division is due to the Linearity of Expectation which does not require for events to be independent, 
$$E(X+Y)=E(X)+E(Y)$$
or in this case
$$E(\sum I_j)=\sum E(I_j)$$
>[!question] Question 3.13
>Suppose you are throwing a dart at a circular board. What is your expected distance from the center? Make any necessary assumptions. Suppose you win a dollar if you hit 10 times in a row inside a radius of $R/2$, where R is the radius of the board. You have to pay 10c for every try. If you try 100 times, how much would you have lost/made in expectation? Does your answer change if you are a professional and your probaility of hitting inside $R/2$ is double of hitting outside $R/2$

**Solution**
Assuming that the board is perfectly circular and thus the area of the board is $\pi R^2$, meaning the area of the scoring radius is $\pi (\frac{R}{2})^2$. The scoring area is $1/4$ the size of the total area of the board. 
If we assume that as an unskilled player that we will hit anywhere on the board with an equal chance then we would hit inside the scoring radius with a probability of $0.25$. To win a dollar we would need to hit inside the radius 10 times in a row meaning a probability of $\frac{1}{4^{10}}$. 

For 100 throws the expected winnings are 
$$E(X)=1\times \frac{100}{2^{10}} + (-0.1)\times 100\approx -9.90$$
which is a bad deal


If we were a professional and the chance of hitting inside the ring is $2/3$ then the expected value is
$$E(X)=1\times\frac{100\times2^{10}}{3^{10}}+(-0.1)\times100\approx-8.27$$
which is still a net loss. 

>[!question] Question 3.14
>A woman has two babies. One of them is a girl, what is the probability that the other is a boy?

The arrangements of two babies are as follows
\[BB,BG,GB,GG\]
If one of them is confirmed a girl then that leaves the last 3 options. Out of the 2 out of the last 3 options contain a boy and therefore the probability is $2/3$.

The order is important as the girl being the older or the younger one is a distinguishing factor which makes it unique. 

>[!question] Question 3.15
>A family has two children of whom you know at least 1 is a girl. What is the probability that both are girls? What if you know that the eldest is a girl? What if you know that they have a girl called Clarissa. 

The arrangements of two children are as follows
\[BB,BG,GB,GG\]
If you know there is at least 1 girl then the probability that both are girls is $1/3$, \[BG,GB,**GG**\].

If you know the eldest is a girl then that leaves only two arrangements. Which means the probability is $1/2$, \[GB,**GG**\].

The name is inconsequential and matches the first case which is $1/3$. \[BG,GB,**GG**\].

>[!question] Question 3.16
>What is the probability that the fourth business day of the month is Thursday?

The key information here is the word business day which refers to the days of Monday to Friday. For the fourth business day of the month the first business day must be Monday. Therefore if the month started with Monday, Saturday or Sunday then the fourth business day would be Thursday. Given this the probability is $3/7$.

It is also important to mention that there are other non-business days that may fall on a weekday which may include public holidays such as Christmas, Good Friday, King/Queens birthday etc.


>[!question] Question 3.17
>You are playing Russian Roulette. There are precisely two bullets in  neighboring chambers of the six shooter revolver. The barrel is spun. The trigger is pulled and the gun does not fire. 
>a) You are next, do you spin again or pull the trigger?
>b) How do the odds change if we load three contiguous chambers?
>c) What if there are three rounds in alternating chambers?

a) The key information is that the bullets are in neighboring chambers. This limits the amount of positions that they are in. As a bullet has been fired then there are 5 chambers left. The amount of ways to arrange two adjacent bullets in 5 slots is $5-2+1=4$ ways. 
Representation of the arrangements of the bullets as an array, X represents the fired shot, the underscore represents empty and B represents the bullet.

1. \[ X , B , B , \_ , \_ , \_ \]
2. \[ X , \_ , B , B , \_ , \_ \]
3. \[ X , \_ , \_ , B , B , \_ \]
4. \[ X , \_ , \_ , \_ , B , B \]
In this scenario we have $1/4$ chance to get a bullet next, which is $0.25$. 
If we choose to spin again we also have the chance to land on the same empty chamber, so we have a $2/6$ chance or $0.3333$. 

Therefore it is better to pull the trigger than to spin again.

b) Using the same logic the amount of ways to arrange 3 adjacent bullets into 5 remaining slots is $5-3+1=3$.
1. \[ X , B , B , B , \_ , \_ \]
2. \[ X , \_ , B , B , B , \_ \]
3. \[ X , \_ , \_ , B , B , B \]
Therefore spinning and not spinning have the same probability and the odds do not change.

c) If the rounds are in alternating chambers and the pervious persons shot did not fire then the possible arrangements of the bullet are.
1. \[ X , B , \_ , B , \_ , B \]
As there is only one possible arrangement where the first person did not get shot then there is a certainty that the next chamber has a bullet and therefore you should spin again. 

>[!question] Question 3.18
>Consider a deck of 52 cards, ordered such that A > K > Q > J > ... >  2. I pick one first, then you pick one, what is the probability that my card is larger than yours.

Let the event that the first card picked is larger than the second be $E_+$ and let the opposite event where the first card is smaller than the second be $E_-$. There is also another case where the cards could be of equal value $E_0$. 

$$P(E_+)+P(E_-)+P(E_0)=1$$
Now $P(E_+)=P(E_-)$ as the total number of events where one card is bigger than another are symmetrical. 

The chance of drawing an equal card is $3/51$. Therefore
$$\begin{eqnarray}
$P(E_+)+P(E_-)+P(E_0)&=&1\\
2P(E_+)+\frac{3}{51}&=&1\\
2P(E_+)&=&\frac{48}{51}\\
P(E_+)&=&\frac{24}{51}\\
&=&\frac{8}{17}\\
\end{eqnarray}$$
>[!question] Question 3.19
>Suppose $2^n$ teams participate in a championship. Once a team loses, it is out. Suppose also that you know the ranking of teams in advance and you know that a team with a higher rank will always win the game with a team of lower rank. In the beginning, all teams are randomly assigned to play with each other. What is the probability that in the final, the best team will play the second best team. 

All that matters is that the teams are on opposite sides of the bracket at the beginning. as they will the best teams in their bracket. The best team will always end up in the final so we need to figure out the starting placement of the second best team. 

There are $2^n$ teams  but we don't want to end up in the same bracket as the best team. If we think about the tournament bracket as a binary tree we can see that exactly half of the spots will be a part of one bracket. Therefore there are $2^n \div 2$ spots where the second best team can start. The total amount of spots they can be placed in is $2^n-1$ as the best team occupies 1 spot. It might be better to understand with the diagram where the blue arrows represent the possible starting positions for the second team.

Therefore the total probability is $$\frac{2^{n-1}}{2^n-1}$$ ![[files/Pasted image 20230608005723.png]]



>[!question] Question 3.20
>A drawer contains 2 red socks and 2 black socks. If you pull out two socks at random, what is the probability that they match.

The colour of the first sock does not matter here we just need the colour of the second sock to match. After pulling the first sock only one of the remaining 3 will match. Therefore the probability is $1/3$.