# Final Analysis

This folder contains the main completed analysis used for the NBA All-Star prediction project.

## Files

### `nba_all_star_analysis.ipynb`

This is the main analysis notebook.

It uses NBA player data from 2015-2025 and contains the primary modeling work used for the final version of the project.

The analysis includes:

- Data preparation
- All-Star classification
- Random Forest modeling
- Logistic regression
- Feature engineering
- Custom player scoring
- All-Star probability estimates
- Potential snub identification
- Player-level model comparisons
- Visualizations

This version represents the last reliable stage of the analysis before I experimented with adding additional data such as True Shooting Percentage and team wins.

### `nba_2015_2025_cleaned.csv`

This is the cleaned player-season dataset used by the notebook.

It contains NBA player statistics from 2015-2025 along with the variables used during the analysis.

## Running the Notebook

The notebook preserves the code from the original project, including the file path that I used on my local computer.

Because of this, the CSV import path may need to be changed before running the notebook on another computer.

The notebook and dataset are stored in the same folder in this repository, so the data can be loaded with:

```python
import pandas as pd

df = pd.read_csv("nba_2015_2025_cleaned.csv")
```

Replace the original local CSV path in the notebook with the line above if necessary.

## Why the Later Experiment Is Not Here

A later version of the project experimented with adding:

- True Shooting Percentage
- Team wins

That version developed data-merging and missing-value problems that reduced the usable dataset.

Rather than presenting that experiment as the final reliable analysis, I preserved it in the `development/` folder as:

```text
v5_ts_team_wins.ipynb
```

This keeps the final analysis separate while still documenting the full development process.

## Development Versions

Earlier versions and experimental branches are available in:

```text
../development/
```

The `development/README.md` file explains what changed between each major version.

## Portfolio Case Study

A visual explanation of the project, its development, model disagreements, limitations, and main lessons is available at:

```text
../portfolio/nba_all_star_project_case_study.pdf
```
