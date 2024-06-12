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

1. **Handling Missing Values**: I first queried the dataframe and made sure that the datacompleteness was complete. Then I checked for null values by calling the dataframe and checking for nulls and the sum. I found that there were 14 rows with missing values in columns that were supposed to be complete. These rows were dropped to ensure the dataset's completeness. The `firstbaron` column, although containing many missing values, was not used in the analysis.
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

## Exploratory Data Analysis

EDA involves visualizing the data to uncover patterns and relationships between variables. Below are some key insights from our EDA.

### Distribution of Gold at 15 Minutes

The distribution of gold at 15 minutes provides insight into the economic state of teams early in the game.

<iframe
  src="assets/gold_distribution.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Creep Score at 15 Minutes

Analyzing the creep score at 15 minutes helps in understanding the team's control over resources.

<iframe
  src="assets/cs_at_15_minutes.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Gold at 10 Minutes

The distribution of gold at 10 minutes provides an early indication of economic advantage.

<iframe
  src="assets/gold_10_minutes.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Win and Loss Based on First Herald

Understanding how securing the first Rift Herald impacts the game's outcome.

<iframe
  src="assets/win_and_loss_first_herald.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

### Win and Loss Based on First Tower

Analyzing the impact of destroying the first tower on the game's outcome.

<iframe
  src="assets/win_and_loss_first_tower.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>










# NMAR Analysis
State whether you believe there is a column in your dataset that is NMAR. Explain your reasoning and any additional data you might want to obtain that could explain the missingness (thereby making it MAR). Make sure to explicitly use the term “NMAR.”

I believe the column firstbaron in my data set could be not missing at random (NMAR) because when I set the datacompleteness column to complete and check for all the null values, there are 320 rows where firstbaron is null. The firstbaron column does not rely on any other columns as it is own objective, it just relies on the column itself. I was also thinking that this column could possibly be NMAR because what if these games ended without firstbaron so that means that those games geniuenly don't have firstbaron. If I knew more information about of the data was collected then I might be able to make it MAR. For example, if there was complications in collecting data for the firstbaron and that is why those values are missing. Even if the datacompleteness column was queried to complete, there may have been issues in collecting this data. If I new this information then I would be able to determine it as MAR. There are 320/19430 rows that are missing the firstbaron data.  