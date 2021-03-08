

# DSI Project 2: Ames Housing Sale Price Prediction


### Problem Statement

In 2011, the Ames Assessor's Office received several requests from the current homeowners asking for advices on remodelling their houses. Homeowners wanted to know which features of the houses should they focus on to make the highest return from sales. Additionally, they wanted to know the future sale prices of those houses given those certain housing features. 

As an employee in the Ames Assessor's Office, I am tasked with creating regression models based on the Ames Housing Dataset, which contained the assessed values for individual residential properties sold in Ames, IA from 2006 to 2010. This model will predict the price of a house at sale and indicate what features have the most and least effect on the house price. I will use R2 and RMSE as evaluation metrics for my models.

### Executive Summary

I started off the project by importing the relevant libraries and two datasets: Train and Test. Train dataset is the data that is needed to be fitted with the Test dataset to evaluate the model. Both datasets have the same features of the house, but Train dataset has the additional feature of "SalePrice", which is our target variable. 

I looked at size and general information of the datasets. Then, I began cleaning the dataset by filling in the missing data as we cannot have null values in our model. I explored the data visualization of the train dataset through histograms, heat map, box plots, and scatter plots. The visualization provided the insights in terms of correlation and outliers between the target variable and other features. I found that the top features for my regression model would be Overall Qual, Gr Liv Area, Garage Area, and Garage Cars as these features have the strongest positive correlation to Sale Price. I also created dummy variables for nominal data and mapped ordinal data with corresponding values based on information given in data dictionary. Then, I dropped some outliers to ensure better prediction for the model. 

I used train/test split to fit both datasets to one another. Then, I created the model benchmarks and linear regression model.I used R2 and RMSE as evaluation metrics for my model. Additionally, I used Ridge and Lasso regression to regularize my regression model. After finding the optimal alpha, I ran the models to find that Lasso regression performed slightly better than Ridge regression, hence I used Lasso model for my final evaluation and Kaggle submission. 

### Conclusion and Recommendations

|Regression Model|Training CV $R^2$ Score|Training CV RMSE Score|
|---|---|---|
|Linear Model|-6.203|1069556644863256|
|Ridge Model|0.898|25097|
|Lasso Model|0.902|24641|

|Regression Model|Testing $R^2$ Score|Testing RMSE Score|
|---|---|---|
|Lasso Model|0.917|22841|

Comparing between the three models, Lasso regression model is the best model because it is best at predicting unseen data as well as giving the least estimated errors. However, the model is slightly underfit because it has high bias and low variance. We can consider removing more outliers from train dataset to lower RMSE.

Looking at coefficients, we found the best features to be used to predict the house price are Gr Liv Area, Overall Qual, BsmtFin SF 1, Year Built, and Total Bsmt SF. On the other hand, the worst features are Condition 1_RRNn, Low Qual Fin SF, MS SubClass_90, Exterior 2nd_AsphShn, and House Style_2.5Fin. The two neighborhoods that might be a good investment are in Neighborhood_NridgHt and Neighborhood_StoneBr. So, these features are the key features of the house that homeowners should consider in order to make highest return from sales. 

The model can be used on other city housing data as well since top features in the model should be similar to any other cities. However, the model can be improved by having the time the house was sold as another feature to get a better prediction on the sale price. 

Some further steps that we can consider are to include the time the house was sold as another feature, whether interaction terms will improve the prediction, what are other outliers we can remove, and whether the prediction is still accurate when apply with other cities housing data.