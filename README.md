# classifier-analysis
Classification models comparison
## Overview - Will a customer accept the coupon?
Assignment Notebook https://github.com/johnsta123/coupon-analysis/blob/main/prompt.ipynb

The goal is to compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines).

## Dataset
**Target variable**: Y — binary, 1 if the driver accepted the coupon, 0 if rejected.
**Coupon types**: coupon column — Bar, Coffee House, Restaurant(<20), Restaurant(20-50), Carry out & Take away.
**Contextual features**: time, weather, temperature, passanger, destination, direction_same, toCoupon_GEQ5min/15min/25min.
**Behavioral features**: Bar, CoffeeHouse, RestaurantLessThan20, Restaurant20To50 — self-reported frequency of visiting each venue type.
**Demographic features**: age, maritalStatus, income, occupation, education, gender, has_children.

