By Eric Sun (z9sun@ucsd.edu) & Sunan Xu (sux002@ucsd.edu)

---

# Introduction
## Abstract
Power outages in the United States can have significant impacts on individuals, communities, businesses, and critical infrastructure. They occur when the supply of electricity to an area is disrupted, resulting in a loss of power. Power outages can occur due to a variety of reasons, including natural disasters, equipment failures, human errors, and intentional acts.

Natural disasters, such as hurricanes, tornadoes, severe storms, earthquakes, and wildfires, can damage power infrastructure, including power lines, transformers, and substations, leading to widespread outages. These events can cause significant disruptions to daily life, including the loss of heating, cooling, lighting, and essential services like healthcare and communication.

Equipment failures, such as malfunctioning transformers, faulty wiring, or aging infrastructure, can also result in power outages. These failures can occur due to regular wear and tear, inadequate maintenance, or unforeseen circumstances.

Human errors, such as construction accidents, excavation damage, or operational mistakes, can inadvertently cause power outages. Additionally, intentional acts of vandalism, sabotage, or cyberattacks targeting the power grid can disrupt the supply of electricity and have severe consequences.

The impacts of power outages can be wide-ranging. They can lead to financial losses for businesses, disrupt critical infrastructure like hospitals and transportation systems, affect communication networks, and compromise public safety. Power outages can also pose risks to vulnerable populations, including the elderly, individuals with medical conditions, and those relying on powered medical devices.

Efforts to minimize power outages and enhance grid resilience involve investments in infrastructure upgrades, regular maintenance, improved monitoring and detection systems, and implementing smart grid technologies. These measures aim to reduce the frequency and duration of outages, enhance response and restoration capabilities, and improve the overall reliability of the power supply.

Understanding the causes and durations of power outages is crucial for developing effective mitigation strategies, improving emergency preparedness, and ensuring a reliable and resilient power grid. By analyzing historical data and identifying patterns and trends, stakeholders can work towards minimizing the impact of power outages and enhancing the overall resilience of the U.S. electrical infrastructure.

## Dataset
Throughout this report, we will use the dataset from Purdue University with the name of *Major Power Outage Risks in the U.S.*, which can also be found [here](https://engineering.purdue.edu/LASCI/research-data/outages/outagerisks). This dataset has major power outage data in the continental U.S. from January 2000 to July 2016.

The dataset provides information on major power outages in the continental United States. It includes details such as the year, month, U.S. state, postal code, NERC (North American Electric Reliability Corporation) region, climate region, cause category, outage duration, electricity demand loss, customers affected, and various economic and demographic characteristics of the affected states.

Number of Rows in the Dataset: 1534 rows.

## Question Identification
As a result, we are able to trigger our research question: *How do demographic factors of West Coast states influence the duration and affecting range of power outages, and what mitigation strategies can be employed to reduce the risk of outages in these regions?*

Some relevant columns:

- `YEAR`: The year when the outage occurred (integer).
- `MONTH`: The month when the outage occurred (float).
- `U.S._STATE`: The name of the U.S. state where the outage occurred (string).
- `POSTAL.CODE`: The postal code of the affected area (string).
- `NERC.REGION`: The NERC region where the outage occurred (string).
- `CLIMATE.REGION`: The climate region of the affected area (string).
- `CAUSE.CATEGORY`: The category of the cause of the outage (string).
- `CAUSE.CATEGORY.DETAIL`: Further details about the cause of the outage (string).
- `OUTAGE.DURATION(mins)`: The duration of the outage in minutes (float).
- `CUSTOMERS.AFFECTED`: The number of customers affected by the outage (float).
- `RES.PRICE(cents / kilowatt-hour)`: Residential price of electricity in cents per kilowatt-hour (float).
- `POPULATION`: The population of the state (float).
- `OUTAGE.START`: The date and time when the outage started (datetime).
- `OUTAGE.RESTORATION`: The date and time when power was restored after the outage (datetime).

---

# Cleaning and EDA (Exploratory Data Analysis)
## Data Cleaning


## Univariate Analysis
*The first two plots are based on the column* `U.S._STATE`.

1. The plot titled "State Power Outage Count" is a bar chart that shows the number of power outages for each state. The color of the bars represents the values of the states. By analyzing the plot, we can identify any trends or variations in power outage counts across different states.
    
    Some states have considerably higher outage counts compared to others, indicating a higher frequency of power disruptions. This could be due to various factors such as weather conditions, infrastructure vulnerabilities, or population density. The color encoding provides additional information, potentially highlighting states with particularly severe outage situations.

    <iframe src="assets/state_power_outage_count.html" width=800 height=600 frameBorder=0></iframe>

2. The plot titled "State Frequency Map" is a choropleth map that visualizes the frequency of power outages across different states in the United States. Each state is color-coded based on the number of outages it has experienced. This graph is important as it provides a spatial representation of outage occurrences, allowing us to identify regions with higher outage frequencies and potentially uncover patterns or correlations between geographic factors and outage occurrences.

    This visualization helps highlight areas that require closer attention for improving resilience and mitigating power outage risks, which is a more direct visualization comparing to the above bar plot.

    <iframe src="assets/state_frequency_map.html" width=800 height=600 frameBorder=0></iframe>

*The third plot is based on the column* `CAUSE.CATEGORY`.

3. The plot titled "Count of Outages by Cause Category" is a bar chart that displays the number of outages categorized by their cause. Each bar represents a specific cause category, and its height corresponds to the count of outages in that category. This graph is important as it allows us to understand the main causes of power outages and identify the categories that contribute the most to the overall outage count.

    The bar chart provides insights into the distribution of power outages based on their cause categories. By analyzing the chart, we can identify the cause categories that are more prevalent in the dataset. This information is valuable for understanding the primary factors leading to power outages and can guide efforts towards implementing preventative measures or improving infrastructure resilience in specific areas.

    <iframe src="assets/outage_count_by_category.html" width=800 height=600 frameBorder=0></iframe>

## Bivariate Analysis

1. The plot titled "Residential vs Commercial Sales" is a scatter plot that compares the sales of electricity in megawatt-hours (MWh) for residential and commercial sectors, and the trendline is shown as OLS regression. Each data point represents a state, and its position on the plot indicates the corresponding values for residential and commercial sales. The color of the data points is based on the population of the state. This graph is important as it helps visualize the relationship between residential and commercial electricity sales and identify any potential correlations or trends.

    Since we have use `POPULATION` as the color, we can clearly find out the relation that with the increasing population among all regions, the corresponding general sales of electricity will also increment, which again verifies a daily circumstance that we realized every day.

    <iframe src="assets/resales_vs_comsales.html" width=800 height=600 frameBorder=0></iframe>

2. The plot titled "Outage Duration by Climate Category" is a box plot that displays the distribution of outage durations in minutes across different climate categories. Each box represents a climate category, and the vertical axis represents the duration of outages in minutes. This graph is important as it allows us to compare the outage durations between different climate categories and identify any variations or trends.

    <iframe src="assets/duration_vs_category.html" width=800 height=600 frameBorder=0></iframe>

3. The plot titled "Correlation Heatmap" visualizes the correlation matrix of the dataset using a color scale. Each cell represents the correlation coefficient between two variables, with cooler colors indicating positive correlations and warmer colors indicating negative correlations. This plot is important as it helps identify relationships and dependencies between different variables in the dataset.

    By analyzing the heatmap, we can gain insights into which variables are strongly correlated or inversely correlated, which can guide further analysis and exploration of causal relationships. It can also help identify potential factors that contribute to power outages and inform decision-making for prevention and mitigation strategies.

    <iframe src="assets/correlation_heatmap.html" width=800 height=600 frameBorder=0></iframe>

## Interesting Aggregates

---

# Assessment of Missingness
## NMAR
The concept of Not Missing At Random (NMAR) implies that the probability of a value being missing is dependent on the actual missing value itself. In the context of this dataset, the column in question records the names of hurricanes responsible for specific power outages. However, it is important to note that not all power outages can be attributed to hurricanes. Some outages may result from facility maintenance or other natural disasters.
Consequently, if a particular power outage is not caused by a hurricane, it is reasonable for the corresponding cell in the hurricane column to be missing. Incorporating an additional column, such as one that records the amount of rainfall during the corresponding time period, could provide further context. For instance, if the rainfall amount is significantly higher than usual, it is more likely that a hurricane is responsible for the power outage, and thus, the hurricane name column would be shown as `NaN`.

## Missingness Dependency Test 1
In this test, we try to find out if the missingness in `CUSTOMERS.AFFECTED` column is depend on the the column `CAUSE.CATEGORY` or not. The `CUSTOMERS.AFFECTED` column signifies the number of individuals impacted by each power outage event, while the `CAUSE.CATEGORY` column categorizes the specific cause behind these power outages. Prior to commencing our analysis, it is important to examine the patterns and characteristics of the missing data distribution.

<iframe src="assets/missing_observed_graph1.html" width=800 height=600 frameBorder=0></iframe>

The graphical representation of the data reveals a limited number of cause categories, including `severe weather` and `public appeal`. Interestingly, a substantial proportion of power outages associated with missing `CUSTOMERS.AFFECTED` values can be attributed to `intentional attack`. Conversely, instances where the `CUSTOMERS.AFFECTED` value is present predominantly align with power outages caused by `severe weather`. To further ascertain whether the missingness follows a Missing at Random (MAR) pattern, we employ a Total Variation Distance (TVD) test following the permutation of the `CUSTOMERS.AFFECTED` column. TVD is selected due to the existence of a few cause categories, allowing us to assess the discrepancies between each category for the missing and non-missing groups. A significance level of 0.01 is employed, and the test is iterated 1000 times, yielding the following results:

<iframe src="assets/missing_tvd_tested_graph1.html" width=800 height=600 frameBorder=0></iframe>

We get the p-value of 0! , and from the graph we can see that the red line and the distribution of the test result are in the two different world. This disparity strongly indicates that the missingness in the `CUSTOMERS.AFFECTED` column follows a Missing at Random (MAR) pattern. The evident distinction between the red line and the test result distribution further supports this conclusion. It becomes evident that the `CAUSE.CATEGORY` column provides valuable insights into the likelihood of missingness within the `CUSTOMERS.AFFECTED` column.

## Missingness Dependency Test 2
In this test, we try to find out if the missingness in `CUSTOMERS.AFFECTED` column is depend on the the column `TOTAL.PRICE` or not. The `TOTAL.PRICE` column categorizes the overall electricity price for each region which endured the power outage at that time (the unit is cents / kilowatt-hour). Prior to commencing our analysis, lets take a look of data distribution again:

<iframe src="assets/missing_ks_observed_graph.html" width=800 height=600 frameBorder=0></iframe>

Observing the graphical representation, it becomes apparent that the two graphs exhibit similar patterns. However, in order to further evaluate the comparison between the distribution of the price and its proportion, we employ the Kolmogorov-Smirnov (KS) test statistic following the permutation of the `CUSTOMERS.AFFECTED` column. The selection of KS is motivated by the desire to assess the similarity of the two groups' distributions, as they are situated within a similar range on the x-axis. By setting a significance level of 0.01, we iterate the test 1000 times, leading to the following results:

<iframe src="assets/missing_ks_tested_graph.html" width=800 height=600 frameBorder=0></iframe>

Based on our testing, the obtained p-value is approximately 0.2 (with slight variability upon each code run), surpassing our predetermined significance level. Consequently, we can confidently conclude that there is no significant relationship between the missingness in the `CUSTOMERS.AFFECTED` column and the `TOTAL.PRICE` column. 

---

# Hypothesis Testing
## Hypothesis Testing with column *OUTAGE.DURATION*
Introduction: Our research question encompasses two main aspects. The first part seeks to understand the influence of demographic factors on the duration of power outages in West  states. To investigate this, we focus on two key columns: `CLIMATE.REGION` and `OUTAGE.DURATION`. The `CLIMATE.REGION` column provides information on the demographic location of each power outage event, while `OUTAGE.DURATION` indicates the length of time for each outage. Our approach begins by selecting data specifically related to the `west` climate region. We then employ hypothesis testing to assess whether being located in the West region results in different outage durations compared to the entire nation. By calculating the mean duration of outages in the West region and comparing it to the mean duration of outages across the entire country, we are able to discern notable differences. Specifically, we find that outage durations in the West region are shorter than those experienced nationwide, thereby helping to establish our null and alternative hypotheses.

**Null Hypothesis**: There is no siginificant difference between outage durations in the West region and those experienced nationwide.

**Alternative Hypothesis**: Outage durations in the West region are shorter than those experienced nationwide.

Hypothesis test & test statistics : The approach we use is that we will randomly select n rows from teh whole data set, n is the number of outage happened in west region, and calculate the means. Our test statistics is mean of the duration of the random slected rows, and we will compared it with our observed statistic (1628.33 min). The cutoff value is 0.01. 

After repeating the test 10000 times, here is what we get:
<iframe src="assets/fig_hyp1_duration.html" width=800 height=600 frameBorder=0></iframe>

Our P value is aound (0.0004), we can reject the null hypothesis and conclude that outage durations in the West region are shorter than those experienced nationwide. We are expcted to have a shorter duration of power outage if we are in the west!

## Hypothesis Testing with column *CUSTOMER.AFFECTED*

Introducton: The second part of our research question is to understand the influence of demographic factors on the population affected on each outage. In another words, we are interested at figure out if each outage happened in the west affect more people compared with the the area of the whole country, since it seems like there are lot of people densed aread in the west. Similar with the previous one, our approach begins by selecting data specifically related to the `west` climate region. By calculating the number of people affected in the West region and comparing it to the mnumber across the entire country, we are able to discern notable differences.

**Null Hypothesis**: The number of people affected by power outages on the West region has no siginificant difference with all regions of the country.

**Alternative Hypothesis**: Compared to the entire country, power outages in the West region affect more people.

Hypothesis test & test statistics : Same as previous one, the approach we use is that we will randomly select n rows from teh whole data set, n is the number of outage happened in west region, and calculate the means of people being affexted. Our test statistics is mean of the population of the random slected rows, and we will compared it with our observed statistic (194579.89). The cutoff value is 0.01. 

After repeating the test 10000 times, here is what we get:
<iframe src="assets/fig_hyp2_affected.html" width=800 height=600 frameBorder=0></iframe>

Our p-value is aound (0.015), even though it is close, but we can not reject our null hypothesis and can not conclude that the outage happend in the west region affect more people compared with all of the regions in the US. 

---

# Conclusion
Overall, as we looked and analyzed through this dataset, we find out that the `CLIMATE.REGION` with the value of 'West' only contains the `U.S._STATE` of California and Neveda using `value_counts()`. After analyzing the relationship between columns and hypothesis testing on these two west-region states, we are able to carry out several mitigation strategies:

- California:

1. Enhancing infrastructure resilience: Invest in modernizing and strengthening the power grid infrastructure, including upgrading transmission and distribution systems, implementing smart grid technologies, and enhancing backup power systems.

2. Implementing vegetation management programs: Establish robust vegetation management programs to prevent wildfires caused by contact between vegetation and power lines. Regularly inspect and trim trees near power lines to minimize the risk of outages caused by falling branches or wildfires.

3. Diversifying energy sources: Promote the development and adoption of renewable energy sources such as solar and wind power, along with energy storage solutions. This diversification can reduce reliance on centralized power generation and improve grid stability during extreme weather events.

4. Enhancing communication and coordination: Improve communication and coordination among utility companies, emergency management agencies, and local communities to ensure timely response and efficient restoration efforts during outages. This includes public awareness campaigns, community emergency preparedness initiatives, and clear communication channels.

- Nevada:

1. Implementing grid modernization: Upgrade and modernize the power grid infrastructure, incorporating advanced technologies for monitoring and managing the grid in real-time. This includes deploying sensors, automation systems, and smart meters to detect and respond to outages more efficiently.

2. Strengthening infrastructure against extreme weather: Evaluate and reinforce infrastructure to withstand extreme weather events, such as high winds or heavy snowfall. This includes proactive maintenance of power lines, transformers, and substations to minimize the risk of failures during adverse weather conditions.

3. Enhancing backup power capabilities: Encourage the installation of backup power systems, such as distributed energy resources (DERs) and microgrids, in critical facilities and vulnerable areas. These systems can provide localized power supply during outages, improving resiliency and reducing the impact on essential services.

4. Promoting energy efficiency and demand response: Implement energy efficiency programs to reduce overall energy demand and peak load. Encourage participation in demand response initiatives, where consumers voluntarily reduce electricity usage during periods of high demand, thereby reducing strain on the grid and the likelihood of outages.

---