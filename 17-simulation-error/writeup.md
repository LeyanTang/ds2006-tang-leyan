# Homework 17
Code:
``````
library(ggplot2)

factor1_levels <- 2^(2:15)
factor2_levels <- c(0.01, 0.05, 0.10, 0.25, 0.50)

results_absolute <- data.frame()
results_relative <- data.frame()

for (level1 in factor1_levels) {
  for (p in factor2_levels) {
    for (experiment in 1:5) {
      x <- runif(rep)
      y <- runif(rep)
      inside_circle <- (x^2 + y^2) <= 1
      estimated_pi <- 4 * sum(inside_circle) / rep
      true_pi <- pi
      absolute_error <- abs(estimated_pi - true_pi)
      relative_error <- absolute_error / true_pi
      
      results_absolute <- rbind(results_absolute, data.frame(Factor1 = log2(level1), Factor2 = p, 
                                                             Experiment = experiment, Absolute_Error = absolute_error))
      results_relative <- rbind(results_relative, data.frame(Factor1 = log2(level1), Factor2 = p, 
                                                             Experiment = experiment, Relative_Error = relative_error))
    }
  }
}


absolute_error_plot <- ggplot(results_absolute, aes(x = Factor1, y = Absolute_Error, color = factor(Factor2))) +
  geom_path() +  
  labs(title = "Absolute Error in π Estimation",
       x = "Log2 Number of Simulations", y = "Absolute Error") +
  theme_minimal()

relative_error_plot <- ggplot(results_relative, aes(x = Factor1, y = Relative_Error, color = factor(Factor2))) +
  geom_path() +  
  labs(title = "Relative Error in π Estimation",
       x = "Log2 Number of Simulations", y = "Relative Error") +
  theme_minimal()

print(absolute_error_plot)
print(relative_error_plot)
``````

