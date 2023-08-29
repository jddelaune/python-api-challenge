# Getting Out of the USA -- A Python API Project with MatPlotLib Visualizations
## Joanna DeLaune
_"Do you need anything from Duty Free?
I gotta get out of the U.S.A"
 -- Ike Reilly_
 
This is a two-part project which uses Python to query the OpenWeatherMap and GeoApify APIs to (1) find weather conditions in a number of randomly selected cities around the world and (2) select vacation destinations.

Data visualizations have been created using Matplotlib.

## Part 1 - Stormy Weather?
In the [first part](WeatherPy.ipynb), we select a set of coordinates randomly and find the nearest city to each latitude and logitude pair, discarding duplicate cities. Using [OpenWeatherMap API](https://openweathermap.org/api), we retrieve weather data from each of these cities and load it into a pandas DataFrame.

Our weather data includes Maximum Temperature, Humidity, Cloud Coverage, and Wind Speed in each city for the day the data was retrieved.  Using MatPlotLib, we create scatter plots to show the relationship (if any) between each of these weather conditions and the city's latitude.

If we want to calculate the linear regression and draw the regression line on our scatter plot, we need to divide the data into northern and southern hemispheres, since they are currently experiencing different seasons.

The regression_plot() function takes two arguments: y column name (i.e., weather factor) and hemisphere. It then outputs a scatter plot with  regression line, r-value, and line equation.

For example, this graph shows the relationship between Latitude and Max Temperature in the northern hemisphere:

![n_temperature_7-22-2023](https://github.com/joannadelaune/python-api-challenge/assets/102549713/106e04ce-91f4-4c5f-813f-d71d550e6c5a)

It shows clearly what we know, that it gets hotter the nearer one gets to the equator. However, there is no strong relationship between latitude and, for example, wind speed:

![s_wind_7-22-2023](https://github.com/joannadelaune/python-api-challenge/assets/102549713/41b07585-f1f3-4d17-a3d5-25580e44efda)

In fact, temperature was the only factor for which we found a relationship strong enough to be remarked upon.

## Part 2 - A Place to Stay
The [second part](VacationPy.ipynb) of the challenge loads the weather data produced in Part 1 into a DataFrame and creates a map that shows a point for each city, with the size of each point corresponding to the humidity in that city.

Next, we search for cities to vacation in that have ideal weather conditions. Because I don't like too-hot or humid weather, I've narrowed the selection to cities with temperatures between 60 and 75 degrees and humidity at 60% or below.

Finally, we query the [GeoApify Places API](https://www.geoapify.com/places-api) to find the first hotel within 10,000 meters of each remaining city's latitude & longitude. Not every city returns a result, but we get enough of them to give us a reasonable choice of destinations all over the world!

![image](https://github.com/joannadelaune/python-api-challenge/assets/102549713/3e9d07b8-054b-4742-bdf0-4b26c126184c)

We update our map to include only the remaining cities in our narrowed down list, adding the hotel name and the country's abbreviation to the hover message for each point on the map.

![image](https://github.com/joannadelaune/python-api-challenge/assets/102549713/85627bb2-921a-48b5-b7be-77fcd3bb16f5)

