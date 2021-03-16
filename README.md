# IRONHACK FINAL PROJECT: Predicting wildfires in California in a two step approach

The danger for wildfires in California is increasing. Is fire season now a year-round reality?

### (1) DATA MINING | NOAA API Scrapping data.ipynb: Scrapping weather data from NOAA API

- seting up & scrapping data from NOAA API for California, United States of America. Please find documentation for NOAA API here: https://www.ncdc.noaa.gov/cdo-web/webservices/v2. Data is returned as json-format. The request for a chosen climate data per time period is automated and stored as pd.DataFrame for further use by each available weather station (4427 unique station IDs).  

*To use the NOAA API you have to register and need an own token. 

### (2.1) DATA PROCESSING | UBER H3 for weather station & fires.ipynb: Mapping weather stations & wildfires with hexagons 

-  The H3 libary is used for indexing locations. Please find documentation for H3: Uber’s Hexagonal Hierarchical Spatial Index here: https://eng.uber.com/h3/. 

- Weather stations are clustered per hexagon. For this model the resolution level 4 is chosen. Please find the created interactive map for available weather stations here: 

- Recorded wildfires between 1992-2015 in California are clustered per hexagon. For this model the resolution level 4 and level 5 are chosen. Please find the created interactive map on level 5 for wildfires here: 

### (2.2) DATA PROCESSING | Time Series Analysis with PROPHET.ipynb: Time Series Analysis with PROPHET is documented for the climate data of Temperature | Precipitation | Wind Speed | Evaporation. 

- Please find the documentation for PROPHET here: https://facebook.github.io/prophet/docs/quick_start.html#python-api. The forecast for 2021-2026 is automated and stored as pd.DataFrame for further use. 

### (3.1) MODELLING STEP 1 | Probability of wildfires.ipynb: In this jupyter notebook the deployment of STEP 1 for the model of wildfires prediction is documented.

- Data Exploration: Between 1992 – 2015 more then 1.8 million wild fires were recorded.
- Feature Engineering: Including urban areas, computing climate data of quarter & years
- Balancing of Data: Manual balancing between fire size classes
- Automated Feature Selection: Tuning down the number of features, weather variables identified as main features
- Grid Search for AdaBoostClassifier: Tuning the hyper-parameters of AdaBoostClassifier.

The accuracy of the model in the TEST set is:  0.97
The kappa of the model in the TEST set is:  0.894

For 2020, the model predicts a record number of fires for the San Francisco area. By the end of 2020, 9,639 fires had burned 4,397,809 acres – more than 4% of California's acres of land.

### (3.2) MODELLING STEP 1 | Predicting wildfire size.ipynb: In this jupyter notebook the deployment of STEP 2 for the model of wildfires prediction is documented. 

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

### (4.1) STORY TELLING | Data base SAN FRANCICSO.ipynb 

In this Jupyter Notebook the data generation for the final project presentation is documented.

### (4.2) STORY TELLING | Use Case SAN FRANCISCO.ipynb

In this Jupyter Notebook the data generation for the final project presentation is documented. 

Predicted wildfires between 2016-2020 for ring 2 nearst neighbours of hexagon of San Francisco are summed. For this model the resolution level 4 chosen. Please find the created interactive map on level 4 for wildfires in the Bay Area here: 

Find the PDF of my presentation on GitHub: https://github.com/caaarov/finalproject_wildfires_CA.

###  IDEAS FOR EXTENDING THE MODEL:
- Setting up a live API to keep the model with live climate & weather data up to date.
- Adding more feature with information about the ecosystem and biodiversity of the hexagons. 
- Labeling hexagons with high percentage of land covered by (diferent kind of forest).
- Using NN to find "hidden features" (like regulations of the state in specific time periods to lower the wildfire risk).
...
