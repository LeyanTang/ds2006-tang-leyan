# Homework 16
## Earnings evolvement over number of games

I used the following code to generate the average earnings:
``````
# Set the parameters
  starting_budget <- 200
  winning_threshold <- 300
  max_games <- 1000
  max_wager <- 100
  R <- 1000  # Number of replicates
  output <- rep(NA, R)
  
  # Create a matrix to store the earnings data for all replicates
  earnings_matrix <- matrix(NA, nrow = R, ncol = max_games)
  
  # Run multiple replicates and store earnings data
  for (r in 1:R) {
    simulation_result <- one_series(max_games, starting_budget, winning_threshold, max_wager)
    earnings <- simulation_result$ending_budget  # No need to subtract starting budget
    # Pad earnings with NAs to match max_games
    earnings <- c(earnings, rep(NA, max_games - length(earnings)))
    earnings_matrix[r, ] <- earnings
  }
  
  # Create a line plot to visualize earnings over wagers
  library(ggplot2)
  earnings_df <- data.frame(GameIndex = 0:(max_games - 1), Earnings = colMeans(earnings_matrix, na.rm = TRUE))
  
  ggplot(earnings_df, aes(x = GameIndex, y = Earnings)) +
    geom_line(size = 1, color = "blue") +
    labs(x = "Wager Number", y = "Earnings") +
    ggtitle(paste("Earnings Evolution Over Wagers (Repetitions:", R, ")")) +  # Include the number of repetitions in the title
    geom_hline(yintercept = starting_budget, linetype = "dashed", color = "red") +  # Set the starting budget line to 200
    geom_hline(yintercept = winning_threshold - starting_budget, linetype = "dotted", color = "green") +  # Add earnings cap line at $300
    geom_vline(xintercept = max_games - 1, linetype = "dotted", color = "blue") +  # Max games (number of wagers) on x-axis as dotted
    theme_minimal()
  
``````

### Explanation:

In this code, I set parameters for a computer simulation that models a game with specific rules. These parameters are as follows:

- 'Starting Budget (starting_budget)': The player begins with $200.
- 'Winning Threshold (winning_threshold)': The player aims to reach $300 in earnings.
- 'Maximum Games (max_games)': The simulation runs for a maximum of 1000 games.
- 'Maximum Wager (max_wager)': The player can bet up to $100 in a single round.
- 'Number of Replicates (R)': The simulation is repeated 1000 times.

The goal is to observe the player's earnings over multiple iterations, adhering to the defined rules.

The code works as follows:

- An 'earnings_matrix' is created to store earnings data for all replicates (1000 rows). Each row represents a game with a maximum of 1000 columns, ensuring uniform data structure.

- A loop runs the simulation 1000 times, where the 'one_series' function calculates earnings based on the parameters. Earnings are recorded in the 'earnings_matrix,' with padding for consistent dimensions.

- After all simulations, a line plot is generated using 'ggplot2.' The x-axis shows the number of plays, and the y-axis represents earnings.

- Axes and the title are labeled, including the number of repetitions (1000).

- 'geom_hline' adds a dashed line at the starting budget ($200), showing where the player begins.

- 'geom_vline' includes a dotted line at the maximum number of games (1000) to illustrate the limit on wagers.

- The plot's theme is set to 'minimal' for a clear presentation.

This code visualizes how a player's earnings change over repeated plays while considering the defined rules and constraints. It provides insights into potential game outcomes within these parameters:


![image](rep1000.png)


## Parameter changing


## Limitations of this simulation
