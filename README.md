## Project Team
 - Thomas Brown
 - Robb Stenman
 - Jed Murphy

## Project 2 Instructions / Directions

- Instructions for [project 2](https://bootcampspot.instructure.com/courses/5432/pages/16-project-2-overview?module_item_id=1201087) provided by the course instructors.

For Project 2, you will work with your group to solve, analyze, or visualize a problem using machine learning (ML), along with the other technologies you’ve learned so far. Here are the specific requirements:

Find a problem worth solving, analyzing, or visualizing.
The dataset(s) for your project must have at least 500 records. (If developing a decision tree/random forest model, you should use at least 1,000 records.)
Use either a supervised or unsupervised ML model to solve, analyze, or visualize the problem.
Evaluate the trained model(s) using testing data. Include any calculations, metrics, or visualizations needed to evaluate the performance.
You must use Scikit-learn.
You must use at least three of the following:
API requests
Matplotlib
Pandas
Pandas plotting
Prophet
Python
Time series analysis

## Project Ideation: 
The team explored several ideas, ultimately choosing to Analyze selected Country Exchange Rates and the relationship to their Gross Domestic Product (GNP). 

## Project Files:
[Data Source for US Treasury Exchange Rate Reporting](https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange#dataset-properties) 

[Data Source for World Bank Gross National Product](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD)


### Important information about the DU-Project-2 Repository

No issues at this time.


## Project Summary

Analyze selected Country Exchange Rates and the relationship to their Gross Domestic Product (GNP). 


## Questions, Analysis and Summary
### Goal 

Goal:  Analyze Exchange Rates for 10 countries and assess correlation to Gross Domestic Product.

Are the exchange rates for a Country a good predictor of annual GNP for that country?
How closely correlated are exchange rates and GNP for a country?


###	Question 1:  Are the exchange rates for a Country a good predictor of annual GNP for that country?

### Question 2:  How closely correlated are exchange rates and GNP for a country?


## Analysis Approach

The analysis was broken into multiple steps with a jupyter notebook for each step.


jupyter notebook: step1_build_base_data.ipynb
- Us Treasury and World bank data, downloaded and saved as .csv files in project Resources are input to Step1
- Cleanup:
    - Apply dictionary to correct Country Names in GDP table to be the same as Country Names in Exchange table
    - Split Currency and Country into two columns
    - Convert Nan to 0
    - Merge Exchange and GDP "inner" on Country
    - Convert Effective Date to YYYYMMDD
    - Add column for Effective Year
- Save DataFrame to /Resources/result_files/step1_build_exchange_gdp_sorted_df.csv 

jupyter notebook: step2_reformat_datafor analysis.ipynb
- step1_build_exchange_gdp_sorted_df.csv is input to Step2
- Melt the dataframe to convert year columns into rows and align them with the 'Year' column
- Filter rows where 'Year' matches 'Year_temp'
-  Drop the 'Year_temp' column
- Reorder columns
- Save converted DataFrame to Resources/result_files/step2_reformat_data_for_analysis.csv

jupyter notebook: step3_analyze_data.ipynb
- step2_reformat_data_for_analysis.csv is input to Step3
- Filter for one contry if needed
- Update Country Code to the ISO numeric value
- Write Updated dataframe and change Country Code to data type int.
- Perform Ridge Regesion.
- Compare Ridge with Linear Regression
- Compute Lasso Regression and compare it with Ridge and Linear Regression
- Calculate mean squared error (MSE).
- Calculate R-squared (R2)






