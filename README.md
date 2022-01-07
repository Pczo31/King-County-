# Phase 2 Project Description


## Project Overview

Our group has been employed by KC Realty Group of Seattle, WA to research and discover which combination of features in single-family homes most influence selling price. Our intent is to develop a multiple regresion model to reveal the top features that guide a home's price. For this project, we will be using the King County Housing Data Set for home sales in the year 2014 and 2015.

### Business Problem

Our group has been employed by KC Realty Group of Seattle, WA to research and discover which combination of features in single-family homes most influence selling price. Our intent is to develop a multiple regresion model to reveal the top features that guide a home's price. For this project, we will be using the King County Housing Data Set for home sales in the year 2014 and 2015.

### The Data

We had to clean out over 20,000 homes in the data set. How the dataset was broken down:
Home Features:
    Number of Bedrooms
    Number of Bathrooms
    Number of Floors
    Square footage of the lot
    Square footage of the living space for the nearest 15 neighbors
    Square footage of the house
    Square footage of the basement
Home Quality:
    The year the house was last renovated
    How good the condition of the home was (on a scale of 1-5)
Location:
    The zip code/city of the home
    If the home is on the water or not
Waterfront:
    Yes or No
View:
    Was sacled from worst to best (0-4)
    
We then dropped date, view, waterfront, yr_renovated, condition, zipcode, sqft_basement to have a better understanding of what the best features are for the home and property increase.

### Questions to be used in analysis

#### As we have discussed how to go about meeting their goals, we are centering our work around 3 questions:

Which features are most highly correlated with price?

Which features are most highly correlated with each other?

Which combinations of features best predict house prices in a multiple regression model?


##Check Correlations and Multicollinearity
Our first two questions deal with how strongly a home's price is correlated to feature variables, and understanding which feature variables are strongly correlated to each other, which can deeply affect our models. The charts and data below assist in those determinations.

###Heatmap 

We created a heatmap to see how the independent features might be correlated to price and to each other: 
![Heatmap](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-06%20at%206.06.06%20PM.png)

###Top 9 variables correlated with price

![Top 9](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-07%20at%2011.24.22%20AM.png)

###Subplots

We created subplots with our 9 variables and quickly discovered that sqft_above needed to be excluded due to the close correlation of sqft_living. We are now left with these 8 variables:
![Subplots](https://github.com/jeffbeech/phase-2-project/blob/main/Images/Screen%20Shot%202022-01-06%20at%205.32.17%20PM.png)

##Answers to Questions 1 & 2

Question 1 - Which features are most correlated with price?
Most often, a correlation of 0.7 or higher is considered highly correlated to price, however, none of our variables meet that threshold. Nonetheless, there are several variables just under the 0.7 mark - sqft_living, grade, sqft_living15, sqft_above and bathrooms represent the top five.

Question 2 - Which features are most correlated with other feature variables?
Most notable is the strong correlation between sqft_living and sqft_above, and sensibly so, since in houses without a basement, the two values would likely be the same. Also, sqft_above is strong correlated with several other variables, so it will be dropped in most of our models to avoid multicollinearity.


## Recommendations

Recommendations
With the models we came up with the top four results came out to be:
Grade
Sqft of Living Space
Waterfront
View


## Conclusion
