# PowerGrid Insights: Illuminating America's Outage Landscape

How do demographic factors of West Coast states influence the duration and affecting range of power outages, and what mitigation strategies can be employed to reduce the risk of outages in these regions?

# Assessment of Missingness
## NMAR
The concept of Not Missing At Random (NMAR) implies that the probability of a value being missing is dependent on the actual missing value itself. In the context of this dataset, the column in question records the names of hurricanes responsible for specific power outages. However, it is important to note that not all power outages can be attributed to hurricanes. Some outages may result from facility maintenance or other natural disasters.
Consequently, if a particular power outage is not caused by a hurricane, it is reasonable for the corresponding cell in the hurricane column to be missing. Incorporating an additional column, such as one that records the amount of rainfall during the corresponding time period, could provide further context. For instance, if the rainfall amount is significantly higher than usual, it is more likely that a hurricane is responsible for the power outage, and thus, the hurricane name column would be shown as NaN. 


## Missingness Test 1
In this test, we try to find out if the missingness in `CUSTOMERS.AFFECTED` column is depend on the the column `CAUSE.CATEGORY` or not. The `CUSTOMERS.AFFECTED` column signifies the number of individuals impacted by each power outage event, while the `CAUSE.CATEGORY` column categorizes the specific cause behind these power outages. Prior to commencing our analysis, it is important to examine the patterns and characteristics of the missing data distribution.
<iframe src="assets/missing_observed_graph1.html" width=800 height=600 frameBorder=0></iframe>


The graphical representation of the data reveals a limited number of cause categories, including `severe weather` and `public appeal`. Interestingly, a substantial proportion of power outages associated with missing `CUSTOMERS.AFFECTED` values can be attributed to `intentional attack`. Conversely, instances where the `CUSTOMERS.AFFECTED` value is present predominantly align with power outages caused by `severe weather`. To further ascertain whether the missingness follows a Missing at Random (MAR) pattern, we employ a Total Variation Distance (TVD) test following the permutation of the `CUSTOMERS.AFFECTED` column. TVD is selected due to the existence of a few cause categories, allowing us to assess the discrepancies between each category for the missing and non-missing groups. A significance level of 0.01 is employed, and the test is iterated 1000 times, yielding the following results:

<iframe src="assets/missing_tvd_tested_graph1.html" width=800 height=600 frameBorder=0></iframe>

We get the P value of 0! , and from the graph we can see that the red line and the distribution of the test result are in the two different world. This disparity strongly indicates that the missingness in the `CUSTOMERS.AFFECTED` column follows a Missing at Random (MAR) pattern. The evident distinction between the red line and the test result distribution further supports this conclusion. It becomes evident that the `CAUSE.CATEGORY` column provides valuable insights into the likelihood of missingness within the `CUSTOMERS.AFFECTED` column.

## Missingness Test 2
In this test, we try to find out if the missingness in `CUSTOMERS.AFFECTED` column is depend on the the column `TOTAL.PRICE` or not. The `TOTAL.PRICE` column categorizes the overall electricity price for each region which endured the power outage at that time (the unit is cents / kilowatt-hour). Prior to commencing our analysis, lets take a look of data distribution again:

<iframe src="assets/missing_ks_observed_graph.html" width=800 height=600 frameBorder=0></iframe>


Observing the graphical representation, it becomes apparent that the two graphs exhibit similar patterns. However, in order to further evaluate the comparison between the distribution of the price and its proportion, we employ the Kolmogorov-Smirnov (KS) test statistic following the permutation of the `CUSTOMERS.AFFECTED` column. The selection of KS is motivated by the desire to assess the similarity of the two groups' distributions, as they are situated within a similar range on the x-axis. By setting a significance level of 0.01, we iterate the test 1000 times, leading to the following results:

<iframe src="assets/missing_ks_tested_graph.html" width=800 height=600 frameBorder=0></iframe>

Based on our  testing, the obtained p-value is approximately 0.2 (with slight variability upon each code run), surpassing our predetermined significance level. Consequently, we can confidently conclude that there is no significant relationship between the missingness in the `CUSTOMERS.AFFECTED` column and the `TOTAL.PRICE` column. 

# Hypothesis Testing

## Hypothesis Testing with column `OUTAGE.DURATION`

Introduction: Our research question encompasses two main aspects. The first part seeks to understand the influence of demographic factors on the duration of power outages in West  states. To investigate this, we focus on two key columns: `CLIMATE.REGION` and `OUTAGE.DURATION`. The `CLIMATE.REGION` column provides information on the demographic location of each power outage event, while `OUTAGE.DURATION` indicates the length of time for each outage. Our approach begins by selecting data specifically related to the `west` climate region. We then employ hypothesis testing to assess whether being located in the West region results in different outage durations compared to the entire nation. By calculating the mean duration of outages in the West region and comparing it to the mean duration of outages across the entire country, we are able to discern notable differences. Specifically, we find that outage durations in the West region are shorter than those experienced nationwide, thereby helping to establish our null and alternative hypotheses.

Null Hypothesis: There is no siginificant difference between outage durations in the West region and those experienced nationwide

Alternative Hypothesis: Outage durations in the West region are shorter than those experienced nationwide

Hypothesis test & test statistics : The approach we use is that we will randomly select n rows from teh whole data set, n is the number of outage happened in west region, and calculate the means. Our test statistics is mean of the duration of the random slected rows, and we will compared it with our observed statistic (1628.33 min). The cutoff value is 0.01. 

After repeating the test 10000 times, here is what we get:
<iframe src="assets/fig_hyp1_duration.html" width=800 height=600 frameBorder=0></iframe>

Our P value is aound (0.0004), we can rejecte the null hypothesis and conclude that outage durations in the West region are shorter than those experienced nationwide. We are expcted to have a shorter duration of power outage if we are in the west!


## Hypothesis Testing with column `CUSTOMER.AFFECTED`

Introducton: The second part of our research question is to understand the influence of demographic factors on the population affected on each outage. In another words, we are interested at figure out if each outage happened in the west affect more people compared with the the area of the whole country, since it seems like there are lot of people densed aread in the west. Similar with the previous one, our approach begins by selecting data specifically related to the `west` climate region. By calculating the number of people affected in the West region and comparing it to the mnumber across the entire country, we are able to discern notable differences.


Null Hypothesis: The number of people affected by power outages on the West region has no siginificant difference with all regions of the country

Alternative Hypothesis: Compared to the entire country, power outages in the West region affect more people

Hypothesis test & test statistics : Same as previous one, the approach we use is that we will randomly select n rows from teh whole data set, n is the number of outage happened in west region, and calculate the means of people being affexted. Our test statistics is mean of the population of the random slected rows, and we will compared it with our observed statistic (194579.89). The cutoff value is 0.01. 

After repeating the test 10000 times, here is what we get:
<iframe src="assets/fig_hyp2_affected.html" width=800 height=600 frameBorder=0></iframe>

Our P value is aound (0.015), even though it is close, but we can not reject our null hypothesis and can not conclude that the outage happend in the west region affect more people compared with all of the regions in the US. 