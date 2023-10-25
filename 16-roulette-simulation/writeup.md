# Homework 16
## Introduction to Roulette
Roulette is a popular and iconic casino game that has been captivating players for centuries. It is a game of chance that originated in France in the 18th century. The name "roulette" itself means "little wheel" in French, and that's exactly what the game revolves around – a spinning wheel. The game is designed for players to bet on where a small ball will land once the wheel comes to a stop.

Players place their bets on various options, including specific numbers, groups of numbers, colors (red or black), odd or even numbers, or high and low ranges. The game's outcome is purely based on chance, as the ball's landing spot is completely unpredictable.

##The Martingale Strategy

The Martingale strategy is a betting system frequently employed in casino games, notably in games like roulette. This approach is characterized by its progressive betting nature, with the fundamental premise of recovering losses and securing a profit equivalent to the initial wager. Here is a structured breakdown of the Martingale strategy:

1. **Initial Wager**: The strategy commences with an initial bet placed on an outcome with approximately a 50/50 probability of success, such as betting on red or black in a game of roulette.
2. **Doubling of Bets Following Losses**: In the event of a loss on the initial bet, the strategy mandates doubling the wager in the subsequent round.
3. **Iterative Doubling with Each Consecutive Loss**: The process continues, with each loss triggering a doubling of the bet in a quest to recoup prior losses.
4. **Resetting After a Win**: Upon achieving a winning outcome, the strategy prompts a return to the initial wager.

The fundamental concept behind the Martingale strategy is the belief that, over time, a winning outcome will eventually be realized, which would subsequently offset all prior losses, ultimately yielding a profit equivalent to the original wager.

## Average Earnings (resubmitted)

- Plot 1: The loser plot:

![image](p1.png)

This plot represents a series of games where the Martingale strategy led to a losing outcome. The x-axis, labeled "Game Index," tracks the progression of games, while the y-axis, labeled "Budget," represents the player's budget over time.

The player starts with an initial budget of $200. The bets are adjusted based on previous outcomes and the maximum wager limit. In this series, the outcome of the first game is "red," which results in a bet of $1.

Subsequent bets and outcomes are calculated using the Martingale strategy. As the player experiences losses, the bets are doubled in an attempt to recover previous losses.

The player's budget fluctuates over time, and as seen in this example, it eventually reaches zero, indicating a losing session.
The series ends when the player's budget falls to zero, which is a stopping rule defined by the Martingale strategy.

- Plot 2: The winner plot:

![image](p2.png)

This plot, on the other hand, represents a series of games where the Martingale strategy led to a winning outcome. It follows the same axes and labels as the first plot, but the outcome is different. Here's an interpretation:

Similar to the first plot, the player starts with a budget of $200 and applies the Martingale strategy.

In this series, the first game's outcome is "red," resulting in a bet of $1. Unlike the "Loser" series, the player experiences favorable outcomes and, as a result, doesn't need to double the bets to recover losses. The player's budget gradually increases as more games are played.

The series continues until the player's budget reaches or exceeds a specified winning threshold of $300, at which point the player stops playing.

## Earnings evolvement over number of wager

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

This code visualizes how a player's earnings change over repeated plays while considering the defined rules and constraints. It provides insights into potential game outcomes within these parameters:


![image](rep1000.png)


## Parameter changing
### Changing starting budget
Holding all others stopping rules constant (winning_threshold <- 300, max_games <- 1000, max_wager <- 100), the first parameter to alter while others being constant is the starting budget. 

Here's the code to generate the plot:
``````
# Load required libraries
require(magrittr)

# Define functions as provided in your code

# Function to run the simulation for different starting budgets
run_simulation_for_budgets <- function(starting_budget, winning_threshold, max_games, max_wager, num_simulations) {
  average_profits <- numeric(length(starting_budget))
  
  for (i in 1:length(starting_budget)) {
    set.seed(i)  # Set a different seed for each simulation
    ledger <- one_series(max_games, starting_budget[i], winning_threshold, max_wager)
    average_profits[i] <- mean(replicate(num_simulations, profit(ledger)))
  }
  
  return(average_profits)
}

# Set the parameters
starting_budget <- seq(100, 500, by = 100)  # Starting budget range
winning_threshold <- 300
max_games <- 1000
max_wager <- 100
num_simulations <- 1000  # Number of simulations to run for each budget

# Run the simulation for different starting budgets
average_profits <- run_simulation_for_budgets(starting_budget, winning_threshold, max_games, max_wager, num_simulations)

# Visualize how changing starting budget affects profits
plot(starting_budget, average_profits, type = "l", lwd = 2, xlab = "Starting Budget", ylab = "Average Profit",
     main = "Effect of Starting Budget on Average Profit")

``````

![image](startingbudget.png)

The first graph in our analysis displays the impact of varying starting budgets on the average profit obtained from a gambling scenario. The x-axis represents different starting budgets, while the y-axis shows the average profit. The simulation was run with starting budgets ranging from $100 to $500 in increments of $100. The results show that as the starting budget increases, the average profit tends to rise as well, and \$200 would have the higest averge profit and remains flat after \$300. This is expected, as a larger initial budget provides more resilience against losses and allows for longer gameplay. However, it's essential to remember that there are diminishing returns, and the relationship between starting budget and average profit may not be linear.

Using the same coding logic, I generated the other three plots by changing the three parameters:

### Changing winning_threshold

Holding all other stopping rules constant (starting_budget <- 200
, max_games <- 1000, max_wager <- 100), I used the same for-loop logic to see how the winnning_threshold would affect the profit, the plot looks like this:

![image](winningthreshold.png)

- Increase to \$400: Initially, as the winning threshold is elevated to \$400, the average profit demonstrates a substantial increase. This pattern is in alignment with a more conservative gambling approach. Players, when setting a higher threshold, become inclined to cease their gambling endeavors once they have achieved or surpassed this more substantial profit level. Consequently, the simulation illustrates an increase in average profit when transitioning from a lower to a \$400 threshold.

- Decrease Beyond \$400: However, a noteworthy observation within the simulation results is that once the winning threshold surpasses \$400 and reaches higher levels, the average profit begins to decline. This decline is indicative of the diminishing returns associated with overly conservative gambling strategies. Setting an excessively high winning threshold might prolong the gaming session and restrict opportunities for realizing profits, potentially leading to a decrease in the average profit.

### Changing max games
Holding all other stopping rules constant (starting_budget <- 200
, winning_threshold <- 300 max_wager <- 100), I used the same for-loop logic to see how the max_games would affect the profit, the plot looks like this:

![image](maxgames.png)

- Initial Increase: As the "max_games" parameter increases, the plot demonstrates a clear uptick in the average profit. This trend aligns with the fundamental notion that a higher value for "max_games" provides more extensive gaming opportunities. With a greater number of games available for play, the chances to accumulate profits multiply, contributing to the initial surge in average profit.

- Plateau Phase: Notably, as the "max_games" parameter reaches an approximate value of 900, the average profit enters a phase of relative stability. This plateau effect signifies that beyond a certain threshold, further extending the maximum number of games does not markedly influence the average profit. The profitability rate maintains consistency, indicating diminishing returns in terms of profit growth.

- Subsequent Decline: The plot highlights a decrease in average profit as "max_games" continues to increase, eventually reaching around 1250. This decline in profit at higher values of "max_games" can be attributed to several factors. Extended gaming sessions elevate the likelihood of encountering unfavorable sequences, which lead to more frequent losses. Moreover, prolonged gameplay exposes players to increased risks and, in some instances, substantial losses, contributing to the observed decline in average profit.

### Changing max wager

Holding all other stopping rules constant (starting_budget <- 200
, winning_threshold <- 300, max_games <- 1000), I used the same for-loop logic to see how the max_wager would affect the profit, the plot looks like this:

![image](maxwager.png)

- Initial Increase: As the "max_wager" parameter is augmented, the plot displays an initial increase in average profit. This trend can be attributed to the fact that a higher maximum wager permits more substantial bets, potentially leading to more significant wins if luck is favorable.

- Stabilization Phase: Following the initial increase, there is a phase of relative stability in average profit. The profit remains relatively constant as "max_wager" is further increased. This phase suggests that beyond a certain threshold, raising the maximum wager amount does not significantly influence the average profit. Profitability stabilizes as a result of this limit, and the potential gains do not increase at the same rate as the wagers.

- Subsequent Decline: Interestingly, as the "max_wager" parameter continues to rise, the plot demonstrates a decline in average profit. This decrease in profit at higher values of "max_wager" can be attributed to heightened risk exposure. Larger wagers may lead to more substantial losses in unfavorable game outcomes, resulting in the observed decline in average profit.

## Limitations of this simulation
- Limited Exploration of Parameters: The simulation explores a predefined set of parameters, such as the starting budget and winning threshold, limiting the generalizability of the results.
- Oversimplification of Betting Strategy: The simulation employs a simplified betting strategy, the Martingale system, which may not accurately represent the diversity of betting strategies used by real players. 
- Idealized Casino Rules: Different casinos may have varying rules and policies, such as maximum bet limits and payout structures. The simulation does not account for these variations, assuming uniform conditions.
- Risk of Short-Term Emphasis: The simulation may give the impression that the Martingale strategy is profitable in the short term, but it does not address the long-term risks associated with this strategy, especially during extended losing streaks.

In summary, the Martingale strategy presents a structured approach to betting in casino games. While it may appear to offer a straightforward path to profit, prudence dictates a comprehensive understanding of its risks and the necessity of careful bankroll management when adopting this strategy.