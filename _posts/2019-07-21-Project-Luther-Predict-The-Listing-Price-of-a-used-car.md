---
layout: post
title: Predict the Listing Price of a Used Car
---

I used to live in a small city in Florida, where public transportation is poor. If I want to go to the mall during weekend, I often have to wait 40 minutes for a bus. Like most people around me, I eventually have to bought a car, a used car. Since then, I always wonder: how much does my car worth now? If I were to buy a new car, which brand holds its value the best? As a data science student, I can finally answer all these questions, by building a model that predict the price of a used car.

## Data Gathering

The next step is to find enough used car data online. On my second week at [Metis](http://thisismetis.com), I have learned basic web scraping with beautiful soup and selenium, so this is a great chance for me to practice my web scraping skills! Web scraping can be time consuming, so my goal is to get only 1000 used car data from Kelley blue book. At such a small training data size, my model can not afford to include too many car brands, so I further limit the car model to Toyota Camry, arguably the best selling midsize car in US. 

The data I obtained almost have a complete description of each car, these includes: numerical features such as the price, year and mileage of the car and categorical features such as: Trim level, which describes extra upgrades to the interior designs and devices of the car, the engine upgrade, accident history, interior and exterior color and so on. After cleaning, I am ready to train a few models. 

## Feature Engineering

The best performing model I built is the second degree polynomial model, the r^2 score is 0.96, but the model I like the most is the vanilla regression model, with as few features as possible. I did the feature selection with LASSO path diagram, see the picture below: 

![LASSO feature selection]({{ site.url }}/images/carlasso.png)

In LARS path, each colored line represents the coefficient associated to a feature in our model, as we tune up the hyper parameter, from right to left, all of the categorical feature quickly get damped out, this tells us only the age and mileage of car has a large impact in a used car's price. We only need these two features in our model.

## Fitting Results

![predict vs actual price]({{ site.url }}/images/carpredict.png)

I plotted the above diagram to see how well the two-feature linear regression model performs on the test data set. In the diagram, every point is the a comparison between predicted and actual price for one car. If we made the perfect prediction, the point will lie on the blue line. Overall the points distributed around the 45 degree line. on the other hand, the r^2 evaluation on test set is 0.91. From both the visual appearance of the diagram and the test score we can tell this model is making good predictions.

## Data Analysis

The advantage of having a model with such simplicity is that, by looking at the coefficients of each feature, we can understand the composition of used car's price: it can be broken down into three parts: base price, annual depreciation and mileage depreciation. My model predict the base price of Toyota Camry to be $21,000. A used Camry will depreciate by its age and mileage, at around $650 per year and $400 per 10,000 miles. A five year old 70,000 mileage Camry will depreciate $3,250 from its age and $2,800 from the mileage, my model predict it worth $14, 950. 

To see which brand of car keeps its value the best, we can compare their depreciation factor. I fitted the same model to a new set of used ford fusion data, and found the main difference between ford fusion and Toyota Camry is that ford fusion has a 40% higher mileage depreciation. We can draw the conclusion that Toyota Camry hold the value better than Ford Fusion.

## Conclusion

I built a vanilla linear regression model that predict a used car's price based on its mileage and age. This model can be trained on small data set yet makes good prediction. From this model we can extract the annual and mileage depreciation factor of different brands and models of cars, this enables us to find the vehicles with the best resell values. 
