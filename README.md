# classifier-analysis
Classification models comparison
## Overview
The goal is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines).

Assignment Notebook https://github.com/johnsta123/classifier-analysis/blob/main/prompt_III.ipynb

## Business Objective
The bank wants to increase the number of customers who subscribe to a term deposit while making fewer, better-targeted phone calls. The goal is to predict which customers are likely to say “yes” before calling them, so the contact center can focus its effort on the likeliest buyers, cut wasted calls, and lower campaign costs.
## Dataset
The data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns.

## Findings:
## Data
-duration (call length) is only known after the call, so the model should be built without it to be usable for deciding whom to call.

-Missing data is stored as the text "unknown" in six categorical columns: default, education, housing, loan, job and marital

-default is almost useless. Only 3 customers answer “yes”, and 21% are unknown, so I dropped it.

-Column names containing a dot (.): replaced the dot with an underscore (_).

-Rename column y: the target column y is renamed to subscribed (a more readable name).

-Duplicates: 12 rows are exact duplicates. They have little effect but removed that.

-column name with . : replaced the column names with . as _

## Model Scenarios and Final Takeaways:
I used these four models for two use cases.

Use case 1: Using only the bank client data features (7).

Use case 2: Using all features except duration, pdays and default.

**Where the model stands:**
| Version | Best test ROC AUC | What it means |
| --- | --- | --- |
|7 bank-information features, default settings | about 0.65, no better than baseline accuracy | Very weak signal |
|7 features, engineered and tuned | about 0.66 | Small gain |
|All features except duration,pdays | about 0.80 | Useful: precision about 0.46 vs an 11% base rate |

Decision tree and logistic regression are tied at the top, KNN is close, and the SVM is slow and weak.


## Next Steps and Recommendations:
column pdays:
value 999 means “never contacted”. It is not a real number of days.
Recommended fix: 
pdays (days since the customer was last contacted in a previous campaign) uses 999 to mean “never contacted” for 96.3% of rows. Rreplace 999 with 0 and added a binary flag pdays_never so the model can distinguish customers who were never contacted from those contacted recently.

campaign_id field: As a tool for analysis and validation add a new field campaign_id, not for the model.

Try gradient boosting and a small tuning budget, tune with RandomizedSearchCV.
Reduce collinearity among the macro features (euribor3m, emp_var_rate, nr_employed). Keep one or combine them, especially to interpret coefficients.

**what can do next:**

A time-based validation comparison, to see how much the scores drop.

A gains and lift chart plus an expected-profit threshold calculator, where you enter the cost of a call and the value of a subscription.

A gradient boosting model with calibration and a feature-importance chart.


**Demographic features**: age, maritalStatus, income, occupation, education, gender, has_children.

