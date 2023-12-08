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


## 4. Continuous Distributions


## 5. Empirical CDF



## 6. Estimation of CDF and PDF from data


## 7. Communicating uncertainty about parameter estimates


## 8. Extra Credit
Because according to QQ-plot, we can see the relationship between the theoretical quantiles against sample quantiles generated from the model, if the model fits the data well then we expect the plot is close to a 45-degree line. Therefore, I added the 45-degree line to the two plots that found that in Plot B, the points closely align with the 45-degree reference line, indicating a higher degree of agreement between the data and the **gamma distribution**, compared to the normal distribution. 

![image](q8.png)