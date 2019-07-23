# NYU-CUSP-Capstone-2019
- This is our capstone projects of NYU CUSP 2019. The topic is: Does Uber/Lyft reduce parking violations in NYC?
- Group member: [Junjie Cai](https://github.com/JunjieTsai), [Junru Lu](https://github.com/LuJunru), [Pranay Anchan](https://github.com/pranay-anchan), [Shijia Gu](https://github.com/sg5718) and [Yuxuan Wang](https://github.com/jasonwang1031)
- Sponsor & Supervisor: [Zhan Guo](https://wagner.nyu.edu/community/faculty/zhan-guo)
- Please refer to our website for more [visualizations](http://uberlyftparkingviolation.github.io/)

# Introduction
- This capstone project aims to explore one potential Uber/Lyft’s impact: whether daily Uber/Lyft trips affect parking violations. NYC daily Uber/Lyft trip and parking ticket data are collected and correlated by taxi cab zone. Three technical models, Fixed Effects, Difference in Difference (DID), and Bayesian Network, are applied on the prepared data. The results of these models show the negative correlation and causal effect between the number of Uber/Lyft trips and parking tickets, suggesting Uber/Lyft help in reducing parking violations in NYC. Given the controversial issues around TNC, this capstone project can assisting in understanding impact of Uber/Lyft and offer policy insight to the TNC regulation.

# Usage
## Step 1: Data Collection
- [Data Collection](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL1_Data_Collection.ipynb): Developed a pipeline to collect all the 42-month FHV and 6-year parking ticket datasets
## Step 2: Data Wrangling
- [Uber & Lyft Data](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL2_FHV_UberLyft.ipynb): Filtered and grouped the Uber/Lyft trips from FHV trips with Spark
- Tickets Data
  - [Street Name](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets1_StreetName.ipynb): Filtered and grouped ticket data with Spark
  - [Geocoding](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets2_Geocoding.ipynb): Converted 350 thousand street names into coordinates through Google Geocoding API.
  - [Taxi Zone](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets3_TaxiZone.ipynb): Mapped the coordinates into taxi zones with R-tree method with Spark
- Additional Data
  - Temporal Datasets

|  | Weather | Holiday | Weekdays | Events (Potential) |
| ------ | ------ | ------ | -- | -- |
| Example | None | None | None | None |

  - Spatial Datasets
#### Taxi Zone Attributes
- 'OBJECTID'/ 'LocationID': Taxi zone ID
- 'Shape_Leng': Taxi zone length
- 'Shape_Area': Taxi zone area
- 'borough': NYC borough number

#### ACS Census
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

#### Crime
- 'FELONY': Number of felony crimes in the taxi zone
- 'VIOLATION': Number of violation crimes in the taxi zone
- 'MISDEMEANOR': Number of misdemeanor crimes in the taxi zone

#### Transportation
- 'subway': Number of subway entrances
- 'bus': Number of bus stops

#### Education
- 'sat': Average score of SAT reading, math, and writing.

#### Parking
- 'meter': Number of merter parking.
- 'parkinglot': Area of parking lot.

#### Potential Datasets
- BBL
- Park
- Parking Regulation Locations and Signs
- Meter parking price
- Garage parking price
- Google POI
- Yelp
## Step 3: Data Integration
- [Data Integration](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL4_Data_Integrating.ipynb):
  - Collected and processed influencing factor datasets, including ACS Census, Crime, Transportation, Education, and Parking data
  - Integrated and output all datasets through spatial/ temporal dimension
## Step 4: Data Analytics
- [Preliminary Analysis](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Preliminary%20Analysis.ipynb):
  - Time series analysis for the whole NYC and every taxi zone
  - Correlation analysis between parking ticket and FHV trips for the whole NYC
  - Correlation analysis for every taxi zone
## Step 5: Modelling
- [OLS](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Modeling1_OLS.ipynb): Multivariate linear regression modeling trial on temporal datasets.
- [Fixed Effect & Bayesian Nework](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Modelling2_FEM_BN.ipynb): Fixed Effect Modelling & Bayesian Nework Modelling
- [Difference in differences](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Modelling3_DID.ipynb): Mimic the design of experimental research, studying the differential effect of Uber/Lyft on NYC's parking violation
