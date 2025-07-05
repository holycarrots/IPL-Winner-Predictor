# IPL Winner Prediction Model

This repository hosts a machine learning project dedicated to predicting the winners of Indian Premier League (IPL) matches. Leveraging historical IPL data, this model aims to uncover key insights, trends, and patterns within the league to forecast future match outcomes.

The project demonstrates the application of machine learning techniques to real-world sports data, providing a data-driven approach to predicting IPL winners.

## Project Files

* `IPL_Predictor.ipynb`: This is the original Jupyter Notebook developed for IPL match prediction.
* `updated_2025.ipynb`: This is the updated version of the IPL prediction model, incorporating several enhancements and expanded data analysis for the 2025 season.

## Introduction

The Indian Premier League (IPL) is one of the most popular and competitive cricket leagues globally. Predicting match outcomes in such a dynamic environment is a challenging task due to numerous influencing factors like team form, player performance, venue conditions, and toss decisions. This project uses historical IPL data to build a robust predictive model, offering insights and forecasts for upcoming matches.

## What's New in `updated_2025.ipynb`?

The `updated_2025.ipynb` notebook represents a significant enhancement over the `IPL_Predictor.ipynb` version. Key differences include:

* **Expanded Data Coverage**: The updated notebook now includes IPL data up to the **2024 season**, providing a more comprehensive and recent dataset for analysis and prediction.
* **Enhanced Data Preprocessing**:
    * **Handling Missing Values**: The `updated_2025.ipynb` explicitly addresses missing values in columns like `result_margin`, `target_runs`, and `target_overs` by imputing them with the median, a robust strategy against outliers.
    * **Team Name Standardization**: A more comprehensive `team_name_mapping` dictionary is applied to standardize old team names (e.g., 'Delhi Daredevils' to 'Delhi Capitals', 'Kings XI Punjab' to 'Punjab Kings'). This ensures consistency across different seasons and prevents data fragmentation under multiple team names.
    * **City Name Standardization**: City names like 'Bengaluru' are now standardized to 'Bangalore' to avoid duplicate entries and improve data quality.
* **Refined Feature Engineering**:
    * **Date Feature Extraction**: The `updated_2025.ipynb` extracts `year`, `month`, and `day` from the `date` column and drops the original `date` column. This provides temporal features for the model.
    * **Season Start/End Years**: New features `season_start` and `season_end` are derived from the `season` column, explicitly capturing the start and end years of each season.
    * **More Granular Player Stats**: The updated notebook introduces a more detailed approach to player statistics, calculating individual stats like `balls_faced`, `innings`, `0s`, `1s`, `2s`, `3s`, `4s`, `6s`, `highest_score`, `player_out`, `batting_avg`, and `batting_strike_rate`. It also calculates `balls_throw`, `wickets`, `overs`, `runs_conceded`, `bowling_econ`, and `bowling_strike_rate` for bowlers. These features significantly enhance the model's understanding of individual player impact.
    * **Fielding Statistics**: The `updated_2025.ipynb` now includes `catches` by players, combining catches by bowlers and fielders.
    * **Man of the Match Count**: A `man_of_the_match_count` feature is added, tallying how many times a player has received this award.
    * **In-Match Live Features**: Crucially, the updated model calculates dynamic in-match features such as `current_score`, `runs_left`, `balls_left`, `wickets_left`, `current_run_rate`, and `required_run_rate`. These real-time metrics are vital for more accurate predictions during a live match scenario.
* **Enhanced Exploratory Data Analysis (EDA)**: The `updated_2025.ipynb` includes a more extensive EDA section with various plots to visualize:
    * Team performance metrics (win percentage, run rate, economy rate, highest/lowest scores, total 4s/6s, average powerplay/death overs scores).
    * Player performance metrics (top run-scorers, batting average vs. strike rate, top wicket-takers, highest individual scores, Man of the Match counts).
    * Seasonal trends (average runs per match by season).
* **Improved Model Training Strategy**: The updated notebook trains and combines two Random Forest Classification models using a `VotingClassifier` with `soft` voting. One model is trained on a random split of the entire dataset, and another specifically excludes the 2024 season for training, then tests on the 2024 season. This ensemble approach aims for better generalization.
* **Hyperparameter Tuning**: `GridSearchCV` is now explicitly used for hyperparameter tuning on the Random Forest classifiers, optimizing `n_estimators`, `max_depth`, and `min_samples_split`.

## Future Plans

I am currently working on developing a **frontend for this prediction model using React**. This will allow users to input match details and receive real-time predictions from the deployed model, making the tool more interactive and user-friendly. The frontend will aim to:

* Provide an intuitive interface for entering match parameters (e.g., teams, venue, current score, overs, wickets).
* Display the prediction results (e.g., win probability for each team) clearly.
* Potentially include visualizations of historical team/player data.

This will transform the backend prediction logic into a fully functional and accessible application.

## Dependencies

The core dependencies for this project include:

* `pandas`
* `numpy`
* `matplotlib`
* `seaborn`
* `scikit-learn`
* `pickle`
