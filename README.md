![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

# How Employee Information Be Used To Predict Their Salary?

## Introduction
For this salary prediction project I am examining different attributes of employee information to predict their salary. 

What does this look like? 


## Data
The data is part of an existing data set that includes employee information. The features of the dataset used include job id, company id, job type, degree, major, industry, years experience and miles the employee lives from from the metropolitan city. The actual size of the dataset is 1,000,000 rows. 

## Preprocessing
For the data cleaning process, I followed the steps listed below.
* Removed 5 rows who's salaries were 0, which indicates missing values 
* Removed 7117 rows with salary more than 220 since this goes beyond the upper 75% percentile
* Certain individuals had a degree beyond high school, but "None" listed for their major, I relabelled as "Missing." The other group with major listed as None were those who had a high school education. It did not make sense to group the two together.
* Imputed categorical variables including company id, job type, degree, major and industry.

## Exploratory Data Analysis

## Modeling

## Conclusion
