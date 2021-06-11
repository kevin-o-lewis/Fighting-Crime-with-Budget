# County Spending Versus Violent Crime in California

## Overview
An exploration of the relationship between California County Budgets and Violent Crime Arrests. This project looks at three budget categories: police, mental health services, and substance abuse services to determine if spending more in any single category will correlate with a reduction in violent crime arrests.

## Data Sources
County Budget data 2003 to 2016: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Years-2002-03-to-2015/esdm-5xr2) \
County Budget data 2017: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Year-2016-17/r97q-afvz) \
County Budget data 2018 to 2019: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Years-2017-18-to-2018/5m9j-k3ce) \
DOJ Arrests Records: [CA Dept. of Justice](https://data-openjustice.doj.ca.gov/sites/default/files/dataset/2020-07/OnlineArrestData1980-2019.csv) \
Population Estimates: [CA State Association of Counties](https://www.counties.org/sites/main/files/file-attachments/population_by_jurisdiction_and_by_county_-_1970_to_2018_-_09-07-2018.xlsx)

## Data Description
The California State Contoller's Office reports county-level budget data for all counties except San Francisco, which has its own county controller and data management system. Due to possible differences in data collection and organization, I excluded San Francisco County from my research. I compiled data from three reports, which together spanned from 2003-2018. I then filtered that data down to three budget categories: Total Police Spending, Total Mental Health Spending, and Total Drug and Alcohol Abuse Services Spending (also referred to as "Substance Abuse Spending" throughout this project). Once I eliminated all counties that reported Zero or Null for any category in any year, I was left with 44 counties, 16 years, and 3 budget categories.

The California Department of Justice reports county-level crime data from 1980-2019. The report I used contains 13 features and 97,000 rows related to the types of crimes, the demographics of the people who were arrested, and the year the arrest occurred. I filtered this dataset to include only arrests for violent crimes from 2003-2018. I further filtered it down to the 44 counties I determined as my sample while cleaning the budget data.
