![alt text](https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/salary-image.png)
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
* Records with a degree and major listed as "None" were replaced with "Missing"
* Imputed categorical variables including company id, job type, degree, major and industry

## Exploratory Data Analysis
I thought it would be fun to ask more immediate exciting questions such as.. Does higher level education result in significant increase in pay? It turns out they are all fairly comparable to a bachelors and masters. 

![alt text](INSERT https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/boxplot_degree.png)

How do industries stack up amongst one another?

![alt text](INSERT https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/boxplot_industry.png)

What if we look specifically at Doctorals by PhD?

![alt text](INSERT https://github.com/kirahman2/salarypredictionportfolio/blob/master/Images/boxplot_doctoral_industry.png)

Though if we look at all these boxplots, what’s important is seeing the upward trend and groups that are provide information to help create a model for predicting salaries. 

What story are we telling… we need to tell a story.. What information does our EDA provide or reveal to us what things we need to include? NEXT, study sashas README to understand the story.
