**Why do friendships matter?**

Our society tends to place an emphasis on romantic relationships and we think that just finding that right person will make us happy and fulfilled. But research shows that friends are actually even more important to our psychological welfare. Friendships have a huge impact on your mental health and happiness. Good friends relieve stress, provide comfort and joy, and prevent loneliness and isolation. Developing close friendships can also have a powerful impact on your physical health. Friends are even tied to longevity, since a Swedish study found that along with physical activity, maintaining a rich network of friends can add significant years to your life. A lack of social connection however may pose as much of a risk as smoking, drinking too much, or leading a sedentary lifestyle. But you can't make friendships out of thin air. Many of us struggle to meet people and develop quality connections. Whatever your age or circumstances, it’s never too late to make new friends and greatly improve your social life, emotional health, and overall well-being. 

**What would your approach to making new friends be?** 

There are countless psychological guides on how to make friends. And undoubtedly this is an essential aspect when approaching new people. But what if it's not just your social skills that determine whether you make friends? What if you could multiply your chances of making friends and vastly increase your friendship network by moving to a certain place? At a certain time of the year?

Our research is concerned with exactly these external factors that influence our social network. We have looked at two **location-based social network** data sets. The users of those networks have checked in to various locations all over the world between April 2008 and October 2010. For each check-in, we know the geographical location, the exact time, the user and all the friends of the user. Based on these check-ins, we could compute the home location of each user and whether or not a check-in was a visit to a friend or not. We will use this data as an unconventional approach to investigate friendship across time and space, providing insights about the external factors that determine someone's social cirlce, like the place of residence and the time of the year.

Let's start inspecting the home locations of our users. To calculate it, we discretised the world in 25x25 km cells, took all the checkins of each user and calculated the home location as the average of all checkins in the most frequently visited cell. This gives us a 85% accuracy of the true user's home location:

{% include world_checkins.html %}

We can see that the users are from all over the world, but a majority lives in either the US or Europe. To be precise, 81281 users live in the US and 76497 somewhere else. This is why in our later analysis, we will make a distinction between US and non-US users in order to not bias our results.


<h2>The spacial dimension</h2>

There are plenty of spacial factors that can determine how many friends you have. Do you live in a rural or urban area? How well are the people in general connected at your place of residence?

**Are inhabitants of urban cities more likely to have friends than inhabitants of rural areas?**

We will start with investigating whether inhabitants of urban cities are more likely to have friends than inhabitants of rural areas. In order to do so, we have to define what a city is. The [UN Statistical Commission](https://blogs.worldbank.org/sustainablecities/how-do-we-define-cities-towns-and-rural-areas) endorsed the Degree of Urbanization stating that cities are settlements which have a population of at least 50,000 inhabitants in contiguous dense grid cells (>1,500 inhabitants per km^2). Applying this criteria, we are left with 1256 non-US cities and 328 US cities.

{% include world_cities.html %}

The next step is to compute whether a citizen lives in a city, which we will do by checking the distance to all cities of the home country of the user. Intuitively, the user lives in a city if the distance to at least on of them is smaller than the expansion of the respective city. Afterwards, we can compute the amount of friends per urban and rural user. For the **Non-US citizens** we get the following table of results:

{% include urban_rural_friends_non_US.html %}

First, we can observe that in general more people live in rural areas than in cities. Each person has at least one friend and 75% at least 9 or 10. The difference arises only in the maximum number of friends. Some users that live in cities have an incredible high number of friends, i.e. up to 1458. For users that live in rural areas, the maximum number of friends is 1066. Let's look at the distribution of friends of Non-US citizens, to visualise these results.

{% include urban_rural_friends_non_US_distribution.html %}

We see the same as in the table, the distributions of friends are more or less the same, but for users living urban there are more extreme numbers of friends. This indicates that living in a city outside the US does not necessarily increase your chances of having more friends! What about the US then? Should we move to the US if we want to increase the amount of friends we have?

To get a first grasp how the situtation looks like for **US citizens**, we look at the table of results.

{% include urban_rural_friends_US.html %}

Again, more people live in rural areas than in cities and the characteristics differ only in the maximum number of friends, which are higher for urban users. Plotting the distribution, we can see clearly that they are more or less the same, but for users living urban there are more extreme numbers of friends.

{% include urban_rural_friends_US_distribution.html %}

Living in the US or not, urban users have the same amount of friends than rural users. So when deciding where to live to increase your chances of having more friends, it does not matter whether you move to a rural or urban area. 

--------------------------------------

**Investigating the structure of the social networks**

We have discovered that the number of friends does not differ much between urban and rural inhabitants. An interesting follow up would be to look at how the friendship network is structured, can we detect communities that correspond to the geographical location of the users?

To investigate this question we used a community detection algorithm on the friendship graph. There are a number of different community detection algorithms, however, due to the size of the data sets we had to restrict ourselves to algorithms that run in near linear time. We settled for the walktrap algorithm (http://arxiv.org/abs/physics/0512106). The algorithm tries to find densely connected subgraphs by performing random walks. The idea is that short random walks tend to stay in the same community.

We also decided to only use US check-ins. This is because we were mostly interested in seeing how cities are distributed in these clusters and introducing country borders would make things much more complicated. 

What we discovered is that, for both data sets, the largest cluster had a pretty even distribution of cities. There was no city clearly dominating. Whats interesting about this is that it many users are quite tightly connected, despite great distances separating them. The largest cluster for the brightkite data set can be seen below.

{% include B1_us.html %}

However, for the smaller clusters there was almost always one city clearly dominating. 
Another observation we made is that some of the largest cities, such as New York and Los Angeles, were quite strongly represented in all clusters, but never dominated. In most clusters where more than 40 % of users were from one city, the city was a bit smaller. In the examples below we show the third and fifth largest clusters for brightkite.

{% include B3_us.html %}

The third largest cluster in the brightkite data set, which is dominated by users living in Denver and Boulder, CO.

{% include B5_us.html %}

The fifth largest cluster in the brightkite data set, which is dominated by users living in Phoenix, AZ.

--------------------------------------


TODO: Devrim: what about RQ4?
4. How does the interconnection between countries/continents differ? Does it depend on the language or religion?

**Non-US citizens**

**US citizens**




--------------------------------------


<h2>The temporal dimension</h2>

Next to the spatial dimension, there is the whole temporal aspect of friendship. When do people visit each other? And how often? Does it depend on whether they live in a city or not or on the season of the year?
We will start do dive into it by inspecting how often users visit each other. Remember, the period where the data was collected is between April 2008 and October 2010, so we will inspect how often users visited each other in this period.

As before we start with the behaviour of the **Non-US citizens**:

{% include Friend_visit_non_US_distribution.html %}

Interestingly enough we can notice that the distribution is approximately trimodal: most people visited their friends very rarely in those 2 1/2 years, between 0 and 500 times, some visited each other around 1000 times, and others even 1500 - 2000 times. This suggests that people have in general either loose or quite intense friendships. But does it depend on whether they live rural or urban?

{% include Friend_visit_non_US_urban.html %}

Here we see quite clearly that there is a difference between people that live urban and those that live rural: users in cities visit each other more than users in rural areas! Moreover, we can say that most of the intense friendships are between people that live in cities, where people in rural areas have more sporadic friendships. Thus if you prefer to have intense friendships, you should definitely consider moving to a city outside of the US. But wait, maybe it is the same pattern for the US? Let's look at all our **US citizens**.


{% include Friend_visit_US_distribution.html  %}

There seems to be a similar pattern present for the users that live in the US: most of them have loose friendships, some are more intense and few are really profound. Again, we investigate which of these users live rural and which live urban.


{% include Friend_visit_US_urban.html  %}

Interestingly enough, tables seem to have turned: for US citizens, the more intense friendships are between users that live in rural areas, where urban users have more sporadic friendships.

Summing up we conclude that if you are a social butterfly and want to have as many loose friendships as possible, you should move to a rural area outside of the US or to a big city inside the US. However if you are interested in deep friendships, you should rather go to a city outside of the US or to the rural areas of the US.


The question that is left unanswered is when do users visit each other? To find this out we will divide each checkin that was a visit to a friend in four categories, one for each season: spring, summer, autumn and winter. Since the seasons change for each site of the globe, we will focus on the checkins of **US citizens**. Thus the months december, january, februrary are winter, march to may are spring, june to august summer and september to november autumn.

TODO insert plot



--------------------------------------

<h2>What about you?</h2>
  
We completed our friendship journey through time and space! 

TODO
  
  



