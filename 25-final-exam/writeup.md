# DS 2006 Final Exam
- **Name**: Leyan Tang
- **ComputingID**: gnv2nh
- **Date**: December 13th, 2023

## 1. The Monty Hall Problem
**A. Strategy 1 wining probability with equal prize assignment**

P(winning a car) = 1/3. When the person made the initial decision to choose door A, there's 1/3 probability that the chosen door has the car and 2/3 probability that the chosen door contains goat because of the assumption that the prize assignment is equal across these three doors. Now, even the host reveals a door B that contains a goat, the initial probabilities still remain unchanged.

However, the for strategy 2, the probabilities to win a car by switching is 2/3. This is because by revealing the goat in another door, the host reassigns the probabilities from that from original one of the goat door to the remaining unopen goat door, making it to have the probability of 2/3, while the original chosen door's probability remains the same of 1/3.

Therefore, the probability of switching is always higher than the initial choise because the host's action updates the information about the location of the car, and the contestant can capitalize on this by switching doors. The probabilities favor the unopened door, making the switching strategy more likely to result in winning the car compared to sticking with the initial choice.

**B. Winning probabilities using R Simulations**
Based on the game function, I ran 10000 simulations and calculated the probabilities for two strategies with random prize assignments:

``````
num_simulations <- 10000
wins_staying <- 0
wins_switching <- 0

for (i in 1:num_simulations) {
  results <- game()
  wins_staying <- wins_staying + (results[1] == "car")
  wins_switching <- wins_switching + (results[2] == "car")
}

prob_staying <- wins_staying / num_simulations
prob_switching <- wins_switching / num_simulations

cat("Strategy 1:", prob_staying, "\n")
cat("Strategy 2:", prob_switching, "\n")
``````
Based on the simulation, probability of winning the car with strategy 1 is 0.3332, and probability of winning the car with strategy 2 is 0.6668, which closely corresponds to the mathematical methods in step A.

**C. Communicating uncertainty**

To further communicate the simulation error, based on Central Limit Theorem, using the mean and standard deviation from the sampling distributions for strategy 1 and strategy 2, and with a 95% confidence interval, I calculated the confidence intervals for the two strategies:

``````
conf_int_prob_staying <- qnorm(c(0.025, 0.975), mean_prob_staying, sd_prob_staying / sqrt(num_simulations))
conf_int_prob_switching <- qnorm(c(0.025, 0.975), mean_prob_switching, sd_prob_switching / sqrt(num_simulations))
``````

The result table is shown below:

![image](p1.png)

There's the inherent variability in the simulations, reflected in the standard deviation of approximately 0.4729 for both staying and switching strategies. The standard deviation provides a measure of the dispersion in the simulated outcomes. 

To further quantify the uncertainty, I computed 95% confidence intervals for both strategies. For the staying strategy, the interval [0.3284, 0.3470] indicates that we can be reasonably confident that the true probability of winning lies within this range. Similarly, for the switching strategy, the 95% confidence interval [0.6530, 0.6716] provides a plausible range for the true probability. This means that, within a 95% confidence level, we can reasonably expect the true probability of winning to be within the specified range for each strategy.

## 2. Conditional Probability
**A. Probability Table**
|             | D+    | D- | Margin  |
| ----------- | ----------- | ----------- | ----------- |
| **T+** | 0.0008    | 0.0999    | 0.1007 |
| &nbsp;&nbsp;&nbsp; Row |0.0079| 0.9921  | |
| &nbsp;&nbsp;&nbsp; Col | 0.8 | 0.1  | |
| **T-** | 0.0002  |0.8991   | 0.8993 |
| &nbsp;&nbsp;&nbsp; Row | 0.0002  | 0.9998  | |
| &nbsp;&nbsp;&nbsp; Col | 0.2 |0.9 | |
| Margin | 0.001  | 0.999   | 1 |

**B. Positive predictive value of the test**
Based on Bayes' Rule, P(D+|T+) can be calculate as P(T+|D+)*P(D+)/P(T+), which is `0.00794439`, as is shown in the row probability on the top left cell.

**C. Calculation of p when P(D+|T+) is 0.5**
If `P(T+|D+) = P(T-|D-) = p`, the key components consisting of are calculated as:

- P(T+|D+) = p
- P(D+) = 0.001
- P(T+) = 0.001*p + 0.999*(1-p) = 0.999-0.998*p

So then the equation of the positive predictive value is p*0.001/(0.999-0.998*p). Equating it to be 0.5, the required p is `0.999`.

## 3. Discrete Distributions
**A. 90th percentile for the number of car accidents**

Using the following code, I calculated that the 90th percentile is 8 accidents per day:
``````
percentile_90 <- qpois(0.9, lambda = 5)
``````

**B. Density Plot**
Using the code as below, I generated the density plot:
``````
accident_counts <- seq(100, 200, by = 1)
density <- dpois(accident_counts, lambda =  5*30)

ggplot(data = data.frame(x = accident_counts, y = density), aes(x, y)) +
  geom_bar(stat = "identity",width = 0.8) +
  labs(title = "Analytical method: Density Plot of Accidents in a 30-Day Period",
       x = "Number of Accidents",
       y = "Density")
``````

![image](p2.png)

**C. Probability of observing 180 or more accidents in a 30 day period**

Using `prob_180_or_more <- 1 - ppois(180 - 1, lambda = 5*30)`, I calculated that this tail probability to be `0.009417947`.


## 4. Continuous Distributions
**A. Probability of DBP lying between 90 and 110 mmHg**



**B. Probability that the discovered femor was from a male**

**C. Probability that 2 or more patients in a cohort of 10 experience an infection within 30 days**

## 5. CDF and PDF
**A. MLE Method**

**B. Gamma Distribution**

**C. Gaussian kernel**

## 6. Uncertainty about estimates
**A. 1/20 support interval**

**B. Symmetric density credible interval**

## 7. Misc Definitions
A. What is a confounding variable?
- Answer: 

B. What is a CDF?
- Answer:

C. What is a PDF? PMF?
- Answer: 

D. What is Simpson’s Paradox?
- Answer: 

E. What is independence?
- Answer:
