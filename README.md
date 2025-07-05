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

- **Total Records**: 101,766  

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

## 🧹 Data Cleaning  

To ensure data quality and suitability for survival analysis, several preprocessing steps were performed:

### 1️⃣ Variable Selection  
Only variables relevant to the survival analysis were retained from the original dataset containing 50 columns. The selected variables were:

- age
- time_in_hospital
- num_lab_procedures
- num_medications 
- number_diagnoses
- insulin
- readmitted 

✅ This step reduced the dataset to a focused subset of **7 key features** for time-to-event modeling.

### 2️⃣ Check for Missing Values  
A missing value assessment was conducted across the selected columns.

✅ **No missing values** were detected in the final filtered subset used for survival analysis.

### 3️⃣ Remove Duplicates  
Duplicate entries can bias model estimates and inflate sample size.

- A check revealed **3,877 duplicate rows**.
  
- All duplicate rows were removed to ensure each patient encounter was uniquely represented.

✅ Final data had **no remaining duplicates**.

### 4️⃣ Filter Invalid or Unknown Categories  
Certain values were invalid or non-informative for modeling:

- Rows with **invalid or unknown ag values** (e.g., **?**) were removed.  

- The **insulin variable** initially included non-standard values like **No**
 
✅ The dataset was filtered to keep only valid insulin usage types:  
 **Up**, **Down**, **Steady**.

### 5️⃣ Define Event and Duration for Survival Modeling  

Two critical columns were created for survival analysis:

- **event**: Indicates whether the patient was readmitted within 30 days  
  - **event = 1** if **readmitted == '<30'**
  - **event = 0** if **readmitted == No or >30**

- **duration**: Time spent in hospital, used as the survival time  
  - **duration = time_in_hospital**

✅ These columns allowed modeling of time-to-event outcomes.

### 6️⃣ Categorical Variable Transformation  

- The **age variable** was stored in ranges like **[60-70)**, so it was converted into an **ordered categorical variable** to preserve group structure during modeling and plotting.
  
- The custom order was defined as:  
  [0-10), [10-20), [20-30), [30-40), [40-50), [50-60), [60-70), [70-80), [80-90), [90-100)
  
### 7️⃣ Medication Grouping  

To analyze the effect of medication usage more meaningfully, the continuous variable **num_medications** was converted into **categorical bins** to form a new column **med_group**:

- **Low**: 0–10 medications
- **Moderate**: 11–20
- **High**: 21–40  
- **Very High**: 41 and above  

✅ This grouping allowed for better interpretation in visualizations and Cox modeling.

### ✅ Final Dataset Summary  

| Step                         | Result            |
|------------------------------|-------------------|
| Initial Rows                 | 101,766           |
| After removing duplicates    | 97,889            |
| After filtering and cleaning | 54,383            |
| Final Columns                | 10                |

The dataset was now clean, well-structured, and ready for **exploratory data analysis** and **survival modeling**.
## 📈 EXPLORATORY DATA ANALYSIS (EDA)

### 📊 Descriptive Statistics

The dataset captures patient-level information on hospital stay, medications, insulin usage, and readmission outcomes, providing rich insights into the risk factors for early hospital return.

- **Mean number of medications**: 16  
- **Standard deviation of medications**: 8.12  
- **Minimum medications prescribed**: 1  
- **25% (Q1)**: 10  
- **50% (Median)**: 16  
- **75% (Q3)**: 21  
- **Maximum medications prescribed**: 81  

- **Mean time in hospital**: 4.7 days  
- **Standard deviation**: 3.4 days  
- **Minimum**: 1 day  
- **Maximum**: 14 days

1️⃣ **Medication count** ranged from **1 to 81**, with a **median of 16**, showing that half of the patients were prescribed more than 16 medications, reflecting polypharmacy common in chronic conditions like diabetes.

2️⃣ The **average number of medications** was **16**, with 75% of patients prescribed up to **21 medications**, suggesting a moderate-to-high treatment burden.

3️⃣ The **average hospital stay** was approximately **4.7 days**, with most patients staying less than a week. Only a few had extended stays up to **14 days**, which could indicate complications or comorbidities.

4️⃣ The **interquartile range** (10 to 21 meds) suggests that **50%** of patients were prescribed between **10 and 21 medications**, offering a baseline for grouping medication levels (Low–Very High).



5️⃣ Most patients were **not readmitted within 30 days**, but a meaningful subset had early readmissions setting the stage for analyzing the influence of age, insulin usage, and medication group on survival probability.

## 📊 Statistical Insights and Data Visualization  

## 📉 Kaplan-Meier Survival Curves
Kaplan-Meier (KM) estimators were used to visualize the probability of **not being readmitted within 30 days** after hospitalization among diabetic patients. These curves help us understand how long patients stay "readmission-free" and how different variables impact that duration.

### 1️⃣ Overall Survival Curve (All Patients)
This Kaplan-Meier curve shows the **overall survival probability** across all patients in the dataset, without dividing them into subgroups.

![Screenshot](Screenshot_20250705-023516.jpg)


- The survival probability starts at 1 (100%) and gradually decreases over time.
- A noticeable drop occurs within the first few days, indicating that **early readmission is fairly common**.
- Most patients were **not readmitted** within 30 days, as shown by the curve leveling off toward the end.

 **Interpretation**: While the overall risk of readmission is moderate, a subset of patients is vulnerable to being readmitted shortly after discharge. This supports the need for identifying high-risk groups using additional variables.
 
 ### 2️⃣ Survival Curve by Insulin Type
This curve compares survival probabilities based on insulin usage: **Up**, **Down**, and **Steady**.

![Screenshot](Screenshot_20250705-023540.jpg)
- Patients with **Steady insulin** had the **highest survival probability**.
- Those with **Up insulin changes** experienced the **steepest decline**, meaning they were readmitted sooner.
- Patients on **Down insulin** fell in between.

 **Interpretation**: Patients whose insulin dosage was increased (Up) might be undergoing more severe diabetes episodes, leading to early readmissions.

 ### 3️⃣ Survival Curve by Age Group
This KM curve divides patients into **age brackets** (e.g., [20–30), [30–40), ..., [90–100)).

![Screenshot](Screenshot_20250705-023559.jpg)
- **Younger age groups** had **higher survival probabilities**.
- The **elderly (especially 80+)** were more likely to be readmitted early.

**Interpretation**: Age significantly impacts readmission risk. Older patients often have multiple comorbidities, reduced recovery capacity, or challenges with managing their medications post-discharge.

### 4️⃣ Survival Curve by Medication Group

Patients were grouped based on the number of medications prescribed:
- **Low**: 0–10 medications
- **Moderate**: 11–20
- **High**: 21–40
- **Very High**: 41+

 ![Screenshot](Screenshot_20250705-023613.jpg)

- The **‘Very High’ group** showed the **highest survival**, suggesting robust medical management.
- The **‘Low’ group** had the **lowest survival**, which may reflect under-treatment or lack of follow-up care.

**Interpretation**: Polypharmacy (taking many medications) may sometimes be protective if it reflects better chronic disease management and adherence to treatment.


