---
title: "Probability"
enableToc: true
tags:
- Probability
---

*P* is used to denote the proportion or probability of an event occuring. 
A is a set. 
Ω denotes the total sample space.
*P(A)* is the probability of event A occuring.  

 $$P(A) = \frac{|A|}{|Ω|}$$
For example if we buy a bushel of apples where Set A contains rotten apples where 
$|A| = 28$ and $|Ω| = 550$ then $P(A) = \frac {28} {550}$

If two sets are disjoint, have no overlapping members, then their probability can be summed. 

Using the previous example, we can reasonably assume that unripe apples cannot be rotten. Therefore the number of "unripe or rotten apples" is equal to the sum of unripe apples and rotten apples. 

$$|A+B| = |A|+|B|$$
Dividing both sides by $|Ω|$, we obtain
$$P(A+B)=P(A)+P(B)$$
If A and B is not disjoint, then the equation becomes an inequality. 
$$|A\cup B| \leq |A|+|B|$$
and therefore 
$$P(A\cup B) \leq P(A)+P(B)$$
The reason it is an inequality is because the intersection of A and B has been accounted for twice in $P(A)+P(B)$. We can rewrite this relationship as an equation.
$$P(A\cup B) = P(A)+P(B)-P(A \cap B)$$
$$P(A\cup B)+P(A \cap B) = P(A)+P(B)$$
## References
Elementary probability theory with stochastic processes and an introduction to mathematical finance - Kai Lai Chung