---
title: "Poisson Distribution"
enableToc: true
tags:
- Poisson Distribution
- Probability Distributions
---
## Poisson Distribution
>[!note] Definition
>A possion distribution is a **discrete** probability distribution which is used for counting things such as '"the probability of 7 people walking into a shop today".
>We have
>$$f(\lambda; x)= \frac{\lambda^x e^{-\lambda}}{x!}$$
>where $\lambda$ is the rate at which people walk in, and x is the number of occurrences of people walking in.

>[!question] Example - Shop
>Suppose that, on average, a person walks into a shop every 15 minutes. What is the probability that 7 people walk in this hour?

**Solution**
In this case $\lambda = 4$ and $x=7$, therefore
$$f(\lambda; x)= \frac{4^7 e^{-4}}{7!}$$
Which is 0.0595.
