---
title: "Spatial Pattern of History Shooting Victims"
date: 2020-12-21T15:34:30-04:00
published: true
tags: [folium, nvplot, interactive map, K-means]
excerpt: "Visualizing the spatial distribution of shooting victims and K-means clustering analysis"
folium-loader:
  folium-chart-1: ["charts/crime_cluster.html", "400"]
  folium-chart-2: ["charts/average_age.html", "400"]
toc: true
toc_sticky: true
---

## Spatial Distribution of Shooting Victims (folium)
Below is an interactive map point out the location of each shooting victim in 2020. One can zoom in and find out nearby shooting victims and the pop out will show date information. With a glance of eye, most of shootings located at middle and southwest of Philadelphia. 

<div id="folium-chart-1"></div>

## Visualizing Number of Victims at a tract scale (hvplot & folium)
Comparing the victims distribution of each year, the hot spot doesn't change too much from 2015 to 2020. Based on the visual obeservation, the high risky area of shrinked from 2019 to 2020. Since the total number of victims surged in 2020, which means victims distribution is highly concentrated this year.(Please [clik][shootings_time] here to see the interactive map)

![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_time.gif)

Comparing the victims distribution by hourly interval, north of downtown is always the hot spot area. From 9 p.m. to 23 p.m., shootings are clustered at the northwest of city. (Please [clik][shootings_hour] here to see the interactive map)

![shootings_hour](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_hour.gif)

Though the count of male victims far exceeds the female, the spatial distribution of two genders show a similar pattern.(Please [clik][shootings_sex] here to see the interactive map)

![shootings_sex](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_sex.gif)

The spatial distribution of different races is significantly different. As we can see, white victims clustered at Upper North, while black victims widely distributed in Upper North, West, Oak Lane and Lower Northeast. (Please [clik][shootings_race] here to see the interactive map)

![shootings_race](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/shootings_race.gif)

Below is a map telling the average age of victims in each tract. In most cases, the average age ranges from 25 to 35. The average is larger in the northeast of Philly. Since there are little victims at Far Northeast. The sample may not sufficient to draw a conclusion.

<div id="folium-chart-2"></div>

## Recognizing the Clusters with K-Means Analysis
```
feature_columns = [
    "lat",
    "lng",
    "Weekday",
    "Hour",
    "Month",
]
features = shootings_clean[feature_columns].copy() 

features.head()
```
![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/k-means.png)

![shootings_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/cluster.png)
