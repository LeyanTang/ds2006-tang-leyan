# Homework 3 - The birthday Problem
## Problem 1
- The R script to solve this riddle would be:
set.seed(1)
one_roster <- function(S = 11){
  birthdays <- sample(x = 365,size = S,replace = TRUE)
  any(duplicated(birthdays))
}
R <- 100000
out <- rep(NA,R)
for(i in 1:R){
  out[i] <- one_roster()
}
prob <- mean(out)
## Problem 2
The `set.seed` command sets the seed for the random number generator used in this simulation. If we use the same seed, we will get the same sequence of random numbers every time we run the simulation. This is helpful for others reproduce the same result.
## Problem 3
`R` represents the number of simulations to be performed. The more rounds of simulation, the more accurate the probability estimates will be.
## Problem 4
The shared birthday probability of a class size of 28, according to my simulation, is 65.403%. Here's the adapted code:
set.seed(1)

one_roster <- function(S = 28){
  birthdays <- sample(x = 365, size = S, replace = TRUE)
  any(duplicated(birthdays))
}

R <- 100000
out2 <- replicate(R, one_roster())
mean(out2)
## Problem 5
- The plot shows the trend between the class size and the probability:
![image](birthday%20plot.png)
## Problem 6
It returns the first instance (enabled by the MIN function) of a duplicated birthday, indicating the index at which the first shared birthday appears within the generated set.

 