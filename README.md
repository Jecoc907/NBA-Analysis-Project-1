# NBA-Analysis-Projects

## Introduction
In this assignment, we are interested in the winning factors for a NBA team by looking at their advanced statistics. We utilized a linear regression on team’s win rate with three variables: Age (Age), Strength of Schedule (SOS), and Simple Rating System (SRS). (Age: players’ age on Feb 1 of the season / SOS: a rating of stren/ SRS: a team rating that takes into account average point differential and strength of schedule. The rating is denominated in points above/below average, where zero is average.) We gathered our dataset which contains 240 observations with 29 columns (we combined the last 8 NBA seasons) from basketball-reference.com (https://www.basketball-reference.com/leagues/NBA_2020.html).![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/558eebc1-0b8b-4a0f-be18-07db0b49f96c)

## Preliminary Analysis
In the preliminary analysis, we used describe() command and histogram to learn the distribution of NBA team’s win rate. From our result, we learned that it averaged 49.93%; the min of 12.20% and max of 89%. Attached is the output of the code.

![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/48c432cc-a28a-4110-bb18-89467ad3df02)
![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/0740af60-eaed-448b-bd5c-59424016c419)

## Variable Selection
Next, since we are interested in regressing on win rate, which is a continuous numerical variable, we decided to use a linear regression. After that, we have to find the most significant variables to be included in the model. The approach we took was similar to a backward stepwise regression while we first included all numerical variables and eliminating the insignificant ones one by one due to either high VIF value or high p-values. We ended up with ‘Age’, ‘SOS’, and ‘SRS’ are included in the final regression model. Although ‘SRS’ is a rating system that takes into account strength of schedule, we don’t see a high correlation between the two variables. Therefore, our final model is Win_rate = Beta_0 + Beta_1(Age) + Beta_2 (SOS) + Beta_3(SRS) + error term.

## Cross-Validation
(1) Validation Set Approach

![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/0bf74a70-99e1-4c3b-b931-92789e2e752c)

(2) K-fold Cross-Validation

![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/c1ef4903-7b14-45df-877b-4d06a4a568f9)

(3) Leave-One-Out Cross Validation

![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/3921c95e-cd64-47c5-9a74-e835abde788a)

![image](https://github.com/Jecoc907/NBA-Analysis-Project-1/assets/71363412/011aff8b-babb-417e-88ab-c5d509736c36)

## Result
Overall, our linear model’s prediction ability with unseen data is decent with an average score over 0.9 and low RMSE. However, among the three cross-validation methods, we believe the validation-set and k-fold cross-validation approach are more preferable than leave-one-out cross validation method in our case. Due to our small sample size, the estimate of model performance from LOOCV may be less stable and more sensitive to variations in the dataset. In our case, we could not get the average score of LOOCV. At the time, because of the small sample size, it led us to conclude that k-fold cross validation is more suitable than validation-set in our case. We would prefer k-fold cv because we don't want to leave 20-25% of our data to train our model (since we are looking at all the advanced statistics from one NBA season, we will only have 30 observations from 30 NBA teams every year.). In conclusion, we will prefer k-fold cross-validation approach.
