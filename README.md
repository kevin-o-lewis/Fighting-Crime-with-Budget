# County Spending Versus Violent Crime in California

## Overview
An exploration of the relationship between California County Budgets and Violent Crime Arrests. This project looks at three budget categories: police, mental health services, and substance abuse services to determine if spending more in any single category will correlate with a greater than average reduction in violent crime arrests.

## Data Sources
County Budget data 2003 to 2016: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Years-2002-03-to-2015/esdm-5xr2) \
County Budget data 2017: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Year-2016-17/r97q-afvz) \
County Budget data 2018 to 2019: [CA State Controller Office](https://bythenumbers.sco.ca.gov/Raw-Data/Counties-Raw-Data-for-Fiscal-Years-2017-18-to-2018/5m9j-k3ce) \
DOJ Arrests Records: [CA Dept. of Justice](https://data-openjustice.doj.ca.gov/sites/default/files/dataset/2020-07/OnlineArrestData1980-2019.csv) \
Population Estimates: [CA State Association of Counties](https://www.counties.org/sites/main/files/file-attachments/population_by_jurisdiction_and_by_county_-_1970_to_2018_-_09-07-2018.xlsx)

## Data Description and Cleaning
The California State Contoller's Office reports county-level budget data for all counties except San Francisco, which has its own county controller and data management system. Due to possible differences in data collection and organization, I excluded San Francisco County from my research. I compiled data from three reports, which together spanned from 2003-2018. I then filtered that data down to three budget categories: Total Police Spending, Total Mental Health Spending, and Total Drug and Alcohol Abuse Services Spending (also referred to as "Substance Abuse Spending" throughout this project). Once I eliminated all counties that reported Zero or Null for any category in any year, which left me with 44 counties, 16 years, and 3 budget categories.

The California Department of Justice reports county-level crime data from 1980-2019. The report I used contains 13 features and 97,000 rows related to the types of crimes, the demographics of the people who were arrested, and the year the arrest occurred. I filtered this dataset to include only arrests for violent crimes from 2003-2018. I further filtered it down to the 44 counties I determined as my sample while cleaning the budget data, described above.

Finally, I pulled yearly population estimates for each county from the California Association of Counties. I used these estimates in conjunction with the DOJ Arrests data to find the arrests per capita for each county and year.

## Exploratory Data Analysis
I began exploring my data in its raw form as .csv and .xslx files and used Apache Spark to run SQL queries to gather the specifc features I wanted to explore. Then I converted the query results to Pandas DataFrames to combine features and plot visualizations with Seaborn and Matplotlib. \ 
At this point I decided to combine the violent crime arrests with population to get arrests per capita in order to avoid population variance from skewing my results.

## Detailed Analysis
The first question I wanted to answer was "Which counties prioritize each of my selected budget categories?" \
To answer this, I created a Pandas DataFrame from the county budget data and added columns for the total spending in the three selected categories, and then columns for each category as a proportion of the total. I then grouped the data frame by county and sorted by each spending category to collect the ten counties that spent the highest proportion in each category.
![Screen Shot 2021-06-11 at 12 19 39 PM](https://user-images.githubusercontent.com/83669741/121738625-4f181d00-caaf-11eb-8b6f-82b78a266259.png)

Next I used the Seaborn library to create a scatterplot with trend lines, plotting each group of ten counties that spent the highest proportion in each budget category.
![Screen Shot 2021-06-11 at 1 17 57 PM](https://user-images.githubusercontent.com/83669741/121744230-72df6100-cab7-11eb-9c82-5ad3d73a5cb1.png)

In order to approximate the correlation of each budget prioritization group with arrest rate, I isolated and compared the slopes of the trend lines below.\
![Screen Shot 2021-06-11 at 1 50 35 PM](https://user-images.githubusercontent.com/83669741/121747272-02870e80-cabc-11eb-9a63-5828addae736.png)

By comparing the slopes of the trend lines above, I determined that although my categorized spending groups all showed a decline in violent crime arrests over the observation period, only the group of counties that prioritized mental health spending showed a decline less than the average state-wide decline in violent crime arrests. At this point I formed a hypothesis test to definitively determine if there was a statistically significant difference between each group and the state-wide average.

<b>Null Hypothesis:</b> There is no correlation between budget prioritization and violent crime arrests. \
<b>Alternative Hypothesis:</b> One or more of the selected budget categories will have a significantly different distribution of arrests compared to the statewide average.\
<b>Hypothesis Test:</b> If there is no correlation between spending prioritization and violent crime arrests, I would expect the counties that spent the highest proportion in each category to have the same distribution of arrests as the average of all counties.\


