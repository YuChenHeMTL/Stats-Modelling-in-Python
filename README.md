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

| Variable      | R-squared value |
| ----------- | ----------- |
| All      | 0.021       |
| Price   | 0.594        |
| Rating   | 0.591        |
| Distance   | 0.368        |
| Review Count   | 0.246        |

## Challenges 
- Learning how to pull from APIs and convert to dataframes
- How to validate data and remove irrelevant information
- Choosing characteristics to build the model on


## Future Goals
- Spend more time on pulling the right data
- Research more about the data
- Could have spent more time learning how each variable relate to the number of bikes in each station
- Try to clean the data better before starting model building