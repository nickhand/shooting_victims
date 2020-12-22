---
title: " Do Gun Violence equally threaten the lives in Philly? "
date: 2019-12-11T15:34:30-04:00
published: true
tags: [python, matplotlib, altair, interactive map]
excerpt: "Exploratory analysis of shooting victims"
altair-loader:
  altair-chart-1: "charts/wound.json"
  altair-chart-2: "charts/hour_male.json"
  altair-chart-3: "charts/hour_female.json"
  altair-chart-4: "charts/hour_district.json"
hv-loader:
  hv-chart-1: "charts/shootings_sex.html"
toc: true
toc_sticky: true
---

## Data Cleaning (Pandas)
The open data contains abundant information shootings, including the age, gender, race and wound types of victims, and the location of crimes.
- Raw data downloaded from OpenData Philly contains 8843 records from 2015 to 2020. Considering spatial analysis and visualization, records without coordinates and beyond the boundary of Philadelphia are dropped.
- New columns `Month`,`Hour` and `Weekday` are extracted from `date_`.


## Sum of Victims by Year and Gender/Race (matplotib)

Below is a bar chart accumulating victims by year and gender. Besides the surging of victims from 2019 to 2020, we found number of female victims are growing but still accounts for a small part of the total.

![growth_by_sex](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/growth_by_sex.png)

From the perspective of race, victims are majority Africa American for the first sight. Comparing the slope of line, from 2019 to 2020, the growth rate of Africa American victims is far greater than the growth rate of white.

![growth_by_race](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/growth_by_race.png)

The victims of gun violence are biased across the gender and race, combining the observation of two maps and considering the 0.868 of male-female ratio and 1.23 of the black-white ratio. We assume that black male is the main group of shooting victims.

## Wound Types and Age of Death Victims (altair)

Victims who died from shootings are selected in this analysis. Below is an interactive scatter map plotted by `Altair`, The age of the victims is mainly between 18 to 50 years old. The cause of death mainly came from gunshot wounds on the head, chest and multiple places on the body.

<div id="altair-chart-1"></div>

## Further Exploration from the Perspective of the Gender Difference (altair)
In this part, we try to exlore the distribution of male and femal victims from the dimension of time and police districts. Since the visualizing limitation of 'altair' is 5000 rows. Only shootings in 2020 are selected.

### Sum of Male/Female Victims by Hour

<div id="altair-chart-2"></div>

<div id="altair-chart-3"></div>

<div id="altair-chart-4"></div>

<div id="hv-chart-1"></div>
