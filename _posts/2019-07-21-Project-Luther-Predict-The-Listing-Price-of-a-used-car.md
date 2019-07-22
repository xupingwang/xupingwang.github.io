---
layout: post
title: Project Luther Predict the Listing Price of a Used Car
---

I used to live in a small city in Florida, where public transportation is poor. If I want to go to the mall during weekend, I often have to wait 40 minutes for a bus. Like most people around me, I eventually have to bought a car, a used car. Since then, I always wonder: how much does my car worth now? If I were to buy a new car, which brand holds its value the best? As a data science student, I can finally answer all these questions, by building a model that predict the price of a used car.

## Data Gathering and EDA

The next step is to find enough used car data online. On my second week at [Metis](http://thisismetis.com), I have learned basic web scraping with beautiful soup and selenium, so this is a great chance for me to practice my web scraping skills! Web scraping can be time consuming, so my goal is to get only 1000 used car data from Kelley blue book. At such a small training data size, my model can not afford to include too many car brands, so I further limit the car model to Toyota Camry, arguably the best selling midsize car in US. 

The data I obtained almost have a complete description of each car, these includes: numerical features such as the price, year and mileage of the car and categorical features such as: Trim level, which describes extra upgrades to the interior designs and devices of the car, the engine upgrade, accident history, interior and exterior color and so on. After some cleaning, I fit a few models to the data. 

## Data Analysis



The baseline model with all features works very well, but I wanted to reduce the complexity of my model. And keep only the features that has large impact on the car price. I plotted the LARS path diagram. Each colored line represents the coefficient associated to a feature in our model, as we tune up the hyper parameter, from right to left, all of the categorical feature get damped out, leaving only age and mileage of the car in our final model. 

I plotted the next diagram to see how well our model performs. In the diagram, every point is the a comparison between predicted and actual price for one car. If we made the perfect prediction, the point will lie on the blue line. Overall the points distributed around the 45 degree line. Visually this model is making good predictions. I have also compute the r square score, which measures how well the 

The simplicity of my model make it possible for us to look directly at the equation and gain insight out of it. The price for a used Toyota Camry consist of three parts: a base price. 




















This is the my first week at [Metis](http://thisismetis.com) as a data science student. In the first project, my teammates and I take on the role of data scientists, to help our client, a fictional organization WTWY, to figure out the time and subway stations to place their volunteers, and collect as many signature as possible in front of the subway station.

## Data and Method

Due to the short amount of time given for the first project, we decided to work mostly on [MTA turnstile data](http://web.mta.info/developers/turnstile.html). We look for top stations in terms of entries count, and find out the day of week that has the most ridership. We believe the sheer size of passenger flow will help the street team achieve their goal.

## Result

![Image test]({{ site.url }}/images/topstations.png)

Our first plot shows the top five stations in terms of average ridership over 5 week's period. These are sub way stations at Penn station, times square, port authority, 86th street and Herald square. We recommand placing volunteers at these five stations for the best result. 

![Image test]({{ site.url }}/images/mtadaily.png)

The next question is, which day of week is the best? To see if weekday and weekend make any differences to the traffic count, we add up entry count statistics from all stations and group by different days of the week. From the diagram we find the traffic count during weekdays are consistanly higher than the weekend's. We suggest sending volunteers only on weekdays. 

![Image test]({{ site.url }}/images/fourhour.png)

The last question we can answer is: what is the best time in each weekday for the volunteers to do their work? In the third plot we trace the station averge entry count in a typical day. The traffic volume is the lowest in the midnight, then increases steadily till noon, it peaks during the evening rush hour then drop to minimun again at next day's midnight. The time we suggest is 4pm to 8pm.

## Conclusion

We recommand WTWY send out street teams on weekdays, during evening rush hour from 4pm to 8pm, to the following stations:
* 34 Street Penn Station
* Time Square 42nd street station
* 42nd street Port Authority station
* 86th street station
* 34th street Herald Square station
