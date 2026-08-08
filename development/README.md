
# Development History

This folder preserves the major development stages of the NBA All-Star prediction project.

The project was exploratory rather than planned as one finished model from the beginning. Each version represents a change in the question, data, modeling approach, or way I interpreted the results.

## v1 - Prototype

**File:** `v1_prototype.ipynb`

The original version of the project.

I started by testing whether basic NBA player statistics could be used to predict All-Star selections.

The main goal at this stage was simply to build a working model and see whether conventional box-score statistics could distinguish All-Stars from non-All-Stars.

This version used a single season and served as the starting point for the later experiments.

---

## v2 - Multi-Season Random Forest

**File:** `v2_multiseason_random_forest.ipynb`

The project was expanded from a single season to multiple seasons from 2015-2025.

The larger dataset gave the model more examples of both All-Stars and non-All-Stars while keeping the analysis within relatively recent NBA history.

This version continued using a Random Forest approach with conventional statistics such as:

- Points
- Assists
- Rebounds
- Steals
- Blocks
- Minutes played

This was also when I became more interested in players the model identified as possible All-Star snubs.

---

## v3 - All-Star Visualizations

**File:** `v3_all_star_visuals.ipynb`

This version expanded the analysis beyond model accuracy.

I began visualizing the model results and examining individual players whose predictions were interesting.

Instead of treating every incorrect prediction as simply an error, I started looking at disagreements between the model and the actual All-Star selections.

These disagreements eventually became one of the main focuses of the project.

---

## v4 - Custom Score

**File:** `v4_custom_score.ipynb`

This version experimented with creating a custom player score.

The goal was to move beyond simply reproducing the official All-Star label and experiment with representing overall player performance using multiple statistics.

Steve Nash became an important benchmark during this stage.

His career made him an interesting test because he was an All-Star and two-time MVP despite not having the type of scoring and rebounding numbers that a simple box-score model might strongly reward.

While experimenting with Nash, I eventually realized that I was beginning to change the model partly to make it recognize a player whose value I already believed it should recognize.

That became an important lesson about overfitting a model to an expected result.

---

## v4 - Probability and Visual Analysis

**File:** `v4_probability_visuals.ipynb`

This branch focused more heavily on predicted All-Star probabilities.

Instead of only classifying a player as an All-Star or non-All-Star, probabilities made it possible to see how strongly the model viewed a player as having an All-Star statistical profile.

This made several types of cases more interesting:

- Strong predicted snubs
- Borderline players
- Actual All-Stars with very low predicted probabilities
- Players whose statistics strongly disagreed with their official selection outcome

Probability ranking became more useful for exploring the model than a simple yes/no prediction.

---

## v5 - True Shooting Percentage and Team Wins

**File:** `v5_ts_team_wins.ipynb`

The final experimental version attempted to add more context to the model.

Two major additions were:

- True Shooting Percentage (TS%)
- Team wins

True Shooting Percentage was added because raw scoring totals do not distinguish between efficient and inefficient scoring.

Team wins were explored because valuable players should generally contribute to winning, although team wins are still a team-level statistic and cannot measure individual value by themselves.

This version developed data-merging and missing-value problems that reduced the usable dataset.

Because of those problems, I do not treat this experiment as the final reliable model.

I kept it in the repository because it documents an important part of the development process: adding theoretically better features does not necessarily improve a project if the supporting data pipeline is unreliable.

---

## What I Learned From the Development Process

The project gradually changed from:

> Can statistics predict NBA All-Star selections?

into a broader question:

> What does the available data make visible about player value, and what does it hide?

Basic box-score statistics are useful, but they naturally reward things that are easy to count.

Other forms of basketball value can be much harder to represent, including:

- Defensive positioning
- Basketball IQ
- Communication
- Off-ball movement
- Screening
- Decision quality
- Spatial impact
- Possession-level context

The project made me interested in eventually using richer forms of basketball data such as tracking data, spatial data, heat maps, and more detailed defensive information.

It also showed me that model disagreements can sometimes be findings themselves rather than simply mistakes that need to be removed.
