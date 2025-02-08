# Cricket Player Classification and Team Selection

## Overview
This project analyzes cricket player statistics to classify players into specific roles (Wicketkeeper, Batsman, All-rounder, Bowler) and selects the optimal team composition using data science techniques. The analysis combines multiple statistical aspects of cricket performance and uses Principal Component Analysis (PCA) for feature selection and weighting.

## Project Steps

### 1. Data Preparation
- Load separate datasets for batting, bowling, fielding, and wicketkeeping statistics
- Initial data cleaning and preprocessing
- Handle missing values and standardize formats

### 2. Data Normalization
- Normalize each statistical category independently
- Scale features by dividing each value by the column's maximum value
- Special handling for inverse metrics (like bowling average and economy rate)
- Remove redundant columns (e.g., 'Centuries' from batting, 'Balls' from bowling)

### 3. Feature Analysis using PCA
- Standardize normalized data using StandardScaler
- Apply PCA to identify key performance indicators
- Calculate feature weights based on PCA component loadings
- Generate visualization plots:
  - Scree plots for variance explanation
  - Loading plots for feature relationships
  - Biplots for data distribution

### 4. Score Calculation
- Compute comprehensive scores for each skill:
  - Batting score (bat_score)
  - Bowling score (bowl_score)
  - Fielding score (field_score)
  - Wicketkeeping score (wik_score)
- Weight features based on PCA analysis results

### 5. Player Classification
- Set role thresholds using 75th percentile scores
- Classify players into roles:
  - Wicketkeeper
  - All-rounder (high batting AND bowling scores)
  - Bowler
  - Batsman
  - Bad_Player (below threshold in all categories)

### 6. Team Selection
- Select final 11 players based on role requirements:
  - 1 Wicketkeeper (highest wik_score)
  - 4 Batsmen (highest bat_score)
  - 3 All-rounders (balanced bat_score and bowl_score)
  - 3 Bowlers (highest bowl_score)

## Dependencies
- Python 3.x
- pandas: Data manipulation and analysis
- numpy: Numerical computing
- matplotlib: Data visualization
- seaborn: Statistical data visualization
- scikit-learn: Machine learning tools (PCA, StandardScaler)

## Usage
1. Ensure all required Python packages are installed:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

2. Place your data files in the project directory:
- bat_stats_clean.csv
- bowl_stats_clean.csv
- field_stats_clean.csv
- wik_stats_clean.csv

3. Run the Jupyter notebook to perform the analysis

## Potential Improvements
- Implement cross-validation for role classification
- Add dynamic team composition rules
- Create an interactive dashboard for results visualization
- Include player form analysis and trend detection
- Add opposition and venue-based analysis

## Data Requirements
Input CSV files should contain the following statistics:
- Batting: Matches, Innings, Runs, Highest Score, Average, Strike Rate, etc.
- Bowling: Matches, Innings, Wickets, Economy, Average, etc.
- Fielding: Matches, Catches, Run-outs, etc.
- Wicketkeeping: Matches, Dismissals, Catches, Stumpings, etc.
