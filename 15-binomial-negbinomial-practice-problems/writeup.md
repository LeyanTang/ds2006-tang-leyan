# Homework 15
## Question 1

In this scenario, each student's outcome is independent of the others, meaning that students can be replaced. We will use the binomial distribution to calculate the probability that 3 or fewer students do not complete out of 29 students.

We use these functions in R to calculate such probability:
``````
p_success <- 0.7
n_trials <- 29

prob_3 <- pbinom(3, size = n_trials, prob = p_success)
prob_3
``````
The probability that 3 or fewer students do not complete the degree is 3.342193e-11.

## Question 2

Since the professor decides to stop advising after a certain number of students, it implies that there is no replacement. The professor's interactions with students are not independent from year to year, and there is no replenishment of students.

We can use the R code to solve this problem:
``````
p_success <- 0.7
years <- 20
students_to_advise <- 10

prob_retire_in_20_years <- dbinom(students_to_advise, size = years, prob = p_success)
prob_retire_in_20_years
``````

The probability that the professor will retire in 20 years is 0.03081708.

## Quesiton 3

The negative binomial distribution is appropriate for situations where we want to calculate the probability of a specific number of successes (in this case, 3 correct solutions) occurring before a specific number of failures (25 submissions) in a sequence of independent trials. In this scenario, we are interested in achieving 3 successes before 25 submissions, and each submission is considered an independent trial.

We can use the R codes as follows:
``````
p_success <- 0.1
n_successes <- 3
n_submissions <- 25

prob_3_prizes_by_25_submissions <- dnbinom(n_successes, size = n_successes, prob = p_success)
prob_3_prizes_by_25_submissions
``````
Therefore, the probability that all three prizes will be awarded by the 25th submission is 0.00729.