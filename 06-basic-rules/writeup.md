# Homework 6: Basic Rules
## Problem 1

For this question ,we use the basic rule of addition:

P(5) = P(5 and A wins) + P(5 and B wins) = 0.08+0.18 = 0.26

P(6) = P(6 and A wins) + P(6 and B wins) = 0.11+0.19 = 0.30

P(5 or 6) = P(5) + P(6) - P(5 and 6) = 0.26 + 0.30 - 0 = 0.56

Therefore, the probability that series ends in 5 or 6 is 0.56.

## Problem 2

This question is a conditional probability and we use the conditional row to generate the probability:

P(A wins|6) = 0.11/(0.11+0.19) = 11/30

Therefore, the probability that team A will win supposing the series ends in 6 games is 11/30.

## Problem 3

P(B or Even games) = P(B) + P(Even games) - P(B and Even games)

P(B) = 0.11+0.18+0.19+0.17 = 0.65

P(Even games) = 0.03+0.11+0.11+0.19 = 0.44

P(B and Even games) = 0.11+0.19 = 0.30

P(B or Even games) = 0.65+0.44-0.30 = 0.79

Therefore, team B wins the series or the series will end after an even number of games is 0.79.

## Problem 4

For this question, we can use the rule of compliment. That is, P(E) = 1 - P(E^c).

P(5 or fewer|A wins) = 1 - P(6 or 7|A wins) = 1 - (0.11+0.13)/(0.03+0.08+0.11+0.13) = 1 - 0.24/0.35 = 11/35

Therefore, the probability the series will end in 5 or fewer games supposing that A wins the series is 11/35.

## Problem 5

Multiplication rule indicates that the probability of at least two people shareing a birthday with a class size of 11 could be the complementary probability of no shared birthdays among the class. Therefore, each person within the group takes a unique birthday within the 365 days. The calculation would be:

P(at least one shared birthday) = 1 - ((365/365) * (364/365) * (363/365) * ... * (355/365)) = 0.14114

Or, we could run the following command in R to generate the computational result:

```
n <- 11
1 - exp(lchoose(365,n) + lfactorial(n) - n*log(365))
```

The result is the same as mathematical solution, which is **0.14114**.

The simulation result is 0.14014 given 100000 repetitions and a seed of 1. The analytical and simulated results are very close, which indicates that simulation is providing an accurate approximation of the probability. The small difference can likely be attributed to the inherent randomness in the simulation process.

Additionallly, if we run the repetitions using the above R code, the generated plot for the probability of at least a shared birthday given a class size of N is pretty close to the one that we had in assignment 3:

```
bp <- function(n) 1 - exp(lchoose(365, n) + lfactorial(n) - n * log(365))
plot(1:80, bp(1:80), col = 'lightblue', lwd = 3)
```
![image](analytic%20solution%20plot.png)
