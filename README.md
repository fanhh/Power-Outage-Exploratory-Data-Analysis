# Dataset Overview

## Introduction

This dataset encompasses Major Power Outage Events in the Continental United States, spanning from January 2000 to July 2016. It provides detailed insights into power outages that affected individual U.S. states at the time of occurrence. The dataset comprises over 1541 rows, each representing a unique power outage event, and is crucial for understanding patterns and causes of power outages across different regions and times.

## Central Question

The analysis centers around the question: "Are certain weather conditions, causes of events, or specific months more likely to lead to power outages?" This question is particularly important as it can assist individuals in understanding and potentially avoiding power outages. By analyzing this data, we can provide valuable information for planning travel or residential choices, aiming to reduce the likelihood of experiencing power outages.

## Why This Matters

Understanding the patterns in power outages is crucial for several reasons:

- **Preventive Planning**: Helps in strategic planning to prevent or mitigate outages.
- **Safety and Convenience**: Assists individuals in making informed decisions about travel or residential locations to avoid the inconvenience and potential hazards associated with power outages.
- **Resource Allocation**: Aids utility companies and government agencies in resource allocation and emergency preparedness, particularly in areas and times more susceptible to outages.

## Key Columns in the Dataset

The dataset contains several columns relevant to our central question:

- `CUSTOMERS.AFFECTED`: Number of customers affected by each power outage.
- `MONTH`: The month when the outage occurred.
- `YEAR`: The year when the outage occurred.
- `OUTAGE.DURATION`: The duration of the outage in minutes.
- `DEMAND.LOSS.MW`: The demand loss in megawatts due to the outage.
- `CAUSE.CATEGORY`: The primary cause category of each outage.

These columns provide essential data for analyzing the occurrence and impact of power outages in relation to time (month and year), weather conditions, and their resultant effects.

## Data Cleaning and Exploratory Data Analysis



## Univariate Analysis

<iframe src="Plots/Plots.html" width=800 height=600 frameBorder=0></iframe>


## Bivariate Analysis

<iframe src="Plots/cause_cust.html" width=800 height=600 frameBorder=0></iframe>


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

A p-value of 0.3538 suggests that there is no statistically significant association between the missingness of data in `CUSTOMERS.AFFECTED` and the `OUTAGE.DURATION`. This indicates that the likelihood of data being missing in the `CUSTOMERS.AFFECTED` column is not influenced by the duration of the power outage.

<iframe src="Plots/pval_notdep.html" width=800 height=600 frameBorder=0></iframe>

## Hypothesis Testing

**Null Hypothesis**: The average outage duration has remained constant or increased from January 2000 till July 2016. (We have not gotten better at fixing outages)

**Alternative Hypothesis**: The average outage duration has decreased overtime, from January 2000 till July 2016. (We have gotten better at fixing outages)

**Test Statistic**: We will be using linear regression to conduct our hypothesis test, as we are measuring over time. Linear regression is the most appropiate tool as it provides a quantitative measure of the strength and direction of the trend we want to investigate, in this case outage duration.

**Significance Level**: We will be using 0.05 as our significance level, as it's the standard significance level for hypothesis testing.

**p-value**: We calculated a p-value less than 0.001

**Conclusion**: We reject our null hypothesis as our p-value is greatly lower than our signifcance level of 0.05. We demonstrate that the amount of time an outage occurs for has decreased from 2000 to 2016. While we cannot a deduce a reason as to why this occurs, its reasonable to say that this is a real trend from 2000 to 2016.

<iframe src="Plots/LR_Outage_Time.html" width=800 height=600 frameBorder=0></iframe>



