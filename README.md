# Tableau Dashboards: Starbucks Popularity in the USA and Drinks' Nutrition Comparison
###### Author: Avianna Bui 

[Link to Tableau dashboard](https://public.tableau.com/shared/F7MFBWZ9P?:display_count=n&:origin=viz_share_link) 

## Introduction and Data Context
Starbucks is the largest coffee chain in the United States regarding physical units, with over 15,000 stores in the U.S. in 2022 (Statista Research Department, 2023). Due to this immense popularity, I started the project with the overarching goal to examine the coffee giant's influence on the quality of life in the U.S.
 
Since the Starbucks API is not public, I resorted to working with publicly available datasets I found online. I used [Kaggle’s Starbucks Store Location 2023](https://www.kaggle.com/datasets/omarsobhy14/starbucks-store-location-2023/data) to create a dashboard examining Starbucks’ popularity by U.S. states and cities, which I joined with the [2019 Census US Population Data By State](https://www.kaggle.com/datasets/peretzcohen/2019-census-us-population-data-by-state) on Kaggle to calculate the store density metric for my analysis. 

I also used the [Official Starbucks Nutritional Dataset](https://github.com/rfordatascience/tidytuesday/blob/master/data/2021/2021-12-21/readme.md) on Tidy Tuesday, which contains nutritional information on every Starbucks’ drinks found in the Starbucks Coffee Company Beverage Nutrition Information, to create a dashboard in which users can compare nutritional values of different Starbucks’ drinks. Finally, I included a Statista’s dataset on state-wise [Heart Disease Death Rates in the United States in 2021](https://www.statista.com/statistics/320799/top-us-states-by-heart-disease-deaths/) to explore the tentative relationship between Starbucks’ popularity and cardiovascular health. Circulatory health was selected as a measure for analysis because based on my exploratory data analysis, which I will further discuss in the next section, many Starbucks drinks are unhealthy for our heart. Combined with the fact that heart disease is the leading cause of death in the U.S. (CDC, 2023), investigating Starbucks’ popularity and nutritional values might help inform people within highly popular Starbucks locations to be more conscious about their drink selections. 

## Data Story and Technical Discussion
As previously mentioned, Starbucks is extremely unhealthy for our cardiovascular system. When I performed exploratory data analysis on the datasets, I created an interactive dot plot displaying how every Starbucks drink of different sizes varies in nutritional values (caffeine, cholesterol, sugar, saturated fat, and trans fat) to examine their impact on well-being. 

To contextualize the “healthy level” of these drinks, I included a red reference line marking each selected nutrient's recommended daily intake. Specifically, the Food and Drug Administration recommends consuming under 400mg of caffeine per day (FDA, 2023), and those with heart disease risk factors should limit their cholesterol intake to 200mg/day (HHS, 2020). Meanwhile, according to the American Heart Association, the daily recommended sugar intake should be limited to 31mg on average for males and females (AHA). When it comes to saturated fat and trans fat, their suggested daily intake are respectively 5-6% (AHA, 2021) and <1% (WHO, 2018) of the total daily calorie consumption. With a 2,000-calorie diet, that means consuming around 11g of saturated fat and 2g of trans fat a day. 

To switch between different nutritional categories, users can click on the table above the dot plot that summarizes the average nutritional value of all drinks. Users should select a nutritional category before examining the plot. As demonstrated in the visualization, several venti drinks exceeded the recommended caffeine intake for a day. More importantly, over half of Starbucks drinks exceeded the recommended daily sugar intake and many contain a high amount of saturated fat (over 5g). When one takes into account every food they consume in a day, such a level of saturated fat is simply too high for one coffee. 

<p align="center">
  <img src="images/pic5.png">
  <em>Over half of Starbucks drinks exceeded the recommended daily sugar intake</em>
</p>

<p align="center">
  <img src="images/pic6.png">
  <em>Many Starbucks drinks have >5g of saturated fat. Combined with other products containing saturated fat that one consumes in a day (e.g. bacon, cheese, ice cream, etc.), one’s diet risks exceeding the recommended daily saturated fat intake</em>
</p>

With this in mind, I moved to examine Starbucks's popularity within each U.S. state and across cities. The assumption is that if Starbucks is unhealthy, people residing in places with greater Starbucks popularity would benefit more from being conscious of their drink choices. 

<p align="center">
  <img src="images/pic1.png">
  <em>Interactive dashboard with Starbucks’ popularity by U.S. state and cities</em>
</p>

To provide a broad depiction of Starbucks' popularity within the U.S., I created a choropleth map with each state colored by Starbucks’ popularity score. The first measure I use to quantify Starbucks’ popularity is store count: looking at the map, it is apparent that California is the state with the highest number of Starbucks stores. However, since the number of stores in a state is greatly influenced by its population size, density, and area, I added a second popularity metric of store density: namely, the state population (in thousands) served by 1 store. In this case, a lower score indicates a greater store density and thus popularity, because a low value suggests that Starbucks invests in more stores within a wider population. Users can select the popularity score they want to display on the U.S. map using the drop-down menu at the upper right corner of the map. 

To aid quicker interpretation, to the right of the map, there is a bar graph depicting the 10 U.S. states with the highest Starbucks store count. The bars are colored pink if the state is also one of the top 10 states regarding store density, and colored grey otherwise. There are only five U.S. states with both a high Starbucks store count and density, indicating a more reliable Starbucks popularity level: California, Washington, Arizona, Colorado, and Virginia. For the remaining states, their high store count might be due to their populous or touristic nature, or due to their large area. 

The map also displays points with each dot representing a city, colored by their majority ownership type (blue for company-owned stores, orange for licensed stores). The majority of Starbucks stores are company-owned, with these stores concentrating in urban areas while licensed store tends to be more spaced out in less crowded places. This makes sense from a strategic business standpoint: the company would want to target investment in metropolitan, high-population areas for greater profits. 
Because Starbucks stores are concentrated in urban regions, it is worth examining Starbucks’ popularity on a city level as well. Under the map and bar graph, I visualized a treemap that presents the cities with the highest store count, with more “popular” cities allotted a bigger size and deeper color in the graph. The five US cities with the greatest number of Starbucks stores are New York, Chicago, Seattle, Houston, and Las Vegas. To facilitate user exploration, I included a filter at the upper right of the treemap where users can type in the number of cities they want to include in the treemap, with the maximum value being 30 cities to avoid overcrowding the plot. The type-in format was selected rather than a slider to allow for better accuracy. In addition, the visualizations on the dashboard are linked, so users can one or more states from the U.S. state map, and the treemap would be modified to include only the cities with high Starbucks popularity within the selected state(s).

<p align="center">
  <img src="images/pic2.png">
  <em>Users can modify the number of cities included in the treemap, and filter the displayed cities by selecting state(s) on the map</em>
</p>

As I examined Starbucks’ popularity in connection with cardiovascular health, Nevada stood out as the only state with both a high Starbucks store density and a high rate of cardiac death, with “high” means being in the top 10 states for the category. 

<p align="center">
  <img src="images/pic3.png">
  <em>Nevada has both a high Starbucks store density and a high rate of cardiac death</em>
</p>

While the reason for this connection requires further in-depth investigation, those residing in Nevada, especially in Las Vegas (since it has the fifth highest Starbucks store count in the U.S.) would be more likely to benefit from a heightened awareness of the nutrition contained in their Starbucks order. To foster nutritional awareness of Starbucks drinks, I created an interactive dashboard that enables users to select their go-to Starbucks order and compare the nutritional values of their favorite drinks. 

<p align="center">
  <img src="images/pic4.png">
  <em>Interactive dashboard to compare nutritional values of different Starbucks drinks</em>
</p>

The dashboard utilizes the same dot plot and the table with an aggregated summary of different nutritional values that I described at the beginning of this section. However, I included a multiple-value, tab filter to the right side of the dashboard where users can select the drinks they want to display in the dot plot. I selected this tab format rather than a drop-down list because it simplifies the interaction from a 2-click process (in a dropdown) into a 1-click process for user selection. Since I expect the users to change the filter often to explore multiple drinks, reducing the number of clicks required to access the filters could improve time efficiency and usability. Different drinks are differentiated with different colors, and Tableau’s default tooltip means users can hover over each dot to see which drink the dot represents and its detailed nutrient value, allowing me to remove the color legend from the dashboard to give space for more necessary components without compromising information.  This details-on-demand interaction is especially useful in this case since color remains the most optimal choice to encode different drinks: it is not feasible to display all drinks on either the x- or y-axis due to space constraints, while color is the second best method to encode categorical data after spatial region (Munzner, 102). 

## Summary of Findings
When it comes to Starbucks’ popularity within the United States, California, Washington, Arizona, Colorado, and Virginia are the five states with both a high store count and store density. In addition, Starbucks stores tend to be concentrated around major metropolitan areas, with the majority of these stores being owned by the company rather than licensed to a third party. 

Many Starbucks drinks exceed or come close to the recommended daily nutritional intake of caffeine, sugar, and saturated fat, which is detrimental to cardiovascular health. As a result, it would be beneficial health-wise to be more conscious about the amount of nutrition contained in your Starbucks order. Those living in states and cities with high Starbucks popularity might benefit more from this awareness since they would be more likely to order from the coffee giant, especially for people in Nevada, which has a high Starbucks store density (for Nevada), high store count (for Las Vegas), and a high rate of death caused by heart disease. 

## Limitations 
Due to the limiting nature of publicly accessible data, the datasets I use within the scope of this project are collected and thus display numbers from different years. While the data for Starbucks’ store location is quite up to date as it was collected in 2023, the state population data came from the 2019 Census, whereas the Starbucks drink dataset only reflected its 2021 menu version. As a result, there would be discrepancies between the representation of results in this project and the actual number. In addition, there is no data for city population. For future implementations of this project, it would be interesting to collect city population data to examine the store density metric on a city-wide level.  

Furthermore, the project does not establish a direct relationship between Starbucks’ popularity and cardiovascular health. Claiming any definitive link without further investigation would be immensely reductive since circulatory health depends on a multitudinous number of factors such as socioeconomic status, education, genetic factors, diet preferences, etc. 

Most importantly, I want to emphasize that different individuals have diverse nutritional needs. It is neither feasible nor inclusive to apply a single number as a “universal” quota for daily intake of any nutrition without accounting for one’s dietary needs, gender, weight, energy needs, etc. The recommended daily intake numbers I use for the Starbucks’ nutrition dashboard are not meant to suggest any definite amount of nutrition that one should or should not consume, but merely act as a reference and means of contextualization so users can be more informed about their drink choices. 

## Bibliography
American Heart Association. “How much sugar is too much?”. Accessed December 23, 2023. https://www.heart.org/en/healthy-living/healthy-eating/eat-smart/sugar/how-much-sugar-is-too-much# 

American Heart Association. (2021). “Saturated Fat”. Accessed December 23, 2023. https://www.heart.org/en/healthy-living/healthy-eating/eat-smart/fats/saturated-fats 

Centers for Disease Control and Prevention. (2023). FastStats - Leading Causes of Death. Accessed December 23, 2023. https://www.cdc.gov/nchs/fastats/leading-causes-of-death.htm 

Cohen, P. (2020). 2019 Census US Population Data By State. Retrieved November 21, 2023. https://www.kaggle.com/datasets/peretzcohen/2019-census-us-population-data-by-state 

Elflein, J. (2023). Heart disease death rates in the United States in 2021, by state. Retrieved December 2, 2023. https://www.statista.com/statistics/320799/top-us-states-by-heart-disease-deaths/

Munzner, T. (2014). “Visualization Analysis and Design”. A K Peters Visualization Series, CRC Press, 2014. https://www.cs.ubc.ca/~tmm/vadbook/ 

Sobhy, O. (2023). Starbucks Store Location 2023: Coffee Giant Growth. Retrieved October 30, 2023. https://www.kaggle.com/datasets/omarsobhy14/starbucks-store-location-2023/data

Statista Research Department. (2023). Number of units of leading coffee shop chains in the U.S. 2022. Accessed December 23, 2023. https://www.statista.com/statistics/920174/number-of-units-of-selected-leading-coffee-house-and-cafe-chains-in-the-us/

Tidy Tuesday. (2021). Official Starbucks Nutritional dataset from Starbucks Coffee Company Beverage Nutrition Information. Retrieved October 15, 2023. https://github.com/rfordatascience/tidytuesday/blob/master/data/2021/2021-12-21/readme.md 

US Department of Health and Human Services. (2020). 2020-2025 Dietary Guidelines for Americans. Accessed December 23, 2023. https://www.dietaryguidelines.gov/sites/default/files/2020-12/Dietary_Guidelines_for_Americans_2020-2025.pdf 

U.S. Food and Drug Administration. (2023). “Spilling the Beans: How Much Caffeine Is Too Much?” Accessed December 23, 2023. www.fda.gov/consumers/consumer-updates/spilling-beans-how-much-caffeine-too-much 

World Health Organization. (2018). “Nutrition: Trans fat”. Accessed December 23, 2023. https://www.who.int/news-room/questions-and-answers/item/nutrition-trans-fat# 
