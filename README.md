# MLAI-CapstoneProject
This is the capstone project for my ML/AI course. In this project, I prepare a time series model to predict groceries sale. 

## Abstract
In this project, I predict groceries sales using Time Series ML/AI analysis and Linear Regression. I train my model on groceries sales data from Jan, 1992 - Mar, 2023 in the St. Louis area published by the U.S Census Bureau. In my time series analysis, I extract the trend, seasonality, and cycles of the data and use this to train and predict my model. Finally, I train a Linear Regression model against the data and compare the results of the two models against Mean Absolute Error and Root Mean Squared Error metrics.

## Data
I will using the <a href='https://fred.stlouisfed.org/series/RSGCSN'>Advanced Retail Sales: Grocery Stores</a> data published by <a href='https://fred.stlouisfed.org/'>Fred Economic Data - St. Louis Fed</a> sourced from the <a href="http://www.census.gov/">U.S. Census Bureau</a> for my analysis. 
This dataset contains sales in millions of dollars since Jan, 1992 until Mar, 2023 at a monthly frequency. This data is <u>not</u> seasonally adjusted. 
I break down the data into training and test sets: Jan, 1992 - Dec, 2016 making up the training set, and Jan, 2017 - Mar, 2023 making up the test set. 

## Model
### Time Series
* I first extracted the trend from the data and project that to the furture set (test set) using linear regression. 
* I then identified the seasonal component of the series. The seasons repeated in a cycle of 12 months. 
* I next predicted the residue using ARMA. 
* I finally added the projected trend, the season and the predicted residue to arrive at the predicted future groceries sales numbers. 

### Linear Regression
* I broke down the date field into individual Year, Month, and Day attributes to train a Linear Regression model on these 3 columns.
* But first, I used Grid Search CV to identify the best polynomial degree to use for my model. Grid Search CV recommended a polynomial degree of 7. 
* I transformed the data into degree 7 polynomial features and trained my model on it.  

## Results
The time series model gave better predictions when the future trend was predicted using a linear regression model. However, the best predictions were provided by a linear regression model on the overall series. 
![Comparision of predictions errors of different models](/Images/models_comparision.png)

## Conclusion
<b>Here are the my main findings from the project: </b>
* Assuming that the trend line will flatten in the future is an invalid assumption. We saw that the errors are the highest with the model built using this assumption. 
* Using Linear Regression to project the trend line into the future and building a time series based on that was much more accurate. The errors reduced by a factor of ~ 20% when compared to the flat trend line model. 
* Including the ARMA model's projected residue into the model had no affect. The errors remained the same. 
* The biggest surprise of the project was that <b>Linear Regression performed the best</b> out of all the models. It's errors were <u>nearly half</u> of the Time series model.

## Future Work
* I will improve the models to have better prediction accuracy.
* Put the model to practical use to make business decisions based off its predictions. 
