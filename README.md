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

# Framing a Prediction Problem

# Baseline Model

# Final Model

# Fairness Analysis