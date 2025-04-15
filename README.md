# HDB Resale Analysis

Group 4
Members:
Aw Shao Yang U2323206F 
Poh Jia Yong U2323306C

Our project has been seperated to notebooks and pdf, notebooks under the folder notebooks and pdf on the top most level. There are also 2 notebooks 1 for full data collection and the other containing, clean, analsysis and NL


## Problem Statement
The Housing Development Board (HDB) flat is a cornerstone of the Authentic Singaporean Experience (for [78% of us](https://www.singstat.gov.sg/find-data/search-by-theme/households/households/latest-data)). While many of us purchase flats directly from HDB through the Build-to-Order (BTO) exercise, there are some factors which will lead to many others purchasing an HDB flat on the resale market instead.

Because a home purchase is typically the most expensive item that many of us purchase in our lives, it is really important that we pay the right amount for the house, as overpaying for a home can cost us a lot of money, typically in the tens of thousands, or hundreds of thousands of dollars.

However, housing prices are determined by a myriad of factors, and it can get very confusing to understand what is the right value to offer for a home. So, this project will aim to address the issue of predicting the resale value of a house.

The problem statement is:
**<center>Can we accurately predict the resale value of a Housing Development Board (HDB) flat based on various housing-related data?</center>**

The audience is mainly sellers and buyers of hdb flat, providing them info on the what, where and when that affects the hdb price


## Data Preparation
Here is an overview on how we prepared the dataset, involving collecting, cleaning and feature engineering

### Collecting 
The dataset collected was from various locations, such as
- Data.gov.sg 
- Wikipedia
- OnemapAPI

Our project involves the use of HDB resale price data in Singapore, hence we decided to collect it from data.gov.sg as it is the core source of singapore relavant data and has a lesser chanxe to be tamperered with. 

In total 4 csvs were downloaded involving hdb resale data from 2000 Jan - 2025 March

Besides HDB data, we also wanted to know the effects on proximity of data, so we collected Mall and MRT names across SG from wikiedia

Finaly we also thiught that geospatial data would help and hence use onemap api to extract the lat and long for mall, mrt and hdb

### Data Cleaning 
Since the data colelcted was from data.gov there was not much to be cleaned however we did the following 
- Check null values
- Check duplicates but decided to keep them 
- Renamed some of the columns to more befitting names
- Re caclculated remaining lease to settle the inconsistencies in the data set and removed null values 
- Check summary stats and graphs for strnage outlier possibilities but all looked relatively normal


### Feature Engineering 
As for feature engineering here are the new data that we created 
- Took the month column and split it into year and month for more usable data 
- Converted storey such as 01-05 into middle, upper and lower storey
- Applied log algorithm to price data to make it less skewed
- Retrieved nearest mrt and mall from hdb
- Generated distance data between house and nearest mall and mrt using equator function 
- Label encoded the HDB flat type column
- One hot encoded the different towns the hdbs were in
- One hot encoded the different flat models

## Exploratory Data Analysis
- Check for outliers in continuous data using boxplots
- Check outliers in target feature using historgram 
- Generated box plot for resale price seperated by flt type and flat model 
- Created correlation plots to check for relations 
- Created a year seperated heatmap for all continuos features to check for correlation between features and resale price wil less noise from yearly resale inflation 
- Use a bar plot to check when is the most active month of putchase count 
- Use a histogram to check most active lease remain resale
- USe chororpleth map to check for correlation between price and floor area across different towns
- Use chororpleth to check for resale price diff in different towns'

## Machine learning techniques 
Here is a summary of all the techniques applied in our project for ML 

### Train Val Test SPlit
Used a train val test split instead of the normal train test split to remove risk of data leakage during model fine tuning

### Models used 
Total we used 3 models inclusive of 
- Linear Regression 
- Random Forest Regressor
- XGBoost Regressor

### Metrics applied 
Metrics used to compare the model performances include 
- RMSE 
- R^2 
- MAE

### GridSearchCV
Applied grid search during fine tuning to find the best set of params to achieve the best model. Process also includes k fold cross validation to ensure that the score is robustly understood and not a one off chance

### Final Testing
All of this was done using Train and val, but the final one to be used at the end used test to validate the performanceto give a score on unseen data


## New things learnt and used include 
- Self collection of data using tools like beautiful soup for webscraping and one map use
- Use of both label encoding and one hot encoding in appropriate situations
- Learnt external visualisation libraries such as folium for choropleth generating
- Used Train val test instead to prevent leakage
- Learnt xgboost as an additional model outside of curriculum 
- Appied concepts like cross validation and grid search