# Homework 17
## The Importance of Estimating Probabilities

Estimating probabilities is a cornerstone of data science. It enables us to make informed decisions based on data and observations. Whether we're predicting stock market trends, determining the likelihood of a disease outbreak, or optimizing supply chain operations, probability estimation plays a central role.

**Absolute error** is a concept used in various fields, including data science, to quantify the magnitude of the difference between an estimated value and the true or expected value. It provides a straightforward way to measure how far off our estimation is from reality. In mathematical terms, absolute error is calculated as the absolute difference between the estimated value (often denoted as p̂) and the true value (denoted as p):

Absolute Error = |p - p̂|

Where "p" represents the true value.
"p̂" represents the estimated or calculated value.

Absolute error is a valuable measure because it gives you a clear sense of the magnitude of your estimation inaccuracies, regardless of whether you overestimated or underestimated the true value.

**Relative error**, on the other hand, provides a standardized way to express the accuracy of an estimation by comparing it to the true value. It is particularly useful when you want to understand how significant your estimation error is relative to the magnitude of the true value. Relative error is calculated as the ratio of the absolute error to the true value:

Relative Error = |p - p̂| / |p|

Where "p" represents the true value.
"p̂" represents the estimated or calculated value.

Relative error is beneficial because it scales the error to the size of the true value. It allows you to compare the accuracy of different estimations, especially when dealing with data of varying scales or magnitudes.


## Ploting the absolute error and relative error
Code:
``````
replicates <- 2^(2:15)
probabilities <- c(0.01, 0.05, 0.10, 0.25, 0.50)

# Initialize matrices to store absolute and relative errors with zeros
absolute_errors <- matrix(0, nrow = length(replicates), ncol = length(probabilities))
relative_errors <- matrix(0, nrow = length(replicates), ncol = length(probabilities))

for (i in 1:length(replicates)) {
  for (j in 1:length(probabilities)) {
    p <- probabilities[j]
    r <- replicates[i]
    p_hat <- rbinom(5000, r, p) / r
    absolute_errors[i, j] <- mean(abs(p_hat - p))
    relative_errors[i, j] <- mean(abs(p_hat - p) / p)
  }
}

# Create a plot of absolute errors
plot(log2(replicates), absolute_errors[, 1], ylim = range(absolute_errors), xlab = 'log2(Replicates)', ylab = 'Absolute Errors', type = 'n')

# Add lines and points for different probabilities
for (i in 1:length(probabilities)) {
  lines(log2(replicates), absolute_errors[, i], col = i, lwd = 1)
  points(log2(replicates), absolute_errors[, i], col = i, pch = 19)
}

# Create a legend for probabilities
legend("topright", legend = as.character(probabilities), col = 1:length(probabilities), pch = 19, title = "Probabilities")

# Create a plot of relative errors
plot(log2(replicates), relative_errors[, 1], ylim = range(relative_errors), xlab = 'log2(Replicates)', ylab = 'Relative Errors', type = 'n')

# Add lines and points for different probabilities
for (i in 1:length(probabilities)) {
  lines(log2(replicates), relative_errors[, i], col = i, lwd = 1)
  points(log2(replicates), relative_errors[, i], col = i, pch = 19)
}

# Create a legend for probabilities
legend("topright", legend = as.character(probabilities), col = 1:length(probabilities), pch = 19, title = "Probabilities")
axis(1, at = log2(replicates), labels = replicates)
``````

And there are the plots generated:
1. Absolute error

![image](abs.png)

2. Relative error

![image](rel.png)

If changing the y-axis to the log2 scale, the plots look like as below:

1. Absolute error

![image](abs2.png)

2. Relative error

![image](rel2.png)

It shows a linear relationship between the IV and DV.
