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

## Significance of the Study

Understanding whether early game statistics can predict the outcome of a match is crucial for players, coaches, and analysts. It can help in developing strategies, improving gameplay, and making informed decisions during live matches. This predictive analysis can also enhance the viewing experience for fans by providing insights into the potential outcome based on early game events.

## Analysis Steps

1. **Data Cleaning and Exploratory Data Analysis (EDA)**: Clean the dataset and perform initial exploratory analysis to understand the distribution and relationships between variables.
2. **Assessment of Missingness**: Evaluate the mechanisms of missing data and determine whether any columns have missing values that are Not Missing At Random (NMAR).
3. **Hypothesis Testing**: Conduct hypothesis tests to explore relationships between variables.
4. **Prediction Problem Framing**: Define the prediction problem, choose the response variable, and determine the evaluation metric.
5. **Baseline Model**: Train a baseline predictive model using early game statistics.
6. **Final Model**: Improve upon the baseline model by engineering new features and tuning hyperparameters.
7. **Fairness Analysis**: Assess whether the model performs equitably across different groups.

The analysis will involve various statistical techniques and machine learning algorithms to achieve the objective. The final deliverable includes a public-facing website that presents the findings in an accessible and engaging manner.



# Introduction
Project for DSC 80 where I try predicting the result of League of Legends games using statistics from the 2020 League of Legends Tournament dataframe. 

Now the question is, can we predict the result of a League of Legends game using early game statistics such as first blood and cs at 15 minutes?

## General Introduction
League of Legends is a game where each team has 5 people and there are 2 teams going against each other. Each player has a role in the game and there are several statistics. Statistics include how much gold each player has, how much cs a player has


# NMAR Analysis
State whether you believe there is a column in your dataset that is NMAR. Explain your reasoning and any additional data you might want to obtain that could explain the missingness (thereby making it MAR). Make sure to explicitly use the term “NMAR.”

I believe the column firstbaron in my data set could be not missing at random (NMAR) because when I set the datacompleteness column to complete and check for all the null values, there are 320 rows where firstbaron is null. The firstbaron column does not rely on any other columns as it is own objective, it just relies on the column itself. I was also thinking that this column could possibly be NMAR because what if these games ended without firstbaron so that means that those games geniuenly don't have firstbaron. If I knew more information about of the data was collected then I might be able to make it MAR. For example, if there was complications in collecting data for the firstbaron and that is why those values are missing. Even if the datacompleteness column was queried to complete, there may have been issues in collecting this data. If I new this information then I would be able to determine it as MAR. There are 320/19430 rows that are missing the firstbaron data.  