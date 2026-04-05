# Analyzing Movie Revenue: A Multivariate Regression & Transformation-Based Modeling Approach

Examining how budget, audience engagement, genre, and release year predict movie revenue using regression models with diagnostic-driven transformations.

**STA302H1 Independent Research Project** — University of Toronto
**Authors:** Andrew Batmunkh, Kevin Cheung

## Overview

Analyzed 3,228 films from the TMDb 5000 Movie Dataset to build and compare regression models predicting box office revenue. The initial linear model showed strong fit (R² ≈ 0.72) but exhibited heteroskedasticity, motivating log-transformations that stabilized residual variance and improved model diagnostics.

## Key Findings

- **log_budget** (β ≈ 0.66) and **log_vote_count** (β ≈ 0.77) were the strongest predictors of revenue (p < 2×10⁻¹⁶)
- Log-linear transformation resolved heteroskedasticity present in the preliminary model
- AIC/BIC comparison confirmed the transformed model as the better fit
- Genre and budget interact — the effect of budget on revenue varies by genre

## Methodology

### 1. Data Cleaning & Feature Engineering
- Extracted `release_year` and `primary_genre` from raw fields
- Created binary indicators for English language and homepage presence
- Filtered to films with non-zero budget and revenue (3,228 observations)

### 2. Preliminary Model
- Standard multiple linear regression with revenue as the response
- Predictors: budget, runtime, popularity, vote average, vote count, release year, language, homepage, genre, and a budget × genre interaction
- Strong R² but residual plots showed heteroskedasticity (non-constant variance)

### 3. Log-Linear Transformation
- Applied log₁₀ to budget, revenue, and vote count
- Re-fit the model with transformed variables
- Residual analysis confirmed stabilized variance and improved normality

### 4. Model Comparison
- AIC and BIC used to formally compare preliminary vs transformed models
- Residual diagnostics (Q-Q plots, residuals vs fitted) validated the final model

## Features Used

| Variable | Description |
|----------|-------------|
| `budget` | Production budget (USD) |
| `runtime` | Film length (minutes) |
| `popularity` | TMDb popularity score |
| `vote_average` | Average user rating (0–10) |
| `vote_count` | Number of user votes |
| `release_year` | Year of release |
| `is_english` | Binary: English language film |
| `has_homepage` | Binary: has an official website |
| `primary_genre` | First listed genre (Action, Drama, etc.) |

## Project Structure

```
movie-revenue-analysis/
├── data/
│   └── tmdb_5000_movies.csv
├── Final_model.Rmd              # Full analysis in R Markdown
├── Final_model.pdf              # Knitted output
├── poster.pdf                   # Poster presentation
└── README.md
```

## Setup & Usage

```r
# Required packages
install.packages(c("tidyverse", "dplyr", "knitr"))

# Open Final_model.Rmd in RStudio and click "Knit"
```

## Data Source

TMDb 5000 Movie Dataset — [Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

## Tech Stack

R · tidyverse · dplyr · knitr · R Markdown
