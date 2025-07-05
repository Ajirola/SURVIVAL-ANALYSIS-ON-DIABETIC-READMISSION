# SURVIVAL-ANALYSIS-ON-DIABETIC-READMISSION

## TABLE OF CONTENTS  

[Project Overview](#-project-overview)

[Description](#-description)  

[Problem Statement](#-problem-statement)  

[Project Objective](#-project-objective)  

[Key Areas Analyzed](#-key-areas-analyzed)  

[Data Source](#-data-source)  

[Dataset Description](#-dataset-description)  

[Tools](#-tools)  

[Methodology](#-methodology)  

[Data Cleaning](#-data-cleaning)  

[Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)  

[Statistical Insights and Data Visualization](#-statistical-insights-and-data-visualization)  

[Recommendation](#-recommendation)  

[Acknowledgement](#-acknowledgement)  

[Contact](#-contact)  

## 📖 Project Overview  
This project explores **time-to-event** data using **survival analysis** to investigate hospital readmission patterns among **diabetic patients**. Using **Kaplan-Meier estimators**, **log-rank tests**, and **the Cox Proportional Hazards Model**, we identify key factors contributing to early readmissions.

## 📌 Description
**Survival analysis** is applied to diabetic US-hospital data for years **1999-2008** to study the duration until a patient is readmitted. The focus is on determining whether characteristics such as **insulin use**, **age**, and **medication count** affect **readmission time**.

##❓ Problem Statement
Hospital readmission within 30 days is a major concern in diabetic care, indicating potential issues in patient management. Understanding the survival patterns of diabetic patients and identifying predictors of early readmission can improve care planning.

##🎯 Objective
To project aim to:
- Estimate survival times of diabetic patients
- Test differences in survival between groups using log-rank tests
- Assess the impact of variables using Cox regression 
- Check proportional hazards assumptions

## 🔍 Key Areas Analyzed

- **Time in Hospital** as survival duration
  
- **Readmission Status**: (readmitted within 30 days or not)  

- **Insulin Types**: (Up, Down, Steady)  

- **Age Groups**: ([0-10), [10-20) ...[90-100))  

- **Medication Level**: grouped into (Low, Moderate, High, Very High)

## Data Source
The dataset was obtained from the **UCI Machine Learning Repository**.

Name: **Diabetes 130-US hospitals for years 1999–2008**

Link to the dataset: https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008
