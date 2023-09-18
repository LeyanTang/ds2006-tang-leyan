# Homework 9
## Qustion 1

- P(Netflix) = 0.44
- P(Hulu) = 0.35
- P(Netflix \& Hulu) = 0.2

Therefore, using the addition rule, 

P(Netflix or Hulu) 
= P(Netflix) + P(Hulu) - P(Netflix \& Hulu)
 = 0.44 + 0.35 - 0.2 
 = 0.59

## Question 2

Because d + 0.8 = 1, so d is 0.2, then c is 0.05 (0.2 - 0.15), a is 0.55 (0.6 - 0.05), b is 0.25 (0.4 - 0.15).

- P(Apple | Laptop)
= 0.55 / 0.8 = 0.6875
- P(Laptop | Apple)
= 0.55 / 0.6 = 0.9167
- P(Laptop and Apple)
= 0.55

## Question 3

If the two variables are independent, P(Laptop and Apple) should be equal to P(Laptop) times P(Apple). However, since P(Laptop) times P(Apple) is 0.48, which is not equal to the joint probability, the two variables are not independent.

## Question 4

Since the three machines generate the same number of widgets, we can simply sum their defect rates and divide it by 3 to get the probability of 0.037.

## Question 5

Let:
- \(N\) be the number of widgets produced by machine C.
- \(2N\) be the number of widgets produced by machine B.
- \(4N\) be the number of widgets produced by machine A.

We can calculate the total number of defective widgets produced by each machine:
- Machine A: \(4N \times 0.1\) defective widgets.
- Machine B: \(2N \times 0.01\) defective widgets.
- Machine C: \(N \times 0.001\) defective widgets.

The total defective widgets produced overall is given by:
\[
\text{Total defective widgets} = (4N \times 0.1) + (2N \times 0.01) + (N \times 0.001)
\]

The total number of widgets produced overall is:
\[
\text{Total widgets} = 4N + 2N + N
\]

Finally, we can calculate the probability that a randomly selected widget is defective as:
\[
P(\text{Defective}) = \frac{\text{Total defective widgets}}{\text{Total widgets}} = \frac{(4N \times 0.1) + (2N \times 0.01) + (N \times 0.001)}{4N + 2N + N}
\]

The probability is 0.06.

## Question 6

$P(A|Defective)$ is equal to $P(Defective|A) * P(A) / P(Defective)$. 

Since $P(Defective)$ is 0.06, $P(A)$ is 4/7 (0.57), $P(Defective|A)$ is 0.1, then $P(Defective|A)$ is equal to **0.952**.

## Question 7

#### P( fair coin selected | flip sequence = TTT )

To find the probability that a fair coin was selected given the flip sequence TTT, we can use Bayes' Theorem. Let:

- A be the event of selecting a fair coin.
- B be the event of getting the flip sequence TTT.

We want to find P(A | B).

Using Bayes' Theorem:

\[P(A | B) = \frac{P(B | A) \cdot P(A)}{P(B)}\]

- P(A) is the probability of selecting a fair coin, which is 4/5 since there are 4 fair coins out of 5.
- P(B | A) is the probability of getting TTT with a fair coin. The probability of getting tails with a fair coin is 0.5, so \(P(B | A) = 0.5^3 = 0.125\).

For calculate P(B):

\[P(B) = P(B | Fair Coin) \cdot P(Fair Coin) + P(B | Biased Coin) \cdot P(Biased Coin)\]

- P(Fair Coin) is the probability of selecting a fair coin, which is 4/5.
- P(Biased Coin) is the probability of selecting the biased coin, which is 1/5.
- P(B | Fair Coin) is 0.125.
- P(B | Biased Coin) is 0.25^3 = 0.015625.

So:

\[P(A | B) = \frac{0.125 \cdot (4/5)}{0.103125} \approx 0.9697\]

So, the probability that a fair coin was selected given the flip sequence TTT is approximately **96.97%**.


#### P( 2 heads in 3 flips | biased coin selected )
Let X be the number of heads in 3 flips with the biased coin.

\[P(X = 2 | Biased Coin) = \binom{3}{2} \cdot (0.75)^2 \cdot (0.25)^1 = 3 \cdot 0.5625 \cdot 0.25 = 0.421875\]

So, the probability of getting 2 heads in 3 flips when the biased coin is selected is approximately **42.19%**.
