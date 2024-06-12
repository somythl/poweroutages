# Zoning Analysis and Predictive Modeling of Customers Affected in a Power Outage

### Created by Samuel Mahjouri and Zoya Hasan

# Introduction

Power outages pose significant risks to the safety, economy, and daily life of U.S. citizens, making it imperative to understand the factors that influence their duration and impact. Our  analysis utilizes a dataset on major power outage events in the continental U.S. from January 2000 to July 2016, provided by Mukherjee, Nateghi, and Hastak from Purdue University. The dataset includes information on geographical location, regional climatic conditions, land-use characteristics, regional electricity consumption patterns, and economic attributes of power outages in various states. Given such a holistic understanding of power outages, we posed the question that could support energy companies when considering where to aid during power outages. Our key question is: What are the key factors that influence the durations of major power outages in the continental U.S., and how can these insights be used to mitigate future outages? This question holds practical implications for utility companies, as well as regional communities. By identifying the determinants of outage durations, energy companies  can better prepare for and respond to future incidents. Given the increasing number and high severity of weather-related disruptions, understanding these dynamics, in correlation to power outages, is more critical than ever. The dataset used in this project has 1534 rows and 56 columns, and offers comprehensive insight to uncover our questions through data analysis. The dataset encompasses information on every major power outage in the United States from 2000 to 2016. Only a handful of columns were used for analysis and prediction, as described below:

Authors: **Samuel Mahjouri and Zoya Hasan**

***

| Feature        | Description     |
|:-------------|:------------------|
| `YEAR`       | The year when the outage occurred| 
| `MONTH` | The month when the outage occurred |
| `U.S._STATE` | State the outage occured in| 
| `OUTAGE.START.DATE`| Day of the year when the outage started |
| `'OUTAGE.START.TIME'`| Time of the day when the outage started |
| `RESTORATION.START.DATE`| Day of the year when energy was restored for outage|
| `'RESTORATION.START.TIME'`| Time of the day when energy was restored for outage|
| `CLMATE.CATEGORY`| Climate episode during outage (Warm/Normal/Cold) |
| `OUTAGE.DURATION`| Duration of outage (minutes) |
| `POPULATION`| Duration of outage (minutes) |
| `DEMAND.LOSS.MW`|  Amount of peak demand lost during an outage event (Megawatt) |
| `CUSTOMERS.AFFECTED`| Number of customers affected by a power outage event |
| `RES.SALES`| Electricity consumption in the residential sector (megawatt-hour)|
| `COM.SALES`| Electricity consumption in the commercial sector (megawatt-hour)|
| `IND.SALES`| Electricity consumption in the industrial sector (megawatt-hour)|
| `TOTAL.SALES`| Total electricity consumption in the U.S. state (megawatt-hour)|
| `UTIL.CONTRI`| % of Utility industry׳s contribution to the total GSP in the State|
| `NERC.REGION`| North American Electric Reliability Corporation (NERC) regions involved in the outage event|
| `CAUSE.CATEGORY`| Event causing the power outage|
# Data Cleaning and Exploratory Data Analysis 
## Here we outline the steps taken to clean our dataset so it is effective for analysis 
1. We  start by dropping missing rows and correctly labeled column titles with their corresponding features.We are only keeping the columns  that we are  working with for analysis. `YEAR`, `MONTH`, `U.S._STATE`, `CLIMATE.REGION`, `CLIMATE.CATEGORY`, `OUTAGE.START`, `OUTAGE.RESTORATION`, `CAUSE.CATEGORY`, `OUTAGE.DURATION`, `DEMAND.LOSS.MW`, `CUSTOMERS.AFFECTED`, `RES.SALES`, `COM.SALES`, `IND.SALES`, `TOTAL.SALES`, `POPULATION`]]
2. Then, we combined the `OUTAGE.START.DATE` and `OUTAGE.START.TIME` columns into a singular `OUTAGE.START` column that utilizes the Timestamp object. We followed the same for `OUTAGE.RESTORATION.DATE` and `OUTAGE.RESTORATION.TIME`, to get the comprehensive ending time for the outage (when the outage was restored). we then dropped the old columns since all the relevant timing was captured in `OUTAGE.STARTv and `OUTAGE.RESTORATION`
3. Next, we filled in missing values from the columns with NAN
Here is the first few rows of our cleaned dataframe. 

|    |   YEAR |   MONTH | U.S._STATE   | CLIMATE.REGION     | CLIMATE.CATEGORY   | OUTAGE.START        | OUTAGE.RESTORATION   | CAUSE.CATEGORY     |   OUTAGE.DURATION |   DEMAND.LOSS.MW |   CUSTOMERS.AFFECTED |   RES.SALES |   COM.SALES |   IND.SALES |   TOTAL.SALES |   POPULATION |
|---:|-------:|--------:|:-------------|:-------------------|:-------------------|:--------------------|:---------------------|:-------------------|------------------:|-----------------:|---------------------:|------------:|------------:|------------:|--------------:|-------------:|
|  0 |   2011 |       7 | Minnesota    | East North Central | normal             | 2011-07-01 17:00:00 | 2011-07-03 20:00:00  | severe weather     |              3060 |              nan |                70000 |     2332915 |     2114774 |     2113291 |       6562520 |      5348119 |
|  1 |   2014 |       5 | Minnesota    | East North Central | normal             | 2014-05-11 18:38:00 | 2014-05-11 18:39:00  | intentional attack |                 1 |              nan |                  nan |     1586986 |     1807756 |     1887927 |       5284231 |      5457125 |
|  2 |   2010 |      10 | Minnesota    | East North Central | cold               | 2010-10-26 20:00:00 | 2010-10-28 22:00:00  | severe weather     |              3000 |              nan |                70000 |     1467293 |     1801683 |     1951295 |       5222116 |      5310903 |
|  3 |   2012 |       6 | Minnesota    | East North Central | normal             | 2012-06-19 04:30:00 | 2012-06-20 23:00:00  | severe weather     |              2550 |              nan |                68200 |     1851519 |     1941174 |     1993026 |       5787064 |      5380443 |
|  4 |   2015 |       7 | Minnesota    | East North Central | warm               | 2015-07-18 02:00:00 | 2015-07-19 07:00:00  | severe weather     |              1740 |              250 |               250000 |     2028875 |     2161612 |     1777937 |       5970339 |      5489594 |

## Univariate Analysis 
We will begin by visualizing power outages by single variables.

#### Here we analyze the distribution of climate categories
It was important for us to first recognize the distributions of climate categories in a pie chart as it shows us what type of climate the majority of power outages lie.
<iframe
  src="assets/univariate-plot-1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

