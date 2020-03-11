# Wrangle Report

Created by Lukas Peterson, Udacity Student

A description of my wrangling efforts to clean dog rating tweets from the Twitter user WeRateDogs for Udacity Data Analyst Nanodegree program. 

`wrangle_act.ipynb` contains the data wrangling code. Data files included in root directory.

## Project Goal:

The goal of this project is to effectively wrangle data related to dog ratings. The data is sourced from the twitter user WeRateDogs. Once we have effectively gathered, assessed, and cleaned our data in this project, it can be used by our analysts downstream.

## Gather:

The data for this project comes from three locations each using a different method of gathering:

- A CSV flat file on-hand titled: twitter-archive-enhanced.csv. Use the Pandas method to_csv() to import this file into a dataframe.
- Image predictions from a neural network predictive model based on the images in each tweet. Download this file from a hosted Udacity server using the requests package.
- Each tweets metrics: favorite count and retweet count obtained from the Twitter API. Obtain these metrics and store them as a dataframe using the tweepy package.

All data files have been included in this project

## Assess:

To assess the data first look at the data visually using pandas. Head(), tail(), and calling the dataframe are useful methods.

Second, programmatically assess the dataframes by looking at the column information, structure, and descriptive statistics. Pandas’ info(), value_counts(), and describe() are useful methods.
Quality Issues:
Twitter archive dataframe assessments include:

  - Some rows include information on retweets and reply tweets, we are only concerned with base tweets
  - There are several retweet and reply columns we do not need
  - Some values are missing in the expanded_urls field
  - Several dog names are missing or incorrect
  - Timestamp column is incorrect datatype of object
  - Some ratings were incorrectly identified from the tweets
  - Source column contained unnecessary HTML tags and formatting
  - Tweet_id column is of type int, we do not need to do any analysis so it should be changed to string

Twitter metric assessments include:

  - Datatypes of retweet_count and favorite_count are incorrect

Tidiness Issues:

  - The twitter archive dataframe has four columns for each dog type
  - The data is separated into three tables, but our data all correlates to the same observation object, dog rating tweets

## Clean:

To clean the data, create a copy of each dataframe and then follow the Define – Code -Test process for each of the documented issues. Address the tidiness concerns first then the quality issues.
Tidiness Cleaning:

To merge the four dog type columns, replace ‘None’ values with an empty string then concatenate the values into a single dog_type column.

Merge the three dataframes into a single master dataframe using the Pandas merge() method.
Quality Cleaning:

To address some column quality issues I used Pandas methods for drop, clip, re-assign, and type casting. For some string type columns I used extract, regular expressions, and string indexing.

Once I cleaned all the documented issues I saved the data to a master dataframe and csv table using Pandas to_csv() method.

## Conclusion:

I was able to successfully clean many of the tidiness and quality issues in the dataset, however there are still many issues related to missing data we could not address. Dog names, dog types are examples of missing data we may never be able to collect if the original user did not include them in the data gathering phase. Tweet URLs are an example of missing data we may be able to collect in the future by programatically scraping the tweets, or manual data entry.

The next steps of the our wrangling efforts are to analyze the data. We will use the act_report to showcase some of our findings.
