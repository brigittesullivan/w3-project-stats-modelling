# Final-Project-Statistical-Modelling-with-Python

5pm April 14: TESTING GIT


## Project/Goals
(fill in your description and goals here)
Perform regression analysis using the city bikes api data and foursquare/yelp api data. 
"Is there a statistically significant relationship between the count of restaurants within 1KM of Montreal City Bikes Stations and the number of total bikes stalls?" 

## Process

1. Extract Data from City Bikes for Montral using API

2. Extract restaurant data from Foursquare API for the locations of each city bikes station in montreal. 
   - discovered there was a default result liminit in the foursquare API set to 10, affecting the output.
3. Join the foursquare and city bikes data 
4. perform EDA 
   - plot num stalls as x, restaurant count as y
   - restaurant count as x, num stalls as x
   ![scatterplot](/w3-project-stats-modelling/images/scatter-plot-fsq-1.png)
5. perform regression analysis 
   - selected restaurant count as x
   - selected num stalls as y
6. document findings from regression analysis
7. iteration 1: Add yelp data
   - extract yelp data 
   - remove yelp data outlier point of 602, bringin data points down to 8
   - build model using yelp data
8. iteration 2: debug city bikes code
   - found bug in city bikes API call that was causing the # of stations to be returned to be only 8. Was using a a for loop on range(len(data)), however the data variable was set to one level too high and was only returning the first 8 stations as a result. In the end Montreal has several hundred city bikes stations. To keep the data manageable, I extracted the first 50 stations for the analysis. If I had more time/unlimited API calls, I would have left all the data as is. 
   - repeat EDA and regression steps once code debugged. 



## Results
(fill in what you found about the comparative quality of API coverage in your chosen area and the results of your model.)


#### Model Analysis - Foursquare:

* very high p-value of 0.676 indicates there is not a statistically significant relationship between the the number of restaurants to effectively predict the # of stalls available
* a negative adjusted r-square value of -0.017 indicates that this model does not effecitively explain any patterns in the data.  
* Despite finding the original bug causing only 8 data points in previous analysis, It's clear that even with additional data points, there is no clear relationship between the count of restaurants and the number of city bikes stalls (See Scatter plots created in Joining Data). 
![regression x = num stals, y = restaurant count, results](/w3-project-stats-modelling/images/regression-result-fsq.png)

#### Model Analysis - Yelp:

* pvalue of 0.406 indicates there is not a statistically significant relationship between the the number of restaurants to effectively predict the # of stalls available
* a negative adjusted r-squared value of -0.009 indicates that this model explains no patterns  in the data. 
* Despite finding the original bug causing only 8 data points in previous analysis, It's clear that even with additional data points, there is no clear relationship between the count of restaurants and the number of city bikes stalls (See Scatter plots created in Joining Data).

![regression x = num stals, y = restaurant count, results](/w3-project-stats-modelling/images/regression-result-yelp.png)

## Challenges 
(discuss challenges you faced in the project)

* I encoutered many issues looping through HTTP request with latitude and longitude, only managed to figure it out after several conversations with mentors.
* I had a bug in the code that caused only a small number of city bikes stations to be returned. This bug lead to a very weak regression models initally. However it was never mentioned that the regression had to be a 'good' model, so chose to proceed. Didn't realise how this would affect the results. Once the bug was addressed, unfortunately the models did not get significantly better. 
* maintaining a realistic project scope meant that I did not have the time to seek out personally satisfying models. 

## Future Goals
(what would you do if you had more time?)

* run entire project using all 712 city bikes station data rather than only 50. 
* add more variables like restaurant rating, price, popularity to attempt to find a statistically significant correlation
* conduct more regressions with different variables
