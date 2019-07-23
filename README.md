# NYU-CUSP-Capstone-2019
- This is one of the capstone projects of NYU CUSP 2019. Our topic is: Does Uber/Lyft reduce parking violations in NYC?
- Group member: [Junjie Cai](https://github.com/JunjieTsai), [Junru Lu](https://github.com/LuJunru), [Pranay Anchan](https://github.com/pranay-anchan), [Shijia Gu](https://github.com/sg5718) and [Yuxuan Wang](jasonwang1031@gmail.com)
- Please refer to our website for more [visualizations](http://uberlyftparkingviolation.github.io/)

# Problem Definition
- The fast expansion of Uber and Lyft result in people suspecting these companies' effect on our urban system, for example, on public transportation and city congestion. However, due to the lack of open data and scientific research, most of its influence has not been proven yet.
- This capstone project aims to explore one potential Uber/Lyft’s impact: whether daily Uber/Lyft trips affect parking violations. NYC daily Uber/Lyft trip and parking ticket data are collected and correlated by taxi cab zone. Three technical models, Fixed Effects, Difference in Difference (DID), and Bayesian Network, are applied on the prepared data. The results of these models show the negative correlation and causal effect between the number of Uber/Lyft trips and parking tickets, suggesting Uber/Lyft help in reducing parking violations in NYC. Given the controversial issues around TNC, this capstone project can assisting in understanding impact of Uber/Lyft and offer policy insight to the TNC regulation.

# Notebooks
- [ETL1_data collection.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL1_data%20collection.ipynb): Developed a pipeline to collect all the 42-month FHV and 6-year parking ticket datasets.
- [ETL2_fhv_UberLyft.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL2_fhv_UberLyft.ipynb): Filtered and grouped the Uber/Lyft trips from FHV trips with Spark for parallel computation.
- [ETL3_tickets1_street name.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_tickets1_street%20name.ipynb): Filtered and grouped ticket data with Spark.
- [ETL3_tickets2_geocoding.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_tickets2_geocoding.ipynb): Converted 350 thousand street names into coordinates through Google Geocoding API.
- [ETL3_tickets3_taxi zone.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_tickets3_taxi%20zone.ipynb): Mapped the coordinates into taxi zones with R-tree method with Spark.
- [ETL4 data integrating.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL4%20data%20integrating.ipynb):
  - Collected and processed influencing factor datasets, including ACS Census, Crime, Transportation, Education, and Parking data;
  - Integrated and output all datasets through spatial/ temporal dimension.
- [Preliminary Analysis.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Preliminary%20Analysis.ipynb):
  - Time series analysis for the whole NYC and every taxi zone;
  - Correlation analysis between parking ticket and FHV trips for the whole NYC;
  -  Correlation analysis for every taxi zone.
- [Modeling1_OLS.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Modeling1_OLS.ipynb): Multivariate linear regression modeling trial on temporal datasets.
- [Modeling2_Fixed Effect Model & Bayesian Nework.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Modeling2_Fixed%20Effect%20Model%20%26%20Bayesian%20Nework.ipynb): Fixed Effect Modeling & Bayesian Nework Modeling

# Datasets
## Temporal Datasets
- Weather
- Holiday
- Weekdays
- Events (Potential)

## Spatial Datasets
### Taxi Zone Attributes
- 'OBJECTID'/ 'LocationID': Taxi zone ID
- 'Shape_Leng': Taxi zone length
- 'Shape_Area': Taxi zone area
- 'borough': NYC borough number

### ACS Census
- 'DensityPop': Population Density
- 'IncomePerCap': Income per capita ($)
- 'Poverty': % under poverty level rate
- 'Professional': % employed in management, business, science, and arts
- 'Service': % employed in service jobs
- 'Office': % employed in sales and office jobs
- 'Construction': % employed in natural resources, construction, and maintenance
- 'Production': % employed in production, transportation, and material movement
- 'Employed': % employed rate (16+)
- 'Unemployment': % Unemployment rate

- 'Drive': % commuting alone in a car, van, or truck
- 'Carpool': % carpooling in a car, van, or truck
- 'Transit': % commuting on public transportation
- 'Walk': % walking to work
- 'OtherTransp': % commuting via other means
- 'WorkAtHome': % working at home
- 'MeanCommuteMean': commute time (minutes)

### Crime
- 'FELONY': Number of felony crimes in the taxi zone
- 'VIOLATION': Number of violation crimes in the taxi zone
- 'MISDEMEANOR': Number of misdemeanor crimes in the taxi zone

### Transportation
- 'subway': Number of subway entrances
- 'bus': Number of bus stops

### Education
- 'sat': Average score of SAT reading, math, and writing.

### Parking
- 'meter': Number of merter parking.
- 'parkinglot': Area of parking lot.

### Potential Datasets
- BBL
- Park
- Parking Regulation Locations and Signs
- Meter parking price
- Garage parking price
- Google POI
- Yelp
