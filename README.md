# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal of this project was to first. Identity the parameters of pulling API information from 3 datasets, pulling information from MobiBikes Vancouver and then parsing Foursquare and yelp to build a dataframe of restaurants and bars within 1000m of each bike station.
1.) Citibike
2.) Foursquare
3.) Yelp

The second goal was to use that information to build an understanding of the relationship between Restaurant Ratings and various variables that might affect it based on the information available to us. 

## Process
### Step 1: Parsing API data
The first step was to parse all 3 sites to create a dataframe. The first was to parse Citibikes for the Vancouver area to find the location of all mobibike stations across Vancouver. The second was to use that dataframe and the coordinates of each location to parse each of the following two datasets for restaurants and bars witin a 1000m radius. The reason for using the Mobibike locations within the parsing parameters was to limit the amount of data that would need to be parsed for each location. 
### Step 2: Creating Databases
Once all three datasets have been parsed and put into CSV dataframes. The next step was to combine the dataframes all together. Yelp and Foursquare were combined simply based on location names, matching each location to each other. Any duplicates were dropped and the data was cleaned and formatted. 

### Step 3: EDA
General EDA was performed on this dataset to work on ensuring all the data was clean and formatted correctly, this is done only on columns that were intended to be used in the regression model later on. Prices were listed as $ on yelp so they were changed to numerical values for the model and a separate categorical column was created as well. Distance was also calculated using a Haversine formula to calculate the distance between each location and the nearest bike station. 

### Step 4: Model
The model was built using the dependent variable of Review counts to understand the relationship between how many reviews a place received in relation to the other available variables such as ratings, distance, and price. The model was built using a linear regression model to determine the relationship between the dependent variable and the independent variables. The model was run using a backwards regression approach so that the most significant variables were used in the model. The model was then tested using the R^2 value to determine if the model was able to predict the dependent variable accurately. Any variables with high P values were removed from the model and it was rerun until only variables with statisically significant variables were left. 

## Results
The results of the API comparison was that foursquare had much more robust datasets available but struggled to find information for places in the city of my choosing (Vancouver), this might not be the case for all cities. Yelp on the other hand, was more targetted in this data but its information was able to be parsed for the locations and it was able to find information for places in the city of my choosing, allowing the regression model more information to be built upon. 

The model itself showed a strong relationship between Ratings, Review counts and price. These were shown to have a high coefficent and low P-values, signifying that their relationships are not based on chance. However, there is an issue of multicollinearity within them so they will need to be studied further for comparison and perhaps additional variables will need to be added to avoid this. Distance was shown to have a small relationship with review counts but with a P-value of above 0.05, it means that we can not definitely confirm that any positive affect on review counts were not simply due to chance. Size of bike stations was also shown to have a positive relationship with review counts, showing that with an increase in the total number of bikes, it created roughly 6 more reviews for a place.

## Challenges 
Throughout the project, several challenges were encountered:

1. **Data Integration**: Combining datasets from different sources presented difficulties, particularly in aligning the locations from Yelp and Foursquare with the Citibike data accurately.

2. **Data Quality**: Inconsistencies and missing values in the datasets required extensive cleaning and preprocessing to ensure the accuracy of the analysis. API were limited in the information that was provided and made it difficult to create robust datasets Multicollinearity was a challenge as variables were highly correlated with each other. This was not ideal for model building, however due to the limits in available information, these variables were still included in the model. 

3. **API Limitations**: Rate limits and data access restrictions from the APIs occasionally hindered data retrieval, necessitating strategies to manage and optimize API calls.

4. **Model Complexity**: Building the regression model involved iterative testing and validation to handle multicollinearity and ensure statistical significance of the variables.

## Future Goals
The following steps would be taken if more time were available to continue the project:

1. **Incorporating Additional Variables**: Including more variables such as weather data, population density, and time of day could potentially improve the accuracy of the model.

2. **Geographic Expansion**: Expanding the dataset to include more cities or regions could provide a more comprehensive understanding of the relationship between bike stations and the quality of nearby businesses. It would also be interesting to breakdown the dataset by regions within Vancouver to understand how different cities compared to each other.

3. **Data Visualization**: Creating interactive visualizations of the data would allow for a more intuitive understanding of the results and could facilitate the exploration of the data in new ways.

4. **Model Refining**: Refining the model to include non-linear relationships or other advanced techniques could potentially improve its accuracy and ability to predict the dependent variable.

5. **Comparative Analysis**: Performing a comparative analysis of the results across different cities or regions could provide insights into the generalizability of the model and the differences between the various locations.
