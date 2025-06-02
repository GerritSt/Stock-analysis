# Project Overview

This project is focused on scraping stock data from **Simply Wall St API** and **Alpha Vantage** using Python.

https://sec-api.io/docs/query-api/python-example

## Features
- Fetch company data by name or ticker

## Goals
- Fetch company data by using the `companyByExchangeAndTickerSymbol` query
- Structure the data into a useful format for analysis
- Use data to summarize good stocks to currently invest in
    - will be dependent on the features that my model specifies

# Project brainsorm:

## Get data:

- Get all companies (this will be for the daily update):
   - scrape the companies into lists of dictonaries
   - put this then into a pandas data frame 
- could use the info from each company to 
- or could use dataframe input into machine model for prediction

## Create a machine learning model:

This machine learning model will be based on the fundumentals of a companies and use this in combination with
 this would then be trained on past data of the companies and then predict if it was a good long term investment in different time zones: 1 year, 2 years , 3years

### Choice of model:
The measure of the goodness for long term investements would be a number between 0 and 1 where 0 is very bad and 1 very good. Therefore a model that uses soft labeling for a binary response class (2 classes) would be best.
- start with logistic regression for interpretability and then progress to more complex models

how would i train a model over different time zones when for example i have 10 years worth of finacial statements? And then when a model predict should it predict based of past data? **use ratios and percentages** to show growth over the years. The statements will only be used to get these metrics.

### Choice of different time zones:
Keep in mind that different time zones might have different signals for goodness of long term investmensts this can also be known as time-based trends.


