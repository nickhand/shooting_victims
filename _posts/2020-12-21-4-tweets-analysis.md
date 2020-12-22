---
title: " What are People’s Attitudes towards Gun Violence on Twitter? "
date: 2020-12-19T15:34:30-04:00
published: true
tags: [python, matplotlib, altair, interactive map]
excerpt: "Exploratory analysis of shooting victims"
toc: true
toc_sticky: true
---
##Wrangling Tweets via Twitter API
Code block below shows how we wrangle 1000 recent tweets by querying `Twitter API`. The searching key words includes `#enoughisenough`, `#gunviolence` and `#shootings`. 
```
# collect tweets related to the phillies
search_words = "#enoughisenough OR #gunviolence OR #shootings  -filter:retweets"

# initialize the cursor
cursor = tw.Cursor(api.search,
                   q=search_words,
                   lang="en",
                   tweet_mode='extended')
tweets = [tweet for tweet in cursor.items(1000)]
```
##Data Cleaning
Before counting the frequency of words, a series of cleaning steps are processed:
- Remove url
- Remove stop words and punctuation
- Remove searching words
- Convert all letters to lowercase

Below is a table showing Top 20 common words found in tweets. From `people`, `time`, `need` and `stop`, we infer that most people hold negative point of shooting violence. Gun violence is not a personal issue, but seriously affects social safety and lives of us. 

![common_words](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/common_words.png)

Word cloud is also plotted with Top 200 words using `WordCloud` package. As we can see, recent social events and famous people are also listed in the common words, such as `covid`, `lockdown` and `trump`.

![word_cloud](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/word_cloud.png)

##Sentiment Analysis
Sentiment analysis is conducted with `textblob` packgae. In this section, polarity and subjectivity of tweets are analyzed. Below are some example of polarity sentiment. It's interesting that both of the minimum and maximum polarity tweets expressed negetive attitude to gun violence. 

```
#minimum polarity
'This is against the constitution and against the people’s mandate. The worst ever decision by PM KP Oli. #EnoughIsEnough #NepaliPolitics'

maximum polarity
'@sultanterri @Injustice1987 @LozzaFox @BorisJohnson Great! 👍 well done #EnoughIsEnough'

```
The histogram of polarity is slightly reight skewed, which indicates that more twitter customers express positive sentiment. However, this doesn't prove that they support Gun Violence. As the example tells, some people cheer about the advancement of the anti-violence movement。 

![polarity](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/polarity.png)

Following are examples of minimum and maximum sujectivity. 

```
#minimum subjectivity
'We tried to warn you #WakeUp Look at what is going on #GetAngry Arrest @MattHancock #CrimesAgainstHumanity #EnoughIsEnough'

#maximum subjectivity
'@conorjrogers @carbonlolly Omfg his OWN INTELLIGENCE COMMUNITY is being ignored for his insane delusions. #EnoughIsEnough !!!'
```
A histogram of subjectivity is also plotted. It's right skewed, which means more people express their opinion with subjective words. 

![subjectivity](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/subjectivity.png)

Judging from the scatter plot, there is negative correlation between subjectivity and polarity. It indicates that subjective words are more likely to express negative sentiment.

![correlation](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/polarity_time.png)

Below are two charts showing how polarity and subjectivity varied during different time period. Generally, tweets posted in the morning are more likely to be negative. Majority of tweets talking about Gun Violence are subjective.

![polarity_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/polarity_time.png)

![subjectivity_time](https://raw.githubusercontent.com/ihcgnahz/shooting_victims/master/charts/subjectivity_time.png)
