# Premier League 2025/26 Prediction Dashboard

A data analysis project that predicts the final outcomes of the 2025/26 Premier League season — champion, runner-up, and relegated teams — using match-results data scraped from the web, cleaned and processed in Python, and visualised in an interactive Power BI dashboard.

---

## Project Overview

This project follows a complete analytics pipeline: **raw scraped data → cleaning → feature engineering → prediction modelling → interactive visualisation.**

Starting from raw fixture data, it builds a full league table, engineers performance metrics (consistency and recent form/momentum), applies a weighted prediction model to project how the season finishes, and presents the results in a five-page Power BI dashboard.

## Predictions

| Outcome | Team |
|---|---|
| 🏆 Predicted Champion | Arsenal |
| 🥈 Predicted Runner-up | Manchester City |
| 🔻 Predicted Relegation | Burnley, Wolves, Tottenham Hotspur |

> Note: The relegation picks reflect a blend of current league position and recent form rather than current standings alone — which is why Tottenham, mid-table on points but on a poor run of form, appears as a predicted faller.

## Data Pipeline

This project demonstrates each stage of a real data workflow:

**1. Collect (raw)** — Fixture and results data for the 2025/26 season was scraped/sourced from the web into a raw Excel file (`data/raw/`). This is the unprocessed starting point, including header rows and formatting as exported.

**2. Clean** — The raw data was cleaned into a tidy match-results table (`data/processed/PL_Match_Results_2025_26.csv`) — one row per played match, with consistent columns for week, date, teams, and scores.

**3. Engineer features** — Using Python, the cleaned results were used to build a full league table and engineer additional metrics, output to a multi-sheet workbook (`data/processed/PL_Analysis_Processed_Data.xlsx`):
- **Standings** — points, W/D/L, goals for/against, goal difference, points-per-game
- **Consistency_Analysis** — variance and standard deviation of points returns
- **Form_Analysis** — points and form trend over each team's last 5 games
- **Complete_Analysis** — all metrics combined

**4. Predict** — A weighted model projected final outcomes, output to `data/predictions/PL_Predictions_Summary.csv`.

**5. Visualise** — The processed data was loaded into Power BI to build the interactive dashboard (`dashboard/`).

## Methodology

**Data source:** Match-by-match results for the 2025/26 season (FBref), covering the played fixtures of a partial season.

**Prediction model:**
- Scored the top teams using a weighted formula combining current position, recent form, overall points-per-game, and consistency.
- Projected each team's final points total by extending current points with form-adjusted estimates for the remaining fixtures.
- The projected final points total determines the champion and runner-up ranking.

## Dashboard

The Power BI dashboard is organised into five pages:

1. **Championship Overview** — full standings table, points-by-team chart, and prediction cards (champion, runner-up, leader points, matches played).
2. **Consistency Analysis** — scatter and column visuals exploring which teams were most/least consistent.
3. **Form & Momentum** — a form table and a trend-coloured chart showing which teams are improving, stable, or declining.
4. **Relegation Battle** — danger-zone table, a wins/draws/losses breakdown of the bottom six, and gauges showing each predicted relegated team's points against the survival line.
5. **Match Explorer** — an interactive page with a team slicer that filters every match (home and away) plus goals scored/conceded for the selected team.

## Dashboard Preview

### 1. Championship Overview
![Championship Overview](screenshots/01-championship-overview.png)

### 2. Consistency Analysis
![Consistency Analysis](screenshots/02-consistency-analysis.png)

### 3. Form & Momentum
![Form and Momentum](screenshots/03-form-momentum.png)

### 4. Relegation Battle
![Relegation Battle](screenshots/04-relegation-battle.png)

### 5. Match Explorer
![Match Explorer](screenshots/05-match-explorer.png)

## Tech Stack

- **Python** (pandas) — data cleaning, processing, and metric engineering
- **Jupyter Notebook** — analysis workflow
- **Power BI Desktop** — interactive dashboard and DAX
- **Excel / CSV** — raw and processed data files
- **FBref** — match results data source

## Repository Structure

```
├── README.md
├── notebook/
│   └── PL_Winner_Analysis_2026.ipynb            # Python: cleaning, processing & prediction
├── data/
│   ├── raw/
│   │   └── premier_league_fixtures_2025_26.xlsx  # Raw scraped fixtures (pre-cleaning)
│   ├── processed/
│   │   ├── PL_Match_Results_2025_26.csv          # Cleaned match results
│   │   └── PL_Analysis_Processed_Data.xlsx       # Engineered features (5 sheets)
│   └── predictions/
│       └── PL_Predictions_Summary.csv            # Final prediction output
├── dashboard/
│   ├── Premier_league_predictions.pbix           # Power BI dashboard
│   └── PL_Purple_Theme.json                      # Custom Power BI theme
└── screenshots/
    ├── 01-championship-overview.png
    ├── 02-consistency-analysis.png
    ├── 03-form-momentum.png
    ├── 04-relegation-battle.png
    └── 05-match-explorer.png
```

## How to View

- **Dashboard screenshots** are shown above and in the `screenshots/` folder — the quickest way to see the work.
- To explore interactively, open `dashboard/Premier_league_predictions.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free). The `PL_Purple_Theme.json` is the custom theme applied to the report.
- To review the analysis, open `notebook/PL_Winner_Analysis_2026.ipynb` (viewable directly on GitHub).
- The `data/` folder shows the full pipeline from raw scraped data through to final predictions.

## Disclaimer

This is a portfolio project for demonstrating data analysis and visualisation skills. The predictions are illustrative model outputs based on partial-season data, not betting advice or definitive forecasts.

---

*Built as a portfolio project combining web-scraped data, Python processing, and Power BI visualisation.*
