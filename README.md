# RIT Student Engagement Analytics & Prediction

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-Ensemble-red)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

## Overview
An end-to-end analytics project analysing 8,558 learner-opportunity records from Rochester Institute of Technology's (RIT) professional development platform. Over four weeks, I moved from raw, uncleaned data through exploratory analysis and machine learning to a set of evidence-backed recommendations, the full lifecycle a data analyst is expected to own.

## Repository Structure
- [Overview](#overview)
- [Project Workflow](#project-workflow)
- [Business Problem](#business-problem)
- [Objectives](#objectives)
- [Dataset](#dataset)
- [Tools & Technologies](#tools--technologies)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Machine Learning Model](#machine-learning-model)
- [Dashboard Preview](#dashboard-preview)
- [Recommendations](#recommendations)
- [My Contributions](#my-contributions)
- [Acknowledgements](#acknowledgements)

## Project Workflow

Raw Dataset

↓

Data Cleaning

↓

Exploratory Data Analysis

↓

Feature Engineering

↓

Machine Learning

↓

Business Insights

↓

Recommendations

## Business Problem
RIT's platform offers students five types of opportunities: Internships, Courses, Events, Competitions, and Engagements. Some opportunities converted almost every applicant into a participant. Others rejected 4 out of 5. Program managers had no reliable way to predict which students would succeed where, or why Internships, the platform's largest and most in-demand category, consistently underperformed every other opportunity type. This project set out to answer both questions with data.


## Objectives
* Clean and validate the raw learner dataset for analysis
* Identify the strongest behavioral, demographic, and structural drivers of participation success
* Build a predictive model to estimate participation probability per opportunity
* Translate findings into actionable, KPI-backed recommendations for program managers

## Dataset
* Source: Rochester Institute of Technology (RIT) learner engagement platform, provided via an Excelerate data internship partnership
* Size: 8,558 learner-opportunity records, 16 original fields (expanded to 43 after feature engineering)
* Scope: 22 unique opportunities across 5 categories, spanning 71 countries and two academic years (2022–2024)
* Target variable: Is_Successful — 1, if a learner was Team Allocated or Started an opportunity, 0 otherwise

## Tools & Technologies
* Excel
* Power BI
* Python 3.10 (pandas · numpy · scikit-learn · XGBoost · matplotlib / seaborn) 
* Google Colab


## Methodology
### 1. Data Cleaning
* Standardized all column names using snake_case.
* Cleaned inconsistent text fields.
* Normalized institution and academic major names using lookup tables.
* Corrected inconsistent date formats.
* Removed invalid records and age-ineligible learners.
* Produced an analysis-ready dataset for EDA and modeling.

### 2. Exploratory Data Analysis
Engineered 13 new features (age, days-to-apply, signup timing bins, cohort period, etc.); 
analyzed success rate by category, geography, major, gender, and timing.

### 3. Feature Engineering & Modeling
Examples of engineered features include:
* Age
* Days_To_Apply
* Signup_Month
* Signup_Quarter
* Engagement_Duration_Days
* Duration_Band
* Country_Group
* Major_Group
* Is_Successful
  
### 4. Insight Synthesis
Converted model output and EDA findings into prioritized, KPI-backed recommendations for stakeholders.


## Key Findings
* Opportunity Category drives everything, success ranges from 21.5% (Internship) to 96.9% (Engagement);
* Internships alone make up 63% of all applications.
* Timing matters, applicants who apply 30–90 days after signup succeed at 53.9%, ~7 points above the platform average.
* Persistence pays, repeat applicants succeed at 54% vs. 41% for first-timers.
* Geography reveals inequity, the US supplies 46.5% of applications but converts at only 39.5%, while Egypt (78%), Kenya (73.7%), and Pakistan (71.2%) convert far higher on a fraction of the volume.
* A pipeline anomaly, January 2024 saw an all-time-high 1,509 applications crash to a 27% success rate after one Internship was oversubscribed.
* One outlier worth studying, Health Care Management Internship converts at 54.8%, the only Internship beating the platform average.

## Machine Learning Model
Three classifiers were trained and combined into a weighted ensemble to predict participation success:

| Model | Accuracy | AUC-ROC | Role |
|---|---|---|---|
| Logistic Regression | 86.0% | 0.958 | Interpretable baseline |
| Random Forest | 94.3% | 0.985 | Lowest false-negative rate |
| XGBoost | 93.6% | 0.985 | Best raw predictive power |
| **Ensemble (50% XGB / 35% RF / 15% LR)** | — | **0.985** | Final probability score used for every ranking |

5-fold cross-validation confirmed the models generalise well, with no meaningful gap between test and CV scores. Two features (Duration Band and Opportunity Category), account for roughly 80% of the model's predictive power, confirming that what a student applies to matters far more than who they are.

## Dashboard Preview
A Power BI dashboard was built alongside the analysis to track:
* Total learners, average age, and median apply time at a glance
* Enrollment distribution by opportunity category (treemap)
* Peak engagement traffic by sign-up period
* Application delay patterns by status and gender

### Dashboard Showing Student Performance and Engagement
<img width="800" height="341" alt="image" src="https://github.com/user-attachments/assets/7ab3fdd8-4dea-4f96-ad32-151a1ebf9ec4" />

### Dataset Overview
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/1df54d1d-ba61-42ca-b806-fd0bc362b0ab" />

### Geographic Distribution of Learners
<img width="800" height="332" alt="image" src="https://github.com/user-attachments/assets/375b9019-872e-4955-ba32-d693b010168c" />

### Geographic & Academic Insights
<img width="800" height="330" alt="image" src="https://github.com/user-attachments/assets/5af8ba50-b153-419a-8cdf-f6eb5dce7a2c" />

### Gender Distribution Table
<img width="800" height="130" alt="image" src="https://github.com/user-attachments/assets/99204be2-bb3d-4173-b764-04dac296a854" />

### Top 10 most Popular Programs
<img width="800" height="281" alt="image" src="https://github.com/user-attachments/assets/431d70b7-0ea0-42b7-a50a-b1a7465fcd0b" />

### Opportunity Category Analysis
<img width="800" height="294" alt="image" src="https://github.com/user-attachments/assets/1b406d23-ec43-4459-9ce0-e2a0fbe14db0" />

### Temporal Participation Trends
<img width="800" height="422" alt="image" src="https://github.com/user-attachments/assets/fbfbba32-9bda-4bab-8a4f-061f14b8cec6" />


## Recommendations
* Scale what already works — expand seats in Courses, Events, and Engagements (84–97% success, near-zero dropout).
* Nudge application timing — a "Day-30 reminder" campaign to push applicants into the highest-converting window.
* Replicate the outlier — study why Health Care Management Internship outperforms every other internship and copy the model.
* Close the internship supply-demand gap — recruit more host partners and auto-redirect rejected internship applicants into equivalent high-converting courses.
* Smooth the pipeline — stagger release dates so no single month gets flooded the way January 2024 was.
* Fix the post-placement dropout leak — all 617 dropouts came from Internships and propose 2- and 4-week onboarding check-ins.

Target KPI: lift platform-wide success from 47.2% → 55%+ within two cohort cycles.


## My Contributions
* Cleaned and validated the dataset
* Engineered analytical features
* Performed exploratory data analysis
* Evaluated machine learning models
* Developed stakeholder recommendations
* Co-presented project findings

## Acknowledgements
This project was completed as part of a Data Insight internship with Excelerate, using a learner engagement dataset provided through Excelerate's partnership with Rochester Institute of Technology (RIT). Thanks to my fellow team members (Aforke Ejoor, Momina Kayani, Ramakrishna Jalakam) for their collaboration across all four weeks of this project.

## Conclusion
This project demonstrates an end-to-end analytics workflow, from cleaning raw operational data through predictive modelling and business recommendation development. Beyond model performance, the project emphasizes translating data into decisions that improve learner engagement and program outcomes.
