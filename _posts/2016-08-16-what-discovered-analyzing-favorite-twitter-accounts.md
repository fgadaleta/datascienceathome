---
layout: post
title: What I discovered by analyzing my favourite Twitter accounts
tags: [analytics, bigdata, data, twitter, data science, visualization]
comments: true
type: post
---

As some might already know, I am a heavy Twitter user. You can find many thoughts of mine, findings and ideas, at least those ones I share with my followers. I also get inspired by the many researchers who, like me, use Twitter on a daily basis.
As a data scientist I constantly analyze my own data, from my Fitbit to my Garmin, emails, documents and of course my Twitter timeline. Which is exactly what I am writing about in this post.

As I am in the process of making a Twitter bot that takes my place when possible - when I am on holiday for instance - I need to know some fundamental info, in order to make the bot behave like a real human, or just being tailored to my own habits. 

Thus, I need to know when do people tweet during the day, when do they reply, how much do they tag their tweets and how long their tweets are. Moreover, I need to collect this information not for the entire Twitter universe, but for the tweets I am interested in and to which the bot will be responding or interacting with.

I know that there are several commercial and free internet services that could collect Twitter statistics. But not at this resolution and so specific to the topic and/or user of my choice. Plus, it’s always fun to make things and see them working.



## Data collection and cleaning

As with any data analytic pipelines, the main ingredient is data, indeed. For this exercise I wrote quite some code, such as a small Twitter client, configured with the API served by [twitter.com](http://www.twitter.com) and fired it up for 9 days, in order to collect 950 thousands tweets about data science, big data and analytics (together with some more tags strictly related to the aforementioned ones).

Then I wrote some code that cleans and normalizes data, doing the usual things from utf-8 decoding to stemming, parsing, and correcting typos, in order to facilitate the analytics engine which I will spin off later on.

At this stage I was already surprised by how dirty public data is and how weirdly people talk, especially on the internet. But stay with me because fun's yet to come.


## Counting and Visualizing


Once data is clean, it is usually ready to be processed for further analysis. I will explain the type of analysis in a later post, when I will also write about my goal. For the time being, let’s just count.
Below are the questions I asked myself, with their data-driven answers.


### How many tweets at each hour of the day

I wanted to know how many tweets (with all my specific conditions, such as topics, and users in my timeline) get generated during the day. If an image is worth thousand words, a barchart is much more. 
Below is a picture of how the aforementioned tweets are distributed during the hours of the day. 
All the days of the week are considered as equal. Many will not agree with this assumption. But it would be quite straightforward to do otherwise. 

As you can see from the picture below, most of the tweets are generated between 2 and 4 PM (Brussels time).

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/tweets_hour.png" />


Other two pictures that complete the story are the distribution of the number of **tags** per tweet

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/num_tweets_tag.png" />

and the distribution of the number of **replies** per tweet

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/num_tweets_reply.png" />




### How many replies at each hour of the day

The second piece of information comes from another picture, in which I count how many times do people reply during the day. Surprisingly, it’s not when the most of the tweets are generated. But at 8PM. 
Did you know that?

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/replies_hour.png" />



### How many tagging tweets at each hour of the day

Then I became even more curious and asked myself *“when do people tag during the day?”* 
The answer comes from the picture below, around 8 PM, even though at a smaller rate than the one to which people reply.

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/tagged_hour.png" />



### What is the average length at each hour of the day

Finally, how much do people type during the day. I mean how many characters are there in a tweet at the different hours of the day. It seems that there is no particular preference for people to tweet shorter or longer. They usually do it at an average length of 134 characters, squeezing the capabilities of Twitter fixed at 140 characters.

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/length_hour.png" />


Despite this limit, however, I visualized the length of 80K tweets sampled from the entire dataset of about 950K, and I got surprised again by the fact that quite a number of tweets exceeded the 140-character limit.
My explanation is due to the expansion of URLs after they got squeezed by URL-shortener services. 
If you find that wrong or have a better explanation, please leave a comment.

<img src="https://s3-eu-west-1.amazonaws.com/wopcontent/uploads/2016/len_distrib.png" />


In a later post I will explain how I used these info and the collected tweets to make the alter ego of Piggy, on Twitter. 

In the mean time... I will enjoy summer!

Happy analytics!

