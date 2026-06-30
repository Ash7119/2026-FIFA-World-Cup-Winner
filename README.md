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

## Notes
- Elo Ratings as of May 27th, 2026.
- Squad values as of June 14th, 2026.
- Results as of June 5th, 2026.
- All World Cup matches are treated as neutral.
