---
title: "Quant questions that you need to know"
enableToc: true
tags:
- 
---
## Monty Hall Problem
>[!question] Monty Hall Problem
>Suppose you’re on a game show, and you’re given the choice of three doors: Behind one door is a car; behind the others, goats. You pick a door, say No. 1, and the host, who knows what’s behind the doors, opens another door, say No. 3, which has a goat. He then says to you, “Do you want to pick door No. 2?” Is it to your advantage to switch your choice?
>
>The standard assumptions are 
>1. The host must always open a door that was not picked by the contestant.
>2.  The host must always open a door to reveal a goat and never the car.
>3.  The host must always offer the chance to switch between the originally chosen door and the remaining closed door



**Solution**
Yes it is in your favour to switch. 
We use [[private/Conditional Probability|Conditional Probability]] to solve this. Firstly, we note that $P(\text{prize door } i) = 1/3$ . 
Supposing the prize is behind door 1 and we pick this door, then the host will open either door 2 or 3, each with probability $1/2$. 
$P(\text{prize door } 1 \text{ AND host opens door } 2) = 1/3 × 1/2 = 1/6$ 
$P(\text{prize door } 1 \text{ AND host opens door } 3) = 1/3 × 1/2 = 1/6$

In the case that we picked door 1 and the prize is not behind door 1, the prize may behind door 2 or door 3. From our assumption the host will always pick a door that was not picked by the contestant  and that they must reveal a goat then they would only have one choice in which door to reveal. 
$P(\text{prize door } 2 \text{ AND host opens door } 3) = 1/3 × 1 = 1/3$
$P(\text{prize door } 3 \text{ AND host opens door } 2) = 1/3 × 1 = 1/3$

Suppose that the prize is behind door 1, and the host opens door 2.
Probability of winning by switching after initally picking door 1 and the host opens door 2 is equal to the probability of door 3 being the winning door AND the host picking door 2 divided by the probability of the host picking door 2.  

P(A) is probability of winning door, in this case door 3.
P(B) is probability of host opening door 2. 

$$\begin{eqnarray}
P(A|B) &=& \frac{P(A\cap B)}{P(B)}\\
&=& \frac{1/3}{1/2}\\
&=& \frac{2}{3}
\end{eqnarray}$$
We do not need to deal with both cases of doors 2 and 3, because they are symmetrical.

The probability of winning by staying after initially picking door 1 and the host opens door 2 is equal to the probability that the prize door is 1 AND the host opens door 2 divided by the probability of the host picking door 2. 
$$\begin{eqnarray}
P(A|B) &=& \frac{P(A\cap B)}{P(B)}\\
&=& \frac{1/6}{1/2}\\
&=& \frac{1}{3}
\end{eqnarray}$$

## Derangements: The Hat Problem
>[!question] The Hat Problem
>(a) $n$ people walk into a room for an event, each having a hat. They leave their hat at the door when they walk in. After the event finishes and they leave, they each pick up one hat at random. What is the probability that no one picks up their own hat? 
>(b) As the value of $n$ approaches infinity, show that the probability tends towards $\frac{1}{e}$

A derangement is a permutation of a set of elements where no element appears in their original position. The symbol representing the number of derangements is $!n$.

(a) To get the probability that no one picks up their own hat we need to find the number of derangements divided by the number of different arrangements. The number of different arrangements in this case is $n!$ as the first person has $n$ hats to choose from, leaving the second person with $(n-1)$ hats to choose from and so on. Therefore the probability is given by $$P(\text{No-one has the same hat})=\frac{!n}{n!}$$
To find out the number of derangements we can count the complementary case.  A derangement can only exist if no hat returns to their owner so if we count the number of arrangements where Hat 1 is returned to Person 1 we then take Hat 1 and Person 1 out of the equation and arrange the hats randomly for the remaining $n-1$ people. Arranging between the $n-1$ remaining people is $(n-1)!$ permutations. However we must do this for every person, as there is $n$ people, there are $n \times (n-1)!$ arrangements which is just $n!$. 

But doing it this way also counts some cases twice. When counting all arrangements where Hat 1 is returned to Person 1, there will be cases where Hat 2 will also be returned to Person 2.

Now when you count all the arrangements where Hat 2 is returned to Person 2 you will end up including the same scenarios again. Therefore to overcome this we need to subtract the case where **both** Hat 1 and Hat 2 get returned correctly to their owner but also repeating this for each combination of two hats.

So each combination of two hats being returned to their owner means there are $n-2$ hats to arrange giving $(n-2)!$ arrangements. However the number of ways to make a pair of two hats is $^nC_2$. Therefore the total amount we overcounted is  
$$\begin{eqnarray}
^nC_2 \times (n-2)! &=& \frac{n!}{2!(n-2)!} \times (n-2)!\\
&=& \frac{n!}{2!}\\
\end{eqnarray}$$
But doing this we still run into the same problem and we have overcompensated for the condition where 3 hats are returned correctly and now need to add them back in. This process will repeat and is known as the [Inclusion-Exclusion Principle](https://en.wikipedia.org/wiki/Inclusion%E2%80%93exclusion_principle)
![[files/includeExcludePrinciple.png]]
If you continue with the same idea for three hats being correctly returned you will find the total amount to be $$\frac{n!}{3!}$$
And this pattern continues for all cases and creating this pattern.
$$\frac{n!}{1!}-\frac{n!}{2!}+\frac{n!}{3!}-\frac{n!}{4!}+\text{...}$$
We can rewrite this into a sum
$$\begin{eqnarray}
\frac{n!}{1!}-\frac{n!}{2!}+\frac{n!}{3!}-\frac{n!}{4!}+\text{...} &=& n!\times (\frac{1}{1!}-\frac{1}{2!}+\frac{1}{3!}-\frac{1}{4!}+\text{...})\\
&=& n!\sum_{i=1}^{n}\frac{(-1)^{i+1}}{i!}\\
\end{eqnarray}$$
Therefore the number of derangements can be written as
$$\begin{eqnarray}
!n &=& n!-n!\sum_{i=1}^{n}\frac{(-1)^{i+1}}{i!}\\
&=& n!(1-\sum_{i=1}^{n}\frac{(-1)^{i+1}}{i!})\\
&=& n!\sum_{i=0}^{n}\frac{(-1)^{i}}{i!}\\
\end{eqnarray}$$
The probability that no one gets the same hat is therefore
 $$\begin{eqnarray}
 P(\text{No-one has the same hat})&=&\frac{!n}{n!}\\
 &=& \frac{n!\sum_{i=0}^{n}\frac{(-1)^{i}}{i!}}{n!}\\
 &=& \sum_{i=0}^{n}\frac{(-1)^{i}}{i!}
 \end{eqnarray}$$

(b) Using the result from part(a), we can note that it is equivalent to the [Taylor Expansion of the exponential function](https://en.wikipedia.org/wiki/Taylor_series#Exponential_function) $e^x$ where $x=-1$. Therefore as $n$ approaches infinity, the probability approaches $\frac{1}{e}$.

## Birthday Paradox
>[!question] The Birthday Paradox
>(a) There are $n$ people in a room. What is the probability that at least two people share the same birthday?
>(b) Find the number of people required in the room such that the probability exceeds 50%.

**Solution**
(a) Assuming a non-leap year, a year has 365 days. With an [[private/Tactics in Probability questions#"At least" questions|"At least" question]] we can take the complementary case. In this case it wouldn't make sense for a case where '1 person shares the same birthday' therefore the complement is the case where no one shares the same birthday.   

$$\begin{eqnarray}
P(X\geq 2) &=& 1-P(X<2)\\
&=& 1-P(X=0)\\
\end{eqnarray}$$
The probability where no one has the same birthday can be calculated with $$\frac{\text{Total number of ways that }n \text{ people can have unique birthdays} }{\text{Total number of birthday arrangements possible for }n \text{ people}}$$
First for the numerator we have to count the number of ways $n$ people can have a unique birthday. As each birthday has to be unique we count **without repetition** to avoid selecting the same birthday. Each individual is also considered unique so therefore the **order matters** as well. For example if Person A was born on Jan 1st and Person B is born on Feb 1st it is an entirely different arrangement to Person A being born on Feb 1st and Person B born on Jan 1st. Referring to the [[private/Tactics in Probability questions#Telling the difference between combinatorics scenarios|Combinatorics differences]] table, we therefore use a permutation $^{365}P_n$.

For the denominator we count the number of ways $n$ people can have birthdays without restrictions. In this case each person has 365 option and there are $n$ people, therefore $365^n$ ways. 
Therefore 
$$\begin{eqnarray}
P(X\geq 2) &=& 1-P(X=0)\\
&=& 1-\frac{^{365}P_n}{365^n}\\
&=& 1-\frac{365!}{365^n(365-n)!}
\end{eqnarray}$$

(b) For this we can basically guess and check as solving for $n$ in this case is difficult by hand. For $n=22$, 
$$1-\frac{^{365}P_{22}}{365^{22}} \approx 0.475695$$
and for $n=23$
$$1-\frac{^{365}P_{23}}{365^{23}} \approx 0.504297$$
Therefore needs 23 people in order to have a probability greater than 50%.

## St. Petersburg Paradox
>[!question] St. Petersburg Paradox
>Oden offers to play a game with you. He defines the rules in the following manner. He flips a fair coin repeatedly until it lands on heads. When it lands on heads, the game ends. At the end of the game, you receive a prize of $\text{\$}2^n$ , where $n$ is the number of times Oden flipped the coin in total. How much money are you willing to pay to play this game?

**Solution**
If you begin a naïve attempt to solve this by calculating the expected value you get,
$$\begin{eqnarray}
E(X)&=&\frac{1}{2}\times2+\frac{1}{4}\times4+\frac{1}{8}\times8+ \text{...}\\
&=& 1+1+1+\text{...}\\
&=& \infty
\end{eqnarray}$$

However in this case you are assuming that Oden has infinite money to give you. 

If the casino (Oden in this case) has finite resources then the game cannot continue when the resources are exhausted. The maximum number of times the casino can flip the coin is given by $log_2(W)$ where $W$ is the amount of money that the casino can pay out. As the resources are finite then the expected value is also finite.
$$E(X)=\sum_{k=1}^{n}\frac{1}{2^k}\times 2^k$$

If the casino is able to pay out just over a million dollars, $2^{20}=1048576$ dollars, then the expected value would be $20.  If the casino is able to pay out over a billion dollars, $2^{30}=1075000000$ dollars, then the expected value would be $30. This is because each flip only adds $1 more expected value. 

Another popular solution is Expected Utility Theory.
We can classify individuals into three categories: Risk Averse, Risk Loving or Risk Neutral. 
Investors are usually classified as Risk Averse.   
We can quantify this idea of risk aversion as a **utility function**. This function can be modelled based on the individual but the idea is that there is a diminishing amount of utility gain at some point for the amount of risk that is taken. Is there a functional difference between $2^{90}$ and $2^{91}$ dollars? In absolute terms the money has doubled but provides no extra function. If you draw the line at 90 flips then there would be a finite amount. 

A common utility model suggested by [Bernoulli](https://en.wikipedia.org/wiki/St._Petersburg_paradox#Expected_utility_theory) is a logarithmic function that models the net change in utility weighted by the probability of that event occurring which can determine the amount of money that a person should be willing to pay up to. 

Another scenario to think about is that rational behavior corresponds to what a rational decision maker would do. Normally




## References
- Paris Kastanias - Quantsoc workshop
- [Wikipedia - Derangement](https://en.wikipedia.org/wiki/Derangement)
- [Numberphile - Derangement](https://youtu.be/qYAWjIVY7Zw)