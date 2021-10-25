# Occupancy rate
This project will analyze the Airbnb listings and identify critical features that mostly affect the occupancy rate of a listing. 
The result of the analysis will help hosts in optimizing their listings and will increase the occupancy rates. 
Optimizing listings will eventually improve both hosts and guests experiences and yield higher retention.

The occupancy rates for each listing is estimated as a function of the average number of reviews per month and minimum required nights. The distibution of occupancy rates is as follows:

![Airbnb1](images/occupancy_hist.png)


Occupancy level is derived from occupancy rates and divide listings as high, average and low occupancy considering the following industry occupancy levels. 
-- The U.S. average occupancy rate is about 46.% by April, 2021. -- An ideal occupancy rate for hotels is between 70% and 95%.

Below the graph after transformation:
![Airbnb2](images/occupancy_nominal.png)

# Classification evaluation metric
Precision is important to categorize the listings correctly. If hosts know, their listings would create high or low occupancy, they would act differently. For example, a host with a low predicted occupancy might invest in various sources and search methods to increase the occupancy rate. So, it is important to provide the right information to the host.

On the other hand, recall is also relevant in this concept. Identifing a high occupancy listing as lower category causes additional costs to the listing host who aims to improve his listings occupancy as well as his profit and might affect adversely the host's revenue from the Airbnb platform. Eventually, this, false negatives, rises the host churn rate from the platform.

The other point need to be considered before picking an evaluation metric is the nature of the target feature. The occupancy level is multiclass and imbalanced. As stated above, I will take a balanced approach between precision and recall with more weight to precision. So, I will use F1 beta metric to evaluate the model performance with an average option 'weighted' to account for label imbalance.

The model will be evaluated candidate models using repeated stratified k-fold cross-validation.

Stratified means that each fold will aim to contain the same mixture of examples by class as the entire training dataset. Repeated means that the evaluation process will be performed multiple times to help avoid fluke results and better capture the variance of the chosen model
[link](https://machinelearningmastery.com/imbalanced-multiclass-classification-with-the-glass-identification-dataset/).

# Baseline Models: kNN and RandomForest
After the cleaning the data and EDA, I select the following features for my baselining:

- Host response rate, type:category - 5 levels: 100%, 85 - 99% , 50- 84%, 0-49% response level and unknows category for listings with no respoense rate information.
- Number of amenities a listing has, type: numerical
- Length of neighborhood, type: numerical
- Availability over next 365 days, type: numerical
- If the host has many listings, type: dummy - 1 if a host has number of listings more than 80% total number of listings



