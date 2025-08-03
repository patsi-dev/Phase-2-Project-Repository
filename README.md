# Movie Studio Profitability Analysis

## Business Understanding

### Problem Statement
Our company wants to launch a movie studio but has no film production experience. We need to identify currently profitable movie types to avoid financial losses from unpopular films.

### Business Objectives
1. Identify top 5 genres with highest profit margins
2. Determine optimal release month for each genre
3. Analyze if low-budget movies (<$10M) can achieve high ROI
4. Recommend 3 proven directors for hire

### Project Goals
- Analyze movie datasets to find patterns in successful films
- Focus on genres, release timing, budgets, and directors
- Create simple, clear recommendations using basic data analysis

### Success Criteria
1. **Genre Recommendations**: 5+ genres with above-average ROI (2010-2020)
2. **Seasonal Strategy**: Top 2-3 months with highest average ROI
3. **Budget Viability**: Proof of high ROI for <$10M films
4. **Director Shortlist**: 3+ proven directors suitable for hire

---

## Data Understanding

### Data Sources Overview
| Dataset          | Key Features                          | Relevance to Project                 |
|------------------|---------------------------------------|--------------------------------------|
| The Numbers (CSV)| Budgets, gross earnings (1975-2019)   | Core profitability calculations      |
| IMDB (SQLite)    | Genres, directors, titles (2010-2020) | Categorization and talent analysis   |
| Rotten Tomatoes  | Critic/audience scores                | Excluded - lacks financial data      |
| TheMovieDB       | Popularity metrics                    | Excluded - no profitability metrics  |
| Box Office Mojo  | Domestic gross (2010-2018)            | Excluded - redundant financial data  |
