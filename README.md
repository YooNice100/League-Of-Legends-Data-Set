# Introduction

## Project Overview

This project is part of DSC 80 where the objective is to predict the outcome of League of Legends games using early game statistics from the 2020 League of Legends Tournament dataset. League of Legends is a popular online multiplayer game where two teams of five players each compete to destroy the opposing team's Nexus, which is the heart of their base.

## Research Question

The primary question we aim to answer is: **Can we predict the result of a League of Legends game using early game statistics such as first blood and creep score at 15 minutes?**

## Dataset Description 

The dataset used for this analysis contains statistics from the 2020 League of Legends Tournament. The dataset includes various features that capture in-game events and team performance metrics. Here are some key columns:

- **league**: The league in which the game was played (e.g., LCK, LEC).
- **side**: The side of the map (e.g., blue or red).
- **firstblood**: Indicator of which team got the first kill.
- **firsttower**: Indicator of which team destroyed the first tower.
- **firstdragon**: Indicator of which team killed the first dragon.
- **firstherald**: Indicator of which team killed the first Rift Herald.
- **firstbaron**: Indicator of which team killed the first Baron Nashor.
- **goldat15**: Total team gold at 15 minutes.
- **csat15**: Total team creep score at 15 minutes.
- **xpat15**: Total team experience points at 15 minutes.
- **csdiffat15**: Difference in creep score at 15 minutes between the two teams.
- **golddiffat15**: Difference in gold at 15 minutes between the two teams.
- **xpdiffat15**: Difference in experience points at 15 minutes between the two teams.
- **result**: The outcome of the game (win or lose).

The dataset consists of 19,430 rows and 15 columns, each representing various in-game statistics and outcomes.


Understanding whether early game statistics can predict the outcome of a match is crucial for players, coaches, and analysts. It can help in developing strategies, improving gameplay, and making informed decisions during live matches. This predictive analysis can also enhance the viewing experience for fans by providing insights into the potential outcome based on early game events.



# Data Cleaning and Exploratory Data Analysis

## Data Cleaning

The data cleaning process involved handling missing values, converting categorical values to boolean, and ensuring correct data types. The cleaned dataset is called `n_of_df_cleaned`.

### Data Cleaning Steps

1. **Handling Missing Values**: I first queried the dataframe and made sure that the datacompleteness column was complete. Then I checked for null values by calling the dataframe and checking for nulls and the sum. I found that there were 14 rows with missing values in columns that were supposed to be complete. These rows were dropped to ensure the dataset's completeness. The `firstbaron` column, although containing many missing values, was not used in the analysis.
2. **Converting Categorical Values to Boolean**: Columns representing binary events (e.g., `firstblood`, `firsttower`) were converted from 0 and 1 to `True` and `False` for better readability and to ensure correct data types.
3. **Ensuring Correct Data Types**: Columns were converted to appropriate data types to ensure accurate computations and analyses.

These steps were essential to ensure that the dataset was clean and reliable for analysis. Cleaning the data helped in obtaining accurate insights and building robust predictive models.

### Head of the Cleaned DataFrame

Below is the head of the cleaned DataFrame:

<iframe
  src="assets/cleaned_data_head.html"
  width="100%"
  height="400"
  frameborder="0"
></iframe>

## Univariate Analysis

### Distribution of Gold at 15 Minutes

Performed Univariate Analysis on the gold at 15 minutes. This distribution of gold at 15 minutes provides insight into the economic state of teams early in the game.

<iframe
  src="assets/gold_distribution.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Creep Score at 15 Minutes

Performed Univariate Analysis on the creep score at 15 minutes.This helps us understand the team's control over minions and other resources at 15 minutes into the game. 

<iframe
  src="assets/cs_at_15_minutes.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Gold at 10 Minutes

Another Univariate Analysis of the gold at 10 minutes. Looks similar to the gold at 15 minutes. 

<iframe
  src="assets/gold_10_minutes.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Win and Loss Based on First Herald

Performed bivariate analysis on the first herald and result statistics in the dataset. I can visualize the wins and losses with teams that got first herald. 


<iframe
  src="assets/win_and_loss_first_herald.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Win and Loss Based on First Tower

Performed bivariate analysis on the first tower and result statistics in the dataset. I can visualize the wins and losses with teams that got first tower. 


<iframe
  src="assets/win_and_loss_first_tower.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

## Aggregate

These are the aggregated sums of early game statistics from the columns: 'result', 'firstherald', 'firstbaron', 'firsttower', 'firstblood', 'goldat15', 'csat15', 'position'. This is grouped by result which is win or lose. 

<iframe
  src="assets/count_agg.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


These are the aggregated proportions of early game statistics from the columns: 'result', 'firstherald', 'firstbaron', 'firsttower', 'firstblood', 'goldat15', 'csat15', 'position'. This is grouped by result which is win or lose. 

<iframe
  src="assets/aggregated_proportions.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



# Assessment of Missingness

## NMAR Analysis

I believe the column firstbaron in my data set could be not missing at random (NMAR) because when I set the datacompleteness column to complete and check for all the null values, there are 320 rows where firstbaron is null. The firstbaron column does not rely on any other columns as it is own objective, it just relies on the column itself. I was also thinking that this column could possibly be NMAR because what if these games ended without firstbaron so that means that those games geniuenly don't have firstbaron. If I knew more information about of the data was collected then I might be able to make it MAR. For example, if there was complications in collecting data for the firstbaron and that is why those values are missing. Even if the datacompleteness column was queried to complete, there may have been issues in collecting this data. If I new this information then I would be able to determine it as MAR. There are 320/19430 rows that are missing the firstbaron data.  

## Missingness Dependency

Here I am going to test if the missingness of firstbaron depends on the league column. I am going to use the test statistic Total Variance Distance. The significance level for both permutation tests will be 0.05.


- **Null Hypothesis**: The distributions are the same for `league` whether `firstbaron` is missing or not.
- **Alternate Hypothesis**: The distributions are different for `league` when `firstbaron` is missing versus when it is not missing.

Here is the data of observed distribution of when league and firstbaron is missing and not missing.


<iframe
  src="assets/baron_dist.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


Here is a bar plot showing the distribution of baron missing vs not missing amongst the Leagues

<iframe
  src="assets/missingness_of_first_baron.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

After performing permutation tests, `0.41618015012510423` is the observed test statistic and the p-value is 0. 

Here is the empricial distribution of the TVD for the test.

<iframe
  src="assets/empirical_dist_of_tvd.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

The p-value is less than 0.05 significance level. We can reject the null hypothesis. This means that the missingness of firstbaron depends on the league column.

The next permutation test is seeing if the firstbaron column depends on the result column. The observed tvd is `0.6667014178482068`. We are testing with a 0.05 significance. 

- **Null Hypothesis**: The distributions are the same for `result` whether `firstbaron` is missing or not.
- **Alternate Hypothesis**: The distributions are different for `result` when `firstbaron` is missing versus when it is not missing.


Here is the distribution of result when baron is missing and when it is not missing. The result values are seperated based on the missingness of firstbaron and the distributions are plotted. The reason why the distributions look the same is because they do not depend on each other. Firstbaron does not depend on the result column. When result is true and result is false, I believe there is same amount of missingness in the firstbaron because that means that the pairs of teams are missing. So say one team has missing data for their firstbaron, their opponent team also has missing data for their firstbaron but one of those teams lose and one of them wins. Therefore the distribution of them look almost the same because for the same amount of missing data for teams that won, there is same amount of missing data for the teams that lost. 

<iframe
  src="assets/dist_of_baron_thing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


<iframe
  src="assets/empirical_tvd_dist.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>



Since the p-value is greater than 0.05 significance, we fail to reject the null hypothesis. This indicates that the missingness of firstbaron does not depend on the result column. 

The p-value is greater than



# Hypothesis Testing

- **Null Hypothesis**: Getting first tower does not affect probability of winning the game
- **Alternate Hypothesis**: Getting the first tower does affect the probability of winning the game.

Test Statistic: Mean difference in the proportion of wins between teams that secured firsttower and teams that did not secure firsttower. Significance level is 0.05.

Observed difference in propotion is: `0.366281044591408`
P-Value: 0

With the hypothesis test performed, with a p-value of 0, we reject the null hypothesis. This suggests that getting the first tower does affect the probability of winning the game but we can not say this is absolute. 


# Framing a Prediction Problem
The prediction problem is :
Are we able to predict if a team will win or lose the game based on early game statistics?

I will perform this using binary classification. 

I will need to one hot encode the boolean columns. I am planning to one hot encode firstblood. Then I'm thinking about using a StandardScaler() on the numeric columns. 

I will use early game statistics such as firstblood, firsttower, firstdragon, firstherald, firstbaron, goldat15, csat15, xpat15.

These features are available during the early game and can provide insights into a team’s likelihood of winning. By using only early game statistics, I can only make a prediction based of the statistics in the beginning of the game. This could be applied to real life scenarios because sometimes we will watch the first 15 minutes of the game and then go and have to eat dinner and this model can help predict whether a team will win or not.

I'm going to split the data into training and test sets. Then, standardize the numeric features and apply one-hot encoding to the categorical features. I'll train a regression model and use F1-score and accuracy to evaluate if the model has improved. Next, I'll train the model using the best hyperparameters I can find. Finally, I'll assess the model's fairness by comparing its performance across different subsets of the data.


# Baseline Model

For the baseline model, I used the LogisticRegression linear model with the following three features: 'csat15', 'firstblood' and 'result'


The 'csat15' column is a quantitative column and I'm going to standardize it using StandardScaler

The 'firstblood' column is nominal and I'm going to encode with OneHotEncoder

Here are the performance results of my model:
Accuracy: `0.6310504634397528`
F1 Score: `0.6339719029374202`

I would say the accuracy score is better than random guessing with 50% and the F1 score is better than 50% but there is room for improvement such as improving the hyperparameters. 


# Final Model


For the final model, I added the following features: csdiffat15, golddiffat15, xpdiffat15

These are all quantitative features and represent the difference in statistics compared to the opposing team. If these values are positive, it indicates that the team is performing better in terms of creep score, gold, and experience points at 15 minutes compared to the opponent. Conversely, negative values indicate that the opponent is performing better. These differences are crucial for predicting the game outcome as they provide a comparative measure of team performance. I believe that when a team has more statistics positive compared to the other team, they are at an upper hand and it can help predict the result of the game.

I used the StandardScaler transformer on the newly added columns and then still the one hot encoder for the firstblood column.

## Model and Hyperparameters
Modeling Algorithm: Random Forest Classifier

I chose Random Forest Classifier because it handles numerical and categorical data well. I thought it would perform well with both types of features.

These are the best hyperparameters I found using grid search:
n_estimators: 300
max_depth: 10
min_samples_split: 2
min_samples_leaf: 1


I used GridSearchCV to select the best hyperparameters. This method explores a range of parameter values to find the best combination for a better accuracy and F1 score. 

The accuracy score is now `0.759783728115345` and the final F1 score is now `0.7599691278621045`. This is over 10% compared to the baseline model. I believe this model's accuracy and F1 score is much better than before but it is not that close to 1 meaning that the precision and recall could be viewed as weak. 


# Fairness Analysis

I am testing the fairness of my model by testing it on different groups. I am trying to see if my model performs worse for teams LCK league compared to those in the LEC league. I will answer this question by performing a permutation test and examining the difference in accuracy between the two groups. 

Group X: Teams in the LCK league.
Group Y: Teams in the LEC league.

Testing using Accuracy

Significance Level: 0.05.

Hypotheses: 
`Null Hypothesis` (H0): Our model is fair. Its accuracy for LCK teams is the same as the accuracy for LEC teams.
`Alternative Hypothesis` (H1): Our model is unfair. Its accuracy for LCK teams is NOT the same as the accuracy for LEC teams.

Test Statistic: Difference in accuracy between teams in the LCK and LEC leagues.

Results
Observed Accuracy for LCK: 0.8424
Observed Accuracy for LEC: 0.7833
Observed Difference: 0.0590
P-value: 0.006

After performing the permutation test, we obtained a p-value of 0.006, which is less than the 0.05 significance level. Consequently, we reject the null hypothesis. This result implies that our model's accuracy significantly differs between the two groups. Hence, our model appears to be unfair, exhibiting a bias towards one group over the other.
