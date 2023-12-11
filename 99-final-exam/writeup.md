# DS 2006 Final Exam
- **Name**: Leyan Tang
- **ComputingID**: gnv2nh
- **Date**: 11:30AM, December 13th, 2023

## 0. Rules of probability
### A. Probability table
|             | Depression score < 13   | Depression score >= 13 | All  |
| ----------- | ----------- | ----------- | ----------- |
| **Planned vaginal delivery** | 0.864   | 0.096   | 0.96 |
| Row |0.9| 0.1  | |
| Col | 0.96 | 0.96  | |
| **Planned caesarean section delivery** | 0.036  |0.004   | 0.04 |
| Row | 0.9  | 0.1  | |
| Col | 0.04 |0.04 | |
| **All** | 0.9  |  0.1  | 1 |

### B. Table update 1
|             | Depression score < 13   | Depression score >= 13 | All  |
| ----------- | ----------- | ----------- | ----------- |
| **Planned vaginal delivery** | 0.63    | 0.07    | 0.7 |
| Row |0.9| 0.1  | |
| Col | 0.7 | 0.7  | |
| **Planned caesarean section delivery** | 0.27  |0.03   | 0.3 |
| Row | 0.9  | 0.1  | |
| Col | 0.3 |0.3 | |
| **All** | 0.9  | 0.1  | 1 |

### C. Table update 2
|             | Depression score < 13   | Depression score >= 13 | All  |
| ----------- | ----------- | ----------- | ----------- |
| **Planned vaginal delivery** | 0.63    | 0.07    | 0.7 |
| Row |0.9| 0.1  | |
| Col | 0.71 | 0.61  | |
| **Planned caesarean section delivery** | 0.255  |0.045   | 0.3 |
| Row | 0.85  | 0.15  | |
| Col | 0.29 |0.39 | |
| **All** | 0.885 | 0.115  | 1 |

### D.Validation
No, the data that match the depression rates could not illustrate the reasoning that the caesarean section delivery leads to higher rates of depression. This is because the data are collected based on the prior belief that within the caesarean section method there's a higher depression rate (15%) already compared with the vaginal delivery (10%), and the unequal split of the two groups (7:3) further makes the caesarean seem higher in the depression rate as it has less significant representation. 

Additionally, there might be other confounding with other factors that haven't be explored, so controlled experiments need to be run based on some fixed factors to draw a concrete conclusion, instead of relying merely on the observational data. For example, such factors may be relevant with the health conditions, age groups, regions of the mother that planned the delivery methods.

## 1. Simulation


## 2. Diagnostics
### A. Probability table
|             | D+    | D- | Margin  |
| ----------- | ----------- | ----------- | ----------- |
| **T+** | 0.00085    | 0.04995    | 0.0508 |
| Row |0.0167| 0.9833  | |
| Col | 0.85 | 0.05  | |
| **T-** | 0.00015  |0.94905   | 0.9492 |
| Row | 0.00016  | 0.99984  | |
| Col | 0.15 |0.95 | |
| Margin | 0.001  | 0.999   | 1 |

### B. Negative predictive value
Based on the table above, P(D-|T-) is the row probability of `0.99984`.

### C. Positive predictive value

Based on the table, I calculated that P(D+|T+) is 0.85\*P(D+)/(0.05 + 0.8\*P(D+)), and the plot is as below:

![image](q2.png)

## 3. Mixture Distributions
### A. 90th percentile
I used the following code to calculate the 90th percentile, since the simulation method is easier:
``````
rhc <- function(n){ rgamma(n,shape=2,scale=2)*rbinom(n,1,.4) }
simulations <- rhc(1000)
percentile_90_sim <- quantile(simulations, 0.9)
print(percentile_90_sim)
``````
The computed result is `5.340455` based on 1000 simulations. 

### B. Class average yearly hospital charge
![image](q3.png)

Here's the code that I used for this density plot:
``````
class_size <- 30
num_classes <- 1000
charges_per_student <- rhc(class_size * num_classes)

class_average_charges <- tapply(charges_per_student, rep(1:num_classes, each = class_size), mean)
class_average_charges <- class_average_charges * class_size

density <- density(class_average_charges)
plot(density, main = "Density Plot of Class Average Yearly Hospital Charge",
     xlab = "Average Yearly Hospital Charge (in thousands of dollars)", col = "skyblue", lwd = 2)
``````
As I chose the total number of classes to be 1000, I first calculated the average charge per student for each class and then timed the class size of 30 for the class average number for all 1000 classes, and then generated the plot.

### C. Probability of less than 10 students with zero charges

Following the simulation method in B, I increased the class number to be 10000, and looping through each class to calculate the number of 0-charge students. Finally, out of the loop, I calculated the probability of less than 1/3 students having zero charges in a randomly selected class to be `0.001`.
``````
class_size <- 30
num_classes <- 10000
charges_per_student <- rhc(class_size * num_classes)
charges_matrix <- matrix(charges_per_student, nrow = num_classes, byrow = TRUE)

count_less_than_third <- 0
for (i in 1:num_classes) {
  count_zero_charges <- sum(charges_matrix[i, ] == 0)
  if (count_zero_charges < class_size / 3) {
    count_less_than_third <- count_less_than_third + 1
  }
}

probability_less_than_third <- count_less_than_third / num_classes
print(probability_less_than_third)
``````
## 4. Continuous Distributions


## 5. Empirical CDF



## 6. Estimation of CDF and PDF from data


## 7. Communicating uncertainty about parameter estimates


## 8. Extra Credit
Because according to QQ-plot, we can see the relationship between the theoretical quantiles against sample quantiles generated from the model, if the model fits the data well then we expect the plot is close to a 45-degree line. Therefore, I added the 45-degree line to the two plots that found that in Plot B, the points closely align with the 45-degree reference line, indicating a higher degree of agreement between the data and the **gamma distribution**, compared to the normal distribution. 

![image](q8.png)