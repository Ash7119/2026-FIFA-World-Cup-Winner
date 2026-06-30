# 2026 FIFA World Cup Winner
A Monte Carlo simulator that predicts the probability of each of the 48 teams winning the 2026 FIFA World Cup. Built in Python using historical match data, Elo ratings, squad information, and machine learning.

It runs 10,000 simulated tournaments from group stage to final. Each simulation uses trained machine learning models to predict  each team's likelihood of reaching the quarterfinals, semifinals, final, and winning the tournament. It displays the result in a form of a table.

## Data
- https://www.kaggle.com/datasets/afonsofernandescruz/2026-fifa-world-cup-historical-elo-ratings?select=elo_ratings_wc2026.csv
- https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017
- https://www.kaggle.com/datasets/mjmotebaheri/world-cup-2026-match-schedule-data-csv-json-ics?select=world-cup-2026-schedule.csvhttps://www.kaggle.com/datasets/mjmotebaheri/world-cup-2026-match-schedule-data-csv-json-ics?select=world-cup-2026-schedule.csv
- https://www.transfermarkt.com/weltmeisterschaft/teilnehmer/pokalwettbewerb/FIWC/saison_id/2025

## Libraries Used
- pandas
- numpy
- xgboost
- scikit-learn
- matplotlib
- beautiful soup

## Pipe Line
### Step 1-Web Scraping
Web scraped the participants of the 2026 FIFA World Cup from transfermarkt. The data includes sqaud size,average agem market value, average market value and foreigners.

### Step 2-Loading and Cleaning the Data
Loaded the data and cleaned every dataset being used in the project.
- Convert all dates to datetime
- Standardize team names across all files using a dictionary (e.g. `"Korea Republic"` → `"South Korea"`, `"Turkiye"` → `"Turkey"`)
- Parse squad financial data (market values, percentages) into numeric columns

### Step 3-Feature Engineering
- For every historical match, attach the correct Elo rating for both teams **as of that match date** using a backward as-of join (`pd.merge_asof`). Stored as `home_elo`, `away_elo`, and `elo_diff`
- Builds the following features for every historical match:
- - **Rolling form** (last 5 games): Average goals scored, average goals conceded, win rate — computed with `shift(1)` to prevent leakage
- **H2H history**: Cumulative win rate between the two specific teams in all prior meetings
- **Elo features**: Home Elo, away Elo, Elo difference
- **Context flags**: Neutral venue, World Cup match, qualifier match
- **Shootout win rates**: Each team's historical penalty shootout win rate (Used in knockout simulation)
- **Squad features**: Avg age, market value, % foreigners (Used in knockout simulation)

### Step 4-Training and Testing
- Train up to 2018
- Val from 2018-Nove 2022
- Test from 2022 FIFA WC onwards


## Notes
- Elo Ratings as of May 27th, 2026.
- Squad values as of June 14th, 2026.
- Results as of June 5th, 2026.
- All World Cup matches are treated as neutral.

