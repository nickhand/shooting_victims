---
title: "Spatial Pattern of Historical Shooting Victims"
date: 2020-12-21T15:34:30-04:00
published: true
tags: [folium, nvplot, interactive map, K-means]
excerpt: "Visualizing the spatial distribution of shooting victims and K-means clustering analysis"
folium-loader:
  folium-chart-1: ["charts/crime_cluster.html", "400"]
  folium-chart-2: ["charts/average_age.html", "400"]
hv-loader:
  shootings-year-chart: "charts/shootings_year.html"
toc: true
toc_sticky: true
---

## Spatial Distribution of Shooting Victims (folium)
Below is an interactive map point out the location of each shooting victim in 2020. One can zoom in and find out nearby shooting victims and the pop out will show date information. With a glance of eye, most of shootings located at middle and southwest of Philadelphia. 

<div id="folium-chart-1"></div>

## Visualizing Number of Victims at a Tract Scale (hvplot & folium)
### Year
Comparing the victims distribution of each year, the hot spot doesn't change too much from 2015 to 2020. Based on the visual obeservation, the high risky area of shrinked from 2019 to 2020. Since the total number of victims surged in 2020, which means victims distribution is highly concentrated this year.(Please [click](https://htmlpreview.github.io/?https://github.com/ihcgnahz/shooting_victims/blob/master/charts/shootings_year.html) here to see the interactive map)

<div id="shootings-year-chart"></div>

![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_time.gif)

### Hour
Comparing the victims distribution by hourly interval, north of downtown is always the hot spot area. From 9 p.m. to 23 p.m., shootings are clustered at the northwest of city. (Please [click](https://htmlpreview.github.io/?https://github.com/ihcgnahz/shooting_victims/blob/master/charts/shootings_hour.html) here to see the interactive map)

![shootings_hour](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_hour.gif)

### Gender
Though the count of male victims far exceeds the female, the spatial distribution of two genders show a similar pattern.(Please [click](https://htmlpreview.github.io/?https://github.com/ihcgnahz/shooting_victims/blob/master/charts/shootings_sex.html) here to see the interactive map)

![shootings_sex](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_sex.gif)

### Race
The spatial distribution of different races is significantly different. As we can see, white victims clustered at Upper North, while black victims widely distributed in Upper North, West, Oak Lane and Lower Northeast. (Please [click](https://htmlpreview.github.io/?https://github.com/ihcgnahz/shooting_victims/blob/master/charts/shootings_race.html) here to see the interactive map)

![shootings_race](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_race.gif)

### Average Age
Below is a map telling the average age of victims in each tract. In most cases, the average age ranges from 25 to 35. The average is larger in the northeast of Philly. Since there are little victims at Far Northeast. The sample may not sufficient to draw a conclusion.

<div id="folium-chart-2"></div>

## Recognizing the Clusters with K-Means Analysis
In the previous section, we made judgment of spatial distribution merely based on the visual observation. In this part, we ran `K-Means` analysis to recognize risky clusters in Philly. Both of spatial and time predictors are selected, including `lat`, `lng`, `Weekday` and `Month`. 
```
feature_columns = [
    "lat",
    "lng",
    "Weekday",
    "Hour",
    "Month",
]
features = shootings_clean[feature_columns].copy() 

```
Top 5 clusters are selected and visualized using `matplotlib`. The average value of time varibales are also calculated.

![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/k-means.png)

Based on the results of 5 clusters. Shootings are more likely to happen at night, wihch corresponds to our previous point of view. The average month is during the summer vacation, which is quite close to the time of George Floyd protests.

![table](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/table.png)

We also plot Top 4 clusters separately. Residents could have a check whether or not their house is close to a cluster according to the base map.

![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/cluster.png)

## Recommendations
- For Citizens
  - Due to safety concerns, it's better to stay at home after 9 p.m., especially for the residents living close to the hot spot area.
  - Since the risk of shootings varied for different time of day, it's better to check the risk of destination before going out.
  - If it is possible, choose a house far from clustering area.
- For Police Department
  - Arrange night patrols and deploy more police forces in high-risk areas.
  - Strengthen safety education for people aged 20 to 35. Recommend reducing travel at night.
  - Raise the defense awareness of residents living close to high-risk neighborhood.
