# Homework 12
## Question 1

No, the series will not be exchangeable because of the homefield advantage. When the series is played exclusively at team A's stadium, Team A is more likely to win games when they are at home, so the sequences that involve Team A wins will be more likely than Team B wins. As a result, the probabilities associated with different sequences will not be equal, and the series is no longer exchangeable.

## Question 2

No, the series will still not be exchangeable. This is because the series played in alternating stadiums will still result in the outcomes where teams play in their homefield being higher in probability. For example, given the stadium sequence, the result of ABABA will be more likely than other outcomes given the homefield advantage.

## Question 3

Yes the series will be exchangeable, because even through there's homefield advantage for team A when the game is played in stadium A, the probability of Team A winning still remains constant throughout the whole game, so does Team B's probability of winning when played in their field. This will result in no difference in the ordering of the outcomes, and so the series will be exchangeable.

## Question 4

In the book, it points out that `Probability` refers to the belief, `likelihood` to the uncertainty of a single event under different circumstances, and chance is a concept pertaining to a `Bernoulli` series. Therefore, in this case, 

- Probability: 
1. $$P(\theta_i)$. This represents the prior probability, which is a constant belief about the parameter $\theta_i$ before considering the specific series outcome.
2. $P(\theta_i | \text{ Series outcome is } ABAAA\text{ })$. This represents the conditional probability, denoted as $P$, of the unknown parameter $\theta_i$ (where $i$ could be A or B) given the observed series outcome "ABAAA." It reflects our updated belief or probability assessment of whether the series is played in stadium A or B based on the specific observed sequence. 

- Likelihood: $P(\text{Series outcome is } ABAAA\text{ }|\theta_i)$. This represents the likelihood, denoted as $P$, of observing the series outcome "ABAAA" given a specific value of the parameter $\theta_i$. It measures how well the data (series outcome) supports different values of the parameter. 

- Chance: $P(\text{ Series outcome is } ABAAA\text{ })$. In the context of a Bernoulli series, this term represents the overall probability of observing the series outcome "ABAAA" regardless of whether it is played in stadium A or B. It can be associated with the concept of "chance" as it quantifies the probability of observing a specific sequence of events in a series of Bernoulli trials.
