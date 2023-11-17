# Analysis of Power Outages

by Luke Lin (lul018@ucsd.edu) & Andrew ()

---

## Introduction 

In this project, we analyze a dataset of power outages across different U.S. states. The dataset provides detailed information about each power outage, including the cause, duration, number of customers affected, and various other factors. Our analysis is centered around the question: “How has outage handling improved over the last decade?”

The dataset contains 1000 rows and the following columns are relevant to our question:
- ‘U.S._STATE’: The state where the power outage occurred.
- ‘OUTAGE.DURATION’: The duration of the power outage in minutes.

## Cleaning and EDA

We started by cleaning the dataset, handling missing values, and converting data types where necessary. We then performed an exploratory data analysis to understand the distribution of power outages across different states, causes, and time periods.

The data cleaning process involved replacing missing values with NaN and converting the ‘OUTAGE.DURATION’ column to numeric. This was necessary because the original data contained some non-numeric values in this column.

Here’s the head of the cleaned DataFrame:


|   OBS |   YEAR |   MONTH | U.S._STATE   | POSTAL.CODE   | NERC.REGION   | CLIMATE.REGION     |   ANOMALY.LEVEL | CLIMATE.CATEGORY   | CAUSE.CATEGORY     | CAUSE.CATEGORY.DETAIL   |   HURRICANE.NAMES |   OUTAGE.DURATION |   DEMAND.LOSS.MW |   CUSTOMERS.AFFECTED |   RES.PRICE |   COM.PRICE |   IND.PRICE |   TOTAL.PRICE |   RES.SALES |   COM.SALES |   IND.SALES |   TOTAL.SALES |   RES.PERCEN |   COM.PERCEN |   IND.PERCEN |   RES.CUSTOMERS |   COM.CUSTOMERS |   IND.CUSTOMERS |   TOTAL.CUSTOMERS |   RES.CUST.PCT |   COM.CUST.PCT |   IND.CUST.PCT |   PC.REALGSP.STATE |   PC.REALGSP.USA |   PC.REALGSP.REL |   PC.REALGSP.CHANGE |   UTIL.REALGSP |   TOTAL.REALGSP |   UTIL.CONTRI |   PI.UTIL.OFUSA |   POPULATION |   POPPCT_URBAN |   POPPCT_UC |   POPDEN_URBAN |   POPDEN_UC |   POPDEN_RURAL |   AREAPCT_URBAN |   AREAPCT_UC |   PCT_LAND |   PCT_WATER_TOT |   PCT_WATER_INLAND | OUTAGE.START        | OUTAGE.RESTORATION   |
|------:|-------:|--------:|:-------------|:--------------|:--------------|:-------------------|----------------:|:-------------------|:-------------------|:------------------------|------------------:|------------------:|-----------------:|---------------------:|------------:|------------:|------------:|--------------:|------------:|------------:|------------:|--------------:|-------------:|-------------:|-------------:|----------------:|----------------:|----------------:|------------------:|---------------:|---------------:|---------------:|-------------------:|-----------------:|-----------------:|--------------------:|---------------:|----------------:|--------------:|----------------:|-------------:|---------------:|------------:|---------------:|------------:|---------------:|----------------:|-------------:|-----------:|----------------:|-------------------:|:--------------------|:---------------------|
|     1 |   2011 |       7 | Minnesota    | MN            | MRO           | East North Central |            -0.3 | normal             | severe weather     | nan                     |               nan |              3060 |              nan |                70000 |       11.6  |        9.18 |        6.81 |          9.28 |     2332915 |     2114774 |     2113291 |       6562520 |      35.5491 |      32.225  |      32.2024 |         2308736 |          276286 |           10673 |           2595696 |        88.9448 |        10.644  |       0.411181 |              51268 |            47586 |          1.07738 |                 1.6 |           4802 |          274182 |       1.75139 |             2.2 |      5348119 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2011-07-01 17:00:00 | 2011-07-03 20:00:00  |
|     2 |   2014 |       5 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | intentional attack | vandalism               |               nan |                 1 |              nan |                  nan |       12.12 |        9.71 |        6.49 |          9.28 |     1586986 |     1807756 |     1887927 |       5284231 |      30.0325 |      34.2104 |      35.7276 |         2345860 |          284978 |            9898 |           2640737 |        88.8335 |        10.7916 |       0.37482  |              53499 |            49091 |          1.08979 |                 1.9 |           5226 |          291955 |       1.79    |             2.2 |      5457125 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2014-05-11 18:38:00 | 2014-05-11 18:39:00  |
|     3 |   2010 |      10 | Minnesota    | MN            | MRO           | East North Central |            -1.5 | cold               | severe weather     | heavy wind              |               nan |              3000 |              nan |                70000 |       10.87 |        8.19 |        6.07 |          8.15 |     1467293 |     1801683 |     1951295 |       5222116 |      28.0977 |      34.501  |      37.366  |         2300291 |          276463 |           10150 |           2586905 |        88.9206 |        10.687  |       0.392361 |              50447 |            47287 |          1.06683 |                 2.7 |           4571 |          267895 |       1.70627 |             2.1 |      5310903 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2010-10-26 20:00:00 | 2010-10-28 22:00:00  |
|     4 |   2012 |       6 | Minnesota    | MN            | MRO           | East North Central |            -0.1 | normal             | severe weather     | thunderstorm            |               nan |              2550 |              nan |                68200 |       11.79 |        9.25 |        6.71 |          9.19 |     1851519 |     1941174 |     1993026 |       5787064 |      31.9941 |      33.5433 |      34.4393 |         2317336 |          278466 |           11010 |           2606813 |        88.8954 |        10.6822 |       0.422355 |              51598 |            48156 |          1.07148 |                 0.6 |           5364 |          277627 |       1.93209 |             2.2 |      5380443 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2012-06-19 04:30:00 | 2012-06-20 23:00:00  |
|     5 |   2015 |       7 | Minnesota    | MN            | MRO           | East North Central |             1.2 | warm               | severe weather     | nan                     |               nan |              1740 |              250 |               250000 |       13.07 |       10.16 |        7.74 |         10.43 |     2028875 |     2161612 |     1777937 |       5970339 |      33.9826 |      36.2059 |      29.7795 |         2374674 |          289044 |            9812 |           2673531 |        88.8216 |        10.8113 |       0.367005 |              54431 |            49844 |          1.09203 |                 1.7 |           4873 |          292023 |       1.6687  |             2.2 |      5489594 |          73.27 |       15.28 |           2279 |      1700.5 |           18.2 |            2.14 |          0.6 |    91.5927 |         8.40733 |            5.47874 | 2015-07-18 02:00:00 | 2015-07-19 07:00:00  |

---

## Univariate Analysis
We first looked at the distribution of the ‘OUTAGE.DURATION’ column. The plot below shows that most power outages last less than 500 minutes, but there are some outages that last much longer.
<iframe src="Assets/Distribution_of_OUTAGE.html" width=800 height=600 frameBorder=0></iframe>

## Bivariate Analysis
Next, we looked at the average outage duration for each state. The plot below shows that some states tend to have longer power outages than others.
<iframe src="Assets/avg_outage_duration.html" width=800 height=600 frameBorder=0></iframe>

## Interesting Aggregates
After seeing large swings in power outage durations, we also examined the average number of customers affected for each state. The table below shows that the average outage duration varies widely from state to state. The table below also includes the latitude and longtitude of each state to display on a heap map using Folium.


| U.S._STATE           |   CUSTOMERS.AFFECTED |   Latitude |   Longitude |
|:---------------------|---------------------:|-----------:|------------:|
| Alabama              |             94328.8  |    33.2589 |    -86.8295 |
| Alaska               |             14273    |    64.446  |   -149.681  |
| Arizona              |             64402.7  |    34.3953 |   -111.763  |
| Arkansas             |             47673.8  |    35.2049 |    -92.4479 |
| California           |            201366    |    36.7015 |   -118.756  |
| Colorado             |             41060.6  |    38.7252 |   -105.608  |
| Connecticut          |             60339.2  |    41.65   |    -72.7342 |
| Delaware             |              3475    |    38.692  |    -75.4013 |
| District of Columbia |            194709    |    38.8938 |    -76.988  |
| Florida              |            289369    |    27.7568 |    -81.464  |
| Georgia              |            120680    |    32.3294 |    -83.1137 |
| Hawaii               |            147237    |    19.5938 |   -155.428  |
| Idaho                |              5833.33 |    43.6448 |   -114.015  |
| Illinois             |            207027    |    40.0797 |    -89.4337 |
| Indiana              |             69551.4  |    40.327  |    -86.1747 |
| Iowa                 |             94000    |    41.9217 |    -93.3123 |
| Kansas               |            108000    |    38.2731 |    -98.5822 |
| Kentucky             |            130531    |    37.5726 |    -85.1551 |
| Louisiana            |            151003    |    30.8704 |    -92.0071 |
| Maine                |             54839.4  |    45.7091 |    -68.859  |
| Maryland             |            120535    |    39.5162 |    -76.9382 |
| Massachusetts        |             77983.4  |    42.3789 |    -72.0324 |
| Michigan             |            152878    |    43.6212 |    -84.6824 |
| Minnesota            |            124007    |    45.9897 |    -94.6113 |
| Mississippi          |              5000    |    32.9715 |    -89.7348 |
| Missouri             |             50611.1  |    38.7605 |    -92.5618 |
| Nebraska             |             87070.7  |    41.737  |    -99.5874 |
| Nevada               |             22220    |    39.5159 |   -116.854  |
| New Hampshire        |             13869.8  |    43.4849 |    -71.6554 |
| New Jersey           |            160217    |    40.0757 |    -74.4042 |
| New Mexico           |            166667    |    34.5802 |   -105.996  |
| New York             |            190676    |    40.7127 |    -74.006  |
| North Carolina       |             99624.8  |    35.673  |    -79.0393 |
| North Dakota         |             34500    |    47.6201 |   -100.541  |
| Ohio                 |            136783    |    40.2254 |    -82.6881 |
| Oklahoma             |            160683    |    34.9551 |    -97.2684 |
| Oregon               |             43958.6  |    43.9793 |   -120.737  |
| Pennsylvania         |            168537    |    40.97   |    -77.7279 |
| South Carolina       |            251913    |    33.6874 |    -80.4364 |
| Tennessee            |             59317.4  |    35.773  |    -86.282  |
| Texas                |            223232    |    31.2639 |    -98.5456 |
| Utah                 |             10227.7  |    39.4225 |   -111.714  |
| Vermont              |                 0    |    44.5991 |    -72.5003 |
| Virginia             |            149429    |    37.1232 |    -78.4928 |
| Washington           |            101944    |    38.895  |    -77.0365 |
| West Virginia        |            179794    |    38.4758 |    -80.8408 |
| Wisconsin            |             45876    |    44.4309 |    -89.6885 |
| Wyoming              |             11833.3  |    43.17   |   -107.569  |

---

Below shows the Heap Map representation of the number of customers affected. 
<iframe src="Assets/heatMap.html" width=800 height=600 frameBorder=0></iframe>


## Missingness Analysis

### NMAR Analysis

In this section, we explored the possibility of Non-Missing at Random (NMAR) in our dataset. While no code is provided for this analysis (as NMAR determination involves reasoning about the data generating process), we believe that the column 'CAUSE.CATEGORY.DETAIL' is likely NMAR. This belief stems from the understanding that detailed descriptions of event categories in 'CAUSE.CATEGORY.DETAIL' could result in complex and non-random missingness. Additional data on the uniqueness or complexity of the cause might help make it Missing at Random (MAR).

### Missingness Dependency

Since our question is based around whether outage handling has improved over time, we chose 'OUTAGE.DURATION' for analysis due to its non-trivial missingness and its contribution to measuring improvements in outage handling. Permutation tests were performed to analyze the dependency of the missingness of 'OUTAGE.DURATION' on other columns.

- **Dependency on 'CUSTOMERS.AFFECTED':**
Null Hypothesis: The missingness of outage duration does not depend on customers affected.

Alternative Hypothesis: The missingness of outage duration depends on customers affected.

We created a new boolean column to indicate missing values in our OUTAGE.DURATION column and used the Kolmogorov-Smirnov test to get a p-value of 0.34 which is higher than our significane level of 0.05. This means we fail to reject the null hypothesis. Below we have a visualization of the two distributions and can see that distribution of CUSTOMERS.AFFECTED is similar in both cases, and that it is likely the missingness of CUSTOMERS.AFFECTED does not depend on the OUTAGE.DURATION column.

<iframe src="Assets/missing1.html" width=800 height=600 frameBorder=0></iframe>
From the graph above we can see that the distribution of customers affected appears to be similar regardless of the missing data in outage duration.

- **Dependency on 'TOTAL.SALES':** Null Hypothesis: The missingness of outage duration does not depend on total sales.

Alternative Hypothesis: The missingness of outage duration depends on total sales.

We created a new boolean column to indicate missing values in our OUTAGE.DURATION column and used the Kolmogorov-Smirnov test to get a p-value of 0.00 which is lower than our significane level of 0.05. This means we reject the null hypothesis. Below we have a visualization of the two distributions and can see that distribution of TOTAL.SALES is different in both cases, and that it is likely the missingness of CUSTOMERS.AFFECTED does depend on the TOTAL.SALES column.

<iframe src="Assets/missing2.html" width=800 height=600 frameBorder=0></iframe>
From the graph above we can see that there tends to be a skew towards lower total sales when it comes to missingness of outage duration.



### Hypothesis Testing

# Permutation Test for Mean Outage Duration (2005 vs. 2015)
In this section, we perform a permutation test to assess whether there is a significant difference in the mean outage duration between the years 2005 and 2015.

## Hypotheses
- **Null Hypothesis (H0):** There is no difference in mean outage duration for outages that occured in 2005 and in 2015.
- **Alternative Hypothesis (H1):** The mean outage duration for outages that occured in 2005 is larger than those that occured in 2015.

## Test Statistic
We choose the difference in mean outage duration between the two years as our test statistic. The observed difference is calculated using the actual data, and we compare this against a distribution of differences obtained by shuffling the outage duration data.

## Significance Level
We set the significance level at 0.05, which is a common choice in hypothesis testing.

## Justification
- The choice of a permutation test is appropriate when the assumptions of parametric tests are not met, or the distribution of the data is unknown.
- We use a one-sided test as we believe outage handling is unlikely to have gotten worse and we are only concerned with how its improved.
- The test statistic (difference in means) aligns with the question of interest, comparing the average outage duration between the two years.
- A significance level of 0.05 is commonly used and provides a balance between Type I and Type II errors.

## Permutation Test Procedure
- **Data Preparation:**
We filter the dataset to include only rows from the years 2005 and 2015.
Missing values are dropped from the dataset.
- **Observation:**
The observed difference in mean outage duration between 2005 and 2015 is computed.
- **Permutation Test Loop (500 Repetitions):**
In each iteration, the outage duration data is shuffled, and the difference in mean outage duration is calculated.
These differences form a distribution under the null hypothesis.
- **P-value Calculation:**
The proportion of permuted mean differences that are greater than or equal to the observed difference is calculated.
- **Results**
The resulting p-value is the probability of observing a difference in mean outage duration as extreme as the observed difference under the assumption that there is no true difference between the years 2005 and 2015.

<iframe src="Assets/conclusion.html" width=800 height=600 frameBorder=0></iframe>
From the figure about we can see the distribution of mean differences that we found when experimenting. Our observed mean difference went far beyond the 0.05th percentile and we can clearly see it is unlikely there is no difference between the groups.

## Conclusion
**P-value: 0.0**
**Conclusion:** Since our p-value is less than the chosen significance level (0.05), we reject the null hypothesis in favor of the alternative hypothesis, suggesting a significant difference in mean outage duration between the years 2005 and 2015. From our tests, we have sufficient evidence to reject our null hypothesis. We therefore reject the idea that outage durations have stayed the same over the past 10 years.


