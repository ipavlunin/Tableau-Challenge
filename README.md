# NY Citi Bike Analytics - Tableau Visualization

## Background

Citi Bike, NYC's official bike share program, was designed to give residents 
and visitors a fun, affordable and convenient alternative to walking, taxis, 
buses and subways.

There are >900 Citi Bike stations across Manhattan, Brooklyn, 
Queens and Jersey City. 

You can join as an Annual Member (Subscriber) or buy a Day Pass or 3-Day Pass 
(Customer), and you can take as many rides as you want while your membership 
or pass is active.


## Assignment

To implement a dashboard or reporting process for answering City officials 
questions on the program taking in consideration the bike data collected, organized, 
and made public on the [Citi Bike System Data](https://www.citibikenyc.com/system-data),
using Tableau in some way.


## Tableau Story 
[Citi Bike System Data Dashboard](https://public.tableau.com/profile/igor3945#!/vizhome/NYCityBikes2019/NYCityBikes?publish=yes)


### 1. Defining the problem to solve

In this activity, the questions requiring answers were identified and
grouped by similarity. Some of the initial questions are:

* How many trips have been recorded during the chosen period
* By what percentage has total ridership grown
* How has the proportion of short-term customers and annual subscribers changed
* What is the gender breakdown of active participants (Male v. Female)
* How effective has gender outreach been in increasing female ridership over the timespan
* What are the peak hours in which bikes are used during summer months? 
* What are the peak hours in which bikes are used during winter months?
* What are the top 10 stations in the city for starting a journey
* What are the top 10 stations in the city for ending a journey
* What are the bottom 10 stations in the city for starting a journey
* What are the bottom 10 stations in the city for ending a journey
* How does the average trip duration change by age
* What is the average distance in miles that a bike is ridden
* Which bikes (by ID) are most likely due for repair or inspection in the timespan
* How variable is the utilization by bike ID
* NYC map with stations and zip codes as a tooltips


### 2. Gathering business knowledge of the Citi Bike project

The objective for this activity was learning about the Program and the rules 
that shaped the data to be analyzed.

Also, the knowledge acquired by doing this activity was useful in the decision
making process done in the next steps.


### 3. Collecting Citi Bike trip data

The Citi Bike System Data provides csv files that include:

Trip Duration (seconds) | Start Time and Date | Stop Time and Date |
Start Station Name | End Station Name | Station ID | Station Lat/Long |
Bike ID | User Type (Customer = 24-hour pass or 3-day pass user; Subscriber = Annual Member) |
Gender (Zero=unknown; 1=male; 2=female) | Year of Birth

During this activity, the period needed to answer the questions 
was set to 2019, and it was necessary to download 12 large csv files.

The csv files were not saved in this repository because they are very large, 
however, the result csv(s) created are available.


### 4. Cleaning and transforming data

The content of the monthly files was read using Pandas and converted to data frames.

For all the files the treatment was the same, however, there were differences
in the data that required specific actions for each year.

For 2019, after reading each file, missing values for Birth Year and 
User Type were identified. The Birth Year was filled with the median 
of the grouping by Gender and Birth Year. The User Type was filled as a 
Customer.

Zip Codes for each station was identified using Geopy library.

With respect to outliers or surprising data points there were certain concerns: 
Trip Duration, Birth Year, and Mileage estimates.

Brief description and finding described under each Tableau visualization.

A function in Python was used to calculate the distance between 
latitude-longitude pairs. See [haversine.py](https://gist.github.com/rochacbruno/2883505).
In this approach, the miles are calculated taking into consideration
only the geographic location of the starting and the ending stations.


### 5. Exploring and analyzing data

Data exploration was made to build intuition and find patterns,
that later were reported as conclusions. The results can be seen 
in the Jupyter Notebooks.


### 6. Creating visualizations

In order to provide an answer to the initial questions, the aggregates
created were loaded in Tableau and some visualizations were made to test
if the information contained on them was enough to satisfy the users'
information needs. 

In the map, all bike stations with a visual indication of the most popular 
locations to start and end a journey with zip code data are showed. Also, 
through filters the user can see how each station's popularity changes over 2019.