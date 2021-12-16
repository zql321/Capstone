## Problem Statement

The goal of this project is to build a classification model to predict if corruption in emails using text mining with the stakeholders being auditors, regulators and company's board of directors who have oversight over company management.

### The Enron Corporation

The Enron Corporation was an American energy company based in Houston, Texas formed in 1985 by Kenneth Lay after merging Houston Natural Gas and InterNorth.  The Enron scandal, initially made public in the fall of 2001, eventually led to the bankruptcy of the Enron Corporation.  The case led not only to the dissolution of Enron, but also the de facto dissolution of Arthur Andersen, one of the five largest accountancy firms in the world at the time.  Additionally, the case caused financial distress thoughtout the energy, trading and financial markets, ultimately leading to the implementation of the Sarbanes-Oxley Act in the US.   In 2001, it was the largest bankruptcy reorganization in American history, though that title was shortlived, with the collapse of Worldcom the following year. Nearly twenty years later the effects of the collapse are still felt in the financial and energy markets.  Given the enormous scope of the corporate failure in risk mangement, auditor oversight, and corporate culture, the red flags that were visible are worth ongoing investigation.


### The Enron Emails

The dataset we are reviewing is the remaining body of corporate emails mostly between 1997-2001.  The remaining body contains data from about 150 users, mostly senior management of Enron, and contains over 500k individual emails.  This data was originally made public, by the Federal Energy Regulatory Commission during its investigation. The source data used this project has been converted to .csv obtained from [**Kaggle**](https://www.kaggle.com/wcukierski/enron-email-dataset) and has not been included in the repository due to its size.

### Project workflow
The following is the general workflow for this project: 
+ **Exploratory Data Analysis (EDA)**
+ **Network Visualization**
+ **Pre-processing and Feature Engineering**
+ **Modeling and Evaluation**
+ **Conclusion and Recommendations**

For the purpose of this project, we will be using both the email metadata and the emails themselves to identify Enron employees requiring further investigation. The process will use a two step analysis where the output of an unsupervised algorithm is used as the input for a supervised learning algorithm to train a model to flag someone as being at risk of committing fraud using their email traffic. 

The model has an F1 score of 97% and would therefore be considered successful as an efficient model to review emails and identify people who may be at risk of committing fraud so that a more in-depth investigation can be performed. 

### Recommendations to further improve the model include:
    
- Getting access to computing resources to run the supervised learning algorithm on the full dataset
- Deeper review of language used in emails to determine if that could be a red flag for fraud# Capstone
