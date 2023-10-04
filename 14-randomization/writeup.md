# Homework 14
## Question 1

In the medical trial, different assumptions about exchangeability can lead to varying results. People's decisions regarding treatment might be influenced by their knowledge of recovery rates by gender, which can introduce the potential for selection bias. To address this issue and reduce the risk of Simpson's paradox, carefully designed experiments "doing" sex through balanced treatment allocation among different sex groups are crucial. However, it's worth noting that while these experimental approaches, like randomization, can alleviate some of the problems, they may also introduce other biases.

On the other hand, in the agricultural trial, the primary challenge lies in the uncontrollability of certain factors, such as crop height. Farmers have no means to predict whether the crop will grow tall or short. Moreover, in the context of the agricultural trial, stratification becomes meaningless due to the unpredictable nature of crop height. Simpson's paradox, which involves stratification and unexpected shifts in results, doesn't come into play. Even without categorizing into specific height ranges, the preference for the black variety remains consistent. Essentially, in the agricultural trial, the "seeing" scenario doesn't encounter Simpson's paradox because stratification is meaningless in hindsight.


## Question 2

Agricultural Trial Figure:
``````
  +--- Variety ---+
  |               |
  |               |
  V               V
 Yield < ------ Height
``````

## Question 3

``````
# Set the total number of trial participants
total_participants <- 100

# Set the number of participants with diabetes
diabetic_participants <- 25

# Randomly assign treatment to all participants
treatment_assignment <- sample(c("T", "T^c"), total_participants, replace = TRUE)

# Create a data frame for the randomization table with intuitive column names
randomization_table <- data.frame(
  Diabetes_Status = rep(c("With Diabetes", "Without Diabetes"), c(diabetic_participants, total_participants - diabetic_participants)),
  Treatment = treatment_assignment
)

# Print the randomization table
cat("Randomization Table:\n")
print(randomization_table)

# Create a contingency table
contingency_table <- table(randomization_table$Diabetes_Status, randomization_table$Treatment)
cat("\nContingency Table:\n")
print(contingency_table)

``````
- Randomization table:
Diabetes_Status Treatment
1      With Diabetes       T^c
2      With Diabetes         T
3      With Diabetes         T
4      With Diabetes         T
5      With Diabetes       T^c
6      With Diabetes         T
7      With Diabetes       T^c
8      With Diabetes         T
9      With Diabetes       T^c
10     With Diabetes       T^c
11     With Diabetes         T
12     With Diabetes       T^c
13     With Diabetes       T^c
14     With Diabetes       T^c
15     With Diabetes         T
16     With Diabetes       T^c
17     With Diabetes         T
18     With Diabetes       T^c
19     With Diabetes       T^c
20     With Diabetes         T
21     With Diabetes         T
22     With Diabetes       T^c
23     With Diabetes       T^c
24     With Diabetes       T^c
25     With Diabetes         T
26  Without Diabetes       T^c
27  Without Diabetes         T
28  Without Diabetes       T^c
29  Without Diabetes       T^c
30  Without Diabetes         T
31  Without Diabetes         T
32  Without Diabetes         T
33  Without Diabetes       T^c
34  Without Diabetes       T^c
35  Without Diabetes       T^c
36  Without Diabetes         T
37  Without Diabetes         T
38  Without Diabetes         T
39  Without Diabetes       T^c
40  Without Diabetes         T
41  Without Diabetes         T
42  Without Diabetes         T
43  Without Diabetes         T
44  Without Diabetes       T^c
45  Without Diabetes       T^c
46  Without Diabetes       T^c
47  Without Diabetes         T
48  Without Diabetes         T
49  Without Diabetes       T^c
50  Without Diabetes         T
51  Without Diabetes         T
52  Without Diabetes       T^c
53  Without Diabetes       T^c
54  Without Diabetes       T^c
55  Without Diabetes       T^c
56  Without Diabetes         T
57  Without Diabetes         T
58  Without Diabetes       T^c
59  Without Diabetes       T^c
60  Without Diabetes       T^c
61  Without Diabetes       T^c
62  Without Diabetes         T
63  Without Diabetes       T^c
64  Without Diabetes         T
65  Without Diabetes       T^c
66  Without Diabetes         T
67  Without Diabetes       T^c
68  Without Diabetes         T
69  Without Diabetes       T^c
70  Without Diabetes         T
71  Without Diabetes       T^c
72  Without Diabetes         T
73  Without Diabetes         T
74  Without Diabetes         T
75  Without Diabetes       T^c
76  Without Diabetes       T^c
77  Without Diabetes         T
78  Without Diabetes         T
79  Without Diabetes         T
80  Without Diabetes         T
81  Without Diabetes       T^c
82  Without Diabetes         T
83  Without Diabetes       T^c
84  Without Diabetes         T
85  Without Diabetes       T^c
86  Without Diabetes         T
87  Without Diabetes         T
88  Without Diabetes         T
89  Without Diabetes         T
90  Without Diabetes       T^c
91  Without Diabetes         T
92  Without Diabetes         T
93  Without Diabetes         T
94  Without Diabetes         T
95  Without Diabetes       T^c
96  Without Diabetes         T
97  Without Diabetes         T
98  Without Diabetes       T^c
99  Without Diabetes         T
100 Without Diabetes       T^c

- Contingency table:
                
|                |   T   |  T^c  |
|----------------|-------|-------|
| With Diabetes  |  11   |  14   |
| Without Diabetes |  42   |  33   |



