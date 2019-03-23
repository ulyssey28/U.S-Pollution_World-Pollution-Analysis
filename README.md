# Air Pollution Analysis (U.S/ World Pollution)

## Background and Focus of this Study

Air pollution is the emission of harmful substances, pollutants, to the atmosphere.

Toxic air pollutants of concern :
* Sulphur dioxide (SO2): Forms in the air  by the burning of fossil fuels by power plants and other industrial facilities
* Nitrogen dioxide (NO2): Forms from vehicle emission and power plants. Can aggravate respiratory diseases 
* Ozone (O3): Harmful to lungs and is the main constituents of smog/haze
* Carbon monoxide (CO): Emitted by vehicles that burn fossil fuels
* Particulate matter (PM2.5) (small suspended particles of varying sizes): Tiny bits of dust, dirt, smoke that hang in the air. Can penetrate into the lungs and cause breathing problems

AQI (Air  Quality Index)
* A measure of how clean or polluted the air is in a given time and location
* Identifies any health risks to individuals 

## Approach 
### Overall Question:
What are some of the major influences on Air pollution and what are some of the effects of air pollution? 

### Analysis Questions:
1. What are the most polluted countries in the world?
 * What are some factors that could influence a region's concentration of pollutant AQI levels
(Example: Populations, GDP, Fuel emmisions...)

With some of these potential influences in mind we then transitioned into a focus on the U.S

2. What is the trends of major air pollutants in the United States over time?

3. How is US GDP trending over time in comaprison to the trend of major air pollutants?

4. How do pollutant levels affect health? 
(What are the effects of high pollutant levels on the following?)
 * Mortality Rates
 * Asthma

## Sources and Datasets
* Open Data Soft World Pollution dataset:
https://public.opendatasoft.com/explore/dataset/worldwide-pollution/table/?disjunctive.country&disjunctive.filename

* Kaggle US Pollution dataset:
https://www.kaggle.com/sogun3/uspollution

* Socrata Sandbox Asthma dataset:
https://bah.demo.socrata.com/Government/DATASET-Asthma-Chronic-Disease-Indicators/neii-ukbv

* Center for Disease Control: 
https://www.cdc.gov/asthma/most_recent_data.htm

* Bureau of Economic Analysis GDP and Personal Income (Regional Data):  
https://apps.bea.gov/iTable/index_regional.cfm

* Environment Protective Agency: 
https://www.epa.gov/

* GMaps Module Documentaion:
https://jupyter-gmaps.readthedocs.io/en/latest/tutorial.html#heatmaps

## World Pollution Heatmap

“A heatmap is a visualization used to depict the intensity of data at geographical points. When the Heatmap Layer is enabled, a colored overlay will appear on top of the map. By default, areas of higher intensity will be colored red, and areas of lower intensity will appear green.” - Google Maps API

I created heatmaps for each pollutant to show aqi levels within different regions throughout the world based on our World pollution API data.

The heatmap produces a neat visual that allows us to potentially make inferences on factors in regions around the world that cause them to have an overall higher concentration of pollutants 

To create these heatmap I use three things.
* Longitudes
* Latitudes
* Pollutant values
(Obtained from the Open Data Soft World Pollution dataset API)

### Open Data Soft World Pollution dataset API
This API is available through the opendatasoft website. As usual to access the json with the data we needed a url. This website was very helpful in that it provided you a way to instantly create the query url based on different parameters

After reading the API documentation and playing around with the url creator, I was able to create a country data search url.

The main logic behind the query code was:
* Create a list of some of the available countries within the data set
* Then create a for loop that would act upon the country list
* Within the for loop I would format a url string based on a country in the country list to obtain data for that specific country when requesting from the API
* Next create a dictionary of relevant data and appended the data to a list of dictionaries which we later used to create a pandas dataframe.
This dataframe would contains data for a specific country, city in the country, longitude and latitude for the site and aqi values for different pollutants at the site.

## Heatmap
To create the heatmap I utilized the python gmaps module

### Steps:

1. Created a gmaps figure

2. Then created a heatmap layer using a gmaps function (that take in latitude and longitude values) and weighted the layer using aqi values

## What is the air pollution trend in the us over time?
To answer that question we turned to us pollution dataset on kaggle
Within this dataset we had relevant air pollution data for various states from 2000 - 2016
To begin our analysis:
We first read the us pollution data csv from kaggle
Note some of the columns provided in the data set
We then created a year column based on the “Date Local” column string and dropped any rows with null values 
We then selected relevant columns and tried different groupby’s to spot trends.
Ultimately we created a dataframe of mean aqi values grouped by year which we use to produce the trend graphs 
Graphed year versus mean aqi value and noticed a clear downward trend meaning that aqi values were going down over time 
Based on this downward trend we decided to see if mortality counts from some air pollution related illness were also going down potentially suggesting a correlation. 








