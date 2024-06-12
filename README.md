# Zoning Analysis and Predictive Modeling of Customers Affected in a Power Outage

### Created by Samuel Mahjouri and Zoya Hasan

## Introduction

Power outages pose significant risks to the safety, economy, and daily life of U.S. citizens, making it imperative to understand the factors that influence their duration and impact. Our  analysis utilizes a dataset on major power outage events in the continental U.S. from January 2000 to July 2016, provided by Mukherjee, Nateghi, and Hastak from Purdue University. The dataset includes information on geographical location, regional climatic conditions, land-use characteristics, regional electricity consumption patterns, and economic attributes of power outages in various states. Given such a holistic understanding of power outages, we posed the question that could support energy companies when considering where to aid during power outages. Our key question is: **What are the key factors that influence the durations of major power outages in the continental U.S., and how can these insights be used to mitigate future outages?** This question holds practical implications for utility companies, as well as regional communities. By identifying the determinants of outage durations, energy companies  can better prepare for and respond to future incidents. Given the increasing number and high severity of weather-related disruptions, understanding these dynamics, in correlation to power outages, is more critical than ever. The dataset used in this project has 1534 rows and 56 columns, and offers comprehensive insight to uncover our questions through data analysis. The dataset encompasses information on every major power outage in the United States from 2000 to 2016. Only a handful of columns were used for analysis and prediction, as described below:


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

### Here we outline the steps taken to clean our dataset so it is effective for analysis 
1. We  start by dropping missing rows and correctly labeled column titles with their corresponding features.We are only keeping the columns  that we are  working with for analysis. `YEAR`, `MONTH`, `U.S._STATE`, `CLIMATE.REGION`, `CLIMATE.CATEGORY`, `OUTAGE.START`, `OUTAGE.RESTORATION`, `CAUSE.CATEGORY`, `OUTAGE.DURATION`, `DEMAND.LOSS.MW`, `CUSTOMERS.AFFECTED`, `RES.SALES`, `COM.SALES`, `IND.SALES`, `TOTAL.SALES`, `POPULATION`]]
2. Then, we combined the `OUTAGE.START.DATE` and `OUTAGE.START.TIME` columns into a singular `OUTAGE.START` column that utilizes the Timestamp object. We followed the same for `OUTAGE.RESTORATION.DATE` and `OUTAGE.RESTORATION.TIME`, to get the comprehensive ending time for the outage (when the outage was restored). we then dropped the old columns since all the relevant timing was captured in `OUTAGE.START` and `OUTAGE.RESTORATION`
3. Next, we filled in missing values from the columns with NAN
Here is the first few rows of our cleaned dataframe. 

<div style="max-height: 400px; overflow-y: scroll;">
  <table border="1" class="dataframe">
    <thead>
      <tr style="text-align: right;">
        <th>YEAR</th>
        <th>MONTH</th>
        <th>U.S._STATE</th>
        <th>CLIMATE.REGION</th>
        <th>CLIMATE.CATEGORY</th>
        <th>OUTAGE.START</th>
        <th>OUTAGE.RESTORATION</th>
        <th>CAUSE.CATEGORY</th>
        <th>OUTAGE.DURATION</th>
        <th>DEMAND.LOSS.MW</th>
        <th>CUSTOMERS.AFFECTED</th>
        <th>RES.SALES</th>
        <th>COM.SALES</th>
        <th>IND.SALES</th>
        <th>TOTAL.SALES</th>
        <th>POPULATION</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>2011</td>
        <td>7</td>
        <td>Minnesota</td>
        <td>East North Central</td>
        <td>normal</td>
        <td>2011-07-01 17:00:00</td>
        <td>2011-07-03 20:00:00</td>
        <td>severe weather</td>
        <td>3060</td>
        <td>nan</td>
        <td>70000</td>
        <td>2332915</td>
        <td>2114774</td>
        <td>2113291</td>
        <td>6562520</td>
        <td>5348119</td>
      </tr>
      <tr>
        <td>2014</td>
        <td>5</td>
        <td>Minnesota</td>
        <td>East North Central</td>
        <td>normal</td>
        <td>2014-05-11 18:38:00</td>
        <td>2014-05-11 18:39:00</td>
        <td>intentional attack</td>
        <td>1</td>
        <td>nan</td>
        <td>nan</td>
        <td>1586986</td>
        <td>1807756</td>
        <td>1887927</td>
        <td>5284231</td>
        <td>5457125</td>
      </tr>
      <tr>
        <td>2010</td>
        <td>10</td>
        <td>Minnesota</td>
        <td>East North Central</td>
        <td>cold</td>
        <td>2010-10-26 20:00:00</td>
        <td>2010-10-28 22:00:00</td>
        <td>severe weather</td>
        <td>3000</td>
        <td>nan</td>
        <td>70000</td>
        <td>1467293</td>
        <td>1801683</td>
        <td>1951295</td>
        <td>5222116</td>
        <td>5310903</td>
      </tr>
      <tr>
        <td>2012</td>
        <td>6</td>
        <td>Minnesota</td>
        <td>East North Central</td>
        <td>normal</td>
        <td>2012-06-19 04:30:00</td>
        <td>2012-06-20 23:00:00</td>
        <td>severe weather</td>
        <td>2550</td>
        <td>nan</td>
        <td>68200</td>
        <td>1851519</td>
        <td>1941174</td>
        <td>1993026</td>
        <td>5787064</td>
        <td>5380443</td>
        
## Univariate Analysis 
We will begin by visualizing power outages by single variables.

#### Here we analyze the distribution of climate categories
It was important for us to first recognize the distributions of climate categories in a pie chart as it shows us what type of climate the majority of power outages occur in.
<iframe
  src="assets/univariate-plot-1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Here we analyze the frequency distribution of outages per month 
The bar graph illusrates a potential predictor for people affected bt power outages, such as month of year, since we notice there is a high frequency of outages in summer months.
<iframe
  src="assets/univariate-plot-2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


## Bivariate Analysis 
We now perfomed a bivariate analysis on energy usage and outage duration in 2 different living sectors. 

#### what is this graph sam
explain the importance and what it shows sam 
<iframe
  src="assets/bivariate-plot-1.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>


#### what is this graph sam
explain the importance and what it shows sam 
<iframe
  src="assets/bivariate-plot-2.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

#### Grouping and Aggregates 
sam why did you choose to do the pivot table this way and what does it show us

| CAUSE.CATEGORY                |        2000-2003 |       2005-2008 |        2009-2012 |        2013-2016 |
|:------------------------------|-----------------:|----------------:|-----------------:|-----------------:|
| equipment failure             | 897928           |     1568480 | 329604           | 262055           |
| fuel supply emergency         |      0           |     0           |      0           |      1           |
| intentional attack            |      0           |     0           | 133234           | 223081           |
| islanding                     |      0           | 49646           |  63164           |  96939           |
| public appeal                 |  55800           | 16000           |  88194           |      0           |
| severe weather                |      25976868 |     44932491 |      43023494 |      21275280 |
| system operability disruption |      11209646 |     3075918 |      2426558 | 806358           |



# Assessment of Missingness

## NMAR Analysis 

The `YEAR`column is likely to be NMAR because the occurrence of an outage in a particular year is typically independent of other features within the dataset. Each outage event should have an associated year, and the missingness of a `YEAR` value would generally not be influenced by the outage's characteristics, but rather the way the data was reported and collected, such as certain companies not reporting data into a source. Therefore, the missingness in the `YEAR`n column would typically depend on the value of the data itself. Additional data that we could collect to determine if the missingness is MAR is collecting information on the documentation practices of power outages over the years, including any regulatory changes in reporting requirements or practices that might have occurred. With this, we could analyze if there is an association between a change in reporting practices, with the missingness of the year values, making it MAR.

## Missingness Dependency 

Looking at the dataset, there are many columns that have missingness that can be assessed, but we focused specifically on the `DEMAND.LOSS.MW`, because we wanted to analyze whether power was supplied efficiently when experiencing an outage. We will test against the missingness using columns `CAUSE.CATEGORY` and `MONTH`. 

### Cause Category
Firstly, we evaluated the distribution of `CAUSE.CATEGORY` when `DEMAND.LOSS.MW `is missing vs not missing.

**Null Hypothesis**: The distribution of CAUSE.CATEGORY is the same when DEAMND.LOSS.MW is missing vs not missing.

**Alternative Hypothesis**: The distribution of CAUSE.CATEGORY is different when DEMAND.LOSS.MW is missing vs not missing.
<iframe
  src="assets/cause-bar-plot.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/cause-dist-chart.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

We observed a total variation distance (TVD) of 0.179,  with a a p value of 0.0 (alpha 0.01). At this value, we reject the null hypothesis in favor of the alternative, establishing that the distribution of CAUSE.CATEGORY.  CAUSE.CATEGORY  is significantly different when DEMAND.LOSS.MW is or is not missing, indicating that the missingness of DEMAND.LOSS.MW is dependent on CAUSE.CATEGORY.

### Month
Secondly, we evaluated the distribution of `MONTH` when `DEMAND.LOSS.MW` is missing vs not missing.

**Null Hypothesis**: The distribution of `MONTH` is the same when `DEMAND.LOSS.MW ` is missing vs not missing.

**Alternative Hypothesis**: The distribution of `MONTH` is different when `DEMAND.LOSS.MW ` is missing vs not missing.

<iframe
  src="assets/month-bar-plot.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

<iframe
  src="assets/month-dist-chart.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

We analyze an observed Total Variation Distance (TVD) of 0.103, with a p-value of 0.026 (alpha 0.01).  At this value, we fail to reject the null hypothesis in favor of the alternative. The distribution of MONTH is not significantly different when `DEMAND.LOSS.MW`  is missing or not missing, indicating that the missingness of `DEMAND.LOSS.MW` is not dependent on Month.

# Hypothesis Testing 

## We will be testing whether the power outage durations are higher on average for industrial areas over commercial areas, since industrial areas may have higher energy consumption than commercial areas; therefore,  the relevant columns for testing this hypothesis are  OUTAGE.DURATION and COM.SALES, IND.SALES, AND TOTAL.SALES

**Null Hypothesis (H₀)**: On average, power outage durations are the same for industrial and commercial areas, they are the same regardless of whether industrial energy consumption is higher or lower than commercial energy consumption.

**Alternative Hypothesis (H₁()**: On average, power outage durations are higher for industrial areas than commercial areas because industrial energy consumption is higher than commercial energy consumption.

**Test Statistic**: Difference in means. 
The mean power outage duration for a commercial area- mean power outage duration of an industrial area.

Although we are only analyzing the mean differences of duration of power outages for only 2 of these 3 living sectors, we went about an approach that could better encompass the proportion of these sectors in terms of the total sales. To do so we followed this process:

1. Calculated the proportion of sales (energy consumption) for each living sector in terms of total sales. 
2. Found which living sector had the max proportion of sales for that row. If the max was RES (meaning the residential living sector primarily had the most energy consumption for that outage), then we proceeded to drop that row, since we only wanted our focus to be on the commercial and industrial sectors.
3. Since the commercial and industrial sectors had very similar energy consumptions, their differences in outage duration were also close together. We classified a threshold (the median of the distribution of differences) to decide whether that outage was COM or IND. The median we used for threshold was 8.08 
4. Calculated observed differences and performed permutation testing.

We then performed a permutation test with 10,000 simulations in order to develop an empirical distribution of the test statistic under the null hypothesis. We obtained a p-value of 0.273, with an alpha of 0.05. We failed to reject the null hypothesis, concluding that ** on average, the duration of power outages is the same for industrial and commercial areas, regardless of whether industrial energy consumption is higher or lower than commercial energy consumption.** 

<iframe
  src="assets/hypothesis-testing-graphing.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

# Framing a Prediction Problem
Our model will try to **predict the number of customers affected by a major power outage**, which is a regression problem. 

The response variable we are predicting is `CUSTOMERS.AFFECTED`, we chose this because this column captures the number of customers in total that are affected by a certain outage. The metric we are using to evaluate our model is R^2, we chose this metric because it is a simplistic, yet efficient way to measure goodness of fit of our model and how well the model's predictions match the actual data. We chose this metric over other metrics because R^2 can be especially helpful in model selection and validation, as well as be used for easy comparison with a baseline model to see how much improvement a more complex model provides.

At the time of prediction, we would know the features: `MONTH`, `YEAR` `TOTAL.CUSTOMERS`, `OUTAGE.START`, `U.S._STATE`, `POPULATION`, `CLIMATE.CATEGORY`, `CAUSE.CATEGORY’, ‘NERC.REGION`, `UTIL.CONTRI`, `TOTAL.SALES`. Understanding these features information will aid us in predicting the number of customers affected by a major power outage.  

# Baseline Model 
Our baseline model employs simple linear regression with two features: `MONTH`, an ordinal categorical column, and `TOTAL.CUSTOMERS`, a numerical column. We selected `MONTH` to capture potential seasonal patterns affecting power outages and `TOTAL.CUSTOMERS` to account for the scale of the customer base impacted by outages. No encoding or transformations were applied, as our goal was to establish a baseline performance using raw data. The model achieved an R^2 value of 0.018 on the test set, meaning that only 1% of the variance in the number of customers affected is explained by these features. This low R^2 suggests that while `MONTH` and `TOTAL.CUSTOMERS` provide some insight, they are insufficient alone to predict the number of affected customers accurately, pointing to the need for more features and advanced modeling techniques to enhance predictive performance.

# Final Model 

# Fairness Analysis 

# Conclusion 
