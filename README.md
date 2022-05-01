# World_Weather_Analysis
## Purpose
Creating a rudimentary vacation itinerary filtered by user preference with randomly generated cities.
## Results
#### Part 1: Retreiving City and Weather Data
A successful app would need a large and random set of cities. To do this, I generated a sufficiently large number of random coordinates (in this case, 2000, but the number could be higher or lower) and found the nearest city to each coordinate, making sure to ignore duplicates. This created a list of 700-800 cities[^1].
Next step is getting the weather for each city. This code takes a long time to run since it is rate-limited by the API request. This then gets exported to a csv.
#### Part 2: Filtering Cities via User Request and Gathering Hotel Data
What good is it to suggest cities the user has no interest in going? In this case, the list is filtered by temperature, but it can be easily refactored to include all of the different metrics of weather. Now we can gather hotel data for each of the preferred destinations[^2] and visualize the different cities via the gmaps module:

![map](/Vacation_Search/WeatherPy_vacation_map.PNG)

Each marker also includes a snippet of the weather in the city. 
#### Part 3: Creating a Travel Itinerary Map
Now comes the fun part: creating a travel plan for the client! This was done manually by choosing four cities in close proximity:

![cities](/Vacation_Itinerary/WeatherPy_travel_map_markers.PNG)

And then creating a travel path with a directions layer on the map.

![route](/Vacation_Itinerary/WeatherPy_travel_map.PNG)

With cities and hotels picked out, all that's left to do is hop on a plane!
## Improvements
The code is slow, particularly during the API requests. This would be sped up with paid APIs or by not gathering new cities every time the code was ran. Since certain cities are overrepresented, a better generation of random coordinates would be a benefit, though difficult to implement. Also adding more filtering criteria would help narrow down the cities. Finally, getting more hotel info, like price or rating, as well as airport information would be a huge bonus to this fairly basic application

[^1]: If the goal was to look at more cities, the number of coordinates generated would need to increase more than you would expect. Because the Earth has many places      with no cities (see: ocean), duplicates will pop up more frequently. Cities on the coast and cities in extreme northern or southern latitude will be overrepresented,    since the Earth is a sphere and has a smaller radius at those latitudes.
[^2]: I added a print statement for the hotel API request because when I first ran it it took nearly a minute for each pull, and I needed to double check that it was        running. This is entirely unnecessary.
