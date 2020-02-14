# Ames Housing Data and Kaggle Challenge
___


## Problem Statement

Homeowners, leasing agents and developers are all interested in knowing where to best invest their money and resources in order to get the greatest return when selling a house.

Investors and realtors are also interested in knowing which houses would be most financially profitable, especially if these evaluations can be discovered first.

Based on the Ames Housing Dataset, I will create a regression model to predict the price of a house at sale.


## Exploratory Data Analysis 

**Null Values**
First, I evaluated the null values in the training data. I found that many features in the data dictionary (relating to Bsmt, Fireplace, Garage, Pool, Misc) had possible values of 'NA' that seemed to be showing up in the dataset as null instead of 'NA'. This was also verified via a value of zero in a related feature. Alley and Fence could not be verified by any other feature. Nonetheless, their missing values were replaced with 'NA', keeping in mind that these could either be unlisted or not existing properties of any single house.

The Lot Frontage features also had a large number of null values that could not be imputed since it is a continuous variable of "Linear feet of street connected to property". After replacing and dropping the columns with too many null values, the remaining rows with null values were dropped from the training data so that they did not prevent the model from running (which was less than two percent of the rows in the dataset).

**Data Types**
In reference to the data dictionary, the data types were evaluated and adjustd as needed. This included dropping the observational identifiers, converting a nominal feature from integers to strings, and assigning numerical values to ordinal features. I then created dummy variables for the remaining nominal object columns.

I also altered the year-related columns to reflect the relative values compared to the time of the sale.

**Outliers**
After reviewing the distributions of the features relative to the Sale Price, I removed a limited number of extreme outliers which seemed to reflect very unusual, atypical sales. 

**Correlations**
I then evaluated the correlations of the remaining features with Sales Price and among each other. In order to address the issue of multicollinearity, I created many interaction terms. Afterwards, I found the highest correlated features of all the existing features to the Sale Price


## Modeling the Data

**Prep the Test Data**
Since I changed many of the features in the training data, I also had to manipulate the test data to display identical changes. This included eliminating null values, changing dtypes, getting dummy variables, and adding interaction terms.

**Modeling & Evaluation**
I used linear regression to model the data, and I evaluated the results based on RMSE and the r2 score using and comparing across train-test split, cross validation, and the whole training set. I also evaluated the model when using a log of the y-variable and iterating through a variety or parameters within the Lasso and RidgeCV functions. 



## Conclusions

In conclusion, I found that creating an expansive list of interaction terms improved my model significantly and resulted in the highest correlations with the Sale Price. It seemed that the interaction between the overall quality of a house and many other features was most impactful in evaluating the Sale Price. It was also not necessary to log the Sale Price when using all of the interaction terms. 

In the end, I was able to explain 90% of the variance in the Sales Prices by the model.

Furthermore, in combining the highest correlations with the highest coefficients (all else held equal), it is likely that the best investment to increase the value of a home may be to increase the capacity of the garage to include another car. Although the features in the model were not expicitly relative to a location, in order to generalize across more than just the town of Ames, it would be best to receive similar data from other cities/towns to evaluate if the model predicts well elsewhere. 