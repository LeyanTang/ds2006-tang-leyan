# Homework 13
## Question 1

If the treatment is balanced between the gender groups, then out of 40 treatments, there should be 20 for females and 20 for males. The 40 placebos should also be sent to gender groups equally. The conditional probabilities should remain the same as the book says.

For each cell in each row, the probability denotes the conditional row probability:

|           | $R$ | $R^c$ | Marginal | 
|-----------|---------------|--------------------|-------------------------------|
| $T$  |16 (0.4) | 24 (0.6) | 40 (0.5)  |  
| $T^c$ | 20 (0.5) | 20 (0.5) | 40 (0.5)|
| **Total**| 36 (0.45) | 44 (0.55) | 80 (1.0)|

We can see the equal forcement let the treatmenet group appear ineffective in improving the recovery rate. 

## Question 2

Let's say there are 120 people participating in total and  80 of them are female, 40 are male. If we use the same conditional row probabilities in each of their group, the full talbe should look like this:

|           | $R$ | $R^c$ | Marginal | 
|-----------|---------------|--------------------|-------------------------------|
| $T$  |20 (1/3) | 40 (2/3) | 60 (0.5)  |  
| $T^c$ | 26 (13/30) | 34 (17/30) | 60 (0.5)|
| **Total**| 46 (0.383) | 74 (0.617) | 120 (1.0)|


## Question 3

From the equation, $
\Delta = P(R|T)-(R|T^c)$ should be absolute because it quantifies the actual difference in probabilities, while $\quad \rho = \frac{P(R|T)}{P(R|T^c)}$ should be relative because it expresses the treatment effect as a ratio or proportion between the treatment and control groups. 

## Question 4

- **Table 1**:
$P(R|T)$ = 16/40 = 0.4
$P(R|T^c)$ = 20/40 = 0.5

So,
$\Delta = P(R|T)-(R|T^c)$ = 0.4 - 0.5 = -0.1
$\quad \rho = \frac{P(R|T)}{P(R|T^c)}$ = 0.4/0.5 = 0.8

- **Table 2**:
$P(R|T)$ = 20/60 = 1/3
$P(R|T^c)$ = 26/60 = 13/30

So,
$\Delta = P(R|T)-(R|T^c)$ = 1/3 - 13/30 = -0.1 
$\quad \rho = \frac{P(R|T)}{P(R|T^c)}$ = 0.769

Based on the calculation, the absolute $\Delta$ is the same but the relative $\quad \rho$ is different. The equations are:

$\Delta$ = -0.1
$\quad \rho$ = $\frac{6-4\alpha}{7-4\alpha}$

Explanation for the general equation:
If alpha is the proportion of women, let men be 40, so that women are 40*alpha/(1-alpha).

So Men's table is:
|           | $R$ | $R^c$ | Marginal | 
|-----------|---------------|--------------------|-------------------------------|
| $T$  |12 |8 | 20  |  
| $T^c$ | 14 | 6 | 20|

Women's table is:

|           | $R$ | $R^c$ | Marginal | 
|-----------|---------------|--------------------|-------------------------------|
| $T$  |4*alpha/(1-alpha) | 16*alpha/(1-alpha)  |  20*alpha/(1-alpha)|
| $T^c$ | 6*alpha/(1-alpha)| 14*alpha/(1-alpha) | 20*alpha/(1-alpha)|

Therefore, the two components are calculated by adding cells up:

- P(R/T) = (4*alpha/(1-alpha) + 12) / (20*alpha/(1-alpha) + 20)
- P(R/T^c) = (6*alpha/(1-alpha) + 14) / (20*alpha/(1-alpha) + 20)

And then two ratios can be calculated by these two components.