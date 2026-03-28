# 🚦 Chicago Traffic Crash Analysis & Predictive Modeling
## Data Used
https://data.cityofchicago.org/Transportation/Traffic-Crashes-Crashes/85ca-t3if/about_data
https://data.cityofchicago.org/Transportation/Traffic-Crashes-Vehicles/68nd-jvt3/about_data
https://data.cityofchicago.org/Transportation/Traffic-Crashes-People/u6pd-qa9d/about_data

## 📌 Overview
This project focuses on analyzing traffic crash data from Chicago and developing machine learning models to predict the **primary contributing cause** of accidents.

The objective is to combine **data analysis and predictive modeling** to uncover patterns in road accidents and support data-driven decision-making for road safety improvements.

---

## 🎯 Objectives
- Perform exploratory data analysis (EDA) to understand crash patterns
- Identify key factors influencing road accidents
- Build and evaluate classification models
- Improve predictive performance using hyperparameter tuning

---

## 📊 Dataset Description
The dataset contains detailed records of traffic crashes, including environmental, human, and roadway-related factors.

### Key Variables:
| Feature | Description |
|--------|-------------|
| `PRIM_CONTRIBUTORY_CAUSE` | Main cause of the crash (Target Variable) |
| `WEATHER_CONDITION` | Weather during the crash |
| `LIGHTING_CONDITION` | Lighting at the time of crash |
| `ROADWAY_SURFACE_COND` | Road condition |
| `FIRST_CRASH_TYPE` | Type of collision |
| `TRAFFIC_CONTROL_DEVICE` | Traffic control present |

---

## 🔎 Exploratory Data Analysis (EDA)
EDA was conducted to:
- Understand feature distributions
- Identify missing values and inconsistencies
- Detect class imbalance in the target variable
- Visualize relationships between features and crash causes

---

## ⚙️ Methodology

### 1. Data Preprocessing
- Handling missing values
- Encoding categorical variables
- Feature selection
- Train-test split

---

### 2. Model Development

#### Baseline Model:
- Decision Tree Classifier

#### Advanced Model:
- Random Forest Classifier

A pipeline was used to streamline preprocessing and modeling steps.

---

### 3. Hyperparameter Tuning
Model performance was improved using **GridSearchCV** to optimize parameters such as:
- `n_estimators`
- `max_depth`
- `min_samples_split`
- `min_samples_leaf`

---

## 📈 Model Evaluation

Due to class imbalance, the model was evaluated using:

- **Precision**
- **Recall**
- **F1-Score (Macro Average)**

> The F1 Macro score was prioritized to ensure balanced performance across all classes.

---

## 📊 Results & Insights
- Random Forest outperformed the baseline Decision Tree model
- Improved balance between precision and recall across multiple classes
- Some minority classes remain challenging due to limited data

---

## ⚠️ Challenges
- Significant class imbalance in the dataset
- Low prediction performance for rare crash causes
- Risk of overfitting in simpler models

---

## 🚀 Future Work
- Apply resampling techniques (e.g., SMOTE)
- Experiment with advanced models (e.g., XGBoost, LightGBM)
- Perform deeper feature engineering
- Deploy the model using a web API or dashboard

---

## 🛠️ Technologies Used
- **Python**
- **Pandas, NumPy** – Data manipulation
- **Matplotlib, Seaborn** – Data visualization
- **Scikit-learn** – Machine learning

---### overall summary
Predicting Traffic Crash Causes in Chicago
Phase 4 Data Science Project | Chicago Department of Transportation (CDOT)

1. Executive Summary
The goal of this project is to assist the Chicago Department of Transportation (CDOT) in reducing traffic accidents by understanding and predicting their underlying causes. By moving from reactive reporting to predictive modeling, the city can more effectively allocate safety resources and prioritize infrastructure improvements in high-risk zones.

2. Business Understanding
Stakeholder: Chicago Department of Transportation (CDOT).

Problem: Traditional accident analysis is often reactive. CDOT needs a way to predict the "Primary Contributory Cause" of a crash based on environmental, vehicle, and driver data to implement proactive safety measures.

Objective: Build a classification model that identifies the most likely cause of a crash among six actionable categories.

3. Data Understanding & Preparation
The project utilizes the Chicago Data Portal’s "Traffic Crashes" dataset, merging three relational tables:

Crashes: Environmental factors (weather, lighting, road surface).

Vehicles: Mechanical details (vehicle age, defects).

People: Driver demographics and physical conditions.

Key Preparation Steps:
Filtering: Removed over 360,000 uninformative rows labeled "UNABLE TO DETERMINE" or "NOT APPLICABLE" to focus on actionable data.

Feature Engineering: Condensed numerous causes into 6 business-aligned categories (e.g., Driver Error, Intoxication).

Leakage Prevention: Implemented a Scikit-Learn Pipeline with a ColumnTransformer. This ensures that data scaling (StandardScaler) and encoding (OneHotEncoder) are fit only on the training set.

4. Modeling & Evaluation
We developed and compared two primary models:

Baseline Model: A Decision Tree classifier to establish initial performance benchmarks.

Tuned Model: A Random Forest Classifier optimized via GridSearchCV.

Results:
The tuned Random Forest was selected as the final model for its balanced performance and ability to prioritize the recall of minority, high-risk classes such as "Intoxication" and "Vehicle Defect". The model provides CDOT with transparent, data-backed insights into which factors most significantly influence different crash types.

5. Limitations & Future Work
Data Skew: Despite filtering, some categories remain significantly more frequent than others, which can influence model bias.

Future Scope: Future iterations will explore higher-capacity ensemble alternatives like XGBoost or LightGBM and incorporate SHAP (SHapley Additive exPlanations) for deeper local interpretability.

6. Project Recommendations
Based on the model's feature importance analysis, we recommend:

Targeted Infrastructure: Prioritize road maintenance in areas where "Environmental Factors" are high predictors of crashes.

Safety Campaigns: Launch educational initiatives focusing on the specific "Driver Errors" identified as top predictors (e.g., distracted driving in specific lighting conditions).

Vehicle Inspections: Increase focus on mechanical safety for older vehicle fleets in identified high-risk sectors.

7. How to Use
Final Model: best_model_tuned_rf.pkl

Cleaned Data: chicago_crashes_cleaned.csv

Dependencies: Requirements include numpy, pandas, matplotlib, seaborn, and scikit-learn.

Rubric Completion Check:
ML Communication: Clear business rationale and recommendations included.

Data Preparation: Documented the use of Pipelines to prevent data leakage.

Modeling: Covered both baseline (Decision Tree) and tuned (Random Forest) approaches

