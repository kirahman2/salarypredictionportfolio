![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary-image.png)
# How Can We Predict Salary Based on Employee Job Descriptions?

## Introduction
For this salary prediction project I examined different attributes of employee information to predict their salary

## Data
The data is part of an existing data set that includes employee information. The features of the dataset include job id, company id, job type, degree, major, industry, years experience and miles the employee lives from from the metropolitan city. The actual size of the dataset is 1,000,000 rows. 

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Removed 5 rows where salary equaled 0, which indicated missing values 
* Removed 7117 rows for salaries more than 220 since this goes beyond the upper 75% percentile (outlier removal)
* Records with a degree and major listed as "None" were replaced with "Missing"
* Imputed categorical variables including company id, job type, degree, major and industry 

## Exploratory Data Analysis
Prior to the exploratory phase I hypothesized that a higher level education equated with a higher salary. To test this theory, I looked at a boxplot of salary compared against degree. It turns out that someone with a PhD earns only slightly more than someone with a masters and bachelors.

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_degree.png)

I was then curious about the different industries and hypothesized that the web industry would be the highest earning. It turns out Finance and Oil are the highest earning industries. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_industry.png)

After examining the results of each feature, I noticed Company Id was divided into 63 groups. After diving deeper and examining each feature against company Id, I did not find signs of grouping. I did however notice variation in the average salary for each Company Id group. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary_compid_.png)

Looking a bit deeper, within each company id group, there were variations in earnings by job title, degree, major and industry. In the example below you can see the slight different in the mean value. The mean salary of Comp19 is 123.9 and for Comp37, 124.2. What's even more obvious are the outliers, which can influence our predictions. 

![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary__comp19.png)
![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary__comp37.png)

The variations in company salary were important signals to consider. 

## Modeling
After examining the data, I removed outliers below the 25th and above the 75th percentile, keeping the inter quartile range. This resulted in 992,418 records in our dataset. 

After reviewing the EDA process, I established the following features as predictors for training the model. 

* Selected companyId,  jobType, degree, major, industry, miles from metropolitan and years experience
* Label encoded all categorical variables 
* Imputed 63 values from companyId
* Imputed 8 values from jobType
* Imputed 5 values from degree
* Imputed 7 values from industry
* Imputed 10 values from major
* Created 4 additional features by applying the groupby method to companyId

This brought us to a total of 11 predictors.

I selected a ¾ - ¼ train-test split for the models.

Here are the results of the regression models below. I first used manual tuning and completed tuning using grid search. 
