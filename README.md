# Executive Summary: Attrition of Frito-Lay

## Task

Students were provided with a dataset prepared by the HR department at Frito-Lay. The objective was to analyze employee attrition and build predictive models to identify factors that contribute to employee turnover. The goal was to support management in understanding key drivers of attrition and to suggest potential interventions to improve employee retention.

Following their analysis, students are to make predictions on a held out test set using their best performing model.

## Dataset

The dataset contains demographic, employment, and satisfaction-related information for employees at Frito-Lay. It includes variables such as age, job role, department, income, years at the company, jobsatisfaction, and whether the employee left the organization (“Attrition”).


## Findings

It was discovered that most attrition occurs during the first couple of years of employment, with the highest level of turnover in Entry level sales jobs.

Entry and Junior level employees that leave often work overtime and have poor work life balance.

Otherwise, lower than expected income was found to drive attrition across all departments. However, higher than average salary did not reduce attrition.

Other important elements were found to be stock option level, marital status, realtionship satisfaction, and years with current manager.

I propose that Quality of Life facotrs, overtime and work life balance, are the biggest drivers of attriton, and therefore should be adressed with intervention meatures.

## Model Metrics

This section includes metrics, which were averaged across 1000 trials.

Metrics include cost impact, and the definitions follow:
  - Cost of Attrition: Annual Salary of all employees that leave.
  - Cost of No Action: Total attrition cost if no action is taken.
  - Cost of Intervention: Quarterly (3 months) salary of all employees
  - Unrealised Attrition: True Positives, recoverable attrition loss from correctly predicted employees
  - Realized Attrition: False Negatives, unrecoverable attrition loss from employees that were not predicted to leave
  - Cost of Action: For calculating Potential Net Benefit: Cost of Intervention + Realized Attrition - Unrealized Attrition
  - Potential Net Benefit: Cost of No Action - Cost of Action

### Naive Bayes:

#### Config:
  - Brute Force (all features used)

#### Performance: 
  - Accuracy: 80.2%
  - Sensitivity: 61.2%
  - Speceficity: 83.9%
  - F1: 0.499
  - Cost of No Action: $8,059,000
  - Cost of Intervention: $2,039,000
  - Realised Attrition: $4,618,000
  - Unrealised Attrition: $3,441,000
  - Potential Net Benefit: $1,402,000

### K-NN:

#### Config:
  - K: sqrt(train size)
  - Features: MonthlyIncome, JobRole, OverTime, WorkLifeBalance, StockOptionLevel, YearsWithCurrentManager, PercentSalaryHike, RelationshipSatisfaction
  - Approach:
      - Seperate dataset by Department, train and test seperate models, merge at the end
      - Oversample examples of Attrition using SMOTE

#### Performance: 
  - Accuracy: 79.8%
  - Sensitivity: 57.2%
  - Speceficity: 84.2%
  - F1: 0.476
  - Cost of No Action: $8,059,000
  - Cost of Intervention: $2,347,000
  - Realised Attrition: $4,230,000
  - Unrealised Attrition: $3,829,000
  - Potential Net Benefit: $1,481,000



## Files
  - Case1Predict9ionsKlein Attrition.csv: Predictions on the held out test set
  - CaseStudy1-data.csv: The original dataset for analysis and model development
  - CaseStudy1CompSet No Attrition.csv: The held out test set with attrition labels removed.
  - Presentation.pptx: A powerpoint presentation of EDA, model evaluation, and reccomendations
  - Project.Rmd: R code that documents EDA and model development
