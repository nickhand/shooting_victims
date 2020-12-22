---
title: "Background: Gun Violence in Philadelphia"
date: 2020-12-21T20:34:30-04:00
categories:
  - Introduction
tags:
  - Gun Violence
  - Philadelphia
  - Data Resource
excerpt: "A background introduction of gun violence"
altair-loader:
  altair-chart-1: "charts/growth_rate.json"
toc: true
toc_sticky: true
---
## Background
![gun_vio](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/assets/images/gun_vio.jpg)
In the United States, gun symbolizes freedom, but also dangerous. The above illustration from [the New York Times](https://www.nytimes.com/interactive/2017/11/06/opinion/how-to-reduce-shootings.html) accuratly conveys this point. Besides COVID-19 **Gun Violence** is the other pandemic swept Philidelphia in 2020. Admittedly, gun issues have always been a probelm threatening public safety in Philly. Shockingly，influenced by pandemic and the George Floyd protests in June, the number of shooting victims in Philadelphia reached the peak compared with the data of past decades. As the bar chart demonstrates, the growth rate of shooting victims from 2019 to 2020 is **47.1%**. Currently, this city urgently needs insights to prevent constant tragedies.To reasonably distribute plice force and better control the gun violence, data of happened crimes is an essential resource.

<div id="altair-chart-1"></div>

Our project aims to analyze the data of shooting victims and try to answer following questions.

- Do shooting violences influence citizens equally across sex, age and race?
- Time and spatial pattern of history shootings crimes.
- What are people’s attitudes towards Gun Violence on Twitter?

## Data Resource
- [Shooting victims][Shooting victims] from 2015 to 2020 is accessed from OpenData Philly API.
- [Zip codes][Zip codes] and [Census tracts 2010][Census tracts 2010] are downloaded from OpenData Philly via GeoService
- 1000 tweets includes #shootings #gunviolence and #enoughisenough are retrieved through [Twitter API][Twitter API]

For python codes and detailed methods of this project, please click [here][here].
   
[Shooting victims]: https://www.opendataphilly.org/dataset/shooting-victims
[Census tracts 2010]: https://www.opendataphilly.org/dataset/census-tracts
[Zip codes]: https://www.opendataphilly.org/dataset/zip-codes
[Twitter API]: https://developer.twitter.com/en/docs
[here]: https://github.com/MUSA-550-Fall-2020/final-project-chi
