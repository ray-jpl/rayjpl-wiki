---
title: "Combinatronics"
enableToc: true
tags:
- Combinatronics
- Factorials
- 
---
## Combinatronics
#### Selection with repeats
>[!note] Definition
> When we count something with repeats, we use the simple formula
> $$n^k$$
> Where $n$ is the number of options available and $k$ is the number of times we select the options. 'With repeats' means after we select the item we 'put it back'.

>[!question] Example - Bank Pin
>How many ways are there to make a 4-digit bank account pin (no restrictions)

**Solution**
We have four "slots" and each of these slots contain one digit. The digit can be any number from 0 to 9, therefore ten choices total. Hence the amount of possible 4-digit bank pins is $10^4=10000$.

#### Factorials
>[!note] Definition
>The factorial of $n$ is defined as 
>$$n! = n(n-1)(n-2)...(3)(2)(1)$$

This is useful when solving selections without repeats

>[!question] Example - 10-digit bank pin
>Suppose we now want to find out how many ways there are to make a 10-digit bank pin. Furthermore, we will add a restriction: we cannot use any digit more than once.

**Solution**
Now we have 10 slots. For the first slot we can put any number, therefore 10 choices. For the second number we can put any number except the number in the first slot, therefore 9 choices. Repeat for each digit in the pin and we get the number of ways as, 
$$10\times 9\times8\times...\times3\times2\times1=10!$$
#### Permutations
>[!note] Definiton
>A permutation is the name given to the case where we have to select items where 
>- We select without replacement 
>- Order **does** matter 
>
>The formula is:
>$$^{n}P_{k} = \frac{n!}{(n - k)!}$$

>[!question] Example - 4-digit bank pin (no repeats)
>How many ways are there to make a 4-digit bank account pin (no repeat digits allowed)?

**Solution**
We have 4 “slots” to select, and each of these slots can contain one digit (no repeats). For the first slot, we have 10 digits available, for the second slot, 9 digits, for the third slot, 8 digits and for the fourth slot, we have 7 digits. Hence we can calculate the number of ways as 
$$10 × 9 × 8 × 7 = 5040$$
Note that 
$$\begin{eqnarray}
10 × 9 × 8 × 7 &=& \frac{10!}{6!}\\
&=& \frac{10!}{(10-4)!}\\
&=& ^{10}P_{4}
\end{eqnarray}$$
This is why we divide by  a factor of $(n − k)!$ because we overcount by that much when we find $n!$.

#### Combinations
>[!note] Definition
>A combination is the name given to the case where we have to select items where 
>- We select without replacement 
>- Order **does not** matter 
>
>The formula is 
>$$^nC_k = \frac{n!}{k!(n − k)!}$$
>The formula is similar to permutations except we divide by a further $k!$ to account for overcounting repeated cases.
>
>We also represent the notation as 
>$$n \choose k$$
>

>[!question] Example - Drawing cards from a deck
>If we draw 5 cards, how many ways can you have a hand with exactly 2 aces from a standard deck of 52 cards?

**Solution**
We firstly note that since we are drawing 5 cards and want any of the 2 to be aces, the order does not matter. There are 4 aces in the deck, and 2 we want, so the way we can pick the two aces by drawing is $^4C_2$. Now for the other 3 cards, we can draw anything but an ace. We have drawn 2 cards already and we do not want the remaining 2 aces, so we have 48 cards left to select from, and we want to draw 3. So we have $^{48}C_3$. We multiply these together to get $^4C_2\times ^{48}C_3 = 103776$

#### Stars and bars
>[!note] Definition
>The stars and bars formula is a way to calculate our last case, namely 
>- **Repeats allowed** 
>- Order **does not** matter 
>
>The formula is given by
>$${n+k-1} \choose {k-1}$$
>
>The problem can be formulated like this: we have $n$ indistinguishable stars and wish to place them into $k$ distinct baskets. How many ways can we arrange the stars? We place “bars” between the “stars” to represent the separation into the baskets. Note that there since there are k baskets, we use $k − 1$ dividers (bars), to represent the k distinct groups. We then select $k − 1$ bars to be placed between the gaps out of the $n + k − 1$ possible gaps.

>[!question] Example
>For example, when $n = 7$ and $k=5$, the tuple (4, 0, 1, 2, 0) may be represented by the following diagram:
>
>![[files/starsbars1.png]]
>To see that there are ${n+k+1} \choose {k-1}$ possible arrangements, observe that any arrangement of stars and bars consists of a total of $n+k−1$ objects, $n$ of which are stars and $k−1$ of which are bars. Thus, we only need to choose $k−1$ of the $n+k−1$ positions to be bars (or, equivalently, choose $n$ of the positions to be stars).

>[!question] Example - At least 1 star in each bar
>For example, with $n=7$ and $k=3$, start by placing the stars in a line:
>![[files/starsbars2.png]]
>There are $n−1$ gaps between stars. A configuration is obtained by choosing $k−1$ of these gaps to contain a bar; therefore there are ${n-1} \choose {k-1}$ possible combinations.








