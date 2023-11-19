# Dataset Overview

## Introduction

This dataset provides an extensive overview of Major Power Outage Events in the Continental United States from January 2000 to July 2016. It includes detailed data on individual power outages across U.S. states, comprising over 1541 unique events. This dataset is invaluable for examining the patterns, causes, and impacts of power outages in different regions and across various time periods.

## Central Question

In light of the evolving nature of power infrastructure and environmental factors, our analysis focuses on the trend of power outages over time: "Have power outages in the United States remained constant, or have they increased over the years?" This question is pivotal in understanding the resilience of power systems against various challenges and in anticipating future trends.

## Why This Matters

Examining the trend of power outages over time is crucial for multiple reasons:

- **Infrastructure Development**: Insights into outage trends can guide the improvement and reinforcement of power infrastructure.
- **Emergency Preparedness**: Understanding whether outages are increasing can help in enhancing emergency response strategies and resource allocation.
- **Policy Making**: Identifying trends in power outages supports informed policy decisions and investments in energy sectors.

## Key Columns in the Dataset

The dataset includes several columns that are instrumental in analyzing the trend and impact of power outages:

- `CUSTOMERS.AFFECTED`: The number of customers impacted by each power outage.
- `MONTH` and `YEAR`: The time when the outage occurred, providing a temporal context.
- `OUTAGE.DURATION`: The duration of each outage, in minutes.
- `DEMAND.LOSS.MW`: The magnitude of demand loss in megawatts.
- `CAUSE.CATEGORY`: The primary cause of each outage.

These columns are essential for understanding the frequency, duration, and causes of power outages, as well as their changing patterns over time.


## Data Cleaning and Exploratory Data Analysis

=======
## Data Cleaning

Our initial step in data preparation involved selectively retaining columns relevant to our analysis: 'YEAR', 'MONTH', 'CLIMATE.CATEGORY', 'CAUSE.CATEGORY', 'OUTAGE.DURATION', 'DEMAND.LOSS.MW', and 'CUSTOMERS.AFFECTED'. This refinement was essential to focus exclusively on variables that directly contribute to understanding power outages.

Subsequently, we addressed the structure and integrity of the data:

- **Indexing**: We set 'OBS' as the DataFrame index for easier data manipulation and referencing.
- **Trimming Rows**: The first row of the DataFrame was excluded, likely due to its irrelevance or incorrect data.
- **Excluding First Column**: The first column was discarded to eliminate unnecessary data, streamlining our dataset further.

Next, we concentrated on standardizing and clarifying the date information:

- **Date Conversion**: We converted 'OUTAGE.START.DATE' and 'OUTAGE.RESTORATION.DATE' into standardized datetime formats, maintaining only the date component for simplicity and consistency.

In dealing with missing values:

- **Missing Values Indicator**: A new column, 'CUSTOMERS.AFFECTED_MISSING', was introduced to mark rows with missing data in the 'CUSTOMERS.AFFECTED' field, enhancing the dataset's reliability for analytical purposes.

Finally, we enhanced the DataFrame’s accessibility:

- **Display Settings**: Adjusted display settings to ensure complete visibility of all DataFrame columns, aiding in comprehensive data examination and validation.

These steps collectively refined our dataset, enhancing its suitability for an in-depth analysis of power outage trends, causes, and impacts over time. The resulting dataset is more manageable, precise, and aligned with our analytical objectives.

Df.Head()

| OBS | YEAR  | MONTH | CLIMATE.CATEGORY | CAUSE.CATEGORY    | OUTAGE.DURATION | DEMAND.LOSS.MW | CUSTOMERS.AFFECTED |
|-----|-------|-------|------------------|-------------------|-----------------|----------------|--------------------|
| 1.0 | 2011  | 7     | normal           | severe weather    | 3060            | NaN            | 70000              |
| 2.0 | 2014  | 5     | normal           | intentional attack| 1               | NaN            | NaN                |
| 3.0 | 2010  | 10    | cold             | severe weather    | 3000            | NaN            | 70000              |
| 4.0 | 2012  | 6     | normal           | severe weather    | 2550            | NaN            | 68200              |
| 5.0 | 2015  | 7     | warm             | severe weather    | 1740            | 250            | 250000             |


## Univariate Analysis

<iframe src="Plots/Plots.html" width=800 height=600 frameBorder=0></iframe>
There is a significant increase in the number of outages during the summer months, particularly in hot weather conditions. Conversely, the early months show a higher frequency of outages in cold weather. For the remainder of the year, outage counts across various weather conditions tend to even out.


## Bivariate Analysis

<iframe src="Plots/Year_Outage.html" width=800 height=600 frameBorder=0></iframe>

This scatter plot visualizes the outage durations throughout the years, with the y-axis depicting how long an outage lasted, and the x-axis grouping the outages by year.

## Interesting Aggregates

The pivot table below presents the number of customers affected by power outages across different years, categorized by month and climate category. This data is critical for several aspects of understanding and managing power outages:

- **Temporal Analysis**: By showing data over various years, the table allows for trend analysis over time. It helps in identifying whether the impact of power outages on customers is changing.

- **Seasonal Variation and Climate Impact**: The categorization by months and climate categories reveals how power outages differ across seasons and under varying climatic conditions.

- **Year-to-Year Comparison**: This layout facilitates a direct comparison between different years, highlighting years with more severe outages.

Here is part of our Aggregates

| YEAR    | 2000.0 | 2001.0 | 2002.0 | 2003.0 | 2004.0 | 2005.0 | 2006.0 | 2007.0 | 2008.0 | 2009.0 | 2010.0 | 2011.0 | 2012.0 | 2013.0 | 2014.0 | 2015.0 | 2016.0 |
|---------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
| MONTH   | CLIMATE.CATEGORY |                                                                                  |
| April   | cold   | NaN    | NaN    | NaN    | NaN    | NaN    | NaN    | NaN    | NaN    | 488689 | NaN    | NaN    | 833000 | NaN    | NaN    | NaN    | NaN    | NaN    |
|         | normal | NaN    | NaN    | 0      | 653530 | 451000 | NaN    | 1085882| 644232 | NaN    | 738093 | NaN    | NaN    | 231770 | 99189  | 299200 | NaN    | NaN    |
|         | warm   | NaN    | NaN    | NaN    | NaN    | NaN    | 361000 | NaN    | NaN    | NaN    | NaN    | 149376 | NaN    | NaN    | NaN    | 582782 | 629967 | 
| August  | cold   | 568567 | NaN    | NaN    | NaN    | NaN    | NaN    | NaN    | 907090 | NaN    | NaN    | 492075 | 5193989| NaN    | NaN    | NaN    | NaN    | NaN    |
|         | normal | NaN    | 600000 | NaN    | 6815350| NaN    | 1702797| 0      | NaN    | 1327773| NaN    | NaN    | NaN    | 1042872| 663339 | NaN    | NaN    | NaN    |
|         | warm   | NaN    | NaN    | 25000  | NaN    | 2617000| NaN    | NaN    | NaN    | NaN    | 348156 | NaN    | NaN    | NaN    | NaN    | NaN    | 1263520| NaN    |
| ...     | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    | ...    |


## Assessment of Missingness

### NMAR (Not Missing At Random) Considerations

Based on the dataset analysis, which includes major power outage events in the continental U.S., I believe that the column `DEMAND.LOSS.MW` could potentially be NMAR (Not Missing At Random). This hypothesis stems from several observations and considerations regarding the nature of the data and the context of power outages:

#### Reasons for `DEMAND.LOSS.MW` Being Potentially NMAR:

1. **Nature of Power Outages**: The missingness in `DEMAND.LOSS.MW` may be related to the actual magnitude or severity of the outage. In cases of minor outages, detailed data like demand loss might not be consistently recorded, whereas major outages are likely to have more comprehensive data.

2. **Reporting Practices Variability**: Different regions or utilities might have varying practices in reporting demand loss, leading to inconsistent data availability.

3. **Data Collection Limitations**: The methods and tools used for data collection could influence the presence or absence of certain data, particularly in `DEMAND.LOSS.MW`.

### Conclusion

The hypothesis that `DEMAND.LOSS.MW` is NMAR is grounded in the belief that the missingness is likely tied to the value of the data itself or the specific circumstances of each outage, rather than being random or solely dependent on observable variables. Additional data and analysis could further elucidate this relationship and potentially reclassify the missingness as MAR.


## Missingness Dependency


### Permutation Test on Customers Affected Dependency on Cause Category

The permutation test conducted to analyze the dependency of missingness in the `CUSTOMERS.AFFECTED` column on the `CAUSE.CATEGORY` yielded compelling results:

- **Observed Statistic**: The observed statistic for the test was 459.1586462953329.
- **P-Value**: The calculated p-value was 0.0.

#### Interpretation

A p-value of 0.0 indicates that there is a statistically significant association between the missingness of data in `CUSTOMERS.AFFECTED` and the `CAUSE.CATEGORY` of the outage. This suggests that the likelihood of data being missing in the `CUSTOMERS.AFFECTED` column is not random but is instead influenced by the cause of the power outage.

<iframe src="Plots/pval_dep.html" width=800 height=600 frameBorder=0></iframe>


### Permutation Test on Customers Affected Dependency on Outage Duration

Another key aspect of our analysis was investigating the dependency of missingness in the `CUSTOMERS.AFFECTED` column on the `OUTAGE.DURATION`. The results of this permutation test were as follows:

- **Observed Statistic**: The observed statistic for this test was -773.5465909090908.
- **P-Value**: The calculated p-value was 0.3538.

#### Interpretation

A p-value of 0.9936 suggests that there is no statistically significant association between the missingness of data in `CUSTOMERS.AFFECTED` and the `OUTAGE.DURATION`. This indicates that the likelihood of data being missing in the `CUSTOMERS.AFFECTED` column is not influenced by the duration of the power outage.

<iframe src="Plots/pval_notdep.html" width=800 height=600 frameBorder=0></iframe>

## Hypothesis Testing

**Null Hypothesis**: The average outage duration has remained constant or increased from January 2000 till July 2016. (We have not gotten better at fixing outages)

**Alternative Hypothesis**: The average outage duration has decreased overtime, from January 2000 till July 2016. (We have gotten better at fixing outages)

**Test Statistic**: We will be using linear regression to conduct our hypothesis test, as we are measuring over time. Linear regression is the most appropiate tool as it provides a quantitative measure of the strength and direction of the trend we want to investigate, in this case outage duration.

**Significance Level**: We will be using 0.05 as our significance level, as it's the standard significance level for hypothesis testing.

**p-value**: We calculated a p-value less than 0.001

**Conclusion**: We reject our null hypothesis as our p-value is greatly lower than our signifcance level of 0.05. We demonstrate that the amount of time an outage occurs for has decreased from 2000 to 2016. While we cannot a deduce a reason as to why this occurs, its reasonable to say that this is a real trend from 2000 to 2016.

<iframe src="Plots/LR_Outage_Time.html" width=800 height=600 frameBorder=0></iframe>



