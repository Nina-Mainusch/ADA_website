**Why do Friendships matter?**

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
The next step is to compute whether a citizen lives in a city, which we will do by checking the distance to all cities of the home country of the user. Intuitively, the user lives in a city if the distance to at least on of them is smaller than the expansion of the respective city. Afterwards, we can compute the amount of friends per urban and rural user. For the **Non-US citizens** we get the following table of results:

{% include urban_rural_friends_non_US.html %}

First, we can observe that in general more people live in rural areas than in cities. Each person has at least one friend and 75% at least 9 or 10. The difference arises only in the maximum number of friends. Some users that live in cities have an incredible high number of friends, i.e. up to 1458. For users that live in rural areas, the maximum number of friends is 1066. Let's look at the distribution of friends of Non-US citizens, to visualise these results.

{% include urban_rural_friends_non_US_distribution.html %}

We see the same as in the table, the distributions of friends are more or less the same, but for users living urban there are more extreme numbers of friends. This indicates that living in a city outside the US does not necessarily increase your chances of having more friends! What about the US then? Should we move to the US if we want to increase the amount of friends we have?

To get a first grasp how the situtation looks like for **US citizens**, we look at the table of results:Let's check whether the results for  are similar.

{% include urban_rural_friends_US.html %}

{% include urban_rural_friends_US_distribution.html %}


--------------------------------------


TODO Carl:
Transition to Subnetworks, RQ 3
Write a paragraph for the motivation why we did subnetworks, how related to topic, plots
"Can we detect certain loosely connected sub-networks which corresponds to a circle of friends or a city? If yes, what is the probability that a user is part of such a circle of friends?"

**US citizens**:

**Non-US citizens**:


--------------------------------------


TODO: Devrim: what about RQ4?
4. How does the interconnection between countries/continents differ? Does it depend on the language or religion?

**US citizens**

**Non-US citizens**


--------------------------------------


<h2>The temporal dimension</h2>

Next to the spatial dimension, there is the whole temporal aspect of friendship. When do people visit each other? And how often? Does it depend on whether they live in a city or not or on the season of the year?
We will start do dive into it by inspecting how often users visit each other. Remember, the period where the data was collected is between April 2008 and October 2010, so we will inspect how often users visited each other in this period.
 
**US citizens**



**Non-US citizens**





{% include Friend_visit_non_US_distribution.html.html %}

{% include Friend_visit_non_US_urban.html.html %}


--------------------------------------

<h2>What about you?</h2>
  
We completed our friendship journey through time and space! 

TODO
  
  



