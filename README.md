# Phase 2 Project Description


## Project Overview

Our group has been employed by KC Realty Group of Seattle, WA to research and discover which combination of features in single-family homes most influence selling price. Our intent is to develop a multiple regresion model to reveal the top features that guide a home's price. For this project, we will be using the King County Housing Data Set for home sales in the year 2014 and 2015.

### Business Problem

Our group has been employed by KC Realty Group of Seattle, WA to research and discover which combination of features in single-family homes most influence selling price. Our intent is to develop a multiple regresion model to reveal the top features that guide a home's price. For this project, we will be using the King County Housing Data Set for home sales in the year 2014 and 2015.

### The Data

We had to clean out over 20,000 homes in the data set. How the dataset was broken down:<BR><BR>
Home Features:<BR><BR>
    Number of Bedrooms<BR>
    Number of Bathrooms<BR>
    Number of Floors<BR>
    Square footage of the lot <BR>
    Square footage of the living space for the nearest 15 neighbors<BR>
    Square footage of the house<BR>
    Square footage of the basement<BR><BR>
Home Quality:<BR><BR>
    The year the house was last renovated<BR>
    How good the condition of the home was (on a scale of 1-5)<BR><BR>
Location:<BR><BR>
    The zip code/city of the home<BR>
    Waterfront: Yes or No<BR>
View: Was sacled from worst to best (0-4)<BR>
    
We then dropped date, view, waterfront, yr_renovated, condition, zipcode, sqft_basement to have a better understanding of what the best features are for the home and property increase.<BR>

### Questions to be used in analysis

#### As we have discussed how to go about meeting their goals, we are centering our work around 3 questions:

Which features are most highly correlated with price?<BR>
Which features are most highly correlated with each other?<BR>
Which combinations of features best predict house prices in a multiple regression model?<BR>


##Check Correlations and Multicollinearity
Our first two questions deal with how strongly a home's price is correlated to feature variables, and understanding which feature variables are strongly correlated to each other, which can deeply affect our models. The charts and data below assist in those determinations.

## Examination of Correlations

### Heatmap 

We created a heatmap to see how the independent features might be correlated to price and to each other: 
![Heatmap](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-06%20at%206.06.06%20PM.png)

### Top 9 variables correlated with price

![Top 9](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.31.35%20AM.png)

### Top variables correlated with each other

![Correlation with each other](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.31.28%20AM.png)

### Subplots

We created subplots with our 9 variables and quickly discovered that sqft_above needed to be excluded due to the close correlation of sqft_living. We are now left with these 8 variables:
![Subplots](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-06%20at%205.32.17%20PM.png)

## Answers to Questions 1 & 2

Question 1 - Which features are most correlated with price?
Most often, a correlation of 0.7 or higher is considered highly correlated to price, however, none of our variables meet that threshold. Nonetheless, there are several variables just under the 0.7 mark - sqft_living, grade, sqft_living15, sqft_above and bathrooms represent the top five.

Question 2 - Which features are most correlated with other feature variables?
Most notable is the strong correlation between sqft_living and sqft_above, and sensibly so, since in houses without a basement, the two values would likely be the same. Also, sqft_above is strong correlated with several other variables, so it will be dropped in most of our models to avoid multicollinearity.

## Regression Modeling
We're now ready to begin our multiple regression modeling. Our process will be the same for each model, beginning with a train - test split, a scatter plot to confirm that our data is behaving in a linear fashion, and then using an ols regression test to find R-squared values and to evaluate the coeffecients. We'll bar graph our top feature coefficient results, make decisions about what's next, and repeat the process until we are satisfied that we have found the best model.

As we move forward, we must satisfy some assumptions. First, there should be a linear relationship between the target variable (price) and the feature (x) variables. Secondly, the data should be homoscedastic, that is, the residuals should have equal variance around the regression line on a scatterplot. The residuals should also follow a normal distribution. And, we are avoiding multicollinearity when possible.

We are especially interested in the R-squared value, since it tells us what proportion of the variability of y around its mean can be explained by the model. This number falls between 0 and 1, and a higher value indicates greater power in prediction. Here we go!

### Train - Test Split
The key purpose of splitting the dataset into training and test sets is to estimate how well the learned model will generalize to new data. For this reason, the train - test split is an essential component of building models.

The score for our train test:

![regscore](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.42.32%20AM.png)

#### We ran multiple models, but the one below gave us the highest R-squared value of .637

![ols](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.41.21%20AM.png)



![regression line](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.40.49%20AM.png)



![barchart](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.42.04%20AM.png)

## Results

The results of our models make recommendations difficult.  First, we had a very narrow dataset consisting of only a few years of data to build our models.  Secondly, our R-Squared values never broke the 0.7 mark after standardization, which weakened the strength of our models.  Here's a chart of our R-squared values for each model: 

![model_summ](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.21.29%20AM.png)

## Question 3

Question 3, "Which combinations of features best predict house prices in a multiple regression model?", can now be answered by recommending the use of our 1st model, which showed sqft_living, grade, view, and waterfront as the variables which have the most affect on home prices.  For each unit of increase, the home price will roughly increase as follows:

Sqft Living Space - $200<BR>
Grade - $37,000<BR>
Waterfront - $467,000<BR>
View - $69,000<BR>

We will clarify to the stakeholder that these results could be improved with more data, but that we believe they can use these features to maximize home prices and profitability for their company and clients.

## Conclusion

Our ultimate conclusion is that this dataset has a mountain of relevant information to make predictions about home prices and relevant features, but a greater range of years of sales and perhaps more data points could provide greater clarity to our analysis.  Thanks for reviewing our models!

