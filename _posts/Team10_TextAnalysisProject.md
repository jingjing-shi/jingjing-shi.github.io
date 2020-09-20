

**Motivation**

<img src="/assets/img/covid_tweets/image1.png" >
<img src="/assets/img/covid_tweets/image2.png" >
<img src="/assets/img/covid_tweets/image3.png" >




**DataSource**

*Covid-19 Twitter Chatter Dataset for Scientific Use*

([PanaceaLab](http://www.panacealab.org/covid19/)

● Data collected from Twitter stream

● Keywords: COVD19, CoronavirusPandemic, COVID-19, covid19, 2019nCoV,CoronaOutbreak, coronavirus, WuhanVirus,coronaviruspandemic, covid-19,2019ncov, coronaoutbreak, wuhanvirus

● Tweet IDs + Timestamps





**Data Processing**

● 24.7 million tweets that tweeted after March 1st to April 7th were gathered
● 10% of tweets were hydrated
● 90,000 tweets contained keywords about China

**Sentiment Model**

● A deep learning model that labels texts with their likelihoods of containing comments that fall into any of the following categories: severely toxic, identity attack, insult and threat was trained. 

● The model was trained on an annotated comments dataset provided by Jigsaw's conversation AI team.
	● Information about the labeling schema used to create that dataset is available on the dataset's webpage.
	● The model scored an average of 0.98 AUC score across the labels.C
	
**Results**

*Overall Trends in Coronavirus Tweets*

<img src="/assets/img/covid_tweets/image4.png" >
*Tweets Related to China Were More Negative*

<img src="/assets/img/covid_tweets/image5.png" >
*Tweets from Users With Default Profile Pictures Were Also More Negative*
<img src="/assets/img/covid_tweets/image5.png" >
