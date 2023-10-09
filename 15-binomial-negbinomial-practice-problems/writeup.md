# Homework 15
## Question 1

In this scenario, each student's outcome is independent of the others, meaning that students can be replaced. We will use the binomial distribution to calculate the probability that 3 or fewer students do not complete out of 29 students.

We use these functions in R to calculate such probability:
``````
prob_fewer_than_3 <- 1 - pbinom(25, 29, 0.7)
``````
The probability that 3 or fewer students do not complete the degree is 0.01209502.

## Question 2

We can use the R code to solve this problem:
``````
p_success <- 0.7
years <- 20
students_to_advise <- 10
simulations <- 100000

# Initialize a counter for retirements
retirement_count <- 0

# Run the simulation
for (sim in 1:simulations) {
  students_remaining <- students_to_advise
  
  for (year in 1:years) {
    if (year <= students_to_advise) {
      students_remaining <- students_to_advise - year + 1
    }
    
    # Randomly determine if a student completes their degree this year
    students_completed_this_year <- rbinom(students_remaining, size = 1, prob = p_success)
    students_remaining <- students_remaining - sum(students_completed_this_year)
    
    # If the professor reaches 0 remaining students, they retire
    if (students_remaining <= 0) {
      retirement_count <- retirement_count + 1
      break
    }
  }
}

# Calculate the probability of retirement within 20 years
probability_retirement <- retirement_count / simulations
cat("Estimated probability of retirement in 20 years:", probability_retirement, "\n")

``````

The probability that the professor will retire in 20 years is 1.

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