# 🏏 2027 ODI World Cup — Team & Venue Intelligence Analysis

## 📌 Project Overview

This project analyzes ODI cricket performance and historical venue data to identify suitable venues for teams participating in the 2027 ICC Men's Cricket World Cup.

The project combines Python-based data preparation and analysis with an interactive Power BI dashboard to evaluate team performance across selected venues and generate team-specific venue recommendations.

The analysis covers 14 teams, 12 official venues, and 168 possible team–venue combinations.

---

## 🎯 Business Objective

The objective of this project is to answer:

- Which venues are most suitable for each team?
- How have teams historically performed across different venues?
- Which venues provide the strongest team-specific performance scores?
- Where is historical team–venue data available?
- Where is fallback scoring required because historical data is unavailable?
- Which teams receive the highest overall venue recommendations?

---

## 📊 Project Scope

| Metric | Value |
|---|---:|
| Teams analyzed | 14 |
| Official venues | 12 |
| Team–venue combinations | 168 |
| Final recommendation coverage – Historical | 78.57% |
| Final recommendation coverage – Fallback | 21.43% |
| Team–venue historical data coverage | 40.48% |
| Team–venue fallback coverage | 59.52% |
| Highest final recommendation score | 87.10 |

### Teams

- Australia
- Bangladesh
- England
- India
- Ireland
- New Zealand
- Pakistan
- Scotland
- South Africa
- Sri Lanka
- West Indies
- Zimbabwe
- Namibia
- Afghanistan

---

## 🗂️ Dataset

The analysis uses men's ODI match data in JSON format.

The original dataset contains 2,565 ODI match files. The raw JSON files are not included in this repository because of their size.

The Python workflow filters and transforms the match data to create the datasets required for team and venue analysis.

### Analysis period

The project focuses on ODI data from 2015 onward.

---

## 🔄 Data Preparation Workflow

```text
Raw ODI JSON Data
        ↓
Python Data Extraction
        ↓
Match Filtering
        ↓
Team & Venue Standardization
        ↓
Historical Team–Venue Summary
        ↓
Batting Performance Analysis
        ↓
Bowling Performance Analysis
        ↓
Venue Scoring
        ↓
Fallback Scoring
        ↓
Final Venue Ranking
        ↓
Power BI Dashboard
```
## 🐍 Python Analysis

Python was used for:

Reading ODI JSON match files
Filtering men's ODI matches
Filtering matches from 2015 onward
Selecting relevant World Cup teams
Standardizing venue names
Creating team–venue historical summaries
Calculating batting performance scores
Calculating bowling performance scores
Combining batting and bowling scores
Creating venue rankings
Applying fallback scoring where historical data was unavailable
Exporting final datasets for Power BI

The main analysis notebook is:
python/2027wc.ipynb

## 🧮 Scoring Methodology
Batting Score

The batting score considers:

Runs per innings
Strike rate
Fours
Sixes

The components are weighted to create a combined batting performance score.

Bowling Score

The bowling score considers:

Wickets per match
Economy
Bowling average
Bowling strike rate

The components are combined to create a bowling performance score.

Overall Venue Score

The overall historical venue performance combines:

Batting performance
Bowling performance

with equal weighting.

##🔁 Fallback Recommendation Logic

Not every team has sufficient historical data at every venue.

When historical team–venue performance is unavailable, the project applies a team-level fallback score so that every team can still receive a venue recommendation.

This creates two different coverage measures.

Final Recommendation Coverage

This measures whether each team's final recommendation came from historical venue data or fallback scoring.

Historical: 78.57%
Fallback: 21.43%
Team–Venue Data Coverage

This measures historical data availability across all 168 possible team–venue combinations.

Historical data available: 40.48%
Fallback required: 59.52%

These two metrics measure different things and should not be interpreted as the same coverage percentage.

##🏆 Key Findings

The final recommendation analysis produced the following top recommendations:

| Rank |	Team |	Recommended Venue |	Final Score |
| 1 |	Pakistan |	Queens Sports Club |	87.10 |
| 2 |	South Africa |	Buffalo Park |	85.63 |
| 3 |	Australia |	Mangaung Oval |	77.20 |
| 4 |	India |	Newlands |	76.65 |
| 5 |	Bangladesh |	SuperSport Park |	70.54 |
| 6 |	England |	Mangaung Oval |	68.78 |
|7 |	Scotland |	Queens Sports Club |	68.16 |
|8 |	Sri Lanka |	Queens Sports Club	65.27 |
|9 |	West Indies |	Harare Sports Club	63.23 |
|10 |	Ireland |	Wanderers Stadium |	62.12 |

The dashboard also provides recommendations for Zimbabwe, New Zealand, Namibia and Afghanistan.

##📈 Power BI Dashboard

The project contains a three-page Power BI dashboard.

Page 1 — Team Intelligence

Provides:

Top 10 team recommendations
Recommended venues
Recommendation data source
Team recommendation table
Historical vs fallback recommendation coverage
Project-level KPIs
Page 2 — Team Analysis

Provides:

Team-specific venue ranking
Venue score breakdown
Top recommended venues
Team recommendation summary
Historical venue analysis
Page 3 — Venue Recommendation Intelligence

Provides:

Team × Venue final score matrix
Historical data coverage
Coverage summary
Historical matches by venue
Venue-level historical analysis
