# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Kaggle Competition - Starter

## Problem Statement

Due to the recent epidemic of West Nile Virus in the Windy City, the Department of Public Health set up a surveillance and control system to help collect data on mosquito numbers, presence of West Nile Virus for captured mosquitos, and weather events.

As part of the Disease And Treatment Agency, division of Societal Cures In Epidemiology and New Creative Engineering (DATA-SCIENCE), we have been tasked to assess the viability of the current spray model, as well as to try and predict occurrence of West Nile Virus in Chicago by training classifier models. This will further refine the current pest management model.

Mosquitoes enjoy wet and warm climates and are most active in temperatures above 80&deg;F. Conversely, when temperatures go below 50&deg;F, mosquitoes go dormant.

The lifecycle for the Culex Pipiens, the most common species of mosquito caught in Chicago, typically range from 2-4 weeks, and even less than a week in the heat of summer.

Our project will seek to:
1. Determine the effectiveness of sprays on the mosquito population
2. Predict the occurence of West Nile Virus
3. Help provide guidelines by which to apply future sprays
4. Conduct a cost benefit analysis on the use of the pesticides in response to the epidemic

After training on the classifier models, the selection of the best model will be guided by the highest ROC-AUC score on the validation set.

## Contents
* Data import, helper functions, cleaning and imputation of missing values
* EDA: Previewing Data and Highlighting Outliers
* Modelling
* Applying our selected model on the Kaggle test set
* Cost-Benefit Analysis and Conclusion

## Executive Summary
TODO: Insert brief writeup on findings


## Dataset

The dataset, along with description, can be found here: [https://www.kaggle.com/c/predict-west-nile-virus/](https://www.kaggle.com/c/predict-west-nile-virus/).


* [`train.csv`](./assets/train.csv): Training set consists of data from 2007, 2009, 2011, and 2013.
* [`test.csv`](./assets/test.csv): Test set consists of data required to predict results for 2008, 2010, 2012, and 2014.
* [`weather.csv`](./assets/weather.csv): Weather data from 2007 to 2014 of 2 stations
* [`spray.csv`](./assets/spray.csv): GIS data of spraying efforts in 2011 and 2013

### Data Dictionary
You can access the data dictionary, split into markdown format [*here*](https://github.com/kkhalis/project_4/blob/master/DataDictionary.md).

You can also access the detailed description of weather info in the Data Dictionary [*here*](https://github.com/kkhalis/project_4/blob/master/assets/noaa_weather_qclcd_documentation.pdf)

## Project Planning
Project Plan Documentation can be found [*here*](https://docs.google.com/spreadsheets/d/1_o3eWrHmSxif5hHflbAwt84u0uXwgWTV/edit#gid=540275792).

## Cost-Benefit Analysis

### Costs

1. Spraying

- [Time of spray](https://www.chicago.gov/city/en/depts/cdph/provdrs/healthy_communities/news/2020/august/city-to-spray-insecticide-thursday-to-kill-mosquitoes.html): Weather permitting, the spraying will begin at dusk on August 13th and continue through the night until approximately 1:00 am, with licensed mosquito abatement technicians in trucks dispensing an ultra-low-volume spray. The material being used to control the adult mosquitoes, Zenivex.


- [Spray rate of Zerivex](https://chicago.cbslocal.com/2017/08/30/spray-mosquitoes-far-south-side-west-nile-prevention/): The chemical used is Zenivex, applied at a rate of 1.5 fluid ounces per acre. That measure is approved by the U.S. EPA to control mosquitoes in outdoor residential and recreational areas.


- [Zerivex cost per acre](file:///C:/Users/caspe/Downloads/Zenivex%20Cost%20Comparison%20Fact%20Sheet.pdf): USD0.67 per acre



- Area of Chicago City: estimated to be 145,300 acres based on Google Search

Based on the above, we assume the cost of spray to be USD $0.67 per acre multiplied by the area of Chicago city, which would be at USD $97,351. This accounts for 1 spraying exercise.

We assume we want to be aggressive and spray every week during the summer months of July, August and September based on our spray effectiveness analysis in the previous notebook, it would cost a total of USD $1,168,212.

For this scenario, we would need to set aside a budget of about USD $1,170,000 to conduct the spraying exercises on an annual basis.

2. Medical Health Costs

- Patients who were hospitalized with acute flaccid paralysis, a partial- to whole-body paralysis caused by WNV infection, had the largest initial and long-term medical costs ([median USD 25,000 and USD 22,000 respectively](https://www.sciencedaily.com/releases/2014/02/140210184713.htm)).


- Number of [human WNV cases](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7241786/) in Chicago region (refer to Table 2): 24 in 2011 and 66 in 2013


- The [CDC site](https://www.cdc.gov/westnile/index.html) shares that while there are no vaccines to prevent or medications to treat WNV in people, about 1 in 5 people who are infected develop a fever and other symptoms and about 1 out of 150 infected people develop a serious, sometimes fatal, illness.  


### Benefits

In a maximum benefit scenario, we assume that due to our aggressive spraying policy, no one contracted the virus.

Conversely, in a scenario where the spray had not been used:

Based on CDC's estimates (1 in 150 people require hospitalization), we assume that 1 person aged 60 and above had contracted the virus and developed a serious illness requiring to be hospitalized. The approximate [economic productivity loss](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3322011/) (referenced from Table 3 in the link) is calculated to be:

The economic productivity loss of 1 person (aged 60 or above) hospitalized is estimated USD 7,500.

We conclude that the prevention of economic productivity loss of USD 7,500 does not justify the spending of USD 1.17 million to spray pesticides.

Based on the analysis above, there were <b>very little benefits</b> of the spraying in 2011 and 2013 due to the pathological nature of the WNV which we have studied so far. Furthermore, referencing back to our previous notebook on the spray data effectiveness analysis, the spray effectiveness is very sensitive to weather patterns.

## Conclusion

In effective pest management, one should consider the use of different spray types and effectiveness, as well as factors influencing the lifecycle of the pest.

When considering only fogging, the typical spray used in residential areas for combating mosquitos, timing of the spray should be strongly considered in reducing a mosquito population due to its time-constrained effectiveness:
1. Timing of rainfall
* Rainfall can have a large impact on the population of mosquitos, with stagnant, trapped water providing fertile breeding ground. In built-up cities such as Chicago, it can be difficult to get rid of all water traps and to completely eliminate sources of stagnant water. Use of fogging 8-10 days after a heavy downpour can be a timely way to eliminate mosquito populations for the day, as they are hatching, and accurately target the spray to its window of maximum effectiveness.

* Spray use should also be avoided when the timing coincides with predictions of rainfall on the day itself. For maximum effectiveness, sprays would have to remain in the air and interact with the mosquito population. Any precipitation during the course of the day would reduce the effectiveness of the spray by taking it out of the air and preventing maximum exposure.

2. Degree Days
* Mosquitos have shown to be most active around a specific temperature band, above 65F, often measured in degree days. When judging appropriate spray effectiveness, degree days can be used to help judge the use and timing of sprays. More days consistently above the 65F band would lead to a faster lifecycle, and a more active population, requiring a more consistent use of spraying. In contrast, we may avoid spraying on cooler days due to the limited effectivness of spraying, particularly when the mosquito population is small. Targeted use specifically in areas that have historically had the West Nile Virus presence can be considered instead.
* In examining our spray data set, sprays have largely been applied in September. This might be one big area of improvement for future spray applications, to shift them towards the summer months, when mosquitos are most active.

3. Wind Speed and Drift
* Wind speed should also be considered on the day of application. Wind speed can cause pesticide drift, removing the pesticide fog from its most effective location. Wind speed of the day should be considered during pesticide application. This is especially important in Chicago, which follows a grid layout, allowing buildings to form wind corridors and exacerbating wind effects.
* Conversely, days with no wind speed can be difficult for spray operators, at speeds below 3km/h, spray can evaporate before arriving at the desired destination of application. A light breeze will provide the operator with the knowledge of the pesticide drift.

4. Sprayer Type
* Sprayer machinery can play an important role in the application of pesticides. A fine nozzle sprayer will help to provide a fine dispersion of the pesticide mist, however, hot days and lower humidity can lead to a faster evaporation of smaller droplets. Conversely, larger particle sizes (>200 microns) may survive the heat and be less affected by wind size, but may not be as effective at delivering the pesticide to pests.

5. Pesticide
* The assumption made is that the spray used is the most commonly use spray for fogging the air and targeting adult mosquitoes. However, standing pesticides can also be used in conjunction with air pesticides, targeting difficult to reach or difficult to clear areas with standing water to eliminate mosquito larvae. This would be a far more long-reaching solution, although constant re-application would be required through each rainfall. Therefore, consideration would have to be given according to the frequency of rainfall and the difficulty of application.

## Recommendations

In conclusion, there were no material benefit to the spraying of pesticides conducted in 2011 and 2013. Therefore, the [best and most economical way](https://www.cdc.gov/westnile/prevention/index.html) to prevent West Nile disease or any other mosquito-borne illness is to reduce the number of mosquitoes around your home and to take personal precautions to avoid mosquito bites. Precautions include:

- When outdoors, apply insect repellent that contains DEET, picaridin, oil of lemon eucalyptus or IR 3535, according to label instructions.
- Wear long-sleeved shirts and long pants when going out
- Make sure doors and windows have tight-fitting screens. Repair or replace screens that have tears or other openings. Try to keep doors and windows shut, especially at night.
- Eliminate sources of water-holding containers that can support mosquito breeding such as tires, buckets, planters, toys, pools, birdbaths, flowerpots, or trash containers
- In communities where there are organized mosquito control programs, contact your municipal government to report areas of stagnant water in roadside ditches, flooded yards and similar locations that may produce mosquitoes.


Presentation slides can be found [*here*](https://docs.google.com/presentation/d/1mcq-PWQ7iOgGA75zJQiJCC4yx7CGViAl/edit?usp=sharing).