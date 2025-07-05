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

## ❓ Problem Statement

Hospital readmission within 30 days is a major concern in diabetic care, indicating potential issues in patient management. Understanding the survival patterns of diabetic patients and identifying predictors of early readmission can improve care planning.

## 🎯 Objective

This project aim to:
1️⃣ Estimate survival times of diabetic patients
2️⃣ Test differences in survival between groups using log-rank tests
3️⃣ Assess the impact of variables using Cox regression 
4️⃣ Check proportional hazards assumptions

## 🔍 Key Areas Analyzed

1️⃣ Kaplan-Meier survival curves by:

  - Age group
    
  - Insulin usage
    
  - Medication group
    
2️⃣ Log-rank tests for group comparison
   
3️⃣ Cox Proportional Hazards Model (with and without stratification)  

4️⃣ Statistical assumption checking

## 🗃️ Data Source

The dataset was obtained from the **UCI Machine Learning Repository**.

Name: **Diabetes 130-US hospitals for years 1999–2008**

Records: **101,766** diabetic hospital encounters

Link to the dataset: https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008

## 📂 Dataset Description  

The dataset contains demographic information, lab results, and hospital outcomes for diabetic patients.

-**Total Records**: 101,766  

- **Initial Columns**: 50
 
For this project, the key variables used include:  

- **readmitted**: Whether the patient was readmitted within 30 days  

- **time_in_hospital**: Number of days spent in the hospital  

- **age**: Patient age group
  
- **insulin**: Insulin usage pattern
  
- **num_medications**: Number of medications prescribed

## 🛠️ Tools Used

- **Language**: Python

- **Libraries**: pandas, numpy, matplotlib, Seaborn, lifeline

## 📒 Methodology  

1️⃣ Import and clean dataset  
2️⃣ Define event and duration variables  
3️⃣ Encode categorical features and group medications  
4️⃣ Plot Kaplan-Meier curves and conduct log-rank tests  
5️⃣ Fit and validate Cox Proportional Hazards models  
6️⃣ Stratify by med_group to handle assumption violations

