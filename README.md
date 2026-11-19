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
-Duplicates: 12 rows are exact duplicates. They have little effect but removed that.

**Demographic features**: age, maritalStatus, income, occupation, education, gender, has_children.

