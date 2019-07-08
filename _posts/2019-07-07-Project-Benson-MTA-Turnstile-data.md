---
layout: post
title: Project Benson MTA Turnstile Data Analysis
---

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

We recommand WTWY sending street teams to the following stations:
* 34 Street Penn Station
* Time Square 42nd street station
* 42nd street Port Authority station
* 86th street station
* 34th street Herald Square station
during weekdays evening rush hour from 4pm to 8pm. 
