# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4: West Nile Virus Prediction

## Group 2 - Dillon, Shaalini, Vee Vian & ZheQin

## Problem Statement 

Due to the recent epidemic of West Nile Virus in the Windy City, we've had the Department of Public Health set up a surveillance and control system. Through data collection, we will learn mosquito population to derive an effective plan to deploy pesticides throughout the city. As Data Scientists from the DATA-SCIENCE, Disease And Treatment Agency, division of Societal Cures in Epidemiology and New Creative Engineering, our tasks are to:

1. Build and select a final model(Logistic Regression/Random Forest Classifier) and make predictions to determine the period and location of pesticide spraying in Windy City to bring down the West Nile Virus infection rate
2. Conduct a cost-benefit analysis for the annual cost projections of various levels of pesticide coverage VS level of pesticide coverage and provide feasible recommendations

Primary stakeholders: CDC, Centers for Disease Control and Prevention 
Secondary stakeholders: Government of Chicago. 

## Executive Summary

This project involves utilizing data collected regarding mosquito population to derive an effective plan to deploy pesticides through Windy City due to the recent epidemic of West Nile Virus in the city. The deliverables from this project are to produce a final model and make predictions to determine the period and location pesticide spraying in Windy City. Also, an in-depth cost-benefit analysis shall be conducted to assist the stakeholders in the decision-making of the effectiveness of pesticide spraying and proposed feasible solutions to better maximize the effectiveness of the pesticide spraying. 

### Data Cleaning

For the first step, we load the 4 datasets which we obtain from Kaggle and did extensive data cleaning which include the following:
- Converting the column names into lowercase
- Checking and dealing with missing data - Generally, we drop the missing data at the initial stage. After feature engineering, we use SimpleImputer to impute the missing values with the mean value from the train data just before modelling to further reducing the number of rows for the train data
- Checking for inconsistencies in the provided data such as mislabelled trap addresses or typo error
- Converting the datatypes to the appropriate dtypes - Example: values in the date columns for all data are convereted to datetime format

### Exploratory Data Analysis (EDA)

For the second step, we did Exploratory Data Analysis (EDA) after data cleaning to have an initial understanding of the data and trends. Some observations include -
- Imbalance data in train data with 95% of the train data with no WNV present, while only 5% with WNV present. We are required to deal with data imbalance before any modelling works is carried out.
- It was observed that there were more mosquitoes in the summer (Jul to August). With the higher number of mosquitoes, the number of wnvpresent is also higher.
- We can see definitive seasonality trends for the occurrence of the WNV in mosquito samples, where August tends to have the highest rates of the virus occurring. The rates were highest in 2007 and 2013.
- Used geopy to plot out the map of Chicago, visualising the weather stations, location of traps placed for catching mosquitoes, WNV outbreak shows that the traps are pretty spread out and the spray generally didnt cover most of the WNV outbreak areas

### Pre-processing and Feature Engineering

For the third step, we did further pre-processing and feature engineering to prepare our data for modelling. We combined features from weather to train and test data to create 2 dataframes. We created additional feature such as heat_cool, tavg and etc and then select our features by creating a correlation plot and dropping features which are highly correlated. Subsequently, we use pd.getdummies to create dummy variables for the feature species and the rest of the features are numerical features.  we use train_test_split with test_size = 0.3 to split the data before modelling. Finally, The argument 'class_weight' for both models is set to 'balanced' to address data imbalance. 

### Modelling and Evaluation

For this project, we will be using the processed data to create 2 models - Logistic Regression and Random Forest Classifier models to determine if there is a presence of WNV given the input data. As mentioned in the EDA, we encountered imbalance data for this project and hence we will not be using tests accuracy score as the primary evaluation metric to select the final model (between Logistic Regression and Random Forest Classifier) to predict the unseen test data. Instead, ROC AUC score and F1 score were chosen as the model evaluation metrics. Cost-sensitive learning was used for this imbalanced classification.

**Summary of Modelling result** 

| Score               | Logistic Regression | Random Forest Classifier |
| ------------------- | ------------------- | ---------------------- |
| Train ROC AUC score | 0.725               | 0.876                  |
| Test ROC AUC score  | 0.736               | 0.852                  |
| Train F1 score      | 0.164               | 0.269                  |
| Test F1 score       | 0.172               | 0.257                  |

Considering the scores in the above, the Random Forest Classifier perform better as compared to the Logistic Regression Model. The f1-score is 0.257 as compared to 0.172 for the Logistic Regression Model. The test ROC AUC scores are also better than the scores of the Logistic Regression. Therefore, the Random Forest Classifier will be selected as the final model to predict the unseen test data. Using feature importance, we are able to obtain that month and temperature average are the 2 most importance features.

Subsequently, the Random Forest Classifier model will then be fitted on the entire train data before using it to predict the unseen test data. The predictions for the unseen test data will then be compiled into Kaggle format and submitted to Kaggle to obtain the area under the ROC curve between the predicted probability that West Nile Virus is present and the observed outcome. The  Kaggle score (ROC AUC score) obtained was 0.69794.

### Cost Benefit Analysis

With reference to a several documents and websites, we have come to an estimation that the cost of pesticide spray which cover the area of Chicago (approximately 150,000 acres) will cost approximately USD$138,000. It can be noted that despite the large number of WNV cases over the last 14 years, there are very few studies which have estimated the initial cost of WNV disease. There are no published data on the economic burden of the specific clinical syndromes seen with WNV infections or the longer term costs of WNV disease incurred several years after the initial illness.

Based on a recent article in 2020, there were 6 cases of WNV infection detected in Chicago and the estimated medical care and productivity (loss) cost incurred would amount to USD $197,000. In summary, it is more economical to spray the whole city with pesticides in order to prevent any potential west nile virus outbreak. Benefits from mosquito spraying would include increased quality of life from fewer people falling sick and fatalities, increased workplace productivity by reducing the number of people falling sick, as well as savings in hospital expenses from treating WNV patients.

### Conclusion and Recommendation

**Improving Model Results**

Improvements which we can make to improve our results include the following -

1. To collect more data to have a more balance dataset
2. Utilize other more sophisticated models such as deep learning, XGBoost to see the results can improve further

**Solutions to reduce WNV infection rate**

In conclusion, spraying has not proven to be significant in reducing infection rates as we observed that WNV infections in mosquitoes actually rose in 2011 and 2013 when pesticide spraying was carried out. However, we believed that more data and more campaigns are required to optimise its impact before entirely ruling out pesticide spraying to reduce WNV infection rate. To further reduce WNV infection rate, we proposed 3 recommendations -

1) Target Clusters
2) Intensify spraying in June and July
3) Concurrent campaigns targeted at mosquito breeding and transmission prevention best practices


## Further Details on Proposed Solutions and Limitations

In the above, we indicated that spraying has not proven to be significant in reducing WNV infection rates and hence provided 3 recommendaiton to address this shortcoming:

1) Target Clusters: We should target clusters around our Top Traps and Top WNV Addresses which are high-occurrence areas that are particularly virulent, and it would maximize the value of the amount invested in spraying.

2) Intensify spraying in June and July: There are many Weather features accelerate mosquito breeding. We already saw earlier the month of August has the highest presence of the West Nile Virus in Chicago and thus for maximum effect, we suggest that spraying to be intensified in the months of June and July leading up to August.

3) Concurrent campaigns targeted at mosquito breeding and transmission prevention best practices: This would include CDC advisories recommending the removal of stagnant water, the usage of mosquito repellant, and wearing long sleeved clothing to prevent bites. If we can educate more of the local population to become harder mosquito targets and reduce transmission on their own cost, this would be a win-win for the CDC and Chicago.

**Limitations:**
Our solutions are a good starting point, but other major factors should be borne in mind, including:

1) COVID-19: It is obvious public knowledge now that this is the world's most urgent viral outbreak to deal with. As the CDC, it only makes sense that it needs to prioritize more dire issues. No other pandemic has taken as large a toll on any given population centre in America than COVID-19. As far as cost-related analyses go - it is estimated that USD 500m has already been lost to COVID-19 in Chicago specifically Still, that doesn't mean WNV should be ignored - it just means that its risk prioritization needs to be adjusted in light of the pandemic

2) Surveillance: Apart from monitoring viral infections, none of our models account for the quality of surveillance systems in use. The CDC already uses mosquito surveillance software to track WNV. What can be further explored then is whether deeper levels of automated machine learning can be applied to procedurally track spraying clusters vs WNV clusters in the event that there are any gaps in spray coverage.

3) Demographic Segmentation: We have not broken down the predictive model further into sub-categories of WNV-related illnesses in humans. Nor have we segmented analyses based on critical population features e.g. age groups in Chicago - senior citizens are more badly impacted, and specific modelling and measures could be trained on this consideration.

## Datasets used

* [`train.csv`](asset/train.csv): Training set consist of data from 2007, 2009, 2011 and 2013. Includes information such as trap, number of mosquitoes caught in this trap, coordinates of the traps and etc
* [`test.csv`](asset/test.csv): Test set which are required to predict the test results for 2008, 2010, 2012 and 2014
* [`spray.csv`](asset/spray.csv): GIS data of spraying efforts in 2011 and 2013 -  Includes location and date
* [`weather.csv`](asset/spray.csv): Weather conditions and data  of the city from 2007 to 2014

The datasets, along with description, can be found here: [https://www.kaggle.com/c/predict-west-nile-virus/](https://www.kaggle.com/c/predict-west-nile-virus/).

## References 
The links shown below are references which were used in this project:
- https://en.wikipedia.org/wiki/Chicago
- https://www.chicago.gov/content/dam/city/depts/cdph/Mosquito-Borne-Diseases/Zenivex.pdf
- https://chicago.cbslocal.com/2017/08/30/spray-mosquitoes-far-south-side-west-nile-prevention/
- http://www.centralmosquitocontrol.com/-/media/files/centralmosquitocontrol-na/us/resources-lit%20files/2015%20zenivex%20pricing%20brochure.pdf
- https://www.chicago.gov/city/en/depts/cdph/provdrs/healthy_communities/news/2020/september/first-human-cases-of-west-nile-virus-in-chicago-for-2020.html
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3945683/
- https://news.wttw.com/2020/05/18/coronavirus-toll-chicago-budget-excess-500-million-official
- https://www.cdc.gov/westnile/resourcepages/mosqSurvSoft.html
- http://www.dph.illinois.gov/topics-services/diseases-and-conditions/west-nile-virus

## Data Dictionary

### Train and Test Dataset

| **Feature**  | **Description**  |
| :-|:-|
| id |Id of the record|
| date | Date |
| address | Approximate address of the location of trap (Sent to the GeoCoder) |
| species | Species of mosquitos |
| block | Block Number of Address |
| street | Street Name |
| trap | Id of the trap |
| addressnumberandstreet | Approximate address returned from GeoCoder |
| latitude | Latitude returned from Geocoder |
| longitude | Longitude returned from Geocoder |
| addressaccuracy | Accuracy returned from Geocoder |
| nummosquitos | Number of mosquitoes caught in this trap |
| wnvpresent | Whether West Nile Virus was present in these mosquitos. 1 means WNV is present, and 0 means not present |
| station | The nearest weather station (1 or 2) nearest to the longitude and latitude of the location of trap |

### Spray Dataset

| **Feature** | **Description**        |
| :---------- | :--------------------- |
| date        | Date of the spray      |
| time        | Time of the spray      |
| latitude    | Latitude of the spray  |
| longitude   | Longitude of the spray |


### Weather Dataset

| **Feature**  | **Description**  |
| :-|:-|
| station |Weather Station 1 or 2|
| tmax | Maximum temperature in degrees Fahrenheit |
| tmin | Minimum temperature in degrees Fahrenheit |
| tavg | Average temperature in degrees Fahrenheit |
| depart | Departure from Normal |
| dewpoint | Average dew point in degrees Fahrenheit |
| wetBulb | Average wet bulb temperature in degrees Fahrenheit |
| heat | Heating (Season begins with July) |
| cool | Cooling (Season beings with January) |
| heat_cool | Difference between the heat and cool columns |
| sunrise | Time of Sunrise (Calculated, not observed) |
| sunset | Time of Sunset (Calculate, not observed |
| codesum | Weather Phenomena |
| depth | Depth of Snow/Ice (on ground)(1200 UTC) in inches |
| water1 | Water (Equivalent (1800 UTC) |
| snowFall | Snowfall precipipation in inches |
| precipTotal | Rainfall and Melted snow precipation in inches |
| stnPressure | Average station pressure |
| seaLevel | Average sea level pressure |
| resultspeed | Resultant wind speed |
| resultdir | Resultant wind direction - (whole degrees) |
| avgspeed | Average wind speed |
