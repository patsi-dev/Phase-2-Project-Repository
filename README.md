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
### Key Findings
1. Top Performing Genres
- Horror films deliver exceptional ROI (912% average)

- Family (687%) and Animation (332%) genres show strong returns

- Drama (301%) and Mystery (287%) provide solid profitability

- Low-budget horror films outperform all others (1143% ROI)

2. Optimal Release Timing
- July releases generate highest returns (350%+ ROI)

- January and October are secondary peak months

- March, September and December show weakest performance

3. Low-Budget Viability
Films under $10M outperform higher-budget movies (506% vs 211% ROI)

- Top low-budget genres: Horror (1143%), Drama (423%), Biography (396%)

- Budget sweet spot: Horror films under $1M deliver 1143% ROI

4. Director Recommendations
**Henry Joost**

Specialization: **Horror**

Avg. ROI: **2503%**

Notable approach: Found-footage style with minimal budgets

**Ariel Schulman**

Specialization: **Horror/Documentary**

Avg. ROI: **2503%**

Key strength: Viral marketing strategies

**James Wan**

Specialization: **Horror**

Avg. ROI: **1486%**

Track record: Successful franchise launches

###Recommendations
Genre Strategy


- Prioritize horror films with budgets under $10M

- Develop 1-2 family animation films annually

- Include limited drama/biography projects for awards potential


Release Calendar

- Target July for tentpole horror releases

- Schedule secondary horror films in January/October

- Avoid March/September releases

Talent Acquisition

- Recruit proven horror specialists first

- Consider drama specialists for prestige projects

- Implement profit-sharing contracts to align incentives

Budget Allocation

- Cap initial productions at $10M

- Allocate 70% of budget to horror films

- Reserve 15% for experimental low-budget projects

## Methodology
### Data Sources
**The Numbers Dataset (2010-2020):**

- Production budgets, worldwide gross earnings, release dates

**IMDB Database:**

- Genre classifications, director credits, film metadata


## Analytical Approach

-Calculated ROI: (Worldwide Gross - Production Budget) / Production Budget

- Identified outliers and capped extreme values (top 1%)

- Analyzed genre performance across budget tiers

- Evaluated seasonal patterns by release month

- Ranked directors by consistency and ROI performance

---

## 3. Data Preparation

### Cleaning Process
1. **Currency Conversion**:
   ```python
   # Convert $110,000,000 → 110000000
   for col in ['production_budget', 'domestic_gross', 'worldwide_gross']:
       df_budget[col] = df_budget[col].str.replace('$', '').str.replace(',', '').astype(int)
   ```

2. **Date Handling**:
   ```python
   df_budget['release_date'] = pd.to_datetime(df_budget['release_date'], format='%b %d, %Y')
   ```

3. **Genre Extraction**:
   ```python
   movies['main_genre'] = movies['genres'].str.split(',').str[0]
   ```

### Merging Strategy
```mermaid
    A[TheNumbers] -->|Title + Year| C[Merged Data]
    B[IMDB] -->|Title + Year| C
    C -->|Movie ID| D[+ Directors]
```

### Feature Engineering
```python
# Profit calculations
movie_df['profit'] = movie_df['worldwide_gross'] - movie_df['production_budget']
movie_df['roi'] = (movie_df['profit'] / movie_df['production_budget']) * 100

# Release month
movie_df['release_month'] = movie_df['release_date'].dt.month_name()

# Budget categories
movie_df['budget_category'] = pd.cut(
    movie_df['production_budget'],
    bins=[0, 10e6, 50e6, float('inf')],
    labels=['low', 'medium', 'high']
)
```

---

 4. Analysis & Results

### 4.1 Top 5 Profitable Genres
```python
top_genres = movie_df.groupby('main_genre')['roi'].mean().nlargest(5)
print(top_genres)
```
| Genre | Avg ROI | 
|-------|---------|
| Horror | 1679% |
| Family | 686% |
| Animation | 332% | 
| Drama | 310% |
| Mystery | 267% |

![Top Genres](https://public.tableau.com/app/profile/warren.patsi/viz/Movies_recommendation/Dashboard1)

### 4.2 Best Release Timing
```python
monthly_roi = movie_df.groupby('release_month')['roi'].mean().nlargest(3)
print(monthly_roi)
```
| Month | Avg ROI |
|-------|---------|
| July | 692% |
| January | 413% |
| October | 341% |

![Monthly ROI](https://public.tableau.com/app/profile/warren.patsi/viz/Movies_recommendation/Dashboard1)

### 4.3 Low-Budget Performance
```python
low_budget_roi = movie_df[movie_df['budget_category']=='low']['roi'].mean()
print(f"Low-budget ROI: {low_budget_roi:.0f}%")
# Output: Low-budget ROI: 576%
```

![Budget Comparison](https://public.tableau.com/app/profile/warren.patsi/viz/Movies_recommendation/Dashboard1)

### 4.4 Director Recommendations
```python
top_directors = director_stats[director_stats['proven_director']].sort_values('avg_roi', ascending=False).head(3)
print(top_directors[['director_clean', 'avg_roi']])
```
| Director | Avg ROI | Specialty |
|----------|---------|-----------|
| William Brent Bell | 5329% | Horror |
| Jordan Peele | 3089% | Horror |
| Barry Jenkins | 2158% | Drama |

![Top Directors](https://public.tableau.com/app/profile/warren.patsi/viz/Movies_recommendation/Dashboard1)

---

## 5. Recommendations

### Strategic Action Plan
1. **Genre Focus**:
   - Produce horror films as primary genre
   - Use drama for secondary productions

2. **Budget Allocation**:
   - Keep 70% of films under $10M budget
   - Target horror films for low-budget productions

3. **Release Calendar**:
   - Schedule major releases in July
   - Use January/October for secondary releases

4. **Director Partnerships**:
   - Prioritize horror specialists
   - Consider Barry Jenkins for drama projects

### Expected Outcomes
| Metric | Current Avg | Our Target |
|--------|-------------|------------|
| ROI | 211% | 500%+ |
| Production Cost | $48M | <$10M |
| Success Rate | 40% | 65%+ |

---