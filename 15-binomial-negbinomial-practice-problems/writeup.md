# Homework 15
## Question 1

In this scenario, each student's outcome is independent of the others, meaning that students can be replaced. We will use the binomial distribution to calculate the probability that 3 or fewer students do not complete out of 29 students.

We use these functions in R to calculate such probability:
``````
prob_fewer_than_3 <- 1 - pbinom(25, 29, 0.7)
``````
The probability that 3 or fewer students do not complete the degree is 0.01209502.

## Question 2 (resubmitted)
Since the professor could only take students during 15 years because of the 5-year program duration, we can calculate the probability that the number of students are equal to or below 9 and take the complimentary probability to arrive at the result:
``````
p <- 0.7
n_successes <- 9
n_failures <- 15

prob_retire_20 <- 1-pbinom(n_successes, n_failures, prob = p)
prob_retire_20
``````

The probability that the professor will retire in 20 years is .7216214.

## Question 3

In this scenario, we are interested in achieving 3 successes before 25 submissions, and we can use pbinom to count for the failed trails until the successes.

We can use the R codes as follows:
``````
p_success <- 0.1
n_successes <- 3
n_submissions <- 25

prob_3_prizes_by_25 <- pnbinom(n_submissions-n_successes, n_successes, prob = p_success)
prob_3_prizes_by_25
``````
Therefore, the probability that all three prizes will be awarded by the 25th submission is 0.4629059.