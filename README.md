# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
- Learn more about API data
- Formatting data in a way that makes sense
- Practice EDA process
- Practice building Models


## Process
### Getting Data
- Going to the City Bikes and check what can we obtain as data
- Getting a list of cities, and choose one of them
- Getting all bike stations in that city and format as DataFrame
- Going to Foursquare and Yelp API and check how we can get relevant business information  around the stations
- Testing the APIs on Postman
- Querying data as JSON from the two endpoints
- Formatting the JSON data as Dataframes and storing in CSV
### EDA process
- Checking which columns have null values
    - Listed the top 20 columns with the most null values
    - Removed the top 18 (e.g. most ‘geocode’ columns)
- Fill null values
    - Filled ‘rating’, ‘distance’, and ‘review_count’ with mean values for each bike station
- Formatting to the correct data types
    - Changed price from ‘$$$’ to 3
- When merging data from the two endpoints, make sure that the data are on the same scale
    - For rating, Foursquare ratings from on a scale from 1 to 10, while Yelp is from 1 to 5, so doubled the ratings from Yelp
- Changing the scale of columns
    - Changed the scale of price from 1-4 to 1-10
- Merging data from bike stations and POIs
- Check which numerical characteristics are more relevant
    - Most relevant columns: Distance, rating, price, review count

### Model Building
- Chose OLS linear regression model for simplicity
- Verify model accuracy
    - Check R-squared values



## Results
### API coverage

For Yelp and Foursquare, I chose to look at the number of restaurants in the area. I found that Yelp had more coverage than
Foursquare because while Foursquare gets an average of 9.5 locations per bike station, Yelp gets an average of 19.2 points of interest, which is more than double.
### Model accuracy

```
                                 OLS Regression Results                                
=======================================================================================
Dep. Variable:             free_bikes   R-squared (uncentered):                   0.603
Model:                            OLS   Adj. R-squared (uncentered):              0.601
Method:                 Least Squares   F-statistic:                              211.5
Date:                Sun, 06 Aug 2023   Prob (F-statistic):                   6.13e-137
Time:                        15:58:22   Log-Likelihood:                         -2282.9
No. Observations:                 700   AIC:                                      4576.
Df Residuals:                     695   BIC:                                      4598.
Df Model:                           5                                                  
Covariance Type:            nonrobust                                                  
================================================================================
                   coef    std err          t      P>|t|      [0.025      0.975]
--------------------------------------------------------------------------------
review_count     0.0080      0.005      1.689      0.092      -0.001       0.017
distance        -0.0028      0.001     -3.030      0.003      -0.005      -0.001
rating           0.4116      0.219      1.879      0.061      -0.019       0.842
price            2.3167      0.861      2.689      0.007       0.625       4.008
count            0.1181      0.065      1.820      0.069      -0.009       0.246
==============================================================================
Omnibus:                      277.902   Durbin-Watson:                   1.825
Prob(Omnibus):                  0.000   Jarque-Bera (JB):             1530.269
Skew:                           1.704   Prob(JB):                         0.00
Kurtosis:                       9.391   Cond. No.                     1.79e+03
==============================================================================
```

We can see from the results that only the distance and the price has a P > |t| values of below 0.05, which means they are the only two variables that are statistically significant. The R-squared value is 0.603, which means that the model explains 60.3% of the variance in the data. And if we look at the coefficients, we can see that the distance has a negative coefficient, which means that the further the POI is from the bike station, the less likely it is to have a free bike. And the price has a positive coefficient, which means that the higher the price of the POI, the more likely it is to have a free bike.
## Challenges 
- Learning how to pull from APIs and convert to dataframes
- How to validate data and remove irrelevant information
- Choosing characteristics to build the model on


## Future Goals
- Spend more time on pulling the right data
- Research more about the data
- Could have spent more time learning how each variable relate to the number of bikes in each station
- Try to clean the data better before starting model building