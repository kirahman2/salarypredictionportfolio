![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary-image.png)
# How Can We Predict Salary Based on Employee Job Descriptions?

## Introduction
For this salary prediction project I examined different attributes of employee information to predict their salary. [Click to View Python Code/Notebook](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Salary%20Prediction%20Notebook.ipynb)

## Data
The data comes from Indeed (job search engine) and includes employee information. The features of the dataset include job id, company id, job type, degree, major, industry, years experience and the distance the employee lives away from the metropolitan city in miles. The actual size of the dataset is 1,000,000 rows. [(data source)](https://www.dropbox.com/sh/sctol7wx1n9qhkh/AAB0LBPBhqmoHLyw04fHRpcPa?dl=0)

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Removed 5 rows where salary equaled 0, which indicated missing values 
* Removed 7117 rows for salaries more than $220,000 since this goes beyond the upper 75% percentile (outlier removal)
* Replaced records with a degree and major listed as "None" with "Missing"
* Imputed categorical variables including company id, job type, degree, major and industry 

## Exploratory Data Analysis
Prior to the exploratory phase I hypothesized that a higher level education equated with a higher salary. To test this theory, I looked at boxplots of salary compared against degree. It turns out that someone with a PhD earns only slightly more than someone with a masters and bachelors. [Click to View Data Analysis Notebook](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Salary%20Prediction%20EDA.ipynb)

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_degree.png)

I was curious about the different industries and hypothesized that the web industry would be the highest earning. It turns out Finance and Oil earn the most. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_industry.png)

After examining the results of each feature, I noticed Company Id was divided into 63 groups. After diving deeper and examining each feature against company Id, I did not find signs of grouping. I did however notice variation in the average salary for each Company Id group. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_compid_.png)

Looking a bit deeper, within each company id group, there were variations in earnings by job title, degree, major and industry. In the example below you can see the slight different in the mean value. The mean salary of Comp19 is 123.9 and for Comp37, 124.2. What's obvious are the outliers, which can influence our predictions. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary__comp19.png)
![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary__comp37.png)

## Modeling
After examining the data, I removed outliers below the 25th and above the 75th percentile, keeping the interquartile range. This resulted in 992,418 records in our dataset. 

After reviewing the EDA process, I established the following features as predictors for training the model. 

* Selected companyId,  jobType, degree, major, industry, milesFromMetropolitan and yearsExperience
* Label encoded all categorical variables 
* Imputed 63 values from companyId
* Imputed 8 values from jobType
* Imputed 5 values from degree
* Imputed 7 values from industry
* Imputed 10 values from major
* Created 4 additional features by applying the groupby method to companyId

This brought us to a total of 11 predictors.

I selected a ¾ - ¼ train-test split for the models.

Below are the results of the regression models after manually tuning and finalizing with grid search. 

| Model   | Performance | Performance with Hyperparam. Tuning | 
| :------------- |:-------------|:-----|
| Random Forest Regressor | 413.84 MSE| 352.18 MSE|
| XGB Regressor     | 350.71 MSE| 340.92 MSE|
| Gradient Boosting Regressor | 350.81 MSE| 341.48 MSE|

While each score varies, it’s apparent that XGB Regressor (XGBR) outperforms all models. One thing to note, XGBR not only out performs Gradient Boosting Regressor (GBR), but out performs significantly in training time (220% faster). This is due to XGBR’s ability to use multiple processors. While my attempting to improve GRB’s score, my initial thought was that increasing the number of trees in GBR would help, but this resulted in overfitting. With XGBR, increasing the trees did not result in overfitting, but instead a better score. This is likely due to the fact that XGBR trains multiple trees at the same time and  takes the average of those trees, which prevents overfitting. 

## Conclusion
One key take away from this project was seeing how an individuals industry influences their salary. For example, one could have a PhD, but can earn more in the Oil and Finance industry than in Service or Education. Perhaps students looking to take out student loans can look at the industry they want to pursue and decide if such a career would allow them to pay off the loan. 

Future iterations of this project would include further EDA and feature engineering specifically for folks who earn more than $220,000 a year. By removing outliers from the upper quartile (75th percentile), our ability to make accurate predictions for salaries beyond that threshold is effected negatively. I would perform more EDA on these records. Then I would create features specific to the subset to enhance the models predictive accuracy for this salary range.
