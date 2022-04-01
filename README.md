# Project 2


### Contents:
- [Problem Statement](#Problem-Statement)
- [Data Dictionary](#Data-Dictionary)
- [Brief Summary of Analysis](#Brief-Summary-of-Analysis)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)


## Problem Statement

As the housing market recently has become more volatile it is important to keep in mind the housing amenities sought after when attempting to buy a home. The price of homes have several determining factors, and the presence or absence of one or more could have drastic effects or none at all. Extensive data from Ames, Iowa about a selection of homes sold between 2006 and 2010, straddling the 2008 financial crisis, could show us the predictive cost of homes when looking at the right amenities it possesses. **What ammenities in and around a home can accurately predict it's market price?**


## Why is this important?

Given the time period this data was collected, it is important knowledge to lenders and perhaps people taking out loans. Having an accurate representation of a house's value could be a factor in keeping the past from repeating itself.


## Data Dictionary

|Feature|Type|Description|
|---|---|---|
Lot Area|float|Lot size in square feet
Overall Qual|int|Rates the overall material and finish of the house
Gr Liv Area|float|Above grade (ground) living area square feet
Full Bath|int|Full bathrooms above grade
Bedroom AbvGr|int|Bedrooms above grade (does NOT include basement bedrooms)
Kitchen Qual|int|Kitchen quality
Age|int|Age of a home (subtract year built from current year)
Location|int|Diserablity of neighborhood based on houses conditions and qualities
RoadRail|int|House is near or adjacent to a railway or road
Exter Overall|int|Exterior Quality and Condition
Bsmt Overall|int|Basement Quality and Condition
Garage Overall|int|Garage Quality and Condition
Kitchen Overall|int|Kitchen above grade and its quality
Fireplace Overall|int|Fireplaces and their quality
Bath AbvGrd|int|Full Bath and Half above grade
Multi Bsmt Type|int|Basement has two types
Total FinBsmt SF|float|Total basement square footage that is finished

## Brief Summary of Analysis

I looked at real estate data for homes sold in Ames, IA between 2006 and 2010. I cleaned the data, then performed exploratory data analysis to identify the best features I could use to design a model that predicts the sale price of a home. With these features, I looked at several model options which I then ran across my testing data. Each model was scored using the same metrics, and the model with the best scores was chosen as the production model. I finished with conclusions and recommendations for the given problem.

There are two important phases one needs to consider when tuning the model:  
Feature selection  
Polynomial transformation 

Feature selection is a technique for choosing features in data that contribute most to the target variable. Here, I used a heat map to rank the features by how correlated they are with the sale price. 

![./images/correlation_features.png](./images/correlation_features.png)


Polynomial transformation is a convenient means of transforming current features by raising them to an exponent. Along with pre-processed interaction variables, allowing interaction terms to be created enmasse for the initial features made way for better predictions with each model tested. Careful not to have an overfit model, the cross-validation score was confirmed to be 0.88 with a standard deviation of 0.017. 



## Conclusions and Recommendations

**Conclusions:**  

The model shown to have the best predicting power when given the created feature was our tuned lasso model. Below is a print-out of it's scores during our training data compared to the other models tested.

|Model|Train|Test|
|---|---|---|
OLS|0.927|0.906
Ridge|0.920|0.911
Lasso|0.913|0.907


*Important coefficients to note:*
When it comes to features that bolster the price of a house, with every increase to general living area and overall quality of the house there was the most significant increase in price at 18891.90.
When it comes to features that hurt the price of the house, with every increase to general living and age of the house, there was the most significant decrease in price at -14989.19.
Below are a handful of the more significant coeffients.

|Feature|Coefficient|
|---|---|
Gr Liv Area Age|-14989.193022
Lot Area^2|-11891.397393
Overall Qual Age|-7021.798554
Bedroom AbvGr Total FinBsmt SF|-3979.916584
Location RoadRail|-3126.361184
Age Bsmt Overall|-1850.336224
Lot Area Bsmt Overall|5616.677636
Lot Area Garage Overall|5729.073846
Bedroom AbvGr Age|6863.732198
Gr Liv Area Bsmt Overall|9401.419072
Age^2|11293.478782
Overall Qual^2|11352.707594
Overall Qual Total FinBsmt SF|14131.759166
Gr Liv Area Kitchen Qual|16726.472155
Overall Qual Gr Liv Area|18891.896306

It is recommended for potential buyers and sellers of homes with certain features to use this model to help predict what the true value of a home might be.

**Next steps:**

Further evaluate and tune the model for a more accurate prediction. Consider adding/engineering more features. Clean data and better format it to prevent large discrepancies in scores early on before deciding on specific features to use.

**Resources:**

[Ames Housing Dataset Documentation](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)  
[Interpreting Interactions in Regression](https://www.theanalysisfactor.com/interpreting-interactions-in-regression/)  

**Data Source:**  

[Ames Housing Dataset](https://www.kaggle.com/prevek18/ames-housing-dataset)