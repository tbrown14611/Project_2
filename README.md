GDP## Project Team
 - Thomas Brown
 - Robb Stenman
 - Jed Murphy

## Project 2 Instructions / Directions

- Instructions for [project 2](https://bootcampspot.instructure.com/courses/5432/pages/16-project-2-overview?module_item_id=1201087) provided by the course instructors.

For Project 2, you will work with your group to solve, analyze, or visualize a problem using machine learning (ML), along with the other technologies you’ve learned so far. Here are the specific requirements:

 - Find a problem worth solving, analyzing, or visualizing.
 - The dataset(s) for your project must have at least 500 records. (If developing a decision tree/random forest model, you should use at least 1,000 records.)
 - Use either a supervised or unsupervised ML model to solve, analyze, or visualize the problem.
 - Evaluate the trained model(s) using testing data. Include any calculations, metrics, or visualizations needed to evaluate the performance.
 - You must use Scikit-learn.
 - You must use at least three of the following:
 - API requests
 - Matplotlib
 - Pandas
 - Pandas plotting
 - Prophet
 - Python
 - Time series analysis

## Project Ideation: 
The team explored several ideas, ultimately choosing to Analyze selected Country Exchange Rates and the relationship to their Gross Domestic Product (GDP Growth). 

## Project Files:
[Data Source for US Treasury Exchange Rate Reporting](https://fiscaldata.treasury.gov/datasets/treasury-reporting-rates-exchange/treasury-reporting-rates-of-exchange#dataset-properties) 

[Data Source for World Bank Gross National Product](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD)


## Important information about the DU-Project-2 Repository

## Data Cleanup Issues

The data from the The Department of the Treasury and the Bureau of the Fiscal Service, GDP Growth, was relatively clean and consistent. For our purposes, we needed to be aware that the data included regions and categories, such as East Asia & Pacific and OECD members, respectively. These were automatically removed since we used the inner join function when combining data sets, so it did not cause any issues.

The data from the World Bank had several inconsistencies. Sometimes the same countries were listed in all Upper Case and sometimes in Title Case. There were several instances where the same country's name was spelled different ways (eg. Azerbaijan and Azerbaidjan).

Several countries had multiple currencies listed. In some cases, the multiple currency listings referred to the same currency but expressed in different ways. For example, the United Kingdom "Pound" and "Pound Sterling" both refer to the currency of the United Kingdom, just phrased differently. Some countries underwent a currency change during the time period covered by the data. In this situation, the old and new currencies would both be listed.


## Project Summary

Analyze selected Country Exchange Rates and the relationship to their Gross Domestic Product (GDP Growth). 

- Project Milestones:	
    - Project ideation – Complete 5/27
    - Data fetching – Complete 5/27
    - Data exploration – Complete 5/30
    - Data transformation – Complete 6/3
    - Data analysis – Complete 6/6
    - Testing – Complete 6/10
    - Creating documentation – Complete 6/10
    - Creating the presentation – Complete 6/10

GitHub repository is free of unnecessary files and folders and has an appropriate .gitignore in use.


## Questions, Analysis and Summary
### Goal 

-Goals: 
 - Analyze Exchange Rates for 10 countries and correlation to GDP Growth.
 - Analyze all 11,762 Exchange Rates for all countries and correlation to GDP Growth.
 - The model demonstrates meaningful predictive power at least 75% classification accuracy or 0.80 R-squared.
 - Are the exchange rates for a Country a good predictor of annual GDP Growth for that Country?
 - How closely correlated are exchange rates and GDP Growth for a country?


###	Question 1:  Are the exchange rates for a Country a good predictor of annual GDP Growth for that country?
- R-squared is used as a measure of fit, or accuracy of the model, but what it actually tells you is about variance.
- Our overall R-squared below indicates the Random Forest Regressor model is a good fit.
- Training (R2) Score: 0.9764628099591433
- Testing (R2) Score: 0.8799472692666176

### Question 2:  How closely correlated are exchange rates and GDP Growth for a country?

Pearson Correlation: -0.03759903238661448  (weak)
Exchange Rates and GDP Growth are negatively correlated. As Exchange Rates go up, GDP Growth goes down.
Pearson is a liner correlation measure, Random Forest Feature Importance should be use for this measure. 

Random Forest Feature importance refers to techniques that calculate a score for all the input features for a given model.
The scores represent the “importance” of each feature.
A higher score means that the specific feature will have a larger effect on the model that is being used to predict a certain variable.
Random Forest Feature Importance measurement:
- Exchange Rate     0.391174
- Effective Date    0.299577
- Country Code      0.309249
- Exchange Rate is the most "important" and has the larger effect on the model to predict GDP Growth.

## Analysis Approach

The analysis was broken into multiple steps with a Jupyter notebook for each step.
- Step1_build_base_data.ipynb
- Step2_reformat_data_for_analysis
- Step3_analyze_data

    Step duration is calculated (see Duration in each step detail below)

The analysis proved that the Random Forest Regressor produces the best R2 R-squared. 
Performance will be improved when the models that are run are reduced to include 
only the Random Forest Regressor model. Duration for step 3 will be updated and the
performance improvement noted.

### Jupyter notebook: step1_build_base_data.ipynb Duration: 0:00:02.035045

- Us Treasury and World bank data, downloaded and saved as .csv files in project Resources are input to Step1
- Cleanup:
    - Apply dictionary to correct Country Names in GDP Growth table to be the same as Country Names in Exchange table
    - Split Currency and Country into two columns
    - Convert Nan to 0
    - Merge Exchange and GDP Growth "inner" on Country
    - Convert Effective Date to YYYYMMDD
    - Add column for Effective Year
- Save DataFrame to /Resources/result_files/step1_build_exchange_gdp_sorted_df.csv 

### Jupyter notebook: step2_reformat_data_for_analysis.ipynb Duration: 0:00:00.305458

- step1_build_exchange_gdp_sorted_df.csv is input to Step2
- Melt the dataframe to convert year columns into rows and align them with the 'Year' column
- Filter rows where 'Year' matches 'Year_temp'
-  Drop the 'Year_temp' column
- Reorder columns
- Save converted DataFrame to Resources/result_files/step2_reformat_data_for_analysis.csv

### Jupyter notebook: step3_analyze_data.ipynb Duration: 0:00:05.307291

- step2_reformat_data_for_analysis.csv is input to Step3
- Filter for one contry if needed
- Update Country Code to the ISO numeric value
- Write Updated dataframe and change Country Code to data type int.
- Perform Ridge Regession.
- Compare Ridge with Linear Regression
- Compute Lasso Regression and compare it with Ridge and Linear Regression
- Calculate mean squared error (MSE).
- Calculate R-squared (R2)
- Random Forest Regressor 


The analysis proved that the Random Forest Regressor produces the best R2 R-squared. 
Performance will be improved when the models that are run are reduced to include only 
the Random Forest Regressor model. 

 ## Performance adjustment measurements (1.2 second improvement)
 
 - Before Adjustment Duration: 0:00:05.307291
 - After Adjustment Duration:  0:00:04.185599


## Result/Conclusion

![alt text](image-2.png)

![alt text](image-5.png)




