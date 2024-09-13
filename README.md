# Loan Data Analysis

## Introduction
This report provides a detailed analysis of loan data through various visualizations. The goal is to uncover insights regarding loan approvals, demographic factors, and financial behaviors.

## Data Overview
- Loan data is the information collected by financial institutions when people apply for loans. It contains various details about the applicants, their financial situation, and whether their loan applications were approved or not. This data helps banks and lenders assess whether they should approve a loan and under what conditions. It also helps them understand trends, predict loan repayment behavior, and manage risks.
- **Description**: The dataset includes information on loan applications, such as marital status, gender, income, and loan amounts.
  - **Gender**: Indicates whether the applicant is male or female.
Example: Male, Female
  - **Married**: Shows whether the applicant is married.
Example: Yes, No
  - **Dependents**: Refers to the number of dependents (children or other people financially reliant on the applicant).
Example: 0, 1, 2, 3+
  - **Education**: Specifies the educational level of the applicant.
Example: Graduate, Not Graduate
  - **Self_Employed**: States whether the applicant is self-employed or works for someone else.
Example: Yes (self-employed), No (employed by a company)
  - **Applicant_Income**: The monthly income of the main applicant.
Example: 5000, 12000 (Currency: Dollars, Pounds, etc.)
  - **Coapplicant_Income**: The monthly income of the co-applicant (if someone else is applying jointly with the main applicant).
Example: 3000, 8000
  - **Loan_Amount**: The total loan amount requested by the applicant.
Example: 150000 (in currency units)
  - **Term**: The duration or repayment period of the loan in months.
Example: 360 (30 years), 180 (15 years)
  - **Credit_History**: Indicates whether the applicant has a good credit history, meaning if they have previously repaid loans on time.
Example: 1 (Good credit history), 0 (Bad credit history)
  - **Area**: Shows where the applicant lives (urban, semi-urban, or rural area).
Example: Urban, Semi-Urban, Rural
  - **Status**: The final outcome of the loan application (whether it was approved or not).
Example: Approved, Rejected


## Visualizations
- **Marital Status vs Loan Status**
  - **Purpose**: To analyze how marital status impacts loan approval rates.
- **Gender Status vs Loan Status**
  - **Purpose**: To examine gender-based differences in loan approval rates.
- **Gender Breakdown**
  - **Purpose**: To visualize the distribution of genders among applicants.
- **Income vs Loan Amount Scatter Plot**
  - **Purpose**: To explore the relationship between applicant income and loan amount requested.
- **Education vs Loan Amount Box Plot**
  - **Purpose**: To compare loan amounts across different educational qualifications.
- **Proportion of Loans for Each Term**
  - **Purpose**: To show the distribution of loan terms among approved loans.
- **Loan Status vs Area**
  - **Purpose**: To analyze variations in loan approval rates based on geographic area.
- **Applicant Income Box Plot**
  - **Purpose**: To illustrate the distribution of applicant incomes.
- **Distribution of Applicant Income**
  - **Purpose**: To visualize the frequency of different income levels among applicants.

## Data Cleaning

### Handling Missing Values

**Overview**  
Handling missing values is crucial to ensure the accuracy and reliability of the data analysis. Missing values can skew results and lead to misleading conclusions.

**Method Used**  
- **Identification of Missing Values**: Missing values were identified using the `isnull()` function in pandas, which highlights gaps in the dataset.
- **Approach for Handling Missing Values**:
  - **Imputation**: For non-critical fields with missing values (e.g., `Dependents`, `Married`, `Gender`,  `Self_Emplyed`), missing values were imputed with the mode of the respective field to avoid data loss while preserving dataset completeness.
  - - **Prediction**: Missing values in the `Credit_History` field were predicted using a RandomForestClassifier. This model was trained on the available data to estimate the missing values based on other features.
**Examples**  
```python
# Identifying missing values
missing_values = data.isnull().sum()

# Imputing missing values with mode
data['Dependents'].fillna(data['Dependents'].mode()[0], inplace=True)

# Filling missing values with predicted values
X_missing = missing_data[features]
missing_data['Credit_History'] = model.predict(X_missing)
data.loc[data['Credit_History'].isnull(), 'Credit_History'] = missing_data['Credit_History']
```

## Results and Insights
Each visualization provides a different perspective on the loan data, helping to uncover insights into loan approval patterns, demographic influences, and financial behaviors. Together, these visualizations offer a comprehensive view of the factors affecting loan applications and approvals, which is valuable for making data-driven decisions, improving loan processes, and addressing any disparities or trends.

