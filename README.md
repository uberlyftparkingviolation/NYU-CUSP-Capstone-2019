# NYU-CUSP-Capstone-2019

# Notebooks
[ETL1_data collection.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL1_data%20collection.ipynb): Developed a pipeline to collect all the 42-month FHV and 6-year parking ticket datasets.
[ETL2_fhv_UberLyft.ipynb](https://github.com/uberlyftparkingviolation/NYU-CUSP-Capstone-2019/blob/master/ETL2_fhv_UberLyft.ipynb)	Filtered and grouped the Uber/Lyft trips from FHV trips with Spark for parallel computation.
•	Filtered and grouped ticket data.
•	Converted 350 thousand street names into coordinates through Google Geocoding API.
•	Map the coordinates into taxi zones with R-tree method.

•	Time series analysis for the whole NYC and every taxi zone
•	Correlation analysis between parking ticket and FHV trips for the whole NYC.
•	Correlation analysis for every taxi zone.

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
