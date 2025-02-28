# NYU-CUSP-Capstone-2019
- This is our capstone projects of NYU CUSP 2019. The topic is: Does Uber/Lyft reduce parking violations in NYC?
- Group member: [Junjie Cai](https://github.com/JunjieTsai), [Junru Lu](https://github.com/LuJunru), [Pranay Anchan](https://github.com/pranay-anchan), [Shijia Gu](https://github.com/sg5718) and [Yuxuan Wang](https://github.com/jasonwang1031)
- Sponsor & Supervisor: [Zhan Guo](https://wagner.nyu.edu/community/faculty/zhan-guo)
- Please refer to our website for more [visualizations](http://uberlyftparkingviolation.github.io/)

# Introduction
- This capstone project aims to explore one potential Uber/Lyft’s impact: whether daily Uber/Lyft trips affect parking violations. NYC daily Uber/Lyft trip and parking ticket data are collected and correlated by taxi cab zone. Three technical models, Fixed Effects, Difference in Difference, and Bayesian Network, are applied on the prepared data. The results of these models show the negative correlation and causal effect between the number of Uber/Lyft trips and parking tickets, suggesting Uber/Lyft help in reducing parking violations in NYC. Given the controversial issues around TNC, this capstone project can assisting in understanding impact of Uber/Lyft and offer policy insight to the TNC regulation. ([Full report](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Capstone_Final_Report.pdf), [PPT](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/Capstone_Final_PPT.pptx))

# Usage
## Step 1: Data Collection
- [Data Collection](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL1_Data_Collection.ipynb): Developed a pipeline to collect all the 42-month FHV and 6-year parking ticket datasets
- Note: all data is open on the Internet. For every data, we've provided either the link or the intermediated form transformed by us. Also, feel free to change data pathes when re-using these codes, as the data may be called differently in our notebooks
## Step 2: Data Preprocessing
- Basic Geo-unit of all data: taxi zone

| OBJECTID / LocationID | Shape_Leng | Shape_Area | borough |
| ------ | ------ | ------ | ------ |
| Taxi zone ID | Taxi zone length | Taxi zone area | NYC borough number |

- [Uber & Lyft Data](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL2_FHV_UberLyft.ipynb): Filtered and grouped the Uber/Lyft trips by taxi zones from FHV trips with Spark.
- Tickets Data
  - [Street Name](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets1_StreetName.ipynb): Filtered and grouped ticket data with Spark
  - [Geocoding](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets2_Geocoding.ipynb): Converted 350 thousand street names into coordinates through Google Geocoding API
  - [Taxi Zone](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL3_Tickets3_TaxiZone.ipynb): Mapped the coordinates into taxi zones with R-tree method with Spark.

- Additional Data

| Temporal Data | Spatial Data | Potential Data |
| ------- | ------ | ------ |
| Weather, Holiday and Weekdays | **ACS, Crime, Transportation, Education and Parking Facilities** | Events, BBL, Park, Parking Regulation Locations and Signs, Meter parking price, Garage parking price, Google POI and Yelp |

**ACS** details

| DensityPop | IncomePerCap | Poverty | Professional | Service | Office |
| ---------- | ------------ | ------- | ------------ | ------- | ------ |
| Population Density | Income per capita ($) | % under poverty level rate | % employed in management, business, science, and arts | % employed in service jobs | % employed in sales and office jobs |

| Production | Employed | Unemployment | Drive | Carpool | Transit | Walk |
| ---------- | -------- | ------------ | ----- | ------- | ------- | ---- |
| % employed in production, transportation, and material movement | % employed rate (16+) | % Unemployment rate | % commuting alone in a car, van, or truck | % carpooling in a car, van, or truck | % commuting on public transportation | % walking to work |

| OtherTransp | WorkAtHome | MeanCommuteMean | Construction |
| ----------- | ---------- | --------------- | ------------ |
| % commuting via other means | % working at home | commute time (minutes) | % employed in natural resources, construction, and maintenance |

**Crime** details

| FELONY | VIOLATION | MISDEMEANOR |
| ------- | ------ | ------ |
| Number of felony crimes in the taxi zone | Number of violation crimes in the taxi zone | Number of misdemeanor crimes in the taxi zone |

**Transportation, Parking Facilities and Education** details

| subway | bus | meter | parkinglot | sat |
| ------- | ------ | ------ | ------ | ------ |
| Number of subway entrances | Number of bus stops | Number of merter parking | Area of parking lot| Average score of SAT reading, math, and writing |

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
