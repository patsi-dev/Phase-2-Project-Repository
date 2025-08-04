# Movie Studio Profitability Analysis
### Introduction
As our company considers entering the film production industry, it's critical to understand what types of movies generate strong returns. Certain genres, release strategies, and creative talent demonstrate consistent profitability, while others present significant financial risks.

This analysis uses historical movie data to identify patterns in successful films across genres, budgets, release timing, and director performance. The goal is to inform production decisions with evidence-based insights, minimizing financial risk for our new studio.

#### For a non-technical presentation of the data, check this [link](https://github.com/patsi-dev/Phase-2-Project-Repository/blob/main/Presentation.pdf)

#### For a Tableau presentation, refer to this [Movie_recommendation](https://public.tableau.com/app/profile/warren.patsi/viz/Movies_recommendation/Dashboard1?publish=yes))

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

---
## Data Analysis
Key Findings
1. Top Performing Genres
Horror films deliver exceptional ROI (912% average)

Family (687%) and Animation (332%) genres show strong returns

Drama (301%) and Mystery (287%) provide solid profitability

Low-budget horror films outperform all others (1143% ROI)

2. Optimal Release Timing
July releases generate highest returns (350%+ ROI)

January and October are secondary peak months

March, September and December show weakest performance

3. Low-Budget Viability
Films under $10M outperform higher-budget movies (506% vs 211% ROI)

Top low-budget genres: Horror (1143%), Drama (423%), Biography (396%)

Budget sweet spot: Horror films under $1M deliver 1143% ROI

4. Director Recommendations
Henry Joost

Specialization: Horror

Avg. ROI: 2503%

Notable approach: Found-footage style with minimal budgets

Ariel Schulman

Specialization: Horror/Documentary

Avg. ROI: 2503%

Key strength: Viral marketing strategies

James Wan

Specialization: Horror

Avg. ROI: 1486%

Track record: Successful franchise launches

Recommendations
Genre Strategy

Prioritize horror films with budgets under $10M

Develop 1-2 family animation films annually

Include limited drama/biography projects for awards potential

Release Calendar

Target July for tentpole horror releases

Schedule secondary horror films in January/October

Avoid March/September releases

Talent Acquisition

Recruit proven horror specialists first

Consider drama specialists for prestige projects

Implement profit-sharing contracts to align incentives

Budget Allocation

Cap initial productions at $10M

Allocate 70% of budget to horror films

Reserve 15% for experimental low-budget projects

Methodology
Data Sources
The Numbers Dataset (2010-2020):
Production budgets, worldwide gross earnings, release dates

IMDB Database:
Genre classifications, director credits, film metadata

Analytical Approach
Calculated ROI: (Worldwide Gross - Production Budget) / Production Budget

Identified outliers and capped extreme values (top 1%)

Analyzed genre performance across budget tiers

Evaluated seasonal patterns by release month

Ranked directors by consistency and ROI performance
