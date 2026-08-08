# NBA All-Star Prediction and Snub Exploration

A personal data science project exploring whether NBA player statistics can predict All-Star selections, identify possible snubs, and reveal limitations in conventional box-score data.

## Project Overview

This project started with a relatively simple question:

**Can basic NBA player statistics predict who becomes an All-Star?**

As I continued working on the project, I became more interested in a second question:

**What can disagreements between the model and actual All-Star selections tell us about the statistics being used?**

Instead of treating every incorrect prediction as simply a model error, I began looking at players who received very high or very low All-Star probabilities compared with their actual selection status.

This changed the project from only a classification problem into an exploration of what conventional basketball statistics reward and what types of player value they may fail to represent.

## Inspiration

The original idea was inspired by Michael Lewis's *The No-Stats All-Star*, an article about Shane Battier and the difficulty of representing some forms of basketball value with traditional statistics.

That idea interested me because statistics such as points, rebounds, and assists are easy to record and compare, while other contributions can be much harder to measure.

Examples include:

- Defensive positioning
- Basketball IQ
- Communication
- Off-ball movement
- Screening
- Decision quality
- Spatial impact
- Possession-level context

Even common statistics do not always represent equal amounts of value.

For example, an assist can come from creating an open shot for a teammate or simply making the final pass before a teammate makes a difficult contested shot. Both possessions are recorded as one assist.

This made me interested in what a machine-learning model would learn if it mainly had access to conventional player statistics.

## Data

The project originally used the 2023 NBA season before being expanded to player-seasons from **2015-2025**.

The expanded dataset contains approximately **3,800 player-season observations**.

Variables explored throughout the project included statistics such as:

- Points
- Assists
- Rebounds
- Steals
- Blocks
- Minutes played
- Shooting percentages
- All-Star selection status

Later experiments also explored adding:

- True Shooting Percentage
- Team wins

The repository includes both the original 2023 dataset and the expanded 2015-2025 dataset so the development of the project can be followed.

## Modeling Approach

The project developed through several versions rather than being created as one finished model.

Methods and techniques explored include:

- Random Forest classification
- Logistic regression
- Feature engineering
- Custom player scoring
- Predicted All-Star probabilities
- Model disagreement analysis
- Data cleaning and merging
- Exploratory visualization

The early versions focused mainly on whether a player could be classified as an All-Star.

Later versions focused more on the **probability** assigned to each player.

This made it possible to distinguish between a player barely missing the model's boundary and a player the model overwhelmingly believed had an All-Star statistical profile.

## Exploring Potential Snubs

One of the most interesting parts of the project became examining players whose model probabilities strongly disagreed with their actual All-Star status.

Examples from the saved results include:

| Player Season | Actual Result | Model Probability |
| --- | --- | ---: |
| Russell Westbrook, 2021 | Not selected | **98.8%** |
| Domantas Sabonis, 2024 | Not selected | **94.0%** |
| Anthony Davis, 2023 | Not selected | **90.8%** |
| James Harden, 2023 | Not selected | **85.4%** |
| Trae Young, 2023 | Not selected | **85.1%** |
| Jimmy Butler, 2023 | Not selected | **48.8%** |
| Andrew Wiggins, 2022 | All-Star | **2.4%** |
| Draymond Green, 2022 | All-Star | **3.6%** |
| Al Horford, 2018 | All-Star | **5.5%** |
| Mike Conley, 2021 | All-Star | **5.8%** |

These results should not be interpreted as objective probabilities that a player deserved an All-Star selection.

Instead, they represent how closely each player's statistical profile matched the patterns the model learned from actual All-Stars.

That distinction became an important part of the project.

## What the Disagreements Showed

Some disagreements were especially useful for understanding the model.

### High-Probability Non-All-Stars

Players such as Russell Westbrook, Domantas Sabonis, James Harden, and Trae Young produced large amounts of measurable box-score production.

Scoring, assists, and rebounds are relatively easy for a model to recognize and reward.

This can create extremely strong model probabilities even though the real All-Star selection process also includes factors the model does not see.

### Low-Probability Actual All-Stars

Players such as Draymond Green, Al Horford, and Mike Conley were interesting for the opposite reason.

Their value was not necessarily represented by extreme scoring or rebounding totals.

Draymond Green was particularly interesting because his result connected directly back to the original Shane Battier inspiration.

Defense, communication, positioning, screening, rotations, and other forms of impact can be important without appearing clearly in basic box-score statistics.

In these situations, a low probability may reveal a limitation in the available data rather than simply a limitation in the player.

## Steve Nash as a Benchmark

Steve Nash became an important test case during development.

His All-Star selections and two MVP awards made him an interesting example because much of his value came from playmaking, efficiency, decision-making, and team offense rather than extreme scoring or rebounding totals.

I initially began changing the model to place more importance on statistics such as assists, efficiency, and winning.

Eventually, I realized that I was beginning to adjust the model partly because I wanted it to recognize a player whose value I already believed it should recognize.

That created an important modeling lesson:

**A benchmark can become a target if the model is repeatedly changed until it produces the expected answer.**

Instead of continuing to force the model toward Nash, I began treating these disagreements as information about what the available variables could and could not represent.

## Era Effects

Expanding the dataset also introduced another problem.

What statistically looks like an NBA All-Star changes over time.

Factors such as:

- League pace
- Scoring environment
- Three-point shooting
- Position roles
- Offensive systems
- Playing style

can change the meaning of the same raw statistics.

Using 2015-2025 kept the main analysis within relatively recent NBA history, but it did not completely solve this problem.

A future version could explicitly compare players against the statistical environment of their era rather than assuming one universal All-Star profile.

## Final Experimental Version

The final experimental branch attempted to add **True Shooting Percentage and team wins**.

True Shooting Percentage was added because raw scoring totals do not distinguish between efficient and inefficient scoring.

Team wins were explored because player value should have some relationship with winning, while recognizing that wins are still a team-level result.

This version developed data-merging and missing-value problems that reduced the usable sample.

Because of this, I preserved the experiment in the development history rather than treating it as the final reliable model.

The failed experiment was still useful because it showed that adding theoretically better variables does not automatically improve a model if the supporting data pipeline is unreliable.

## Repository Structure

```text
nba-all-star-prediction/
│
├── README.md
│
├── final-analysis/
│   ├── nba_all_star_analysis.ipynb
│   └── nba_2015_2025_cleaned.csv
│
├── development/
│   ├── README.md
│   ├── v1_prototype.ipynb
│   ├── v2_multiseason_random_forest.ipynb
│   ├── v3_all_star_visuals.ipynb
│   ├── v4_custom_score.ipynb
│   ├── v4_probability_visuals.ipynb
│   └── v5_ts_team_wins.ipynb
│
├── data/
│   ├── nba_2023_cleaned.csv
│   ├── nba_2015_2025_cleaned.csv
│   └── nba_team_stats.csv
│
└── portfolio/
    └── nba_all_star_project_case_study.pdf
```

## Development History

The `development/` folder preserves the major versions of the project instead of only showing the finished analysis.

This includes the progression from:

**single-season prototype → multi-season model → visualization and probability analysis → custom scoring → efficiency and team-context experiments**

See `development/README.md` for a description of what changed in each version.

## Portfolio Case Study

A more visual and detailed explanation of the project is available here:

**[`portfolio/nba_all_star_project_case_study.pdf`](portfolio/nba_all_star_project_case_study.pdf)**

The case study focuses on the motivation behind the project, its development, the Steve Nash benchmark, model disagreements, limitations, and what I learned from the process.

## Limitations

This project has several important limitations.

The model relies heavily on conventional season-level statistics and therefore cannot fully represent many forms of basketball impact.

The official All-Star label also depends on factors outside the model, including:

- Voting
- Conference competition
- Roster construction
- Injuries and replacements
- Team context
- Narrative
- Timing of selection

For that reason, the project should not be interpreted as an objective ranking of which players deserved to become All-Stars.

It is better understood as an exploration of how statistical profiles compare with the real selection outcomes.

## Future Work

If I continued the project, I would be most interested in expanding the **types of data** used rather than simply adding more conventional statistics.

Possible directions include:

- Player tracking data
- Shot-location data
- Heat maps
- Spatial analysis
- Defensive tracking
- Lineup data
- Possession-level information
- Era-adjusted statistics
- More advanced efficiency and impact metrics

Another possible direction would be separating two different problems:

1. **Predicting who will be selected as an All-Star**
2. **Estimating which players provide All-Star-level value**

Those questions overlap, but they are not the same.

## What I Learned

I began this project with very little Python experience.

Building and repeatedly changing it gave me practical experience with:

- Python
- Jupyter Notebook
- pandas
- scikit-learn
- Random Forest models
- Logistic regression
- Feature engineering
- Data cleaning
- Data merging
- Probability interpretation
- Model evaluation
- Data visualization

The biggest lesson was not simply how to improve model accuracy.

It was learning that the variables available to a model determine what the model is capable of recognizing.

A model disagreement can sometimes be more interesting than a correct prediction because it creates a reason to ask **why** the model and reality disagree.

## Author

**Michael Shepherd**  
Data Science  
Pennsylvania State University
