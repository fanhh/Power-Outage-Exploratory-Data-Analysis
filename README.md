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


