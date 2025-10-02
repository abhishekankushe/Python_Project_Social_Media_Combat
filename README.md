# Python_Project_Social_Media_Combat

Social Media Combat: EDA, Risk Scoring, and Digital Detox
A data science project analyzing student social media usage to uncover patterns across demographics, quantify addiction risk, and auto‑suggest digital detox strategies using explainable, rule‑based classification with clear EDA and storytelling deliverables.

Highlights
End‑to‑end EDA on usage, sleep, mental health, and conflicts, with clear plots and labeled insights for stakeholders.

Transparent risk tiers derived from AvgDailyUsageHours and mapped, actionable detox suggestions per student.

Reproducible notebook with consistent schema, no missing values in the provided sample, and exportable artifacts.

Table of contents
Overview

Dataset

Project structure

Environment setup

How to run

Methodology

Results

Visuals

Reproducibility and next steps

Ethics

Author and license

Overview
This project explores how daily social media usage relates to sleep, mental health, and relationship conflicts among students, building risk tiers and recommendations to support healthier usage patterns and communication with non‑technical stakeholders.

Dataset
File: Students-Social-Media-Addiction.csv with 705 student‑level rows across diverse countries and platforms for EDA and feature derivation.

Key fields:

StudentID: Integer unique identifier.

Age: Integer 18–24 across High School, Undergraduate, Graduate cohorts.

Gender: Categorical (Male, Female).

AcademicLevel: Categorical (High School, Undergraduate, Graduate).

Country: Categorical with broad geographic coverage (e.g., India, USA, UK, Japan).

AvgDailyUsageHours: Float hours/day, typical range ~1.5–8.5, used for risk tiers.

MostUsedPlatform: Categorical (Instagram, TikTok, YouTube, Facebook, LinkedIn, Twitter/Snapchat) plus regional platforms (WeChat, LINE, KakaoTalk, VK, WhatsApp).

AffectsAcademicPerformance: Yes/No self‑report.

SleepHoursPerNight: Float ~3.8–9.6 hours/night.

MentalHealthScore: Numeric 1–10 style proxy with values in ~4–9.6 range in the file.

RelationshipStatus: Single, In Relationship, Complicated.

ConflictsOverSocialMedia: Integer frequency score (0–9 visible).

AddictedScore: Integer/ordinal indicator (e.g., 1–9 in file).

Quality notes:

Column names are consistent and load cleanly via read_csv; showcased rows indicate no nulls and appropriate dtypes, though dtype enforcement is shown in the notebook as a safeguard.

Derived fields:

RiskLevel from AvgDailyUsageHours: <3 Low, 3–6 Medium, >6 High.

DetoxSuggestion from RiskLevel for tailored guidance.

Project structure
notebooks/ Python_Project_Social_Media_Combat_By_Abhishek_Ankushe.ipynb (Colab/Jupyter EDA, risk rules, visuals).

data/ Students-Social-Media-Addiction.csv (place actual CSV here; adjust path in notebook).

reports/ Python_Project_Social_Media_Combat_By_Abhishek_Ankushe.pdf (narrative outputs and screenshots).

src/ Optional utilities for loading, plotting, and rules if modularizing from the notebook.

Environment setup
Core libraries:

Python 3.x, pandas, numpy, seaborn, matplotlib; optional Google Colab for Drive mount and execution.

Quick install:

pip install pandas numpy seaborn matplotlib jupyter.

How to run
Open the notebook:

Launch notebooks/Python_Project_Social_Media_Combat_By_Abhishek_Ankushe.ipynb in Jupyter or Colab; if using Colab, run Drive mount and set the CSV path accordingly.

Execute cells in order:

Load CSV and validate df.head/df.describe/isnull/dtypes; optional dtype enforcement examples are included.

Run EDA: usage by age/gender; addiction by age/education/gender; sleep vs academic impact; sleep vs mental health; relationship vs conflicts.

Plot correlation heatmap over numeric features (usage, sleep, mental health, conflicts, addiction).

Create RiskLevel via classify_risk(AvgDailyUsageHours) and DetoxSuggestion via suggest_detox(RiskLevel); inspect value_counts and samples.

Render labeled plots (bar, pie, line, heatmap) and export artifacts as needed.

Optional exports:

Save figures to reports/ and an enriched CSV with RiskLevel and DetoxSuggestion to data/ for downstream BI or app integration.

Methodology
EDA: Groupby summaries, descriptive stats, and seaborn/matplotlib visualizations to surface demographic and behavioral patterns.

Rules: Simple thresholds on AvgDailyUsageHours for explainable Low/Medium/High risk tiers, then mapped detox guidance to ensure clarity for non‑technical audiences.

Communication: A concise 10‑line narrative and labeled plots for stakeholder consumption.

Results
Usage patterns: Age 18 shows the highest average daily usage; females slightly higher than males overall in this dataset.

Addiction patterns: High School cohort and age 18 exhibit the highest addiction levels; gender differences are small.

Well‑being links: Higher usage correlates positively with AddictedScore and conflicts, and negatively with sleep hours and mental health scores, with strong magnitudes in the heatmap.

Risk distribution: Medium Risk is the largest segment; High and Low are smaller; each student receives a tailored detox suggestion.

Visuals
Includes:

Bar chart: Average AddictedScore by AcademicLevel with value labels.

Pie chart: Risk level distribution.

Heatmap: Correlations of key numeric variables with annotations.

Line plot: AvgDailyUsageHours by Age with point labels.

Reproducibility and next steps
Deterministic rules ensure consistent outputs; modularization can move logic to src/ for reuse and testing.

Extensions:

Feature engineering and ML to predict AddictedScore/RiskLevel; benchmark Logistic Regression, Trees/GBMs; add SHAP for interpretability.

Build a Streamlit or Power BI dashboard for operational use by educators or counselors.

Add unit tests and CI to validate data loading, rule logic, and plot generation.

Ethics
Treat sensitive attributes carefully; the dataset appears suited for academic demonstration, but real deployments require consent, privacy protections, and cautious interpretation of correlations without causal claims.

Quick code snippet (risk rules)
python
def classify_risk(usage_hours: float) -> str:
    if usage_hours < 3:
        return "Low Risk"
    elif 3 <= usage_hours <= 6:
        return "Medium Risk"
    else:
        return "High Risk"

def suggest_detox(risk_level: str) -> str:
    if risk_level == "High Risk":
        return "Consider significantly reducing usage, set strict limits, and seek professional help if needed."
    elif risk_level == "Medium Risk":
        return "Set daily time limits, schedule screen-free activities, and be mindful of usage."
    else:
        return "Maintain healthy habits and awareness."
Author and license
Author: Abhishek Ankushe; notebook and report curated for EDA and data storytelling.

License: Recommend MIT for code; confirm data usage rights based on the CSV provenance before redistribution.
