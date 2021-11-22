# Airbnb-Occupancy Rate Classification

## Question

This project will analyze the Airbnb listings and identify critical features that mostly affect the occupancy rate of a listing. 
The result of the analysis will help hosts in improving their listings with the most critical features. 
Achieving higher the occupancy rates yields highre revenues to hosts and to the platform. 
Thus, occupancy rate optimization can be used as a revenue management tool. 

## Data

The data is collected from [Inside Airbnb](http://insideairbnb.com/about.html) and cover over 30K listings in New York City, till September, 2021. 
The summary description of the dataset is as follows:
- Listings, including full descriptions and average review score (about 70 features).
- Reviews, including unique id for each reviewer and detailed comments.

The features in the data set are grouped into 5 groups as follows:
- Host related: Host response time, Host since, Host superhost ...

- Location related: Neighborhood, Latitude, Longitude , Neighborhood overview...

- Listings related: Property type, Rooms, Bathrooms, Accommodates  ...

- Rental related: Availability 30, 90 , 365 days, Min/ Max nights, Instant Bookable, Price ...

- Guest experience related: Reviews, Scores, First/Last Review ...

The occupancy rates for each listing is estimated as a function of the average number of reviews per month and minimum required nights assuming that 30% of the stays writes reviews.
Occupancy level is derived from occupancy rates and divided listings as high, average and low occupancy considering the following industry occupancy levels.
- The U.S. average occupancy rate is about 46% by April, 2021. 
-  An ideal occupancy rate for hotels is between 70% and 95%.


## Baseline Models and Evaluation Metric
Models for baselining :

-SVC

-KNN 

-Bagging

-RandomForest

The models are evaluated using repeated stratified k-fold cross-validation.Stratified means that each fold will aim to contain the same mixture of examples by class as the entire training dataset. 
Repeated means that the evaluation process will be performed multiple times to help avoid unlikely results and better capture the variance of the chosen model
[link](https://machinelearningmastery.com/imbalanced-multiclass-classification-with-the-glass-identification-dataset/).

Evaluation Metric:

Precision is important to categorize the listings correctly. If hosts know, their listings would create high or low occupancy, they would act differently. 
For example, a host with a low predicted occupancy might invest in various sources and search methods to increase the occupancy rate. 
So, it is important to provide the right information to the host.

On the other hand, recall is also relevant in this concept. Identifing a high occupancy listing as lower category causes additional costs to the listing host who aims to improve his listings occupancy 
as well as his profit and might affect adversely the host's revenue from the Airbnb platform. Eventually, this, false negatives, rises the host churn rate from the platform.

The other point need to be considered before picking an evaluation metric is the nature of the target feature. 
The occupancy level is multiclass and imbalanced. As stated above, I will take a balanced approach between precision and recall with more weight to precision. 
So, I use F-beta metric to evaluate the model performance with an average option 'weighted' to account for label imbalance. 
I also use balanced accuracy to evaluate the models as a second metric.


After baseline modeling, RandomForest and XGBoost are selected with the total 27 features. Some of these features are original features like accommodates, bathrooms, bedrooms, room type, host since, first review since.
Some are engineered features like amenities count, host response rate category, description length, Kitchen, Parking.   

Backward and Forward Selection Methods and GridSearch are used for feature selection and model tuning. The final model is XGBoost Model with 22 features with Fbeta(beta =0.75) = 0.59 
and Balanced Accuracy = 0.46. 

The most critical features affecting the occupancy level are identified as follows:
- Listings related: detail description of the listing, being instant bookable.
- Host related: response time,response rate, superhost, total listings of a host.
- Rental related: number of amenities. 

## Tools:
Pandas, numpy and scikit for cleaning, EDA and classification modelling.

Matplotlib and seaborn for visualisations.
