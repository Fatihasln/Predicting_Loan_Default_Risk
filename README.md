Credit Risk Analysis & Predictive Modeling

📖 Project Overview

This project focuses on building a machine learning model to predict the likelihood of a loan applicant defaulting. The goal is to assist financial institutions in making data-driven lending decisions to mitigate risk.

The workflow encompasses a full data science pipeline:

Exploratory Data Analysis (EDA) to understand the data structure and distributions.

Data Preprocessing to handle missing values and encode categorical variables.

Feature Engineering to create powerful new predictors.

Unsupervised Learning (PCA & K-Means) to identify natural customer segments.

Supervised Learning to train and evaluate multiple classification models.

Model Evaluation & Selection to choose the best-performing model for deployment.

The XGBoost model emerged as the most effective predictor of credit default risk.

📊 Dataset
The dataset used is credit_risk_dataset.csv, which contains 32,581 observations and 12 features related to personal, financial, and loan-specific attributes.

Key Features:

person_age: Applicant's age

person_income: Annual income

person_home_ownership: Home ownership status (e.g., Rent, Mortgage, Own)

person_emp_length: Employment length (in years)

loan_intent: The purpose of the loan

loan_grade: Loan grade assigned by the lender (A-G)

loan_amnt: The amount of the loan applied for

loan_int_rate: The interest rate for the loan

loan_status: Target variable (0 = non-default, 1 = default)

loan_percent_income: Loan amount divided by annual income

cb_person_default_on_file: Historical default status

cb_person_cred_hist_length: Credit history length

🛠️ Methodology & Steps
1. Data Preprocessing & EDA
Missing Value Imputation: Median imputation was used for missing values in person_emp_length and loan_int_rate.

Data Visualization: Histograms and bar plots were used to understand the distribution of numerical and categorical variables. The target variable was found to be imbalanced (~21.8% default rate).

Outlier Handling: Outliers were identified in features like person_age and noted for context.

2. Feature Engineering
One-Hot Encoding: Applied to categorical variables (person_home_ownership, loan_intent, loan_grade).

New Feature Creation: The most impactful feature, income_loan_ratio (person_income / loan_amnt), was created to measure a borrower's ability to service debt.

Feature Scaling: All numerical features were standardized (mean=0, std=1) to ensure equal contribution during model training.

3. Unsupervised Learning - Customer Segmentation
Dimensionality Reduction (PCA): The first 15 principal components were selected, explaining ~95% of the variance in the data.

Clustering (K-Means): The Elbow Method determined the optimal number of clusters to be K=3.

Cluster 1 (High Risk): 38% default rate, lower income, typically renters, loan grade 'C'.

Cluster 2 (Low Risk): 10% default rate, highest income, typically have a mortgage, loan grade 'A'.

Cluster 3 (Medium Risk): 24% default rate, mixed home ownership, loan grade 'B'.

4. Predictive Modeling
Three classification models were trained on an 80/20 train-test split:

Logistic Regression (Baseline model)

Random Forest (Robust ensemble method)

XGBoost (High-performance gradient boosting)

5. Model Evaluation
Models were evaluated based on Accuracy, Precision, Recall, F1-Score, and ROC-AUC.

Model	Accuracy	Precision	Recall	F1-Score	ROC-AUC
Logistic Regression	0.861	0.882	0.950	0.915	0.871
Random Forest	0.931	0.924	0.994	0.958	0.935
XGBoost	0.936	0.929	0.995	0.961	0.948
🏆 Results & Conclusion
Best Model: XGBoost achieved the highest test ROC-AUC score of 0.948, demonstrating superior performance in distinguishing between defaulting and non-defaulting applicants.

Key Drivers of Risk: The top 5 most important features identified by the XGBoost model were:

income_loan_ratio (Engineered feature)

loan_int_rate

person_home_ownership_RENT

person_income

person_emp_length

Business Impact: This model can be deployed as a reliable tool to support credit approval decisions, helping to minimize financial risk and improve lending strategies. The customer segments identified can also be used for targeted marketing.
