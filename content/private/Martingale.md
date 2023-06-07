---
title: "Martingale"
enableToc: true
tags:
- Martingale 
---
## Martingale
A martingale is a sequence of random variables $(X_1,X_2,X_3,...,X_n)$ defined on a probability space. The sequence of random variables is said to be a martingale if, for any positive integer $n$, the expected value of $X_{n+1}$ is equal to $X_n$. In other words the conditional expectation of the next value in the next sequence, given the past information, is equal to the current value. 

## Martingale System (Betting System)
The martingale system/strategy uses the idea that statistically you cannot lose every time and thus you should increase the amount invested. 

This method is commonly compared to betting on a game in hopes to break even. A gambler would win their stake if a coin flip comes up heads or lose it if it comes back as tails. The strategy would involve doubling their bet after each loss so that the first win would recover all previous losses and also win an amount equal to the original bet. Over time the probability of eventually flipping a head approaches 1, however this assumes that the gambler has unlimited amount of money to cover each losing bet. 
