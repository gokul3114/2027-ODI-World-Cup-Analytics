# 🗂️ Dataset Documentation

This folder contains the structured datasets generated from the ODI cricket data analysis for the **2027 ODI World Cup Team & Venue Intelligence Analysis** project.

The datasets are prepared using Python and Pandas and are used for team performance analysis, venue scoring, recommendation generation, and Power BI visualization.

---

## 📌 Source Dataset

The analysis uses **men's ODI match data in JSON format**.

The original dataset contains **2,565 ODI match files**. The raw JSON files are not included in this repository because of their size.

The Python workflow extracts and transforms the relevant match information required for team and venue analysis.

---

## 📅 Analysis Period

The project focuses on **ODI data from 2015 onward**.

---

## 🏏 Teams Analyzed

The analysis covers 14 teams:

- Afghanistan
- Australia
- Bangladesh
- England
- India
- Ireland
- Namibia
- New Zealand
- Pakistan
- Scotland
- South Africa
- Sri Lanka
- West Indies
- Zimbabwe

---

## 🏟️ Project Scope

| Metric | Value |
|---|---:|
| Teams analyzed | 14 |
| Official venues | 12 |
| Team–venue combinations | 168 |
| Original ODI JSON files | 2,565 |
| Analysis period | 2015 onward |

---

# 📁 Dataset Files

The following CSV files are the main analytical outputs used in the project.

| File | Description |
|---|---|
| `historical_team_venue_summary.csv` | Historical ODI match summary by team and venue |
| `final_venue_ranking.csv` | Team–venue batting, bowling, overall, fallback, and final recommendation scores |
| `final_recommendations.csv` | Final recommended venue for each team with recommendation score and data source |
| `recommendation_summary.csv` | Summary metrics supporting the final recommendation analysis |
| `top_3_venue.csv` | Top three venue recommendations for each team |

These datasets are generated from the Python analysis and are used as inputs for the Power BI dashboard.

---

# 🔄 Project Workflow

The project follows an end-to-end data analytics workflow, starting with raw ODI match data and ending with team-specific venue recommendations and an interactive Power BI dashboard.

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
Performance Scoring
        ↓
Fallback Scoring
        ↓
Final Venue Ranking
        ↓
Recommendation Generation
        ↓
Power BI Dashboard
        ↓
Business Insights
```

---

# 🐍 Python Analysis

Python was used as the primary data preparation and analysis layer for processing the raw ODI JSON files and generating the datasets required for venue recommendation analysis.

## Data Extraction

The Python workflow reads the raw ODI JSON match files and extracts the relevant match and innings information required for the analysis.

The extracted data includes information related to:

- Match format
- Match date
- Teams
- Venue
- Innings
- Runs
- Strike rate
- Fours
- Sixes
- Wickets
- Economy
- Bowling average
- Bowling strike rate

---

## Data Filtering

The raw dataset was filtered to:

- Include men's ODI matches
- Include matches from 2015 onward
- Focus on the 14 teams included in the project
- Retain relevant venue information

---

## Data Transformation

The extracted match-level data was transformed into structured analytical datasets by:

- Standardizing team names
- Standardizing venue names
- Grouping historical performance by team and venue
- Aggregating batting metrics
- Aggregating bowling metrics
- Preparing performance metrics for scoring
- Creating ranking datasets
- Preparing recommendation datasets

---

# 🧹 Data Preparation

The raw ODI dataset consists of individual JSON match files. The data was processed and transformed into structured datasets suitable for team performance analysis, venue scoring, ranking, and visualization.

## 1. JSON Data Extraction

Relevant match and innings-level information was extracted from the raw JSON files using Python.

## 2. Match Filtering

The dataset was filtered to include:

- Men's ODI matches
- Matches from 2015 onward
- Matches involving the teams included in the project scope

## 3. Team Filtering

The analysis was restricted to the 14 teams selected for the 2027 ODI World Cup analysis.

## 4. Venue Standardization

Venue names were standardized to ensure consistent identification of venues across different match records.

## 5. Historical Aggregation

Match-level information was aggregated to create historical team–venue performance summaries.

This provides the basis for comparing how individual teams have performed at different venues.

## 6. Feature Preparation

Relevant batting and bowling metrics were prepared for the scoring methodology.

### Batting Metrics

- Runs per innings
- Strike rate
- Fours
- Sixes

### Bowling Metrics

- Wickets per match
- Economy
- Bowling average
- Bowling strike rate

## 7. Scoring Dataset Creation

The prepared metrics were used to generate:

- Historical team–venue summaries
- Batting performance scores
- Bowling performance scores
- Overall venue scores
- Final venue rankings
- Final recommendations

## 8. Handling Limited Historical Data

Not every team–venue combination has historical performance data.

The project therefore identifies combinations where historical team–venue data is unavailable and applies the defined **team-level fallback scoring approach**.

## 9. Power BI Data Preparation

The final analytical datasets are exported as CSV files and used as inputs for the Power BI dashboard.

---

# 🧮 Scoring Methodology

The project converts historical team performance into comparable venue performance scores.

The scoring methodology evaluates batting and bowling performance separately before combining them into an overall venue score.

## 🏏 Batting Score

The batting score considers:

- Runs per innings — **40%**
- Strike rate — **30%**
- Fours — **15%**
- Sixes — **15%**

The four components are converted into comparable percentile-based scores and combined using the above weights.

## 🎯 Bowling Score

The bowling score considers:

- Wickets per match — **40%**
- Economy — **25%**
- Bowling average — **20%**
- Bowling strike rate — **15%**

For economy, bowling average, and bowling strike rate, lower values are treated as better performance.

## 📊 Overall Venue Score

The overall historical venue performance score combines:

- Batting performance — **50%**
- Bowling performance — **50%**

The resulting score is used to compare and rank venues for each team.

### Scoring Process

```text
Batting Metrics
      ↓
Batting Score
      │
      ├──────────────┐
      │              │
      ↓              ↓
Overall Venue Score ← Bowling Score
      ↑              ↑
      │              │
      └──────────────┘
        Bowling Metrics
```

---

# 🔁 Fallback Recommendation Logic

Historical team–venue data is not available for every possible team–venue combination.

To ensure that every team receives a venue recommendation, the project applies a **team-level fallback score** when historical team–venue performance data is unavailable.

## Why Fallback Scoring Is Required

There are **168 possible team–venue combinations** across 14 teams and 12 venues.

However, historical ODI data does not provide team-specific performance information for every combination.

Instead of excluding these combinations, the project identifies missing historical coverage and applies the fallback scoring methodology.

---

## 📌 Final Recommendation Coverage

This measures whether each team's final recommendation was generated using historical venue data or fallback scoring.

| Recommendation Source | Coverage |
|---|---:|
| Historical | 78.57% |
| Fallback | 21.43% |

This means **11 of the 14 final team recommendations** are based on historical team–venue data, while **3 recommendations** use the team-level fallback approach.

---

## 📌 Team–Venue Historical Data Coverage

This measures historical data availability across all 168 possible team–venue combinations.

| Data Availability | Coverage |
|---|---:|
| Historical data available | 40.48% |
| Fallback required | 59.52% |

---

## ⚠️ Important Difference

These two metrics measure different aspects of the analysis:

- **Final Recommendation Coverage** shows the source of the final recommended venue for each team.
- **Team–Venue Data Coverage** shows the availability of historical data across all possible team–venue combinations.

Therefore, the two percentages should **not** be interpreted as the same metric.

---

## Recommendation Process

```text
Team–Venue Combination
          ↓
Historical Data Available?
       ↙       ↘
     Yes        No
      ↓          ↓
Historical    Fallback
  Score        Score
      ↘        ↙
     Final Venue Score
           ↓
      Venue Ranking
           ↓
    Team Recommendation
```

---

# 📈 Power BI Dashboard

The project includes a **three-page Power BI dashboard** designed to present team performance, venue analysis, recommendation scores, and historical data coverage.

## Page 1 — Team Intelligence

The Team Intelligence page provides an overall view of the recommendations.

It includes:

- Top team recommendations
- Recommended venues
- Recommendation data source
- Team recommendation table
- Historical vs fallback recommendation coverage
- Project-level KPIs

## Page 2 — Team Analysis

The Team Analysis page provides detailed team-specific venue analysis.

It includes:

- Team-specific venue rankings
- Venue score breakdown
- Top recommended venues
- Team recommendation summary
- Historical venue analysis

## Page 3 — Venue Recommendation Intelligence

The Venue Recommendation Intelligence page provides a detailed view of the team–venue scoring framework.

It includes:

- Team × Venue final score matrix
- Historical data coverage
- Coverage summary
- Historical matches by venue
- Venue-level historical analysis

---

## Dashboard File

```text
powerbi/2027wc_dashboard.pbit
```

---

# 💼 Business Questions Answered

The project addresses the following business and analytical questions:

1. Which venue is most suitable for each team based on historical performance?
2. How does team performance vary across different venues?
3. Which venues receive the highest performance scores for each team?
4. How much historical team–venue data is available?
5. Which recommendations are based on historical team–venue performance?
6. Where is fallback scoring required?
7. Which teams receive the highest final venue recommendation scores?
8. How do batting and bowling performance contribute to venue suitability?
9. Which team–venue combinations have historical performance data?
10. How can historical performance data be transformed into a structured venue recommendation?

---

# 💡 Business Value

This project demonstrates how historical sports data can be transformed into a structured **decision-support solution** rather than simply reporting historical statistics.

The analysis converts raw match data into measurable performance indicators and then uses those indicators to generate team-specific venue recommendations.

## Analytical Value

The project demonstrates the ability to:

- Work with large collections of semi-structured JSON files
- Transform raw match data into structured analytical datasets
- Analyze team and venue performance
- Develop a performance scoring methodology
- Handle incomplete historical data
- Apply fallback logic
- Rank alternatives based on analytical scores
- Communicate results through an interactive Power BI dashboard

---

## Decision-Support Framework

The overall analytical process follows:

```text
Raw Data
   ↓
Data Preparation
   ↓
Performance Metrics
   ↓
Scoring
   ↓
Ranking
   ↓
Recommendation
   ↓
Dashboard
```

---

# 🎓 Skills Demonstrated

## Technical Skills

**Python • Pandas • Jupyter Notebook • Power BI • DAX • JSON • CSV • GitHub**

## Data Analytics Skills

**Data Extraction • Data Preparation • Data Cleaning • Data Transformation • Data Aggregation • Exploratory Analysis • KPI Analysis • Performance Scoring • Ranking Analysis • Data Visualization • Dashboard Development**

## Business Analytics Skills

**Business Problem Solving • Comparative Analysis • Decision Support • Data-Driven Recommendations • Business Insight Generation • Analytical Storytelling**

## Data Handling Skills

**Semi-Structured Data • JSON Processing • Historical Data Analysis • Team–Venue Analysis • Missing Data Handling • Fallback Logic • Structured Dataset Creation**

---

# ⚠️ Data Availability Note

The original ODI JSON dataset contains **2,565 match files** and is not included in this repository.

Only the processed analytical CSV datasets are included in the `dataset/` folder.

The processed datasets are sufficient to review the analytical outputs and reproduce the Power BI analysis using the provided Power BI template.

---

# 📌 Project Scope Summary

This dataset package supports the analysis of:

**14 teams × 12 venues = 168 possible team–venue combinations**

The final analytical workflow uses historical performance where available and a team-level fallback score where historical team–venue data is unavailable.

The resulting scores are used to rank venues and generate team-specific recommendations for the **2027 ODI World Cup Team & Venue Intelligence Analysis**.

---

## 🔗 Related Project Files

The complete project includes:

```text
2027-ODI-World-Cup-Analytics/
│
├── README.md
│
├── python/
│   └── 2027wc.ipynb
│
├── dataset/
│   ├── historical_team_venue_summary.csv
│   ├── final_venue_ranking.csv
│   ├── final_recommendations.csv
│   ├── recommendation_summary.csv
│   ├── top_3_venue.csv
│   └── README.md
│
├── powerbi/
│   └── 2027wc_dashboard.pbit
│
├── report/
│   ├── 2027_ODI_World_Cup_Team_Venue_Intelligence_Report.pdf
│   └── 2027_ODI_World_Cup_Team_Venue_Intelligence_Report.docx
│
├── presentation/
│   └── 2027_ODI_World_Cup_Presentation.pptx
│
└── dashboard pdf/
    └── 2027wc_analysis_dashboard.pdf
```

---

## 👤 Project

**2027 ODI World Cup — Team & Venue Intelligence Analysis**

**Role:** Data Analyst / Portfolio Project

**Primary Tools:** Python, Pandas, Jupyter Notebook, Power BI, DAX, CSV, JSON, GitHub
