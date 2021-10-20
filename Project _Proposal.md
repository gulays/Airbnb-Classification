# Airbnb Listing Perfonmance - Occupancy Rate Classification 

## Question/Need
This project will analyze the Airbnb listings and identify critical features that mostly affect the occupancy rate of a listing. 
The result of the analysis will help hosts in optimizing their listings and will increase the occupancy rates. 
Optimizing listings will eventually improve both hosts and guests experiences and yield higher retention.

## Data
The data will be collected from [Inside Airbnb](http://insideairbnb.com/about.html) and cover over 30K listings in Los Angeles, till September, 2021. 
The summary description of the dataset is as follows:
- Listings, including full descriptions and average review score (about 70 features).
- Reviews, including unique id for each reviewer and detailed comments.

The occupancy rates for each listing will be estimated as a function of the number of reviews per month, minimum nights and 365 days availability features. 
Then a new variable will be defined to differentiate high from low performing listings, i.e. high (low) occupancy listings where corresponding rates are greater (less) than a threshold point. This threshold will be chosen considering the average Airbnb occupancy rates in recents years and occupancy rates of hotels. Some relevant statistics are given below. 

- The average Airbnb occupancy rate in LA are about 65% in 2019, 54% in 2020 and 53% in 2021 (by August, 2021)[^1],[^2].
- The U.S. average occupancy rate is about 46.% by April, 2021 [^3]. 
- An ideal occupancy rate for hotels is between 70% and 95%[^4].


## Workflow 

- Data Cleaning and initial EDA
- Estimate occupancy rates and create a new variable as occupancy (high or low)
- Create a baseline classification model by using a few features
- Improve the baseline model using various classification models and feature engineering
- Compare models with cross-validation
- Select an optimal model identifyand identify the most critical features that affect the occupancy.

## Tools:
Pandas, numpy and scikit for cleaning, EDA and classification modelling.
Matplotlib and seaborn for visualisations.

## MVP Goal:

EDA and baseline classification model, i.e. Logistic regression. 


[^1]: [Link1](https://www.dpgo.com/go/data-insights-july-august-2021/)
[^2]: [Link3](https://www.airdna.co/blog/how-to-optimize-your-airbnb-occupancy-rate-with-data-analytics)
[^3]: [Link2](https://capitalcounselor.com/airbnb-statistics/)
[^4]:[Link4](https://hoteltechreport.com/news/occupancy-rate)
