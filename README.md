# python-api-challenge
 
This is a two-part project which uses Python to query the OpenWeatherMap GeoApify APIs to find weather conditions in a number of randomly selected cities around the world and select vacation destimations.

In the first part, we select a set of coordinates randomly and find the nearest city to each latitude and logitude pair, discarding duplicate cities. Using OpenWeatherMap API, we retrieve weather data from each of these cities and load it into a pandas DataFrame.

Our weather data includes Maximum Temperature, Humidity, Cloud Coverage, and Wind Speed in each city for the day the data was retrieved.  Using MatPlotLib, we create scatter plots to show the relationship (if any) between each of these weather conditions and the city's latitude.

If we want to calculate the linear regression and draw the regression line on our scatter plot, we need to divide the data into northern and southern hemispheres, since they are currently experiencing different seasons.

The regression_plot() function takes two arguments: y column name (i.e., weather factor) and hemisphere. It then outputs a scatter plot with  regression line, r-value, and line equation.



The second part of the challenge loads the weather data produced in Part 1 into a DataFrame and creates a map that shows a point for each city, with the size of each point corresponding to the humidity in that city.

Next, we search for cities to vacation in that have ideal weather conditions. Because I don't like too-hot or humid weather, I've narrowed the selection to cities with temperatures between 60 and 75 degrees and humidity at 60% or below.

Finally, we query the GeoApify API to find the first hotel within 10,000 meters of each remaining city's latitude & longitude. Not every city returns a result, but we get enough of them to give us a reasonable choice of destinations all over the world!

We update our map to include only the remaining cities in our narrowed down list, adding the hotel name and the country's abbreviation to the hover message for each point on the map.