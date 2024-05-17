# COVID-19-Data-Analysis-
## Project Overview:
This project aims to analyze COVID-19 data to gain insights into the pandemic's impact globally. By leveraging data transformation techniques and visual analytics, we can better understand trends and make informed decisions. The project involves collecting data, transforming it using Power Query, calculating important metrics, and visualizing the results in Power BI. The project comprises the following steps:
* Data collection from a reliable source.
* Data transformation to clean and prepare the data.
* Calculation of key metrics such as death and recovery rates, and classification of zones based on the number of cases.
* Visualization of the data using Power BI to create an interactive dashboard.
### Data Collection:
The COVID-19 data was collected from the Worldometers website:
[Worldometers COVID-19 Data](https://www.worldometers.info/coronavirus/#google_vignette).
#### Data Transformation:
Data transformation was performed using Power Query. The following steps were taken:
* All null values were identified and removed to ensure data quality and accuracy. This step is crucial to avoid errors in calculations and visualizations.
* Columns that were not relevant to the analysis were removed. This step helps in simplifying the dataset and focusing on the most critical information.
* Two new measures in the table were added: Death rate and recovery rate.This was done by using the following formulas:
  '''dax
  Death Rate = DIVIDE(SUM('Table 1'[TotalDeaths]),SUM('Table 1'[TotalCases]))
  Recovery Rate = DIVIDE(SUM('Table 1'[TotalRecovered]),SUM('Table 1'[TotalCases]))
  ```
* Classifying Zones:
  Union Health Ministry revised a list of districts under red, orange and green zones. If a particular district has over 15 cases, then it will be considered a hotspot, and be classified as a red zone. For districts whose COVID-19 cases are below 15 and don’t seem to be increasing at present, they will be labelled orange zones. Green zones will be the districts with zero COVID-19 cases.
  So a new column was added in the dataset by using the follwing formula:
  ```dax
  zone = IF('Table 1'[Serious,Critical]>15,"Red Zone",IF('Table 1'[Serious,Critical]>0,"Orange zone","Green zone"))
  ```
##### Data Visualization:
The transformed data was visualized using Power BI. Key charts displayed total deaths, total cases, and active cases by continent, providing a comparative view of the pandemic's impact across different regions. A map was added that displayed red, orange, green zones. Various cards that displayed Death Rate, Recovery Rate, total deaths, total cases, and active cases that can be filtered by continents.

###### Power BI Dashboard:
An interactive dashboard was created in Power BI to allow users to explore the data and gain insights. Key features of the dashboard include:
* A global overview of COVID-19 cases.
* Detailed statistics for specific regions.
* Filters to view data by region, and zone classification.
* Visual representation of death and recovery rates.

  
