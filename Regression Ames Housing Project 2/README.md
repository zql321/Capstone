# Project 2: Ames Housing Data

## Problem Statement 
[[Ames]](https://en.wikipedia.org/wiki/Ames,_Iowa) is a city in Story County, Iowa, United States with the characteristics of a college town where there is a young population and education is the key anchor of the local economy with the Iowa State University being the biggest employer in Ames.

We are working for General Asset Investments which is a real-estate investment company looking to decide on whether to invest in a property in Ames. As an analyst in the Investments team, my taks is to perform data exploration and design a house price prediction model for our business development team. The business case for this project are detailed below:
1. Data exploration of past real estate transactions in the Ames, Iowa region, would help us to understand the geographical discrepancy in home prices, and which estate to focus on when we search for houses with deep discounts. 
2. A mathematically-backed prediction model to share with the Investments team regarding our analysis of home prices.

The Investments team is unable to decide on whether to invest in a property in Ames as there are many factors which would affect housing prices. Many of these factors (variables) are categorical in nature and it is difficult for an average investor to dicipher such complexity and translate the data into useful information for decision making.

A regression model can be constructed based on the Ames Housing Dataset. This model would help to explain how dfferent variables affect housing prices and predict the price of a house in Ames.(model and scope)

Using the predictive model, the Investments team would be able to discover undervalued properties in Ames as they uncover the answers to the following problems:

*** Which features of a property are important in predicting sale prices of houses in Ames?**

*** What is the predicted sale price of a house in Ames based on its features?**

Success is evaluated based on answering the problem statements with the model producing the lowest Root Mean Squared Error (RMSE). Other stakeholders who may be keen in getting answer to the above questions could include current home owners who are thinking of selling their property or town council of Ames. For the purpose of the project, we would focus on the primary stakeholders, which is the Investments team.

## Executive Summary
We have examined the Ames housing dataset consisting of various attributes along with the sale prices from 2006 to 2010 which is obtained from the Ames Assessor's Office. 

Analysis has been conducted over the features of a property which affects the sale price by utilizing various regression models. The optimal mode with best performance would be used to inform the Investments team on what are the key attributes affecting housing prices and to predict a property's price.

## Findings

Findings from our predictive model shows that the top 5 of the best predictors fall into 2 main categories

**A) Size**

1. Above grade (ground) living area in square feet

2. Total square feet of basement area
    
3. Size of garage in square feet
    
**B) Quality**

1. Overall material and finish quality of the house

2. Year Built/Year Remodelled

Other key findings indicate that housing location matters with Sawyer West and SWISU (South and West of Iowa State University) as the prefered locations which collaborates with our observation that Ames is a college town with the the locations around the Iowa State University being the most desired given that it is the biggest employer in Ames 

Interestingly, there are some factors that have a negative impact on housing prices. Full baths and detached garage types are the biggest negative predictors. This could also indicate that property in Ames could be designed for student rentals and features such as full baths and detached garage types would not be desired by students since these features use up living areas and might not be utilized as much or as not as convenient in the case of detached garage types.

#### Housing Price Prediction(Valuation)

Our model does relatively well in predicting houses that were priced below USD 400,000. However, the variance between our predictions and true values start to increase after the USD 400,000 mark. 

## Conclusion & Recommendations

Based on our findings, we would be able to answer the questions that we have formulated as part of the problem statement.

* Which features of a property are important in predicting sale prices of houses in Ames?

We recommend the Investments team to consider the top 5 predictors, size of living area, size of basement, size of garage and overall quality and finish of house and the year built/year remodelled which is an indicator of the quality and finish of the house as well before investing in properties in Ames.

The Investments team should also focus on locations close to Iowa State University, which is the biggest employer of the population in Ames and take note that full baths and detached garages have a negative impact on housing prices.

* What is the predicted sale price of a house in Ames based on its features?

We would be able to answer this question based on attributes of a property the Investment team would like to purchase.
However, an important point to take note of is that the model works well for properties under USD 400K.
Other risks to consider as well are:

1. Refreshing of the model with more recent data which would be recommended to consider the effects of external anomalies (i.e. the 2008 Financial Crisis which arose from a US housing bubble)
2. Include additional factors in line with best practices in real estate domain knowledge which are currently unavailable (i.e. access/distance to public transportation)
