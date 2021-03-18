## IRONHACK FINAL PROJECT: Predicting wildfires in California, two step approach

**What is the project all about?** The danger of wildfires on the West Coast, especially in California is increasing. Facing the multiple dimensions of climate change, one may ask: Is fire season now a year-round reality? To answer this question, I decided to work on a model predicting the amount and size of wildfires in California in a two step approach.

Please find the description of each Jupyter Notebook below:

#### (1) DATA MINING | NOAA API Scrapping data.ipynb: Scrapping weather data from NOAA API

- Setting up NOAA API for scrapping weather data of California, United States of America.
- Scrapping data from NOAA API was done from 1975 (for wind speed and evaporation starting 1985) to 2020.
- Please find documentation for NOAA API here: https://www.ncdc.noaa.gov/cdo-web/webservices/v2. Data is returned as json-format. The request for a chosen climate data per time period is automated and stored as pd.DataFrame for further use by each available weather station (4427 unique station IDs).  

*To use the NOAA API you have to register to get an own token. 

#### (2.1) DATA PROCESSING | UBER H3 for weather station & fires.ipynb: Mapping weather stations & wildfires with hexagons 

- The H3 libary is used for indexing locations in California. Please find documentation for H3: Uber’s Hexagonal Hierarchical Spatial Index here: https://eng.uber.com/h3/. 

- Weather stations are clustered per hexagon. For this model the resolution level 4 is chosen. Please find the created interactive map for available weather stations here: https://github.com/caaarov/finalproject_wildfires_CA/blob/master/files/map_weather%20stations%20CA.html

- Recorded wildfires between 1992-2015 in California are clustered per hexagon. For this model the resolution level 4 and level 5 are chosen. Please find the created interactive map on level 5 for wildfires here: https://github.com/caaarov/finalproject_wildfires_CA/blob/master/files/map_wildfires_level%205_CA.html

#### (2.2) DATA PROCESSING | Time Series Analysis with PROPHET.ipynb: Time Series Analysis with PROPHET is documented for the climate data of Temperature | Precipitation | Wind Speed | Evaporation. 

- The Time Series Analysis with PROPHET was done for the next five years (2021 - 2026).
- Please find the documentation for PROPHET here: https://facebook.github.io/prophet/docs/quick_start.html#python-api. The forecast for 2021-2026 is automated and stored as pd.DataFrame for further use. 

#### (3.1) MODELING STEP 1 | Probability of wildfires.ipynb: In this jupyter notebook the deployment of STEP 1 for the model of wildfires prediction is documented.

- Data Exploration: Between 1992 – 2015 more than 1.8 million wild fires were recorded. Find e.g. details about fire size and cause in section 1. 
- Feature Engineering: Urban areas are included, climate data of the last quarter & year is computed.
- Balancing of Data: Manual balancing between fire size classes to reduce the false negative predictions of the model (increasing the recall score).
- Automated Feature Selection: Tuning down the number of features, weather variables were identified as main features.
- Grid Search for AdaBoostClassifier: Tuning the hyper-parameters of AdaBoostClassifier.

The accuracy of the model in the TEST set is:  0.97

The kappa of the model in the TEST set is:  0.894

For 2020, the model predicts a record number of fires for the San Francisco area. By the end of 2020, 9,639 fires had burned 4,397,809 acres – more than 4% of California's acres of land. For 2020, the model predicts a record number of fires for the area around San Francisco.

#### (3.2) MODELING STEP 1 | Predicting wildfire size.ipynb: In this jupyter notebook the deployment of STEP 2 for the model of wildfires prediction is documented. 

** **IN PROGRESS** **

- Number of fires between 4 – 20 km2 is increasing in California. 
- Automated Feature Selection: Tuning down the number of features.
- For the prediciton of the wildfire size the imbalance of the size of recorded wildfires is challenging. 

718101 A (- 0.25 acres)

606186 B (0.26 - 9.9 acres) 

64670  C (10 - 99.9 acres)   

13231  D (100 - 299 acres)   

6465   E (300 - 999 acres)  

4400   F (1000 - 4999 acres)

2696   G (5000 acres)


- Model is still under evaluation and not sophisticated enough for a reliable prediction of fire size.

#### (4.1) STORY TELLING | Data base SAN FRANCICSO.ipynb 

In this Jupyter Notebook the data generation for the final project presentation is documented.

#### (4.2) STORY TELLING | Use Case SAN FRANCISCO.ipynb

In this Jupyter Notebook the data generation for the final project presentation is documented. 

Predicted wildfires between 2016-2020 for ring 2 nearst neighbours of hexagon of San Francisco are summed. For this model the resolution level 4 is chosen. Please find the created interactive map on level 4 for wildfires in the Bay Area here: https://github.com/caaarov/finalproject_wildfires_CA/blob/master/files/map_2021-predictions_San%20Francisco%20Area%20.html

Find the PDF of my presentation on GitHub: https://github.com/caaarov/finalproject_wildfires_CA/blob/master/Wildfires%20in%20California%20-%20A%20Machine%20Learning%20Model.pdf.

####  IDEAS FOR EXTENDING THE MODEL:
- Setting up a live connection to NOAA API to keep the model with live climate & weather data up to date.
- Adding more feature with information about the ecosystem and biodiversity of the hexagons. 
- Labeling hexagons with high percentage of land covered by forest areas.
- Using level 5 or 6 for H3 indexing for higher granularity.
- Using NN to find "hidden features" (like regulations of the state in specific time periods to lower the wildfire risk).

...
